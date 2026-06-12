---
title: "is C++ programming possible in ubuntu?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by ellankavi on 2008-08-12
i'd like to know if C++ programming/C programming is possible in ubuntu. If it is, pls do tell me how...

---

### Post by null byte on 2008-08-12
Yes, sure it is.

Use gcc/g++ as compiler. If you prefer an IDE, I suggest you [Code::Blocks]("http://codeblocks.org").

---

### Post by Crafty Kisses on 2008-08-12
> **ellankavi said:**
> i'd like to know if C++ programming/C programming is possible in ubuntu. If it is, pls do tell me how...

This link maybe helpful > [http://ubuntuforums.org/showthread.php?t=375812](http://ubuntuforums.org/showthread.php?t=375812)

You'd probably wanna use something called "CodeBlocks"

---

### Post by Eisenwinter on 2008-08-12
Of course it's possible.

It is in fact, easier than in windows.

write your code in a text editor (I recommend gedit, it has excellent syntax highlighting), open up terminal, and type gcc <path to C/CPP file> to compile it.

You'll get a file, in the same path of the source file, called a.out.

In terminal then type <path to a.out file>/a.out.

Example:
```
gcc ~/calc.c
-after compiling is finished-
~/a.out
```

---

### Post by ellankavi on 2008-08-12
that's nice... hope codeblock has GUI:)

---

### Post by null byte on 2008-08-12
> **ellankavi said:**
> that's nice... hope codeblock has GUI:)
Code::Blocks has also wxWidgets for RAD :)

---

### Post by Crafty Kisses on 2008-08-12
> **null byte said:**
> Code::Blocks has also wxWidgets for RAD :)

Yeah, and again I think already stated in this thread, but in some cases Linux is way better for programming and what not, anyway there is great information in the Ubuntu Documentation, you can look there and get a lot more information.

---

### Post by ellankavi on 2008-08-12
installed codeblocks and tried a simple cout program.. this was the error i got:
sh: /home/ellankavi/Desktop/untitled1: Permission denied

Got no error in building

---

### Post by tarps87 on 2008-08-12
> **Eisenwinter said:**
> 
write your code in a text editor (I recommend gedit, it has excellent syntax highlighting), open up terminal, and type gcc <path to C/CPP file> to compile it.


If you type:
g++ <path to C/CPP file> -o <out put filename>
you can name your output file

gcc = c
g++ = c++

emacs is another good text editor for programming

---

### Post by null byte on 2008-08-12
> **ellankavi said:**
> installed codeblocks and tried a simple cout program.. this was the error i got:
sh: /home/ellankavi/Desktop/untitled1: Permission denied

Got no error in building
Terminal:
```

cd Desktop
chmod u+x untitled1
./untitled1

```

---

### Post by ad_267 on 2008-08-12
You have to make the file executable. You can use the command null byte posted to do that or right click on the file and select properties to change permissions.

---

### Post by rabatitat on 2008-08-12
Yes.

gcc also compiles other languages Fortran, C, Assembly, etc.

---

