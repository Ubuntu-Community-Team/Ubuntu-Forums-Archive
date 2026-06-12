---
title: "How do I Make My Own GUI In C++"
date: 2012-09-24
forum: Programming Talk
---

### Post by Kris1994 on 2012-09-24
Hello, I was wondering how I would go about making my own GUI in c++. I want to do this
without any frameworks, basically I want to create my own GUI from scratch no 
dependencies. I don't want any built-in API either. Just pure C++.

Please respond.
thanx :)

---

### Post by satsujinka on 2012-09-24
What you're describing is basically impossible. At some point in time you'll need some combination of assembly, system calls, OpenGL, Xlib/XCB, or a tool kit.

---

### Post by JKyleOKC on 2012-09-24
Since you say "no API" that means you have to start right down at the bare metal and learn how to interpret keycodes into characters, put dots on the monitor and arrange them to form letters and words, and handle the critical timing details for getting data to and from your disk drives. None of this is really practical in any high-level language; it requires finely tuned assembly language coding.

Keep in mind that very few people have ever accomplished all this on a solo basis. Even Linus took several years to come up with the original Linux kernel, and that was with the help of dozens of folk on UseNet.

It's a noble goal, but be prepared for several years of trial and error for each part of the process. And to be strict about it, "no API" would rule out the possibility of using any of the standard C++ libraries, even...

---

