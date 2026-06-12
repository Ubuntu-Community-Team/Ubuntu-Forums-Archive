---
title: "Can't compile with KDevelop."
date: 2006-01-27
forum: Programming Talk
---

### Post by YourSurrogateGod on 2006-01-27
Ok, so in order to get more acquainted with KDevelop, I figured that I would try out a simple hello world program. Now the problem is that whenever I build/execute/install/configure the entire project, I get the below:
```
There is no Makefile in this directory
and no configure script for this project.
Run automake & friends and configure first?
```
Why am I getting this error? Anyone know how to fix it?

I have g++ 4.0 installed... it should compile fine.

---

### Post by amohanty on 2006-01-27
Disclaimer: I havent used KDevelop in a long time. This is from the last time I used.

You will need to provide a Makefile in your project's root. A make file is essentially a list of instructions to make to compile, link and build your app. Tutorials are numerous on the web. There are other options too like ant ([http://ant.apache.org](http://ant.apache.org)) though it is mainly used for java apps.

HTH
AM

Google:
[http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=makefile+tutorial](http://www.google.com/search?sourceid=mozclient&ie=utf-8&oe=utf-8&q=makefile+tutorial)

---

