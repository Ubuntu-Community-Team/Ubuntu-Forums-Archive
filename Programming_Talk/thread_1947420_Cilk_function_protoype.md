---
title: "Cilk function protoype"
date: 2012-03-26
forum: Programming Talk
---

### Post by newport_j on 2012-03-26
I am trying to cilkify some c code using the gnu version of cilk that is discussed in the cilk 5.4.6 manual. I already have a running program that is written in c. It works very well, but it is too slow. I want it to work faster.
 
So I started to cilkify this program, by putting in the word cilk in front of main at the main program line, and adding #include <cilk-lib.cilkh> in the include file section of main.cilk. It compiled easily. I had not spawned or added any cilk for yet.
 
Now I spawn the first function called in cilk main, which was WEG by typing spawn in front of the name of the function WEG that was called and going to the WEG function itself and adding cilk in front of void WEG for cilk void WEG. I also changed the name from WEG.c to WEG.cilk. I added #include <cilk-lib.cilkh> in the include file WEG.cilk. 
 
Everything seemed okay, but when I tried to compile it stated that I was redeclaring WEG.c. Now that makes sense because I did add cilk in front of void WEG and got cilk void WEG. I redclared WEG and its prototype was now incorrect. 
 
I have a function definition header file that has the prototype of all the function used in the program. Upon making the changes outlined in the program above (which merely meant to add cilk in front of void cilk, and adding #include <cilk-lib.cilkh> in the heaer file section of WEG.cilk  
 
The question is where do change of add the cilk void WEG function's prototype? I went to where I orginally defined the prototypes and redefined my defintion of void weg (.... by adding cilk void WEG(... . Now this is not c standard and according to the manual I put the folliwing in:
 
#pragma lang  -c
 
cilk void WEG(...
 
#pragma lang +c
 
 
It did not like it. it gave me the error:
 
expected '=', ',',';', 'asm' or '__attribute__' before 'void'
 
and so forth.
 
I also tried 
 
#pragma lang  +cilk
 
#pragma lang  -cilk
 
aound my redefined WEG function. That also did not work.
 
I am unsure as to what to try next. I read somewhere hat tha also may put cilk function protoypes into a *.cilkh file. This is the latest gnu version of cilk.
 
So what should I do? By cilkifying the existing c code, I am redeclaring void WEG(..., But if I change the existing prototype and then put lines above and below it to show it is not c code, well the compiler does not like it.
 
What do I do?
 
I have also tried to capitalize the commands:
 
#pragma lang  -C
 
cilk void WEG(...
 
#pragma lang +C
 
 
or
 
 
#pragma lang  +Cilk
 
cilk void WEG(...
 
#pragma lang   -Cilk
 
 
That did not work either.
 
What do I change to prototype my cilk function?
 
Any help appreciated. Thanks in advance.
 
 
Newport_j

---

### Post by newport_j on 2012-03-26
Let me just boil this down. Where do you put cilk function prototypes? I tried several ways in the previous pst and none worked. Must I create a separate *.cilkh file?
 
Thanks in advance.
 
 
Newport_j

---

