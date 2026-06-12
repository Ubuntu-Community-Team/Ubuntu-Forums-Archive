---
title: "Ubuntu freezing randomly"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by alexjohnc3 on 2008-05-04
Often Ubuntu freezes for no apparent reason for a minute or two. The OS itself doesn't freeze, but rather the screen does. If I'm playing music the music keeps playing and I can move the cursor, but everything on the screen is frozen (aside from the cursor). It's incredibly annoying, so I'd appreciate any help! Thanks in advance!

Update: Okay, kwacka's solution didn't work. When it freezes it goes up to 100% CPU usage and I think the process doing this is "xorg".

---

### Post by kwacka on 2008-05-04
Using top, I found that occasional freezes were due to trackerd

Going to System --> Prefernces --> Sessions --> Startup Programs & unselecting 'Tracker' cured it for me.

---

### Post by alexjohnc3 on 2008-05-07
> **kwacka said:**
> Using top, I found that occasional freezes were due to trackerd

Going to System --> Prefernces --> Sessions --> Startup Programs & unselecting 'Tracker' cured it for me.

Thanks for the suggestion! Should I also disable Tracker Applet?

---

### Post by Delever on 2008-05-07
Make sure to check for updates!

They should fix compiz-animations related problem and evolution related problem.

---

### Post by alexjohnc3 on 2008-05-24
Okay, kwacka's solution didn't work. When it freezes it goes up to 100% CPU usage and I think the process doing this is "xorg".

---

### Post by Hypo_Mix on 2008-05-25
you problem sounds identical to mine, from what i have found on the forums the problem seems to be due to what was mentioned above, its a "compiz-animations related problem" problem.

so its not your PC specifically.

so you can either try sutting that off for now (no idea how) or wait for a fix (no idea how long)

---

### Post by sam_delta on 2008-05-25
to shut compiz off g into system>prefference>appearence, and under effects tab, select none

tell us how it goes

sam

---

### Post by Inxsible on 2008-05-25
what are your system specs? Maybe Ubuntu is not geared for your system. You can try out a lighter DM like xfce which is the default DM in Xubuntu. Another is Fluxbox which is in Fluxbuntu. Other light WMs are IceWM, Blackbox, Openbox, PekWM and Enlightenment.

or you can also try out other distros like Puppy.

---

