---
title: "Help!!!! Need to create a partiton for Vista"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by neothorn2301 on 2008-06-05
I currently have Ubuntu as my primary O.S. I installed it after Vista crashed after installing service pack 1. I need to run Vista or XP (I have both) Being a newbie I totally reinstalled Ubuntu and  created additional partitions (Which I should had did in the first place) In the man. mode. However when I went to install Vista on any of the partitions it will not allow me to install Vista on any of the partitions, Vista keeps telling me that it needs a NTFS file system. So my question is, How do I create a NTFS file partition, so that I can install Vista on one of those partitions. And please include any additional help I might need to beable to boot into either Ubuntu or Vista. I love Ubuntu, I just need Vista on my system for work, because sometimes I need to work from home, and our PACS system (Digital imaging software is not supported by Ubuntu) Please help!!! Thank you


EDIT: I do not have the Live CD. I have yet to get it in the mail, and I need to work this out before tomorrow, Thanks for all your guys help, I have been reading many post on this site, and you guys have helped me out al ot.

---

### Post by PoopyTheJ on 2008-06-05
Does Vista not give you the option of formatting the partition as NTFS? In WinXP when you load you can choose whatever partition you like formatted however you like and reformat as NTFS, I'm not totally familiar with Vista's install but I'm pretty sure you should have the same option. I do know that if you don;t have Vista setup for a primary and not a logical partition you're in trouble as Windows can't handle not being on the primary partition. If you have a primary partition free and reformat it using NTFS then after you reload Vista you're gonna need to reinstall grub as Vista will wipe it out so you can only boot to vista. Check this guide out for instructions on that [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

After looking around I found this image showing a Vista Install on a logical drive so that I guess works with Vista however below the screen you'll see a Drive Options (Advanced) area click there and you can probably format the partition to NTFS.

[http://i.t.com.com/i/tr/downloads/images/shultz1/dual_boot/dual_boot_vista_9.png](http://i.t.com.com/i/tr/downloads/images/shultz1/dual_boot/dual_boot_vista_9.png)

---

### Post by bumanie on 2008-06-05
Usually windows will ask whether you want to format to a ntfs filesystem. You could do this from ubuntu by installing gparted and getting it to format you have put aside for vista to be formated to ntfs. It is best if vista is on the first partitionof the primary hard drive. Once you have installed vista, you will need to reinstall grub to achieve a dual boot.

---

### Post by neothorn2301 on 2008-06-05
So, you mean to tell me that there is nothing that i can do to get a NTFS partition on my machine? No, Vista gives you no option to format into a NTFS file, I even left a spot on my harddrive with no partition, and vista will still not install a partition. IS THERE A PROGRAM THAT WILL CREATE A NTFS FILE IN UBUNTU? Gparted doesnt work. All of the NFTS format box is all greyed out. I believe that you have to first have a NTFS partition on you hard drive before you use gparted to edit it. Any ideas of how to MAKE a new NTFS partition I currently have NO nfts partition.

---

### Post by Paqman on 2008-06-05
Gparted will make NTFS partitions, but not on a drive that's mounted at the time. Boot into your LiveCD, run Gparted and you should be fine.

---

### Post by Bill magee on 2008-06-05
Hi Neothorn, you can also install VirtualBox (or any other emulation software) and install your Windows into the partition create by VirtualBox. I have done that, and Windows works the same as it would in a separate boot partition.

---

### Post by PoopyTheJ on 2008-06-05
Were you able te resolve your issue? If you can't get Vista to work try XP, XP doesn't care where the drive is, or what the partition is currently it'll format as NTFS, boot from a WINXP CD go through like your going to install format the partition you want as NTFS, once it starts the install drop out and insert your Vista CD if you're stuck on having Vista, otherwise just install XP. You'll have less headaches though still more than Ubuntu unfortunately.

Otherwise just backup the ubuntu stuff you want, unless you've spent aeons getting it setup like you want and wipe it out and reinstall. A PITA I know but you'll get windows installed that way.

---

### Post by wenuswilson on 2008-06-06
> **neothorn2301 said:**
> So, you mean to tell me that there is nothing that i can do to get a NTFS partition on my machine? No, Vista gives you no option to format into a NTFS file, I even left a spot on my harddrive with no partition, and vista will still not install a partition. IS THERE A PROGRAM THAT WILL CREATE A NTFS FILE IN UBUNTU? Gparted doesnt work. All of the NFTS format box is all greyed out. I believe that you have to first have a NTFS partition on you hard drive before you use gparted to edit it. Any ideas of how to MAKE a new NTFS partition I currently have NO nfts partition.

I found a way to get ntfs to work in gparted, but as of yet, haven't gotten it to work to install a fresh XP install.

> sudo apt-get install ntfsprogs

---

