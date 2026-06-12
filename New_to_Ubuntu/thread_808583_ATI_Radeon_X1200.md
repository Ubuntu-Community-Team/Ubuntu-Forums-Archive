---
title: "ATI Radeon X1200"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Jaded Misanthrope on 2008-05-26
Could somebody point me in the right direction for getting the drivers for the ATI Radeon X1200 graphics card for Ubuntu? I'm pretty much stuck with it (I'm on a laptop), so any help with getting them would be great. :)

---

### Post by Alex J. on 2008-05-27
Dido. Have you had any luck yet? I'm an ultra newbie and can't find the drivers either. They seem to have every driver listed on the ATI website BUT that one. 

I'm actually posting this from Vista.
**Any help anyone?**:( :( :( :(

---

### Post by squirrelplayingtag on 2008-05-27
It looks like it's the same driver for the x1300 as well. Here are the release notes which lists your card as supported. ([https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_85_linux.html))

The easiest way is through envy in my opinion. In the terminal
```

sudo aptitude install envyng-core

```

Or manually. [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by Alex J. on 2008-05-28
Thanks so much. Works like a charm now, and I have the lovely Compiz stuff. Don't know why they didn't make it clearer what driver it needed on the ATI website. 8)

---

### Post by drkameleon on 2008-05-28
ATI's website (and their drivers as well...) are kinda messed up... :p

---

### Post by oedha on 2008-05-28
> **Jaded Misanthrope said:**
> Could somebody point me in the right direction for getting the drivers for the ATI Radeon X1200 graphics card for Ubuntu? I'm pretty much stuck with it (I'm on a laptop), so any help with getting them would be great. :)

just enable the ATI on system - administration - hardware drivers then reboot
it worked for me on X1250 and RV505 :)

---

### Post by Jaded Misanthrope on 2008-05-28
Hopefully, installing what squirrelplayingtag suggested will work to fix an issue I have been having with running Source games through Wine (I just get a screen with varying colours if I try to start a game; the menu itself is fine, as is sound).

---

### Post by swimstarguy on 2010-02-18
Holy crap, a necropost!!!

I'm having the same issue on the same laptop and didn't want to start a new thread when one was already there. 


The driver that came with the 9.10 CD isn't working properly.
EnvyNG isn't cutting it.
ATI no longer has the driver listed on their site.
System>Administration>Hardware Drivers doesn't have anything listed.

Has this issue been resolved or documented for anyone? I've been searching and searching and I haven't found anything that currently works, all the solutions are outdated and unsupported.

Help? Please? *offers cookies*

---

### Post by Wizard of Cause on 2010-03-06
Hmm...so far, I've gone through the sequences for updating my drivers as listed here and have gone through the steps of getting the necessary ATI config tools in an attempt to get my s-video output working to my LCD tv.

No luck so far. Can anyone help me? I'm running an ATI Radeon x1200 graphics card on a Toshiba laptop. The output worked great with windows, but whenever I aticonfig --initial in Terminal, it says no supported adapters detected.

Help...please? My girlfriend and I need to watch The Office on out flatscreen and now I've gone and converted my OS to this wonderful, yet demanding Ubuntu.

---

### Post by 3rdalbum on 2010-03-07
> **swimstarguy said:**
> Holy crap, a necropost!!!

I'm having the same issue on the same laptop and didn't want to start a new thread when one was already there.

Late in 2008 (after the thread was started), ATI abandoned support for your graphics adapter. There is no longer a Catalyst driver for your graphics adapter (the old one doesn't work on any Ubuntu version after 8.10).

You are stuck with the open-source driver, which is improving but still not quite 'there yet'.

Attempting to install the ATI Catalyst driver with one of these unsupported graphics adapters will usually result in a black screen, so if I were you I wouldn't even try it.

Your LCD TV probably has a VGA input which you could try. It should work with the open driver.

---

### Post by Lowzow on 2010-03-09
What you are saying is that there is no hope to get this videocard installed properly under linux?

It's still working under windows (7) with the x1300 driver.
But here I fail to install it. (newb)

---

### Post by halitech on 2010-03-09
can you turn the laptop and see things on the screen? If you can see things when you turn the laptop on, *A* driver is installed and working properly. It may not be your preferred driver (ATI Catalyst) that will allow you to use TV out but it is working. If you need the tv out option, either drop back to Ubuntu 8.04 where the ATI catalyst driver still works, revert back to windows or learn to program and write a driver yourself are the 3 options I can think of.

---

### Post by Easy Limits on 2010-03-09
I just recently installed 9.10 64 bit  on my Toshiba laptop and the X1200 video card works fine.  I didn't have to look for a driver.

---

### Post by Mark Phelps on 2010-03-10
> **Easy Limits said:**
> I just recently installed 9.10 64 bit  on my Toshiba laptop and the X1200 video card works fine.  I didn't have to look for a driver.

That's because it's using the default open source driver.

My X1600 also works fine in 9.10 -- using the default open source driver.

---

### Post by teledyn on 2010-06-10
> **Mark Phelps said:**
> That's because it's using the default open source driver.

My X1600 also works fine in 9.10 -- using the default open source driver.

in 10.04 the default driver performance is better than in 9.x, but it makes the screen go unusably all wavy on my acer flatscreen.  I think we x1200 are ASOL until the open source driver gets up to speed, and seeing as its an extinct chipset, there's probably not much impetus to get that done.

time to check out the [ZaReason TEO]("http://www.linux-netbook.com/zareason-teo")?

---

### Post by rajeev1204 on 2010-06-10
> **teledyn said:**
> in 10.04 the default driver performance is better than in 9.x, but it makes the screen go unusably all wavy on my acer flatscreen.  I think we x1200 are ASOL until the open source driver gets up to speed, and seeing as its an extinct chipset, there's probably not much impetus to get that done.

time to check out the [ZaReason TEO]("http://www.linux-netbook.com/zareason-teo")?


Very old thread 2 years old, but ill just clarify a few things for those with this chipset.

The x1200 is only supported with the ATI open source drivers and they work really well now.Certain games might not work with them and ubuntu 8.04 is the only way to install ATI proprietary drivers so those who are desperate should stick with 8.04 .

[http://ati.amd.com/products/catalyst/linux.html](http://ati.amd.com/products/catalyst/linux.html)  should answer many of the doubts you have and there are other links in there for more info.

For drivers, [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

---

### Post by Sef on 2010-06-10
Locked Necromancing.  Please start a new thread and provide a link if you want to mention the thread.

---

