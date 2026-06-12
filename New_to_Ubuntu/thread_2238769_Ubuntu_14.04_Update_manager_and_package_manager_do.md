---
title: "Ubuntu 14.04 Update manager and package manager doesn't open anymore"
date: 2014-08-09
forum: New to Ubuntu
---

### Post by tatianeps2 on 2014-08-09
There is this red icon near the battery status icon, clock and other icons. It only reads:
- An error ocurred checking updates.
- Show updates
- Show notifications
- Preferences

[ATTACH=CONFIG]255362[/ATTACH]

Nothing happens at all when I click any red icon's options.

And going into Settings > Software&Update manager nothing happens. Nothing at all. O.o

It's gone far beyond my (limited) skills to fix things on Ubuntu.

Please help. :confused:

I've already tried:
```
sudo apt-get update
sudo apt-get upgrade
```

After the upgrade, it only says that there's nothing to update, nothing new to install, nothing to remove and nothing not updated:
```
$ sudo apt-get upgrade 
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
Calculando atualização... Pronto
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
```

I've already tried:
```
sudo rm /var/lib/apt/lists/* -vf
```
Then:
```
sudo apt-get update
```

Nothing happened. No error. But the red icon is still there.

This is my sources list:
```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://br.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://br.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://br.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://br.archive.ubuntu.com/ubuntu/ trusty universe
deb http://br.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://br.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://br.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://br.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://br.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
#deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
```

sources.list.d is empty
```
$ ls /etc/apt/sources.list.d
```

And this is /var/lib/apt/lists
```
$ ls /var/lib/apt/lists/
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_binary-amd64_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_binary-i386_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_i18n_Translation-en
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_main_source_Sources
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-amd64_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-i386_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_i18n_Translation-en
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_source_Sources
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_Release
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_Release.gpg
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-amd64_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_binary-i386_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_i18n_Translation-en
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_restricted_source_Sources
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_binary-amd64_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_binary-i386_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_i18n_Translation-en
br.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_source_Sources
br.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en
br.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-pt
br.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-pt%5fBR
br.archive.ubuntu.com_ubuntu_dists_trusty_main_source_Sources
br.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-amd64_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-i386_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-en
br.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-pt
br.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_i18n_Translation-pt%5fBR
br.archive.ubuntu.com_ubuntu_dists_trusty_multiverse_source_Sources
br.archive.ubuntu.com_ubuntu_dists_trusty_Release
br.archive.ubuntu.com_ubuntu_dists_trusty_Release.gpg
br.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-amd64_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty_restricted_binary-i386_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty_restricted_i18n_Translation-en
br.archive.ubuntu.com_ubuntu_dists_trusty_restricted_i18n_Translation-pt
br.archive.ubuntu.com_ubuntu_dists_trusty_restricted_i18n_Translation-pt%5fBR
br.archive.ubuntu.com_ubuntu_dists_trusty_restricted_source_Sources
br.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-amd64_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty_universe_binary-i386_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-en
br.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-pt
br.archive.ubuntu.com_ubuntu_dists_trusty_universe_i18n_Translation-pt%5fBR
br.archive.ubuntu.com_ubuntu_dists_trusty_universe_source_Sources
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-amd64_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_binary-i386_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_i18n_Translation-en
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_main_source_Sources
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_binary-amd64_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_binary-i386_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_i18n_Translation-en
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_source_Sources
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_Release
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_Release.gpg
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-amd64_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_binary-i386_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_i18n_Translation-en
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_restricted_source_Sources
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_binary-amd64_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_binary-i386_Packages
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_i18n_Translation-en
br.archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_source_Sources
extras.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages
extras.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages
extras.ubuntu.com_ubuntu_dists_trusty_main_source_Sources
extras.ubuntu.com_ubuntu_dists_trusty_Release
extras.ubuntu.com_ubuntu_dists_trusty_Release.gpg
lock
partial
security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_main_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_trusty-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_source_Sources
security.ubuntu.com_ubuntu_dists_trusty-security_Release
security.ubuntu.com_ubuntu_dists_trusty-security_Release.gpg
security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_restricted_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_trusty-security_restricted_source_Sources
security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-amd64_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_trusty-security_universe_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_trusty-security_universe_source_Sources
```

---

