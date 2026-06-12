---
title: "C++ basics"
date: 2006-03-02
forum: Programming Talk
---

### Post by grim918 on 2006-03-02
What are considered the C++ basics. I just finished my first C++ book which dealt with nothing but command line programs. I still don't feel like I have learned much. I want to move on and start learning GUI programming with QT, but they advise that I should know the C++ basics. I am comfortable working with pointers, building my own classes and anything else that was in the book that my school used. The book did not teach us anything advanced though. We only learned how to deal with datatypes. If I choose to teach myself QT will it be harder for me, or should I try to find myself a more advanced book on C++. Would it be possible to do both. Thank you for any advice you can give me.

---

### Post by darth_vector on 2006-03-02
basic stuff includes:
flow control
string manipulation
pointers
data types
oo design
data structures (ie. the STL)
templates
sorting algorithms
and much other stuff.

in most cases, command line programs are all you need.

---

### Post by grim918 on 2006-03-02
The other stuff is what i get confused about. Either way, I'm just going to start teaching myself some GUI programming.

---

### Post by moberry on 2006-03-02
If you are good with pointers. You should be fine. It would be good to brush up on some advanced data types. Start off with linked lists, then try out binary trees. That will teach you ALOT about how memory is layed out, "how programming works." This is what I did and it helped alot.

-jordan

---

### Post by grim918 on 2006-03-03
Do you know where I can find some online resources for advanced datatypes. I have tried to find some advanced stuff on C++ but I can't find something that explains how things work. Most tutorials just throw a bunch of code at you and don't explain anything, or do you know of a good book.

---

### Post by jerome bettis on 2006-03-03
concepts of programming languages by sebesta might be what you're looking for.  it covers abstract data types, as well the stack and heap, which is fundamental to c++ and OOP.  lots of other complicated c++ stuff is covered, it's a text book but after reading it i really started to understand how c++ works and wrote better code.

it's not all c++ though, but languages in general.  but c++ is so big it covers the stuff you need to understand to avoid sloppy code.

---

### Post by thumper on 2006-03-03
[QUOTE=grim918]Do you know where I can find some online resources for advanced datatypes. I have tried to find some advanced stuff on C++ but I can't find something that explains how things work. Most tutorials just throw a bunch of code at you and don't explain anything, or do you know of a good book.[/QUOTE]What do you mean by "advanced datatypes"?

My suggestion would to become very familiar with the standard containers (vector, list, deque, set, multiset, map and multimap), and their adapters (stack, queue).  Understand when to use each one, and what the performance is like for different operations (inserting at the start, middle, end, and reading are most common).

Once you have a good grasp of these, creating complex datatypes using the standard containers is much easier.

Get a copy of "The C++ Standard Library: A Tutorial and Reference" by Nicolai M. Josuttis, ISBN 0201379260.  This is a very good book, and all the top C++ people I know have a copy and refer to it frequently.

Don't be put off by the cost, think of it as an investment.  You will be referring to it often.  Can't stress that enough.

---

### Post by grim918 on 2006-03-03
Thank you thumper. That is the kind of book I been looking for. I looked it up on amazon. who cares about the cost. Your right, it is an investment.

---

### Post by thumper on 2006-03-03
You won't regret it.

Not sure how much cash you've got, but here are some other recommendations:
Effective C++ (3rd Edition), Scott Meyers
More Effective C++, Scott Meyers
Exceptional C++, Herb Sutter
 - in fact you can't really go wrong with any of the books in the Addison Wesley C++ in depth series.

Try not to get sucked in to Bjarne's "C++ Programming Language", although I have a copy, I hardly look at it preferring to go to Nico's book or the C++ standard itself.

---

### Post by pharcyde on 2006-03-04
Check out [www.cppreference.com](www.cppreference.com).  If you are familiar with building advanced structures from these data types, then I suggest looking at [www.boost.org](www.boost.org).  Most of the stuff in the boost library is very advanced but there is some really neat stuff there.

I would suggest learning when to use the correct data types for what type of applicatiosn you are building.  You can use google to look up Ordered notation for various algorithms and data structures pertaining to search, insertion and space complexity.  This is important to know if you are building libraries for large scale operations, embedded system, etc.

The biggest thing that I never learned in school/books was using function pointers (callbacks) with advanced data structures and algorithms.  Using these can provide very nice generic maintainable code.  The other thing that is pretty cool to learn is utilizing the C/C++ preprocessor.  I've learned some really cool tricks for creatnig generic inline macros and librarie decalarations that are very scalable.  The boost library has a very cool preprocessor thing if you are interested in that type of thing.

---

### Post by LordHunter317 on 2006-03-04
[QUOTE=pharcyde] The other thing that is pretty cool to learn is utilizing the C/C++ preprocessor.[/quote]No, it isn't.  This is something you should stay around from beyond the requirements to include header files and properly create them cross-platform.  It's an evil, and an abortion.

---

### Post by pharcyde on 2006-03-04
[QUOTE=LordHunter317]No, it isn't.  This is something you should stay around from beyond the requirements to include header files and properly create them cross-platform.  It's an evil, and an abortion.[/QUOTE]

I know some people believe strongly as you do.  I should probably clarify what I meant on this statement.  I wasn't talking about using macros for inline and slapping them around haphazardly. declarations because of no type checking and hard to read/modify code.  I do think it is good for writing redudant code when writing libraries for other people that need to be fast and when said people are not trying to modify or are not concerned with the low level implementations of it. Besides its still neat to learn.

---

### Post by Lux Perpetua on 2006-03-04
What genericity issues do macros solve that templates don't? What cool tricks are you referring to?

---

### Post by LordHunter317 on 2006-03-04
[QUOTE=pharcyde]I do think it is good for writing redudant code when writing libraries for other people that need to be fast and when said people are not trying to modify or are not concerned with the low level implementations of it.[/quote]Why?  Why not use templates and meta-programming, if necessary?

Preprocessor macros are nearly useless in C++, because inline functions and turing-complete templates can provide.  That being said, real macros would still be useful on occassion, if only to hide some of the syntatical blemishes of the latter.

Their primary use is to really resolve configuration issues that can only be resolved by having different sources, or where that is the best solution.  

> Besides its still neat to learn.It's far neater to learn real macros, like in Scheme, Nemerle or any one of the other functional languages.

---

### Post by pharcyde on 2006-03-04
[QUOTE=Lux Perpetua]What genericity issues do macros solve that templates don't? What cool tricks are you referring to?[/QUOTE]

I wasn't referring to genericity issues related to simple template declarations.  I have seen macros get around some nasty nested template idioms that occur in different compilers.  These were being used in combination with conditional preprocessor statements.

[QUOTE=LordHunter317]It's far neater to learn real macros, like in Scheme, Nemerle or any one of the other functional languages.[/QUOTE]

I haven't used those languages for anything before.  What are they used for?  What languages are they similar too?

I'm glad you guys responded with questions/pointers regarding this issue.  Maybe we can fork a thread that can discuss these types of issues further. I love talking about these types of things and getting others perspectives on coding practices. :)

---

### Post by LordHunter317 on 2006-03-04
[QUOTE=pharcyde]I wasn't referring to genericity issues related to simple template declarations.  I have seen macros get around some nasty nested template idioms that occur in different compilers.[/quote]Using them to work around compiler issues would fall under the acceptable category I listed above.

Certainly for an introductory programmer, they're a non-issue.  It's not even an issue for most library designers.


> I haven't used those languages for anything before.  What are they used for?  What languages are they similar too?They're functional languages.  Scheme is a LISP.  Nemerle is a essentially a functional version of C#.

---

