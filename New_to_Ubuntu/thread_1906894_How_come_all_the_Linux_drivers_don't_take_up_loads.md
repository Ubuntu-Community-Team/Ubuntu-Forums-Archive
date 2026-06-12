---
title: "How come all the Linux drivers don't take up loads of space?"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by androssofer on 2012-01-10
this has bugged me for a while. 

so you get Ubuntu, or Linux in general.. install it, and it works, then plug in a device... it works..

those drivers must come from somewhere.. do they not take loads of space? because there is alot of devices that 'just work'

i know you can download additional drivers etc, but it always works before that...

what kind of black magic is this!?

---

### Post by TeoBigusGeekus on 2012-01-10
Open source -> Different programs can use shared libraries.
The same piece of software that's half a gig in windows could be just 100mb or less in linux.

---

### Post by mastablasta on 2012-01-10
> **TeoBigusGeekus said:**
> Open source -> Different programs can use shared libraries.
The same piece of software that's half a gig in windows could be just 100mb or less in linux.
 
that's one part. the downside is that libraries upgrade on system upgrade or change and then can then become incompatible with only some software (as they are shared). this can be a nightmare. as you have to go hunting for old libraries if you can find them. and then when you do there is a chance they will not want to coexists with the new ones. common user doesn't see the issue here. developers might.
 
another thing is that Kernel itself has drivers build in. they are often generic and work with most things but sometimes they don't if hardware is a bit more specific.
 
windows also has drivers for most things but it is prefered to use the ones provided by manufacturers for plenty of devices. as they are better and often updated, pathced...they would also provide new libraries, since they don't know what libraries you are using. and since maybe another programme uses the old libraries. so they will be a bit fatter package.
 
a similar way of dealing with libraries is also found in PC-BSD i believe.

---

### Post by mike555 on 2012-01-10
Also on Windows when you load a "driver" from a cd you end up with extra junk programs you may not want ,and they take up room.

---

### Post by mastablasta on 2012-01-10
that happens if you use autorun function and use that installer, but if you browse directly to the driver .exe file this will not/should not happen.

---

