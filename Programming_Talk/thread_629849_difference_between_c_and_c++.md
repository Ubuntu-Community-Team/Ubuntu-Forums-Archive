---
title: "difference between c and c++"
date: 2007-12-02
forum: Programming Talk
---

### Post by limac on 2007-12-02
hey,

What is the major difference between c and c++? and is it possible for me to learn c++ without learning c first?

Thanks

---

### Post by Auria on 2007-12-02
1) C++ supports object-oriented programming in the language, C does not
2) Yes you can learn C++ without having prior C knowledge, anyway if you learn C++ you will learn C basics along the way because C++ is based on C

---

### Post by limac on 2007-12-02
And what are the major usage of c++? c? And which one do u suggest i go with?

---

### Post by iharrold on 2007-12-02
C++ in my opinion.  Namely due to OOP allowing for more modular coding and a quicker crossover to other languages.

Also In my opinion, if you know C++ you can do C aswell.

---

### Post by LaRoza on 2007-12-02
> **iharrold said:**
> 
Also In my opinion, if you know C++ you can do C aswell.

If you mean learning the syntax of C, then that is true.

C and C++ are difference languages, although many say that C is a subset of C++, I do not think that is true.

C is a very simple language; C++ can be confusing, but isn't complicated either.

---

### Post by Auria on 2007-12-02
I personnaly prefer C++. Even if you don't use the advanced features, being able to use stuff like namespaces, and using new/delete instead of malloc/free are IMO worth it.
Also, most big projects are written with OOP or at least with OOP-like techniques. It takes time to master but IMO OOP is a big plus

(some people say they don't like OOP, but in many cases - though not all - it's just because they don't master it. the main reason for going with C instead of C++ is simplicity)

---

### Post by Fbot1 on 2007-12-02
[en.wikipedia:Compatibility of C and C++]("http://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B")

---

### Post by limac on 2007-12-02
I pasted this command in gedit:

#include<iostream>
using namespace std;

int main(void)
{
	
	double dnumber1 = 0.0; 
	double dnumber2 = 0.0;
	double dnumber3 = 0.0;
	double daverage = 0.0;

	cout<< "please enter 3 numbers!";<< endl;
	cin>> dnumber1;
	cin>> dnumber2;
	cin>> dnumber3;

	daverage = (dnumber1 + dnumber2 + dnumber3) /3;
	cout<< "the average of the numbers are: "<< daverage << endl;

	return 0;
}

and saved it as "c++.cpp"

Then when i tried to run it thru terminal this is what it said:

limac@limac-ubuntu:~$ cd ~/Desktop
limac@limac-ubuntu:~/Desktop$ g++ -o c++ c++.cpp
c++.cpp: In function ‘int main()’:
c++.cpp:12: error: expected primary-expression before ‘<<’ token
limac@limac-ubuntu:~/Desktop$ 

What went wrong???

---

### Post by LaRoza on 2007-12-02
> **limac said:**
> I pasted this command in gedit:

#include<iostream>
using namespace std;

int main(void)
{
	
	double dnumber1 = 0.0; 
	double dnumber2 = 0.0;
	double dnumber3 = 0.0;
	double daverage = 0.0;

	cout<< "please enter 3 numbers!" << endl;
	cin>> dnumber1;
	cin>> dnumber2;
	cin>> dnumber3;

	daverage = (dnumber1 + dnumber2 + dnumber3) /3;
	cout<< "the average of the numbers are: "<< daverage << endl;

	return 0;
}


You can had an extra semi colon.

---

### Post by limac on 2007-12-02
where was that?

---

### Post by Auria on 2007-12-02
cout<< "please enter 3 numbers!"[COLOR="DarkRed"]_**;**_[/COLOR]<< endl;

---

### Post by mellowd on 2007-12-02
Part of learning to program is learning how to debug. They go hand in hand

---

### Post by LaRoza on 2007-12-02
> **limac said:**
> where was that?

There error messages are cryptic, but the line number given is usually correct, +/- 1 line.

---

### Post by limac on 2007-12-03
Thanks for those answers they worked!!!

And also I installed dev-c++ (bloodshed) compiler but couldn't run the file after compiling it successfully. I mean if I click on run no actions take place.

what to do to fix that?

---

### Post by smartbei on 2007-12-04
Are you sure nothing happens?

In dev-c++ the console window closes as soon as the program finished execution (main returns). Add this at the end (but before the return of course) so that the window will stay open:
```

int test;
cin >> test;

```

---

### Post by kvorion on 2007-12-04
Write a getch() or a cin>> statement towards the end of your program so that the output window remains there till you can view it

---

### Post by SteveHillier on 2007-12-04
> **LaRoza said:**
> C is a very simple language; C++ can be confusing, but isn't complicated either.

The old saying used to be you can learn a new programming language in 3 months but you need 6 months to learn C.
C is very simple at certain levels.  Because of it low use of reserved words and simplistic syntax you can get to grips with some of it relative easily, however to be really good does take a bit longer.
I have seen good code and I have seen awful code.
Good code would consist of small functions, good flow control, tight lops etc.  |I used to work on the basis that if a function went over more than two screens it was probably getting too big.
I have seen some function stretching over a 30 page listing.  It is almost impossible to see how the code is controlled and is a nightmare to debug.
So maybe the language is simple but what you do with is may not be.  Ultimately you pays your money and take your choice.

---

### Post by pmasiar on 2007-12-04
Learning syntax of a language is one thing. Learning idiomatic usage of language, libraries and data structures is different - and takes substantially more time.

Catch with learning C  vs C++ is: idioms are different, valid C is bad C++ and vice versa. 

Disclosure: I am not C/C++ expert but this is what real experts repeated over and over in previous discussions. :-)

