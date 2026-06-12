---
title: "Tomboy / Gnotes"
date: 2011-05-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by VinDSL on 2011-05-21
I can't get Tomboy to fire up in UbuOO, from the desktop.

Tomboy runs from CLI, but errors out & closes when I try to open a note.

I installed Gnotes, and it runs just fine, but I don't see any way to sync it with Ubuntu One (where I store Tomboy notes).

Anyone have a workaround?  Either fixing Tomboy, or sync'ing Gnotes with Ubu One?

---

### Post by amano on 2011-05-22
There hasn't been any sync support for Gnote coded yet. Not for Ubuntu One, not for anything else. That's the thing where it is still lacking in comparison to Tomboy.

---

### Post by VinDSL on 2011-05-22
> **amano said:**
> There hasn't been any sync support for Gnote coded yet. Not for Ubuntu One, not for anything else. That's the thing where it is still lacking in comparison to Tomboy.
Drat!  Well, that's creates a real problem for me.  :(

I (mostly) run dev branches, and can't trust my notes (or even the OS) to be there, the next time I boot up.

Ubuntu One is a lovely place to store them...

Hopefully, Tomboy will be working soon and/or Gnotes will acquire the ability to sync to Ubu One.

Thanks for the reply!

I was starting to wonder if anybody else even took notes et al.  :D

---

### Post by VinDSL on 2011-05-22
Oops!  Just realized I've been typing Gnotes, instead of Gnote.  :oops:

Anyway, I figured out a workaround, of sorts.

I simply copy n' pasted my notes from:


