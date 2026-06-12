---
title: "[SOLVED] svideo grief"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by erutufon on 2008-08-28
Hi
I am trying to get svideo output to a tv, so i can watch things straight from the computer onto the tv.  I have a radeon 7000 graphics card and am running ubuntu 8.04.  I tried the method in the wiki from a fresh install, and have had no luck - it seems to have left me a low graphics mode.  I have been banging my head against this problem for ages now - can anyone help?

---

### Post by LowSky on 2008-08-28
Have you installed the ATI drivers?

---

### Post by erutufon on 2008-08-28
I had major problems so i installed ubuntu again.  it worked, and I was able to get the visual effects up to "extra", so i assumed the correct drivers were installed.

---

### Post by overdrank on 2008-08-28
> **erutufon said:**
> I had major problems so i installed ubuntu again.  it worked, and I was able to get the visual effects up to "extra", so i assumed the correct drivers were installed.

Hi and have you tried using the display configure  ```
gksu displayconfig-gtk
```

---

### Post by erutufon on 2008-08-28
hi and thanks for the reply!
I have tried using the display config code you mentioned, but I get a single option, with no way to add screens or change anything.  Is this me being a moron, or somethign else? (I am regularly a moron!)

---

### Post by erutufon on 2008-08-28
the graphics card option on the gksu displayconfig-gtk screen is reading ati ATI mach 8 mach 32 mach 64.....
when I select the driver by name (the generic RADEON) then I get to a test screen that is a mixture of grey and green dots.

---

### Post by overdrank on 2008-08-28
> **erutufon said:**
> the graphics card option on the gksu displayconfig-gtk screen is reading ati ATI mach 8 mach 32 mach 64.....
when I select the driver by name (the generic RADEON) then I get to a test screen that is a mixture of grey and green dots.

Hi and yes that has been my experience as I stated in a thread this day. You may still save the settings and try it after reboot. If the option fails you can use xfix option by booting into recovery mode and fix your graphics. Although ati has stopped support on this model and others older than the 9500.

---

### Post by erutufon on 2008-08-28
ok thanks - will give that a try

---

### Post by erutufon on 2008-09-03
have been trying to solve this problem for a while now, and have tried using the advice on the wiki and the ati drivers page. I had no luck - seemed to run into errors on the wiki page, and my skills at terminal are pretty low as I'm a noob.

the aim was to get a "media pc", which would plug into the tv via the svideo, so that (legally downloaded) films could be watched without burning to disk, as well as internet on the tv etc.

So after a fair amount of faffing, I got the computer to spit out a tv out through the svideo, but only if the pc was in low graphics mode. I achieved this by going through each radeon driver in turn, testing it out and hoping it would work. one of them did, but with low graphics mode the monitor looked crap. So i thought I would tweak it, to sort it out. I broke it (foolish). after a fresh install, I couldn't get it to work at all, and was mightily pissed off. In frustration, i thought to try another distro, and put a Freespire disk into the cd drive and booted it up. this worked first time, pretty much. I had to change the graphics drivers to VESA, which I could do on the set up screen as I was installing. Within half an hour, i could watch computer output on the tv.

If anyone else has the same problem (radeon 7000, can't get the tv output to work), then i recommend trying freespire. I am still using ubuntu on another pc, because I like it, understand it (a bit) and it's good. but for this application, it seems like freespire is simply a lot easier to set up, particularly for a noob. As for freespire itself, it seems a bit strange and clunky after ubuntu, but I think as i get used to it, it should be fine.

---

