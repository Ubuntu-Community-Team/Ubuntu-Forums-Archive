---
title: "relative path question"
date: 2009-02-11
forum: Programming Talk
---

### Post by jmartrican on 2009-02-11
I wrote an application in C++ where I use relative path name for accessing its config file (i never went back to clean it up).  Anyways the application is launched from a Java website running on Tomcat using the System.exec routine.

Here is the weird part.  We have two servers with this website and my application installed.  The relative path causes an issue in server_1 but server_2 does not seem to have a problem with the relative path.  Both are running Ubuntu 8.04.

Is anyone aware of any OS environment settings (or anything else) that can cause this differences in behavior?

thanks!

---

