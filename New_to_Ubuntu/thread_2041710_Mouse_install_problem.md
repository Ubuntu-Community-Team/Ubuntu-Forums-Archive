---
title: "Mouse install problem"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by intoutdoor on 2012-08-13
Hello,

I just installed ubuntu for the first time yesterday (first experience with linux) and I'm trying to install a peripheral mouse. I searched for additional drivers, but the system returned nothing.  I've searched this forum but can't find any general mouse installation info, everything is quite specific and irrelevant to my situation unfortunately.  Is there a simple secret that I am missing to install my mouse (Logitech m315 wireless) or is it fairly complex and requires the use of the command line?

Any quick advice would be greatly appreciated. 

Thank you

---

### Post by Kalanac on 2012-08-13
Hello,

From the looks of things, this should just work out of the box if it's a USB receiver mouse.  I take it that it's not a bluetooth device or similar?  And can you confirm it works in Windows or some other operating system?


Things to check would be your USB settings in BIOS.  Also, open a terminal (ctrl+alt+t) and type:

```
lsusb
```

This will give a list of all currently detected USB devices and will give a good starting point for troubleshooting.  Oh, and is it safe to assume you're running 12.04: Perfect Pangolin?

---

### Post by intoutdoor on 2012-08-13
Thank you so much for that command, I saw that it was installed, turns out, the battery was dead, as I hadn't used it in a while.  Feel like moron now...

Thank you very much though, that command is quite useful.

---

### Post by Kalanac on 2012-08-13
No trouble at all, I've had similar problems in the past :D  The simple solutions are often the ones we overlook.

Don't forget to mark the thread as solved :)

---

