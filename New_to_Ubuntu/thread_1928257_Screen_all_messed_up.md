---
title: "Screen all messed up"
date: 2012-02-19
forum: New to Ubuntu
---

### Post by theducksfan2010 on 2012-02-19
I was following this tutorial to get compiz fusion to work and got down to the additional drivers screen, and well I don't have any. How do I reverse what was done so my computer looks good again?

[http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-11.10-oneiric-ocelot](http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-11.10-oneiric-ocelot)

---

### Post by winh8r on 2012-02-19
Probably a good idea to open a terminal and using the "up" arrow key, go back through the commands and post which ones you have entered.

That way someone will be able to see what you have done and possibly get you back to square one again.

Hope this is of some help to you.

---

### Post by theducksfan2010 on 2012-02-19
I typed in everything in the terminal up until the screen where it shows the additional drivers box

sudo apt-get install compizconfig-settings-manager

sudo nano /etc/modprobe.d/blacklist.conf

blacklist nouveau

sudo update-initramfs -u -v

I got to 
What you need however is the NVIDIA accelerated graphics card driver (version current) [Recommended], so select it and click on Activate. The drivers will then be downloaded. After that, you will need to restart your machine, but don't do that yet. You need to do one more thing, which is to specify the driver to boot with in your xorg.conf file. Back this config file up however in case anything should be broken on reboot. Afterwars open a terminal and enter:
  sudo nano /etc/X11/xorg.conf


but had no additonal drviers on my screen.

---

### Post by Krytarik on 2012-02-19
> **theducksfan2010 said:**
> sudo nano /etc/modprobe.d/blacklist.conf

blacklist nouveau

sudo update-initramfs -u -v
Isn't it obvious to you, what you need to do!?:

[LIST=1]
[*]Revert the upper modification.
[*]Re-run the lower command.
[/LIST]
Regards.

---

### Post by theducksfan2010 on 2012-02-19
Obvious yes, but how the he** to do it, I have no clue.

---

### Post by Krytarik on 2012-02-19
> **theducksfan2010 said:**
> Obvious yes, but how the he** to do it, I have no clue.
Then simply run these commands:
```
sudo sed -i '/blacklist\ nouveau/d' /etc/modprobe.d/blacklist.conf
sudo update-initramfs -u -v
```
Thereafter, reboot.

---

### Post by theducksfan2010 on 2012-02-20
Thanks for the help, I had JUST started a fresh install right before the last post. Hopefully I never get this problem again, But if I do, I have a starting point to go from, ty.

---

