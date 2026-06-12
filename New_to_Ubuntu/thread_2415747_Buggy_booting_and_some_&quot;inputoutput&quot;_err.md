---
title: "Buggy booting and some &quot;input/output&quot; errors"
date: 2019-03-30
forum: New to Ubuntu
---

### Post by vik99 on 2019-03-30
Hello everyone. 
I recently installed ubuntu and my booting is a little bugged. And for Ubuntu and for Windows when I am trying to boot into Ubuntu I am getting only a purple picture which stays about 30-40 seconds and then I can press left click and start using Ubuntu.
For windows, after choosing in Grub I am getting again a purple picture this time with some shreds like broken glass and the same story (just with ENTER or maybe the same way).
I have not posted the pictures because they're just purple .. :/
I was searching for some solutions they said just "sudo update-grub". And these are the errors I get after the command.

[https://ibb.co/Ks0FZRZ](https://ibb.co/Ks0FZRZ)

[IMG]https://ibb.co/Ks0FZRZ[/IMG]
[IMG]https://ibb.co/Ks0FZRZ[/IMG]
Sorry about bad English. :/
Thanks.

EDIT: Here is the summary report. [http://paste.ubuntu.com/p/dQndHYcs7z/](http://paste.ubuntu.com/p/dQndHYcs7z/)

---

### Post by Rubi1200 on 2019-04-01
Hi and welcome to the forums:-)

Please use a LiveCD/USB and then follow the instructions to create a summary report you can then paste here so we can see what is going on:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thanks.

---

### Post by vik99 on 2019-04-01
> **Rubi1200 said:**
> Hi and welcome to the forums:-)

Please use a LiveCD/USB and then follow the instructions to create a summary report you can then paste here so we can see what is going on:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thanks.

Thanks for letting me know what to do mate. I appreciate it. I just edited my post with the summary report , hope u will get something useful. :)

---

### Post by oldfred on 2019-04-01
Multiple errors I am not familiar with.
Have you updated UEFI/BIOS and SSD firmware to latest versions from vendor? Many have that issue.
Your flash drive shows 16.04.4, but install says newest 18.04.2. Best to use same version live installer to repair system or use your 18.04 installer.

What brand/model system? Latitude 6540 (from screenshot)
Confirm Secure boot is off, if you have that, as Boot-Repair just commented it could not tell.
Specs on line say that is i5-4310u, so it would be UEFI system. But Intel graphics should just work.

If you get grub menu, then grub is working and it is other boot issue. 
Are you able to boot recovery mode from grub menu?

You do have legacy/BIOS boot from MBR partitioned drive. Microsoft required vendors to install in UEFI mode on gpt partitioned drives since 2012, so most hardware now is UEFI. But users can install in the legacy BIOS/MBR mode.

But Windows 10 is not dual boot friendly with BIOS.
Grub only boots working Windows. And that means Windows cannot be hibernated. Windows fast start up sets hibernation flag, so grub then will not boot Windows. And then the only fix is to temporarily reinstall a Windows boot loader, fix Windows & then restore grub. 
With UEFI, all you have to do is in UEFI choose to one time boot Windows to fix it.

Windows will also turn fast start up back on with updates, so always have both a flash drive with Ubuntu live and a Windows 10 repair/recovery flash drive or installer with repair console.

---

### Post by vik99 on 2019-04-01
> **oldfred said:**
> Multiple errors I am not familiar with.
Have you updated UEFI/BIOS and SSD firmware to latest versions from vendor? Many have that issue.
Your flash drive shows 16.04.4, but install says newest 18.04.2. Best to use same version live installer to repair system or use your 18.04 installer.

What brand/model system? Latitude 6540 (from screenshot)
Confirm Secure boot is off, if you have that, as Boot-Repair just commented it could not tell.
Specs on line say that is i5-4310u, so it would be UEFI system. But Intel graphics should just work.

If you get grub menu, then grub is working and it is other boot issue. 
Are you able to boot recovery mode from grub menu?

You do have legacy/BIOS boot from MBR partitioned drive. Microsoft required vendors to install in UEFI mode on gpt partitioned drives since 2012, so most hardware now is UEFI. But users can install in the legacy BIOS/MBR mode.

But Windows 10 is not dual boot friendly with BIOS.
Grub only boots working Windows. And that means Windows cannot be hibernated. Windows fast start up sets hibernation flag, so grub then will not boot Windows. And then the only fix is to temporarily reinstall a Windows boot loader, fix Windows & then restore grub. 
With UEFI, all you have to do is in UEFI choose to one time boot Windows to fix it.

Windows will also turn fast start up back on with updates, so always have both a flash drive with Ubuntu live and a Windows 10 repair/recovery flash drive or installer with repair console.

Hello man, thanks for trying to help first.
Yes, some bios-update was available on Dell Site and I installed it. 


To mention too I recently(about 10 days) installed Windows 10 so 
I hope the Bios update is the latest.


On my disc is Ubuntu 16.04 , when I installed, ubuntu offered me to install the 
update 18.04 and I installed it.


Yes, its Dell Latitude E6540.
It's Intel i5-4210M 2.60GHz
, AMD Radeon 8790M, 
Intel HD 4600, 
256GB SSD.


Secure boot is off. In the boot setup, I saw some option to choose between Legacy
and UEFI boot and Legacy is chosen maybe that can be a problem?


I get the grub menu and its working fine until that, I can choose between Windows
and Ubuntu after I choose I got the problems. I can use and Windows and Ubuntu system but in the way I mentioned. 
Some clicks and enters on the just purple picture to get in the system...


Yeah, I am able to boot into recovery mode.


To add, when I was installing ubuntu I manually created the partitions, one EXT4 '/' and a swap. 
And I used about 30gb 2gb for swap and rest for that EXT4 '/'. 
What I see that I haven't done, people were using 3 disks One this "EXT4 /"
a swap one and the home one. 
Maybe I should reinstall Ubuntu with a home partition with chosen cursor on that home partition instead of "EXT4 '/'? 
Or maybe 30gb is too small?
I found on Dell site an Ubuntu 12.04 driver, should I install that too?
[https://imgur.com/98jYSfC](https://imgur.com/98jYSfC)
[IMG]https://imgur.com/98jYSfC[/IMG]

---

### Post by oldfred on 2019-04-01
Back with 12.04 I saw Dell had updated drivers as Sputnik. And then I saw where all the 12.04 drivers were included in 14.04LTS. So you should not install any drivers with your system. Only if a very new system and not installing newest Ubuntu may you need drivers.

Most with Dell have needed UEFI update and also the SSD firmware update.
And then drives all have to be AHCI, not RAID, nor Intel SRT in UEFI settings.

If you just installed Windows, you may want to consider reinstalling in UEFI boot mode.
How you boot install media UEFI or BIOS is then how it installs.  If your Dell came with Windows pre-installed it would have been UEFI and your Product key is in UEFI. If you install in BIOS mode, temporary key will expire and you have to purchase another one from Microsoft.
       Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)
[https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key)

I use 25 or 30GB for / (root) but have  a large data partition. Newer users find separate /home easier as that automatically mounts it, sets ownership and sets permissions. If you have data partitions using Linux formats you have to do all that manually. Not really difficult once you know how, but a lot for a new user.
 
Default new Ubuntu installs now just have / (root) as default. Swap is now a file, so swap partition not required. And if UEFI, then you also need an ESP - efi system partition, but if Windows in UEFI mode has an ESP, you do not create another one.

---

