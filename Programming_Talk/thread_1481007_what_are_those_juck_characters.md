---
title: "what are those juck characters?"
date: 2010-05-12
forum: Programming Talk
---

### Post by Max Destruction on 2010-05-12
hello all,

i have a question about those foreign 'junk' looking characters that present when i read in binary files. what are they?

i understand what binary code is, and than it looks like 00110101000111 etc. if that is the case, and these characters are neither ascii or 0011 tyle characters, what are they?

i want to understand! :( :P

---

### Post by Tony Flury on 2010-05-12
Ascii is only defined (i think this is right) for character codes 0 to 128 (encompassing the latin characters, control codes and punctuation marks etc). Any byte value > 128 could be interpreted in a variety of ways, including as a Junk character, or the start of a extended Unicode character - it depends on the progam you are using to display the file.

The upshot is, if you want to look at the contents of a binary file - don't use a text editor, use a program designed to do the job, which will display the file in Hex/Octal/decimal bytes (and maybe with an ASCII translation where appropriate). I can't think of the name of binary file display tool right now - as I have never needed to use one.

---

### Post by lisati on 2010-05-12
> **Tony Flury said:**
> 
The upshot is, if you want to look at the contents of a binary file - don't use a text editor, use a program designed to do the job, which will display the file in Hex/Octal/decimal bytes (and maybe with an ASCII translation where appropriate). I can't think of the name of binary file display tool right now - as I have never needed to use one.
+1

[Hexdump]("http://www.oreillynet.com/linux/cmd/cmd.csp?path=h/hexdump") might do the trick - it is installed by default on my machine (10.04)

---

### Post by Max Destruction on 2010-05-12
ok thanks guys (will mark as solved)

i have a new question tho now, i just did a hexdump on a bin file (sed)

```

000d2c0 323a 0805 0000 0000 0000 0000 0000 0000
000d2d0 b488 0805 3245 0805 0000 0000 0000 0000
000d2e0 0000 0000 b48c 0805 3251 0805 0000 0000
000d2f0 0000 0000 0000 0000 b490 0805 0000 0000
000d300 0000 0000 0000 0000 0000 0000 0000 0000
000d310 0001 0000 631c 0805 0000 0000 002d 0000
000d320 6328 0805 0001 0000 0100 0000 b380 0805
000d330 0001 0000 2e00 6873 7473 7472 6261 2e00
000d340 6e69 6574 7072 2e00 6f6e 6574 412e 4942
000d350 742d 6761 2e00 6f6e 6574 672e 756e 622e
000d360 6975 646c 692d 0064 672e 756e 682e 7361
000d370 0068 642e 6e79 7973 006d 642e 6e79 7473
000d380 0072 672e 756e 762e 7265 6973 6e6f 2e00
```

why are there characters that are not 0's or 1's?

---

### Post by lisati on 2010-05-12
That's "[hexadecimal]("http://en.wikipedia.org/wiki/Hexadecimal")"

---

### Post by roccivic on 2010-05-12
If you need to edit a binary file:
```
sudo apt-get install ghex
```

---

### Post by Max Destruction on 2010-05-12
is there any way i can edit a  binary file in binary? just convert it from hex and edit? or is it more complicated?
(is reverse engineering really that simple?)

---

### Post by ibuclaw on 2010-05-12
> **Max Destruction said:**
> is there any way i can edit a  binary file in binary? just convert it from hex and edit? or is it more complicated?
(is reverse engineering really that simple?)

You know ... I'm not sure of a program that will actually output an application respresentation in 1's and 0's.

There is, however:

**hexdump** - to dump hex representation
**od** - which traditionally is used to dump octal representation, but can also show ascii, decimal (signed / unsigned) and float.
**strings** - to output all valid alphanumeric strings in a file / binary.
**objdump** - capable of outputting a loose asm representation of the binary / object file. And given that debugging code is embedded in the executable, you can extract data such as lines and filenames of the binary file (useful for debugging applications / compilers).

Regards

---

### Post by StephenF on 2010-05-12
The real question should be, "Is hexadecimal that difficult?". Hex was adopted to make binary as human readable as possible. Each character be it numerical or in the range A-F represents a 4 bit (binary digit block) with letters A through F representing the blocks that amount to 10 through 15. That way each block is represented by a single digit.

0000 = 0
0010 = 2
0011 = 3
1111 = F

A 32 bit binary number can be represented with eight hexadecimal digits. This is a lot easier to proof read. Try saying a 32 bit binary number out loud then its hexadecimal equivalent.

Finally, most hex editors (hexdump is not an editor) will allow you to select a block of bytes and read the value contained in various number bases and formats.

---

### Post by Max Destruction on 2010-05-12
ok. 

so, hex is hard to read (but easier than binary). but it would be easy for enough for a computer to read yeah?

for example, if a program converted hex to ascii, that would seem to me to imply that the ascii code would be the programs source code (human readable)? i cannot believe that this is true though because otherwise any program could be decompiled with a click..

i am missing something ....:/

---

### Post by ibuclaw on 2010-05-12
> **Max Destruction said:**
> ok. 

so, hex is hard to read (but easier than binary). but it would be easy for enough for a computer to read yeah?

for example, if a program converted hex to ascii, that would seem to me to imply that the ascii code would be the programs source code (human readable)? i cannot believe that this is true though because otherwise any program could be decompiled with a click..

i am missing something ....:/

No, there is a **strong** difference between an applications **high level language** source code and the object file generated from a compiler processing it.

An ascii representation of hex would look like jibberish.

Here is an example of an od -a dump
```

0000000 del   E   L   F soh soh soh nul nul nul nul nul nul nul nul nul
0000020 soh nul etx nul soh nul nul nul nul nul nul nul nul nul nul nul
0000040   ( nul nul nul nul nul nul nul   4 nul nul nul nul nul   ( nul
0000060  ht nul ack nul   U  ht   e   ]   C nul nul nul nul   G   C   C
0000100   :  sp   (   U   b   u   n   t   u  sp   4   .   4   .   3   -
0000120   4   u   b   u   n   t   u   5   )  sp   4   .   4   .   3 nul
0000140 nul   .   s   y   m   t   a   b nul   .   s   t   r   t   a   b
0000160 nul   .   s   h   s   t   r   t   a   b nul   .   t   e   x   t
0000200 nul   .   d   a   t   a nul   .   b   s   s nul   .   c   o   m
0000220   m   e   n   t nul   .   n   o   t   e   .   G   N   U   -   s
0000240   t   a   c   k nul nul nul nul nul nul nul nul nul nul nul nul
0000260 nul nul nul nul nul nul nul nul nul nul nul nul nul nul nul nul
*
0000320 esc nul nul nul soh nul nul nul ack nul nul nul nul nul nul nul
0000340   4 nul nul nul enq nul nul nul nul nul nul nul nul nul nul nul
0000360 eot nul nul nul nul nul nul nul   ! nul nul nul soh nul nul nul
0000400 etx nul nul nul nul nul nul nul   < nul nul nul nul nul nul nul
0000420 nul nul nul nul nul nul nul nul eot nul nul nul nul nul nul nul
0000440   ' nul nul nul  bs nul nul nul etx nul nul nul nul nul nul nul
0000460   < nul nul nul nul nul nul nul nul nul nul nul nul nul nul nul
0000500 eot nul nul nul nul nul nul nul   , nul nul nul soh nul nul nul
0000520   0 nul nul nul nul nul nul nul   < nul nul nul   $ nul nul nul
0000540 nul nul nul nul nul nul nul nul soh nul nul nul soh nul nul nul
0000560   5 nul nul nul soh nul nul nul nul nul nul nul nul nul nul nul
0000600   ` nul nul nul nul nul nul nul nul nul nul nul nul nul nul nul
0000620 soh nul nul nul nul nul nul nul dc1 nul nul nul etx nul nul nul
0000640 nul nul nul nul nul nul nul nul   ` nul nul nul   E nul nul nul
0000660 nul nul nul nul nul nul nul nul soh nul nul nul nul nul nul nul
0000700 soh nul nul nul stx nul nul nul nul nul nul nul nul nul nul nul
0000720 dle stx nul nul nul nul nul nul  bs nul nul nul bel nul nul nul
0000740 eot nul nul nul dle nul nul nul  ht nul nul nul etx nul nul nul
0000760 nul nul nul nul nul nul nul nul dle stx nul nul  cr nul nul nul
0001000 nul nul nul nul nul nul nul nul soh nul nul nul nul nul nul nul
0001020 nul nul nul nul nul nul nul nul nul nul nul nul nul nul nul nul
0001040 soh nul nul nul nul nul nul nul nul nul nul nul eot nul   q del
0001060 nul nul nul nul nul nul nul nul nul nul nul nul etx nul soh nul
0001100 nul nul nul nul nul nul nul nul nul nul nul nul etx nul stx nul
0001120 nul nul nul nul nul nul nul nul nul nul nul nul etx nul etx nul
0001140 nul nul nul nul nul nul nul nul nul nul nul nul etx nul enq nul
0001160 nul nul nul nul nul nul nul nul nul nul nul nul etx nul eot nul
0001200  bs nul nul nul nul nul nul nul enq nul nul nul dc2 nul soh nul
0001220 nul   t   e   s   t   .   c nul   m   a   i   n nul
0001235

```



Luckily (for us application debuggers), there are tools out there that help to make it in a more human readable format.

Here is the same file, but using an objdump -d dump.
```


test.o:     file format elf32-i386


Disassembly of section .text:

00000000 <main>:
   0:	55                   	push   %ebp
   1:	89 e5                	mov    %esp,%ebp
   3:	5d                   	pop    %ebp
   4:	c3                   	ret    

```

From this code, would be able to guess the contents of the source file?

Well... if you are half competent, you'd be right in thinking:
```
main(){}
```
The minimal valid C code needed to create a binary object.


But it if were something a little more complex, chances am you wouldn't know how to make an identical C representation of it...

---

### Post by Tony Flury on 2010-05-12
The hex codes you can see is the hex version of the machine code - the register access, value moves etc. The source code is very different. In effect the Source code is a set of instructions to a compiler to produce the machine code.

You can convert some machine code back to source code - for some languages - but not by reading the binary file in ASCII. Any decompilation you do could well loose a lot in translation - including all the variable names, comments, and many of the advanced features of the language.

---

### Post by randomizer101 on 2010-05-12
> **Max Destruction said:**
> ok. 

so, hex is hard to read (but easier than binary). but it would be easy for enough for a computer to read yeah?

for example, if a program converted hex to ascii, that would seem to me to imply that the ascii code would be the programs source code (human readable)? i cannot believe that this is true though because otherwise any program could be decompiled with a click..

i am missing something ....:/

Translating the hex dump to ascii would not give you the source code. The hex is a base-16 representation of the binary, and converting it to ascii (although not standard 7-bit ascii) may give you something like this:

.Ò¸5«\røO&#338;îÒ©.D®r#i&#8221;"Q&#8221;jÏân...w«.=.&#382;«ª8"{)Gq1..Î¢9TF6$¸±{@&#8482;u.²N*fÓ¾.Û[â&#8222;._r¦Bípy&#402;u.&#339;].U&#381;p&#339;¨yÿÿÏ®ÃS&#8230;Ó&#8249;.&#8221;î.ì¾&#8226;]V¥uÇyª&#8220;Õïm&#8240;>8T[`×&#8230;ÛMÖ¡SÁ&#8224;&#8220;=6&#8216;D&#8221;&#8217;a§%&#339;ÊáÕ^&#8218;*@â|Ø!xS3

If you can work out what that is you get a cookie. :)

