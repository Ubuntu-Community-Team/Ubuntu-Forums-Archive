---
title: "Installation error on updates.."
date: 2012-04-14
forum: New to Ubuntu
---

### Post by JDM_SOHC on 2012-04-14
I'm trying to install these updates that have been downloaded already in package manager but i keep getting thing error..


Failed to download package files. Check your internet connection. 
Failed to fetch cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/pool/main/p/patch/patch_2.6.1-3_amd64.deb File not found
Failed to fetch cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/pool/main/d/dkms/dkms_2.2.0.3-1ubuntu1_all.deb File not found
Failed to fetch cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu5_amd64.deb File not found
Failed to fetch cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/pool/main/f/fakeroot/fakeroot_1.18.2-1_amd64.deb File not found
Failed to fetch cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/pool/main/u/user-setup/user-setup_1.41ubuntu1_all.deb File not found
Failed to fetch cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120328)]/pool/main/l/lupin/lupin-support_0.51_amd64.deb File not found


I'm on Ubuntu 11.10 and I'm trying to upgrade to 12.04... And my internet is fine.

---

### Post by theknightlinux on 2012-04-14
Lets see if this works. Open up a terminal by pressing ctrl-alt-t at the same time, and just type the following: sudo apt-get install

---

### Post by JDM_SOHC on 2012-04-14
> **theknightlinux said:**
> Lets see if this works. Open up a terminal by pressing ctrl-alt-t at the same time, and just type the following: sudo apt-get install

said this
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

---

### Post by theknightlinux on 2012-04-14
Type sudo apt-get update

...oh and then again sudo-apt get install.

---

### Post by JDM_SOHC on 2012-04-14
> **theknightlinux said:**
> Type sudo apt-get update

...oh and then again sudo-apt get install.

lol, now it says..

0 upgraded, 0 newly installed, 0 to remove and 207 not upgraded.
shane@ubuntu:~$

---

### Post by RJARRRPCGP on 2012-04-14
You need to go to the repository settings menu and uncheck everything for the optical drive.

---

### Post by JDM_SOHC on 2012-04-14
> **RJARRRPCGP said:**
> You need to go to the repository settings menu and uncheck everything for the optical drive.

How do I find those settings..?? I'm used to pre-unity type interface where everything was @ the top now with this sidebar i'm a bit more inclined to learning the new way around...

---

### Post by theknightlinux on 2012-04-14
Top right corner- system settings- software sources.

---

### Post by theknightlinux on 2012-04-14
[LEFT][COLOR=#333333][FONT=Ubuntu]Try this on your own risk :p. On a terminal type:

echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf

sudo apt-get update

sudo apt-get upgrade
[/FONT][/COLOR][/LEFT]

---

### Post by theknightlinux on 2012-04-14
If it gets you out of the web just try to enable your network again.

---

### Post by theknightlinux on 2012-04-16
How did it go?

---

