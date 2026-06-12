---
title: "[SOLVED] Evolution and Ms Exchange Servers"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by ant2ne on 2008-10-27
Hey, I'm trying to get my work e-mail to load into my evolution. Under "Server Type:" I don't get a selection for "Exchange".  What gives?

---

### Post by Nxion on 2008-10-30
Most likely you don't have the exchange plug in installed. You can install it like this below.

```
sudo apt-get install evolution-common evolution-data-server evolution-exchange evolution-plugins evolution-webcal
```Also ....

Do you know what version of Exchange your office is running? Is it 2003 or 2007? 

Evolution is not compatible with the current version of Exchange 2007.  The latest word is that Evolution will not be compatible with Exchange 2007 until at least version 2.2.6.   I don't expect to see the Evolution v. 2.2.6

---

### Post by ant2ne on 2008-10-30
version 2003

---

### Post by Nxion on 2008-11-03
> **ant2ne said:**
> version 2003

Ok, then if you just do what I had in my last post, then you should have the Exchange plug in.

---

### Post by ant2ne on 2008-11-03
Works thanks

---

### Post by Nxion on 2008-11-04
> **ant2ne said:**
> Works thanks


No worries. glad I could help :). 

Don't forget to make the thread solved :)

---

### Post by ant2ne on 2008-11-04
How I do that?

---

### Post by justchange on 2008-11-04
At the top of the thread, towards the right, is a dropdown menu: **[COLOR="Red"]Thread Tools[/COLOR]** , Mark as Solved is at the bottom of the list (only in threads that you have authored.)

---

