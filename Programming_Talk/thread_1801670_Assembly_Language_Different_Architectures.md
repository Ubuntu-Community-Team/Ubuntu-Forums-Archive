---
title: "Assembly Language: Different Architectures?"
date: 2011-07-10
forum: Programming Talk
---

### Post by gingerkid101 on 2011-07-10
At my school, they teach us Assembly in SPARC Architecture.

How can I learn Assembly on my PC using UBUNTU m4 assembler and gcc compiler?

It doesn't recognize my registers, which I know as
%g0 to %g6, %o0 to %o6, %l1 to l6, and %i0 to %i6

It also doesn't recognize my memory allocation
save %sp, -96, %sp


Any knowledgeable people out there that can help me learn the specifics of assembly on my computer?

I am on an AMD Phenom X4 9750 quad-core processor, not sure if the processor has anything to do with assembly. I am pretty confused about the matter, honestly.

---

### Post by lisati on 2011-07-10
> **gingerkid101 said:**
> 

I am on an AMD Phenom X4 9750 quad-core processor, not sure if the processor has anything to do with assembly. I am pretty confused about the matter, honestly.

Assembly language depends a lot more on the specific processor family that you're writing a program for than a higher level language does, as it written in a way that is a lot closer to what is actually happening in the hardware. You are likely to run into challenges of the kind you mention because AMD processors have a different instruction set and architecture to a SPARC-based system.

---

### Post by abybaddi on 2011-07-11
> **lisati said:**
> Assembly language depends a lot more on the specific processor family that you're writing a program for than a higher level language does, as it written in a way that is a lot closer to what is actually happening in the hardware. You are likely to run into challenges of the kind you mention because AMD processors have a different instruction set and architecture to a SPARC-based system.

