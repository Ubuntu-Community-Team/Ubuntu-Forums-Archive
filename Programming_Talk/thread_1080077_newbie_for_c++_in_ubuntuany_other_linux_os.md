---
title: "newbie for c++ in ubuntu/any other linux os"
date: 2009-02-25
forum: Programming Talk
---

### Post by cool_vaidya on 2009-02-25
hi  i am new to ubuntu can anyone tell how to write cpp program in ubuntu.
  thanks in advance..............................

---

### Post by null.byte on 2009-02-25
```

nano filename.cpp
g++ filename.cpp -o filename

```

---

### Post by soltanis on 2009-02-25
Step 1. Learn the language.

[http://cplusplus.com/](http://cplusplus.com/)

Step 2. Obtain a compiler.

```

(in a terminal)
sudo apt-get install gcc

```

You will also need to install development libraries and headers, but the gcc package should give you a basic build environment I think.

Step 3. Learn to use the compiler.

I would not suggest using the manpage -- it's really complicated for really no good reason. Just use this syntax:

```

gcc -o <executable name> <source1>.cpp <source2>.cpp ... <source n>.cpp

```

Step 4. Gear up your favorite editor for code editing.

Look around on the Internet for how to turn gedit into a pretty sweet coding environment, or use an IDE like Code::Blocks or Eclipse.

Step 5. Write programs.

Write programs, write programs, write programs. When they break, try to fix them. If you can't, get help. It's a long-term commitment -- learning a complex language like C++ is going to take a lot of time (probably more than a decade to master) but that's no reason not to start. Don't mind people who discourage you; they all started from the same boat you're in.

---

### Post by .Maleficus. on 2009-02-25
Learning C++ is a good place to start.

After that, install the build-essential pacakage, which contains the compiler (gcc) and other useful goodies.
```
sudo apt-get install build-essential
```

Use an IDE or text editor to write your code.

---

