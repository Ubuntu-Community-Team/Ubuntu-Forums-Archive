---
title: "Ubuntu 12.04 Windows 8 UEFI dual boot problem"
date: 2013-08-21
forum: New to Ubuntu
---

### Post by Christian Heinrichs on 2013-08-21
Hello ubuntu forums,

First of all: I am a beginner, so bear with me.

Now here is the story:
I wanted to dual boot a Windows 8 64 bit version with Ubuntu 12.04.2 LTS 64 bit version,
preferrably using the windows boot manager with help of EasyBCD.
Windows was preinstalled, not Ubuntu.

And here is what I tried:


[LIST]
[*]Create two partitions in the windows storage manager, 1 for Ubuntu and 1 for swap 
[*]Boot from Ubuntu CD, installing Ubuntu in the according partition 
[*]Complete installation and reboot. 
[/LIST]


This is the part where the problems started.
At first Ubuntu would not boot, after I made an entry for it with EasyBCD with an error saying: ```
NST/AutoNeoGrub0.mbr not found
```
Then I tried to fix it myself, which went terribly wrong by resetting the BCD configuration via EasyBCD.
It led to Windows 8 not being able to boot, while Ubuntu was able to boot now from GRUB if I remember correctly.

So I went into Ubuntu and installed all updates including one proprietary recommended AMD driver.
The OS reminded me of rebooting before the driver could be installed, which I did.
What surprise, Ubuntu just shows verbose messages and doesn't start.
I locked myself out of two operating systems.

I seeked help and posted a question on AskUbuntu.
Thanks to Rod Smith over at [AskUbuntu]("http://askubuntu.com/questions/334186/ubuntu-12-04-2-windows-8-uefi-dual-boot"), I was able to get Windows back.
I followed his instructions, except step 7 because I wasn't able to install the debian package of rEFInd.

He didn't answer to my comment yet, so I hope you could help me with getting Ubuntu to boot.

---

### Post by oldfred on 2013-08-21
What I know of gpt partitioning I learned from Rod Smith. And his rEFInd has been around booting UEFI  (macs) systems before Windows and Ubuntu  converted to UEFI. So he knows UEFI. But he is not a fan of Boot-Repair which for Ubuntu usually works. He will comment on the "kluges" it uses but those are just work arounds for Windows systems with defective UEFI.

Is your system UEFI or BIOS? If UEFI you should not be using EasyBCD except to repair Windows issues. UEFI had multiple boot capability. With BIOS booting some use EasyBCD, but it installs grub4dos and makes grub2 install in less than a reliable mode (blocklists). 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Christian Heinrichs on 2013-08-21
I forgot to mention that my system is UEFI.

[Here](http://paste.ubuntu.com/6011637) is the BootInfo report.

---

### Post by oldfred on 2013-08-21
You are showing the signed kernels are installed, so you should be able to boot from UEFI menu the ubuntu entry with secure boot on or off. And it looks like Boot-Repair as added working Windows chain load entries. So you should also be able to boot Windows from UEFI or from grub.

If you are getting black screen that is video issue after booting.

---

### Post by Christian Heinrichs on 2013-08-21
I am able to boot Windows without problems, but my last remaining problem is getting Ubuntu to work.
If I boot Ubuntu I get a black screen, which fills up with verbose messages and then freezes with a blinking white cursor.

How can I fix this?

---

### Post by oldfred on 2013-08-21
What video card/chip?

You can try recovery mode which has nomodeset as default.

Or add nomodeset on linux line in grub menu. You may also need other settings or different ones depending on video and other system requirements.

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by Christian Heinrichs on 2013-08-21
> **oldfred said:**
> What video card/chip?

AMD Radeon HD 7670M

[LIST]
[*]If I go into recovery mode and select resume normal boot, a black screen fills up with messages and stops at "Stopping System V runlevel compatibility" 
[*]Booting in failsafeX mode gives me a blinking underscore in the top left with a black screen 
[*]Replacing quiet splash with nomodeset on the first try gave me a purple screen. On the second try I got a black screen filling up with messages until "usb not accepting address error -62" and the boot stops. 
[/LIST]

---

### Post by Christian Heinrichs on 2013-08-22
I updated the post.
What now?

---

### Post by oldfred on 2013-08-22
I do not know AMD, but generally you need to install the proprietary drivers for it and then would not need nomodeset.
But it seems like you have another error. It should not be throwing a usb error on booting. Do you still have a flash drive plugged in?
Or it may need another boot parameter in addition to nomodeset.

A few users with different systems have reported they needed extra boot parameters. What system is this.
Also some have found UEFI/BIOS settings that seem unrelated that make a difference.

Some of the parameters others used, but try one at a time with nomodeset.

        Some systems need these boot parameters
ACPI=Off nomodeset 
pci=nomsi noapic
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w

    
 Some other boot options
acpi_osi=Linux 
acpi_backlight=vendor

Not sure if still current on not, as yours is the newest series of AMD.
 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)
