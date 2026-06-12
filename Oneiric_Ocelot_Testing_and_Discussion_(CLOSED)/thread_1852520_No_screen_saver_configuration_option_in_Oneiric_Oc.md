---
title: "No screen saver configuration option in Oneiric Ocelot"
date: 2011-09-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mmasroorali on 2011-09-30
There do not seem to be any screen saver configuration option in Oneiric Ocelot. I installed xscreensaver. Looked under appearance, displays, screen, without any avail.

Things were fine in 11.04.

What is it I might be missing?

---

### Post by jbicha on 2011-09-30
Check the dash. xscreensaver is not integrated into System Settings.

---

### Post by Luke has no name on 2011-09-30
I can't find screensaver settings or font settings in the control panel.

---

### Post by cariboo on 2011-09-30
> **Luke has no name said:**
> I can't find screensaver settings or font settings in the control panel.

The gnome devs feel we don't need a screensaver anymore, to set screen timeout and lock settings check System Settings->Screen, to change font and size, you'll need to install gnome-tweak-tool, which also installs gnome shell. If you only want to change font size, click System Settings->Appearance.

---

### Post by madjr on 2011-09-30
> **cariboo907 said:**
> The gnome devs feel we don't need a screensaver anymore, to set screen timeout and lock settings check System Settings->Screen, to change font and size, you'll need to install gnome-tweak-tool, which also installs gnome shell. If you only want to change font size, click System Settings->Appearance.

still there is a blue-print to bring screen saver back (building it directly into compiz or something)

---

### Post by cariboo on 2011-09-30
We are in [Final Freeze]("https://wiki.ubuntu.com/FinalFreeze"), so we won't be seeing any new features until PP

---

### Post by Utew on 2011-09-30
@mmasroorali, 

You might want to check out Electric Sheep (screensaver).. my favorite, it's in the repositories. After install run *electricsheep* from your favorite Terminal. :p

---

### Post by thatguruguy on 2011-09-30
> **Utew said:**
> @mmasroorali, 

You might want to check out Electric Sheep (screensaver).. my favorite, it's in the repositories. After install run *electricsheep* from your favorite Terminal. :p

I've used electric sheep in Natty.  When you run it from terminal in 11.10, it runs in an mplayer window.  Which is nice, but not what's intended.  Will it run as a general screen saver (i.e., coming on automatically after a set period of time)?

---

### Post by Utew on 2011-10-01
@thatguruguy 
At this point the Mplayer option seems to be the only way to get electricsheep to run. 

If, in their wisdom the Gnome devs decide that we can have screen savers, perhaps that'll change. I'm curious myself, maybe I'll drop the electricsheep developer(s) a note and see if they have any advice. 

I know it may seem like a minor point to most, but I've always had a strange fascination with exceptional screen savers and would like to have a more configurable set of options and choices for same in 11.10.

---

### Post by mmasroorali on 2011-10-01
> **Utew said:**
> @thatguruguy 
At this point the Mplayer option seems to be the only way to get electricsheep to run. 

If, in their wisdom the Gnome devs decide that we can have screen savers, perhaps that'll change. I'm curious myself, maybe I'll drop the electricsheep developer(s) a note and see if they have any advice. 

I know it may seem like a minor point to most, but I've always had a strange fascination with exceptional screen savers and would like to have a more configurable set of options and choices for same in 11.10.

I am surprised that they find it unnecessary. It may sound ludicrous to some, but we can not ignore the look good value of a screen saver, specially when they appear at random. 

My two cents worth.

---

### Post by wgarcia on 2011-10-01
I'm not sure, but isn't it that it is not available because they still have not ported the screensavers to the new Gnome libraries? I seem to have read somewhere that they would do it eventually but that they have directed the priorities to other areas.

---

### Post by mmasroorali on 2011-10-01
> **wgarcia said:**
> I'm not sure, but isn't it that it is not available because they still have not ported the screensavers to the new Gnome libraries? I seem to have read somewhere that they would do it eventually but that they have directed the priorities to other areas.

I am afraid that I will have to disagree with you. Please see responses #'s 4 and 6, which clearly says that there will not be any screen savers any more.

---

