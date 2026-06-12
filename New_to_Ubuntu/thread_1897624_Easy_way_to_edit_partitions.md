---
title: "Easy way to edit partitions?"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by JoanJohnson on 2011-12-19
I was wondering if there was an easy way to shorten or delete partitions.
A partition is, from my understanding, a memory slot reserved for a particular OS, right? I had Windows up until a few days ago, and I think the partition for it may still be there. If I can delete that partition and use the space for Ubuntu, I could download more things and I wouldn't feel like I was wasting things on my computer. I want to be as efficient as possible. 
So, is there a command or a downloadable software that will help me in this venture? 
Thanks for any and all advice.

---

### Post by Frogs Hair on 2011-12-19
Install GParted from the software center .

---

### Post by Frogs Hair on 2011-12-19
GParted Q & A [http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by JoanJohnson on 2011-12-19
Alright I'm at GParted...but I can't tell what is what.

Edit// There's one labeled DELLUTILITY, and has the flag diag, the other is Recovery with the flag boot. One is OS mounted /host. I'm not sure what those mean at all.

---

### Post by bodhi.zazen on 2011-12-19
You should manage your partitions from a live CD. gparted is included in the desktop CD.

You start gparted and unomunt the swap partition, which can be done from gparted.

Follow the menu or if you need a guide see the gparted documentation (you are already on the web site), but it is very straight forward for most.

---

### Post by *^kyfds( on 2011-12-19
i always used the ubuntu USB installation to change my partitions...


but then again i always pick the stupidest options.

---

### Post by hhh on 2011-12-19
Any partition with an NTFS file system is Windows (probably /dev/sda1). Any partition with an ext3 or ext4 filesystem is Linux, and I bet you can guess what linux-swap is.

To delete a Windows partition, right-click it and choose delete, then apply (I'm always disagree with people deleting their Windows partitions, though, unless they really have no hard drive space to spare. What if you have a Windows-only program you have to run? Plus, another OS on the hard drive is handy if your Linux one goes on the fritz.

You won't be able to resize your Ubuntu/Linux partition while you are booted into it as it needs to be unmounted. To resize a Windows partition, use an Ubuntu LiveCD (it should have GParted on it) or download and burn the latest version of GParted...
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

!!!!Back up important files before resizing, their is a chance the resize will fail and you will need to reinstall Linux!!!!

-edit- Apologies to bodhi and cheese, I was composing as you were posting.

---

### Post by JoanJohnson on 2011-12-19
I think I may understand now, thank you. I have formatted my other two systems to Linux, ext3. I left my boot ntfs system, just in case. Besides, I have the space I need now. Thank you!

---

