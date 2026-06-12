---
title: "Is it 'safe' to switch between different Nvidia drivers from Additional Drivers tab?"
date: 2013-06-09
forum: New to Ubuntu
---

### Post by Naygral on 2013-06-09
The card I use: 7900 GTX

**The question: **If I install the *nvidia-304-update*, but find it to cause problems - is it safe for me to just use *nvidia-304* without any further work than to check that driver in the additional driver tab and restart my computer after I applied the change?

In my head (as a Windows user) I am afraid that a conflict between several installed nvidia drivers may cause more harm than good. Should I remove the first driver that I installed before trying another one or is it perfectly safe to switch between different drivers on Lubuntu without any work in between the switches?

Thank you for any help you can provide!

---

### Post by Autodave on 2013-06-09
How are you applying the new driver: from a command line, internet download, or what?

---

### Post by deadflowr on 2013-06-09
Removing it is always the safer option, rather then trying to switch.
Removing it, and then removing the xorg.conf file, and then rebooting usually clears it pretty good.

---

### Post by Naygral on 2013-06-09
> **Autodave said:**
> How are you applying the new driver: from a command line, internet download, or what?

Done entirely through the Additional Drivers tab found in Lubuntu's Software Sources that was installed with the system.

---

### Post by hamishmb on 2013-06-09
Using the GUI, I'd recommand uninstalling the old driver first, but generally I find it's okay. I've done this a few times, and never had any problems :)

---

