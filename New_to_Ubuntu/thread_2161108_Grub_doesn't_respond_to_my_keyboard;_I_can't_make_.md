---
title: "Grub doesn't respond to my keyboard; I can't make a selection"
date: 2013-07-09
forum: New to Ubuntu
---

### Post by Traxster on 2013-07-09
Hi guys/gals,



Ran into a minor issue. Just as the title states, grub v2.00, will not recognize acer aspire s3 (with Ubuntu 13.04 x64 installed) keyboard and I cant make a selection. Bios version is 2.07. I did find another related thread [here]("http://ubuntuforums.org/showthread.php?t=1957426"), however, it has been closed and it did not help me. 

In bios, under boot, there are 2 boot options to select from. Currently it is set up with UEFI. I tried switching to legacy bios, however, I received message no operatings system available. 

Any help would be greatly appreciated.

traxster

---

### Post by DeathByDenim on 2013-07-09
I assume the keyboard does work when you've actually booted into Ubuntu, right?
I'm not sure why your keyboard doesn't work in Grub, but at least I can tell you that it does work on my Acer Aspire V3 using legacy BIOS. (I'm assuming the S3 is similar at least to the V3)

The reason you get "no operating systems available" is because you installed Ubuntu under UEFI, rather than under BIOS. I've installed 13.04 using BIOS mode rather then UEFI because I couldn't get Ubuntu to boot at all after completely erasing the hard disk to get rid of Windows 8.

---

### Post by grahammechanical on 2013-07-09
You can check in BIOS the settings you have for keyboard. Is the keyboard PS2 and is the BIOS set for USB or is it the other way around, USB keyboard but the BIOS setting is for PS2?

In my BIOS there is a setting for Legacy USB support. If set to [auto] it allows the system to detect the presence of USB devices a startup.

There is also a setting for Plug and Play OS. If set to [No] the BIOS configures all the devices in the system. When set to [yes] and when a Plug and Play OS is installed, the OS configure the Plug and Play devices not need for boot.

What do you see in your BIOS? The manufacturer does not expect the keyboard to be needed between the BIOS running and the OS loading. That could be the problem.

Regards.

---

### Post by Traxster on 2013-07-09
> **DeathByDenim said:**
> I assume the keyboard does work when you've actually booted into Ubuntu, right?
I'm not sure why your keyboard doesn't work in Grub, but at least I can tell you that it does work on my Acer Aspire V3 using legacy BIOS. (I'm assuming the S3 is similar at least to the V3)

The reason you get "no operating systems available" is because you installed Ubuntu under UEFI, rather than under BIOS. I've installed 13.04 using BIOS mode rather then UEFI because I couldn't get Ubuntu to boot at all after completely erasing the hard disk to get rid of Windows 8.


yes, the keyboard works otherwise.

---

### Post by Traxster on 2013-07-09
> **grahammechanical said:**
> You can check in BIOS the settings you have for keyboard. Is the keyboard PS2 and is the BIOS set for USB or is it the other way around, USB keyboard but the BIOS setting is for PS2?

In my BIOS there is a setting for Legacy USB support. If set to [auto] it allows the system to detect the presence of USB devices a startup.
,
There is also a setting for Plug and Play OS. If set to [No] the BIOS configures all the devices in the system. When set to [yes] and when a Plug and Play OS is installed, the OS configure the Plug and Play devices not need for boot.

What do you see in your BIOS? The manufacturer does not expect the keyboard to be needed between the BIOS running and the OS loading. That could be the problem.

Regards.

in my bios I can't find any specific settings for my keyboard. The only tabs are; information,main,security,boot,exit. Should there be a keyboard tab?

on the boot tab, under boot mode, in item specific help, it lists 3 boot type posibilities; dual type, legacy type, or UEFI, however, when I try to change those values, it only allows either UEFI or legacy. What happened to dual type? I don't see any settings for plug and play.

thanks again,

traxster

---

### Post by oldfred on 2013-07-09
It may be just a USB setting for legacy, meaning it will see the old USB keyboard & mouse type devices.

Sometimes you have to turn off UEFI to get the option to turn on legacy or BIOS. Dual may boot either but you may have to turn both UEFI and Legacy on or off? Settings with UEFI with many systems are very confusing and just required trial & error, unless someone has your exact model and knows.

Is UEFI/BIOS 2.07 the latest version?

---

### Post by Traxster on 2013-07-14
> **oldfred said:**
> 


As far as I know, it is the latest version. I will double check however. anyhow, the problem seems to have corrected itself, I will report back with more details, as I am not exactly certain what I did, that made the differrence.

---

