---
title: "Installed themes does not appear in Appearance Preferences"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by telekarlsen on 2008-09-26
When I'm trying to install Mac4Lin Metacity theme I get this feedback :"GNOME Theme Mac4Lin_GTK_v0.4 correctly installed"

However, it doesn't show up among the other preinstalled themes.
It does exist in .themes folder.

Where am I doing the wrong thing?
.themes is 755

---

### Post by PierreDeKat on 2008-09-26
Some theme packages may not be entire themes, but instead partial themes, like a different window border, for instance. So if Metacity considers the theme "installed", it probably is.

The way to access it would be to open your theme dialog, select one of the themes as a starting point, then click "Customize" down at the bottom. This will pull up a whole new dialog with preferences for "Controls", "Colors", "Window Border", "Icons", and "Pointer".

My guess is, you will find what you installed as a "Window Border" option and perhaps an "Icon" option.

---

### Post by DJ_Peng on 2008-09-26
This is actually a known issue (and has been discussed in the Mac4Lin support threads, but I don't have links handy). When you add the Mac4Lin themes you will see a theme labeled *Custom...*, which you can save with whatever name you desire. You can confirm that the Mac4Lin components are selected by using the Customize button.

Mac4Lin 1.0 resolves that issue, from what I'm seeing in the RC. Not sure when it's due out though.

---

### Post by telekarlsen on 2008-09-26
Thank you for your replies.

You are both correct about the Customize option.

I was trying to follow this guide:[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac]("http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac"), but couldn't make it through due to certain "mis-matches"
Maybe 8.10 with Gnome 2.24 and an updated Mac4Lin will make my day.. :-|

Thanks

---

### Post by DJ_Peng on 2008-09-27
There is a release client for Mac4Lin 1.0, with links and info in the [support thread]("http://ubuntuforums.org/showthread.php?p=5767692"). You may want to post the problem you're having there. infra_red_dude and some of the other users there are really helpful for resolving issues. (Not that some of the users aren't helpful, but some are really good at finding solutions.)

---

