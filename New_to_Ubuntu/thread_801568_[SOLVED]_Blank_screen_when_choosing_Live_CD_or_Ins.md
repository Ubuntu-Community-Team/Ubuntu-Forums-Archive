---
title: "[SOLVED] Blank screen when choosing Live CD or Install"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by BlakTygr on 2008-05-20
Hi all. New guy here and very new to Linux.

[LIST]
[*]ASUS P4P800S Motherboard
[*]ACPI x86 based pc
[*]Intel Pentium 4 CPU 3.00 GHz
[*]NVIDIA Geforce FX5200 (Microsoft Corporation WDDM)
[*]SoundMAX Integrated Digital Audio
[*]Vista (Home Basic)
[/LIST]

When I boot from the CD and choose either the Live CD or Install option, I get a small, blinking, lonely, horizontal cursor in the upper left corner of a black screen. what am I doing wrong or what hardware is incompatible to Ubuntu in my system? :confused:

I appreciate any help with this.

---

### Post by shifty_powers on 2008-05-20
do you know what version you downloaded?

edit: and have you tried the check cd for defaults option?

---

### Post by bumanie on 2008-05-20
As long as the md5checksum was OK on the download and that the burn was Ok, you should try the alternate cd. It is text based and often installs on systems that have similar problems to what you are describing.

---

### Post by BlakTygr on 2008-05-20
> **shifty_powers said:**
> do you know what version you downloaded?

edit: and have you tried the check cd for defaults option?

Hey Shifty ):P , thanks for replying.

Answer
[LIST]
[*]Ubuntu 8.04
[*]I verified the md5 sum of the .iso file and checked to make sure that all files were burned to the CD. I think I did the check CD option also. I know I did a memory test ( didn't need to, I have a Gig of memory). I might have to do what the guy below you said to do.
[/LIST]

---

### Post by BlakTygr on 2008-05-20
> **bumanie said:**
> As long as the md5checksum was OK on the download and that the burn was Ok, you should try the alternate cd. It is text based and often installs on systems that have similar problems to what you are describing.

Hey bumanie ):P , thanks for replying.

Yes I did a md5checksum and the burn was fine for the CD. I guess i'll have to go the Alternate CD route and hope for the best.

Wish me luck!

---

### Post by BlakTygr on 2008-05-23
Hi everyone,

OK...Yesterday I finally figured this thing out and I'm embarrased to say that the answer was right in front of my face included in the menu. The F6 boot options. Ubuntu has a problem booting from my machine because of the ACPI/APIC sytem in my Bios I guess. So in the F6 boot options I checked "acpi=off" and "nolapic". Pressed enter for the Live Cd option and it booted. Yes! I had fun checking out some of the main features I was interested in and decided that this would be a fun OS that I can get to learn. So I installed it. You'll have to check my other thread to see what problem I ran into next. but for now the booting the Live CD issue has been solved for me. I hope this can help someone else or give them an idea of how to boot the Live CD.

---

