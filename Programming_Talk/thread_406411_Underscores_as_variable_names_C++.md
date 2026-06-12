---
title: "Underscores as variable names? C++"
date: 2007-04-10
forum: Programming Talk
---

### Post by qpwoeiruty on 2007-04-10
Is there any point to using underscores to start a local variable name or using _ by itself (or multiple __'s) other than making the code impossible to read? I have used just a _ for a variable name in the past for for loops in place of the typical "i", since I had already used it but a friend recently showed me some code like the following and I can't follow it at all or comprehend how someone can actually code like that. 

```
void ____(char _,int* __)
{     
     int ___ = 0, _____ = _;
     for (int _______ = 0;_______ < 8;_______++)
     {
          ___ = pow(2,7-_______);
          *__ = _____ / ___; __++;
          _____ %= ___;
     }
}
```

So is there any purpose to this or what?:confused: :confused: :confused:

---

### Post by rplantz on 2007-04-10
You already stated one really good reason not to do this -- it's almost impossible to read.

Another reason is that many global system names begin with underscores. If you make up a name that begins with underscores, it may collide with a global one that is being used by the system.

I heard about a guy who used various combinations of 0 (zero), O (upper-case oh), 1 (one), and l (lower-case ell) for his variable names. He did it as a joke.

---

### Post by slavik on 2007-04-10
afaik: objective C approach uses underscores in the beginning of variables to signify what is allowed to be read/written

---

### Post by ansi on 2007-04-11
My two cents: I use names with one underscore for local variables (e.g.: struct myStruct var_) in C, and names with one underscore for private members of classes in C++. I think it makes better program's readability.

---

### Post by winch on 2007-04-11
From [http://www.mozilla.org/hacking/portable-cpp.html#no_reserved_names](http://www.mozilla.org/hacking/portable-cpp.html#no_reserved_names)

> According to the C++ Standard, 17.4.3.1.2 Global Names [lib.global.names], paragraph 1:

Certain sets of names and function signatures are always reserved to the implementation:

    * Each name that contains a double underscore (__) or begins with an underscore followed by an uppercase letter (2.11) is reserved to the implemenation for any use.
    * Each name that begins with an underscore is reserved to the implementation for use as a name in the global namespace.


---

### Post by harun on 2007-04-11
As some have said people will use that in C++ sometimes for local variables, I prefer "l_" (L underscore) to prefix local variables. I don't like the look of underscores as the first letter and sometimes if people also use two of them it is hard to spot which has two and which have one. That would be extra bad practice.

So to answer your question, no there is no purpose to it and should be avoided unless the project you are working on was already started this way and changing it in the middle would mess others up.

---

### Post by hardyn on 2007-04-11
it looks like a comp sci exam question to me.

---

### Post by M$LOL on 2007-04-11
How on Earth are you meant to know how many underscores are in each one?

---

### Post by hardyn on 2007-04-11
I actully think it is supposed to look like this, your friend might have been playing a big of a joke?...


(4) [5 marks]
Complete the following code sample

void ____(char _,int* __)
{     
     int ___ = 0, _____ = _;
     for (int _______ = 0;_______ < 8;_______++)
     {
          ___ = pow(2,7-_______);
          *__ = _____ / ___; __++;
          _____ %= ___;
     }
}



look better now?

---

### Post by KaeseEs on 2007-04-11
That sort've looks like output from a lousy decompiler.

</2cents>

---

### Post by qpwoeiruty on 2007-04-11
> **hardyn said:**
> I actully think it is supposed to look like this, your friend might have been playing a big of a joke?...

I was thinking that he was but I copied it and was able to compile it without any errors. He said it was a character to binary converter.
I can't get it to work though. I don't know if it's because it's a junk function that doesn't really do anything or if it's a test question like you said or if I copied it wrong or  if I'm not calling it right, since I'm not so good on bit operators...

This is what I tried:
```
#include <iostream>

int pow(int b, int p) {
	if(p > 0) return b*pow(b,--p);
	else return 1;
}

void ____(char _,int* __)
{
int ___ = 0, _____ = _;
for (int _______ = 0;_______ < 8;_______++)
{
___ = pow(2,7-_______);
*__ = _____ / ___; __++;
_____ %= ___;
}
}

int main() {
	int* a; char b='A';
	
	____(b,a);
	
	for (int i = 7; i >= 0; i--) putchar(*a & (1 << i) ? '1' : '0'); 
	
	return (0);
}
```

Do you think he's just playing a joke on me? That'd be kind of annoying since I spent about an hour trying to figure this thing out and getting it to run properly...

As for _'s. In general I try to use them sparingly:
variables: something_new
functions: somethingNew
classes: SomethingNew
global variables: SOMETHING_NEW_

I've always wondered if my style is poor, especially with global variables, since I don't see many people writing them like that. I feel the same about the braces (like in pow or main above).

winch: What about constants in math.h? M_PI, M_E, and others that I can't remember unless I open the math.h file, like M_2_SQRTPIl

Ed: and yes, I know I could have used math.h for pow, but since it's an easy function anyway, I decided to just rewrite it

---

### Post by phossal on 2007-04-13
> **hardyn said:**
> it looks like a comp sci exam question to me.

LMAO. Of course! I can't believe no one said it sooner, and I can't believe no one laughed at you. That's *funny.* Your second post was hilarious. Some people just reject the truth. How many geeks does it take to get a joke?

---

### Post by HolyJoe on 2007-04-13
I saw some guy make a *fine* thing, after he completed his program, he use a tool to make his code impossible read, such as xxy1, xyyl, yxx, etc.

---

