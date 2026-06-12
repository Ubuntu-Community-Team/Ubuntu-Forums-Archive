---
title: "HP 250 G3 not booting on Ubuntu 12.04"
date: 2015-09-19
forum: New to Ubuntu
---

### Post by Lyta on 2015-09-19
Hi everyone,
 
I'm new to Linux and just installed Ubuntu 12.04 on a cheap HP laptop model (250 G3), after trying out the newest Ubuntu version, as well as various flavours of Linux Mint and Fedora. The computer has serious problems booting and shutting down with any Linux distro, but with Ubuntu 12.04 the problems seem to have been limited a little. Now the only problem is that the computer gets stuck on the booting screen - the one with the dots under the Ubuntu logo. I tried updating the system through the update manager, checking the BIOS options for Legacy and UEFI boot options (UEFI gets priority even with Legacy activated, and there's no way to change that). I installed Boot Repair, ran the diagnostics and repairs but the problem persists. I have to do a hard boot by shutting down the computer through the power button several times, before it can boot properly. I'm afraid if I keep this up the computer will be damaged. So I'm posting the Boot Repair generated file link here, in case someone can help me. I'm getting desperate and thinking of switching to Windows, even though I'd rather keep Linux and start learning the shell.

[http://paste.ubuntu.com/12479894/](http://paste.ubuntu.com/12479894/)

---

### Post by nknwn on 2015-09-19
The "Boot Repair generated file" says that the boot files are far away form the start of the disk - and that might cause problems or words to that effect. It suggests creating a boot partition with Gparted. However I would recommend using GParted to wipe your disk clean in preparation for installing Lubuntu which is a light weight and capable Linux - Just let Lubuntu installer arrange the partitions [http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)

---

### Post by grahammechanical on 2015-09-19
Boot Repair is an excellent utility but it only has the purpose of fixing boot loader problems. Problems that occur after the boot loader has passed control to the Linux kernel cannot be fixed by Boot Repair. Whether or not you should install Ubuntu or Lubuntu is irrelevent to this problem which will most likely be present with Lubuntu as it is with Ubuntu, Linux Mint and Fedora. Or do you see different problems with those other two Linux distributions?

Question: Did the Ubuntu live session load correctly? If the live session runs correctly and the installed restart fails in some way, then we must think about the differences between the live session and an installed session. And the difference? The live session does not use a proprietary video driver but an open source video driver. If when installing we tick the box "Install third party software" we get some proprietary audio and video codecs and a proprietary video driver. So, you could try installing by not ticking that box.

If the install restart gets to to a working Ubuntu desktop, then you can install those proprietary audio and video codecs by installing Ubuntu Restricted Extras from the Ubuntu Software Centre. And you can install a proprietary video driver from Additional Drivers if you think that is necessary.

Regards

P.S. You describe the HP 250 G3 as a cheap laptop. That may be so but I see nothing in the specification to indicate that you need to install Lubuntu instead of Ubuntu. In fact you might be better off installing Ubuntu 14.04. The support period is longer than 12.04 and the machine has plenty of RAM (4 GB)

---

### Post by nknwn on 2015-09-20
The reason I recommend Lubuntu is that it has a more up to date kernel than Ubuntu. I maybe should have recommended updating the kernel in Ubuntu instead but I wondered if the partition warning also had some bearing on the problem.

---

### Post by Lyta on 2015-09-20
In fact I installed and uninstalled 2 different flavours of Mint (Rebecca and Rafaela), the latest Ubuntu (Trusty Tahr 14.04) and one flavour of Fedora. I saw the same problems in booting (the computer got stuck on the logo screen), only with those distros there were also problems during reboot, logoff and shutdown. I had to use the su command to shut the computer down from the terminal. That only worked occasionally, other times I had to do a hard shutdown through the power button. 

What you say about the video drivers might be right, as I didn't see any problems during the live sessions. The problems in all distros and flavours started when I actually installed the OS. I'm not doing a dual boot and the hard drive doesn't have any partitions that I intentionally created. The computer came with DOS and I just installed Linux on it. I thought about a lighter version like Lubuntu, but since the computer is brand new - I bought it 10 days ago and still struggling with finding a functional Linux distro for it - and as you say has plenty of RAM, I didn't see the need to use Lubuntu or similar. I'll try your suggestion, to re-install Ubuntu with the third party software button unchecked, and log back in here to report on the results. One question though: if I install the proprietary drivers through the software center, won't the booting problem return since they're back in the system?

Thanks very much for your reply :)

---

### Post by Lyta on 2015-09-20
Graham: In fact I installed and uninstalled 2 different flavours of Mint (Rebecca and Rafaela), the latest Ubuntu (Trusty Tahr 14.04) and one flavour of Fedora. I saw the same problems in booting (the computer got stuck on the logo screen), only with those distros there were also problems during reboot, logoff and shutdown. I had to use the su command to shut the computer down from the terminal. That only worked occasionally, other times I had to do a hard shutdown through the power button. 

What you say about the video drivers might be right, as I didn't see any problems during the live sessions. The problems in all distros and flavours started when I actually installed the OS. I'm not doing a dual boot and the hard drive doesn't have any partitions that I intentionally created. The computer came with DOS and I just installed Linux on it. I thought about a lighter version like Lubuntu, but since the computer is brand new - I bought it 10 days ago and still struggling with finding a functional Linux distro for it - and as you say has plenty of RAM, I didn't see the need to use Lubuntu or similar. I'll try your suggestion, to re-install Ubuntu with the third party software button unchecked, and log back in here to report on the results. One question though: if I install the proprietary drivers through the software center, won't the booting problem return since they're back in the system?

Thanks very much for your reply :)

