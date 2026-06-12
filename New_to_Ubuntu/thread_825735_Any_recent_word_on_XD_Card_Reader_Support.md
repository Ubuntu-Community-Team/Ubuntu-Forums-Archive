---
title: "Any recent word on XD Card Reader Support?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Brightbelt on 2008-06-11
Hi,
I have an HP dv9000 Pavilion Laptop which has a built in SD/XD card reader for digital cameras. (My HP is Core 2 Duo; 2.7 gHz; 2 gb of ram; 2 internal HD's).

I've read a lot of posts on this - Ubuntu and otherwise - and many of the posts are now simply out-dated.

So is there any recent buzz about XD card reader support for Ubuntu?

Many Thanks for any help,...
Frank B.

---

### Post by Colin82 on 2008-06-11
Not sure about your specific laptop, but my Toshiba A135-S4427 has an internal card reader and it works perfectly, no configuration needed.

Running Hardy

---

### Post by niteshifter on 2008-06-11
H,

Ubuntu doesn't care if it's XD, SD, Duo or whatever kind of memory card. It does care about what card reader controller chip your system has. Figuring out what hardware you have, then asking the question may get you more mileage (lspci and/or sudo lshw are your friends in this).

Or get one of those inexpensive multiplex USB card readers. I've a SanDisk ImageMate that works A-OK, no hassles at all. Cost was $15.

---

### Post by Inxsible on 2008-06-11
I think the op meant he has an internal card reader which he would like to make it work. The last I used it only sd cards were recognized. Sony memory sticks are not. I have never used xd, but I guess they were not recognized either.

But yeah, the alternatives are there like a usb reader or simply connecting the camera with usb while the card is in it, will also give you access to it much the same way as the usb readers do.

---

### Post by timcredible on 2008-06-11
most probably specific to the card reader in your laptop - my dell vostro card reader works perfectly, so does my hp pavillion desktop card reader, and my hp psc printer card reader.  unfortunately, you may need to do some research on how to find the make/model of your card reader (probably lspci command) and then manually configure the system to recognize it.  if that doesn't work, just buy an external card reader for probably $15 and use that.

---

### Post by Brightbelt on 2008-06-11
Many Thanks for your responses, and ironically, the reason I didn't mention lspci is because I've really already looked into that. But clarity always helps out, so....

My lspci shows my XD reader to be the following number sequence: 07:05.4 And, a point of interest here is that it does NOT list it as an "unknown device". The manufacturer 'Ricoh' and device 'XD reader' are explicitly named etc. 

It has been suggested that one could add these to the /etc/modprobe.preload file: 
```

sdhci
mmc_core
mmc_block

```
I tried that and got no result. FYI, I am on PCLOS Gnome 2008 with this HP dv9000 laptop. I'm asking here because I've got Ubuntu on another computer and am more familiar with it. Also I have a feeling Ubuntu might configure this more easily than PCLOS will and I would change distros and install Ubuntu on this laptop if this were configurable in Ubuntu.

As always, Many Thanks for your help,....Frank B.

---

### Post by Brightbelt on 2008-06-11
.....For those who want the original:
```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

Many Thanks, Frank B.

---

### Post by Inxsible on 2008-06-11
The hardware's detected alright, but it don't work :)

If you notice it also detects Sony memory stick card reader -- but try putting one in and it won't even see it :(

---

### Post by Brightbelt on 2008-06-11
Just to elaborate on my intentions here... I know it sounds petty, but I really LOVE having the camera card reader built into the laptop, so I can just pop the card in. 

Isn't that what the digital age is about?:)
(...satisfying those extremely specific points of laziness!)

---

### Post by stchman on 2008-06-11
> **Brightbelt said:**
> Hi,
I have an HP dv9000 Pavilion Laptop which has a built in SD/XD card reader for digital cameras. (My HP is Core 2 Duo; 2.7 gHz; 2 gb of ram; 2 internal HD's).

I've read a lot of posts on this - Ubuntu and otherwise - and many of the posts are now simply out-dated.

So is there any recent buzz about XD card reader support for Ubuntu?

Many Thanks for any help,...
Frank B.

If your laptop is anything like mine it has a Ti 5 in 1 card reader.  The latest kernel in Hardy supprots SD no problem but xD is not supported.

You can get a USB xD adapter off ebay for around $5.  Strange thing is my girlfriends Vista equipped laptop uses the same reader and her says SD and xD but it does not work with SD but works with xD very well.

---

### Post by LowSky on 2008-06-11
did some google searching try this its for MMC memory but it might apply to your issue as well

[http://intr.overt.org/blog/?p=59](http://intr.overt.org/blog/?p=59)

just type the instructions it gives to point to your xD controller, i changed their code to match yours forom your posted output, make sure its right before using my code.
```

**# /sbin/setpci -s &#8216;07:05.4&#8242; 0xCA=0×57** (Write Enable)
**# /sbin/setpci -s &#8216;07:05.4&#8242; 0xCB=0×02** (MMC Disable)
**# /sbin/setpci -s &#8216;07:05.4&#8242; 0xCA=0×00 **(Write Disable)
```

---

### Post by Brightbelt on 2008-06-11
Many Thanks LowSky. I had tried that code already actually. And I get a response that the "directory does not exist". I just type the lines there at the prompts, right? 

Apparently - and a fellow linux expert pointed this out to me as well - the article mentions flat out that the code only works for MMC memory situations and that XD card folks are still out of luck.

The writer is a little vague though; he suggests putting that code into a "startup script" but doesn't tell someone how that's done. 

Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-06-11
Here's the quote down below the article:

> Hmm? xD? There’s absolutely no support for xD cards in the linux kernel. No amount of bit flipping will change that.

---

### Post by niteshifter on 2008-06-11
Hi,

Again, the kernel doesn't care about memory cards, it cares about chips (hardware): a given XD card controller might not have support, but another will. A search on google.com/linux "kernel XD card support" shows that many have problems with xD cards and also that many don't. So this:

> Hmm? xD? There’s absolutely no support for xD cards in the linux kernel. No amount of bit flipping will change that. 

is not correct. It was once correct, but those days have passed. Just like once there was absolutely no support for SCSI devices, USB devices, PCI bus and so on.

I have a Dell 1420n. The Ricoh R5C822, R5C843 and R5C592 controllers do work with Ubuntu. That covers: SD/SDIO/MMC/MS/MSPro MMC and Memory Stick devices.

This machine also sports a Ricoh xD-Picture Card controller, but it does not work - not because of any shortcoming with kernel / Ubuntu - but because there is not a physical interface for that card type. The manual says it does, the Dell web page says it does. Physical inspection of the hardware definitively says it does not - so I can't speak to how xD works with Ubuntu with built-in hardware. My external SanDisk reads / writes to xD perfectly.

I mention this with such specificity because the slot on this machine will accept an xD card, it will physically go in, but there are no contacts present for the card to mate with. This explains why xD doesn't work on some Dell models, I've this feeling others are in the same boat, be they using Dells or not. It's a parts supplier issue.

> Just to elaborate on my intentions here... I know it sounds petty, but I really LOVE having the camera card reader built into the laptop, so I can just pop the card in.

Actually, no it isn't petty. We call 'em Personal Computers for many reasons - and it's not unreasonable to expect that your hardware should work. Dealing with the deficit in performance is another matter entirely. It depends upon the individual's needs and tolerance - in my case it worked out to balancing sending the machine back (and doing without a laptop) vs just using the SanDisk unit I already had. YMMV

---

### Post by googatrix on 2008-06-21
Hi,

I have an HP Pavilion dv2699 laptop with a built in 5-in-1 card reader slot which includes xD cards. The card reader works fine with SD cards, but not with xD. The controllers are the same as the ones niteshifter mentions:

```
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

My questions is:

> **niteshifter said:**
> 
I mention this with such specificity because the slot on this machine will accept an xD card, it will physically go in, but there are no contacts present for the card to mate with. This explains why xD doesn't work on some Dell models, I've this feeling others are in the same boat, be they using Dells or not. It's a parts supplier issue.


Do you mean the actual hardware on your Dell does not support xD cards? This cannot be true in my case, because the card reader works with xD cards in Vista (dual boot on the same laptop).

Given that the HW works fine and the Ricoh xD-Picture Card Controller appears in lspci, how can I take this forward and make it work in Ubuntu? 

> **niteshifter said:**
> 
it's not unreasonable to expect that your hardware should work


Couldn't agree more, and given that both my digital cameras use xD cards this is something that would really improve my user experience with Ubuntu...

Many thanks for any help!

---

### Post by ddswanson@gmail.com on 2008-06-21
dv2000t

xD does not work (SD works), also the Palm multimedia Cards do not work for me.
](*,)](*,)](*,)

