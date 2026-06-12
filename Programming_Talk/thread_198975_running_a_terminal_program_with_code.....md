---
title: "running a terminal program with code...."
date: 2006-06-18
forum: Programming Talk
---

### Post by orlox on 2006-06-18
I've been thinking in a project lately, for wich I would need to execute a terminal program, give input to it, and receive the output back....

Does anyone know how to do this??? I was pretending to use Java for this, but if anyone knows how to make this on C or something like that, It would also be usefull...

---

### Post by kewldude606 on 2006-06-18
In shell this is how you would do it:
varname=`command to do, as you would on the command line` # note the backticks.

In PHP, there are quite a few methods:
passthru will display the output (unless you use an output buffer).
exec returns a string with the output of the last line of output.
[More here]("http://us3.php.net/manual/en/ref.exec.php")

C++ is usually very similiar to PHP, so there is probably some include that you can use to get the functionality described above.

---

### Post by orlox on 2006-06-18
Thanx! I was pretending to create a web app for wich I needed to do this, so the info on php is quite usefull...I'l see where I can get with that

---

### Post by bieber on 2006-06-18
I'm not sure what kewldude is talking about.  PHP is nothing like C++, aside from trifling syntactical similarities.

Anywho, if it's a webapp, you'll probably be interested in the php shell_exec() command, which takes as an argument a string containing a command to execute, executes it on the server, and returns the results from stdout.

For instance, if you want to display a list of programs in /usr/bin on the server, you could run
[code]
<?php
     echo( shell_exec( "ls /usr/bin" ) );
?>

---

### Post by ynef on 2006-06-19
If you're asking what I think you are -- running a program from a C program, giving it parameters and saving the output -- then you need to get familiar with the calls to fork() and exec(), as well as dup(). If you have access to Advanced Programming in the Unix Environment by Stevens and Rago[1], this would be a good time to crack it open. Apparently you can download the source code of all examples in the book -- do that, and you should be able to learn a ton.

[1] [http://www.kohala.com/start/apue.html](http://www.kohala.com/start/apue.html)

---

### Post by yaaarrrgg on 2006-06-19
to do this in java 

[http://java.sun.com/developer/codesamples/examplets/java.lang/89.html](http://java.sun.com/developer/codesamples/examplets/java.lang/89.html)
[http://java.sun.com/developer/codesamples/examplets/java.lang/90.html](http://java.sun.com/developer/codesamples/examplets/java.lang/90.html)
[http://java.sun.com/developer/codesamples/examplets/java.lang/91.html](http://java.sun.com/developer/codesamples/examplets/java.lang/91.html)

A word of caution though... if this is an app that will live on the web?   Calling a terminal program like this could open up some big security holes.

Things to consider for example: is there any check on what is posted (and the buffer sizes)?  Or suppose someone passed a variable like " /usr/bin; rm -rf ~" to a command like "ls".  etc...  I would be careful with terminal programs, since they're extremely hard to make secure.

---

