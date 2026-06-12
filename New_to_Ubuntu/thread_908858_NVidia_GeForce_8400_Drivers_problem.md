---
title: "NVidia GeForce 8400 Drivers problem"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by dellxpsm1530 on 2008-09-02
Actually i am new to ubuntu(8.04).I have NVDIA GeForce 8400 graphics accelerator in my computer.I have got a problem.After i enable the driver and restart the computer, i am not able to see the actual screen(only bars can be seen) .So i thought of doing one thing.Everytime i shut-down i uninstall the driver of it(NVDIA GeForce 8400) manually and everytime i log in i install it manually so that i can enjoy the effects while working.And it works(except some features). Can anyone tell me the solution for it so that i dont have to install the driver wen i start and i dont have to uninstall the driver when i shut down(behaves normally).Any kind of help would b great.Thank you...

---

### Post by chris062689 on 2008-09-02
How are you installing the drivers?
Try installing Envy, and using the manual installation.

---

### Post by dellxpsm1530 on 2008-09-02
I have tried that.but still it doesnot work.I also would like to mention that while shutting down the system i use EnvyNG to remove the drivers..i am also not able to open xorg.conf.i think there is the problem..can anyone give the detailed solution.Ill b very thankful to him/her.

by the way thanks 4 replying

---

### Post by falcon61102 on 2008-09-02
It sounds like your refresh rate is messing you up when you restart.  Why it is changing when you restart, I have no idea.  Since you can install the drivers no problem, go ahead and install them but this time don't uninstall them before you restart.  When you restart, pick the recovery mode in the GRUB menu and load up Ubuntu in recovery.  Once you login, open a terminal and type:
```
sudo nvidia-settings
```
Go through the menus and adjust any settings you find necessary and then click on the Save Xorg.conf button.  Then restart and hopefully that will overwrite any previous settings in your xorg.conf that were giving you trouble.

---

### Post by dellxpsm1530 on 2008-09-03
in the X server display configuration should i put the resolution as auto or i should put it as 1280x800?

---

### Post by dellxpsm1530 on 2008-09-03
should i tick the include X display names in the config file ?

---

### Post by Sinkingships7 on 2008-09-03
Why not use the drivers from the repos? That's the same card I have, and the nvidia-glx-new package works absolutely perfectly for me.

---

### Post by falcon61102 on 2008-09-03
You can do both.  If 1280x800 is the native resolution for the display you are using, then that's what AUTO is going to set it to anyway.  If you want to be sure, go ahead and set that.  And the x display names provide more detail in the xorg.conf so you shouldn't have any problems using them.  

Were you able to reset the refresh rate?

---

### Post by dellxpsm1530 on 2008-09-03
noopes .where can i get the option for the refresh rate?

---

### Post by falcon61102 on 2008-09-03
It's in there, I can't remember the exact menu but I know there's an option for it.

---

