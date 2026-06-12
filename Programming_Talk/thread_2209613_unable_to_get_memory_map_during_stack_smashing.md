---
title: "unable to get memory map during stack smashing"
date: 2014-03-06
forum: Programming Talk
---

### Post by IAMTubby on 2014-03-06
Hello,
 I read on the internet that on building the below C code with the following options, it gives a memory map giving more details. However, I am unable to get the memory map. Please find below the output I get and the expected output.

Code
```
[COLOR=gray][FONT=Consolas]#include[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#800000][FONT=Consolas]<stdio.h>[/FONT][/COLOR][COLOR=gray]#include[/COLOR] [COLOR=#800000]<string.h>[/COLOR]

[COLOR=#2B91AF]int[/COLOR] check_password([COLOR=#00008B]char[/COLOR] *password){
    [COLOR=#2B91AF]int[/COLOR] flag = [COLOR=#800000]0[/COLOR];
    [COLOR=#00008B]char[/COLOR] buffer[[COLOR=#800000]20[/COLOR]];
    strcpy(buffer, password);

    [COLOR=#00008B]if[/COLOR](strcmp(buffer, [COLOR=#800000]"mypass"[/COLOR]) == [COLOR=#800000]0[/COLOR]){
        flag = [COLOR=#800000]1[/COLOR];
    }
    [COLOR=#00008B]if[/COLOR](strcmp(buffer, [COLOR=#800000]"yourpass"[/COLOR]) == [COLOR=#800000]0[/COLOR]){
        flag = [COLOR=#800000]1[/COLOR];
    }
    [COLOR=#00008B]return[/COLOR] flag;
}

[COLOR=#2B91AF]int[/COLOR] main([COLOR=#2B91AF]int[/COLOR] argc, [COLOR=#00008B]char[/COLOR] *argv[]){
    [COLOR=#00008B]if[/COLOR](argc >= [COLOR=#800000]2[/COLOR]){
        [COLOR=#00008B]if[/COLOR](check_password(argv[[COLOR=#800000]1[/COLOR]])){
            printf([COLOR=#800000]"%s"[/COLOR], [COLOR=#800000]"Access grainted\n"[/COLOR]);
        }[COLOR=#00008B]else[/COLOR]{
            printf([COLOR=#800000]"%s"[/COLOR], [COLOR=#800000]"Access denined\n"[/COLOR]);
        }
    }[COLOR=#00008B]else[/COLOR]{
        printf([COLOR=#800000]"%s"[/COLOR], [COLOR=#800000]"Please enter password!\n"[/COLOR]);
    } 
[COLOR=#000000][FONT=Consolas]}[/FONT][/COLOR]
```

Built code using the following options
```
gcc -g -fstack-protector test_overflow.c
```

Ran it as
```
./a.out 999999999999999999999999999999999999999999999999999999
```

