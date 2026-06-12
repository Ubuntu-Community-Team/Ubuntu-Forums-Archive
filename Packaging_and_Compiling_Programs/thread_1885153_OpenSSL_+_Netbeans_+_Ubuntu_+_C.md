---
title: "OpenSSL + Netbeans + Ubuntu + C"
date: 2011-11-22
forum: Packaging and Compiling Programs
---

### Post by ang3lo on 2011-11-22
Hi guys


I am having a problem in Ubuntu 11.10 + Netbeans 7.01 because I can't compile my C program that uses openssl.


I installed the "libssl-dev" through comand line and when I use the command 'pkg-config --libs openssl' it returns '-lssl -lcrypto'. So the openssl lib installation was done properly right?


However when I compile the project in the Netbeans I get these messages

```
main.c:(.text+0x11d): undefined reference to `SSL_load_error_strings'
main.c:(.text+0x122): undefined reference to `SSL_library_init'
main.c:(.text+0x127): undefined reference to `SSLv23_client_method'
main.c:(.text+0x12f): undefined reference to `SSL_CTX_new'
main.c:(.text+0x14c): undefined reference to `ERR_print_errors_fp'
main.c:(.text+0x15a): undefined reference to `SSL_new'
main.c:(.text+0x177): undefined reference to `ERR_print_errors_fp'
main.c:(.text+0x18e): undefined reference to `SSL_set_fd'
main.c:(.text+0x19f): undefined reference to `ERR_print_errors_fp'
main.c:(.text+0x1ad): undefined reference to `SSL_connect'
main.c:(.text+0x1bf): undefined reference to `ERR_print_errors_fp'
```

As far as I know the problem apparently is in the linker, but I don't know how to solve this. Can anyone help me please?

Thanks Guys

---

### Post by Bachstelze on 2011-11-22
What command are you compiling with? Yes, I know you said you are using Netbeans. What command does it run?

---

### Post by ang3lo on 2011-11-22
If I am correct I have to use the '-lcrypto -lssl" right? In the Netbeans project options I tried to place those arguments the maybe I am putting them in the wrong place. The full compiler output is this, where it is possible to see that the Netbeans compiling command if I not wrong is 

> gcc -Wall -lssl -lcrypto   -c -I/usr/include/openssl -MMD -MP -MF build/Debug/GNU-Linux-x86/main.o.d -o build/Debug/GNU-Linux-x86/main.o main.c



```
"/usr/bin/make" -f nbproject/Makefile-Debug.mk QMAKE= SUBPROJECTS= .clean-conf
make[1]: Entering directory `/home/ang3lo/NetBeansProjects/ssl_demo'
rm -f -r build/Debug
rm -f dist/Debug/GNU-Linux-x86/ssl_demo
make[1]: Leaving directory `/home/ang3lo/NetBeansProjects/ssl_demo'

CLEAN SUCCESSFUL (total time: 116ms)
"/usr/bin/make" -f nbproject/Makefile-Debug.mk QMAKE= SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/ang3lo/NetBeansProjects/ssl_demo'
"/usr/bin/make"  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/ssl_demo
make[2]: Entering directory `/home/ang3lo/NetBeansProjects/ssl_demo'
mkdir -p build/Debug/GNU-Linux-x86
rm -f build/Debug/GNU-Linux-x86/main.o.d
gcc -Wall -lssl -lcrypto   -c -I/usr/include/openssl -MMD -MP -MF build/Debug/GNU-Linux-x86/main.o.d -o build/Debug/GNU-Linux-x86/main.o main.c
mkdir -p dist/Debug/GNU-Linux-x86
gcc -Wall -lssl -lcrypto    -o dist/Debug/GNU-Linux-x86/ssl_demo build/Debug/GNU-Linux-x86/main.o -L/usr/include/openssl 
build/Debug/GNU-Linux-x86/main.o: In function `sslConnect':
main.c:(.text+0x11d): undefined reference to `SSL_load_error_strings'
main.c:(.text+0x122): undefined reference to `SSL_library_init'
main.c:(.text+0x127): undefined reference to `SSLv23_client_method'
main.c:(.text+0x12f): undefined reference to `SSL_CTX_new'
main.c:(.text+0x14c): undefined reference to `ERR_print_errors_fp'
main.c:(.text+0x15a): undefined reference to `SSL_new'
main.c:(.text+0x177): undefined reference to `ERR_print_errors_fp'
main.c:(.text+0x18e): undefined reference to `SSL_set_fd'
main.c:(.text+0x19f): undefined reference to `ERR_print_errors_fp'
main.c:(.text+0x1ad): undefined reference to `SSL_connect'
main.c:(.text+0x1bf): undefined reference to `ERR_print_errors_fp'
build/Debug/GNU-Linux-x86/main.o: In function `sslDisconnect':
main.c:(.text+0x206): undefined reference to `SSL_shutdown'
main.c:(.text+0x214): undefined reference to `SSL_free'
main.c:(.text+0x22c): undefined reference to `SSL_CTX_free'
build/Debug/GNU-Linux-x86/main.o: In function `sslRead':
main.c:(.text+0x2f3): undefined reference to `SSL_read'
build/Debug/GNU-Linux-x86/main.o: In function `sslWrite':
main.c:(.text+0x3a4): undefined reference to `SSL_write'
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/ssl_demo] Error 1
make[2]: Leaving directory `/home/ang3lo/NetBeansProjects/ssl_demo'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/ang3lo/NetBeansProjects/ssl_demo'
make: *** [.build-impl] Error 2

BUILD FAILED (exit value 2, total time: 668ms)
 

```

---

### Post by Bachstelze on 2011-11-22
Yes, the parameters are correct but you are putting them in the wrong place. The command should be:

```
gcc -Wall -c -I/usr/include/openssl -MMD -MP -MF build/Debug/GNU-Linux-x86/main.o.d -o build/Debug/GNU-Linux-x86/main.o main.c -lssl -lcrypto
```

---

### Post by ang3lo on 2011-11-22
Thank you for the reply, but do you know where in the Netbeans I can/should place that? Because I tried before but I was no able to find where and how show I place the arguments so they are in correct order.

Thanks

---

### Post by Bachstelze on 2011-11-22
Sorry, I don't use Netbeans (or any IDE, for that matter).

---

### Post by ang3lo on 2011-11-22
But in you opinion the problem is the order of the arguments right?
I will try to figure it out them and see if I get any luck on that.

---

### Post by Bachstelze on 2011-11-22
> **ang3lo said:**
> But in you opinion the problem is the order of the arguments right?
I will try to figure it out them and see if I get any luck on that.

It's not "in my opinion", that's definitely the problem. But I can't tell you how to change the ordering in Netbeans, because I don't use it.

---

### Post by ang3lo on 2011-11-25
Hi, 

Thanks for the help, the problem in finally solved.
The solution in Netbeans is like this

Project Properties -> Linker -> Libraries -> clic on the 3 dots -> add option -> other option -> and add -lcrypto and -lssl separately

Now the program will be compiled ;)

---

