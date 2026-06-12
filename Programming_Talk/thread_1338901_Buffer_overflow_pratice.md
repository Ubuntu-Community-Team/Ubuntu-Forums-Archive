---
title: "Buffer overflow pratice"
date: 2009-11-26
forum: Programming Talk
---

### Post by jerg on 2009-11-26
ASLR

yes, Address Space Layout Randomization does anyone know how to disable this feature or maybe you can help me otherwise.....


I'm currently learning what happens in memory when a buffer-overflow occurs. I'm reading a book which demonstrates a buffer-overflow and debugs it with the gcc (gdb) compiler.

Here's the basic overflow program from the book:
```

//overflow.c
[COLOR="Red"]#include <string.h>[/COLOR]

main(){
   char str1[10];			//declare a 10 byte string
   //next copy 35 bytes of "A" to str1
   strcpy (str1, "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA");
}

```

For some reason the book didn't include the the string header file (<string.h>). I placed it in myself to make compilation possible.

Anywayz when I followed the book instructions which went like this:

```

$                         //notice we start out at user privileges "$"
$gcc &#8211;ggdb &#8211;o overflow overflow.c
./overflow
09963:   Segmentation fault

```

```

$gdb &#8211;q overflow
(gdb) run
Starting program: /book/overflow
Program received signal SIGSEGV, Segmentation fault.
0x41414141 in ?? ()
(gdb) info reg eip
eip            0x41414141        0x41414141
(gdb) q
A debugging session is active.
Do you still want to close the debugger?(y or n) y
$

```

But when I tried it I got a different results, here is the output when I ran my program:

```

$ ./overflow
*** stack smashing detected ***: ./overflow terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7f67da8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7f67d60]
./overflow[0x804845c]
[COLOR="Red"][0x41414141][/COLOR]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:06 3704767    /home/ordonez/Documents/Development/C/overflow
08049000-0804a000 r--p 00000000 08:06 3704767    /home/ordonez/Documents/Development/C/overflow
0804a000-0804b000 rw-p 00001000 08:06 3704767    /home/ordonez/Documents/Development/C/overflow
0804b000-0806c000 rw-p 0804b000 00:00 0          [heap]
b7e5a000-b7e67000 r-xp 00000000 08:06 368705     /lib/libgcc_s.so.1
b7e67000-b7e68000 r--p 0000c000 08:06 368705     /lib/libgcc_s.so.1
b7e68000-b7e69000 rw-p 0000d000 08:06 368705     /lib/libgcc_s.so.1
b7e69000-b7e6a000 rw-p b7e69000 00:00 0 
b7e6a000-b7fc6000 r-xp 00000000 08:06 386037     /lib/tls/i686/cmov/libc-2.9.so
b7fc6000-b7fc7000 ---p 0015c000 08:06 386037     /lib/tls/i686/cmov/libc-2.9.so
b7fc7000-b7fc9000 r--p 0015c000 08:06 386037     /lib/tls/i686/cmov/libc-2.9.so
b7fc9000-b7fca000 rw-p 0015e000 08:06 386037     /lib/tls/i686/cmov/libc-2.9.so
b7fca000-b7fcd000 rw-p b7fca000 00:00 0 
b7fdf000-b7fe1000 rw-p b7fdf000 00:00 0 
b7fe1000-b7fe2000 r-xp b7fe1000 00:00 0          [vdso]
b7fe2000-b7ffe000 r-xp 00000000 08:06 368654     /lib/ld-2.9.so
b7ffe000-b7fff000 r--p 0001b000 08:06 368654     /lib/ld-2.9.so
b7fff000-b8000000 rw-p 0001c000 08:06 368654     /lib/ld-2.9.so
bffeb000-c0000000 rw-p bffeb000 00:00 0          [stack]
Aborted

```

I'm really not familiar with gcc outputted information although I'd assume that the segmentation fault occurred because of the '[0x41414141]' part highlighted in red. 

I eventually will learn how to read these output, however I just want to know if I'm on the right track.

But assuming I was on the right track I continued debugging the program with gdb:

