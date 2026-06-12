---
title: "how to retrieve icons of packages in ubuntu?"
date: 2015-05-28
forum: Programming Talk
---

### Post by wisdom2 on 2015-05-28
Hello, i need to retrieve packages' icons using python apt in ubuntu.  For example if my software's package name is "eclipse", using python apt  or etc., i need to access icon of filezilla, then i will display this  icon on my gui. How can i retrieve icon of any package(for example  eclipse)?

 I traversed python apt documents, tutorials but i  couldn't find any solution. I tried to find ubuntu software center's  api. But it didn't help.


Thanks in advance

---

### Post by wisdom2 on 2015-05-28
Hello, i need to retrieve packages' icons using python apt in ubuntu.    For example if my software's package name is "eclipse", using python apt    or etc., i need to access icon of filezilla, then i will display this    icon on my gui. How can i retrieve icon of any package(for example    eclipse)?

 I traversed python apt documents, tutorials but i  couldn't find any  solution. 


Thanks in advance

---

### Post by ian-weisser on 2015-05-28
The icons are provided by the app-install-data package, not software-center nor python-apt.
The icons are in /usr/share/app-install/icons

---

### Post by wisdom2 on 2015-05-28
All possible software's icons are included in this directory, right? 


I looked at this directory. There are 1945 icons in this directory. Then, whenever a new software is added to ubuntu repository, the new software's icon is added to this directory. Am i riight?

---

### Post by slickymaster on 2015-05-28
Thread closed. Duplicate [here]("http://ubuntuforums.org/showthread.php?t=2280166").

Please do not create duplicate threads, it dilutes the community’s efforts to provide support and causes confusion.

---

### Post by ian-weisser on 2015-05-30
> **wisdom2 said:**
> All possible software's icons are included in this directory, right? 

Goodness, no.
Many packages have no icon at all (libpurple), but are dependencies pulled in by user-facing applications.
Many packages are user-facing, but have no icon because they are command-line only (openssh_client)
Some packages are user-facing and GUI, but have no icon because of packaging mistakes, or sometimes the developer just doesn't create  an icon.

Neither Ubuntu nor Debian *require* an icon for acceptance of a package.
Lack of an icon is considered a valid bug in the software. Neither Debian nor Ubuntu have any way to compel a developer to fix that bug. (nor should they)
User-facing applications submitted to Ubuntu via the Ubuntu SDK and developer.ubuntu.com should have an icon. But lack of an icon seems not fatal.


> **wisdom2 said:**
>  I looked at this directory. There are 1945 icons in this directory. Then, whenever a new software is added to ubuntu repository, the new software's icon is added to this directory. Am i riight?

It's added, but the process of adding may not be automatic.
You should research the project behind app-install-data --or ask the Debian maintainer-- if a-i-d was some kind on one-shot data dump, or how it's being maintained and new applications are getting into it.
You should also ask if a-i-d will be maintained after Ubuntu migrates away from Software Center during the Unity 8 transition in a year or two.

---

