---
title: "[Puppy] How do I get my Belkin Wireless Card to Work?"
date: 2009-01-03
forum: Other OS Talk
---

### Post by fiddler616 on 2009-01-03
Hello,
I recently installed Puppy on my dinosaur laptop ([this]("http://support.gateway.com/s/Mobile/Solo_Series/P2150/P2150nv.shtml") one). I'm a fan, but my PCMCIA wireless card, from Belkin, doesn't work (I've been through the network wizard, which didn't work, and the few modules I tried didn't work either).
How do I get it to work?

Thank you.

---

### Post by wolfen69 on 2009-01-03
it will usually suggest a module for you to use. start with that, then do autodhcp.

what does ```
lspci
``` say? we would need to know the chipset of the card.

---

### Post by fiddler616 on 2009-01-04
> **wolfen69 said:**
> it will usually suggest a module for you to use. start with that, then do autodhcp.

what does ```
lspci
``` say? we would need to know the chipset of the card.
The module it suggested didn't work. Um...what's autodhcp? (I'm sorry about my ignorance...)
```

# lspci
00:00.0 Class 0600: 8086:7190 (rev 03)
00:01.0 Class 0604: 8086:7191 (rev 03)
00:07.0 Class 0601: 8086:7110 (rev 02)
00:07.1 Class 0101: 8086:7111 (rev 01)
00:07.2 Class 0c03: 8086:7112 (rev 01)
00:07.3 Class 0680: 8086:7113 (rev 03)
00:08.0 Class 0607: 8086:ac1c (rev 01)
00:08.1 Class 0607: 8086:ac1c (rev 01)
00:09.0 Class 0401: 1102:8938
00:0a.0 Class 0780: 8086:0448 (rev 01)
01:00.0 Class 0300: 8086:4c4d (rev 64)
02:00.0 Class 0280: 8086:4320 (rev 03)
```
(Wow, that was a pain to type out...)

---

### Post by wolfen69 on 2009-01-04
> The module it suggested didn't work. Um...what's autodhcp? (I'm sorry about my ignorance...)
it's what tou have to run after you put in your wireless info. it's the first window that pops up.

---

### Post by fiddler616 on 2009-01-04
> **wolfen69 said:**
> it's what tou have to run after you put in your wireless info. it's the first window that pops up.
Eh...am I doing something wrong? I go to Menu>Setup>Network Wizard, and then it just gives me the option to load a module (and clicking on that gives me the ndiswrapper option too).
Thanks for your help though.

---

