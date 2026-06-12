---
title: "[SOLVED] apt-get upgrade kept back - why ?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by WitchCraft on 2008-07-06
when i run apt-get upgrade i get:
> 
apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  consolekit f-spot gnome-applets gnome-panel grub gvfs gvfs-backends hpijs
  hplip initramfs-tools language-support-writing-en linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
  ssl-cert totem totem-gstreamer totem-mozilla totem-plugins udev xserver-xorg
  xserver-xorg-video-all xserver-xorg-video-amd
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.


Now a few questions: 
1. Why are packages hold back?
2. How to un-holdback them?
3. Is 2. safe?

---

### Post by cariboo on 2008-07-06
The packages are held back because there are dependencies that are not being met, usually there is a library that is to old. Just give it a day or three and new files will come through that meet the dependencies, and then they will be installed.

Jim

---

### Post by gettinoriginal on 2008-07-06
I am also a noowbie, but you might try "sudo apt-get", they may need root permission and password to complete.

---

### Post by tjwoosta on 2008-07-06
first do

sudo apt-get update

then do

sudo apt-get upgrade

(sudo is the key)

---

### Post by pluckypigeon on 2008-07-06
```
sudo apt-get dist-upgrade
```

That should be what you need

Edit: I Assume it is holding them back because it wants to install dependencies as well as upgrades. If this is the case and the dependencies are official then it should be safe.

---

### Post by tamoneya on 2008-07-06
> **WitchCraft said:**
> when i run apt-get upgrade i get:


Now a few questions: 
1. Why are packages hold back?
2. How to un-holdback them?
3. Is 2. safe?

often it means that to update some of your packages it is required for you to remove old ones or add new ones.  This is not done during a normal upgrade.  The dist-upgrade mentioned by the previous user will "un-holdback" the packages.

---

### Post by Bubba64 on 2008-07-07
I have had the same thing happen when 3rd party repositories are open or closed in software sources I forget which. I think open, the Ubuntu source may not install while the 3rd party repository is open, with a upgrade of a Ubuntu of the same basic package but different versions.

---

### Post by WitchCraft on 2008-07-07
> **tamoneya said:**
> often it means that to update some of your packages it is required for you to remove old ones or add new ones.  This is not done during a normal upgrade.  The dist-upgrade mentioned by the previous user will "un-holdback" the packages.

ah, ok, apt-get dist-upgrade solved it.

---

### Post by pluckypigeon on 2008-07-07
> **WitchCraft said:**
> ah, ok, apt-get dist-upgrade solved it.

Glad I could help:)

---

### Post by pluckypigeon on 2008-07-08
yep, sudo apt-get dist-upgrade

---

### Post by Saint Angeles on 2008-07-09
im having this problem with alien-arena...

```
steve@skynet:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  alien-arena
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

does this just mean i have to wait for [whatever the dependency is], is updated? like, if it requires a newer alien-arena-data (just an example) and that package isnt available yet, do i just wait or do i yell and scream at somebody?

---

### Post by philinux on 2008-07-09
> **Saint Angeles said:**
> im having this problem with alien-arena...

```
steve@skynet:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  alien-arena
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

does this just mean i have to wait for [whatever the dependency is], is updated? like, if it requires a newer alien-arena-data (just an example) and that package isnt available yet, do i just wait or do i yell and scream at somebody?

Just wait. It needs Alien-arena version 7. Version 6 is installed at the moment

---

### Post by pluckypigeon on 2008-07-09
> **Saint Angeles said:**
> im having this problem with alien-arena...

```
steve@skynet:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  alien-arena
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

does this just mean i have to wait for [whatever the dependency is], is updated? like, if it requires a newer alien-arena-data (just an example) and that package isnt available yet, do i just wait or do i yell and scream at somebody?

open up synaptic. click once on alien arena 7 and press "CTRL E" then, from the drop down menu select 6. This will make it look tidy until 7 comes out anyway:)

---

### Post by panosssvent19 on 2008-12-19
```
panos@panos-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

I have the same problem but with the restricted modules what i can do????
I have to wait???

---

### Post by WitchCraft on 2009-01-14
> **panosssvent19 said:**
> ```
panos@panos-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

I have the same problem but with the restricted modules what i can do????
I have to wait???

No you don't have to wait!
```

sudo apt-get dist-upgrade

```

---

