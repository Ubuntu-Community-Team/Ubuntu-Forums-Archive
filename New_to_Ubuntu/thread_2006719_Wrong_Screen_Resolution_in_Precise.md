---
title: "Wrong Screen Resolution in Precise"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by mlnease on 2012-06-19
Hello,

Precise doesn't correctly identify my graphics card --Intel  82Q963/Q965 Integrated Graphics Controller (rev 02)--and I can't set the  resolution (1280 x 1024 (5:4), Refresh Rate 75Hz).  In the monitor  setting, it is shown as 1280 x 1024, Refresh Rate 60Hz--but about half  an inch is cut off from the right side of my screen.  A bit awkward as  that's where I keep my window buttons...

If I change the refresh rate manually to 75Hz, the screen flickers catastrophically and all input it disabled.

Anyone else have a similar problem with this controller?  It works perfectly in Ubuntu 10.04 on another partition, by the way.

Ubuntu 12.04
XFCE Desktop

Any advice would be much appreciated.

Thanks in Advance,

mike

---

### Post by theDaveTheRave on 2012-06-19
mlnease,

I don't want to sound silly but..
couple of things, are you running XFCE on both partitions, I aks because I run xubuntu and it chops the bottom off no end of windows when they open!

Also when you say you loose about half an inch at one side, are you saying that your "button" are physically not visible. Does this change when you alter the refresh rate to 75HZ (ie you can now see your buttons).

If it is the case that the buttons suddenly become visible, can I make some really daft suggestions.

Move your buttons to another edge of the screen, to see if the new edge is now the one that is "missing" (just to prove that it isn't a problem with the menu bar).

Do you have another deskto environment to test to see if it is a XFCE problem (particularly if you are running a different environment on your other partition).

You should be able to pull the settings from your old setup (drivers etc), but I'm not that sure of how you would do this.

You may find others with your graphics card have experienced the same problems, so check out the bug trackers...

I know it doesn't really help that much, but... maybe it will get you on your way to a solution.

David

---

### Post by mlnease on 2012-06-19
Hi David,

And thanks for the quick response:

> **theDaveTheRave said:**
> mlnease,

I don't want to sound silly but..
couple of things, are you running XFCE on both partitions, I aks because I run xubuntu and it chops the bottom off no end of windows when they open!
Not silly at all, but no, the other partion features Lucid with GNOME2.
> Also when you say you loose about half an inch at one side, are you saying that your "button" are physically not visible. Does this change when you alter the refresh rate to 75HZ (ie you can now see your buttons).No--changing the refresh rate to 75Hz fubars the display.  It flickers and scrolls madly and any input becomes impossible.> 
If it is the case that the buttons suddenly become visible, can I make some really daft suggestions. Move your buttons to another edge of the screen, to see if the new edge is now the one that is "missing" (just to prove that it isn't a problem with the menu bar).Actually I have tried that--it's *always* the right edge of the screen that's cut off (of any maximized window).> Do you have another deskto environment to test to see if it is a XFCE problem (particularly if you are running a different environment on your other partition).As above--Lucid with GNOME2, which works flawlessly.> You should be able to pull the settings from your old setup (drivers etc), but I'm not that sure of how you would do this.A mystery to me, too--> You may find others with your graphics card have experienced the same problems, so check out the bug trackers...Yes, thanks, I've been doing that.  No luck so far.> I know it doesn't really help that much, but... maybe it will get you on your way to a solution.

DavidI think it does help even if only to force me to go over old ground again--I find things that way sometimes.  Thanks again for your time and attention.

mike

---

### Post by theDaveTheRave on 2012-06-20
mlnease,

so the first step as I see it is to try XFCE on your lucid install and gnome2 on precise.

If it is always one particlar side of the screen that is very odd.

It could be that there is an issue with 'window placement' and 'size' so everything is made too large and over to one side by accident, unfortunately I don't know how to start on troubleshooting that one (as I say on my assus it seems to be the OK|Cancel buttons on the bottom of input screens. I find it anoying but can live it as a 'bug' on such a small screen, and I haven't bothered to look into it properly).

I guess it must be a bug in the driver and it not collecting the correct screen resolution. do you have another screen to plug in to see if the same thing happens?

Sorry again for not really being that much help.

David

---

### Post by mlnease on 2012-06-20
> **theDaveTheRave said:**
> mlnease,

so the first step as I see it is to try XFCE on your lucid install and gnome2 on precise.

If it is always one particlar side of the screen that is very odd.

It could be that there is an issue with 'window placement' and 'size' so everything is made too large and over to one side by accident, unfortunately I don't know how to start on troubleshooting that one (as I say on my assus it seems to be the OK|Cancel buttons on the bottom of input screens. I find it anoying but can live it as a 'bug' on such a small screen, and I haven't bothered to look into it properly).

I guess it must be a bug in the driver and it not collecting the correct screen resolution. do you have another screen to plug in to see if the same thing happens?

Sorry again for not really being that much help.

David
That's an interesting thought (the switcheroo) and a good idea.  I might give it a try--but I've hosed a couple of installs by adding and removing DEs (I'm definitely a tweak-it-till-it-breaks guy), and I have these exactly as I like them othewise.  So I guess I'll just let it slide for now.

Thanks again for your time and trouble.

mike

---

### Post by theDaveTheRave on 2012-06-22
remember that if you find a solution to put it in the thread.

I'm surprised you manage to kill your installs just with the addition of a desktop environment !  You must really like to play !

David

---

### Post by mlnease on 2012-06-22
> **theDaveTheRave said:**
> remember that if you find a solution to put it in the thread.

I'm surprised you manage to kill your installs just with the addition of a desktop environment !  You must really like to play !

David
Well, it was really adding then deleting several DEs...and yes, I really do!

Thanks again!

mike

---

