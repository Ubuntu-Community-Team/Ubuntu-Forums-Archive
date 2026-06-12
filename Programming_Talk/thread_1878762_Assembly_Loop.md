---
title: "Assembly: Loop?"
date: 2011-11-10
forum: Programming Talk
---

### Post by fallenshadow on 2011-11-10
How can you do a loop in assembly comparing to a preset number so the loop will end? (when it matches that preset number)

Im trying to learn assembly but to be honest I really suck at it. I find programming in any other language easier.

I want to do something like a for loop in C++ and Java.

---

### Post by 11jmb on 2011-11-10
> **fallenshadow said:**
> I find programming in any other language easier.


The point of assembly programming is not to be easy, it is to be informative.

there is no **for** or **while** operation in assembly, but you will want to have a count variable that you increment or decrement each iteration, and at the end or beginning of each iteration (while vs. do-while) you will have some form of branch statement comparing to your count variable.

---

### Post by matt_symes on 2011-11-10
Hi

> How can you do a loop in assembly comparing to a preset number so the loop will end?There are a number of ways to do this and one way is to use the ecx register (set the preset value in the ecx register) and the loop command.

[http://en.wikibooks.org/wiki/X86_Assembly/Control_Flow](http://en.wikibooks.org/wiki/X86_Assembly/Control_Flow) (*intel syntax*)

It depends on exactly what you are trying to achieve with the loop.

Kind regards

---

### Post by fallenshadow on 2011-11-10
Thanks for the help guys I figured it out! :D

---

### Post by Bachstelze on 2011-11-10
> **11jmb said:**
> The point of assembly programming is not to be easy, **it is to be informative**.


Surely you jest.

---

### Post by 11jmb on 2011-11-10
> **Bachstelze said:**
> Surely you jest.

I was going to try a "don't call me shirley" response, but it just doesn't work in text :)

I do not jest. It is not something that everybody has to learn, and direct assembly programming is barely relevant to modern development, but knowledge of assembly is a must for anybody who wants to learn about architectures or operating systems.

---

### Post by lisati on 2011-11-10
Reading this thread reminded me of using the "JCXZ" (Jump if CX is zero) instruction in a couple of 16-bit programs back in the 90s. Borland's user guide for Turbo Assembler mentions a 32-bit version, JECXZ. The copy I have only covers up to the 80386, so I'd need to do a search for something similar on newer CPUs. One of the "LOOP" instructions would probably suit many programs better.

---

### Post by matt_symes on 2011-11-10
Hi

For the OP and Lisati. Go to the source. x86 instruction set.

[http://www.intel.com/content/www/us/en/processors/architectures-software-developer-manuals.html](http://www.intel.com/content/www/us/en/processors/architectures-software-developer-manuals.html)

Kind regards

---

### Post by Arndt on 2011-11-10
> **11jmb said:**
> The point of assembly programming is not to be easy, it is to be informative.



This sounded to me like "the point of atoms is to give students practice with the microscope", but in the light of your further comments, I understand what you mean.

---

