---
title: "[How To] &quot;real&quot; font shadow in Kubuntu (KDE) desktop"
date: 2007-02-11
forum: Outdated Tutorials &amp; Tips
---

### Post by Joao_a on 2007-02-11
I don't like the default font shadow of Kubuntu.
cf. [http://shots.osdir.com/slideshows/slideshow.php?release=752&slide=4]("http://shots.osdir.com/slideshows/slideshow.php?release=752&slide=4")

I remeber a day, when using another distro, having what i will call here "true" font shadow and not "outline" font shadow as it is in Kubuntu.
I accepted that because i didn't know how to change it.

Of course i tried the 'right click on desktop'->'desktop config'->'advanced options'->'enable shadow' but i just got the "outlined" text and not "real" shadowed text.

Well today i went further and found those:
[LIST]
[*][http://baghira.sourceforge.net/OS_Clone-french.php#step]("http://baghira.sourceforge.net/OS_Clone-french.php#step5")
[*] [http://www.kde.nl/doc/kdesktop/shadow.html]("http://www.kde.nl/doc/kdesktop/shadow.html")
[*] [http://www.linux-user.de/ausgabe/2004/09/014-ksplitter/index.html]("http://www.linux-user.de/ausgabe/2004/09/014-ksplitter/index.html") the "Ganz schön schattig" part
[/LIST]

Well i followed the instructions:

[LIST=1]
[*]<Alt>+<F2>
[*]kate ~/.kde/share/config/kdesktoprc
[*]find the "[FMSettings]" part
[*]make sure there's a "ShadowEnabled=true" entry (without the "")
[*]add a "ShadowParameters=" entry (without the "")
[*] and right after the "=" add "2,2,4.0,100.0,2,2,1" (kde style) **or** "0,1,16.0,192.0,2,4,0" (OSX style) **or** "1,1,32.0,139.0,2,4,0" (winxp style) - each time without the ""
[*] save it
[*]<Alt>+<F2>
[*]dcop kdesktop KDesktopIface configure
[*]and *voilà*
[/LIST]

I think **this is a must have** and should be enabled by default the correct way in Kubuntu (maybe in Feisty?) and in KDE in general!
*It's all in the details...* and if KDE (Kubuntu) can do it why not use/show it?

*In concreto* here is what i got (see attachements):
[LIST]
[*]kde-kde_32.png - ShadowParameters=2,2,4.0,100.0,2,2,1
[*]kde-osx.png - ShadowParameters=0,1,16.0,192.0,2,4,0
[*]kde-soft_outlined.png (default?) - ShadowParameters=0,0,4.0,170.0,1,4,0
[*]kde-winxp.png - ShadowParameters=1,1,32.0,139.0,2,4,0
[/LIST]

---

