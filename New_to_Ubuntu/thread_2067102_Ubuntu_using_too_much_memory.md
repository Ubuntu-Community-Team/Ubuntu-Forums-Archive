---
title: "Ubuntu using too much memory?"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by silentcontrol on 2012-10-06
Hello, I've just installed Ubuntu 32-bit, using wubi.exe. I was wondering why Ubuntu is using so much memory even after rebooting.

Don't really know if it has any influence over it, but now I have a dual boot (Win XP and Ubuntu) and Ubuntu is installed on the same Hard Disk as Win XP, but on another partition of the disk.

---

### Post by albandy on 2012-10-06
Linux uses free ram for caching purposes. Don't mind about it, it's normal and this ram will be available when needed. 

As you can see you're not using swap memmory, so there is no memmory resources problem.

---

### Post by mikewhatever on 2012-10-06
What makes you think it uses much RAM? It looks decent from the screenshot with Firefox and gnome terminal open.

---

### Post by silentcontrol on 2012-10-06
> **albandy said:**
> Linux uses free ram for caching purposes. Don't mind about it, it's normal and this ram will be available when needed. 

As you can see you're not using swap memmory, so there is no memmory resources problem.

Ok, thanks for the reply.

> **mikewhatever said:**
> What makes you think it uses much RAM? It looks decent from the screenshot with Firefox and gnome terminal open.

Well, I'm new to Ubuntu, and I'm used to Win XP memory usage.

---

### Post by Cheesemill on 2012-10-06
According to your screen shot you are only using around 285MB, there's nothing wrong with that.

---

### Post by Peripheral Visionary on 2012-10-06
[This]("http://www.linuxatemyram.com/") page should help explain what you think you're seeing. Excerpt:

> Linux is borrowing unused memory for disk caching. This makes it looks  like you are low on memory, but you are not! Everything is fine!  				

It's one of the reasons Linux is so wonderful and speedy even on modest older hardware.  

[Help! Linux ate my RAM]("http://www.linuxatemyram.com/")!

Enjoy!

---

