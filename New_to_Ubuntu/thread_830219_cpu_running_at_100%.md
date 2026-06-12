---
title: "cpu running at 100%"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Lokuststar on 2008-06-15
so i have been running ubuntu for a little over a month now. run into some problems, but fixed most of them. but after running the system for a few hours, if im listening to music it will start to clip. everything runs slow as hell. if i check sysrtem monitor it says that my cpu is running at nearly 100%. but im not running any programs that are heavy.  i am running a AMD Sempron(tm)   2800+, so it has plenty of speed to keep up. any ideas?

---

### Post by MasterSander on 2008-06-15
What application is using all the CPU? Go to the system monitor to find out, System > Management > System Monitor or type top in a terminal.

---

### Post by tamoneya on 2008-06-15
Something is probably broken and running out of control.  In order to find out what post the output of:```
top
```This output changes about once per second but we just need one "frame" of it.  Anyone will do.  You can copy in terminal with ctrl-alt-C and then paste into the forums.

---

### Post by TeoBigusGeekus on 2008-06-15
What is the application that uses so much cpu? 
You can check that in the tab Processes of the System Monitor.

---

### Post by markbuntu on 2008-06-15
Compiz will do that if you have a transparent desktop and gears or atlantis or snowflakes or something like that running inside the cube.

---

