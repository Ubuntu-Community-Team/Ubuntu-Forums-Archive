---
title: "which editor to use for C programming in ubunto"
date: 2009-02-07
forum: Programming Talk
---

### Post by xardox69@gmail.com on 2009-02-07
hi guys,i am studying operating systems course and my teacher has given an assignment to compile two C codes.But i really dont have any idea which editor to use for compiling c programs.I have done coding in C++ in Visual Basic in Windows.I will be very greatfull of you people if you help me out on this one.And please by using layman language because i dont understand lunix terminologies.

---

### Post by null.byte on 2009-02-07
Hello. 

You cannot code C++ in Visual Basic, they are two different programming languages. By the way, I would recommend **vim**. If you don't have time to learn it, **nano** is also a good solution.

You can compile the code after writing it in the editor by using g++.

---

### Post by xardox69@gmail.com on 2009-02-07
> **null.byte said:**
> Hello. 

You cannot code C++ in Visual Basic, they are two different programming languages. By the way, I would recommend **vim**. If you don't have time to learn it, **nano** is also a good solution.

You can compile the code after writing it in the editor by using g++.
oh sorry it was visual c++ not vb.ok thanks for the advise and ill bug you back in case of some problem and hell yeah i have to submit it on 14th Feb.thanks

---

### Post by dwhitney67 on 2009-02-07
1)  Place your two C files in a folder (or home directory).

2)  Use gedit to edit these files (if needed).

3)  Use the command line to compile/link your program:

a)  Launch a gnome-terminal

b)  If necessary, change directory to the folder where your files reside
```

cd folder

```

c)  Compile/link programs
```

gcc file1.c file2.c -o myexec

```

d)  If necessary, fix compile and/or link errors (go back to Step 2.)

e)  Run the program
```

./myexec

```

---

### Post by nvteighen on 2009-02-07
If it's just quick work, GNOME's default editor Gedit will be enough. Look at Applications->Accesories->Text Editor. It's a very nice tool usually underestimated (activate its plugins!).

---

### Post by xardox69@gmail.com on 2009-02-09
hey guys i ma not getting you people.where is the root directory?

---

### Post by hessiess on 2009-02-09
> **xardox69@gmail.com said:**
> hey guys i ma not getting you people.where is the root directory?

cd /

---

### Post by xardox69@gmail.com on 2009-02-09
hey i have written the c code on the text file and saved it at desktop.now what should i do??now how i camplie it?

---

### Post by xardox69@gmail.com on 2009-02-09
now in the terminal window i have written this command:
gcc my1.c            (my1.c is my c file and i have written it on text pad and then saved it as my.c)
the terminal is giving me error "No such file or directory"
????????????????????

---

### Post by xardox69@gmail.com on 2009-02-09
i have checked the path of the file.it is /home/usman/Desktop
in the terminal window i have written cd/home/usman/desktop
but it is giving me error no such file or directory
what should i do?????anyone?

---

### Post by PmDematagoda on 2009-02-09
First of all I suggest that you get used to using the terminal and such ways of navigating it, reading up on the man pages using:-
```
man *name-of-command*
``` is a great way of doing so. The commands you would need are:-
```
cd - to change directory
ls - to list the contents in a directory.
mv - to move a file or folder.
cp - to copy a file or folder.
gcc - to compile the files.
```

Since you saved the files on the desktop, you need to move to the Desktop folder with:-
```
cd ~/Desktop
```
and then compile it with:-
```
gcc my1.c -o my1
```

The above code can be broken up as such:-
```
gcc - just the name of the compiler executable.
my1.c - the name of the source file to compile.
-o - to specify an output file name.
my1 - the name of the output file(can be anything you want.)
```

And about writing C code, I always found the Emacs editor to be very useful:).

---

### Post by slavik on 2009-02-09
Please read the stickied thread at the top of this forum, they contain good information and there is a HOWTO for compiling C or C++ code.

---

### Post by xardox69@gmail.com on 2009-02-09
now i have two programs written and have their resulting executable object files.now how do i compare the size  of the two executable object files.(using 1s and -1 command?)

---

### Post by slavik on 2009-02-09
man ls

---

### Post by PmDematagoda on 2009-02-09
> **slavik said:**
> Please read the stickied thread at the top of this forum, they contain good information and there is a HOWTO for compiling C or C++ code.

+1.

About the size comparison, you could use the -s option of ls, which you could have found with a brief reading of the ls man page.

---

### Post by xardox69@gmail.com on 2009-02-09
now i have to write a program which determines whether a given input object file is a Relocatable Object File
or an Executable Object File By reading the type field in the ELF header.......
please tell me firstly..... is  ElF header in the executable file?..

---

### Post by ZuLuuuuuu on 2009-02-09
> **null.byte said:**
> Hello. 

