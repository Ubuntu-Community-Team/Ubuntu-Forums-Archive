---
title: "Eclipse CDT debug problem"
date: 2010-08-11
forum: Programming Talk
---

### Post by harishgp on 2010-08-11
Hi,
   I know it is not the right place to ask this question, but as the eclipse forum has given no response for my query ,I turn to here. 

I wanted to debug a modification of an openly available C program(If it helps, it is the SVMlight code  by Joachims).  

This is what I did.

1. It had a makefile in itself and so I created a makefile project, imported the files and built it. 
2. Two executables were created(as expected) and I created two run configurations for them and it successfully ran.
3. But when I debug the project, it says that the "source is unavailable" . I checked the source lookup directory and it had the project folder listed .

PS: Unlike the "executable project" ,No extra files like the "debug" folder and .d files were created after the build . I assumed this was normal for makefile projects, maybe it is the issue?

How to solve this issue?? please help.

Thanks,
Harish

---

### Post by dwhitney67 on 2010-08-11
Someplace in your Makefile, typically where you have defined CFLAGS, you require the -g option so that symbolic information is included in the debug version of the executable.

Something like:
```

...

CFLAGS += -g

...

```
Since you are dealing with Eclipse, you will need to hunt through the compiler options to find where you may indicate that you want to build a debug version of your project.

[rant]
Btw, I dislike IDEs.  If you had learned to work without an IDE, you probably would've known how to resolve this issue without having to post a query on the forum.  IDEs do not further one's knowledge; it stifles it.
[/rant]

---

### Post by harishgp on 2010-08-12
@ dwhitney 
Thanks.. It works now..

---

