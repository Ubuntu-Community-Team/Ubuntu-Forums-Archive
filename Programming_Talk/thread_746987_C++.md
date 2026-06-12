---
title: "C++"
date: 2008-04-06
forum: Programming Talk
---

### Post by petersonjacob on 2008-04-06
i am programming using C++ and am having trouble compiling my script, i made it executable and when i use #!/usr/bin/g++ i get a mean error, what should be the first line of my C++ script, to initialize an interpreter?

---

### Post by BaffledMollusc on 2008-04-06
> **petersonjacob said:**
> i am programming using C++ and am having trouble compiling my script, i made it executable and when i use #!/usr/bin/g++ i get a mean error, what should be the first line of my C++ script, to initialize an interpreter?

I'm a bit confused. Is the type of script you're talking about a bash script, i.e. a shell script? If so, it uses an interpreted language not a compiled one. 

You can compile your C++ source code with g++, and then run the resulting executable from the command line, a script, or file browser or whatever. 

Can you say exactly what you're trying to do?

---

### Post by LaRoza on 2008-04-06
See the sticky in the programming talk (thread moved)

You can't use g++ that way. The sticky will explain it.

C++ isn't normally interpreted and g++ isn't an interpreter anyway.

---

### Post by hessiess on 2008-04-06
```
main : main.cpp
	g++ main.cpp -o main
		
clean :
	rm -rf main
```

put this into a file called 'makefile' in the same directory as the program. 
change 'main.cpp' to the naime of your program.
open a terminal.
cd to directory.
type 'make'
type ./'name of program'

---

