---
title: "Dell Inspiron 3537, dual boot"
date: 2014-12-12
forum: New to Ubuntu
---

### Post by skille on 2014-12-12
Hello, I am pretty new to Ubuntu. I decided to install ubuntu on my Dell Laptop with dual boot (Windows 8.1).
 After I made a new partition on my ssd  (which also hosts Windows), I installed Ubuntu 14.10 . 
My problem now is that sometimes when I choose Windows from the grub menu, it just shows a black screen with some weird random colors and never really boots.
 Sometimes it boots perfectly though, it seems like a weird bug or something. 

I read something relevant in this page [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting) 
> 
[COLOR=#333333][FONT=Ubuntu]Some machines [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu](all Dell laptops, all new Apple from 2010 on, some Lenovo) have bugs in their UEFI firmware, preventing them from booting (black screen).
[/FONT][/COLOR][COLOR=#000000]*Linux Kernel 3.0 (and higher versions) includes patches with workarounds for them. It is therefore recommended to use a Linux kernel of version 3.0 or higher.*[/COLOR][COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]
My exact laptop model is Dell Inspiron 3537.

Thank you in advance.

---

### Post by mörgæs on 2014-12-12
When quoting please mention the whole context. The next lines are

> Linux Kernel 3.0 (and higher versions) includes patches with workarounds for them. It is therefore recommended to use a Linux kernel of version 3.0 or higher.

---

### Post by skille on 2014-12-12
Ok thanks. But how exactly can I find these workarounds?

edit: Solved it by installing boot-repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mörgæs on 2014-12-12
Good that you got it solved. 
Anyway, to answer your question: The [list]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions") shows which kernel is in use in various releases. 14.10 uses kernel 3.16, so the fixes added into kernel 3 are also available here.

---

