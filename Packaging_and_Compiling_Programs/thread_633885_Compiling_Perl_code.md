---
title: "Compiling Perl code"
date: 2007-12-07
forum: Packaging and Compiling Programs
---

### Post by roberto22085 on 2007-12-07
I have recently been teaching myself Perl. So far, I think it's absolutely amazing. I just have one problem. I don't know how to compile the source file using the command line in Ubuntu (7.10). I also know C++, and I compile my code with the command *g++ filename.cpp -o filename*. I am looking for a similar command for my Perl code.

So far the only way I have been able to compile my code is by clicking the 'compile' button in Geany. But I would also like to know the command using the command line...if there is one.

One other question. After compiling code (C++ or Perl) you obviously cannot edit the code again in  the compiled file. I know you keep the source file in case you need to change something later, but my question is, is it actually necessary to compile the code? What are the pros/cons to compiling vs. just having #!/usr/bin/perl at the top of the code and making it executable??

Thanks in advance!

---

### Post by roberto22085 on 2007-12-07
I think I may have actually answered my own question. In Geany at the bottom, there is a compile tab. If you click that tab it shows this command *perl -MO=Bytecode,-H,-o"list.pl"c "list.pl"*

I tried it on one other file and it worked (I changed the filename obviously). But I looked at the help page for the Perl program and it says that -M is something for modules and doesn't give any information on the O. Nothing on the Perl help file says anything about compiling.

I did read that Perl was an interpreted language, like Python. But now my problem is, why would Geany allow a user to "compile" Perl code? If it is truly interpreted as Python is, it shouldn't be able to be compiled right??? As far as I know Python code cannot be compiled.

---

### Post by meatpan on 2007-12-07
> **roberto22085 said:**
> 
I did read that Perl was an interpreted language, like Python. But now my problem is, why would Geany allow a user to "compile" Perl code? If it is truly interpreted as Python is, it shouldn't be able to be compiled right??? As far as I know Python code cannot be compiled.

Yes and no.  Both python and perl expose techniques for bundling elements of the interpreter and your code in a single cohesive unit, so you essentially get a standalone 'executable' program.  There is a bit of perl documentation that will help you understand.  Run 'perldoc perlcompile' for more info.

BTW, If you are missing the perldoc program, you might need to install it: 'sudo apt-get install perl-doc'.

---