Expected output
```
[COLOR=#000000][FONT=Consolas]ab@cd[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]-[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]x[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]:[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]$ [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]./[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]a[/FONT][/COLOR][COLOR=#000000][FONT=Consolas].[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]out wepassssssssssssssssss[/FONT][/COLOR]*** [COLOR=#2B91AF]stack[/COLOR] smashing detected ***: ./a.out terminated
======= [COLOR=#2B91AF]Backtrace[/COLOR]: =========
/lib/tls/i686/cmov/libc.so.[COLOR=#800000]6[/COLOR](__fortify_fail+[COLOR=#800000]0x48[/COLOR])[[COLOR=#800000]0xce0ed8[/COLOR]]
/lib/tls/i686/cmov/libc.so.[COLOR=#800000]6[/COLOR](__fortify_fail+[COLOR=#800000]0x0[/COLOR])[[COLOR=#800000]0xce0e90[/COLOR]]
./a.out[[COLOR=#800000]0x8048524[/COLOR]]
./a.out[[COLOR=#800000]0x8048545[/COLOR]]
/lib/tls/i686/cmov/libc.so.[COLOR=#800000]6[/COLOR](__libc_start_main+[COLOR=#800000]0xe6[/COLOR])[[COLOR=#800000]0xc16b56[/COLOR]]
./a.out[[COLOR=#800000]0x8048411[/COLOR]]
======= [COLOR=#2B91AF]Memory[/COLOR] [COLOR=#2B91AF]map[/COLOR]: ========
[COLOR=#800000]007d9000[/COLOR]-[COLOR=#800000]007f5000[/COLOR] r-xp [COLOR=#800000]00000000[/COLOR] [COLOR=#800000]08[/COLOR]:[COLOR=#800000]06[/COLOR] [COLOR=#800000]5776[/COLOR]       /lib/libgcc_s.so.[COLOR=#800000]1[/COLOR]
[COLOR=#800000]007f5000[/COLOR]-[COLOR=#800000]007f6000[/COLOR] r--p [COLOR=#800000]0001b000[/COLOR] [COLOR=#800000]08[/COLOR]:[COLOR=#800000]06[/COLOR] [COLOR=#800000]5776[/COLOR]       /lib/libgcc_s.so.[COLOR=#800000]1[/COLOR]
[COLOR=#800000]007f6000[/COLOR]-[COLOR=#800000]007f7000[/COLOR] rw-p [COLOR=#800000]0001c000[/COLOR] [COLOR=#800000]08[/COLOR]:[COLOR=#800000]06[/COLOR] [COLOR=#800000]5776[/COLOR]       /lib/libgcc_s.so.[COLOR=#800000]1[/COLOR]
[COLOR=#800000]0090a000[/COLOR]-[COLOR=#800000]0090b000[/COLOR] r-xp [COLOR=#800000]00000000[/COLOR] [COLOR=#800000]00[/COLOR]:[COLOR=#800000]00[/COLOR] [COLOR=#800000]0[/COLOR]          [vdso]
[COLOR=#800000]00c00000[/COLOR]-[COLOR=#800000]00d3e000[/COLOR] r-xp [COLOR=#800000]00000000[/COLOR] [COLOR=#800000]08[/COLOR]:[COLOR=#800000]06[/COLOR] [COLOR=#800000]1183[/COLOR]       /lib/tls/i686/cmov/libc-[COLOR=#800000]2.10[/COLOR].[COLOR=#800000]1.so[/COLOR]
[COLOR=#800000]00d3e000[/COLOR]-[COLOR=#800000]00d3f000[/COLOR] ---p [COLOR=#800000]0013e000[/COLOR] [COLOR=#800000]08[/COLOR]:[COLOR=#800000]06[/COLOR] [COLOR=#800000]1183[/COLOR]       /lib/tls/i686/cmov/libc-[COLOR=#800000]2.10[/COLOR].[COLOR=#800000]1.so[/COLOR]
[COLOR=#800000]00d3f000[/COLOR]-[COLOR=#800000]00d41000[/COLOR] r--p [COLOR=#800000]0013e000[/COLOR] [COLOR=#800000]08[/COLOR]:[COLOR=#800000]06[/COLOR] [COLOR=#800000]1183[/COLOR]       /lib/tls/i686/cmov/libc-[COLOR=#800000]2.10[/COLOR].[COLOR=#800000]1.so[/COLOR]
[COLOR=#800000]00d41000[/COLOR]-[COLOR=#800000]00d42000[/COLOR] rw-p [COLOR=#800000]00140000[/COLOR] [COLOR=#800000]08[/COLOR]:[COLOR=#800000]06[/COLOR] [COLOR=#800000]1183[/COLOR]       /lib/tls/i686/cmov/libc-[COLOR=#800000]2.10[/COLOR].[COLOR=#800000]1.so[/COLOR]
[COLOR=#800000]00d42000[/COLOR]-[COLOR=#800000]00d45000[/COLOR] rw-p [COLOR=#800000]00000000[/COLOR] [COLOR=#800000]00[/COLOR]:[COLOR=#800000]00[/COLOR] [COLOR=#800000]0[/COLOR] 
[COLOR=#800000]00e0c000[/COLOR]-[COLOR=#800000]00e27000[/COLOR] r-xp [COLOR=#800000]00000000[/COLOR] [COLOR=#800000]08[/COLOR]:[COLOR=#800000]06[/COLOR] [COLOR=#800000]4213[/COLOR]       /lib/ld-[COLOR=#800000]2.10[/COLOR].[COLOR=#800000]1.so[/COLOR]
[COLOR=#800000]00e27000[/COLOR]-[COLOR=#800000]00e28000[/COLOR] r--p [COLOR=#800000]0001a000[/COLOR] [COLOR=#800000]08[/COLOR]:[COLOR=#800000]06[/COLOR] [COLOR=#800000]4213[/COLOR]       /lib/ld-[COLOR=#800000]2.10[/COLOR].[COLOR=#800000]1.so[/COLOR]
[COLOR=#800000]00e28000[/COLOR]-[COLOR=#800000]00e29000[/COLOR] rw-p [COLOR=#800000]0001b000[/COLOR] [COLOR=#800000]08[/COLOR]:[COLOR=#800000]06[/COLOR] [COLOR=#800000]4213[/COLOR]       /lib/ld-[COLOR=#800000]2.10[/COLOR].[COLOR=#800000]1.so[/COLOR]
[COLOR=#800000]08048000[/COLOR]-[COLOR=#800000]08049000[/COLOR] r-xp [COLOR=#800000]00000000[/COLOR] [COLOR=#800000]08[/COLOR]:[COLOR=#800000]05[/COLOR] [COLOR=#800000]1056811[/COLOR]    /dos/hacking/test/a.out
[COLOR=#800000]08049000[/COLOR]-[COLOR=#800000]0804a000[/COLOR] r--p [COLOR=#800000]00000000[/COLOR] [COLOR=#800000]08[/COLOR]:[COLOR=#800000]05[/COLOR] [COLOR=#800000]1056811[/COLOR]    /dos/hacking/test/a.out
[COLOR=#800000]0804a000[/COLOR]-[COLOR=#800000]0804b000[/COLOR] rw-p [COLOR=#800000]00001000[/COLOR] [COLOR=#800000]08[/COLOR]:[COLOR=#800000]05[/COLOR] [COLOR=#800000]1056811[/COLOR]    /dos/hacking/test/a.out
[COLOR=#800000]08675000[/COLOR]-[COLOR=#800000]08696000[/COLOR] rw-p [COLOR=#800000]00000000[/COLOR] [COLOR=#800000]00[/COLOR]:[COLOR=#800000]00[/COLOR] [COLOR=#800000]0[/COLOR]          [heap]
b76fe000-b76ff000 rw-p [COLOR=#800000]00000000[/COLOR] [COLOR=#800000]00[/COLOR]:[COLOR=#800000]00[/COLOR] [COLOR=#800000]0[/COLOR] 
b7717000-b7719000 rw-p [COLOR=#800000]00000000[/COLOR] [COLOR=#800000]00[/COLOR]:[COLOR=#800000]00[/COLOR] [COLOR=#800000]0[/COLOR] 
bfc1c000-bfc31000 rw-p [COLOR=#800000]00000000[/COLOR] [COLOR=#800000]00[/COLOR]:[COLOR=#800000]00[/COLOR] [COLOR=#800000]0[/COLOR]          [[COLOR=#2B91AF]stack[/COLOR]] 
[COLOR=#2B91AF][FONT=Consolas]Aborted[/FONT][/COLOR]
```

