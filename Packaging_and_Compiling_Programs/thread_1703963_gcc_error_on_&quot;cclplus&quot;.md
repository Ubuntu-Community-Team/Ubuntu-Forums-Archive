---
title: "gcc error on &quot;cclplus&quot;"
date: 2011-03-10
forum: Packaging and Compiling Programs
---

### Post by indrajit_1 on 2011-03-10
All,

I wrote a small C++ program on my newly installed Ubuntu to test gcc on it. I named the file test.cpp.

Now through the gcc seems to be able to compile a basic C program correctly, for the above file the result it gives is:

"gcc:exec: cannot find cclplus. no such file or directory"

or something which is very close (I am writing from Windows since the Internet connection is only available for me here.)

Help appreciated.
Indrajit

---

### Post by nickleboyblue on 2011-03-10
Uh, call me stupid, but I don't see the file you were talking about...

Make sure it's installed:

```
sudo apt-get install build-essential
```

---

### Post by indrajit_1 on 2011-04-08
Thanks,

That worked.

---

### Post by J.M.Ward on 2012-01-11
I would like to thank both indrajit_1 (for asking the question) and nickleboyblue (for answering it so succinctly).

I was having a hard time trying to get Netbeans to build and run a simple C++ program, and getting the error message mentioned by indrajit_1.  Netbeans put gcc in the C++ compiler tool box, and while I wondered about this, I just assumed gcc could do C and C++.  Then I Googled the problem, found this thread, ran nickleboyblue's one-liner, and did a rescan in Netbeans, which found g++.  It worked immediately!

Many thanks to you both, guys; I hope you see this - you have saved me hours of head-scratching!

Best wishes,
JMW  :D:D:D

---

