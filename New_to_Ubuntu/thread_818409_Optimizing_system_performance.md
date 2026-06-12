---
title: "Optimizing system performance"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by 625 on 2008-06-04
Hey folks. I've been using Linux for a little while, and I'm enjoying it enough to consider using it as my primary OS. As such I'd like to get things running as well as possible and hammer out some of my (admittedly few) problems.

Something I can't help but notice is that scrolling through pretty much anything, especially in Firefox, can get a bit choppy. Framerate drops significantly on webpages with large animated images, and flash is extremely choppy, uselessly so in the case of something fullscreened. Enabling the NVidia restricted drivers appeared to help, but certainly not to the extent expected.

Presumably unrelated, but also irksome, is that when playing a ROM in ZSNES, as smoothly as the game may run, the input from my gamepad seems to be on just enough of a delay to make any game requiring timely response all but unplayable.


New to this as I am, I can only assume there are changes, no doubt obvious ones that I never thought of, that I can make to improve system performance ever so slightly.

System specs:
Ubuntu 8.04
Athlon 64 3500+
1 GB RAM
Geforce 8600 GT
/ and /home on separate ext3 partitions on a dual-platter 640 GB SATA
PS2 controller connected via USB Trio Linker Plus

I'll be more than willing to provide any more information as requested, and will readily report on any suggested actions.

---

### Post by 625 on 2008-06-04
Oh, and I'm running the default Gnome-based desktop environment, if that might have anything to do with it, but when I tried them, fluxbox and xfce either didn't appear to do much better or did a little worse.

---

### Post by sayakb on 2008-06-04
Maybe this would help: [http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php](http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php)

---

### Post by 625 on 2008-06-04
That helps a bit. Flash is smoother, ZSNES is more responsive, but there's still room for improvement. If the system monitor is to be believed, CPU load seems to sit at about 25%-40% with nothing in particular going and about 60% with Firefox idling. While I'm not quite sure I trust that reading, something sure seems to be up.

---

### Post by 625 on 2008-06-05
Oh god any other suggestions? I'm not running any extraneous or particularly busy processes. Should I try to install newer video drivers, or a lighter weight desktop environment?

---

### Post by thinkpeace on 2008-06-12
I would like some more suggestions as well, as I also suffer from choppiness

---

### Post by gr4nf on 2008-06-12
a nibler desktop would help. try xfce4.

---

### Post by philinux on 2008-06-12
With your specs you should be flying.

Use

top

in the terminal or install htop and use that to see whats hogging the cpu.

It could be trackerd, you can turn it off in Prefs> Search and indexing.

---

### Post by Sinkingships7 on 2008-06-12
The reason your system monitor is telling you that you are using about 25-40% processing power is because of the monitor itself. Always been a bit of an annoyance if you ask me. The system monitor requires processing power to render the "graphics" you see scrolling to the left, giving you a chart of what your resources look like.

---

### Post by philinux on 2008-06-12
> **Sinkingships7 said:**
> The reason your system monitor is telling you that you are using about 25-40% processing power is because of the monitor itself. Always been a bit of an annoyance if you ask me. The system monitor requires processing power to render the "graphics" you see scrolling to the left, giving you a chart of what your resources look like.

Agreed, top is better for this.

---

### Post by thinkpeace on 2008-06-20
I downloaded htop, and everything looked fine.  only 8 or 9% of my cpu was being used.  But as soon as I open firefox or openoffice or anything the program on the top jumps up to 100%.  This is when I get choppiness.  I have no idea what that program is.  Can anyone tell me what it is?  edit: I attached a screenshot.


thanks for all the help

Andrew

---

### Post by markbuntu on 2008-06-20
Tracker uses a lot of cpu when you use any app that uses the file system It does nothing for me so I turned it off. 

You can go to System/Adminstration/Services and turn off all the stuff you don't use like Palm and bluetooth and braille and tracker, etc. You can also use Boot Up Manager (bum) to stop a lot of extraneous stuff from loading at boot. bum is in the repository.

If you have your desktop set to transparent and are running atlantis or gears or something in the cube, that will use a lot of your cpu all the time.

---

