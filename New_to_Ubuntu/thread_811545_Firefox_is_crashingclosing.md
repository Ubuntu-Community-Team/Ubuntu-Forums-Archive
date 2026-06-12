---
title: "Firefox is crashing/closing"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by discmaster on 2008-05-29
I noticed this happening this morning. I am using ff 2.0 and at random times, if I click on a link ff will close completely. When I try to relaunch the browser, I get the "circle" (hourglass on windows) for a few seconds & then that goes away & the browser never opens.

I have to reboot to get it to work again. I decided to install ff 3.0, thinking that may solve it, but it did the same thing almost right away. I have now uninstalled 3.0, & am typing this using the original 2.0 install.

Anyone have any ideas on this, what may be causing the browser to close like that? 

Thanks in advance! :)

---

### Post by billgoldberg on 2008-05-29
I had the same problem in gutsy gibbon with ff2 and ff3 beta.

In hardy heron it doesn't seem to happen anymore, there is  aspecial ubuntu add-on installed by default in hardy heron, so that could be why (not sure).

See if you can find that add-on and install it, or use another browser like epiphany, opera, ...

---

### Post by discmaster on 2008-05-29
> I had the same problem in gutsy gibbon with ff2 and ff3 beta.

In hardy heron it doesn't seem to happen anymore, there is aspecial ubuntu add-on installed by default in hardy heron, so that could be why (not sure).

See if you can find that add-on and install it, or use another browser like epiphany, opera, ... Can't say I've had this issue before. What is the add-on you are referring to ? I am using Opera now, seems okay, but of course, that isn't solving my real problem with firefox. :(

---

### Post by discmaster on 2008-05-29
I see an issue with opera here - can y'all hep me with it? When I move the mouse over to the vertical scroll bar on the right side, it slides off of the bar. I have to manually place it on the bar. How can I fix this?

I want to be able to "throw" the mouse onto the side of the screen, just like with ff & have it automatically land on the scroll bar.

---

### Post by discmaster on 2008-05-30
Anyone with any ideas on the firefox crashing/closing problem? This is unbearable. I am having to continually reboot in order to restart ff after it crashes. IS there any way to fix this? A log file to show what is going on?

Any ideas at all? :confused:  :confused:  :confused:

---

### Post by Cato2 on 2008-05-30
Try doing ```
firefox -safe-mode
``` from a terminal.  Also, firefox -ProfileManager is worth trying - creating a new profile will help establish whether it's your existing profile (extensions or plugins etc) or Firefox proper that's causing the problem.

The error on restart may be due to an existing page in your Firefox session (stored tabs) - you can also backup the session* files in your profile, then delete them, to see if that helps.

---

### Post by james_vanb on 2008-06-04
I believe the add-on is called Noscript and is referenced in the following Mozilla Bug Report:

[http://forums.mozillazine.org/viewtopic.php?t=662388&sid=b35dd7f53b012079d9822cba2d55584b](http://forums.mozillazine.org/viewtopic.php?t=662388&sid=b35dd7f53b012079d9822cba2d55584b)

There is also another post echoing this problem, see:

[http://ubuntuforums.org/showthread.php?t=811889&highlight=firefox+crashes](http://ubuntuforums.org/showthread.php?t=811889&highlight=firefox+crashes)

See also:

[http://ubuntuforums.org/showthread.php?t=805314&highlight=firefox+crashes](http://ubuntuforums.org/showthread.php?t=805314&highlight=firefox+crashes)

By the way, I'm also getting abrupt crashes in Firefox 3b5 when I try to stream video, although a reboot is not necessary.

---

