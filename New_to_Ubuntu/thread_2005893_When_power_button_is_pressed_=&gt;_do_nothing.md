---
title: "When power button is pressed =&gt; do nothing?"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by jamesbeat on 2012-06-18
I have a computer running Ubuntu 10.04LTS hooked up to my tv in the living room for skype and watching movies.
Trouble is, my 20 month old daughter is fascinated with it!

I've 'baby proofed' it as much as possible:
I built a custom bracket for the webcam and attached it to the tv stand with screws.
Used double sided tape to secure the keyboard.
Glued a piece of plastic to the case that covers the button on the DVD drive so that it can only be opened via software.
These measures have taken care of most of the problems, but a big one remains: she keeps pressing the power button. This puts the computer into some suspend or sleep mode from which it can only be woken by holding the power button down to turn it off completely, then turning it on again :(

In a rare flash of genius, it occurred to me that if I told Ubuntu to 'do nothing' when the power button is pressed, the button could be used to turn the machine on but not off.

My elation was short lived however, because there is no such option.

Is there a workaround for this?

---

### Post by sudodus on 2012-06-18
Have a look at your BIOS menu system! Maybe there is an option, that the computer will boot at power on, and then you don't need the power button, and can put a piece of plastic to the case that covers the power button too.

*Edit: I mean that you use 'a switch on the power cord, hidden or too high for her to find/reach'.*

---

### Post by Grenage on 2012-06-18
Alternatively, put a cheap replacement switch somewhere else - on the case's rear, or far away.  If you don't want any switches, you can install a cheap TV card that supports power on by remote (uses a power pass-through); I did that on a machine some years ago.

---

### Post by jamesbeat on 2012-06-18
That option is not available in the bios (and the bios is updated to the final version for this machine).

I did think about moving the power button, but the problem is that she watches and copies us. As soon as she saw us reach around, say the back or the top of the case, she'd explore and find it.

Buying a TV card just to use the remote seems a bit OTT, but I guess it would work.

Is there absolutely no way to do this in software?

---

### Post by Paqman on 2012-06-18
No way you can put the box somewhere out of the way? Behind the TV?

You can get stick-on covers for things like cooker knobs, but I found them no match for an inquisitive toddler.

---

### Post by Grenage on 2012-06-19
> **jamesbeat said:**
> I did think about moving the power button, but the problem is that she watches and copies us. As soon as she saw us reach around, say the back or the top of the case, she'd explore and find it.

Buying a TV card just to use the remote seems a bit OTT, but I guess it would work.

You can get some pretty cheap cards.  Back to moving the power button, you could position it well out of reach of the nipper, it doesn't have to be on the case.

---

### Post by kanikilu on 2012-06-19
As fun as fake/decoy buttons sound, you should be able to disable the power button via software...

I'm not sure if the move to dconf was before or after 10.04, but in the default 12.04, the easiest way to accomplish this is in **dconf-editor** and to navigate to **org > gnome > settings-daemon > plugins> power** and then change **button-power** to *nothing*.

If it's gconf, I'm not really sure...maybe see if there is a similar entry in **gconf-editor**?

Alternatively, some people report that simply modifying /etc/acpi/powerbtn.sh (and restarting the computer or acpid service) works, but it didn't for me, only the gnome-settings-daemon change worked...

---

