---
title: "Confused about 64bit or 32 bit"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by Phoenix CMXIV on 2008-10-23
here is a link to my **[COLOR="Blue"][CPU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115037")[/COLOR]**

I believe it is 64bit Compatible, i am not sure, I dont wanna dowload the wrong thing.

The download for the 64bit say AMD and INTEL CPU, but the file itself says AMD. what should i dowload???

---

### Post by JeeZiTsDave on 2008-10-23
Yes, it is 64bit, I have the same processor with Ubuntu 8.04 Hardy.

Hope It Helps!

---

### Post by tuxxy on 2008-10-23
You could download the 64-bit version yes :)

---

### Post by bsharp on 2008-10-23
It is 64-bit. Go ahead and use it to its full potential.

Read this also:
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by Phoenix CMXIV on 2008-10-23
OH MY GOD THAT WAS FAST!!!! HOLY **** i posted it and sent a txt to my g/f and i have 3 relpies!!!

---

### Post by ARhere on 2008-10-23
LMAO, glad you like Ubuntu support.

Others might disagree with this, but if you are new to Linux you might want to consider installing the 32-bit version anyways.

A 32-bit OS will work just fine on a 64-bit processors, but a lot of software is still compiled for the 32-bit processor at a _minimal_ needs some interaction from the user to work on a 64-bit platform.

Again, if you are new then I advise the 32-bit version for now.

-AR

---

### Post by tuxxy on 2008-10-23
> **ARhere said:**
> LMAO, glad you like Ubuntu support.

Others might disagree with this, but if you are new to Linux you might want to consider installing the 32-bit version anyways.

A 32-bit OS will work just fine on a 64-bit processors, but a lot of software is still compiled for the 32-bit processor at a _minimal_ needs some interaction from the user to work on a 64-bit platform.

Again, if you are new then I advise the 32-bit version for now.

-AR

What is this lot of software that is only 32-bit compatible? apart from the flash plugin which is useless on 32-bit aswell :confused:

I have setup 64-bit on new users machines without any problems in the past, maybe you could elaborate?

---

### Post by bsharp on 2008-10-23
> **ARhere said:**
> A 32-bit OS will work just fine on a 64-bit processors, but a lot of software is still compiled for the 32-bit processor at a _minimal_ needs some interaction from the user to work on a 64-bit platform.

Not totally true, flash is installed with a simple:

```
sudo apt-get install nspluginwrapper
```

Java with:

```
sudo apt-get install ia32-libs ia32-sun-java6-bin ia32-sun-java6-plugin
```

No more interaction than installing any other package.

---

### Post by Phoenix CMXIV on 2008-10-23
Well i Just Finished Dowloading the 64bit CD, so ill go with that

---

### Post by DoubleMcLovin on 2008-10-23
the fingerprint splash screen ([http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468]("http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468")) for example isn't compatible with 64bit yet, you will need to compile from source to get it to work from my understanding. but I am new to linux also so I could be mistaken =\

---

### Post by ptn107 on 2008-10-23
> **ARhere said:**
> LMAO, glad you like Ubuntu support.

Others might disagree with this, but if you are new to Linux you might want to consider installing the 32-bit version anyways.

A 32-bit OS will work just fine on a 64-bit processors, but a lot of software is still compiled for the 32-bit processor at a _minimal_ needs some interaction from the user to work on a 64-bit platform.

Again, if you are new then I advise the 32-bit version for now.

-AR

I've been using Ubuntu 64-bit since 7.04.  You shouldn't have any problems.

---

### Post by Bölvaður on 2008-10-23
> **bsharp said:**
> Not totally true, flash is installed with a simple:

```
sudo apt-get install nspluginwrapper
```


What the helvíti?
nspluginwraper isn't in the repos is it? Didnt show up on my search

---

### Post by HittingSmoke on 2008-10-23
I've gone through the same dilemma and I'm gonna try and make this real easy. Do you have, or have a use for more than 3 GB of RAM?

If your answer is no, install 32 bit Ubuntu. People will tell you that 64 bit runs better, others will tell you 32 bit runs better.

In all reality the biggest thing it effects is memory addressing. A 32 bit OS can only use just over 3 GB of RAM, which even itself is more than 99% of people ever use. I'm still running 1 GB and never dip in to swap while running movies with all sorts of other programs running in my multiple desktops while I'm working.

Flash and Java are well known as the biggest headaches, which in most cases can be easily worked out on a 64 bit install with a google search, but sometimes problems still arise. There are other less popular packages that are a complete pain on a 64 bit install.

Bottom line, I'd go with 32 bit unless you have a large amount of ram and the need to use it. 64 bit is the way of the future, but some companies who have a grip on the status of current required software wont recognize that quite yet.

---

### Post by sonu 1807 on 2008-10-24
Read [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428) it will surely help. Just recently I moved from 32-bit to 64-bit and I am not facing any issues . I use EVDO device for surfing. I do feel my internet speed has improved after moving to 64-bit

---

### Post by MasterNetra on 2008-10-24
There are somethings that don't directly work with 64 bit. Like adobe air, which i still haven't been able to install using the work around or getlibs. Otherwise it seems fine enough to me and I have a Intel Core 2 Duo too. :)

However, I'll probably switch to 32 bit Intrepid sense i would like to use a few things without the need for a work around, or period. (Wanna have to use windows less :) ). I have only 1 GB of ram so no problem.

---

### Post by Paqman on 2008-10-24
> **HittingSmoke said:**
> 
Flash and Java are well known as the biggest headaches, which in most cases can be easily worked out on a 64 bit install with a google search, but sometimes problems still arise.


Neither of those are an issue any more, either. Installing ubuntu-restricted-extras will sort both out in one step (and a few other useful things, as well).

---

### Post by hyper_ch on 2008-10-24
> **HittingSmoke said:**
> In all reality the biggest thing it effects is memory addressing. A 32 bit OS can only use just over 3 GB of RAM, which even itself is more than 99% of people ever use. I'm still running 1 GB and never dip in to swap while running movies with all sorts of other programs running in my multiple desktops while I'm working.
Yet you are not everyone. Especially when you rip dvds into nice little movies you will note a big improvement. Also with other software that's optimized for 64bit.

I mean why stick to an old 32-bit version if 64-bit is no challenge anymore to get up and running?

At least in Linux there is no real reason anymore to not use 64-bit. I mean you don't buy a 500 HP Ferrari and throttle it down to 100 HP because you're not allowed to drive faster than x km/h.

---

