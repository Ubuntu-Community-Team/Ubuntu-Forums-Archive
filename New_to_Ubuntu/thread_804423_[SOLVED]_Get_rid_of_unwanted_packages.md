---
title: "[SOLVED] Get rid of unwanted packages?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by Dani Filth on 2008-05-23
Hi folks,

According to [this thread](http://ubuntuforums.org/showthread.php?p=5023773#post5023773), I gave it a try to install smb4k, but that brought together a lot of extra packages like :
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
[b]The following extra packages will be installed:
  cryptsetup dmsetup kcontrol kdebase-bin kdebase-bin-kde3 kdebase-data
  kdebase-kio-plugins kdesktop kfind kicker konqueror konqueror-nsplugins
  libdbus-qt-1-1c2 libkonq4
Suggested packages:
  khelpcenter mtools kicker-applets menu gij-4.1 konq-plugins ksvg libgcj7-awt
  libjessie-java
Recommended packages:
  kamera kdemultimedia-kio-plugins
The following NEW packages will be installed:
  cryptsetup dmsetup kcontrol kdebase-bin kdebase-bin-kde3 kdebase-data
  kdebase-kio-plugins kdesktop kfind kicker konqueror konqueror-nsplugins
  libdbus-qt-1-1c2 libkonq4 smb4k[/b]
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.2MB of archives.
After this operation, 55.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y


But after a short while, I found out that smb4k is not convenient to remotely access Windows shares, so that I decided to get rid of it.
However, I typed "sudo apt-get remove smb4k" in the terminal which only gave me the result :
> Building dependency tree       
Reading state information... Done
[b]The following packages will be REMOVED:
  smb4k[/b]
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4088kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 126498 files and directories currently installed.)
Removing smb4k ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

I even tried autoremove & autoclean but they didn't seem to find those unwanted packages and couldn't remove them.
> 
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


> 
sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done


So, is there a way to get rid of them automatically like the way they were installed in my PC, or I have no choice but to "sudo apt-get remove packagename" manually?

---

### Post by iaculallad on 2008-05-23
You can use the Add/Remove option of Ubuntu. This will automatically include files related with the applications you want to be removed.

Applications->Add/Remove

---

### Post by Dani Filth on 2008-05-23
Hi iaculallad,

That didn't remove all the extra packages, for instance, I now still have Konqueror in Applications/Internet/Konqueror. Plus, it also added in a sub-menu "Other" in Applications with so many unnecessary(I think) stuffs that I want to get rid of.

An odd thing is, if I search for "Konqueror" in Add/Remove in Applications, "Konqueror" is unchecked, but it's still there in my menu :confused:

---

### Post by Trebaruna on 2008-05-23
Have you tried looking at Synaptic? If you sort packages by status it will seperately list packages that aren't used by anything else anymore.
Also, if you're confident those packages aren't needed anymore just copy paste them all, like so:

```

sudo apt-get purge cryptsetup dmsetup kcontrol kdebase-bin kdebase-bin-kde3 kdebase-data
kdebase-kio-plugins kdesktop kfind kicker konqueror konqueror-nsplugins
libdbus-qt-1-1c2 libkonq4 smb4k

```

The purge option tells apt-get to also remove configuration files and the likes. If you don't want that, replace purge with remove.

EDIT: Ah, duh. It installed Konqueror, which is an application by itself. It will not be listed for autoclean because you can use it. Still, if you don't need it you can get rid of it all the same. Just make sure the above command doesn't drag other packages with it.

---

### Post by Dani Filth on 2008-05-23
Thanks Trebaruna, it works well :popcorn:

---

### Post by saj0577 on 2008-05-23
In the future use
```
sudo aptitude install {package name}
```
Example

```
sudo aptitude install smb4k
```

To Remove
```
sudo aptitude remove smb4k
```

Saj

---

