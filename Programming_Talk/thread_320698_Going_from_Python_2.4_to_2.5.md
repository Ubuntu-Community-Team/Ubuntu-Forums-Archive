---
title: "Going from Python 2.4 to 2.5"
date: 2006-12-17
forum: Programming Talk
---

### Post by samjh on 2006-12-17
Just a noob question:

I'm trying to install Python 2.5 and remove 2.4.  But when I try removing 2.4, either using synaptic or aptitude, there are masses of packages that it wants to remove (it looks like half the packages in my linux installation!).

How do I do a clean upgrade from 2.4 to 2.5 without breaking anything?

---

### Post by pmasiar on 2006-12-17
> **samjh said:**
> How do I do a clean upgrade from 2.4 to 2.5 without breaking anything?

[Setting Python2.5 to Run From The Command Line]("http://ubuntuforums.org/showthread.php?t=315362") asked 4 days ago.

Looks like FAQ - someone has idea where some Ubuntu python FAQs are? Some wiki?

---

### Post by JDahl on 2006-12-17
why don't you just have both version installed, and explicitly invoke it as 'python2.5'
when you need it?

Some of the Python extension modules have not been upgraded to version 2.5 yet,  so
it's better to have both versions for the time being.

---

### Post by samjh on 2006-12-17
It seems to result in breakage.  I'll just keep 2.4 for now.

---

### Post by Wybiral on 2006-12-17
Yeah, to avoid any possible conflict's, I would do what JDahl said.

---

### Post by pmasiar on 2006-12-17
> **samjh said:**
> It seems to result in breakage.  I'll just keep 2.4 for now.

What 2.5 features are important for you? You can access many via "from __future__ import ..." IIUC

---