---

### Post by raul_ on 2007-12-04
BAsically they are used to implement different programming paradigms-

---

### Post by bobbocanfly on 2007-12-04
```
cout<< "please enter 3 numbers!"**;**<< endl;
```

Edit: Ignore, already been answered above

---

### Post by Hairy_Palms on 2007-12-04
which to learn is dependandt on what you want to do, if your planning to make GUI apps then C++ is easier to do than C, but well written C apps are very efficiant in resource usage, i personally need to use C much more than C++ because i program microprocessers and almost all microprocessers must be programmed in assembler or C,

---

### Post by JupiterV2 on 2007-12-04
Speaking from personal experience, C++ is more human intelligible. What I mean is, I found it easier to represent my ideas/thoughts in code form in C++ because of OOP design. By no means is C++ more powerful than C, as C excels in areas that C++ does not  but that it is easier, or perhaps faster,  to be "good" at C++ than C just as another poster has already stated.

---

### Post by Wybiral on 2007-12-04
> **JupiterV2 said:**
> Speaking from personal experience, C++ is more human intelligible. What I mean is, I found it easier to represent my ideas/thoughts in code form in C++ because of OOP design. By no means is C++ more powerful than C, as C excels in areas that C++ does not  but that it is easier, or perhaps faster,  to be "good" at C++ than C just as another poster has already stated.

I certainly know what you mean. But at the same time, for a real beginner, learning C++ may present some extra hurdles that C doesn't. Templates and OOP can be overwhelming if you're unfamiliar with some of the simpler aspects of programming.

But, to be my own devils advocate, the amount of manual memory management and pointer magic required in C will also present hurdles for a beginner. So, I guess, take your pick :)

---

### Post by raul_ on 2007-12-04
> **Wybiral said:**
> But, to be my own devils advocate, the amount of manual memory management and pointer magic required in C will also present hurdles for a beginner. So, I guess, take your pick :)

i would say they represent hurdles for an expert :lolflag:

"Segfault happens"

---

### Post by evymetal on 2007-12-04
> **Wybiral said:**
> Templates and OOP can be overwhelming if you're unfamiliar with some of the simpler aspects of programming.


