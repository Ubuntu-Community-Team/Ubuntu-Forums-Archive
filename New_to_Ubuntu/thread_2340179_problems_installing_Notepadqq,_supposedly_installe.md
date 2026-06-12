---
title: "problems installing Notepadqq, supposedly installed"
date: 2016-10-16
forum: New to Ubuntu
---

### Post by 20GT on 2016-10-16
Ok I tried to install [Notepadqq]("http://notepadqq.altervista.org/wp/download/")

I did what it said but when I searched for Notepadqq It found nothing

```



steve@ubuntu16-4lts:~$ sudo add-apt-repository ppa:notepadqq-team/notepadqq
[sudo] password for steve: 
 Notepadqq text editor
 More info: https://launchpad.net/~notepadqq-team/+archive/ubuntu/notepadqq
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmp736hk5f2/secring.gpg' created
gpg: keyring `/tmp/tmp736hk5f2/pubring.gpg' created
gpg: requesting key 63DE9CD4 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp736hk5f2/trustdb.gpg: trustdb created
gpg: key 63DE9CD4: public key "Launchpad PPA for Notepadqq Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
steve@ubuntu16-4lts:~$ sudo apt-get update
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                     
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]    
Get:4 http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu xenial InRelease [17.5 kB]
Get:6 http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu xenial/main amd64 Packages [932 B]
Hit:7 https://apt.dockerproject.org/repo ubuntu-xenial InRelease               
Hit:8 http://us.archive.ubuntu.com/ubuntu xenial InRelease               
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]
Get:10 http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu xenial/main i386 Packages [932 B]
Get:11 http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu xenial/main Translation-en [424 B]
Hit:12 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease          
Fetched 210 kB in 2s (89.0 kB/s)
Reading package lists... Done
steve@ubuntu16-4lts:~$ sudo apt-get install notepadqq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-28 linux-headers-4.4.0-28-generic linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-headers-4.4.0-36
  linux-headers-4.4.0-36-generic linux-image-4.4.0-28-generic
  linux-image-4.4.0-31-generic linux-image-4.4.0-34-generic
  linux-image-4.4.0-36-generic linux-image-extra-4.4.0-28-generic
  linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-34-generic
  linux-image-extra-4.4.0-36-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  notepadqq-common
The following NEW packages will be installed:
  notepadqq notepadqq-common
0 upgraded, 2 newly installed, 0 to remove and 222 not upgraded.
Need to get 1,010 kB of archives.
After this operation, 5,495 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu xenial/main amd64 notepadqq-common all 0.53.0-0~xenial1 [749 kB]
Get:2 http://ppa.launchpad.net/notepadqq-team/notepadqq/ubuntu xenial/main amd64 notepadqq amd64 0.53.0-0~xenial1 [261 kB]
Fetched 1,010 kB in 6s (154 kB/s)                                              
Selecting previously unselected package notepadqq-common.
(Reading database ... 402291 files and directories currently installed.)
Preparing to unpack .../notepadqq-common_0.53.0-0~xenial1_all.deb ...
Unpacking notepadqq-common (0.53.0-0~xenial1) ...
Selecting previously unselected package notepadqq.
Preparing to unpack .../notepadqq_0.53.0-0~xenial1_amd64.deb ...
Unpacking notepadqq (0.53.0-0~xenial1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160523-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up notepadqq-common (0.53.0-0~xenial1) ...
Setting up notepadqq (0.53.0-0~xenial1) ...
update-alternatives: using /usr/lib/notepadqq/notepadqq.sh to provide /usr/bin/notepadqq (notepadqq) in auto mode
steve@ubuntu16-4lts:~$ 



```

---

### Post by Impavidus on 2016-10-16
It says it installed and it says it created /usr/bin/notepadqq. So you should be able to start notepadqq by using that command. I don't know that software, but if you want a laucher for it to make it appear in the menus, you may have to create a .desktop file for it yourself. That is a simple text file. You can pick one of the many .desktop files on your system as an example and create a new one for notepadqq.

On a separate note, you have 16 autoremovable packages and 222 upgrades waiting. I assume you automatically install security upgrades, but maybe it's time for some cleanup.

---

### Post by 20GT on 2016-10-16
thanks

---

### Post by 20GT on 2016-10-16
how do I do this "clean up"?

---

### Post by oldos2er on 2016-10-16
```

The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-28 linux-headers-4.4.0-28-generic linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-headers-4.4.0-36
  linux-headers-4.4.0-36-generic linux-image-4.4.0-28-generic
  linux-image-4.4.0-31-generic linux-image-4.4.0-34-generic
  linux-image-4.4.0-36-generic linux-image-extra-4.4.0-28-generic
  linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-34-generic
  linux-image-extra-4.4.0-36-generic
Use '[COLOR=#ff0000]sudo apt autoremove[/COLOR]' to remove them.
``` In order to get the 222 updates still pending, use ```
sudo apt update
sudo apt full-upgrade
```

---

### Post by 20GT on 2016-10-16
thanks I googled

```
[COLOR=#111111][FONT=Consolas]apt-get dist-upgrade[/FONT][/COLOR]
```

would 

```
apt-get dist-upgrade
```

be better?

---

### Post by 20GT on 2016-10-16
I had a previous drive go bad and lost my windows 8 is this update going to risk my ubuntu OS? At this moment its all I have

---

### Post by oldos2er on 2016-10-16
*apt-get dist-upgrade* is the old way. Both *apt-get dist-upgrade* and *apt full-upgrade* should do the same thing, it's just a little easier to type apt rather than apt-get.

Edit: Be careful when googling for Ubuntu information that it applies to the version you're running, and/or isn't out of date.

---

