---
title: "Extended monitor problems"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by woodbe7 on 2008-11-19
Hello to all!  I, of course, am new to Ubuntu, but learning quite quickly.  The one hardware hurdle I am running against is setting up an extended monitor (not a clone).

I am running Hardy (8.04) on the following system:
IBM Thinkpad T42p
Video: ATI FireGL Mobility T2

I have tried this on both the s-video and VGA ports, same result.

I have installed the updated ATI drivers and Catalyst Control Center (CCC) from ATI (thread 677119).

I am able to setup single, clone & big display.

The following is encountered with extended display:
launch CCC and setup appropriate montiors
reboot
enter username & password (only active screen is the laptop)
both screens activate (mouse can be viewed)
X does not load

I then have to press CTRL-AlT-F1 to launch terminal.  I then run:
sudo aticonfig --initial -f to erase the prior monitor settings.  Then back to square one...

Any thoughts?

---

### Post by Billybob97060 on 2008-11-19
I was having a very similar issue myself, and the only way i got it to work was to go into my resolution and change to something that equaled both widths added together and a standard height for example: 2800X900 and than go into the aticonfig and choose big desktop right, but still at that i had an issue with crashing, you might give it a shot, though..

---

### Post by woodbe7 on 2008-11-20
That would be all and good, except that I am attempting to use a church presentation software program, DataSoul.  The way the program works is that the main display (laptop) shows a control panel, while the extended desktop (hooked up to a projector) is showing the slides.  The awesome advantage to this program is that I can CHANGE info on the fly!

If I can't get the extended monitor to work, I have to fall back on Open Office Presenter, which cannot be changed once I start it...=(

---

