---
title: "Loader???"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by skitzer1 on 2012-03-04
Hope i get his right this time.I have a concern.Bare in mind i am a complete novice to open source.My dual boot was mess although the grub did infact load.My concerns are this.I found spyware and trojans on my W7 which has the grub installed.However is it possible that the Hackers who hijacked my browser also compromised my grub as i don't know how long they were on my system one of the trojans was rogue paypal loader.So there must have been spying for quite some time.i have noticed Hdd activity when O\S is idle,i just put that down to AGV running scans.My fear is that if the Grub can be manipulated to what ends,and how can i check to see if this is so???thank you for taking the time to read this and for any input.

---

### Post by 2F4U on 2012-03-04
If hackers have  been able to break into your computer, they could have been doing almost everything, including manipulation of grub and even the installed Ubuntu system.

---

### Post by Mark Phelps on 2012-03-04
In its native form, without special drivers, Windows can't understand Linux filesystems.  So it's highly unlikely that any "hackers" messed around with GRUB.

Browser hijacking tends to happen most often using "rootkits" -- and the Kaspersky site has a free rootkit remover for download known as TDSSkiller.  You should download that and run it in Win7.

---

### Post by skitzer1 on 2012-03-04
> **Mark Phelps said:**
> In its native form, without special drivers, Windows can't understand Linux filesystems. So it's highly unlikely that any "hackers" messed around with GRUB.
 
Browser hijacking tends to happen most often using "rootkits" -- and the Kaspersky site has a free rootkit remover for download known as TDSSkiller. You should download that and run it in Win7.
 
Thank you so much for your input mark.

---

### Post by mcduck on 2012-03-04
> **Mark Phelps said:**
> In its native form, without special drivers, Windows can't understand Linux filesystems.  So it's highly unlikely that any "hackers" messed around with GRUB.

Browser hijacking tends to happen most often using "rootkits" -- and the Kaspersky site has a free rootkit remover for download known as TDSSkiller.  You should download that and run it in Win7.

Furthermore, the loader part of Grub isn't actually installed on any of the filesystems, it's located on the MBR section of the hard drive, before any of the partitions.

While there are some boot sector viruses around, they are very rare these days, and making one that specifically targets Grub installs wouldn't make much sense. (And as pretty much every BIOS contains option to protect boot sector, and making a normal virus works just fine and is much easier than making a boot sector virus, they are more a part of computing history than a potential threat)

---

### Post by 3rdalbum on 2012-03-04
I'll just add too that its highly unlikely that an actual person attacked your computer. Malware is usually all automated to infect as many computers as possible, and once there it may download other malware automatically.

Malware is probably not written to even look for GRUB. That is a very specific, not-very-helpful piece of information for a malware author.

---

