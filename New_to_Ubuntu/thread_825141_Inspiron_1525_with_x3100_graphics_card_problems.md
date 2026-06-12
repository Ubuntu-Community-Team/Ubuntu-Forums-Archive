---
title: "Inspiron 1525 with x3100 graphics card problems"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by cjdawson73 on 2008-06-10
Absolute newbie here. Running 8.04. Haven't been able to find much to help me that worked. during boot up system enters 'safe' graphics' mode. after startup, i go to screen resolution, it says 'cloned output', wont let me select anything other than 1280 x 800. I'm trying to:

1. Get the laptop to startup without error
2. Enable visual effects
3. Use external display (dell widescreen)

how do install the latest driver? it doesn't seem that card is detected?

thanks for any tips.

---

### Post by cjdawson73 on 2008-06-11
Okay, i've to it start up without error, exteranal monitor does work (resolution is right but it seems fuzzy). desktop effects do not work though. Any ideas?

---

### Post by cjdawson73 on 2008-06-11
this doesn't look right

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by mgranet on 2008-06-11
I believe I read here a while back that the X3100 has been blacklisted on Compiz due to some bugs. Here's how to force it:

1) ALT + F2
2) gksudo gedit /usr/bin/compiz
3) Add a [#] in front of [T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" # intel 965] to turn it into a comment rather than delete it (minus the [])

---

### Post by cjdawson73 on 2008-06-11
thanks, but when i ran it, it did not contain "T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" # intel 965

---

### Post by kanati on 2008-06-11
I can't really help you with your problem, but I have an x3100 in my Inspiron 1420 and it works with compiz-fusion just fine.  At least that confirms that it should be possible.  I should mention that I originally installed the Dell modified version of 7.04 which didn't work with desktop effects.  The unmodified version of 8.04 has worked perfectly for me.

---

### Post by danbodoh on 2008-06-13
I've been running compiz and effects on a 1525 since 7.10 (Ubuntu-supplied, not-dell-supplied OS) with no problems.  Can you post your /var/log/Xorg.0.log?

Dan Bodoh

---

### Post by cjdawson73 on 2008-06-13
here it is

---

### Post by danbodoh on 2008-06-13
Looks like your loading some kind of nvidia glx module, which eventually fails.  There shouldn't be any nvidia stuff in /etc/X11/xorg.conf (unless you have an nvidia card in your inspiron 1525?)

Here's the modules section of my /etc/X11/xorg.conf:

```

Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
        Load            "dri"
EndSection

```

Dan Bodoh

---

