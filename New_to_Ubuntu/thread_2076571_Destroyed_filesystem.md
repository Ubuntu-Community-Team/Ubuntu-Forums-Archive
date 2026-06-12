---
title: "Destroyed filesystem"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by sanfili on 2012-10-26
I did some kind of mess and I cancelled the Ubuntu partition so, when I  tryed to restart my computer I got the message" UNKNOWN FILESYSTEM   -- GRUB RESCUE".
BUT the worst is that I can't IPL from any device (Floppy or CD) since I have the same answer. The installed op sys is Windows7 on partition 1.
on the same disk there is the hidden partition of system image ond the hidden partition of the recovery.
I hope you can help me, I am a real beginner with GRUB!

---

### Post by Zyl on 2012-10-26
I assume you did use GParted?
What was the state of you harddrive? (what partitions)
What operation(s) did you start?
Which of them completed and which did you cancel?
What does GParted list when you run it from an Ubuntu Live CD now?
What Ubuntu version are you using?

---

### Post by NikTh on 2012-10-26
Hi,

you have to boot from a LiveCD of Ubuntu. You have to manage how to boot from a LiveCD or USB or else any help would be in vain. 

If you manage to boot from a Live-media of Ubuntu , then you can try to correct your filesystem or even better , copy all your important data  to an external media (HDD) and try to install from scratch.

Thanks

---

### Post by Mark Phelps on 2012-10-26
Cancelling out of the installation left the machine in some kind of interim state -- and in that case, it won't be able to finish booting from the hard drive.

The very least you need to find out is if you overwrote or otherwise damaged the Win7 install already on the drive.

To do that, you will have to boot from an Ubuntu LiveCD or LiveUSB.  There's no way around that.

Your getting the GRUB messages means your BIOS is still trying to boot from the hard drive.  You will have to go into the BIOS settings and change it to boot from the CD or USB -- whichever you need.

You typically change boot options on modern PCs by pressing F12.

Once you get to an Ubuntu desktop, open a terminal and enter "sudo fdisk -lu" (without the quotes and using a lowercase L, not a one).  That will list out the partitions on the drive.  Post the result back here.

---

