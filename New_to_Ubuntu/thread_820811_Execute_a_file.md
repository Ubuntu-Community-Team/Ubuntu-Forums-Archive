---
title: "Execute a file"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by harsh_ on 2008-06-06
I made a c file naming harsh.c and then executed the following on a terminal: gcc harsh.c and then ./a.out

I wanted to make it an executable file so i used
chmod +x harsh.c
Even that worked, but now- how do i execute it further...is there any command or ./a.out is the only command; because if i have more than 1 .c files; ./a.out will correspond to last compiled file...is there no way to store the object form???

---

### Post by KingTermite on 2008-06-06
First of all,  you don't need to make the source file exectuable, only the executable file (hence its name), a.out. Although, it should set a.out to be executable by default when you compile it.

I'm new to Linux and haven't started developing anything just yet, but from when I used to use Unix back at school (10 years ago), sometimes we had to put an "@" in front of the file (or was that just scripts???).

---

### Post by KingTermite on 2008-06-06
> **harsh_ said:**
> because if i have more than 1 .c files; ./a.out will correspond to last compiled file...is there no way to store the object form???
If you have more than 1 .c file for the same project or do you  mean each a different program?

If each a different program then you can use a switch to tell gcc to name the output executable file something other than a.out so each had an appropriate name.

if each c file is part of the same project then you start getting into really long command lines or need to create a make file (or use an IDE like Eclipse).

---

### Post by The Cog on 2008-06-06
As king termite says, if it's a single source file program, you can tell gcc to rename the output file. like this:
gcc -o myprog myprog.c
which produces an executable called myprog. Of course, you can just rename a.out instead.

---

### Post by Joeb454 on 2008-06-06
True you can rename a.out :) Usually when compiling C app's, I would run ```
gcc file.c -o myfile
``` Then I would run ```
./myfile
``` :)

---

### Post by stchman on 2008-06-06
> **harsh_ said:**
> I made a c file naming harsh.c and then executed the following on a terminal: gcc harsh.c and then ./a.out

I wanted to make it an executable file so i used
chmod +x harsh.c
Even that worked, but now- how do i execute it further...is there any command or ./a.out is the only command; because if i have more than 1 .c files; ./a.out will correspond to last compiled file...is there no way to store the object form???

The .c file is source code and therefore does not need to be executable.

Once you compile the .c source code it will create an executable program.  Use the following command to compile it.

```
gcc -o harsh harsh.c
```

This will create an executable program called harsh.

---

### Post by harsh_ on 2008-06-07
Thanks a tonne guys....
Finally it works

---

