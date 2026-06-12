---
title: "Boot repair"
date: 2015-05-28
forum: New to Ubuntu
---

### Post by michael_young5 on 2015-05-28
Hi,

I am a beginner to using Ubuntu. I need to learn ROS which require me to install Ubuntu 14.04 in my Acer laptop pre-installed Windows 8.1. I made a Ubuntu liveUSB, installed it by shrinking win disk and partitioning the free space following tutorial at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI). However, after installation the Grub2 was not launched, it directly went into windows. I then follow the instructions on the above same link using boot repair to fix this issue, but it seems not working as no boot menu was shown allowing me to choose OS. Before installing I already disabled win fast mode and secure boot. After running boot repair following instructions in the above website I also ran a command in windows admin mode: bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi. 

I find I cannot do anything except for seeking help here. The URL after I ran boot repair in try uBuntu is: [http://paste.ubuntu.com/11411561/](http://paste.ubuntu.com/11411561/) . Thanks for any ideas you might have about this case.

Michael

---

### Post by oldfred on 2015-05-28
Several with Acer said they had to add a password to enable some settings that then allowed them to set Ubuntu as default boot.

 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

---

### Post by michael_young5 on 2015-05-28
Dear OldFred,

Thanks for prompt reply. My laptop is Acer V3 112P.

I tried the first link, walked through it's steps but still I got into Windows after reboot.

The second link seems not about my specific question. I will follow your third link, which has a fairly long text.

In addition, I just checked my paste information (see the second link in my starting post), in the first several lines it says Linux bootloader in not in MBR of sda but in sdb1, which is my USB pen drive. Is it the reason that I cannot get Grub2? How to set the bootloader  to the correct place? 

Michael

---

### Post by oldfred on 2015-05-28
This is your sda2 or your ESP - efi system partition.
And it shows the Ubuntu boot files as well as Windows.

>      Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/MokManager.efi /EFI/[COLOR=#ff0000]ubuntu[/COLOR]/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 



With UEFI you do not have boot loader in gpt partitioned drive's protective MBR.
The boot loader in sdb, is for the live installer which can be booted with BIOS from MBR, or with UEFI from its own /EFI/Boot folder.

Did you enable trust as mentioned in one thread. I have seem many other Acer various models with same configuration where you have to specifically allow Ubuntu to boot.

Even though different model, same issue:
[http://ubuntuforums.org/showthread.php?t=2253311&p=13180374#post13180374](http://ubuntuforums.org/showthread.php?t=2253311&p=13180374#post13180374)

---