### Post by Bashing-om on 2014-08-09
tatianeps2; Hello;

You have some some homework.
What is needed now is some additional info. What results from terminal commands:
```

sudo apt-get -f install 
sudo dpkg -C
sudo dpkg --audit

```
Maybe will yield some hints as to the nature of the problem.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by tatianeps2 on 2014-08-09
Everything here:

```
$ sudo apt-get -f install
[sudo] password for <user>: 
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
```

```
$ sudo dpkg -C
Aos seguintes pacotes falta o ficheiro de controlo md5sum na base de dados,
necessitam ser reinstalados:
 libjson0:amd64       JSON manipulation library (transitional package)
 libjson0:i386        JSON manipulation library (transitional package)
```


```
$ sudo dpkg --audit
Aos seguintes pacotes falta o ficheiro de controlo md5sum na base de dados,
necessitam ser reinstalados:
 libjson0:amd64       JSON manipulation library (transitional package)
 libjson0:i386        JSON manipulation library (transitional package)
```

Beyond the info you asked for, there is something else: in the last few automatic updates there were some "transitional dummy packages" (image attached) that I didn't install (unchecked them) because their names are meaningless. My rule of thumb is: if I don't know what something is, I don't install it.

Edit: this image of automatic update I already had saved before the problem reported here started.

---

### Post by tatianeps2 on 2014-08-10
After:
```
$ sudo apt-get --reinstall install libjson0
```

The commands below did not throw any error.
```
$ debsums -l
$ sudo dpkg -C
$ sudo dpkg --audit
```

But the problem is not solved yet. The red icon is still there and Software &Update Manager doesn't open.

---

### Post by Bashing-om on 2014-08-10
tatianeps2; Well, well,

Time to do some more homework;
Take a look with terminal commands:
```

apt-cache show libjson0
apt-cache depends libjson0

``` as only one instance of what is required.
My conclusion is that they are required as advised:
> 
sysop@1404mini:~$ apt-cache show libjson0
Package: libjson0
Priority: [color=red]required[/color]

Following the tree for one package ( of many);
```

dpkg -l libjson-c2

```
Now see if your conclusion is not to install what the package manager recommends.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by tatianeps2 on 2014-08-10
Do you mean that hidden under that weird name, "transitional dummy package", there was something actually very important for the system? WOW!

Edit:
Before I come back to the forum to check you previous reply, Bashing-om, I was really freaking out. So I did something that is not the smartest thing, but is  the answer for almost all Ubuntu issues: I reinstalled it. 

When I upgraded from 12.04 to 14.04 on June 28 (or 29, not sure) with **sudo update-manager -d** there were a few weird things, but it didn't keep the update to go through and the system to work. These weird things might relate to the problem posted here, plus the thing with "transitional dummy packages".

I'm a "backup freak" LOL and my /home directory is in a separate partition. So, since this time the install was with the same version of Ubuntu as the last one, 14.04.01, everything is running smooth after the install.

I do appreciate your time and effort to help me, Bashing-om. And I did learn a few things: some dpkg options to check whats going with the system and that I should not unckeck stuff on Update Manager (but I hope they don't come with meaningless names anymore). Tks! =D

Edit [2]:
Just adding one more thought. There was another machine with the same red icon thing and more options on right-click menu. On that one everything worked out, because the Update Manager was working, then Ubuntu kinda fixed itself.

---

### Post by Bashing-om on 2014-08-10
tatianeps2; Yeah;

That is the shinning thing about our operating system of choice - we have the option/ability to (RE-)install. With good backups and a good internet connection, back up in 20 minutes and nothing is lost. 
But, always keep this in mind, when that nuclear solution is applied, little is learned.

Package management; Can you imagine what managing this operating system was like before the development of "dpkg" ? There is strong reason that the system of package management exists, and with in that system are a great many checks and balances to insure the integrity and validity of the system. I fully now trust it !
There are means to see/check the condition of the package manager, and ask it if it needs a bit of help. An in the event of needed assistance to the package manager there are the means to help. - It is all in knowing how.

However, I do agree that there is no feeling of security such as in a nice fresh clean install ... Start all over with a clean slate.


In my world, system administration begins with package management. For your continued education may I offer my 1st package management resource:
[https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites](https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites)

correct our errors in judgement and
[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

