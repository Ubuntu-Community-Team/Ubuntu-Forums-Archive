---
title: "I can't install freeglut3-dev"
date: 2006-05-10
forum: Repositories &amp; Backports
---

### Post by FabienB on 2006-05-10
Hi all,

When I try to install freeglut3-dev package, I get the following error :

[FONT="Courier New"]fabien@frpcf256470:~$ sudo apt-get install freeglut3-dev
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Certains paquets ne peuvent être installés. Ceci peut signifier
que vous avez demandé l'impossible, ou bien, si vous utilisez
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.

Puisque vous n'avez demandé qu'une seule opération, le paquet n'est
probablement pas installable et vous devriez envoyer un rapport de bogue.
L'information suivante devrait vous aider à résoudre la situation :

Les paquets suivants contiennent des dépendances non satisfaites :
  freeglut3-dev: Dépend: xlibmesa-gl-dev mais il n'est pas installable ou
                          libgl-dev
                 Dépend: xlibmesa-glu-dev mais il n'est pas installable ou
                          libglu-dev
E: Paquets défectueux
[/FONT]

Which means, in english, that freeglut3-dev depends on xlibmesagl-dev and xlibmesa-glu-dev, but both aren't installable because I can't find them in any repository (universe, multiverse, etc...).

Any idea ?

---

### Post by FabienB on 2006-05-10
My sources.list

# 
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

