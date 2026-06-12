---
title: "Appearances and preferences"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-06-03
Suddenly Appearances and preferences menu uses 100% CPU when I try to change desktop background, theme etc....Is there a fix for this? I can't remember it to use this much CPU earlier :confused:

---

### Post by _sphinx_ on 2008-06-03
I was having the similar problem but I my case the 100% cpu usage was just for 5 or 6 second so I really didn't cared about that thing. For what amount of time are you having that kind of usages?

---

### Post by kpkeerthi on 2008-06-03
> **peakshysteria said:**
> Suddenly Appearances and preferences menu uses 100% CPU when I try to change desktop background, theme etc....Is there a fix for this? I can't remember it to use this much CPU earlier :confused:
I noticed that too but I guess that was because I had a lot of themes/backgrounds added in there. I cleaned unused ones and it was back to normal.

---

### Post by terrordrone on 2008-06-03
when your system slows down, type top in shell 
post the output of first 5-6 lines

---

### Post by peakshysteria on 2008-06-03
> **_sphinx_ said:**
> I was having the similar problem but I my case the 100% cpu usage was just for 5 or 6 second so I really didn't cared about that thing. For what amount of time are you having that kind of usages?

For as long as I have the Appearances and preferences menu open. When i close it it gets down to normal. It's not a big deal since I'm not there for very long. But it would be nice if it where as it should be.

> **kpkeerthi said:**
> I noticed that too but I guess that was because I had a lot of themes/backgrounds added in there. I cleaned unused ones and it was back to normal.

I guess there really aren't a limit to how many themes backgrounds you can have? Can't say I've added a wast amount exactly :)

> **terrordrone said:**
> when your system slows down, type top in shell 
post the output of first 5-6 lines

Gnome-appearance seems to use between 68-85% The rest is other things. But anyway it's not as it should be. It were never like this before. The only big change is that I've checked hardy-proposed. Nothing else I can think of. Everything else is running very smooth now actually. It's only this little thing (and flash, java, ATI, lol)...

---

### Post by peakshysteria on 2008-06-03
Eh, sorry for the double post. terrordrone here's a screenshot of top intended for the above post :)

Edit:

The issue seems to have resolved itself. Got an update this morning. Among other things a kernel update (2.6.24-18-generic). Now the excessive CPU use problem is gone :)

---

### Post by Woormy on 2008-06-04
> **peakshysteria said:**
> Suddenly Appearances and preferences menu uses 100% CPU when I try to change desktop background, theme etc....Is there a fix for this? I can't remember it to use this much CPU earlier :confused:

I have the same problem but it started after installing security and kernel updates.

I'm seeing now that it lags when trying to change wallpaper but not themes.

---

### Post by CharlieFoxtrot on 2008-06-04
Same here. Changed desktop background. Then couldn't change back. 

Ah, found something. I am unable to select a wallpaper with the MOUSE. Selecting wallpaper works fine however using the arrow keys. Conky reports gnome-appearance process using 40-50% cpu. I have a Core 2 Duo processor, so it's using most of one cpu. Don't know if that's normal.

If you can't change background wallpaper, try selecting with your arrow keys.

---

### Post by peakshysteria on 2008-06-05
It solved it self in my end. Just waited it off. Now everything is smooth again :)

---

### Post by FuturePilot on 2008-06-05
Bug
[https://bugs.launchpad.net/ubuntu/hardy/+source/nautilus/+bug/236778]("https://bugs.launchpad.net/ubuntu/hardy/+source/nautilus/+bug/236778")
One of the recent updates caused this. A fix is on the way.

---

