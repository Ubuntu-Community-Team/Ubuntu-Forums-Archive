---
title: "upgdared my hardware , now I have no Graphic"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by medya on 2008-07-05
I totaly upgraded my pc 
, cpu, motherboard, graphic card... except the Hard disk, which has ubuntu on it.


the graphic seems to be messed up ....how I can re-configure the thigns ?

---

### Post by sydbat on 2008-07-05
Update the driver for your video card. What is your new video card?

---

### Post by sdennie on 2008-07-05
You could try rebooting into recovery mode and then choosing xfix from the menu if you are using Hardy.  That may not completely fix the problem but, it should get you to the point where the machine is usable and you can install the proper drivers you might need (which, if you have nvidia or ati, will probably be in System->Administration->Hardware Drivers).

---

### Post by neurostu on 2008-07-05
So the previous hardware configuration probably uesd a different video driver then your new configuration.  You need to un-install the old driver and install the correct new one.  

What was your old video card?

What is your current video card?

---

### Post by medya on 2008-07-09
my old card was nvidia AGP 
my new one ins nvida 8700 pci express

---

### Post by neurostu on 2008-07-11
can you boot into the command line?  What you need to do is remove the old video drive.  I think it something like nvidia-glx... I'm not sure...

try:
```

aptitude search nvidia

```
anything with an **i** on the left is installed.  Uninstall it all and then reboot.  Ubuntu should default to the VESA driver, and you should then be able to use the Hardware Driver Manager to install the new nvidia driver.  If that doesn't work then try installing:
```

nvidia-glx-new

```
then try installing something like:
```

nvidia-settings

```
you might need to search for it with aptitude search nvidia
then run the nvidia settings panel and then remember to Save Configuration to Xorg.conf.

That should work...

---

### Post by LowSky on 2008-07-11
your best bet is to boot into recovery mode and type this command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It will reconfigure all yourinputs form mouse to keyboard to graphics

---

### Post by neurostu on 2008-07-11
> **LowSky said:**
> your best bet is to boot into recovery mode and type this command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It will reconfigure all yourinputs form mouse to keyboard to graphics

This is actually a great idea, this will save you the trouble of having to remove the old drivers and get vesa running.

---

### Post by markbuntu on 2008-07-11
Make sure that if your new mobo has built in video that it is disabled in the bios and the bios actually recognizes your card and has it enabled.

I recently got a new video card and had no problems at all. Installed the new card, disabled the on board video in the bios and Ubuntu recognized the new card right out of the box, loaded VESA and got me into gnome and then told me that a restricted driver was available for it. Got that, smooth sailing.

---

### Post by medya on 2008-07-13
I tried all the above things... no video just command line (I start in recovery mode)

---

