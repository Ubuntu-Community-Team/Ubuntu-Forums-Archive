---
title: "Unable to install"
date: 2012-06-17
forum: New to Ubuntu
---

### Post by rito090884 on 2012-06-17
Hi all , 
I have recently bought a alienware M17x - spec are below : 
Intel i7 2860 proccessor ,
64 bit OS ,
16gb ram , 
3 GB DDR3 NVDIA Graphics. 
For the last three days i had been trying to install ubuntu 12.04 LTS , but have failed. 
What i have done is the below : 
Download the iso image from Ubuntu site : 
Run it through Daemon tools / Also did burn a image and ran it / Tried using the WUBI Installer too. 
Issues i am facing are : The Installation is proceeding but - at the end it is throwing the error : Unable to execute Grub - and terminating : 
I tried to run boot repair from the ubuntu site - ( downloaded it , burned an image , ran it / Also ran the live cd and opened a terminal and ran commands ) .. nothing successful. 
I tried to install ubuntu 9.10 instead then , but still it failed from the WUBI : some HTTP 404 Error . 

================================
I have ubuntu installed on my intel 32 bit os , along side windows , and it works fine. 

====================

So to summarize , i am not being able to install ubuntu 64bit , on my new system . 
Can someone tell me where i am going wrong , or what i need to do .. 

Thanks and Regards, 
Ritabrata Mukherjee 
[EMAIL="mukherjee.ritabrata84@gmail.com"][/EMAIL]

---

### Post by drs305 on 2012-06-17
Welcome to the Ubuntu Forums. Sorry about the installation troubles!

Even though Grub may not have installed the remainder of the installation may have succeeded. If you think it may be intact you could run the boot info script from within Boot Repair and post the link. We could then see if it might be salvagable.

By the way, I'd recommend editing your post and removing your email address. We aggressively try to eliminate spammers but your address is still vulnerable to being retrieved by people you won't want to hear from.

---

### Post by rito090884 on 2012-06-17
Just to add on this : 
I had installed Sun virtual box - and installed these images : they worked absolutely fine on it .

---

### Post by rito090884 on 2012-06-17
Done , removed the email address : 
I tried to update the boot loader and re run the grub , but still did not succeed. 
Here are the links for boot-loader issues : 