Now Java and .NET binaries can be decompiled I believe, but that's because they aren't compiled into machine code until runtime.  They instead use a much more human-readable intermediate bytecode (don't quote me on that for Java though, I don't know it that well).

---

### Post by Max Destruction on 2010-05-12
ahhhhh.

got it.

cheers guys O:)

---

### Post by jwbrase on 2010-05-12
> **Max Destruction said:**
> hello all,

i have a question about those foreign 'junk' looking characters that present when i read in binary files. what are they?

i understand what binary code is, and than it looks like 00110101000111 etc. if that is the case, and these characters are neither ascii or 0011 tyle characters, what are they?

i want to understand! :( :P

I think you misunderstand: You say "...if ... these characters are neither ASCII or 0011 style characters...", but that's not how it works. Information in a computer is *only* "0011 style" numbers, and ASCII is just a special way of giving *meaning* to those numbers. 01000100 can mean either the ascii character D, or the number 68 (44 in Hexadecimal), in an executable it could also mean an instruction for the computer to do something.

So when you open up a binary file in a text editor, you're telling your computer "tell me what this string of 1's and 0's means if we interpret it with ASCII", and you generally get garbage. (Actually, you're usually telling it to interpret it with an extension of ASCII, since modern computers divide numbers up into chunks of 8 1's and 0's, while ASCII uses just 7. That means you have an extra one or zero to assign extra symbols (or other meaning) to).

When you execute a binary file, you're telling your computer "Interpret this string of 1's and 0's as instructions and do what it says".

In other contexts, you might tell it to interpret 1's and 0's as numbers, and so forth.

But any given string of 1's and 0's can be interpreted as any of these (and quite a few other things as well). It's just that normally you'll only be able to *usefully* interpret it as one thing, and the rest will all be meaningless garbage.

> **ibuclaw said:**
> You know ... I'm not sure of a program that will actually output an application respresentation in 1's and 0's.

Beav, in the repositories, will do this, though the UI is a pain.

---

