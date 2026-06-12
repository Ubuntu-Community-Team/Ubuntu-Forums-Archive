---
title: "Two Weird Problems VLC &amp; FireFox"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by mrdosa on 2008-06-03
I have installed the latest Ubuntu 8.04
Lately, I am unable to fast forward any video on VLC using the ctrl+right arrow or shift+right arrow from the key board. When I do that, only the time stamp changes and video gets all fuzzy but nothing happens. It keeps playing. Strangely I can properly fast forward movies on Totem.

The other problem I am facing is with firefox.
I am unable to save any book marks. Every page i book mark mysteriously disappears the next time I open firefox. Once I visited some site, dont know which, but after that my firefox opened up to my home page [i had put show blank page as start up option] and later some windows opened up saying i installed some option on firefox. I have no idea what I did. But I cant find that now. I am able to browse and all, but the book marks are not getting saved.


Please help me out guys!!

---

### Post by xfceuser on 2008-06-03
vlc problem maybe a bug. a quick solution to the firefox is to unistal then install again. make sure you have no important settings in firefox remained (then you can back them up). 
if this did not solve the problem, a bit stronger action is to
also before installing again, empty the folder at ~/.mozilla/firefox (which includes settings and plugins for firefox)
but this way you may need to install also any plugins for firefox if any was being used.

*** another method that might solve the problem without any uninstallation, is to type in terminal,
firefox -profilemanager

then make a new profile, and use it instead of default. now on.

---

### Post by mrdosa on 2008-06-03
Hi. Is there nothing I can do about VLC problem? I will try out firefox thing. And if I reinstall firefox, will I lose all the present bookmarks, and settings?

---

### Post by xfceuser on 2008-06-05
> **mahender.mandala said:**
> Hi. Is there nothing I can do about VLC problem? I will try out firefox thing. And if I reinstall firefox, will I lose all the present bookmarks, and settings?

not necessarily, but it is possible. if you delete the folder i said, all firefox settings will be reseted, but unless you have some settings that you dont remember, it is not a problem.
also you can back up your bookmarks.

---

