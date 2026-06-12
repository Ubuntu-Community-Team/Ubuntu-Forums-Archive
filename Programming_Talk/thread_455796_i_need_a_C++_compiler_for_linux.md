---
title: "i need a C++ compiler for linux"
date: 2007-05-27
forum: Programming Talk
---

### Post by bosshoof on 2007-05-27
Hi
i need a C++ compiler for linux

---

### Post by xtacocorex on 2007-05-27
```
sudo apt-get install build-essential
```

---

### Post by bosshoof on 2007-05-27
> **xtacocorex said:**
> ```
sudo apt-get install build-essential
```

thanks

i did so

but i can't find the compiler  under programming  :(
where to find it ?

---

### Post by xtacocorex on 2007-05-27
The compilers are terminal based.

If you have a code written, for this example we'll use hello.cpp for a hello world program we'd do the following to compile it.
```
g++ -o ./hello hello.cpp
```
To run the code, you will do:
```
./hello
```

---

### Post by public_void on 2007-05-27
You can install an IDE like Anjuta which will use g++ as the c++ compiler.

---

