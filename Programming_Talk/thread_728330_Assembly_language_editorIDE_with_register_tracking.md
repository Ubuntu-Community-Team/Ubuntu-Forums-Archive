---
title: "Assembly language editor/IDE with register tracking?"
date: 2008-03-18
forum: Programming Talk
---

### Post by Peter Cordes on 2008-03-18
I'm optimizing a small piece of assembly code.  (rshift.asm for AMD64 from libgmp).

I started to make a spreadsheet to keep track of what's in each XMM register after each instruction.  (columns for the XMM registers, rows for the instructions).  Then I thought, there should be a program to do this.  You could fill in symbolic names for parts of the XMM register after a load, and it would follow the state of the XMM registers.

Even cooler would be if it had an instruction reference built in, and you could tell it you want this part of this XMM register to contain something, and it would come up with all the instructions/sequences that accomplish that.  There is already a GPLed code that finds an optimal sequence, see [http://gmplib.org/list-archives/gmp-devel/2007-January/000708.html](http://gmplib.org/list-archives/gmp-devel/2007-January/000708.html)
and [http://en.wikipedia.org/wiki/Superoptimization](http://en.wikipedia.org/wiki/Superoptimization)

I'm pretty new at actually coding routines in asm, and SSE/SSE2 has lots of different instructions for shuffling/packing data.  I can't remember what they all are, let alone what they all do exactly.  It would be really cool to be able to say I want this part of this register to wind up containing what started in this other register, and I don't care what the other half of the register contains.  Then I'd get a list of choices of sequences of instructions.  I could mouse over them and the register-tracking would update with the effects of the sequence I was considering.


 So does anyone know of an AMD64 (or even just x86) assembly editor that can do anything like that?  Even just tracking registers, without the superoptimizing?  If not, someone should write one.  I suppose bochs would have code to run the x86 and AMD64 instruction sets.  But it's probably so tweaked for speed that it would be hard to just take the parts I'd need.  Instruction decoding isn't needed, since we're working in terms of the instructions, not their machine code.

 Ideally the editor would have a pipeline simulator for Core 2, K8, K10, etc.  so you could see how the OOO core handled your code.  I don't really see that happening without some serious help from Intel/AMD.  I read that AMD CodeAnalyst has a pipeline simulator for AMD CPUs, but it's not open source.

---

### Post by NathanB on 2008-03-18
The only thing ( that *I* am aware of ) that comes close { in the Atomic Bomb sense, not in the Horseshoes or Hand-grenade sense } to what you are describing is Jeff Owen's AsmIDE collection of tools:

[http://members.save-net.com/jko%40save-net.com/asm/](http://members.save-net.com/jko%40save-net.com/asm/)

The "pointy-clicky-ness" of these tools is NOT provided via a "cartoon" GUI, but is instead presented in the DOS-era 'Norton Commander' style.

I doubt that there is much 64-bit support, however Jeff *has* been extremely buzy with updating the collection -- especially the AsmBUG and related tools.

Nathan.

---

### Post by Peter Cordes on 2008-03-19
> **NathanB said:**
> The only thing ( that *I* am aware of ) that comes close { in the Atomic Bomb sense, not in the Horseshoes or Hand-grenade sense }


 Yes, I think I can just barely feel the heat from the radiation from that direction... :)

 The doc part with an x86 instruction set reference looked good, except that it doesn't include any MMX/SSE instructions.  Nice and fast tty-based program, too, which is always nice.

 Thanks.

---

### Post by bdsatish on 2008-03-19
Yes, Jeff's AsmBug is one of the best debuggers for assembly. A slightly outdated is ALD (assembly language debugger):

[http://ald.sourceforge.net/](http://ald.sourceforge.net/)

This is extremely good too.

And over all, we have the king: GDB, the GNU Debugger. I know how to use it to debug (register tracking + single stepping) ASM code. The advantage is that, GDB works seamlessly with others in the GNU toolchain. It is installed by default in binutils. 

I'm off to lunch now, but if you are interested in using GDB for asm, google it. I'll post my instructions, if you are interested.

---

### Post by Peter Cordes on 2008-03-19
> **bdsatish said:**
> 
And over all, we have the king: GDB, the GNU Debugger.


 I guess I should say that I currently use emacs (or jed sometimes), the GNU toolchain, and gdb for edit/compile,assemble/debug.  They work great.  I don't really need suggestions that are just alternatives to them.

 My main problem was keeping track of what's in what XMM register while I'm unrolling/software pipelining a loop.  It's hard for my brain to remember everything across the context switch to looking in the insn set reference for an instruction that does what I want and back.

 I did end up just making a spreadsheet with columns for the XMM registers, and starting with each cell containing a formula of =cell above.  When I write an instruction, I write in the new value.  OpenOffice has a highlight-function-values toggle, which makes all the formula results show green, and stuff I type show black.  This highlights when there's a change.

 Here's the spreadsheet, if you want to see exactly what I'm talking about.
[http://cordes.ca/repos/gmp-shift/asm.ods](http://cordes.ca/repos/gmp-shift/asm.ods)
[http://gmplib.org/list-archives/gmp-devel/2008-March/000771.html](http://gmplib.org/list-archives/gmp-devel/2008-March/000771.html)

 This worked quite well, but it would be even nicer if there was a program that at least saved you the trouble of filling in register values all the time.  It would have to prompt you for a symbolic name for the register after a load, though.

 I'm not trying to write large amounts of code in asm, I'm trying to optimize single functions.  Frequently I end up changing which register I'm using for what when I see a way to do something with fewer instructions.

 So thanks for the suggestions, but it's looking like if I want what I'm describing, I'll have to write it myself.

---

