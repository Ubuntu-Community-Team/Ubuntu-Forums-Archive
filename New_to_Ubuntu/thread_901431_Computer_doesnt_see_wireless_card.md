---
title: "Computer doesnt see wireless card"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by elucho02 on 2008-08-26
I have been having the itch to try Linux for the longest time. I finally came around to trying Ubuntu. now I am having a problem and seeking help. I installed Ubuntu on a VMware workstation and now it seems like the machine is not seeing my PCI wireless card. 

hopefully this helps:
iwconfig

lo      no wireless extensions
eth0    no wireless extensions

lspci

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge(rev 01)
00:00.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE Interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:0f.0 VGA compatible controller: VMWare Inc Abstract SVGA II Adapter
00:10.0 SCSI Storage Controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPTDual Ultra320 SCSI (rev 01)
00:11.0 PCI Bridge: VMware Inc Unknown Device 0790 (rev 02)
02:00.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
02:01.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:02.0 USB Controller: VMware Inc Abstract USB2 EHCI controller

Thanks for the help

---

### Post by coolercooler on 2008-08-26
Ignore pls.

---

### Post by OffAxis on 2008-08-26
You can check here to see if your card is supported:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

and here's a good troubleshooting guide:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by nicedude on 2008-08-26
[elucho02]("http://ubuntuforums.org/member.php?u=651717"), wifi can be hard to even figure out exactly what chipset you have, so if you post as much as you know others here like me could tell you more. Please post the model # off the sticker on the bottom of the laptop with extra numbers if present ( ie I have a Acer 5520 but it says on my sticker Acer 5520-5716 which can tell more sometimes ).

---

### Post by elucho02 on 2008-08-26
I have the "Intel(R) PRO/Wireless 2200BG" is not the card that came with the laptop. I bought it some time ago.

---

### Post by liquidfunk on 2008-08-26
I'm unsure of your post, but from what I gather you are running it in a VM.

 Try running it from a LiveCD and try it then. 

VMs aren't great for checking out your hardware support.

---

### Post by elucho02 on 2008-08-26
ok. I will try using the Live cd and i will let you know what happened.

---

### Post by Mr. Velociraptor on 2008-08-26
I'm new to linux too, and I heard only ubuntu 8.04 automatically uses wi-fi.
I'm probably wrong, but still.

---

### Post by liquidfunk on 2008-08-26
What did you mean by the automatically uses Wifi?

  Ubuntu is very good in that the hardware detection is quite broad. So a lot of things will work without any tweaking. 

 Wireless cards such as Broadcom, Atheros and such may need to have 'Restricted Drivers' but they will work without much hassle. From experience, a lot of Intel, RaLink, and often Atheros cards work out of the box. 

 Remember that Ubuntu isn't the only distribution of Linux. Just because it is backed by great marketing doesn't mean that all the others are useless.

 Have a look at some of the other distributions. Mandriva, OpenSUSE, Fedora, Debian, Slackware, Gentoo are generally the most commonly used, though there are the smaller forks of these projects with benefits to each of them. 

 Sometimes I've had something not work in Ubuntu but work in Debian.

---

