---
title: "HP Notebook having problems booting into ANY LINUX..."
date: 2014-05-06
forum: New to Ubuntu
---

### Post by ovingiv on 2014-05-06
Afternoon from WI... I have been having problems installing any form of linux onto a HP Notebook 2000 2d19wm. It has a AMD E-300 APU with Radeon HD Graphics running 1.3 GHz. 
(Full specs on bottom of post)

I have tried
Kali
Ubuntu 10.10, 11.10, 12.04 LTS, 13.04 LTS.
BackTrack 4, 5
xUbuntu
kUbuntu

They all seem to freeze after the bootloader (from what the distro came with). 

When I run a Live CD, it works all fine. Wi-Fi, ethernet, usbs, camera, mic, jacks, speakers, HDMI, vga, SD card slot.

The system originally came with Windows 8. Any help would be great.
P.S. I would like to use Kali if possible

..Specs..

Windows    Windows Version 6.2 (Build 9200)
Memory (RAM)    3571 MB
CPU Info    AMD E-300 APU with Radeon(tm) HD Graphics
CPU Speed    1299.8 MHz
Sound Card    Speakers (Realtek High Definiti | 
Display Adapters    AMD Radeon HD 6310 Graphics | AMD Radeon HD 6310 Graphics
Monitors    1x; Generic PnP Monitor | 
Screen Resolution    1366 X 768 - 32 bit
Network    Network Present
Network Adapters    TAP-Windows Adapter V9 | Microsoft Wi-Fi Direct Virtual Adapter | Qualcomm Atheros AR9485 802.11b/g/n WiFi Adapter
CD / DVD Drives    3x (E: | F: | G: | ) E: hp      CDDVDW SN-208DB  | F:  | G:
Ports    COM Ports NOT Present. LPT Port NOT Present. 
Mouse    5 Button Wheel Mouse Present
Hard Disks    C:  275.0GB | D:  22.0GB
Hard Disks - Free    C:  73.1GB | D:  2.2GB
USB Controllers    4 host controllers.
Firewire (1394)    Not Detected
Manufacturer     Insyde
Product Make     HP 2000 Notebook PC
AC Power Status    OffLine
Time Zone    Central Standard Time
Battery Status    High
Motherboard     Hewlett-Packard 188B
SM BIOS    F.37

---

### Post by adamalbanowicz on 2014-05-07
I wish I could help... the latest HP computers that I got all seem to not allow me to dual boot. So, I have given them to my daughters who only want windows and have instead gotten new hard drives to replace the crashed hard drives... I think something in the HP version of UEFI is stopping stuff in Win 8 and Win 8.1 as I had both refuse to change... also had the Win 8 machine refuse to upgrade to Win 8.1... but maybe someone here will have more luck as the UK support site was useless...HP is starting to sux...

---

### Post by mastablasta on 2014-05-07
how did you install? is windows secure boot enable disabled?: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

btw that thing must run slow on windows 8. :-O

---

### Post by ovingiv on 2014-05-07
mastablasta, I have tried to install it through USB, cd disk and a network install. Yes secure boot was disabled. Windows 8 actually ran fast after some updates. Installed 8.1 pro w/ media center and runs decently. I even tried to swap to bigger hard drive and install Windows 7 SP1, that also failed to install. Would not restart after installing (would not automatically restart).

---

### Post by mastablasta on 2014-05-08
efi partition was made? check the link i posted for possible clues. it seems install on UEFI depends from mashcine to mashcine. so much for UEFI standards...

---

### Post by ovingiv on 2014-05-14
For installing Windows 7, no, no efi partition was made.

---

### Post by mastablasta on 2014-05-15
you said: 
> The system originally came with Windows 8
efi partition might need to be on linux. please read the link i posted.


are you instaling (Ubuntu) linux as the only system? does it install normally (i.e. no issues reported)? what is the last message when it freezes? did you try running ubuntu live after install and using boot repair tool?

edit: also since it's a boot issue boot into live session start up boot repair tool and post the results of boot info script here.

---

### Post by ovingiv on 2014-05-17
Okey I don't know what I did but, I had iDuel booted Windows 7 and Ubuntu on a desktop with a 3.5" drive and I swaped my orgional hard drive from my laptop with the one preinstalled Ubuntu 14.04 LTS and it loaded the boot loader and loaded both Win 7 and Ubuntu... 

After that, I was then able to install Kali. I will close this fourm with "Fixed".

Thank all of you who helped.

---