[INDENT]/home/<username>/.local/share/**tomboy** -> /home/<username>/.local/share/**gnote**[/INDENT]


That way, I can use Gnote until Tomboy starts working again.

I'll sync Gnote to Ubu One via Nautilus, e.g. no plugin needed.

Winning!  Duh!

---

### Post by MAFoElffen on 2011-05-22
> **VinDSL said:**
> I can't get Tomboy to fire up in UbuOO, from the desktop.

Tomboy runs from CLI, but errors out & closes when I try to open a note.

I installed Gnotes, and it runs just fine, but I don't see any way to sync it with Ubuntu One (where I store Tomboy notes).

Anyone have a workaround?  Either fixing Tomboy, or sync'ing Gnotes with Ubu One?
Are your unresolved  dependencies "resolved" yet?  I'm on server base with ubuntu-desktop / you desktop...  My unresolved depencies from the "Let The Breakage Begin" is left at Tomboy and about 5 openjdk packages,...  So Tomboy is still a no-go for me since then.

Might be connected there somehow.  I'm still hoping that resolves with the repo updates as we get closer to alpha1, but I guess we'll see.

---

### Post by zekopeko on 2011-05-23
> **VinDSL said:**
> Oops!  Just realized I've been typing Gnotes, instead of Gnote.  :oops:

Anyway, I figured out a workaround, of sorts.

I simply copy n' pasted my notes from:


[INDENT]/home/<username>/.local/share/**tomboy** -> /home/<username>/.local/share/**gnote**[/INDENT]


That way, I can use Gnote until Tomboy starts working again.

I'll sync Gnote to Ubu One via Nautilus, e.g. no plugin needed.

Winning!  Duh!

Just take note that Gnote doesn't promise compatibility with Tomboy (you can import but there is no guarantee of export). You could be locked into Gnote.

---

### Post by gnomeuser on 2011-05-23
> **VinDSL said:**
> I can't get Tomboy to fire up in UbuOO, from the desktop.

Tomboy runs from CLI, but errors out & closes when I try to open a note.

I installed Gnotes, and it runs just fine, but I don't see any way to sync it with Ubuntu One (where I store Tomboy notes).

Anyone have a workaround?  Either fixing Tomboy, or sync'ing Gnotes with Ubu One?

Can you please file a bug on this ubuntu-bug tomboy should suffice.

---

### Post by VinDSL on 2011-05-24
> **gnomeuser said:**
> Can you please file a bug on this ubuntu-bug tomboy should suffice.
Will do...  ;)

---

### Post by VinDSL on 2011-05-27
Tomboy started working (open, save, sync with Ubu One, et cetera) after the last update cycle.

I'll go update the bug report...

---

### Post by VinDSL on 2011-06-26
**_[COLOR="DarkOrange"]26-JUN-2011[/COLOR]_**

LoL!  I swear... I must be the only UbuOO tester that uses Tomboy.  :D

Tomboy hasn't worked (for me) since 3-Jun, e.g. since Alpha-1.

I kept *thinking* that someone would mention it, in these threads, but they didn't, sooo...

I judged that it was either a local problem, or nobody else uses Tomboy, blah, blah, blah.

Anyway, today's update provided the fix:


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-26-jun-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-26-jun-2011.png")[/INDENT]


Er...

How do you get by without Tomboy - crayon and a piece of cardboard - sticky tabs on your monitor - memorization?!?!?!?

I don't get it...  :confused:

---

### Post by lucazade on 2011-06-26
> **VinDSL said:**
> 

Er...

How do you get by without Tomboy - crayon and a piece of cardboard - sticky tabs on your monitor - memorization?!?!?!?

I don't get it...  :confused:

I prefer a hierarchical note manager like Zim Wiki
[http://www.zim-wiki.org/](http://www.zim-wiki.org/)

---

### Post by VinDSL on 2011-06-26
Whoa!  Nice one!  I must give it a try...  :)

I rely on notes (et al.) and Tomboy is okay, when it works.

It's perpetually broken in dev releases, thus a poor choice during the testing phase.

Thanks, for the suggestion.  ;)

---

### Post by lucazade on 2011-06-26
glad you liked it! Unbreakable and crossplatform..can't live without!

---

### Post by garvinrick4 on 2011-06-26
> It's perpetually broken in dev releases, thus a poor choice during the testing phase.I was under the impression it had to do with mono
First time it has been a broken package for myself:
Fixed for me today with this upgrade:
Start-Date: 2011-06-26  13:37:31
Upgrade: tomboy:amd64 (1.6.1-0ubuntu4, 1.6.1-0ubuntu5), linux-libc-dev:amd64 (3.0-1.2, 3.0-2.3)
End-Date: 2011-06-26  13:38:02

---

### Post by cariboo on 2011-06-26
I personally use [zim]("http://zim-wiki.org/"), and back it up to my local server.

---

### Post by lidex on 2011-06-27
> **VinDSL said:**
> **_[COLOR="DarkOrange"]26-JUN-2011[/COLOR]_**

LoL!  I swear... I must be the only UbuOO tester that uses Tomboy.  :D

Tomboy hasn't worked (for me) since 3-Jun, e.g. since Alpha-1.

I kept *thinking* that someone would mention it, in these threads, but they didn't, sooo...

I judged that it was either a local problem, or nobody else uses Tomboy, blah, blah, blah.

Anyway, today's update provided the fix:


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-26-jun-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-26-jun-2011.png")[/INDENT]


Er...

How do you get by without Tomboy - crayon and a piece of cardboard - sticky tabs on your monitor - memorization?!?!?!?

I don't get it...  :confused:

I use it and had some issues as well. Believe it started working when I added it to systray-whitelist in dconf-editor.

OT alert --
...but it only feels like 100, nice.

---

### Post by VinDSL on 2011-06-27
> **lidex said:**
> OT alert --
...but it only feels like 100, nice.
Heh!

Yeah, my Tuniq Tower cooler isn't for looks...  :D


[INDENT][IMG]http://vindsl.com/images/vindsl-cooler-2.jpg[/IMG][/INDENT]

---

### Post by VinDSL on 2011-06-27
> **cariboo907 said:**
> I personally use [zim]("http://zim-wiki.org/"), and back it up to my local server.
I think that's what I'll do, then backup-the-backup to Ubuntu One.  ;)

---

### Post by jfernyhough on 2011-06-27
Does anyone know of an easy way to import tomboy/gnote notes into Zim? I've found a python script from 2008 but I'm not sure if formats have changed since then.

---

### Post by lucazade on 2011-06-27
> **jfernyhough said:**
> Does anyone know of an easy way to import tomboy/gnote notes into Zim? I've found a python script from 2008 but I'm not sure if formats have changed since then.

Unfortunately no..
IIRC is tomboy is based on XML , zim on plain TXT files.. when I switched to zim I spent some hours of select text and middle-click :D

---

