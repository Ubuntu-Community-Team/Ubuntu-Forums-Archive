---
title: "problem not getting permission to acces workspace"
date: 2011-09-19
forum: Programming Talk
---

### Post by shubham1 on 2011-09-19
i have partion neamed workspace
code block is not getting permission to acces the partion workspace code block can load the file but not compile it syas permission deinied i chagned the chmod to 777 with -R before any one suggests it.

---

### Post by karlson on 2011-09-19
> **shubham1 said:**
> i have partion neamed workspace
code block is not getting permission to acces the partion workspace code block can load the file but not compile it syas permission deinied i chagned the chmod to 777 with -R before any one suggests it.

The last thing you did should not be done as a best practice.

What you should do is open a shell go into the workspace directory and check who owns and what permissions are set and go from there.

---

### Post by shubham1 on 2011-09-19
> **karlson said:**
> The last thing you did should not be done as a best practice.

What you should do is open a shell go into the workspace directory and check who owns and what permissions are set and go from there.
workspace i not a diretcory its a filesystem i am the owner
folder acces is creates and deletes files

---

### Post by shubham1 on 2011-09-20
my porblem has sloved beaacuxse of my other thread
[http://ubuntuforums.org/showthread.php?p=11268288#post11268288](http://ubuntuforums.org/showthread.php?p=11268288#post11268288)

---

