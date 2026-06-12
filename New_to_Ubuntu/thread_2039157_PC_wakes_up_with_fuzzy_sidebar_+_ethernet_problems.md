---
title: "PC wakes up with fuzzy sidebar + ethernet problems (Compiz?)"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by Aquanet on 2012-08-08
Whenever my pc wakes up from suspension the left and top sidebars seems fuzzy as if a driver or something crashed. I'm not sure what's causing it but it seems related to compiz. 

My internet doesn't work after waking up either, I have to disconnect it then plug it back in, then turn on the wired connection in the system settings.

specs:
Ubuntu 12.04 (32bit)
AMD Athlon(tm) 2.1GHz X2 Dual Core Processor BE-2350
nVidia GeForce 6150SE (integrated graphics)
2GB RAM

---

### Post by Aquanet on 2012-08-08
bump

I also had a problem with the screen going blank and saying "Out of range" but I think I fixed that by editing grub.

---

### Post by audiomick on 2012-08-08
> **Aquanet said:**
> bump

It is considered polite to wait a day or so before you bump a thread. 

> 
I also had a problem with the screen going blank and saying "Out of range" but I think I fixed that by editing grub.

I can't see changing your grub file making a difference to and "out of range" error message. That indicates that your video card is doing something incorrectly, and grub doesn't have any influence on video cards that I am aware of. Had you changed anything else?

It occurs to me to ask if you are using the appropriate nVidia proprietary drivers for that video card?

I have seen a similar problem on my laptop that it loses my 3G dongle when it goes into suspend. I don't know why, though. Sorry.

---

### Post by Aquanet on 2012-08-08
> **audiomick said:**
> It is considered polite to wait a day or so before you bump a thread.Thanks for the reply. I looked for anything indicating this in a sticky or announcement but found nothing. I know large forums tend to have regulations for it.


> I can't see changing your grub file making a difference to and "out of range" error message. That indicates that your video card is doing something incorrectly, and grub doesn't have any influence on video cards that I am aware of. Had you changed anything else?I'm not exactly sure what to tell you but this site is what I used:
[http://ubuntuguide.net/monitor-signal-out-of-range-problem-in-ubuntu-12-04-precise-fresh-installation](http://ubuntuguide.net/monitor-signal-out-of-range-problem-in-ubuntu-12-04-precise-fresh-installation)
 
I changed "#GRUB_GFXMODE=640x480" to 1920x1080

> It occurs to me to ask if you are using the appropriate nVidia proprietary drivers for that video card?

I have seen a similar problem on my laptop that it loses my 3G dongle when it goes into suspend. I don't know why, though. Sorry.Well, I'm provided with four options and I'm not sure which is the right one to use, none seem to fix the issue however.

[[IMG]http://i.imgur.com/T0J0js.png[/IMG]](http://imgur.com/T0J0j)
^ I set my settings to use the first option, but just haven't restarted the pc yet.

---

### Post by audiomick on 2012-08-08
> **Aquanet said:**
> I'm not exactly sure what to tell you but this site is what I used:
[http://ubuntuguide.net/monitor-signal-out-of-range-problem-in-ubuntu-12-04-precise-fresh-installation](http://ubuntuguide.net/monitor-signal-out-of-range-problem-in-ubuntu-12-04-precise-fresh-installation)
 
I changed "#GRUB_GFXMODE=640x480" to 1920x1080


Ok, you're right of course. That relates to the resolution that is used during the boot process. 

> 
Well, I'm provided with four options and I'm not sure which is the right one to use.

I generally stick to the one that has "reccomended" after it. I think that is the best idea unless you have concrete reasons to use a different one. I have seen the odd thread here and there where people were having problems with the reccomended (newer) driver and had to use and older one, but I doubt if that is relevant to you.

I'm afraid I can't really help you with your resume problems, then. Sorry. I hope someone else turns up who is more useful.

---

### Post by Aquanet on 2012-08-08
> **audiomick said:**
> Ok, you're right of course. That relates to the resolution that is used during the boot process. Alright 

> I generally stick to the one that has "reccomended" after it. I think that is the best idea unless you have concrete reasons to use a different one. I have seen the odd thread here and there where people were having problems with the reccomended (newer) driver and had to use and older one, but I doubt if that is relevant to you.

I'm afraid I can't really help you with your resume problems, then. Sorry. I hope someone else turns up who is more useful.
I'll switch to the recommended and see if I have any further issues.

As for the other problems, yeah hopefully someone else can help. :)

---

### Post by Lingadharini on 2012-08-08
Your video driver clashes with the settings of compiz. Try removing compiz, everything will come back to normal.
I had the same problem. My dual boot system always gets problem with my display driver in my windows 7. So, I removed compiz in my lucid and everything is back to normal now.

---

### Post by Aquanet on 2012-08-08
> **Lingadharini said:**
> Your video driver clashes with the settings of compiz. Try removing compiz, everything will come back to normal.
I had the same problem. My dual boot system always gets problem with my display driver in my windows 7. So, I removed compiz in my lucid and everything is back to normal now.

Thanks I switched to 2D, but I won't know if it's fixed until the comp goes into suspension.

---

### Post by Aquanet on 2012-08-09
> **Lingadharini said:**
> Your video driver clashes with the settings of compiz. Try removing compiz, everything will come back to normal.
I had the same problem. My dual boot system always gets problem with my display driver in my windows 7. So, I removed compiz in my lucid and everything is back to normal now.

Okay, yep you were right, that was the issue with the sidebars / graphics. Thanks. :)

The network connection was still mot working though, but it's real simple to work around, it's alright if there's no known solution.

---

### Post by Aquanet on 2012-09-10
> **Aquanet said:**
> 

I also had a problem with the screen going blank and saying "Out of range" but I think I fixed that by editing grub.

I fixed the problem. The issue was that GRUB couldn't handle the resolution I was setting it to boot in(1920x1080), so I used Grub Customizer and set it to 800x600.

Thread can be closed now.

---

