---
title: "Can't install to hard disk"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by spider1780 on 2011-11-25
I have just built a SFF sytem using a Zotac NM10-E-E Motherboard (Mini ITX with dual core 1.8GHz Atom CPU) + 4Gb Crucial DDR2-6400. The board has no IDE, just 2xSATA. I've used a SATA-IDE adaptor from ebay so I can re-use a slim IDE dvd drive. 

I have also acquired a 30Gb IBM SATA SSD (ex blade server). This works fine as an additional drive in my main desktop system. I have scanned it and there are no errors.

The BIOS appears to allow me to boot from a an HDD, optical disk or pendrive. When the SSD or a pendrive is connected at boot it is recognised by the BIOS setup utility.

1. If I boot the system from a MS-DOS or Mythbuntu boot CD, with no SSD or pendrive connected, it boots OK.

2. If I add the SSD and leave the boot order to boot from Mythbuntu in the optical drive; then I get the Zotac flash screen, some activity on the dvd drive, and nothing but a steady cursor.

3. Same problem with Win7, XP or a boootable DOS CD.

4. Same problem if disconnect the SSD and insert a pendrive, set order to optical then USB drive, and start up with a bootable O/S disc in the DVD drive.

5. If I remove the SSD and pendrive I can boot from the optical drive again.

6. If I boot with Linux as in 1. above, then insert the pendrive I can install Linux on the Pendrive and boot from that OK.

Running the system from a pendrive is not a long-term option. Any thoughts as to what I can try?

---

### Post by spider1780 on 2011-11-26
It occurs to me that the answer might be so basic that people think this question is a strange joke.
I really do need help with this. It's been a few years since I've built a system and I can't think what I'm doing wrong. Can anyone tell me where I might start looking?
Thanks.

---

### Post by jjex22 on 2011-11-26
Hi there! ah the fun and games of DIY! 

Does your Zotec board have a one time boot option? for example at my asus screen I can press F2 for enter BIOS or F12 for Manual boot selection, or something similar - for one time only boots. This should work as it basically removes all other devices from the boot order and only boots of the selected device.

Failing that, have you tried removing everything from the boot order apart from the CD/DVD drive when trying to install?


This one's going to seem a little bit silly, but bare with me - how long does it hang for? our old Dell hangs for about 20s with a flash drive connected before moving on with it's duties - I think it's reading the drive for some reason - not supposed to! the amount of times I hit ctrl+alt+del before I gave up, got a coffee, came back and it was booted!

You could also check if there has been a Bios update to address this - if so you should be able to do it via a freedos live usb/CD

As a last resort you could just do the same as you did with the flash drive - once boot's been handed over to the cd drive, manually connect the SSD drive to install? I've done this before with a RAID controller that was being a Dbag.

If you can't get anwhere with any of this, use another PC to make a live usb of linux/ windows installer - I haven't seen one for dos around, but I've not been looking - My MS-DOS is very happy in it's VM honestly believing it's still 1994!

---

### Post by LinuxFan999 on 2011-11-26
It sounds like you might possibly have a defective BIOS on your motherboard.
 
Try re-flashing the BIOS and see if that helps.

---

### Post by spider1780 on 2011-11-27
Thanks for your replies. 
My board doesn't have a one-time boot option so far as I have been able to find from the documentation.
I have now tried removing all but the CD from the boot order and connecting the SSD before booting. It still hangs. If I remove the SSD and reboot, it's OK again.
I've left it half an hour or more and there's been no change, so no just a case of impatience this time, though I have been caught out by that in the past.
I also tried to connect the SSD after booting, but it isn't recognised by Ubuntu (using: ***sudo lshw -C disk***). I have no linux experience, so if there's anything I can do to get the disk recognised at this point then please let me know.
I will try a bios update/refresh - I've noticed that I have to reset to system defaults after some failures before it will even cold boot. Can anyone tell me how to determine the current bios version from within Ubuntu?
Thanks.

---

### Post by spider1780 on 2011-11-27
This brand new Mboard come with Atom D525 installed. The latest version of the BIOS was Dec 2010 and was introduced specifically to support the D525 CPU. So unlikely I have an old BIOS. 
Still worth a try re-flashing though. Just need to work out how to do that from USB...

---

### Post by spider1780 on 2011-11-27
OK. Made a bootable DOS USB drive and flashed BIOS with latest version from Zotac.
But I still can't boot from the CD or USB while the SSD is attached, even with only one device in the boot order in BIOS setup.
Any more ideas please?

---

### Post by jjex22 on 2011-11-28
I know this is a log shot, but you could try re-connecting the ssd to your other pc - 1 to test it hasn't inexplicably failed since last test, and 2 - try reformatting it with gparted - go device and reset mbr, then add a fat32 partition to fill up the disk?

Just trying to rule out hardware failure - does your other pc have a sata disk drive to rule out the ide->sata card being at fault?

Also have you tried connecting a standard hard drive and seeing if the same thing happens - basically try swaping each part to narrow down what's causing the problem? 

I've not been able to find any similar faults searching for zotec and ssd, which leads me to think there's a hardware fault issue.

---

