---
title: "ARM assembly under Linux"
date: 2012-06-26
forum: Programming Talk
---

### Post by chuchi on 2012-06-26
Hi there!!
 

 I need to learn ARM assembly, and I use Linux. Please, could you give me any starting point about how to install it?? I do not pretend that you teach me ARM assembly. Just a link.
 

 thank you very much!!!

---

### Post by youknowme on 2012-06-27
> **chuchi said:**
> Hi there!!
 

 I need to learn ARM assembly, and I use Linux. Please, could you give me any starting point about how to install it?? I do not pretend that you teach me ARM assembly. Just a link.
 

 thank you very much!!!

This might be useful to start you off
[http://www.coranac.com/tonc/text/asm.htm](http://www.coranac.com/tonc/text/asm.htm)

---

### Post by SevenMachines on 2012-06-27
Been a year or so, but i think this works? Although personally I recommend setting up a chroot or pbuilder arm environment, its less hassle with more complicated programs, or at least was in my previous experience.

```
$ apt-get install gcc-4.6-arm-linux-gnueabi libc6-dev-armel-cross

$ cat hello.s 
.data

msg:
.ascii "Hello, ARM World!\n"
len = . - msg


.text

.globl _start
_start:
/* write syscall */
mov %r0, $1 
ldr %r1, =msg 
ldr %r2, =len 
mov %r7, $4 
swi $0 

/* exit syscall */
mov %r0, $0 
mov %r7, $1 
swi $0


$ arm-linux-gnueabi-as -o hello.o hello.s

$ arm-linux-gnueabi-ld -o hello hello.o

$ file hello
hello: ELF 32-bit LSB executable, ARM, version 1 (SYSV), statically linked, not stripped

$ ./hello 
Hello, ARM World!
```

---

### Post by chuchi on 2012-06-27
Hi!! thank you very much for reply. But that type of instructions is of the form: Mov source,dest.  The syntax instructions on ARM is : Mov dest,source. This is what I need

Thank you very much!

---

### Post by chuchi on 2012-06-27
Ok I was wrong, your code is right!! I am very sorry!!

Everything is ok, except when I type ./hello I get

```

bash: ./hello: cannot execute binary file

```

Why??

Thank you very much!

---

### Post by SevenMachines on 2012-06-27
Yes. its just at&t syntax versus intel.

Sorry, obviously the binary is arm and not x86 so wont run, I just forgot I had qemu emulation enabled. Try,

```
$ ./hello 
bash: ./hello: cannot execute binary file

# Set up qemu arm emulation
$ sudo apt-get install qemu-user-static

$ ./hello 
Hello, ARM World!

```

---

### Post by chuchi on 2012-06-27
HI!! now it works!! thank you very very much!!

---

### Post by chuchi on 2012-06-28
Hi again!!

Do you know any way of debugging in qemu?

Surfing the net they say you have to install and configure a new kernel. Is there any other way??

thank you very much!!

---

### Post by SevenMachines on 2012-06-28
You can set qemu to wait on a gdb connection

```
# In a terminal
$ qemu-arm-static -g 10101 ./hello 
```

```
# In a new terminal
$ sudo apt-get install gdb-multiarch
```

Then start gdb-multiarch, load symbols, and connect gdb to qemu, eg
```
$gdb-multiarch 

(gdb) list _start
8	.text
9	
10	.globl _start
11	_start:
12	/* write syscall */
13	mov %r0, $1 
14	ldr %r1, =msg 
15	ldr %r2, =len 
16	mov %r7, $4 
17	swi $0 

(gdb) b 16
Breakpoint 1 at 0x8080: file hello.s, line 16.


(gdb) target remote :10101
Remote debugging using :10101
[New Remote target]
[Switching to Remote target]
_start () at hello.s:13
13	mov %r0, $1 

(gdb) c
Continuing.

Breakpoint 1, _start () at hello.s:16
16	mov %r7, $4 
(gdb) n
17	swi $0 
(gdb) n
20	mov %r0, $0 
(gdb) c 
Continuing.
[Inferior 1 (Remote target) exited normally]

```

[EDIT] You'll want debugging information ie
$ arm-linux-gnueabi-as -gstabs -o hello.o hello.s

---