Well I'm certainly not unfamiliar with programming, and C++ still scares the living daylights out of me. Much prefer C, it's slightly faster and to be honest I love the Pointer Magic. (but then I only use either for numerical work)

---

### Post by SteveHillier on 2007-12-05
> **evymetal said:**
> Well I'm certainly not unfamiliar with programming, and C++ still scares the living daylights out of me. Much prefer C, it's slightly faster and to be honest I love the Pointer Magic. (but then I only use either for numerical work)

C++ scares me as well (as does C#) but that is because I do not understand OOP.  I spent a number of years writing C for DOS and I feel I was quite good at it, but I stopped programming at the time when OOP was gaining ascendancy.  As a previous post says, what you choose also depends on what you are trying to do.  I once programmed in Fortran which for floating point numbers was great (and far better than C when all you had was the FP libraries).  So I would not like to try to write a linear program in C nor would I try to write an OS in Fortran.

You could say by way of analogy which is better beer or wine.  Please provide your own answer to that!!

---

### Post by dptxp on 2007-12-05
Classes in of C++, can be implemented to some extent by using structures. If you keep off from classes, especially the more complicated classes as friend classes, C++ is more convenient.

Java, derived from C, has two major differences, there is no goto and
there are no pointers.

All 3 are pretty similar.

---

### Post by tyoc on 2007-12-05
havent readed the complete thread, but I want to answer from some time now this thread

I will take random quotes and answer them

> C++ supports object-oriented programming in the language, C does not
OOP is a paradigm, C++ has built-in support for OO, but in C you can code OO, with or without structures (like suguested by post before).

>  C and C++ are difference languages, although many say that C is a subset of C++, I do not think that is true.
 
 C is a very simple language; C++ can be confusing, but isn't complicated either.

Normally C++ will be translated to C (IIRC), thus who is the subset?? C++ is "more specific"... I mean take this example [http://students.ceid.upatras.gr/~sxanth/lwc/](http://students.ceid.upatras.gr/~sxanth/lwc/) take the point.

Also for some critisism (but thats not the point, isn't?)  on OO I suguest [http://www.geocities.com/tablizer/oopbad.htm](http://www.geocities.com/tablizer/oopbad.htm)

---

### Post by Wybiral on 2007-12-05
> **tyoc said:**
> ... [http://www.geocities.com/tablizer/oopbad.htm](http://www.geocities.com/tablizer/oopbad.htm)

Some of the stuff on that Geocities link is hilarious! That has to be a joke, right?

---

### Post by Auria on 2007-12-05
> **tyoc said:**
> 
Normally C++ will be translated to C (IIRC),

huh, the first C++ compiler ever did that, i would be extremely surprised to learn that any recent C++ compiler still works like that

---

### Post by LaRoza on 2007-12-05
> **Auria said:**
> huh, the first C++ compiler ever did that, i would be extremely surprised to learn that any recent C++ compiler still works like that

The one in the link did.

C is translated to assembly in gcc.

---

### Post by SteveHillier on 2007-12-06
> **dptxp said:**
> Java, derived from C, has two major differences, there is no goto and
there are no pointers.

All 3 are pretty similar.

The point here is that they are syntactically similar but then the similarity ends.  Those of us who are used to a switch statement in C (and convert all options to integer values) find it requires thought when you start using a switch in Java.  And I am sure there are many other examples, but I cannot spare time to research it.

---

### Post by aks44 on 2007-12-06
> **Auria said:**
> huh, the first C++ compiler ever did that, i would be extremely surprised to learn that any recent C++ compiler still works like that

One of the best C++ compilers out there ([Comeau]("http://www.comeaucomputing.com/")) still produces C code. Those guys decided they'd let C compilers handle the low-level stuff, so they could focus on C++ standard-compliance.

AFAIK they're the only compiler who handles the export keyword (which tells much about the rest, since export is a very small detail in the standard, yet quite hard to implement).



Back to C vs C++... IMHO PHP is closer to C than C is close to C++. IOW, don't let the syntax fool you, they don't have much in common.

---

