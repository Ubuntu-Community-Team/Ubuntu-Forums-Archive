---
title: "Triple boot update problem"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by yakinikku on 2012-03-01
Hello all,

I was wondering if I could get some assistance.  I currently have a system that is triple booting.  Windows 7 was installed first, then 2 ubuntu variants were installed after that.  The installs went fine.  

In order it went like this: Windows 7, Ubuntu Variant 1, Ubuntu Variant 2.

All 3 OSs boot just fine.  When I installed Ubuntu Variant 2 I did not install a boot loader because I wanted to use the boot loader from Ubuntu Variant 1.  Grub is installed on Ubuntu Variant 1 and I think this is the crux of my problem. 

I recently saw that there was a major update to Ubuntu Variant 2, and as per the instructions I ran an apt-get dist-upgrade from the terminal.  However, part of the postinst hook script requires that it run update-grub.  This causes the install to fail.  Is there any way that I can bypass grub update so I can complete the dist-upgrade?  TIA all!

---

### Post by yakinikku on 2012-03-01
I solved this issue by installing grub to the Ubuntu Variant 2 partition rather than the main partiton.  This did not destroy my grub configuration.

---

### Post by Bucky Ball on 2012-03-01
Great. Please mark thread as 'Solved' from 'Thread Tools' to help others. ;)

---

### Post by oldfred on 2012-03-01
If you blank this out - unchoose all drives, then grub will not reinstall on updates.

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

