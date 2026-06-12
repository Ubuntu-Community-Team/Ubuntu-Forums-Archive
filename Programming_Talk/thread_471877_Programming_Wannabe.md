---
title: "Programming Wannabe"
date: 2007-06-12
forum: Programming Talk
---

### Post by Sethalos on 2007-06-12
Greetings,

I figured this would be an excellent place to post a question.

I am a Network Engineer with Windows, I have over 25+ certifications as for as MS, Cisco, Oracle, CompTIA, and CISSP. I'm a relative noob to Linux (2 months) however in that time I have completely switched over. I run Windows only through VirtualBox now and use it only when I absolutely have to. So I'm also in the process of learning the Linux environment.

Now, I'm looking to branch out and add some development experience. I'd like some advice on what would be a good language to start. I'm not looking to build apps or any high end programming as that. More doing server scripting, web developement, OS batch scripting...etc.

I have been considering Perl, PHP, VBscript, Java.

I have absolutely no background in programming, and would need to start at the very bottom of the learning ladder.

I would reallllly appreciate some advice from those of you programming gurus out there.

Seth

---

### Post by LaRoza on 2007-06-12
Learning Python first would be good, look at this thread:

[http://ubuntuforums.org/showthread.php?t=255970](http://ubuntuforums.org/showthread.php?t=255970)

Python is powerful, useful, and easy to learn.

You should also look into C++, this is an excellent tutorial:

[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

Python is interpreted, so you won't need to compile, C++ must be compiled.

There are thousands of languages but these are major ones that are useful to know:

C++
JAVA
Python
Perl
Ruby

And the web languages,
ECMAScript
PHP

I'm sure people can make cases for learning one language or another, but you have to start somewhere. Python would be a good place to start, plus, the interpreter is already on Linux in almost every distro.

Ready to start? [http://en.wikibooks.org/wiki/Non-Programmer's_Tutorial_for_Python/Contents]("http://en.wikibooks.org/wiki/Non-Programmer's_Tutorial_for_Python/Contents")

---

### Post by Sethalos on 2007-06-12
Wow, thanks very much for that.

Python seems to be a good place to start as any then. I have already begun the tutorials.

Just as a follow up question though.  Having learned one language, is it a very big step to interpret others, say Java or Perl?  I'm of the understanding that if I learn one the others will be much easier to learn. Or are they completely different with regards to syntax and form?

Thanks

Seth

---

### Post by LaRoza on 2007-06-12
To answer your questions: yes

The languages are all different, but all have very common elements. For example, of all the languages I listed, that I know have a "while" loop. 

in Python:
```

while x<10:
    print x
    +(+x)

```
in C++:
```

#include <iostream>
int main()
{
   int x=0;
   while(x<10)
   {
      std::cout<< x<<std::endl
      x++
   }
   return 0;
}

```
Both will do exactly the same thing, printing:
> 
0
1
2
3
4
5
6
7
8
9

On the console window, but they do it with different syntax.

So, learning one language makes it easier to learn others, for someone who first learned C++, Python is extremely easy to learn, for someone who learns Python first, C++ will be easier to learn because all the concepts will not be foreign except for a few things.

I personally study more than one language at a time, I find it helpful. The more you learn, the faster you learn. (I'm sure you level out at some point, but by then, you'll be knowledgable)

---

### Post by ruy_lopez on 2007-06-12
As a network engineer, you might prefer looking at C programming. While you can do socket programming with Python, most of the command line network tools are written using C, for good reason. 
 
for general introduction to C: Kernighan & Richie's *The C programming language* (Prentice Hall). 
for socket programming, Richard Stevens' *Unix Network Programming* (Addison-Wesley).

Another reason to study C, a lot of other languages borrow many of C's features.

---

### Post by Shocm on 2007-06-12
My .02 worth 

Web Development - PHP or Rails (a ruby framework)

Server scripting / OS batch scripting - Python, Ruby, or Perl (old school) 

Perl and PHP are very similar. Once you learn one its not too hard to pick up the other. Python may be the easiest one to learn from scratch. To me its a very "naturally spoken" programming language. All those languages have very large and active communities which can be important when looking for help on something. 

Enjoy.

---

### Post by LaRoza on 2007-06-12
^ Good advice, but it doesn't really matter what language you start with, once you learn basic programming concepts, learning another language is not as difficult. So learning Python, then C/C++ is beneficial.

No language that is used is completely different from the others, C++ and Python and Java have very big differences, but are similar in a way that facilitates learning them all.

---

### Post by Sethalos on 2007-06-12
Thank you all very much for your advice. I believe I will start with Python and set my goals there. I will also review PERL while I can.

I'm sure you'll see more of me as time passes here, lol.

Seth

---

### Post by LaRoza on 2007-06-12
Hopefully, you'll see more of us. :)

---

### Post by Hendrixski on 2007-06-12
It honestly does not matter which programming language you start with, or which editor you use.  It matters that you do it.  People will tell you "eewww, python" or "java is evil".  whatever.  they don't know what they're talking about.  There's no *wrong* language... except maybe Visual Basic  ... J/K

If you have Oracle certifications then you know SQL... so you know at least one programming language.  You know how logical operators and loops and all that stuff works.  :-)  Learning a new language is easier and easier the more you know.

Developing for open source projects is more fun than any video game you can ever play.  If you want to start contrinbuting to Ubuntu there are TONS of avenues available that help lower the barrier of entry.  There's lots of great documentation and lots of helpful friendly people.

welcome to the community!

---

### Post by LaRoza on 2007-06-12
> **Hendrixski said:**
> It honestly does not matter which programming language you start with, or which editor you use.  It matters that you do it.  People will tell you "eewww, python" or "java is evil".  whatever.  they don't know what they're talking about.  There's no *wrong* language... except maybe Visual Basic  ... J/K


:)

---

### Post by Hendrixski on 2007-06-12
> **LaRoza said:**
> To answer your questions: yes

The languages are all different, but all have very common elements. For example, of all the languages I listed, that I know have a "while" loop. 

in Python:
```

while x<10:
    print x
    +(+x)

```
in C++:
```

#include <iostream>
int main()
{
   int x=0;
   while(x<10)
   {
      std::cout<< x<<std::endl
      x++
   }
   return 0;
}

```
Both will do exactly the same thing, printing:

On the console window, but they do it with different syntax.

So, learning one language makes it easier to learn others, for someone who first learned C++, Python is extremely easy to learn, for someone who learns Python first, C++ will be easier to learn because all the concepts will not be foreign except for a few things.

I personally study more than one language at a time, I find it helpful. The more you learn, the faster you learn. (I'm sure you level out at some point, but by then, you'll be knowledgable)



you would want a for loop for that in C++
```

for(int i = 0; i < 10; i++){
  cout<< i << endl;
}

```

---

### Post by LaRoza on 2007-06-12
I know, but I was demonstrating a while loop. I should have just done a simple "Hello world" with C++, JAVA, and Python. 

Actually, I almost did use a for loop, but I had already done the Python code with a while loop.

---

