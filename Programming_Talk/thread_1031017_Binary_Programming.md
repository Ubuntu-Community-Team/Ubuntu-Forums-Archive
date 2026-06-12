---
title: "Binary Programming"
date: 2009-01-04
forum: Programming Talk
---

### Post by Liliitha on 2009-01-04
Is it still possible to make a very small program in Binary and if so where in the computer could you input the information to make this program functional?

---

### Post by CptPicard on 2009-01-04
Grab your favourite hex editor and hack away.

Of course, most sane people at least use an assembler...

---

### Post by Wybiral on 2009-01-05
1. Learn assembly (you'll need to know how opcodes work, assembly is just a disguised version of them)
2. Learn about the elf executable format (this is a good start: [http://www.muppetlabs.com/~breadbox/software/ELF.txt](http://www.muppetlabs.com/~breadbox/software/ELF.txt))
3. Learn all of the hex values for your processors opcodes :) (have fun parsing through your intel manual)
4. Have even more fun manually setting all of the (dynamically moving, as you change your code) jump/entry points and manually encoding integers/floats into hex values

May I ask _why_ you would possibly want to do this?

---

### Post by monkeyking on 2009-01-05
Do you want to learn this stuff,
or do you want something fast.

Check my post here, if it is just for the learning experience
[http://ubuntuforums.org/showpost.php?p=6496578&postcount=22](http://ubuntuforums.org/showpost.php?p=6496578&postcount=22)

---

### Post by Liliitha on 2009-01-05
> **Wybiral said:**
> 1. Learn assembly (you'll need to know how opcodes work, assembly is just a disguised version of them)
2. Learn about the elf executable format (this is a good start: [http://www.muppetlabs.com/~breadbox/software/ELF.txt](http://www.muppetlabs.com/~breadbox/software/ELF.txt))
3. Learn all of the hex values for your processors opcodes :) (have fun parsing through your intel manual)
4. Have even more fun manually setting all of the (dynamically moving, as you change your code) jump/entry points and manually encoding integers/floats into hex values

May I ask _why_ you would possibly want to do this?

Assembly is a good way to learn how the computer is working on every process but doing it in Binary will probably give me more much needed insight on how the computer functions.  ._.

---

### Post by masque7 on 2009-01-05
> **Liliitha said:**
> Assembly is a good way to learn how the computer is working on every process but doing it in Binary will probably give me more much needed insight on how the computer functions.  ._.
The reason programming languages were created was to get away from binary...

---

### Post by jespdj on 2009-01-05
> **Liliitha said:**
> Assembly is a good way to learn how the computer is working on every process but doing it in Binary will probably give me more much needed insight on how the computer functions.  ._.
I don't think programming in binary will teach you a lot of useful things about how a computer functions.

If you want to learn how the microprocessor works, programming it in assembly is the best way to learn it. Read [Intel's processor programming manuals](http://www.intel.com/products/processor/manuals/) to learn all the details of programming the processor.

---

### Post by pp. on 2009-01-05
> **Liliitha said:**
> Assembly is a good way to learn how the computer is working on every process but doing it in Binary will probably give me more much needed insight on how the computer functions.  ._.

Given that the matrix printers of old could print every digit as a 5x7 dot matrix of pixels, by your logic you could gain even more insights by manually coding each of the ones and noughts as a matrix of pixels.

```
..X.. .XXX.
.XX.. X...X
X.X.. X...X
..X.. X...X
..X.. X...X
..X.. X...X
.XXX. .XXX.
```

LOL

---

### Post by Wybiral on 2009-01-05
> **Liliitha said:**
> Assembly is a good way to learn how the computer is working on every process but doing it in Binary will probably give me more much needed insight on how the computer functions.  ._.

Not really... For the most part, the assembly mnemonics will map pretty evenly to the processors opcodes. It's just you'll be reading and writing numbers instead of memorable mnemonics, and you'll have to manually adjust all the jump points and such. It's not going to help you understand anything more than assembly and you'll need to learn assembly first anyway to understand the instruction set...

---

### Post by Kilon on 2009-01-05
You can easily get lost in Assembly code. Study it for the fun but do not study with the hope that it will help you understand how a computer works. A computer is a highly complex machine. 

Assembly is only part of the picture. A very small part.

---

### Post by efexD on 2009-01-05
My best guess is HEX, Assembly, and making your own EXE.

---

### Post by pmasiar on 2009-01-06
> **Liliitha said:**
> Assembly is a good way to learn how the computer is working on every process but doing it in Binary will probably give me more much needed insight on how the computer functions.  ._.

This is advice from someone who has little if any experience in assembly programming. As Wyb said above, there is no difference between ASM and binary programming, only that ASM allows you to use mnemonic names for opcodes and variables, and calculates all offsets for you. Binary programming teaches you nothing more than ASM does (unless you count memory allocation and calculating ofsets as valuable skill).

---