lspci | grep Ricoh
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by stiv2k on 2008-07-14
Yup! Same issue here with HP dv9009nr and same Ricoh 5-in-1 card reader.  May I extend much encouragement to whomever may attempt to provide support for this!
=D>=D>=D>

---

### Post by BoardDWorld on 2008-07-29
Thanks for all the information everyone has provided, particularly you Brightbelt. I have the same Ricoh device in my DV9224TX and this thread has at least given me a clear answer on XD support.

And yes Laptop owners won't find purchasing an external reader a solution. It's simply dual boot for now.

---

### Post by ghstzr0 on 2008-10-06
> I have a Dell 1420n. The Ricoh R5C822, R5C843 and R5C592 controllers do work with Ubuntu. That covers: SD/SDIO/MMC/MS/MSPro MMC and Memory Stick devices.

This machine also sports a Ricoh xD-Picture Card controller, but it does not work - not because of any shortcoming with kernel / Ubuntu - but because there is not a physical interface for that card type. The manual says it does, the Dell web page says it does. Physical inspection of the hardware definitively says it does not - so I can't speak to how xD works with Ubuntu with built-in hardware. My external SanDisk reads / writes to xD perfectly.

I mention this with such specificity because the slot on this machine will accept an xD card, it will physically go in, but there are no contacts present for the card to mate with. This explains why xD doesn't work on some Dell models, I've this feeling others are in the same boat, be they using Dells or not. It's a parts supplier issue.

