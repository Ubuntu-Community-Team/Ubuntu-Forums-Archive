---
title: "[SOLVED] Eclipse CDT - float result displayed like integer"
date: 2008-05-12
forum: Programming Talk
---

### Post by iblazev on 2008-05-12
Hello!
Can anyone help me with this problem? 
I just installed Eclipse and CDT and tried a simple code like this:


int a,b;
float c;
c=a/b;
cout << c;

What I get as a result is an integer. Any ideas?

---

### Post by Quikee on 2008-05-12
> **iblazev said:**
> Hello!
Can anyone help me with this problem? 
I just installed Eclipse and CDT and tried a simple code like this:


int a,b;
float c;
c=a/b;
cout << c;

What I get as a result is an integer. Any ideas?

This is because a / b is regarded as integer division because both a and b are ints. Casting to float one of the variables should do the trick ( c = a / (float) b; ).

---

### Post by iblazev on 2008-05-12
> **Quikee said:**
> This is because a / b is regarded as integer division because both a and b are ints. Casting to float one of the variables should do the trick ( c = a / (float) b; ).

Haven't thought about that since it all worked in Visual C 6. Will try it your way:) 
Thanx

---

### Post by dempl_dempl on 2008-05-12
Visual C(++) 6 is  not ANSI compliant. 

Cheers!

---

### Post by iblazev on 2008-05-12
> **dempl_dempl said:**
> Visual C(++) 6 is  not ANSI compliant. 

Cheers!

Since I'm not full into programming, would you, please, explain why is that relevant? 
If you have any link where I could read more about it, that would help too:)

---

### Post by RIchard James13 on 2008-05-12
Not being ANSI compliant means the compiler does not follow the ANSI rules. The main compiler in Linux GCC is ANSI compliant so it does follow the ANSI rules.

Imagine that in your country everybody drove on the right hand side of the road. Now imagine that some people want to drive on the left hand side of the road. Without an agreement on which side of the road to drive on there would be traffic chaos. The same goes for computer code, there are rules that we try to follow. For instance if your program had 10,000 lines of code and you just ported it from a non-ANSI compiler where it works to a ANSI compiler where it doesn't work. Lots of work to find all the places the code is wrong just because people don't want to follow the standards. Lucky for you the code is only a few lines hey?

As for the actual ANSI rules for C++ they would be written into a thing they call a standard. Each standard has is dated so if a newer standard comes out people know to follow the new standard. There are not just standards for C++ code there are standards for things like building materials for houses and such. Also ANSI is just American National Standards Institute, there are other bodies(organisations) that do the same thing in different countries and there is an International organisation called the ISO as well. A lot of standards organisations charge for a printed copy of the standard which can suck if you want to study it.

---

### Post by WW on 2008-05-12
> **iblazev said:**
> Since I'm not full into programming, would you, please, explain why is that relevant?

You quoted dempl_dempl in your post, but I hope you don't mind if I jump in.

Division of integers in C and C++ always results in an integer.  The division operator / gives the quotient, and the modulus operator % gives the remainder.  For example, if a=21 and b=4, the value of a/b is 5 (not 5.25), and a % b is 1.

When given your code sample with a=21 and b=4, if Visual C/C++ does not print 5, then I would call that a bug in Visual C/C++.
> **iblazev said:**
> 
If you have any link where I could read more about it, that would help too:)
A google for "C++ integer division" will return lots of links where this is explained.  For example, [here](http://aspire.cs.uah.edu/textbook/CPP7004.html) or [here](http://www.cprogramming.com/tutorial/lesson11.html) (scroll down to the section "Typecasts in practice").

---

### Post by iblazev on 2008-05-13
Thanx ppl for clarifying some things. Although I know about standards, I didn't know that gcc and VC use different standards. 
As for my simple code, since I was just trying to renew my knowledge of programming, I just haven't thought about that int/int won't give float as a result in program. Now I fear what else I might do wrong:)

---

### Post by RIchard James13 on 2008-05-13
If you don't make mistakes you can't learn from them. If you aren't learning then you won't become a better programmer. Better to make mistakes and learn than to stop making progress.

---

