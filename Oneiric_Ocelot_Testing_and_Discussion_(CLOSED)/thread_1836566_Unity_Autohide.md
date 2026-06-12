---
title: "Unity Autohide"
date: 2011-08-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2011-08-31
Unity plug in, dodge windows and dodge active windows does not work, auto hide does.
Any one else see this or know whats wrong ?

Thanks

---

### Post by rbrick49 on 2011-08-31
i think its broken from todays updates cecil

---

### Post by mc4man on 2011-08-31
Did see it quite often on an install of 08/20 after about 5 days or so - seemed to be no good way to fix. (switching workspaces seemed to bring it on but not conclusively..
Since dumping that install for one from 08/27 it hasn't yet occurred.

---

### Post by cecilpierce on 2011-08-31
> **rbrick49 said:**
> i think its broken from todays updates cecil

Thanks, I think mine has been acting up for a week or so ???
Just went to nvidia-current and that din not help, oh well have to wait and see  :lolflag:

Thanks for the reply, thought I was all alone here

---

### Post by cecilpierce on 2011-08-31
> **mc4man said:**
> Did see it quite often on an install of 08/20 after about 5 days or so - seemed to be no good way to fix. (switching workspaces seemed to bring it on but not conclusively..
Since dumping that install for one from 08/27 it hasn't yet occurred.

Seems like I tried 2D and then back to 3D and it started working but after reboot it stoped auto-hide again. 
Oh well !!!

---

### Post by vpharry on 2011-08-31
You may try restartin unity. Just Press *ALT+F2* and type **unity --replace**

---

### Post by pbhedlund on 2011-10-07
I keep having issues with dodge windows. Sometimes it works, sometimes it doesn't. Interestingly I have discovered that adding BottomLeft to Reveal Mode always works even if Left doesn't.

Anyone else see this or have any tips?

MacBook Air 3,2; nvidia driver

---

### Post by ubj on 2011-10-07
> **pbhedlund said:**
> I keep having issues with dodge windows. Sometimes it works, sometimes it doesn't. Interestingly I have discovered that adding BottomLeft to Reveal Mode always works even if Left doesn't.

Anyone else see this or have any tips?

MacBook Air 3,2; nvidia driver

[http://ubuntuforums.org/showthread.php?t=1836566](http://ubuntuforums.org/showthread.php?t=1836566)

---

### Post by pbhedlund on 2011-10-07
> **ubj said:**
> [http://ubuntuforums.org/showthread.php?t=1836566](http://ubuntuforums.org/showthread.php?t=1836566)

Yes, that's this thread but the last post was more than a month ago and issues persist.

Yes, I can do the Unity replace thing and it works, but is there any new information?

---

### Post by makitso on 2011-10-07
I tried to use Unity / Auto hide with AWN.  The problem is that whenever you launch an app from AWN or move a folder anywhere on the desktop, Unity pops half way out.   I have tried to prevent Unity from doing this but no luck to this point.[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

---

### Post by effenberg0x0 on 2011-10-07
I think I figured it out. Unity panel is "dodging" an "invisible" active window here. You minimize / restore a window (I'm doing it to Thunderbird) a couple of times until it gets invisible (if you right click the desktop you see Thunderbird options and not nautilus options). At this point, the Unity panel won't come out anymore.

My workaround was to go to ccsm and deactivate the dodge behavior in Unity Plugin (set to always show panel). 

There are many bug reports for the "invisible window" problem, so I won't report it again, don't think its necessary.

Regards,
Effenberg

**EDIT: **I am not sure, but I think Unity panel is behaving more stable when I kill Conky.

---

### Post by mc4man on 2011-10-07
> **makitso said:**
> I tried to use Unity / Auto hide with AWN.  The problem is that whenever you launch an app from AWN or move a folder anywhere on the desktop, Unity pops half way out.   I have tried to prevent Unity from doing this but no luck to this point.
The launcher reveal on cursor grab & move on a file cannot be disabled, it's a non-optional feature

---

