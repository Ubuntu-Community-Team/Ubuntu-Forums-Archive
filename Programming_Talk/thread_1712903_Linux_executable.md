---
title: "Linux executable"
date: 2011-03-23
forum: Programming Talk
---

### Post by ki4jgt on 2011-03-23
Back when I was first learning about Linux someone compared a few file types to Windows exe files. I know .bin was one of them, but I searching for the other one. I keep thinking .ls I know I'm relating ls to the terminal LOL. I know any file can be made executable, but I'm looking for the ones which are automatically associated with execution. I'm also wanting to know if I can convert from .py to what ever file type it is.

---

### Post by JupiterV2 on 2011-03-23
Linux binaries don't normally have any extension. Changing a file's extension doesn't change its data. A python script is just that, a script. Removing, or changing a .py extension to anything else (.exe in Windows) does not make it an executable. In order to convert a python script to binary you need a program called py2exe (or something like that, I've never used it). 

Linux uses flags to determine what can be executed/run. If what you are wanting is just to have someone type in the name of your script to run it, just make it executable with 'chmod'. If you don't want to users to see the .py extension, just rename the script without the .py extension or create a symlink to it with 'ln' (i.e. ~/bin/myscript -> ~/bin/myscript.py).

---

### Post by ki4jgt on 2011-03-23
> **JupiterV2 said:**
> Linux binaries don't normally have any extension. Changing a file's extension doesn't change its data. A python script is just that, a script. Removing, or changing a .py extension to anything else (.exe in Windows) does not make it an executable. In order to convert a python script to binary you need a program called py2exe (or something like that, I've never used it). 

Linux uses flags to determine what can be executed/run. If what you are wanting is just to have someone type in the name of your script to run it, just make it executable with 'chmod'. If you don't want to users to see the .py extension, just rename the script without the .py extension or create a symlink to it with 'ln' (i.e. ~/bin/myscript -> ~/bin/myscript.py).

O no I realize I can't just rename LOL. . . I'm wanting to convert to the .whatever that I was taught was linux's default executable file type.

I just referenced another program I had installed on my netbook and the extension is: sh

I wanted to convert from .py to sh, if it's possible?

---

### Post by Vaphell on 2011-03-23
linux doesn't really care about file names - .sh is just a convention and you can do without (just as many system tools being shell scripts in reality do already). You can try to execute any file (executable bit set) as long as the system knows how.
If you put in the very first line of your script **#!/bin/bash**, the system will use bash to execute it, if you put **#!/usr/bin/env python** in your code, it will try default python interpreter.

if you want to have the same functionality in different format, you'd need to write in bash everything that python program did. Why bother?

---

### Post by Simian Man on 2011-03-23
Linux only executable file format is Elf.  Elf files typically have no extension.  Then there are numerous kinds of scripts that are executed by some interpreter such as sh, python etc.  These typically have extensions that specify the type.

Whether a file is "executable" is a whole nother issue.  Elf files are set to executable, but so are many scripts.  In this case the scripts are just are through an interpreter.

There is no way, and no reason, to "convert" a script to an executable format.  Just set the executable bit with chmod and use it like any other.

---

