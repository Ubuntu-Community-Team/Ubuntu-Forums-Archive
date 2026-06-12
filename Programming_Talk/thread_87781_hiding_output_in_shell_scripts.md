---
title: "hiding output in shell scripts"
date: 2005-11-08
forum: Programming Talk
---

### Post by Brando569 on 2005-11-08
hey im writing a shell script to install apps that i use alot im new to writing them and is there any way that i can hide the output of everything (something equivalent to @echo off in batch programming) and only see stuff in the terminal either when i use echo or when theres an error? and one other thing, is there a command for apt-get or another program of the like that will install the dependencies of a deb package automatically?

---

### Post by darth_vector on 2005-11-09
you can redirect stdout to /dev/null by adding

1>/dev/null

at the end of each line of your script that will produce output.

you can redirect errors the same way by adding

2>/dev/null

---

### Post by nagilum on 2005-11-09
Most commands do have an option to turn off normal output to the console, like '-q' or something like that. Check the manpages of the commands you use.

I would not recommend using the '2>/dev/null' as darth_vector described since you will miss all errors. If you do not want any output but still detect errors redirecting the errors to a logfile with '2>error.log' is a better way. In addition you might want to use the bash builtin command 'set -e' to assure the script terminates immediately when one of the commands in it fails. See 'man bash' for more details.

---

### Post by darth_vector on 2005-11-09
[QUOTE=nagilum]I would not recommend using the '2>/dev/null' as darth_vector described since you will miss all errors. If you do not want any output but still detect errors redirecting the errors to a logfile with '2>error.log' is a better way.[/QUOTE]

good point!

---

### Post by Brando569 on 2005-11-10
thanks for the help guys i found the switches, its not as as clean as a batch file could be but oh well, linux is better then windows...

> is there a command for apt-get or another program of the like that will install the dependencies of a deb package automatically?

just to clarify what i meant, is there a way for apt-get to install dependencies for a package that is local? 
ex. issuing the cmd for installing superkaramba w/out issuing the comands before it for the installation of the dependencies

---

