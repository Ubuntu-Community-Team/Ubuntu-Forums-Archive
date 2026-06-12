---
title: "Why does my 4gb of ram show up as 3?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-05-31
So I got this new laptop and it has 4 gb of ram in it, but ubuntu only recognizes it as 3gb. What's up with that?

---

### Post by knavarathna92 on 2008-05-31
are you running 64 bit or 32 bit?

---

### Post by mgranet on 2008-05-31
32 bit systems can only handle 4GB TOTAL; i.e., including video card memory and the like. As you have other memory in the system, this detracts from the 4GB total. If you have a 64 bit proc, you will need to install the 64bit version of the Ubuntus to utilize all your RAM.

---

### Post by CryptiniteDemon on 2008-05-31
Well crap.  I installed 32 bit because I wanted to keep it in sync more easily with my desktop system.  I spent 3 hours doing all my customizations for it.  So the question comes down to do I feel like reinstalling for an extra gig of memory I'll never actually use?  I mean I rarely go over even 1 gig running a bunch of virtual machines.

---

### Post by shifty_powers on 2008-05-31
think you've answered your own question there ;)

---

### Post by stalkier on 2008-05-31
> **CryptiniteDemon said:**
> Well crap.  I installed 32 bit because I wanted to keep it in sync more easily with my desktop system.  I spent 3 hours doing all my customizations for it.  So the question comes down to do I feel like reinstalling for an extra gig of memory I'll never actually use?  I mean I rarely go over even 1 gig running a bunch of virtual machines.

I know what you mean. Is it really worth it? Only you can answer that. Personally I am looking forward to receiving my 1 GB DDR in a few days to make 1.5GB.

---

### Post by Mentem on 2008-05-31
If it makes you feel any better

1) you will probably have to reinstall sooner or later

2) since you've already done the configuration, the next time you do it, it goes alot faster

---

### Post by forestpixie on 2008-05-31
> **Mentem said:**
> If it makes you feel any better

1) you will probably have to reinstall sooner or later

2) since you've already done the configuration, the next time you do it, it goes alot faster

Can you use config files for 32bit apps in a 64 bit system? More a real question than rhetorical one :)

---

### Post by shae on 2008-05-31
You could recompile your kernel to enable support for memory over 4GB.

---

### Post by Joeb454 on 2008-05-31
To be totally honest - until the OP is ready to use 64 bit, then I don't see the point of installing it. When are you ever going to use over 3GB RAM on Ubuntu?

---

