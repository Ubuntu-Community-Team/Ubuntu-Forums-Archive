---
title: "A new tool to monitor OpenGL support status"
date: 2011-03-22
forum: Programming Talk
---

### Post by barisurum on 2011-03-22
Hi there everyone!

I've just started to write a tool to view opengl support status of a linux box. Its called GL-Status. Its licensed under GPL. Sourceforge project site follows:

[https://sourceforge.net/projects/gl-status/](https://sourceforge.net/projects/gl-status/)

It uses:

Qt for gui
SDL for opengl context creation
and of course OpenGL

Its currently in a very early stage of development. The current development version is 0.0.9. At this moment feedbacks from the community are important for the future. So feel free to leave your comments either to this thread, or to [email]baris.glstatus@gmail.com[/email], or if you have a sourceforge account you can review it. Also feel free to contribute bug fixes, features etc. Thanks.

---

### Post by slavik on 2011-03-22
add a command line version to dump the data into a file (not sure if you already do this).

Also, consider outputting extension support and such (similar to what glxinfo does).

---

### Post by barisurum on 2011-03-23
> add a command line version to dump the data into a file (not sure if you already do this).

Yes it sounds beneficial for system administrators. Will look into it.
> 
Also, consider outputting extension support and such (similar to what glxinfo does).

Its already in the plans. I think I'll have no problem checking and listing them nicely using GLEW. But I doubt I can hack good OpenGL benchmark tests that can be considered mission-critical quality. I'll appreciate any help in this area :D

Thanks for your comments.

---

### Post by slavik on 2011-03-23
> **barisurum said:**
> Yes it sounds beneficial for system administrators. Will look into it.


Its already in the plans. I think I'll have no problem checking and listing them nicely using GLEW. But I doubt I can hack good OpenGL benchmark tests that can be considered mission-critical quality. I'll appreciate any help in this area :D

Thanks for your comments.
for benchmarks, I'd suggest looking at GLExcess. :)

---

### Post by barisurum on 2011-03-23
Yes I'm aware of GLExcess. The difference between GL-Status and GLExcess is (will be) that MY PROGRAM! :) will test every extension and functions in them exclusively, one by one, or in a batch query. While demo-like tests are also a wannabe feature, I aim to make it suitable for both pro GL guys and GL fans alike.

---

### Post by slavik on 2011-03-23
time to wipe drool off my keyboard ;)

---

### Post by barisurum on 2011-03-23
Contributors will be listed both on the webpages and the about tab (as mentioned on the GPL license). Also you can apply for project membership if you have something unresistable in you bag. I suggest first reading the ROADMAP.txt included in the package. Additions to the roadmap are welcome for both contributors and project members. I'm currently working on the website of the project. Will be ready shortly.

---