nknwn: I took note of that paragraph too, downloaded and installed the gparted package, but when I ran the program I didn't understand much. I'm not good with partitions. There was only one disk available, since I'm not dual-booting anyway, and in the program Help it says that if it's the main disk being used, they don't make it editable for safety reasons or something. Either I didn't get something right - very likely - or I can't make the partition as per the instructions. Also, how do I update the Ubuntu kernel? Sorry for sounding such a newb.

---

### Post by nknwn on 2015-09-20
When I installed Ubuntu 14.04 recently it arranged the partitions automatically before installing . To be able to resize/move/delete partitions with Gparted the partitions must not be in use. It should be run from a live disk in your case. So I'd say you should go ahead and install Ubuntu again following Graham's advice. Then if necessary I'll post a bit about updating the Kernel. :)

---

### Post by Lyta on 2015-09-26
Sorry for the late reply, I was swamped with work stuff. I re-installed Ubuntu 12.04 following Graham's advice and disabling proprietary software. Then installed the Boot Repair ppa and ran the diagnostics again. It asked me to purge the grub and re-install it. After doing that the problem seems to have been solved for now. The computer is booting properly with no delays, and logoff/ shutdown/ reboot is also smooth. So for the time being it seems that was the problem, tnx guys!

---

### Post by Lyta on 2015-10-01
Unfortunately the problem re-appeared, today I had to do 15 (!!) hard shutdowns to be able to get into the system, even in safe recovery mode. There are some mentions of solving UEFI problems in this thread, can anyone point me to the right direction? Is there anything useful in there? I'm thinking perhaps the advice of creating a 300MB grub partition. Perhaps the system needs to have partitions to read from, as mentioned in the thread linked below. So how do I create a grub partition through gparted?
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by nknwn on 2015-10-01
Run:
[B]lsmod | grep video
[/B]..in the Terminal - Paste here. This should tell us which video driver is in use.

Also Run:
[B]sudo parted -l
[/B]Paste the results here(in between code tags to make it easier to read - Code tags are available in the Advanced edit feature of this forum)


How well is your computer running otherwise? Is it sometimes locking up? I'm wondering if your Hard drive might be failing, It can take a long time and a lot of frustration before the disk finally gives up.

---

### Post by Lyta on 2015-10-02
The computer is new, I bought it about 3 weeks ago and everything seems to be running fine, hardware-wise. I haven't even had time to use it properly for my studies, which was the initial purpose, due to my struggles with Linux boot process. All I seem to do is try to make Linux work, lol! Latest update on my case:
Running ubuntu from a usb stick, I used gparted to create a 1GB partition at the beginning of the disk, and then tried to assign that partition as the one where the computer boots from, using this tutorial: [https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)
But according to the instructions generated in Boot Repair, my computer boots from an EFI file, and the boot partition had to be in FAT32 format instead of ext4, which is recommended in most threads and tutorials around the net. I did that and followed the steps in Boot Repair, then I booted my computer properly from the hard drive and entered the BIOS. I switched the boot options from Windows to Ubuntu, and kept hitting enter on that option until I reached the final subdirectory, and chose the grub file. I saved and exited. After that there was a screen asking me which mode I wanted to boot in - normal mode, recovery mode etc. I chose normal mode and the computer booted without any issues. Tried it a couple times more and no issues so far. Now that the boot sector is at the beginning of the disk and in the correct format, perhaps the problem will be solved? Fingers crossed. Here are the results from the commands you asked me to run.

```
sudo parted -lModel: ATA WDC WD5000LPVX-6 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 3      1049kB  1050MB  1049MB  primary   fat32           boot
 1      1050MB  496GB   495GB   primary   ext4
 2      496GB   500GB   4180MB  extended
 5      496GB   500GB   4180MB  logical   linux-swap(v1)

```

```
lsmod|grep video
uvcvideo               82247  0 
videobuf2_core         40972  1 uvcvideo
videodev              139761  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
video                  19914  1 i915_bdw
```

---

### Post by Lyta on 2015-10-02
Now I have this problem: [http://ubuntuforums.org/showthread.php?t=1965810](http://ubuntuforums.org/showthread.php?t=1965810)
The hard drive makes this weird beeping sound before booting. And I need to go through the same process I described above in the BIOS to boot the OS. I'm going to try one last time to fix it, and if I can't I'll install Windows again, and maybe learn how to use Linux from a live usb drive first. Otherwise I don't see the computer surviving for long.

---

### Post by nknwn on 2015-10-03
Is this Bios designed specifically to prevent booting anything other than Windows from the internal hard drive....? It seems like it.
In one of the pages you linked there is a section titled: [B]Systems that only boot Windows from UEFI. [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
[/B]where it says : [B]A: Manually rename files efi hard drive boot files in efi partition /EFI/Boot

[/B]It may or may not work but for me it's a hack too far anyway as it would likely be messed up in a future system upgrade.

Booting an external drive with Ubuntu might indeed be your best option on that laptop. That is how I choose to run Ubuntu. I have considered dual boot with Windows 8 but I don't trust the boot process not to become messed up at some point. Or even immediately. :)

---

### Post by Lyta on 2015-10-05
I suspect so, perhaps the vendor uninstalled Windows while maintaining the BIOS settings for them? Dunno. I installed Windows anyway, because after so many hard boots and shutdowns I ran the risk of frying the motherboard or hard drive. I am now running Ubuntu from a usb drive, learning the shell from there. Perhaps when I know more about Linux and have become more of an 'expert' in the subject I might install it on a new machine and start doing stuff with it. For the time being the usb drive will have to suffice - perhaps even an old desktop I have here. It's weird because on an Acer Aspire One netbook I have, Ubuntu runs like a charm. I installed it and after that it never bothered me again. So it must be the computer's BIOS.

---

