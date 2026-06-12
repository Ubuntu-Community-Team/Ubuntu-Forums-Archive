---
title: "64 bit running 32 bit apps"
date: 2010-08-31
forum: Recurring Discussions
---

### Post by Cityscape on 2010-08-31
Hi Guys. I am considering switching to 64 bit Ubuntu but a lot of programs are only available in 32 bit. Can 64 bit Ubuntu run all the 32 programs like 64 bit Windows can?

---

### Post by lukeiamyourfather on 2010-08-31
> **Cityscape said:**
> I am considering switching to 64 bit Ubuntu but a lot of programs are only available in 32 bit.


Like what? Almost everything is available as native 64-bit except for Flash.

> **Cityscape said:**
> 
Can 64 bit Ubuntu run all the 32 programs like 64 bit Windows can?

Yes, but with a few caveats.

---

### Post by Cityscape on 2010-08-31
Example: Picasa is not available for 64 bit. So most 32 bit linux programs will fine on 64 bit Linux?

And then what to do about Adobe flash player?

---

### Post by scorp123 on 2010-08-31
> **Cityscape said:**
> So most 32 bit linux programs will fine on 64 bit Linux? In 99.99% of the time yes. There are a few odd programs that behave a bit strange. Adobe Flash is one of them. But usually you don't have to bother about this. The vast majority of all the apps simply work and you won't really notice a big difference ... except maybe that with 64-bit things go a bit faster ... That's because 64-bit OS can handle and manage far more memory; therefore there is a bit of a performance gain when it comes to I/O and cacheing ... everything feels a slight bit faster than before.

> **Cityscape said:**
>  And then what to do about Adobe flash player? That one runs inside a 32-bit compatibility wrapper. Installation used to be complicated and you needed to configure things manually ... not anymore though. If you want Adobe Flash you just configure your system to get all the needed plugins from the Medibuntu repository and then everything is automagically configured for you.

Just be warned that Adobe Flash sometimes may hang, or crash your browser. But other than that I can't think of any negative side effects :)

---

### Post by Cityscape on 2010-08-31
scorp123: Thanks a lot! That's exactly what I needed to know. :)

---

### Post by Crempel on 2010-08-31
I am running Lucid 64-bit and have no problems with either picasa or flash. The latter I got thru synaptic, and picasa is a Windows program that runs under a special version of wine, provided by google with picasa. I even got the latest picasa 3.8 installed and working, which is not yet available for Linux. There is a good instruction re how to do this (installing 3.0 first and then updating using the .exe file); sorry I don't remember the URL, but if you google around (picasa for Linux etc) you're bound to find it.

---

### Post by rewyllys on 2010-08-31
> **Crempel said:**
> I am running Lucid 64-bit and have no problems with either picasa or flash. The latter I got thru synaptic, and picasa is a Windows program that runs under a special version of wine, provided by google with picasa. I even got the latest picasa 3.8 installed and working, which is not yet available for Linux. There is a good instruction re how to do this (installing 3.0 first and then updating using the .exe file); sorry I don't remember the URL, but if you google around (picasa for Linux etc) you're bound to find it.

I suspect the instruction you're thinking of is:

