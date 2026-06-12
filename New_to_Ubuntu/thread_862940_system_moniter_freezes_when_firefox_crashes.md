---
title: "system moniter freezes when firefox crashes"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by moonbat% on 2008-07-18
hey im running 8.04 with firefox 3.0.  whenever firefox freezes for whatever reason, and i try to end the process with system moniter, it freezes too.  i have to restart my laptop to get firefox to shut down properly.  anyone knows what gives?

---

### Post by Mister.Vash on 2008-07-18
Next time it happens, try this

Don't try to end it with System Monitor - use system monitor to get the process ID for firefox

once you have the process ID, open a terminal window and use the kill command.  For example, if the process id was 9420 run
kill 9420
from the terminal and see if that works

---

### Post by carusoswi on 2008-07-31
> **Mister.Vash said:**
> Next time it happens, try this

Don't try to end it with System Monitor - use system monitor to get the process ID for firefox

once you have the process ID, open a terminal window and use the kill command.  For example, if the process id was 9420 run
kill 9420
from the terminal and see if that works

When Firefox freezes on me, the entire system is frozen - no keyboard response, no mouse pointer, nothing.  No option but to reboot.

This started recently, and I assume it is connected to recent upgrades of Firefox.

Caruso

---

### Post by billgoldberg on 2008-07-31
> **moonbat% said:**
> hey im running 8.04 with firefox 3.0.  whenever firefox freezes for whatever reason, and i try to end the process with system moniter, it freezes too.  i have to restart my laptop to get firefox to shut down properly.  anyone knows what gives?

Use the "top" command in a terminal or install htop and use the "htop" command in the terminal.

Kill firefox with 

"pkill firefox" in a terminal.

However, when firefox crashes, 99.99% of the time it's because of flash.

You can prevent it by switching to ALSA in (system-> preferences -> sound) and remove libflashsupport if you have it installed

> sudo apt-get autoremove libflashsupport --purge

Also, using [flash player 10 beta 2]("http://linuxowns.wordpress.com/2008/07/15/install-flash-player-10-beta-2/") will improve stability.


I'm using alsa with flash player 10 beta and haven't had a crash in ages.

edit: If the system isn't responding, use "ctrl + alt + backspace" to restart the X server. This will bring you back to the login screen.

---

