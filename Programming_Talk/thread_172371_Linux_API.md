---
title: "Linux API?"
date: 2006-05-08
forum: Programming Talk
---

### Post by treak007 on 2006-05-08
Hi,
I am currently migrating from win32 development and am interested in developing applications for linux. I was curious as to whether there is a linux api or some type of documentation of how to program for Ubuntu in c++. Thanks in advance.

---

### Post by RavenOfOdin on 2006-05-08
[QUOTE=treak007]Hi,
I am currently migrating from win32 development and am interested in developing applications for linux. I was curious as to whether there is a linux api or some type of documentation of how to program for Ubuntu in c++. Thanks in advance.[/QUOTE]

You mean BSD style C++?

90% of C/C++ is similar between the two API's, not counting portability issues and/or little things like class design.  Certain things that Windows would let you do without trouble (IE put a semicolon after the closing bracket of a class) your Linux installation will whine at you for.

I had to port a networking app of mine to Linux just a month ago and there were about like 35 lines of errors in the Windows version, not using its API, where it compiled and ran cleanly before.

Try your hardest to forget and/or unlearn MFC, then put your mind around straight C++ code. It'll come easier after that.

Since you asked, there are man pages related to programming in Linux as well:

```

man tcp
man ip
man sockets
man sysctl
man ddp
man capabilities

```

Just access them from the console and you're good to go.

---

### Post by treak007 on 2006-05-08
Thanks a ton

---

