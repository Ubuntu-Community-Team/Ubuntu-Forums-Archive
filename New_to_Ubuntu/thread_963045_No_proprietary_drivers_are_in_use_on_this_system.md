---
title: "No proprietary drivers are in use on this system"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by arsenal fan from canada on 2008-10-29
Hi I am new to ubuntu and i am not able to connect to my wireless router so i clicked on Hardware drivers and there was a popup that stated No proprietary drivers are in use on this system. So my question is:

1. How do i connect to the wireless? Please give me a step to step guide.

2. How do I solve the proprietary drivers issue?

Thanks in advance

---

### Post by ethoxyethaan on 2008-10-29
Hello and welcome,

can you open up a terminal window and gime us the output of:
```
lspci
```
thanks!

---

### Post by snova on 2008-10-29
Lack of proprietary drivers is not an "issue". It's simply a classification. If a vendor writes a driver and doesn't release source code, it counts as proprietary. The difference doesn't matter to a lot of people (including me), especially when they have benefits.

There are philosophical reasons not to use them. If you can go without them, great; but if you need some, fine.

You may need one for your wireless, depending on the card in question. What kind is it?

---

