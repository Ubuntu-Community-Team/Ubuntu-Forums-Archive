---
title: "Ubuntu on second hard drive"
date: 2019-03-07
forum: New to Ubuntu
---

### Post by name7891 on 2019-03-07
Greetings community,

I would like to install Ubuntu on a separate HDD because in some cases it is possible that windows/linux tries sometimes to overwrite in some cases the boot loader I would like to know how to do it to be sure to have two working operating systems in the end and which operating system I boot will be decided by boot order -> choosing boot device at startup. (On my primary HDD is a Win10 installed)

The SSD contains the W10 and it is using the old MBR in case it matters. The HDD I plan to install Ubuntu on provides a 300 GB partition. I will not need to provide a swap (will use a swap file in case I need to - 32 GB RAM) and I also don't plan to separate /home, / and /boot.


Thank you very much in advance.

---

### Post by jdeca57 on 2019-03-07
It is possible to install Ubuntu on an external drive. And the boot order will allow you to choose that external installation. I've done that. But in my experience it's been to much of an hassle and I don't recommend ir. I fail to find a question in your post. If you were asking can it be done then the answer is yes.

---

### Post by name7891 on 2019-03-07
The question is how can it be done - but maybe not on an external drive but an internal one (a different one then the one W10 is running on - like I wrote in the first post) - how can I be 100% sure that linux doesn't make my windows boot loader/hook whatever thing unavailable?

---

### Post by oldfred on 2019-03-07
If Windows is BIOS/MBR, better to install Ubuntu in BIOS, but they you have a choice of 35 year old MBR or newer gpt partitioning. 
Ubuntu will boot in either BIOS or UEFI mode from gpt if you have correctly supporting partitions. If you use gpt now and include both the ESP  for future UEFI and bios_grub for current install in BIOS mode you have configured it for future use. If just MBR and then you want to use drive with new UEFI system, you will have ot convert to gpt and that may erase drive and full backup required.
With MBR you also have the 4 primary partition limit. Best to install Ubuntu into a logical partition. 

Often best to just disconnect Windows drive to avoid confusion. You can partition in advance, but only really need / (root) as ext4 if BIOS. If UEFI then you also need an ESP (FAT32). All other partitions are optional.

Whether you partition in advance or partition while installing, be sure to choose to install boot loader to same drive as you are installing Ubuntu. If you did not disconnect Windows drive, then drive may be sdb or another drive, and you need to install grub to that same drive.

       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
    
Older versions, but process is the same and screens have only changed slightly.
               And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions.

---

### Post by jdeca57 on 2019-03-08
> **name7891 said:**
> The question is how can it be done - but maybe not on an external drive but an internal one (a different one then the one W10 is running on - like I wrote in the first post) - how can I be 100% sure that linux doesn't make my windows boot loader/hook whatever thing unavailable?
That last question can be answered from the Windows side: you can always restore the Windows boot, it's a matter of using a boot disk and the instructions are found on the internet. The problem would then be that you don't see the Linux partition any more but if you install on a different disk there is zero chance of losing Windows. You may have to boot the rescue disk and that's it. Actually that advice is correct even with an internal disk separate from the Windows disk.

---

### Post by name7891 on 2019-03-10
Thanks so far for your help, wasn't sure how "automatic" all this accessibility functions in ubuntu are. But you can pretty much decide for yourself where to put the bootloader.
I installed Ubuntu today three times twice on the internal HDD and once on an ssd connected via usb3 all installations could be started after installation but none was actually usable. When I start ubuntu from my bootable usb stick it was perfectly fine, fluently running. When I started the installed versions, they were so slow that I had a lot of problems navigating the mouse to the login field. After I typed a letter I had to wait for 2 seconds until it appeared and when I managed to finish to put my password into the field, Ubuntu tried to initialise the user session and returned without error to the login-screen. At first I would like to fix the responsiveness of the system. 

How can it be done?

(My system is with 32 GB DDR4 Ram and a i7-8700k and a 1080ti should be capable of running an ubuntu os)

---

### Post by oldfred on 2019-03-10
With the nVidia card you need nomodeset boot parameter until you install the nVidia driver from Ubuntu repository.
Have you installed that?

Something really wrong that it is that slow.
What motherboard?

Can you boot recovery mode and is that better, it automatically uses nomodeset.

---

### Post by name7891 on 2019-03-10
My motherboard is the ASRock Z370 Extreme4. During installation I allowed ubuntu to pull all necessary (even third party) packages thought that it maybe grabs some of the necessary drivers. Will try the recovery thing tomorrow. After installation I am not able to install anything anymore. If the installation would be less complicated - with a shell and with the good old chroot to install necessary packages.

---

### Post by oldfred on 2019-03-10
With that new of a system, you really should be using UEFI with gpt partitioning.

If you can boot recovery mode you are at terminal and can install (if Internet enabled) or run repairs before mounting system.
You can always chroot from live installer.

Microsoft in 2012 required vendors to install in UEFI mode on gpt drives with release of Windows 8. Faster booting & UEFI Secure Boot. And gpt has various redundancies that MBR does not have.

---

### Post by name7891 on 2019-03-11
I switched my windows system to uefi and reinstalled ubuntu using gpt  and uefi - now everything works, seems like mbr is not that well  supported anymore.

---

### Post by hypotoad on 2019-03-11
I have a desktop with Win 10 and two hard drives, a week ago I just unplugged the first drive with Win 10 and installed Ubuntu 18.04 LTS on the second drive, then plugged the first drive back in. Now when I boot the computer I press F10 for the boot menu and can either boot Win 10 or Ubuntu. If I do nothing Win 10 boots. Works like a charm.

---

### Post by rbr1227 on 2019-03-13
After previous failed attempts at dual-booting, I finally implemented a mobile rack setup in my desktop to switch between Ubuntu and Windows hard drives. Documents I want to share between the systems are installed on a third drive that is always connected. I have been using this setup for years and it always works great.

---

### Post by monkeybrain20122 on 2019-03-13
I  set up something like that for my boss a few months ago on a high end machine, Win10 came with machine, and I installed Ubuntu in an external ssd. I had to disable fast boot in bios and did something (I forgot what) to boot it off. Actually I installed Ubuntu on the external hd using my own machine but since the graphic cards use the same driver that was no issues to work off his once the boot issue was solved. 

It used to be very easy, but with laptops now you may have to jump through some hoops because of secure boot and uefi, it depends on the model and the hardware.

---

