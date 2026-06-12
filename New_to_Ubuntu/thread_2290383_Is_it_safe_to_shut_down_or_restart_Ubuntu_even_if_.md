---
title: "Is it safe to shut down or restart Ubuntu even if I don't unmount/eject my USB?"
date: 2015-08-12
forum: New to Ubuntu
---

### Post by Austin_Muckelrath on 2015-08-12
I have, successfully, installed Ubuntu on my 32GB USB flash drive. However, I thought about using this from computer to computer - from my desktop computer to my MacBook Air. When I'm using Ubuntu on my USB, and just my USB alone, it won't mess up my USB if, for whatever reason, I shut down or restart my computer, you know, without ejecting my USB? Again, I'm new to this.

---

### Post by mastablasta on 2015-08-12
when you shutdown or reboot it will unmounts all drives (USB, HDD ....). you can see this if you shutdown or reboot via terminal.

---

### Post by col48 on 2015-08-12
I think your only vulnerability would be if you were writing to the USB when there was a power cut, and even then the files you were not editing should be OK.

---

### Post by Austin_Muckelrath on 2015-08-12
So, in other words, just clicking "shut down" or "Restart" won't do any harm to my USB? As in the whole OS Itself unmounts/ejects itself from my USB? I don't know any of this stuff, unfortunately. >.<

---

### Post by howefield on 2015-08-13
> **Austin_Muckelrath said:**
> So, in other words, just clicking "shut down" or "Restart" won't do any harm to my USB? As in the whole OS Itself unmounts/ejects itself from my USB? I don't know any of this stuff, unfortunately. >.<

Yes, that's pretty much it. Shutting down and restarting in the normal way will not harm the USB. Unintentional shutdowns / powering off is another matter of course.

---

### Post by col48 on 2015-08-13
Look at it this way:  it doesn't do any harm to the Hard Drive if you booted from there, does it?  So why should it affect the USB?

It's only if something is in the process of editing a file on the USB that there could be an issue in the event of a sudden shutdown as when the power is cut to a running system.  Even then, Ubuntu is robust enough to warn you next time you boot up that the last shutdown was untidy and boot up cleanly.

If your session included accepting system updates - which would involve writing possibly large files to the USB - be more cautious.  To be absolutely safe, make sure you have ejected the USB before powering off.  Chances are you'd get away with it even then, but better safe than sorry.

---

