---
title: "Stung by Jammy Jellyfish"
date: 2022-05-15
forum: New to Ubuntu
---

### Post by msh8er on 2022-05-15
I've dabbled with ubuntu since release 14.  I used 20.04 with Win7 for awhile and this past week, I decided to part company with Microsoft and Norton and hopefully Google and Amazon.   I rounded up BitTorrent, Rufus, and Jellyfish download, which survived Friday, 5/13.  Win7, and lots of Web related stuff survived, but Win10 didn't.  I think I misdirected Rufus, which wiped out Win10, but I apparently have a faulty iso, as I don't have a bootable Jellyfish.

QUESTION: What software/downloads would you suggest I need to salvage my mess?  I watched the tutorials on creating the bootable USB even though I remembered the basics.  Any suggestion will be appreciated.

BUT I OBVIOUSLY DIDN'T DO A GOOD JOB WITH BACKUPS.
Extra credit if you know about Hollerith without a search engine.
Thanks,  msh8er

---

### Post by grahammechanical on 2022-05-15
I can only guess that you used Rufus to burn the Ubuntu 22.04 ISO image not on to a USB memory stick but onto the partition that held Windows 10.

We use utilities like Rufus to burn a Ubuntu ISO image to a USB memory stick. Then we set the BIOS/UEFI of the motherboard to look for an operating system on the USB memory stick and usually a live session of Ubuntu will boot/load. We can use the live session to Try or Install Ubuntu. If I am correct about what you did, then I can only say that I have no idea what you can do next.

Do you want advice on dual or triple booting Ubuntu and Windows 7 and also Windows 10? Please give us information about your hardware. You need to create unallocated space for Ubuntu. Use Windows utilities to create that unallocated space and make sure that Windows can boot. Do you want advice on using the Ubuntu installer and installing using the Something Else option?

Did you misdirect Rufus or the Ubuntu installer?

Regards

---

### Post by msh8er on 2022-05-15
[[COLOR=#000000]grahammechanical[/COLOR]]("https://ubuntuforums.org/member.php?u=1087323")[COLOR=#000000]   Thank you for allowing me to clarify.  I *think I *probably pushed the  Rufus button to create a bootable Usb to wipe out my Win10.  Oysters were waiting.
In any case, I seem to have a corrupted Iso and I'm looking for GUESSES as to how to proceed.  
Win10 is not available.  i had a small collection of advice and software which i wiped out.  I'm asking if there  are win7 apps which I can use to recover... or do I need to start from scratch?
Any advice welcome.
msh8er[/COLOR]

---

### Post by yetimon_64 on 2022-05-15
> **msh8er said:**
> ...but I apparently have a faulty iso, as I don't have a bootable Jellyfish...

> **msh8er said:**
> ...I seem to have a corrupted Iso and I'm looking for GUESSES as to how to proceed...

First thing before proceeding is to check the downloaded iso is/isn't corrupt for certain. 
[[COLOR=#0000ff]--Here--[/COLOR]]("https://releases.ubuntu.com/22.04/SHA256SUMS") is a link to the current Jammy Jellyfish release page file "SHA256SUMS". 

The command to run in the terminal against the downloaded iso file is "sha256sum", then compare that output with the checksum in the website file "SHA256SUMS". If the terminal output and the value in the SHA256SUMS link are identical then your download is good. If so much as one character differs then the download is corrupted. Copy/pasting both the terminal output and the entry for you iso from "SHA256SUMS" into an editor on adjacent lines makes for very easy checking visually/manually.

eg. assuming your download is in ~/Downloads...
 ```
sha256sum /home/$USER/Downloads/ubuntu-22.04-desktop-amd64.iso
```

Edit: a further link to information re verifying a download...[[COLOR="#0000FF"]--Here--[/COLOR]]("https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview")

---

### Post by Impavidus on 2022-05-16
Verifying the download using the sha256 checksum is a good step, but if you downloaded it by torrent, it was checked automatically.

I've never used rufus. There are several tools for making live usbs. Some have some settings, which you may have to get right (UEFI or legacy, persistence or not), other tools are simply one size fits all (both UEFI and legacy, no persistence). Some computers don't work with all settings, some tools are broken, some usb drives are broken and some computers don't want to boot from every usb port.

If you've lost some important files that were stored on your Win10 partition, first use Windows tools for file recovery, if you can. Also make backups of your files on other partitions, put them on an external drive and cleanly remove and physically unplug that backup drive. Accidentally wiping out Windows while installing Ubuntu is very easy. Creating and running the live usb should be quite safe though.

---

### Post by msh8er on 2022-05-16
Thank you very much for your thorough advice.  The checksums did match !!!! so I'm now believing I messed up with Rufus.
Going to try my luck with Ubuntu's usb creator.

---

### Post by msh8er on 2022-05-16
Thank you for your advice.  I totally wiped Win10, so I'm now definitely committed to the Jellyfish.
I'm about to try the Ubuntu tool to create a boot USB.

---

