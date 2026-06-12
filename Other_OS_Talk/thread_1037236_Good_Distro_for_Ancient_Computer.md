---
title: "Good Distro for Ancient Computer?"
date: 2009-01-11
forum: Other OS Talk
---

### Post by Captain Hat on 2009-01-11
Hey, I've got this old computer on me, It's currently got Windows 98, 48 mb of RAM, a 300 Mhz processor, and a 4 GB hard disc. I decided to just convert it into a Linux system to give it some new life and to perhaps use it as a platform to mess around with the system without endangering the files on my main computer.

I tried a version of Ubuntu that used GTK+ 1.2 or so, and was supposed to be for older computers, but never got anywhere with it. DSL didn't work either, it would freeze up in the middle of loading and would never do anything else.

So if you could suggest some for me to try, I'd appreciate it.

---

### Post by Grant A. on 2009-01-11
[http://www.puppylinux.org/]("http://www.puppylinux.org/")

---

### Post by cardinals_fan on 2009-01-11
NetBSD would be my choice.  A command-line Slackware system might be nice too.

---

### Post by Sprut1 on 2009-01-11
> **Grant A. said:**
> [http://www.puppylinux.org/]("http://www.puppylinux.org/")

+1, I vote for this too, it runs so well, I just love it.

---

### Post by ugm6hr on 2009-01-11
Most modern GUI distros will struggle.

Surprised DSL won't boot.  I have used it (v3.x) on something similar before (P2 / 36MB RAM).

Delilinux *might* boot, but I think the latest now requires 64MB too.

---

### Post by Bungo Pony on 2009-01-11
I'm also surprised that DSL doesn't work on it. I have yet to find a computer (with lower specs than a 486 with 16M RAM) that DSL *won't* run on.

Try installing DSL onto the hard drive using a different PC, and then transplant the HD back into your old 300 MHz machine. That's usually what I do when I encounter a computer that won't boot off a CD. It may work for stubborn hardware like yours.

---

### Post by blackened on 2009-01-11
> **Captain Hat said:**
> Hey, I've got this old computer on me, It's currently got Windows 98, 48 mb of RAM, a 300 Mhz processor, and a 4 GB hard disc. I decided to just convert it into a Linux system to give it some new life and to perhaps use it as a platform to mess around with the system without endangering the files on my main computer.

I tried a version of Ubuntu that used GTK+ 1.2 or so, and was supposed to be for older computers, but never got anywhere with it. DSL didn't work either, it would freeze up in the middle of loading and would never do anything else.

So if you could suggest some for me to try, I'd appreciate it.

You may need to use the syslinux version of dsl (info [here]("http://damnsmalllinux.org/wiki/index.php/Which_File_do_I_download%3F_(long_version)")). I recently had to use it on an old laptop and it worked a charm with the proper boot options.

---

### Post by exploder on 2009-01-11
SliTaz should run on those specs.

[http://www.slitaz.org/en/get/](http://www.slitaz.org/en/get/)

---

### Post by cardinals_fan on 2009-01-11
> **exploder said:**
> SliTaz should run on those specs.

[http://www.slitaz.org/en/get/](http://www.slitaz.org/en/get/)
Yes, but not very well.

---

### Post by exploder on 2009-01-11
> Yes, but not very well. 

For me it only used 30 MB of RAM. I don't think there is much out there that will use less.

---

### Post by cardinals_fan on 2009-01-11
> **exploder said:**
> For me it only used 30 MB of RAM. I don't think there is much out there that will use less.
CLI SliTaz should use ~18 MB.  I wouldn't run X on that machine.

---

### Post by fistfullofroses on 2009-01-11
+1 for SliTaz

It's the most lightweight but functional distribution I have seen in quite sometime. I would certainly run X on that machine. You wouldn't be able to run a full X server implementation, but TinyX or Xvesa should be just fine. Note that these are stripped X servers and you will not have all of the functions of a normal X Windows system (just a GUI with keyboard and mouse). If the machine will do vesa modes in CLI you can use a small X.

---

### Post by |{urse on 2009-01-11
knoppix, at those bus speeds an old 48x cd-rom is better than the then current hdd technology for the unit. I'd use a flash drive for your persistent $home.

---

### Post by cardinals_fan on 2009-01-11
> **fistfullofroses said:**
> +1 for SliTaz

It's the most lightweight but functional distribution I have seen in quite sometime. I would certainly run X on that machine. You wouldn't be able to run a full X server implementation, but TinyX or Xvesa should be just fine. Note that these are stripped X servers and you will not have all of the functions of a normal X Windows system (just a GUI with keyboard and mouse). If the machine will do vesa modes in CLI you can use a small X.
In my opinion, Xvesa > regular Xorg.

---

### Post by Sorivenul on 2009-01-11
[FreeDOS]("http://www.freedos.org/") + [OpenGEM]("http://gem.shaneland.co.uk/"). 

Or [Tiny Core Linux]("http://www.tinycorelinux.com/").

---

### Post by zmjjmz on 2009-01-11
DeLi would be a nice option. Hell, you could buy a bunch of small hard drives and install different lightweight operating systems on each one and then swap them out when you want a different OS.
So following that, among my suggestions would be:
DSL (try transplanting it), DeLi, BasicLinux, and FreeDOS + OpenGEM.
Those are what I've personally tried on similar machines (worse, actually), but some that I'd like to try are:
TinyCore Linux, Visopsys, Tiny Linux, ttylinux, and AROS.

---

### Post by ugm6hr on 2009-01-12
> **zmjjmz said:**
> .. and AROS.

I'd like to see that working too. It should certainly run well on old hardware.

Is it in a usable state at the moment (i.e. networking / USB support etc)?

---

### Post by K.Mandla on 2009-01-12
If it's an i686, you could run Arch on it. If it's anything else, you could run Debian on it. 

I'd put Crux on it, but I am biased. ;)

What kind of graphics card is in it?

---

### Post by snowpine on 2009-01-12
SliTaz is probably too "heavy" for that computer. I recommend 128mb of ram for stable or 160mb for cooking. You might be able to boot the "loram" flavor with only 48mb of ram, but it will probably crash as soon as you try to start Firefox. You really need a distro with a lightweight browser such as dillo or links.

My suggestion is keep trying with DSL; have you asked over on their forums to try and troubleshoot?

---

### Post by Grant A. on 2009-01-12
> **Sorivenul said:**
> [FreeDOS]("http://www.freedos.org/") + [OpenGEM]("http://gem.shaneland.co.uk/"). 

I wouldn't say the computer is THAT bad. I mean, isn't that the equivalent of Windows 3.11 with Progman? He might be able to atleast use icewm or jwm with puppy. If all else fails though, that would be the last choice.

---

### Post by ugm6hr on 2009-01-12
> **Grant A. said:**
>  He might be able to atleast use icewm or jwm with puppy.

Not sure about that.  48MB was certainly not enough for Puppy2.14.

---

### Post by mikjp on 2009-01-14
Memory is certainly the bottleneck in your case. Installation with a live CD is out of the question, you need a distro that has a text mode installer.

I've used on a Pentium 100 with 40 MB RAM both Debian 3.1 and Slackware 11. 

I suggest you to try Slack 12.2 with a lightweight window manager (pekwm, openbox, windowmaker etc).

Greetings,

Mikko

---

### Post by Sabayon on 2009-01-14
Hehehe Ancient Computer. I wonder if xfce or maybe a version xubuntu would work.

---

### Post by mikjp on 2009-01-24
> **Sabayon said:**
> Hehehe Ancient Computer. I wonder if xfce or maybe a version xubuntu would work.

No, they would not.

mikko

---

### Post by fistfullofroses on 2009-01-24
> **Captain Hat said:**
> Hey, I've got this old computer on me, It's currently got Windows 98, 48 mb of RAM, a 300 Mhz processor, and a 4 GB hard disc. I decided to just convert it into a Linux system to give it some new life and to perhaps use it as a platform to mess around with the system without endangering the files on my main computer.

I tried a version of Ubuntu that used GTK+ 1.2 or so, and was supposed to be for older computers, but never got anywhere with it. DSL didn't work either, it would freeze up in the middle of loading and would never do anything else.

So if you could suggest some for me to try, I'd appreciate it.

THERE IS A STICKY THREAD FOR THIS QUESTION... please look there before asking.

---

### Post by Ed. Yang on 2009-02-05
Hi CaptainHat.

I've received an old computer that's close to your specs as well.
I've really burned lot's of hours just to get the machine to run.

I've tried out various small sized distros such as LXDE or FLUXBUNTU, and even XUBUNTU. Non of these works. I guess it may have to to with the compatibility of the processor....
The biggest problem that i encountered frequently was "kernel panic"s, as well as optical drive failures... and it just goes on and on...until i came to puppylinux.

I've tried version 4.12, doesn't work... tries with 4.11...
It works.

Maybe you can go with this distro as well...

---

### Post by mpsii on 2009-02-05
My vote goes for DSL or Puppy, since you only have 48MB of RAM.

---

### Post by punx45 on 2009-02-06
how about floppix [http://floppix.ccai.com/](http://floppix.ccai.com/)

it fits on 2 floppies and runs completely from ram!

hmm.. no HDD support, maybe not so useful.

or try the server edition of ubuntu.   no gui by default.   pretty light on the disk space too i think, since it leaves out most of the friendly user apps.

or you could be real Uber and start with just a kernel.. no clue how to go about that haha..

---

### Post by darrelljon on 2009-02-07
Floppix is command line only.

---

### Post by jay576 on 2009-02-08
DeLi is cool and runs on 486 up so your computer should run it.
[http://www.delilinux.org/](http://www.delilinux.org/)

---

### Post by zmjjmz on 2009-02-08
Regarding floppy distros, BasicLinux is a good choice. 2 floppies, and it's extendable through provided kernel modules. It initially supports HDDs so you can do HDD installs out of the floppy. (They take a bit of work though)

---

