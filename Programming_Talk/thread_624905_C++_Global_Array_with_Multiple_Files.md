---
title: "C++ Global Array with Multiple Files"
date: 2007-11-27
forum: Programming Talk
---

### Post by TreeFinger on 2007-11-27
I have a multiple file project as some of you may know. This is not a project that is getting graded, I am doing it for my own good, you have my word.

I am trying to declare global arrays that will be used through out the whole program in multiple functions. I declared these global arrays in the file that holds my main function. The other functions are not recognizing the declarations though. Do I need to put them in a header file?

---

### Post by dwhitney67 on 2007-11-27
If you are writing code in C++, why are you using global variables?

All variables should be encapsulated within a class, well at least that's the theory when it comes to OOD.

If you must use a global variable, then usually these are defined in one module, and then within the others that need to reference it, the tag "extern" is used.

For example, in module 1:

```
int var;

int main()
{
   ...
}
```

In module 2:

```
extern int var;

...
```

---

### Post by TreeFinger on 2007-11-27
Haven't learned about classes yet :( I am just reading about pointers..

This part of the project is after the chapter on arrays.

The book tells me:

'Add the following global arrays to the program:'

then it lists the global arrays I need to have.


After I create the global arrays it tells me to modify a function so it has parameters including all the arrays I just added.

I guess if I was using a single file program it would be easy to declare global arrays.

---

### Post by dwhitney67 on 2007-11-27
It seems like the class you are taking is perhaps a combo between C and C++, which syntactically have very many similarities.

I think many universities (maybe high schools?) prefer to teach Java as an introduction course to software programming because it enforces the OOD/OOP concepts more than C++.

Anyhow, I hope you will succeed with your assignment with the information I provided earlier.

---

### Post by TreeFinger on 2007-11-27
I am in university. I am taking an introductory computer science course. The language is C++.. the book we are using is 'Starting Out with C++.. From Control Structures Through Objects'. by: Tony Gaddis.

I am probably the only person in the class who actually reads and uses the book. Next semester I have an introductory to Java course. I am not that excited about it. I'd rather continue with C++.

In the summer I was learning C but I read somewhere it is good to learn C++ and then C. So I plan to do that when I am good in C++.

Thanks for the replies. I got it working.. even though I have no idea what extern does. Never heard of it.

---

### Post by SledgeHammer_999 on 2007-11-27
Treefinger, I recommend you this tutorial [http://cplusplus.com/doc/tutorial/](http://cplusplus.com/doc/tutorial/). You are going to learn all the basic C++ stuff really quickly. Then you can read your book for more details. I am noob in C++ but with this tutorial I am understanding  C++ pretty welland I am able to write programs.

---

### Post by neffk on 2008-02-08
BTW, you can get into problems with extern array syntax.  In more detail:  [http://kevin.l.neff.googlepages.com/externarrays](http://kevin.l.neff.googlepages.com/externarrays)

---

### Post by slavik on 2008-02-09
have you tried the following?
```
g++ main.cpp othercode.cpp
```

---

