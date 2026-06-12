---
title: "Modules crashes kernel when trying to access keyboard LED's"
date: 2013-11-12
forum: Programming Talk
---

### Post by prashanth.kumar.n on 2013-11-12
[COLOR=#000000][FONT=Arial]I was searching for a simple driver to demo talking to real world HW with the available interface on PC and came across a Keyboard LED programming. This program first seems to be published in tdlp for older kernels which has been modified to work with new kernels at the below link. When i run the below code, my system freezes.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][http://tuxthink.blogspot.in/2013/02/kbledsc-for-linux-kernel-version-375.html](http://tuxthink.blogspot.in/2013/02/kbledsc-for-linux-kernel-version-375.html)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I am using ubuntu 11.10 with kernel as 3.0.0.2-generic. Any idea what could be causing the hang?
I tried dumping dmesg but it crashes so instantly that i cannot capture the same.[/FONT][/COLOR]

---

### Post by tgalati4 on 2013-11-12
Well, there are a few differences between kernel 3.0.0 and 3.7.5.  Send an email to the blog site owner and ask for ideas as to what changes to make to get it to work on 3.0.0.

Perhaps consider upgrading to a newer version.

---