```

$ gdb -q overflow
(gdb) run
Starting program: /home/ordonez/Documents/Development/C/overflow 
*** stack smashing detected ***: /home/ordonez/Documents/Development/C/overflow terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7f67da8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7f67d60]
/home/ordonez/Documents/Development/C/overflow[0x804845c]
[0x41414141]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:06 3704767    /home/ordonez/Documents/Development/C/overflow
08049000-0804a000 r--p 00000000 08:06 3704767    /home/ordonez/Documents/Development/C/overflow
0804a000-0804b000 rw-p 00001000 08:06 3704767    /home/ordonez/Documents/Development/C/overflow
0804b000-0806c000 rw-p 0804b000 00:00 0          [heap]
b7e5a000-b7e67000 r-xp 00000000 08:06 368705     /lib/libgcc_s.so.1
b7e67000-b7e68000 r--p 0000c000 08:06 368705     /lib/libgcc_s.so.1
b7e68000-b7e69000 rw-p 0000d000 08:06 368705     /lib/libgcc_s.so.1
b7e69000-b7e6a000 rw-p b7e69000 00:00 0 
b7e6a000-b7fc6000 r-xp 00000000 08:06 386037     /lib/tls/i686/cmov/libc-2.9.so
b7fc6000-b7fc7000 ---p 0015c000 08:06 386037     /lib/tls/i686/cmov/libc-2.9.so
b7fc7000-b7fc9000 r--p 0015c000 08:06 386037     /lib/tls/i686/cmov/libc-2.9.so
b7fc9000-b7fca000 rw-p 0015e000 08:06 386037     /lib/tls/i686/cmov/libc-2.9.so
b7fca000-b7fcd000 rw-p b7fca000 00:00 0 
b7fdf000-b7fe1000 rw-p b7fdf000 00:00 0 
b7fe1000-b7fe2000 r-xp b7fe1000 00:00 0          [vdso]
b7fe2000-b7ffe000 r-xp 00000000 08:06 368654     /lib/ld-2.9.so
b7ffe000-b7fff000 r--p 0001b000 08:06 368654     /lib/ld-2.9.so
b7fff000-b8000000 rw-p 0001c000 08:06 368654     /lib/ld-2.9.so
bffeb000-c0000000 rw-p bffeb000 00:00 0          [stack]

Program received signal SIGABRT, Aborted.
0xb7fe1430 in __kernel_vsyscall ()
(gdb) info reg eip
eip            0xb7fe1430	0xb7fe1430 <__kernel_vsyscall+16>
(gdb) 


```

And the 'eip' register contained another memory address from what the book said. This is my problem however I believe ASLR is causing this problem because the book said after this exercise:

```

**CAUTION** Fedora and other recent builds use Address Space Layout
Randomization (ASLR) to randomize stack memory calls and will have mixed
results for the rest of this chapter. If you wish to use one of these builds,
disable the ASLR as follows:

#echo "0" > /proc/sys/kernel/randomize_va_space
#echo "0" > /proc/sys/kernel/exec-shield
#echo "0" > /proc/sys/kernel/exec-shield-randomize


```

When I cat '/proc/sys/kernel/randomize_va_space'. It outputted '2', but for the other two files they weren't found I got the output:

```

$ cat: /proc/sys/kernel/exec-shield
cat: /proc/sys/kernel/exec-shield: No such file or directory
$ cat: /proc/sys/kernel/exec-shield-randomize: No such file or directory
cat: /proc/sys/kernel/exec-shield-randomize: No such file or directory

```

I believe its the ASLR setting thats causing the issue with incorrect results from the book. But now I have another problem at hand, how to disable ASLR? So does anyone know how to disable ASLR or if thats not the issue and you understand what's happening point me in the right direction.

Oh and the book I'm currently reading is "McGraw Hill Gray Hat Hacking 2nd Edition". If that helps.

[IMG]http://www.ebooknetworking.com/books/007/149/big0071495681.jpg[/IMG]
 
Thanks in advance

1 love,
j3rg

---

