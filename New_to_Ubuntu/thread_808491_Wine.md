---
title: "Wine"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by x88a on 2008-05-26
Wine is a program that allows windows progam to be used in Linux, correct?
However, is there a restriction to the type of programs supported by Wine?
if yes, where can i see this list?

Does anyone know how to install Wine?
How do i use it?
any readme file for it?

TQ

---

### Post by AndyCooll on 2008-05-26
You'll find all you need to know about Wine here: [Wine HQ]("http://www.winehq.org/")
Or from our own forums here: [Wine]("http://ubuntuforums.org/forumdisplay.php?f=313") 

IIRC you can install Wine from the repos. You may need to enable the multiverse repository first (System > Administration > System Sources).

Once installed it works like a compatibility layer. So from a command line you'd type something along the lines of "wine /path/to/setup.exe".


:cool:

---

### Post by x88a on 2008-05-27
btw, Wine does not support all programs, right?

---

### Post by kesman on 2008-05-27
Wine has a large application database, that contains info about every program that is able to run with it. Games, Graphics, Video editing, anything goes.

---

### Post by sayakb on 2008-05-27
Wine supports: [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by x88a on 2008-05-27
> **kesman said:**
> Wine has a large application database, that contains info about every program that is able to run with it. Games, Graphics, Video editing, anything goes.

just to be sure.....do u mean that Wine supports everything?

---

### Post by x88a on 2008-05-27
> **LinuxIsInnovation said:**
> Wine supports: [http://appdb.winehq.org](http://appdb.winehq.org)

i saw this website.
this is the part that confuses me.
Isnt there a search option or a cmoplete lists of programs it supports?

---

### Post by adobrakic on 2008-05-27
[http://appdb.winehq.org/appbrowse.php](http://appdb.winehq.org/appbrowse.php)

---

### Post by cheesypoof on 2008-05-27
There is a "Search the AppDB" on the website. Look along the left side. Additionally, most programs have been tested by users, so you should be able to find out quickly whether it is supported or not. I have been very pleased with the ability of Wine to get applications like Photoshop, Ventrilo, and Steam games to work. Remember that wine installs to... "/home/user/.wine" <-- I think :|

---

### Post by s_spiff on 2008-05-27
Also it's been suggested somewhere ( don't remember where exactly, probably their download page itself ) that it's safer to use their repo's instead of the ubuntu repos to install Wine ( and Wine only!) as some people have had issues with the Ubuntu Repo version. I haven't used the Ubuntu Repo version, so cannot really verify this. Anyways, incase you need it, the repo's provided by Wine are given here :
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by housam on 2008-05-27
You can read more here.[[COLOR="Red"]_http://www.psychocats.net/ubuntu/wine_[/COLOR]]("http://www.psychocats.net/ubuntu/wine")

---