Just wanted to point out that you may be wrong on this...

**I have that exact model: Dell Inspiron 1420n, and the xD reader DOES work, but only in Windows.**  There are physical contacts for the card (you have to insert the card at the very bottom of the slot).  The reason it does not work (a I understand it) in Ubuntu is because Ricoh will not release the specs so a driver can be written to support this format.

Of course, you could have a slightly different setup than I do, but I doubt it since it's the exact same model...

---

### Post by acreech on 2008-12-03
I am having the same issue with the Ricoh 5 in 1 card reader. It reads SD but not xD. 

Lots of luck to anyoone trying to firgure out how to make this work in Ubuntu. 

I am on an Acer Aspire 7520-5185 laptop computer.

Thanks

---

### Post by msully725 on 2008-12-16
I also have the Ricoh xD reader. After some brief research I found the [Alauda Project]("http://alauda.sourceforge.net/wikka.php?wakka=HomePage") stating xD support since kernel 2.6.16-rc1. This suggests xD reading is possible, but our Ricoh controller is in need of a driver.

I'm going to keep looking and prodding for Ricoh xD controller support.

---

### Post by Captain_tux on 2009-01-03
> **msully725 said:**
> I also have the Ricoh xD reader. After some brief research I found the [Alauda Project]("http://alauda.sourceforge.net/wikka.php?wakka=HomePage") stating xD support since kernel 2.6.16-rc1. This suggests xD reading is possible, but our Ricoh controller is in need of a driver.

I'm going to keep looking and prodding for Ricoh xD controller support.

Hey msully -

Any luck???

---

### Post by Captain_tux on 2009-01-04
If anyone is interested, I found a "work around" for this issue: I purchased a Targus USB Memory Stick Card Reader/Writer for $9 at Walmart that works just beautifully... it mounts automatically and **F-Spot** opens as soon as I click on the MISC folder of the card... you can then use **F-Spot** to import/copy your pictures.

Interestingly enough, the box says it supports Mac & Windows, but again, this works just fine for me... and for 9 bucks, it's not a bad fix.

