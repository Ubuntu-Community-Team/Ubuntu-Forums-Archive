---
title: "Installed Ubuntu From USB, No visuals"
date: 2015-01-11
forum: New to Ubuntu
---

### Post by raymond20 on 2015-01-11
I've been using Ubuntu from USB and decided to install it on a new desktop. Installed it from Try Ubuntu. It was working fine visually after installation until shutting down. Afterwards upon reboot there's no visuals, even when plugging in the USB. Not too sure what happened since it was working fine until after shutdown. Not too sure what to try in fear of doing more damage.

---

### Post by Bucky Ball on 2015-01-11
Welcome. Maybe a silly question, but are you positive it has installed to the hard drive? Is the BIOS set to boot from the correct drive? Are you getting any messages or just a blank, black screen?

Shutdown, take out USB dongle(s), boot and enter the BIOS, check the boot device is the correct hard drive. Any luck?

---

### Post by raymond20 on 2015-01-11
Pretty sure, also tried booting with the hard Drive Disconnected with no USB and USB. Blank Blank Screen, no BIOS. Should I try unhooking and rebooking the Video card? All fans are running including the Graphic Card's.

Relevent parts if needed.

AMD A8-7600 Kaveri Quad-Core 3.1GHz 


MSI A58M-E33 FM2+ / FM2 AMD A58 (Bolton D2) HDMI Micro ATX AMD Motherboard


GeoForce GtX 759Ti

---

### Post by Bucky Ball on 2015-01-11
Which version of Ubuntu are you using? 

When you say 'no BIOS', do you mean you can't get into the BIOS? You are hitting the right keys but nothing's happening? Are you getting nothing at all, right from boot. No manufacturer's splash screen straight after boot (if often only sticks around for a second or two)?

You could try reconnecting vid card if you think you may have bumped it or it has somehow become dislodged. Leave the hard drive in, just not the USB stick. Then we know we are working from the HDD and the USB stick does not confuse things.

Just to confirm, when you boot from the USB stick you are getting exactly the same black screen as booting from the hard drive? Exactly the same issue? If so, this could be hardware. How old is the vid card?

---

### Post by alex313 on 2015-01-11
Try Ubuntu will Not write any thinking on you harddisk. Press F12 at boot and select boot from harddisk.

---

### Post by raymond20 on 2015-01-11
No visuals at all as in no output detected for all configurations. 
Should there be something to tell me if I have audio if it's just a video problem? 
Card is a bit old and lightly used though, Friend ordered it a while back but found a deal for a better card and kept it around for when I was going to make this Desktop.

---

### Post by corneldardenjr-y on 2015-01-12
Have you checked to make sure the GRUB boot loader is on the right disk (not the USB)? Also, do you get a BIOS screen?

---

### Post by raymond20 on 2015-01-12
Get no visual signal at all. As in monitor doesn't appear to get anything to show at all, not even a blank screen from the computer rather than the monitor. Ubuntu 14.04  was installed from the USB to the Hard Drive so GRUB should be on that right? I'm pretty sure the answer is no but installing Ubuntu doesn't change the Graphics Card or MotherBoard directly right?

---

### Post by Bucky Ball on 2015-01-12
> **raymond20 said:**
> ... installing Ubuntu doesn't change the Graphics Card or MotherBoard directly right?

No. If you are getting no BIOS options when you boot the machine it may have nothing to do with the OS, though, regardless of which OS it is. If you don't even get a manufacturer splash screen or any options to choose a boot device or enter the BIOS, I'd possibly try testing a different graphics card, if you can get your hands on one. If there's no sign of life from go to whoa, that may be the direction to start looking in. 

Another silly question and you've probably done this, but you've checked the cable from the computer to the screen is firmly connected? Could you try a different cable for starters? Might be easier to procure than another graphics card ...

---

### Post by raymond20 on 2015-01-12
I'll look for another cable as well as try a different monitor, but it's definently looking like it's the Graphics card although I have no idea how it went kaput right after Installation and shutdown. Thank you all for the help, I'll post results later.

---

### Post by mastablasta on 2015-01-12
you have two graphics cards. one is in the AMD APU the other one is NVidia. did you install any proprietary drivers? if so which ones (AMD or nVidia)? what get's detectect in "try it" session? did you try swithing the cable to the other GPU?

---

### Post by Bucky Ball on 2015-01-12
> **mastablasta said:**
> you have two graphics cards. one is in the AMD APU the other one is NVidia. did you install any proprietary drivers? if so which ones (AMD or nVidia)? what get's detectect in "try it" session? did you try swithing the cable to the other GPU?

^^^
This. Good thinking. It sounds, though, that the OP can't boot to the Live session from the USB anymore either, though. Same blank, black screen.

---

### Post by raymond20 on 2015-01-12
Didn't think about the other GPU, tried it with the other HDMI  connection area but no dice. With or without USB. Also tried without the Geoforce Card plugged in getting the same results, no visual signal at all. With the Geoforce card unplugged I'm not too sure what that means now.

HDMI cable works fine, tested with Wii U.

---

### Post by raymond20 on 2015-01-12
Tried with VGA cables now with a different monitor. Tested on a laptop and worked fine on that. Still same no visuals from Desktop though.

---

### Post by mastablasta on 2015-01-13
take the NVidia GPU card out, then try to boot into live session.

can you reach BIOS?

---

### Post by raymond20 on 2015-01-13
Tried it, still no visual signal with VGA or HDMI. With USB and no USB.

---

### Post by raymond20 on 2015-01-16
Also tried resetting the CMOS by removing the battery for an hour, still nothing.

---

