---
title: "Need to protect keyboard"
date: 2010-05-05
forum: Programming Talk
---

### Post by RLN37 on 2010-05-05
I've written a process-control program in gforth which works very nicely, except for one practical problem:  The controlling computer will be operated by rather non-technical people.  If they hit an errant key or key combination (eg, Ctrl-C, Ctrl-Y, Ctrl-\, etc), they could lose control of the process by accidentally closing the program, or shifting the program to the background, etc.

So the question is how to allow only certain keys to cause any action, until one specific key combination that I (the programmer) can specify as the one to close the program and return control to the Ubuntu o/s.  Until that closing key combination occurs I want to be sure the only actions possible are the ones provided for in my process-control program.

Any hints about how to bring this about would be greatly appreciated.  And, yes, you guessed it - I'm not a very experienced Linux programmer.

---

### Post by myrtle1908 on 2010-05-06
I don't know much about Forth but in most languages you deal with this via signals.  Maybe start here [http://rosettacode.org/wiki/Handle_a_signal](http://rosettacode.org/wiki/Handle_a_signal) ... there is a Forth example for trapping SIGINT (often created by the user typing ctrl-C).

Good Luck!

---

### Post by soltanis on 2010-05-06
Set those signals to ignore. No idea how to do that in Forth. But bravo for writing this in Forth.

---

