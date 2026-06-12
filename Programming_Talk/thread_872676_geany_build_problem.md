---
title: "geany build problem"
date: 2008-07-28
forum: Programming Talk
---

### Post by hammeraxe on 2008-07-28
I am trying to compile a C++ project in geany. Each of the separate source files compiles without errors and produces an object file. The problem is: when I try to build the executable it throws a whole bunch of errors at me.
All of them go like: 
```

undefined reference to 'some_function_from_included_file()'  

```

It seems that geany is ignoring my #include statements. Could this be true? Or am i doing something wrong?

---

### Post by dribeas on 2008-07-28
> **hammeraxe said:**
> I am trying to compile a C++ project in geany. Each of the separate source files compiles without errors and produces an object file. The problem is: when I try to build the executable it throws a whole bunch of errors at me.
All of them go like: 
```

undefined reference to 'some_function_from_included_file()'  

```

It seems that geany is ignoring my #include statements. Could this be true? Or am i doing something wrong?

It's probably in stickies... You must differentiate between compile and link time errors. 'undefined reference' is a link time error and has nothing to do with #include's but with the libraries you are (not) linking against.

   David

---

### Post by hammeraxe on 2008-07-28
This is not about external libraries. I have a self-made header #included. Every time I call a function declared in that header I get this error i mentioned above. Do i have to add any special command line options for this to work? I couldn't find anything useful in the stickies (probably because i dont know what to look for) :D

---

### Post by galileon on 2008-07-28
at some point you need to link the separate .o files into a single binary, that way it finds the address of the functions. google "g++ link".

---

