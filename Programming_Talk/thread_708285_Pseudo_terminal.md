---
title: "Pseudo terminal"
date: 2008-02-26
forum: Programming Talk
---

### Post by aditi on 2008-02-26
i am trying to develop a program to create a pseudo terminal...but im not familiar with pseudo terminals so could sum one help me out with the program flow ??

---

### Post by LaRoza on 2008-02-26
Look into [xterm]("http://en.wikipedia.org/wiki/Xterm")

---

### Post by Zwack on 2008-02-26
If you're not familiar with pseudo terminals why do you need to create one?

It might make more sense for you to find out about pseudo terminals before trying to create them...

[http://en.wikipedia.org/wiki/Pseudo_terminal]("http://en.wikipedia.org/wiki/Pseudo_terminal")
[http://www.gnu.org/software/libtool/manual/libc/Pseudo_002dTerminal-Pairs.html]("http://www.gnu.org/software/libtool/manual/libc/Pseudo_002dTerminal-Pairs.html")

Z.

---

### Post by Glaxed on 2008-02-26
vte?

---

### Post by Zwack on 2008-02-26
I guess we need to know what the actual question is...

I assumed that we were talking opening a pseudo terminal master/slave pair here, but the advice seems to be about fake terminals...

which is it?

Z.

---

### Post by aditi on 2008-03-01
we've read about pseudo terminals..we are trying to simulate something very similar to ssh which is why we need to use pseudo terminals. We've tried creating the master-slave pair using forkpty. 
Here we are assuming the child process is the slave but we cant see the output of the child process anywhere. ( for starters we've jus put a printf here ) .Because we could not see the output any where, we redirected STDOUT within the child to a separate file. Here we got the output in the file.  

So we are not able to figure out how to get the ouput of the slave terminal and how to establish a connection between the master and slave. 
So can anyone tell me if im on the right track and what exactly should be the program flow ??

---

### Post by baxterdog on 2008-03-01
but ssh is already implemented in our terminal. just type ssh .... whatever.

---

### Post by aditi on 2008-03-01
yes, SSH uses our terminal, but it also uses pseudo terminals if you look into the SSH code... it's needed as commands need to be executed on a remote machine.

---

### Post by Mr. C. on 2008-03-01
End of term project?

How about you show the outline of what you have already.  You're asking a lot of others before you've earned your chits.

---

### Post by supirman on 2008-03-01
Get a copy of "Advanced Programming in the UNIX Environment".  Chapter 19 covers pseudo-terminals in detail.

[http://www.amazon.com/Programming-Environment-Addison-Wesley-Professional-Computing/dp/0201563177](http://www.amazon.com/Programming-Environment-Addison-Wesley-Professional-Computing/dp/0201563177)

---

