---
title: "[SOLVED] Autoplay for ubuntu?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-07-30
[IMG]http://img150.imageshack.us/img150/4269/autoplayoi5.png[/IMG]

Is there a similar feature like windows autoplay for Linux? which will give me options of what i would like to do with the removable media which i plugged in?

Thanks in advance:D

---

### Post by halitech on 2008-07-30
if you go to System - Preferences - Removable drives and media you can set those all up there

---

### Post by SunnyRabbiera on 2008-07-30
It does have a autoload of sorts, with most DVD's or disks totem opens up a good percent of the time. or with external hard drives and such it will load nautilus.
KDE 3 does one better by offering options like windows on what you can choose to open a DVD and such.
Gnome used to have a feature like this but its been dropped for some stupid reason or another, thus is one of the many reasons I dont like gnome though I will take it anyday over KDE 4.

> **halitech said:**
> if you go to System - Preferences - Removable drives and media you can set those all up there

Sadly its very limited compared to the way it was before.
Now you have a dialog in nautilus that gives you totem, or nothing limiting options...

---

### Post by Xerp on 2008-07-30
Mine does autoplay for the things I use - like my camera, ipod and DVDs. Trying to get autoplay for something specific?

---

### Post by m_ad on 2008-07-30
This looks like it only gives options for Cameras, PDAs, Printers & Scanners or Input Devices (Mice, Keyboards, etc).

---

### Post by SunnyRabbiera on 2008-07-30
> **m_ad said:**
> This looks like it only gives options for Cameras, PDAs, Printers & Scanners or Input Devices (Mice, Keyboards, etc).

Yeh thats all in the newer version of gnome, older versions used to offer options with that app but now its very limited...
And I very much dislike it.

---

### Post by halitech on 2008-07-30
> **SunnyRabbiera said:**
> 
Sadly its very limited compared to the way it was before.
Now you have a dialog in nautilus that gives you totem, or nothing limiting options...

I've actually changed mine for DVDs to open in VLC, just entered in vlc %m and when I put in a DVD it opens in vlc. I never used the option previously, just accepted the defaults when I was learning so wasn't until 7.10 that I started playing around more

edit: just checked my laptop that has 8.04 on it and I see what you mean, very limited now. good thing the laptop doesn't have a cd drive so it doesn't really matter on it.

---

### Post by SunnyRabbiera on 2008-07-30
yeh its so much of a pain now, I hope they resolve that in the next version but the gnome development team is known for crap like this...
These days its kde 3 that looks the best out of all of them, but its loosing its support every day in favor of the inferior (for now) KDE 4

---

### Post by mujrim on 2008-07-30
How would you change the autoplay for DVD?  I have VLC installed, and I would like to use that to watch DVDs, but when I insert a DVD, Totem Movie Player pops open.

---

### Post by kamitsukai on 2008-07-30
Thanks but i was hoping for something like autoplay as sometimes i might like to backup my dvds (legal here...) and other times i might want to watch it or if i have pictures on  my thumb drive i would maybe like to view it as a sideshow without going in to something like nautilus to hunt the pictures down :|
-----------

Also as KDE have released a new revamped version (KDE 4) is gnome planning on going slightly more eyecandyish? (yes i know hat "eye-candy-ish" isn't a word lol)

---

### Post by SunnyRabbiera on 2008-07-30
Its difficult I am afraid, blame that on the gnome development team, read this topic:
[http://ubuntuforums.org/showthread.php?t=869921&highlight=default+DVD+player](http://ubuntuforums.org/showthread.php?t=869921&highlight=default+DVD+player)

---

### Post by m_ad on 2008-07-30
> **mujrim said:**
> How would you change the autoplay for DVD?  I have VLC installed, and I would like to use that to watch DVDs, but when I insert a DVD, Totem Movie Player pops open.

You can actually change what applications open when certain media is inserted, but you can't have options like the dialog the OP showed. In nautilus, open Edit->Preferences and click the Media tab. This should do it :)

EDIT: Actually, what happens when you select "Ask what to do?"

---

### Post by SunnyRabbiera on 2008-07-30
> **kamitsukai said:**
> Thanks but i was hoping for something like autoplay as sometimes i might like to backup my dvds (legal here...) and other times i might want to watch it or if i have pictures on  my thumb drive i would maybe like to view it as a sideshow without going in to something like nautilus to hunt the pictures down :|
-----------

Also as KDE have released a new revamped version (KDE 4) is gnome planning on going slightly more eyecandyish? (yes i know hat "eye-candy-ish" isn't a word lol)

Nah, there are no plans for a gnome 3 right now, a revamp like that wont come anytime soon.
In a way thats good as I think KDE 4 was rushed.

> **m_ad said:**
> You can actually change what applications open when certain media is inserted, but you can't have options like the dialog the OP showed. In nautilus, open Edit->Preferences and click the Media tab. This should do it :)

EDIT: Actually, what happens when you select "Ask what to do?"

Sadly this doesnt do diddly, gnome just targets totem.

---

### Post by kamitsukai on 2008-07-30
Well thanks anyway :D hopefully the gnome developers will re-implement the feature in the **_near_** future:lolflag: although it's not enough to sway me to KDE...

---

### Post by SunnyRabbiera on 2008-07-30
Trust me the gnome team has done some stupid crap in its day.

---

### Post by mujrim on 2008-07-30
Thanks Sunny, it was pretty simple though.

---

### Post by mc4man on 2008-07-30
While it is limited you can get some added functions with a little fooling around.
Vlc is easy to add as here [http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

You can also add other apps thru defaults.list and or mimeapps.list though one must be very careful about re editing the same line in defaults multiple times.
You can also either create a new .desktop or copy an existing one, rename it, change the exec=, and add it thru defaults.list, and or mimeapps.list.
example of copy
[http://ubuntuforums.org/showthread.php?t=874280](http://ubuntuforums.org/showthread.php?t=874280)

Again you have to be careful about overusing these lists - things can get borked easily. 

With the exception of vlc (used above link method) I use apps that gnome adds as choices that _I'm not going to use_ to run scripts that will open an app that i want to use. This method is very safe and easily reverted.
For example i use banshee to autoplay cds with amarok and gxine to autorun vobcopy for dvds.
Irregardless of what action I've set as the default if I want to use another one holding down the shift while inserting media brings up a choice box.

using scripts off of autorun
[http://ubuntuforums.org/showthread.php?p=5456622#post5456622](http://ubuntuforums.org/showthread.php?p=5456622#post5456622)
info specific to amarok
[http://ubuntuforums.org/showthread.php?p=5459412#post5459412](http://ubuntuforums.org/showthread.php?p=5459412#post5459412)

---

