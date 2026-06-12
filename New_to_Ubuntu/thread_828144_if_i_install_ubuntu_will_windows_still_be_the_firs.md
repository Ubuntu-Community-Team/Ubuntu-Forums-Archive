---
title: "if i install ubuntu will windows still be the first option for boot?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by RedTooth on 2008-06-13
i want it to be the first option, is that possible? 

So if i turn it on and leave then the 30 second timer starts to pick the highlighted OS, will it be ubuntu or windows?

---

### Post by bumanie on 2008-06-13
A wubi install lists windows as the first OS. In a dual boot situation, windows can also be set as the 'defaultOS' if one wants.

---

### Post by melrom on 2008-06-13
it will be Ubuntu by default. but yes, this is an easy change. give me a sec to type it. i just wanted to answer your question right away.

okay, once you install Ubuntu, if you're making a dual boot situation [I have no experience with Wubi]:

type into a terminal:

```

gksu gedit /boot/grub/menu.lst

```

To edit the boot order. 

Refer to this: [http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)

You can also change the timeout to something like 60 seconds, if you'd like longer to decide.

---

### Post by Cypher on 2008-06-13
Change the value of "savedefault" from false to true in /boot/grub/menu.lst and this way GRUB will remember your last booted OS and will always boot that first..

---