### Post by SouthOfHell on 2009-11-27
[here you go](http://www.milw0rm.com/video/watch.php?id=48).  It's titled win32 how-to, but you can apply the same practice with gdb + gcc.  Well I have anyhow, quite interesting tbh.

---

### Post by lisati on 2009-11-27
My $0.01: 0x41 is the ASCII equivalent of the letter 'A'.

---

### Post by Arndt on 2009-11-27
> **SouthOfHell said:**
> [here you go](http://www.milw0rm.com/video/watch.php?id=48).  It's titled win32 how-to, but you can apply the same practice with gdb + gcc.  Well I have anyhow, quite interesting tbh.

This forum thread is about this subject: [http://ubuntuforums.org/showthread.php?t=1291856](http://ubuntuforums.org/showthread.php?t=1291856).

---

### Post by grayrainbow on 2009-11-27
man setarch

---

### Post by jerg on 2009-11-28
Thanks all ......well I did some further reading and found out by just setting '/proc/sys/kernel/randomize_va_space' to 0 did disable ASLR. What I really want to ask is if anyone know why the EIP register wasn't overwritten ....I even tried 2500 A's but that return with a perfectly fine address.... not 0x41414141 ....if anyone know I would really apperciate your help

Thnx in advance

jerg

---

### Post by grayrainbow on 2009-11-29
> **jerg said:**
> 
```

$gdb &#8211;q overflow
(gdb) run
Starting program: /book/overflow
Program received signal SIGSEGV, Segmentation fault.
0x41414141 in ?? ()
(gdb) info reg eip
eip            0x41414141        0x41414141
(gdb) q
A debugging session is active.
Do you still want to close the debugger?(y or n) y
$

```

What more you want?

P.S. [http://www.codef00.com/projects.php]("http://www.codef00.com/projects.php")

---

### Post by jerg on 2009-11-29
I want the whole world!!!....muhahahaha ....... yo grayrainbow read correctly thats the information from the book (McGraw Hill Gray Hat Hacking Vol. 2) ...the information I got as a result from the program was as I said:

```

$ gdb -q overflow
(gdb) run
Starting program: /home/ordonez/Documents/Development/C/overflow 
*** stack smashing detected ***: /home/ordonez/Documents/Development/C/overflow terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7f67da8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xb7f67d60]
/home/ordonez/Documents/Development/C/overflow[0x804845c]
[0x41414141]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:06 3704767    /home/ordonez/Documents/Development/C/overflow
08049000-0804a000 r--p 00000000 08:06 3704767    /home/ordonez/Documents/Development/C/overflow
0804a000-0804b000 rw-p 00001000 08:06 3704767    /home/ordonez/Documents/Development/C/overflow
0804b000-0806c000 rw-p 0804b000 00:00 0          [heap]
b7e5a000-b7e67000 r-xp 00000000 08:06 368705     /lib/libgcc_s.so.1
b7e67000-b7e68000 r--p 0000c000 08:06 368705     /lib/libgcc_s.so.1
b7e68000-b7e69000 rw-p 0000d000 08:06 368705     /lib/libgcc_s.so.1
b7e69000-b7e6a000 rw-p b7e69000 00:00 0 
b7e6a000-b7fc6000 r-xp 00000000 08:06 386037     /lib/tls/i686/cmov/libc-2.9.so
b7fc6000-b7fc7000 ---p 0015c000 08:06 386037     /lib/tls/i686/cmov/libc-2.9.so
b7fc7000-b7fc9000 r--p 0015c000 08:06 386037     /lib/tls/i686/cmov/libc-2.9.so
b7fc9000-b7fca000 rw-p 0015e000 08:06 386037     /lib/tls/i686/cmov/libc-2.9.so
b7fca000-b7fcd000 rw-p b7fca000 00:00 0 
b7fdf000-b7fe1000 rw-p b7fdf000 00:00 0 
b7fe1000-b7fe2000 r-xp b7fe1000 00:00 0          [vdso]
b7fe2000-b7ffe000 r-xp 00000000 08:06 368654     /lib/ld-2.9.so
b7ffe000-b7fff000 r--p 0001b000 08:06 368654     /lib/ld-2.9.so
b7fff000-b8000000 rw-p 0001c000 08:06 368654     /lib/ld-2.9.so
bffeb000-c0000000 rw-p bffeb000 00:00 0          [stack]

Program received signal SIGABRT, Aborted.
0xb7fe1430 in __kernel_vsyscall ()
[COLOR="Red"](gdb) info reg eip
eip            0xb7fe1430	0xb7fe1430 <__kernel_vsyscall+16>[/COLOR]
(gdb)

```

If you don't know the answer don't worry I don't want to hassle anyone about the issue . I'm still searching the web as to why this issue occurs myself. However if anyone knows the answer and it ain't no hassle for them to answer it then be my guest and explained.

Thanks
jerg

---

### Post by grayrainbow on 2009-11-30
If you want to have kids, you have to make sex, not somebody else. Get a disassembler and don't "speak" stupid stuff.

---

### Post by jerg on 2009-11-30
ok boss

---

