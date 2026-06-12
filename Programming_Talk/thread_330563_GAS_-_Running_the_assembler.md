---
title: "GAS - Running the assembler"
date: 2007-01-03
forum: Programming Talk
---

### Post by phossal on 2007-01-03
Where can I find a quality manual for as (assembler)? The links I have to GAS via gcc.org are all broken. I don't see the reference in their list of manuals. The tutorials and guides available per Google aren't detailed enough for what I'm looking for. 

In addition, I have a basic understanding of the gcc wrapper, but I'm hung up on the ld command. In the same way that the following will produce an executable:
```
 
gcc -o<name> source.c

``` 

is there a similar way in the ld command? My limited testing of:
```

ld -static /path/crt1.0.... asmSource.s -ofileName

```
does produce a file, but it isn't executable.

---

### Post by Wybiral on 2007-01-03
> **phossal said:**
> Where I can find a quality manual for as (assembler)? The links I have to GAS via gcc.org are all broken. I don't see the reference in their list of manuals. The tutorials and guides available per Google aren't detailed enough for what I'm looking for. 

In addition, I have a basic understanding of the gcc wrapper, but I'm hung up on the ld command. In the same way that the following will produce an executable:
```
 
gcc -o<name> source.c

``` 

is there a similar way in the ld command? My limited testing of:
```

ld -static /path/crt1.0.... asmSource.s -ofileName

```
does produce a file, but it isn't executable.

This site has a pretty good manual on the GAS assembler: [http://www.gnu.org/software/binutils/manual/gas-2.9.1/html_mono/as.html](http://www.gnu.org/software/binutils/manual/gas-2.9.1/html_mono/as.html)

I don't understand what you're asking about the commands... It's fairly easy to compile with GAS using these commands...

```

as MY_PROGRAM.s -o MY_OBJECT.o
ld MY_OBJECT.o

```

MY_PROGRAM.s is your assembly source. "as" assembles it into an object file, and "ld" links the object into an executable.

---

### Post by phossal on 2007-01-03
> **Wybiral said:**
> MY_PROGRAM.s is your assembly source. "as" assembles it into an object file, and "ld" links the object into an executable.

Thanks for the 'pointer' to the manual. 

The ld command links the object into an executable. Along with the object.o file, there are usually paths to other resources that you pass: the things you're trying to link.

It's not uncommon to pass paths to /usr/lib/crt1.o, /usr/lib/crti.o, etc. In fact, try to follow your own commands to compile a "Hello, World" object file, beginning with a listing file (gcc -S hello.c). It doesn't work.

---

### Post by winch on 2007-01-03
Use
gcc -v hello.c -o hello
To see what gcc is doing with as and ld.

---

### Post by phossal on 2007-01-03
That's a good idea. Thank you. It just might not work for the things that do not have a corresponding source file. But I can probably figure enough out that way. Thanks again.

---

### Post by phossal on 2007-01-14
> **Wybiral said:**
> 
```

as MY_PROGRAM.s -o MY_OBJECT.o
ld MY_OBJECT.o

```


You're one of a dozen people I routinely see in posts, and one of a half dozen who's advice I value. When I run the commands shown above, I get:

```
bash 3.1:as S.s -o S.o
bash 3.1:ld S.o
ld: warning: cannot find entry symbol _start; defaulting to 0000000008048094
S.o: In function `main':
S.c:(.text+0x19): undefined reference to `puts'
bash 3.1:
```

Out of curiosity, does that series work on *your* machine?

---

### Post by Wybiral on 2007-01-14
Oh, thats because the assembly code uses "main" instead of "_start"

When you use gcc, it uses "main" (like C)

When you use as, it uses "_start" (like a lot of assemblers)

If you are compiling an assembly output of a C compile, then you need to use gcc because it will name the start location "main"

It really just depends what you need, if you're using external libs from C, then you need to use "main" and gcc. If it's all pure assembly, then you can use "_start" and "as"

Sorry, I forgot to mention that!

---

### Post by phossal on 2007-01-14
It appears that after running AS like so:
```
as -V -Qy -o S.o S.s
```
gcc is running *this* as the ld command:
```

/usr/lib/gcc/i486-linux-gnu/4.1.2/collect2 --eh-frame-hdr -m elf_i386 -dynamic-linker /lib/ld-linux.so.2 -oS /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crt1.o /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.1.2/crtbegin.o -L/usr/lib/gcc/i486-linux-gnu/4.1.2 -L/usr/lib/gcc/i486-linux-gnu/4.1.2 -L/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib -L/lib/../lib -L/usr/lib/../lib [COLOR="Blue"]**S.o **[/COLOR]-lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc/i486-linux-gnu/4.1.2/crtend.o /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/crtn.o
```

---

### Post by Wybiral on 2007-01-14
I have to be honest, gas is fun... But I only use it when I need to compile something I disassembled or dumped from a C compile (which you can do BTW with the "-S" flag when you are compiling a C program... The assembly code that's dumped compiles as-is in the gcc compiler)

But when I want to do actual assembly programming I use nasm because it's more portable and the code looks much cleaner. You can also optimize nasm assembly code much easier (for size, not speed).

---

### Post by phossal on 2007-01-14
I have a few ways to work with the gcc tools now. Per usual, *thanks*. :D

---

