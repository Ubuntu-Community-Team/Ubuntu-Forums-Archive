---
title: "Grub/OS boot manager"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by Entyrion on 2013-07-17
I have been using Ubuntu as my primary OS and I love it. I also have Win7 installed for gaming and the odd compatibility requirement (rarely use it anymore). My issue is that I recently installed Trisquel on my hard drive just to poke around for fun. I was expecting it to show up as a new option in my Ubuntu grub/OS boot screen, but instead, I always boot to Trisquel's instead and am forced to select my OSes from there.

I had set up my Ubuntu grub screen with my preferred OS priority, shorter default countdown, and I just plain preferred the purple screen. What can I do to ignore whatever Trisquel installed that is overriding my old Ubuntu boot up screen?

Thanks!

---

### Post by oldfred on 2013-07-17
You can just boot into Ubuntu and easily install its grub2 boot loader to the MBR.

 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

But each install of grub2 remembers where it installed and on major updates may reinstall. Not sure how Trisquel works but with Ubuntu you can run these commands.

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
# if you unchoose everything then it will not reinstall anywhere.

---

