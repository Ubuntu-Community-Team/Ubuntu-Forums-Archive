---
title: "[SOLVED] Change panel text"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by dinostabOMG on 2008-09-07
I found tons of advice on how to change the COLOR of panel text, but I can't change the text itself. I right click on my upper panel (in Hardy), and go to edit - I want to change the text of the menu items, but this option isn't offered. How can this be done?

---

### Post by m_duck on 2008-09-07
Hi, I think if you goto System -> Preferences -> Appearance and then goto the 'Font' tab, there are about 5 options to change different sets of fonts. I think if you have a play around with it, one of them will change the font on the panels.

---

### Post by dinostabOMG on 2008-09-08
Ah, no I actually want to change the WORDS.

Specifically, I am sick of seeing "Advanced Desktop Effects Settings." I want to change it to "Compiz Config Settings Manager" which is what the thing is actually called, because I always forget the abbreviation when I need it.

---

### Post by m_duck on 2008-09-08
Ah, sorry, misinterpreted it. I'm just reinstalling Ubuntu at the moment but from [http://ubuntuforums.org/showthread.php?t=803897](http://ubuntuforums.org/showthread.php?t=803897) if you goto System -> Preferences -> Main Menu, it allows you to modify various aspects of your menus, including renaming the entries.

---

### Post by LowSky on 2008-09-08
right clcik on applications, edit menus, go to preferences, then to Advanced Desktop Effects Settings, right click on it and change the name.

---

### Post by dinostabOMG on 2008-09-12
Hi guys,

Neither of these things worked, I'm sorry to say. 

LowSky: If you use the Edit Menus dialogue, right clicking on any particular item has no effect, so I can't change the name this way.

m_duck: I actually don't have a Main Menu entry under my preferences. What is this panel's name, so I can run it with Alt+F2?

Thanks for looking into this nonetheless.

---

### Post by dinostabOMG on 2008-09-15
No ideas? I think the right-click, Edit Menus solution used to work, is this a new "feature" in Hardy?

---

### Post by TheUbGuy on 2008-09-15
> **dinostabOMG said:**
> No ideas? I think the right-click, Edit Menus solution used to work, is this a new "feature" in Hardy?

I have it  in my Preferences - called Main Menu ..... in a terminal type alacarte

---

### Post by cariboo on 2008-09-15
Hit Alt-F2 and type:

```
alacarte
```

This will bring up the menu editor. You might want to reinstall ubuntu-desktop to fix the missing menus

Jim

---

### Post by Offramp on 2008-09-15
I am new to this but just tried this to change a menu entry.

To rename a menu entry, bring up the menu editor as previously discussed. Right click over the menu entry you want to change and select Properties.  In here you can change the menu entry to whatever name you wish.

I am tyring to find where the "Places" menu is organised so that I can make some changes to that.

---

### Post by dinostabOMG on 2008-09-16
I don't know why it is, but this simple thing that seems to be working for everyone else doesn't work for me. When I right-click I get nothing.

However, I did find a solution:

```
sudo apt-get install alacarte
alacarte
```

Then you can enable the menu editor on the "Other" menu in applications.  This one has a properties button that worked just fine for me.

---

### Post by dinostabOMG on 2008-09-16
> **cariboo907 said:**
> Hit Alt-F2 and type:

```
alacarte
```

This will bring up the menu editor. You might want to reinstall ubuntu-desktop to fix the missing menus

Jim

I notice you were getting at that now. I don't know why, but a lot of programs seem to be get spontaneously uninstalled from my installation. I've also found it to be much less stable and reliable than Gutsy; I might downgrade.

---

