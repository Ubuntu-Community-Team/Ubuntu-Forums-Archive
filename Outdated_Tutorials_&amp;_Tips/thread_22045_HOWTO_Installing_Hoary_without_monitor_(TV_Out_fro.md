---
title: "HOWTO: Installing Hoary without monitor (TV Out from scratch)"
date: 2005-03-25
forum: Outdated Tutorials &amp; Tips
---

### Post by acariquara on 2005-03-25
No monitor needed! 

First, you will need:
NVidia TVOut (in this example the NForce2/GeForce4 MX440 was used)
Hoary "Array 7" CD

Fire up your computer already connected to the TV set. No monitor needed if your BIOS is already set up (some ASUS mainboards default to PAL output, so check that out first). If you can boot Hoary from textmode directly on your TVOut, you are set.

Install Hoary as usual. Don't worry about monitor settings for now. After a while, you will be prompted to remove the CD and reboot. Do that.

Chances are that you will be staring at a blank screen after a while. No problem. 

Press at the same time [CTRL] [ALT] [F1]
You will be prompted to login in textmode. Login as usual.
Now type:

sudo bash
(enter your password as prompted)
apt-get install nvidia-glx
apt-get install nvidia-glx-config

after that

nvidia-glx-config enable

and then...

dpkg-reconfigure xserver-xorg

It is *VERY* important that, at this point, if you have a monitor connected, turn it off and disconnect it. Go through the menus (choose nvidia server, NOT NV) until you are prompted to choose either "Simple", "Medium" or "Advanced" for the mode lines.

Choose "Medium".

Next you will be asked the best resolution your display could handle.

That's 800x600@60Hz.

Keep advancing through the options. When you are back at the prompt, press:

[CTRL][ALT][F7]

Blank screen again.

Press

[CTRL][ALT][BACKSPACE]

After a while, the NVidia logo should appear on your screen. Done!

---

### Post by dregoroid on 2008-03-02
thanks. everything works great with GeForce4 MX440 agp 8x
but for me the right package was nvidia-glx-legacy instead of nvidia-glx

---

