---
title: "3D games not running, or extremly low fps"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by boho103 on 2008-05-31
I have installed my ati drivers through a tutorial and I'm on hardy 8.04, and I have an ATI radeon x1400 installed, and I have 2 gigs of ram. Yet I cannot run 3d games, or they do run but at extremely low framerate. I tried re-installing the drivers through envyNG but I am getting this error. 
Exception: ('\nEnvyNG ERROR: The following packages cannot be installed:',)
That is the last line of the error, anybody know of a fix?
Please help, and if you could direct me through it Via AIM, that would be extremely helpful.

---

### Post by Ripfox on 2008-05-31
One thing I think is that all previous attempts to install drivers must be completely removed before using Envy. I think it says that on the website.

---

### Post by SunnyRabbiera on 2008-05-31
also please list the games you are having issues with.
Please keep in mind gaming and ATI support in Ubuntu is still not perfect, its not our fault but it can get annoying for sure.

---

### Post by Bataille23 on 2008-05-31
Also, are you talking about Windows games (running via Wine or Cedega) or native Linux games?  If you're running Windows games through Wine, I wouldn't expect much out of newer ('00+) games -- that's been MY experience, at least.  And I don't know about you're system architecture, but running on 64-bit Ubuntu doesn't help matters much either, as far as compatibility is concerned.  I would imagine the same goes for most all "third arch" OSes.

---

### Post by boho103 on 2008-05-31
Oh, well its native games to linux, like tremulous and open arena and such games. Oh and yes, originally I had removed the previous drivers to install the ATI drivers. But yes, even though I have the ATI drivers installed, I used the catalyist 8.5 method on this page
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
Its listed as method 2. I don't understand why my games wouldn't be working, I mean I have compiz working with the full 3d cube, shouldn't my computer be able to run ACTUAL 3d games?

---

### Post by Bataille23 on 2008-05-31
Ah.  Hmmmm...that IS strange.  I'll have to try those games out and see if I get the same problem.  I WILL say, however, that I switched to metacity after running native Linux games (Windows ports, to be accurate, like Postal 2 and Civilization 4: Call to Power) -- or, to be more accurate still, NOT running native Linux games, because they didn't work with Compiz.  Now that I'm bored with those games, I reinstalled Compiz, so I'll see if it's the same kind of problem.

---

### Post by Ripfox on 2008-05-31
This may be obvious, but did you try switching OFF compiz while playing these games? It sometimes creates a conflict.

---

### Post by Bataille23 on 2008-05-31
> **Ripfox said:**
> This may be obvious, but did you try switching OFF compiz while playing these games? It sometimes creates a conflict.
Ummm...yeah!  That's actually a really good idea...I didn't know you could even do that :X 

I downloaded tremulous and played it for a few seconds on my laptop (with compiz), and I would say it's compiz that's causing the problem.  If not, you might check your internet connection.  Oftentimes a bad internet connection will result in undesirable speeds, resultant graphical glitches, and eczema.  That has been my experience, at least.  Except the eczema.  But you can't be too careful, you know.

---

### Post by boho103 on 2008-06-01
disabling compiz actually almost worked
I used the
metacity --replace
and then
when I started tremulous
it opened
like it maximized with a black screen
but then it crashed : / soon after
no loading menu or such
just black screen and crash
open arena does the same thing
any other ideas?
should I post my xorg.conf?

---

### Post by boho103 on 2008-06-06
Anybody please? This is still a problem : /

---

