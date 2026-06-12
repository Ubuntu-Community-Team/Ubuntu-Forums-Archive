---
title: "Ubuntu freezing on startup"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by Daniel_Browning on 2013-10-21
I just installed Ubuntu on my laptop. This is my first attempt at using Linux, so I'm pretty lost. The install went smoothly until the end, when it was unable to install grub. I searched on google and decided to try the automated disk-repair tool.  After several attempts, I was able to get grub installed. Now the problem I'm having is that ubuntu will boot to the desktop and everything works fine for a few seconds, then my computer freezes up again.

I'm at a loss as to what to try now. Any advice would be much appreciated.

---

### Post by Jake Sweeney on 2013-10-21
Try to run Ubuntu on your laptop via an external medium such as a USB flash drive. Then, if it runs smoothly, you'll know that it is a problem with the internel HDD, not the computer's other hardware components. If it's the internal HDD then I'd try and reinstall Ubuntu, subsequently reinstalling the GRUB bootloader and aloowing Ubuntu to load without any hiccups ;)

---

### Post by fantab on 2013-10-21
What machine is this? Specifications please.
Why do you think your HDD is corrupt? Did something happen with your previous OS?
Boot with Ubuntu DVD/USB and "Try Ubuntu without installing"... See if everything is working alright. Now, open the utility called 'Disks'- select your HDD and run SMART tests. If there is any problem with your HDD you will know. 
Sometimes the problem could be a bad download of ubuntu.iso or a bad burn. Do a [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") on your downloaded .iso. If the sum matches then re-BURN the .iso.

---

### Post by Daniel_Browning on 2013-10-21
It's a custom laptop made by Malibal.

Intel Core i7-3960X CPU @ 3.30GHz 
Intel X79 Chipset
Dual nVidia GTX 680M cards
one 750GB hdd and two 60GB sdd's in RAID0

I'm able to run ubuntu off the flash drive with no issues (besides having to select nolapic on boot), which is also the medium I used to install it. However I ran SMART tests on all three of my drives and nothing turned up. When I first got this pc I tried to install Windows, but I couldn't get 64 bit to work because of a driver not being signed. I ran 32 bit for a while, then got frustrated and decided to give linux a shot.

I tried reinstalling ubuntu and grub, but to no avail. I have been using 13.10, but I just downloaded a fresh iso of 12.04 and I'm going to give that a try.

I'll be glad to post any other specs or info if it's any help.

---

### Post by fantab on 2013-10-22
You are booting ubuntu 64bit right?

---

### Post by Daniel_Browning on 2013-10-22
Yes.

---

### Post by fantab on 2013-10-22
The problem I think is with RAID.  Do you have your HDD too in RAID array? 
I don't know much about RAID. So you should wait for someone who knows more about installing Ubuntu on RAID. You may want to add 'RAID0' in your Thread Title.

Meanwhile you can learn more about Ubuntu and RAID:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Search the forums and you will find more info.

Or it could be a Graphics issue:
Try [nomodeset ]("http://ubuntuforums.org/showthread.php?t=1613132")at boot and see if it helps.

Good luck...

---

### Post by Daniel_Browning on 2013-10-23
[ATTACH=CONFIG]247192[/ATTACH]
The hdd isn't in Raid, so I tried installing on that. Adding nolapic and nomodeset and booting off the hdd gets me to the purple loading screen, but then it gets suck. I pushed esc and found that this appears every time I try to boot up. I'm assuming this is related, but I don't know enough about computers to even know what the errors are referring to :\

---

