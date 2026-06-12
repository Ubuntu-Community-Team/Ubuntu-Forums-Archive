---
title: "I have a 2 screen set up: every time I restart I need to totally reconfigure"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by surelock22 on 2008-11-18
How annoying is this:

I wouldn't even restart if I didn't have to, but SOMETIMES when I try to use FireFox, it just doesn't load. And as a computer (and Videogame) user of 25 + years, step 1: try again. Step 2: REBOOT!

Problem comes when I reboot: I have 2 screens plugged into the back of my GeForce 6800XT: a Vizio 32" WS HDTV and a ViewSonic 19" CRT with 4:3 ratio. I can get everything EXACTLY as I like it, but with the Nvidia driver I have (Nvidia X 177) I can't totally figure out how to keep those settings SAVED. In the settings, if I click "Save X Configure File, but then I get an error message ("Failed to parse existing X config file '/etc/X11/xorg.conf').

It then goes to a screen where I can choose where I want to save it, well, I DON'T KNOW WHERE TO SAVE IT BECAUSE I'M STILL HAVING THIS PROBLEM.

HELP. This is only an annoyance, but I'm sure it can be fixed pretty easily.

---

### Post by overdrank on 2008-11-18
> **surelock22 said:**
> How annoying is this:

I wouldn't even restart if I didn't have to, but SOMETIMES when I try to use FireFox, it just doesn't load. And as a computer (and Videogame) user of 25 + years, step 1: try again. Step 2: REBOOT!

Problem comes when I reboot: I have 2 screens plugged into the back of my GeForce 6800XT: a Vizio 32" WS HDTV and a ViewSonic 19" CRT with 4:3 ratio. I can get everything EXACTLY as I like it, but with the Nvidia driver I have (Nvidia X 177) I can't totally figure out how to keep those settings SAVED. In the settings, if I click "Save X Configure File, but then I get an error message ("Failed to parse existing X config file '/etc/X11/xorg.conf').

It then goes to a screen where I can choose where I want to save it, well, I DON'T KNOW WHERE TO SAVE IT BECAUSE I'M STILL HAVING THIS PROBLEM.

HELP. This is only an annoyance, but I'm sure it can be fixed pretty easily.

Are you using the command ```
gksu nvidia-settings
```

---

### Post by surelock22 on 2008-11-18
ok, i opened the terminal, entered the command, and it brought up the same Nvidia configuration menus from before. BUT when I tried saving the X screen configuration file, on top of the same error message I previously reported, in the command terminal it read:

Undefined Device "(null)" referenced by Screen "Default Screen".

Is this something I may need to change in BIOS or something?

---

### Post by elev on 2009-01-25
The "gksu nvidia-settings" command worked for me.  Thanks!

---

