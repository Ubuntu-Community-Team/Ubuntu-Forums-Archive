---
title: "Hardy T61 suspend overview"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by pflanzenmoerder on 2008-05-16
Ok, I think it would be good to get a list of T61 models that work or don't work with suspend.
Grab your version identifier using "hal-device |grep system.hardware.product", check the version of your bios and tell us if suspend to ram works.

T61 14.1" with nvidia (non open source drivers)
BIOS 2.17
system.hardware.product = '7662CTO'

Suspend not working (tried all available tutorials, was working with 7.10)

---

### Post by jbrown96 on 2008-05-17
I have a t61p and suspend works fine after applying a couple of changes to /etc/default/acpi-support. 

I think this thread is unnecessary. There's a whole website [ThinkWiki]("http://www.thinkwiki.org/wiki/ThinkWiki") related to Thinkpads. 

And here's the Ubuntu docs for it too [Suspend with Nivida cards]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

---

### Post by pflanzenmoerder on 2008-05-19
Oh yes, there are tons of pages dealing with that problem.
But just looking around in the forums shows that the different suggestions simply don't work for everyone.
My model id for example is not even listen in the different possible configs.
And it doesn't work (did work in 7.10).
So I think getting an overview what models work with what bios would be nice.

---

