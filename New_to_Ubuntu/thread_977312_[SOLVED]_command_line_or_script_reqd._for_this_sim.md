---
title: "[SOLVED] command line or script reqd. for this simple operation.."
date: 2008-11-10
forum: New to Ubuntu
---

### Post by sazan on 2008-11-10
hi.. 
i am runnin a simple command line to store any command's output into a file..

eg. ls > temp.txt will store o/p of ls in temp.txt.. 

but therez a catch that when i use commands like 'lvs','webinfo -u' ,etc. where there might be some error generated that error is not displayed in the text file.. 

so can anyone tell me a method or a script (like perl script) to help me out so that i can hav everythin in my text file for the command entered.. 

thanks in advance

---

### Post by prshah on 2008-11-10
> **sazan said:**
> 

eg. ls > temp.txt will store o/p of ls in temp.txt.. 

where there might be some error generated that error is not displayed in the text file.. 


You can redirect error output to a file with "2>"; eg ```
ls > temp.txt 2> error.txt
``` will send output to temp.txt and errors to errors.txt.

---

### Post by sazan on 2008-11-10
isn't there anyone with a solution ???

---

### Post by sazan on 2008-11-10
> **prshah said:**
> You can redirect error output to a file with "2>"; eg ```
ls > temp.txt 2> error.txt
``` will send output to temp.txt and errors to errors.txt.

hey thanks... it worked !!!:guitar::guitar::guitar:

---

