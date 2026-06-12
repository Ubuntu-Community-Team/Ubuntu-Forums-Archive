---
title: "gstreamer programming or other media programming?"
date: 2008-06-17
forum: Programming Talk
---

### Post by keeler1 on 2008-06-17
I am trying as somewhat of a summer project to write myself a media player.  I have chosen QT as the graphical frontend because it is cross-platform and fairly easy to understand.  I have been looking into a gstreamer backend because it will work on windows as well ( I hope to use my media player on windows and linux)  

On the gstreamer page it says the c++ language bindings are not complete.  Can I download the partially complete version somewhere?  Has anyone every used them or are they so incomplete that they can not be used.

I was going to just use the regular c bindings but the gObject model is pretty convoluted and was hoping it would be better in c++ with c++'s classes, inheritance and polymorphism. 

Are there any other good media backends that are cross-platform?

---

### Post by pmasiar on 2008-06-17
There are zillions media players. You will learn more, and your code will be more useful for community, if instead creating yet another half-working clone you joined existing project, and helped to fix couple of bugs instead.

---

### Post by keeler1 on 2008-06-19
I wanted to write my own because I dont like any of the rest.  The interfaces are pretty poor on most of the ones I have tried out.  Also I want to put in a lot of functionality that is not in most media players.  I also want to leave out some because I find it useless.

---

### Post by SledgeHammer_999 on 2008-06-19
I was thinking to write a GTK media player using gstreamer and C++ because I miss the functionality of Media Player Classic(windows) and because Totem sucks and there's no other gstreamer media player around!!! But now I have exams so... 

@keeler1 I haven't tried the c++ bindings. I used the c bindings just to expirement. I think when they say "partially implemented" they maybe mean that they work for the gstreamer-core but not for the other extras. Well, I haven't looked it myself.

---

### Post by keeler1 on 2008-06-19
There are a couple of other gstreamer based media players but their interfaces are aweful.

Also other than just the usual music playback and browsing I plan to add a searching mechanism, Video playback and searching (as well as tag/content based searches where the tag or a description is defined by the user), for photos I will do the same thing and also implement a slideshow mechanism.

I was looking at using QT rather than GTK+ because I wanted to minimize the amount of gObject use. c is not object oriented and making it so makes the code ugly.  

Gnome is great but it could definitely use a c++ upgrade.

---

### Post by keifer on 2008-06-19
Are you aware that Qt 4.4 ships with [Phonon](http://doc.trolltech.com/4.4/phonon-module.html)? Since you are already planning to use Qt, I don't really see much of a disadvantage to using it. I personaly have never used Phonon, but I have heard some good things about it. Might be worth checking out. :)

---

### Post by SledgeHammer_999 on 2008-06-19
> **keeler1 said:**
> 
Also other than just the usual music playback and browsing I plan to add a searching mechanism, Video playback and searching (as well as tag/content based searches where the tag or a description is defined by the user), for photos I will do the same thing and also implement a slideshow mechanism.
I think Banshee does that(haven't tried it myself)

> **keeler1 said:**
> I was looking at using QT rather than GTK+ because I wanted to minimize the amount of gObject use. c is not object oriented and making it so makes the code ugly.  

Well I was going to use gtkmm and c bindings for gstreamer(don't take me seriously I am really amateur with coding)

---

### Post by StOoZ on 2008-06-20
> **keifer said:**
> Are you aware that Qt 4.4 ships with [Phonon](http://doc.trolltech.com/4.4/phonon-module.html)? Since you are already planning to use Qt, I don't really see much of a disadvantage to using it. I personaly have never used Phonon, but I have heard some good things about it. Might be worth checking out. :)

thats cool , new to 4.4 and didnt know that. :guitar:
10x

---

### Post by ankursethi on 2008-06-21
Gstreamer is not the only library you can use. Look into Phonon, Xine, Mplayer ...

As far as I know, creating an MPlayer front end would be fairly trivial. You can then focus on the actual media player interface rather than worrying about the underlying median engine.

Obviously, it will be a bonus if you could contribute to something like Totem instead. I'd really like to see Winamp-like behavior there. For example, automatically add "Play in Totem" and "Enqueue in Totem" to the context menu when Totem is running.

It's okay if you're doing this for fun. Make your own, learn from it and *then* contribute to bigger projects.

---

### Post by keeler1 on 2008-06-21
Thanks for the Phonon tip.  I had no idea qt had its own multimedia stuff.  This should help a lot.

---

