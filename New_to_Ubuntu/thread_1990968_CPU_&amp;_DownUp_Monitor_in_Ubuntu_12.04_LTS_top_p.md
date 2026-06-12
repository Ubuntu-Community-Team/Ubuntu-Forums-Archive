---
title: "CPU &amp; Down/Up Monitor in Ubuntu 12.04 LTS top panel?"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by rez182 on 2012-05-30
Hello, i really miss gnome 2, but unity gives me lots of space & multiple active window view in one button.

but i really need a small CPU and Internet Download / Upload monitor which 10.10 (Gnome 2) had.

is there any way to put a widget or something up there in 12.04 LTS?

**Note:** No gnome 2 fork suggestions please. id like to stick to unity.

**P.S:** heard about MATE, but could not find how to install it in 12.04...

Thanks in advance... A little over a year using linux... Ubuntu rocks :guitar:

EDIT: The title should say 12.04 LTS, NOT 12.10, mistype...

---

### Post by FreddyGod on 2012-05-30
Hi. In Unity you can use indicator-multiload ([https://launchpad.net/~indicator-multiload/+archive/stable-daily](https://launchpad.net/~indicator-multiload/+archive/stable-daily) - just add this ppa ('sudo add-apt-repository ppa:indicator-multiload/stable-daily && sudo apt-get update' in terminal)
then just find in Software Center 'indicator-multiload' (or just write in terminal : 'sudo apt-get install indicator-multiload')

this is exactly like the applet in gnome 2, with CPU, RAM, Network, Swap, Load and Harddisk monitoring :).

After this find in Unity: 'System Load Indicator'
To make it start automatically every boot, enter in Preferences in System Load Indicator (click on it in unity panel after starting it and select 'Preferences') and check 'autostart'

---

### Post by rez182 on 2012-05-31
thanks alot @FreddyGod

works like a charm....

but i notice coming from 10.10 to 12.04, the system load is almost always above 60-70%...where as in 10.10 it was hardly above 0%... is it cause of Unity? Does it cause the battery to die out sooner?

Thanks again for the solution....

---

