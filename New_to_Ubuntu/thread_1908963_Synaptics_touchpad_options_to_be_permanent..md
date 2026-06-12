---
title: "Synaptics touchpad options to be permanent."
date: 2012-01-14
forum: New to Ubuntu
---

### Post by il_maniscalco on 2012-01-14
I really don't know if this is a "absolute beginner talk" issue, but it's prudent to start here, then perhaps someone will move this somewhere else.
I've been investigating all the afternoon in trying to let the "LockedDrag" option of my Synaptics Touchpad to work, and I did not find the solution.

For what I understood this could be a bug of Ubuntu 11.10, but I'm not sure if really was a bug and now is solved, however here's what I did.

One thing I figured is that using the synclient command, I could make the following:

[HTML]
     synaptics LockedDrags=1
[/HTML]

Doing this the locked drag works.
But if I:

[HTML]
     sudo rmmod psmouse
     sudo modprobe psmouse
[/HTML]

The options are reset.
So I found that I should edit my 50-synaptics.conf file located in the /usr/share/X11/xorg.conf.d directory (actually the file says I should copy it in the /etc/X11/xorg.conf.d directory and in fact I tried also to do this), adding the

[HTML]
     Option "LockedDrags" "1"
[/HTML]

line in the input section.
But have no success, the option will never appear on, and checking through synclient will actually confirm it's still off. I also tried to create a xorg.conf file in the X11 directory, no change.

So please what should I do?

---

### Post by I_can_see_the_light on 2012-01-14
Do you modprobe the psmouse module often? I don't quite understand what it is that you need to do. Do you want the LockedDrags option to be present at startup?

If that's the case then you can create a file called autostart.sh with the following contents:
```
#!/bin/bash
synclient LockedDrags=1 &
```Place the file inside **/home/<username>/bin/** and make it executable, then add it to *Startup Applications*.

---

### Post by il_maniscalco on 2012-01-14
ok I realized I could create a script but I wondered if that was the cleanest way to the the task.

By the way: I just checked the startup applications, and there is one who's called: 

no name - no description

what's this and why is there? :)

---

### Post by I_can_see_the_light on 2012-01-14
> **il_maniscalco said:**
> ok I realized I could create a script but I wondered if that was the cleanest way to the the task.
I'm not sure, there could be some sort of graphical application to set those settings for you. In KDE there's Synaptik but I don't know of any Gnome application, take a look in the Software Center :)

> **il_maniscalco said:**
> By the way: I just checked the startup applications, and there is one who's called: 

no name - no description

what's this and why is there? :)

I really don't know, it's not present on my machine. If you click it and then select *Edit*, what's the command that should be executed?

---

### Post by il_maniscalco on 2012-01-14
unfortunately there's no synaptics option gui at least I did not find it and did not find nothing about online. Instead I found other people having this issue, basically that the conf file for the driver is "overwhelmed" by a gnome damon which reset the default settings..
> 
I really don't know, it's not present on my machine. If you click it and then select *Edit*, what's the command that should be executed?

it's all empty.
I removed that; probably it was something reminiscence of Unity (I use gnome)
thanks

---

