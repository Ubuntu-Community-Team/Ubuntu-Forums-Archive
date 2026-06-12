---
title: "Wine, notepad, gedit - how to make gedit default for .txt files?"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by scruffyeagle on 2011-11-04
I'm running Ubuntu v10.04 LTS 32-bit on a Dell Inspiron 9400 laptop. My default display is 1440x900.

When I installed Wine, notepad became the default editor/viewer for .txt files. Opening w/ gedit via the "open with" & having the checkmark checked to make gedit the default program doesn't work. It still defaults to notepad, which is a pain in the you-know-what, because of Wine's display limitations. (Can't set colors of theme, etc.)

Is there any way other than removing Wine, to make gedit the default editor for .txt files?

---

### Post by mc4man on 2011-11-04
Right click on any text file > **Properties** > open with & choose gedit (text editor

---

### Post by scruffyeagle on 2011-11-04
> **mc4man said:**
> Right click on any text file > **Properties** > open with & choose gedit (text editor

Thanks for the reply. That seems to have done it. I'll know for sure, after I reboot.

---

### Post by scruffyeagle on 2011-11-09
> **mc4man said:**
> Right click on any text file > **Properties** > open with & choose gedit (text editor

Hi, I'm back again!

Nope, it didn't work. The assignment of ".txt" files to gedit didn't survive a reboot. The default has returned to being notepad.

---

### Post by Mark Phelps on 2011-11-09
Used to edit a file named defaults.list -- but that seems to have changed recently.

See the link below for details:

[http://www.johannes-eva.net/change-the-default-application-ubuntu-linux]("http://www.johannes-eva.net/change-the-default-application-ubuntu-linux")

---

