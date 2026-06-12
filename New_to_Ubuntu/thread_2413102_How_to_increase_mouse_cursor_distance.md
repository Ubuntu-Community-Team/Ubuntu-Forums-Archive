---
title: "How to increase mouse cursor distance ?"
date: 2019-02-21
forum: New to Ubuntu
---

### Post by bitsnpcs on 2019-02-21
Hello,

I have increased the mouse speed in Settings>Devices>Mouse & Touchpad, the slider is all the way to the right.
When I move the mouse on the desk, the cursor doesn't move far enough on the screen. 
It is more than 10cm I have to move the mouse on the desk to go from one side of the screen to the other (19" screen), it should be about 2cm-2.5cm.
If the mouse speed slider were numbered 1-10 and it is at 10 now, I likely need it to be at 12-14, it is difficult to tell until the distance movement is correct.

Is there a way to increase the speed and distance ?

The mouse scrolling and clicking speed is fine.

---

### Post by Autodave on 2019-02-21
Did this problem just start?  Have you tried another mouse to make sure that you don't have a failed mouse?

---

### Post by bitsnpcs on 2019-02-21
It has been like it since install, Ubuntu was preinstalled on the computer. I have just begun using it last week or so.
The mouse is working correctly/not failed, I also use it on my other desktop computer with an Ubuntu based distro, it works correctly on that.

The mouse is Logitech optical, USB, wired. The computer is i7 Coffee Lake 8th Generation, 16GB DDR4 Ram, hard drive is boot SSD 480GB.
The computer it works on with the other distro is i7 Sky Lake, 7th generation, 16GB Ram, hard drive 1TB.

---

### Post by ajgreeny on 2019-02-21
Does the **Acceleration** setting help?
Try increasing that.

---

### Post by bitsnpcs on 2019-02-21
I am not sure where the Acceleration setting is ?
In Settings>Devices>Mouse & Touchpad, the Mouse settings available are "Mouse Speed" (set all the way to the right), and below this is Natural Scrolling, which can be set to On or Off (it is set to Off). Looking through the rest of the Settings areas there is not one for Acceleration.

In Tweaks under Keyboard & Mouse there is a setting called Acceleration Profile, the options are "Adaptive", "Default", and "Flat", this is set to "Default". 
I have just tried Adaptive and Flat, they seem the same, no change that is visible in the mouse cursor movement or behaviour..

---

### Post by CatKiller on 2019-02-21
There are [many](https://wiki.archlinux.org/index.php/Mouse_acceleration) ways to change how mouse inputs are interpreted. That page is about acceleration specifically, but it does list the interfaces that you could use. It would simply be different setting names to change the speed rather than the acceleration.

I fully expect the Gnome devs to remove all options to configure the mouse soon.

---

### Post by bitsnpcs on 2019-02-21
I have fixed it now.
I installed something called **dconf editor** in Ubuntu Software then changed the mouse speed to 1.0 as its maximum, this did not fix it, I then changed it to 2.0, this fixed it, it saved the setting as 1.0 though, but it is fixed.
The default acceleration was slow, I changed it to flat it stayed slow, I changed it back to default it now moved further so I saved it.
The cursor no longer moves like it is in mud, it is free.

---

