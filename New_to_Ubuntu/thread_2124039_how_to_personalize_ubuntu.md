---
title: "how to personalize ubuntu?"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by cheatos on 2013-03-09
Hi all,

after a recent PC upgrade i have gotten back to ubuntu.
However, I'm still looking for the menu where I can personalize the behavior, i.e. the most practical thing, that windows automatically get focused and pop up when i move the mouse over them. Couldn't find it in the System Settings program :(
Where do i have to look?

Thanks for your help

---

### Post by fiodev on 2013-03-09
gnome-tweak-tool is popular for personalizing
apt-get install gnome-tweak-tool

---

### Post by cheatos on 2013-03-09
so there is no more options than the ones in system settings?
Thats too bad. I used to have 11.04 it was pretty awesome what you could configure. Don't want to install a lot of tools because my install currently is running on a USB-stick

---

### Post by arpanaut on 2013-03-09
For mouseover focus try this: [http://ubuntuforums.org/showthread.php?t=1950977](http://ubuntuforums.org/showthread.php?t=1950977)
or: [http://ubuntuforums.org/showthread.php?t=1994512](http://ubuntuforums.org/showthread.php?t=1994512)

---

### Post by Frogs Hair on 2013-03-09
As well as the Tweak Tool Install the Compiz Config Settings Manager  from the software center and there are Unity behavior settings. The settings can be accessed easier from Ubuntu Tweak after the CCSM is installed. [http://www.webupd8.org/2012/11/ubuntu-tweak-gets-full-ubuntu-1210.html](http://www.webupd8.org/2012/11/ubuntu-tweak-gets-full-ubuntu-1210.html)

Themes and icons can be found here but get correct themes for your Ubuntu version. [http://gnome-look.org/?xsection=home](http://gnome-look.org/?xsection=home)

---

### Post by cheatos on 2013-03-09
so sorry for the probably stupid question, but what is the ccsm mentioned in these two threads?
Cannot find it via the launcher.
ok, compiz config settings manager thanks for clarifying frogs hair!
too bad though that ubuntu doesn't have a built-in tool anymore. compiz used to give me some weird problems back in 11.04

---

### Post by stinkeye on 2013-03-09
> **cheatos said:**
> so there is no more options than the ones in system settings?
Thats too bad. I used to have 11.04 it was pretty awesome what you could configure. Don't want to install a lot of tools because my install currently is running on a USB-stick
As unity is a plugin for compiz you would need to install compizconfig-settings-manager for unity and window manager settings.
```
sudo apt-get install compizconfig-settings-manager
```

Enter ccsm in the dash to run.
Focus behaviour is in ccsm > general options

---

### Post by cheatos on 2013-03-09
Thanks for your help. Im installing it right now :)
Still i think that this is some serious downgrade :/
In lubuntu which i used in the meantime i could also configure this behaviour directly

---

### Post by cheatos on 2013-03-09
okay, so it runs now. I have adjusted the auto.raise delay to 200 (i think milliseconds doesnt say so in the program)
but nothing happens.
Will i have to restart x server?
In the meantime i have restarted my xserver but nothing changed. Still no elevation of the window by mouseover :(
I realy liked that feature over windows and would love to have it again.
if it won't work as i want it to, would i be able to have the ubuntu desktop look and feel but with a lubuntu "under the hood"? Because there it worked well

---

### Post by stinkeye on 2013-03-09
> **cheatos said:**
> okay, so it runs now. I have adjusted the auto.raise delay to 200 (i think milliseconds doesnt say so in the program)
but nothing happens.
Will i have to restart x server?
In the meantime i have restarted my xserver but nothing changed. Still no elevation of the window by mouseover :(
I realy liked that feature over windows and would love to have it again.
if it won't work as i want it to, would i be able to have the ubuntu desktop look and feel but with a lubuntu "under the hood"? Because there it worked well
Have you unmarked "click to focus"

---

### Post by deadflowr on 2013-03-09
> [COLOR=#000000]Will i have to restart x server?[/COLOR]

You shouldn't have to.

Though, when you institute any changes through ccsm, there will be a period when it will seem like it is broken.
Best practice is to wait it out.
Killing X, while it readjusts itself can result in bad breakage.

It's typically the reason for the warning you get when you first launch it.
Most people unfamiliar with ccsm, when first used, will think the program broke the desktop, but in reality it takes a little time for the adjustments to take place. They then kill X, and that leaves compiz settings in a twilight zone.

---

### Post by cheatos on 2013-03-20
> Have you unmarked "click to focus"

That was it, missed the tick there.
Thanks alot

---

### Post by cheatos on 2013-03-20
uhmm and another thing...
How do i mark this as solved?
The new layout is still confusing me...

---

### Post by stinkeye on 2013-03-20
[CENTER]SEE BELOW
[color="#40e0d0"][b]|
|
|
|
|
v[/b][/color][/center]

---

### Post by cheatos on 2013-03-20
thanks, marked it correctly now.

---

