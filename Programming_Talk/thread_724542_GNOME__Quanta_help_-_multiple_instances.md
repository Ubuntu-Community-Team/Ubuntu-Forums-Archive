---
title: "GNOME / Quanta help - multiple instances"
date: 2008-03-14
forum: Programming Talk
---

### Post by emaag on 2008-03-14
Collective Knowledge : 

Here's a bug that I found that I was hoping someone would have a solution to: 

I have managed to associate my file in the gnome browser so that clicking on the file opens the correct application. But here's my problem:

When I click on the first *.php file it starts up Quanta and loads it in the app, but when I click on a second file it start up yet another instance of Quanta, is there some way that I can do it so that it does not instantiate a new version of the program, but sends it to the already open copy of it? 

I appreciate any information that would help me solve this. 

I also have this happening in GEdit, and I'm sure it's the same solution for both.

Thank you
EM

---

### Post by mssever on 2008-03-14
That's the responsibility of the individual app. For example, Firefox's wrapper checks whether Firefox is already running. If so, it sends an appropriate command to the running process and exits. Otherwise, it starts a new process.

---

