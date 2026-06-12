---
title: "tty"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by cybo on 2008-04-24
Question about tty command.
I'm slowly but surely learning about UNIX and Linux. I have read something about terminals but didn't quite get it. 

I typed tty command (at work) and got the following response:
/dev/pst/151

Can someone explain what does it mean?

Thnx

---

### Post by Diabolis on 2008-04-24
You can learn about commands reading their help messages or man pages. You can also google almost everything that pops out in a terminal, from commands to complete error messages.
```
tty --help
man tty
```

---

### Post by otrojake on 2008-04-24
According to the man page it "prints the file name of the terminal connected to standard input."  As far as I can tell is it just gives the terminal number.  If I open up two terminals the first one gives me /dev/pts/0 and the second one gives me /dev/pts/1.

---

### Post by Stevko on 2008-04-24
If you open one terminal and write tty it gives you file for that terminal. If you write anything to that file from anywhere, it will be put to that terminal.
Try:
open two terminal windows and find their filenames using tty in both (in my case one is /dev/pts/1 and second /dev/pts/2 (I will refer to them as terminal 1 and terminal 2).
In terminal 2 write ```
echo Hello world! > /dev/pts/1
```
It will be displayed in terminal 1.
You can try writing ```
cat /dev/pts/1
``` in terminal 2. It should show everything you write in terminal 1 in terminal 2 (however, it will not do that immediatelly - you first have to finish line in terminal 1 (either by pressing enter or ctrl+c) - I am not sure about exact cause, but I assume it has to do something with how bash handles the input from terminal).

---

### Post by cybo on 2008-04-24
Thank you everyone.
Diabolis, I'm still trying to get used to man pages format. It is a little hard to read.

---

