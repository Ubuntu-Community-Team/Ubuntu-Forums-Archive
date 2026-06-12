---
title: "Creating a Native C &amp; GTK2 Bittorrent Client"
date: 2007-02-28
forum: Programming Talk
---

### Post by Benitez on 2007-02-28
[SIZE="3"]
Okay, here it goes again...

I have taken a look at some of the Python sources for the original BitTorrent client, and I want to know if anyone is either working on or would be interested in working on a natively built BitTorrent library in portable C code, and also to make a front-end that has the same or better functionality of uTorrent that just uses GTK+ 2 so that it can be kept very lightweight.

My thought on this would be that the C BitTorrent library would be something portable for those that are more apt to want to program in C instead of Python. While I have few problems with Python, I keep thinking that Python probably brings some more overhead than a native C implementation, hence my reason for wanting to make said implementation. Having it made portable would also allow for porting to either Windows, *BSD, or OS X.

The reason for having the GTK+ 2 front-end is so that it can be used in fairly light-weight environments such as XFCE (probably not something like Fluxbox or OpenBox, but maybe a port can be made???) and similar environment. 

I'd prefer to keep the builds for both of them as portable as possible and also as lightweight as possible (I am looking to hopefully build something as small and as light as uTorrent, which I find to be an *awesome* application), so I want to emulate (as in create something like or better) this application and hopefully make it something that could be included natively in something like Xubuntu or even GNOME itself.

So what do you all think? Grandiose idea, possible, impossible, etc???

If I were to make an attempt to port the BitTorrent library to do this, would anyone be able to help, or would this be a futile attempt?
[/SIZE]

---

### Post by duff on 2007-02-28
C++ version --> [http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)

---

### Post by Benitez on 2007-02-28
> **duff said:**
> C++ version --> [http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)
[SIZE="3"]
Not exactly what I was looking for but I guess I'll work with what I can get. I can probably port libtorrent from C++ to plain ol' C and then go on from there...

Anyone else got any ideas or opinions??
[/SIZE]

---

### Post by Benitez on 2007-03-03
[SIZE="3"]
Okay, so I have looked at some of the code for libtorrent. I don't like it; it is quite confusing to me, but that is likely due to me not understanding much of it.

I have also read some of the specification and all that. I think I also require a written library to do SHA-1 encoding and decoding.

So, does anyone that has done some hacking on the libtorrent library know where I should start??? I am a 'programmer' equivalent to a second-year college student at a mediocre college if anyone wants to know my programming experience.

Seriously though, I would like to work on a project like this but I could use some guidance. Again, I will be programming this in **C**, not C++ or Objective-C or any other dialect. Just plain old **C**.

Or am I going about this the wrong way? If so, please feel free to tell me also.
[/SIZE]

---

### Post by lnostdal on 2007-03-03
well to me the extra overhead of using python in the original implementation is a none-issue

but if you need this; go ahead .. if others need this (i don't know); go ahead 

know what would trump this though? a python-compiler that compiles to native optimized machine-code .. this way you'd get a faster original bittorrent-implementation + many other things written in python would go faster automatically :)

---