Yes, he speaks the truth. For assembly under linux you can use Netwide Assembler or have a look at this:[http://asm.sourceforge.net/](http://asm.sourceforge.net/)

The language would be very different from the SPARC-based language.

---

### Post by slavik on 2011-07-11
if you didn't learn in class that different processors have different ISAs, then drop class, turn off computer and never touch it again.

---

### Post by Lux Perpetua on 2011-07-11
> **gingerkid101 said:**
> I am pretty confused about the matter, honestly.Clearly, but we all were once...

Your AMD processor will never run SPARC code, even if you managed to assemble it somehow (with SPARC cross-binutils). AMD processors are Intel-compatible, so to assemble and run code on your computer, you should start by learning about the x86 instruction set. 

I should warn you that writing x86 code is more difficult (IMHO) than coding for SPARC. Two central difficulties are (1) rather few general-purpose registers, and (2) high non-orthogonality, which makes it easy to accidentally write instructions that don't actually exist, at least until you get used to certain things. 

Also, FYI, m4 is not an assembler; it is a text preprocessor. It has nothing particularly to do with assembly.

---

### Post by gingerkid101 on 2011-07-11
> **slavik said:**
> if you didn't learn in class that different processors have different ISAs, then drop class, turn off computer and never touch it again.

troll detected.

---

### Post by gingerkid101 on 2011-07-11
> **Lux Perpetua said:**
> Clearly, but we all were once...

Your AMD processor will never run SPARC code, even if you managed to assemble it somehow (with SPARC cross-binutils). AMD processors are Intel-compatible, so to assemble and run code on your computer, you should start by learning about the x86 instruction set. 

I should warn you that writing x86 code is more difficult (IMHO) than coding for SPARC. Two central difficulties are (1) rather few general-purpose registers, and (2) high non-orthogonality, which makes it easy to accidentally write instructions that don't actually exist, at least until you get used to certain things. 

Also, FYI, m4 is not an assembler; it is a text preprocessor. It has nothing particularly to do with assembly.

Few more questions:
What is the difference between a text preprocessor and an assembler?
Are programs compiled in SPARC not able to be run on systems with other processors?
Is this why it was impossible to run Windows on Macs when they had PowerPC processors?

Thanks again, Chris.

---

### Post by ziekfiguur on 2011-07-11
> **gingerkid101 said:**
> Few more questions:
What is the difference between a text preprocessor and an assembler?
Are programs compiled in SPARC not able to be run on systems with other processors?
Is this why it was impossible to run Windows on Macs when they had PowerPC processors?

Thanks again, Chris.

The fact that you don't know the answers to these questions indicates that there is something seriously wrong with the class you are taking at school.
I would advise you to start reading the book you can find on [this page]("http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/index.html"), there are separate versions for windows and linux, make sure you get the right one. Even if you don't want to use the HLA macro's and library used by the book, it has all information you should know about writing assembly and explains it in a (IMO) very readable way.

---

### Post by Lux Perpetua on 2011-07-11
> **gingerkid101 said:**
> Few more questions:
What is the difference between a text preprocessor and an assembler?The former expands macros in text. The latter translates assembly language to machine code. As you can see, they're not very similar. 
> **gingerkid101 said:**
> Are programs compiled in SPARC not able to be run on systems with other processors?What do you mean "compiled in SPARC?" Compiled on a SPARC machine, or written in SPARC assembly? In either case, though, the answer is that such a program wouldn't run on another type of processor, as far as you're concerned (since you're not going to be cross-compiling any time soon).

---

### Post by TwoEars on 2011-07-11
> **gingerkid101 said:**
> Few more questions:
What is the difference between a text preprocessor and an assembler?
Are programs compiled in SPARC not able to be run on systems with other processors?
Is this why it was impossible to run Windows on Macs when they had PowerPC processors?

Thanks again, Chris.

You seem a little lost. If you're just starting your class, then I recommend waiting until you've learnt more, or perhaps reading more books on the subjects. These are fundamental questions that you really should be able to answer yourself.

---

### Post by Bachstelze on 2011-07-11
I think what you need is a book that focuses more on real-life systems, because you seem to have a problem grasping concepts without an example. [CS:APP](http://csapp.cs.cmu.edu/) would probebly be a good choice for you.

---

### Post by gingerkid101 on 2011-07-11
> **TwoEars said:**
> You seem a little lost. If you're just starting your class, then I recommend waiting until you've learnt more, or perhaps reading more books on the subjects. These are fundamental questions that you really should be able to answer yourself.

This is what I hate about a lot of programming classes. A lot of them just blindly tell you what to do to make a program work without explaining why it works that way. We are pretty far into the course. Given, this is just the first entry level course for assembly. I'm taking another class on Computer Architecture next semester which is the next one to follow this one.

I could write you a fully functional and optimized SPARC program in assembly if needed, but it seems pointless as SPARC is not even used anymore outside of the server on which we compile and run our code.

---

### Post by gingerkid101 on 2011-07-11
> **Bachstelze said:**
> I think what you need is a book that focuses more on real-life systems, because you seem to have a problem grasping concepts without an example. [CS:APP]("http://csapp.cs.cmu.edu/") would probebly be a good choice for you.

I would hardly say that I have problems grasping concepts, as they were never presented to me before now...

The title of the class is Computer Organization and Programming. Next on the scale for me to take is Computer Architecture. I'm assuming that once I get into Computer Architecture, they'll do a better job of explaining these things, but these specifics (or maybe they just take for granted that everybody already knows these things) were not mentioned in this class.

It's pretty useless that they teach assembly in SPARC when they should be teaching x86 which seems to be the much more applicable and practical version, given the current state of technology.

---

### Post by TwoEars on 2011-07-11
> **gingerkid101 said:**
> This is what I hate about a lot of programming classes. A lot of them just blindly tell you what to do to make a program work without explaining why it works that way. We are pretty far into the course. Given, this is just the first entry level course for assembly. I'm taking another class on Computer Architecture next semester which is the next one to follow this one.

I could write you a fully functional and optimized SPARC program in assembly if needed, but it seems pointless as SPARC is not even used anymore outside of the server on which we compile and run our code.

The reason why SPARC is used is because it's a very simple and easy to learn language compared more complex ones such as x86. The idea is to give you a general understanding of an assembly language - the same reason why languages such as Delphi are still used to teach. It is to give you an idea of the fundamentals, not to teach you everything in the whole world. ;)

If, for whatever reason, you need to learn assembly in x86 for a job or for personal interest, then learning the SPARC version gives a good place to start from.

---

### Post by abybaddi on 2011-07-11
> **slavik said:**
> if you didn't learn in class that different processors have different ISAs, then drop class, turn off computer and never touch it again.


Suits your signature. LOL!

---

### Post by slavik on 2011-07-11
> **TwoEars said:**
> The reason why SPARC is used is because it's a very simple and easy to learn language compared more complex ones such as x86. The idea is to give you a general understanding of an assembly language - the same reason why languages such as Delphi are still used to teach. It is to give you an idea of the fundamentals, not to teach you everything in the whole world. ;)

If, for whatever reason, you need to learn assembly in x86 for a job or for personal interest, then learning the SPARC version gives a good place to start from.
x86 is not complicated, x86 is plain stupid. even the old ibm/370 had a better ISA.

ibm/370 allowed you to do add where you could specify the target for the result, in x86 terms, it could be something like this:
```
add eax, ebx, ecx
```
where the mathematical equivalent is:
```
ecx = eax + ebx
```

---

### Post by lisati on 2011-07-11
<aside>
Glad to see that someone else here has done some IBM/370 assembly programming! It has been a while.....
</aside>

---

### Post by slavik on 2011-07-11
> **lisati said:**
> <aside>
Glad to see that someone else here has done some IBM/370 assembly programming! It has been a while.....
</aside>
a professor told me ... ;)

---

### Post by TwoEars on 2011-07-11
> **slavik said:**
> x86 is not complicated, x86 is plain stupid. even the old ibm/370 had a better ISA.

ibm/370 allowed you to do add where you could specify the target for the result, in x86 terms, it could be something like this:
```
add eax, ebx, ecx
```
where the mathematical equivalent is:
```
ecx = eax + ebx
```

Complicity is merely a degree of stupidity ;)

---

