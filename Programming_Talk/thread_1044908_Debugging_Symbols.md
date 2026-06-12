---
title: "Debugging Symbols"
date: 2009-01-19
forum: Programming Talk
---

### Post by Jesdisciple on 2009-01-19
When I try to debug my C project with gdb, it can't tell me much about the program's state and often gets lost if the stack gets too deep.  It complains about not finding any debugging symbols; I've Googled around a bit and not found any relevant instructions for developers - only for bug-reporters.  (Valgrind's Memcheck, on the other hand, doesn't seem bothered.)

Can someone please point me in the correct direction for this?  Thanks!

---

### Post by nvteighen on 2009-01-20
Are you compiling with the -g flag?

Example:
```

gcc -o myprog myprog.c -Wall -g

```

This is also valid for g++.

---

### Post by Jesdisciple on 2009-01-20
That makes GCC complain about a huge list of function redefinitions, but it doesn't give any line numbers - just hex addresses.  And it indicates the main file, which only defines two functions, but I don't include any source files except from that one.  ???

---

### Post by nvteighen on 2009-01-20
That's the linker.

Two possibilities:
1) You're linking some module twice (are you using a Makefile?)
2) You named two functions the same in two different places.

If not, then, please show us the code.

---

### Post by Jesdisciple on 2009-01-20
I link header files multiple times, but I thought redeclaration was legal.  I only include *.h files except in main.c, and no *.h has any runtime instructions.

No, I wasn't using makefiles; I'm reading up on them now.  But what use is a preprocessor #include if a makefile takes care of that anyway?

---

### Post by nvteighen on 2009-01-20
> **Jesdisciple said:**
> I link header files multiple times, but I thought redeclaration was legal.  I only include *.h files except in main.c, and no *.h has any runtime instructions.

No, I wasn't using makefiles; I'm reading up on them now.  But what use is a preprocessor #include if a makefile takes care of that anyway?

You're confused. The header files are not linked, but included. The C (and C++) compilation takes four steps: Headers are "pasted" into the source at the first one (preprocessing).

Linking, is the last step, and it's when the function references **in the binary** are resolved, either to a library or by joining all .o files into the executable.

So, please answer these questions:
1) Are you using more than one .c file?
2) Are you using some library?

And if you post the source code + the error messages, it'll be much easier to help, of course ;)

---

### Post by Jesdisciple on 2009-01-20
So only header files are to be included and all sources should be linked?  (I still don't understand how anything got redefined.)

Yes, I'm using four source files and three header files.  I've attached them as they were before I started fiddling with makefiles.  (The only difference in the source is .h extensions in the main.c include statements.)  I was using this command to compile them:```
gcc main.c -Wall -o ./outliner
```

I'm loosely patterning my makefiles after [http://www.cs.bris.ac.uk/Teaching/Resources/COMSM1401/pm_lectures/Paul/exercises/compile_make_intro.html]("http://www.cs.bris.ac.uk/Teaching/Resources/COMSM1401/pm_lectures/Paul/exercises/compile_make_intro.html").  (The application's name is inconsistent because I'm in the process of renaming it; Outliner is the new name.)  Surprisingly, the makefiles finally work after several tries.

ListMan/Makefile
```
# Makefile

outliner: main.o outline.o ../Jesdisciple/list.o ../Jesdisciple/toolkit.o
	gcc -g -o outliner main.o outline.o ../Jesdisciple/list.o ../Jesdisciple/toolkit.o

main.o outline.o: outline.c main.c
	gcc -g -c outline.c main.c

include ../Jesdisciple/Makefile
```

Jesdisciple/Makefile
```
# Makefile

toolkit.o list.o: list.c toolkit.c
	gcc -g -c list.c toolkit.c
```

---

### Post by Zugzwang on 2009-01-21
To give you an example, in your "toolkit.h", you have:
```

char *root, *home;

```

This is a definition. In order to get it correctly (and have a declaration instead), write:
```

extern char *root;
extern char *home;

```
and put "char *root, *home;" into one of the C-files.

You are doing it precisely the other way around!

---

### Post by bruce89 on 2009-01-21
You also have no header guards. You should have somthing like

```

#ifndef __TOOLKIT_H__
#define __TOOLKIT_H__

<header content>

#endif /* __TOOLKIT_H__ */
```

This stops headers being included more than once in a source file causing redefined warnings.

Also, you have a lot of platform dependent bits, it may be easier to use something like GLib for certain things (though that might defeat the purpose of this project).

---

### Post by Jesdisciple on 2009-01-22
Zugzwang, perhaps I'm using faulty definitions of "declaration" and "definition."  I was (am) under the impression that a declaration identifies a variable's (or function's) type, while a definition describes the actual information.  Thus a declaration may or may not be "extern"; the value is the only difference between the two types of statements.

Thanks Bruce; I didn't understand why NetBeans put those there when it worked.  (If I hadn't somehow wrecked part of my system including NetBeans, I still wouldn't know anything about compiling via the command line.)

> **bruce89 said:**
> Also, you have a lot of platform dependent bits, it may be easier to use something like GLib for certain things (though that might defeat the purpose of this project).I was referred elsewhere to [NSPR]("http://www.mozilla.org/projects/nspr/"); do you know the (dis)advantages of each?

---

### Post by Jesdisciple on 2009-01-23
(bump)  I greatly appreciate the help in getting this to work, but can I please get clarification for my two remaining questions?  (I should note that I asked a question "elsewhere" for a different problem with the same project; I don't cross-post to communities.)

---

### Post by bruce89 on 2009-01-23
> **Jesdisciple said:**
> I was referred elsewhere to [NSPR]("http://www.mozilla.org/projects/nspr/"); do you know the (dis)advantages of each?

All I know is that NSPR is used by Mozilla, whereas use of GLib is more widespread.

---

