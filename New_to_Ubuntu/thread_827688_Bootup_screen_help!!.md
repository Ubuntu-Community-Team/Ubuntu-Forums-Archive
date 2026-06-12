---
title: "Bootup screen help?!?!?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by GRAYgoose12 on 2008-06-13
hi well i unistalled ubuntu feisty fawn to install hard heron but when i restarted the computer it was still their so i decided to bootup with it and it said something like Midrr.dll cannot be found it may be corrupt so i tried to reinstall it and unistall to get rid of the ubuntu ann automatically start vista but noo their are 2 ubuntu and both say that. Midrr.dll or something is corrupt how do i remove those to ubuntu things in the bootup menu ss vist will auomatically run

---

### Post by Bodsda on 2008-06-13
You said that you were going to install Hardy Heron so im assuming you have the live cd (or a live cd of some sort)

boot up the live cd and open a terminal

NOTE: This would be a good time to backup any important files on any of the Ubuntu partitions.



type ```
sudo fdisk -l
```

Now this should show disk information and disk partitions.
Make a note of all the Ubuntu partitions  e.g /dev/sda2

Next in the terminal type
```
gksudo gparted
```

Now you should see a partitioning program load. In the top right hand corner you need to select the correct hard drive (The one with the problematic Ubuntu's on it)
Then delete all the ext3/linux/swap partitions, basically any partitions related to those installs need to be deleted. Then close gparted.

Fire up the installer and install Ubuntu.

I wasnt too sure if you were asking how to get Ubuntu working or how to get back to vista.

To make your system boot vista automagically, go into your system bios and change the first boot device to the vista hard drive. Then boot the vista recovery disk, at the recovery prompt type 
```
fixmbr
```

Then reboot without the cd in the drive and vista should boot.

Hope this helped

Bodsda

---

### Post by GRAYgoose12 on 2008-06-14
but it made my ubuntu partitions disapear and they are not hidden 
so do put the live cd in and can i use the demo part
also this is my bootup menu pretty much
---
Vista
Ubuntu
Ubuntu
---
those are what i can choose from neither of the ubuntu work they say they are corrupted and so howo i make the boot menu look like this 
---
Vista
---

---

### Post by Bodsda on 2008-06-18
if you mean how do you remove ubuntu, you can boot into vista and just delete the partitions 

or
[http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html](http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html)

Also, if theres anything you need help with that could keep ubuntu on your machine, just let me no and il try and help.

---

### Post by Sef on 2008-06-18
From the Live CD, Applications > Accessories > Terminal

then type in the code that Bodsda recommended:

```
sudo fdisk -l
``` Small L.  Copy and paste the results here.

---

