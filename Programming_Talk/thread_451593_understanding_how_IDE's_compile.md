---
title: "understanding how IDE's compile"
date: 2007-05-22
forum: Programming Talk
---

### Post by theorem_hunter on 2007-05-22
i am looking for a sequence diagram that can explain to me how source code is taken from a editor & then all the "magic" that happens when the compile button is pressed, like how it passes through the file system, then to the linker, & then finally to the compiler.

when i googled, i got to a bunch of adverts trying to sell me a UML tool, under google image source i just found sequence diagram examples, but none explaining how IDE's or compilers work...

thanks

---

### Post by LaRoza on 2007-05-22
I do not know the exact mechanism, but I can describe how you turn a text editor, Crimson Editor, into an IDE.

You basically link the editor to the compiler, linker, debugger, and executor and it send the info just like you would with a command line compiler. 

If you installed an IDE, like DevCPP, you could find g++,gcc,gdb in its folders. 

The IDE just provides an interface to all the real programs.

Note: DevCPP is what I use in Windows, I use the command line in linux. Crimson Editor is what I use for many coding tasks for the Web, but I also use it as an Java IDE, so I can compile and execute with out using a command line.

---

### Post by theorem_hunter on 2007-05-22
ok thanks, well i am making a diagram & i will post it here when i am done...

---

### Post by theorem_hunter on 2007-05-28
well here is the image i made. i got 8/10 for it as an assignment so i must be sort of right!

---

### Post by Game_Ender on 2007-05-28
The linker does not syntax check.  It simpler than your diagram and you really don't need one.  It just a few steps:
 1. You save your source file on disk
 2. The IDE invokes the compiler and gives it the path to your source file(s)
 3. The preprocessors processes all those lines that begin with "#"
 4. The compiler acts on the preprocessed code and produces object file(s) on disk
 5. The linker is invoked and given the path to all object files and libraries you wish to make into a program.
 6. The linker writes the finished executable to the file system.
 7. The IDE runs this executable file and shows you its output.

On any step 2-6 the preprocessor, compiler and linker could exit early with an error exit code.  If that is the case your IDE parses the text output which describes the error and shows it to you.  If the error is in you code they often let you double click errors and which takes you to the offending spot in your code.

---

### Post by theorem_hunter on 2007-05-28
thanks, i agree, your steps are much simpiler to under stand

---

### Post by slavik on 2007-05-28
simple C compilation (C++ might be a bit more complex because of templates):
Source code -> CPP (C Pre-Processor) -> CC (C Compiler) -> Linker -> ready to run program. :)

---

