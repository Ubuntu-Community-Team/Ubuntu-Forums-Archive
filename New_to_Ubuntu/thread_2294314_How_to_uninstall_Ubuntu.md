---
title: "How to uninstall Ubuntu?"
date: 2015-09-10
forum: New to Ubuntu
---

### Post by mark246 on 2015-09-10
Hi i had installed ubuntu on my laptop i am looking to see how to unisnatll really hope Someone can help

---

### Post by yancek on 2015-09-10
Ubuntu is a Linux operating system.  You don't uninstall it unless you had a wubi install inside windows.  The general process is to simply format the partition(s) on which you had Ubuntu before or during the install of the other operating system.  Are you planning to install something else?  If so, what?

---

### Post by mark246 on 2015-09-10
hi yes to let you know i scrubbed the laptop by mistake and formated the hard drive so windows 8 disapeard i had no back up discs so only system i could get installed is the linux i now have a copy of windows 10 but i need to get the linux off any help would be great

---

### Post by Bucky Ball on 2015-09-10
Welcome. Boot from the live USB or disk and at the options 'Try Ubuntu'. When at a desktop, launch Gparted, right click and remove the partitions on the drive (make sure they are unmounted), close gparted, restart or shutdown machine.

Next time you post, if there is one, could you please check the second link in my signature and [this]("https://duckduckgo.com/?q=remove+ubuntu").

---

### Post by arochester on 2015-09-10
Just put the Windows 10 disk in the CD/DVD-Rom and boot from the CD/DVD-Rom.

---

### Post by Bucky Ball on 2015-09-10
> **arochester said:**
> Just put the Windows 10 disk in the CD/DVD-Rom and boot from the CD/DVD-Rom.

Windows may not recognise the EXT partitions to delete them properly or at all. Unsure. Better to kill the partitions. Windows doesn't natively know what they are, unless something miraculous has happened with Win10. :-k

---

### Post by QDR06VV9 on 2015-09-10
> **arochester said:**
> Just put the Windows 10 disk in the CD/DVD-Rom and boot from the CD/DVD-Rom.
+1
You will how ever have to manually delete the Linux partitions and from there you should be good to go.
Bucky Ball's suggestion to use gparted will save that step and just install windows smoothly.
How To Clean Install Windows 10 From USB/DVD (With Pictures)
[http://www.intowindows.com/how-to-clean-install-windows-10-from-usb-dvd/](http://www.intowindows.com/how-to-clean-install-windows-10-from-usb-dvd/)
Good luck

---

### Post by mark246 on 2015-09-10
really struggling anyone able to give a wee help as to what i have to do sorry if dumb lol

---

### Post by monkeybrain20122 on 2015-09-10
If you can't manage partitions,  then Install virtualbox and put your Windows there. :)

---

### Post by grahammechanical on 2015-09-10
These links will provide you with the information on how to use Gparted from a Ubuntu live session.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://gparted.org/display-doc.php?name=help-manual](http://gparted.org/display-doc.php?name=help-manual)

If Ubuntu is the only OS hard disk then delete the partitions. If there is another OS on the drive then you must restore the boot loader of that OS before you delete the Ubuntu Partitions.

Once you have a drive that is full of unallocated space you can then run the Windows Install disk. I have never installed Windows 10 but from my one experience of installing Windows 8 pre-view I learnt that the Windows 8 installer would not allow Windows 8 to be installed unless I first used the installer to create and format at least one Windows partition. I can only guess that Windows 10 is similar.

For all I know the Windows 10 installer make notice a hard disk with all unallocated space and offer to install to the hard disk without any fuss.

Regards.

---

### Post by chemist931 on 2015-09-12
Well, if you installed Ubuntu on top of your Windows 10 and don't have the backup disk, you will need your product key to reinstall Windows 10.  Download the W10 .iso file from the Microsoft (spasm) website, then burn it on a DVD or a USB drive, then install with the product key.  This won't work unless you have the product key.  And if you don't have the key, and you don't have another operating system, why would you delete a perfectly capable one such as 'Buntu?
EDIT:
Sorry, I know this doesn't really answer the question, but why uninstall the OS for nothing?

---

### Post by Lewjay on 2015-09-19
Where or what is gparted and how do you use it?

---

### Post by Lewjay on 2015-09-19
No help whatsoever to us non tech folks.  I have gparted but have no idea what I'm looking at. I have all kind of partitions and dva 1,2,3,4,5,6,7 etc.  I see one that says OS and one that says Linux.  I tried to set up a WIN10 recovery but it won't run from the thumb drive.

---

### Post by Lewjay on 2015-09-19
this is what my gparted shows
/dev/sda1    NTFS    SYSTEM
unallocated
/dev/sda2 !   NTFS    OS
/dev/sda3     extended
/dev/sda5     NTFS    /media/7d8d876643FF49BA
/dev/sda6     ext 4
unallocated
/dev/sda7     linux swap
/dev/sda4     NTFS     HP Recovery


now what do I delete??

---

### Post by Bucky Ball on 2015-09-19
Please use code tags for terminal output. See last link in my signature.

As mentioned, you're EXT partitions are the Linux ones. Right click, unmount and delete /dev/sda6 and sda7. I have mentioned already these are the Linux partitions and Windows doesn't have a clue about EXT partitions.

---

### Post by chemist931 on 2015-09-22
Your best bet is to just insert the W10 disc and boot from that.  You can just wipe your drive again (I don't think W10 has a problem with wiping competing operating systems) and reinstall W10.  Although I beg you to stick with Ubuntu.  We don't want to spread the word of the devil.
:lolflag:

---

### Post by Bucky Ball on 2015-09-22
> **chemist931 said:**
> Your best bet is to just insert the W10 disc and boot from that.  You can just wipe your drive again (I don't think W10 has a problem with wiping competing operating systems) and reinstall W10.  Although I beg you to stick with Ubuntu.  We don't want to spread the word of the devil.
:lolflag:

Have you read my previous posts? Win will get stuck trying to remove the EXT partitions as it doesn't know what they are. You must delete them by booting from the Ubuntu live install media and using Gparted or another Linux software.

Best to read at least a few posts rather than just the first. :)

---

