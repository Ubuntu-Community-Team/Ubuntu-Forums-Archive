---
title: "Bios"
date: 2021-12-25
forum: New to Ubuntu
---

### Post by maruankc on 2021-12-25
Hello! I'm new to Linux, sort of, I've used it before about 10 years ago, but this is the first time I've decided to install it myself, in an attempt to revive an old laptop.

However, I'm not very smart for computers, so I'm struggling a bit, but still managing, however I have something on my mind that I can't find anywhere, it's about the BIOS, more specifically about the process I did to install Ubuntu with my USB Flash Drive.

I went on the Advanced tab in the BIOS and changed Fast BIOS from Enabled to Disabled and UBS S3 Wake-up from Disabled to Enabled.

On the Boot tab I changed Secure Boot from Enabled to Disabled, and then OS Mode Selection from UEFI OS to CSM OS.

In the Boot Priority Order I changed it and put USB HDD in the 1st spot, when it used to be the 6th, the order ended up being:
1. USB HDD
2. Windows Boot Manager
3. SATA HDD
4. SATA CD
5. USB CD
6. USB FDD
7. Network

Now, the laptop is booting up perfectly fine, and I'm enjoying Ubuntu, but I wonder if I have to change any of these settings back to their previous defaults. One thing I've been thinking about, if I put Windows Boot Manager in the 1st position again, does it mean that it'll try to boot Windows? What options should I change back to how they were and which are better as they are now? I don't know what most of it means unfortunately.

Any help is very much appreciated, and I thank you all in advance.
Also, it December 25th right now, so Merry Christmas to you all, I hope you all have a good day!

---

### Post by Frogs Hair on 2021-12-25
> [COLOR=#000000]Now, the laptop is booting up perfectly fine, and I'm enjoying Ubuntu, but I wonder if I have to change any of these settings back to their previous defaults. One thing I've been thinking about, if I put Windows Boot Manager in the 1st position again, does it mean that it'll try to boot Windows? What options should I change back to how they were and which are better as they are now? I don't know what most of it means unfortunately.[/COLOR]

Hello [COLOR=#000000]maruankc:[/COLOR]

You don't really need to change anything unless you want to change the boot order. Assuming this a dual boot, the Win boot manager  will boot first if set that way.  I have two drive dual boot with Win 11 and have 11 set to boot first just to facilitate windows update when a reboot is required to finish an update. I do this to avoid having to make a boot selection during the update.

---

### Post by oldfred on 2021-12-25
While many vendors still call it BIOS, it really has been UEFI since 2012 when Microsoft required vendors to install in UEFI boot mode to gpt partitioned drives. 
Old Windows BIOS installs only work with MBR(msdos) partitioned drives.

If you have UEFI or CSM/BIOS/Legacy selection it is a UEFI system. 
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

So if you turned CSM on and have installed in BIOS boot mode, you have booting with old BIOS mode.
The selection in UEFI, is then the default for installed systems. But if selecting an install from UEFI boot menu (often f12) that may override default.
But, how you boot install media for both Windows & Ubuntu (UEFI or BIOS) is then how it installs. That is independant of default UEFI setting for installed systems.
Grub will only dual boot other systems installed in same boot mode.
UEFI & BIOS are not compatible or once you start booting in one mode, you cannot switch.

---

### Post by maruankc on 2021-12-25
I'm not using the dual boot, I believe Ubuntu overwrote Windows 8 completely when I installed it, at least I hope so, because I did choose the option to erase the disk and all and not the one with the dual boot. Only noticeable difference I can see while booting is that before it'd show the Samsung logo, now it still does, but with instructions on the bottom of the screen.

F2 for setup --- F4 for recovery

I don't know if that's important or not, and I'm afraid of breaking something if I do it, especially F4, it seems to be booting up fine. I believe F2 brings up the same BIOS screen as before still.

---

### Post by grahammechanical on 2021-12-25
> One thing I've been thinking about, if I put Windows Boot Manager in the  1st position again, does it mean that it'll try to boot Windows?

How could it load Windows? You installed Ubuntu by selecting the Erase disk and install Ubuntu option. Believe us, the installer did exactly that! You now have a boot option in the boot priority list that will not work. All that will happen is that the motherboard will fail to find a Windows boot loader and therefore look for the second option on the list. And so on until it finds a boot loader or reaches the end of the list. Then you will see a "no operating system found." message.

Do you have a USB hard drive with an OS on it? Is Ubuntu installed on the SATA hard drive? If Ubuntu is on the SATA drive and there are no other operating systems installed then the motherboard will find Ubuntu every time anyway.

You could try editing the boot priority list to remove the Windows option. But as you are unfamiliar with the UEFI settings utility I would not recommend that you do that.

Do you not have a motherboard user manual? Sometimes the manufacturer's web site will offer an electronic version for download.

Regards

---

### Post by maruankc on 2021-12-25
> **grahammechanical said:**
> How could it load Windows? You installed Ubuntu by selecting the Erase disk and install Ubuntu option. Believe us, the installer did exactly that! You now have a boot option in the boot priority list that will not work. All that will happen is that the motherboard will fail to find a Windows boot loader and therefore look for the second option on the list. And so on until it finds a boot loader or reaches the end of the list. Then you will see a "no operating system found." message.

Do you have a USB hard drive with an OS on it? Is Ubuntu installed on the SATA hard drive? If Ubuntu is on the SATA drive and there are no other operating systems installed then the motherboard will find Ubuntu every time anyway.

You could try editing the boot priority list to remove the Windows option. But as you are unfamiliar with the UEFI settings utility I would not recommend that you do that.

Do you not have a motherboard user manual? Sometimes the manufacturer's web site will offer an electronic version for download.

Regards

I see, that makes me feel a lot more calm, thank you.

I suppose everything is working as it should then, the only thing I wonder is what that "F4 - Recovery" on the booting screen means, though as long as I don't press it I should be fine.

I'll see if I can find a motherboard user manual, it must be lying around somewhere, it's an old laptop, but my family usually doesn't throw instructions away, so I should be able to find it.

Once again, thank you very much for the help!

---

