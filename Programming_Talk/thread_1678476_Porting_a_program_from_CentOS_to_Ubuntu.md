---
title: "Porting a program from CentOS to Ubuntu"
date: 2011-01-30
forum: Programming Talk
---

### Post by OneLine on 2011-01-30
Hi, if there was a program that was on CentOS (example), and someone wanted to port it to Ubuntu, how would someone go about going that? Thank You.

---

### Post by Zugzwang on 2011-01-30
[LIST=1]
[*]Check which libraries are used by the program. Are they available for Ubuntu as well? What is the minimum version number of the libraries that are still compatible with the program?
[*]Check if the program uses any speciality of CentOS. Does it do something system-dependent, i.e., package management, driver configuration or the like?
[*]If the first two points do not exhibit something that prevents you from porting them, get a copy of the source code of the program and try to compile it. 
[*]If the previous step worked, you might want to have a look at the Debian package management system to build installable .deb files for the application.
[/LIST]

---

### Post by unknownPoster on 2011-01-30
The process might not even be as tedious as Zugzwang mentioned if the application is written in Python or Java or something similar.

---

### Post by lavinog on 2011-01-30
> **OneLine said:**
> Hi, if there was a program that was on CentOS (example), and someone wanted to port it to Ubuntu, how would someone go about going that? Thank You.

You might get a better answer if you can describe what the program does or what it is.

---

### Post by juancarlospaco on 2011-01-30
run it into an LXC

---

### Post by wmcbrine on 2011-01-31
There's negligible difference between CentOS and Ubuntu, from the average app's point of view. I'm not sure it even makes sense to speak of "porting" in such a case. The biggest issue is that CentOS tends to run way behind the times, so its libraries are old.

I'd start by just copying over the binary and see if it runs. If not, then get the source and recompile it. It's not likely that you'd have to do more.

---

