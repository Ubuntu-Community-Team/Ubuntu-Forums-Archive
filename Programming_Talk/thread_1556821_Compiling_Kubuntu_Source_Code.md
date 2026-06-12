---
title: "Compiling Kubuntu Source Code"
date: 2010-08-19
forum: Programming Talk
---

### Post by rjcalifornia on 2010-08-19
Hello! I want to download the source code of Kubuntu 10.04. However, before doing that I would like to know how  can I compile it? I mean, what do I have to do in order to create the iso image from the source code...?

Thanks!!
:lolflag:

---

### Post by Bachstelze on 2010-08-20
There is no such thing as "the source code of Kubuntu".  Kubuntu is a collection of software, not a single program.  You can get the source code for a particular package with

```
apt-get source <package_name>
```

To make an ISO, you can look at Remastersys (though that's not how the ISOs you download are made, it should be good enough for you).

---

### Post by rjcalifornia on 2010-08-20
I think I didn't explain well enough.

I want to download this:
[http://cdimage.ubuntu.com/kubuntu/releases/10.04/release/source/](http://cdimage.ubuntu.com/kubuntu/releases/10.04/release/source/)
that is the source code of kubuntu. I want to know how can it be compile?

---

### Post by Bachstelze on 2010-08-20
The ISOs contain the source packages, which are the same thing you get with [font=monospace]apt-get source[/font]. To create the binary packages, you can use debuild or pbuilder, see [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

---

### Post by schauerlich on 2010-08-20
> **Bachstelze said:**
> The ISOs contain the source packages, which are the same thing you get with [font=monospace]apt-get source[/font]. To create the binary packages, you can use debuild or pbuilder, see [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

I think he wants to build everything gentoo style.

---

### Post by rjcalifornia on 2010-08-20
> **schauerlich said:**
> I think he wants to build everything gentoo style.

You got that right! Can I use that cd image to build everything like you stated before????

---

### Post by phrostbyte on 2010-08-21
[apt-build]("apt:apt-build") can build your entire Ubuntu system from scratch and even add custom optimisations to the build.

Word of caution: It takes a really really really long time even on a modern quad-core. It would be useful to have a few supercomputers lying around.

---

### Post by CptPicard on 2010-08-21
> **rjcalifornia said:**
> You got that right! Can I use that cd image to build everything like you stated before????

Mind you, there is more to building a distribution than just compiling source. Most of it is actually about the packaging and integrating the packages and fixing up the configuration...

You really don't gain much from watching the compiler output scroll by, but if you're interested in from-source distributions, you should probably be looking at Gentoo, as that teaches you about the configuration aspect as well, which is what you *do* want to be learning right now.

---

### Post by rjcalifornia on 2010-08-25
> **CptPicard said:**
> Mind you, there is more to building a distribution than just compiling source. Most of it is actually about the packaging and integrating the packages and fixing up the configuration...

You really don't gain much from watching the compiler output scroll by, but if you're interested in from-source distributions, you should probably be looking at Gentoo, as that teaches you about the configuration aspect as well, which is what you *do* want to be learning right now.


oh ok... so is not that easy... :(

---

### Post by Bachstelze on 2010-08-25
> **rjcalifornia said:**
> oh ok... so is not that easy... :(

If it were, distributions wouldn't have so many people working on them...

---

