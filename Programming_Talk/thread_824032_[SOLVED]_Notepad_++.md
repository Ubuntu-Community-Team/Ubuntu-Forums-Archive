---
title: "[SOLVED] Notepad ++"
date: 2008-06-09
forum: Programming Talk
---

### Post by yami280 on 2008-06-09
Hi, I just installed Ubuntu and I was wondering is there anyway to have Notepad ++ for Ubuntu.  If not are there any programs out there that are like Notepad ++?

---

### Post by mike_g on 2008-06-09
If you grab some plugins for gedit it can do pretty much all the stuff Notepad++ does (and more if you want).
[http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins)

---

### Post by KingTermite on 2008-06-09
[http://ubuntuprogramming.wikidot.com/Tools](http://ubuntuprogramming.wikidot.com/Tools)

I've only just started with Ubuntu, and I'm using Nedit (which I learned to use back in college 10 years ago). There's probably better out there now.

I've heard some good things about Jedit, but something about it annoyed me (forget what it was now).

---

### Post by inportb on 2008-06-09
Geany is an awesome text editor. So is Kate (but that's part of the KDE suite). In general Linux has very nice text editors.

---

### Post by jimv on 2008-06-09
I'd be willing to bet that Notepad++ works perfect in WINE.

---

### Post by Sinkingships7 on 2008-06-09
> **jimv said:**
> I'd be willing to bet that Notepad++ works perfect in WINE.

It does. Tested by me.

However, I do suggest Geany over Notepad++.

---

### Post by altonbr on 2008-06-09
> **jimv said:**
> I'd be willing to bet that Notepad++ works perfect in WINE.

It does, it works quite well, just no integration with GNOME/Nautilus like gEdit.

---

### Post by altonbr on 2008-06-09
> **mike_g said:**
> If you grab some plugins for gedit it can do pretty much all the stuff Notepad++ does (and more if you want).
[http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins)

Its funny that that page doesn't even explain how to install gEdit plugins. How lame.

---

### Post by Can+~ on 2008-06-09
sudo aptitude install gedit-plugins

Things I would recommend:
-gedit for quick things
-geany for medium things, usually suits everything.
-editra for big things, but still not "project big".
-Eclipse for large projects, with the plugin for the proper language.

I use this setting for both C/C++ and Python. Never acutally learnt Vim or emacs.

---

### Post by altonbr on 2008-06-09
> **Can+~ said:**
> sudo aptitude install gedit-plugins

That doesn't have the plugins I want, but thanks, that is definitely needed.

---

### Post by Joeb454 on 2008-06-09
Notepad++ *does* work with Wine, except that the menu's look horrible ;)

I've moved on to other text editors since I switched to Ubuntu (read: vim) :D

---

### Post by KingTermite on 2008-06-09
> **inportb said:**
> Geany is an awesome text editor. So is Kate (but that's part of the KDE suite). In general Linux has very nice text editors.

Awesomeness!! Still new and hadn't seen this app yet. Even if I don't use it as an IDE, it looks like a hell of a kick *** editor.

---

### Post by -grubby on 2008-06-09
I'd recommend Kate to replace it, even if you don't like KDE apps (I will not use any other editor unless it's Crimson - but that's a Windows app)

---

### Post by Barriehie on 2008-06-09
Geany seams really good, it just made it to my top panel.  I recall using Kate but it seemed to have to 'wait' to do things.  Better said it had some delays or something going on so I ditched it.

Barrie

---

### Post by inportb on 2008-06-10
I discovered Geany quite recently when I was looking for lightweight syntax-highlighting editors. gEdit was a bit too heavy, and Kate was obviously too heavy =p

Don't get me wrong, though. I use KDE and I think Kate is great. lol.

---

### Post by irrdev on 2008-06-10
If you are looking to replace Notepad++, then I would highly recommend [Bluefish Editor]("http://bluefish.openoffice.nl/"). It uses GTK+, and has built-in programming documentation, auto-completion, tabbed editing... you name it! It is more actively maintained than Nedit, and has a much nicer interface. It is definitely the closest native alternative to Notepad++ on Linux.

---

### Post by Sockerdrickan on 2008-06-10
Yeah I'd go with Geany for sure / Gedit sometimes

---

### Post by altonbr on 2008-06-10
geany would be great if I could just edit the syntax highlighting. I'm so used to gEdit's 'Oblivion' theme that I just can't switch. Plus gEdit has GREAT auto-completion tools that can be extended or modified.

If gedit seems simple. wait until you look through it's plugins.

For extra plugins, as mentioned above, try
```
sudo aptitude install gedit-plugins
```

---

### Post by Can+~ on 2008-06-10
Hmm.. interesting, there's a python autocompletion plugin:

[http://github.com/fenrrir/geditpycompletion/tree/master](http://github.com/fenrrir/geditpycompletion/tree/master)

It is nice, but it needs Ctrl+Alt+Space to make it work (instead of typing os.<popup>)... Worth hacking.

---

### Post by yami280 on 2008-06-10
Well, I tried the gedit plugins and i like them.. but i don't like gedit.  I like geany's interface.. but it doesn't have any python plugins... though i think i'll stay with geany

I hate setting up new OS's . gotta find all the apps for them and stuff.  took me a year to fully smooth out Vista.  then it went crap on me.

---

### Post by Can+~ on 2008-06-10
> **yami280 said:**
> Well, I tried the gedit plugins and i like them.. but i don't like gedit.  I like geany's interface.. but it doesn't have any python plugins... though i think i'll stay with geany

I hate setting up new OS's . gotta find all the apps for them and stuff.  took me a year to fully smooth out Vista.  then it went crap on me.

At least you got the repository (long live aptitude!).

Also, there are some threads on ubuntuforums about applications similar to the ones on windows.

---

### Post by altonbr on 2008-06-10
> **yami280 said:**
> Well, I tried the gedit plugins and i like them.. but i don't like gedit.  I like geany's interface.. but it doesn't have any python plugins... though i think i'll stay with geany

I hate setting up new OS's . gotta find all the apps for them and stuff.  took me a year to fully smooth out Vista.  then it went crap on me.

What's Vista? ;)

---

### Post by yami280 on 2008-06-10
> **altonbr said:**
> What's Vista? ;)

lol funny. its very similiar to hell.  except.. theres UAC control.

---

### Post by altonbr on 2008-06-10
> **yami280 said:**
> lol funny. its very similiar to hell.  except.. theres UAC control.

But does it work?

---

### Post by Twitch6000 on 2008-06-10
I think if you really liked using notepad++ in windows like I did just use it in wine.It works great and other then the look in wine no problems.Other then that I like gedit with the plugins.

---

