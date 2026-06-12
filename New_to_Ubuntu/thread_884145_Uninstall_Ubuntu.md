---
title: "Uninstall Ubuntu"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by th00ht on 2008-08-08
How do I uninstall Ubuntu from my system? Whenever I boot my machine it goes through a "grub" menu where I need to select Microsoft Vista.

How do I reinstall Microsofts loader again?'

---

### Post by cdtech on 2008-08-08
Insert your windows disc and "fixmbr" to reinstall the MBR.

---

### Post by rossjman1 on 2008-08-08
If you would still like to keep Ubuntu, you can edit the /boot/grub menu.lst to make Grub boot Vista by default. Just do a search, there are plenty of threads that tell you how to do this.
To get rid of Ubuntu, make sure you have an Ubuntu live cd and Windows boot disk. Pop the Ubuntu Live CD in your computer, and boot into it. Open the partition manager (GParted) and delete the entire Ubuntu partition and swap partition. Now extend your Windows partition to fill the empty space. Take the Live CD out and pop your Windows boot disk in and reboot. Once the Windows disk is loaded go into the recovery console and type fixmbr like the above user posted.

---

### Post by ibootindos on 2008-08-09
so I don't have my windows disc?

---

### Post by SunnyRabbiera on 2008-08-09
you really dont need to remove the whole OS to make windows primary.
But why do you want to remove ubuntu, have any valid reasons?
I would still have a dual boot personally, I cant stand the thought of vista only.

---

### Post by arpanaut on 2008-08-09
You'll need to restore Vista's mbr. If you have no disc you can get one here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Instructions here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You want to "fix boot" and "fix mbr"!

---

### Post by st33med on 2008-08-09
Would you like to move Microsoft Windows to the top of the GRUB menu?

In the terminal, type:
```
sudo gedit /boot/grub/menu.lst
```
There should be a line at the bottom with a few line pertaining to your XP install. Cut and paste it above these lines that look something like this:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5e98fc16-cae5-49af-8c7e-5268a558c888 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-19-generic
```

It would be the first one at the top.

---

### Post by pi.boy.travis on 2008-08-09
Even if you don't use Ubuntu, it's a good idea to keep it around, in case Vista ever fails (and it is likely to at some point)

---

### Post by cdtech on 2008-08-09
Technically it would be better to change the default boot order using the line within the menu.lst:
```
default		0
```
Change to whatever your order is within your menu.lst, rather than edit the entire list. This protects the menu.lst from corruption.

Then issue the command:
```
sudo update-grub
```

---

