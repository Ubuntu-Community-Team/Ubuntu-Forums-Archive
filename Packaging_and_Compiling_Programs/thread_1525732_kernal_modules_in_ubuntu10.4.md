---
title: "kernal modules in ubuntu10.4"
date: 2010-07-07
forum: Packaging and Compiling Programs
---

### Post by malazhussein on 2010-07-07
hello everyone,
i am a new member in Ubuntu forums , and i have a problem on dealing with kernel module in Ubuntu 10.4 , and that is i am writing a program to capture running processes's information with the struct task_struct using c or c++. i found a program contain the header file linux/module.h but the comilers gcc and g++ couldn't recognize this library , when i search in internet i found that i must download a package called linux header and i found many packages in the Ubuntu software center including "generic complete linux kernel" , " header files related to linux kernel version....." that is too many versions and i don't know which one of them to download. i download some of them but still have the error :
"error: linux/module.h: No such file or directory"
please,help me

---

### Post by kemra on 2010-07-07
You will need the linux kernel header file with the same version number as the kernel you are currently running. If memory serves you can install the correct files with this:

```
sudo apt-get install kernel-headers-`uname -v`
```

---

### Post by malazhussein on 2010-07-08
i try that command line and it gave me :
"
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-headers-#37-Ubuntu
"
and when i type:uname -a
i get:Linux ubuntu 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
so i type :
sudo apt-get install kernel-headers-2.6.32-23-generic


but it didn't work , also:
sudo apt-get install kernel-headers-2.6.32-23-generic #37-Ubuntu

---

### Post by SevenMachines on 2010-07-08
hi, try
$sudo apt-get install linux-headers-`uname -r`

---

### Post by malazhussein on 2010-07-08
thank you for reply,
but i want kernel modules header and the execution of the previous command line gave me that the headers are already installed.when i execute the program with the library #include <linux/module.h> it still give me error: No such file or directory
if there is anybody know how to execute the program (kernel module) using the makefile,please tell me

---

### Post by SevenMachines on 2010-07-08
normally you'd add the path to the includes to the compiler using -I/path/to/includes/ but if memory serves right, kernels are a little different. You can use something like the makefile in the example below, in this case for a source file called hello.c, replace the obj-m line with your own examples and it should make the module for you 
> [COLOR=#000000]obj-m += hello.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean[/COLOR]this came from the [linux kernel module tutorial]("http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN121") if you want more information, i'd recommend it, its pretty good

[EDIT] note the above example for a very basic module, if you can post the code or a link to it if you're still having problems?

---

### Post by malazhussein on 2010-07-10
thank you sooooooo  much ,that works with me and there is no error in compiling.but when i type :
malaz@ubuntu:~/ser$ insmod hello-5.ko mystring="bebop" mybyte=255 myintArray=-1
to get the execution of the program it gave me:
insmod: error inserting 'hello-5.ko': -1 Operation not permitted


the book is at:
[http://tldp.org/LDP/lkmpg/2.6/html/x323.html](http://tldp.org/LDP/lkmpg/2.6/html/x323.html)

and is there anyway to do this program with c++?,because i am using it together with qt 4

---

### Post by SevenMachines on 2010-07-10
are you running insmod as root?
$sudo insmod hello-5.ko mystring="bebop" mybyte=255 myintArray=-1

as far as i know, but i dont know much kernel stuff, its all in c, all the bits i've seen are. maybe you could hack around to do something to make your own module c++ but i'd probably just keep the module in c myself. maybe someone who's done some kernel modules knows better

---

### Post by malazhussein on 2010-07-10
by sudo,IT'S WORK thank you.
i use hello-1 because it is very simple and i insert it in the kernel and also removed it but it didn't print either "hello world" statement nor "good bye" world statement!!!!!

---

