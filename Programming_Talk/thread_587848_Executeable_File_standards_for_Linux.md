---
title: "Executeable File standards for Linux"
date: 2007-10-23
forum: Programming Talk
---

### Post by shoaibnawaz on 2007-10-23
I am new to Linux. I am ambiguous about execution files for Linux. As "exe" is one of executable standard in Windows. I came to know Executable and Linking Format (ELF) is standard executable format in Unix and Linux. In addition to ELF what are the other executable formats used in Linux.

---

### Post by Shin_Gouki2501 on 2007-10-23
depends on language
soem times there are o or so files ( object , shared object).
U can also use Java ;)

---

### Post by wolfbone on 2007-10-23
$ objdump -i

---

### Post by captaink on 2007-10-23
I'm rather new too, but as I've seen untill now, there is no standard for executables. If you check the properties of a file, you will see an attribute saying "this file is executable". This means that ANY file can be executed. This makes easy use of scripts.
Also, if you check out an executable file you execute, ex. firefox, downloaded from mozilla site, you actually execute a text file with a reference to firefox-bin, that is the bytecode of the main program. 
Also, keep in mind that a linux system does not pay attention to the extentions, the extention is used for your own ease of use.

That's how linux does the job. No restrictions! Just pure computing.
Keep learning...

---

### Post by shoaibnawaz on 2007-10-23
Actually I am searching for any standard. Just now I came to know about another thing that is ABI (Applicaiton Binary Interface), an application binary interface describes the low-level interface between an application program and the operating system, between an application and its libraries, or between component parts of the application. So there are as many executable standards and they might be following ABI standards of Linux.

I want classified list of them either they are script based or binary based.

---

### Post by CptPicard on 2007-10-23
a.out was the old format, these days executable binaries are ELF. ABI is a more general term that has to do with binary compatibility.

Mind you, if you are coming from Windows, you do need to remember what above posters said... if you just make any file executable, the shell can try to run it, usually through some interpreter that is declared at the top of your file, which is usually some script.

---

### Post by mjwood0 on 2007-10-23
I think that there is a bit of confusion here with regards to binary executables, or simply running a script file.

As mentioned, any file can be made executable.  This is a bit confusing though.  If you made a text file executable, you are telling the OS (Linux Kernel) that you wish to run what's in the file as if you were typing it at the command line.  This works fine for scripts as there is a line at the top such as:
```
#!/bin/bash
```

This line tells the kernel what interpreter you wish to use for the file.  If this line isn't present, you'll execute the file, line by line, in the current shell.  

A binary executable is completely different.  From my understanding, the GCC Suite will compile things to an ELF binary.  If debugging is enabled, you'll get a DWARF output.  The ELF binary is executed not by running every line on the command prompt, but by loading the program in memory and branching execution to the start address of the program.

The one thing you will notice compared to windows is that there is no extension required for an executable file such as .exe.

---

### Post by LaRoza on 2007-10-23
To the OP:

To make a file executable: ```
chmod +x <fileName>
```

To make a script, open with its interpreter: [code]#! /usr/bin/<interpreterName>[/code[

The "#!" is has meaning to the shell when it is the first character, the path after it should point to an interpreter. If you mark a file as executable, you can run a script as you would another program.

This differs from Windows, where the file  extension is used to determine what interpreter to use, and whether the file is executable.

---

### Post by pmasiar on 2007-10-23
bash, python, perl, ruby, php - it all can be executable. 

In Linux, you have freedom to choose the (free) language most adequate for the task in hand. So it depends what is your task.

---

### Post by slavik on 2007-10-23
but what does it mean for a directory to be executable?

NOTE: I know the answer. :)

---

### Post by Ramses de Norre on 2007-10-23
> **slavik said:**
> but what does it mean for a directory to be executable?

NOTE: I know the answer. :)

That it's browsable.

---

### Post by CptPicard on 2007-10-23
> **Ramses de Norre said:**
> That it's browsable.

... sort of... I'd say it can be a part of path. It's "navigable". You can't neccessarily "browse" it which in my book would mean you can +read it as well.. :)

---

### Post by DMills on 2007-10-23
> **mjwood0 said:**
> 
A binary executable is completely different.  From my understanding, the GCC Suite will compile things to an ELF binary.  If debugging is enabled, you'll get a DWARF output.  The ELF binary is executed not by running every line on the command prompt, but by loading the program in memory and branching execution to the start address of the program.


Actually, there is an 'interpreter' for ELF files just as there is for shell, perl, awk, python and whatever. 

If you look at the .interp section of an ELF file (use something like [php]objdump -s /bin/cat | less[/php]) you will see something like (this on a 64 bit box, 32 bit is slightly different):
[php]
/bin/cat:     file format elf64-x86-64

Contents of section .interp:
<Hex> /lib64/ld-linux-
<Hex> x86-64.so.2.    [/php]This is a symbolic link to /lib64/ld-2.5.so  which is the filename and path of the dynamic loader responsible for resolving the dynamically linked elf file dependencies and starting the program it has built in memory (The dynamic loader is of course itself statically linked!) . 

Thus the ELF compiled executable startup is not meaningfully different from the startup of a script except in the detail of calling the dynamic loader instead of the shell interpreter. 

Incidentally, you can create shared libs that have the interesting property of being directly executable! Try for example running /lib/libc.so.6 in a terminal. Thus a shared library can be (but normally is not) an executable in its own right. 

HTH.

Regards, Dan.

---

### Post by slavik on 2007-10-24
> **Ramses de Norre said:**
> That it's browsable.
nope.

if you have a directory "blah" that has execute but not read flags set, you can't do an ls on it, you can do cd to it, but ls won't work (no permission). What you can do is get to a file in blah if you know the name and have proper permission to that! Very useful in web programming since you can disallow indexes this way (when you go to a dir but the index file is non-existant)

---

### Post by shoaibnawaz on 2007-10-24
> **LaRoza said:**
> To the OP:

To make a file executable: ```
chmod +x <fileName>
```

To make a script, open with its interpreter: [code]#! /usr/bin/<interpreterName>[/code[

The "#!" is has meaning to the shell when it is the first character, the path after it should point to an interpreter. If you mark a file as executable, you can run a script as you would another program.

This differs from Windows, where the file  extension is used to determine what interpreter to use, and whether the file is executable.

what can be used in addition to +x

I means, I write an HTML script and save it as filename.html, and whenever I try to open it by double clicking, text editor try to open it instead of Browser. How can I adjust my HTML script file as executable by default browser installed in Linux.

---

