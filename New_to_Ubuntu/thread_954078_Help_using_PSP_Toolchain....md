---
title: "Help using PSP Toolchain..."
date: 2008-10-20
forum: New to Ubuntu
---

### Post by cjmabry25 on 2008-10-20
**EDIT: I FIGURED OUT MY PROBLEM. SOMETHING I JUST MISTYPED. THANKS**


Hi again! I'm new to ubuntu but learning and am having trouble installing and using the PSP Toolchain. I'm learning to code in C and to  my understanding by installing the PSP Toolchain, this will give me the things I need to convert the source code into an EBOOT, which are PSP game's format.

Anyways, I followed [this]("http://soledadpenades.com/2008/09/01/installing-the-psp-toolchain-in-ubuntu/") guide, but didn't do the part at the bottom that says it was optional because I don't know what that means yet. :) Anyways, after downloading the Toolchain all night, I changed my directory to the psptoolchain, then I created a helloworld directory to store my Hello World app. I made my main.c and Makefile files, but when i navigate to my helloworld directory in the terminal and type make i get this -

```
chris@chris-desktop:~/psptoolchain/psptoolchain/helloworld$ make
psp-gcc -I. -I/usr/local/pspdev/psp/sdk/include -O2 -G0 -Wall -D_PSP_FW_VERSION=150   -c -o main.o main.c
main.c: In function &#8216;SetupCallbacks&#8217;:
main.c:44: warning: &#8216;main&#8217; is normally a non-static function
main.c:50: error: expected declaration or statement at end of input
make: *** [main.o] Error 1

```

I hope this is the right place to post it. I'm new to Ubuntu and C and am not sure if I did this right. If I need to include my main.c or Makefile files I will :) Thanks :)

---

