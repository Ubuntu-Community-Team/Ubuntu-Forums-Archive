---
title: "I have three questions"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by MA7rBRr on 2013-07-31
I have Ubuntu installed, the latest 13.04.

1) How do you get this uninstalled?
2) My second question is how do put the boot order the way you want to be in?
3) My third question, how do you the package installer to know where to start?

---

### Post by humpmihk-msn on 2013-07-31
remove Ubuntu - If Ubuntu is installed in its own partition, in windows you can delete the Ubuntu created partitions they will be of an unrecognised type. Then remove grub by booting on a Windows install CD opening a terminal and running the following command ***BootRec.exe /fixmbr***

change boot order - have a look at this [http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html](http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html)

Package installer - open the Ubuntu software centre and choose the applications you want and click install

---

### Post by MA7rBRr on 2013-07-31
Where do I get that command to run this.  What about an HP.

---

### Post by ian-weisser on 2013-07-31
Too vague. Please describe -in detail- exactly what you want.

For example,
Your #1 indicated you want to uninstall (delete) ALL of Ubuntu. Is that what you intended? Or do you want to remove some application? Or something else?
Your #2 makes no sense if you uninstalled Ubuntu in #1.
Your #3 also makes no sense. Start to do what?

---

### Post by MA7rBRr on 2013-07-31
Yes, I want to delete all of it, I guess I wouldn't have to do two other things step 2, and 3, just to see if i can do this.

---

### Post by Mark Phelps on 2013-07-31
You have provided no details that help us answer your questions ...

Removing Ubuntu from a PC that is running only it, is a very different situation from removing Ubuntu from a PC that is also running another OS, such as Windows, especially if you then want the PC to reboot automatically into Windows when you are done.

Also, removing Ubuntu from an install INSIDE of Windows is very different from removing Ubuntu from an install to its own partitions.

You need to tell us -- in detail -- what you HAVE, before we can help you.

---

### Post by MA7rBRr on 2013-07-31
I got one hard drive wheres as Windows 7 and Ubuntu 13.04 are on it.  I don't think I will now know what kind of installation I received, because I just through the the defaults as a standard.

---

### Post by Paqman on 2013-07-31
Open your file browser in Ubuntu. Do you have a location in the filesystem called /host? If so then you installed using Wubi, if not then you must have installed Ubuntu on its own partition.

---

### Post by GwL3eNC on 2013-07-31
Hi, 

this is about nr 2) My second question is how do put the boot order the way you want to be in?

It's cool, in 3 of my 10 answers i tell about it. I cant handle the grub config files, where you can
change the boot order. I use the grub-customizer for this purpose. 

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

It's pretty easy. Try it out.

---

### Post by Mark Phelps on 2013-08-01
GRUB only works with Linux, not with Windows.  IF the OP removes Ubuntu from their machine, GRUB will do them no good.

To the OP: go into Win7, open Control Panel, and Programs and Features -- and see if Ubuntu is listed as an app.  IF it is, then simply remove it the same way you would remove any other Windows app.

If Ubuntu is not listed as an app, then do the following (in Win7):
1) Download and install EasyBCD from NeoSmart Technologies
2) Open EasyBCD and select BCD BackupRepair, and the select recreate/repair boot files.  This will restore the Windows boot to the MBR, overwriting GRUB
3) Using the Win7 Disk Management utility, remove the Linux filesystem partition(s)

When you reboot, the PC should boot directly into Win7.

---

### Post by MA7rBRr on 2013-08-01
I did that, installed EasyBCD, and nothing happened as the outcome.  I had also did the part you mentioned in step two and now it is calling it ebuntu.  The strange thing is it did not get rid of the extra space, it was reserved for linux.

---

