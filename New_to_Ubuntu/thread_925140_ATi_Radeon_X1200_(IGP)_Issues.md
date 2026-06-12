---
title: "ATi Radeon X1200 (IGP) Issues"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by WastePotato on 2008-09-20
Hello All,

Where can I get the ATI Linux Driver for my X1200?

And How do I install and configure it?

Thanks.

---

### Post by WastePotato on 2008-09-20
Anyone? :/

---

### Post by nothingspecial on 2008-09-20
Is this an atheros wireless card?
Some googling suggests it is

---

### Post by samdude9 on 2008-09-20
It's a graphics card...

and why do you need it?

I expect one is built into x.org for you (the basic program which makes everything graphics based run).

details please?

I had troubles with a gfx card once but it seems almost all drivers are now included....

Sam

---

### Post by WastePotato on 2008-09-20
I was told that I need it to run Compiz.

Plus, Google Earth runs really slow and told me to update my graphics card driver.

---

### Post by samdude9 on 2008-09-20
ah ok,

have you tried running compiz manager or whatever they call it now anyway?

Sam

---

### Post by WastePotato on 2008-09-20
Yes, when I tried to start it, it logged me out.

---

### Post by WastePotato on 2008-09-20
Yes, but I don't really know how that would change anything... :/

---

### Post by samdude9 on 2008-09-20
right ok... thanks for the info

please can you try doing...

# dpkg-reconfigure xserver-xorg

as root?

it'll give you a long string of questions and you just have to answer as best you can...

if you have another pc available, you might want to leave it accessible incase you get stuck (so you can answer a question)...

good luck anyway... see you on the other side :p

Sam

---

### Post by WastePotato on 2008-09-20
Yes! It worked!

Thank you so much!

:popcorn:

---

### Post by samdude9 on 2008-09-20
> **WastePotato said:**
> Yes! It worked!

Thank you so much!

:popcorn:

No problem :)

Glad I could help, have fun with ubuntu :)

Sam

---

