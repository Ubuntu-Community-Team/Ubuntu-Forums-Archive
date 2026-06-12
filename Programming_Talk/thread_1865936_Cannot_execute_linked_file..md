---
title: "Cannot execute linked file."
date: 2011-10-20
forum: Programming Talk
---

### Post by cgroza on 2011-10-20
Hello everyone.
I am trying to link some nasm code to the C standard library.
The assembly and linkage works fine.
But when I try to execute my file, I get no such file or directory.
I do an "ls", and there is my file.
So here are the commands I run:
```

nasm -felf fibonaci.asm
ld -o fibs fibonaci.o -lc
./fibs

```And here is the "ls":
```

ls
assembler.asm  fibonaci.asm  fibonaci.o  fibs

```Someone suggested me to do an strace, so here is that one too:
```
strace ./fibs
execve("./fibs", ["./fibs"], [/* 42 vars */]) = -1 ENOENT (No such file or directory)
dup(2)                                  = 3
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb783c000
_llseek(3, 0, 0xbfc126f4, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: No such file or di"..., 40strace: exec: No such file or directory
) = 40
close(3)                                = 0
munmap(0xb783c000, 4096)                = 0
exit_group(1)                           = ?

```I get the same problem on both my Ubuntu and Slackware installs.

Thank you.

---

### Post by ofnuts on 2011-10-20
Stupid question, but is the ./fibs file marked executable?

---

### Post by cgroza on 2011-10-20
> **ofnuts said:**
> Stupid question, but is the ./fibs file marked executable?
Yes it is:
```
ls -l | grep fibs
-rwxr-xr-x 1 cgroza users 1962 Oct 20 21:31 fibs

```Never mind the time stamp, still have to fix the system clock on Slackware. :D
And even if it wasn't, the output would have been "permission denied", not no such file or directory.

---

### Post by karlson on 2011-10-20
> **cgroza said:**
> I get the same problem on both my Ubuntu and Slackware installs.

Thank you.

What happens when you do:
```

strace <path to fibs>/fibs

```

One more what does
```

ls ./fibs

```
show?

---

### Post by Bachstelze on 2011-10-20
Care to share your code? I always do assembly with gas/gcc so I'm curious about how it would work on nasm.

---

### Post by karlson on 2011-10-20
> **Bachstelze said:**
> Care to share your code? I always do assembly with gas/gcc so I'm curious about how it would work on nasm.

Could be wrong but this may be it
[http://ubuntuforums.org/showthread.php?t=1865896](http://ubuntuforums.org/showthread.php?t=1865896)

---

### Post by Bachstelze on 2011-10-20
> **karlson said:**
> Could be wrong but this may be it
[http://ubuntuforums.org/showthread.php?t=1865896](http://ubuntuforums.org/showthread.php?t=1865896)

Nah that one is stand alone, it doesn't need to be linked with libc.

---

### Post by gsmanners on 2011-10-20
Linking is a pain. Maybe you could try doing all that in [gcc inline assembly]("http://www.ibiblio.org/gferg/ldp/GCC-Inline-Assembly-HOWTO.html").

---

### Post by Arndt on 2011-10-21
> **cgroza said:**
> Hello everyone.
I am trying to link some nasm code to the C standard library.
The assembly and linkage works fine.
But when I try to execute my file, I get no such file or directory.
I do an "ls", and there is my file.


Does "file fibs" say something interesting? You can look at the output from "objdump fibs" too. Did you set a start address for the program?

---

### Post by cgroza on 2011-10-21
Sorry for the late response. Had a long day of school.

> **Arndt said:**
> Does "file fibs" say something interesting? You can look at the output from "objdump fibs" too. Did you set a start address for the program?

Here it is:
```

file fibs
fibs: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), not stripped

```> **Bachstelze said:**
> Care to share your code? I always do assembly with gas/gcc so I'm curious about how it would work on nasm.

The code is similar to the one karlson pointed:
```

section .data:
    formatStr:     db 'Fib: %i',10

section .text
    global _start
    extern printf
    
_start:
    mov ecx, 0        ;will keep the before last fibonnaci number
    mov edx, 1        ;will keep the last fibonnaci number
    mov eax, 0        ;will keep a fibonnaci index counter
    
    jmp fibonaci        ;start fibonnaci

exit:
    push edx            ;push fib on the stack
    push formatStr        ;push format string on stack
    call printf            ;call printf
    
    mov eax, 1
    mov ebx, 0
    int 80h

fibonaci:
    cmp eax, 5         ;have we reached the max counter?
    jle nexfib             ;no? go again
    jmp exit               ;yes? output and exit

nexfib:
    inc eax            ;increment counter
    inc eax
    add edx, ecx        ;add last fib with before last fib
    add ecx, edx        ;add before last fib with last fib. before last fib changes value

    jmp fibonaci        ;loop


```> **karlson said:**
> What happens when you do:
```

strace <path to fibs>/fibs

```One more what does
```

ls ./fibs

```show?
It shows up:
```
ls fibs
fibs
```I have already posted the strace.

---

### Post by karlson on 2011-10-21
> **cgroza said:**
> 
I have already posted the strace.

you posted:
```

strace ./fibs

```

I was looking for:
```

strace /<full path>/fibs

```

and just for kicks:
```

mv ./fibs ./new_fibonacci

```
and then try to run it.

---

### Post by cgroza on 2011-10-21
> **karlson said:**
> you posted:
```

strace ./fibs

```I was looking for:
```

strace /<full path>/fibs

```
Sorry. Here is it:
```

strace /home/cgroza/nasm/fibs


execve("/home/cgroza/nasm/fibs", ["/home/cgroza/nasm/fibs"], [/* 36 vars */]) = -1 ENOENT (No such file or directory)
dup(2)                                  = 3
fcntl64(3, F_GETFL)                     = 0x8002 (flags O_RDWR|O_LARGEFILE)
fstat64(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb76e9000
_llseek(3, 0, 0xbfd4803c, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: No such file or di"..., 40strace: exec: No such file or directory
) = 40
close(3)                                = 0
munmap(0xb76e9000, 4096)                = 0
exit_group(1)                           = ?


```

---

### Post by Arndt on 2011-10-21
I found that if you change the symbol '_start' in your program to 'main' and then link with this command:

```
gcc -o fibs fibs.o -lc
```

you get an executable program. Exactly why it doesn't work with your code I don't know, but combining ld and -lc seems to work badly. I searched a bit, but couldn't find a single example of a nasm program on Linux that used printf.

---

### Post by cgroza on 2011-10-21
> **Arndt said:**
> I found that if you change the symbol '_start' in your program to 'main' and then link with this command:

```
gcc -o fibs fibs.o -lc
```you get an executable program. Exactly why it doesn't work with your code I don't know, but combining ld and -lc seems to work badly. I searched a bit, but couldn't find a single example of a nasm program on Linux that used printf.
That worked great. Thanks.
I think I will use gcc to do the linkage from now on.
I wonder if there is any bug filled for this...

---

