---
title: "Dock on Gnome 3"
date: 2011-06-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xxhopingtearsxx on 2011-06-02
How do I get a dock on Gnome 3? I hear I need to install extensions, but I've seen some websites and they don't seem to provide easy instructions.

I know how to use Terminal, I've been using Ubuntu for years, but I still need help for certain things..

---

### Post by garvinrick4 on 2011-06-02
```
sudo apt-get install docky
```Add icons in docky settings and then anything you open can right click on in docky and
have it pin to dock.
(Also go to Keyboard shortcuts and make the ones you want.
And you can hit windows key and just type in like firefox and hit enter. Never have to touch mouse or pad this way.) Any app. even type in home f hit enter for home folder.
Windows key and d
Lots of ways to reduce mouse use in gnome 3
Set some key commands same as you use in Unity interface so as 
to not have to think of which ones to use all the time while in a session.

---

### Post by xxhopingtearsxx on 2011-06-02
> **garvinrick4 said:**
> ```
sudo apt-get install docky
```Add icons in docky settings and then anything you open can right click on in docky and
have it pin to dock.

I've used Gnome Do Docky before but the one I was looking for was the one in here [http://www.webupd8.org/2011/04/gnome-shell-extensions-additional.html](http://www.webupd8.org/2011/04/gnome-shell-extensions-additional.html) that I've been referred to several times in a chat room.. but I don't see much answers. :(

---

### Post by garvinrick4 on 2011-06-02
> I've used Gnome Do Docky before but the one I was looking for was the one in here [http://www.webupd8.org/2011/04/gnome...dditional.html]("http://www.webupd8.org/2011/04/gnome-shell-extensions-additional.html") that I've been referred to several times in a chat room.. but I don't see much answers
I have not seen anything on this at all. Good luck to you xxhopingtearsxx

---

### Post by 23dornot23d on 2011-06-02
cairo-dock works


[B]sudo apt-get update

sudo apt-get install cairo-dock[/B]


when you run cairo-dock for the first time right click on it go upto cairo-dock - to the right
brings up a sub menu .....
...... it allows you to set it to start automatically the next time you log-in ......

hope this helps ......

---

### Post by mc4man on 2011-06-02
I guess you could get it from this ppa (one of the gnome-shell-extensions packages
[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)
(if you didn't wish to add the ppa then you could probably just dl the .deb, extract it, browse to usr/share/gnome-shell/extensions and move the 'dock@gnome-shell-extensions.gnome.org' folder to ~/.local/share/gnome-shell/extensions and then Alt+F2 r 
like in screen

(I'm trying 3 ext.'s right now, the most useful is the places-menu one from [http://git.gnome.org/browse/gnome-shell-extensions/](http://git.gnome.org/browse/gnome-shell-extensions/)

---

### Post by xxhopingtearsxx on 2011-06-03
I got it from gnome-shell-extensions hours ago. My inernet was down so I couldn't post it.

But now I find it a little annoying, but I can't for the life of me seem to get rid of it.. or these annoying buttons on the menubar that shows my favorite icons. I don't know how I got that, but I know it was from an extension. I deleted the extensions folder, too. I'm just dumfounded.

---

