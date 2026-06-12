---
title: "Attempted Ubuntu-Windows Dual Boot. Now No Operating System Found"
date: 2020-04-11
forum: New to Ubuntu
---

### Post by fjwuserone on 2020-04-11
Hi,

I attempted to dual boot linux and windows on a brand new HP Spectre x360. I followed online instructions, created a new partition in windows, live installed from USB...all that good stuff. Everything seemed to be working well, I finished the ubuntu install and restarted which booted me directly into windows. Using some more online guides, I attempted to fix this by running the following command: ```
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
```

After running that command, I restarted and am now faced with "no operating system found" anytime I boot the computer. I've looked through various forums and tried a few things from a live usb install, but had no luck. At this point I'm in need of help as I'd rather not mess something up and create even more problems (like wiping windows if I haven't already).

Two things I've done since that point are:
1. Removed ubuntu from the boot order using efibootmgr. I now realize that probably didn't help but it currently looks like:
```
ubuntu@ubuntu:~$ efibootmgr
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0001,0002,0003
Boot0001* Windows Boot Manager
Boot0002* Internal Hard Disk
Boot0003* USB Drive (UEFI) -  USB DISK 2.0 PMAP

```

2. Attempted to use boot-repair. Unfortunately boot-repair didn't have any recommended instructions but I do have the diagnostic paste-bin - [http://paste.ubuntu.com/p/ZZh2jwd69b/](http://paste.ubuntu.com/p/ZZh2jwd69b/)

Any help is greatly appreciated, thanks.

---

### Post by oldfred on 2020-04-11
It looks like you still have drives set to RAID/Intel RST, not AHCI.
But for Windows to work you have to install the AHCI drivers first.
And in Windows make sure fast start up is off. 

A lot of HP 360 threads.
HP Spectre x360 Disable Optane (should use gpt to boot installer in UEFI mode, but MBR may work)
[https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume](https://askubuntu.com/questions/1204386/windows-10-wont-boot-after-dual-boot-installation-optane-volume)
HP X360 Update UEFI F20
[https://ubuntuforums.org/showthread.php?t=2439220](https://ubuntuforums.org/showthread.php?t=2439220)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477](https://bbs.archlinux.org/viewtopic.php?pid=1858477#p1858477)
HP Envy x360 with Core i5-10210U Intel UHD Graphics Hardware Acceleration 
[https://ubuntuforums.org/showthread.php?t=2432438](https://ubuntuforums.org/showthread.php?t=2432438)
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086)
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)

---

### Post by fjwuserone on 2020-04-11
Thanks for the links. The top one did the trick. I had to disable optane from bios

---

