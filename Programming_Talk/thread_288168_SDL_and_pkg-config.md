---
title: "SDL and pkg-config?"
date: 2006-10-29
forum: Programming Talk
---

### Post by poly-poly man on 2006-10-29
I am old to linux but new to Ubuntu. I am in the final leg of developing Timidgtk 0.03 (it took so long because of this one bug), and needed a new gtk (because I believe the old has a large memory leak, or something like that).

Anyway, for development, I need GTK ( I apt-got gtk-dev) and sdl (and all sub-packages, including devs). Unfortunately, I never got the sdl.pc file for pkg-config. Is this because it has been put in a different spot, or do I need to do something else?

tia,

poly-p man 

I wanted to at least try out Ubuntu. It's amazing how easy it is to do updates, grab extra packes, etc., but it truly isn't a built-for-development OS.

---

### Post by hod139 on 2006-11-27
Installing libsdl1.2-dev should set up pkg-config for you.  You should be able to type
```

sdl-config --cflags --libs

```

Also check out this [howto]("http://ubuntuforums.org/showthread.php?t=304650") for SDL related advice.

---

### Post by Mickeysofine1972 on 2006-11-27
Firstly, I'd like to welcome you to Ubuntu!

you will find that Ubuntu is great for development, you just need to know how to set it up ;-)

Good call hod139 btw! also check out the ubuntu game developers wiki here [http://ubunut-gamedev.pbwiki.com](http://ubunut-gamedev.pbwiki.com) its a growing resource for SDL anf general game development.

Mike

BTW: if anyone has feedback about the SDL setup guide please letus know if your having problems.

---

