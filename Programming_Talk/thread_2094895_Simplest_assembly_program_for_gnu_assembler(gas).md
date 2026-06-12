---
title: "Simplest assembly program for gnu assembler(gas)"
date: 2012-12-15
forum: Programming Talk
---

### Post by 681ankit on 2012-12-15
Hello, I am trying to learn programming using gas.But I did not find any tutorial that will show me the simplest program sample that I can run on my PC.
            I searched over Internet from a day, but I didn't find it.
            
            I want a sample code that will store(move) value 1 into register eax and steps for assembling and loading ..thanks..That will surely help me to get started , into writing the assembly language programs..
           thanks..

---

### Post by ehrt74 on 2012-12-15
Here's a fairly short example:

```

.section .text

        .globl main
main:   
        movl $1, %eax
        movl $5, %ebx

        int $0x80


```

save as myprogram.s and compile and run with:

```

gcc myprogram.s
./a.out
echo $?

```

Taken (with some changes) from: [http://savannah.nongnu.org/projects/pgubook/]("http://savannah.nongnu.org/projects/pgubook/")

---

### Post by 681ankit on 2012-12-15
thanks for reply .. I got it now..

---

### Post by ehrt74 on 2012-12-15
There's one thing worth mentioning as the book has certain problems. The world has changed since 2002!

For example, the book states that an assembly program starts at the _start label. I tried this, and it didn't compile, so I wrote a minimum C program:
```

int main() {
  return 2;
}

```
and compiled it with
```

> gcc myfile.c -S -O5

```
to see what the current convention is. If you ever get stuck because of changes, this could be a good method to use.

---

### Post by trent.josephsen on 2012-12-15
Good job omitting the step where _start comes in. The assembly output of a C compiler is not equivalent to what you would write if you were programming in "raw" assembly. For instance, the label "main" is only meaningful in C, which is why that program won't do anything if you assemble it without using gcc (gcc links against libc). I don't know what problem you had with _start but I imagine it might be related to using gcc as an assembler.

If you want to see what gcc *actually* outputs, disassemble the binary (**Note** this is not recommended as a way to learn assembly! It contains a lot of libc nonsense that you would not write).

```
$ gcc -o file file.c
$ objdump -d file
```

---

### Post by ehrt74 on 2012-12-18
trent.josephsen is quite correct that you can assemble and link an executable without using the label 'main'. an example would be:

```

.section .text

        .globl _start
_start:   
        movl $1, %eax
        movl $5, %ebx

        int $0x80

```

which you would then assemble, link and run by entering:
```

> as myfile.s -o myfile.o
> ld -s myfile.o -o myfile
> ./myfile

```

Hope this adds to the general confusion :)

---

