---
title: "Can Ubuntu do this?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by AnonymousFan9 on 2008-10-14
Forgive me for mentioning such an evil program, but with Windows Media Player you could "minimize to taskbar" and there would be a little mini player on your taskbar. Can Rhythmbox do something like this? Or is there something I can do with gnome panel to at least display what's now playing and let me hit "next" or "back"?

Thanks!

---

### Post by Separ on 2008-10-14
I know Amarok can but that's for KDE, I think Banshee can, give that a go.

---

### Post by soxs on 2008-10-14
> **AnonymousFan9 said:**
> Forgive me for mentioning such an evil program, but with Windows Media Player you could "minimize to taskbar" and there would be a little mini player on your taskbar. Can Rhythmbox do something like this? Or is there something I can do with gnome panel to at least display what's now playing and let me hit "next" or "back"?

Thanks!

```
sudo apt-get install music-applet
```
This applet can be added to any of your panels and supports multiple media players.

If the repository version is too old to support your wanted media player, you may checkout [www.getdeb.net](www.getdeb.net) , there should be a quite up to date version

---

### Post by OutOfReach on 2008-10-14
As far as I know, Rhythmbox in Hardy has an icon in the system tray (task bar), but it doesn't allow minimizing to it. In Intrepid (an upcoming Ubuntu release, October 30), Rhythmbox does allow minimizing to the system tray.

---

### Post by Paul41 on 2008-10-14
Banshee does have something similar.

```
sudo apt-get install banshee
```

---

### Post by LowSky on 2008-10-14
just confirming that banshee  will work from tray, so will exhaile.

---

### Post by Kevbert on 2008-10-14
You can use Amarok in Ubuntu. Run up Amarok so you have the wolf icon in the top righthand corner of the desktop. If you right-click on the icon you get the menu.

---

### Post by hyper_ch on 2008-10-14
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

Or in short terms: Help others to help you ;)

---

### Post by ethoxyethaan on 2008-10-14
the program "alltray" can minimize anything you like.

---

### Post by Kellemora on 2008-10-14
Hi AF9

This may not apply at all, BUT, in Ubuntu you can have other windows open.
By default it only shows too down in the lower right hand side of your panel.

I have 4 windows on one machine and 6 on another and can have all of them doing something differently.

I actually LIKE the fact I don't have to minimize something and just move to another window to work on something else.

That feature is ONE of the reasons I made the switch to Ubuntu from DOZE in the first place!

TTUL
Gary

---

### Post by gjoellee on 2008-10-14
Amarok works just fine in GNOME but is ment for KDE

---

### Post by Sponzenbroekske on 2008-10-14
> **OutOfReach said:**
> As far as I know, Rhythmbox in Hardy has an icon in the system tray (task bar), but it doesn't allow minimizing to it. In Intrepid (an upcoming Ubuntu release, October 30), Rhythmbox does allow minimizing to the system tray.

You have a system tray icon of rhtyhmbox, right? right!
So if you want to minimize it to the taskbar press minimize (duh!)
If you want to minimize it to the SYSTEM TRAY press the system tray icon! :d

EDIT: @ all, I think it was solved in post 3 and minimizing to the taskbar like in vista/xp aint minimizing to the system tray, I don't want to be difficult but you gotta press the icon first and the press i.e. "next", with windows and the applet in the third post you can hit the button roght away :D

---

### Post by chrisod on 2008-10-14
If I click the task bar icon in Rhythmbox it minimizes to the task bar. If I hover over the icon it tells me the current song and artist, and if I right click on the icon I can fast forward, pause, etc. 

I know I did not install any other program to do this  - it may be enabled via one of the Rhythmbox plugins that ship with the application though.

---

### Post by porchrat on 2008-10-14
> **chrisod said:**
> If I click the task bar icon in Rhythmbox it minimizes to the task bar. If I hover over the icon it tells me the current song and artist, and if I right click on the icon I can fast forward, pause, etc. 

I know I did not install any other program to do this  - it may be enabled via one of the Rhythmbox plugins that ship with the application though.

Rhythmbox has an icon in the top right corner (just left of the clock) that looks like a little iPod when it is playing.  If you click that icon the window disappears and you merely need to click that icon again to bring up the window again.  Viola!

---

### Post by crjackson on 2008-10-14
> **OutOfReach said:**
> As far as I know, Rhythmbox in Hardy has an icon in the system tray (task bar), but it doesn't allow minimizing to it. In Intrepid (an upcoming Ubuntu release, October 30), Rhythmbox does allow minimizing to the system tray.

So does Hardy. Just click the icon and RBox with be minimized to the notification area (aka: system try). There won't be a mini-player but it will leave your window bar clear.

---

### Post by muadnu on 2008-10-14
Another music player that does it is Exaile...

```
sudo apt-get install exaile
```

---

### Post by ashmew2 on 2008-10-15
> **soxs said:**
> ```
sudo apt-get install music-applet
```
This applet can be added to any of your panels and supports multiple media players.

If the repository version is too old to support your wanted media player, you may checkout [www.getdeb.net](www.getdeb.net) , there should be a quite up to date version

Thanks for that... +1 !

---

### Post by Keen101 on 2008-10-15
[http://alltray.sourceforge.net/](http://alltray.sourceforge.net/)

all tray can minimize any program that doesn't do it nativly.

---

### Post by AnonymousFan9 on 2008-10-17
> **soxs said:**
> ```
sudo apt-get install music-applet
```
This applet can be added to any of your panels and supports multiple media players.

If the repository version is too old to support your wanted media player, you may checkout [www.getdeb.net](www.getdeb.net) , there should be a quite up to date version

Thanks, that's exactly what I was looking for!

I realize there is a Rhythmbox icon in the top right, but I like having the play/pause/next buttons and song title up there without having to right click first

---

### Post by soxs on 2008-10-17
> **AnonymousFan9 said:**
> Thanks, that's exactly what I was looking for!

I realize there is a Rhythmbox icon in the top right, but I like having the play/pause/next buttons and song title up there without having to right click first

There is a thanks button in the bottom right of my post, press it "thank" me ;-)

---

### Post by reg4c on 2008-10-18
Yaaay for Intrepid users

Minimize to tray for Rhythmbox is great
Ow, and if you are using AWN, the media control applet is really slick
On click, it will show you buttons for next, pause, and previous, as well as the
album artwork: I like it. When Rhythmbox is not started the applet will do it.

Cheerio

---

