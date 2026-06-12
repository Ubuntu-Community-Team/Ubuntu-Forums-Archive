---
title: "Code::Blocks 16.01"
date: 2016-02-24
forum: Packaging and Compiling Programs
---

### Post by dannyk2 on 2016-02-24
Hello everyone
I am running Ubuntu MATE 15.10 and i am about to start learning C++ but i see that in Synaptic the Code::Blocks version there is only 13.12-3. So i went along to codeblocks.org/downloads and would like to download the latest version which is Code::Blocks 16.01. The trouble is i don't know how to compile the source code and install it. Would someone like to help me please. Thanks

---

### Post by T.J. on 2016-02-24
Welcome!  

I could, but I don't think it would be the best thing for you. The C++ language version will be the same version either way. CodeBlocks (CB) is just a development environment.  GCC is the default C++ compiler, and that won't be changed with CB, even if you upgrade CB. In general, you should use the CB version that is maintained in the archives - even if it is older - as it is likely to be more stable and and compatible with your copy of Ubuntu.   If you insist on using the new version of CodeBlocks, using Damien Moore's personal version would probably be easier for you.  Please keep in mind that a personal archive (PPA) is not an official release., so it may have problems.  I very much recommend that you stick with the older version and wait for the next Ubuntu release in April.  

[https://launchpad.net/~damien-moore/+archive/ubuntu/codeblocks-stable](https://launchpad.net/~damien-moore/+archive/ubuntu/codeblocks-stable)

You can get started now, either way! =) The C++ code will be the same, and projects should work when the new version is made available.  If you have questions about C++, getting setup, etc as I am sure you will - please feel free to send me a personal message or post here on the thread.  I'd be very happy to help you take your first steps into a new world.

Just as a note on Mate specifically, it is important for you to know that Mate is not written in C++, but C using the GTK+ toolkit, which is not the same thing as C++.  You CAN write code for Mate in C++, but most of the existing code is in C.

Happy Coding!

Best Wishes,
T.J.

---

