---
title: "How To Install Hauppauge Nova-T 500"
date: 2007-03-14
forum: Outdated Tutorials &amp; Tips
---

### Post by dalejefferson on 2007-03-14
Hi all,

I found a great lack of quality install guides for this card so I've added one to our new wiki. [http://wiki.efficientpc.co.uk]("http://wiki.efficientpc.co.uk")

Guide is available here:  [http://wiki.efficientpc.co.uk/index.php/Install_Nova-T_500_On_Ubuntu_Linux]("http://wiki.efficientpc.co.uk/index.php/Install_Nova-T_500_On_Ubuntu_Linux")

The card works great and is very well priced, the only problem is the lack of support for the Remote control. We use a Microsoft Media Center remote. 
Guide here:  [http://wiki.efficientpc.co.uk/index.php/Lirc_mceusb2]("http://wiki.efficientpc.co.uk/index.php/Lirc_mceusb2")

Feel free to spread any of these guides as their available under GNU Free Documentation License 1.2

---

### Post by drifting on 2007-03-25
Blast!
Dug out old P4 PC, installed Ubuntu (What a breeze that was) ran out and bought a Nova-T 500 (Good grief PC World are expensive, but got to have toys now) Fired up web browser.........No website with instructions, of all the days to have your site down! Starting to take this personally now. :)

Paul.

---

### Post by dalejefferson on 2007-03-26
Sorry, 

We swapped hosts over the weekend. Had a bit of a nightmare with apache hitting MaxClients.
And we moved over to a Oscommerce website.

Sorted Now

Ps I posted the guide on Mythtv's Wiki as well.

---

### Post by drifting on 2007-03-26
Noticed you were back up, did a quick search yesturday and found the information on Mythtv's Wiki, but then went on to establish that I needed a longer aerial cable, so all in all Sunday was not going to be my day for playing Myth.

Thanks for the reply.

Paul.

---

### Post by nattugglan on 2007-04-28
Hi dalejefferson!

Do you have/can you wite a step-by-step guide to installing (and configuring) Nova-T-500 and MythTV on a clean installation of Ubuntu 7.04 Feisty?

I found your [**_Asgard Mythtv Dual Tuner Base Unit_**]("http://efficientpc.co.uk/product_info.php?cPath=23&products_id=38") and it looks like you have everything working (except the Hauppauge remote)?

nattugglan

---

### Post by drifting on 2007-04-28
Unless Dale knows different, from what I have found is that the remote is not supported in Linux (yet) I have followed Dales instructions and used an MS Media Centre remote, works quite well, but I have no idea what all the keys do yet as I am still fighting to get X to work with my TV resolution.

Paul.

---

### Post by nattugglan on 2007-04-28
> **drifting said:**
> Unless Dale knows different, from what I have found is that the remote is not supported in Linux (yet)
Thanks for your reply. Yes, that's what I've found as well. I just want to get the card and MythTV running, and it looks like Dale has everything figured out on 7.04. :) 
I will use my Logitech diNovo Edge bluetooth keyboard until I can find a solution for the remote.

nattugglan

---

### Post by nattugglan on 2007-04-29
Scanning in MythTV didn't work at all for me, so I've been testing with ***dvb-utils*** instead.

force_lna_activation is set to 1:
```
$ more /sys/module/dvb_usb_dib0700/parameters/force_lna_activation
1
```

Scanning with the ***scan*** command seems to work, but some of the channels are missing in the finished channels.conf file..
It looks like the channels from two muxes are missing.

Tuning with ***tzap*** seems to work, but the snr doesn't look promising(?). The snr is all 0000.
```
$ tzap -r "svt1"
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 522000000 Hz
video pid 0x03fb, audio pid 0x03fa
status 03 | signal 8521 | snr 0000 | ber 001fffff | unc 00000000 | 
status 1f | signal 86d4 | snr 0000 | ber 00000000 | unc 0000020d | FE_HAS_LOCK
status 1f | signal 87a3 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 8701 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 8795 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 86fe | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 86b6 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 8753 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 8710 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 8735 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 855e | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 850c | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 859d | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
```

