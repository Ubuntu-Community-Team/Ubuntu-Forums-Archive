---
title: "starting int main(int argc,char *argv[])............"
date: 2009-03-30
forum: Programming Talk
---

### Post by abhilashm86 on 2009-03-30
in linux os,how exactly os knows when c++ object file is kept on main memory?
is that os triggers a function called "c startup()" routine, then this
cstartup() invokes main(int argc,char *argv[]).Then where this main function returns?
i just got to know about it but confused, how actually it happens?

---

### Post by Tony Flury on 2009-03-30
What happens is that Linux has a standard format for all executable files. The file will include things such as indicators of the entry point of the programm.

The C compiler and linker will build one of these standard executable files, and will include the indicators to point into the file where the main() function has been translated.

When you try to run the executable, the linux OS will load the executable file, and look for the entry point indicators, and execute the relevant part of the executable file. So long as we are talking about a fully compiled programm, the OS has no knowledge of which actual language was used to create the program.
With interpreted or partial compiled programms (for instance Python, Java, perl, Shell Scrips, and many others), then the OS will execute a Interpreter or VM first (which will be a fully compiled application).

To my knowledge all Linux full executables (whether they be written in C or another compiled language) all deal with the command line in the same way, i.e. all the arguments are placed on the start before the executable's entry point is called.

---

### Post by abhilashm86 on 2009-03-30
yes sure, what you told was true, when an executable is placed, 
everything gets converted to machine level program format, use of registers it just executes.
do linux OS has any function like "cstartup" function to know where main() function is, this is highlight of my question..........

---

### Post by monkeyking on 2009-03-30
It should depend on the underlaying platform.

Most unixes today use the elf format.
[http://en.wikipedia.org/wiki/Executable_and_Linkable_Format](http://en.wikipedia.org/wiki/Executable_and_Linkable_Format)

You should read up on this if you are interested in this very low level or highlevel stuff. Depending on your viewpoint :)


Most programmers, don't care about this aspect of software development.
And I don't think you would need to know it, unless your are doing system programming.

---

### Post by abhilashm86 on 2009-03-31
ya even i was not intrested untill in class, my teacher highlighted about this, i googled but it din't really show what i wanted:) now it's fine.......

---

