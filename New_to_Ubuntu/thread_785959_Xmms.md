---
title: "Xmms?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by chadwit on 2008-05-07
ok - I just installed XMMS with all the options. The synaptic icons are green. But I'll be damned if I can figure out how to start the thing. I file search on XMMS turns up an icon .png file and a little file called xmms2tray.desktop file in usr/share/app-install/icons & desktop (respectively). That's it. I have no XMMS listed in apps->sound/video (which is where I would think it would be) or in any of the other menus. Did I do something wrong? Can this only be started from the CLI or something?

thanks.....

---

### Post by Delever on 2008-05-07
What happens if you type in terminal xmms?

---

### Post by chadwit on 2008-05-07
bash: xmms: command not found

---

### Post by Delever on 2008-05-07
Hm, probably it is xmms2 then? Try xmms2

---

### Post by Delever on 2008-05-07
Ok, some research showed, that xmms2 is not graphical, you need to install graphical frontends to use xmms2. You can find them by doing search for xmms in Programs->Add/Remove. That should add appropriate shortcuts.

If you want old xmms, try this link:
[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)

---

### Post by jbonll05 on 2008-05-07
The xmms2tray icon gives you a popup with, among other choices, "play, stop, next, previous" choices. It also has several more, including "quit". I am using Ubuntu 8.04 and only play remote lists(radio) and use the "movie player". Some use the "Real Player.

---

### Post by chadwit on 2008-05-07
xmms2 in terminal brings up a laundry list of commands. I don't see anything in add/remove other than an option to download an icon. So in order for me to use the slick GUI stuff as seen on their web page I need to install xmms sans the 2?

My ultimate goal here is to just be able to stream radio from the internets. In researching, XMMS was recommended. If you or anyone else has a better suggestion, please hit me with it.

---

### Post by Delever on 2008-05-07
> **chadwit said:**
> xmms2 in terminal brings up a laundry list of commands. I don't see anything in add/remove other than an option to download an icon. So in order for me to use the slick GUI stuff as seen on their web page I need to install xmms sans the 2?

My ultimate goal here is to just be able to stream radio from the internets. In researching, XMMS was recommended. If you or anyone else has a better suggestion, please hit me with it.

Searching xmms in add/remove brings up not only icon, but also several graphical front-ends for xmms2. You can read descriptions and try them to decide what you need (I never tried, I live ok with amarok).

---

### Post by aktiwers on 2008-05-07
I could not install or find it in the repos either. I installed Audacious instead!

```
sudo apt-get install audacious
```

It's very almost the same - a fork..  a good fork ;)

---

### Post by rustutzman on 2008-05-07
bmpx just abut does it all! It's in the repositories.

Russ

---

### Post by chadwit on 2008-05-07
I don't see any other XMMS options in my add/remove other than the icon. Maybe I have the wrong/different Software Sources. In add/remove, it says Amarok is for KDE. Will that work in GNOME? 
Does Audacious play the streaming radio? I don't see that listed in the description. I'm kinda looking for something with EQ capability, recording streams, stuff like that.....I guess at this point I'd settle for anything that'll work since I dusted my XP partition and committed to the U.....

---

### Post by Delever on 2008-05-07
Amarok works beatifully for me in GNOME. It can play streams, too, but can't record them. It has lots of features, and many plugins. Hmmm, maybe some of them can record streams too.

---

### Post by divali on 2008-05-10
[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)
This fix worked for me in Hardy. I wouldn't be without Xmms.
Thanks Sartek.

---

