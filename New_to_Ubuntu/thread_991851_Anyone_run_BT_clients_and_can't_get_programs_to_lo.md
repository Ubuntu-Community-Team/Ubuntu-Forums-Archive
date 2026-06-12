---
title: "Anyone run BT clients and can't get programs to load after a long bit of DL / UL-ing?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by surelock22 on 2008-11-24
Ok, I've kinda posted on this problem before, but I don't think I dedicated an entire thread on it.

When I run BT Clients (I did use Transmission and now kTORRENT) for a looooooooong time (well, I have to to get my gigs of stuff!), I can't get FireFox or Virtual Box to run. They attempt to load, then they just stop trying until I alt + ctrl + backspace log back in. What's the deal with this?

Anyone have any suggestions as what's causing this and / or the fix ? It's a little annoying to have to reboot, but I can deal with it if it's not causing major problems with my FAT.


:confused:

---

### Post by Trail on 2008-11-24
> 
THXINADVNCE!
KTHXBAI!
CHZBURGERTYMZ!!


not helping.

Anyways, first thing to try would be to launch firefox through a console to check the error messages and see if there is any sort of failure, and troubleshoot based on that. Simply open the terminal of your choise and type firefox. If firefox fails to start, look for errors there.

Other than that, check your memory consumption at the time that firefox fails to start. Also, you might try to set ktorrent's memory allocation setting to 'low'.

And by the way, avoid using Ctrl-Alt-Backspace to relog, as it's killing the processes. Use the normal logout button instead if you value your data's integrity.

---

### Post by surelock22 on 2008-11-26
I'll try running Firefox in terminal, and I'll check Memory consumption. 

Also, I'm still having the same problem of my Nvidia driver not loading up correctly upon reboot and it forces me to re-install the driver and reset the x config file through terminal and re-boot.

I'm just gonna leave my stuff on 24/7, and that way I won't have to deal with this Nvidia driver problem AS MUCH. Utility bill ? Screw it, I'll just make sure I'm always DLing when I'm not "using" the PC.

:guitar:

---

