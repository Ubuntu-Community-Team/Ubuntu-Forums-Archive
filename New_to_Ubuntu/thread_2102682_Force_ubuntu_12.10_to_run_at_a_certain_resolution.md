---
title: "Force ubuntu 12.10 to run at a certain resolution"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by MrGibbage on 2013-01-07
I have a fresh install of ubuntu 12.10 for a home theater PC. It is connected to my plasma tv over hdmi. I mostly interact with the computer over VNC when I need to change settings, etc. The problem is, if the tv/receiver is turned off, ubuntu does not detect a display device and I get an error stating so and something about low-graphics mode. I would like ubuntu to just ignore this and still start up at the right resolution without complaining. Is this possible? How do I do it?

---

### Post by williejones on 2013-01-07
You can edit grub to start up in a selected vga mode by adding a boot parameter VGA=xxx (where xxx is the mode you wish to start in). information. Copy the following into a browser > en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers

---

