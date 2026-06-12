---
title: "[SOLVED] &amp;quot;lost&amp;quot; functions in custom shared library after name change"
date: 2008-12-05
forum: Programming Talk
---

### Post by Bulletbeast on 2008-12-05
So, yet another hurdle. The functions in my library, libdissonance, had generic names such as "chord", "name" and "invert". I decided to decrease ambiguity by changing them to ones such as "_chord", "_chord_name" and "_chord_invert". And, pow!, my executable doesn't link against the new names. Instead:

```

chord.c: In function ‘notes’:
...
chord.c:217: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
...

```
where said argument 2 is a function which returns char*.

and, more importantly:

```

chord.o: In function `names':
/home/egasimus/Dev/dissonance/dissonance-cli/src/chord.c:160: undefined reference to `_chord_name'
chord.o: In function `main':
/home/egasimus/Dev/dissonance/dissonance-cli/src/chord.c:309: undefined reference to `_chord'

```

Any idea why this is happening?

---

### Post by stroyan on 2008-12-05
It looks like you failed to update the declarations for at least some
of the functions when you changed their names.  The default for calling
an undeclared function is to assume that it returns an int.  Perhaps you
have declarations of the functions in a header file that you have not
changed.

  If you are compiling "chord.c" with g++ then the actual symbol name
of each function will be a mangled name that depends on the types of
the parameters and the return value.  That could cause a difference that
would trigger the "undefined reference" message.

---

### Post by Bulletbeast on 2008-12-06
Well, I'm compiling with gcc. And header files were the first thing I changed. Anyway, if it was a header, wouldn't the compiler give out an error instead of the linker?

---

### Post by nvteighen on 2008-12-06
Where is your library located? If you placed it into a non-standard path, you have to use g++ -L flag to specify the directory in which these libraries lie, not only -l. Maybe the issue is just an incorrect compiling command.

Other possibility is that you recompiled the shared library incorrectly. Have you used -fpic and -shared?

But also, better review the code (also the library's).

---

### Post by stroyan on 2008-12-06
The gcc compiler won't give an error for using an undeclared function.
It will make assumptions like int return type and parameter types that
match the passed parameters.  The first sign of trouble may be a linker
error, (or a warning that you are passing an int function result instead
of a char*).

There are many unstated details that people reading your posting must make
assumptions about.  The simplest explanation for the warning and error
message is a typo or overlooked update step.

  You may have failed to edit all symbols correctly.
  You may still be using old object files or library files.

I am going to drift a bit off of the errors topic.  I wonder exactly what
the symbol renaming was motivated by.  If the symbols are exported by
a shared library and used by a program then I would not expect them to
have an underscore prefix.  They might have a common prefix of letters
related to the library name.  But a leading underscore is more commonly
used for fields and symbols that are internal to an implementation.

If you are creating shared libraries then the "How to Write Shared Libraries"
paper at [http://people.redhat.com/drepper/dsohowto.pdf](http://people.redhat.com/drepper/dsohowto.pdf) is a worthwhile read.
It has much information about how to make shared library symbol management
efficient.  It also shows how to keep symbols used within a library hidden
from other libraries to avoid unintentional collisions.

---

### Post by Bulletbeast on 2008-12-06
Well I'm using autotools-generated makefiles, and gcc is called with -fPIC and -shared. The library is installed in /usr/local/bin, and it all used to work correctly before changing names. I couldn't decide on an appropriate prefix so I decided to go with an underscore (like in conio, I think?). I can't imagine what could I be doing wrong.

Thanks for the document, by the way.

---

### Post by Bulletbeast on 2008-12-10
Any help? I've tried defining the functions as extern in the header file, but that didn't help, either. I could post my source - it's a mess, though.

---

### Post by Bulletbeast on 2008-12-29
For some reason, the underscores were what was causing the problem. Changed all function names to lowerCamelCase and works.

---

