---
title: "New to Ubuntu, have questions about installing alongside Win8"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by lerxs on 2012-12-02
I have always been intrigued with Linux, but have never decided to try it until now.
I currently have an HP 2000-bf69WM Windows 8 laptop, that I want to install Ubuntu on.

I have read of problems with UEFI and Secure Boot, and i'm not sure if my installation will be successful. Can I expect issues? Would I be able to use the Windows installer on the website? Has anyone had experience with this particular machine?

---

### Post by oldfred on 2012-12-02
Welcome to the forums.

It does vary by Vendor and model. Is this a system with the small SSD or Intel SRT? That adds complications.

Some have installed without issue, others had issues and some will not work at all. You will need to download Boot-Repair or manually update the grub menu entry for Windows. It still creates a BIOS type entry. You can manually correct it but it is just easier to use Boot-Repair and it will create the correct chain load entry for Windows efi boot.

Does not work, currrently:
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)

    I have not seen your specific model.

Some have installed with secure boot on. Others have had to turn it off. Ubuntu 12.10 64 bit with grub2 2.00 has the updates to work with secure boot. 
       [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell]("https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell")

    Some other models that have worked.
       Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)
Acer V5-571P-6815 secure boot off worked
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Windows 8 & Ubuntu [  ASUS K55A 
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by black veils on 2012-12-03
also its an HP, so probably has all 4 primary partitions used, which needs to be dealt with, before you can install another operating system.

---

### Post by YannBuntu on 2012-12-03
> **black veils said:**
> also its an HP, so probably has all 4 primary partitions used, which needs to be dealt with, before you can install another operating system.

No, with Windows8 there is UEFI/SecureBoot, so always GPT disk (which don't have the 4 primary limit).

---

### Post by black veils on 2012-12-03
> **YannBuntu said:**
> No, with Windows8 there is UEFI/SecureBoot, so always GPT disk (which don't have the 4 primary limit).

haha yes i forgot that.

---

### Post by lerxs on 2012-12-03
> **oldfred said:**
> 
Is this a system with the small SSD or Intel SRT? That adds complications.


I believe it's just a SATA HDD, i'm not that familiar with SRT, so forgive me for that.
There are alot of things I haven't kept up with over the years.
Thank you for taking the time to post those resources, i've read most of them already.

While i'm confident in my skills and knowledge of computers, i'm still afraid i'll screw something up. :/ I may need step by step instructions at this point. Or I may wait until I have another machine to dedicate to linux, as I don't want to install it on my Win 7 desktop. The only option right now is this laptop, but I would like to keep Win8.

Here is a screenshot of my disk, for the above users.
 [[IMG]http://i.imgur.com/UQaBV.png[/IMG]](http://imgur.com/UQaBV)

---

### Post by oldfred on 2012-12-03
If it had the Intel SRT you would see a small 16 or 32GB SSD drive. 

Since it is UEFI and then gpt partitioning, you should just be able to shrink Windows and create Linux partitions. Use Windows to shrink itself and reboot as it wants to update its new size with chkdsk or other fixes. But do not create partitions with Windows. Use gparted or the installer to create new partitions.

With Windows 8, it really is important to create another NTFS shared data partition, so you do not write into the Windows 8 partition.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)


Ubuntu 64 bit 12.10 should install whether secure boot is on or off. But it does not create a correct grub menu chain load item to Windows. So ignore those and use Boot-Repair to add a correct efi chain load entry.

---

