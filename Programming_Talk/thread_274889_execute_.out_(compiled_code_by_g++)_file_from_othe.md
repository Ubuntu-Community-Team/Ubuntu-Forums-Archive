---
title: "execute .out (compiled code by g++) file from other directory"
date: 2006-10-10
forum: Programming Talk
---

### Post by ShendZ on 2006-10-10
hi coders,
i make a java servlet which can compile code submitted online.
then, the compiled code will be tested and the output will be recorded.

my problem is, when the servlet compiles the code from its directory (let's say /usr/local/tomcat/webapps/online_compiler/testedcode/a.cpp), a.out file will be placed in my home folder.
to execute the file, then, i should issue ./a.out

my question is, how could i run .out file from other directory?
currently, my servlet can do the work but it will generate .out files in my home folder.
i want the out files are put in my project folder which is in /usr/local/tomcat/webapps/online_compiler/testedcode/

i know i can use g++ /usr/local/tomcat/webapps/online_compiler/a.cpp -o /usr/local/tomcat/webapps/online_compiler/a.out but if i issue ./a.out it wont be able to find my out file.
my servlet code's workingspace is in my home folder and i dont know if i can change that.

hopefully u guys can understand my explaination. basically, i want to know how to run .out file from other directory
./a.out can only be issued in the same directory where a.out is

thx in advance

-shendy

---

### Post by meng on 2006-10-10
./ just indicates the directory you are currently in, so of course it's not going to work if you happen to be in another directory.
What about:
/usr/local/tomcat/webapps/online_compiler/a.out
does that work?

---

### Post by ShendZ on 2006-10-11
Yes! Thank you. I tried to do "a.out" in Desktop and I assumed /path/a.out won't work.

Thank you very much.

---

