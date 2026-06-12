---
title: "Do newer Ubuntu releases lose capability?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by benali72 on 2008-07-27
Please forgive a naive question, but I've tried both 6.06 and 8.04 on about a dozen older PCs and laptops (single-core P-IVs, P-IIIs and Celerons.)

I've found that 6.06 installs BETTER on many of them than 8.04.

(By "better", I mean 6.06 recognizes devices properly or more accurately.)

For example, the machine I'm composing this post on is a P-III Toshiba laptop.  6.06 correctly recognizes its screen and gives it a resolution of 1024 by 768, while 8.04 only offers a max screen resolution of 800 by 600.

Why would 6.06 install better on some systems than 8.04?

Is device-recognition code actually removed from Ubuntu as it is evolved into new releases?

Thank you for your feedback.

---

### Post by Joeb454 on 2008-07-27
I don't think so. I think it's just that 8.04 is designed for a PC's which are a little newer.

Of course you could do a minimal install, which may allow you to install 8.04 on older PC's (as I think it may be a hardware issue)

---

### Post by kamitsukai on 2008-07-27
well 8.04 is probably better suited to newer machines as it contains drivers for newer hardware were as 6.06 would have better support for older hardware as it is an older release..

at least this is my understanding

---

### Post by davidsrsb on 2008-07-27
The Linux kernel does drop support for old hardware that does not have a maintainer, but this in practice means at least 10 years plus or really rare devices

---

### Post by benali72 on 2008-07-27
It appears to me that the developers have to yank out older code in order to keep the size of the produce reasonable... which probably works great for most people.  

But since I'm working with older machines, it's a bit disturbing to find that an older Ubuntu release sometimes works better than a newer one.

I think going forward I'll try 8.04 on a machine first, and if it doesn't recognize devices properly, use 6.06 as my fallback.

That way each machine will get the newest release of Ubuntu it can easily handle.

(I'll simplify the situation by excluding 7.x).

Thanks.

---

### Post by txcrackers on 2008-07-27
> **benali72 said:**
> But since I'm working with older machines, it's a bit disturbing to find that an older Ubuntu release sometimes works better than a newer one.

Try installing Vista on one of them for a bit of perspective. ;)

---

### Post by Methuselah on 2008-07-27
I think graphics drivers and X are the main culprit.
As far as I know, some changes took place even between Gutsy and Hardy.
For example, the screen and graphics menu item was removed yet it didn't configure itself to my widescreen resolutions.
For many people, it woun't be obvious how to fix it with the menu item gome.

---

### Post by benali72 on 2008-07-28
Thanks for the idea.  I did some more testing, and I think you're right... the graphics drivers and X appear to be what has changed.

With the Toshiba laptop example I gave above, I found that---

6.06 -- boots great
7.10 -- hangs during boot (apparently due to screen graphics problem)
8.04 -- boots (but gives incorrect screen resolution of 800 x 600) 

I found if the Toshiba fails to boot due to screen problems, if I copy a valid xorg.conf file into /etc/X11, it works fine.  Problem solved!  Thank you for the help.

---

### Post by Methuselah on 2008-07-28
Great!

Basically, many distros are shipping newer X without xorg.conf because it's *supposed* to configure itself on startup. 

Unfortunately, it frequently doesn't and I had to generate an xorg.conf to get proper resolutions as well.

Luckily, the one spit out by **X -configure** worked fine for me.

---

### Post by CatKiller on 2008-07-28
Lots of the old infrastructure wasn't really extensible to the new ways that people are using hardware. For example, hot-plug support for displays and roaming networking profiles for wireless networking. These all had to be changed in fairly fundamental ways to put in the new functionality. This is obviously an ongoing process.

As such, the methods that were sufficient for automatic configuration for the old uses were also changed.

6.06 LTS will still get security updates till next summer, so if that works better for you there is no reason not to use it. Hopefully, by the time you need to upgrade, the improvements will have matured sufficiently for your hardware to work as it should. Otherwise, as you've found, it is still possible to configure the hardware using the old methods.

---

### Post by billgoldberg on 2008-07-28
> **kamitsukai said:**
> well 8.04 is probably better suited to newer machines as it contains drivers for newer hardware were as 6.06 would have better support for older hardware as it is an older release..

at least this is my understanding

8.04 should have better driver support than 6.06 (newer kernel).

Like the op said, xorg was to blame.

---

### Post by Sef on 2008-07-28
> 6.06 LTS will still get security updates till next summer

For the desktop, the Long Term Support runs out in June 2009, while for the server it runs out in June 2011.

---

