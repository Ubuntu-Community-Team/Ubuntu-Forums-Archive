---
title: "[C++] Clearing a Line of Output"
date: 2010-05-11
forum: Programming Talk
---

### Post by dodle on 2010-05-11
I've come up with somewhat of a solution to this using the [color=#0099ff]iomanip[/color] library.  My program uses carriage returns ([color=green]\r[/color]) to print a "percentage complete" (int x) inline:
```
85% -- Processing
```My problem is that when it gets to 100%, I want to print "100% Done!".  By just using a carriage return, the output looks like this:
```
100% Done!cessing
```So I have used a manipulator to put whitespace over the "cessing":
[php]cout << "\r" << x << "% Done!\a" << setw(21) << setfill(' ');[/php]
This works, but I was wondering if there was a smarter way to do it.

---

### Post by MadCow108 on 2010-05-11
that method seems fine to me. What your the problem with it?

terminal output is not easy to handle directly as it is highly dependent on the underlying terminal (and thus not very portable). It is not covered by the c++ standard.
for more advanced terminal io stuff with reasonable portability you should use a library like ncurses.

---

### Post by dodle on 2010-05-11
Okay, I just felt like I was using more of a workaround than a solution.

**Edit:** ncurses looks interesting.

---