Received output
```
$ ./a.out 999999999999999999999999999999999999999999999999999999999999999999999999999999999999999*** stack smashing detected ***: ./a.out terminated
Segmentation fault

```

Please let me know how I can see the memory map and how I can decipher the line in code which causes this behaviour.

Thanks.

---

### Post by trent.josephsen on 2014-03-07
One of the possible outcomes of trampling all over your stack is not being able to tell where you came from. All those 9's are clobbbering data in the stack that you need in order to print that backtrace. Running it with a somewhat shorter string (try length 25) will do what you expect.

Interestingly, running it with a string of length exactly 32 (99999999999999999999999999999999) seems to sometimes trigger the segfault and sometimes print the backtrace / memory map. I have no idea why that would be, unless perhaps it has to do with alignment of the "guard variable" -fstack-protector uses.

---

### Post by Bachstelze on 2014-03-08
The "memory map" printed is not very useful anyway. Much better is to run the program in gdb and use the *examine* command.

---

### Post by IAMTubby on 2014-03-09
> **trent.josephsen said:**
> One of the possible outcomes of trampling all over your stack is not being able to tell where you came from. All those 9's are clobbbering data in the stack that you need in order to print that backtrace. Running it with a somewhat shorter string (try length 25) will do what you expect.


> **Bachstelze said:**
> The "memory map" printed is not very useful anyway. Much better is to run the program in gdb and use the *examine* command.

