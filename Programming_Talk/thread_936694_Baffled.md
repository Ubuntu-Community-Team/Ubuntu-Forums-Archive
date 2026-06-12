---
title: "Baffled"
date: 2008-10-03
forum: Programming Talk
---

### Post by sohaikia1 on 2008-10-03
I wrote a C program that calls the function getenv().The source compiles and runs ok. The thing is I forgot to put '#include <stdlib.h>' in my source code. How come this is possible?

---

### Post by yoda2031 on 2008-10-03
It will compile successfully as long as you don't have "treat warnings as errors" set (not sure how to do this with gcc).  Implicit declarations will exhibit undefined behaviour.  When you say it "runs" ok, that's the bit I'd be worried about - if "getenv()" does what you're expecting it to despite never being declared... I don't know how to help, but you're pretty damn lucky that it does!

It will also not warn you unless you use the -Wall flag (gcc, this is), or maybe one of my other flags... I lose track, sometimes... I think it's -Wall...

Anyway, I hope this clears things up for you :)

---

### Post by nvteighen on 2008-10-03
It will work because getenv() is in the C Std. Library, which is always linked to by the compiler by default. So, the compiler may complain because it won't be able to check whether you're passing the correct parameters to getenv() or not (that's the whole point of header files), but it will happily continue the process, leaving the symbol "getenv" pending for being processed by the linker, as you haven't defined the function anywhere (the header file will just declare it).

Then, the linker looks up the symbols and makes them refer to the libraries you are linking to. As the "getenv" symbol is found in the Std. Library, it succesfully finishes compilation up; but, if you were asking for the function gtk_widget_destroy() without linking to the GTK+ libraries, it would fail.

---

### Post by Lux Perpetua on 2008-10-03
The compiler should warn you if you call a function without having its declaration. However, it may well be that a declaration is already included by one of your other includes, in which case the compiler will see it and not complain. This is more common than you might think. For example, you probably use the definitions in stddef.h all the time, but chances are you don't usually include stddef.h explicity because it is used by other standard headers.

---

### Post by LaRoza on 2008-10-03
> **sohaikia1 said:**
> I wrote a C program that calls the function getenv().The source compiles and runs ok. The thing is I forgot to put '#include <stdlib.h>' in my source code. How come this is possible?

To clarify, the header files (*.h) have no functioning C code in them. It is all prototypes and preprocessor directives. (The closest you to get function code are macros).

Essentially, you are just calling a defined function without a prototype, as the c stdlib is linked automatically, but there is a switch to turn that off and you'd have to link manually (if you used it) (the switch is in the man page).

---

### Post by dribeas on 2008-10-04
> **LaRoza said:**
> To clarify, the header files (*.h) have no functioning C code in them. It is all prototypes and preprocessor directives.

To be precise, you forgot inlines, which are real function definitions, but that is just a side note. More often than not, your right and there are no function definitions.

---

### Post by LaRoza on 2008-10-04
> **dribeas said:**
> To be precise, you forgot inlines, which are real function definitions, but that is just a side note. More often than not, your right and there are no function definitions.

inlines? What is that? inline is a C++ keyword.

---

### Post by dribeas on 2008-10-04
> **LaRoza said:**
> inlines? What is that? inline is a C++ keyword.

Inline is both a C (C99) and a C++ keyword. GCC has its own inline rule, which is not standard. The rules for inlines are a little tricky, but they are there.

First two google references: [Inline functions in C]("http://www.greenend.org.uk/rjk/2003/03/inline.html") and [wikipedia|[http://en.wikipedia.org/wiki/Inline_function]](http://en.wikipedia.org/wiki/Inline_function]) article on inlines (in general, with some C specifics)

---

