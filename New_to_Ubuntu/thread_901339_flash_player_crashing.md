---
title: "flash player crashing"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by mpgarate on 2008-08-26
I've had this same problem for ages and tried all different fixes.. but is there anything that will really fix the flash crash?

---

### Post by alienexplorers on 2008-08-26
I am having the same problem.  Everytime I go to a flash page my firefox crashes (Just turns off).

---

### Post by Joeb454 on 2008-08-26
It's more adobe than anything else.

Are you running 32 bit or 64 bit?

---

### Post by mpgarate on 2008-08-26
32. I tried one 'fix' that just replaced flash with an ugly gray box instead of crashing. To get flash back I had to restart firefox every time

---

### Post by chrisod on 2008-08-26
Not to thread jack, but since I didn't get any answers in the multimedia forum last week. [This is the only site]("http://Effinfunny.com.com") I have found that will never work for me. (humor site, probably NSFW) The flash there takes down Firefox 3 every single time. I upgraded to the most recent Flash 10 release candidate and it made no difference. I also uninstalled pulseaudio since it frequently gets blamed. It's not a flash - pulseaudio conflict.

Can anybody here play one of the flash videos there? Maybe we can learn something if anybody has a system set up that can handle the flash on that site.

---

### Post by mpgarate on 2008-08-26
I must say I'm really surprised there wasnt some simple fix released ages go.. this is a MAJOR problem with hardy that seems undealt with

---

### Post by niccholaspage on 2008-08-26
Hm..My Desktop had the same problem.What I did was uninstall the flashplugin-nonfree And get the one from adobe.com.This didn't crash firefox.

---

### Post by chrisod on 2008-08-26
It's not an Ubuntu problem, it's an Adobe problem. This is the ultimate example of the dangers of proprietary formats. Flash doesn't work right, and the only options are to wait for the Flash developer to fix it, or try to reverse engineer something. Neither is really a good solution.

---

### Post by philinux on 2008-08-26
> **chrisod said:**
> Not to thread jack, but since I didn't get any answers in the multimedia forum last week. [This is the only site]("http://Effinfunny.com.com") I have found that will never work for me. (humor site, probably NSFW) The flash there takes down Firefox 3 every single time. I upgraded to the most recent Flash 10 release candidate and it made no difference. I also uninstalled pulseaudio since it frequently gets blamed. It's not a flash - pulseaudio conflict.

Can anybody here play one of the flash videos there? Maybe we can learn something if anybody has a system set up that can handle the flash on that site.

This site works ok for me. One flash vid gave a white screen but others were fine.

---

### Post by chrisod on 2008-08-26
@Phil: So what is your browser / flash set up look like?

---

### Post by Crafty Kisses on 2008-08-26
You could try Gnash.

---

### Post by mpgarate on 2008-08-30
I tried this method from launchpad. so far so good

> 1. Upgrade to Flash 10 (at release candidate status as of 13/8)
2. Drop libflashsupport completely (it causes instability in Flash 9 and 10)
3. Fix bug [#198453]("https://bugs.launchpad.net/bugs/198453")

---

### Post by vishzilla on 2008-08-30
Or better try out Adobe Flash 10 rc1. Its supposed to iron out all the bugs of 9.

---

### Post by mpgarate on 2008-08-30
yea thats a big part of the fix. essentially I upgradedto 10, removed libflashsupport, installed some packages and edited some files as instructed [here]("https://bugs.launchpad.net/bugs/198453")

I posted detailed instructions of exactly what I did [over at my blog]("http://mikesubuntu.blogspot.com/2008/08/how-to-fix-flash-crash-in-hardy.html")

---

