---
title: "C compilation"
date: 2011-10-05
forum: Programming Talk
---

### Post by orrymr on 2011-10-05
Hi 
My question is about C compilation; once I compile a C program (cc -o test test.c) I end up, as expected with an executable called test. If I right click and check the properties I'm told that I have the following:
executable (application/x-executable).

My question then is this; does this compiled file contain the ones and zeros that make up machine code? Or is it some sort of intermediate? How does my machine know that this is an executable, and not an image, for example?

Thanks in advance

---

### Post by ofnuts on 2011-10-05
> **orrymr said:**
> Hi 
My question is about C compilation; once I compile a C program (cc -o test test.c) I end up, as expected with an executable called test. If I right click and check the properties I'm told that I have the following:
executable (application/x-executable).

My question then is this; does this compiled file contain the ones and zeros that make up machine code? Or is it some sort of intermediate? How does my machine know that this is an executable, and not an image, for example?

Thanks in advance1) yes (*),  2) because it has the execute bit set, and contains 0x7F,"ELF" as the first bytes.

(*) Sort of, the code is relocatable, ie, the bits that are addresses aren't final and will modified at load time. See [http://en.wikipedia.org/wiki/Executable_and_Linkable_Format](http://en.wikipedia.org/wiki/Executable_and_Linkable_Format) for the full story.

---

### Post by orrymr on 2011-10-05
So the header informs the cpu what type of file it's dealing with? Because it sees 0x7F as the first few bytes it know that what follows must be executable machine code?

I don't really understand the ELF file layout that follows though (program header, etc). Any further reading you could suggest that explains it?

---

### Post by ofnuts on 2011-10-05
> **orrymr said:**
> So the header informs the cpu what type of file it's dealing with? Because it sees 0x7F as the first few bytes it know that what follows must be executable machine code?Not the CPU, but the progam loader. And if it were to see "#!" it knows the path to an interpreter comes next, hence the "#!/bin/sh" at the beginning of shell scripts.


> **orrymr said:**
> I don't really understand the ELF file layout that follows though (program header, etc). Any further reading you could suggest that explains it?See here for the basics: [http://en.wikipedia.org/wiki/Link_editor](http://en.wikipedia.org/wiki/Link_editor) and follow the links in the "see also" section.

---

### Post by lensman3 on 2011-10-05
From a command line:
"ld test"
to see the libraries that the executable needs to run.

type  in "nm test" 
to see what are modules are called and the called routines.  This works best on .o files.

type in "objdump -l -d test" 
to dump the object code back to human readable stuff.  This works best on .o files.  objdump has a lot of options.  Compile the routine with debug on.  Compile "cc -o test.obj test.c"

Look at the "strip" program to strip the debug info out of a program.  Then run nm, ld, and objdump on the files.

Have fun.

---

### Post by Arndt on 2011-10-06
> **lensman3 said:**
> From a command line:
"ld test"
to see the libraries that the executable needs to run.


You may mean 'ldd' here.

---

