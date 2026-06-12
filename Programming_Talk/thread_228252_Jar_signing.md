---
title: "Jar signing"
date: 2006-08-02
forum: Programming Talk
---

### Post by hod139 on 2006-08-02
I wrote a little [rigid body java web start demo]("http://www.cs.rpi.edu/%7Esberard/lcp_applet/"), which relies on a native C library for solving the formulation.  Therefore, I had to digitally sign the jar file containing the C lib and in order for the application to start the user has to accept my signature.  For now, I just made my own certificate so a warning that this signature cannot be verified is displayed.  Is there a free way to get a trusted signature?

---

