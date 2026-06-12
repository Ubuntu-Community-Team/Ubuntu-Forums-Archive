---
title: "make: Nothing to be done for '{file_name}."
date: 2015-05-15
forum: New to Ubuntu
---

### Post by nicholas7 on 2015-05-15
I just installed Ubuntu and am trying to compile a .c file i created with make (file) and it prints...

```
make: Nothing to be done for '{file_name}'.
```

I googled I saw that I had to type ./configure in... (says its a unknown command) and I had to edit a file called 'MakeFile' which I don't have... Any ideas on how to fix please?

---

### Post by steeldriver on 2015-05-15
What is the name of the .c file, and what command did you type exactly? 

It is possible to use `make` without a makefile (it will attempt to do something sensible based on the target and source files), but you at least give it a target e.g. if you have a file called hello.c then

```

make hello

```

should attempt to invoke a suitable C-compiler - something like
```

cc     hello.c   -o hello

```

---

### Post by nicholas7 on 2015-05-15
> **steeldriver said:**
> What is the name of the .c file, and what command did you type exactly? 

It is possible to use `make` without a makefile (it will attempt to do something sensible based on the target and source files), but you at least give it a target e.g. if you have a file called hello.c then

```

make hello

```

should attempt to invoke a suitable C-compiler - something like
```

cc     hello.c   -o hello

```

I had a file called hello.c, and ran
```
make hello.c
```
And the error pops up... Because of this i have to manually type out tons of arguments, which is a real pain.

---

### Post by nicholas7 on 2015-05-16
Found out the error was I typed in .c at the end of the make, thanks for your help!

---

