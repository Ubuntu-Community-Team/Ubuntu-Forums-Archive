---
title: "Problems with package update"
date: 2005-01-19
forum: Repositories &amp; Backports
---

### Post by buenaventura_d on 2005-01-19
High everybody,

I have installed Ubuntu since some days and I have some problems to update packages via synaptics or apt-get.
The error message is following :
"Preconfiguring packages ...
(Lecture de la base de données... dpkg : erreur de traitement de /var/cache/apt/archives/libmagick6_5%3a6.0.2.5-1ubuntu1.3_i386.deb (--unpack) :
files list file for package `libgimp2.0' is missing final newline
Des erreurs ont été rencontrées pendant l'exécution :
/var/cache/apt/archives/libmagick6_5%3a6.0.2.5-1ubuntu1.3_i386.deb
L'exécution a été arrêtée car il y avait trop d'erreurs.
E: Sub-process /usr/bin/dpkg returned an error code (1)" 

Have you any idea ?
I'm really newbie...

Thanks a lot

Buenaventura

---

### Post by feneks on 2005-01-19
Have you already installed anything with apt-get or Synaptic?
What do you want to install?
Your output isn't in english this might scare others away :wink:

Je sais Francais. C'est pourquoi je peux lire cette texte. 
In fact I haven't written/spoken Frensh for 4 years!


Okay think
```
sudo apt-get update
or
sudo apt-get clean
```
won't help - but give it a try.

```
sudo apt-get -f install 
```
could solve the problem

---

