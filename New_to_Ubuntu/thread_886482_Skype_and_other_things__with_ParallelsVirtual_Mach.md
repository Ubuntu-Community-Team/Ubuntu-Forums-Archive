---
title: "Skype and other things  with Parallels/Virtual Machine?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Nebelhom on 2008-08-11
Hi guys,

Quick question about Parallels/VMWare: If Skype doesn't work with microphone and camera mode on ubuntu (tried a lot and it didn't work), should I be able to use one of the above softwares to run windows in parallel to use it via windows? This is purely generally speaking, because it is one of the things that I haven't got to work yet in ubuntu (but works well on XP) and will soon be heavily relying on again.
If so, which one would you suggest? 

the other software that I would need to use in the near future is ChemDraw (sorry, I'm slightly different kind of geek) which doesn't have any support in linux (yet) afaik. any idea whether I can copy/paste structures from VMWare into open office document?

cheers,

Nebelhom

---

### Post by bpowell2005 on 2008-08-11
To answer your second question: I use VMWare the other way (run Ubuntu on Windows)...but I can not copy and paste between them...if I select "Copy" in the virtual machine, then that data is stored on the Virtual Machines clipboard, not the host.

However, you can run Open Office on the Virtual Windows installation, and save a document from there to a shared resource.

---

### Post by Nebelhom on 2008-08-11
Poo! ;( Ok, first drawback if it is true for the other way round - windows in ubuntu, that is (don't see why not).

Ah well, thanks anyways, I'll probably just try to use Skype via this. Which software would be good? Afaik, VMWare is free and Parallels commercially available... that right?

---

### Post by dmizer on 2008-08-11
There's no reason not to try skype.  I was able to get a USB phone to work in an Ubuntu hosted XP guest in vmware but it wouldn't work in Ubuntu.

I've been using vmware server for at least 3 years now with zero complaints.

There's also a new open source virtual machine called [virtualbox](http://www.virtualbox.org/), but some people seem to have difficulty getting networking set up correctly.

As for ChemDraw, [Wine](http://www.winehq.org/) might be an option for you: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=3060](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3060)

```
sudo aptitude install wine
```

---

### Post by Nebelhom on 2008-08-11
Hey thanks dmizer,

you're giving me some hope at least :). Will try it right after work.

I never gave Wine a try for [_this reason_.]("http://ubuntuforums.org/showthread.php?t=411537")

cheers guys

Nebelhom

EDIT: Sorry, I just found out that there have been made advances by the Wine team to get ChemDraw to work now. [_According to their website_]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7667&iTestingId=23828") it has a gold rating now.

...Should have researched into the topic a bit more. stupid me.

---

