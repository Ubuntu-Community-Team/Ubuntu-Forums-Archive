---
title: "installing software? USC not working."
date: 2011-12-16
forum: New to Ubuntu
---

### Post by monsterbronc on 2011-12-16
Im finally online, and I would love to get some dvd player/ripper programs, and a few others, but how?
Im on dialup, does that matter?
Ive opened ubuntu software center, and surfed around, I find a program I want and select it, at the bottom it will say available from the "universe" (or multiverse etc) source, and at the far right is a "use this source" button, but it wont let me select it, do I need to be at a specific website?

I logged on useing firefox, and was able to get firefox add ons just fine.

 Ive tried the "sudo apt-get install blobity bla" and this is what happens...

> monsterbronc@DeepThoughtII:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wine

again, do I need to be at a specific website, or what?

and the guide that came with Ubuntu is basically worthless to me, heres what it says to use  SPM and USC...
> 
Synaptic Package Manager

While "apt-get" and "aptitude" are fast ways of installing programs/packages, you can also use the
Synaptic Package Manager (Menu -> System -> Administration -> Synaptic Manager), a GUI method for
installing programs/packages. Most (but not all) programs/packages available with apt-get install will also
be available from the Synaptic Package Manager. This is the preferred method for most desktop users. In
this guide, when you see
sudo apt-get install package
you can simply search for package in Synaptic and install it that way.
Menu -> System -> Administration -> Synaptic Package Manager
• Search for the name of the program/package. You can also search for a word in its
description.
-> Mark for Installation -> Apply
• The selected program(s) will be automatically installed, along with its dependencies.

Ubuntu Software Center (Add/Remove Programs)

Not all packages available from apt-get, aptitude, and Synaptic Package Manager are available in the
Ubuntu Software Center. However, it is the easiest interface for new users of Ubuntu and directs them to
preferred packages.
Menu -> Applications -> Ubuntu Software Center
• Search for the sort of program you want to add. Example: type MP3 to see a list of mp3
software.
-> Mark for Installation -> Apply
• The selected program(s) will be automatically installed.

I see no "-> Mark for Installation -> Apply" anywhere

I honestly thought once I was online this would be easy,  but truthfully, this is getting to be more and more a PITA.

Thanks for your help, Steve

---

### Post by jerome1232 on 2011-12-16
I honestly don't use those gui's, but have you updated your package list?

Try

```
sudo apt-get update
sudo apt-get install wine
```

Since your on dial-up, grab a soda :P

---

### Post by hakermania on 2011-12-16
> **jerome1232 said:**
> Since your on dial-up, grab a soda :P

On the other thread:
```
Spilled a soda into your keyboard?
```

I loled :P

Heh. True, when GUIs fail, use terminal, if this fails then you need help :D

---

### Post by jerome1232 on 2011-12-16
Lol, okay, keep it away from your keyboard! (I admit, I go through them I bit more often than I should, soda's and keyboards both)

---

### Post by monsterbronc on 2011-12-16
> **jerome1232 said:**
> I honestly don't use those gui's, but have you updated your package list?

Try

```
sudo apt-get update
sudo apt-get install wine
```Since your on dial-up, grab a soda :P

Somethins happinin, But I think I slowed it down by posting this.

---

### Post by cortman on 2011-12-16
Your repositories probably just need updating, as the other guys said.

> **monsterbronc said:**
> 
monsterbronc@DeepThoughtII

Deep Thought FTW! See my location.

---

### Post by monsterbronc on 2011-12-16
> **cortman said:**
> Your repositories probably just need updating, as the other guys said.



Deep Thought FTW! See my location.

Hey, Ive been there.
The butnu box is Earth
the dual boot is DeepthoughtII(windows boots as Hal 5000)
and the laptops Deepthought

and most of my screensavers are the wobbly text fourty-2, or some variation (OMG, Im a Geek)

roll d20

anyways, it downloaded, took a while, but I ran out of time and Ill have to tinker later, did it install automatically, or do I have to manually configure the update?

Soda? Who needs soda when you've got Tequila? when boogering with computers
I find I need mental lubricant:)

---

### Post by cortman on 2011-12-16
> **monsterbronc said:**
> Hey, Ive been there.
The butnu box is Earth
the dual boot is DeepthoughtII(windows boots as Hal 5000)
and the laptops Deepthought

and most of my screensavers are the wobbly text fourty-2, or some variation (OMG, Im a Geek)

roll d20

anyways, it downloaded, took a while, but I ran out of time and Ill have to tinker later, did it install automatically, or do I have to manually configure the update?

Soda? Who needs soda when you've got Tequila? when boogering with computers
I find I need mental lubricant:)

If you ran sudo apt-get install wine, it installed it. Run that command to download/install wine.

Great computer names! Your login name should be Lunkwill or Phook.

---

### Post by jerome1232 on 2011-12-16
Yup should be there, the gui's should all work as well now.

edit: No tequila for me, religious reasons :P

---

### Post by monsterbronc on 2011-12-21
thanks guys, all is working, wine was BIG and took a while, (for dialup anyways), If I knew how to remark this post as solved, I would.

---

### Post by jerome1232 on 2011-12-21
Thread Tools - Mark as Solved

---

