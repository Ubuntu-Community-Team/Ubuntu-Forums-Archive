---
title: "lsb-release update issue"
date: 2011-08-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by maximiliengolum on 2011-08-17
Hello, sorry for my english, i'm french.
I'm using oneiric 32bits, with 3.0.0-8-generic kernel.
From Yesterday, the pakage lsb-release don't want to update, apt return this error message:

moi@Portable:~$ sudo apt-get upgrade
[sudo] password for moi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Les paquets suivants seront mis à jour*:
  lsb-release
1 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
17 partiellement installés ou enlevés.
Il est nécessaire de prendre 0 o/11,1 ko dans les archives.
Après cette opération, 4 096 o d'espace disque seront libérés.
Souhaitez-vous continuer [O/n]*? O       
(Lecture de la base de données... 184088 fichiers et répertoires déjà installés.)
Préparation du remplacement de lsb-release 4.0-0ubuntu13 (en utilisant .../lsb-release_4.0-0ubuntu14_i386.deb) ...
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 24, in <module>
    import logging
EOFError: EOF read where not expected
dpkg*: avertissement*:*le sous-processus ancien script pre-removal a retourné une erreur de sortie d'état 1
dpkg - tentative d'exécution du script du nouveau paquet à la place ...
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 24, in <module>
    import logging
EOFError: EOF read where not expected
dpkg*: erreur de traitement de /var/cache/apt/archives/lsb-release_4.0-0ubuntu14_i386.deb (--unpack)*:
 le sous-processus nouveau script pre-removal a retourné une erreur de sortie d'état 1
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/py3compile", line 26, in <module>
    import logging
EOFError: EOF read where not expected
dpkg*: erreur lors du nettoyage*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 1
Des erreurs ont été rencontrées pendant l'exécution*:
 /var/cache/apt/archives/lsb-release_4.0-0ubuntu14_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
moi@Portable:~$ 

I'v tried apt-get upgrade -f ; apt-get clean ; to download the pakage lsb-release_4.0-0ubuntu14_all.deb and force to instill it with dpkg ; to launch ubuntu in recovery mode and launch dpkg.

But no one of this trying solved my issue, want can i do?

---

### Post by drs305 on 2011-08-17
The lsb_release pre-removal script is generating the first error. Try renaming this script and then attempt to reinstall lsb_release. If the post-rm error still exists we can try renaming that file as well.

```
sudo mv /var/lib/dpkg/info/lsb-release.prerm /var/lib/dpkg/info/lsb-release.prerm.bad
sudo apt-get install --reinstall lsb-release
```

---

### Post by dino99 on 2011-08-17
select "main" server from synaptic, then update and

sudo dpkg-reconfigure lsb-release

---

### Post by maximiliengolum on 2011-08-18
Thanks for yours replies, I've tried yours solutions, lsb-release is partially installed (it don't want to configure), and now, 19 others package are too.. 

