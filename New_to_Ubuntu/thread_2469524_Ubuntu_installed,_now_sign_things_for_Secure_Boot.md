---
title: "Ubuntu installed, now sign things for Secure Boot"
date: 2021-12-01
forum: New to Ubuntu
---

### Post by samhobbs on 2021-12-01
[COLOR=#000000][FONT=Verdana]I used [Install Ubuntu desktop]("https://ubuntu.com/tutorials/install-ubuntu-desktop") to install Ubuntu into a portable drive. When I try it I get:

Code:
error: /boot/vmlinuz-5.11.0-41-generic has invalid signature
error: you need to load the kernel first.

Many people just disable Secure Boot but that applies to all operating systems in the system so I do not want that.

I have been using Windows 10 for two decades. I am a developer. I am ready to switch to Linux. I have installed Ubuntu in a thumb drive and I have created a Puppy Linux in a thumb drive. So then I tried using the Ubuntu thumb drive to install Ubuntu in a USB portable drive, but I cannot boot that.[/FONT][/COLOR]
[COLOR=#000000]
[FONT=Verdana]I found [/FONT][How to sign things for Secure Boot]("https://ubuntu.com/blog/how-to-sign-things-for-secure-boot")[FONT=Verdana] but I am not sure how much of that, if any, can be done using Windows Subsystem for Linux. I have Ubuntu on a USB thumb drive if that will work and if WSL will not. I have gotten to the [/FONT]*Certificates in shim*[FONT=Verdana] section; I have MOK.priv and MOK.der files in my WSL's user directory. After that the instructions include restarting the system and messing with the kernel so I suspect I cannot use WSL to do that much at least. WSL cannot access the files in the Ubuntu in the portable drive. Is there a chance that the Ubuntu on the portable drive is good and I just have to do the secure boot signing? If so then how do I proceed; what system do I need to use to proceed?

[/FONT][/COLOR]Am I correct that the [Install Ubuntu desktop]("https://ubuntu.com/tutorials/install-ubuntu-desktop")[COLOR=#000000][FONT=Verdana] instructions should include something about this?[/FONT][/COLOR]

I first posted this question in [Ubuntu installed, now sign things for Secure Boot]("https://www.linuxquestions.org/questions/linux-newbie-8/ubuntu-installed-now-sign-things-for-secure-boot-4175704310/") and one response says I *have done an incomplete install of Ubuntu* but there is not much help otherwise.

---

### Post by tea for one on 2021-12-02
You did not mention which Ubuntu version you installed.

Ubuntu 20.04 and 21.10 will boot with secure boot enabled.
Create your installation USB device
De-activate, isolate or physically remove your internal Windows drives.
Attach your installation device and also your target device.
Boot the installer in UEFI mode
Allow the installer to create the required partitions

Alternatively, you could create a portable Ubuntu device with [COLOR="#0000FF"]persistent[/COLOR] storage.
Details here [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by oldfred on 2021-12-02
How you boot install media, UEFI with Secure Boot, UEFI (without Secure boot), or BIOS/CSM/Legacy is then how it installs.

The Secure boot install will auto sign kernels & grub. But if you need proprietary drivers like nVidia which Ubuntu cannot sign, then you have to manually sign that. I believe the installer will ask that during install, but I do not use Secure boot at current time.

---

### Post by samhobbs on 2021-12-03
I have had success. So here are a few things that could help others.

For the first attempt (the attempt I asked about here) I used Rufus to create the thumb drive. The instructions say balenaEtcher but provide separate instructions for Rufus. I think Rufus was not the problem but that is for others to consider.

You people say things like *Boot the installer in UEFI mode* but that is vague; I do not know how to do that. I realize that it is difficult to be clear because (if I understand) the procedure varies by computer. For me, I finally realized that there is a UEFI band across each of the icons when I boot from UEFI setup so that was not a problem for me but what "boot in UEFI mode" means will likely be unclear for others also.

If Windows is used to create a thumb drive to install from then here are a couple of resources. First, in *System Information* look for *BIOS Mode*; it should be UEFI. I can get to System Information by going to *Administrative Tools*. Next see [Boot to UEFI Mode or Legacy BIOS mode | Microsoft Docs]("https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/boot-to-uefi-mode-or-legacy-bios-mode?view=windows-11"), especially *Boot only when in UEFI mode*.

The next thing, and probably the most important for me, is that the first time I did not think I had any need to install third-party software so I chose not to. This time I noticed that installing third-party software includes using Secure Boot (the instructions do not show or say that) and this time I knew I wanted Secure Boot. And then it just worked.

For Secure Boot it asked for a password for use later but it did not use it; I hope I can remember that password if I need it in the future. I should write it somewhere, right? Or can I be certain it will not be needed?

Oh, one thing did not work; it did not connect to the internet. I will try again later.

I did not disconnect or disable my Windows drives or partitions but doing that could prevent someone from doing something they regret later. The thing that is not clear to me is if there is a need to update the Windows system (such as boot partition; I am not sure) with boot configuration. I guess not; I guess the important thing is the UEFI in the system.

---

### Post by samhobbs on 2021-12-04
The Ubuntu I have installed to the thumb drive then the portable drive is from ubuntu-20.04.3-desktop-amd64.iso.

The portable drive install worked once but then it did not. The system acted as if it does not exist. So I did the install again. And discovered more material for the instructions.

The first time I did it I did not know what MOK Enable (as in [UEFI/SecureBoot - Ubuntu Wiki]("https://wiki.ubuntu.com/UEFI/SecureBoot")?) was for so I did not do it. This time I did and I was asked for the password that I was not asked for previously (as I described in my previous reply). It seems to be working.

Except Ubuntu is still messing with my system's clock. I assume it is a problem with the timezone. I thought I set the timezone correctly.

---