Recording with ***tzap -o*** doesn't work.
```
$ tzap -o ~/Desktop/svt1_test "svt1"
tzap: invalid option -- o
```

***femon -a 0*** gives the following:
```
$ femon -a 0
using '/dev/dvb/adapter0/frontend0'
FE: DiBcom 3000MC/P (TERRESTRIAL)
status 1f | signal 8b25 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 8b25 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 8b25 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal 8b25 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
```

***femon -a 1*** gives the following:
```
$ femon -a 1
using '/dev/dvb/adapter1/frontend0'
FE: DiBcom 3000MC/P (TERRESTRIAL)
status 00 | signal 0000 | snr 0000 | ber 001fffff | unc 00000000 | 
status 00 | signal 0000 | snr 0000 | ber 001fffff | unc 00000000 | 
status 00 | signal 0000 | snr 0000 | ber 001fffff | unc 00000000 | 
status 00 | signal 0000 | snr 0000 | ber 001fffff | unc 00000000 | 
```

Seems like adapter1 can't lock on to the signal?
I tried to run ***femon*** on both adapters at the same time, and the results remained the same.
FE_HAS_LOCK on adapter0 and nothing on adapter1.

nattugglan

---

### Post by nattugglan on 2007-04-29
The missing channels were easy to fix.
The initial channel file (for my area) that comes with dvb-utils is outdated. I created my own initial channel file with the correct frequencies (using the frequencies listed in EyeTV on my Mac OS X box). And now all channels are found.

Another problem down. X to go. :) 

nattugglan

---

### Post by drifting on 2007-04-29
Good luck with X, I have been reading up for weeks on this, and being a noob it's a veritable minefield. Not sure how I am going to proceed, either continue with the inbuilt Intel chipset graphics & 955resolution, or change the Graphics car over for an ATI 9250.

Wish I understood this modline lark.

Paul.

---

### Post by nattugglan on 2007-04-29
Hi drifting!

With X I meant *'unknown number of problems'*. Not X11. :)

<off topic>
I had some serious problems with the screen resolution on my Mac mini G4 boxes. I found the solution a while back and just posted the solution in my thread: [Solution.]("http://ubuntuforums.org/showpost.php?p=2560578&postcount=21")
The solution was much simpler than all the 'guides' I had read.
I simply edited xorg.conf. Perhaps that can help you?
</off topic>

nattugglan

---

### Post by dalejefferson on 2007-04-30
> **nattugglan said:**
> Hi dalejefferson!

Do you have/can you wite a step-by-step guide to installing (and configuring) Nova-T-500 and MythTV on a clean installation of Ubuntu 7.04 Feisty?

I found your [**_Asgard Mythtv Dual Tuner Base Unit_**]("http://efficientpc.co.uk/product_info.php?cPath=23&products_id=38") and it looks like you have everything working (except the Hauppauge remote)?

nattugglan

Hi Guys,

The Nova-T 500 works 'out the box' on a fresh install of Feisty the driver is built into the kernel.
The remote control still is not supported.

---

### Post by nattugglan on 2007-04-30
> **dalejefferson said:**
> Hi Guys,

The Nova-T 500 works 'out the box' on a fresh install of Feisty the driver is built into the kernel.
The remote control still is not supported.
Hi there, dalejefferson!

I take it you have no problems scanning for channels in MythTV?

When I tried to scan for channels in MythTV, none were found.
Quote from LinuxTV: "scanning (or tuning with any AUTO parameters) is known to be broken in kernel 2.6.20, and probably earlier kernels too. Fixed in kernel 2.6.21".
Feisty has 2.6.20-15.

Has your boxes been stable?
Have you had problems with kernel oops?

nattugglan

---

### Post by tez1982 on 2007-05-09
I've recently decided to set myself up a media center, i've figured out everything except how to get my Nova-T 500 Dual Tuner working? Put on a fresh install of Feisty Fawn and it dosent seem to have detected it? Am i missing something obvious?

