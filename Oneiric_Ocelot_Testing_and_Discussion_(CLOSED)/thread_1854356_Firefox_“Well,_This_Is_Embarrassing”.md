---
title: "Firefox: “Well, This Is Embarrassing”"
date: 2011-10-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by philinux on 2011-10-04
I get this every time I boot up and start Firefox.

Anyone else get this?

---

### Post by VinDSL on 2011-10-04
> **philinux said:**
> I get this every time I boot up and start Firefox.

Anyone else get this?
What?  That it's embarrassing?!?!?

Hold on, let me try...

It opened just fine, but it is embarrassing.  I'm an Opera user.  ;)

---

### Post by jtarin on 2011-10-04
> **philinux said:**
> I get this every time I boot up and start Firefox.

Anyone else get this?It can happen when your not connected and Firefox cannot find the address. If you have your connection and Firefox come up at boot you might put a [delay]("http://linux.about.com/library/cmd/blcmdln_after.htm") on the browser command.
There is also "sleep" (man sleep) and "at" (man at).

---

### Post by philinux on 2011-10-04
> **VinDSL said:**
> What?  That it's embarrassing?!?!?

Hold on, let me try...

It opened just fine, but it is embarrassing.  I'm an Opera user.  ;)

Lol, yes quite.

Well anyways I bugged it.
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/867424](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/867424)

---

### Post by coffeecat on 2011-10-04
@philinux, your link needs fixing! :wink:

I get the "well this is :oops:" message if I've had to do a Alt+SysRq+R -> E -> I -> S -> U -> B and firefox was still open, or if I've done some sort of ungraceful exit from the desktop, but I don't see it routinely.

---

### Post by philinux on 2011-10-04
> **coffeecat said:**
> @philinux, your link needs fixing! :wink:

I get the "well this is :oops:" message if I've had to do a Alt+SysRq+R -> E -> I -> S -> U -> B and firefox was still open, or if I've done some sort of ungraceful exit from the desktop, but I don't see it routinely.

Link fixed. Not had to reisub at all so something off. I'll try removing some addons.

---

### Post by sgage on 2011-10-04
> **coffeecat said:**
> @philinux, your link needs fixing! :wink:

I get the "well this is :oops:" message if I've had to do a Alt+SysRq+R -> E -> I -> S -> U -> B and firefox was still open, or if I've done some sort of ungraceful exit from the desktop, but I don't see it routinely.

Same here - I only see this when there has been an "ungraceful exit".

---

### Post by sammiev on 2011-10-04
> **sgage said:**
> Same here - I only see this when there has been an "ungraceful exit".

I had it happen once a few weeks back on a "ungraceful exit" as well. Never happen since.

---

### Post by ventrical on 2011-10-04
> **philinux said:**
> Link fixed. Not had to reisub at all so something off. I'll try removing some addons.

Phil,

 I get this dern message every cotton picking time I log on .. gracefully or ungracefully ... I think there is a HUGE problem with firefox. Thanks for filing the bug. I thought it was normal behaviour!!!

---

### Post by Rasa1111 on 2011-10-04
it only happens for me when I (improperly) close firefox with multiple tabs open.
Say if i have more than one tab open, and i just shut down or reboot, instead of closing out firefox first. 

It's just a way to give you the chance to re-open the tabs you had open when you closed it out.

---

### Post by quids on 2011-10-04
Yes I've been getting that.

I thought it could have been to do with me being lazy and copying over my .mozilla folder over from 11.04 instead of using Firefox Sync to add another computer.

---

### Post by philinux on 2011-10-04
> **quids said:**
> Yes I've been getting that.

I thought it could have been to do with me being lazy and copying over my .mozilla folder over from 11.04 instead of using Firefox Sync to add another computer.

Ah that maybe it. I copied .mozilla from natty into home. I'll try deleting it and start a new profile.

---

### Post by lidex on 2011-10-04
I wonder if you can work-around that in about:config

Have you changed any of the resume/restore options for sessionstore?

---

