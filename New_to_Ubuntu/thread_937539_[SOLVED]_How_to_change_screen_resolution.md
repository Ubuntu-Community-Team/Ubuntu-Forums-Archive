---
title: "[SOLVED] How to change screen resolution"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by kc5hwb on 2008-10-04
I just got a new widescreen monitor and wanted to update my screen resolution to include 1440x900.  However when I follow the instructions below, not only did it not give me an option to choose my screen resolutions, but is also removed all the previous options I have and now my 2 choices are 800x600 and 640x480.  Something must have changed with Hardy because the instructions below are what i used last time, I kept a record of them.  How can I add more resolutions to Hardy?


The change the screen resolution properties:

first <CNTRL><ALT><F1> to get a login prompt - login in to your account

Code:

sudo dpkg-reconfigure xserver-xorg


follow the prompts, answer all the questions - when you get to the Monitor config part choose Medium. Then select the resolution & refresh rate you want as default. Go through the rest and save. You should get a warning "overwriting possibly-customised configuration" - this just lets you know the name of the old (backup) config.

---

### Post by kc5hwb on 2008-10-04
anyone?

---

### Post by lyni on 2008-10-04
on my Ubuntu 8.04 it is System>Preferences>Screen Resolution. then you have the choice to change it.
does that help?

---

### Post by kc5hwb on 2008-10-04
No, I go there and the only options I see are 800 and 640.  There is another way to go into the xserver and give it more options to show in the menu you are talking about, but it must have changed in Hardy because it isn't working anymore.

---

### Post by Perfect Storm on 2008-10-04
Which card do you have?

---

### Post by kc5hwb on 2008-10-04
[http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=1&model=332](http://www.uabit.com/index.php?option=com_content&task=view&id=32&Itemid=48&page=1&model=332)

It comes with an integrated onboard GeForce 6100 GPU.  So what I had to do to get it running was this...

I downloaded the most current driver from here...
[http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)

---

### Post by Perfect Storm on 2008-10-04
If the driver is up and running;

```
gksudo nvidia-settings
```

restart X

---

### Post by kc5hwb on 2008-10-04
that doesn't seem to be doing anything

---

### Post by Perfect Storm on 2008-10-04
oh, then you havn't installed the nvidia driver. Have you tried (the easist way). the restricted driver that comes with Ubuntu? (System ---> Administration ---> Hardware Drivers)?

If they don't work, try ENVY.
```
sudo apt-get install envyng-gtk
```

---

### Post by kc5hwb on 2008-10-04
That did work, thanks.  I had already installed the drivers, but for some reason they were showing disabled.  After re-enabling and rebooting, it is working now.

---

### Post by olican101 on 2008-10-06
i tried this but its just saying no proprietary drivers are in use on this system (i am using voodoo3)

---

