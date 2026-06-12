---
title: "What project should I hack on?"
date: 2006-01-09
forum: Programming Talk
---

### Post by joeljkp on 2006-01-09
So I'm sitting here at work waiting for various things to run. This happens a lot, and I usually have a good bit of time to kill before things end.

So, I'm trying to find a good project to hack on a bit here at work while I'm waiting around. I'm on Solaris 8 with both GCC and Sun Studio, so doing some porting work is a possibility.

Any suggestions?

---

### Post by welsh_spud on 2006-01-09
[http://sourceforge.net/](http://sourceforge.net/) is briming with FOSS projects that may like.

---

### Post by joeljkp on 2006-01-09
[QUOTE=welsh_spud][http://sourceforge.net/](http://sourceforge.net/) is briming with FOSS projects that may like.[/QUOTE]
Well, yeah, but I'm overwhelmed by choices. I'm looking for specific recommendations.

---

### Post by hentaidan on 2006-01-09
Well if you're taking suggestions, I have quite a few "niggles" with some programs that I'd sort out myself if I knew how to code ;-)

---

### Post by joeljkp on 2006-01-09
[QUOTE=hentaidan]Well if you're taking suggestions, I have quite a few "niggles" with some programs that I'd sort out myself if I knew how to code ;-)[/QUOTE]
Go for it :)

---

### Post by hentaidan on 2006-01-09
Well off the top of my head...

**Xfce **could do with a few improvements
[LIST]
[*]better customization of the panel, i.e. allowing complete removal, better graple bars
[*]I also don't like the way it places the menu (dependant on cursor) when you click on a programs icon in the title bar, perhaps an option to "do like GNOME etc." where the menu appears the same place regardless of where you click
[*] an option on when you right click on programs in the task bar to move to another workspace
[/LIST]

**Galeon** is a cool and quick browser that I found recently,
[LIST]
[*]but it appears to like crashing a lot
[*]and some sort of better customization of the address bar, bookmarks etc., to enable more viewport space
[/LIST]

**gmail-notify**
[LIST]
[*]seems to insist on freezing every so often, esp. when disconnected from the net
[*]and seems to enjoy shooting the "new email" notification half way up my screen
[/LIST]

I should really file bug reports for half of these though....

---

### Post by gord on 2006-01-10
you should really do something you are actually interested in, allthough if you happen to have absolutly no interests whatso ever and are a robot of some kind, [wine](http://www.winehq.com) can allways do with some help.

---

### Post by joeljkp on 2006-01-10
Bah, 4 good suggestions, and none I can actually do :)

xfce, galeon, and gmail-notify all require gtk2, which Solaris 8 doesn't have, and can't support due to lack of RENDER. And wine isn't of much use on a sparc box :)

Wine's interesting though, I hack on it a bit at home.

---

### Post by -Rick- on 2006-01-10
[QUOTE=joeljkp]I'm on Solaris 8 with both GCC and Sun Studio, so doing some porting work is a possibility.

Any suggestions?[/QUOTE]
If you want you can try to compile my project on Solaris...I want unix ports...lots of them :)

[https://developer.berlios.de/projects/nixstaller/](https://developer.berlios.de/projects/nixstaller/)

I haven't released anything yet (currently finishing first version) and the site needs some work.

---

### Post by joeljkp on 2006-01-10
[QUOTE=-Rick-]If you want you can try to compile my project on Solaris...I want unix ports...lots of them :)[/QUOTE]

Sounds good, I'll check it out.

---

### Post by joeljkp on 2006-01-10
Argh, you don't happen to have a CVS mirror of the repo, do you? My Solaris box doesn't have subversion.

---

### Post by -Rick- on 2006-01-10
[QUOTE=joeljkp]Argh, you don't happen to have a CVS mirror of the repo, do you? My Solaris box doesn't have subversion.[/QUOTE]
I only use svn. But after some quick googling I found this: [http://www.sunfreeware.com/programlistintel8.html#subversion](http://www.sunfreeware.com/programlistintel8.html#subversion)

---

### Post by Omnios on 2006-01-10
How about starting  a new project. A Karamba/Superkaramba type dock app program for gnome. There are many dock apps for Gnome but they useualy take up a lot of resources when running Gnome. Somehow Superkaaramba takes up very little resources which I think is done by carefull coding and scripts that take very little resources when accessing sensors etc, though I find it uses heavy resources when accessign terminal through grip. 

 It may be possible to make a asimilar app for Gnome that takes very little resources to run and easy to script for customisation. One of the main reasons I also use KDE is I made my own SuperKaramba app that takes up 5 megs ram and about 1 to 3% cpu.

---

