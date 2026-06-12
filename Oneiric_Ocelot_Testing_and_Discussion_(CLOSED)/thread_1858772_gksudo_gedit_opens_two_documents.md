---
title: "gksudo gedit opens two documents??"
date: 2011-10-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by beew on 2011-10-13
I encountered a strange problem. Whenever I tried to open some configuration file with ```
gksudo gedit xxx
``` gedit would open the document xxx as well as another blank "untitled document".

Wonder what is wrong.

---

### Post by effenberg0x0 on 2011-10-13
+1...
Have you created a Bug Report yet?

Regards,
Effenberg

---

### Post by mc4man on 2011-10-13
Still an open bug, reported 4 months ago - 
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076)

---

### Post by mc4man on 2011-10-13
Just in case you also want to use nautilus-gksu  - this  has yet to be taken care of , though easily fixed locally
[https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/817383](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/817383)

---

### Post by effenberg0x0 on 2011-10-13
4 months... I had never noticed this bug as, instead of using gksudo, I have the supposedly very bad habit of using sudo <gui app> in console, like sudo gedit test.txt, etc.

Regards,
Effenberg

---

### Post by mc4man on 2011-10-13
> **effenberg0x0 said:**
> 4 months... I had never noticed this bug as, instead of using gksudo, I have the supposedly very bad habit of using sudo <gui app> in console, like sudo gedit test.txt, etc.

Regards,
Effenberg
Well it's an upstream bug & so it's likely up to gnome to fix or not.

Myself don't use gksudo gedit much though do use  specific nautilus-actions for .desktops, one for user. one for root.
In the case of the root N-A the extra docu. also opens, can be a pita
(on some installs it could be ignored & closed without comment, on others it always prompts..., no rhyme or reason there.

---

