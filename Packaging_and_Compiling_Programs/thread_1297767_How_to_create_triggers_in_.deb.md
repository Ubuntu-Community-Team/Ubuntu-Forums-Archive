---
title: "How to create triggers in .deb ?"
date: 2009-10-22
forum: Packaging and Compiling Programs
---

### Post by benj.david on 2009-10-22
Hi all,
I'm currently packaging program in deb archives and I would like to activate triggers when other deb are installed.
Actually I would like to do the same as man-db or ufw do when ssh is installed : (sorry it's in French)
$ sudo aptitude install ssh
...
Les NOUVEAUX paquets suivants vont être installés*:
  openssh-server{a} ssh 
...
Préconfiguration des paquets...
Sélection du paquet openssh-server précédemment désélectionné.
(Lecture de la base de données... 234142 fichiers et répertoires déjà installés.)
Dépaquetage de openssh-server (à partir de .../openssh-server_1%3a5.1p1-5ubuntu1_i386.deb) ...
Sélection du paquet ssh précédemment désélectionné.
Dépaquetage de ssh (à partir de .../ssh_1%3a5.1p1-5ubuntu1_all.deb) ...
[B]Traitement des actions différées («*triggers*») pour « ufw »...
Traitement des actions différées («*triggers*») pour « man-db »...[/B]
Paramétrage de openssh-server (1:5.1p1-5ubuntu1) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
 * Restarting OpenBSD Secure Shell server sshd                                                                                                             [ OK ] 

Paramétrage de ssh (1:5.1p1-5ubuntu1) ...
...
$
(initramfs-tools does the same when is kernel or grub is installed)

The only clue I've found is in postinst script :
$ cat /var/lib/dpkg/info/man-db.postinst
#!/bin/sh -e
...
if [ "$1" = triggered ]; then
    # We don't print a status message here, as dpkg already said
    # "Processing triggers for man-db ...".
    run_mandb -pq
    exit 0
fi
...
but how this script is linked with the installation of SSH ??
(not found in any ssh/openssh scripts)

Many thanks for your help.
Ben

---

### Post by dinxter on 2009-10-23
hi there. as far as i know there are 2 main ways to activate triggers, though i'm no expert in this area :) 

1. Activate trigger when package installs
In this case the package being installed calls a trigger by adding the line 
activate <trigger name>
to  debian/triggers
Where the trigger name is one of those in /var/lib/dpkg/triggers. For example, package is a kernel, so it calls the trigger on update-initramfs when it installs

2.Trigger package on file change. 
This is what man-db and ufw you mention above do. Add the line
interest /path/to/some/file/to/watch/
to debian/triggers in your package. This adds the line
/path/to/some/fle/to/watch my-package-name
to /var/lib/dpkg/triggers/File
When the watched file or directory changes on installation of some other package, the trigger on your package is called. As you mention, the trigger calls your packages postinst script with the option "triggered", so you need to add something to your postinst script to deal with it and actually do something.

---

### Post by dinxter on 2009-10-23
Maybe the link below will be more help
[http://lists.debian.org/debian-dpkg/2007/04/msg00076.html](http://lists.debian.org/debian-dpkg/2007/04/msg00076.html)
as far as i know this is still accurate (!?)

---

### Post by benj.david on 2009-10-26
Hi all,
Thank you dinxter !! It works well !!

Regards,
ben

---

