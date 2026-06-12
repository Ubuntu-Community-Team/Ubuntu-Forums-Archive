---
title: "Converting a C file to a.out"
date: 2012-09-02
forum: Programming Talk
---

### Post by IAMTubby on 2012-09-02
Hey,
I have a few questions.

1)Can you give me more insight into how a C file is converted into a a.out file ?

2)Why is it called an a.out file. I read that it stands for assembler output. But we are not using an assembler , we are using a gcc compiler right ? (Read that an assembler takes Assembler Pnemonics as input whereas a compiler takes a C file as input.)

3)Isn't a compiler supposed to convert the C file to a binary ? But when I do a vi a.out, I don't see any 0's and 1's. It's all ```
@^@^D^@^@^
``` kind of thing.

4)Once the C file is converted to a.out, WHAT IS IT THAT RUNS THE a.out FILE ? THAT IS, WHEN I DO, ./a.out, WHAT IS HAPPENING ? IS IT THE ALU THAT IS RUNNING THE CODE? OR IS THAT A VERY BOOKISH UMBRELLA WORD ?

---

### Post by Bachstelze on 2012-09-02
1) The preprocessor processes your # directives, the compiler compiles your code to assembly, the assembler compiles it to machine language, and the linker adds all the necessary bits to make it a complete executable. If you want more details, get a book on compilers.

2) See above. You do use an assembler, among other things. The name a.out really is irrelevant, though, and the -o flag of gcc is the most widely used.

3) You are mistaken about the meaning of "binary". *Every file* in a computer is made of bits, including text files. vim displays text files, meaning it divides the file into chunks of 8 bits, and reads them as characters (for example 01000001 corresponds to the letter A). When we say a file is a "binary file", it doesn't mean that it is made of 0s and 1s (because all files are), but that it is not a text file, meaning its bits cannot be divided into chunks of 8 and interpreted as readable characters. When you see ^@ in vim, it means that the corresponding byte consists of eight 0s.

4) If you want to know every detail of what happens, again, get a book. The operating system is responsible for running your program, and of course it is the processor that runs the actual code. ALU means Arithmetic-Logic Unit, and it is the part of the processor that performs, you guessed it, arithmetic and logic operations, like addition, substraction and logical AND. (Generally the ALU works only on integers, floating-point operations are done on another part of the processor.)

---

### Post by Mistrpopo on 2012-09-02
> **IAMTubby said:**
> 
1)Can you give me more insight into how a C file is converted into a a.out file ?

a.out is just the default output name for the gcc compiler. You can use your gcc compiler to compile your C code and give a different output name like this:

```
gcc <input_file>.c -o <output_file>
```

example:
```
gcc myfirstprog.c -o myfirstprog
```

This will produce a binary EXECUTABLE file.

> 3)Isn't a compiler supposed to convert the C file to a binary ? But when  I do a vi a.out, I don't see any 0's and 1's. It's all  ```
@^@^D^@^@^
``` kind of thing.

Well, yes. Everything is made of 0 and 1. Even your text files and your source code. The difference is, when you open your source code file in vi, the 0s and 1s, put together in chunks of 8bits, make readable text. This is called ASCII code. A binary program is not made to be readable text, so the 0s and 1s put together in vi do not make any sense.

> 4)Once the C file is converted to a.out, WHAT IS IT THAT RUNS THE a.out  FILE ? THAT IS, WHEN I DO, ./a.out, WHAT IS HAPPENING ? IS IT THE ALU  THAT IS RUNNING THE CODE? OR IS THAT A VERY BOOKISH UMBRELLA WORD ?

I am sure you do not need your CAPS LOCK. Please avoid doing this.
To answer simply, your operating system (I suppose Ubuntu) loads your program and then it runs by itself.

---

### Post by IAMTubby on 2012-09-02
Thanks for the great explanation.

a.What does machine language look like ? Why is it in the form of ^@ on a text editor ?

b.It is wrong of me to hope to see 0's and 1's on vi, because vi is a TEXT editor right ? So, if i see a 0, it actually means 8 0's. Thanks for making me think in this direction.

c.How does the file that the ALU runs look like ? Is there a way to see that file, on say, a ASSEMBLY editor, (NOT a text editor - my latest understanding based on your previous post)

d.If I see the assembly output on an Assembly editor, will it be in the form of 0's and 1's ?

---

### Post by IAMTubby on 2012-09-02
> **Bachstelze said:**
> 1) The preprocessor processes your # directives, the compiler compiles your code to assembly, the assembler compiles it to machine language, and the linker adds all the necessary bits to make it a complete executable. If you want more details, get a book on compilers.

2) See above. You do use an assembler, among other things. The name a.out really is irrelevant, though, and the -o flag of gcc is the most widely used.

3) You are mistaken about the meaning of "binary". *Every file* in a computer is made of bits, including text files. vim displays text files, meaning it divides the file into chunks of 8 bits, and reads them as characters (for example 01000001 corresponds to the letter A). When we say a file is a "binary file", it doesn't mean that it is made of 0s and 1s (because all files are), but that it is not a text file, meaning its bits cannot be divided into chunks of 8 and interpreted as readable characters. When you see ^@ in vim, it means that the corresponding byte consists of eight 0s.

4) If you want to know every detail of what happens, again, get a book. The operating system is responsible for running your program, and of course it is the processor that runs the actual code. ALU means Arithmetic-Logic Unit, and it is the part of the processor that performs, you guessed it, arithmetic and logic operations, like addition, substraction and logical AND. (Generally the ALU works only on integers, floating-point operations are done on another part of the processor.)
Thanks for the great explanation.

a.What does machine language look like ? Why is it in the form of ^@ on a text editor ?

b.It is wrong of me to hope to see 0's and 1's on vi, because vi is a TEXT editor right ? So, if i see a 0, it actually means 8 0's. Thanks for making me think in this direction.

c.How does the file that the ALU runs look like ? Is there a way to see that file, on say, a ASSEMBLY editor, (NOT a text editor - my latest understanding based on your previous post)

d.If I see the assembly output on an Assembly editor, will it be in the form of 0's and 1's ?

---

### Post by IAMTubby on 2012-09-02
Thanks MistrPopo,
will avoid the caps lock in future. I'm sorry.

---

### Post by Bachstelze on 2012-09-02
> **IAMTubby said:**
> 
a.What does machine language look like ? Why is it in the form of ^@ on a text editor ?

b.It is wrong of me to hope to see 0's and 1's on vi, because vi is a TEXT editor right ? So, if i see a 0, it actually means 8 0's. Thanks for making me think in this direction.

I answered that in my previous message, I do not like repeating myself.

> c.How does the file that the ALU runs look like ? Is there a way to see that file, on say, a ASSEMBLY editor, (NOT a text editor - my latest understanding based on your previous post)

It is not useful to see the actual machine code, because it is not human-readable. It is better to look at something pretty close but readable, which is the sequence of assembly instructions that the machine code represents. You can do that by passing the -S flag to gcc:

```
gcc -S file.c
```

will create an assembly source file named file.s. If you have a compiled file, you can use objdump, but it is more complicated.

> d.If I see the assembly output on an Assembly editor, will it be in the form of 0's and 1's ?

The closest you can get to the 0s and 1s is to see a dump in hexadecimal, with e.g. hexdump.

---

### Post by CptPicard on 2012-09-02
> **IAMTubby said:**
> 
a.What does machine language look like ?

It's just a sequence of bits that the CPU knows how to interpret according to its instruction set. This depends on the CPU architecture.

> 
 Why is it in the form of ^@ on a text editor ?

Because of character encodings. The text editor has been programmed to display a certain set of bits by showing a certain character. What kind of set of bits means what kind of a displayed character is a matter of this agreed-upon character encoding.

> 
b.It is wrong of me to hope to see 0's and 1's on vi, because vi is a TEXT editor right ?

Yes. Vi assumes that the stuff in the file is to be interpreted as text, according to the character encoding in use.

> 
 So, if i see a 0, it actually means 8 0's.

This is the case only if the character encoding says that 8 bits where all bits are 0 should result in displaying a character "0". It is not so in any character encoding that I can think of, but it could certainly be agreed upon so.

> 
c.How does the file that the ALU runs look like ?

See the first response. In binary object files there is usually more stuff in there for the loader, linker and so on... and of course the ALU alone does not run anything really. It executes certain instructions in the machine code.

> 
 Is there a way to see that file, on say, a ASSEMBLY editor, (NOT a text editor - my latest understanding based on your previous post)

Well, you could take a look at hex editors for viewing and editing non-text-files. These are not "assembly editors"; assembly is some syntactic sugar for generating binary object files that contain instructions for the processor.

> 
d.If I see the assembly output on an Assembly editor, will it be in the form of 0's and 1's ?

Let's assume we're talking about "hex" editors here. Those generally display the file using the hexadecimal number system. It would be possible to view the file in terms of binary representation too. After all, the contents can be viewed as just numbers; it is irrelevant which base you use.

---

### Post by gardnan on 2012-09-02
> **IAMTubby said:**
> Thanks for the great explanation.

a.What does machine language look like ? Why is it in the form of ^@ on a text editor ?

b.It is wrong of me to hope to see 0's and 1's on vi, because vi is a TEXT editor right ? So, if i see a 0, it actually means 8 0's. Thanks for making me think in this direction.

c.How does the file that the ALU runs look like ? Is there a way to see that file, on say, a ASSEMBLY editor, (NOT a text editor - my latest understanding based on your previous post)

d.If I see the assembly output on an Assembly editor, will it be in the form of 0's and 1's ?

Machine language is just a series of bytes that to a human would look like nonsense, and would vary from processor to processor.

There is also no such thing really as an "Assembly editor". If you want to edit binary files, you can use a hex editor (a program that allows you to use hexadecimal to read and edit the bytes in a file). 

If you want to see the assembly output (what is between C code and machine language) then you can pass the -S option to the C compiler.

---

### Post by The Cog on 2012-09-02
> So, if i see a 0, it actually means 8 0's. Thanks for making me think in this direction.Actually, no. A text editor assumes that each byte represents a character, according to the ASCII code. ASCII assigns a value for each printable character, and the  value for the character '0' happens to be 48, which is 00110000 in binary. Not all values havea  corresponding character assigned, which is why a text editor has trouble with binary files that could contain any byte values at all.

> c.How does the file that the ALU runs look like ? Is there a way to see that file, on say, a ASSEMBLY editor, (NOT a text editor - my latest understanding based on your previous post)You can see the contents of any file with the program hd, which gives you a hex dump of the file contents. It shows the value of each byte in hex rather than binary, and also prints the ascii character of any bytes that happen to fall into the ascii printable range. This command will print the contents of a.out this way:
```
hd a.out
```

---

### Post by IAMTubby on 2012-09-02
Thanks to all of you. Would like to summarize what I've understood.
The entire compilation-running process consists of these steps:
---------------------------------------------------------------------------------------------

1)Preprocessor Directives 
It processes your #directives and expands your inline code, does macro expansions etc

2)Compiler
eg. gcc. It converts your .c file into assembly instructions. This can be viewed by doing a gcc -S <filename>.c

3)Assembler
The Assembler takes the assembly instructions/pnemonics and converts into machine level code/machine language. This is done by gcc -o <filename.c>. This machine code can be viewed in 2 ways
  a)vi a.out . But this looks weird because of character encodings. The text editor has been programmed to display a certain set of bits by showing a certain character. What kind of set of bits means what kind of a displayed character is a matter of this agreed-upon character encoding.(Quoting CptPicard)

  b)hexdump a.out

4)Linker
Linking is the process of combining various pieces of code and data together to form a single executable that can be loaded in memory

5)Loader
Loader loads this combined/linked machine code into the memory.

6)Execution - OS/ALU
Once the loading is complete, the OS, ALU take on the processing of this machine code.

PS
----
1)Sometimes people say compiler takes the c file and converts to machine code. That's because, they loosely refer to Compiler as (Compiler  + Assembler). Same reason why a.out is assembler output, because it's the assembler that gives the final machine code.

2)An OS/ALU cannot execute assembly code. It can only execute the machine code, given by the assembler.


Shall mark the thread as solved after a couple of replies/feedback.

Thanks.

---

### Post by Bachstelze on 2012-09-02
> **IAMTubby said:**
> 
This can be viewed by doing a gcc -S <filename>.c

gcc -S file.c does both 1 and 2.

> This is done by gcc **-o output_file** <filename.c>

Fixed that for you. Also, gcc file.c does 1, 2, 3 and 4. If you want to only do 1, 2 and 3, do gcc -c file.c, it will output file.o.

> 6)Execution - OS/ALU
Once the loading is complete, the OS, ALU take on the processing of this machine code.

Why do you insist on referring to the ALU? You were told several times that it is only one part of the CPU, and you should really say "CPU" here instead of "ALU".

> PS : Sometimes people say compiler takes the c file and converts to machine code. That's because, they loosely refer to Compiler as (Compiler  + Assembler)

I disagree with your use of "loosely".

---

### Post by IAMTubby on 2012-09-02
Bachstelze,
Thanks a lot for the review. Yes, shall not refere to ALU again. I understand that is only 1 part of the CPU. 

MistrPopo, CptPicard, gardnan, The Cog
Thanks a lot for your replies. Understood the process.

Marking the thread as solved.

---

### Post by IAMTubby on 2012-10-03
> **Bachstelze said:**
> 
Also, gcc file.c does 1, 2, 3 and 4.
Bachstelze, old thread I'm sorry, but wanted to clarify a couple of things.

1)So, does that mean that GCC is not just a compiler, but 
**Inline expander(any other name for it ?)  +  Compiler  +  Assembler  +  Linker ?**

2)My post - > Once the loading is complete, the OS, ALU take on the processing of this machine code.

Your post - > ALU(slighly edited) is only one part of the CPU, and you should really say "CPU" here instead of "ALU".
Can you give me an example of 1 more component of the CPU that does processing instructions ?

I'm sorry to dig up an old thread, but my understanding of things has improved slightly and wanted to clarify the remaining doubts.
Thanks :)

---

### Post by Bachstelze on 2012-10-03
> **IAMTubby said:**
> 
1)So, does that mean that GCC is not just a compiler, but 
**Inline expander(any other name for it ?)  +  Compiler  +  Assembler  +  Linker ?**

It depends how you define the term "compiler".

> Can you give me an example of 1 more component of the CPU that does processing instructions ?

It depends how you define the terms "processing" and "instructions".

On that topic as well, instead of asking random questions on a forum, grab a book and read it. It's the only way to get a decent understanding of it.

---

### Post by JKyleOKC on 2012-10-03
I agree that "compiler" probably has as many different meanings as there are people using the word, but I think I can answer your question in context. The gcc program is, after all the definitions are sliced and diced, a multi-level translator. It accepts as input a file of "source code" written in any of several programming languages, such as C or C++, and initially translates the instructions contained therein into a standard internal format that makes subsequent translation more accurate. It next translates them, again, into assembly language instructions for the specific CPU architecture desired (for example, Intel/AMD or PPC). Finally those assembly language instructions are translated into the binary bytes that form the actual program, and written to an output "object file."

Depending on the options chosen, that file can be the final output, or can be automatically linked with support libraries and assigned memory locations by a linker.

We usually have the options set up in a Makefile so that this whole process takes place behind the scenes, and we see only the final finished executable program as output.

As for CPU components, others include a Memory Management unit and usually a couple of internal memory caches. Since today's CPU chips contain literally millions of transistors only the CPU designers pay much attention to their internal arrangement.

Hope this helps! Knowing what actually goes on behind the scenes is a great help in troubleshooting, so learning all these arcane details is going to be quite helpful to you in the future. Keep at it!

---

### Post by IAMTubby on 2012-10-04
> **Bachstelze said:**
> It depends how you define the term "compiler".



It depends how you define the terms "processing" and "instructions".

On that topic as well, instead of asking random questions on a forum, grab a book and read it. It's the only way to get a decent understanding of it.
Thanks Bachstelze, I have got a good overview, thanks to the replies. Now, as you said, I think I should get hold of a good book to know the exact sequence.
Thanks a lot!

---

### Post by IAMTubby on 2012-10-04
> **JKyleOKC said:**
> 
Thanks JKyleOKC :).
The summary was very helpful and gave me a good idea of the things I should read in more details.

---

### Post by IAMTubby on 2012-12-01
> **JKyleOKC said:**
> 
Depending on the options chosen, that file can be the final output, or can be automatically linked with support libraries and assigned memory locations by a linker.

JKyleOKC, I have a question again. If I were to build a test.c program step-by-step, this is what I would do
a)gcc -E test.c - expands include files and macros 
b)gcc -S test.c - generates assembly instructions in test.s
c)gcc -c test.c - generates the object file which contains machine instructions, but IS NOT linked
d)gcc test.o -o test -  generates the final exe called test from test.o which is ready to run.

My questions are as follows
1)Is there a way to generate the object file from the .s file. (right now, by giving the -c option , I'm generating the object file from the .c file and not the .s file right ?
2)If I'm working with only a single .c file, and no headers/libraries etc, what is the need for linking , in that case, shouldn't gcc -c also give me an exe and not an object file. Just a thought.

> 
so learning all these arcane details is going to be quite helpful to you in the future. Keep at it!I would like to learn the concepts more systematically. Can you suggest me a book for the same ? Is a book on gcc the best way to go about it ? I tried reading Silberchatz and felt it didn't fit my requirement, although it's a great book.

Thanks a lot :)

---

### Post by trent.josephsen on 2012-12-01
Firstly, -E, -S and -c tell gcc where to stop, not which stages to do. When run on a plain source file, -c does preprocessing, compilation, and assembly; -S does preprocessing and compilation; -E just does preprocessing. If you wanted to do one stage of just assembly, you'd have to tell it to use the preprocessed, compiled .s file rather than using the .c file. Maybe this answers your first question?

As for the second one, linking is a necessary requirement. C programs don't run in a vaccuum; they depend on the C runtime library, which must be linked during this stage. Linking also includes stuff like generating the ELF headers and putting the entry point of the program at a specific location in the file so that it can eventually be executed. So, no, you can't skip linking.

---

### Post by JKyleOKC on 2012-12-01
> If I'm working with only a single .c file, and no headers/libraries etc,  what is the need for linking , in that case, shouldn't gcc -c also give  me an exe and not an object file. Just a thought.Since the C language itself contains no facilities for input or output, such a program might be capable of being tested via a debugger but would not be capable of actual use. At an absolute minimum, any C program must include the "stdio" header in order to use the "standard input/output" library that makes it possible to communicate with and control the program.

There's good reason for this; input and output are the specific areas where details vary widely from one system to the next. For instance, input may come from a network connection, from a touch screen, from a keyboard, or from many other sources, each of which requires its own specialized code. Output may go to a screen, a printer, or another device, and again the details will vary with the device. Even two different keyboards or printers will require different drivers. By putting all of this into a special i/o library, the compiler does not need to be aware of any of it; it can simply tell the library to read or write.

As for a book to study, the starting point ought to be "The C Programming Language" by Kernighan and Ritchie, which is the very first ever written. Dennis Ritchie was one of the co-inventors of the language, and Brian Kernighan was instrumental in its early development. While standardization efforts subsequently added polish to the language, its basic concepts have never changed, so the K&R volume remains the best introduction.

And GCC is much more than "just" a C compiler; it's a generalized language translator that can deal with other programming languages equally well.

---

### Post by trent.josephsen on 2012-12-01
As an aside, if you're interested in seeing the difference between the linked executable and the compiled object file, you can disassemble the executable with objdump (use the -d option) and compare the assembly instructions there with what you find in the .s file. You may find it educational. Or confusing. Either way really.

---

### Post by IAMTubby on 2012-12-03
> **trent.josephsen said:**
> Firstly, -E, -S and -c tell gcc where to stop, not which stages to do. When run on a plain source file, -c does preprocessing, compilation, and assembly; -S does preprocessing and compilation; -E just does preprocessing. If you wanted to do one stage of just assembly, you'd have to tell it to use the preprocessed, compiled .s file rather than using the .c file. Maybe this answers your first question?

As for the second one, linking is a necessary requirement. C programs don't run in a vaccuum; they depend on the C runtime library, which must be linked during this stage. Linking also includes stuff like generating the ELF headers and putting the entry point of the program at a specific location in the file so that it can eventually be executed. So, no, you can't skip linking.
Thanks a lot trent. Both answers were very helpful and answers my question.

> **trent.josephsen said:**
> As an aside, if you're interested in seeing the difference between the linked executable and the compiled object file, you can disassemble the executable with objdump (use the -d option) and compare the assembly instructions there with what you find in the .s file. You may find it educational. Or confusing. Either way really.
I shall try this out in some time.

---

### Post by IAMTubby on 2012-12-03
> **JKyleOKC said:**
> Since the C language itself contains no facilities for input or output, such a program might be capable of being tested via a debugger but would not be capable of actual use. At an absolute minimum, any C program must include the "stdio" header in order to use the "standard input/output" library that makes it possible to communicate with and control the program.
Thanks a lot JKyleOKC for the reply, but I need some further clarification on this. Please check the quote below.

> **IAMTubby said:**
> Thanks to all of you. Would like to summarize what I've understood.
The entire compilation-running process consists of these steps:
---------------------------------------------------------------------------------------------

1)Preprocessor Directives 
It processes your #directives and expands your inline code, does macro expansions etc

I had made an attempt to try and summarize the steps in the build process.
I thought that expanding the headers(say stdio.h) was done as the first step by Preprocessor directives and not by the linker. But reading your previous reply, I got the feeling that this part is done by the linker, and so we need the linking stage even for a single-file program. Sir, I'm sorry if I have assumed this part incorrectly.
Please advise.
Thanks.

---

### Post by Bachstelze on 2012-12-03
The header files contain only the definitions of the functions, not their code. Their code lies in the library files, and the library files are linked with your object files at link-time to create an executable. Even if you do not include any headers you still need linking, because your .c file does not contain everything that is needed to create an executable.

---

