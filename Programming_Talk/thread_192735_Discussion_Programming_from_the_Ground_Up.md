---
title: "Discussion: Programming from the Ground Up"
date: 2006-06-09
forum: Programming Talk
---

### Post by elemental666 on 2006-06-09
mkay, so I know a few language, but I've never messed with assembly before.  So I decided to learn.  To do so I'm reading "Programming from the Gound Up" which can be found [here]("http://download.savannah.gnu.org/releases/pgubook/ProgrammingGroundUp-1-0-booksize.pdf").

Right off the bat, I'm having trouble... I entered the first program into gedit and saved it as exit.s, assembled and linked it.  Ran it and it return 0 as expected.

I then edited the line:
```
 movl $0, %ebx
```
to:
```
 movl $200, %ebx
```
assembled and linked, ran it and it still returns 0?

exit.s looks like this now:
```

.section .data

.section .text
.globl _start
_start:
movl $1, %eax
movl $200, %ebx
init $0x80

```

Im running i686 kernel on a P4 M, any help?

---

### Post by Arndt on 2006-06-09
[QUOTE=elemental666]mkay, so I know a few language, but I've never messed with assembly before.  So I decided to learn.  To do so I'm reading "Programming from the Gound Up" which can be found [here]("http://download.savannah.gnu.org/releases/pgubook/ProgrammingGroundUp-1-0-booksize.pdf").

Right off the bat, I'm having trouble... I entered the first program into gedit and saved it as exit.s, assembled and linked it.  Ran it and it return 0 as expected.

I then edited the line:
```
 movl $0, %ebx
```
to:
```
 movl $200, %ebx
```
assembled and linked, ran it and it still returns 0?

exit.s looks like this now:
```

.section .data

.section .text
.globl _start
_start:
movl $1, %eax
movl $200, %ebx
init $0x80

```

Im running i686 kernel on a P4 M, any help?[/QUOTE]

For what it's worth, when I do the same, I get 200, as expected. Try all the steps again: modify the file, save the file in the editor, assemble it, link it. Maybe there was an error message you didn't catch, because "init" above should be "int".

---

### Post by elemental666 on 2006-06-09
the actual code said int, I posted from a different machine.  I dunno what the deal was, but I just tried it and it worked.  crazy

---

### Post by rplantz on 2006-06-09
One of the problems I have with that book is that it treats assembly lanugage separately. If you wish to integrate your assembly language functions with C/C++, the standard in the 32-bit x86 world is to place the return value in eax. For example, a program that simply returns a value would be
```

        .text
        .globl  main

main:   pushl   %ebp        # save caller's base pointer
        movl    %esp, %ebp  # establish our base pointer

        movl    $0, %eax    # return 0 to caller
        movl    %ebp, %esp  # restore stack pointer
        popl    %ebp        # restore caller's base pointer
        ret                 # back to caller

```
which is essentially equivalent to
```

int main() {
   return 0;
}

```

You can assemble this with ```

as --gstabs -o doNothing.o doNothing.s

```
and link it with the necessary C libraries with ```

gcc -o doNothing doNothing.o

```

The --gstabs assembler option allows you to use symbols in gdb.

Using gcc for the linking phase instead of ld automatically links in the C libraries. If you use ld, you need to explicitly list all the libraries.

---

