---
title: "Need help with a program"
date: 2007-05-06
forum: Programming Talk
---

### Post by computerjunkie on 2007-05-06
Hey, I was just wondering if anyone could help me get started on a perl program I want to write. I'm a novice programmer, at best and have don't know how invoke terminal commands in a perl script.

Basically what I want to do is make a perl program that outputs "what directory would you like to encrypt?" The user would then input a directory (aka /home/name/mystuff/workdocuments) and the program would cd to that directory and use the dir command and convert all of the filenames with a specific ending (i.e .txt or .doc or .pls etc) to variables and save them in RAM. (I think in C++ thats "infile>>variablename;") or something close to that. It would then use the bcrypt program to encrypt the files. it would run the bcrypt program, so it would have to output the request for the input of a password and then the verification of the password for the encrypted files. 

The use of bcrypt is incredibly simple. ie: name@domain:~$bcrypt file1.doc, file2.doc, file3.doc   

I dont know how to invoke normal commands in a perl program. If this question is unacceptable for this forum, or in the wrong place please move it to the appropriate place or delete it. thanks for any help with this.

---

### Post by Ramses de Norre on 2007-05-07
Are you looking for something like this: ```
#!/bin/perl

@args = ("ls","-la");
system(@args);

```

---

### Post by computerjunkie on 2007-05-09
I just dont know how to reference shell commands in perl and I'm unsure in perl what type of variable (string, etc) woudl be appropriate for saving names of files into memory.

---

### Post by Ramses de Norre on 2007-05-10
Well I showed you how to use commands, make an array containing the command and any additional parameters (@args=("sudo","vi","/etc/fstab") ), then call system with the array as argument (system(@args) ).

[Here](http://www.comp.leeds.ac.uk/Perl/filehandling.html) is some info about file handling, the whole tutorial is pretty good so you might want to read the other pages too.

---

