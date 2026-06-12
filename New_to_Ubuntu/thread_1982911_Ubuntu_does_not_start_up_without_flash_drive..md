---
title: "Ubuntu does not start up without flash drive."
date: 2012-05-19
forum: New to Ubuntu
---

### Post by Solitary7 on 2012-05-19
Good day, everybody. I am very new to Linux as I literally took a leap of faith and completely formated my HD to start from scratch with Ubuntu. Everything was great until I encountered one problem. 

I downloaded ISO image and made my flash drive bootable. When I chose the installation, I chose install Ubuntu instead of the Windows and I chose the whole hard drive as the destination (I did not go into advanced partitioning tools). The Installation went smoothly, but[COLOR=Red] I cannot reboot my laptop without the flash drive. It just won't boot from the hard drive.[/COLOR] I was trying to find out how I can reinstall linux but google didn't help. 

Thanks for your help in advance.

---

### Post by jtarin on 2012-05-19
During installation you chose to install the Grub boot loader to your USB stick and you should have chosen the MBR of your HDD. Probably /dev/sda, if you've only one HDD and it is dedicated to Ubuntu. You don't have to reinstall the entire OS...just Grub. I like to use the [CHROOT]("https://help.ubuntu.com/community/Grub2/Installing#ChRoot") method, however your free to choose any method on that page for re-installing.

---

### Post by Solitary7 on 2012-05-19
> **jtarin said:**
> During installation you chose to install the Grub boot loader to your USB stick and you should have chosen the MBR of your HDD. Probably /dev/sda, if you've only one HDD and it is dedicated to Ubuntu. You don't have to reinstall the entire OS...just Grub. I like to use the [CHROOT]("https://help.ubuntu.com/community/Grub2/Installing#ChRoot") method, however your free to choose any method on that page for re-installing.

Thanks for the reply. I didn't really chose anything during the first installation as I just chose the whole hard drive and Linux did the rest. 

But i fixed the issue. What I did was create a new bootable flash with start up disk creator and reinstalled the whole thing. But when I got to the point of selecting a hard drive, I went into advanced options and formatted a partition for swap and Ext4 manually. :P

---