the first one : 
**[http://paste.ubuntu.com/1042248/](http://paste.ubuntu.com/1042248/)**


i sent out this to boot-repair.gmail.com , 
got a reply from yann to try it again - as he had updated the boot-repair. 
i did try but failed again : here is the link : 

http:/[/paste.ubuntu.com/1045002]("http://paste.ubuntu.com/1045002")

---

### Post by rito090884 on 2012-06-17
So to summarize what i have done is : 
For the 32 bit system : Windows 7 home premium
1: Installed Ubuntu 9.10 on a 32 bit system - worked fine.
==========================================================
For the 64 bit system : Windows 7 home premium
2: Tried to install the same on my Alienware m17x ( 64 bit os ) : HTTP 404 error. 
3: Tried to install the same on Sun Virtual box installed on windows  : Worked fine. 
4: Downloaded Ubuntu 9.10 x64 - tried to install using WUBI - HTTP 404 error. 
5: Downloaded Ubuntu 12.04 X64 - Tried to install - error - boot- loaded issue 
6: downloaded Boot-repair and burned on CD . Tried to repair - no good. 
7: Ubuntu X64 got installed correctly and worked fine on Sun Virtual box.

==================================================
for Boot Repair i followed instructions on this link : 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
====================================
Thanks and Regards,
Rito

---

### Post by LawM on 2012-06-17
Try re-installing the grub:

Step 1: boot from linux live CD
Step 2: open a terminal and see which one is your linux partition:
   fdisk -l -> look for the disk with the linux partition (in my case, /dev/sda5).
Step 3: mount your hdd:

   mount /dev/sda5 /mnt
   mount -o bind /proc /mnt/proc
   mount -o bind /dev /mnt/dev
   mount -o bind /sys /mnt/sys

Step 4: chroot in the mounted filesystem
   chroot /mnt /bin/bash
 Step 5: install grub
   grub-install /dev/sda

Step 6: reboot

If the OS was properly installed, that should do the trick, otherwise it's time to try something else.

---

### Post by rito090884 on 2012-06-18
Hi , 
This is what is happening : 
the 12.04 Installation is executing : Downloading and installing the languages : 
but its throwing error in executing grub : Unable to find boot loader .. 

i get three options : 
1: Select boot loader location 
2: Complete installation without boot-loader 
3: Terminate installation 
==========
Before proceeding on what you have suggested which option should i choose ? 

Thanks and Regards, 
Rito

---

### Post by UltimateCat on 2012-06-18
> **rito090884 said:**
> So to summarize what i have done is : 
For the 32 bit system : Windows 7 home premium
1: Installed Ubuntu 9.10 on a 32 bit system - worked fine.
==========================================================
For the 64 bit system : Windows 7 home premium
2: Tried to install the same on my Alienware m17x ( 64 bit os ) : HTTP 404 error. 
3: Tried to install the same on Sun Virtual box installed on windows  : Worked fine. 
4: Downloaded Ubuntu 9.10 x64 - tried to install using WUBI - HTTP 404 error. 
5: Downloaded Ubuntu 12.04 X64 - Tried to install - error - boot- loaded issue 
6: downloaded Boot-repair and burned on CD . Tried to repair - no good. 
7: Ubuntu X64 got installed correctly and worked fine on Sun Virtual box.

==================================================
for Boot Repair i followed instructions on this link : 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
====================================
Thanks and Regards,
Rito

I spoke with a certified computer tech last week and long story short he very strongly advised me not to install Ubuntu on the Alienware labtop.
He than said that Alienware is only for gaming.
I didn't question him further but I am curious why not-

---

### Post by Shadius on 2012-06-18
> **UltimateCat said:**
> He than said that Alienware is only for gaming.
I didn't question him further but I am curious why not-

I disagree that Alienware is *only* for gaming. That's like saying a certain brand of computer is only built for one purpose. :---) I would say that the statement made by that "computer tech" is full of crap and I'm sure that the owner of the Alienware doesn't *only* use his computer for gaming. :)

---

### Post by gnusci on 2012-06-18
Your system has nothing special. Did the LiveCD run well?

---

### Post by rito090884 on 2012-06-18
Yeah , live cd did work well , 
the only issue is , its not being able to find the boot-loader 
and throwing error unable to execute grub.. this comes at the end .. i will post a screen shot for the same later in the day .

---

### Post by drs305 on 2012-06-18
I have reviewed some notes that indicate the Alternate CD is needed for installing with RAID. The official  release notes also indicate this CD should be used for LVM and RAID setups.

[http://releases.ubuntu.com/precise/]("http://releases.ubuntu.com/precise/")

---

### Post by rito090884 on 2012-06-18
Hi all, 
Could nt believe but this is true - The checksums did not match  - 
all my partitions got corrupted , had to format the whole system through command line ( Nice learning by the way ) : 

Secondly i am reformatting windows now - next ubuntu - so lets hope this time works : And yeah i did download the alternate cd - and checksum matches .. so lets hope for the best .. 

Cheers 
Rito

---

### Post by rito090884 on 2012-06-18
Hi All, 
I have reformatted my system and downloaded the wubi installer.. * no images 
right now i am getting this error : 

06-18 23:15 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz, basename=ubuntu-12.04-wubi-amd64.tar.xz, length=512730488, text=None
06-18 23:17 DEBUG  downloader: download finished (read 27262976 bytes)
06-18 23:17 DEBUG  TaskList: ### Finished download
06-18 23:17 DEBUG  TaskList: ## Finished get_diskimage
06-18 23:17 DEBUG  TaskList: ## Running extract_diskimage...
06-18 23:17 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
06-18 23:17 DEBUG  TaskList: # Cancelling tasklist
06-18 23:17 DEBUG  TaskList: # Finished tasklist
06-18 23:17 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2

===== 
Any idea what can be turn around ?

---

### Post by Futurian on 2012-06-18
I wonder if it would work without WUBI. That is, use, for example, GParted to repartition the drive, creating a new empty partition. Then use the Ubuntu installer (not the WUBI installer) to install 12.04 onto the new empty partition.

But perhaps you don't want to risk the repartitioning, or have other reasons to avoid repartitioning. The WUBI should work.

Good luck anyway.

---

### Post by rito090884 on 2012-06-18
Hi All, 
Here is the latest update : 
I used WUBI to download Ubuntu 11.10 - Successful download . 
Also it allowed me to install inside windows for which i made a 30gb space allocation. 
I rebooted by system and do see ubuntu on dual boot option ( ready to install ). .. 
But once i select ubuntu it proceeds and then hangs... 

Currently , As suggested here i have given download for the alternate cds for ubuntu 12 and ubuntu 11 for both 32 bit and 64 on torrentz. 

===================

---

### Post by rito090884 on 2012-06-20
Hi all, 
No good news.. i had downloaded the ubuntu 12.04 X64 alternate cd 
Burned it to a disk and tried to install, . 
Went pretty good but again it failed at the boot loader. 
I did fdisk -l , got my linux partition and specifically tried to mention it , but still fatal error. 

I proceeded with " install without the boot loader , and installation succeeded. 
But when i rebooted , it again took me to the grub restore prompt , where i tried to bring back the windows boot.cfg , but everything failed again . Was not able to restart into windows 7 again. 
This is the 6th time i reformatted my 3 months old alienware .. 
Just a note - i tried to install the ubuntu 11.10 using ubi - it did get installed , also i can see the dual boot option , but when i tried to enter ubuntu it again prompts for grub .. 
=======================================================
As of now , i have given up hope on ubuntu 12.04 on my X64 . 
Will 11.10 i would say partial success as i could still boot into windows. 
===============================================
So what are your suggestions on this now : 
40 - Failed installations  from last friday 
10 : Reformatting of whole hdd. 
===================================
My main purpose is to install was7 on linux and work on it . so I choose ubuntu as it had never failed before . 
Is there anything to do with my HDD Partition type - its one single strip - RAID0.
====================================
Right now , as no other option is available i have installed vmware 8.0 , and would install ubuntu on it- and then was7 . tough one , but i was looking for a dual boot option as i am more into unix admin / was admin . 

=======================================

Please suggest :(

Thanks and Regards, 
Rito

---

### Post by rito090884 on 2012-06-20
Just found some links which i hope would be useful 

[http://askubuntu.com/questions/45038/dual-boot-ubuntu-11-04-vista-32-with-a-raid-0](http://askubuntu.com/questions/45038/dual-boot-ubuntu-11-04-vista-32-with-a-raid-0)

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

[https://bbs.archlinux.org/viewtopic.php?id=132809](https://bbs.archlinux.org/viewtopic.php?id=132809)
======================

The first link is the one which actually points to the issue i am facing .. 
Can someone help me out , on how do i proceed with the installation with reference to the 1st link :

---

### Post by Futurian on 2012-06-20
I wonder if running "boot-repair" [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) after installation but before trying to boot the new system would help.

---

### Post by rito090884 on 2012-06-20
Trial and Tested , 
This did not work... !!! 

i have the boot repair burned on a cd .. it has failed.

---

### Post by YannBuntu on 2012-06-21
> **rito090884 said:**
> i have the boot repair burned on a cd .. it has failed.

Please indicate the URL that appeared after using Boot-Repair's "Recommended repair".

---

### Post by rito090884 on 2012-06-23
Hi Everyone , 
Finally and i mean Finally its success.... 
I removed my two hard disks from Raid0 Partition , 
Reinstalled windows 7 , and then booted from the Ubuntu 12.04 from the alternate Cd 

And wow !!! all worked fine , and now i am working on dual booting ... !!!!! 

So , the issue was with my Raid0 and nothing else it seems... 


Thanks everyone for your posts , i learnt a lot ... :guitar:

---

### Post by Futurian on 2012-06-24
Congratulations, and your information will be helpful to others, including me. Thank you.

---

### Post by Futurian on 2012-06-25
Do you know whether or not the switchable graphics capability on your Alienware laptop works under Ubuntu? It would be nice if it did, so that the user could choose between battery life and graphics power based on what they were doing at the time.

Thanks.

---

### Post by rito090884 on 2012-06-27
Need to check on that .. 
well i installed ubuntu only for linux , and on top of that Websphere 7 ND ... 

Graphics - can u tell me how do i check that in ubuntu .. will do it and update .. 
and yeah , i believe this info of my ordeal on getting ubuntu on raid0 ( alienware ) is a really worthy one .. learnt a hell lot ..

---

