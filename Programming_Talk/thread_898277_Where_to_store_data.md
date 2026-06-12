---
title: "Where to store data?"
date: 2008-08-23
forum: Programming Talk
---

### Post by jomiolto on 2008-08-23
Where should my applications generally store their data? Should I use */usr/share* or perhaps */usr/local/share*? (I don't quite understand the difference between the two of them :confused: and I've seen both used by various applications, although */usr/share* seems to be more common, at least on Ubuntu).

What about images and documentation? Can I store them on the same directory as other data, or should I use something like */usr/share/pixmaps* and */usr/share/doc* (as some applications seem to do).

I'm wondering if there's some kind of an etiquette on these things, and whether it will cause people trouble if I pick the wrong directory -- or can I just use which ever directory seems convenient to me? (I know about the Unix Filesystem Hierarchy, but it doesn't seem to answer all the questions, nor does it say much about the difference between */usr/share* and */usr/local/share*).

Thanks in advance and apologies if this has been asked before -- I couldn't find anything past the filesystem hierarchy thing when I tried to search for an answer to this.

---

### Post by jinksys on 2008-08-23
Since ubuntu conforms to the Linux Standard Base (LSB), that is where I would look.  It says, 

> 
From: [LSB Website](http://refspecs.linux-foundation.org/LSB_3.2.0/LSB-Core-generic/LSB-Core-generic/execenvfhs.html)

An LSB conforming application shall conform to the Filesystem Hierarchy Standard.


The current Filesystem Hierarchy Standard the LSB uses, [here](http://www.pathname.com/fhs/pub/fhs-2.3.html).

---

### Post by jomiolto on 2008-08-23
> **jinksys said:**
> The current Filesystem Hierarchy Standard the LSB uses, [here](http://www.pathname.com/fhs/pub/fhs-2.3.html).

Thanks, but that is exactly the Filesystem Hierarchy I was talking in my post :)

The only thing it mentions about the difference between */usr/share* and */usr/local/share* is this:

> Any program or package which contains or requires data that doesn't need to be modified should store that data in /usr/share (or /usr/local/share, if installed locally).

I don't quiet understand what it means by "installed locally".

Also, that specification mentions nothing about */usr/pixmaps* and says that */usr/share/doc* is "optional", but as I've seen them used by so many applications, I thought there was somekind of a standard or etiquette considering their usage, but I guess not... :confused:

Well, I guess I'm just going to store all the read-only data (pictures, sounds, documentation, etc.) my applications need in */usr/share/application-name/*, and then change it later, if someone complains and gives me a good reason on why the data should be somewhere else. :)

---

### Post by jinksys on 2008-08-23
#-o Oops, must have skipped over that part.

But to answer your question, all your read-only data should go in /usr/share/app-name.  Whatever subdirectories beyond that are up to you, it's your software after all.

---

### Post by CptPicard on 2008-08-23
Isn't the difference between "local" and non-local that non-local stuff "belongs to the distribution" and "local" stuff has been installed from "outside"? I stick everything I compile myself into "local".

You could also imagine a situation where all the usual stuff is mounted off some network drive, and "local" is stuff on the local drive.

---

### Post by jomiolto on 2008-08-23
> **CptPicard said:**
> Isn't the difference between "local" and non-local that non-local stuff "belongs to the distribution" and "local" stuff has been installed from "outside"? I stick everything I compile myself into "local".

That actually makes very much sense! Thanks. I wonder how I never thought of that -- especially as many (most?) programs I've compiled from source have installed themselves in */usr/local/*. If that's true, then perhaps I should stick my binaries to */usr/local/bin/* too, instead of */usr/bin*...

---

### Post by nvteighen on 2008-08-23
/usr/local is conventionally used for non-distribution system-wide resources so you avoid overwriting a distribution resource by accident.

But, wasn't in principle /opt meant for that?

---

### Post by Sinkingships7 on 2008-08-23
> **nvteighen said:**
> /usr/local is conventionally used for non-distribution system-wide resources so you avoid overwriting a distribution resource by accident.

But, wasn't in principle /opt meant for that?

I use /opt for the OP's purpose.

---

### Post by CptPicard on 2008-08-23
> **nvteighen said:**
> 
But, wasn't in principle /opt meant for that?

/opt is meant for "packages" that entirely have their own subdirectory structure instead of the bin, lib, doc, src, share ... subdivision. Hence I for example usually just unzip the eclipse tarball into /opt.

---

### Post by ad_267 on 2008-08-23
Yeah I haven't really decided which way to go. I have some in /usr/local/share and some in /opt. I think if it comes with it's own installer it usually ends up in /usr/local/share and if it's an an archive I put it in /opt.

---

