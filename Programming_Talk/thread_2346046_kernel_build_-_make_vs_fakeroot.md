---
title: "kernel build - make vs fakeroot"
date: 2016-12-10
forum: Programming Talk
---

### Post by ranchu-panchu on 2016-12-10
Hello,

I've see 2 different methods for building ubuntu kernel:
1. using fakeroot & debian/rules.[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]2. using simple "make uImage"

The 2nd method, I'm more familiar with from other embedded linux, and is *much* more faster.
I would like to understand if there is any added value for the first method over the second, and if there is any real requirements for doing the first method.

I am using the 2nd with a console, and I am afriad that maybe I will need the more complex build so that gui and other features shall be supported (I am using an image which was build using the 1st method, and currently update uImage every time with the 2nd method only) ?

Thank you,
Ran

---

