---
title: "Installer crashes after detecting hardware"
date: 2015-09-22
forum: New to Ubuntu
---

### Post by Harpratap on 2015-09-22
I have an an old laptop HP Compaq 2210b with Intel Core 2 duo, 2GB RAM and onboard intel graphics.
I got this laptop from a family member and it came with windows 8 installed. I formatted the C: drive and installed windows XP as windows 8 was very slow.
Now I'm trying to install ubuntu 15.04 (64 bit) from usb drive but I can't get past installer crashed.

The main issue is that the BIOS on this thing is password locked, there is a password for power on and another one for entering the setup mode. I know the power ON password but not the setup one.
All the threads with similar issue suggest solutions involving UEFI/fastboot/Secure boot. But I'm not able to see/or change these settings since I have a locked BIOS. I don't know if this device has UEFI or traditional BIOS. 

One thing that made a bit of difference was connecting to wifi and installing updates, it crashed at installing additional packages instead of detecting hardware this time.
I have 3 partitions on my 160GB drive: 50GB for XP, 2GB for swap and remaining for /

---

### Post by grahammechanical on 2015-09-22
Did that machine come with Windows 8 pre-installed? If not then it is very unlikely that the motherboard has secure boot or a UEFI boot system. If you check the HP Compaq site for the specifications of this machine you will find that the original OS was Windows Vista. So, I think you should forget about secure boot and UEFI as causing this problem.

Be more concerned that according to HP the machine uses up to 384 MB shared system memory. That reduces the memory for the OS and indicates that the video adapter may not be capable of running Unity 3D which is the default user interface with Ubuntu.

Apart from trying again with Xubuntu or Lubuntu or Ubuntu Mint you do not actually say what happened. "Installer crashed" and "crashed at installing additional packages" does not give us any clue as to what the problem could be or even if it is happening with the live session or an installed session of Ubuntu or during the installation process itself.

So, does the live session work fine? If the live session works fine, then I suggest installing without ticking the box "Install third party software." Then Ubuntu or Lubuntu or whatever will install using the same open source video driver that the live session uses.

[http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c01123782-9](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c01123782-9)

Regards.

---

### Post by Harpratap on 2015-09-22
Thanks, LXLE got installed without any issues. I don't know how, but my friend with lower graphics, RAM and older CPU can run Unity and KDE just fine on his desktop.
Ubuntu worked fine on live session but Kubuntu showed a black screen after booting for me. 

Now that I have a *buntu distro, can I use KDE or Unity or any one of these heavy GUIs?

---

