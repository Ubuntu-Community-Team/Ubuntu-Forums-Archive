---
title: "Last update corrupted my WeatherChannel screenlet"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by S2UIRR3L on 2012-05-04
Has anyone else encountered this?

The update manager just popped up (04-MAY-2012) and as usual, I just accepted everything that was checked in the list (entered my password, it started downloading, installing, ect.) and now my WeatherChannel screenlet is stuck. When I try to re-activate it, it does nothing but get stuck on the desktop and it takes a LONG time before I can left-click to delete it.

Does anyone have any idea what may have caused this?

---

### Post by kostkon on 2012-05-04
Try resetting it from the screenlets manager, not just restarting it.

---

### Post by S2UIRR3L on 2012-05-04
I've tried and it just hangs there, turns gray scale (not responding) then comes back as if I haven't touched it in the first place.

Here's a screen capture that I've uploaded to this site when everything was working. The info might be outdated tho, so...

Is there a way to "go back" sort of like System Restore? I don't have much to lose, everything is externally backed up.

(KEEP IN MIND - THE PHOTO BELOW SHOWS MY DESKTOP AS IT WAS WHEN IT WORKED - WEATHER ISN'T THERE NOW)


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216080&d=1334519056[/IMG]

---

### Post by Peripheral Visionary on 2012-05-04
I use Xubuntu 10.04 and my Xfce weather applet (also Weather Channel based) also quit working today and remains "greyed out" and won't refresh. I suspect it may be a Weather Channel thing and not a 'buntu issue at all.

---

### Post by Peripheral Visionary on 2012-05-04
Okay, my weather applet just "came back on" a few minutes ago. Yours too?

---

### Post by S2UIRR3L on 2012-05-05
Just checked it and wow - it's back and working like a champ!
Who knows what it was, but it was screwing with my pc BAD!!!

I'm going to leave this open for a few more days, just in case
some thing is still wrong... If nothing else, I'll mark it SOLVED.

Thanks a million every one!!!

-Leo

---

### Post by shof2k on 2012-05-06
Not sure if this is related, but I found there was a python bug in the screenlet after installing 12.04. Something about a library that is now deprecated. It was easy enough to fix after googling the error.  Let me know if you want more details.

Peace

---

### Post by JKyleOKC on 2012-05-06
FWIW, my Weather Update panel goodie in Xubuntu 10.04 exhibited the same symptoms for a couple of days. It's written in C, not Python, but gets its data from The Weather Channel also. I suspect the problem is/was at TWC, not at our machines at all.

It's working fine this morning, just as it had been for several years before this past few days...

---

### Post by Curtis6767 on 2012-05-06
Weather Channel has been doing a lot of work on their site this past week including a complete facial. Data pages are now completely different.

Related?

---

### Post by shof2k on 2012-05-06
Still working here

---

### Post by S2UIRR3L on 2012-05-06
> **shof2k said:**
> Not sure if this is related, but I found there was a python bug in the screenlet after installing 12.04. Something about a library that is now deprecated. It was easy enough to fix after googling the error.  Let me know if you want more details


You're more than welcome to post a link to the "fix" that you found. I'm sure there's more and more people moving onto 12.04 (I'm on 10.04). But it's very useful information and I thank you for contributing to this post. As I said before, I'll wait a few more days before marking it solved, even tho my weather thing is all straitened out and works perfect again.

I'm starting to agree that it was TWC because I didn't tweak anything to make it work again.

-Leo

---

### Post by shof2k on 2012-05-07
It was using the ClearWeather Screenlet.  After downloading and installing it, change the script ~/.screenlets/ClearWeather/ClearWeatherScreenlet.py by:

1) Comment out the line "from Numeric import *" so it looks like
```
 #from Numeric import *
```
2) Add the following line
```
 import numpy 
```

All should be well

---

### Post by S2UIRR3L on 2012-05-08
> **shof2k said:**
> It was using the ClearWeather Screenlet.  After downloading and installing it, change the script ~/.screenlets/ClearWeather/ClearWeatherScreenlet.py by:

1) Comment out the line "from Numeric import *" so it looks like
```
 #from Numeric import *
```2) Add the following line
```
 import numpy 
```All should be well

Thanks a million!

---

### Post by S2UIRR3L on 2012-05-12
Thanks a million for all the input guys - It's very much appreciated!!!

-Leo

---

