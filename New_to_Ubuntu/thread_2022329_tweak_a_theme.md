---
title: "tweak a theme?"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by jllipke on 2012-07-10
I recently downloaded and installed GnomishDark theme and MyUnity, and when I go to google and type something in, it types in the colour white, so I cannot see it. also any search bar will be coloured in black instead of white. For instance, the search bar for ubuntu forums in the upper right hand corner is black and types in a darker black.

Is there a way to modify this?

---

### Post by Krytarik on 2012-07-10
> **jllipke said:**
> I recently downloaded and installed GnomishDark theme and MyUnity, and when I go to google and type something in, it types in the colour white, so I cannot see it. also any search bar will be coloured in black instead of white. For instance, the search bar for ubuntu forums in the upper right hand corner is black and types in a darker black.
Presuming that you don't really want to change the input boxes of your overall theme, but only fix them within websites in your web browser, and since at least Chromium/Chrome doesn't have that issue, and thus I bet you are using Firefox, please see my earlier post here:

[http://ubuntuforums.org/showthread.php?p=10606786#post10606786](http://ubuntuforums.org/showthread.php?p=10606786#post10606786)

Regards.

---

### Post by jllipke on 2012-07-10
ok.. where can I find the directory in 12.04?

---

### Post by Krytarik on 2012-07-10
> **jllipke said:**
> ok.. where can I find the directory in 12.04?
Should be the same place in Precise 12.04, i.e. under "~/.mozilla/firefox/PROFILE"  [in your home directory (~), hidden (.), and the latter is by default appended by ".default"], but since it seems like the "chrome" directory isn't created by Firefox by default anymore, you may need to create it yourself.

---

