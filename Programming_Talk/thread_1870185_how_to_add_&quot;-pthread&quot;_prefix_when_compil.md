---
title: "how to add &quot;-pthread&quot; prefix when compiling in IDE like geany or code::blocks ?"
date: 2011-10-26
forum: Programming Talk
---

### Post by shevin on 2011-10-26
guys
I want to write and compile a program that has pthread in it in IDE . 

 in terminal I use -pthread option of gcc to compile it, (otherwise I would get error frmo gcc) but in IDEs like geany or code::blocks I dont know how to tell it to use -pthread when it compiles so it deosnt give me error ?


btw, which IDE , I should use for programs in C ?

---

### Post by NovaAesa on 2011-10-27
For code blocks:

Go to settings -> compiler and debugger -> linker setting and add pthread there.

As for which IDE, use whichever one you like the best.

---

### Post by shevin on 2011-10-27
in the linker setting I can see
Other linker options , shall I enter -pthread ? or pthread or what

---

