---
title: "segmentation fault on 32 bit system but not on 64 bit"
date: 2011-04-19
forum: Programming Talk
---

### Post by ibtkm on 2011-04-19
hi all.
i have a special program in c++ language . when I make it on 64 bit system and start it then it works normally.
but when i make it on 32 bit system and start it then it will have a segmentation fault.
how can i solve this problem or how can i find the root of the problem?

tnx a lot.

---

### Post by NovaAesa on 2011-04-19
Start with compiling with the -g flag, then run the program in gdb to see where the seg fault is occuring. Are you the author of the program?

---

### Post by slavik on 2011-04-19
> **ibtkm said:**
> hi all.
i have a special program in c++ language . when I make it on 64 bit system and start it then it works normally.
but when i make it on 32 bit system and start it then it will have a segmentation fault.
how can i solve this problem or how can i find the root of the problem?

tnx a lot.
we are mind readers and can spot issues in your code ...

---

### Post by nvteighen on 2011-04-19
Just in case: are you recompiling the code for each platform or did you use the same executable on both? 

If you are recompiling it in 32 and 64-bit, then I bet that code relies on some undefined behaivor. Do what NovaAesa has told you, but please show us the failing code if you don't know how to proceed.

---

### Post by ibtkm on 2011-04-19
at first i should say that my source code is big and i can't put them here. my main problem is an extraordinary problem. i don't have only seg fault problem. when i add some cout to my source code to debugging my program then we will have a seg fault in another line! i can't understand how cout can change the program process.
by the way I have an another problem. i use -g flag in make file and so i can list my source code in gdb and i can find the feg faulted line. but in this case it doesn't show the line number! it is not normal.

does anybody have a special idea?

---

### Post by Npl on 2011-04-19
Theres not much to say without seeing code, other that it seems to be seriously bugged.

And if you wonder, standard methods like cout failing can easily be the result of previously encountered bugs (which dont have to report to you but just mess up the state of the program, think about puring sand into a gastank - it wont show until you start the engine). run your program through valgrind, this can help you to figure out when things go wrong.

---

### Post by ssam on 2011-04-19
you have a heisenbug

segfaults tend to be caused by things like using uninitialised memory, writing off the end of an array and similar bugs. what happens when you do this depends highly on the memory layout of your program. if you write to an element beyond an array it may land in some other bit of your programs data that is not going to be used again, and so be harmless. or it may overwrite something important which then causes something to segfault.

things like changing compiler options, or adding extra code can cause data to be in different places.

gdb can often get you a backtrace of where the problem is. valgrind may be able to spot use of uninitialised memory.

i think there are some stack protection options in gcc that may help find some bugs. also make sure you have all the gcc warnings turned on, and have a check through them.

---

