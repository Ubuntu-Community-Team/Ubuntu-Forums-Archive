---
title: "Restoring windows MBR after GRUB errors"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by User X on 2008-06-04
I am looking for some help restoring my windows MBR.  After installing Ubuntu 8.04 and GRUB I am getting a lot of errors using GRUB to dual boot.  I have Windows XP on two 200Gb drives being mirrored in a raid array and I installed Ubuntu on a seperate 40Gb drive.  I get Grub error 15, 17, and now 21 when I boot the system and my motherboard has a boot manager built into my bios that I would like to use instead of GRUB but I cannot boot to either drive right now. I have run FIXMBR on the 40Gb and if I use my bios to boot to that drive I get "invalid system disk, please replace and press return" or something.  I have to make a raid driver disk at work today so I can boot to the repair console from windows XP and see my raid drives but what do I do after that?  Just run FIXMBR and FIXBOOT?  Is that all I need to do?  I am not worried about the 40Gb drive right now I just need to get my Windows XP back.  Right now if I try to boot to my raid drives I get a grub error.  I assume this is because Grub is loaded in the MBR of this drive - ?  Thanks for any help!

---

### Post by Nessa on 2008-06-04
Theoretically, yes. You'll only need to run FIXMBR. FIXBOOT is optional but you can run it too for good measure. Good luck!

---

### Post by Biggy on 2008-06-04
Download [Super Grub Disk]("http://www.supergrubdisk.org/index.php") ,burn iso image to CD. boot from cd to fix grub

---

### Post by maculata on 2008-06-04
> **Nessa said:**
> Theoretically, yes. You'll only need to run FIXMBR. FIXBOOT is optional but you can run it too for good measure. Good luck!

What he ^^^ said...

---

### Post by Duck2006 on 2008-06-04
You can do it with the live CD of ubuntu as well.

[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

[http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)

---

### Post by sweeneytodd on 2008-06-04
think the original command was something like"fdisk /mbr"

---

### Post by Joeb454 on 2008-06-04
In XP I know it's ```
fixmbr
``` though for vista it's a little different (I can't remember exactly)

---

### Post by bjorn on 2008-06-04
Not sure if this will work but the Windows/DOS fdisk has a fix MBR option.

fdisk /mbr

If you boot off the Windows XP install CD in to  the command line rescue mode you may be able to do this.

---

### Post by sweeneytodd on 2008-06-04
would still try fdisk /mbr if fixmbr doesn't work as i have fixed mbr problems with this command, might of been win98 though, still worth a crack if other command doesn't work, please label as solved if u have rectified problem, i'm pretty new to forums and just thinking of the experts in this field reading already solved issues and responding and wasting there time.

---

### Post by User X on 2008-06-04
Thanks everyone for the help.  I will trty this tonight and let you know how I make out.  I have a lot of information on my windows drives and I am nervous about doing anything with the drives for fear that I may loose information.  I am puzzled as to why grub would be on these drives anyway where I installed Ubuntu to the 40Gb drive???  Can anyone reasure me that the windows information is not lost?

---

### Post by User X on 2008-06-04
Thanks guys!  It worked like a charm!  I am going to install Ubuntu now on the 40gig drive using the alternate CD and choose not to install Grub.  Then I should be able to use my Bios to select a device to boot from.  Thanks again for all the help!

---

### Post by bjorn on 2008-06-04
> **User X said:**
> Thanks guys!  It worked like a charm!

Please confirm which method worked for you.

---

