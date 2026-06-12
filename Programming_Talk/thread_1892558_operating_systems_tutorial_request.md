---
title: "operating systems tutorial request"
date: 2011-12-08
forum: Programming Talk
---

### Post by Lilykos on 2011-12-08
hello everyone i am an undergraduate it student and i am in a difficult position...can anyone help me? what i am looking for is a tutorial or website or something like that that is about operating systems programming, stuff like fork(), shared memory, semaphores,processes etc. what i am looking for is a down to earth, practical and simple approach for me to learn and mainly use immediately (as the deadline is approaching...sigh). for example something that has answers on questions like how to define a semaphore, how to use fork, how is semop and the other functions properly used etc....can anyone help me???
thanks in advance to all the community here!

//sorry if this is the wrong thread, i looked all the others and it seemed the most appropriate

---

### Post by CoffeeRain on 2011-12-08
If you are looking at Unix, you might be looking for a bash tutorial. If this is right, I could give you a link to a pretty good one.

---

### Post by karlson on 2011-12-08
> **CoffeeRain said:**
> If you are looking at Unix, you might be looking for a bash tutorial. If this is right, I could give you a link to a pretty good one.

By the questions asked it's not bash or csh or tcsh or any other shell.

---

### Post by karlson on 2011-12-08
> **Lilykos said:**
> hello everyone i am an undergraduate it student and i am in a difficult position...can anyone help me? what i am looking for is a tutorial or website or something like that that is about operating systems programming, stuff like fork(), shared memory, semaphores,processes etc. what i am looking for is a down to earth, practical and simple approach for me to learn and mainly use immediately (as the deadline is approaching...sigh). for example something that has answers on questions like how to define a semaphore, how to use fork, how is semop and the other functions properly used etc....can anyone help me???
thanks in advance to all the community here!

//sorry if this is the wrong thread, i looked all the others and it seemed the most appropriate

What you need is basically this:

[http://www.amazon.com/Programming-Environment-Addison-Wesley-Professional-Computing/dp/0321525949/ref=sr_1_1?ie=UTF8&qid=1323356257&sr=8-1](http://www.amazon.com/Programming-Environment-Addison-Wesley-Professional-Computing/dp/0321525949/ref=sr_1_1?ie=UTF8&qid=1323356257&sr=8-1)

If you can't afford to buy one or you should be able to get one in the library.

---

### Post by 11jmb on 2011-12-08
[http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-828-operating-system-engineering-fall-2006/](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-828-operating-system-engineering-fall-2006/)

MIT has a lot of online CS courses that are publicly available.

---

### Post by Lilykos on 2011-12-08
i am not really sure what are all these you say, i am pretty new to linux programming...i am looking for a tutorial about the way the commands and functions work in a standard linux environment, writing in c and compiling with gcc...is this information enough? to let ou understand i am provided with this book [here]("http://www.amazon.com/Modern-Operating-Systems-Andrew-Tanenbaum/dp/0136006639") but it is not practical or simple enough....

---

### Post by CoffeeRain on 2011-12-08
Do you want to know how the file system and stuff like that works? Languages like C and python are the same, except for the c include files. Bash is the language that interacts with the file system and computer. Learning bash, or even the basics, could help you get your way around the computer. MIT open courseware is good.

---

### Post by Lilykos on 2011-12-08
no, what i want is some simple explanations rgarding how to use the common functions and commands...

to be more specific:i have to use fork().i know that the general way of usage is something like that:
  (&#945;)  x = fork(); 
  (&#946;)  if (x == 0) 
  (&#947;)    < ...... > 
  (&#948;)  else 
  (&#949;)    < ...... > 
but i dont have an active example, a source code that i can compile and run and actually learn how to use it....that's why i am asking for a practical tutorial...

---

### Post by 11jmb on 2011-12-08
Well the glibc manual is not a bad place to start. It is a bit lengthy, but check out ch. 25, it will give you a decent intro to linux programming including syscalls, arguments and environment variables

[http://www.gnu.org/s/libc/manual/html_mono/libc.html#Program-Basics](http://www.gnu.org/s/libc/manual/html_mono/libc.html#Program-Basics)

---

### Post by Lilykos on 2011-12-08
thank you!!i believe something like that will help a lot! thanks a lot to everyone who answered!

---

