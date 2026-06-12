---
title: "Why isn't there  a static, compiled version of Python?"
date: 2012-07-23
forum: Programming Talk
---

### Post by Superpelican12 on 2012-07-23
A.k.a why are all easy to learn languages with a nice syntax (Python, Ruby etc.) interpreted? Why aren't there compiled versions of Python and/or Ruby? Why isn't there a language which combines easy to learn, easy to read and fun to program in with effiency and performance? I have read about D, but D still features some of the ugly parts of C++ (for example the way you have to add  a variable in a text string) and it misses a lot of libraries. For example the D-binding for GTK (GTKD) is still at GTK version 2.24...

---

### Post by trent.josephsen on 2012-07-23
What benefit would native compilation bring to Python or Ruby?

How would *you* design a language to be "easy to learn, easy to read", "fun to program in", and fast? How does Python, Ruby, Perl, C, Java, or your other language of choice not meet these needs?

---

### Post by DangerOnTheRanger on 2012-07-23
Sounds like you're looking for something like [Cython]("http://cython.org").

---

### Post by MadCow108 on 2012-07-23
you might want to look at boo:
[http://boo.codehaus.org/](http://boo.codehaus.org/)

its a good mix between dynamic and static compiled language with a python like syntax and compiled bytecode performance


there is also jython and ironpython which compile normal python to bytecode, but the performance gain is not so great due to the dynamic nature of python.

---

### Post by 3Miro on 2012-07-23
In C, you will have a variable "int a". This variable will take up exactly 4 bytes of memory and operations like "a++" will take exactly one instruction. int a is fast, but you have to explicitly declare "int" and you cannot use a to store anything other than a 32-bit integer.

In Python, you can have a variable "a", but a can be an integer or double or a whole class. Every time you reference "a", Python has to figure out if it is an integer or class, hence any operation on "a" will take several cycles.

This doesn't even go into dynamic memory.

The reason why Python is slower than C doesn't come from it being compiled. Python is slower than C because the syntax is very simple and Python has to do a lot of the "difficult" stuff behind the scenes for you.

Easy syntax and speed are mutually exclusive.

You can do even faster than C, as C also does some things in the background. Compare C to Assembler to see what I mean.

---

### Post by Superpelican12 on 2012-07-23
> **trent.josephsen said:**
> What benefit would native compilation bring to Python or Ruby?

How would *you* design a language to be "easy to learn, easy to read", "fun to program in", and fast? How does Python, Ruby, Perl, C, Java, or your other language of choice not meet these needs?

How I would design a language that meets all those requirements?
I would use the syntax of Python 3.2 remove the dependence  on indentation. 
And instead use curly braces to begin and end blocks of code (just like in C). Make Python static by requiring the programmer to define the data type (like in C). Which also removes the requirement to directly  assign a value to variable when declaring a variable and this also increases the performance.  Also the language  should  have a garbage collector and further automatic memory management. 

Why you would want such a language? Well it would broaden the use of Python.
You could write large, professional 3D games in one easy to read language.
Also the language could be used for mobile app development.
It would increase battery life and there won't be such a need for quad core
SOCs to run all apps, games and your fancy interface  smoothly. It would be easier for beginners to start developing apps. And would greatly reduce maintenance  costs because it's easier to to read.

EDIT: @3Miro I know what you mean, that' s exactly why I think Python should be statically typed. Of course I'm not a professional in language design(actually  I'm till learning to program (in Python). I was just curious why such a language  doesn't exist. I know that the language  I described  above will never meet the performance  of C/C++. But at least come a lot closer than the performance  of Python currently comes. 

Also when I will ever need performance, I will learn Cython. I already heard of it ;)

---

### Post by The Cog on 2012-07-23
Have a look at Googe's Go language ([http://golang.org/](http://golang.org/)). This is quite python-like and is properly compiled.

---

### Post by MadCow108 on 2012-07-23
> **Superpelican12 said:**
> How I would design a language that meets all those requirements?
I would use the syntax of Python 3.2 remove the dependence  on indentation. 
And instead use curly braces to begin and end blocks of code (just like in C). Make Python static by requiring the programmer to define the datatype (like in C). Which also removes the requirement to directly  assign a value to variable when declaring a variable and this also increases the performance.  Also the language  should  have a garbage collector and further automatic memory management. 

and what would be the difference of that to C then?
you can use garbage collectors with C too.

or just use go.

---

### Post by Bachstelze on 2012-07-23
> **Superpelican12 said:**
> How I would design a language that meets all those requirements?
I would use the syntax of Python 3.2 remove the dependence  on indentation. 
And instead use curly braces to begin and end blocks of code (just like in C). Make Python static by requiring the programmer to define the datatype (like in C). Which also removes the requirement to directly  assign a value to variable when declaring a variable and this also increases the performance.  Also the language  should  have a garbage collector and further automatic memory management. 

This is not designing a language, this is just stating some vague properties, that's very easy. Then you have to do the actual design, and write the compiler. Good luck. :)

---

### Post by juancarlospaco on 2012-07-23
You can compile python .py to C using shedskin or nuitka, google them, both GPL

---

### Post by 3Miro on 2012-07-23
> **Superpelican12 said:**
> 
EDIT: @3Miro I know what you mean, that' s exactly why I think Python should be statically typed. Of course I'm not a professional in language (arctually  I'm till learning to program (in Python). I was just curious why such a language  doesn't exist. I know that the language  I described  above will never meet the performance  of C/C++. But at least come alot closer than the performance  of Python currently  is. 


The garbage collector is the definitely the part of Python that increases the memory requirement compared to C. The static types was an example, the real problem would be to make efficient memory management that is both fast and reliable.

How familiar are you with memory management on C/C++? IMO, what you propose simply cannot be done.

---

### Post by MadCow108 on 2012-07-23
memory management is nowadays widely recognized as better than manual management.
Not only in programmer time but also in runtime (and in case of a bad programmer also memory usage). garbage collectors don't suck anymore since many years. Even in higher level embedded space its very common now.

what costs the performance and memory is mainly just the dynamic nature and interpreter. a list of things is not just a block of memory its a block of memory full of pointers pointing to more blocks of memory.
If you combine python with a decent tracing JIT you can archive C like performance easily usage (see pypy for an example)

---

### Post by trent.josephsen on 2012-07-23
Let's suppose that a hypothetical language U meets your requirements. It's easy to learn, easy to write, easy to read, capable of expressing every possible complex construct, and compiles to a small native binary that performs equally well or better than the best-written C version.

The U compiler (I'm hoping there isn't a real language named U) must therefore interpret programming constructs that *are conceptually different, but have the same effect* and compile them to *equivalently fast* machine code. A simple example might be using a for-loop vs. a while-loop to iterate over something. A more complex example might be calling object.foo() versus obj_foo(object). Those things are conceptually equivalent, so they should perform the same, without forcing the programmer to drop into C-land with manual memory management and all that nonsense. Right? (If you're suspicious, it's because I'm laying a trap for you.)

Then it's not sufficient for the U compiler to merely compile the code. In order to perform the necessary optimizations, it needs to "understand" the instructions, read between the lines, and figure out which parts are important to what will actually happen in practice...

I was going to continue at length but I think this has gone long enough. Bottom line, U doesn't exist because we don't have the resources necessary to make it work. To paraphrase a famous philosopher, "if static typing was all we needed to make Python as fast as C, don't you think we'd have heard of it before?"

(Not sure why you're picking on significant whitespace, btw -- it's definitely one of Python's strengths and an important aspect to the "easy-to-read" requirement.)

---

### Post by slavik on 2012-07-23
> **MadCow108 said:**
> memory management is nowadays widely recognized as better than manual management.
Not only in programmer time but also in runtime (and in case of a bad programmer also memory usage). garbage collectors don't suck anymore since many years. Even in higher level embedded space its very common now.

what costs the performance and memory is mainly just the dynamic nature and interpreter. a list of things is not just a block of memory its a block of memory full of pointers pointing to more blocks of memory.
If you combine python with a decent tracing JIT you can archive C like performance easily usage (see pypy for an example)
And yet, OutOfMemoryError and FullGC spins are the #1 reason why I restart JVMs. Programmer time is not expensive, it is dirt cheap. Good programmer time is expensive. Just like in every other profession, there are those who know what they are doing and those who don't.

---

### Post by Superpelican12 on 2012-07-24
> **3Miro said:**
> 
How familiar are you with memory management on C/C++? IMO, what you propose simply cannot be done.
Well  I have never really learned C/C++ (have tried to learn C++, but found  it a little to complicated as first language, especially the memory  memory management), but I do understand what pointers are (have read: [http://www.cplusplus.com/doc/tutorial/pointers/](http://www.cplusplus.com/doc/tutorial/pointers/)  and understand the article) I also know that you allocate memory in C  with malloc(), deallocate with free(). And in C++ with delete(). I'm  sure this is not everything about memory management in C/C++ :wink:, but at least I know something...

Also  it seems to me (correct me if I'm wrong)it actually is possible to  create a language with reasonable performance (close to C/C++) with  automatic memory management/garbage collector, look at D ([http://www.dlang.org](http://www.dlang.org))  and Go which' s performance is almost as good as C's (there was a  website it had  "debian" in it's name, I can't remember the exact name,  to compare the performance of programming languages, Go performed almost  as good as C, with the other languages far behind). But of course the  ultimate language will never exist (but you can make compromises). 

> The U compiler (I'm hoping there isn't a real language named U)
Fortunately a programming language named  "U" doesn't exist ([http://en.wikipedia.org/wiki/List_of_programming_languages](http://en.wikipedia.org/wiki/List_of_programming_languages)) ;)

> In C, you will have a variable "int a". This variable will take up  exactly 4 bytes of memory and operations like "a++" will take exactly  one instruction. int a is fast, but you have to explicitly declare "int"  and you cannot use a to store anything other than a 32-bit integer.

In Python, you can have a variable "a", but a can be an integer or  double or a whole class. Every time you reference "a", Python has to  figure out if it is an integer or class, hence any operation on "a" will  take several cycles.
That's why I think "U" should be statically typed (with almost the same implementation of data types as plain C)

For example this program in Python:
```

a = input("Please enter a number:")

def main()
 b = a**2
 mytext = "Your number squared = "
 print( mytext + b + "!")

```
would be this in "U":
```

int a
a = input("Please enter a number:")

def main() {
int b;
str mytext;
b = a**2;
mytext = "Your number squared = ";
print(mytext + b + "!");
}

```
Of  course as I stated earlier I'm absolute not a language design  professional (neither are an advanced programmer, just learning Python).  But "U" is how my ideal language would look like.

> 
It's easy to learn, easy to write, easy to read, capable of expressing  every possible complex construct, and compiles to a small native binary  that performs equally well or better than the best-written C version.

Also  3MIRO seems to be stating several times that I want my ideal language  to perform better than C/C++. While I actually meant that my language  should come closer to C/C++ performance (for example like Go). I  understand that you can't have everything ;). But a nice compromise may  be possible...

> 
You can use garbage collectors with C too.

Are  there also garbage collectors for C++, which allow you to don't use  pointers, malloc etc. at all? Similar to how you handle data types in  Python (but of course static)?

> 
Python is slower than C because the syntax is very simple and Python has  to do a lot of the "difficult" stuff behind the scenes for you.

So  the example(?) you showed me about C being statically typed and Python  dynamic, probably is only an example? And what you showed me was  actually only a little piece of the whole picture?

---

### Post by NilPointer on 2012-07-24
There is RPython, which is restricted subset of Python. It has garbage collection but doesn't feature python's dynamic features and can be compiled. It boasts to have same execution speed as C and in some cases to be even faster. Unfortunately, I didn't find standalone RPython. If I remember correctly, it's part of PyPy project.

---

### Post by Superpelican12 on 2012-07-24
Is RPython compatible with existing CPython libraries?

---

### Post by NilPointer on 2012-07-24
> **Superpelican12 said:**
> Is RPython compatible with existing CPython libraries?

Pure python libraries can be used via PyPy (Full python interpreter implemented on top of RPython).

Some Python code should be compatible with RPython.

Update: Check out shedskin - it's RPython-to-C++ translator (after translating to C++ it can be compiled). Looks like it works (but requires to install several libraries and development files packages). Although translation speed is low (shedskin seems to be implemented in full Python) and compiled binaries seem oversized (231 KB helloworld, probably because of GC and other statically linked libraries). But anyway, I got few simple Python programs compiled to standalone binaries.

---

### Post by Superpelican12 on 2012-07-24
Thanks @Nilpointer for being so kind to spend some of your time helping me out.
I understand why all the libraries for CPython are not compatible. 

But I think I'd rather stick with Cython as it is more mature and has good compatibility with CPython libs  ;). Also it seems to have been for a lot of projects already.

---

### Post by 3Miro on 2012-07-24
> **Superpelican12 said:**
> Well  I have never really learned C/C++ 

You should learn it then, it will give you a much better understanding of how computers work.

---

### Post by Superpelican12 on 2012-07-24
Should I only study some basics to understand  how computers work? Or should I learn the whole language? Should I really use the language  as my main general purpose language or just read some tutorials and some basic exercises and use Python for the rest?

Also should I learn C, C++ or both? I personally prefer C+, but
C seems to be more used for low-level  stuff. Plus I could
use it with Cython. And I actually don't need the Polish  of C++, I'll probably
do all the object oriented stuff, the GUI etc. in Python. And only use C
for the low level stuf and the simple and stupid number crunching etc.

I've already ordered some C books and one C++ book at the library (are local library
unfortunately has quite a limited selection of books, especially in things related to computers. So all the cool stuff has to come from other bigger libraries).

---

### Post by 3Miro on 2012-07-24
> **Superpelican12 said:**
> Should I only study some basics to understand  how computers work? Or should I learn the whole language? Should I really use the language  as my main general purpose language or just read some tutorials and some basic exercises and use Python for the rest?


If you want to learn how things work on the lowest level, then you need to learn as much C as possible.

C++ is better for a "general purpose" language.

There are so many languages because they all have strengths and weaknesses. You should never restrict yourself to one language, you should know as many of them as possible. You should use whatever language is best for the job that you are trying to do.

I think that a person with good understanding C/C++ can learn new languages really quickly. A person with good understanding of Python (or Java or C# or Ruby) will probably find C/C++ hard to learn.

---

### Post by CptPicard on 2012-07-25
> **3Miro said:**
> A person with good understanding of Python (or Java or C# or Ruby) will probably find C/C++ hard to learn.

This is the age-old low-level vs. high-level language conceptual understanding discussion that we seem to come back to pretty much any time someone asks for example what the most beneficial learning curve for a beginner is.

Personally, while I agree with the sentiment that one should expose oneself to as many languages as one can because they give you somewhat different takes on how to approach problems, the supposedly "how computers work" understanding that C is supposed to give you is overrated by many people. Even the computational model assembly exposes is not really "how computers *really* work"; the CPU microcode does all kinds of things underneath the x86 instruction set compatibility layer.

Manual memory management is often brought up at this point; I've always been rather lukewarm about its "meaning" to a programmer. Sure, you'll want to understand it as a resource management problem and pointers are to be seen as an example of "indirection" which is pretty important in programs... but it's also rather boring and "dumb bug"-prone stuff that holds back actual doing of things. To elevate it in significance beyond what it is, seems to ignore that there is so much more interesting stuff in programming.

C++ is particularly problematic as it adds more language-related "complication" than it addresses handling actual inherent complexity in the problem. That's why I would never suggest that a n00b spend too much time learning C++ specifically; once one is more competent as a programmer in general one can deal with the associated issues and quirks more comfortably.

I guess this opinion comes from the fact that my own evolution as a programmer went from doing Pascal and C to Java -- and then meeting languages like Python and in particular Lisp (and Prolog), which were rather mind-blowing and liberating from drudgery. And I really would never say that C "makes me understand Lisp better" for example -- it's just not part of the mental model there. 

Really, the idea that lower-level languages somehow communicate something conceptually to higher-level languages is just even theoretically wrong, as either can be written in terms of the other, and the underlying implementation is just completely opaque. There is no conceptual communication.

---

### Post by 3Miro on 2012-07-25
- the OP already knows Python, he is interested in learning how and why C/C++ code often times makes for faster programs. Learning C/C++ is the best way to understand this.

- I switched from C++ to Python fairly easily. On the other hand, people that already know Python will have to learn the whole new concept of memory management and static variables. People who know only Python have to put an effort to learn C/C++.

- Lisp is a fundamentally different language from a class of its own. I don't see how it is relevant here.

- An algorithm is independent from implementation, but a bad implementation can ruin a good algorithm. A programmer should know both how to make an algorithm and how to implement it (in multiple languages).

@CptPicard: you are reiterating an old argument that is floating around, but I don't see how it is related to this particular discussion.

---

### Post by Superpelican12 on 2012-07-25
> 
If you want to learn how things work on the lowest level, then you need to learn as much C as possible.
Should I learn all the low level things? And therefore try to master C?

> 
C++ is better for a "general purpose" language.
Better than Python (as general purpose language)?

> 
There are so many languages because they all have strengths and  weaknesses. You should never restrict yourself to one language, you  should know as many of them as possible.
You should use whatever  language is best for the job that you are trying to do.
I understand. You wouldn't try to remove a nail with a knive, would you? ;)

> 
I think that a person with good understanding C/C++ can learn new  languages really quickly. A person with good understanding of Python (or  Java or C# or Ruby) will probably find C/C++ hard to learn.
So  you think it is better to stop learning Python now? And learn C/C++  first? So you mean it will be more difficult to learn C/C++ after  learning Python than just learning C/C++ straight away? 

I've  always read that it better to start with a simpler language like Python  or Ruby. Because a powerful and therefore unfortunately also difficult  language would distract the beginning programmer from actually learning  to program. It would cause the programmer to concentrate more on the  language itself and not on learning to programming/learn solving  programs. I'm not sure if this is true (so correct me if I'm wrong), but  this is what I've read...

EDIT: @3Miro I actually don't really know Python, I'm (beginning to) just learning it, the most difficult & long program I've written in Python is this:
```

#!/usr/bin/python3

import math
import random 

def answerisright():
 newquestion()
 answeriswrong()
 
def newquestion():
 a = random.randrange(1, 35, 1)
 b = random.randrange(1, 35, 1)
 print("Triangle side A =")
 print(a)
 print("Triangle side B =")
 print(b)
 print("Calculate triangle side C with the Pythagorean Theorem/A²+B²=C²") 
 global csquare_cpu
 csquare_cpu = (a ** 2)+(b ** 2)

def answeriswrong():
 usersanswer = input("Please enter the answer:")
 if usersanswer == "":
  print("You didn't answer anything!")
  answeriswrong()
 elif usersanswer[0:14] != "square root of":
  print("Invalid answer! Please try again.")
  answeriswrong() 
 else:
  csquare_user = usersanswer[15:20]
  csquare_user_int = int(csquare_user)
 
  if csquare_user_int == csquare_cpu:
   print("Good job! You answered the right answer!")
   answerisright()
  else:
   print("Wrong answer! Please, try again.")
   answeriswrong()

answerisright()

```
[https://sites.google.com/site/superpelicanprograms/products/pythagorean-python](https://sites.google.com/site/superpelicanprograms/products/pythagorean-python)
Also may I ask you to review some of my code? I'm not sure this is the best way to implement this program

---

### Post by CptPicard on 2012-07-25
IMO it is quite relevant indeed to the theme of what exactly lower-level languages deliver in terms of understanding to the higher-level language programmer, which is one of the things that was brought up. Those points are worth knowing to the OP-kind of poster.

I am quite interested in the ways programmers mentally model their problems and how the used language relates to that mental model. This is not to discourage learning of C (or C++, I dislike speaking of them as one and the same in these contexts, they're quite different), but really, just a perspective-issue for the OP to consider.

---

### Post by CptPicard on 2012-07-25
> **Superpelican12 said:**
> 
I've  always read that it better to start with a simpler language like Python  or Ruby. Because a powerful and therefore unfortunately also difficult  language would distract the beginning programmer from actually learning  to program.

This what I for one would say and suggest. Get comfortable in Python first, which will get you in the mindset and already give you most of the general understanding of what you'll need to know. In addition, it will introduce you to some interesting ideas such as proper higher-order functions rather easily. After Python, I'd say you're 80% of the way already, and you'll get there relatively painlessly and quickly.

Mind you, the concepts such language "power" and supposed necessarily increasing "difficulty" with power are somewhat nebulous concepts that we've been debating here for years. There is "complicatedness" (read: difficulty without benefit), there is "runtime speed", there is "expressiveness" (can do much and various things combining well-thought-out language concepts)... I am starting to believe that people just develop their feel for these things as they go along, and some end up stressing the abstraction and some the lower-level implementation.

Admittedly if I had to just "pick one" language that I'd have to use to the end of my days, it might be either C or C++, but that would be only because at some points I'd have to get closer to the metal. But, fortunately, I don't have to make that kind of a choice.

---

### Post by 3Miro on 2012-07-25
> **Superpelican12 said:**
> 
Better than Python (as general purpose language)?

C++ is a better general purpose language than C. Compared to Python, C++ has both advantages and disadvantages. Couple of years ago, it was the case that most programs in the Ubuntu repository were written in C++. I believe it is still the case, but I may be wrong.

> 
So  you think it is better to stop learning Python now? And learn C/C++  first? So you mean it will be more difficult to learn C/C++ after  learning Python than just learning C/C++ straight away? 

This is the argument that CptPicard was talking about. Some people prefer to go C -> C++ -> Python, others prefer Python -> C++ -> C. I went the first route and if I had to learn it again I would still start with C. However, other people don't think this is working for them ... may depend on the person.

I think that a good programmer should know C, C++ and Python. C/C++ will take longer to learn, but going form C/C++ to Python should be relatively easy. Python is probably easier to learn as a first language, but going to C/C++ will require an effort. You pick your path.

I guess you can try learning both languages at the same time too, I don't know how this would work.

---

### Post by 3Miro on 2012-07-25
> **Superpelican12 said:**
> 
```

#!/usr/bin/python3

import math
import random 

def answerisright():
 newquestion()
 answeriswrong()
 
def newquestion():
 a = random.randrange(1, 35, 1)
 b = random.randrange(1, 35, 1)
 print("Triangle side A =")
 print(a)
 print("Triangle side B =")
 print(b)
 print("Calculate triangle side C with the Pythagorean Theorem/A²+B²=C²") 
 global csquare_cpu
 csquare_cpu = (a ** 2)+(b ** 2)

def answeriswrong():
 usersanswer = input("Please enter the answer:")
 if usersanswer == "":
  print("You didn't answer anything!")
  answeriswrong()
 elif usersanswer[0:14] != "square root of":
  print("Invalid answer! Please try again.")
  answeriswrong() 
 else:
  csquare_user = usersanswer[15:20]
  csquare_user_int = int(csquare_user)
 
  if csquare_user_int == csquare_cpu:
   print("Good job! You answered the right answer!")
   answerisright()
  else:
   print("Wrong answer! Please, try again.")
   answeriswrong()

answerisright()

```
[https://sites.google.com/site/superpelicanprograms/products/pythagorean-python](https://sites.google.com/site/superpelicanprograms/products/pythagorean-python)
Also may I ask you to review some of my code? I'm not sure this is the best way to implement this program

Your program works, which is the most important thing at this point. Here are some pointers:

- avoid recursion (a function calling itself). Recursion can be very powerful, but Python has limitations on how many levels of recursion it can use. There is no need to use recursion if you can do it loops just as easily.

- name your functions with meaningful names so that other people can understand them. "answeriswrong" and "answeriswrong" were misleading names.

- global variables should also be avoided, unless absolutely necessary. Local variables are better to pass information from one function to the next. If you have a complex piece of code, local variables are easier to track.

- unless I had read your code, there was no way for me to know the format of the answer. If you want the user to enter something as specific as "square root of ", then you should let them know.

```
#!/usr/bin/python3

import math
import random 

def mainloop():
 while (True):
  squareOfAnswer = newquestion()
  testAnswer(squareOfAnswer) 
 
def newquestion():
 a = random.randrange(1, 35, 1)
 b = random.randrange(1, 35, 1)
 print("Triangle side A =")
 print(a)
 print("Triangle side B =")
 print(b)
 print("Calculate triangle side C with the Pythagorean Theorem/A²+B²=C²") 
 return (a ** 2)+(b ** 2)

def testAnswer( squareOfAnswer ):
 bRightAnswer = False
 while ( not bRightAnswer ):
  usersanswer = input("Please enter the answer:")
  if usersanswer == "":
   print("You didn't answer anything!")
  elif usersanswer[0:14] != "square root of":
   print("Invalid answer! Your answer should look like: \n square root of XXX \n where XXX is an integer.\n Please try again.")
  else:
   csquare_user = usersanswer[15:20]
   csquare_user_int = int(csquare_user)
 
   if csquare_user_int == squareOfAnswer:
    print("Good job! You answered the right answer!")
    bRightAnswer = True
   else:
    print("Wrong answer! Please, try again.")

mainloop()
```

---

### Post by trent.josephsen on 2012-07-25
> **3Miro said:**
> C++ is a better general purpose language than C.
> **3Miro said:**
> - avoid recursion (a function calling itself).

I strongly disapprove of both these statements.

---

### Post by Superpelican12 on 2012-07-25
I think I will just go on learning Python and use it as my general purpose language. Later on (when I need it) I'll learn plain C for the performance and low level stuff. 
Plain C also works with Cython (what I will probably be using for performance and low level)
I think that it will suit *me *better to start learning Python (3) as first language, because it will be easier to *just* get programming and actually exercise and program real software (the best way to learn things (especially in computing) seems to just do it).

> 
Your program works, which is the most important thing at this point.
Isn't learning a good coding style the most important thing for a beginner? If I teach myself bad habits and continue to use that style in my future (more complicated) programs...

> 
avoid recursion (a function calling itself). Recursion can be very  powerful, but Python has limitations on how many levels of recursion it  can use. There is no need to use recursion if you can do it loops just  as easily.
Yes, that's the main reason I said I was not sure if this was a good implementation. A friend of mine also just started learning Python. I had told him about my little script and he wrote his own implementation, which was based on a while loop. After he showed me his program, I began to doubt if my program was actually well written. His program looked so simple, everybody would immediately understand how it works. At the same time it'll take a while before someone would  understand my code. My program looked so cluttered compared to his.

> 
Name your functions with meaningful names so that other people can  understand them. "answeriswrong" and "answeriswrong" were misleading  names.
Yes I know, I were already thinking about renaming "answeriswrong", because it is a part of "answerisright", which makes it really confusing.

> 
Global variables should also be avoided, unless absolutely necessary.  Local variables are better to pass information from one function to the  next. If you have a complex piece of code, local variables are easier to  track.
I only used one global variable, but that was because it was absolutely necessary to let the program run. The interpreter was complaining, so I needed to make that variable global. I know that you should only use public classes and variables when needed. I don't fully understand your solution (to not using an integer). I don't fully understand what "return x" does. You didn't save the result of a**2 + b**2 or did you?
If you don't save it how can you access the result later on to check if the answer is right?

Please mind I'm just a beginner ;)

> 
Unless I had read your code, there was no way for me to know the format  of the answer. If you want the user to enter something as specific as  "square root of ", then you should let them know.
Yes I know, I already knew that ;). Therefore I distribute my program in a zip archive or tar.gz archive, which also includes a readme.txt file, which explains the user how to answer. You can download one of the archives from [https://sites.google.com/site/superpelicanprograms/products/pythagorean-python](https://sites.google.com/site/superpelicanprograms/products/pythagorean-python). 

> 
 Couple of years ago, it was the case that most programs in the Ubuntu  repository were written in C++. I believe it is still the case, but I  may be wrong.
To me seems Python is also one of the most popular languages for Ubuntu development and a lot of Ubuntu programs are written in it. I may also be wrong of course.

EDIT:
> **trent.josephsen said:**
> 
I strongly disapprove of both these statements.

Would you mind to explain why? The quoted post above on it's own doesn't really add something to this discussion IMHO. If you would explain why, that maybe helpful for others. Now it's more like "Well trent.josephsen's opinion is X and my opinion is Y. End of the story."
That doesn't really add something if you understand what I mean ;)
Of course I'm not a moderator and therefore I do not have the right to complain about your posts... And this is not an offense

---

### Post by 3Miro on 2012-07-25
> **Superpelican12 said:**
> 
Isn't learning a good coding style the most important thing for a beginner? If I teach myself bad habits and continue to use that style in my future (more complicated) programs...

"Style" is useful only if you can follow the logic of a program. If you cannot follow the logic and cannot get something working, then style is useless. I don't mean that you shouldn't be learning good style, I am just saying that the first step is get the basic idea of the programming logic.

> 
I only used one global variable, but that was because it was absolutely necessary to let the program run. The interpreter was complaining, so I needed to make that variable global. I know that you should only use public classes and variables when needed. I don't fully understand your solution (to not using an integer). I don't fully understand what "return x" does. You didn't save the result of a**2 + b**2 or did you?
If you don't save it how can you access the result later on to check if the answer is right?

Please mind I'm just a beginner ;)


"return (a ** 2)+(b ** 2)" takes the value of the expression and passes it back to the place in the code where "newquestion()" was called. "squareOfAnswer = newquestion()" executes "newquestion()" and then takes the returned value "(a ** 2)+(b ** 2)" and puts it in "squareOfAnswer". This is a much better way to communicate information from one function to the next.

> 
To me seems Python is also one of the most popular languages for Ubuntu development and a lot of Ubuntu programs are written in it. I may also be wrong of course.

Python may have an edge when it comes to the number of new programs that were written, however, older programs are mostly C++.

> 
Would you mind to explain why? 

Python has limitation on the number of recursion steps it can take, if a function calls itself too many times, the program will crash. There are some algorithms that are best implemented with recursion, there are languages like Lisp that are all about recursion, but recursion on Python should generally be avoided.

C++ was designed as an extension to C to make it more flexible and better suited for general purpose programming.

Although, trent.josephsen does make a really good argument.

---

### Post by Superpelican12 on 2012-07-25
> 
This is a much better way to communicate information from one function to the next.

Could you explain why this is a much better way? Because it isn't fully This is a much better way to communicate information from one function to the next.clear to me why.
If you say the statement "squareOfAnswer = newquestion()" first executes "newquestion()" it seems more efficient to me (and also so simpler) to just put the result in a variable. This way the computer doesn't have to run the whole statement just to determine what "squareOfAnswer" means. Also how do you let "newquestion()" return 2 integers (that need to be global)?

The "EDIT-part" of my last reply was actually meant for @trent.josephsen not for @3Miro ;)

---

### Post by 3Miro on 2012-07-25
> **Superpelican12 said:**
> Could you explain why this is a much better way? Because it isn't fully This is a much better way to communicate information from one function to the next.clear to me why.
If you say the statement "squareOfAnswer = newquestion()" first executes "newquestion()" it seems more efficient to me (and also so simpler) to just put the result in a variable. This way the computer doesn't have to run the whole statement just to determine what "squareOfAnswer" means. Also how do you let "newquestion()" return 2 integers (that need to be global)?


"squareOfAnswer = newquestion()" does the exact same thing as the case with global variable, the only difference is that the result is placed in squareOfAnswer, which is a local variable. Global variables are generally considered "bad style", anyone can read "squareOfAnswer = newquestion()" and figure out that the output of "newquestion()" is placed into squareOfAnswer, otherwise they have to peek inside of newquestion() to figure out where things are going. See this link that talks about functions and passing variables:

[http://www.penzilla.net/tutorials/python/functions/](http://www.penzilla.net/tutorials/python/functions/)

---

### Post by Superpelican12 on 2012-07-25
Why do global variables exist if you shouldn't use them?

 I'm still reading the webpage which the link in your last post links to. 

But  I still find it difficult to understand what a tuple is and what the  differences are between tuples and lists. Yes, lists are "mutable" and  use square brackets. Where tuples are "immutable" and use parentheses. I  also still don't fully understand what "mutable" and "immutable" mean.  Wikipedia says that it means that you can't change the content of an  immutable datatype after you declared it and assign a value to it for  the first time. I've read that strings are "immutable" in Python. But  how can strings be immutable if they're variables? You can change  strings with:
```

mystring1 = "Hello World!"
print(mystring1)
mystring1 = "Hello everybody!"
print(mystring1)

```
I  don't understand what tuples are and what's the benefit of them above  lists. And what "mutable" and "immutable" exactly mean...

---

### Post by juancarlospaco on 2012-07-25
Tuples are read-only lists.
Tuples are A LOT light weight than Lists, use less RAM memory.
Tuples do NOT use any kind of bracket or parentheses, try: 

```
myTuple = 1,2,3 
type(myTuple)
```

Strings can be immutable, if theyre variables, 
because they are a completely different thing.

```

# mystring1 variable points to inmutable "Hello World!" string
mystring1 = "Hello World!"  

# print a mutable variable pointing to an inmutable string
print(mystring1)  

# mystring1 variable gets re-pointed to ANOTHER inmutable "Hello everybody!" string
mystring1 = "Hello everybody!"  

# print a mutable variable pointing to an inmutable string
print(mystring1)  

```

Some things are created thinking on save memory and make program go faster, 
if i remember correctly on Python, a 4 Booleans fit on the same memory as 1 Float (both empty), a Float get calculated faster than a Integer, depends on the situation an Integer can be or can not be more precise than a Float, depends on the situation both do not work, and you need a Long type which precision dont have limit but the hardware resources to handle it and its slow, and theres even more types too...

---

### Post by trent.josephsen on 2012-07-25
> **Superpelican12 said:**
> Would you mind to explain why? The quoted post above on it's own doesn't really add something to this discussion IMHO. If you would explain why, that maybe helpful for others. Now it's more like "Well trent.josephsen's opinion is X and my opinion is Y. End of the story."

Yeah, you're right. I'll explain. For reference the statements were "C++ is a better general purpose language than C" and "avoid recursion", and I'm only picking on those because I think by and large 3Miro is giving good advice.

My beef is that both are unqualified statements that really can't be applied generically. Not that they're false -- they're too vague to have a truth value. Like curtains are better than bedsheets, or English is better than Latin.

I won't ask what it means for one general purpose language to be better than another because I think 3Miro probably meant a more specific type of "better".

As for avoiding recursion, I'll gladly agree that there are many things for which you shouldn't use recursion, and in this instance it does, in fact, cause a bug that an iterative solution would not have. But "avoid recursion" is a blanket statement that doesn't address the differences between the recursive solution and the iterative. I doubt anyone would try to traverse a file system using iteration; that's a good example of a problem for which recursion is (almost always) the right solution.

You'll eventually get a feel for when recursion is appropriate. There's not really a rule of thumb.

Actually, come to think of it, a blanket ban on global variables can cause the same kind of confusion, and apparently already has in this thread:

> **Superpelican12 said:**
> Why do global variables exist if you shouldn't use them?

Because there are some cases where you can use them effectively. They're useful for maintaining a global state. I can't think of a good example right now. What you used it for was passing a variable back from a function, which is not thread safe or easy to read.

Again, you'll eventually get a feel for this kind of thing. I've only been programming for 5 or 6 years so I'm not trying to pass myself off as an expert, either.

---

### Post by Superpelican12 on 2012-07-26
So that strings are immutable means I can't do this?:
> 
mystring1  = "Hello"
mystring1.append(" World!")
print(mystring1)

with as output:
[OUTPUT]
Hello World!
[/OUTPUT]
And only can completely overwrite strings, like:
```

mystring1 = "Hello"
print(mystring1)
mystring1 = "Hello World!"

```
[OUTPUT]
Hello World!
[/OUTPUT]
I'm now reading this webpage: [http://www.hetland.org/writing/instant-python.html](http://www.hetland.org/writing/instant-python.html)
Especially the parts on abstraction, tuples and immutable/mutable

---

### Post by Tony Flury on 2012-07-26
> **Superpelican12 said:**
> So that strings are immutable means I can't do this?:
```

mystring1 = "Hello"
mystring1.append(" World!")
print(mystring1) 

```
with as output:
[OUTPUT]
Hello World!
[/OUTPUT]
And only can completely overwrite strings, like:
```

mystring1 = "Hello"
print(mystring1)
mystring1 = "Hello World!"

```
[OUTPUT]
Hello World!
[/OUTPUT]
I'm now reading this webpage: [http://www.hetland.org/writing/instant-python.html](http://www.hetland.org/writing/instant-python.html)
Especially the parts on abstraction, tuples and immutable/mutable

Immutable means that the string data in memory is not changable. what your code fragment is doing with the append - if append exists on strings (is append a Python 3 feature) is that it creates a new string, and leaves the old one behind : 
```

mys1 = "Hello"
mys2 = mys1
mys1= mys1 + " World"
print mys1, mys2

Hello World Hello

```
i.e. you can't change the content of the string - and the origial string still exists (because we assigned mys2 to point to it too). If could look at the addresses in memory of the object they are very different.

Same with tuples :

```

myt1 = 0,1,2
myt2 = myt1
myt1[1]=4 # Wrong - will generate an error
myt1 = myt1[0],4,myt1[2] # this will work - 
print myt1,myt2

Output : 
(0, 4, 2) (0, 1, 2)

```

---

### Post by Superpelican12 on 2012-07-26
So this:
```

a = "Hello World!"
b = a

```
actually means that "b=a" doesn't copy the value of a and puts it in to b, but actually "b" only points to the current value of b? But how can it be that if I do this:
```

abc = "a", "b", "c"
a = abc[0]
print(a)
Output:
a
abc  = "d", "b", "c"
print(a)
Output:
a

```
the second time printing the value of a still gives "a" as output? While you said that if "copy" the value of a variable it actually only points to the current value of the other variable.

Maybe learning C++ (which means mastering it's manual memory management and pointers) is easier than Python and it's immutable tuples :(

---

### Post by juancarlospaco on 2012-07-26
Look at the id() method, it will explain a lot.

**For every modification you can do to an immutable you are just creating another thing in memory.**

Variables can point to anything.

---

### Post by Tony Flury on 2012-07-26
> **Superpelican12 said:**
> So this:
```

a = "Hello World!"
b = a

```
actually means that "b=a" doesn't copy the value of a and puts it in to b, but actually "b" only points to the current value of b? 

Strictly speaking b is made to point to same place that a points to - but it is a one off association. The string "Hello World!" is held in memory and both a and b point to it. After that b does not "remember" that it is a copy of a, it remembers it is pointing to "Hello World!". so you can change what a points to - another string, an integer, whatever, and b will still be "Hello World!"

> 
But how can it be that if I do this:
```

abc = "a", "b", "c"
a = abc[0]
print(a)
Output:
a
abc  = "d", "b", "c"
print(a)
Output:
a

```
the second time printing the value of a still gives "a" as output? While you said that if "copy" the value of a variable it actually only points to the current value of the other variable.

Maybe learning C++ (which means mastering it's manual memory management and pointers) is easier than Python and it's immutable tuples :(

This is correct behaviour if you think about it.
a=abc[0] makes the variable a point to the same data that a[0] CURRENTLY points to - i.e. "a". The variable a just "points" to the "a" string, it does not keep track that this was an element of abc.

The fact that you go on to change what abc[0] points does does not change the fact that a still points to "a"

Using the id function to look at the addresses : 
```

>>> abc = "a", "b", "c"
>>> a = abc[0]
>>> print id(a), id(abc), id(abc[0])
3078314432 3078511068 3078314432
>>> abc = "d","e","f"
>>> print id(a), id(abc), id(abc[0])
3078314432 3078511668 3078767456

```
as you see the id (address) which abc[0] refers to has changed, but the address which a refers to hasn't. 

just because you set a variable to a value from an array doesn't mean that the variable changes when you change the array - the same happens in C and C++.

---

### Post by Superpelican12 on 2012-07-26
Thanks all now I really understand everything! :D
But how can immutable types safe memory if when you change
a variable it makes a new object in the memory?  Doesn't this extremely increase
the RAM usage? All those unused objects will be in the memory until the GC
removes them...

I've read several times that mutable objects use more
memory. How can they use more memory if when they are the existing object
is only edited? To me with my current knowledge this seems much more efficient.

---

### Post by trent.josephsen on 2012-07-26
> **Superpelican12 said:**
> Thanks all now I really understand everything! :D
But how can immutable types safe memory if when you change
a variable it makes a new object in the memory?  Doesn't this extremely increase
the RAM usage? All those unused objects will be in the memory until the GC
removes them...

I've read several times that mutable objects use more
memory. How can they use more memory if when they are the existing object
is only edited? To me with my current knowledge this seems much more efficient.
Simple. Consider this array:

```
v = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
```

v[0] through v[9] can all refer to the same immutable object. You can change (say) v[9] to refer to a different object, but the other nine elements still refer to the same immutable zero. If ints were mutable, you would have to create 10 objects to store 10 different zeros that all act exactly the same.

In fact, you can verify this with Python's "is" operator, which tells you if two references refer to the same object:

```
>>> v     
[0, 0, 0, 0, 0, 0, 0, 0, 0, 1]
>>> for i in range(len(v)):
...     print('v[{}] ({}): {}'.format(i, v[i], v[i] is v[0]))
... 
v[0] (0): True
v[1] (0): True
v[2] (0): True
v[3] (0): True
v[4] (0): True
v[5] (0): True
v[6] (0): True
v[7] (0): True
v[8] (0): True
v[9] (1): False
```

This shows that all the zeros in v refer to the same object as v[0], while the 1 refers to a different object.

Python re-uses some immutable objects automatically, so even if you come to the same value by different means, Python often won't create a new object:

```
>>> 3 - 5 is -1 * 2
True
>>> 'hell' + 'o' is 'h' + 'ello'
True
```

It's not perfect, though, especially if you go beyond small integers and short strings:

```
>>> 1.5 is 3 / 2
False
>>> 1.5 == 3 / 2
True
>>> 'foobarbazzzzzzzzzzzzzzzzzzzzz' is 'foo' + 'bar' + 'baz' + 20 * 'z'
False
>>> 'foobarbazzzzzzzzzzzzzzzzzzzzz' == 'foo' + 'bar' + 'baz' + 20 * 'z'
True
```

You can use the sys.getrefcount function to see how many references there are to a given object. Many small integers and certain strings will have a high refcount from the beginning, since Python uses them internally.

```
>>> import sys
>>> sys.getrefcount(0)
406
>>> sys.getrefcount('__name__')
121
```

You can even see the refcount change as you create and delete references to an object:

```
>>> x = 'foobar' # create an object and one reference to it
>>> sys.getrefcount(x) # passing x to sysrefcount creates another reference
2
>>> y = x # creating a new reference to the same object
>>> sys.getrefcount(x)
3
>>> v = list()
>>> for i in range(100): # create 100 new references to the same object
...     v.append(x)
... 
>>> sys.getrefcount(x)
103
>>> del y # delete a reference
>>> sys.getrefcount(x)
102
>>> del v # delete 100 references at once
>>> sys.getrefcount(x)
2
```

I've probably just made this topic about a thousand times more complicated than it needs to be, but hey, you did ask :) Hope it helps at least a little bit.

A word of encouragement, though -- this is a complex topic and you shouldn't feel pressured to fully understand it right away. In my high school programming class (which was Java-based) we didn't discuss this until second semester and there were still people who didn't get it. Most of the time it's not important to distinguish between variables, references, and objects; the underlying model acts how you expect it to most of the time. You wouldn't expect "x = 0; y = 0; y = 1" to set x = 1, would you?

---

### Post by NilPointer on 2012-07-27
> Python has limitation on the number of recursion steps it can take, if a function calls itself too many times, the program will crash. There are some algorithms that are best implemented with recursion, there are languages like Lisp that are all about recursion, but recursion on Python should generally be avoided.

Yes, it has default interpreter stack size of 1000. But...

> sys.getrecursionlimit()

Return the current value of the recursion limit, the maximum depth of the Python interpreter stack. This limit prevents infinite recursion from causing an overflow of the C stack and crashing Python. It can be set by setrecursionlimit().

...apparently, this is just precaution from C stack overflow and can be changed.

---

### Post by Superpelican12 on 2012-07-27
But how do mutable objects work?

---

### Post by Tony Flury on 2012-07-27
> **Superpelican12 said:**
> But how do mutable objects work?

Take the most obvious item - a list. I am not sure how exactly lists are implemented in python, but i would imagine they might be a linked list  - so evey item in the list is effectively an object, and each item has links to the next and previous objects. These list entry items don't hold the data, they hold a reference to an object (say an inteeger object, or a string object, or maybe a custom object) (remember that in python all values are objects too (as shown by trent.josephsen))

So if you want to add something to a python list, internally just creating a new list enty object, point it at the object holding the value you are adding, and attach the list entry object to the relevant part of the list. 

If You want to change the value of an item in the list : you take your list entry and point it to an object containig the new value, and the ref count of the old value will decrease by one.

Similar things will happen with Dictionaries etc.

---

### Post by Tony Flury on 2012-07-27
One way of looking at mutable vs immutable : 

it makes sense to do this : 
```

a = "Hello"
a ="World"

```

but not this : 
```

"Hello" = "World"

```
The variable a is mutable, but the string it points to is not.

I do notice that this discussion has strayed a long way from the OP original intention - maybe it is time (belatedly) to start a new thread ?

---

### Post by NilPointer on 2012-07-27
> **Tony Flury said:**
> i would imagine they might be a linked list

Not exactly. From what I understand, python lists are arrays of pointers. First, linked lists have too much overhead, since you have to iterate over all elements just to find one at certain index. Since lists are one of Python's key features, it wouldn't be good if they had heavy perfomance impact. With list of pointers we have array with fixed-sized pointers and getting required pointer is very easy and fast.

Also, with each new element (no matter what type and size), list grows by 4 bytes (checked via sys.getsizeof()). Which indicates that lists don't actually store data, they just hold 4 byte pointers for their elements.

---

### Post by Tony Flury on 2012-07-27
> **NilPointer said:**
> Not exactly. From what I understand, python lists are arrays of pointers. First, linked lists have too much overhead, since you have to iterate over all elements just to find one at certain index. Since lists are one of Python's key features, it wouldn't be good if they had heavy perfomance impact. With list of pointers we have array with fixed-sized pointers.

Also, with each new element (no matter what type and size), list grows by 4 bytes (checked via sys.getsizeof()). Which indicates that lists don't actually store data, they just hold 4 byte pointers for their elements.

Good point - arrays would be more efficient. I agree that they only store a pointer to the actual value.

---

### Post by Superpelican12 on 2012-07-29
Hello everyone,

I think I currently understand the tuples and  immutable vs mutable stuff some I'm moving on again in the official  Python 3k tutorial ;). 

I have only one question left about what mutable exactly means, does that lists are mutable mean that I can use *.append*  on the lists (the arrays of pointers), without the list actually  creating a new array of pointers in the memory? I did this in the  interactive Python 3k shell:
```

>>> abc = ["a", "b", "c"]

```
and this
```

id(abc)

```
returned: 17345136
and when I did this:
```

abc.append("d")
id(abc)

```
still returned: 17345136. So I guess what I stated above is right?

---

### Post by Some Penguin on 2012-07-29
Pretty much.  The reference remains the same; the referent has changed... which means, for instance, every other variable that is merely a reference to the same referent will have access to the changed value (well, modulo possible threading issues.  I'm not terribly familiar with Python's implementation of multithreading.  But I can tell you that there exist languages for which multiple variables nominally referring to the same object can, in fact, perceive different referents if the references are in different threads and there's an absence of locking or the like -- Java, for instance).

With an immutable object, you can only change what a variable refers to by making it refer to an entirely different object.  Anything that still refers to the old referent still sees it what it was, because THAT hasn't changed.

With a mutable object, you can change the referent itself.  This  is often more convenient and can prevent the gratuitous creation of large numbers of objects (it would be grossly inefficient to manage a massive, immutable by cloning it each time you wanted to change a single value!), but means that there's more ways to shoot yourself in the foot.  For instance, it's generally a bad idea to use the full state of mutable objects as hash keys... (see [http://stackoverflow.com/questions/7842049/are-mutable-hashmap-keys-a-dangerous-practice]("http://stackoverflow.com/questions/7842049/are-mutable-hashmap-keys-a-dangerous-practice") for some commentary).

---

### Post by Superpelican12 on 2012-07-30
But how can this happen then?:
```

>>> abc = ["a", "b", "c"]
>>> id(abc)
30722672
>>> abc = ["a", "b", "c", "d"]
>>> id(abc)
30730504

```
I thought lists where mutable?

---

### Post by Some Penguin on 2012-07-30
> **Superpelican12 said:**
> But how can this happen then?:
```

>>> abc = ["a", "b", "c"]
>>> id(abc)
30722672
>>> abc = ["a", "b", "c", "d"]
>>> id(abc)
30730504

```
I thought lists where mutable?

*sigh*  Changing the reference to point to a new list != changing the list it referred to.

'abc' isn't the list.  It's a reference to the list.  You're free to make it refer to a completely different list.  You're also free to modify the list that 'abc' refers to.

---

### Post by trent.josephsen on 2012-07-30
> **Some Penguin said:**
> 'abc' isn't the list.  It's a reference to the list.

QFT. **Variables are references**. I think this is a big part of OP's confusion.

---

### Post by StephenF on 2012-07-31
> **Some Penguin said:**
> You're free to make it refer to a completely different list.
Or something that isn't even a list.

---

### Post by Trixar_za on 2012-08-02
Why not give [Nimrod]("http://nimrod-code.org/") or Vala's Genie a go. Both fit your requirements (more or less). Personally I prefer Nimrod myself :P

---

### Post by thek3nger on 2012-08-04
Cython is a great example of python-like language that can be compiled in binary code with great performance boos (100-1000 times faster for CPU-intensive application).

However the [Cython FAQ]("http://wiki.cython.org/FAQ") answer in details to your initial question. :)

You can also take a look to Genie. :)

---

### Post by Superpelican12 on 2012-08-04
Thanks everyone for all the help. I'll sure look at Vala/Genie some time. And if I ever need performance I'll sure learn Cython. 

I recently received the book "Beginning Python, using Python 2.6 and Python 3.1" by James Payne. And I'm currently reading that. I haven't read the full book (still at page 73 of the 548 :D ) but so far I really like to book. It teaches you the absolute basic things and at the end you find yourself doing very interesting things. As soon it' s done teaching the basics, it starts teaching you very different, interesting things. Like GUI programming with Tkinter, using XML, accessing databases, text processing, building modules, network programming, extension programming with C and also the real object oriented part. I'm currently still at the rather boring basics part. So haven't read the more interesting parts yet...

I currently have only one question left: when I'm done reading the book I want to start GUI programming. Tkinter seems to be fine for little programs (and I therefore probably will use it for little stuff), but it looks awful and for bigger programs I would like to use either GTK or Qt. However I can't choose between using GTK3 (PyGObject/PyGI) and Qt (either PySide or PyQt4). The Qt bindings both have a really clean syntax and I prefer the signal/slots (Qt) mechanism over the signal/handler mechanism (GTK(3)). Also Qt seems to be much more than only a GUI library. It is really feature full (I see that as a pro). But GTK3/PyGObject also seems to have a decent syntax and a lot of programs are already written in GTK. Also GTK has better compatibility with Ubuntu and XFCE/LXDE/Gnome/Unity. While using Qt pulls in all the Qt stuff.

Also if I decide to use Qt, I have to decide whether to stick with PyQt4 or use PySide. I actually prefer PySide (it has a nice documentation and is much closer to Qt itself. Because it is developed by Nokia/Qt them self.). But PySide has a higher memory usage than PyQt and PyGObject. For example a simple Hello World program implemented in PySide uses 18 mb of memory (according to Gnome Sys mon.)! Exactly the same program using PyQt4 uses only 11 mb. Another simple program using GTK3 uses the same as PyQt. As I'm also going to develop for mobile platforms in the future (Jolla OS/Meego which uses Qt - [http://www.engadget.com/2012/07/07/jolla-promises-meego-will-live-on-plans-new-smartphone/](http://www.engadget.com/2012/07/07/jolla-promises-meego-will-live-on-plans-new-smartphone/) and [https://en.wikipedia.org/wiki/Jolla](https://en.wikipedia.org/wiki/Jolla)) this (the high memory usage) could become a problem. Also I'm not sure whether the Jolla Dev environment will support PyQt or PySide. PySide seems the most logical to me (as it's closer to Qt itself, while PyQt is created and maintained by Riverbank Ltd.).

Which of the bindings/GUI toolkits should I choose. Qt has a lot of pros for me (signal/slots, future dev for Jolla OS (my next phone will probably be a Jolla Linux phone), nice syntax, very feature full). While GTK has been used more for Ubuntu and other Linux software. Most DEs and therefore also there apps are written in GTK...

Which one should I choose? PyGObject, PyQt4 or PySide?

---

### Post by Tony Flury on 2012-08-04
> **Superpelican12 said:**
> 

..... cut for brevity.....

Which one should I choose? PyGObject, PyQt4 or PySide?

Can i suggest you start a new thread for this question - as it is no longer really related to the original thread or the title ?

---

### Post by Superpelican12 on 2012-08-04
Yes I will create a new thread. However I'm a bit scared of creating a new thread, when the discussion changes. I did create a new thread on some other forum (not on Ubuntu Forums) and they didn't really appreciate that I created a new thread because of this argument.

I agree with you that it is a better idea to start a new thread.

---

