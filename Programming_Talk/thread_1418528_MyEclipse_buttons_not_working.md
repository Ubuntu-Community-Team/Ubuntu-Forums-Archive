---
title: "MyEclipse buttons not working"
date: 2010-02-28
forum: Programming Talk
---

### Post by cjnkns on 2010-02-28
Hey all - 


I tried installing MyEclipse a few months ago and the buttons were not working correctly. Today, I tried again and still I have the same issue.

After some searching people mention adding GDK_NATIVE_WINDOWS=1 but this does not work either.

This is really ridiculous that this STILL doesn't work does someone please have a fix for this?

Linux is supposed to allow you to get more work done not make it frustrating and impossible. (sorry I am just frustrated :) )

---

### Post by GregBrannon on 2010-02-28
Try launching from a script that includes this instead of your line:

export GDK_NATIVE_WINDOWS=true

---

