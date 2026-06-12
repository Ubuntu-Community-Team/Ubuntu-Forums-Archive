---
title: "GDB breakpoint problem"
date: 2010-02-17
forum: Programming Talk
---

### Post by EricDallal on 2010-02-17
I am trying to set breakpoints for a C++ program that I compiled with the -g flag. I can set breakpoints by calling break <function name>, but not by calling break <line number>. I am getting the following error:

Error in re-setting breakpoint 3: Function "MPO" not defined.

Anybody have a clue why this happens?

Thank you immensely for any help.

---

### Post by nvteighen on 2010-02-17
> **EricDallal said:**
> I am trying to set breakpoints for a C++ program that I compiled with the -g flag. I can set breakpoints by calling break <function name>, but not by calling break <line number>. I am getting the following error:

Error in re-setting breakpoint 3: Function "MPO" not defined.

Anybody have a clue why this happens?

Thank you immensely for any help.

Very probably because C++ function names are mangled... I never used GDB to debug C++ programs (I actually almost don't use C++ :p), but it's the only logical reason I can think of.

Is it a class method? If it is, maybe using class::method may help you.

---

### Post by EricDallal on 2010-02-17
There are no classes in the file. Furthermore, there is no function called MPO. The file is called "MPO 2.cpp". The word MPO doesn't appear anywhere in the file (except in comments). Could this be a problem related to the fact that there is a space in the file name?

---

### Post by EricDallal on 2010-02-17
Ok wow. That actually seems to be the problem. I can't understand why there are so many programs in linux that just explode whenever they see a space.

---

### Post by sharpdust on 2010-02-17
> **EricDallal said:**
> Ok wow. That actually seems to be the problem. I can't understand why there are so many programs in linux that just explode whenever they see a space.

Rule of thumb is to never use any of the following characters: space, &, *, \, $, and ?.

I won't go over all the characters, but the space problem is the way programs in *nix handle passed in arguments.
For example:

```
g++ SomeProgram .cpp
```

g++ thinks you sent it two arguments SomeProgram and .cpp.

To resolve this issue, you need to either escape the space, or quote the entire input.

Escaping the space

```
g++ SomeProgram\ .cpp
```

Quoting the input

```
g++ 'SomeProgram.cpp
```

But to make things easier, just never put a space in a file name.

---

