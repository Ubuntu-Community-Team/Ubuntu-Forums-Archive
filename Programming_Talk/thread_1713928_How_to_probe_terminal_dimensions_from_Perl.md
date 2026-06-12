---
title: "How to probe terminal dimensions from Perl"
date: 2011-03-24
forum: Programming Talk
---

### Post by paxxus on 2011-03-24
As the title says. I want to probe the number of lines and number of columns in the terminal (xterm). Is this possible?

---

### Post by johnl on 2011-03-24
You can find the height and width in the environmental variables LINES and COLUMNS.

An alternative is to perform a TIOCGWINSZ ioctl().

---

### Post by paxxus on 2011-03-25
Thanks john - TIOCGWINSZ also gives a lot more relevant hits in Google than what I searched for before.

---

