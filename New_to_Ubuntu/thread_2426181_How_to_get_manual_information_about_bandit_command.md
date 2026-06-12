---
title: "How to get manual information about bandit command"
date: 2019-09-05
forum: New to Ubuntu
---

### Post by zak100 on 2019-09-05
Hi,

There is a hint in Level15-->16 of bandit section which says:

**Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…**

I tried to get: man "CONNECTED COMMANDS" but I am not getting any information. Somebody please guide me.

Zulfi.

---

### Post by TheFu on 2019-09-05
I have no idea what bandit is. Never heard of it before.  Every Linux program should have a manpage, period.  If it doesn't, then you should complain to that project team.

**man bandit**
Use the / to search for any specific section.  'q' to quite.
You can also use **xman**, if you prefer.


If you want to learn to use the man command, use **man man**.  There is brilliance in the way it works, the way each manpage is laid out and the included sections. However, it does take a little time to learn this layout, before it starts to make sense. Once you understand, you'll appreciate the order of the sections with the initially cryptic summary at the top.  Trust me, that summary is all most intermediate Unix people need.

---

### Post by uRock on 2019-09-06
Does this help? [https://buildmedia.readthedocs.org/media/pdf/bandit/latest/bandit.pdf](https://buildmedia.readthedocs.org/media/pdf/bandit/latest/bandit.pdf)

---

