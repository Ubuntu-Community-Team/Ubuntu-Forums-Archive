---
title: "Learning Assembly"
date: 2006-01-05
forum: Programming Talk
---

### Post by Burke on 2006-01-05
This seems like the kind of thing that would have been posted before, but I searched and could not find it, so here I am. ;)

I'm about to embark on a most likely painful quest to learn assembly. I have extremely little knowledge on the subject and was wondering if anyone has a favourite book or online resource on the subject that they would like to share to get me started.

Any help would be greatly appreciated.

---

### Post by cwaldbieser on 2006-01-05
[QUOTE=Burke]This seems like the kind of thing that would have been posted before, but I searched and could not find it, so here I am. ;)

I'm about to embark on a most likely painful quest to learn assembly. I have extremely little knowledge on the subject and was wondering if anyone has a favourite book or online resource on the subject that they would like to share to get me started.

Any help would be greatly appreciated.[/QUOTE]
Just to clarify, do you want to learn it for x86?

---

### Post by Burke on 2006-01-05
That's the plan.

---

### Post by csowm5je on 2006-01-05
** Programming from the Ground Up**
introduction to programming using Linux assembly language.
[http://www.cafepress.com/bartlettpublish.8640017](http://www.cafepress.com/bartlettpublish.8640017)
[http://www.amazon.com/gp/product/0975283847/002-9987578-3756020?n=283155](http://www.amazon.com/gp/product/0975283847/002-9987578-3756020?n=283155)

---

### Post by Burke on 2006-01-05
Awesome. Thanks very much. I will definitely pick up a copy of that. As a bonus, its within that magical limit of 500 pages which determines whether or not I finish a book :)

---

### Post by kudu on 2006-01-05
[QUOTE=csowm5je]** Programming from the Ground Up**
introduction to programming using Linux assembly language.
[http://www.cafepress.com/bartlettpublish.8640017](http://www.cafepress.com/bartlettpublish.8640017)
[http://www.amazon.com/gp/product/0975283847/002-9987578-3756020?n=283155](http://www.amazon.com/gp/product/0975283847/002-9987578-3756020?n=283155)[/QUOTE]


Great book for Linux assembly programming. There's also HLA - The Art of Assembly Language. Google it.

In fact...Google Linux Assembly and a bunch of sources you shall find, including tutorials.

kudu...out

---

### Post by csowm5je on 2006-02-13
[http://download.savannah.gnu.org/releases/pgubook/ProgrammingGroundUp-1-0-booksize.pdf](http://download.savannah.gnu.org/releases/pgubook/ProgrammingGroundUp-1-0-booksize.pdf)

---

### Post by orlox on 2006-02-13
check this site

[http://asm.sourceforge.net/](http://asm.sourceforge.net/)

---

### Post by DarkW0lf on 2006-03-31
The HLA links are:

[http://webster.cs.ucr.edu/](http://webster.cs.ucr.edu/)
[http://www.geocities.com/kahlinor/HLA.html](http://www.geocities.com/kahlinor/HLA.html)

Sevag has some great utilities that make setting up/using HLA much easier.

---

### Post by sharperguy on 2006-04-01
Love Programming from the ground up and would have recommended tit had i not been too late. BTW anyone know an emulator-thing which will let me write code in "assembly language" exept it is coded the same way as on BBC computers (cant remember which processor they use) ie it dosnt actually assemble the code but converts it as HLL's do exept the code looks just like that type of assembly. 

Reason: I will have to learn it for advanced higher computing and i though t would help to know it before hand (since im already learning i686 assembly for the fun of it out of the abouve ebook).

---

### Post by LordHunter317 on 2006-04-01
I think the better question is *why* do you want to learn x86 assembly?

If you want to learn assembly, don't learn x86 assembly.  Really.  It's simply retarded and a headache to deal with.  

Unfortunately, it's all I know so I can't recommend any other books, but I would do some research.

---

### Post by sharperguy on 2006-04-01
maybea because x86 is the only system acessable?

---

### Post by supirman on 2006-04-02
x86 assembly isn't too bad after you get familiar with it.  One thing that can be confusing is the assembler syntax -- especially when viewing different tutorials.  I prefer the AT&T style (which the GNU assembler uses), which is of the form:  op src, dest.  Plus I like how registered are prefixed with %, immediate operands with $, etc.

Now if you want to see ugly, mix real mode and protected mode assembly.  Dealing with the segment:offset addressing, setting up a proper gdt, mixing 16  and 32 bit code, etc is a pain, but I found it fun.  I was given the task of writing a custom x86 bootloader for my company's new products so I had to deal with all of this.  As I said, it was a pain, but luckily I'm a massochist :)

BTW, if you ever wanted to write your own bootloader (mostly for learning purposes) I'd recommend setting up an emulator, such as Bochs.  Bochs has support for using it's internal debugger, or for interfacing with gdb.  Stepping line by line through your code is a great tool, especially when new to assembly.  When deveoping the bootloader for our new product, there was no way to know if anything was happening correctly, so having Bochs was invaluable.  It does have a shortcoming at this point, in that it doesn't support  P6 instructions, such as cmovcc and it will just die if it comes across one.  

Assembly can very fun, so good luck!

---

### Post by Azrael on 2006-04-02
[quote=LordHunter317]
If you want to learn assembly, don't learn x86 assembly.  Really.  It's simply retarded and a headache to deal with.[/quote]
Bullshit. I, for one, find it quite logical and straightforward to deal with.

---

### Post by rplantz on 2006-04-02
[QUOTE=Azrael]Bullshit. I, for one, find it quite logical and straightforward to deal with.[/QUOTE]

I've been working with assembly language for over 40 years on many machines, including z80, Data General Nova/Eclipse, DEC PDP-11, 680xx, PPC, IBM Series/1, i86, Itanium, etc. Projects range from a CT scanner to a shipping container handling system. And I've taught the class at the university level for over 20 years.

The best (most honest) remark I've heard about which assembly language is best came in the middle 1970s when I asked a friend about the Data General Nova compared to the DEC PDP-11. He first discussed the differences in the assembly languages. (We would now probably call the Nova RISC and the PDP-11 CISC.) He said that you could solve a problem with fewer lines of code on the PDP-11, but both machines took about the same amount of time. Then he said that he preferred the Nova and added that was probably because he had **written much more code for it and was more used to it.**

I always remember his remarks whenever I see discussions about which language is better.

---

### Post by Gustav on 2006-04-02
I learned assembler on a calculator that run on a z80 processor (Ti-83). And I have programmed some on a Motorola 68000.

The basic measurement for how fun it is to program assembler on a special processor is - how limited the language is (the more limited, the more fun).

In a school-project I and two others built a computer. In that we built our own processor with our own assembler language. The output was a TV-screen (we only had one instruction to write a pixel at a time at the screen) and the input was two TAC2 joystics. That was great to program on :)

---

### Post by Azrael on 2006-04-02
edited due to latent indifference

---

