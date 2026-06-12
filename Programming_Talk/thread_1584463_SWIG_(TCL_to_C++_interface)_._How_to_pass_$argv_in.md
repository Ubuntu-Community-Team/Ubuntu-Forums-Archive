---
title: "SWIG (TCL to C++ interface) . How to pass $argv into my C++ function"
date: 2010-09-29
forum: Programming Talk
---

### Post by agupta_shaan on 2010-09-29
Hi All,

I am creating a interface between my C++ code to a TCL script using SWIG.

There is a function in my root class called 

int analyseFiles(int argc , char** argv)

After SWIG compilation , when i use it in my TCL script like following :

load ./test.so test
set sVersion 1.0
set pRoot [new_Root]
Root_setVersion $pRoot $sVersion 
puts $argv
set status [Root_analyzeFiles $pRoot $argc $argv]

I get the following error :
Error: Type error. Expected a pointer
    while executing
"Root_analyzeFiles $pRoot $argc $argv"
    invoked from within
"set status [Root_analyzeFiles $pRoot $argc $argv]"
    
What i could make out was that the TCL $argv is not being converted into a char**
I dont know how to fix this.

I even tried using %typemap as one weblink suggested but that also gives the same error.

Any help would be highly welcome.

-regards
Abhinav

---

