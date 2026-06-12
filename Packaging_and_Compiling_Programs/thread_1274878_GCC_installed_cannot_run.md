---
title: "GCC installed cannot run"
date: 2009-09-25
forum: Packaging and Compiling Programs
---

### Post by MM12 on 2009-09-25
So i installed GCC from the synaptic package manager, installed successfully... but how do i open it, it's not anywhere in my menus. there is probably a terminal command for it but i have no idea what it is, i did type in GCC just to see if something comes up but nothing did. I also tried running the executables in the /usr/bin folder but nothing popped up on my screen.

I really need GCC to work so i have a C++ program for school, i tried MS visual express and hated it, and bloodshed dev C++ but it wasn't working on vista. I want GCC because i know it will just work. Thanks for any help you can lend me!

-MM12

---

### Post by lisati on 2009-09-25
gcc is commonly run from the command line (applications->accesories->terminaL), other forum users might be able to point you to an IDE that appears in the menu.

example: 
```
gcc filename.c -o outputfile[code]
Assuming the compilation was successful, you'd then type the following to run the program:
[code]./outputfile
```
(Replace "filename.c" and "outputfile" with whatever you want to call your program)

---

### Post by MM12 on 2009-09-25
ok so there is less of an interface? and more of a notepad/terminal way of doing it? so i write all the code in terminal? the attempt to compile from there?

should i look into getting Bloodshed Dev C++ for linux? (Bloodshed is what i use at school so it may be a good choice)

Thanks!

---

### Post by unmole on 2009-09-25
GCC is only a compiler not an IDE. So to compile a program, first use gedit to write your code,save it as filename.cc in your home directory then in the terminal run 

c++ filename.cc -o outputfilename

If it compiles without any errors,you can  run your program by typing ./outputfile in the terminal

---

### Post by unmole on 2009-09-25
IF you want an IDE try installing Anjuta from the repos

---

### Post by MM12 on 2009-09-25
awesome guys, thanks i think i'll use the two options together to create some well relatively noob code :-) Thanks for all the quick responses!!!

---