sudo apt-get install fglrx
#sudo aticonfig --initial -f
sudo aticonfig --adapter=all --initial
After reboot to get Catalyst Control Center
sudo apt-get install fglrx-amdcccle

---

### Post by Christian Heinrichs on 2013-08-22
> **oldfred said:**
> Do you still have a flash drive plugged in?
I do have a usb mouse and a usb modem plugged in.
Other than that, nothing.

> **oldfred said:**
> What system is this.
Do you mean the system model?

Thank you oldfred for pointing me in the right direction.
I booted Ubuntu with the text parameter and entered the command "sudo apt-get install fglrx" and it started booting normal!
How can I thank you via the "Thank you" function?

But one problem is left.
Everytime when I click or scroll the cursor disappears for just a second.
Should I install the AMD proprietary driver for this or will it make things worse?

---

### Post by oldfred on 2013-08-22
I thought the fglrx driver was the proprietary driver. 
But you may want to review if configuration or other settings are required.

---

### Post by Christian Heinrichs on 2013-08-22
Well, I gave Ubuntu the following command "sudo apt-get install fglrx" in the text session.
But the additional drivers program says that no proprietary drivers are in use on this system.
It shows these four entries:

[LIST]
[*]ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) 
[*]ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) 
[*]ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) 
[*]ATI/AMD proprietary FGLRX graphics driver (post-release updates) 
[/LIST]

[B]New problem:
[/B]While waiting for your answer I installed the FGLRX driver again I suppose by clicking the fourth entry.
                       Ubuntu now boots, but there are graphic errors and I can't navigate.
                       What did I do wrong this time again?

---

### Post by oldfred on 2013-08-22
Again I do not know AMD. 

With my nVidia it would on some versions say not installed but really was. And with nVidia I also get mulitple versions. My nVidia card is older so the newest is not required so I typically install a newer but not newest version. Not sure which version you may want or need.

---

### Post by Christian Heinrichs on 2013-08-22
If it's possible I want the newest stable version.
But I don't know if I should actually choose the proprietary driver or the open source one, because from my very little experience the proprietary driver makes a lot of trouble.

Please answer.

---

### Post by oldfred on 2013-08-23
I think you lose a lot of performance with the open source version.

 Ubuntu 13.04 Desktop Comparison: 6 Desktops, 5 Driver/GPU Combinations
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1)

---

### Post by Christian Heinrichs on 2013-08-23
So I got Ubuntu up again with the [Linux Tech Tips](http://www.linuxtechtips.com/2012/12/amd-radeon-hd-7670m-on-ubuntu-1204.html) guide.
I thought fglrx would now be installed, but the Additional Drivers program shows otherwise.
This made me run a few tests I found on the [Unofficial Wiki for the ATI Linux Driver](http://wiki.cchtml.com/index.php/Frequently_Asked_Questions).

The most tests were unsuccessful, so it looks like the install didn't work.

Should I make a new thread and mark this one as solved?
Because this is now a graphics driver question and not a dual boot question anymore.

I want to thank you oldfred for taking your time and helping me!

---

### Post by oldfred on 2013-08-23
Yes best to have a title that those who know more about AMD and video issues may respond to. They may not even look at a thread on boot issues.

You are welcome.

---

