---
title: "Cannot &quot;Try&quot; Ubuntu and cannot install from both USB and DVD"
date: 2014-10-27
forum: New to Ubuntu
---

### Post by Gloris_Ian on 2014-10-27
Hey! I decided to give Ubuntu a try after trying it at my local library, I red a lot of fine reviews plus, I was always concerned about security, and decided to ditch windows, however, I am having multiple issues with: 1. installing ubuntu and 2. trying ubuntu live

First of all, I am an absolute newbie when it comes to unbuntu so please bear with my idiocy. I am knowledgable when it comes to windows.

Details: Ubuntu 14.04. LTS burned with Universal USB Installer, 1.9 to USB, also burned on a DVD with Nero. It was an ISO downloaded from the official Ubuntu website. Also, burned it to dvd properly, not just "copy - paste" i know it wouldn't work that way.

Issue 1: Happens when i &#8222;try&#8220; Ubuntu live without installing it to any HDD. What happens is that first after it loads to desktop, weird artifact and glitches start to occur, like tiny orange dots and tiny lines that move around slowly sometimes rapidly. That is bearable, however, after 30 or so seconds into my &#8222;try&#8220; session, the screen and everything hangs and I have no option and can't do anything, I just have to restart my PC. Confirmed that it happens every single time after 10+ tries- Happens on both USB and CD Ubuntu boot. Issue is the same no matter the usb or dvd.

Issues 2: Happens when I attempt to install Ubuntu, without deleting/overwriting windows, I choose the option of installing besides it. What happens is that in the middle of install it just stops and I get the following error message: &#8222;The installer encountered an unrecoverable error&#8220; and then it just hangs. Happens on both Usb and dvd doesn't matter. Also, the entire process of installation up to the error happens with the orange dots and artifacts until hang. Not in live session, I can't do it in live session since it hangs after 30 or so seconds, read issue 1.
 
Any help would be greatly appreciated, help a fellow would-be Ubunter!

---

### Post by sudodus on 2014-10-27
Welcome to the Ubuntu Forums :-)

I think you have problems with the driver for the graphics card, but it might be something else, so please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It helps us give relevant advice.

You can also start looking at a wiki page, how to add boot options. Maybe the first one to try is nomodeset.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by haplorrhine on 2014-10-27
I had installation problems trying to install 32-bit (i386) on a 64-bit processor.

You can see your processor architecture from terminal with
```
uname -p
```

---

### Post by Gloris_Ian on 2014-10-27
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

I think you have problems with the driver for the graphics card, but it might be something else, so please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It helps us give relevant advice.

You can also start looking at a wiki page, how to add boot options. Maybe the first one to try is nomodeset.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Brand name and model: ASUSTek, don't know which model is, how do I find that out?
CPU: Intel Pentium G840 @ 2,8GHz
RAM (size): 4 GB
graphics: AMD RAdeon HD 6570
wifi chip/car: don't use wifi, I use wired internet, modem is SAGEM 2604

Nomodeset? Sorry I am not following you, can't find it anywhere on that link you gave me

---

### Post by Gloris_Ian on 2014-10-27
> **haplorrhine said:**
> I had installation problems trying to install 32-bit (i386) on a 64-bit processor.

You can see your processor architecture from terminal with
```
uname -p
```

My CPU is 64, and I checked, I downloaded the correct Ubuntu 64 version I believe it is

---

### Post by deadflowr on 2014-10-27
When you boot and get the Ubuntu menu to select the install, try, check disk stuff, press F6 options and, I believe you press the spacebar to highlight the selections given. Here select nomodeset, then press ESC and then try booting.

---

### Post by Gloris_Ian on 2014-10-27
> **deadflowr said:**
> When you boot and get the Ubuntu menu to select the install, try, check disk stuff, press F6 options and, I believe you press the spacebar to highlight the selections given. Here select nomodeset, then press ESC and then try booting.

Will do, thanks, gonna reply here when I do it

---

### Post by sammiev on 2014-10-27
When you boot from the media select F6 from the menu at the bottom of the screen and select Nomodeset.

---

### Post by sudodus on 2014-10-27
I suspect that the kernel has problems to cooperate with the Radeon graphics, so continue to explore one or several boot options (you can test with more than one at the same time).

---

### Post by Gloris_Ian on 2014-10-27
> **sudodus said:**
> I suspect that the kernel has problems to cooperate with the Radeon graphics, so continue to explore one or several boot options (you can test with more than one at the same time).

Ok, I used *check disk for defects* and it said No errors found for DVD, but it did find 4 errors for USB, not sure if that helps.

Also, tried booting unbuntu with NOMODESET to try it without installing, works fine, no graphical errors or glitches, and no hanging or freezing. Thinking about trying to install with nomodest but what If I install and then it hangs with old error message? Then I ruined the partition and wasted space?

---

### Post by sudodus on 2014-10-27
If you add nomodeset after the the dashes in the boot line

.... some boot options -- nomodeset

it will be ported to the installed system, which should make it work.

The disk space is never wasted. Maybe time is wasted, but the disk space can be re-used.

---

### Post by Gloris_Ian on 2014-10-27
> **sudodus said:**
> If you add nomodeset after the the dashes in the boot line

.... some boot options -- nomodeset

it will be ported to the installed system, which should make it work.

The disk space is never wasted. Maybe time is wasted, but the disk space can be re-used.

Well, not exactly wasted, what I meant to say was, could it corrupt my windows partition if it hangs in the middle of the install process? Anways, thank for all your help so far, gonna try this out tommorow and gonna let you know!

---

### Post by sudodus on 2014-10-27
If it gets stuck and hangs during installation will not damage Windows. But if you use 'Install alongside' it might do that. Instead you should select ***'Something else'*** at the partitioning window. This means 'Manual partitioning', and you have full control of what will happen.

If you are not sure what to do (the meaning of the alternatives), please ask here. Several people are able to help, different persons depending on the time (of day) you ask.

---

### Post by Gloris_Ian on 2014-10-28
Managed to install with nomodeset a fresh ubuntu alongside windows for now. Probably gonna ditch it alltogether eventually, anyhow, no Issues detected so far, so thanks! :)

---

### Post by sudodus on 2014-10-28
Congratulations :KS

... and when you feel that the problem of this thread is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

