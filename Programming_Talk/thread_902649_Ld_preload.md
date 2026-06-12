---
title: "Ld_preload"
date: 2008-08-27
forum: Programming Talk
---

### Post by lookforlohith on 2008-08-27
sir 
i have a problem with LD_PRELOAD

it not loading please help

i have 2 files 

main.c , foo.c

main.c

#include<stdio.h>
int main()
{
foo();
}

foo.c

#include<stdio.h>
foo()
{
printf("lohith");
}

cc -o libfoo.so foo.c
created a shared library 

libfoo.so

now if i do

$export LD_PRELOAD=`pwd`/libfoo.so

and im compiling 
$cc main.c

i expect it to run properly because libfoo.so must be preloaded and foo should print 
$lohith

but


lohi@look:~/cl/ld$ ls
libfoo.so  main.c  
lohi@look:~/cl/ld$ echo $LD_PRELOAD

lohi@look:~/cl/ld$ export LD_PRELOAD=`pwd`/libfoo.so
lohi@look:~/cl/ld$ echo $LD_PRELOAD
/home/lohi/cl/ld/libfoo.so
lohi@look:~/cl/ld$ 
lohi@look:~/cl/ld$ cc main.c
/tmp/ccPN7BtV.o: In function `main':
main.c:(.text+0x12): undefined reference to `foo'
collect2: ld returned 1 exit status
lohi@look:~/cl/ld$


this is the error


/tmp/ccPN7BtV.o: In function `main':
main.c:(.text+0x12): undefined reference to `foo'
collect2: ld returned 1 exit status


y is it ???????????
please help

---

### Post by jpeddicord on 2008-08-27
Moved to Programming Talk.

---

