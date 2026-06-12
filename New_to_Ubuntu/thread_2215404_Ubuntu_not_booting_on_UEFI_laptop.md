---
title: "Ubuntu not booting on UEFI laptop"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by nnvt on 2014-04-06
Hey guys i'm having some issues with getting my ubuntu installation up and running.

this is what I do:

Install ubuntu to /dev/sda5 while formatting it and changing the mount point to / 

after that I boot into the recovery mode to fix my amd radeon driver

then I reboot and this is where it happens it doesn't boot! (well sometimes it does and then it works really well but as soon as I change something in the BIOS or even open it it will stop booting and requires a reinstall) it goes to the ubuntu logo and it loads one dot then all dots are colored and then the computer reboots into windows 8.1 I tried to show the log by pressing one of the arrow keys but the screen went black (sometimes it briefly shows the log and it shows that it is stopping all the services)

I had to reinstall ubuntu over 15 times today because it barely works!

my computer: HP pavilion 17 e177-sb
amd APU a10-4600m
amd radeon graphics
insyde F.31 as UEFI BIOS
ubuntu version 13.10
Legacy support is turned on
secure boot is turned off
virtualization technology is turned on
partition table is GPT
windows version: Windows 8.1

I hope someone can help me with this or at least show me whats wrong (i'm pretty sure the amd driver has nothing to do with it because when ubuntu boots it works just fine) 

thanks,

nnvt

---

### Post by nnvt on 2014-04-07
Can anyone please help me??!! 

Everytime I open my BIOS (insyde F.31) then it's bye bye ubuntu and it will no longer boot even if I don't change anything in the BIOS

---

### Post by nnvt on 2014-04-07
Problem solved: installed linux mint and it works now even with secure boot on

conclusion: Ubuntu absolutely hates UEFI!!

---

### Post by mastablasta on 2014-04-07
> **nnvt said:**
> after that I boot into the recovery mode to fix my amd radeon driver



why in recovery mode? how did you "fix" it? do you use AMD proprietary drivers? since you have A10 APU would you be willing to try out the 14.04 beta (suitable for intermediate users)?

when you managed to boot check the system logs. especialy boot logs.

if you think it's not driver boot into live session and use boot info script in boot repair tool. that should give us some clue as to what is happening pon boot.

edit: mint is Ubuntu with cinnamon interface, a few extra or different utilities and a few tweaks.

---

### Post by nnvt on 2014-04-07
I'll try that thanks for replying! well I put my AMD radeon drivers onto a external HDD boot in to recovery mode then drop down to root and remount my hdd as rw then i mount mye external hdd to /media and cd to the driver folder and do sudo ./amd... and I can install the driver! 

i'll try the 14.04 beta

---

### Post by nnvt on 2014-04-08
That version is having the same issue and now i'm having some issues with mint and grub too :/ I get grub install failed! I had to use boot-repair a few times to get it fixed and now mint is having the exact same issue as ubuntu I don't know what's wrong with this laptop

---

### Post by mastablasta on 2014-04-08
have you tried any of the boot options on boot?: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

also drivers are not supposed to be installed in recovery mode i believe. 

be sure to also read this regarding Ubuntu and UEFI: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2014-04-08
Do you have fast boot or always on hiberantion off in Windows.

Also Windows updates UEFI to make Windows default if you do any system things, so it will keep trying to be default.

With 8.1 there is a bug in grub that with secure boot on you cannot boot Windows from grub menu.
       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464"]https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464

[/URL]
 Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[URL="https://coderwall.com/p/vfyqkg"]https://coderwall.com/p/vfyqkg

      [/URL]
 Another possible work around. HP Pavalion G7
[http://ubuntuforums.org/showthread.php?t=2112273](http://ubuntuforums.org/showthread.php?t=2112273)

    [URL="https://coderwall.com/p/vfyqkg"]
[/URL]

[URL="https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464"]
[/URL]

---

### Post by nnvt on 2014-04-08
I formatted my linux partition as EXT3 instead of EXT4 with os-uninstaller and so far ubuntu is working properly even after opening my BIOS let's hope it stays that way

---

### Post by nnvt on 2014-04-09
Having issues again so I decided to install fgrlx and fglrx-amcccle and that succeeded then I did amdconfig --adapter=all --initial because I have dual graphics (A10-4600m) and now my system boots every time but the Xserver fails to start with an error undefined symbol: ukiOpen (I currently have mint installed but I assume this would be the same for Ubuntu)

---

### Post by mastablasta on 2014-04-09
what is the second GPU?

A10-4600m is supported and even certified (_[COLOR=#810081][http://www.ubuntu.com/certification/hardware/201204-10860/](http://www.ubuntu.com/certification/hardware/201204-10860/)[/COLOR]_) to work well in Ubuntu. so it is a bit strange the trouble you are having.

[http://askubuntu.com/questions/166538/problems-with-ubuntu-and-amd-a10-4655m-apu](http://askubuntu.com/questions/166538/problems-with-ubuntu-and-amd-a10-4655m-apu)

what version of Ubuntu/Mint are you trying to install? there were some bugs in older kernels with this chip.
uname -a 

to get the info.

---

### Post by nnvt on 2014-04-09
My second GPU is a Radeon HD 8670M and i'm trying to install Mint 16/ubuntu 14.04 and ubuntu 13.10 and all are having this issue I currently disabled fast startup from windows 8 and i'm gonna try again.


EDIT: so I tried installing it again and I assumed wrong the fglrx and fglrx-amdcccle packages DO work in Ubuntu and I currently have Ubuntu 14.04 up and running i'm still facing some performance issues but I hope it doesn't break again :D

---

### Post by mastablasta on 2014-04-09
check performance in terminal using to or htop commands (htop needs to be installed). you can hopefully pin down the process that is causing the performance issue.

---

### Post by nnvt on 2014-04-09
My sound is a bit choppy and when playing games or using flash the frames aren't really smooth


HTOP says that chromium-browser is using about 99% of the cpu :o


EDIT: it stopped booting again this morning even tho I was playing minecraft and it was all running smooth yesterday evening but I got it booting by using the "resume" option in recovery!

EDIT2: now I found out it boots sometimes and sometimes it doesn't it doesn't make any sense

EDIT3: I think I found the problem; the kernel I tried booting with kernel 3.13.0-19 instead of 3.13.0-23 and it boots fine

EDIT4: it seems to be the xserver instead whenever I try to do amdconfig --adapter=all --initial (which is neccesary for the amd drivers) it stops booting, if I restore the original file it boots up again!

---

