---
title: "Qt Creator: &quot;No valid Qt versions found&quot;"
date: 2012-07-05
forum: Programming Talk
---

### Post by rebelplankton on 2012-07-05
Whenever I try to create a new project, I always get this "No valid Qt versions found" message on the targets tab, and when I go to Tools>Options>Build and Run>Qt Versions I find the version with a warning sign. I attached a couple screen shots. I really need help because i am new on Ubuntu and programming with Qt Creator and I dont understand very well what the versions are. Thanks.

---

### Post by spjackson on 2012-07-05
Check that you have qt4-dev-tools and build-essential packages installed.

---

### Post by rebelplankton on 2012-07-05
> **spjackson said:**
> Check that you have qt4-dev-tools and build-essential packages installed.

Yes, I have them installed. Actually, Everything was working great a few days ago. I think the problem begun when I installed a C++ library. What can I do?

---

### Post by snip3r8 on 2012-07-05
Do you have the qmake-qt4 package? and what library did you install that you suspect may have broken Qt

---

### Post by rebelplankton on 2012-07-05
> **snip3r8 said:**
> Do you have the qmake-qt4 package? and what library did you install that you suspect may have broken Qt

Yes! I have qmake-qt4!...and I installed curses.h

---

