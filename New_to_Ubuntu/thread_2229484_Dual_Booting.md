---
title: "Dual Booting"
date: 2014-06-13
forum: New to Ubuntu
---

### Post by robert1305-gmail on 2014-06-13
Hi,

I dual boot using Linux Mint and Ubuntu.

When I boot up I have the choice of either, but the first in line is Ubuntu, and this auto starts if I am not there to change the choice, what I would like to do is to make Mint the first choice, is there anyway of doing this ?

Regards Bob

---

### Post by Harry.k on 2014-06-13
[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

---

### Post by pfeiffep on 2014-06-13
[http://www.computerandyou.net/2011/08/how-to-change-the-default-boot-order-in-grub-2-in-ubuntu-10-04-10-10-and-11-04/](http://www.computerandyou.net/2011/08/how-to-change-the-default-boot-order-in-grub-2-in-ubuntu-10-04-10-10-and-11-04/)

---

### Post by oldfred on 2014-06-13
Grub customizer does add its own scripts depending on what changes you do.

Easier to boot into Mint and just install its grub to MBR if both are on sda.
       sudo grub-install /dev/sda

But both systems may remember where installed and on major grub update reinstall to MBR. If you unchoose everything then it should not reinstall.

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by robert1305-gmail on 2014-06-14
Thanks for the replies guys much appreciated

Regards Bob

---

