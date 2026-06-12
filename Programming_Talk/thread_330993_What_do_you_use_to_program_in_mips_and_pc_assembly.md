---
title: "What do you use to program in mips and pc assembly?"
date: 2007-01-03
forum: Programming Talk
---

### Post by suki on 2007-01-03
Could you please suggest what to use when programming for mips and pc assembly? Something with an easy interface would be nice. 

Before someone suggests Spim, it doesn't work on Edgy so well.

---

### Post by StormGuy on 2007-01-04
I'm looking for a similar program, myself.

---

### Post by StormGuy on 2007-01-04
bump

---

### Post by Wybiral on 2007-01-04
I've never used mips, but by PC assembly I assume you mean like at&t and intel assembly? Maybe I misinterpreted the question... But if you do mean intel/at&t then you need an assembler. [Nasm]("http://nasm.sourceforge.net/") for intel assembly, [GAS]("http://www.gnu.org/software/binutils/manual/gas-2.9.1/html_mono/as.html") for at&t assembly. I don't know what you mean by easy interface, I've never seen any assembly IDE's, I've always used a text editor and the command line to compile, and to the best of my knowledge thats what most assembly programmers do.

[Fasm]("http://flatassembler.net/") is also a good assembler for linux.


BTW, GAS is part of the GNU GCC compiler.

---

### Post by suki on 2007-01-04
> **Wybiral said:**
> I've never used mips, but by PC assembly I assume you mean like at&t and intel assembly? Maybe I misinterpreted the question... But if you do mean intel/at&t then you need an assembler. [Nasm]("http://nasm.sourceforge.net/") for intel assembly, [GAS]("http://www.gnu.org/software/binutils/manual/gas-2.9.1/html_mono/as.html") for at&t assembly. I don't know what you mean by easy interface, I've never seen any assembly IDE's, I've always used a text editor and the command line to compile, and to the best of my knowledge thats what most assembly programmers do.

[Fasm]("http://flatassembler.net/") is also a good assembler for linux.


BTW, GAS is part of the GNU GCC compiler.

Yes, that's what I meant regarding PC assembly. Thank you. Hopefully someone will shed some light on what to do for mips.

---

### Post by toojays on 2007-01-04
It's the same deal for MIPS, but you need to compile GAS to that it recognises MIPS instructions and assembles them accordingly.

---

### Post by Andrew &quot;Crusader&quot; on 2008-01-27
I can`t say, is it really food or bad - but i just found "MARS (MIPS Assembler and Runtime Simulator)" at
 [http://courses.missouristate.edu/KenVollmar/MARS/index.htm]("http://courses.missouristate.edu/KenVollmar/MARS/index.htm")

It is "An IDE for MIPS Assembly Language Programming. MARS is a lightweight interactive development environment (IDE) for programming in MIPS assembly language, intended for educational-level use with Patterson and Hennessy's Computer Organization and Design, 3rd edition."

I haven`t tested it yet - but i need right that kind of software for my job ;-)

---

