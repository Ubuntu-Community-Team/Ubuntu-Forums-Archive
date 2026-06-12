---
title: "[SOLVED] USB San Disk Cruiser Stick"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-08-10
When I insert my San Disk 'mini cruiser' mem stick, I receive a pop up unable to launch... I've tried re-booting the system, No Luck. Any sugestions??? The stick works fine on a Windows XP OS.

---

### Post by fenT1 on 2008-08-10
> **CoCoKnots said:**
> When I insert my San Disk 'mini cruiser' mem stick, I receive a pop up unable to launch... I've tried re-booting the system, No Luck. Any sugestions??? The stick works fine on a Windows XP OS.

are you talking about the U3 application? or just accessing the files?

---

### Post by CoCoKnots on 2008-08-10
Just getting the files...

---

### Post by fenT1 on 2008-08-10
```
tail -f /var/log/messages
```

output?

---

### Post by CoCoKnots on 2008-08-10
Thanks, Here is a snapshot of the terminal page... Does this mean that it should work or just inform me of what the issue is... Sorry, I don'r know exactly what I'm looking at.

---

### Post by fenT1 on 2008-08-10
> **CoCoKnots said:**
> Thanks, Here is a snapshot of the terminal page... Does this mean that it should work or just inform me of what the issue is... Sorry, I don'r know exactly what I'm looking at.

just to inform


as you can see from the first line the kernel is reading the removable drive. the other lines are displaying write protect off, you say that  with xp it works, is it the same computer? if no then...

write protect is in your bios. You select "enable" write protect and it will ask you for a password. Note: not all bios versions offer this option.

---

### Post by CoCoKnots on 2008-08-10
Sorry, I used the word 'Launch' in the orginal message... It should be 'Mount'. Thanks

---

### Post by CoCoKnots on 2008-08-10
How do I 'enable' the bios? What is strange is that the stick has been working fine with Ubuntu the last few times I have used it until this evening??? That's why I tried it on another computer... to see if the stick had been damaged.

---

### Post by fenT1 on 2008-08-10
> **CoCoKnots said:**
> How do I 'enable' the bios?

to access the bios you have to restart your computer and press F12 or F2 depending on your computer before the computer start loading the os.

> **CoCoKnots said:**
>  What is strange is that the stick has been working fine with Ubuntu the last few times I have used it until this evening??? That's why I tried it on another computer... to see if the stick had been damaged.


try another usb port before changing the bios settings.

---

### Post by CoCoKnots on 2008-08-11
Ok, I tried re-booting my system. F2 was the correct key to enter the setup. However, the Bios only allows the enable command is activate the boot drive. The memory stick is an older one... I think I'll just save the files I need on the computer with Windows XP & transfer them to a New memory stick drive & see if that works. It may be a good excuse to up grade. I appreciate all of the help. Thanks Again.

---

### Post by fenT1 on 2008-08-11
> **CoCoKnots said:**
> Ok, I tried re-booting my system. F2 was the correct key to enter the setup. However, the Bios only allows the enable command is activate the boot drive. The memory stick is an older one... I think I'll just save the files I need on the computer with Windows XP & transfer them to a New memory stick drive & see if that works. It may be a good excuse to up grade. I appreciate all of the help. Thanks Again.

good option, keep it around it might come in handy later. cheers.):P

---

### Post by penguinv on 2008-08-11
I have an Imation 512 that I got at Target.
NP

just FYI
works with windows, works with mac, works with ubuntu.
now I need to get clamwin to check it...
that's PortableApps for Viruses etc!

---

