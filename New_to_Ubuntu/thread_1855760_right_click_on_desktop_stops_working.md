---
title: "right click on desktop stops working"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by beew on 2011-10-06
Hi,

I have been messing with Lubuntu, I tried to change the wall paper by right clicking on the desktop and somehow I screwed up something and now right clicking on the desktop no longer does anything.

Help!

---

### Post by ubudog on 2011-10-06
Hey there, do you know what you did?  Can you notice any changes after doing what you did?

---

### Post by beew on 2011-10-06
I accidentally checked a box and then the application shut down because of jittery mouse movement I suppose and afterwards there are more options when right clicking a folder like "open in the same tab, open in the same window, open in terminal, file manager" these were not there before. I can't say exactly what was the box that I clicked because it was an accident.

I am wondering if there is a configuration file somewhere I can edit to get the function back.

Thanks.

---

### Post by ubudog on 2011-10-06
I haven't used Lubuntu - do you know what desktop manager it uses (Openbox, XFCE, Gnome)?

---

### Post by beew on 2011-10-06
> **ubudog said:**
> I haven't used Lubuntu - do you know what desktop manager it uses (Openbox, XFCE, Gnome)?

I think it is suppose to be LXDE but I have also installed compiz so that may become the desktop manager.

---

### Post by ubudog on 2011-10-06
You could try resetting LXDE:
[http://forum.lxde.org/viewtopic.php?t=94&f=8](http://forum.lxde.org/viewtopic.php?t=94&f=8)

That may help - but it should reset your appearance settings.

---

### Post by beew on 2011-10-06
Hi,

Strangely enough I removed the whole folder .config/lxpanel while the panel settings were restored the right click function still doesn't work.

Also removing .config/lxession and .config/pcmanfm don't work.

---

### Post by beew on 2011-10-07
I found a solution!

I installed the Lubuntu-control-center from this ppa [https://launchpad.net/~lubuntu-desktop/+archive/ppa](https://launchpad.net/~lubuntu-desktop/+archive/ppa)

In it there is an option called background,when you click it a window pops up with the tile "desktop preference", which is the same popup window that I was accessing by right clicking before I messed up. My problem was caused by accidentally checking the box "Show menus provided by window managers when desktop is clicked" under the advanded tab. I unchecked it and the right click function is restored.

I have 3 thoughts

1) There has to be a more elegant way to fix this problem by editing some file rather than having to install an extra piece of software. I still can't find the configuration file.

2) The Lubuntu-control-center should be installed by default, or at least in the repo, it is very useful because lubuntu's options are all over the places and are rather limited comparing to gnome or kde. I luckily stumbled upon it in an unrelated thread when randomly googling.

3)The option that caused my problem is completely counter intuitive, by the wording of it you would think that checking and unchecking the box would have the opposite effect than what it actually does.

---

### Post by ClientAlive on 2011-10-07
> **beew said:**
> I found a solution!

I installed the Lubuntu-control-center from this ppa [https://launchpad.net/~lubuntu-desktop/+archive/ppa](https://launchpad.net/~lubuntu-desktop/+archive/ppa)

In it there is an option called background,when you click it a window pops up with the tile "desktop preference", which is the same popup window that I was accessing by right clicking before I messed up. My problem was caused by accidentally checking the box "Show menus provided by window managers when desktop is clicked" under the advanded tab. I unchecked it and the right click function is restored.

I have 3 thoughts

1) There has to be a more elegant way to fix this problem by editing some file rather than having to install an extra piece of software. I still can't find the configuration file.

2) The Lubuntu-control-center should be installed by default, or at least in the repo, it is very useful because lubuntu's options are all over the places and are rather limited comparing to gnome or kde. I luckily stumbled upon it in an unrelated thread when randomly googling.

3)The option that caused my problem is completely counter intuitive, by the wording of it you would think that checking and unchecking the box would have the opposite effect than what it actually does.


Hi beew,

I'm not really familiar with a lot of it but could the following contain any info that's useful to you? An absolute path or two? Not sure if it's applicable. You'd know better than me I think.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540929](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540929)

HTH

:)
-----------

PS: third post down is interesting too.
-----------

Edit:

/etc/lxsession/

??

---

