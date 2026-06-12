---
title: "addr2line doesn't work - returns ??:0"
date: 2019-05-09
forum: Programming Talk
---

### Post by israeli on 2019-05-09
Hi everyone,
I created a simple C++ program with a crash to practice addr2line command.
But when I call to addr2line with the error address, all I get is "??:0"
Why am I getting that?

My Ubuntu version is: Ubuntu 18.04.1 LTS

The backtrace from the program is:
```

Error: signal 11:./exec(_Z21PrintCallStackOnErrori+0x2b)[0x55af08f2fc95]
/lib/x86_64-linux-gnu/libc.so.6(+0x3ef20)[0x7f348f003f20]
./exec(_Z5FuncAv+0x14)[0x55af08f2fcf0]
./exec(main+0x1a)[0x55af08f2fd32]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xe7)[0x7f348efe6b97]
./exec(_start+0x2a)[0x55af08f2fb8a]
```

addr2line command:
```
addr2line -e exec 0x55af08f2fcf0
```

Output:
```
??:0
```

In additional, when calling "objdump -D exec | grep FuncA" FuncA is 0xcdc
Output:
```

     0000000000000cdc <_Z5FuncAv>: d2d:    e8 aa ff ff ff
     callq  cdc <_Z5FuncAv>
     c8c:    74 63                    je     cf1 <_Z5FuncAv+0x15>
     c9b:    73 73                    jae    d10 <_Z5FuncAv+0x34>
     c9d:    70 6e                    jo     d0d <_Z5FuncAv+0x31>
     ca8:    75 5f                    jne    d09 <_Z5FuncAv+0x2d>
     cc4:    67 65 72 49              addr32 gs jb d11 <_Z5FuncAv+0x35>
     cc8:    73 45                    jae    d0f <_Z5FuncAv+0x33>
     ccf:    78 45                    js     d16 <_Z5FuncAv+0x3a>
     cff:    74 00                    je     d01 <_Z5FuncAv+0x25>
     d06:    72 00                    jb     d08 <_Z5FuncAv+0x2c>
```



How can I fix addr2line to return the error line number?
Thanks.

---

### Post by norobro on 2019-05-09
I was not aware of the program addr2line and thus have never used it. Anyway here's my WAG. 

From the man page:> Given an address in an executable or an offset in a section of a relocatable object,

The address that you are using with addr2line is the runtime address on the stack. Your program has segfaulted so when you run addr2line the executable is no longer in memory and that address is invalid (??:0). 

Here's my simple example:```
/data/c++_progs/signal$ g++ -g signal.cpp

$ ./a.out
./a.out(+0x11c1) [0x55ce6392f1c1]
/lib/x86_64-linux-gnu/libc.so.6(+0x37840) [0x7efe57eb6840]
./a.out(+0x1234) [0x55ce6392f234]
./a.out(+0x1257) [0x55ce6392f257]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xeb) [0x7efe57ea309b]
./a.out(+0x10ea) [0x55ce6392f0ea]

$ addr2line -e a.out 0x1234
/data/c++_progs/signal/signal.cpp:25

```

And a check using gdb:```
$ gdb -q ./a.out
Reading symbols from a.out...done.
(gdb) r
Starting program: /data/c++_progs/signal/a.out 


Program received signal SIGSEGV, Segmentation fault.
0x0000555555555234 in func () at signal.cpp:25
25          *p = 0x0;
(gdb) c
Continuing.
/data/c++_progs/signal/a.out(+0x11c1) [0x5555555551c1]
/lib/x86_64-linux-gnu/libc.so.6(+0x37840) [0x7ffff7af7840]
/data/c++_progs/signal/a.out(+0x1234) [0x555555555234]
/data/c++_progs/signal/a.out(+0x1257) [0x555555555257]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xeb) [0x7ffff7ae409b]
/data/c++_progs/signal/a.out(+0x10ea) [0x5555555550ea]
[Inferior 1 (process 15712) exited with code 013]
(gdb) bt
No stack.
(gdb) q

```


Since you compiled with "-rdynamic" you have to run objdump (nm, readelf) to find the offset of FuncA. The following should give you the file and line number of the statement that is causing the segfault:
```
addr2line -e exec 0xcf0  # 0xcdc + 0x14

```
HTH

---

### Post by israeli on 2019-05-10
Thanks a lot! you really helped me to find out why addr2line doesn't work correctly.
Now I wrote a simple script that find the correct line (using objdump and offset).

Thanks!

---

### Post by sudicom on 2019-08-27
Hi!

Can you share this script, please!

---

