---
title: "Can no longer open Terminal or Natilus"
date: 2018-06-30
forum: New to Ubuntu
---

### Post by dlakes2112 on 2018-06-30
When I booted my pc today (Ubuntu 18.04) 3 unusual things happened. 1) I got a window about a password keyring asking for my password. 2) Terminal would not longer launch. 3) Natilus would no longer launch. (I hear my drive loading something, but nothing comes on the screen)

The last thing I did to my PC was to install Chrome. Everything seemed ok at that point.

I saw something on Google about checking my Region / Language settings, but they are set correct.
Ubuntu Software still works, but there is no uninstall (re-install) option for gnome term or Natilus.


I can get to a command only screen by Ctr+Alt+F3 but have no idea what to do there other than to log in. 

Any idea what happened and how I can fix it? 
Thanks!!

---

### Post by Hund on 2018-06-30
Welcome!

Have you tried installing another terminal emulator? If that works you could try to run your default terminal emulator and Nautilus from there to see if you get any error messages.

---

### Post by dlakes2112 on 2018-06-30
I tried two of them, neither will launch. Same thing...I hear the HD loading something and briefly see the name on top next to "ACTIVITIES" but then it goes away.

---

### Post by dlakes2112 on 2018-07-01
I have now tired  sudo dpkg-reconfigure gnome-terminal under command line (ctrl+alt+F3) and that ran...but did not help.

I see under gnome logs that it says under Important / security  "Failed to start gnome terminal server" and when i click it, it says sender:systmd Audit session 1 priority 3

I also notice that screen shot app will not load either.

---

### Post by The Cog on 2018-07-01
You might possibly learn something by switching to the Ctl-Alt-F3 console and entering this command:
```
export DISPLAY=:0
gnome-terminal
```
(In case you didn't know, Alt-F7 gets you back to the GUI)

If gnome-terminal is crashing for some reason, it might output an error message to the console as it dies and that might possibly give you a clue.

---

### Post by Zanara on 2018-07-01
With so many programs not working, I decided something catastrophic happened so I just did a re-install.

---

