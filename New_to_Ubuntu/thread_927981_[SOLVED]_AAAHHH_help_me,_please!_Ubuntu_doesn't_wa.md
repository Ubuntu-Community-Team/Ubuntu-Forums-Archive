---
title: "[SOLVED] AAAHHH help me, please! Ubuntu doesn't want to start!"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Crayboff on 2008-09-23
When I boot up my computer I start Ubuntu normally it doesn't enter  the graphical mode sign in screen like i know but it opens up BusyBox or whatever it is called. I got it to work in Recovery mode, once. However when I turned off my computer and later started it up again and recovery mode didn't work. Currently, I am running a memtest, i don't think that will do anything, but I'm pretty desperate. I also have Vista running on the same computer, and Vista works.


**Manufacturer:** Dell
**Model:** Inspiron 1521
**Processor:** AMD Turion 64 X2 Mobile Technology TL-58 1.90GHz
**Memory (RAM):** 1918MB
**System Type:** 32-bit 
**Operating System:** Ubuntu 8.04.1 (Hardy Heron), Windows Vista Home Premium

---

### Post by Tatty on 2008-09-23
Have you previously been able to boot this Ubuntu install without problems?  If so then what did you do just before it started failing to boot?

---

### Post by Crayboff on 2008-09-23
> **Tatty said:**
> Have you previously been able to boot this Ubuntu install without problems?  If so then what did you do just before it started failing to boot?
I have had no problem with this installation before today. All i was doing last night was chatting on IRC in #xkcd. I did not install anything last night and didn't do any systemwide changes.

The only thing I did was accidentally start Vista and I force shut it down and then tried to start Ubuntu.

---

### Post by Crafty Kisses on 2008-09-23
Try booting back into Vista and shutting it down the proper way, and booting back into Ubuntu, that should solve your issues.

---

### Post by quinnten83 on 2008-09-23
This might be important, but how did you install Ubuntu?
Was it via Wubi, or did you partition the drive yourself?

---

### Post by Crayboff on 2008-09-23
Starting Vista and shutting it down properly worked like a charm! thanks, Codename!

But, quinnten83, why does me having used Wubi (for some reason the Live CD wouldn't let me partition my harddrive. Wubi was reccommended to me by people on Ubuntu Forums).


Thanks, again, guys.
-Crayboff

---

### Post by Tatty on 2008-09-23
> **Crayboff said:**
> But, quinnten83, why does me having used Wubi (for some reason the Live CD wouldn't let me partition my harddrive. Wubi was reccommended to me by people on Ubuntu Forums).

When you use wubi, it uses your windows filesystem to store ubuntu.  Therefore if there is a problem with the windows filesystem (such as not shuting down cleanly) then it can affect your ubuntu install.

---

### Post by Crayboff on 2008-09-23
hmm does that also mean that I can't uninstall Wubi? and would it be possible to expand the amount of memory designated to Ubuntu (30GB) now?

---

### Post by Tatty on 2008-09-23
I have never used WUBI so im not sure about expanding the memory, although I imagine you can probabaly.  I believe to uninstall you just uninstall the same way you would uninstall anything in XP  (via the add/remove in the XP control panel)

---