[http://www.walmart.com/catalog/detail.gsp?image=http://i.walmartimages.com/i/p/00/87/14/36/00/0087143600538_500X500.jpg&product_id=9722060&iIndex=1&isVariant=false&corpCard=false&type=0](http://www.walmart.com/catalog/detail.gsp?image=http://i.walmartimages.com/i/p/00/87/14/36/00/0087143600538_500X500.jpg&product_id=9722060&iIndex=1&isVariant=false&corpCard=false&type=0)

---

### Post by 73ckn797 on 2009-01-04
My Toshiba (see specs below) would not read the Sony memory stick with SD adapter but would if using a USB adapter. I did not like it but it is a workable solution. No more problem since I replaced my digital camera that uses SD/xD.

---

### Post by M0GEJ on 2009-01-06
I am having the same problem with my HP DV2500 laptop. Annoyingly enough I did not bring the docking station for my camera along with me. The SD card from my dad's camera works no problem in the integrated card reader but the XD card doesn't even show.

---

### Post by niteshifter on 2009-01-06
> **ghstzr0 said:**
> Just wanted to point out that you may be wrong on this...

**I have that exact model: Dell Inspiron 1420n, and the xD reader DOES work, but only in Windows.**  There are physical contacts for the card (you have to insert the card at the very bottom of the slot).  The reason it does not work (a I understand it) in Ubuntu is because Ricoh will not release the specs so a driver can be written to support this format.

Of course, you could have a slightly different setup than I do, but I doubt it since it's the exact same model...

Just stay with me here:

Well, here we are - a year later and this subject comes up. Also being a year later - and just last week I fished a fuzz ball out of the fan with a shaved down toothpick - time to disassemble the machine and blow the dust out. And take a picture of the card reader slot area and show the missing xD connector (which a couple of other web sites mention) ....

The flippin' (my language was a bit stronger, but this is a family forum) 'cover' for the xD slot was stuck down, invisible from the front. **You are correct:** It does have an xD slot. And it does not work with 7.10 (kernel 2.6.22-16). Not a sign of it in dmesg output.

So ... as to my post of a half year back: Nevermind :oops:

---

### Post by Purple8 on 2009-03-22
Does anybody know if we are any closer to having Ricoh xd reader support. Im loving ubuntu so far but this is my last thing to get working.  Well apart from sage if i was to use ubuntu for clients.

---

### Post by googatrix on 2009-03-23
A bug is open on Launchpad. You can track the progress here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490").

---

### Post by leoh on 2010-02-03
Any news about this? Same issue as everyone here with an HP dv2621.

---

### Post by Radar Rider on 2010-03-13
> **Captain_tux said:**
> If anyone is interested, I found a "work around" for this issue: I purchased a Targus USB Memory Stick Card Reader/Writer for $9 at Walmart that works just beautifully... it mounts automatically and **F-Spot** opens as soon as I click on the MISC folder of the card... you can then use **F-Spot** to import/copy your pictures.

Interestingly enough, the box says it supports Mac & Windows, but again, this works just fine for me... and for 9 bucks, it's not a bad fix.

[http://www.walmart.com/catalog/detail.gsp?image=http://i.walmartimages.com/i/p/00/87/14/36/00/0087143600538_500X500.jpg&product_id=9722060&iIndex=1&isVariant=false&corpCard=false&type=0](http://www.walmart.com/catalog/detail.gsp?image=http://i.walmartimages.com/i/p/00/87/14/36/00/0087143600538_500X500.jpg&product_id=9722060&iIndex=1&isVariant=false&corpCard=false&type=0)


This worked for me as well. I am running Karmic 64-bit, and haven't had a lick of USB device trouble in this release, or in Jaunty 64-bit Studio, or in Hardy 32-bit on the same machine. I just got back from Wal-Mart with the Targus SD reader, and the SD card I've been unable to read in my chassis-based or external multi-format card readers now works like a champ. Semper Fi to my fellow former Marine, and thanks for the G2.

---

### Post by Ellio-pc on 2010-08-02
I Have a Dell Inspiron and got my xd card reader to work. Go to the following link:

[http://ubuntuforums.org/showthread.php?t=1454403](http://ubuntuforums.org/showthread.php?t=1454403)

---

