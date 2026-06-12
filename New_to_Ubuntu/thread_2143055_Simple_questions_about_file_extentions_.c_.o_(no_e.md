---
title: "Simple questions about file extentions .c .o (no extention) and .ps"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by BudworthTDog on 2013-05-07
I've been using Ubuntu since 2009 and while I have dug into a fair amount of "under the hood" type of things I've decided to really get into the heart and soul of it all. Basically instead of learning things as I need them I'm reading through books and taking notes starting with all the basics and branching out deeper and deeper and learning things whither I think I need them or not. This way I can run into skills and ideas that I never knew existed. Point being is this question doesn't lead to something that needs a solution, rather it's just something I'm curious about in case it pops up later

In this book I'm reading through (Practical Guide to Ubuntu Linux by Marki Sobell) it list some basic file extensions and what they mean. I'm familiar with almost all of them but wanted some clarification. I know the first 3 obtain to C programming which I wont study up on later but it wouldnt hurt to have a loose grasp on what they are for when I see them floating around in files. 
 
**_example table_**
compute.c  =  a C programming source file
compute.o = The object code file for compute.c
compute  =  the executable file for compute

so my understanding/what I don't understand is
.c is where all the code is written for the program
.o I don't understand what "object code" is
the no extension file is what you use when you run the program. The thing I'm confused about is how does the contents of that file differ from the .c file   How I interpret it at this point is that the executable file reads all the source code from the .c file. In which case why not just make the .c file and executable file and do away with the file with no extension 

and lastly one example of a common extension the list 
.ps  =  A PostScript file
What is a post script file?

---

### Post by Impavidus on 2013-05-07
In general file extensions don't have much meaning in Linux, but some programs use them and they can be a useful convention.

When compiling a c program several steps happen. First the preprocessor, assembler and compiler run to turn the source code into machine code. Where the source code says: "Call function func with arguments "blah", 6 and the variable x" (in other words, func("blah", 6, x)) this first step generates a code which says: "Store the address of the static string in this programs data sector with content "blah" on the stack, then put the integer 6 on the stack, then read the contents of the address belonging to variable x and put it on the stack, save the current position in the code on the stack and tranfer execution of the program to the point referenced by the function func." These instructions are stored in the .o file.

Conversion of the .o file to the file without extension is done by the linker. The linker replaces statements like "transfer execution of the program to the point referenced by function func" with "transfer execution of the program to position 0x1234" or, if the function is defined in an external library, with "When loading this program to memory, also load file libxyz.so.1.2" and "transfer execution to the code in file libxyx.so.1.2 at position 0x1234". Files of type .so are shared object files, more or less the same as the .o object files, but used as shared libraries. The .1.2 is a version number.

This all means that the executable is a translation of the .c file, made by the compiler. The compiler reads the .c file, the executable runs on the computer.

Making the .c file executable instead of compiling the program is what happens in scripting languages, like python, perl etc. This is more convenient (except when you want the source to remain hidden), but slower. Therefore high-performance stuff is not scripted but written in compiled languages.

PostScript files are one of my favorites. PS is a page description format designed by Adobe in the 1980s. It was mostly replaced by its simplification PDF, which was designed to run on cheap hardware instead of the professional printers from the 1980s. I remember someone telling me he knew someone who had written a chess program in PostScript to run on the university's printers, because back then they had more computing power than the students' servers. Since then PDF has been given some new features not present in PS.

PostScript is a Turing complete scripting language, so you can do basically anything in it. Even writing documents that appear differently every time they are printed is possible, using the random function. I once wrote a labyrinth generator in PostScript, so that everyone recieving a copy of the student association's magazine got a different one. Usually the files are computer generated, bloated and unreadable by humans, but I sometimes make hand-crafted PS code, giving very compact and pecise vector graphics using things like loops, procedures and recursion, not available in PDF. PostScript is also very common as PS Type 1 fonts, but they tend to use the .pfb suffix.

---

