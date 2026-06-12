---
title: "installing themes in 12.04?"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by cabz on 2012-09-09
I am trying to install some new themes in xubuntu 12.04 and I cannot seem to make them work.
I went into my home/username folder and created a .themes folder and extracted them all there . but they do not show up in the appearance tab in the settings manager.
so after some digging i found the standard themes in usr/share/themes.
But I cannot move my themes folders into the usr/share/thems folder. is there a way to get root access to move them? do i have to do this in a terminal window? and if so how?.
thanks

---

### Post by Bigtime_Scrub on 2012-09-09
Where did you get your themes and what themes are you trying to install? 

Extracting your themes into .themes in your home folder should work for your user. Putting them into /usr/share/themes just enables theme system wide for all users. Essentially for your purposes they are the same thing.

---

### Post by cabz on 2012-09-09
> **Bigtime_Scrub said:**
> Where did you get your themes and what themes are you trying to install? 

Extracting your themes into .themes in your home folder should work for your user. Putting them into /usr/share/themes just enables theme system wide for all users. Essentially for your purposes they are the same thing.

I downloaded them from xfcelook.org
I got two that had 3 options in each
151465plasmabugfix.tar.gz and xaphire.xfwm4.pack.tar.gz
these are the ones I downloaded so if i dont have to put them into the usr/share/themes folder how do i get them to work?

---

### Post by cabz on 2012-09-09
well heres a small update, I rebooted the pc and one of my new themes now shows up in the main "appearance" list. the plasma one works fine . I have also noticed that the plasma theme has gtk-2 gtk-3 and xfwn4 files in there folders and the theme with only xfwm4 in its folder wont show up. does this mean that the xfwm4 just wont work? and I just need to use gtk2/3 themes?

---

### Post by Toz on 2012-09-09
If the theme has gtk-2.0 and gtk-3.0 folders, then it is an appearance theme and you can set in "Settings Manager -> Appearance". If it has an xfwm4 folder, then it is a window manager theme and can be set in the "Settings Manager -> Window Manager".

More detailed explanation here: [http://ubuntuforums.org/showpost.php?p=12038130&postcount=4]("http://ubuntuforums.org/showpost.php?p=12038130&postcount=4")

---

### Post by cabz on 2012-09-10
> **Toz said:**
> If the theme has gtk-2.0 and gtk-3.0 folders, then it is an appearance theme and you can set in "Settings Manager -> Appearance". If it has an xfwm4 folder, then it is a window manager theme and can be set in the "Settings Manager -> Window Manager".
 
More detailed explanation here: [http://ubuntuforums.org/showpost.php?p=12038130&postcount=4](http://ubuntuforums.org/showpost.php?p=12038130&postcount=4)
cool Thanks for the help.

---

