---
title: "problems after ubuntu partion delete"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by riljos on 2012-04-06
i was getting rid of the ubuntu partion on my computer, and successfully removed the partion, but windows re booted and now i cant boot windows up. it comes up with an error about GRUB and an "unknown filesystem". not sure how to get around this, any help would be nice.
       thanks!!
 
btw, i dont have a windows boot disc, so solutios in that category would be helpful also!!

---

### Post by coffeecat on 2012-04-06
Hi - welcome to the forum.

Your problem is that part of the grub booting code was in your Ubuntu partition, and now you have only part of grub orphaned in the mbr of the boot disc. You need to re-install the Windows boot code to the mbr which normally requires a Windows installation disc. If you don't have one, you can install equivalent code from an Ubuntu live CD or USB. Do you have one? Boot up the Ubuntu live CD and try one of the three methods described here:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

The first two require an internet connection so that you can install either lilo or mbr. If you can't connect to the internet from the live session, try the third method for which you don't need the first - "sudo apt-get install syslinux" - line. The file /usr/lib/syslinux/mbr.bin is already in the tin, so to speak. But be very careful when typing that dd command in. One typo could do a lot of damage.

---

### Post by riljos on 2012-04-06
the ubuntu live cd is the ubuntu install disc right?
(sorry im kinda new to this)

---

### Post by coffeecat on 2012-04-06
Yup. Tap any key when you see two small icons at the base of a purple screen. This will take you to a text menu where you can select to boot into a live desktop with "Try Ubuntu" I think the wording is. That's so long as it's version 10.04 or later.

If the CD boots past that stage, there is a selection between "Try Ubuntu" and "Install Ubuntu". "Try Ubuntu" will take you to the live desktop. If you have an ethernet cable plugged in it will connect automatically, or you can connect wirelessly so long as your wireless card is supported out-of-the-box.

---

### Post by riljos on 2012-04-06
the computer i'm using has 8.04 on it, will that be any different?

---

### Post by coffeecat on 2012-04-06
When you say the computer has 8.04 on it, do you mean that's the version of Ubuntu you've just deleted? If you have a 8.04 live CD you won't be able to run the first two commands because the 8.04 repositories are long closed. It's an obsolete, unsupported version. I don't know whether the third method will work - I don't remember whether 8.04 had the file /usr/lib/syslinux/mbr.bin included.

Can you borrow a Windows install disc? It has to be a proper Microsoft one, not a manufacturer's OEM image recovery disc. Or you could download a recent version of Ubuntu here:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

Or have a look on the SuperGrubDisk page:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It's a long time since I've used SGD, and much has changed, but I see they mention fixing the Windows mbr, which is what you need.

---

