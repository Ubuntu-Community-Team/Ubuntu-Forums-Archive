---
title: "grub rescue&gt; grub error ubuntu boot"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by vidmantasdd on 2012-06-11
hi,
I had  problem with **grub rescue>** ,and sorted out with next way:
booted from  ubuntu live usb(cd) , go to places-computer-file system and  find file **/boot/grub/menu.lst** open file menu.lst and copy everything.
Next- go to your drive where is your not working ubuntu , and look in **/boot/grub/menu.lst **
on my computer,this file was missing,so with sudo gedit in terminal, i  opened new text editor, pasted copy of **/boot/grub/menu.lst **from live usb  and saved file in /boot/grub/  where is not working ubuntu. And **reboot  computer**.
And - my crashed Ubuntu working normal now :)
As well, **make sure** you got same ubuntu system on live usb ( for example,my was ubuntu 10.04 64bit on hdd and same on live usb)
Let me know ,if it works for you:)
bye......:KS

---

### Post by YannBuntu on 2012-06-11
hi
this won't work with most of users, because menu.lst is for GRUB1, which is obsolete (not maintained any more). Current versions of Ubuntu use GRUB2 by default.
Some users still have GRUB1 because it comes from successive upgrades.
See [https://help.ubuntu.com/community/Grub2/Upgrading](https://help.ubuntu.com/community/Grub2/Upgrading) if you want to upgrade to GRUB2.

---

### Post by vidmantasdd on 2012-06-11
In my case, when I had error - grub rescue> , I checked directory **/boot/grub/ **in which file **menu.lst **was missing. So probably other ubuntu users got same problem.
sudo apt-get install grub2 or sudo apt-get install grub don't sorted out my problem.
So, users have to go to **/boot/grub/ **and look for **menu.lst **file.
If file not exist, need simply create this file from ubuntu live usb (CD) directory **/boot/grubmenu.lst  **

---

### Post by drs305 on 2012-06-11
I believe you meant "/boot/grub/menu.lst" rather than "/boot/grubmenu.lst". However, if running a LiveCD the user would also need to mount the real Ubuntu partition. In this case the address would become /<mountpoint>/boot/grub/menu.lst.

In either case, if you were at a Grub rescue prompt it meant that the system was using Grub 2 and not Grub legacy. As *YannBuntu* stated, menu.lst is not used by Grub 2 so I don't know how your system repaired itself. 

Very few users still need a menu.lst file and for those experiencing difficulties with Grub 2 I strongly recommend using *YannBuntu's* Boot Repair app. There is a link in my signature line.

In any case, I'm glad you are now able to boot.

---

