---
title: "Help for cross compiling test program for openmoko neo free runner phone"
date: 2010-12-06
forum: Packaging and Compiling Programs
---

### Post by sohail_linux on 2010-12-06
Hi everyone ,
May peace be with you , I am trying to cross compile a simple hello world program to run on my openmoko linux phone. I have installed ubuntu-9 on my system and using handhelds crosstool chain arm-linux-gcc-3.3.2.tar.bz2, there are no compile time errors but when i try to run it on phone it says  "line-1 Syntax error: word unexpected (expecting ")") " , thanks

Regards ,
sohail

---

### Post by SevenMachines on 2010-12-06
You would need to post some code and what commands you did to build it for a closer look, although i dont have an armel device to test it myself :(
But, as an example, on the latest ubuntu release which has much better armel cross compiling support.

> $ sudo apt-get install libc6-dev-armel-cross gcc-arm-linux-gnueabi hello.c:
> #include <stdio.h>

int main (int args, char * argv []){
    printf ("Hello!");
    return 0;
}> $ arm-linux-gnueabi-gcc -o hello hello.c 
That *should* build an arm binary as far as i know, but i dont't have an armel device to test it on so hopefully someone else knows better :)

---

### Post by sohail_linux on 2010-12-19
thanks for ur reply , I was using another toolchain which was not built for my device. Now I am using the right toolchaing , ubuntu forums didn't alert me about ur post , anyway ,thanks once again

---

