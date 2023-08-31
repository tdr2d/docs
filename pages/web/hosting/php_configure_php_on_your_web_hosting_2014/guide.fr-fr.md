---
title: "Hébergement web - Environnement, version PHP, « .ovhconfig »"
excerpt: "Découvrez comment modifier l'environnement d'exécution, la version PHP, le pare-feu applicatif, le moteur, le mode et l'« .ovhconfig » d'un hébergement web"
updated: 2023-08-29
---

## Objectif

Les offres d'[hébergement web OVHcloud](https://www.ovhcloud.com/fr/web-hosting/){.external} permettent d’héberger le site web que vous souhaitez, tant que celui-ci est compatible avec la [configuration de nos infrastructures mutualisées](https://webhosting-infos.hosting.ovh.net){.external}.
Toutefois, sur nos infrastructures mutualisées, vous pouvez modifier les paramètres suivants pour votre hébergement web :

- [l'environnement d'exécution](#runtime-evironment)
- [la version de PHP](#php-versions)
- [le moteur d'exécution PHP](#php-runtime)
- **le pare-feu applicatif** : sécurité qui filtre les requêtes entrantes de votre hébergement web;
- **le mode d'exécution** : permet de gérer le comportement du cache des fichiers statiques de votre site web (des images par exemple) ainsi que le traitement des erreurs PHP.

Ces paramètres de configuration sont modifiables de deux manières :

- Depuis votre [espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr);
- Depuis l'espace de stockage FTP de votre hébergement web OVHcloud à l'aide d'un fichier nommé « .ovhconfig ».

> [!primary]
>
> Les fichiers « .ovhconfig » sont des fichiers de configuration serveur et sont automatiquement reconnus comme tel par l'infrastructure d'hébergement mutualisée.
> Ils sont présents nativement et par défaut à la « racine FTP » de l'espace de stockage FTP de votre hébergement web.
> Ils contiennent les valeurs des éléments évoqués au dessus.
>

En résumé, modifier la configuration de votre hébergement web depuis l'espace client OVHcloud ou modifier les valeurs présentes dans le fichier « .ovhconfig » revient à réaliser la même opération.

**Découvrez comment modifier l'environnement d'exécution, la version PHP, le pare-feu applicatif, le moteur, le mode et l'« .ovhconfig » d'un hébergement web.**

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/X31MNMLw064" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Prérequis

- Disposer d’une offre d’[hébergement web OVHcloud](https://www.ovhcloud.com/fr/web-hosting/){.external}, à l'exception d'une offre d'hébergement Cloud Web.
- Avoir accès à votre offre d’hébergement web depuis l’[espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr) ou connaître les informations permettant de se connecter à l'[espace de stockage FTP](/pages/web/hosting/ftp_connection). 

## En pratique

D'abord, nous vous présenterons [l'ensemble des paramètres de configuration disponibles sur les hébergements web OVHcloud](#all-parameters) et leurs valeurs techniques.
Ensuite, nous vous expliquerons les 2 méthodes pour modifier ces paramètres [depuis votre espace client OVHcloud](#setting-ovh-manager) ou directement à [depuis le fichier « .ovhconfig »](#setting-ovhconfig).

### 1 - Description des paramètres de configuration disponibles sur les hébergements web OVHcloud <a name="all-parameters"></a>

Avant de commencer, retrouvez ci-après la description technique de chacun des paramètres modifiables sur les hébergements web OVHcloud.

> [!warning]
>
> Modifier au moins l'un de ces éléments peut avoir des conséquences sur l'affichage ou le bon fonctionnement de votre site web. **Assurez-vous au préalable que votre site web est compatible avec les changements que vous souhaitez effectuer dans la configuration de votre hébergement web.** Contactez un [prestataire spécialisé](https://partner.ovhcloud.com/fr/directory/) si vous éprouvez des difficultés.
>

####  1.1 - Les environnements d'exécution <a name="runtime-evironment"></a>

Les environnements d'exécution contiennent un ensemble de langages de programmation. En fonction de l'environnement d'exécution choisi, les langages sont disponibles dans des versions plus ou moins avancées. L'objectif de ces environnements est de vous permettre d'exécuter correctement les fichiers qui composent votre site web, en adéquation avec vos besoins techniques. Cela permet de modifier certaines valeurs techniques de votre hébergement web.

Sur les hébergements web OVHcloud, nous proposons **3** environnements d'exécution : *Legacy*, *Stable* et *Stable64*.
Retrouvez ci-dessous les éléments contenus dans nos différents environnements d'exécution :

|Environnements|Legacy|Stable|Stable64|
|---|---|---|---|
|architecture|32 bits|32 bits|64 bits|
|Version PHP minimum|5.4|5.4|7.4|
|Openssl|1.0.1t|1.0.1t|1.1.1n|
|Python|2.7 et 3.4|2.7 et 3.7|2.7 et 3.7|
|Ruby|2.1|2.1|2.5|
|Rails|4.1|4.1|5.2|
|Perl|5.20|5.20|5.28|
|git|2.1|2.1|2.20|

> [!primary]
>
> L'environnement *Legacy* peut être utile pour d'anciens sites utilisant encore de vieilles versions de PHP. Cependant, nous vous recommandons vivement d'utiliser l'environnement *Stable64* bénéficiant des dernières mises à jour. **Assurez-vous cependant que votre site web est bien compatible avant d'entamer tout changement.**
> 

####  1.2 - Les versions de PHP <a name="php-versions"></a>

PHP est un langage de programmation dynamique utilisé pour réaliser des sites web. Pour votre site web et en fonction de l'ancienneté, des mises à jour effectuées ou de certaines variables nécessaires à son bon fonctionnement, vous pouvez être amené à changer la version de PHP qu'il utilise

Plusieurs versions du langage de programmation PHP existent. Les évolutions de versions apportent des correctifs divers, ainsi que l'ajout ou l'arrêt de fonctionnalités. OVHcloud propose les dernières versions majeures de PHP dont vous pouvez retrouver la liste [ici](https://www.ovhcloud.com/fr/web-hosting/uc-programming-language/). 

Certaines versions de PHP ne fonctionnent qu'avec certains environnements d'exécution. Vous trouverez ci-après les versions de PHP disponibles sur les hébergements mutualisés OVHcloud et [les environnements d'exécution](#runtime-evironment) compatibles :

|Versions PHP|Environnements d'exécution compatibles|
|---|---|
|5.4, 5.5, 5.6 et 7.0|Legacy, Stable|
|7.1, 7.2 et 7.3|Stable|
|7.4, 8.0 et 8.1 (bêta)|stable64|

> [!primary]
>
> Du fait que certaines fonctionnalités peuvent ne pas être maintenues au fil des nouvelles versions, **assurez-vous, avant d'entamer tout changement, que la nouvelle version de PHP souhaitée est compatible avec votre site internet.**
>

Même si OVHcloud gère l'installation des dernières versions de PHP sur ses serveurs, il vous revient de vous assurer que votre site web est **toujours à jour** et compatible avec les dernières versions de PHP. Pour vous en assurer, deux possibilités existent selon le site web que vous utilisez :

**Cas n°1 : vous utilisez un Content Management System (CMS)** tel que *WordPress*, *Joomla!*, *PrestaShop* ou *Drupal* : 

- Consultez la documentation officielle créée par l'éditeur du CMS que vous utilisez.
- Prenez note des informations concernant les prérequis techniques nécessaires au fonctionnement de votre CMS, ainsi que la manipulation permettant de le mettre à jour.
- Si nécessaire, mettez à jour votre CMS en vous assurant que la nouvelle version est compatible avec l'hébergement web OVHcloud.

**Cas n°2 : vous utilisez un site basé sur une solution personnalisée** : 

- Rapprochez-vous du webmaster ayant créé le site web.
- Aidez-vous de la [documentation officielle PHP](http://php.net/manual/en/appendices.php){.external} donnant plus d'informations sur les migrations de version.
- Si nécessaire, mettez à jour le code de votre site web en vous assurant que celui-ci reste compatible avec l'hébergement web OVHcloud.

Si besoin, vous pouvez connaître la version de PHP actuellement utilisée par votre hébergement web de deux façons :

- **via l'espace client OVHcloud** : connectez-vous à [l'espace client OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/fr/&ovhSubsidiary=fr){.external} puis rendez-vous dans la partie `Web Cloud`{.action}. Dans la colonne de gauche, cliquez sur `Hébergements`{.action} puis choisissez l'hébergement web concerné. Dans l'onglet `Informations générales`{.action}, repérez la version en dessous de *Version PHP globale*. 

![phpversion](images/change-php-version-step1.png){.thumbnail}

> [!primary]
> Si un symbole rond de couleur bleue est présent, patientez quelques minutes le temps que la version s'actualise.
>

- **via un script** : Créez un script **.php** contenant uniquement le code suivant :

```php
<?php phpinfo(); ?>
```

Mettez-le ensuite en ligne sur votre [espace de stockage FTP](/pages/web/hosting/ftp_connection), puis appelez-le en accédant à son adresse/URL complète.

> [!warning]
>
> La modification de la version de PHP via un fichier « .htaccess » n'est plus possible sur les dernières offres d'[hébergement web OVHcloud](https://www.ovhcloud.com/fr/web-hosting/){.external}.<br>
> La commande permettant de changer la version de PHP dans le fichier « .htaccess » ne permet pas non plus d'utiliser les versions récentes de PHP sur nos infrastructures.
> Pour cela, vous devrez obligatoirement utiliser le fichier « .ovhconfig ».
>

####  1.3 - Les moteurs d'exécutions PHP <a name="php-runtime"></a>

Les moteurs d'exécutions PHP sont des programmes permettant d'exécuter des actions sur le serveur web selon une méthode donnée. Généralement, ce paramètre est modifié pour agir sur la vitesse d'exécution des requêtes générées par les visiteurs de votre site web.

Sur les hébergements web OVHcloud, nous proposons **2** moteurs d'exécutions PHP : *php* et *phpcgi*.


## Aller plus loin

[Se connecter à l’espace de stockage de son hébergement Web](/pages/web/hosting/ftp_connection){.external}

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](https://partner.ovhcloud.com/fr/directory/).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](https://www.ovhcloud.com/fr/support-levels/).

Échangez avec notre communauté d'utilisateurs sur <https://community.ovh.com>