[http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html](http://www.webupd8.org/2010/04/how-to-install-picasa-36-in-ubuntu.html)

---

### Post by tgm4883 on 2010-08-31
> **Cityscape said:**
> Example: Picasa is not available for 64 bit.


Please don't spread FUD.

[http://picasa.google.com/linux/download.html#picasa30](http://picasa.google.com/linux/download.html#picasa30)

---

### Post by lukeiamyourfather on 2010-09-01
> **tgm4883 said:**
> Please don't spread FUD.

[http://picasa.google.com/linux/download.html#picasa30](http://picasa.google.com/linux/download.html#picasa30)

Technically Picasa is only 32-bit, even the amd64 package.

[http://picasa.google.com/linux/faq.html#2](http://picasa.google.com/linux/faq.html#2)

Though it'll still work fine on a 64-bit system.

---

### Post by Perfect Storm on 2010-09-01
If you're running into a 32-bit application (most likely a close source app) install **ia32-libs** package and you're ready.

---

### Post by tgm4883 on 2010-09-01
> **lukeiamyourfather said:**
> Technically Picasa is only 32-bit, even the amd64 package.

[http://picasa.google.com/linux/faq.html#2](http://picasa.google.com/linux/faq.html#2)

Though it'll still work fine on a 64-bit system.

Your a letter of the law instead of spirit of the law type of person aren't you ;)

Re-read the statement. 

> Example: Picasa is not available for 64 bit.

Last I checked, providing a amd64 deb is making it available for 64-bit. Had they provided a 32-bit only deb that didn't work on 64-bit machines, I would have agreed with you.

---

### Post by Jazzy_Jeff on 2010-09-01
> **tgm4883 said:**
> Your a letter of the law instead of spirit of the law type of person aren't you ;)

Re-read the statement. 



Last I checked, providing a amd64 deb is making it available for 64-bit. Had they provided a 32-bit only deb that didn't work on 64-bit machines, I would have agreed with you.

So what? Is this worth arguing over?

---

### Post by tgm4883 on 2010-09-01
> **Jazzy_Jeff said:**
> So what? Is this worth arguing over?

Actually yea, if someone calls me out don't I have the right to defend my statement?

---

### Post by lukeiamyourfather on 2010-09-01
> **tgm4883 said:**
> Actually yea, if someone calls me out don't I have the right to defend my statement?

Not arguing, just pointing out the statement isn't entirely FUD like you had mentioned previously because Picasa ***is*** 32-bit. There's some truth behind it which is possibly what led the original poster to believe it might not work on a 64-bit system. We're all on the same page knowing Picasa will work on a 64-bit Linux system. 8-[

---

### Post by tgm4883 on 2010-09-01
> **lukeiamyourfather said:**
> Not arguing, just pointing out the statement isn't entirely FUD like you had mentioned previously because Picasa ***is*** 32-bit. There's some truth behind it which is possibly what led the original poster to believe it might not work on a 64-bit system. We're all on the same page knowing Picasa will work on a 64-bit Linux system. 8-[

If you look at the installation of Picasa, you will notice that it actually is the windows version shipped with its own version of wine. Shouldn't we also say that Picasa isn't available for 32-bit Linux?

---

### Post by philinux on 2010-09-01
Moved to Recurring.

---

### Post by lukeiamyourfather on 2010-09-01
> **tgm4883 said:**
> If you look at the installation of Picasa, you will notice that it actually is the windows version shipped with its own version of wine. Shouldn't we also say that Picasa isn't available for 32-bit Linux?

I guess so. As long as you also say it still works with 32-bit and 64-bit Linux! :lol:

---

### Post by tgm4883 on 2010-09-01
> **lukeiamyourfather said:**
> I guess so. As long as you also say it still works with 32-bit and 64-bit Linux! :lol:

Wow, really? What's next, Amarok isn't available for Ubuntu because it's a QT app?

---

### Post by formaldehyde_spoon on 2010-09-01
> **lukeiamyourfather said:**
> Like what? Almost everything is available as native 64-bit except for Flash.<br/>...
Flash is still available for 64 bit, you just can't download it from Adobe.

---

### Post by lukeiamyourfather on 2010-09-02
> **tgm4883 said:**
> Wow, really? What's next, Amarok isn't available for Ubuntu because it's a QT app?

You're missing the point. :roll:

---

### Post by tgm4883 on 2010-09-02
> **lukeiamyourfather said:**
> You're missing the point. :roll:

Then point it out for me :)

---

### Post by Perfect Storm on 2010-09-02
Please take that discussion to PM, thanks.


regards
A.I. Dude
Ubuntu Forum Staff

---

