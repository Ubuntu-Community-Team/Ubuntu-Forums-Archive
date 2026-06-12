---
title: "Blue Screen of Death!!!"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by TheMemphisExperience on 2008-06-23
So my screen was doing something strange at startup, which it has done in the past. Traditionally, I corrected that problem by just restarting.

This time, I went to screen resolution settings and turned the monitor upside down. Not only did it not correct the original problem, it disallowed any further interaction with the system.

Now the computer boots and goes into the baby blue screen of death. Unusable. ON the plus side, when I use the power button to shut down, I can see my wallpaper upside down. I can also move the mouse around while in BBSOD. 

I have autostart enabled and ctrl+alt+backspace does nothing. 

Clues?

---

### Post by stchman on 2008-06-23
> **TheMemphisExperience said:**
> So my screen was doing something strange at startup, which it has done in the past. Traditionally, I corrected that problem by just restarting.

This time, I went to screen resolution settings and turned the monitor upside down. Not only did it not correct the original problem, it disallowed any further interaction with the system.

Now the computer boots and goes into the baby blue screen of death. Unusable. ON the plus side, when I use the power button to shut down, I can see my wallpaper upside down. I can also move the mouse around while in BBSOD. 

I have autostart enabled and ctrl+alt+backspace does nothing. 

Clues?

Sounds like the display is going bad.  Did you try a different monitor?

---

### Post by TheMemphisExperience on 2008-06-23
Unfortunately, this is happening on my laptop. I'm using my Vista partition right now. When I have access to a second monitor later, I will try to connect it to that display, but unless I activate it, I don't recall if it will register.

I'm hoping for some fix that doesn't involve a reinstall of Ubuntu. Although, I do need to perform one anyway as There is some space on the HDD not being used that I'd like to assign to Ubuntu. It's just that I don't *want* to do a reinstall.

---

### Post by django0909 on 2008-06-23
Something like this happened to a laptop I used to run XP on a long while ago. Turned out to be a damaged ribbon cable between the display and the unit itself. Unfixable, sadly...

---

### Post by TheMemphisExperience on 2008-06-23
I do not think it is the display. Running in Vista right now, everything looks just fine.

---

### Post by TheMemphisExperience on 2008-06-23
So I succeeded in using ctrl+alt+backspace to reach the login screen. I went into failsafe GNOME. Works. I opened up a terminal and the like. I have no panels or Compiz_Fusion. 

Is this an X thing? I have no clue as to that.

Does anyone know how to fire up the screen manager from terminal?

---

### Post by fenian on 2008-06-23
After you hit ctrl+alt+backspace choose failsafe terminal from sessions ,login and enter this command...

> sudo dpkg-reconfigure -phigh xserver-xorg

this will reset your xorg to default settings (you will have to reinstall restricted drivers to get compiz working) after it finishes reboot with the command...
> 
sudo reboot

---

