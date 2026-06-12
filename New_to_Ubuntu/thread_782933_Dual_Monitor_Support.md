---
title: "Dual Monitor Support"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by SumoRoller on 2008-05-05
Is there dual monitor support?  I'm running a Nvidia 7800GTX and am pretty sure I have the latest driver.  I've searched elsewhere and found one article but it seemed a little more advanced than what I feel comfortable with.

---

### Post by pro003 on 2008-05-05
there is a nice thread [here]("http://ubuntuforums.org/showthread.php?t=221174"):

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by graben3 on 2008-05-05
First, make sure you have the right driver enabled.

Type glxgears in a new terminal window. If you get aroud 800 FPS & more you 
probably have 3d enabled.

If not, try going in synaptic and install envyng (envy is a cool utility made to install ati or nvidia drivers easily).

Install your driver with envy ng. You will have to reboot.

If your driver was already installed and you don't have the nvidia utility to configure your screens, just type this in a terminal :
sudo apt-get install nvidia-settings
Skip this step if you installed your driver with envy.

Then you should have in System -> Administration -> Nvidia X Server settings. Just edit this menu entry to add gksudo before the command because you wont be able to save anything you configured in this utility if you dont change this.

Run it and change you screen configuration with this utility. It always worked well for me and I have dual screen 1680x1050 x2 with compiz enabled. My card is a Nvidia 7600 gt 512MB.

My system specs :
P4 2.4
2.5 GB RAM
Dual screen 1680x1050 side by side
Desktop effects/Compiz on both screens
Nvidia 7600 GT 512 MB RAM

---

### Post by graben3 on 2008-05-05
Don't use any utility that comes with ubuntu for dual screen support. I tried them many times and it always got my configuration progress worse than better.

---

