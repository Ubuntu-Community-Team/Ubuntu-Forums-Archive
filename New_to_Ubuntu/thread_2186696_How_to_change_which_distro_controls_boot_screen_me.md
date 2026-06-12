---
title: "How to change which distro controls boot screen menu"
date: 2013-11-08
forum: New to Ubuntu
---

### Post by egeezer on 2013-11-08
On a multiboot installation, how can I change which of the installed distros controlls the entries on the boot screen menu?  The problem I have is that I removed some old kernels from a frequently-used, continuously updated Xubuntu 12.04 distro a while ago.  After some distro-hopping on other partitions, I now find the boot screen menu is out of date with the existing kernels.  

I remember several Ubuntus ago there was even a GUI choice of which distro would have control of the boot screen.  Now I can't seem to find any specific advice on this.

TIA for any helpful replies!

---

### Post by deadflowr on 2013-11-08
I'd boot into the Xubuntu 12.04 distro, since that's the one you use the most (it seems) and run
```
sudo grub-install /dev/sda
```
of course this is if the disk is /dev/sda
It should state No errors reported.
then run 
```
sudo update-grub
```
Which will clean the listings up.

Typically though, the top entry is the one in charge of the booting.
You can normally just boot into that one and run the second command.
If anything goes wrong, look at this
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by egeezer on 2013-11-08
Good grief, what a fast answer!  And a flawless one at that - it worked perfectly!  And since I will probably continue distro-hopping, I thank you in advance for all the times your advice will probably save me in the future!

---

