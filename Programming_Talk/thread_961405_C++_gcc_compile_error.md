---
title: "C++ gcc compile error"
date: 2008-10-28
forum: Programming Talk
---

### Post by mulder_edu on 2008-10-28
I'm working on a programming project in MinGW.  I keep getting the error "error: 'time' does not name a type".  I'm trying to overload the minus operator in order to subtract the seconds variable of one time object from the seconds of another.

```
//class definition
class time
{
private:
	int seconds;
	bool IsAM;
public:
	time(int, int, string);
	time operator-(time);
	bool operator<(const time&);
	int getHours();
	int getMinutes();
	bool getIsAM();
};
//overloaded operator
time time::operator-(time t)
{
	time temp;
	temp.seconds = seconds - t.seconds;
	return temp;
}
```

It seems to be erroring on the return value of 'time'.  If anyone has an idea of what is going on, that would be great.  Thanks.

---

### Post by Zugzwang on 2008-10-28
In general, class names should start with an uppercase letter. Otherwise you might get conflicts.

In this case, your problem is that there's already a function named "time" and the compiler takes that instead of your class at that point.

Either rename your class or put it into a namespace and explicitly refer to that.

---

### Post by namegame on 2008-10-28
Your subject line also suggests that you are compiling C++ source code with gcc. I would recommend using g++ instead.

---

### Post by nvteighen on 2008-10-28
> **namegame said:**
> Your subject line also suggests that you are compiling C++ source code with gcc. I would recommend using g++ instead.
Aren't both exactly the same? (That gcc calls g++ for C++?)

---

### Post by snova on 2008-10-28
Technically they are all no more than frontends that call the appropriate sequence of Compiler -> Assembler -> Linker, leaving some out if necessary.

The C compiler is actually located at "/usr/lib/gcc/PLATFORM/VERSION/cc1" and the C++ compiler is cc1plus.

g++ links in additional C++ specific libraries, but it's otherwise the same as gcc.

---

### Post by namegame on 2008-10-28
> **snova said:**
> 
g++ links in additional C++ specific libraries, but it's otherwise the same as gcc.

This is the reason I suggested it. The Computer Science Professors just recommend it just to avoid any possible issues with not having the libraries.

---

### Post by arkangel on 2008-10-28
the structure of your code is correct in principle 

the problem is that  <string>  calls <ctime>  and time is a function of ctime 

just use other name for your class

---

### Post by Gulyan on 2008-10-28
try to use time_t

---

