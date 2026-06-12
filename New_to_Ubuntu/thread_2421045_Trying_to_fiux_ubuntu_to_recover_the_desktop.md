---
title: "Trying to fiux ubuntu to recover the desktop"
date: 2019-06-15
forum: New to Ubuntu
---

### Post by regor02 on 2019-06-15
Hi,

I am trying to update ubuntu mate on my raspi , since I add problem with my desktop that disapeared. 
I was working on the xstart to get a vnc server starting on boot of the raspi. 
I think i made a mistake , then i lost access to raspi. 
I have find way to connect using the cntrl-alt-F1 on the black screen with a flashing point 

I am able to connect through Putty from my computer.
Bellow is what i have when i try to update.

could you help me


[HTML]Welcome to Ubuntu 16.04.6 LTS (GNU/Linux 4.4.38-v7+ armv7l)
 * Documentation:  https://help.ubuntu.com * Management:     https://landscape.canonical.com * Support:        https://ubuntu.com/advantage
0 paquet peut être mis à jour.0 mise à jour de sécurité.
Last login: Mon Jun 10 19:20:11 2019roger@roger-desktop:~$ sudo apt-get install update-manager-core[sudo] password for roger:Lecture des listes de paquets... FaitConstruction de l'arbre des dépendancesLecture des informations d'état... Faitupdate-manager-core est déjà la version la plus récente (1:16.04.15).update-manager-core passé en « installé manuellement ».0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.roger@roger-desktop:~$ sudo apt-get updateErr :1 http://ppa.launchpad.net/ubuntu-mate-dev/welcome/ubuntu xenial InRelease  Ne parvient pas à résoudre « ppa.launchpad.net »Err :2 http://ppa.launchpad.net/ubuntu-mate-dev/xenial-mate/ubuntu xenial InRelease  Ne parvient pas à résoudre « ppa.launchpad.net »Err :3 http://ppa.launchpad.net/ubuntu-pi-flavour-makers/ppa/ubuntu xenial InRelease  Ne parvient pas à résoudre « ppa.launchpad.net »Err :4 http://ports.ubuntu.com xenial InRelease  Ne parvient pas à résoudre « ports.ubuntu.com »Err :5 http://ports.ubuntu.com xenial-updates InRelease  Ne parvient pas à résoudre « ports.ubuntu.com »Err :6 http://ports.ubuntu.com xenial-security InRelease  Ne parvient pas à résoudre « ports.ubuntu.com »Err :7 http://ports.ubuntu.com xenial-backports InRelease  Ne parvient pas à résoudre « ports.ubuntu.com »Lecture des listes de paquets... FaitW: Impossible de récupérer http://ports.ubuntu.com/dists/xenial/InRelease  Ne parvient pas à résoudre « ports.ubuntu.com »W: Impossible de récupérer http://ports.ubuntu.com/dists/xenial-updates/InRelease  Ne parvient pas à résoudre « ports.ubuntu.com »W: Impossible de récupérer http://ports.ubuntu.com/dists/xenial-security/InRelease  Ne parvient pas à résoudre « ports.ubuntu.com »W: Impossible de récupérer http://ports.ubuntu.com/dists/xenial-backports/InRelease  Ne parvient pas à résoudre « ports.ubuntu.com »W: Impossible de récupérer http://ppa.launchpad.net/ubuntu-mate-dev/welcome/ubuntu/dists/xenial/InRelease  Ne parvient pas à résoudre « ppa.launchpad.net »W: Impossible de récupérer http://ppa.launchpad.net/ubuntu-mate-dev/xenial-mate/ubuntu/dists/xenial/InRelease  Ne parvient pas à résoudre « ppa.launchpad.net »W: Impossible de récupérer http://ppa.launchpad.net/ubuntu-pi-flavour-makers/ppa/ubuntu/dists/xenial/InRelease  Ne parvient pas à résoudre « ppa.launchpad.net »W: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.[/HTML]

---

