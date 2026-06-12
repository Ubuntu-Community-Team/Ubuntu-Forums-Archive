---
title: "BASIC interpreters for Linux?"
date: 2016-01-10
forum: Programming Talk
---

### Post by Zeikcied on 2016-01-10
I have a bunch of old BASIC scripts from high school and college programming courses, and I thought it would be fun to revisit them and play around with them a bit.

Thing is, they're different types of BASIC.  The ones from high school were from a version of BASIC (I'm not entirely sure the name) that was for Mac OS 8 or 9 in the late-90s.  It was unstructured, so you'd have lines like this (could have mistakes, as I haven't used BASIC in a long time):
5 start
10 go to 20
20 print "Yay"
25 end

Meanwhile, in the college course, we used QBASIC, which is structured, but not object-oriented.

It would be great if I could find a program that could run both types of BASIC.  If not, then two different programs would work.  I know FreeBASIC is supposed to be able to run QBASIC scripts, but the examples on its wiki seem more geared toward object-oriented scripting.  So yeah, anyone know any programs that would work? :)

---

### Post by ian-weisser on 2016-01-10
Here's one way to look in the Ubuntu repositories for available BASIC interpreters:

```
$ apt-cache search basic | grep BASIC

basic256 - educational BASIC programming environment for children
brandy - BBC BASIC V interpreter
bwbasic - Bywater BASIC Interpreter
sdlbasic - BASIC interpreter for game development
```

---

