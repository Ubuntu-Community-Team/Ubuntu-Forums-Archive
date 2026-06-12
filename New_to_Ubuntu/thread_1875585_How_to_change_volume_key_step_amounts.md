---
title: "How to change volume key step amounts?"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by jayi on 2011-11-05
Hello! I am using xubuntu 11.10 and I was wondering how to change the volume key step amount? What I mean by this is that when I hover over the volume control and move it with the mouse scroll button, it moves by a huge amount when I actually want to make only a very small adjustment to the volume level.

In ubuntu, I know I used this solution:

> 
[LIST=1]
[*]Press Alt+F2 to bring up the “Run” box.
[*]Type in “**gconf-editor**” and press enter.
[*]Select “**Apps** > **gnome_settings_daemon**“
[*]On the right hand side you’ll have a single option named “**volume_step**“
[*]Change the numerical value (*6* by default) to a lower one (*3* seems pretty good)
[/LIST]


(I got these instructions from a website but I'm not putting the link because I'm not sure if that is ok according to forum rules?)

However, in xubuntu things seem a little bit different and I cannot do this. Does anyone have any experience with this?

Bonus would be if someone knows a way to configure keyboard shortcuts to change the volume.

Thank you. :)

---

### Post by azertyh on 2011-11-05
> **jayi said:**
> Bonus would be if someone knows a way to configure keyboard shortcuts to change the volume.

hello,

yes, it's possible.

to increase the volume, settings > settings manager > keyboard > shortcuts > add > command = amixer set Master 5+ > ok > hit the key you want to increase the volume > ok.

to decrease the volume, the command is amixer set Master 5-

of course, you can set 10+ or 1+.

hope it was clear.

---

### Post by jayi on 2011-11-05
> **azertyh said:**
> hello,

yes, it's possible.

to increase the volume, settings > settings manager > keyboard > shortcuts > add > command = amixer set Master 5+ > ok > hit the key you want to increase the volume > ok.

to decrease the volume, the command is amixer set Master 5-

of course, you can set 10+ or 1+.

hope it was clear.

Hi, thanks for this information. Unfortunately, it does not work for me. :(

When I press the shortcut key I assigned (<Shift><Control>Left), there is no volume change no matter how much I pressed and there is no visual indicator that the volume is changing like there was before when I used ubuntu with gnome.

---

### Post by azertyh on 2011-11-12
hello,
what happens if you type the command in a terminal?
try also amixer sset Master 5+.

---

### Post by kid1000002000 on 2012-01-15
Workarounds are good, but don't forget to subscribe to this bug.
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/871133](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/871133)

---

### Post by paul079 on 2012-01-24
To change the volume_step value, what you want is Applications->Settings->Settings Editor

I think that's the right name, I can't look at it right now, but you want the *Editor* & not the *Manager*.  Volume step is in the drop down under "sound".  Highlight it, click the edit button (pencil at the top), and change the value to whatever you want.


As far as the shortcuts go, sorry, but I can't help you there.  I'm still trying to get mine working on a fresh installation on my desktop (my laptop worked automatically).

---

### Post by paul079 on 2012-01-24
Have a look at this:
[http://docs.xfce.org/xfce/xfce4-settings/keyboard]("http://docs.xfce.org/xfce/xfce4-settings/keyboard")

5% in the commands is the step amount.


Note: This is in *Settings Manager[I] and not *Settings Editor[/I] (just want to clarify since it is confusing sometimes).  I can't try it myself until I get home tonight to see if it works.



I do know this, in a terminal typing ```
man -q 'mix'
``` will list all of the mixers installed on your system.  Then, ```
man + *your mixer*
``` will give you the command switches for it (to put for the shortcuts).

---

