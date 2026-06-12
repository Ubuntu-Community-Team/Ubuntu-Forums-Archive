---
title: "How to implement preferences"
date: 2005-07-21
forum: Programming Talk
---

### Post by josuealcalde on 2005-07-21
I am working in a simple gtk application. It is a gtk application developed using C++ and libGlade. It is not a gnome application.

I want to implement some preferences, which should be saved for next sessions. I would like to know if there is any standard or api to make this simple, or if I should implement this as I would like.

---

### Post by LordHunter317 on 2005-07-21
You could use GConf, which is the GNOME API for such things.  Other than that, there's no offical standard, use whatever's most convient / useful.

---

### Post by josuealcalde on 2005-07-21
I know Gconf, but I don't want to depend on it.

---

