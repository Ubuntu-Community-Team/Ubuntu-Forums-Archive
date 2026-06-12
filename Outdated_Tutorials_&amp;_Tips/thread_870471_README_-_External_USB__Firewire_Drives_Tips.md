---
title: "README - External USB / Firewire Drives Tips"
date: 2008-07-25
forum: Outdated Tutorials &amp; Tips
---

### Post by old_salt on 2008-07-25
Moderator - Please feel free to adjust this accordingly - Thanks, Tony

A few initial tips or README for ANY _external_ USB/IEEE1394 Hard Drive.

**NOTE:** This pertains **ONLY** to taking an old hard drive and installing it into an enclosure kit to make it an external USB or Firewire device. **_*THIS DOES NOT*_** refer to one of those 1-touch automatic backup drives or IOMEGA setups that include software or are labeled for Winblows! DIY Hard Drive conversions using the enclosure kit only.

I bought an enclosure to convert my 200Gb WD IDE drive to an external drive. I've done this countless times at work (USB Enclosure) however I HATE USB and prefer Firewire (for obvious reasons). Each build was different and no two drives are the same so just bear with me as I hope I save anyone interested a LOT of time and frustration BEFORE attempting to edit fstab, grub, manual mounting and scripts etc.

1. BEFORE closing the case and connecting the unit up, test to see if everything works as per the installation instructions for the enclosure kit.

IF Automount fails **OR **your system doesn't detect or show the drive (for whatever reason), proceed to step 2.

2. Remove the jumper from the drive completely. 
Test Again. This works about 80% of the time.

3. If test fails again, move the jumper to slave and then to CS (Cable Select).

If this fails then proceed to more detailed instructions in this forum however I'm very confident this will resolve your problem. E/K/Myth/Ubuntu has proven "Out-of-box" support for these devices and in keeping with the KISS rule (keep it simple ...) I'd rather defer the drastic stuff (manual editing of files which usually results in forced recovery mode) to a measure of last resort. 

Every drive is different. My experience was most WD drives is they  require no jumper while others did, either in the Master or Slave configuration. Samsung, IBM, Toshiba, Hitachi etc, they are all different and you will just have to play around. At least it's only 4 settings to try and I did mention to leave the case open until you got the unit working before sealing it up. Following these instructions takes less than 5 minutes. 

I tried the fstab edits and other suggestions and almost toasted my system until I went back to basics during troubleshooting. 

For work we usually get the cheap $25 USB Enclosures. As stated above, I HATE USB for obvious reasons and prefer Firewire whenever possible as it's much faster, reliable and solid especially under Linux.

I purchased from Tiger Direct the CompUSA brand Combo IEEE1394a & USB2.0 (backward compatible to USB1.1) enclosure for $35 (SKU 306103). It came complete with cables as well. It supports PC and MAC including OSX. Given this I figured Hardy should be no problem. =D>

I started out as per the instructions included in the kit but no connection. I removed the jumper completely and everything worked perfectly both USB and Firewire. The drive automounted and the dialog box opened up upon connect just like a CD.

ISSUE: when connected via USB, large transfers, IE; 100mb or more resulted in disconnects from the unit. Thanks Linus for not completely fixing all the USB issues. Minor transfers that were successful were only at 23Mbs or less.

As for Firewire? It works flawlessly and much faster than USB and never misses a beat. Transfer rate is off the scale. 

A Firewire PCI card for your PC is about $10 or less from Tiger or most stores. I got it to dump Videos off my Camcorder through Kino. So I had a need and use for a firewire card. Most systems today have at least one built in. If you have a chance or ever have the option to do so, I HIGHLY RECOMMEND using the Firewire path over USB. It's just better technology.

I hope this helps anyone having issues getting a USB external drive or Combo unit working in short order.

:popcorn:

---