```
moi@Portable:~$ sudo apt-get upgrade
[sudo] password for moi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
20 partiellement installés ou enlevés.[COLOR="MediumTurquoise"](20 partially installed or removed)[/COLOR]
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n]*? O
Paramétrage de lsb-release (4.0-0ubuntu14) ...
Traceback (most recent call last):
  File "/usr/bin/py3compile", line 26, in <module>
    import logging
EOFError: EOF read where not expected
dpkg*: erreur de traitement de lsb-release (--configure)*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 1
dpkg*: des problèmes de dépendances empêchent la configuration de ubuntu-minimal*:
 ubuntu-minimal dépend de lsb-release*; cependant*:
 Le paquet lsb-release n'est pas encore configuré.
dpkg*: erreur de traitement de ubuntu-minimal (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de update-manager-core*:No apport report written because the error message indicates its a followup error from a previous failure.

 update-manager-core dépend de lsb-release*; cependant*:
 Le paquet lsb-release n'est pas encore configuré.
dpkg*: erreur de traitement de update-manager-core (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de python-software-properties*:No apport report written because the error message indicates its a followup error from a previous failure.

 python-software-properties dépend de lsb-release*; cependant*:
 Le paquet lsb-release n'est pas encore configuré.
dpkg*: erreur de traitement de python-software-properties (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de python-aptdaemon*:No apport report written because MaxReports is reached already

 python-aptdaemon dépend de python-software-properties*; cependant*:
 Le paquet python-software-properties n'est pas encore configuré.
dpkg*: erreur de traitement de python-aptdaemon (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de aptdaemon*:No apport report written because MaxReports is reached already

 aptdaemon dépend de python-aptdaemon (= 0.43+bzr670-0ubuntu1)*; cependant*:
 Le paquet python-aptdaemon n'est pas encore configuré.
dpkg*: erreur de traitement de aptdaemon (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de python-aptdaemon.gtk3widgets*:No apport report written because MaxReports is reached already

 python-aptdaemon.gtk3widgets dépend de python-aptdaemon (= 0.43+bzr670-0ubuntu1)*; cependant*:
 Le paquet python-aptdaemon n'est pas encore configuré.
dpkg*: erreur de traitement de python-aptdaemon.gtk3widgets (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de language-selector-gnome*:No apport report written because MaxReports is reached already

 language-selector-gnome dépend de aptdaemon (>= 0.40+bzr527)*; cependant*:
 Le paquet aptdaemon n'est pas encore configuré.
 language-selector-gnome dépend de python-aptdaemon.gtk3widgets*; cependant*:
 Le paquet python-aptdaemon.gtk3widgets n'est pas encore configuré.
dpkg*: erreur de traitement de language-selector-gnome (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de python-aptdaemon.gtkwidgets*:No apport report written because MaxReports is reached already

 python-aptdaemon.gtkwidgets dépend de python-aptdaemon (= 0.43+bzr670-0ubuntu1)*; cependant*:
 Le paquet python-aptdaemon n'est pas encore configuré.
dpkg*: erreur de traitement de python-aptdaemon.gtkwidgets (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de python-aptdaemon-gtk*:No apport report written because MaxReports is reached already

 python-aptdaemon-gtk dépend de python-aptdaemon.gtkwidgets (= 0.43+bzr670-0ubuntu1)*; cependant*:
 Le paquet python-aptdaemon.gtkwidgets n'est pas encore configuré.
 python-aptdaemon-gtk dépend de python-aptdaemon.gtk3widgets (= 0.43+bzr670-0ubuntu1)*; cependant*:
 Le paquet python-aptdaemon.gtk3widgets n'est pas encore configuré.
dpkg*: erreur de traitement de python-aptdaemon-gtk (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de software-center*:No apport report written because MaxReports is reached already

 software-center dépend de python-aptdaemon (>= 0.40)*; cependant*:
 Le paquet python-aptdaemon n'est pas encore configuré.
 software-center dépend de python-aptdaemon-gtk*; cependant*:
 Le paquet python-aptdaemon-gtk n'est pas encore configuré.
 software-center dépend de aptdaemon (>= 0.40)*; cependant*:
 Le paquet aptdaemon n'est pas encore configuré.
dpkg*: erreur de traitement de software-center (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de software-properties-gtk*:No apport report written because MaxReports is reached already

 software-properties-gtk dépend de python-software-properties*; cependant*:
 Le paquet python-software-properties n'est pas encore configuré.
 software-properties-gtk dépend de python-aptdaemon.gtk3widgets*; cependant*:
 Le paquet python-aptdaemon.gtk3widgets n'est pas encore configuré.
dpkg*: erreur de traitement de software-properties-gtk (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de update-manager*:No apport report written because MaxReports is reached already

 update-manager dépend de update-manager-core (= 1:0.152.14)*; cependant*:
 Le paquet update-manager-core n'est pas encore configuré.
dpkg*: erreur de traitement de update-manager (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de ubuntu-desktop*:
 ubuntu-desktop dépend de language-selector-gnome*; cependant*:
 Le paquet language-selector-gnome n'est pas encore configuré.No apport report written because MaxReports is reached already

 ubuntu-desktop dépend de software-center*; cependant*:
 Le paquet software-center n'est pas encore configuré.
 ubuntu-desktop dépend de software-properties-gtk*; cependant*:
 Le paquet software-properties-gtk n'est pas encore configuré.
 ubuntu-desktop dépend de update-manager*; cependant*:
 Le paquet update-manager n'est pas encore configuré.
dpkg*: erreur de traitement de ubuntu-desktop (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de lsb-core*:No apport report written because MaxReports is reached already

 lsb-core dépend de lsb-release*; cependant*:
 Le paquet lsb-release n'est pas encore configuré.
dpkg*: erreur de traitement de lsb-core (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de lsb-graphics*:No apport report written because MaxReports is reached already

 lsb-graphics dépend de lsb-core*; cependant*:
 Le paquet lsb-core n'est pas encore configuré.
dpkg*: erreur de traitement de lsb-graphics (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de lsb-cxx*:
 lsb-cxx dépend de lsb-core*; cependant*:
 Le paquet lsb-core n'est pas encore configuré.No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already

dpkg*: erreur de traitement de lsb-cxx (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de lsb-desktop*:
 lsb-desktop dépend de lsb-graphics*; cependant*:
 Le paquet lsb-graphics n'est pas encore configuré.
dpkg*: erreur de traitement de lsb-desktop (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de lsb-printing*:No apport report written because MaxReports is reached already

 lsb-printing dépend de lsb-core (>= 4.0)*; cependant*:
 Le paquet lsb-core n'est pas encore configuré.
dpkg*: erreur de traitement de lsb-printing (--configure)*:
 problèmes de dépendances - laissé non configuré
dpkg*: des problèmes de dépendances empêchent la configuration de lsb*:No apport report written because MaxReports is reached already

 lsb dépend de lsb-core*; cependant*:
 Le paquet lsb-core n'est pas encore configuré.
 lsb dépend de lsb-graphics*; cependant*:
 Le paquet lsb-graphics n'est pas encore configuré.
 lsb dépend de lsb-cxx*; cependant*:
 Le paquet lsb-cxx n'est pas encore configuré.
 lsb dépend de lsb-desktop*; cependant*:
 Le paquet lsb-desktop n'est pas encore configuré.
 lsb dépend de lsb-printing*; cependant*:
 Le paquet lsb-printing n'est pas encore configuré.
dpkg*: erreur de traitement de lsb (--configure)*:
 problèmes de dépendances - laissé non configuré
No apport report written because MaxReports is reached already
                                                              Des erreurs ont été rencontrées pendant l'exécution*:
[COLOR="MediumTurquoise"]the 20 packages[/COLOR]
 lsb-release
 ubuntu-minimal
 update-manager-core
 python-software-properties
 python-aptdaemon
 aptdaemon
 python-aptdaemon.gtk3widgets
 language-selector-gnome
 python-aptdaemon.gtkwidgets
 python-aptdaemon-gtk
 software-center
 software-properties-gtk
 update-manager
 ubuntu-desktop
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb-desktop
 lsb-printing
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)
moi@Portable:~$ 

```

---

### Post by cariboo on 2011-08-18
I'd suggest you install aptitude, and use:

```
aptitude safe-upgrade
```

as doing a partial upgrade is going to lead to problems.

If you aren't using the Main repository to do your updates, I suggest you do.

---

### Post by maximiliengolum on 2011-08-19
Hello cariboo907,
I have the same error message with aptitude...

---

### Post by maximiliengolum on 2011-08-20
I've thinked about the soluce of drs305, it worked for the pre-install, but the post-install for lsb-release was not solved, so i've used this command line:
```
sudo mv /var/lib/dpkg/info/lsb-release.postinst /var/lib/dpkg/info/lsb-release.postinst.bad
sudo mv /var/lib/dpkg/info/lsb-release.postrm /var/lib/dpkg/info/lsb-release.postrm.bad
sudo apt-get install --reinstall lsb-release
```

And that worked \o/

problem solve ^^ thank you all

---

