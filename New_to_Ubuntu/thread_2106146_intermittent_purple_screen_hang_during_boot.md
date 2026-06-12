---
title: "intermittent purple screen hang during boot"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2013-01-18
Hi,    I upgraded to 11.10 Oneiric on my Acer Aspire One 522 netbook back in Oct 2011 and it ran OK for 11 months until Sept 2012 when it started to experience intermittent purple screen hangs during booting.

So for the last 4 months,  sometimes I go from grub to log-in successfully and there's no problem,  but other times I see Oneiric loading normally for about 21 seconds after grub,  then a couple of black and white screen flashes,   followed by a purple screen totally unresponsive hang that I can only clear with a power down.  I've tried various remedies mentioned in other threads like "F6" and "Cntl-Alt-F1" to "Cntl-Alt-F6" and "Cntl-Alt-Backspace"  and pressing "e" immediately after grub selection"  and "pressing power-off briefly" several times,  but the hang is completely unresponsive to all these.

I didn't make any significant changes in Sept 2012 that I'm aware of other than accepting regular updates,  which makes me suspect this phenomenon must somehow have been caused by one of those updates.

When this hang occurs,  it only happens about 30 seconds after grub selection, wwhich is before any command line loading appears.  Note that I've replaced "quiet splash" with "",  So once I reach log-in,  I know I've got past the danger time for this trouble to happen.    I've also tried adding "noefi" but the trouble still occurs.  

Sometimes it happens repeatedly and I have to keep trying re-booting up to 4 times before one is successful.  Selecting recovery mode usually works though.   Other times I get a whole run of successful reboots.   Rebooting to Oneiric from a previous seesion in Windows XP nearly always fails first time though.   

This never used to happen with Natty,  nor did it on my first 11 months on Oneiric so something in a Sept 2012 Oneric update is all I can think of to blame.

Any ideas?    Suggestions?

---

### Post by Sleepy-zz-John on 2013-02-05
Since my above post 2 weeks ago,  I've been trying connecting an external monitor via VGA socket on my netbook,  and for the 5 or 6 days I had this connected,  I didn't experience a single purple hang.   I've now had to remove that monitor and go back to my built-in screen,  and the purple hangs have started again.   So I conclude that this problem must be something to do with the built-in monitor on my AspireOne 522 or the interaction with its driver.

Does this new clue help anyone to come up with a suggestion,  I wonder?

---

