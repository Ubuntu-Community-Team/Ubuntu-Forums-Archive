---
title: "I am unable to compile and my java programs"
date: 2008-09-27
forum: Programming Talk
---

### Post by faraday005 on 2008-09-27
i just started using ubuntu 8.04 and i have installed netbeans. the problem is that anytime i try to compile my java programs with **javac** from the terminal i keep seeing this

fara@fara-laptop:~$ javac Welcome.java
javac: file not found: Welcome.java
Usage: javac <options> <source files>
use -help for a list of possible options

can anybody help me to go around this. thanx

---

### Post by Kadrus on 2008-09-27
You have to place the file in your home directory if I am not mistaken.
Where is it located now?

---

### Post by faraday005 on 2008-09-27
the program is located on my desktop

---

### Post by Kadrus on 2008-09-27
well in terminal you can do:
```
cd ~/Desktop
```
and compile the program using javac.
It should work.

---

### Post by faraday005 on 2008-09-27
thanx anyway Kadrus, i have just been able to compile and run the program. i change directory to Desktop before compiling and it worked. thank you!

---

### Post by Kadrus on 2008-09-27
Mark the thread as solved so people can know that there is no more problem.

---

