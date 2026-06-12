---
title: "Problem with program compiled with fpc"
date: 2008-11-25
forum: Programming Talk
---

### Post by serpantman on 2008-11-25
Hi, im starting to learn free pascal and i wrote my first prog with it and compiled it. After i tried to execute it with
 sh firstfpc

and this error returned

firstfpc: 1: Syntax error: "(" unexpected

NOTE that this error comes when trying to execute the program, not compile it. Whats wrong/how do i fix it??

---

### Post by namegame on 2008-11-25
It would be very helpful if you could post your code as well. 

It's kind of hard to determine what the problem may be with only the compiler error.

---

### Post by serpantman on 2008-11-25
It's not a compiler error because it compiles without error???
I get that error when executing.

Anyways here's the code, its the first one i wrote just to see if my compiler even works. So if anyone makes fun of me im gonna punch them in the */%^#@%!!!

program firstprog;

const

	one = 45;
	two = 7;
	three = 68;
	four = 2;
	five =  34;

var

	sum : integer;
	average : real;

begin

	sum := one+two+three+four+five;
	average := sum / 5;
	
	write('sum is ',sum,' and average is ',average);
end.

---

### Post by wmcbrine on 2008-11-25
If it's a compiled binary, you shouldn't be trying to execute it via a shell. Try:

./firstfpc

(assuming that you actually have a binary called "firstfpc").

P.S. I can confirm that, trying to execute a randomly-selected ELF binary via sh, I get exactly that error:

$ sh ztelnet
ztelnet: 1: Syntax error: "(" unexpected

So, that's your problem.

---

### Post by serpantman on 2008-11-25
Thanks!!! Solved.

Edit: How do i mark it solved? Sorry.

---

