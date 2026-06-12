---
title: "Setting system time using Java"
date: 2009-06-18
forum: Programming Talk
---

### Post by Kralizec on 2009-06-18
Hello programmers! I'm writing a program to take in a gps signal and use it to set the system time. The problem I am having is when it comes to setting the system time. I am attempting to use a Runtime.exec() command to execute a system "date" call. However, it doesn't work. I've tried to tackle the permissions issues with gksu, but the manner in which I have it set up, a loop causes many authorization prompts to pop up (minor annoyance). I think my problem may lie more in my syntax on the date command or something...Attached is the script I am using and the source file (as a txt document).

---

