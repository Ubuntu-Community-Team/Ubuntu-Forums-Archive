---
title: "[SOLVED] 50 pin SCSI card operation in Hardy"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by bwallum on 2008-06-12
I have an old HP Scanjet 5p scanner. It works fine on an XP box using a pci SCSI card. The SCSI format is ultra, the outlet (lead connector) is 50 pin high density. It has an internal 50 pin connector which is not high density. 

When I fit the card to a pci slot in my Ubuntu box it causes the OS to hang during boot.

I have Xsane loaded and the scanner is listed as being fully supported by xsane. However, I presume I need a SCSI driver to be loaded prior to the operating system. Can anybody help me with this please?

Regards
Bob

---

### Post by Golem XIV on 2008-06-12
SCSI interfaces are a pain in the behind to set up, but once set up properly they are very fast and reliable.  There's a bunch of things that need to be checked.  First, when exactly does the system lock up?  Before BIOS POST, before the GRUB bootloader, before the Ubuntu logo shows up, after?  Do you happen to know which card it is? Does the card have a BIOS (it should report at power up with something like "Press Ctrl-A to enter SCSI BIOS Settings")? Have you enabled termination on the scanner (assuming it's the only device attached to the SCSI card)? There should be a jumper or switch on the scanner to enable/disable termination.  What SCSI ID have you assigned to the scanner?  What SCSI ID is assigned to the card?  Does the card have termination enabled?

---

### Post by bwallum on 2008-06-12
Thanks for the check list! Most helpful. I also discovered that it was necessary to turn the scanner on before booting up the pc. I have now got to the point where Hardy loads. During post I get the SCSI card reporting and after some fiddling (thanks for the <ctrl>A tip) I get POST to report the scanner on SCSI #2 with no errors reported.

SCSI #2 coincides with the hardware switch on the scanner.

When I run xsane however, it cannot find a device. 

The card is:-

SCSI Card
---------------------------
This 32-bit PCI to Ultra SCSI adapter supports up to 7 Ultra SCSI devices. One Internal 50-pin, and one external 50-pin high density connector are provided. Up to 20 MB per second throughput is possible
--------------------------
Model
Adaptec AHA-2940AU
Other numbers on sticker on main chip
984300-02 C
9752
--------------------------
Sticker on reverse of circuit board
1 47790 49300 8 (with bar code)
I/O-ADAP-SCSI2940

2nd Sticker on reverse of circuit board
BS0C75127T2 (with bar code)
MADE IN SINGAPORE
---------------------------
Motherboard slot type -PCI
---------------------------
BIOS
589247-00 D
BIOS 2E00
v1.32
1997
---------------------------
Stamped on back plate
60MPF
9047-8287B
---------------------------
Supported Protocols
SCSI-1
SCSI-2
SCSI-3
UltraSCSI
---------------------------

I think I am down to fine tweaking of the SCSI setup and/or xsane. Over to you....

---

### Post by Golem XIV on 2008-06-12
OK, looks like the SCSI chain is configured correctly, there are no SCSI ID conflicts and termination is set properly (otherwise the card would complain).  The Adaptec AHA-2940AU is a fairly standard card *even though a bit old).

Type **lspci** in a terminal window to check if Ubuntu has recognized the 2940AU card.  It wil list all your PCI devices, so you will need to look a bit.

<edit> I looked a bit around and found some info [here]("http://ubuntuforums.org/archive/index.php/t-11718.html") and [here]("http://ubuntuforums.org/showthread.php?t=243702") that may be helpful </edit>

---

### Post by bwallum on 2008-06-13
```
lspci
```gives
> 00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:09.0 SCSI storage controller: Adaptec AIC-7861 (rev 03)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

The SCSI card is picked up. I tried to reset the scanner hardware to SCSI0 and then set the card to SCSI0. The card correctly identifies SCSI0 as the scanner during POST. However, when I run 
```
sane-find-scanner
``` I get nothing
> # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.


```
sudo sane-find-scanner
``` I get
>  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

