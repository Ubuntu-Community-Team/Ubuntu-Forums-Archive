---
title: "LXDE and GNOME in the same system?"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by antthann on 2013-12-26
Hi,

I was trying to make my speakers work in my new Lubuntu 13.10. This is in desktop computer.
I found this from a forum and typed it in the terminal :

"
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop linux-image-`uname -r` libasound2

"
[FONT=arial]So, if I got it right, now I downloaded GNOME. I want to stay in LXDE. How I can undo this and how I can make my USB speakers work. Cheers.[/FONT]

---

### Post by mikewhatever on 2013-12-26
Here are the links on [howto remove gnome]("http://lmgtfy.com/?q=ubuntu+remove+gnome"). As for USB speakers, you'll need to switch the sound device, so try alsamxer (f6 for sound devices), or install alsamixer-gui.

---

### Post by antthann on 2013-12-27
Thanks mike, I managed to remove GNOME.
USB speakers and digital camera are still not responding. Even I downloaded alsamixer-gui.

---

### Post by mikewhatever on 2013-12-27
Have you been able to switch to the USB audio device?

---

