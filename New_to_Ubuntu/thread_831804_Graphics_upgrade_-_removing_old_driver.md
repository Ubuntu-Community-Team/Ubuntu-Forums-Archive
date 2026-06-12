---
title: "Graphics upgrade - removing old driver"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Clearview on 2008-06-17
Hi there.

My Ubuntu (7.10) PC currently uses a ATi 9500 graphics card for which I use the fglrx driver.

Following an upgrade on another PC I now have an Nvidia Geforce 6800GT spare and would like to use it in my Ubuntu PC instead of the ATi card.

Being relatively new to Ubuntu I was wondering how this should be done, and whether it will affect other aspects of my PC, for example Compiz Fusion.

Many thanks in advance.

---

### Post by aktiwers on 2008-06-17
To install the newest Nvidia driver do like in this small guide I made:
[http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735](http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735)

Just remember to download the latest driver here:
[http://www.nvidia.com/object/linux_display_x86_71.86.04.html](http://www.nvidia.com/object/linux_display_x86_71.86.04.html)

and remember to change the commands containing the driver file name(the 3. and 2. last steps in my guide).

To remove your ATI drivers ( you don't really have to do this, they will just not be in use), we would need to know how you installed them I guess.

Edit:
By the way, I have done this myself before..  exchanging an ATI 9800pro with Nvidia 6200LE and Ubuntu would not start X afterwards (no GUI).

So maybe your best bet is to install the nvidia driver like in my guide and instead of reboot(the last step in the guide), just shutdown, change the cards, and boot up again.

---

### Post by Clearview on 2008-06-17
Thanks for the reply.

If it's safe not to remove the ATi driver, could I just remove my old ATi card and replace it with the Geforce *before* carrying out the procedure you describe?

---

### Post by aktiwers on 2008-06-18
If you switch the cards before installing the Nvidia driver, you are likely to be unable to start your GUI and the computer will boot up in full-terminal mode. Atleast this is what happed to me. If you install the drivers first, then shutdown and switch the cards, and boot up again, I think you will be fine :)

---

