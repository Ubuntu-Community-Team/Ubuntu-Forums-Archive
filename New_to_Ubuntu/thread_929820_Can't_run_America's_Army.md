---
title: "Can't run America's Army ??"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Christian91 on 2008-09-25
Hey guys, 

Pretty new to linux so wanted to try out some games... I have downloaded and installed America's Army but can't run it. I have been looking a lot around and done all the things that people have posted. 

I have gone into preferences and ticked the box so it is executable so I don't think that is the problem. When i try to run it just does nothing ?

I'd be very grateful for some help ;)

---

### Post by TriSwords on 2008-09-25
Do you have WINE installed?

Check [http://appdb.winehq.org/](http://appdb.winehq.org/) and see if Wine supports it.

---

### Post by billgoldberg on 2008-09-25
> **TriSwords said:**
> Do you have WINE installed?

Check [http://appdb.winehq.org/](http://appdb.winehq.org/) and see if Wine supports it.

Don't give advice if you don't know anything about the subject.

AA has a native linux version.

--

I never tried it, nor do I feel the need to try it so I can't help you.

---

### Post by Christian91 on 2008-09-25
yes, it's a native linux version so i don't think i can run it through wine.. I have tried it though, but don't work.

---

### Post by philinux on 2008-09-25
> **Christian91 said:**
> yes, it's a native linux version so i don't think i can run it through wine.. I have tried it though, but don't work.

Run it from a terminal and see what error it spits out.

---

### Post by TriSwords on 2008-09-25
I was under the impression they didnt make the Linux version anymore. At least I cant find anything past 2.5 of it. Maybe I missed it.

---

### Post by Christian91 on 2008-09-25
Do you write anything in front of it in terminal ?

---

### Post by semitone36 on 2008-09-25
No you shouldn't have to put anything in front of it.

You might want to repost this thread in the gaming and leisure forum.  The people there are really good with this sort of stuff.

---

### Post by chuckyp on 2008-09-25
> **Christian91 said:**
> Hey guys, 

Pretty new to linux so wanted to try out some games... I have downloaded and installed America's Army but can't run it. I have been looking a lot around and done all the things that people have posted. 

I have gone into preferences and ticked the box so it is executable so I don't think that is the problem. When i try to run it just does nothing ?

I'd be very grateful for some help ;)

Open a terminal and navigate to the directory where you extracted the game. Then try running the executable see what error you get. Most likely you will need 3d drivers for your video card. Which are availible in System > Administration > Hardware Drivers

---

### Post by semitone36 on 2008-09-25
What kind of architecture do you have? (64bit or 32bit)

---

### Post by Christian91 on 2008-09-25
Alright cheers, i'm just a noob with this sort of thing so i did it here ;)

---

### Post by Christian91 on 2008-09-25
I think i do have 3d drivers, this is what it says when i try in terminal:


christian@christian-laptop:~$ '/home/christian/armyops/armyops' 
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

