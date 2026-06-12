---
title: "C++: Add character to string?"
date: 2010-02-21
forum: Programming Talk
---

### Post by Imaginary-r4e- on 2010-02-21
Hi! 

I want to do the following:
```
string += char;
```
And have tried it like this:
```
string += string(char);
```
And this:
```

stringstream << char;
stringstream >> string2;
string1 += string2;
```
None of them work accurately. When running the first one I receive the following error-message:
> /home/anton/programming/codeblocks/test/main.cpp|79|error: invalid conversion from ‘char’ to ‘const char*’|
And the second one does not fit with the needs of the application.

Does anyone have a solution for this?

*Best Regards, Imaginary-r4e-.*

---

### Post by MadCow108 on 2010-02-21
the + operator of string is overloaded for char so the first should work assuming your variable is not called "char" as that is a reserved word
[http://www.cplusplus.com/reference/string/operator+/](http://www.cplusplus.com/reference/string/operator+/)

the error message suggests the problem is elsewhere

do you have something like that in your codE?
```

const char * a = 'd';

```
this is illegal as single quotes denote char and not char*

---

### Post by Imaginary-r4e- on 2010-02-21
This is how the char is set: string[int]

Code:
```
string += string[int];
```

---

### Post by Some Penguin on 2010-02-21
What is the type of 'string' ?

---

### Post by MadCow108 on 2010-02-21
> **Imaginary-r4e- said:**
> This is how the char is set: string[int]

Code:
```
string += string[int];
```

ok what should I do with this nonsense? pseudocode is useless for finding syntax errors ...
please provide valid code/the line which gives the error

---

### Post by Imaginary-r4e- on 2010-02-21
Oh, sorry. Seems like I've been mixing up languages :oops:

Anyways, this is what I have now but I still get the same error message.
> string1 += string(string2.at(int));

Error message: /home/anton/programming/codeblocks/test/main.cpp|79|error: invalid conversion from &#8216;char&#8217; to &#8216;const char*&#8217;|

---

### Post by Some Penguin on 2010-02-21
Are 'string' and 'int' actual variable names, or are you still refusing to show actual code?

---

### Post by Imaginary-r4e- on 2010-02-21
There was never any need to show the code. Solved the problem simply by removing string(). Looks like this now and works like a charm:
```
a += b.at(x);
//Or
string1 += string2.at(int); //Just to clarify
```

---

### Post by MadCow108 on 2010-02-21
the string constructor does not take a char as returned by .at() (or the [] operator
[http://www.cplusplus.com/reference/string/string/string/](http://www.cplusplus.com/reference/string/string/string/)

as + takes char you also don't need to convert it to a string in the first place

---

### Post by dwhitney67 on 2010-02-21
> **Imaginary-r4e- said:**
> There was never any need to show the code.
Much thanks for wasting everybody's time.

P.S.  If your code uses single character variable names, I hate to guess what your name is.

---

