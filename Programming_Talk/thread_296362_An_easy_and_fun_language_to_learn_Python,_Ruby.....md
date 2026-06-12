---
title: "An easy and fun language to learn? Python, Ruby....?"
date: 2006-11-09
forum: Programming Talk
---

### Post by confusco on 2006-11-09
I want to learn some programming.

I want a fun language I can put to use quickly writing as little code as possible or wasting time. So I've heard good things about Python and Ruby. Ruby's philosophy about using the computer, not the computer using YOU is neat :KS 

Which should I go with for a first language? Python or Ruby? What are the main differences? Is there another language I should consider?

---

### Post by skymt on 2006-11-09
You want a fun language? Try learning Ruby with [this (poignant) guide](http://poignantguide.net/ruby/). It's definitely the funniest programming book I've ever read, and it explains the concepts very well.

---

### Post by Choad on 2006-11-09
totally depends what you want to do

if you wanted to make a game, a database app, a console app etc. the advice would be different

---

### Post by confusco on 2006-11-09
General purpose, nothing advanced or particular. So what about Python vs Ruby

---

### Post by Choad on 2006-11-09
meh, i would suggest c# because its a wonderful language. very similar to java, which in turn is none too dis-similar to c/++ so you learn 4 for the price of 1 ;)

out of python and ruby, i have only tried python and its quite cool, but really wierd compared to most other languages. it's white-space sensitive for a start. thats something you hardly ever find. and yet it is very weakly-typed... which is generally not a good way to learn programming

having said that, it is bloody easy :D

---

### Post by Tomosaur on 2006-11-09
Python is great if you don't want to find yourself reading manuals and hunting down obscure web pages, but it probably won't prepare you for any of the 'more powerful' languages if you decide to take it further, since it's quite different.

---

### Post by confusco on 2006-11-09
> **Tomosaur said:**
> but it probably won't prepare you for any of the 'more powerful' languages if you decide to take it further, since it's quite different.


Why?

---

### Post by skymt on 2006-11-09
Python will actually do a very good job of teaching the basics. It has a little of everything: object-orientation, procedural programming, functional programming, and other buzzwords. Concepts you learn in Python transfer very well to other languages.

If you decide to start with Java, then you learn Java. If you choose C++, you learn C++. If you learn Python (or Ruby), you learn programming. (My opinion only, blah, blah, disclaimer.)

That's especially true if you use the Poignant Guide I linked to earlier. It focuses on the conceptual side of OO programming, which will come in handy for almost any language.

---

### Post by Choad on 2006-11-09
> **confusco said:**
> Why?
like i said, weak type casting and white-spcae sensitive, and also the syntax if very different

heres an example

c++ code
```

int a, b;
a = 1;
b = 1;
if (a == b) {
    do_something();
    b += 1;
    }
for (int i = 0; i < 5; i++) {
    cout < i;
    }

```

c# code
```

int a, b;
a = 1;
b = 1;
if (a == b) {
    do_something();
    b += 1;
    }
for (int i = 0; i < 5; i++) {
    Console.WriteLine(i);
    }

```

java code
```

int a, b;
a = 1;
b = 1;
if (a == b) {
    do_something();
    b += 1;
    }
for (int i = 0; i < 5; i++) {
    System.out.println(i);
    }

```
(i probably did this wrong, havent actually done much java)

python code
```

a = 1
b = 1
if a==b:
    do_something()
    b = b+1
for i in range(6):
    print i

```

---

### Post by confusco on 2006-11-09
> **skymt said:**
> 

If you decide to start with Java, then you learn Java. If you choose C++, you learn C++. If you learn Python (or Ruby), you learn programming. (My opinion only, blah, blah, disclaimer.)


My friend said exactly the same thing about Ruby.

---

### Post by skymt on 2006-11-09
> **Choad said:**
> like i said, weak type casting and white-spcae sensitive, and also the syntax if very different

Actually, no. Python uses dynamic, strong typing. See [Wikipedia](http://en.wikipedia.org/wiki/Python_%28programming_language%29#Type_system) for details. Syntax changes from language to language anyway. Concepts are the most important thing for a beginner to learn.

Also, Python is a major language. Not only is it used heavily throughout Ubuntu, it's also used internally at Google, ILM and NASA ([among others](http://www.python.org/about/success/)).

---

### Post by Choad on 2006-11-09
ok, well i got my terminology wrong

what i meant was that in python there is no such thing as an integer or a single or a double per se. it will convert between them for you. 

its a real bitch having to go from that to static typing in many other languages. and im not saying python is bad in any way! its great. i just dont think it teaches such great habits

how many colleges/universities teach you in python? how many in java/c(++/#)

in fairness my college taught me visual basic which is a big old pile of crap :S but my uni teaches me c# and later on java and c++

---

### Post by Engnome on 2006-11-09
All the advice I can give is don't start with a language that doesn't have require you to convert integers to char and all that. It should also have a garbage collector. You will very soon get bored if you start out with those kind of languages, especially if you only want to have fun. I'm sure ruby, python and perl are all great to start out with. Give each language an hour or two and then come back to the one you like the most.

> **Choad said:**
> 
how many colleges/universities teach you in python? how many in java/c(++/#)


We actually had PHP in our first term, odd choice. After that ended I wasn't really sure what to try next so I tried a few (python perl java) and simple took what I liked. (perl)

---

### Post by confusco on 2006-11-09
> **Engnome said:**
> All the advice I can give is don't start with a language that doesn't have require you to convert integers to char and all that. It should also have a garbage collector. You will very soon get bored if you start out with those kind of languages, especially if you only want to have fun. 

I don't know, if you messed up on your writing, but it doesn't make sense to me, or I can't understand. Can you restate that in other words? So does Ruby require you to convert integers to char and "all that" or no?

What languages are "those kind of languages" that I'll get bored with?

---

### Post by SoloSalsa on 2006-11-09
Yo Choad, that was great.  I've never actively looked for programing opinions, but I've always looked for comparisons.  I've learned a week of C++, and am taking a year of Java now.  People often speak of their favorites, or just say ease of use, but never say useful things or feature comparison, annoyance comparing, syntax intuitiveness, etc.  But your simple code boxes were beautiful.

---

### Post by daniel of sarnia on 2006-11-09
> **Choad said:**
> ok, well i got my terminology wrong

what i meant was that in python there is no such thing as an integer or a single or a double per se. it will convert between them for you. 

its a real bitch having to go from that to static typing in many other languages. and im not saying python is bad in any way! its great. i just dont think it teaches such great habits

how many colleges/universities teach you in python? how many in java/c(++/#)

in fairness my college taught me visual basic which is a big old pile of crap :S but my uni teaches me c# and later on java and c++

I would not pick a language because a school uses, look at what's being used in the real world, ubuntu dose most all of it's developmint in python. I don't even use python that much mostly I work in C++ now (although I vary much like it). What bothers me though is people that complain about it's white space, that is the way everyone should code weather it's sensitive to white space or not. In my school, coding in C++ or java, if we don't use white space to make are code as easy to read as possable we loses marks. Hell my teacher won't give over 50% on anything that is not indented and using white space nicely. I agree with her, try to maintain a thousand lines of mess long after it was first written.

Python's a grate starting point, I don't really like ruby because everthing has to be an object from what I understand. So it sometimes a longer to do really simple things.

I also like C# but I have not given it a hard look and I don't really see an advantage to using it over c++ and python together.

I hate java, it's just not for me. It does not work how I think, that's just a personal thing. What bugs me is that you wright about the same amount of code if you had done it in c++, only it goes slower. I just plain don't like using it. But hay you might, give it a try and see if you do. 

I still recommend python as the "funniest" though. It dose after all get its name from Monty Python's Flying Circus. ;)

---

### Post by Jessehk on 2006-11-09
If you want to learn a fun language for the sheer joy of it, then I would suggest Python.

 I say that as somebody who likes Ruby, but feels it is becoming far too "write-only": code is easily written and read with difficulty. I feel that there are too many clever ways of doing something that prevent a program's purpose from being clear. Metaclasses and a variety of "hacks" in Ruby take the place of clear intentions and readable code in Python.

---

### Post by reynoldlariza on 2006-11-09
python?! ehehehehe...
eheheheh python!?

---

### Post by confusco on 2006-11-10
> **Jessehk said:**
> If you want to learn a fun language for the sheer joy of it, then I would suggest Python.

 I say that as somebody who likes Ruby, but feels it is becoming far too "write-only": code is easily written and read with difficulty. I feel that there are too many clever ways of doing something that prevent a program's purpose from being clear. Metaclasses and a variety of "hacks" in Ruby take the place of clear intentions and readable code in Python.

Very interesting. What do others think?

---

### Post by ghostdog74 on 2006-11-10
> **confusco said:**
> 
Which should I go with for a first language? Python or Ruby? What are the main differences? Is there another language I should consider?
Learn both. And you will know the differences. Choose the one that you like. Then after that maybe choose and learn C#. AFter that compare against the one you liked. Choose the better one. Continue this process to reach the one language that you liked MOST.:-D

---

### Post by Magnes on 2006-11-10
I think C++ is worth learning. Although it's not as easy as others.

---

### Post by Choad on 2006-11-10
i think this thread demonstrates well that every lnguage has plenty of fans, its down to personal taste and *what you need to get done*

you certainly couldnt have written linux in python, because it is interpreted and the interpreter runs on top of the os (linux)

but deluge wouldnt be being developed so rapidly if it was done in c/++ i dont think. i dunno. each has advantages

---

### Post by Engnome on 2006-11-10
> **confusco said:**
> I don't know, if you messed up on your writing, but it doesn't make sense to me, or I can't understand. Can you restate that in other words? So does Ruby require you to convert integers to char and "all that" or no?

What languages are "those kind of languages" that I'll get bored with?

ops yeah that is a typo :oops: (english is not my native language)

What I meant is of course that ruby, perl and python are nice to the programmer and that they don't require you to learn so much in the beginning but lets you do some real programs without as much hassle as c/c++, java and c#

---

### Post by confusco on 2006-11-10
Gotcha. I'm reading the Poignant Ruby guide now.

---

### Post by skeeterbug on 2006-11-10
> **Jessehk said:**
> If you want to learn a fun language for the sheer joy of it, then I would suggest Python.

 I say that as somebody who likes Ruby, but feels it is becoming far too "write-only": code is easily written and read with difficulty. I feel that there are too many clever ways of doing something that prevent a program's purpose from being clear. Metaclasses and a variety of "hacks" in Ruby take the place of clear intentions and readable code in Python.

Really? What exactly are the hacks in Ruby?

---

### Post by skymt on 2006-11-10
> **confusco said:**
> Gotcha. I'm reading the Poignant Ruby guide now.

Great! If you want to learn Python too, check out [How to Think Like a Computer Scientist](http://www.ibiblio.org/obp/thinkCSpy/), the best free Python book I've found. Ruby's my favorite language, but sometimes Python is the better language for the job.

---

### Post by deanlinkous on 2006-11-10
c

---

### Post by Ubuntist on 2006-11-10
You wouldn't go wrong with either Python or Ruby.  They're both fun and powerful too.  But let me put in a word for Scheme, which is very flexible, elegant and powerful.  And there's a great free on-line text, *Structure and Interpretation of Computer Programs.  *By then end of that book, you're not just playing around with databases or something like that, [I]you're writing a compiler!

[/I]Granted, Scheme isn't the easiest language to learn, but even if you learn just a little bit, you'll see a very different approach to programming.

---

### Post by whatintheworldisthat on 2006-11-10
I'm currently learning python and I've had a wonderful experience so far. My favorite aspect about python is that it is just plain readable. You can read code with no python experience and pretty much figure out what its doing.

Python's sensitive whitespace (indentation) is god's gift to humans IMHO.

I chose python over ruby because it is much more widely used than ruby. Faster than ruby, but still not fast compared to compiled languages of course. Love the documentation. Excellent library and 3rd party modules for just about anything. Its fun!

Python and ruby have very similar design philosophies, and are both excellent to get started with. One thing that blew my mind I was looking into ruby was the necessity of "end" statements that are not present in python.

---