found SCSI processor "HP C5110A 3701" at /dev/sg0
  # Your SCSI scanner was detected. It may or may not be supported by SANE. Try
  # scanimage -L and read the backend's manpage.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


So, I have some progess. However it appears that I have to set up a permission in order to use it 'non root'.

I had at look at your two 'here' 's and think that some things have changed since they were written.

I guess I need to find the file that tells sane where to look for the scanner and change the permissions???

Interestingly, when I run ```
scanimage -L
``` I get > device `v4l:/dev/video0' is a Noname DEF-299A Camera virtual devicewhich is my usb web cam. Something going on with usb configuration???

---

### Post by Golem XIV on 2008-06-13
I can't help you with sane because I don't know anything about it (that's why I looked up those posts) but I do know something about SCSI.

Two things are important with any SCSI chain:  ID and termination.

SCSI IDs have to be unique.  if you have both the card and the scanner as ID 0 then they won't work.  It doesn't matter which ID each has, *as long as they are different*.  The SCSI card is usually set to ID 7; your scanner can be set to any number except the ID that your card has been set to (assuming that the card and the scanner are the only things connected to the SCSI cable).

The second thing is termination.  Both ends of the chain must be terminated.  Again assuming that the only elements on the SCSI chain are the card and the scanner, then both need to have termination enabled.  For the card, do this in the card's BIOS (through Ctrl-A) and for the scanner there should be a switch or a jumper that enables or disables termination.  Make sure termination is enabled.

I hope this will help.  Sorry if I can't be of more assistance.

---

### Post by bwallum on 2008-06-13
The card is on default SCSI#7 as you note, the scanner is on SCSI#0. POST picks up the scanner at SCSI#0 and ```
sudo sane-find-scanner
```gives> found SCSI processor "HP C5110A 3701" at /dev/sg0The scanner has two 50pin high density ports at the rear. I connect to one of these, the other port I presume is used to daisy chain if required. There is nothing on the second port. The scanner works fine using the same cable setup and the same SCSI card on an XP box. I think the SCSI side of things is possibly ok, thanks for getting me there, I've learnt a lot.

Can you help with setting permissions so that the scanner is detected when I'm not root? What is setting up a group all about?

---

### Post by Golem XIV on 2008-06-15
try
```
sudo chmod o=+rw /dev/sg0
```
to set the permissions.

Good luck!

---

### Post by H.Callahan on 2008-06-15
> **bwallum said:**
> The scanner has two 50pin high density ports at the rear. I connect to one of these, the other port I presume is used to daisy chain if required.
If your scanner does not have an option to do internal termination, then that second port needs to have an external terminator on it.  It should look something like: 

[img]http://www.icintracom.com/america/product_thumb.php?img=../global_catalog/images/201421pro.jpg&w=90&h=61[/img]

SCSI can sometimes work (marginally) without proper termination, but it is like anything else that is out of specification.  Sometimes it will and sometimes it won't.  Different software or OS behaving differently with unterminated SCSI does not surprise me.

---

### Post by bwallum on 2008-06-15
Here's a big wet sloppy kiss mmmmmmmmmmmmmmmmmmmmmmmmmmmmhhhhhhhhhhhhhhhh! I luv ya!

That is exactly what it needed, Set the permissions to include the user! Now scanning a treat.

Have a thanks on me!

---

### Post by bwallum on 2008-06-15
Thanks H. It appears the HP 5p (5110C) has the port nearest the side for itself, the port nearest the middle for linking to other devices. If the port nearest the side is used alone it auto terminates. Thanks for prodding me to check it out. By good fortune I was plugged into the correct port.

---

### Post by bwallum on 2008-06-16
Just one teeny little problem left. When I turn my computer off and then on again I lose the chmod setting, it reverts back to root. How do I make it a permanent chmod that can survive a reboot?

ANSWER is here 
[http://ubuntuforums.org/showthread.php?p=5196471#post5196471](http://ubuntuforums.org/showthread.php?p=5196471#post5196471)

---

