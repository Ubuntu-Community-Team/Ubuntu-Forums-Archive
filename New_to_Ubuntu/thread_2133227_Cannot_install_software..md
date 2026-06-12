---
title: "Cannot install software."
date: 2013-04-07
forum: New to Ubuntu
---

### Post by guillaumesoucy on 2013-04-07
Hi, 

I have downloaded a program and when I right click on it and I select Ubuntu Softwae Center I recive that error:  cannot install libxml-simple-perl

Please see the screen shot,

Someone know how fix that?

Thanks, 

Guillaume

---

### Post by dillonboardman on 2013-04-07
Have you tried installing it from the Terminal? If it doesn't install that way, it SHOULD at least give a hint as to why.

---

### Post by guillaumesoucy on 2013-04-07
Hi, 

How I can try to install it from the teminal, the company who issue the software dont give a commande like sudo get apt.

Guillaume

---

### Post by dillonboardman on 2013-04-07
Assuming that the package that you're installing is a .deb

sudo dpkg -i package_file.deb

I hope that this helps.

---

### Post by oldos2er on 2013-04-07
Run ```
sudo apt-get update
``` in a terminal, then retry the install.

---

### Post by Frogs Hair on 2013-04-07
You may have a dependency conflict. 

Install: ```
sudo dpkg -i packagename.deb
```

---

### Post by guillaumesoucy on 2013-04-07
Hi, 

Thats do something but there was missing packet with the name begining by ''lib'' where I can find these packet?

Thanks, 

Guillaume

---

### Post by guillaumesoucy on 2013-04-07
Hi, 

The terminal said 

guillaumesoucy@Zawack-004:~$ sudo dpkg -i storagemadeeasy_4.0.1.deb
[sudo] password for guillaumesoucy: 
(Lecture de la base de données... 172246 fichiers et répertoires déjà installés.)
Préparation du remplacement de storagemadeeasy 4.0-1 (en utilisant storagemadeeasy_4.0.1.deb) ...
delete /usr/bin/smemount
Dépaquetage de la mise à jour de storagemadeeasy ...
dpkg : des problèmes de dépendances empêchent la configuration de storagemadeeasy :
 storagemadeeasy dépend de libqt4-core (>= 4.3) ; cependant :
  Le paquet libqt4-core n'est pas installé.
 storagemadeeasy dépend de libxml-simple-perl ; cependant :
  Le paquet libxml-simple-perl n'est pas installé.
 storagemadeeasy dépend de libqt4-gui ; cependant :
  Le paquet libqt4-gui n'est pas installé.
 storagemadeeasy dépend de libqt4-dev ; cependant :
  Le paquet libqt4-dev n'est pas installé.
dpkg : erreur de traitement de storagemadeeasy (--install) :
 problèmes de dépendances - laissé non configuré
Traitement des actions différées (« triggers ») pour « desktop-file-utils »...
Traitement des actions différées (« triggers ») pour « bamfdaemon »...
Rebuilding /usr/share/applications/bamf.index...
Traitement des actions différées (« triggers ») pour « gnome-menus »...
Des erreurs ont été rencontrées pendant l'exécution :
 storagemadeeasy
guillaumesoucy@Zawack-004:~$ 


Its in french.

Guillaume

---

### Post by guillaumesoucy on 2013-04-07
Sorry I dont see your post before, I will try. 

Guillaume

---

### Post by guillaumesoucy on 2013-04-07
Hi, 

I try but thats always said 

Hi, 

The terminal said 

guillaumesoucy@Zawack-004:~$ sudo dpkg -i storagemadeeasy_4.0.1.deb
[sudo] password for guillaumesoucy: 
(Lecture de la base de données... 172246 fichiers et répertoires déjà installés.)
Préparation du remplacement de storagemadeeasy 4.0-1 (en utilisant storagemadeeasy_4.0.1.deb) ...
delete /usr/bin/smemount
Dépaquetage de la mise à jour de storagemadeeasy ...
dpkg : des problèmes de dépendances empêchent la configuration de storagemadeeasy :
 storagemadeeasy dépend de libqt4-core (>= 4.3) ; cependant :
  Le paquet libqt4-core n'est pas installé.
 storagemadeeasy dépend de libxml-simple-perl ; cependant :
  Le paquet libxml-simple-perl n'est pas installé.
 storagemadeeasy dépend de libqt4-gui ; cependant :
  Le paquet libqt4-gui n'est pas installé.
 storagemadeeasy dépend de libqt4-dev ; cependant :
  Le paquet libqt4-dev n'est pas installé.
