---
title: "[SOLVED] DVD Ripper/shockwave"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Homelinux on 2008-08-17
am in need of a good dvd ripper, i have tried a lot on my windows pc and one worked really well but know it is like my computer decided to not let it work any more.Was using the [[COLOR="Blue"]"Free DVD Ripper 2.25"[/COLOR]]("http://www.freewarezoom.com/archives/free-dvd-ripper") can any one suggest a good one? I heard of _acidrip_ is that any good? I moved my dvd burner over to my Ubuntu pc today so any help would be great.also is there any way to install shockwave on to Ubuntu? i am trying to get the [[COLOR="Blue"]youtube interface[/COLOR]]("http://bibasoftware.com/?page_id=31") installed and it installed fine but it says i need shockwave controller installed. Was able to install youtube interface through wine.

---

### Post by pi.boy.travis on 2008-08-17
I use Thoggen for ripping DVD's.  It's in the repositories.  You can install it via add/remove or synaptic.

---

### Post by anjilslaire on 2008-08-17
Also, if you need something to get past the newer DVD encryption schemes, DVDFab HD Decrypter under wine works perfectly. Once it's on your hard drive, you can do what you want with the files
[http://www.dvdfab.com/free.htm]("http://www.dvdfab.com/free.htm")

---

### Post by pi.boy.travis on 2008-08-17
One more thing on DVD ripping, make sure you have these packages installed:

```
libdvdnav4
libdvdread3
```

And if you need encrypted DVDs run:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Hope this helps!

---

### Post by petedct on 2008-08-17
k9copy has worked well for me. It's in the repos as well.

---

### Post by Homelinux on 2008-08-17
thankyou guys i will try them all and see what works now i just need my shockwave problem resolved and i am good. off course my next issue to be solved is my server question. whitch i will post tomorrow.

---

### Post by pi.boy.travis on 2008-08-17
I don't know too much about adobe stuff, but did you try the proprietary flash plugin listed in synaptic?

---

### Post by mcduck on 2008-08-18
If it really is asking for Shockwave (not Shockwave Flash) there is not much you can do. Macromedia never releaed a Shockwave plugin for Linux, and it doesn't look like Adobe is planning to do that either.

Well, I suppose you *could* use Wine to run a Windows browser + Shockwave.

---

### Post by petronell on 2008-08-18
dvd:rip

it's in the repositories.

daveR

---

### Post by rohedin on 2008-08-18
Shockwave is a tricky bugger to get working under Linux. The only way I've ever done it is by downloading FireFox for Windows and then running that under Wine, then install shockwave inside it.

 The problem is that a lot of the time it crashes and fails hopelessly. It's really down to luck whether certain shockwave applets run. However one thing to note is that I got a higher success rate when I used FireFox 2. I don't know whether it was FF2 or just an older version of shockwave that did it, but I managed to get iSketch to work.


Good luck anyway.

---

### Post by skiddly on 2008-11-04
> **petedct said:**
> k9copy has worked well for me. It's in the repos as well.

i just looked in the add remove and cant see k9 copy or is it only for kubuntu sorry im a newbie

---

### Post by skiddly on 2008-11-04
> **pi.boy.travis said:**
> I use Thoggen for ripping DVD's.  It's in the repositories.  You can install it via add/remove or synaptic.

im installing thogen to try ripping once ive mastered that what do i use to burn to disc so it will play on normal dvd player thanks colcol

---

### Post by pi.boy.travis on 2008-11-05
I use DeVeDe to make video DVDs.  It's in the repos.

---

