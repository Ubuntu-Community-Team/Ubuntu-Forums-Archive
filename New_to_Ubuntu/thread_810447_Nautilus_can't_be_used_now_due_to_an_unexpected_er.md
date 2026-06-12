---
title: "Nautilus can't be used now due to an unexpected error"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by jba6511 on 2008-05-28
after applying the latest updates this morning I receive the following message after rebooting:

"Natilus can't be used now due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem."

I have also lost the top bar on swiftfox that allows minimizing, maximizing and closing windows. I tried the usual F10, F11 and F12 keys to try and recover from this but they are not working. Terminal and evolution both still have this bar. Not sure if this is related to the error above.

Any ideas on what needs to be done to resolve this? I am running hardy with all updates.

---

### Post by alexandremrj on 2008-05-28
Your best bet will be to due what the error says:

run

killall bonobo-activation-server

and then try using nautilus and see if the error message disapears

---

### Post by Tokke on 2008-06-09
I have the same problem.  I started my computer today and all I saw after login in  was my background.  No menu bar, no icons, nothing.  Sometimes when I reboot I get the error message: **"Nautilus can't be used now due to an unexpected error from Bonobo when attempting to locate the factory. Killing Bonobo activation server and restarting Nautilus may help fix the problem"**
I managed to open a browser pressing ctrl-alt-esc but that is all I can do.  ctrl-alt-F1 wont work I just get some flashy screencolors.
Can anyone explain me what I can do (in newbie language please?)

Thx in advance

Tokke

---

### Post by pigphish on 2008-06-11
Just made updates, rebooted and got the same issue here. I cannot get my menus on top and bottom for gnome. Im running hardy heron. 

I have a full desktop though an can browse (after opening a folder) to /usr/bin and execute apps like firefox. CTL+ALT+f1 (through f8) all work. I tried killing bonobo in tty1:
        killall bonobo-activation-server
and CTL+ALT+bkspace (in tty7) and i get the same deal. how can i just restart the gui? how can i check the event logs to see what is failing?

---

### Post by pigphish on 2008-06-11
turned out to be my fault. I uninstalled evolution. 

Installing ubuntu-desktop package fixed the issue for me. 

sudo apt-get remove ubuntu-desktop 
sudo apt-get install ubuntu-desktop 

(I only needed to do the install as i already uninstalled it)

also ran:

sudo apt-get update
sudo apt-get upgrade

hope this helps.

---

### Post by markosjal on 2008-08-28
How do you access the terminal after the Error from the GUI?

---

### Post by WRDN on 2008-08-28
> **markosjal said:**
> How do you access the terminal after the Error from the GUI?

Press Alt + F2, then enter "gnome-terminal".

I've encountered this problem before, and i've fixed it by killing bonobo-activation-server, then logging out and in again.

---

### Post by markosjal on 2008-08-31
still not sure how one would log out of Nautilis (which is not running due to the error) then log in again.

---

