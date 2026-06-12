---
title: "Does XMMS work with 8.04?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by MUNDO5555 on 2008-04-27
HI i am really new to linux and i've gotten around ok so far.  A friend told me xmms is like winamp and i'd like to try it out.  i installed xmms2 through synaptic but it does not show up anywhere?  i poked around and xmms website says it does not work with gtk+2.  i saw some gtk2 stuff installed on my computer in synaptic.  does this mean xmms does not work with 8.04?

---

### Post by reyhan on 2008-04-27
XMMS work fine with 8.04...
i just finished upgrade to Ubuntu 8.04 on my other computer 
and its work fine....

---

### Post by MUNDO5555 on 2008-04-27
ok i guess that means im missing something or doing something wrong.  i will have a go at it again.

---

### Post by reyhan on 2008-04-27
but maybe if you install fresh 
Ubuntu theres no XMMS

---

### Post by natrixgli on 2008-04-27
I recommend audacious as it's in the repositories and very similar. It works with Streamtuner, too.


```
sudo apt-get install audacious
```

---

### Post by PinkFloyd102489 on 2008-04-27
I had to compile XMMS from source. I hated XMMS2, since it was essentially MPD with a different name and crappy frontends.

I still use the original XMMS too.

---

### Post by semjaza on 2008-07-03
I've tried to create a package here:  [http://www.ungab.com/content/xmms-ubuntu-804-hardy-heron]("http://www.ungab.com/content/xmms-ubuntu-804-hardy-heron")

I've also linked to the page that explains how to install from source and another attempt at making a Ubuntu 8.04 package.  Hope this helps. :)

---

### Post by stchman on 2008-07-03
> **MUNDO5555 said:**
> HI i am really new to linux and i've gotten around ok so far.  A friend told me xmms is like winamp and i'd like to try it out.  i installed xmms2 through synaptic but it does not show up anywhere?  i poked around and xmms website says it does not work with gtk+2.  i saw some gtk2 stuff installed on my computer in synaptic.  does this mean xmms does not work with 8.04?

Yes audacious is a direct replacement for XMMS.  All the skins and everything work as well.

---

### Post by aktiwers on 2008-07-03
I still like XMMS better than audacious.

In Hardy they removed it from the repos, so you need to compile it yourself.

here we go:
[http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html](http://blog.sartek.net/2008/04/install-xmms-on-ubuntu-804-hardy-heron.html)

---

### Post by bluepowder7 on 2008-07-03
there's debs of xmms for hardy, in both i386 and amd64 versions.

i386:
[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

amd64:
[https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2)

---

### Post by rburkartjo on 2008-07-04
blue, tks for the link on installing xmms in hardy. when i upgrade to 8.04 xmms was gone and i tried different links to try to download. the one you posted worked great. used the deb/cheesemaker

---

### Post by Mr.Auer on 2008-08-24
Im really sad that XMMS was removed from official repos.
It is still, over 10 years after its inception, the only player that consistently works on all my computers, old and new, and is consistently stable. Audacious is not. It will not run without skipping on my Eee pc, for example. XMMS will, and its also very light on resources. Only thing I could complain about it is its ugly menus - but who cares when it works :)

Does anyone know WHY XMMS was removed? I originally made a bug report of this in, I think Gutsy? Or was Edgy the first one to drop it?

But hey, thanks for the precompiled amd64/i386..Now I dont have to compile it myself for all my different arch boxes :)

---

### Post by Malta paul on 2008-08-24
The original version of XMMS dose not work with 8.04, but an updated version of the original dose. (I don't mean XMMS2)
Here is the link:
[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

Works good for me :)

---

