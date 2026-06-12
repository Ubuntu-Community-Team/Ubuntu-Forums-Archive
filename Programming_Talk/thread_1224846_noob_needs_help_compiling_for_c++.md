---
title: "noob needs help compiling for c++"
date: 2009-07-27
forum: Programming Talk
---

### Post by Titan00 on 2009-07-27
hey guys,
I'm sure tis has been asked before, but I can't find it after searching google for a while.  See I'm in college and I like to do little programs like input a input b a plus b is c.  Simple stuff.  I'm trying to do that with ubuntu in C++, but so far, i have no luck compiling.  I'm using anjuta, which I'm not entirely sure is the correct program to use, and I'm saving the source file as a .cxx file.  It's in my /home/shaw folder, so now what.  I can use the terminal to do this right?  Or can I use anjuta to compile and run it?  

Any help would be awesome!


ps I'm a total linux noob (finally kicked vista last week) so I'm gonna need serious step by step instructions.  thanks!

---

### Post by Danzyg on 2009-07-27
I am in no position  to help, mostly because I am in the same boat as you. Except for the fact that you are older and seem to know more than me already ... I am having the same issue with compiling for C++ and would also like to see the answer to this question =)

---

### Post by monraaf on 2009-07-27
[[COLOR="Blue"]_Sticky: Programming Tools and References_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1006662")

---

### Post by Krupski on 2009-07-28
> **Titan00 said:**
> hey guys,
I'm sure tis has been asked before, but I can't find it after searching google for a while.  See I'm in college and I like to do little programs like input a input b a plus b is c.  Simple stuff.  I'm trying to do that with ubuntu in C++, but so far, i have no luck compiling.  I'm using anjuta, which I'm not entirely sure is the correct program to use, and I'm saving the source file as a .cxx file.  It's in my /home/shaw folder, so now what.  I can use the terminal to do this right?  Or can I use anjuta to compile and run it?  

Any help would be awesome!


ps I'm a total linux noob (finally kicked vista last week) so I'm gonna need serious step by step instructions.  thanks!

We can't do schoolwork or homework for you, but if you post the code you wrote so far, someone here could give you some pointers (no pun intended)!  :)

---

### Post by Krupski on 2009-07-28
> **Danzyg said:**
> I am in no position  to help, mostly because I am in the same boat as you. Except for the fact that you are older and seem to know more than me already ... I am having the same issue with compiling for C++ and would also like to see the answer to this question =)

What kind of problem compiling do you have? Compiler error messages? Resulting code doesn't work? Don't even know how to use the compiler?

Need more info.

---

### Post by James- on 2009-07-28
Anjuta should be able to compile/run it for you, I believe it's under Project->Build then go Project->Run, personally I don't like anjuta, because it doesn't have the "intellisense". I like eclipse(but porting project is problematic) and code::blocks

Each one has it's ups and downs =)

---

### Post by kjohansen on 2009-07-28
if you open a terminal in your home file you can type:

```

g++ filename.cpp -o filename

```

This assumes that you have build-essetials installed.  

```

sudo apt-get install build-essentials

```

---

