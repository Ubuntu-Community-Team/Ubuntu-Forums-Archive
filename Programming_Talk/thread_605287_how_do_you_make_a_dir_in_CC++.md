---
title: "how do you make a dir in C/C++"
date: 2007-11-06
forum: Programming Talk
---

### Post by Mr. Book on 2007-11-06
Simple question, I know I must be doing something wrong. I want to make a directory inside my C++ program. I've looked online and found tutorials that say there is a mkdir() function included in <sys/dir.h> (all this does is include dirent.h). This is true and I have gotten it to work under mingw with the code:

if(0<mkdir("doc")) { printf("ERROR\n") return 1; }

But my code does not compile on my ubuntu system. I get the following error:

xcg.cpp:305: error: &#8216;mkdir&#8217; was not declared in this scope

I did a search inside dirent.h and could not find the string mkdir. searching on google & this forums haven't show what i have been looking for because the "make" and "mkdir" commands overshadow the function that I am looking for. I know this is a simple task and I feel stupid for not being able to find it. any help would be greatly appreciated.

---

### Post by vladan.b on 2007-11-06
You probably found this in google too
```
http://www.informit.com/guides/content.aspx?g=cplusplus&seqNum=245
```

Perhaps the directory name is not compatible, causing mkdir() to fail.

---

### Post by Steven_B on 2007-11-06
Try <sys/stat.h>.

---

### Post by Mr. Book on 2007-11-06
> **Steven_B said:**
> Try <sys/stat.h>.

that did the trick. well kinda, i am missing a parameter now, but knowing the include file lead me to this link:

[http://www.opengroup.org/onlinepubs/000095399/functions/mkdir.html](http://www.opengroup.org/onlinepubs/000095399/functions/mkdir.html)

Thank you

---

### Post by dwhitney67 on 2007-11-07
Also look at the man-page:

```
$ man 2 mkdir
```

All the info you need is there.

---

### Post by hod139 on 2007-11-07
Also check out Boost's filesystem library:
[http://www.boost.org/libs/filesystem/doc/index.htm](http://www.boost.org/libs/filesystem/doc/index.htm)

---

