---
title: "3 operating systems ?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-11
i couldnt make up my mind wich distro of ubuntu i liked so i decided to use ubuntu and kubuntu.heres the problem i have winblows on my first hd as well as ubuntu,and i have kubuntu installed on a usb drive.now all is well when the usb drive is plugged in,but when unplugged i get error21 the obvious answer is to redo the grub entry (hd0)but i checked out the grub menu list on ubuntu and kubuntu isnt there.just ubuntu and winblows.(i keep windows just for my palm)anyway i checked the grub menu list in kubuntu,and all3 are listed??how did that happen/i thought when you saved to the mbr,it was written there.ive already been through the whole usb hd routine a couple times.but i didnt have windows to confuse the mix.is it possible to copy the entry from the kubuntu grub menu,and copy it to the ubuntu menu?
or is there something else i can do?
rick

---

### Post by adult swim on 2008-08-11
easy fix, forget about your usb drive.
boot into ubuntu, open a terminal and run ```
sudo apt-get install kubuntu-desktop
```log out and whenever you are at the login screen, from the opotions menu select sessions and then select kde.  that will launch kubuntu.

---

### Post by tarps87 on 2008-08-11
The grub will be in /boot/grub/menu.lst so it should be possible to copy the sections you need.  You will have to make sure the hard drives are correct but you can use fdisk -l to work this out.
I hope this helps

---

### Post by rizitis on 2008-08-11
You can do it from synaptic package manager.
Just check  "kubuntu-desktop" and apply...

---

### Post by rixtr66 on 2008-08-11
what about the menu list in kubuntu?will the list in ubuntu override it without hassels?the reason i have two ubuntu installs is i use one without compiz for 3d graphics and 2d graphics,and the other i use all the wizbang effects of compiz and some office apps and browsing.
rick

---

### Post by tarps87 on 2008-08-11
If your bios is set to boot from usb first, your kubuntu grub will be used when your usb is connected, when it is not attached it should be using the ubuntu grub.  If you add kubuntu to the ubuntu list it will probably load  the kubuntu grub when you select kubuntu. I am not at my pc at the moment so I can not test this. From how it sounds a solution would be to set the ubuntu grub so it has all three os and change you kubuntu grub so it only lists itself.  Before trying to edit the list make a backup and only do one at a time, that way if it goes wrong you can copy the old one back and try again

---

### Post by sandysandy on 2008-08-11
have a look at this thread on how to reinstall GRUB

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)


other thread on how to install standalone GRUB

[http://ubuntuforums.org/showthread.php?t=880798](http://ubuntuforums.org/showthread.php?t=880798)

regards

---

### Post by rixtr66 on 2008-08-11
ok i copied the kubuntu grub menu to the end of the ubuntu grub menu list,i also added #this entry automatically added by the debian installer for an existing#linux installation on /dev/sdb1,i thought that might be important.
i ran into a little trouble changing the grub to root,im used to installing the mbr to (hd0,0) or (hd0) i kinda forgot about the windows installation.
but i recovered and added the mbr to (hd0,4)-(hd0)the only thing i havnt done is change the grub menu in kubuntu,should i?everything works and boots like it is supposed to.except on restarts i get an error21 when choosing kubuntu from the boot menu.so far so good thanks for the info!
rick

---

### Post by tarps87 on 2008-08-11
> **rixtr66 said:**
> 
the only thing i havnt done is change the grub menu in kubuntu,should i?


As long as kubuntu boots ok I would worry about changing it.  If you decide to change it later you will only need the kubuntu section in, in the grub # is just a comment.  I'll have a look for the error21 problem and let you know if i find anything

---

### Post by LowSky on 2008-08-11
if you want to control compiz effects, install the compiz-fusion tray icon.

```
sudo apt-get install fusion-icon
```

(in Gnome sorry I don't know KDE) go to system> preferences >sessions and add the program to start up

use the command ```
fusion-icon --no-start
```

That way it will load the desktop effects that you used.

---

### Post by t0p on 2008-08-11
> **rixtr66 said:**
> ok i copied the kubuntu grub menu to the end of the ubuntu grub menu list,i also added #this entry automatically added by the debian installer for an existing#linux installation on /dev/sdb1,i thought that might be important.

Any line beginning with # is a **comment** and will be ignored by ubuntu.

---

### Post by tarps87 on 2008-08-11
Error 21 means "Can not find disk" so it is possible its just the way the bios loads the usb on a reboot.
This may fix it:
```

grub-install /dev/sda (sda is probaly the usb but you can use fdisk -l to check)
```
This should repair the grub on the usb.
(It maybe a bios problem not a grub one though)

---

