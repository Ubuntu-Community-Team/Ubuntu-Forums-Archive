---
title: "problem compiling a bash script with shc"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by alfredoq on 2013-02-22
Good afternoon everyone. I want to set an environment variable using a binary executable, so I constructed  the following script (test.sh):

#!/bin/bash 
export TEST=/usr/bin


When I open a new console and type:

. ./test.sh

the environment variable is set. However, after compiling this script with "shc" and executing the resulting binary with:

./binary_file

the environment is not set

Any help on how to tackle this problem is greatly appreciated,

kind regards

Alfredo

---

### Post by cybergalvez on 2013-02-22
from the website 
> shc itself is not a compiler such as cc, it  rather  encodes
     and encrypts a shell script and generates C source code with
     the added expiration capability. It  then  uses  the  system
     compiler  to compile a stripped binary which behaves exactly
     like the  original  script.  Upon  execution,  the  compiled
     binary  will  decrypt and execute the code with the shell -c
     option.  Unfortunatelly, it will  not  give  you  any  speed
     improvement as a real C program would.

so it looks like your script is run in a separate shell which is why the variable is not set. 

just a quess on my part

---

