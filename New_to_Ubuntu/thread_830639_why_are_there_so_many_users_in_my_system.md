---
title: "why are there so many users in my system ?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by dexter.deepak on 2008-06-16
i cant understand the fundamental of creating "system users".as an example..tomcat, for me is just a process, just like a normal java program ..so even the operating system should treat it like a normal program..why to give tomcat a user status ?? is it because tomcat needs to have more resources ?? can i also make a small program and provide it a user status ??:confused: 
and how can i login as the user "tomcat" ??

---

### Post by sdennie on 2008-06-16
The primary reason for having lots of different "users" on a Unix machine is for security.  You can give users or groups limited privileges and they are less likely to wreck your machine.  An easy to understand example of this is the "admin" group. Users not in the admin group aren't allowed to use the sudo command (and, if they try, it logs the attempt).  Having lots of users with varying permissions allows a very fine grained control over what a particular "user" (even if that user is just a placeholder for a process) can do.

---

### Post by dexter.deepak on 2008-06-16
THANKS for making me understand the role of users...but can "i" create a process which acts like a "user" ??

---

### Post by vishzilla on 2008-06-16
The processes you are talking about are actually logical users which applications carry out specific tasks with them. We can create only a physical user and for every user we are assigned to a group with the same name

---

### Post by dexter.deepak on 2008-06-16
but what mechanism is used to create this "logical" user for executing a set of programs ? i would like to create such a user...

---

