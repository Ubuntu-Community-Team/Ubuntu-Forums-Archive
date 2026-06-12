---
title: "Shell script- find exec [HELP]"
date: 2011-01-28
forum: Programming Talk
---

### Post by achuthpnr on 2011-01-28
Hello

I am trying to write a shell script to run a c program which resides in all sub-folders in a path
the c program accepts two arguments
the code i made is something like this after searching

find . -type f -name 'program' -exec {} xxx.txt 0.05 \;

but it is not working
also i want to copy a specific file to be copied to sub-folders which contains a specific file 

Googling didn't give me any noticeable results and I am a beginner.

---

### Post by conradin on 2011-01-28
What is the program?
(So I can set this up and see where its going wrong)

---

### Post by Arndt on 2011-01-28
> **achuthpnr said:**
> Hello

I am trying to write a shell script to run a c program which resides in all sub-folders in a path
the c program accepts two arguments
the code i made is something like this after searching

find . -type f -name 'program' -exec {} xxx.txt 0.05 \;

but it is not working
also i want to copy a specific file to be copied to sub-folders which contains a specific file 

Googling didn't give me any noticeable results and I am a beginner.

When you say it's "not working", what happens?

Having one copy of a program in every subdirectory seems to me to be very odd. Why is it that way?

---

### Post by achuthpnr on 2011-01-28
it is not showing any error message. but there is no result file created by that program

it is a small c program to read and convert one data file xxx.txt using some parameter which is 0.05

there are so many folders and sub-folders where i need to run it. so i copied it to all the folders. after it is executed, i just delete it from all the folders

---

### Post by Vaphell on 2011-01-28
may be the issue of relative path
when you give . as a dir all results will be relative to that, eg
./something
./something/else
maybe exec part assumes incorrect directory and because of that ./ in program's path fails?
try
```
find **"$PWD"** -type f -name 'program' -exec **"{}"** xxx.txt 0.05 \;
```

$pwd will expand to full path and " " protects against spaces in directory names

---

### Post by achuthpnr on 2011-01-31
> **Vaphell said:**
> may be the issue of relative path
when you give . as a dir all results will be relative to that, eg
./something
./something/else
maybe exec part assumes incorrect directory and because of that ./ in program's path fails?
try
```
find **"$PWD"** -type f -name 'program' -exec **"{}"** xxx.txt 0.05 \;
```

$pwd will expand to full path and " " protects against spaces in directory names
One step forward. I can see an error message by the program - xxx.txt not found

xxx.txt file is in the same folder of the program and this is same for many folders/ sub-folders

---

### Post by Arndt on 2011-01-31
> **achuthpnr said:**
> One step forward. I can see an error message by the program - xxx.txt not found

xxx.txt file is in the same folder of the program and this is same for many folders/ sub-folders

The man page for 'find' says this for -exec:

```
The specified
              command is run once for each matched file.  The command is  exe&#8208;
              cuted  in  the starting directory.   There are unavoidable secu&#8208;
              rity problems surrounding use of the -exec  action;  you  should
              use the -execdir option instead.
```

It seems it is -execdir that you want. I think that option does not exist in all implementations of 'find'.

---

### Post by Vaphell on 2011-01-31
try this (find all directories, execute DIR/program DIR/xxx.txt 0.05)
```
find $PWD -type d -exec "{}"/program "{}"/xxx.txt 0.05 \;
```
or using -execdir
```
find . -type f -iname program -execdir ./program xxx.txt 0.05 \;
```

---

### Post by achuthpnr on 2011-02-01
> **Vaphell said:**
> try this (find all directories, execute DIR/program DIR/xxx.txt 0.05)
```
find $PWD -type d -exec "{}"/program "{}"/xxx.txt 0.05 \;
```or using -execdir
```
find . -type f -iname program -execdir ./program xxx.txt 0.05 \;
```
-execdir did the trick. 
-exec did run but I was getting the output file in PWD other than where it is supposed to be - as written in the man page

Thanks

---

