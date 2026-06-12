---
title: "What exactly makes drivers &quot;better&quot; than other drives?"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by venom104 on 2013-01-03
Okay...so, usually when I boot into windows it is because I want to play the black ops zombies mod...but since it's so hard to get a decent game now (one that goes beyond level 15), I usually just play alone on linux under wine. I need to boot into windows for the performance hit.

Now...here is the thing. I boot into windows...I dont know...maybe 2 times a month. Whenever I do, I usually always get notified that my video card driver is out of date...see here for more details...

[http://www.geforce.com/drivers/results/54625#](http://www.geforce.com/drivers/results/54625#)

okay, now...before the mods move this because I am talking alot windows...this isn't a windows only question. I compile the nvidia driver that I get from the nvidia site on ubuntu every so often (and they don't come up with new versions of the kernel module as often as they do for windows)...but the NEWER drivers are USUALLY better in terms of FPS.

Why do they constantly update the drivers so often? It would seem like they are admitting they don't know what they are doing so they have to keep releasing constant streams of drivers...I mean really...are there better data structures/algorithms that come out as fast as these drivers are coming out...is that why the new ones are better?

Why do they offer such a "huge" performance boost every few months? What are they doing that is different, and why do they keep doing it so often?

EDIT: Maybe they get better mathematicians, physicists, and programmers every month?

---

### Post by cariboo on 2013-01-03
In linux, the reason graphics drivers are updated, is to make use of new features, bug fixes, or to work with a newer version of X.

Ubuntu usually gets Nvidia updates, before any of the other distributions, so the version in the repositories is always fairly up-to-date, so there really is no need to manually install the binary driver from Nvidia.

As an aside, Nvidia has claimed they are improving driver performance, due to the upcoming availability of Steam on Ubuntu.

---

### Post by venom104 on 2013-01-03
> **cariboo907 said:**
> In linux, the reason graphics drivers are updated, is to make use of new features, bug fixes, or to work with a newer version of X.

Ubuntu usually gets Nvidia updates, before any of the other distributions, so the version in the repositories is always fairly up-to-date, so there really is no need to manually install the binary driver from Nvidia.

As an aside, Nvidia has claimed they are improving driver performance, due to the upcoming availability of Steam on Ubuntu.

That doesn't really answer my question though...why do new drivers offer better performance that drivers released just a few months earlier? What new information are they using that they didn't have before...data structures/algorithms/more advanced (accurate) math/more advanced physics...what are they doing to make them better?

---

### Post by squakie on 2013-01-03
> **venom104 said:**
> That doesn't really answer my question though...why do new drivers offer better performance that drivers released just a few months earlier? What new information are they using that they didn't have before...data structures/algorithms/more advanced (accurate) math/more advanced physics...what are they doing to make them better?

See the first line in Cariboo907's reply.  They fix bugs, add enhancements (which can both have something to do with performance).

---

### Post by venom104 on 2013-01-03
> **squakie said:**
> See the first line in Cariboo907's reply.  They fix bugs, add enhancements (which can both have something to do with performance).

Still doesn't answer the question of why new drivers seem to come out bi-monthly.

---

### Post by Wim Sturkenboom on 2013-01-03
On the nVidia website you can find what has changed for a specific driver; but I guess that does not answer the question either ;) Randomly picked example [http://www.nvidia.com/object/linux-display-ia32-310.19-driver.html](http://www.nvidia.com/object/linux-display-ia32-310.19-driver.html)

Your question is why a previous version of a driver could not be as good as the newer one and only the manufacturer (of the proprietary driver) can answer that question. If a manufacturer provides open source drivers, you have the ability to compare the source code of versions and see what has changed.

---

### Post by lisati on 2013-01-04
> **venom104 said:**
> Still doesn't answer the question of why new drivers seem to come out bi-monthly.

If only it was as simple as plugging things in and everything works perfectly..... :D 

I can only speak for myself, but when I've developed software, I have almost invariably later thought of ways of improving what I have done, even though I might have a usable product.

---

