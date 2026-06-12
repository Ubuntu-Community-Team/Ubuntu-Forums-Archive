---
title: "Gdk+ or Qt3/4"
date: 2010-02-23
forum: Programming Talk
---

### Post by madmax.santana on 2010-02-23
Well. if someone has been keeping tabs on me, he might know that I have been very much into programming GUI applications in Ubuntu / Linux...

As it seems, I have so far learned at least how to approach an objective while designing applications! I am not a pro, but my knowledge and experience has increased considerably as to that on last weekend. I have been in on Gtk+ and recently the Glade!

But suddenly it struck me, as someone pointed out in some other thread I had posted to ask for help in an entirely different matter, that maybe starting with gtk+ is just a waste of time. If I am going to build an application which runs on most of the Linux distributions, I might watch my step... As maybe, the application written in gtk+ are not compatible with Kde, Xfce or other desktop environments!!! I need to confirm that!!! 

Are gtk+ applications portable to other desktop environments?

Well, if no, it is very sad! I have a very impatient personality! I shall definitely lose hope in gtk+ since it will no longer charm me! But I shall be on to the other envoirnment that you people might suggest!

Somewhere, someone named Qt3... Well, is that the answer??? Are Qt3 applications portable to other desktops beside KDE???

Please give your opinions!

---

### Post by nerdy_kid on 2010-02-23
i dont know who told you that, but he was wrong :)
gtk runs no problem on other DEs besides GNOME. (I use KDE4.4)
In my (somewhat limited) experience, most Linux DEs use GTK+.  The only one that doesnt, as far as i know, is KDE, which as you know, uses QT.  I am not a programmer, but looking at the interface differences, QT would be the way to go IMHO.  It seems to be more powerful, as far as embedding apps, widget support and theming control.  It is also easy (so ive heard) to port to Windows.  I think it really depends on what you are going to use it for.

---

### Post by madmax.santana on 2010-02-23
Thanks pal...

Plus, I just came across this
[http://digg.com/linux_unix/GTK_vs_QT](http://digg.com/linux_unix/GTK_vs_QT)

And it has given me quite a peace-of-mind thing! :) Glad you could help. Thanks a lot! Problem solved... I just wanted to know if GTK apps could run on other platforms!
But I shall be sure to give KDE a try as well... :)

---

### Post by Some Penguin on 2010-02-23
It's not a question of compatibility so much as it is a question of dependencies and conveniences.  You could use Motif if you liked; it'd just be more inconvenient for the users since they may not happen to have Motif libraries already installed, and might be more work to integrate with things like docks and so forth.

---

### Post by CptPicard on 2010-02-24
As far as "technology" goes, I've always been partial to Qt... it really has everything in a nicely designed set of libraries, and it's portable too. The only downside is C++ which makes harder to bind to it and thus tries to enforce a language on you...

Now that Nokia owns Trolltech and is putting a lot of effort in the development tools -- and intends to put that as the GUI library on top of new Symbian kernels and and the Maemo devices as well, I've been dusting off my Qt knowledge in anticipation...

---

### Post by madmax.santana on 2010-02-24
Yeah, you know, I haven't started with Qt yet... Just had a look at some codes. And I already like it.

I haven't been involved with C previously. But I knew how it worked since it was almost same at C++... So I didn't have a problem learning Gtk+. But I sure did have problem coping with the C like code... I managed it alright but I didn't "like" it, if you know what I mean...


So far, looking at the code of a Qt app gives me feeling like, "yeah baby, that's like real code, man"... Hahaha! I will go for it... Classes and object models intrigue me, and I guess Qt will be more fun than Gtk+ was! :)

[COLOR=Red]**Edit:**[/COLOR] [COLOR=SeaGreen]Oh, I didn't see who posted the above entry. I see now. It's CptPicard... Hi there, Cap'n! Please don't start ripping off my comments over "disliking" C or about liking Qt... Hahaha, just kidding! Looking forward to your views on my ideology... :)[/COLOR]

---

