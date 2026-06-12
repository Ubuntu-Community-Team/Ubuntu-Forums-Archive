---
title: "Programatically knowing inactive system"
date: 2011-02-20
forum: Programming Talk
---

### Post by nipunreddevil on 2011-02-20
What are the methods which can be employed to figure out when a system is inactive(idle) for some threshold time duration?How to know this via some script etc.
NB:Although i would like to work on Linux,but ideally would like to know some general features/algorithms which help detect the same for any computing environment.

---

### Post by tgalati4 on 2011-02-20
ruptime
rwho
rwhod

---

### Post by nipunreddevil on 2011-02-20
> **tgalati4 said:**
> ruptime
rwho
rwhod

PLease may you elucidate.
Does this take into consideration a situation like
I am the only user logged to my system and suppose there's no activity on my part,not even mouse movement etc.Ubuntu by default uses some algo in the power management whereby the display turn after some time of no activity.Something of this type is what i desire

---

### Post by nipunreddevil on 2011-02-20
Any answers?

---

### Post by nipunreddevil on 2011-02-23
Let me reframe the question.How can i program to know when to turn my display etc off?

---

### Post by slavik on 2011-02-23
> **nipunreddevil said:**
> Let me reframe the question.How can i program to know when to turn my display etc off?
monitor input events, no input events for 5 min -> screen saver

---

### Post by rnerwein on 2011-02-24
> **nipunreddevil said:**
> What are the methods which can be employed to figure out when a system is inactive(idle) for some threshold time duration?How to know this via some script etc.
NB:Although i would like to work on Linux,but ideally would like to know some general features/algorithms which help detect the same for any computing environment.

hello
if you want to figure this out you need different interfaces in uninx/linux.
on uninx ( solaris ) you can use /dev/kmem on linux you can use /proc to retrive the data.
but i think your problem is how to design "idle" because the system is always a little busy ( sync, network ...)
and what time slice you want to declare ( is there a screensaver running ? - get the cpu usage from it )
hope it helps a little.
ciao

---

### Post by nipunreddevil on 2011-02-26
How can i know how the screen save knows that it's 5 mins no activity and it may turn on.

---

### Post by rnerwein on 2011-03-02
> **nipunreddevil said:**
> How can i know how the screen save knows that it's 5 mins no activity and it may turn on.
high
watch your keyboard, mouse and every thing you got as an input.
ciao

---

### Post by cgroza on 2011-03-02
> **rnerwein said:**
> high
watch your keyboard, mouse and every thing you got as an input.
ciao
+1, The user may be away, but a program could do heavy processing.

---

### Post by SledgeHammer_999 on 2011-03-02
I think the main way is to use the xlib and XScreenSaver api. Unfortunately I can't give example code. Only some links:

1. [http://stackoverflow.com/questions/222606/detecting-keyboard-mouse-activity-in-linux](http://stackoverflow.com/questions/222606/detecting-keyboard-mouse-activity-in-linux)
2. [http://stackoverflow.com/questions/351185/is-there-a-simple-way-to-detect-mouse-or-keyboard-activity-in-linux-xorg-qt4-kde4](http://stackoverflow.com/questions/351185/is-there-a-simple-way-to-detect-mouse-or-keyboard-activity-in-linux-xorg-qt4-kde4)

---

