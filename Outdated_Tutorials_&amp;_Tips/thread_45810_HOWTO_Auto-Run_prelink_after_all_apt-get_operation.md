---
title: "HOWTO: Auto-Run prelink after all apt-get operations"
date: 2005-07-01
forum: Outdated Tutorials &amp; Tips
---

### Post by intangible on 2005-07-01
This assumes you already have prelink installed on your system.
If you have not set it up yet, follow this howto: [thread]1971[/thread]

Everyone knows the biggest problem with prelink is that it's possible after an update, your programs may be running with old prelinked settings, and you should run prelink after library updates;  Well this howto automates that for you.

The following makes prelink run after every apt-get action (apt-get install, apt-get remove)

**sudo gedit /etc/apt/apt.conf** (the file may not exist yet)

```
DPkg::Post-Invoke {"echo Running prelink, please wait...;/etc/cron.daily/prelink";}
```

Viola! :)

That will also run inside synaptic, and should be ran by anything else that uses apt.

---

### Post by poofyhairguy on 2005-07-01
Nice. Thats very much what YAST does. 

This rocks!

---

### Post by gammyhand on 2005-07-05
[QUOTE=poofyhairguy]Nice. Thats very much what YAST does. 

This rocks![/QUOTE]
 Fit! Very fit!

---

### Post by bored2k on 2005-07-05
:D Marvelous. +2 points for horny dude !ª

---

### Post by geearf on 2005-07-14
Hello,

isn't there a way to only prelink what's been installed ?
Cause a normal prelink is so long, i can't see myself waiting for it every time I install something.

Thanks,

---

### Post by bored2k on 2005-07-14
[QUOTE=geearf]Hello,

isn't there a way to only prelink what's been installed ?
Cause a normal prelink is so long, i can't see myself waiting for it every time I install something.

Thanks,[/QUOTE]
 Prelink is only slow the first time. If you don't do a lot of changes, prelink will be really fast.

---

### Post by geearf on 2005-07-14
ooh,

well i am trying to see that right now,

i've fulfilled a complete prelink (or i think so), and after installing bittornado i am doing it again, and you're right it was'nt that long :)

---

### Post by bored2k on 2005-07-14
[QUOTE=geearf]ooh,

well i am trying to see that right now,

i've fulfilled a complete prelink (or i think so), and after installing bittornado i am doing it again, and you're right it was'nt that long :)[/QUOTE]
 Every 14 days you will get a "slow" prelink.

---

### Post by geearf on 2005-07-14
Yes that i know, but i thought that running this command was always the long one, and the short one was with some more parameters or stuff to the prelink bin, well whatever .... :)

---

### Post by Kyral on 2005-07-14
Imagine the prelink after upgrading to Breezy in Oct :P

---

### Post by McQuaid on 2005-07-14
I've never played with prelinking yet.  How do you deal with this if you occasionally compile software.

---

### Post by bored2k on 2005-07-14
[QUOTE=McQuaid]I've never played with prelinking yet.  How do you deal with this if you occasionally compile software.[/QUOTE]
 Every 14 your system prelinks automatically, but if you want to do it manually, you just run
/etc/cron.d/prelink I believe. Or just run prelink -amvR

---

### Post by geearf on 2005-07-14
Well in fact it did not seem that good.

I use a lot kynaptic, i've installed a small package and the prelink went on for almost an hour till I shut it down to use kynaptic again.

So I really don't know, was it because of kynaptic ?
or because of the prelink?

---

### Post by henriquemaia on 2005-07-15
Having followed both HowTos, everything worked fine.

Thanks a lot for this one!

---

