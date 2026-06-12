---
title: "run binary text file?"
date: 2009-08-15
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2009-08-15
Is there any way to make a text file with just this is in it:
```

1001

```
(Decimal value 7, ASCII value for system beep)
And have the computer interpret the 1001 as binary?

I tried changing permissions and making it executable and running it but it didn't work.

Why not? And how can I get this to work?

Hmmmmm

Thanks everyone.

---

### Post by Hexorg on 2009-08-15
You can write a little script to convert such file into the actual binary file (take groups of 8 characters convert them to one byte, and record it to another file).

Except I'm not sure if you will be able to run the new file because executables don't immediately contain opcodes, they have so sort of a header for a compatability with different processors.

---

### Post by Can+~ on 2009-08-15
There's a reason we've got compilers+linkers and assemblers, the things you code are translated to binary instructions, like (inventing):

```

 001010     00010     11000     00000      00000    00000000   
load word   dest      base      offset     shift    funccode

```

So in this fictional assembly line (which looks like MIPS) each set of bits denote a certain thing:

**load word:** Instruction to read from memory
**dest:** The number of the registry to store the value on registry 00010 (2)
**base: **Get the base address on memory to read from registry 11000 (24)
**offset:** The offset from the base, 0.
**shift:** No shifting here.
**funccode:** Function code, used for some instructions that have multiple things (e.g. arithmetic +, etc)

To get your computer to beep on plain binary (not ascii btw), you should store the number of the beep code to a registry, then the proper interrupt id, and finally issue an interruption to the processor.

As you can see, computer code is more complex than you think. There's a set of instructions (now you get why the numbers 386, 486, 586... on the processor?) and specific syntax depending on the architecture, main reason why are more "higher-level" ways to do it.

---

### Post by NathanB on 2009-08-16
> **Hexorg said:**
> 
Except I'm not sure if you will be able to run the new file because executables don't immediately contain opcodes, they have so sort of a header for a compatability with different processors.

Totally false!

Executables *do* contain opcodes -- and optionally contain other items such as, for instance, debugging information and application resources.

A 'header' is for what?? I think you might be thinking about a "stub" -- on certain platforms a 'stub' would run first to set-up a "backwards compatibility" environment and then launch the rest of the executable.  In general, CPUs only understand opcodes -- they cannot parse a header.  An executable's header is read by the Operating System's loader {Google "linkers and loaders"} to determine the kind of resources the program will need.

---

### Post by NathanB on 2009-08-16
> **c0mput3r_n3rD said:**
> Is there any way to make a text file with just this is in it:
```

1001

```
(Decimal value 7, ASCII value for system beep)

False...

1001 = 9, ASCII for HLT

0111 = 7, ASCII for BEL

> And have the computer interpret the 1001 as binary?

I tried changing permissions and making it executable and running it but it didn't work.

Why not? And how can I get this to work?


That is certainly a valid method for generating executables.  However, you need to include a little more data.  For instance, you need instructions for sending the BEL code to the Operating System STDOUT facilities.  You will also need to include some data to tell the Loader { Google search for "Linkers and Loaders" for a description } how to prepare for the execution of the program.  Assuming Linux is your platform, I suggest reading about the ELF requirements:

[http://en.wikipedia.org/wiki/Executable_and_Linkable_Format](http://en.wikipedia.org/wiki/Executable_and_Linkable_Format)

[http://www.muppetlabs.com/~breadbox/software/tiny/teensy.html](http://www.muppetlabs.com/~breadbox/software/tiny/teensy.html)

[http://www.muppetlabs.com/~breadbox/software/tiny/](http://www.muppetlabs.com/~breadbox/software/tiny/)

---

### Post by c0mput3r_n3rD on 2009-08-16
Thanks every body, I learned a lot!

And sorry for saying that 1001 was 7, my math was TOTALLY off! I was really tired when I decided to figure this out.  8 + 1 == 7...oh boy.   Thanks for every one not totally calling me out on this! haha

---

### Post by NathanB on 2009-08-16
Oh heck, dude, I've got more pedanticism for ya.  hehehe!
{{ Well, we **are** programmers -- if we didn't have a tendency to be pedantic... to be detail-oriented... to be intensely interested in how things work "under the hood", then we wouldn't be able to code our way out of a paper bag! }}

Truth is, your text file doesn't even store the number nine (other than the human-readable representation of a binary number).  What it actually stores is the ASCII codes for those 4 characters that you typed.  Namely:  the value 48 for the '0' character and 49 for the '1' character.  So, it stores the sequence...```
49, 48, 48, 49
```...followed by the new-line sequence.

By the way, welcome to the pedantic personality-type -- that and persistence are the two qualities that one must obtain in order to learn how to program.

---

### Post by Lux Perpetua on 2009-08-17
> **Can+~ said:**
> There's a reason we've got compilers+linkers and assemblers, the things you code are translated to binary instructions, like (inventing):

```

 001010     00010     11000     00000      00000    00000000   
load word   dest      base      offset     shift    funccode

```

So in this fictional assembly line (which looks like MIPS) each set of bits denote a certain thing:

**load word:** Instruction to read from memory
**dest:** The number of the registry to store the value on registry 00010 (2)
**base: **Get the base address on memory to read from registry 11000 (24)
**offset:** The offset from the base, 0.
**shift:** No shifting here.
**funccode:** Function code, used for some instructions that have multiple things (e.g. arithmetic +, etc)

To get your computer to beep on plain binary (not ascii btw), you should store the number of the beep code to a registry, then the proper interrupt id, and finally issue an interruption to the processor.

As you can see, computer code is more complex than you think. There's a set of instructions (now you get why the numbers 386, 486, 586... on the processor?) and specific syntax depending on the architecture, main reason why are more "higher-level" ways to do it....in short, the ASCII character for "beep" is no more an instruction telling the computer to produce a beep than the ASCII character 'A' is an instruction telling it to print a big "A" on your screen. In both, the character itself is just data; making the computer do something requires *code*, not data.

---

