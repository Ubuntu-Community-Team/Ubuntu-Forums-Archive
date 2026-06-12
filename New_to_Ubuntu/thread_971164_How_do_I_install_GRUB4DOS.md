---
title: "How do I install GRUB4DOS ?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by andrewwg94 on 2008-11-04
I want to install it on the MBR so that it replaces the GRUB that Ubuntu installs. (I'm constantly installing/removing linux, so it's convenient to just put grub on my windows partition).

---

### Post by louieb on 2008-11-04
Haven't used grub4dos. What I did was make a dedicated grub partition it has GRUB install in it and nothing else. so it can be small 4mb is more than enough. 

When the PC boots it load the the GRUB menu from the dedicated partition. The GRUB menu itself is simple. Just some chainloader statements to boot whatever  OS  in that partition. 
[IDBS make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")

---

### Post by caljohnsmith on 2008-11-04
I just wanted to mention that it's important to use a Grub4DOS version that is the 6-28-08 version or more recent, because it has the ability to boot the newer Linux ext3 partitions that use a 256 byte inode size, which is true of Intrepid. You can download the 7-21-08 version from [here]("http://download.gna.org/grub4dos/grub4dos-0.4.4-2008-07-21.zip"). Then to install Grub4DOS to the MBR, probably the easiest way is with the grubinst_gui.exe program from [here]("http://internap.dl.sourceforge.net/sourceforge/grub4dos/grubinst_1.0.1_bin_win.zip"). All you need to do is put the grldr file from the 7-21-08 package in your Windows root directory, and also put your Ubuntu menu.lst in the Windows root directory too. If you menu.lst uses the newer "uuid" notation of Intrepid, you'll have to change it to use the "root (hdX,Y)" notation instead for Grub4DOS, if I remember correctly. 

If you need more specifics, let me know, but that's the general idea. :)

---

