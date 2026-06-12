---
title: "problem using ld to link 64 bit executable"
date: 2013-05-21
forum: Programming Talk
---

### Post by allynm on 2013-05-21
Hello everyone,

Perhaps an assembly language maven can give me some guidance.  I have what seems to me to be a simple 64bit "hello world" program that assembles nicely with the following command:

       as --64 -c 64bit.s

The resulting .o file is identified as a class "ELF64" using readelf -a command.  Examing the .o code using objdump all seems well.

However, when I try to link using:

       ld -o 64bit 64bit.o

I get this message:

       "ld: i386-86-64 architecture of input file `64bit.o' is incompatible with i386 output"

Now, as near as I can tell from the man page for as using the --64 switch with as command should yield a 64 bit object file.  And, according to readelf it does.  And object code is created with the appropriate 64 bit regisers identified.  Note that I am making no libraries in the code--it's "pure" 64bit code--no calls to C libraries.

BTW, the processor is an AMD Athlon II P340 Dual-Core machine.

I'm stumped.

Thanks,
Mark Allyn

---

### Post by oldos2er on 2013-05-21
Moved to Programming Talk.

---

### Post by allynm on 2013-05-21
Thanks.  Wasn't aware of this subforum.  It is indeed the right place for my query.
-Mark

---

### Post by genime on 2013-05-21
I also met this problem, when I compiled on another computer(also 64bit system) is ok, but switch to a new pc,
when I execute make, there are errors below:
[COLOR=#000000][FONT=Lucida Grande]gcc -Wall -g -o linkSearch1 linkList1.o[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]/usr/bin/ld: i386 architecture of input file `linkList1.o' is incompatible with i386:x86-64 output[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]collect2: error: ld returned 1 exit status[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]make: *** [linkSearch1] Error 1

after that I add -32m option and complied again. but the error message as below:

[/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]gcc -Wall -g -c linkList1.c LinkList.h comm.h [/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]gcc -Wall -g -m32 -o linkSearch1 linkList1.o[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]/usr/bin/ld: cannot find crt1.o: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]/usr/bin/ld: cannot find crti.o: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgcc.a when searching for -lgcc[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]/usr/bin/ld: cannot find -lgcc[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgcc_s.so when searching for -lgcc_s[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]/usr/bin/ld: cannot find -lgcc_s[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]/usr/bin/ld: cannot find -lc[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgcc.a when searching for -lgcc[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]/usr/bin/ld: cannot find -lgcc[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgcc_s.so when searching for -lgcc_s[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]/usr/bin/ld: cannot find -lgcc_s[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]/usr/bin/ld: cannot find crtn.o: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]collect2: error: ld returned 1 exit status[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]make: *** [linkSearch1] Error 1

very strange...

Hope someone can help me, Many thanks![/FONT][/COLOR]

---

### Post by genime on 2013-05-21
I deleted .o file and compile success..... Maybe different pc has different complied result i think.

---

### Post by SledgeHammer_999 on 2013-05-21
@allynm

It seems that ld tries to output a 32bit binary from the error message.
Unfortunately I don't have more experience on this. Just my 2 cents.

---

