---
title: "Right click -&gt; Set as Background?"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by d4m1r on 2012-05-12
Does anyone know of such a script that works for 12.04? I had one working under 11.10 that I found online, but it doesn't work under 12.04 nor does a popular (older package) called **nautilus-wallpaper**. Basically, I'd like a right click option added when right clicking on an image file where I can set that particular image as the new desktop background.

Is this possible under 12.04? :confused:

---

### Post by ubuntu27 on 2012-05-12
You are right. I did not even notice that I didn't had the option to set a picture as wallpaper with right click. I have nautilus-wallpaper installed on Ubuntu 12.04, but it doesn't work.

I was going to suggest you using [Ubuntu-Tweak]("http://ubuntu-tweak.com/") to install the script, but upon testing it, I found out it doesn't work either.

It seems to be [this bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus-wallpaper/+bug/875845")

A commenter mentioned a work around.

[QUOTE=cometdog]workaround:
install nautilus actions, then add an action "Set as Wallpaper"

Path: gsettings
Parameters: set org.gnome.desktop.background picture-uri %u[/QUOTE]

---

### Post by d4m1r on 2012-05-12
Thanks for that workaround! It is far from ideal but it does work for me under 12.04 (after logging out and back in)....I can right click on an image file -> Nautilus-Actions -> Set as Wallpaper, and it does change the background.

---

### Post by mc4man on 2012-05-12
The other option is the nautilus actions extra ppa's, has a nautilus-wallpaper-changer extension (Set as Wallpaper in context menu) & many others. Uses nautilus python extensions & the ppa's are actively supported

release ppa
[https://launchpad.net/~nae-team/+archive/ppa](https://launchpad.net/~nae-team/+archive/ppa)

daily ppa
[https://launchpad.net/~nae-team/+archive/daily](https://launchpad.net/~nae-team/+archive/daily)

---

