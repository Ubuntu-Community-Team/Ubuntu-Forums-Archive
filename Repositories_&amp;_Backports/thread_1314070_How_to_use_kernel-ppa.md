---
title: "How to use kernel-ppa?"
date: 2009-11-04
forum: Repositories &amp; Backports
---

### Post by martin_lindhe on 2009-11-04
Hello

I am trying to setup and use kernel-ppa from [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

so that i can install the kernel 2.6.32-rc6 from the ppa into my Karmic installation.

I see that this kernel is compiled and exists in [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc6/)


However i cannot get the ppa to work.

according to the ppa page, i should add:

"deb [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main"

this give me a 404-file not found.

I replaced lucid with karmic and get another 404.

By looking at the directory-structure I see only hardy & intrepid listed.
So i am wondering, how can I use this ppa to install a working kernel?

I also tried using 

"deb [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) intrepid main"

PS- I know how to manually download the .deb files and install em. I am not asking about that, i am asking about the PPA.

---

### Post by daveshep on 2009-11-12
yeah good question mate, i'm pretty keen to see an answer to this one!

---

### Post by ambrish7 on 2009-11-12
Hello Every Budy
Good morning all of you;

please tell me { How to enable wireless lan card in ubuntu os}

---

### Post by VladNistor on 2009-11-15
That PPA appears to be empty, and the apt line should be 
deb [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main

Get them from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by Juzz on 2010-02-08
I can't see the ppa for neither karmic nor lucid :/

Is there a reason for this? Do you have to use something else?

---

### Post by kenjiru on 2010-02-27
I get the same message:
```

Failed to fetch http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by babyhuey on 2010-03-01
Do those kernels in the ppa have standard Ubuntu patches applied or are they vanilla?

---

### Post by DouglasAWh on 2010-03-30
Any news?

---

### Post by The Pixel Developer on 2010-04-14
[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

---

### Post by BrokeMahPC on 2010-04-27
That link worked for me - you have to include the all.deb!
So you need 3 files.

---

### Post by mohiter4 on 2011-02-11
> **martin_lindhe said:**
> Hello

I am trying to setup and use kernel-ppa from [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

so that i can install the kernel 2.6.32-rc6 from the ppa into my Karmic installation.

I see that this kernel is compiled and exists in [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc6/)


However i cannot get the ppa to work.

according to the ppa page, i should add:

"deb [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) lucid main"

this give me a 404-file not found.

I replaced lucid with karmic and get another 404.

By looking at the directory-structure I see only hardy & intrepid listed.
So i am wondering, how can I use this ppa to install a working kernel?

I also tried using 

"deb [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) intrepid main"

PS- I know how to manually download the .deb files and install em. I am not asking about that, i am asking about the PPA.
@martin: the ppa that you should use is "ppa:kernel-ppa/ppa", refer this link [http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa](http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa).

---

