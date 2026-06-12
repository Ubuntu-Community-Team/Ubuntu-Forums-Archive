---
title: "Need help on removing Ubuntu from HDD and dual boot"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by sn00pd0gg1 on 2008-05-01
Need help on removing Ubuntu from HDD and dual boot...
Please tell me how do I do it...
Thanks

---

### Post by diablo75 on 2008-05-01
First, you should download and burn off a Gparted ISO to boot from so you can select your Linux partitions and delete them.  You can find the latest ISO available for download here:

[http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-11.iso?modtime=1197927842&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-11.iso?modtime=1197927842&big_mirror=0)

Once you have the primary ext3 partition and your swap partition deleted, you should be able to resize your windows NTFS partition back out to fill in the gap.

Next, you will probably want to remove the grub menu.  This can be done with a windows recovery CD via the recover console (see the fixboot/fixmbr commands here:  [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058) )

---

### Post by Michael.Godawski on 2008-05-01
Here is a good site about dual booting:

[http://apc.simbient.com.au/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apc.simbient.com.au/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

I would just install Windows ( if you want to  install this OS) on the whole drive, then make space for ubuntu.

---

### Post by linux phreak on 2008-05-01
Use this link 

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by sn00pd0gg1 on 2008-05-01
thanks...

---

### Post by sn00pd0gg1 on 2008-05-01
but my comp is runnning on windows vista

---

### Post by bigken on 2008-05-01
judst boot into windows delete or format the ubuntu partitions 
boot from windows XP cd press R for recovery console select 1 for windows partition
just hit enter for the admin password then type** fixmbr** enter **fixboot** enter **exit** enter  your machine will now reboot into windows

---

### Post by linux phreak on 2008-05-01
Just google "remove ubuntu" and you will get it.Here is one i got.
[http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html](http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html)

---

