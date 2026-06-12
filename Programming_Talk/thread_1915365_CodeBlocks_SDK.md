---
title: "CodeBlocks SDK"
date: 2012-01-26
forum: Programming Talk
---

### Post by vanangamudi on 2012-01-26
I hav installed codeblocks SDK but cannot find where it has been installed... I'm developing Arduino Plugin for CodeBlocks....

---

### Post by bouncingwilf on 2012-01-26
Not sure what you're looking for but I suspect you will find it in .Codeblocks in your home directory - Use ctrl-h to see hidden directory/files.

Bouncingwilf

---

### Post by vanangamudi on 2012-01-26
> **bouncingwilf said:**
> Not sure what you're looking for but I suspect you will find it in .Codeblocks in your home directory - Use ctrl-h to see hidden directory/files.

Bouncingwilf


Yeah I found it. now the problem wxprec.h file. i know the location of the file but how do I include this file to compiler..
lik pkg-config codeblocks --cflags

sumthng like that for wxWidgets....

---

### Post by vanangamudi on 2012-01-26
I found it

```
` wx-config --libs`
```

thats the command to include wxWidget libs.....

similarly to include wxWidgets header files

```
` wx-config --cflags`
```

---

### Post by bouncingwilf on 2012-01-26
From memory it's something like:
Settings -> Compiler and Debugger -> Other options    

add any other include paths there 

Bouncingwilf

---

