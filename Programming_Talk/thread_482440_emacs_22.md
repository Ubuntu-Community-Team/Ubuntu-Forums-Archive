---
title: "emacs 22"
date: 2007-06-23
forum: Programming Talk
---

### Post by vambo on 2007-06-23
Anyone know if there's a repo with this on it yet? It's been out for weeks, there must be one somewhere with it  :(

---

### Post by KaeseEs on 2007-06-23
I would assume Emacs 22 will be in Gutsy.  However, it's possible that a Feisty package will eventually be backported.

---

### Post by vambo on 2007-06-23
The "eventually" bit doesn't sound all that promising!!!!
Sounds like a diy job :(

---

### Post by xtacocorex on 2007-06-23
You could, if you really wanted it, uninstall the version of emacs you have and compile the newest version.

---

### Post by KaeseEs on 2007-06-24
I rechecked, and there is a Debian repository for Emacs 22.  Just google 'emacs 22 deb' and you'll find a site with the repo.  The wisdom of installing a package built for Debian on an Ubuntu system is somewhat questionable, but if you REALLY want it...

---

### Post by daveluciffer on 2007-07-23
You can install the newest version by 
(1) extract package
(2) ./configure
(3) check if there are any header or dev repositories missing for building, especially support for X
(4) sudo make
(5) sudo make install
(6) install the newest version of cedet, ecb
(7) make changes in your .emacs file

then enjoy!

---

### Post by vak on 2008-03-24
April 2008 is close and emacs 22 still isn't in repo. There should be a reason. Anyone knows why? License wars?

/me uses the emacs-snapshot since almost 1 year...

---

### Post by aks44 on 2008-03-24
> **vak said:**
> April 2008 is close and emacs 22 still isn't in repo. There should be a reason. Anyone knows why? License wars?

/me uses the emacs-snapshot since almost 1 year...

FWIW emacs 22 is in the feisty-backports and gutsy repositories.

---