You cannot code C++ in Visual Basic, they are two different programming languages. By the way, I would recommend **vim**. If you don't have time to learn it, **nano** is also a good solution.

You can compile the code after writing it in the editor by using g++.

Recommending Vim to somebody who doesn't even know how Ubuntu and Linux are spelled or doesn't even know the difference between C++ and Visual Basic?

---

### Post by Krupski on 2009-02-09
> **xardox69@gmail.com said:**
> hi guys,i am studying operating systems course and my teacher has given an assignment to compile two C codes.But i really dont have any idea which editor to use for compiling c programs.I have done coding in C++ in Visual Basic in Windows.I will be very greatfull of you people if you help me out on this one.And please by using layman language because i dont understand lunix terminologies.

I use nano in Linux as the text editor for everything (C source, BASH scripts, etc..)

For C programs, I usually write them in Windows using the LCC-Win32 development system because it has a nice IDE and debugger. Then, when the code works I remove the carriage returns ( :) ) and copy the source to Linux, then recompile with GCC.

I'm sure this is not the optimal way to do it, but it's the way I do it... FWIW.

-- Roger

---

### Post by Krupski on 2009-02-09
> **ZuLuuuuuu said:**
> Recommending Vim to somebody who doesn't even know how Ubuntu and Linux are spelled or doesn't even know the difference between C++ and Visual Basic?

Try as I may, I cannot figure out VI or VIM.

It's supposedly so great, yet I can't even write a text file that says "hello" without screwing up 20 times!

Nano is (in my opinion) a lot better.

---

### Post by Krupski on 2009-02-09
> **xardox69@gmail.com said:**
> hey guys i ma not getting you people.where is the root directory?

Ha ha! funny!

Sorry... the root directory is your main, top directory.

Think of it, literally, as a tree.

The roots (or maybe the trunk) are the root directory, the branches are subdirectories like "/dev" and "/etc" and "/proc".

The smaller branches on the big main branches are more directories off the main directories.

Lastly, the leaves are the individual files which reside on their branches (in their directories).

But, EVERYTHING emanates, or comes from the main trunk... the root.

Think of it another way... a filing cabinet. The cabinet itself is the "root". Inside the root are many folders called "directories". In each folder there can be sheets of paper (documents) which are the individual files.

There could be folders inside other folders (i.e. subdirectories) such as a folder called "Bills, 2008" and then 12 folders inside it marked "January", "February", etc...

You can move files (sheets of paper) between folders, you can add or delete (throw out) files. You can even move folders around to different places, but they all must remain inside the filing cabinet (the root).

Picturing it this way, does it make sense?

-- Roger

---

### Post by xardox69@gmail.com on 2009-02-09
i ma trying to download nano and it always says wrong architecture
[http://packages.debian.org/etch/powerpc/nano/download](http://packages.debian.org/etch/powerpc/nano/download)
even when i select power pc

---

### Post by Sorivenul on 2009-02-09
> **xardox69@gmail.com said:**
> i ma trying to download nano and it always says wrong architecture
[http://packages.debian.org/etch/powerpc/nano/download](http://packages.debian.org/etch/powerpc/nano/download)
even when i select power pc

nano should be installed by default. 

In a terminal just type:
```
nano
```

The commands are listed at the bottom of the editor.

---

### Post by xardox69@gmail.com on 2009-02-09
ok.got nano.now i need to compile a file at desktop.what to do?

---

### Post by xardox69@gmail.com on 2009-02-09
i am not able to open an executable file of the c code file .i need to know the format of the object file

---

### Post by Gordon Bennett on 2009-02-09
By the way, if all you want to do is just program and run your code, instead of mucking about for hours with the command-line, there are three excellent IDE's, all easily installable from Ubuntu's 'Add/Remove...' menu:

[COLOR="Blue"]Anjuta[/COLOR] - nice and fast native IDE and compiler.
[COLOR="Blue"]Eclipse[/COLOR] - more extensive Java-based compiler (Ganymede version from their website provides a pre-made C/C++ version).
[COLOR="Blue"]CodeBlocks[/COLOR] - More focused on C++ code.

With most of these a simple 'New C project' from the menu will generate the template files for you, then 'Build' and 'Run' - they generate proper Makefiles too so you can easily look at how they work in respect to your build.

---

### Post by Sorivenul on 2009-02-09
As has been said, the Stickies in this Forum offer great advice and tutorials on compiling C/C++ code. 

```
cd /home/yourusernamehere/Desktop
```
```
gcc nameofyourcfilehere.c -o nameofprogramhere
```

You cannot compile code directly from nano, as far as I know. If you want an editor that will help compile your code, Geany or Anjuta are two common IDEs.

---

### Post by Caduceus on 2009-02-09
Here's what I do (Assuming I have a C file called "Hello"):

gcc -o hello /home/sam/Desktop/Hello.c

Compiles fine like that, then it's just:

/home/sam/hello

To run it

---

