---
title: "Startup USB works fine, Install won't finish booting?"
date: 2011-10-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by crjackson on 2011-10-09
Okay, the USB stick I've been using for testing works great on my desktop. Compiz all apps etc...

I decided to install to HD and now I can't get splash screen, and then it just stops altogether at the LightDM loading line [failed]

I have an nVidia 8800 graphics card and I think this MIGHT be the issue. I booted into the recovery terminal, got all the updates and tried again but same issue.

Why would the video driver on the LiveUSB work perfectly and not an installed version.

How can I get back to a functional desktop on this system?

Laptop with Intel video works fine...

---

### Post by Spr0k3t on 2011-10-09
I've got a crazy garbled screen before the system shows the boot logo.  When I hit CTRL-ALT-DEL, it boots fine.

---

### Post by crjackson on 2011-10-09
I get a text screen while loading which has

* stopping automatic crash report generation [fail]

* starting load fallback graphics devices [fail]

* starting LightDm Display Manager [ok]

it never goes any further than that.

ctrl-alt-delete only causes a reboot.

---

### Post by crjackson on 2011-10-10
Any suggestions?

---

### Post by harry_r_s on 2011-10-10
Try installing a driver for Linux from the nvidia website!

---

### Post by crjackson on 2011-10-10
> **harry_r_s said:**
> Try installing a driver for Linux from the nvidia website!

That didn't work. Going back to 10.10.  Maybe the next release will work for me.

---

### Post by lidex on 2011-10-10
Geforce 8800 GTS here working with no problems. Are you using the nvidia-current driver and have you generated an xorg.conf file with:
```
sudo nvidia-xconfig
```

---

### Post by MAFoElffen on 2011-10-10
You have 2 threads going on the same?  Refer to my post on your other thread: [http://ubuntuforums.org/showthread.php?t=1857588](http://ubuntuforums.org/showthread.php?t=1857588)

---

### Post by crjackson on 2011-10-10
> **MAFoElffen said:**
> You have 2 threads going on the same?  Refer to my post on your other thread: [http://ubuntuforums.org/showthread.php?t=1857588](http://ubuntuforums.org/showthread.php?t=1857588)

MODS, please close this thread.

---

### Post by lisati on 2011-10-10
> **crjackson said:**
> MODS, please close this thread.

Done.

---

