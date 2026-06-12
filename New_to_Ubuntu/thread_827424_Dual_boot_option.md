---
title: "Dual boot option"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Robk0000 on 2008-06-12
I installed ubuntu last weekend and LOVE IT. Superfast and no loading, love it. Let me get to the point though, i have Vista installed on a 500 gb hdd, and Ubuntu on my 250 gb hdd. I installed ubuntu first and then vista, Now i understand you can install both on a single hdd, and partition it so that you have an option to dual boot from a screen upon boot up. How can i get to the dual boot option screen with my current setup?

Thanks.

---

### Post by powerpleb on 2008-06-12
> **Robk0000 said:**
> I installed ubuntu last weekend and LOVE IT. Superfast and no loading, love it. Let me get to the point though, i have Vista installed on a 500 gb hdd, and Ubuntu on my 250 gb hdd. I installed ubuntu first and then vista, Now i understand you can install both on a single hdd, and partition it so that you have an option to dual boot from a screen upon boot up. How can i get to the dual boot option screen with my current setup?

Thanks.

You need to use GRUB to do that... Put a Vista option into the GRUB menu since you installed Vista second. To do this you can install startupmanager
```
 sudo aptitude install startupmanager
```
It's an easy way to fiddle with GRUB

In the newest Ubuntu the menu is hidden, you may notice a prompt saying 'Press ESC to see menu, 5,4,3,2,1' or something when Ubuntu starts loading. If you press ESC you will see this menu.

---

### Post by omi291 on 2008-06-12
Is this any help?

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Robk0000 on 2008-06-12
i just gave it a try and recieved this in the gnome terminal 
> 

rob@rob-desktop:~$ sudo aptitude install startupmanager
[sudo] password for rob: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
rob@rob-desktop:~$ 

I have recieved this message several times in doing random stuff. What is dpkg?

---

### Post by powerpleb on 2008-06-12
> **Robk0000 said:**
> 
I have recieved this message several times in doing random stuff. What is dpkg?

dpkg is the program that installs the contents of .deb files (packages) onto your system
aptitude basically downloads a package off the internet, checks to see what other software it needs installed to be able to run (these are called dependencies) and downloads them too, then tells dpkg to install them on your system
Did you try running the command it told you to?
```
sudo dpkg --configure -a
```

---

### Post by Sef on 2008-06-12
In the Terminal (Applications > Accessories > Terminal)

type this command:

```
sudo dpkg --configure -a
```

---

### Post by Robk0000 on 2008-06-12
Okay i ran the configure a for dpkg and it updated, and am downloading the grub manager i believe. Im going to hit esc when i restart the pc this time. And see if i can figure this out, please let me know what i should be looking for.

---

### Post by powerpleb on 2008-06-12
> **Robk0000 said:**
> Okay i ran the configure a for dpkg and it updated, and am downloading the grub manager i believe. Im going to hit esc when i restart the pc this time. And see if i can figure this out, please let me know what i should be looking for.

You need to run the GRUB manager before you restart and add Vista's partition to the menu it will probably be in System>>Administration>>Startup Manager (I use Xubuntu so my menus are different). If Vista is still on another hard drive and that hard drive is connected you can dual boot with that. 

Otherwise, If you want them on the same hard drive you will have to boot up the live CD, open Partition Editor (ALT+F2 then gksudo gparted), make the main partition smaller, create a new partition (if you are going to put Vista on it make sure you make it a FAT32 or NTFS partition) then reboot and install your OS on the new partition.
The link omi291 provided does a better explanation of this then I can.

---

### Post by Robk0000 on 2008-06-12
> **powerpleb said:**
> You need to run the GRUB manager before you restart and add Vista's partition to the menu it will probably be in System>>Administration>>Startup Manager (I use Xubuntu so my menus are different). If Vista is still on another hard drive and that hard drive is connected you can dual boot with that.

This is the method i want to go with, im running the startup manager as i type. The only thing i can do in the program is change default operating system, display res, show bootloader menu, security (passwords for boot meny) and kernal amount.

---

### Post by Xiong Chiamiov on 2008-06-12
I'm not sure how to do it graphically, but if you post the output of
```

sudo fdisk -l

```
I can help you do it manually.

---

### Post by Robk0000 on 2008-06-12
> rob@rob-desktop:~$ sudo fdisk -l
[sudo] password for rob: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60a160a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x478ab117

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488384512    7  HPFS/NTFS
rob@rob-desktop:~$sdf

---

### Post by powerpleb on 2008-06-12
Sorry I had a look at Start-Up Manager and it can't add Windows partitions to the GRUB menu, so sorry for wasting your time. This is how you do it manually:

open up /boot/grub/menu.lst with an editor```
sudo gedit /boot/grub/menu.lst
```
Add this to the bottom of the file```

title		Windows Vista
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```

Also look for the place where it says 'hiddenmenu' and add a '#' to the start of it so it looks like '#hiddenmenu'
This will mean the menu is displayed every time you switch on your computer.

Reboot.

---

### Post by Robk0000 on 2008-06-13
That made it work awesome, i have deleted 2 of the options so now i have, Vista, ununtu and mem test. 1 question before i thank you for your help, Can i create a guest account for login under ubuntu? When i try to create one i always have to have a password, but as a guest i would much rather not require one.

---

### Post by powerpleb on 2008-06-14
> **Robk0000 said:**
> That made it work awesome, i have deleted 2 of the options so now i have, Vista, ununtu and mem test. 1 question before i thank you for your help, Can i create a guest account for login under ubuntu? When i try to create one i always have to have a password, but as a guest i would much rather not require one.

Linux doesn't do accounts without passwords, so no, sorry.

Also, when there are items in the GRUB menu such as extra kernels and recovery mode it's a good idea to keep them in there. If you don't want them showing up in the menu you can add a '#' to the start of the line. This tells the computer to ignore it. That way if you need to boot into recovery mode ever you can just remove the '#' and they will show up in the menu.

---

