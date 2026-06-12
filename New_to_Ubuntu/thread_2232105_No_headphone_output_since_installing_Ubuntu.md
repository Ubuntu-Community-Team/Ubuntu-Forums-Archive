---
title: "No headphone output since installing Ubuntu"
date: 2014-06-29
forum: New to Ubuntu
---

### Post by grannyflats on 2014-06-29
Regarding Ubuntu 14.04
Using laptop and internal speakers working properly.
Sound card is detected.
When plugging in powered speakers to headphone output there is no signal.
Nothing is muted, all volume is up.
Output device automaticaly sets to "headphones" when plugging in powered speakers to headphone output.

Using the same setup that worked perfectly with Windows Vista
I have reinstalled Pulse Audio
I have reinstalled ALSA.

Still, only internal speakers working properly.

How can I track down the problem?

---

### Post by nerdtron on 2014-06-30
I'm not sure if alsamixer is still in ubuntu but, type in "alsamixer" on the terminal when you plug your earphone. Use the arrow key to navigate and increase the volumes in there. If you see a level with M, it means muted so change that see if it works.

---

