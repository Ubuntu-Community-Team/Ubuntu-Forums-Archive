---
title: "skype"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by ccl4 on 2008-07-13
hello,
i followed the instruction to install skype however error appears:> ccl4@ccl4-laptop:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skype

please help

---

### Post by halitech on 2008-07-13
isn't skype in the repos?

---

### Post by TSS on 2008-07-13
Skype is not in the repositories.
This should help you though: [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by halitech on 2008-07-13
my mistake, was thinking it was 8-[

---

### Post by tuxxy on 2008-07-13
You need to add the skype repo

Goto Software Sources and add

> deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

Now try again :)

---

