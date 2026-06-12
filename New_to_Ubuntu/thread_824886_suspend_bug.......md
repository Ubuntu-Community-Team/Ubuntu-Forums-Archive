---
title: "suspend bug......?"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by aalr1986 on 2008-06-10
I'm having a problem with HH.

when I suspend the machine, it comes back from that well, but when I do it a second time, it won't go back to my desktop, it gives me a blank screen, and I have to reboot the system.....

is anyone familiar with this?

---

### Post by aalr1986 on 2008-06-10
oh and btw, I have a DELL Vostro 1500 laptop, 2gb ddr667, core2duo 2.0, nvidia 8600m gt 256mb, 160hdd 7200rpm..

(if all this matters)

---

### Post by aalr1986 on 2008-06-10
.. anyone?

---

### Post by HydroModeler on 2008-06-10
> **aalr1986 said:**
> .. anyone?

Just type in your password and hit enter.  That should work...it does for me.  As I understand it, it is a problem with compiz and the video driver (?).  I am pretty new to all of this myself, but what you describe sounds like what was happening to me.  I will post some of the links I used to figure this out when I get home tonight.  Also I found a patched version of compiz that seems to fix it.  I will post a link to that too.

---

### Post by vprasaj on 2008-06-11
I have just solved my problem. The same thing.

O.K. I have AGP card (nvidia 6600gt). I added in /etc/X11/xorg.conf in section "Device"

```
Option "NvAGP"  "1"
```


Now it looks like this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option "NvAGP"  "1" 
EndSection
```

Then I edited  /etc/default/acpi-support
and changed
```
POST_VIDEO=true
```
to
```
POST_VIDEO=false
```

Rebooted and tested.

Now I can suspend and hibernate.\\:D/[-o<

This was my problem... (for 3 years #-o)

I hope this helps to someone...

Edit:
If I use compiz, then it resumes with white blank screen. But i just type password (blindly), and everything is back.

---

