---
title: "Can't add/remove applications"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by frasermorrison on 2008-08-15
Newbie in need of help!

I can't add ANY packages on Add/Remove Applications because it says "The list of applications is not available". So I press reload. It reloads. I click on one of the boxes again, and it comes up with that message again.

I understand that changing "Preferences" to download from Internet solves the problem in most occasions ([http://ubuntuforums.org/showthread.php?t=579701](http://ubuntuforums.org/showthread.php?t=579701)) but the problem i am having is Preferences not opening. This also does this when trying to open System Sources. It comes up with the enter Password box but once i have entered my password nothing else happens.

Any form of help whatsoever would be much appreciated...

---

### Post by iaculallad on 2008-08-15
> **frasermorrison said:**
> Newbie in need of help!

I can't add ANY packages on Add/Remove Applications because it says "The list of applications is not available". So I press reload. It reloads. I click on one of the boxes again, and it comes up with that message again.

I understand that changing "Preferences" to download from Internet solves the problem in most occasions ([http://ubuntuforums.org/showthread.php?t=579701](http://ubuntuforums.org/showthread.php?t=579701)) but the problem i am having is Preferences not opening. This also does this when trying to open System Sources. It comes up with the enter Password box but once i have entered my password nothing else happens.

Any form of help whatsoever would be much appreciated...

Post whatever displays when you issue the following command in your terminal:

```
cat /etc/hosts
```

---

### Post by frasermorrison on 2008-08-15
127.0.0.1 localhost
127.0.1.1 fraser-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by LowSky on 2008-08-15
open a termial and type the following commands
programs > accessories > terminal

sudo apt-get update
 sudo apt-get upgrade

---

### Post by iaculallad on 2008-08-15
> **frasermorrison said:**
> 127.0.0.1 localhost
127.0.1.1 fraser-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Could you include your terminal prompt:

i.e:

```
ian@gutsy-gibbon:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 gutsy-gibbon

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
ian@gutsy-gibbon:~$ 

```

---

### Post by frasermorrison on 2008-08-15
Ah, sorry about that

fraser@fraser-desktop:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 fraser-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
fraser@fraser-desktop:~$

---

### Post by frasermorrison on 2008-08-15
> **LowSky said:**
> open a termial and type the following commands
programs > accessories > terminal

sudo apt-get update
 sudo apt-get upgrade

Won't let me type in my password

---

### Post by iaculallad on 2008-08-15
That's normal with Ubuntu, it does not echo your password on your terminal. Just input your password and press Enter.

---

### Post by frasermorrison on 2008-08-15
OK i now have this, all well?...

fraser@fraser-desktop:~$ sudo apt-get update
[sudo] password for fraser: 
Ign cdrom://Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2) hardy/main Translation-en_GB
Ign cdrom://Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2) hardy/restricted Translation-en_GB
Reading package lists... Done
fraser@fraser-desktop:~$

---

### Post by iaculallad on 2008-08-15
> **frasermorrison said:**
> OK i now have this, all well?...

fraser@fraser-desktop:~$ sudo apt-get update
[sudo] password for fraser: 
Ign cdrom://Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2) hardy/main Translation-en_GB
Ign cdrom://Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2) hardy/restricted Translation-en_GB
Reading package lists... Done
fraser@fraser-desktop:~$

All well.. Try:

```
sudo apt-get upgrade
```

---

### Post by frasermorrison on 2008-08-15
fraser@fraser-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  apt apt-utils aptitude initscripts libaspell15 libgnomecanvas2-0
  libgnomevfs2-0 libgnomevfs2-common libgtk2.0-0 libgtk2.0-common python-apt
  update-manager-core xbase-clients
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
fraser@fraser-desktop:~$

---

### Post by iaculallad on 2008-08-15
> **frasermorrison said:**
> fraser@fraser-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  apt apt-utils aptitude initscripts libaspell15 libgnomecanvas2-0
  libgnomevfs2-0 libgnomevfs2-common libgtk2.0-0 libgtk2.0-common python-apt
  update-manager-core xbase-clients
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
fraser@fraser-desktop:~$

You're good to go..

---

### Post by frasermorrison on 2008-08-15
Great, thank you very much for your help kind sir. Much appreciated :)

---

### Post by iaculallad on 2008-08-15
> **frasermorrison said:**
> Great, thank you very much for your help kind sir. Much appreciated :)

You're welcome. Feel free to always come back in the forum if you have problems/questions, there are too many helping hands are available in the forum to help you.

---

