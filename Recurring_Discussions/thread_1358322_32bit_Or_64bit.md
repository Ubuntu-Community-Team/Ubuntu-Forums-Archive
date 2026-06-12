---
title: "32bit Or 64bit?"
date: 2009-12-18
forum: Recurring Discussions
---

### Post by beegary on 2009-12-18
I have seen questions on these forums like 'are you running 64bit'.
 
What difference does this make to Ubuntu? How do I know if I am running 32 or 64?
I intalled using the wubi instalelr and do not remember being asked which version to install.
 
Am I just being stoopid?

---

### Post by philinux on 2009-12-18
Apps>Access>terminal.

```
uname -a
```

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

Best link I've ever found. I've been running 64 bit for yonks.

Important thing is can your machine run 64 bit. What are the specs.

---

### Post by proxess on 2009-12-18
> **beegary said:**
> I have seen questions on these forums like 'are you running 64bit'.
 
What difference does this make to Ubuntu? How do I know if I am running 32 or 64?
I intalled using the wubi installer and do not remember being asked which version to install.

Only certain processors, namely recent ones support 64 bit. If you installed through wubi, and downloaded the CD without choosing whether you wanted 32 or 64 bit, then you have 32 bit, that's the default choice on Ubuntu's website.

---

### Post by beegary on 2009-12-18
Oh I see, its only for the best of the best?
i doubt mine is then, but ill check when I boot it up on the way home.
I have a Samsung NC10 Netbook, it has an Intel Atom processor. Considering how much i paid for it i very much doubt that it is 64 bit
 
thanks peeps

---

### Post by philinux on 2009-12-18
> **beegary said:**
> I have seen questions on these forums like 'are you running 64bit'.
 
What difference does this make to Ubuntu? How do I know if I am running 32 or 64?
I intalled using the wubi instalelr and do not remember being asked which version to install.
 
Am I just being stoopid?

Check your processor with this command.

```
cat  /proc/cpuinfo | grep model
```

---

### Post by 3rdalbum on 2009-12-18
> **proxess said:**
> Only certain processors, namely recent ones support 64 bit. If you installed through wubi, and downloaded the CD without choosing whether you wanted 32 or 64 bit, then you have 32 bit, that's the default choice on Ubuntu's website.

Correction. If you download the CD from the Ubuntu website and you didn't choose whether you wanted 32-bit or 64-bit (amd64), then you probably have 32-bit.

If you downloaded the Wubi installer and it downloaded Ubuntu for you, then it will download the 64-bit edition if your CPU can handle it.

```
ls /var/cache/apt/archives | grep "i386"
```

If you get any results, then you've got 32-bit.

```
ls /var/cache/apt/archives | grep "amd64"
```

If you get any results, you've got 64-bit.

If you don't get any results from either, then install something :-)

---

### Post by Grenage on 2009-12-18
> Oh I see, its only for the best of the best?

No, x64 is old tech.  There are x64 Atom CPUs, but unless you have 3-4+ GB RAM, don't bother, just use x32.

---

### Post by 3rdalbum on 2009-12-18
> **beegary said:**
> Oh I see, its only for the best of the best?
i doubt mine is then, but ill check when I boot it up on the way home.
I have a Samsung NC10 Netbook, it has an Intel Atom processor. Considering how much i paid for it i very much doubt that it is 64 bit
 
thanks peeps

If it's an Atom-based netbook, then it's almost certainly 32-bit. I think the only 64-bit Atoms are desktop versions.

Actually, 64-bit isn't "only for the best of the best". The only PC processors today that aren't 64-bit are the Atoms. All AMD processors have supported it for donkey's years, and all Core 2-era processors and later except for Atom have supported it; actually there were a few Pentium 4-era Intel CPUs that supported 64-bit.

---

### Post by 3rdalbum on 2009-12-18
> **beegary said:**
> I have seen questions on these forums like 'are you running 64bit'.
 
What difference does this make to Ubuntu?

Not a lot. 64-bit processors can do certain types of math faster, and can address more RAM. If you download a package manually and try to install it, you'll only succeed if the package is marked for "amd64" or "all" architectures.

So make sure you keep downloading those "i386" (32-bit) packages for your netbook.

---

### Post by scrapmetal on 2009-12-18
Stick to 32 bit. Have tried 64, then need extra library's. Have broken most of them :confused:(versions). Just broke 9.10 32bit, on this machine. Probably boot loader as was updating from previous version. Keep 8.04.3 LTS as my work horse, and XP as a gamer. So 3 way boot. From trial and error of an idiot, I recommend 32.:) Not second rate :popcorn:

---

### Post by adbge on 2009-12-18
64bit quirks have by and large been ironed out by most modern operating systems. I'm currently finding Ubuntu Karmic x64 quite painless. 

For any user considering 32 vs 64, if you can run 64 bit, do so.

---

### Post by samh785 on 2009-12-18
> **adbge said:**
> 64bit quirks have by and large been ironed out by most modern operating systems. I'm currently finding Ubuntu Karmic x64 quite painless. 

For any user considering 32 vs 64, if you can run 64 bit, do so.
This statement rings true!

---

### Post by Merk42 on 2009-12-18
[SIZE="3"]**Why, why isn't this topic a sticky? I see this question posted almost every day.**[/SIZE]

beegary, you should be running 32bit as the NC10 Netbook doesn't have a 64bit compatible processor.

---

### Post by bodhi.zazen on 2009-12-18
> **Merk42 said:**
> [SIZE=3]**Why, why isn't this topic a sticky? I see this question posted almost every day.**[/SIZE]

beegary, you should be running 32bit as the NC10 Netbook doesn't have a 64bit compatible processor.

Because it is a recurring discussion.

Typically the OP posts such a question without performing even a cursory search , which would reveal the multiple daily threads, and so they ask the same question, and the same discussion ensues.

What makes you think a sticky would help in the slightest ?

The bottom line, if you have a 64 bit processor, start with a 64 bit OS.

uname does not give accurate information on your processor, run:

```
grep --color=always ' lm ' /proc/cpuinfo
```

If you get any output you have a 64 bit processor.

[http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/](http://www.cyberciti.biz/faq/linux-how-to-find-if-processor-is-64-bit-or-not/)

---

### Post by Tibuda on 2009-12-18
> **Merk42 said:**
> [SIZE="3"]**Why, why isn't this topic a sticky? I see this question posted almost every day.**[/SIZE]

beegary, you should be running 32bit as the NC10 Netbook doesn't have a 64bit compatible processor.

The people that don't make searches probably don't read stickies also.

---

### Post by beegary on 2009-12-18
Sorry guys, I did do a quick search for my topic when I was writing the thread.
 
I'll search more closely next time. Im always  being told off for having a mans look

---

