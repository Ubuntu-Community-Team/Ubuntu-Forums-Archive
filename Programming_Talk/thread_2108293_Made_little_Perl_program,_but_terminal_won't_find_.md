---
title: "Made little Perl program, but terminal won't find it?"
date: 2013-01-24
forum: Programming Talk
---

### Post by Likwid Flux on 2013-01-24
So I'm just starting out with perl (literally just got the book for learning it yesterday) and one of the exercises, was making this program in text editor in ubuntu:
#!/usr/bin/perl
print "Hello, world!\n";

then I went and saved it and it said I have to identify it as an executionable file or something like that. Here is the full paragraph:

You may also need to do something so that your system knows it’s an executable program (that is, a command). What you’ll do depends upon your system; maybe you
won’t have to do anything more than save the program in a certain place. (Your current
directory will generally be fine.) On Unix systems, you mark a program as being executable using the chmod command, perhaps like this:
$ chmod a+x my_program



I entered  that phrase: chmod a+x my_program 
((the file was called my program, I named it that))

and terminal gave me this:  chmod: cannot access 'my_program' : no such file or directory

and I tried renaming the program with a space and with the underscore, and placing it in different places like my documents, but it just keeps saying no such file or directory. Please help!!!!

---

### Post by coldraven on 2013-01-24
Try this
```
./my_program
```
The ./ (dot and forward slash) means that the script you are trying to run is in the current directory. Otherwise I think you would have to give the whole path to it.```
/home/joe-bloggs/my_program
```

---

### Post by micahpage on 2013-01-24
by default the terminal is in directory /home/<username> . It appears that your file you created is not in that directory. If you put the file in ~/Documents, then the command would be
```
$ chmod a+x ~/Documents/my_program
```which is giving the full path to the file

Or 
```
cd Docuements
``````
chmod a+x my_program
```> I entered  that phrase: chmod a+x my_program That is not a "phrase" it is a command.
where:
[CMD] [MODE] [PATH TO FILE]
where path to file could simply be the filename, "if" you are in the directory that the file resides, otherwise the full path must be used to the file

If your file has an ext, that also will need to be added to the command as well

---

### Post by Vaphell on 2013-01-24
if the program is in the directory not listed in $PATH (*echo $PATH* to see the list), you have to give path explicitly, eg ***./**program* or ***~/**program* or ***/home/me/some_dir/**program* or whatever.
in case of hand-made tools you can create *bin* directory inside your home. In ubuntu the terminal is configured by default to check for existence of that directory and adds it to the $PATH variable.

---

### Post by Likwid Flux on 2013-01-24
Alright, thanks a lot everyone! That REALLY helped me!

---