dpkg : erreur de traitement de storagemadeeasy (--install) :
 problèmes de dépendances - laissé non configuré
Traitement des actions différées (« triggers ») pour « desktop-file-utils »...
Traitement des actions différées (« triggers ») pour « bamfdaemon »...
Rebuilding /usr/share/applications/bamf.index...
Traitement des actions différées (« triggers ») pour « gnome-menus »...
Des erreurs ont été rencontrées pendant l'exécution :
 storagemadeeasy
guillaumesoucy@Zawack-004:~$ 

Guillaume

---

### Post by guillaumesoucy on 2013-04-07
If I download libqt4-core.deb and I do in the terminal sudo dpkg -i libqt4-core.deb, there was others dependencys. Did you know if there was a way to install all dependencys in the same time?

Thanks,


Guillaume

---

### Post by slooksterpsv on 2013-04-07
sudo apt-get install -f

It'll go through, install the dependencies and install the program you were trying to install.

---

### Post by guillaumesoucy on 2013-04-07
Hi, 

I enter the command sudo apt-get install -f, packet seem to be installed but when entering sudo dpkg -i storagemadeeasy_4.0.1.deb for installing the software thats show other packet dependency but there was less packet missing. Please see the log.



guillaumesoucy@Zawack-004:~$ sudo apt-get install -f
[sudo] password for guillaumesoucy: 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  libfuse-dev libhttp-daemon-perl libfile-listing-perl libwww-robotrules-perl
  libfuse-perl libnet-ssleay-perl liburi-perl libxml-namespacesupport-perl
  libfilesys-statvfs-perl g++-4.6 libhttp-date-perl liblwp-mediatypes-perl
  libfont-afm-perl libmailtools-perl libsocket6-perl libhtml-parser-perl g++
  libxml-parser-perl liblwp-protocol-https-perl qt4-qmake liblchown-perl
  libio-socket-inet6-perl libtimedate-perl libhtml-form-perl
  libhttp-negotiate-perl libsepol1 libhtml-format-perl libencode-locale-perl
  libselinux1-dev libhtml-tree-perl libxml-sax-base-perl libio-socket-ssl-perl
  libwww-perl fuse-utils libhttp-cookies-perl libstdc++6-4.6-dev
  libhttp-message-perl libhtml-tagset-perl libsepol1-dev libnet-http-perl
Veuillez utiliser « apt-get autoremove » pour les supprimer.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
guillaumesoucy@Zawack-004:~$ sudo dpkg -i storagemadeeasy_4.0.1.deb
Sélection du paquet storagemadeeasy précédemment désélectionné.
(Lecture de la base de données... 173091 fichiers et répertoires déjà installés.)
Dépaquetage de storagemadeeasy (à partir de storagemadeeasy_4.0.1.deb) ...
dpkg : des problèmes de dépendances empêchent la configuration de storagemadeeasy :
 storagemadeeasy dépend de libqt4-core (>= 4.3) ; cependant :
  Le paquet libqt4-core n'est pas installé.
 storagemadeeasy dépend de libxml-simple-perl ; cependant :
  Le paquet libxml-simple-perl n'est pas installé.
 storagemadeeasy dépend de libqt4-gui ; cependant :
  Le paquet libqt4-gui n'est pas installé.
 storagemadeeasy dépend de libqt4-dev ; cependant :
  Le paquet libqt4-dev n'est pas installé.
dpkg : erreur de traitement de storagemadeeasy (--install) :
 problèmes de dépendances - laissé non configuré
Traitement des actions différées (« triggers ») pour « desktop-file-utils »...
Traitement des actions différées (« triggers ») pour « bamfdaemon »...
Rebuilding /usr/share/applications/bamf.index...
Traitement des actions différées (« triggers ») pour « gnome-menus »...
Des erreurs ont été rencontrées pendant l'exécution :
 storagemadeeasy
