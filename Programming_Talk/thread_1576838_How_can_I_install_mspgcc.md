---
title: "How can I install mspgcc?"
date: 2010-09-17
forum: Programming Talk
---

### Post by Kdar on 2010-09-17
Does anyone know if there is a tutorial somewhere on how to install mspgcc?

---

### Post by GregBrannon on 2010-09-17
Does this help?

[http://www.scribd.com/doc/219845/msp430-mspgcc-eclipse-ubuntu-tutorial]("http://www.scribd.com/doc/219845/msp430-mspgcc-eclipse-ubuntu-tutorial")

---

### Post by MadCow108 on 2010-09-18
here's a ppa:
[https://launchpad.net/~adamhorden/+archive/msp430](https://launchpad.net/~adamhorden/+archive/msp430)

---

### Post by Kdar on 2010-09-18
oh great. I didn't know there was ppa for this. Makes it so much easier!

seems like this ppa is not working, at least my ubuntu can't connect to it now.

---

### Post by Kdar on 2010-09-18
Here what I get:
```
W: Failed to fetch http://ppa.launchpad.net/adamhorden/msp430/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found


```

---

### Post by MadCow108 on 2010-09-18
the ppa is only for karmic and jaunty
but it should also work in lucid so do not replace the karmic/jaunty with lucid in the sources list.

If not you could still use the package to build from source
I helped somebody at university installing this shortly ago, I'll ask him if there where any problems on monday.

---

### Post by Kdar on 2010-09-18
it worked when I changed from lucid to jaunty. thanks

---

### Post by Kdar on 2010-09-19
Now I just need to figure out how to use it in IDE.

---

### Post by Tim5924 on 2010-11-10
> **GregBrannon said:**
> Does this help?

[http://www.scribd.com/doc/219845/msp430-mspgcc-eclipse-ubuntu-tutorial](http://www.scribd.com/doc/219845/msp430-mspgcc-eclipse-ubuntu-tutorial)
The files referred to by the article in the *Linux Journal  *in the above URL are so old (2003).  Are they any good?

---

### Post by Tim5924 on 2010-11-10
> **Kdar said:**
> it worked when I changed from lucid to jaunty. thanks
I am running Maverick, 64 bit.  I am getting similar errors about nonexistent repositories, despite declaring correct sources: 

deb [http://ppa.launchpad.net/adamhorden/msp430/ubuntu](http://ppa.launchpad.net/adamhorden/msp430/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/adamhorden/msp430/ubuntu](http://ppa.launchpad.net/adamhorden/msp430/ubuntu) jaunty main

(Same errors with "karmic" instead of "jaunty.")

W: Failed to fetch [http://ppa.launchpad.net/adamhorden/msp430/ubuntu/dists/jaunty/main/source/Sources.gz](http://ppa.launchpad.net/adamhorden/msp430/ubuntu/dists/jaunty/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/adamhorden/msp430/ubuntu/dists/jaunty/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/adamhorden/msp430/ubuntu/dists/jaunty/main/binary-amd64/Packages.gz)  404  Not Found

---

### Post by wkhasintha on 2010-11-11
it worked for me. much thanx

---

### Post by MadCow108 on 2010-11-11
> **Tim5924 said:**
> I am running Maverick, 64 bit.  I am getting similar errors about nonexistent repositories, despite declaring correct sources: 

deb [http://ppa.launchpad.net/adamhorden/msp430/ubuntu](http://ppa.launchpad.net/adamhorden/msp430/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/adamhorden/msp430/ubuntu](http://ppa.launchpad.net/adamhorden/msp430/ubuntu) jaunty main

(Same errors with "karmic" instead of "jaunty.")

W: Failed to fetch [http://ppa.launchpad.net/adamhorden/msp430/ubuntu/dists/jaunty/main/source/Sources.gz](http://ppa.launchpad.net/adamhorden/msp430/ubuntu/dists/jaunty/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/adamhorden/msp430/ubuntu/dists/jaunty/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/adamhorden/msp430/ubuntu/dists/jaunty/main/binary-amd64/Packages.gz)  404  Not Found

the ppa has changed to mspgcc4 ([http://mspgcc4.sourceforge.net/):](http://mspgcc4.sourceforge.net/):)
[https://launchpad.net/~msp430-development-daily/+archive/development-builds](https://launchpad.net/~msp430-development-daily/+archive/development-builds)

---

