---
title: "gcc: passing defines on the command line with $(cat file)"
date: 2008-03-10
forum: Programming Talk
---

### Post by flostre on 2008-03-10
Hi all,

I am in a group working on a big software project. Lately, I tried to make the gcc call more readable by condensing all defines. The problem boils down to this:

If you are using defines like so:
```

#include <iostream>

int main() {
  std::cout << MSG << std::endl;
}

```

you can define them on the command line like so:
g++ -DMSG=\"Hello\" -o talk talk.cc

If you use multiple words, you have to quote like so:
g++ -DMSG="\"Hello world\"" -o talk talk.cc

If for some reason you want to read the defines from a file (which I do), you can say:
g++ $(cat defines) -o talk talk.cc

With the file 'defines' containing
```
-DMSG=\"Hello\"
```

**My problem**: How do you get this to work with a multiple word define? 
If you straigt-forwardly say
```
-DMSG="\"Hello world\""
```
in 'defines', you get the error:
g++: world\"": No such file or directory

I've tried almost all combinations of \, " and '. I get the impression that cat does something funky to force g++ to break the file contents at spaces when passing it to the arg-vector of g++.

Thanks, flostre

---

### Post by mssever on 2008-03-10
Actually, cat isn't doing something funky; bash is. Bash is very aggressive in its tokenizing. Change your call to  ```
g++ "$(cat defines)" -o talk talk.cc
``` You might need to adjust how/which quotes in your file to backslash-escape, if any.

---

### Post by WW on 2008-03-10
Alternatively, you could create a file like this:

**defines.h**:
```
#define MSG  "Hello, world!"
#define MSG2 "Goodbye, cruel world!"
```
and use the **-include** or **-imacros** option:
> 
$ g++ -include defines.h -o talk talk.cc


---

### Post by Jessehk on 2008-03-10
> **WW said:**
> Alternatively, you could create a file like this:

**defines.h**:
```
#define MSG  "Hello, world!"
#define MSG2 "Goodbye, cruel world!"
```
and use the **-include** or **-imacros** option:

Agreed. Or, you could just create a header that's *#include*'ed from all files that need the definitions. I don't really know why you'd bother trying to do it any other way...

---

### Post by flostre on 2008-03-12
@msserver: that only works if you have just one define

I went with WW's approach.

The reason we don't just have one global include is separation of concerns plus dynamicality. Our software is compiled as a collection of quite some dynamic libraries, each with its own Makefile (not called recursively, but iteratively). Defines from one library should be defined in the libraries headers where they belong. Some defines, however, have to be determined at compile time (current revision, username, hostname,...). These are the ones we're talking about. They are defined in the Makefile of the library that introduces the need for them, but passed to every file. All in all we have quite some defines in the g++ call which puts too much output to the terminal. So I wanted to put the defines into a file - which is now working.

Thanks, flostre

---

