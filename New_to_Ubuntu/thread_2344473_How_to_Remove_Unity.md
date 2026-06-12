---
title: "How to Remove Unity"
date: 2016-11-25
forum: New to Ubuntu
---

### Post by iamchuckles on 2016-11-25
How to Remove Unity

I have installed Unity, having read that this was a good idea. Unfortunately I subsequently read that installing Unity on a system with Lubuntu is a bad idea and unnecessary..

It does not seem to cause any problems. The only hint that it is even on the system is the presence of ‘Photo Lens for Unity’ in the apps list. Photo lens shows ERROR when clicked on. So the only real objection I can think of is that it is probably tying up some memory unnecessarily.

I am using Lubuntu 16.10 and am a recent Windows refugee.

So would someone please tell me how to get rid of Unity?

Thanks

P.S. - is there a way to tell just how much space Unity is taking up?

---

### Post by mikewhatever on 2016-11-25
It's really very simple. If you wanted to use Unity, or just try it out, then installing it was a good idea. It sounds silly when someone says it's unnecessary ...
Anyway, to remove it, run the following in a terminal window:
```

sudo apt-get remove nautilus gnome-power-manager gnome-screensaver gnome-termina* gnome-pane* gnome-applet* gnome-bluetooth gnome-desktop* gnome-sessio* gnome-user* gnome-shell-common compiz compiz* unity unity* hud zeitgeist zeitgeist* python-zeitgeist libzeitgeist* activity-log-manager-common gnome-control-center gnome-screenshot overlay-scrollba* && sudo apt-get install xubuntu-community-wallpapers && sudo apt-get autoremove
```

Info source: [https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative)

---

### Post by g33zr on 2016-11-25
@iamchuckles: Unity has received a bad rap, but play with it for a spell and you'll discover that it's a brilliant, well-designed DE. I didn't like it the first time I tried it either, but that was when it first came out. Returning to Ubuntu after a long hiatus, I find that it's an improvement over other DEs I've tried and it's a handy tool, too. Give it a chance before you remove it.

---

### Post by iamchuckles on 2016-11-26
Thanks to Mike and g33zr. Unity does not appear to be compatible with Lubuntu so I have removed it following Mike's advice. However, longer term I intend to move from Lubuntu to Ubuntu and will definitely try Unity at that time based on g33zr's recommendation.

Thanks again to you both.

---