Thanks trent.josephsen, Bachstelze. For me any input between lengths 21-33 seems to work(as in, gives the memory map)
This is the output I get
```
$ ./a.out 999999999999999999999999999999999*** stack smashing detected ***: ./a.out terminated
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(__fortify_fail+0x45)[0xc1c085]
/lib/i386-linux-gnu/libc.so.6(+0xed037)[0xc1c037]
./a.out[0x8048508]
./a.out[0x804852e]
======= Memory map: ========
0096f000-0098b000 r-xp 00000000 08:05 3834       /lib/i386-linux-gnu/libgcc_s.so.1
0098b000-0098c000 r--p 0001b000 08:05 3834       /lib/i386-linux-gnu/libgcc_s.so.1
0098c000-0098d000 rw-p 0001c000 08:05 3834       /lib/i386-linux-gnu/libgcc_s.so.1
00b2f000-00cab000 r-xp 00000000 08:05 3036       /lib/i386-linux-gnu/libc-2.13.so
00cab000-00cad000 r--p 0017c000 08:05 3036       /lib/i386-linux-gnu/libc-2.13.so
00cad000-00cae000 rw-p 0017e000 08:05 3036       /lib/i386-linux-gnu/libc-2.13.so
00cae000-00cb1000 rw-p 00000000 00:00 0 
00ed0000-00eee000 r-xp 00000000 08:05 8226       /lib/i386-linux-gnu/ld-2.13.so
00eee000-00eef000 r--p 0001d000 08:05 8226       /lib/i386-linux-gnu/ld-2.13.so
00eef000-00ef0000 rw-p 0001e000 08:05 8226       /lib/i386-linux-gnu/ld-2.13.so
00f70000-00f71000 r-xp 00000000 00:00 0          [vdso]
08048000-08049000 r-xp 00000000 08:07 2880399    /home/IAMTubby/Desktop/a.out
08049000-0804a000 r--p 00000000 08:07 2880399    /home/IAMTubby/Desktop/a.out
0804a000-0804b000 rw-p 00001000 08:07 2880399    /home/IAMTubby/Desktop/a.out
0986c000-0988d000 rw-p 00000000 00:00 0          [heap]
b7848000-b7849000 rw-p 00000000 00:00 0 
b785b000-b785d000 rw-p 00000000 00:00 0 
bff23000-bff44000 rw-p 00000000 00:00 0          [stack]
Aborted

```

But I would like to see the line number which causes the stack smashing. I tried quite a few things, but none of them give me the line number. I guess I'm not using them the right way. Would you be able to help me here ?
1. Ran addr2line as follows
$ addr2line -e a.out 2880399
??:0

2. Tried info symbol on gdb
(gdb) info symbol 2880399
__divtf3 + 4271 in section .text of /lib/i386-linux-gnu/libgcc_s.so.1

3. Tried the examine command on gdb
(gdb) x/s buffer
0xbffff2a8:      "\002"

---

### Post by Bachstelze on 2014-03-09
> **IAMTubby said:**
> 
But I would like to see the line number which causes the stack smashing.

I have no idea what you mean by that...