### Post by grandtoubab on 2011-10-01
hello,
In screen properties you can set how to turn off it
[[img]http://pix.toile-libre.org/upload/thumb/1317458826.png[/img]](http://pix.toile-libre.org/?img=1317458826.png)

---

### Post by mmasroorali on 2011-10-01
> **grandtoubab said:**
> hello,
In screen properties you can set how to turn off it
[[img]http://pix.toile-libre.org/upload/thumb/1317458826.png[/img]](http://pix.toile-libre.org/?img=1317458826.png)

Thanks, but I have found that far. I am looking for screensavers. Previously, we had two time outs, one for screen saver, another for turning off the screen.

---

### Post by grandtoubab on 2011-10-01
in fact screen saver is no more appropriate as it don't save anything :) it you want save energy, just turn it off, what you are looking for is much more a screen eyecandy :popcorn:

---

### Post by t1497f35 on 2011-10-01
> **grandtoubab said:**
> in fact screen saver is no more appropriate as it don't save anything :) it you want save energy, just turn it off, what you are looking for is much more a screen eyecandy :popcorn:
No, it's the screensaver type people are used to across all major desktop OSes.

Also, "Screen" from settings is broken, I set it to "Never" and this crapware starts dimming the monitor instantly! This behavior is random as now after a few minutes of fumbling with it by turning it on and off it stopped dimming my monitor instantly. I set it to 1 hour but it kicks in in like 10 minutes. I'm disappointed - since gnome 3.2 is final and out and we don't have a screensaver, and the other option (the "Screen" option) is a lame duck. I'm not ranting, it's true.

---

### Post by rtalcott on 2011-10-01
I have the same problem with the instant dimming then it goes black after a short time... this is not the behavior that I have set either...

---

### Post by mmasroorali on 2011-10-01
> **t1497f35 said:**
> No, it's the screensaver type people are used to across all major desktop OSes.

Also, "Screen" from settings is broken, I set it to "Never" and this crapware starts dimming the monitor instantly! This behavior is random as now after a few minutes of fumbling with it by turning it on and off it stopped dimming my monitor instantly. I set it to 1 hour but it kicks in in like 10 minutes. I'm disappointed - since gnome 3.2 is final and out and we don't have a screensaver, and the other option (the "Screen" option) is a lame duck. I'm not ranting, it's true.

Perhaps I am saying too much here, but I am not sure whether those who say and try to establish that "we do not need screen saver any more and it is to be excluded from Ubuntu plus 1" have other agendas. Was it too much to add? Now when I try to convince my colleague that Ubuntu is something to give a try and he finds that there is no-screen-saver in Ubuntu, what should I tell him? Well...., err...., you do not need it. And he will think that it is such an OS which does NOT EVEN HAVE a screen saver.

A very mediocre comment? Perhaps yes. But we should know that we want bring mass people to Ubuntu. Those in the upper deck should know that.

---

### Post by grandtoubab on 2011-10-01
that is another problem with hibernate and/or suspend which do not work
try this to disable this functions
[I]Maurício Luciano 
 7 July 2010 at 03:36 

This solved for me on my Ubuntu 10.04.

In a Terminal &#8594; gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.upower.policy

There are two sections in this file, the first for suspend and the second for hibernate. In section will be a line with:
<action id="org.freedesktop.upower.suspend">
...
<allow_active>yes</allow_active>

Change this entry from &#8220;yes&#8221; to &#8220;no&#8221; to disable suspend.
<action id="org.freedesktop.upower.hibernate">
...
<allow_active>yes</allow_active>

Change this entry from &#8220;yes&#8221; to &#8220;no&#8221; to disable hibernate.

For disable the functions keys:
gconftool -s /apps/gnome-power-manager/buttons/hibernate -t string interactive
gconftool -s /apps/gnome-power-manager/buttons/suspend -t string interactive[/I]

[https://jeremy.visser.name/2007/02/how-to-disable-suspend-and-hibernate-for-all-users-in-ubuntu/](https://jeremy.visser.name/2007/02/how-to-disable-suspend-and-hibernate-for-all-users-in-ubuntu/)

It works for me

---

### Post by FootySr on 2011-10-01
I really don't need my monitor turned off for me but as others have said setting it to "never" isn't working. 

I prefer having a screensaver and then turning my monitor off manually when I'm stepping away from my desk for longer periods. 

This just seems like an oversight in development. :(

---

### Post by FootySr on 2011-10-06
Finally today's update has fixed this issue for me. I've set it to never and so far my screen hasn't turned off. ;)

Thank you!  :D

---

