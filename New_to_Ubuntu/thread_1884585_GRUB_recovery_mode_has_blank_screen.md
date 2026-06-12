---
title: "GRUB recovery mode has blank screen"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-11-21
After my video card failed, I used the on-board video on the motherboard. That changed caused the GRUB boot-time to not output a readable signal by the monitor. (blank screen) I got some help at this forum and installed Startup Manager applet and set the advanced options for 800x600. That returned me to a viewable selection of kernels, memory tests and boot windows options, but not GRUB Recovery mode(s). After a week the vid card maker sent me a replacement video card. I installed it, and switched the BIOS from video-internal to pci-e (it's an EVGA 9500GT a pci-e device). 

On boot if I select Recovery mode, the screen still blanks and after a moment a message flashes by (VGA=769 is deprecated) and a bunch of words that go by way too quickly to read. I tried to take a photo, but it's way too fast. After that VGA= message, the screen blanks. However, I can push the Enter (CR) key, and that starts the "Resume Normal Boot" function. So, presumably pressing the up or down cursor keys would take me somewhere in the GRUB recover options. Which I don't do, without being able to see what I am selecting. I have tried the one I know from memory: Resume Normal Boot. 

I have manually updated the GRUB with sudo update-grub. All went well at the terminal.

Anybody know how to return my system to normal????

I continue to have this problem in Precise Pangolin 12.04.

---

