---
title: "Corrupt partitions at install"
date: 2013-10-14
forum: New to Ubuntu
---

### Post by hackernewtolinux on 2013-10-14
Hi guys. I am a computer enthusiast, and know a little bit of linux, but being a 16yo and needed to go back to windows everytime i install linux. but now after getting my new laptop which was Pre-installed with windows 8, I am really really freaked out.The metro UI,other aspects, I AM TRULY, irritated and am switching back to linux FOREVER!!! I watched as microsoft gripped my own computer out of my own hands. SO, getting back to the point i have only used backtrack and kali linux(debian) before and haven't gone too much into it. 

[SIZE=5]Please consider me as a newbie or a n00b or whatever you want and help me kindly.

[SIZE=2]Now the other day i was installing ubuntu 12.04 with windows 8 as dual boot.[/SIZE][/SIZE]
now here is a mistake. i was impatient at the end while ubuntu was at installing system and force shut down. windows booted fine, but i wanted ubuntu again and the grub2 wouldnt install. so i when i used boot-repair it said i had to unmount the drive and hence i dismounted all partitions and formatted them. they were filled , and windows was lost. so when i tried to install ubuntu again it said that the partitions were corrupt of full(i dont remember but it said that i need to merge the partitions.) hence now i am using this 
[http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux](http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux)
and am re-formatting and will try to re-install ubuntu again after the hardrive will finish 
dd if=/dev/zero of=/dev/sda bs=1M
.

if in anycase it fails do you have any advice for me? this computer is my saving for a lot of time and i dont want to loose it and this thread is from my fear

thanks

---

### Post by Lars Noodén on 2013-10-14
Please, please fix the spelling in the title.

---

### Post by harrypotter7 on 2013-10-14
Alright boot the ubuntu cd and when it asks **"install ubuntu along side windows or erase entire or something else " select something else** make ur own partition and format the disks and then try to install it.

here is the link step by step

[http://www.ubuntu.com/download/desktop/install-desktop-long-term-support](http://www.ubuntu.com/download/desktop/install-desktop-long-term-support)

---

### Post by Elfy on 2013-10-14
Please do not use silly titles for threads. 

People use titles to search for issues - [http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

---

### Post by Lars Noodén on 2013-10-14
When you get to the partitioning menu again and select "something else" look for the existing Linux parition and use that.  It should be EXT4.  If you used the default installation settings before, you should have only one to choose from.  You'll need to make it a mount point for the root of your system "/" and you want to format it.  Be sure that the swap partition is also there but if it is, you don't need to do anything about it, the system will find and use it automatically.

---

### Post by hackernewtolinux on 2013-10-14
ok guys, i did a low level partition and it didnt work. so i formatted it using ubuntu installation, now it is stuck at downloading packages (0:00 remaining). i tried hitting skip but no use

---

### Post by harrypotter7 on 2013-10-14
then **uncheck the option download packages while installing** at the start or make sure ur internet connection is working properly

---

### Post by oldfred on 2013-10-14
Did you totally erase drive or do you still have Windows 8.
If you have Windows 8 pre-installed then you have UEFI booting and need to install Ubuntu in UEFI mode to easily dual boot.
If you have totally erased drive you can install Ubuntu in the old BIOS/CSM mode or in the new UEFI boot mode. You can use gpt partitioning with either BIOS or UEFI, but if thinking of using Windows it will only boot from gpt partitioned drives with UEFI.
       Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

If your want UEFI, lots more info in link in my signature. UEFI make it more complicated as now you have to choose UEFI or BIOS booting when you install and then may have gpt or MBR(msdos) partitioning. 
How you boot install media for both Windows & Ubuntu is how it installs.

      
 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by hackernewtolinux on 2013-10-14
okay then, i used a live version and use gparted, formated the whole hard drive including mbr, and partition tables. turned my pc into legacy mode and did an install and now it works just fine. thanks a lot guys for your help. no wonder why people say forum support is immediate. im sticking with linux even if i have a legit windows

---

### Post by moshefeit on 2013-10-14
LOL, I bet you were panic that time lol

---

