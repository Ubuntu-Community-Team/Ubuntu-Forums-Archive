---
title: "Trying to ld a program (assembly language)(make executable from .o)"
date: 2024-02-14
forum: Packaging and Compiling Programs
---

### Post by ppetit69 on 2024-02-14
I have a small test program written in assembler.  It assembles fine.  The command "ld wins6.o -o wins6 -lX11 runs, without error message.  When I then try to run the resulting program, ./wins6, I get "No such file or directory".  I look at the executable file, best I can with the editor and dolphin, and can see nothing wrong with it. Any suggestions?  Further info: This is on kubuntu LTS.  The program has a call on XOpenDisplay.

---

### Post by TheFu on 2024-02-15
I've never used **ld** directly. I always use **gcc** as the compiler to also link programs.

Also, I've never done ASM on x86 that wasn't inline to a C program.

```
$ gcc -o wins6 wins6.o -lX11
```
would be the expected linker.  The location of the libX11.so file would be in a default directory, so gcc would find it.  If not, specify the full path to the file.

If that created the wins6 file, but it doesn't run, I'd use the **file** command to see what type of header the program has.
```
$ file wins6
```

---

### Post by ppetit69 on 2024-02-15
Thank you for your help, TheFu.  It is the right approach.  You started me down a long journey, which ended up working.  I still got error messages, but experimentation led me to the final additional touch: adding "-no-pie" in the gcc command line solved the last problem.

Thanks again.

---

### Post by TheFu on 2024-02-16
Please "Thread Tools" ---> "SOLVED".

Help the community here.  It would also be nice if you posted the exact, working, link, command.

---

