---
title: "Where is Strict Version (ex: 22.04.1 not 22.04.2)"
date: 2023-08-05
forum: New to Ubuntu
---

### Post by stakano on 2023-08-05
Hi,

I need ubuntu 22.04.1, not 22.04.2 in order to use particular software which does not support 22.04.2.
I see the download site including local region server, but could not see the version.
Not only 22.04, other versions are also newest versions (ex; only shows 20.04.6).

Where is such the intermediate versions?

Best,
stakano

---

### Post by TheFu on 2023-08-05
Canonical changed their support for .x releases about 5 yrs ago if the HWE is used.  The kernel versions in the .1, .2, .3, .4 releases which map to non-LTS kernels have support until the next .release comes out, about every 6 months.  Let me find a webpage that helps explain.
[https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle](https://ubuntu.com/about/release-cycle#ubuntu-kernel-release-cycle)  They call it HWE Rolling Release.

Or did I misunderstand?

---

### Post by stakano on 2023-08-05
Hi,

The software has a license which checks OS (kernel) version.
I have tried to install the software to 22.04.2, but it did not run.

Best,
stakano

---

### Post by TheFu on 2023-08-05
How are those checked performed?  If they use **lsb_release -d**, you can manually change that.
OTOH, if they are truly dependent on specific library versions, in theory, library versions shouldn't change within a single release, except in the 3rd level.

libfoo.x.y.z.so    So, only "z" should change in a release, never x or y numbers.  z relates to bug fixes, not API changes or functional changes. Should be fine.  That's the goal by programmers.


I suppose we can't really chat about getting around license restrictions here. I'll stop now.

I checked my local Ubuntu Mirror (GA Tech) for 22.04.1 and they have 22.04 and 22.04.2 as well.  Hummmm.

My archive server had a HDD failure a few weeks ago.  I need to see what killed it and may have a 22.04.1 server ISO somewhere. If I do, I can get you a wormhole link to grab it.  If I don't have it, someone in my LUG probably does, somewhere.  We use wormhole to exchange files, so if you attend the LUG meeting tomorrow and ask, someone may have it.  

Regardless, you'll want to get wormhole setup.  
[https://www.omgubuntu.co.uk/2017/06/wormhole-fast-secure-way-send-files-users-cli](https://www.omgubuntu.co.uk/2017/06/wormhole-fast-secure-way-send-files-users-cli)
[https://magic-wormhole.readthedocs.io/en/latest/file-transfer-protocol.html](https://magic-wormhole.readthedocs.io/en/latest/file-transfer-protocol.html)

It will take me some time to physically move some HDDs around. Check back in an hour.

---

### Post by stakano on 2023-08-05
Oh, I appliciate your kindness!

Best,
stakano

---

### Post by TheFu on 2023-08-05
Found this: ubuntu-22.04.1-live-server-amd64.iso, but it is on a disk array that could fail. Let me move it somewhere else and I'll PM you with the wormhole receive stuff in a bit.

---

### Post by donald187 on 2023-08-05
There's also this.

[http://old-releases.ubuntu.com/releases/jammy/](http://old-releases.ubuntu.com/releases/jammy/)

Scroll down to 22.04.1.

---

### Post by TheFu on 2023-08-05
> **donald187 said:**
> There's also this.

[http://old-releases.ubuntu.com/releases/jammy/](http://old-releases.ubuntu.com/releases/jammy/)

Scroll down to 22.04.1.

Getting it from that link is 1000x better than getting it from some guy over the internet.  Get it there.   I'm killing my **wormhole send**, so ignore the PM.

---

### Post by stakano on 2023-08-06
Hi donald187-san,

Thank you for your imformation, I found it and could install.

Best,
stakano

---

### Post by stakano on 2023-08-06
Hi TheFu-san,

Thank you very much for your kindness, have a nice weekend!

Best,
stakano

---

### Post by TheFu on 2023-08-06
stakano-san, 

Yoi sh&#363;matsu o osugoshi kudasai. Watashi wa s&#363;-nenkan T&#333;ky&#333; de danzoku-teki ni hataraite imashitaga, nihongo o hanasu koto o mananda

---

### Post by donald187 on 2023-08-06
> **stakano said:**
> Hi donald187-san,

Thank you for your imformation, I found it and could install.

Best,
stakano

Glad I could help. :)

---

