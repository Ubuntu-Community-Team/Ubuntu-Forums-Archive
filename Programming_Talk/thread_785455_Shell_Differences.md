---
title: "Shell Differences"
date: 2008-05-07
forum: Programming Talk
---

### Post by picopir8 on 2008-05-07
Are there any good references that highlight the nuances between different shells.  I have some code written as a sh script but need it to be msh script but as one would expect, simply changing the top line of the file does not make it work.  There are some differences in the syntax that need to be resolved before the code will work as a msh script.

---

### Post by yaaarrrgg on 2008-05-09
> **picopir8 said:**
> Are there any good references that highlight the nuances between different shells.  I have some code written as a sh script but need it to be msh script but as one would expect, simply changing the top line of the file does not make it work.  There are some differences in the syntax that need to be resolved before the code will work as a msh script.

Windows powershell?  I don't think there's any real overlap in the two languages ... meaning you'll probably have to rewrite the script from scratch.  

I couldn't find any good documentation, so I suspect you'd be better off porting to some other cross platform scripting language.

---

### Post by LaRoza on 2008-05-09
> **picopir8 said:**
> Are there any good references that highlight the nuances between different shells.  I have some code written as a sh script but need it to be msh script but as one would expect, simply changing the top line of the file does not make it work.  There are some differences in the syntax that need to be resolved before the code will work as a msh script.

Shells are different by definition, otherwise they wouldn't have different names.

Some are compatible on certain levels. For example, I believe than any script written for dash would work in bash, but not the other way around (I think)

If msh is for Windows powershell, you'll have to rewrite it unless MS made this like a *nix shell.

---

### Post by dwhitney67 on 2008-05-09
> **LaRoza said:**
> Some are compatible on certain levels. For example, I believe than any script written for dash would work in bash, but not the other way around (I think)

You are correct!  I found this out when developing a CLFS (cross-compiled linux from scratch) system.  Some of the instructions given in the guide would not work on Ubuntu, but had no trouble whatsoever when developing under Fedora.  Soon after I found out that Ubuntu uses dash, which is a subset of bash.

Here's a command I could not get to work with dash:
```
$ cp file.{cpp,bak}
```

This command is the same as:
```
$ cp file.cpp file.bak
```

---

### Post by slavik on 2008-05-10
differences in shells are like differences in programming languages, there are no nuacenses, just completely different languages (syntax differences are substantial as are features)

---

### Post by picopir8 on 2008-05-15
Sorry for the confusion, msh is "Minimal Shell".  It is a stripped down shell that is sometimes used in initrd to keep the size down.  I do not use Windows so I was unaware that msh also meant microsoft shell.

I do have a couple shell reference books, but it would be nice if there was a single reference which highlights the syntactical differences.

---

### Post by slavik on 2008-05-15
> **picopir8 said:**
> Sorry for the confusion, msh is "Minimal Shell".  It is a stripped down shell that is sometimes used in initrd to keep the size down.  I do not use Windows so I was unaware that msh also meant microsoft shell.

I do have a couple shell reference books, but it would be nice if there was a single reference which highlights the syntactical differences.

I agree, but writing a book to highlight the syntactical differences would be a large undertaking (to start, what shells should be compared?)

I say, use zoidberg. :P

---

