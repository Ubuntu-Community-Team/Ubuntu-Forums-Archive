---
title: "make - custom kernel module  include rpmp.h"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by weiserhood on 2012-02-17
Hey i am fairly new to t he world of linux but have been writing c code for a few years. I am writing a custom kernel module that hooks into netfiltters inside the kernel. I have used the forums before to find answers to my problems other people have already solved though this time i came up short. So I am posting my own thread 

 I have some code taken from an online example as my_module.c their is a call to include a header file 
#include 'rpmp.h'

when I run make on the file (Makefile I am pretty sure is correct) 
i get told that the file does not exist in my headers file which is true. 

this rpmp.h has many functions which i need to call apparently can anyone tell me what it is and or where I can get the header files to include it. 
I am running Ubuntu 11, on kernel linux-3.0.0-12-generic 
any help or knowledge of rpmp.h and its functionality would be greatly apreciated as i cant find much online documenting it 

cheers, 
Brendan

---

