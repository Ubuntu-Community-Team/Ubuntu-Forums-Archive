---
title: "Using the gnu assembler for os development"
date: 2008-01-12
forum: Programming Talk
---

### Post by jimmyhilldrix on 2008-01-12
I recently inherited an old x86 PC and thought it would be fun to try writing a small OS for it.  I've written operating systems for the HC11 and PIC microcontrollers but I've never tried x86.  

I would like to use the as assembler to do this because I have a book that teaches that syntax.  When I compile boot sectors, however, a lot of extra data is inserted into the executable file (the first four characters are ".ELF")  I can only assume that the linker is trying to create a Linux executable which requires all of the extra instructions.  

Is there a directive that I can pass the as assembler that will force it to give me a straight assembly and not anything extra?

---

### Post by Wybiral on 2008-01-12
I'm not sure about the GNU assembler, but if you're able to use NASM, you can use the flag "-f bin" to tell it not to add any executable/object file linking info. You might be able to find the right flag using "man as" (no guarantees, but it's a good place to look).

---

### Post by Lster on 2008-01-12
Hi jimmyhilldrix

I was and still am developing a smaller kernel in my free time. I use Nasm and GCC entirely and never had any problems. Asking at OSDev might be a good idea or searching the manuals as Wybirals suggests.

Happy coding.

---

