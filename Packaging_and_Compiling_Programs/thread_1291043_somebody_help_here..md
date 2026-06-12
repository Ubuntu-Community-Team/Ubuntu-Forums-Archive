---
title: "somebody help here."
date: 2009-10-14
forum: Packaging and Compiling Programs
---

### Post by mpande on 2009-10-14
I need the command that make me run my C/C++ file written in geditor. If i can get direct software package which Debug and run C/C++ programs.

---

### Post by Giblet5 on 2009-10-14
You can install and use one of the many integrated development environment (IDE) tools by either searching Google for ubuntu+ide or by bringing up synaptic and searching for "ide".

If you want to do it from the command line - and most developers do - you can invoke the C++ compiler like this:
```
g++ MyCode.cpp -o MyCode
```

That will take your source file, MyCode.cpp, compile it, link it with default libraries, and write the executable to MyCode in the current directory. To test, it's: ```
./MyCode
```

gcc = C compiler
g++ = C++ compiler
gdb = debugger
make = build management

Tip: "kate" is a better C/C++ editor.

---

### Post by NoBugs! on 2009-10-27
If you're wanting to code, run and debug all in one program you might look into an IDE program such as Anjuta or Netbeans. (They are in Ubuntu repository)

---

