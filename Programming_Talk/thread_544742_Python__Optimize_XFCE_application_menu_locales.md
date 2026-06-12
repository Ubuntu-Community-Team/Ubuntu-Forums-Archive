---
title: "Python / Optimize XFCE application menu locales"
date: 2007-09-06
forum: Programming Talk
---

### Post by kahrn on 2007-09-06
**This topic is now obselete and may not be updated. A new thread can be found at [http://ubuntuforums.org/showthread.php?t=542987]("http://ubuntuforums.org/showthread.php?t=542987")**

**Introduction**
Xfce, just like kde/gnome can use an application menu which can have shortcuts. Each one of those shortcuts is actually a file, and all of those files are located in &#8220;/usr/share/applications/&#8221; on most systems running xfce4 and gnome.

**How it works**
If you trawl around &#8220;/usr/share/applications/&#8221; and take a look at some of those files, you will notice that some of them have a lot of locale data which you probably do not need. It is possible to remove that locale data, and thus save a very small amount of hard disk space. I decided to write a script which can open each shortcut in a directory, and then remove all the locale data from each file in that directory. The end result is, on a standard Xubuntu system I can save almost 200kb of filespace just from removing the locale data from those shortcuts. It is also possible that the shortcuts will load faster on old machines as they don&#8217;t have to load as much data.. although that would be almost unnoticeable at best.

**How to remove**
If you want to remove all your locale data, I created a script using python to automate the process and remove it from all files in &#8220;/usr/share/applications/&#8221;. It can also create a backup automatically if you specify. This script should work with any system running Xfce4 or gnome, but has only been tested in [COLOR="RoyalBlue"]Xubuntu 7.04[/COLOR], [COLOR="RoyalBlue"]Xubuntu 7.10 tribe 5[/COLOR] and [COLOR="DarkOrange"]Ubuntu 7.04[/COLOR].

**Download**
You can find it at [http://kahrn.wordpress.com/scripts/]("http://kahrn.wordpress.com/scripts/"), and 0.2.2 at [http://kahrn.pastebin.com/f1bf15aba]("http://kahrn.pastebin.com/f1bf15aba")

The script is licensed under the GNU GPL so you can adapt it and change it however you wish (based upon the GNU GPL..). If you have any feedback on how I can improve it I would be pleased. I would also be pleased if anyone had any information about optimizing the shortcuts further, as well as people posting results from their optimizations.

---

