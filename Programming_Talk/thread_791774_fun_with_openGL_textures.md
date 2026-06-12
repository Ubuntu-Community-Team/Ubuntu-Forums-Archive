---
title: "fun with openGL textures"
date: 2008-05-12
forum: Programming Talk
---

### Post by destructchaos on 2008-05-12
Hi all,

I recently started developing a 2D rendering engine for an independent research project at my university.  The lab I was working in recently made the switch from openSuse 10.3 to Kubuntu 8.04.  The switch broke all of my texture rendering code in that I can no longer display textures.  If anyone has any ideas as to why the OS switch would break my code, I'd love the assistance.

I've posted the code to my personal web server: [http://www.celtrenicdesigns.com/havoc_src/](http://www.celtrenicdesigns.com/havoc_src/)

Thanks.

---

### Post by jespdj on 2008-05-13
It's hard to say with so little information.

The first thing I would look at is the video driver. Are you using a different video driver, or a different version of the video driver, on Kubuntu?

What exactly goes wrong? Can you still compile your code without errors? What happens if you try to run it, do you get any error messages or does it look wrong? What are the error messages and/or how does the output differ from what you had before/what you expect?

---

### Post by destructchaos on 2008-05-13
The video driver is the same.

The code compiles without producing any errors or warnings.  <-- The frustrating part

When I run the program, where I previously had a 4 squares with 2 different semi-transparent PNGs mapped to them, I now have 4 white squares with nothing mapped to them.

The only difference that I've been able to find between openSuse and Kubuntu is that Kubuntu uses a different version of automake, but that shouldn't affect something as basic as texture mapping in openGL, should it?

---

### Post by jespdj on 2008-05-14
Do you still have binaries compiled on openSuse? What happens if you run those on Kubuntu? If those binaries work and your Kubuntu-compiled binaries don't, then it's very likely a problem with the compiler or other build tools on Kubuntu.

What video card (brand / model) and what driver are you using exactly?

---

### Post by destructchaos on 2008-05-15
OK, it took longer than expected, but I got a VM of openSuse running and recompiled my code on it.  That binary works as expected in openSuse but acts the same as the binary I compiled in Kubuntu when run on Kubuntu.

The video card is an Intel 945.  I'm running the default Intel i810 driver.

---

### Post by prshah on 2008-05-15
> **destructchaos said:**
> 
The video card is an Intel 945.  I'm running the default Intel i810 driver.

The i810 driver is outdated. Use ```
sudo apt-get install xserver-xorg-video-intel
``` to snag the latest driver, then edit your /etc/X11/xorg.conf, and look for the line:> Driver "i810" and change it to > Driver "intel" if it's not already done. Save, logout, restart X server (ctrl+Alt+bksp) and then check.

---

### Post by destructchaos on 2008-05-15
the xserver-xorg-video-intel package is already installed.

Wow, the xorg.conf file has been stripped down in 8.04.  The video card section contains only:
```
Identifier    "Configured Video Device"
```
There is no Driver line any more.

---

### Post by prshah on 2008-05-16
> **destructchaos said:**
> the xserver-xorg-video-intel package is already installed.

Wow, the xorg.conf file has been stripped down in 8.04.  The video card section contains only:
```
Identifier    "Configured Video Device"
```
There is no Driver line any more.

Then just add the line anywhere after the line above: eg:
```
Identifier    "Configured Video Device"
Driver    "intel"
```

---

### Post by destructchaos on 2008-05-16
Driver successfully updated ... no change to program behavior.

---

### Post by destructchaos on 2008-05-17
OK, it's officially not a Kubuntu problem, but a Kubuntu on my machine problem.  I installed Kubuntu in a VM on my machine at home, compiled my code and the program ran as expected, so if anyone has an idea what could be wrong, I'd love the help.  If you need more info about anything, just ask.

Thanks.

---

### Post by destructchaos on 2008-05-18
i hate to do this, but *bump*.  Anyone have any ideas on this one?

---

### Post by rnodal on 2008-06-11
Could you please post the source code at least the part where you create the textures or fix the link that you had?

-r

---

### Post by destructchaos on 2008-08-07
it was a POTS issue where the intel drivers would fail silently while the nvidia drivers would load the textures.  i changed the image from 250x250 to 256x256 and the world was a happy place again.

---

### Post by rnodal on 2008-08-07
I'm happy for you. Those power of two dimensions ](*,).

---

