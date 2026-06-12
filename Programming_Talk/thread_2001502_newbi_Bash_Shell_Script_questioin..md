---
title: "newbi Bash Shell Script questioin."
date: 2012-06-11
forum: Programming Talk
---

### Post by beterhans on 2012-06-11
Hello I'm learn how to write bash script buy read this PDF

Advanced Bash-Scripting Guide by Mendel Cooper

at the if test section
you can use 

if [[ ??? ]]

or (( .... ))

to test something

I can do it at command line

but can't do it in script? return like this:

test.sh: 8: 1: not found
Exit status of "(( 1 ))" is 127.

seacrhed google but google can't search " (( )) " or " [[ ]] "

---

### Post by ofnuts on 2012-06-11
> **beterhans said:**
> Hello I'm learn how to write bash script buy read this PDF

Advanced Bash-Scripting Guide by Mendel Cooper

at the if test section
you can use 

if [[ ??? ]]

or (( .... ))

to test something

I can do it at command line

but can't do it in script? return like this:

test.sh: 8: 1: not found
Exit status of "(( 1 ))" is 127.

seacrhed google but google can't search " (( )) " or " [[ ]] "
Testing uses the square brackets. Post the code you use here. 

Make sure you are using bash, your script file should start by "#! /bin/bash" (other things may elicit other interpreters with a different syntax)

---

### Post by codemaniac on 2012-06-11
"primaries" that make up the TEST-COMMAND are put between "[]" or "[[]]" built-in while doing conditional checking in shell .

A suggested above please post the exact code and make sure you are pointing to bash to execute the shell script , because some bash 4.0 conventions are not supported in older versions of bash and bourne shell .

---

### Post by sisco311 on 2012-06-11
I don't recommend the ABS guide for beginners. Check out the one from my signature. 

sh is the POSIX or Bourne shell, NOT bash. ;)

See: [http://mywiki.wooledge.org/BashGuide/Practices](http://mywiki.wooledge.org/BashGuide/Practices)

---

