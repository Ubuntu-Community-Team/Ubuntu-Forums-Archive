---
title: "[SOLVED] Blackbox recommended?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by koji042 on 2008-07-17
Hi, I recently became interested in a window manager called Blackbox. But I have a few concerns/questions:

1. Would Blackbox be recommended for a Linux newbie? From what I've read, the whole window manager seems to be based around scripts...

2. I've heard that Blackbox has two related projects, Openbox and Fluxbox; how are they different from each other?

3. Would I be able to run GNOME applications if I were to use Blackbox?

Any help is appreciated. Thanks much. :)

---

### Post by Hooya on 2008-07-17
I run Fluxbox so I can answer your questions a little bit anyway.

I'm pretty much still a Linux Noob, although I've always been pretty fearless when it comes to computer stuff.  The thing about Fluxbox (and likely Blackbox) is that you have a very high level of control over the way your window manager works.  Keyboard shortcuts and menus are COMPLETELY customizable in a pretty easy to deal with way - human readable text files.  The downside is that you really HAVE to customize everything, because so little of it is done automatically like Gnome or KDE.  If you really understand your system and aren't afraid to try things Fluxbox can work really well.  It just takes a while to figure out how you want things and then to get them to work right.

You'll get really good at custom commands that look a lot like command line things, but they'll be in a menu or whatever.  Once you get the hang of it it's really fast and efficient, but it takes a while to get there.

Of course, once you have it the way you like it you can just backup your config files and when you have to do a new install or migrate to a new computer it'll be exactly like how you left it once you get the programs installed.

Gnome applications run just fine, although you'll find many of them unnecessary to run all the time.  I use the Gnome wireless manager for my laptop, but that's it.  Obviously GTK programs will work just fine if you have the right dependencies installed.

I can't really tell you how the three variants you mention are different since I've only used Fluxbox, although there's a little information on that on the Fluxbox webpage.

Feel free to PM me with questions you might have if you start trying Fluxbox out, since I'm also coming from a newbie perspective I might have a different insight on problems you might have than some more experienced people on the board.

---

### Post by markjensen on 2008-07-17
In addition, all of the *boxes have **no** desktop icons by default.  Nor do they use a "Start" button.    You can add in desktop icons (yuck!) if you like with a number of add-ons, but I have grown rather fond of a clean desktop (desktops tend to gather unorganized clutter, if you haven't noticed).

Menu operations are accessed by a right-click on the desktop, anywhere your mouse happens to be.  This is a lot more efficient than having to run over to a corner any time you want to access your menus.

Openbox starts at a more basic start than Fluxbox.  Openbox does not include a panel (task bar) by default, but one can be added.   Flux also includes such built-in "eye candy" (if you can call it that) of menu icons.  Last I looked at Openbox, it didn't...  At least not by itself.

I use Fluxbox because I had an older system that I wanted the extra lightness to avoid consuming a lot of resources just for showing a desktop.    I have only played with Openbox once, and they are pretty much on equal footing for resource usage and performance.

If you are new-ish, maybe Fluxbox would be a bit more comfortable with its default panel and icons in the menus.   But feel free to explore any or all of them.  I do recommend trying it for a week, if you can.  I promise it will grow on you (or at least not feel as awkward as it might during the first day).

---

### Post by Inxsible on 2008-07-17
I would second that you go ahead and use it.

Blackbox doesn't have as much support or popularity as Openbox does, IMO.

I use Fluxbox and Openbox on my Debian and Arch respectively. The machine that I installed these on, would never be able to run Ubuntu and Xubuntu was also very troubled in that environment.

Since I started fluxbox and Openbox, they have kinda become my primary WMs when I want to get some work done.

I even plan to use them on my brand new computer as well. True - that you can't get fancy effects of Compiz...but then you can also run openbox on Gnome - so when you wanna show off your Linux box to people..just log into gnome or when you wanna get some work done without the fancy stuff...log into openbox :)

---

### Post by urukrama on 2008-07-17
I'd recommend you start with Openbox. It is easier to configure than Fluxbox through Obconf (to change Openbox' preferences) and Obmenu (to edit the menu). (I know Fluxbox has some configuration apps too, but I've never found them to be as stable or user-friendly as Openbox').

You can make Openbox look like anything you want, but if you'd like some ideas, check out the monthly desktop thread in the Community Café. If you want to give Openbox a try, have a look at the link in my signature. I'm sure you'll find it useful.

---

### Post by koji042 on 2008-07-17
Thanks for all your input. :)
I think I'll try using Fluxbox first and then Openbox at some later point in time.

Again thank you.

---

### Post by Hooya on 2008-07-17
> **urukrama said:**
> I'd recommend you start with Openbox. It is easier to configure than Fluxbox through Obconf (to change Openbox' preferences) and Obmenu (to edit the menu). (I know Fluxbox has some configuration apps too, but I've never found them to be as stable or user-friendly as Openbox').

You can make Openbox look like anything you want, but if you'd like some ideas, check out the monthly desktop thread in the Community Café. If you want to give Openbox a try, have a look at the link in my signature. I'm sure you'll find it useful.

The analog in Fluxbox is called "fluxconf".  "$ sudo apt-get install fluxconf" will get it for you.  It has three components to run: fluxconf, fluxmenu and fluxkeys.  It's not a maintained package anymore so parts of it are pretty useless.  Do NOT use fluxkeys, as it breaks your mouse buttons (not permanently).  The keys file is easy enough to edit on your own.  fluxconf is pretty worthless really, so forget about it.  fluxmenu, however, is a much simpler way to edit the right click menu than editing the text file by hand since it handles the syntax for you, has drag and drop, and as of now it doesn't break anything.

First thing you'll want to do is copy the default menu file to your home configuration to make it easier to edit.  ```
sudo cp /etc/X11/fluxbox/fluxbox-menu ~/.fluxbox/menu
```  You'll see in that file it says to do this: > # to use your own menu, copy this to ~/.fluxbox/menu, then edit
# ~/.fluxbox/init and change the session.menuFile path to ~/.fluxbox/menu
After that it's just a matter of setting it how you want.

To customize your look you can download most of the fluxbox themes out there from here: [http://themes.freshmeat.net/browse/962/](http://themes.freshmeat.net/browse/962/)
Extract the .tar.gz files to ~/.fluxbox/styles and they'll show up in your right click menu.

You'll also probably find the program "fbrun" to be pretty handy as well, so you might want to make a shortcut key for that right away (I use Super+R).  It's a super simple run dialog.

Have fun with it.  I've switched both my laptop and my desktop to Fluxbox (the laptop was running Xfce and the desktop running Gnome).

---

