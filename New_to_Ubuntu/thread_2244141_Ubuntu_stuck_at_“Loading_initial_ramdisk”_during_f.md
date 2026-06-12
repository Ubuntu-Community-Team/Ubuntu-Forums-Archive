---
title: "Ubuntu stuck at “Loading initial ramdisk” during first boot"
date: 2014-09-14
forum: New to Ubuntu
---

### Post by Foxcraz on 2014-09-14
My Ubuntu 14.04.1 (3.13.0-32-generic) seems to not boot right after a fresh install from a Live DVD (tried it multiple times and also from a bootable USB stick as well).

Boot repair info: [http://paste.ubuntu.com/8328560/](http://paste.ubuntu.com/8328560/)
Graphics card info:
ubuntu@ubuntu:~$ lspci -nnk | grep -iA3 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8650G] [1002:990b]
    Subsystem: Lenovo Device [17aa:397c]
    Kernel driver in use: radeon
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller [1002:9902]

My laptop is a Lenovo G505s.

I tried following the information on [My computer boots to a black screen, what options do I have to fix it?]("http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it"), but that didn't help. To be more specific I tried the following recommendations: 1) Replaced "quiet splash" with "no splash" 2) Replaced "quite splash" with "nomodeset" 3) Replaced "quite splash" with "radeon.modeset=0". The first two options doesn't get to the loading initial ramdisk message (it is stuck post the loading linux message). The last option gets stuck after the loading initial ramdisk message (the same issue I face without editing the boot command list).

Let me know how to proceed with fixing this problem.[/FONT][/COLOR]
Btw, I tried installing Ubuntu in the UEFI mode and that installed and booted with no issues. Unfortunately I need to have Ubuntu work in the Legacy mode (non-UEFI) since I have to dual boot this with another OS that doesn't work in UEFI mode. Anyways, I am stuck right now even in trying to get a normal Ubuntu only installation in the Legacy mode, though the LiveDVD mode works fine.

[Crossposting from AskUbuntu, since I got no reply there]

---

