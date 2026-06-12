---
title: "Program compiles on Ubuntu but on on Suse"
date: 2011-02-13
forum: Programming Talk
---

### Post by technmom on 2011-02-13
I have Ubuntu 10.04 at home and compiled a program at home but when I tried doing that on another in the lab it gets a segmentation fault
They are running Suse in the lab.

---

### Post by linuxsyst on 2011-02-13
OK but which compilier?

---

### Post by Zugzwang on 2011-02-13
Are you really getting the segmentation while compiling the program and not while running the compiled program?

If it is really the compilation process that causes a segfault, then you can't do much about it other than seeing if there are updates for the SuSE Linux version available.

---

### Post by nvteighen on 2011-02-13
1. Is really the segfault occurring when *compiling* on SUSE? If it is, then please report it to your sysadmin. Maybe something has to be updated before reporting a bug on the compiler. Btw, what compiler is it?

2. Is it that you compile the program on Ubuntu and then you try to run the binary on SUSE without recompiling? That's a mistake: the libraries might not be the same and a segfault may happen.

3. And here's what I think is happening: your code has some bug that for some reason doesn't trigger on Ubuntu but does in SUSE. It can be that you're relying on undefined behaivor (which is undefined, of course) or that the compilers are set differently in both systems. Please, post us a small code snippet that produces the segfault.

---

### Post by technmom on 2011-02-13
sorry I don't know why I said compiling I meant running. I'm going back to look again and recompile If I can.

---

### Post by Zugzwang on 2011-02-14
> **technmom said:**
> sorry I don't know why I said compiling I meant running. I'm going back to look again and recompile If I can.

That's a good first step. Also check if your program probably does something nasty with the memory management, which leads to undefined behaviour. At home (or at the lab), compile your program using the "-g" switch and run it using the valgrind tool.

```

valgrind --tool=memcheck ./yourprogram

```

Watch out for warnings emitted by valgrind. You might have to install the respective Ubuntu package first.

---

