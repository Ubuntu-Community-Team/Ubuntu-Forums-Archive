---
title: "Webcam problems"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by daneandrewlam on 2012-11-29
Hello everyone,

Firstly, I'm sorry if this has been covered in another thread (as I'm sure it undoubtedly has!)

I've just received a new customised computer through pcspecialist.co.uk. I opted not to pay an extra £80 and instead take many users' recommendations to install Ubuntu instead. It's my first day and seems great. However, I can't seem to install the drivers that came on a CD with the computer.

In particular I've been trying to use the webcam, which hasn't been detected. The Driver Installtion CD won't run in Ubuntu and autoruns with Wine Windows Program Loader. The problem is it says that my computer doesn't minimum system requirements to run the driver, which I'm sure isn't true.

Here are the computer's components (below.)

Any help would be greatly appreciated!

Thanks in advance!

Chassis & Display	UltraNote: 14" Glossy HD LED Backlit Widescreen (1366x768)
Processor (CPU)	Intel® Core™i7 Dual Core Mobile Processor i7-3520M (2.90GHz) 4MB
Change to: Intel® Core™i7 Quad Core Mobile Processor i7-3632QM (2.20GHz) 6MB
Memory (RAM)	8GB SAMSUNG 1600MHz SODIMM DDR3 MEMORY (2 x 4GB)
Graphics Card	Intel® HD Graphics 4000 Video Memory Technology up to 1.7GB
2nd Graphics Card	NONE
Memory - 1st Hard Disk	240GB INTEL® 335 SERIES SSD, SATA 6 Gb/s (upto 500MB/sR | 450MB/sW)
SSD CACHE DRIVE	NONE
1st DVD/BLU-RAY Drive	Ultra Slim 8x SATA DVD±R/RW/Dual Layer (+ 24x CD-RW)
Memory Card Reader	Internal 9 in 1 Card Reader (MMC/RSMMC/SD: Mini, XC & HC/MS: Pro & Duo)
Sound Card	Intel 2 Channel High Definition Audio + MIC/Headphone Jack
Network Facilities	GIGABIT LAN & WIRELESS INTEL® N-2230 (300Mbps) + BLUETOOTH
USB Options	2 x USB 3.0 PORTS + 1 x USB 2.0 PORT AS STANDARD
Battery	UltraNote Series 6 Cell Lithium Ion Battery (62.16WH) (Up to 7 Hours)
Power Lead & Adaptor	1 x UK Power Lead & 65W AC Adaptor
Operating System	NO OPERATING SYSTEM REQUIRED
Office Software	NO OFFICE SOFTWARE
Anti-Virus	NO ANTI-VIRUS SOFTWARE
Laptop Cooling Stands	NONE
Carry Case	NONE
Monitor	NONE
Keyboard & Mouse	INTEGRATED UK KEYBOARD
Mouse	INTEGRATED 2 BUTTON TOUCHPAD MOUSE
Speakers	NONE
Webcam	INTEGRATED 2.0 MEGAPIXEL WEBCAM

---

### Post by grahammechanical on 2012-11-29
This

> I can't seem to install the drivers that came on a CD with the computer.

you will not be able to do. It is my guess that those drivers are for installing the webcam in the Windows operating system. I do not think that wine is any use for installing Windows drivers to work in Linux.

This is the best that I can come up with:

[https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam")

[https://help.ubuntu.com/community/Webcam/Troubleshooting]("https://help.ubuntu.com/community/Webcam/Troubleshooting")

Regards.

---

### Post by audiomick on 2012-11-29
> **daneandrewlam said:**
> ...However, I can't seem to install the drivers that came on a CD with the computer.

There are almost certainly no Linux drivers on there, so you can probably use the CD as a beer coaster. 

Linux deals with drivers a bit differently to Windows. Most drivers are integrated into the kernel, i.e. you don't need to install them. The exceptions are the instances where there are proprietary drivers which cannot, due to licence restrictions, be freely distributed. These can generally be  obtained using the additional drivers facility. I believe that is  in the menu system settings> software on 12.10. Is that the Ubuntu version you have?

Perhaps you could post what isn't working apart from your webcam, or is it only that?

---

### Post by XXYZGuy on 2012-12-06
When you set up Ubuntu were you offered the opportunity to have your picture taken, and did your webcam spring to life at that moment?  Mine did, then it took ages to figure out how to awaken it again.

Is your webcam connected? I know it sounds stupid but it might not be plugged in!   I have  3 webcams, they're all plugged in but only 2 register, the Logitech and the Colorvis.  The Swann Sportscam only registers as a drive, like a flash drive, but it can double as a webcam in  a certain mode on Windows OS.  It appears not all webcam's are  supported.

---

### Post by mike555 on 2012-12-06
You might want to install " GuvcView " .

---

### Post by piemonkey on 2012-12-23
I've got the same model as you, right down to the meaty core i7 ;)

I'm running Kubuntu 12.10 and I've had no problems with the webcam, I even had a skype chat the other day. If you're running 12.04 then maybe the drivers aren't included, but other than that I'd assume anything that works for me should work for you.

If you went for the LTS version (12.04), maybe give 12.10 a go with a live usb, and see if it works.

---

