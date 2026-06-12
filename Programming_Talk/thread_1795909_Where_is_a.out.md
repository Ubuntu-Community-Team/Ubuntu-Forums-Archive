---
title: "Where is a.out?"
date: 2011-07-03
forum: Programming Talk
---

### Post by smilinggoomba on 2011-07-03
Hello.
First off, I am running Ubuntu 11.04 on an Acer Aspire One alongside Windows 7.  I compiled a "Hello World" program in C using gcc, as helloworld.o.  The compilation was successful, but I can't find helloworld.o.  I ran a search of files and folders, but couldn't find it.  Could somebody please help?

---

### Post by nvteighen on 2011-07-03
Hm...

The usual procedure is the following one:

```

gcc -o myapp myapp.c -Wall

```

The -o option allows you to choose the name for your executable, in my example, myapp. The executable will be created in the same directory.

Then, you run it this way:
```

./myapp

```

---

