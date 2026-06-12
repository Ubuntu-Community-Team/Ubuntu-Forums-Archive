---
title: "Replace sysvinit with upstart (edgy)"
date: 2006-10-26
forum: Outdated Tutorials &amp; Tips
---

### Post by mattme on 2006-10-26
For those who don't know - Edgy includes upstart, a replacement for ye olde sysvinit, the boot sequence that takes your computer from the kernel unpack to Gnome.
([http://upstart.ubuntu.com/](http://upstart.ubuntu.com/))

sysvinit and upstart can't coexist on your system. Upstart is installed by default in Edgy if you install from CD, but if you've upgraded online, you'll still be using sysvinit.
- to test run
dpgk-query -s sysvinit / upstart

To replace sysvinit with upstart
sudo apt-get install upstart startup-tasks system-services upstart-compat-sysv upstart-logd
(this will demand to remove sysvinit)

If you're doing anything particular exotic at book, I wouldn't recommend this - "if it ain't broke, don't fix it".

---

### Post by McLoud on 2006-10-28
It seems the upgrade already install upstart:

```

mcloud@Sanctuary:~$ sudo apt-get install upstart startup-tasks system-services upstart-compat-sysv upstart-logd
Password:
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências       
Reading state information... Pronto 
upstart já é a versão mais nova.
startup-tasks já é a versão mais nova.
system-services já é a versão mais nova.
upstart-compat-sysv já é a versão mais nova.
upstart-logd já é a versão mais nova.
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.

```

---

### Post by keybuk on 2006-10-30
> **mattme said:**
> sysvinit and upstart can't coexist on your system. Upstart is installed by default in Edgy if you install from CD, but if you've upgraded online, you'll still be using sysvinit.

This is not entirely true ... provided you follow the upgrade procedure in the release notes, and provided you haven't uninstalled ubuntu-minimal at any point, you will have upstart automatically installed as part of the upgrade.

---

### Post by stalefries on 2006-10-30
So, we only need to do this if we've uninstalled ubuntu-minimal at some point?

---

### Post by codypumper on 2006-10-31
It wasn't installed on mine via upgrade, and I don't have ubuntu-minimal

---

### Post by clickwir on 2006-11-01
I just upgraded Kubuntu dapper to edgy the other day by modifying my /etc/apt/sources.lst file.

:~$ sudo apt-get -s install ubuntu-minimal
Reading package lists... Done
Building dependency tree
Reading state information... Done
ubuntu-minimal is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

:~$ sudo apt-get -s install upstart startup-tasks system-services upstart-compat-sysv upstart-logd
Reading package lists... Done
Building dependency tree
Reading state information... Done
upstart is already the newest version.
startup-tasks is already the newest version.
system-services is already the newest version.
upstart-compat-sysv is already the newest version.
upstart-logd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Says I already have upstart. Don't know how else to tell... but looks like it.

---

### Post by hype on 2006-11-02
Boot/shut down time are so much faster now with upstart.
Provided its not a really "old" project, its going to rock more and more !.

Good job Keybuk! (nice to see a leet core-dev here :D)

---

### Post by Mr Fat Bat on 2006-11-19
I did an upgrade from Dapper and it appears that i'm using upstart.

On another note, is there an upstart config guide somewhere?  I'd like to know how it works!

---

### Post by nilou on 2006-12-07
There is a README in /usr/share/doc/upstart/

---

