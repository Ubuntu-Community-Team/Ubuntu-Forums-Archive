---
title: "Hardware Identification"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by Cuttysark on 2008-10-17
Is there a program that will tell me what components are in my computer, the same or similar to the Windows System Information one? Something that would save me from having to physically look inside. I do know it has an AMD Athlon 64 processor and 500 Mb of memory but I have no idea regarding, for example, the graphics card.

I ask this to try to find out if it's maybe a hardware problem that is causing a problem I'm having. Every so often, everything losses colour and goes grey scale. Sometimes just the active program, sometimes the whole desktop. Sometimes it will clear itself after a few seconds, sometimes it requires a reboot.

I happened briefly as I was about to log into this site to post. At the time, I had Amarok open and playing, Firefox, and System Monitor. Everything went greyscale apart from the top panel, and the music still played. It's driving me crazy.

---

### Post by philinux on 2008-10-17
There are these commands from terminal.

lspci
lsusb
sudo lshw -short

---

### Post by Tamlynmac on 2008-10-17
Have you looked at "Hardinfo"? It's in the Synaptic Package Manager. I think it may be what you're looking for.

---

### Post by ChildOfMana on 2008-10-17
You could also type the following command into a terminal:

> sudo lshw -html > hardware.html

This will deposit a HTML document in your /home folder with all your hardware info neatly displayed within.

---

### Post by Cuttysark on 2008-10-17
Okay, thanks guys, I got the info okay, but can't see anything other than only having 500Mb of memory that might cause this. Does anyone have any ideas?

---

### Post by handydan918 on 2008-10-17
> **Cuttysark said:**
> Okay, thanks guys, I got the info okay, but can't see anything other than only having 500Mb of memory that might cause this. Does anyone have any ideas?

Yeah, try running memtest. Let it run overnite, and see what it comes up with. This sort of hit and miss problem could easily be bad RAM....

---

