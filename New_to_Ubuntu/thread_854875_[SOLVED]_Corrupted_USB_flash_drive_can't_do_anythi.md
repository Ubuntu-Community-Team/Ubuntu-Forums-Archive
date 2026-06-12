---
title: "[SOLVED] Corrupted USB flash drive can't do anything"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by AOZ on 2008-07-09
hi all
My Sandisk 4GB flash drive for some reason is completely fubar. I was just transferring songs from this linux laptop to my windows box when it decided that it was now going to be a read only device with 1GB of hidden files. I can't format it on my windows box because it says i don't have the rights. I can't delete the (im assuming corrupted) .Trash folder either. Anyone have any ideas? 
P.S. i've tried a few ways i found on the internet to format a drive in the CLI but it all looked a bit sketchy which is why im back here.

---

### Post by ChameleonDave on 2008-07-09
Do you just want to format the drive (easy), or do you want to attempt to recover the files on it (tricky)?

---

### Post by AOZ on 2008-07-09
format i coudl care less about whats on it

---

### Post by ChameleonDave on 2008-07-09
> **AOZ said:**
> format i coudl care less about whats on it

Use GParted.

You probably have it already.  If not, you can install it in Synaptic, or by typing "sudo apt-get install gparted" on the command line.

Plug in your device.

Start GParted from the application list, or by typing "gksudo gparted" on the command line.

There will be a drop-down list in the top right.  Each item is a drive on your system.  For me, the first item is my hard drive containing Ubuntu and my Files, the second item is my hard drive containing Windows XP, and the third item is the USB stick that I currently have plugged in.  Select the one corresponding to your device.  It's probably the last one.  It will contain one big partition.

You can then use the interface to reformat that partition to whatever filesystem you like.  FAT is the usual choice, though you could be daring and go for Ext3 if you will only use the device with Linux, or NTFS if you will only use this device with Windows.

---

### Post by AOZ on 2008-07-09
k i formatted it but now it doesnt show up on my desktop when i plug it in. gparted still sees it. Is it because i need to mount it in the terminal? if so how? thanks for ur help

---

### Post by ChameleonDave on 2008-07-10
> **AOZ said:**
> k i formatted it but now it doesnt show up on my desktop when i plug it in. gparted still sees it. Is it because i need to mount it in the terminal? if so how? thanks for ur help

Plug it in.  What is the output of "sudo blkid" from the terminal?

GNOME (you are using GNOME, aren't you?) should automount the drive.  KDE automounts mine for me.  If it doesn't, then that's a different problem.  You should nevertheless be able to resort to manually mounting in from the command line.  I think there is a chance that something (perhaps GParted) is interfering with the automounting.  Perhaps you should trying logging out, logging back in, then inserting the drive.

To mount from the command line, you need to know the exact name of the device.  Blkid will help with that.

---

### Post by AOZ on 2008-07-10
woooo yay closing gparted worked thanks alot dave

---

### Post by ChameleonDave on 2008-07-10
> **AOZ said:**
> woooo yay closing gparted worked thanks alot dave

Great!

One last bit of advice.

It is helpful for your drive to have a label, so that it comes up with something recognisable when you plug it in.

I'm assuming you formatted it as FAT.  Use GParted or "sudo blkid" to see what the drive identifier is.  Then do this:

```
sudo apt-get install mtools
sudo mlabel -i /dev/**sdb1** ::*AOZ_drive*

```

Replace the bit in **bold** with the correct drive identifier.  Replace the bit in *italics* with what you want the label to be.

---

### Post by johnystevenson on 2009-03-01
hey

thanks for the how-to, i had fried my flash drive but with your help it is going again

2 things i have not figured out;
how to label the drive
how to say thanks in a thread
cheers
johny

---