tez@tezmedia:~$ uname -a
Linux tezmedia 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
tez@tezmedia:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer FX41 motherboard
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: ec000000-edffffff
        Prefetchable memory behind bridge: e0000000-e7ffffff
        Capabilities: <access denied>

00:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at c000 [size=32]
        Capabilities: <access denied>

00:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at c400 [size=32]
        Capabilities: <access denied>

00:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at ee011000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at c800 [size=256]
        Memory at ee010000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 40000000 [disabled] [size=64K]
        Capabilities: <access denied>

00:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
        Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at ee012000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at cc00 [size=128]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at d000 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at d400 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at d800 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer FX41 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at ee013000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer FX41 motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer FX41 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 20
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at dc00 [size=16]
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer FX41 motherboard (Realtek ALC650 codec)
        Flags: medium devsel, IRQ 21
        I/O ports at e000 [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
        Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at ed000000 [disabled] [size=128K]
        Capabilities: <access denied>

---

### Post by dalejefferson on 2007-05-09
> **tez1982 said:**
> I've recently decided to set myself up a media center, i've figured out everything except how to get my Nova-T 500 Dual Tuner working? Put on a fresh install of Feisty Fawn and it dosent seem to have detected it? Am i missing something obvious?

tez@tezmedia:~$ uname -a
Linux tezmedia 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
tez@tezmedia:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer FX41 motherboard
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>



Its a USB device so use 

```
lsusb
```

---

### Post by dave_chimaera on 2007-07-22
Help!

Ive got the card in but I can't gt it working - lsusb shows it but in myth I get an error 'cannot open card' and using the DVB-utils to test I get a 'tuning failed' error message

I've tried with both the drivers included in Feisty and also the guide posted at the top of this thread and see the same problem both times - can anyone help?

Will supply any required info but you might need to tell me how to get it - still getting the hang of linux ;)

Cheers

EDIT: w00t! Cracked it!

---

### Post by nattugglan on 2007-07-25
dalejefferson?

> **nattugglan said:**
> Hi there, dalejefferson!

I take it you have no problems scanning for channels in MythTV?

When I tried to scan for channels in MythTV, none were found.
Quote from LinuxTV: "scanning (or tuning with any AUTO parameters) is known to be broken in kernel 2.6.20, and probably earlier kernels too. Fixed in kernel 2.6.21".
Feisty has 2.6.20-15.

Has your boxes been stable?
Have you had problems with kernel oops?

nattugglan

---

### Post by MLCT on 2007-08-19
Can anyone confirm the nature of the "firmware" for this card.

I have a dual boot Feisty & XP.  After having run with the card in XP for a few months and having gotten a bit fed up of the poor software I decided to configure the card for Ubuntu.  I have followed all the instructions and have it all working (& MythTV is pretty impressive compared to anything XP can provide).

The questions come with regard to the dual boot nature.  The first time I went back into XP I noticed a quick "found new hardware" icon that was quickly registered away as "Nova-DT".  Now given that XP doesn't see any of the ubuntu structures at all this confused me as for XP the card should be identical to what was there before.

Then after a bit of reading I come across this:

[http://www.hauppauge.co.uk/board/showthread.php?t=12907](http://www.hauppauge.co.uk/board/showthread.php?t=12907)

The gist of which is that speculation each time a boot into each OS is being done the eprom chip is being flashed with the respective OS's firmware - something that has a limited lifespan.

So my question is - is the linux firmware "firmware", ie. that is flashed to the card?  If that is the case then it does appear to be a bit dangerous to configure this card for dual-booters as it may very well fry the card - something I don't want to risk.

---

### Post by neilevan814 on 2009-02-23
Hi Dale, I was wondering what happened to your guide for the Happauge Nove-T 500 MCE tuner installation.  Will it be back up?

---

### Post by DrWarm on 2009-02-26
On [http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI) has a section on Ubuntu near the bottom.

Looks like it should work straight away with 8.10

---

