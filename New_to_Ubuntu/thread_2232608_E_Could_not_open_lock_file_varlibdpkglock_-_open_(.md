---
title: "E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)"
date: 2014-07-03
forum: New to Ubuntu
---

### Post by kasparlai123 on 2014-07-03
First i aborted a crashed wine install, after that i have these errors 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

, then i removed the /var/lib/dpkg/lock file and restarted, after that i tryed to install wifi driver for my laptop, but it said Segmentation error. Well, then i tryed everything written on forums i found and i ended up with this : [http://paste.ubuntu.com/7740710/](http://paste.ubuntu.com/7740710/) sorry for some estonian, but i think you understand the most important things.

---

### Post by nerdtron on 2014-07-03
It should be " sudo apt-get -f install".

---

### Post by kasparlai123 on 2014-07-04
I tryed it, but got those errors: [http://paste.ubuntu.com/7745705/](http://paste.ubuntu.com/7745705/)...

---

### Post by kasparlai123 on 2014-07-04
I tryed to get that package, and i get this error if i want to install any package:
dominik@Dominiku:~$ sudo apt-get install debconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done


You might want to run 'apt-get -f install' to correct these:
Järgmistel pakettidel on lahendamata sõltuvusi:
bcmwl-kernel-source : Depends: dkms aga seda ei paigaldata
Depends: linux-libc-dev aga seda ei paigaldata
Depends: libc6-dev aga seda ei paigaldata
debconf : PreDepends: perl-base (>= 5.6.1-4) aga seda ei paigaldata
Recommends: apt-utils (>= 0.5.1) aga seda ei paigaldata
Recommends: debconf-i18n aga seda ei paigaldata
E: Lahendamata sõltuvused. Proovi käsku 'apt-get -f install' ilma pakettideta (või määra lahendus).
dominik@Dominiku:~$

---

### Post by nerdtron on 2014-07-04
Have you tried updating first?

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install

---