---

### Post by IAMTubby on 2014-03-09
> **Bachstelze said:**
> I have no idea what you mean by that...
Hello Bachstelze,
I mean, I would like to see that the line ```
strcpy(buffer, password);
``` is the one which causes the stack smashing.
For this, I tried the addr2line, info symbol and examine command in gdb. But was not able to get the corresponding line.

---

### Post by Bachstelze on 2014-03-09
What else could it be?

---

### Post by Bachstelze on 2014-03-09
Is that what you want to do?

```
firas@itsuki ~ % cat test.c 
#include<stdio.h>
#include <string.h>

int check_password(char *password){
    int flag = 0;
    char buffer[20];
    strcpy(buffer, password);

    if(strcmp(buffer, "mypass") == 0){
        flag = 1;
    }
    if(strcmp(buffer, "yourpass") == 0){
        flag = 1;
    }
    return flag;
}

int main(int argc, char *argv[]){
    if(argc >= 2){
        if(check_password(argv[1])){
            printf("%s", "Access grainted\n");
        }else{
            printf("%s", "Access denined\n");
        }
    }else{
        printf("%s", "Please enter password!\n");
    } 
}
firas@itsuki ~ % gcc -m32 -g -o test test.c 
firas@itsuki ~ % gdb --args ./test 1111111111111111111111111111111111111111111111111111111
Reading symbols from /home/firas/test...done.
(gdb) run
Starting program: /home/firas/test 1111111111111111111111111111111111111111111111111111111
*** stack smashing detected ***: /home/firas/test terminated

Program received signal SIGSEGV, Segmentation fault.
0xf7df9b19 in ?? () from /lib/i386-linux-gnu/libgcc_s.so.1
(gdb) bt
#0  0xf7df9b19 in ?? () from /lib/i386-linux-gnu/libgcc_s.so.1
#1  0xf7dfa6e1 in _Unwind_Backtrace () from /lib/i386-linux-gnu/libgcc_s.so.1
#2  0xf7f1e0e7 in __GI___backtrace (array=0xffffd400, size=64) at ../sysdeps/i386/backtrace.c:127
#3  0xf7e843b0 in __libc_message (do_abort=2, fmt=0xf7f7d467 "*** %s ***: %s terminated\n")
    at ../sysdeps/unix/sysv/linux/libc_fatal.c:180
#4  0xf7f1deb5 in __GI___fortify_fail (msg=0xf7f7d44f "stack smashing detected") at fortify_fail.c:32
#5  0xf7f1de6a in __stack_chk_fail () at stack_chk_fail.c:29
#6  0x08048508 in check_password (password=0xffffd7bc '1' <repeats 55 times>) at test.c:16
#7  0x31313131 in ?? ()
#8  0x31313131 in ?? ()
#9  0x31313131 in ?? ()
#10 0x31313131 in ?? ()
#11 0x00313131 in ?? ()
#12 0x08048560 in ?? ()
Backtrace stopped: previous frame inner to this frame (corrupt stack?)
(gdb) quit
A debugging session is active.

	Inferior 1 [process 24847] will be killed.

Quit anyway? (y or n) y
firas@itsuki ~ % addr2line -e test 0x08048508 
/home/firas/test.c:16
```

Note that it does not tell exactly which line caused the smashing, only the line when the system noticed that smashing had occurred. If you want to know exactly when the smashing occurred, you have to use a tool like valgrind.

---

### Post by IAMTubby on 2014-03-13
> **Bachstelze said:**
> Is that what you want to do?
Bachstelze, I'm very sorry for taking so long to reply. I tried out what you gave me and this is exactly what I wanted. Thanks a lot :)

> **trent.josephsen said:**
> One of the possible outcomes of trampling all over your stack is not being able to tell where you came from. All those 9's are clobbbering data in the stack that you need in order to print that backtrace. Running it with a somewhat shorter string (try length 25) will do what you expect.
Thanks trent.josephsen for the reason on why it wasn't showing the details with the long input.

Marking the thread as solved.

---