guillaumesoucy@Zawack-004:~$ 

How to install libqt4-core?

Thanks.

Guillaume

---

### Post by Impavidus on 2013-04-07
Try```

sudo apt-get install libqt4-core libxml-simple-perl libqt4-gui libqt4-dev

```
It seems those are the dependencies you need. This command will automatically install all dependencies of these four packages as well.

BTW, running```
sudo apt-get autoremove
``` won't hurt. You've quite a lot of packages that can be cleaned up.

---

### Post by guillaumesoucy on 2013-04-07
Hi, 

The packages have other depencency too. 

guillaumesoucy@Zawack-004:~$ sudo apt-get install libqt4-core libxml-simple-perl libqt4-gui libqt4-dev
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Vous pouvez lancer « apt-get -f install » pour corriger ces problèmes :
Les paquets suivants contiennent des dépendances non satisfaites :
 libqt4-core : Dépend: libqt4-dbus (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
               Dépend: libqt4-network (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
               Dépend: libqt4-script (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
               Dépend: libqt4-test (= 4:4.8.1-0ubuntu4) mais ne sera pas installé
               Dépend: libqt4-xml (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
               Dépend: libqtcore4 (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
 libqt4-dev : Dépend: libqt4-dbus (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
              Dépend: libqt4-declarative (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
              Dépend: libqt4-designer (= 4:4.8.1-0ubuntu4) mais ne sera pas installé
              Dépend: libqt4-help (= 4:4.8.1-0ubuntu4) mais ne sera pas installé
              Dépend: libqt4-network (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
              Dépend: libqt4-qt3support (= 4:4.8.1-0ubuntu4) mais ne sera pas installé
              Dépend: libqt4-script (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
              Dépend: libqt4-scripttools (= 4:4.8.1-0ubuntu4) mais ne sera pas installé
              Dépend: libqt4-sql (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
              Dépend: libqt4-svg (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
              Dépend: libqt4-test (= 4:4.8.1-0ubuntu4) mais ne sera pas installé
              Dépend: libqt4-xml (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
              Dépend: libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
              Dépend: libqtcore4 (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
              Dépend: libqtgui4 (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
              Dépend: qt4-linguist-tools (= 4:4.8.1-0ubuntu4) mais ne sera pas installé
              Recommande: libqt4-opengl-dev (= 4:4.8.1-0ubuntu4) mais ne sera pas installé
              Recommande: libqtwebkit-dev (>= 2.0~) mais ne sera pas installé
 libqt4-gui : Dépend: libqt4-designer (= 4:4.8.1-0ubuntu4) mais ne sera pas installé
              Dépend: libqt4-opengl (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
              Dépend: libqt4-svg (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
              Dépend: libqtgui4 (= 4:4.8.1-0ubuntu4) mais 4:4.8.1-0ubuntu4.3 devra être installé
 libxml-simple-perl : Dépend: libxml-sax-perl mais ne sera pas installé
                      Dépend: libxml-libxml-perl mais ne sera pas installé ou
                               libxml-sax-expat-perl mais ne sera pas installé
E: Dépendances non satisfaites. Essayez « apt-get -f install » sans paquet
(ou indiquez une solution).
guillaumesoucy@Zawack-004:~$ 

Did you know how install these packets too?

Thanks,

Guillaume

---

### Post by Impavidus on 2013-04-07
There is a version mix-up in your package system. Things shouldn't be this complicated. It says it needs version 4:4.8.1-0ubuntu4 of several packages, but can only install version 4:4.8.1-0ubuntu4.3. (On my system (12.04 LTS) these packages are at version 4:4.8.1-0ubuntu4.4)

You haven't told us your Ubuntu version yet. Could you?

---

### Post by guillaumesoucy on 2013-04-07
Hi, 

I use Ubuntu 12.04 LTS

Guillaume

---

### Post by schragge on 2013-04-07
[size=-1]*Removed. Sorry, wrongly posted*[/size]

---

### Post by guillaumesoucy on 2013-04-07
ok

---

