---
layout: post
title: SIG collaboratif
subtitle: Solution simple et gratuite
author: Zoran
published: true
---

Travailler, ce n'est peut-être pas toujours la chose la plus passionnante, mais c'est quand même plus amusant (et plus efficace) en collaboration. Il y a, dans le monde de SIG, bien de solutions pour le travail collaboratif sur un même jeu de données, mais le plus souvent elles sont soit couteuses, soit exigeantes au niveau technique. Cependant, il existe un moyen quelque peu obscur, caché dans le benthos de l’internet, qui permet d’utiliser l’architecture collaborative – gratuitement. Le hébergeur (fournisseur / prestataire ) [Alwaysdata]( www.alwaysdata.com) (la compagnie est française malgré le nom) offre dans son paquet découverte l’hébergement des bases de données PostGIS, très performantes et largement utilisées dans le monde SIG.

Nous verrons maintenant comment aborder le problème le plus basique : créer une base de données en ligne pour s’y connecter par la suite.

1)	D’abord il faut créer un compte sur le site d’[Awaysdata](www.alwaysdata.com) et ajouter ensuite une base de données PostgreSQL (dans le tableau de bord, choisir *Bases de données >> PostgreSQL*). Renseignez le nom de la base, et surtout cochez la case PostGIS (ce dernier étant une extension de PostgreSQL).

![2017-06-10-alwaysdata1.png]({{site.baseurl}}/img/2017-06-10-alwaysdata1.jpg)


2)	Ensuite, il faut ajouter un/des utilisateurs et renseigner le/les mots de passe (toujours dans la même rubrique « *Bases de données >> PostgreSQL* »). Pour l’utilisateur-propriétaire, le mot de passe est le même que pour le compte même (sauf si spécifié autrement).

![2017-06-10-alwaysdata2.png]({{site.baseurl}}/img/2017-06-10-alwaysdata2.jpg)

  
3)	Enfin le dernier élément, l’adresse internet de notre base. Celle-ci sera affichée après la création de la base et devrait ressembler à « postgresql-NOM_DE_INSCRIPTION.awaysdata.net ». Notez-la.
 
![2017-06-10-alwaysdata3.png]({{site.baseurl}}/img/2017-06-10-alwaysdata3.jpg)

Nous disposons maintenant de quatre informations nécessaires : adresse de la base, son nom et le nom d’utilisateur avec son mot de passe. D’autres utilisateurs/collaborateurs peuvent être ajoutés par la suite, bien évidemment.
Je passerai maintenant au QGIS pour faire marcher l’engin. Il s’agit tout simplement d’une connexion à la base de données, ce qui devrait être faisable par n’importe quel logiciel SIG digne de ce nom.  

a)	Approche directe : Ajouter une couche PostGIS. Choisir une nouvelle connexion et remplir les cases avec nos informations. 

![2017-06-10-QGIS1.jpg]({{site.baseurl}}/img/2017-06-10-QGIS1.jpg)

Ensuite, dans *Database >> Manager* utiliser la fonction Import layer pour ajouter les données (parce que la base est vide …)

b)	Approche « comme il faut ». On devrait plutôt gérer nos sources de données dans le QGIS Browser, c’est plus propre. Donc, tout simplement, créer une connexion en renseignant les mêmes informations que dessus (laissez vide la case « service »). Passez, ensuite, dans le QGIS et ajoutez la couche PostGIS depuis cette connexion.


![2017-06-10-QGIS2.jpg]({{site.baseurl}}/img/2017-06-10-QGIS2.jpg)

Et voilà, une solution « pro » ! PostGIS est capable de gèrer *des centaines* d’utilisteurs, donc pas de souci au niveau de software. Pour des usages avancés, vous avez l’accès direct à la base PostGIS via l’addresse [phppgadmin.alwaysdata.com](https://phppgadmin.alwaysdata.com/). (C’est le sujet pour une autre occasion…)
 
## B-mol (il y en toujours un…)

La solution décrite ici utilise un paquet promotionnel : aucune obligation particulière n'est pas impliquée de part de l’hébergeur (ci j’ai bien compris). En effet, votre compte, *avec tous vos données* sera d’abord suspendu dans le cas d’une période d’inactivité supérieure à deux mois, pour se faire carrément *effacer* suite à 30 jours supplémentaires (au mois c’est mon expérience). Il s’agit, en fin de compte, d’un paquet gratuit, promotionnel, mais avec des fonctionnalités assez avancées (notamment au niveau d’instalation de PostGIS) : on ne devrait pas critiquer, c’est déjà pas mal ! Investissez quelques sous dans le cas d’un travail plus sérieux… (Je n’ai aucun lien avec la compagnie.) 

La taille de l’hébergement entier est limité à 100 mb : cela devrait souffrir pour une utilisation plutôt légère, mais probablement pas pour des projets d’envergure.

Enfin, restent tous les problèmes d’organisation d’une base collective. Par exemple, qu’est-ce qu’il se passe dans le cas de modification par plusieurs utilisateurs en même temps ? Sans un paramétrage supplémentaire, c’est le plus rapide qui gagne. Mais, c’est le problème pour une autre occasion… [(voir ici, par exemple)](http://workshops.boundlessgeo.com/postgis-intro/history_tracking.html)
