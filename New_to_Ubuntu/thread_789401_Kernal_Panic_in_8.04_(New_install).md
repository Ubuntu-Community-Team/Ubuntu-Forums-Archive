---
title: "Kernal Panic in 8.04 (New install)"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by DarkNight_DS on 2008-05-10
I just recently jumped into the Ubuntu OS world and have been having an issue with Kernal Panics.  I would like to figure out what is causing the kernal to freeze up and how I can fix it.

I'm not over clocking any of the components in my PC.  Windows XP runs fine on the same system.

I have the following hardware:

Athlon 3800+ X2 S939 winchester core
ATI X800 video card
ASUS s939 motherboard
2 GB of ram (dual channel)
500GB Western Digital HD
Creative Labs Sound Blaster Audigy

The freezes are very random, sometimes within the first few minutes after booting, sometimes after a few hours.  Is there some info I can grab from my box that would help someone see what's happening to my system?

I've run Mtest X86 on the system and it found no errors with my ram.

Probably helps if I mention I'm running the 64 bit version of Ubuntu which I grabbed from Ubuntu.com

Thanks!

---

### Post by joshsmith on 2008-05-10
i'd guess these arent kernel panics unless you have some specific reason to think so. it takes a lot to knock the kernel out.

if it is your system crashing, pressing ctrl+alt+backspace does an instant log out, should get you out of a crash

---

### Post by spiderbatdad on 2008-05-10
As a note, windows must be shut down cleanly prior to booting into ubuntu...not hibernated or force quit.

---

### Post by joshsmith on 2008-05-10
@spiderbatdad
that is not relevant to this problem. although it is true that if ubuntu isnt shut down properly then you may have trouble accessing an ntfs drive as windows locks it, but that is not even slightly related to a kernel panic

---

### Post by spiderbatdad on 2008-05-10
> **joshsmith said:**
> @spiderbatdad
that is not relevant to this problem. although it is true that if ubuntu isnt shut down properly then you may have trouble accessing an ntfs drive as windows locks it, but that is not even slightly related to a kernel panic

Not true imo. Kernel Panic message can be generated simply as an error message when initramfs fails. Not shutting down WINDOWS properly can result in a numbers of hardware/firmware malfunctions when booting Ubuntu. I have been around the forums long enough (member since 2005) to have seen this issue many times...though thanks for your input.

---

### Post by joshsmith on 2008-05-10
ok, maybe i'm wrong. i'll look out for that being a possible issue. 
thanks for telling me

---

### Post by nefrin on 2008-05-10
double posted by accident

---

### Post by nefrin on 2008-05-10
I was also having Kernal Panic issues when I made the recent switch from Vista to Ubuntu. As it turns out, I had a bad RAM stick that was causing segmentation faults (if you are seeing that in the boot up, segfaults are a memory issue).

Here are a couple of tips that were passed to me to check to see if you are having a RAM issue that is causing the panics:

[I]When a program crashes, run this in terminal, look for consistant messages

dmesg | tail -n 30 | less[/I]

This will display the last 30 messages your computer is sending internally. 

This script help me greatly in trouble shooting my Kernal Panic and random program shutdowns. Hope you find them as useful.

---

### Post by DarkNight_DS on 2008-05-11
I have been shutting down windows properly.  

Basically I assumed it was a kernal panic due to my scroll lock and caps lock lights flashing on my motherboard.  Can I still use the ctrl-alt-backspace command to get me out of these things?

If I can.. I'll definitely use the command to check my last 30 commands.

---

### Post by DarkNight_DS on 2008-05-11
Update:  My computer crashed again, this time it was a full up lock for sure.  Ctrl-alt-backspace did nothing for me and I had no flashing lights on the keyboard.  It happened when I clicked on a samba network share which was auto mounted on my desktop.

---

### Post by SunnyRabbiera on 2008-05-11
how did you install ubuntu might I ask?

---

### Post by DarkNight_DS on 2008-05-11
I grabbed the iso from ubuntu.com burned it to disc using nero.  I then installed it by resizing and partitioning my Windows NTFS drive through the Ubuntu installation.

---

### Post by DarkNight_DS on 2008-05-13
Does anyone have any insight for me?

---

### Post by DarkNight_DS on 2008-05-17
I'm still hoping to get this fixed.  So if anyone has any more input for me I'd gladly take it and supply back details.  I want to run Ubuntu on my PC so please, any help is appreciated.

---

