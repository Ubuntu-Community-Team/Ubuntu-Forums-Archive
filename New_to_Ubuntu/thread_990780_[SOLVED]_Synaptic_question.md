---
title: "[SOLVED] Synaptic question"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Orographic on 2008-11-23
Hi all,

I've been enjoying using Ibex via Wubi and installed Opera a week or so ago via their website as I need it to adjust my router settings. IE6 is supposed to be the only way to adjust the settings in this older router but Opera works too. It wasn't in the Ibex packet manager at the time.

My question:

I started Synaptic this evening and now Opera in in there. What made it appear all of a sudden?

---

### Post by nhasian on 2008-11-23
maybe the deb package added a line to your /etc/apt/sources.list ?  that's where the package manager gets all their programs from.

---

### Post by Elfy on 2008-11-23
By using a deb to install opera - which is what I assume you did - Synaptic became aware of it - you'll be able to remove it using Synaptic. If the deb was in your apt cache then Synaptic would also be able to reinstall it.

Any program you install with a deb will appear in Synaptic.

---

### Post by Orographic on 2008-11-23
Thanks guys, that is cool. :)

---

