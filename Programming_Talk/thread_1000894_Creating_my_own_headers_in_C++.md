---
title: "Creating my own headers in C++?"
date: 2008-12-03
forum: Programming Talk
---

### Post by extruct on 2008-12-03
Hello all. I was wondering is there a way to create my own header files?
Lets say I want to implant Binary Tree class. I don't want to copy and add BinaryTree.cpp and BinaryTree.h to each of my projects that will use it, instead I want to put the .h file in /usr/include and be able to write:
#include <BinaryTree.h>
In every project that needs it.
But as you know I will get a bunch of errors (probably "unresolved external symbol"). So how it is possible to make this work?

Thanks a lot!

---

### Post by davidbilla on 2008-12-03
Personally, I choose to put my own header files in a custom directory and compile with -I option.

```

$ gcc -I [your-headerfile-directory-path] prgname.c
```

---

### Post by Sydius on 2008-12-03
If it includes a .cpp file, it must be made into a library, and linked against.  If there isn't much in the .cpp file, you can move it all to the .h file and just include it, assuming it is only a class definition.

---

### Post by davidbilla on 2008-12-03
Hey sorry. I thought it was C. So g++ it is, then!

---

### Post by dwhitney67 on 2008-12-03
> **davidbilla said:**
> Personally, I choose to put my own header files in a custom directory and compile with -I option.

```

$ gcc -I [your-headerfile-directory-path] prgname.c
```

Correct!  Or install your personal header files in /usr/local/include.  If that directory does not exist, then create it.  Similarly, personal library file(s) can go in /usr/local/lib.

---

### Post by hessiess on 2008-12-03
personally I just add '-I ./' to the G++ command. makes G++ look in the current directory for includes.

---

### Post by extruct on 2008-12-03
Since I haven't tested it yet, I would like to ask one more thing:
I put both files (.h & .cpp) in some folder that add -I to gcc/g++ with the folder were those files located and I'm done? No need to work with dynamic libraries (so called DLL's in win or SO's in unix [as far as I know])?

Thanks a lot gain!

---

### Post by Sydius on 2008-12-03
> **extruct said:**
> Since I haven't tested it yet, I would like to ask one more thing:
I put both files (.h & .cpp) in some folder that add -I to gcc/g++ with the folder were those files located and I'm done? No need to work with dynamic libraries (so called DLL's in win or SO's in unix [as far as I know])?

Thanks a lot gain!

Like I said before, if there is a .cpp file, it must be compiled into a library and linked against.

---

### Post by Sydius on 2008-12-03
> **hessiess said:**
> personally I just add '-I ./' to the G++ command. makes G++ look in the current directory for includes.

It should do that automatically.  At least it does for me.  No need to tell it to look in the current directory.  I think the OP was wanting to avoid having to have a copy of the header in the same directory as every project he wants to include it into, anyway.

---

