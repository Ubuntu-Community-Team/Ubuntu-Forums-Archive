---
title: "Install ubuntu 12.10 and windows 8 issues"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by mna0307 on 2013-04-14
Hey there...i have tried all the posts but was unable to get any help...i want to install ubuntu12.10 on my windows 8 64 bit system...i used a desktop version of it..ubuntu-12.10-desktop-amd64...i installed it using a bootable pen drive...it didnt detect windows 8...still i installed it successfully creation partitions by my own...

after successful installation on reboot it does not show any option to choose windows or ubuntu..it just boots windows...tried everything wasnt able to fix it..

next i downloaded vmware...and tried using ubuntu by creating a virtual platform...now this worked..but had some problems...it should not differ from the ubuntu tht i had got if the grub had detected ubuntu...as soon as i start my virtual ubuntu created using vmware...i get a terminal immediately without my asking it to do so...and the background is changed...it is not like ubuntu bt different....

my problem is tht when i try to install g++ or emacs using sudo apt-get install g++/emacs...it displays an error saying tht the file is not present there and cud be present in any of the listed packages...now when i try installing those packages...it says tht g++ is not present in these packages...what should i do..can u please help me out??? i m a beginner in ubuntu and get disheartened when all my efforts on ubuntu turn up to be a failure..please suggest sumthing..

---

### Post by JohnDillinger43 on 2013-04-14
Don't know if you've tried any of these: [http://askubuntu.com/questions/225028/dual-boot-windows-8-with-ubuntu-12-10](http://askubuntu.com/questions/225028/dual-boot-windows-8-with-ubuntu-12-10)

---

### Post by wildmanne39 on 2013-04-14
I changed the title to be more descriptive so you can get the help you need.

---

### Post by mna0307 on 2013-04-14
I tried this but on my system even when secure boot i off..windows 8 shows up..there is no sign of ubuntu even after it being perfectly installed..

---

### Post by JohnDillinger43 on 2013-04-14
The problem is almost certainly with the GRUB bootloader.  Typically with a dual boot installation you set it up to load GRUB first, to give you the option of booting to either Ubuntu or Windows.  In your case it sounds like something went wrong so that the Windows bootloader runs first, which means you never get the chance to select Ubuntu.  Could you give a little more information about your partitioning scheme?  Are Ubuntu and Windows on the same drive?  I haven't used Windows 8, but I know Win7 uses the first three partitions for various things, so when I added Ubuntu to my laptop I did an extended partition and put Ubuntu there.

---

### Post by mna0307 on 2013-04-14
> **JohnDillinger43 said:**
> The problem is almost certainly with the GRUB bootloader.  Typically with a dual boot installation you set it up to load GRUB first, to give you the option of booting to either Ubuntu or Windows.  In your case it sounds like something went wrong so that the Windows bootloader runs first, which means you never get the chance to select Ubuntu.  Could you give a little more information about your partitioning scheme?  Are Ubuntu and Windows on the same drive?  I haven't used Windows 8, but I know Win7 uses the first three partitions for various things, so when I added Ubuntu to my laptop I did an extended partition and put Ubuntu there.


on installing ubuntu it doesnot detect windows 8...so  dont get to know in which drive windows 8 is..so i abondon the installation go to windows 8 free some space...restart the installation and create partitions from the free space...ext4 and swap format...

---

### Post by JohnDillinger43 on 2013-04-14
Okay -- so it sounds like you have them on the same drive?  What partitions did you do for Ubuntu?  For instance, I have separate boot, swap, root, and home partitions, but not all of those are required.  Also relevant is where you installed the bootloader.  This is something it asks you during the installation.  People have various opinions on whether it should be installed on a drive or a partition; I usually do it on the drive rather than a specific partition.  I would think that if you installed it on one of your Ubuntu partitions that might be why you're not getting a menu: the BIOS is running the first bootloader it finds, which is probably the Windows bootloader in your first partition (which would be labeled sda1 by Ubuntu).

Probably what you'll have to do is boot from your USB drive and edit your GRUB menu from there.  It's theoretically possible to edit GRUB from Windows, but I wouldn't recommend it.  Once you're booted in an Ubuntu environment it'll be much easier to find your GRUB menu and tweak it so that you get it every time you boot.  There's a great tutorial on GRUB here: [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html).  One thing I would try to avoid is manually editing the grub.conf file in your boot partition.  Newer versions of Ubuntu are usually set up to automatically edit this file based on high-level input from the user, so manually editing it can mess stuff up if you don't know exactly what you're doing.

---

### Post by oldfred on 2013-04-14
Was this Windows 8 that you installed or a system with it pre-installed?
May be best to see all the details.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

