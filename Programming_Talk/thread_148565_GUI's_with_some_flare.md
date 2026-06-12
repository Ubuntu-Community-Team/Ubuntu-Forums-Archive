---
title: "GUI's with some flare?"
date: 2006-03-22
forum: Programming Talk
---

### Post by zootreeves on 2006-03-22
I want to start making a GUI for my program, but I want to make it a bit different (not your standard grey GTK). In windows I really like the fact that many apps have different styles (like itunes, wmp, norton antivirus etc), is it possible to do this in linux?

The only exmple of this I have really seen is Songbird ([http://www.songbirdnest.com](http://www.songbirdnest.com)) and [http://ed2k-gtk-gui.sourceforge.net/screenshots.shtml](http://ed2k-gtk-gui.sourceforge.net/screenshots.shtml) where they have changed the GTK background color. How are itunes etc done in windows? is it VB?

---

### Post by IYY on 2006-03-22
> How are itunes etc done in windows? is it VB?

No real programs are written in VB. These days, I think most people use C#.

---

### Post by glug101 on 2006-03-22
[QUOTE=IYY]No real programs are written in VB. These days, I think most people use C#.[/QUOTE]
Actually, believe it or not, I just interviewed at a place that uses visual basic for their main (proprietary) product.  Of course, there are a lot of windows bits that need to be purchased along with it (it's point of sale software), but the key bits that I would support are written in Visual Basic.

Though this approach does seem sick and wrong to me, it's a great company;)

---

### Post by zootreeves on 2006-03-22
So is there some toolkit/framework in windows that allows you to make your own style GUI's? Is there not one for linux?

The mplayer bar ([http://www.linux-fuer-alle.de/images/docs/98/mplayer-blue.png](http://www.linux-fuer-alle.de/images/docs/98/mplayer-blue.png)) is a nice example of what I am looking to do. I think that is done in C++, but how? Are there any books/turoials or something on stuff like this, can someone help point me in the right direction..

---

### Post by anti-net on 2006-03-22
I'm also looking for stuff to improve the GUI on the GNOME front. KDE has very nice GUI but it still is't as nice as commerical stuff like OS 10 and that rip off...Vista! but looking at the screenshots of drapper with the new gnome, theses are looking more pretty.

---

### Post by wmcbrine on 2006-03-22
[QUOTE=zootreeves]I want to start making a GUI for my program, but I want to make it a bit different (not your standard grey GTK). In windows I really like the fact that many apps have different styles (like itunes, wmp, norton antivirus etc), is it possible to do this in linux?[/quote]
X (the base windowing system used in Linux) is the original and king when it comes to apps using a variety of incompatible looks, via different toolkits. Nowadays, we're (finally) lucky to have two fairly comprehensive systems, from which users can pick one, and get all the apps they need, with a consistent look. But of course all the other toolkits are still available, too.

To each his own, but I don't share your taste for programs that each has its own GUI.  Apps should respect the themes chosen by the user.

---

### Post by gord on 2006-03-22
here here!

just to note, songburd uses XUL, which is basically gecko (what mozilla/firefox is based on) via xulrunner, so its more of a html thing.

---

### Post by LordHunter317 on 2006-03-22
[QUOTE=IYY]No real programs are written in VB. These days, I think most people use C#.[/QUOTE]VB.NET is by and large C# with a more verbose syntax, and VB6 was used everywhere.  It was the MS business language for quite sometime, for better or worse.  

And please, please, don't do this.  While I'm not a huge fan of a consistent GUI *per se*, custom widgets that try to be skinnable and fancy tend to annoy me more than help me.

---

