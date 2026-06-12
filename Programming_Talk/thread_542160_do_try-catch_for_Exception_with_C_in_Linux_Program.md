---
title: "do try-catch for Exception with C in Linux Programming"
date: 2007-09-03
forum: Programming Talk
---

### Post by saeedeh1363 on 2007-09-03
I need a program that it can  do try-catch for Exception(example Devide by zero) With assert Function.this program should write in Linux with C programming(Example in IDE eclipse in Linux)

do you any has source this code???



Thanks very much

---

### Post by ryno519 on 2007-09-03
Not a C programmer, so don't take my words for face value. I don't think there is native exception handling standard C.

---

### Post by nanotube on 2007-09-03
> **ryno519 said:**
> Not a C programmer, so don't take my words for face value. I don't think there is native exception handling standard C.

well... python is written in C :)
you can get the source from [http://www.python.org](http://www.python.org)

---

### Post by aks44 on 2007-09-03
C does not have exceptions. You may want to look for C++.

However, things like divide-by-zero (or any other CPU interrupt for instance) are handled in Linux using signals.

The catch being: you can't safely throw a C++ exception from a signal handler, unless you add tons of boiler plate code (boolean flags + tests after each and every relevant instruction). This slows down the code to a point that you really don't want to convert signals to exceptions.

---

### Post by aks44 on 2007-09-03
> **nanotube said:**
> well... python is written in C :)
you can get the source from [http://www.python.org](http://www.python.org)

Just because Python has exceptions doesn't mean that the C language supports exceptions natively. Just like C++, Python's exceptions are an additional layer over raw C code (kind of a "library" if you want to put it that way).

---

### Post by nanotube on 2007-09-03
> **aks44 said:**
> Just because Python has exceptions doesn't mean that the C language supports exceptions natively.

of course not, and i wasn't implying otherwise. 
he was looking for "a program" "written in C" that can "do exceptions", and since python is essentially "a program", and since it is "written in C", and since it can "do exceptions", i was suggesting it as an example. 

i mean, it was mostly a joke :), but literally following the semantics of his question (which was none too clear to begin with), it fits what he was asking for.

---

### Post by WitchCraft on 2010-11-15
You can't really do it in C.
The best you can do is this here:
[http://www.on-time.com/ddj0011.htm](http://www.on-time.com/ddj0011.htm)


But you can do it with C++:
```

try 
{
	std::fstream fin;
	fin.exceptions( std::fstream::failbit );
	fin.open("nosuchfile.ext", std::fstream::in);
	// And not
	//fin.open(f, std::ios::in);
}
catch (std::exception& e)
{
	std::cout << "Exception: " << e.what();
}

```

PS: Yea, I know, I just revived a 3 years old thread.

---

### Post by LightningRose on 2010-11-15
Try-Catch is just another way to check error returns.

In 'C' this is called, "checking the function's return code for error".

Exceptions in modern OOP languages are not exceptions in the classic sense. 

Exceptions in the classic sense are not simple errors returned by functions, they are programming errors that generate 'signals' such as array subscripts out of bounds (SEGFAULT), and divide by zero errors (SIGFPE).

You can catch these signals in your code, but there's not much you can do but exit gracefully from your program.

[http://linux.die.net/man/2/signal](http://linux.die.net/man/2/signal)
[http://en.wikipedia.org/wiki/SIGFPE](http://en.wikipedia.org/wiki/SIGFPE)
[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)

You may be able to Google some 'C' tutorials for signal handling, but for an introduction to Linux systems programming, I recommend the book "The Linux Programmer's Toolbox", by John Fusco.

---

### Post by worksofcraft on 2010-11-15
> **WitchCraft said:**
> 

PS: Yea, I know, I just revived a 3 years old thread.

Well what you wanna go do that for ?

---

### Post by saulgoode on 2010-11-15
> **WitchCraft said:**
> You can't really do it in C.
The best you can do is this here:
[http://www.on-time.com/ddj0011.htm](http://www.on-time.com/ddj0011.htm)

Another (better?) way to do it in C is to write a signal handler for SIGFPE ('man sigaction').

---

