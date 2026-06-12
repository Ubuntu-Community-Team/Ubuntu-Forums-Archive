---
title: "Error while running Makefile library. thanks for your help"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by FarahMakki1992 on 2012-10-06
the error:  farah@farah-VirtualBox:~$ gcc libmy_string.a /usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/crt1.o: In function `_start': (.text+0x18: undefined reference to `main' collect2: ld returned 1 exit status   and the code for the library is as follows:
  library : my_string.o
        ar rcs libmy_string.a my_string.o
run: string_compare.c
        gcc -o run string_compare.o -L. -lmy_string
string_compare.o: string_compare.c my_string.h
                gcc -c string_compare.c
my_string.o: my_string.c my_string.h
                gcc -c my_string.c

  library : my_string.o
        ar rcs libmy_string.a my_string.o
.PHONY: clean
clean:
        rm -rf *.o run

  thank you for your help in advance additional information: my main method is in string_compare.c and method  and header are my_string.c and my_string.h respectively

---

