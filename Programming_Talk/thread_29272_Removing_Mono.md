---
title: "Removing Mono"
date: 2005-04-23
forum: Programming Talk
---

### Post by Hoshimaru on 2005-04-23
Hi,

I don't know how I did it, but probably without my brains in my proximity...
When trying to upgrade MonoDevelop to version 0.6 from SVN, I had to upgrade gtk-sharp and gtk-sourceview as well.

This somehow broke my working Mono installation. The problem is that the make uninstalls don't work anymore. So I've polluted my Ubuntu system with a broken mono and deps.

Is there a way to completely clean it ?

I'm looking forward to a solution. Otherwise I'll have to dump this Ubuntu install and start all over again :(

---

### Post by sas on 2005-04-23
You could read the configure/make files and find where it installed each file and remove it...I don't know of a cleaner way around it.

---

