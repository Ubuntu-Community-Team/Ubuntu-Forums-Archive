---
title: "gdb debug program compiled in another machine"
date: 2016-03-20
forum: Programming Talk
---

### Post by chuchi on 2016-03-20
Hi there!

I want to apologize if this question is very stupid.

I want to debug a program with 'gdb' and the program has been compiled using this instruction in 'gcc':

```

gcc -g test.c -o test

```

Then I copied the executable file to another machine, but gdb can not find the sources. This is the output when I try to set a break point:

```

Reading symbols from test...done. 
(gdb) break test.c:7 
Breakpoint 1 at 0x8048426: file test.c, line 7. 
(gdb) start  
Temporary breakpoint 2 at 0x8048426: file test.c, line 7. 
Starting program: /home/user/test  
 
Breakpoint 1, main () at test.c:7 
7    test.c: No such file or directory.

```

Is there a way to see the source code of a program that has been compiled from another machine in gdb?

Or is it mandatory to have the source code in the same machine as gdb?

Thank you very much!

---

### Post by spjackson on 2016-03-20
If you want to debug at source code level, you need the source code on the debugging machine. Otherwise you are restricted to assembler level debugging.

---

### Post by chuchi on 2016-03-21
Hi spjackson,

Thank you very much for your response!

I thought I could debug using gdb server. I mean, debug from the source code machine to the machine that contains the program. I have never done it before.

---

