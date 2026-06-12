---
title: "How to i18n a Qt Designer .ui?"
date: 2008-09-09
forum: Programming Talk
---

### Post by Vadi on 2008-09-09
Hi all,

Does anyone have experience with internationalizing Qt Designer .ui files? I did a bit of research and found the Qt Linguist, however that doesn't cut it as it uses it's own home-made (certified for Windows Vista, it boasts) system that is incompatible with Launchpad's Rosetta (which uses GNU GetText).

I don't have experience with on GetText, but I understand how the basics work. But how would I go about using it on a .ui file that's compiled by Qt and whatnot? Can anyone help out with some links/info?

---

### Post by samjh on 2008-09-10
Just use Qt Linguist, and make sure to use the tr() method in your source code.

Why **don't** you want to use Qt Linguist?  What is so bad about it, and why do you feel you **must** rely on Rosetta or the GNU Gettext library?

---

### Post by Vadi on 2008-09-10
Yes, I don't want to use Qt Linguist. Rosetta is a far superior way for translating projects (no program dependencies, great interface, strings are shared across the all of Launchpad projects).

I'm not impressed by the linguist's home-made style either.

---

