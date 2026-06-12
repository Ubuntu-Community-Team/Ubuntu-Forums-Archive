---
title: "I am having troubles starting to learn programming.. where should I start?"
date: 2007-05-12
forum: Programming Talk
---

### Post by billdotson on 2007-05-12
I have no prior programming knowledge and I have been trying to learn programming recently.  I have heard that python is a good language to start with but I can't seem to find any free resources that the general consensus says are good for learning programming.  Dive into python (on it's site) talks like it is for people who have programming experience and are just wanting to learn python.  I have read a few chapters of Think Like a CSpy but it started to get confusing and I felt like it was assuming that I knew some programming concepts that I did not.  Are there any good resources where I can begin to learn programming by learning python?

I would prefer to not have to pay for resources but if I need to to get some good resources to learn with I guess I could.

---

### Post by pmasiar on 2007-05-12
Python is good choice. Sticky on this forum has has loads of info for every language, including Python. . See also link in my sig

---

### Post by Mirrorball on 2007-05-12
You can also post your questions here if there is something that you read and didn't understand.

---

### Post by slavik on 2007-05-13
I suggest starting with a simpler language like C or Scheme (Scheme was made for teaching programming and the syntax is very easy)

---

### Post by pmasiar on 2007-05-13
> **slavik said:**
> I suggest starting with a simpler language like C or Scheme (Scheme was made for teaching programming and the syntax is very easy)

You must be kidding, making fun from an innocent beginner: C being simpler that Python? And scheme is was made to teaching *functional* programming, but I would not recommend that style to beginners with no experience in programming.

Compare 99 bottles in [Python](http://www.99-bottles-of-beer.net/language-python-808.html) and [scheme](http://www.99-bottles-of-beer.net/language-scheme-852.html)

---

### Post by gaylapdancer on 2007-05-13
Python is definitely a good one to start off on. Don't do what I did and go straight for C and C++.... 

Python Programming for the Absolute Beginner 
by Michael Dawson   ISBN:1592000738 

That is a -very- good beginner book, followed by:

Python 2.1 Bible
by Dave Brueck and Stephen Tanner  ISBN:0-7645-4807-7


Programming Python, 3rd Edition 
By Mark Lutz  Print ISBN-10: 0-596-00925-9  Print ISBN-13: 978-0-59-600925-0 

Is also quite good.

---

### Post by zano2k5 on 2007-05-13
i want to learn c and c++ any help and what book i can get i dont have any  experience with c and c++ because i mostly wanna program emulator and other stuff and i kinda wanna turn a game desiner later on in life i just wanna to know all there is in this world

---

### Post by jfinkels on 2007-05-13
There's nothing wrong with learning C first. If you want to better understand memory allocation and such, go for C!

---

### Post by gaylapdancer on 2007-05-13
For C:

C: In a Nutshell 
By Tony Crawford, Peter Prinz 
ISBN: 0-596-00697-7 

I also have a learning C interactive tutorial on CD which is quite good....

For C++:

C++ in a Nutshell 
By Ray Lischner 
ISBN : 0-596-00298-X 


I have some more kicking around, the SAMS teach yourself (Insert Language here) in XYZ (Unit of time here) kind. I think I have The SAMS teach yourself C and C++ in 24 Days somewhere.....

---

### Post by slavik on 2007-05-14
> **pmasiar said:**
> You must be kidding, making fun from an innocent beginner: C being simpler that Python? And scheme is was made to teaching *functional* programming, but I would not recommend that style to beginners with no experience in programming.

Compare 99 bottles in [Python](http://www.99-bottles-of-beer.net/language-python-808.html) and [scheme](http://www.99-bottles-of-beer.net/language-scheme-852.html)

1. isn't a list an object? (no it isn't, I thought everything was an object)
2. K&R book teaches C and yet it is very small.
3. don't forget that scheme does not have loops while python does

---

### Post by LaRoza on 2007-05-14
For C++, this tutorial [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/) is very good, it has more than many books for beginners and is easy to follow.

---

### Post by pmasiar on 2007-05-14
> **slavik said:**
> 1. isn't a list an object? (no it isn't, I thought everything was an object)

Not sure what is your concern here. Anyway, Python is language for solving practical problems, not for language lawyers.

> 2. K&R book teaches C and yet it is very small.

You seems to be one of many experienced programmers who keep forgetting that beginners are different experts. K&R is excellent book, but it is for expereinced programmer who learns C as second or 3rd language, and is 100% useless for total beginner. I am really tired to reminding experienced programmers that beginners obviously need different books, they keep suggesting beginners books for experts because they (experts) personally liked them. 

When *I* want to recommend a book for beginner, I am consciously trying to evaluate book from POV of beginner, and then ask a beginner to confirm my opinion. It is not book for me - it is a book for beginner.

> 3. don't forget that scheme does not have loops while python does

This is really funny one. It does not make sense to me at all. How it is relevant to anything?

You mean to say that Scheme is simpler than Python, because Scheme does not have loops? Do you truly believe that recursion is simpler to comprehend for beginner than loop?

---

### Post by raul_ on 2007-05-14
I'm an IT student, and in my college we start with Scheme, and we take C in the 2nd semester. I still think C is the best

---

### Post by pmasiar on 2007-05-14
> **raul_ said:**
> I'm an IT student, and in my college we start with Scheme, and we take C in the 2nd semester. I still think C is the best

I agree that C is easier to comprehend for beginner than Scheme. But did you tried Python?

---

### Post by slavik on 2007-05-14
actually, MIT starts teaching programming by using Scheme. :)

The point about Scheme not having loops was because in the two 99 bottle examples you provided, python used loops, which make certain things much simpler.

To the OP, if you want to learn programming, try to take everyday tasks and separate them into steps, then take each of those steps and separate them into steps even more. Then try to get an idea for a program (something that does text processing or some such) and separate that into steps and then pick a language and implement it in that language. Picking which language to use for learning programming is not very important.

The only difference between languages for a beginning programmer is when you get to concepts that are required that you understand in order to be able to do anything.

for example, consider a "string" in C, versus Java.

to find out the length of a C string, you call strlen() and give it the pointer to the character array, strlen() will return the length.
in Java, you simply call the method of the string object called length.

samples (lots of code is cut out):
C ==
char *str = "Hello World!";
int length;
length = strlen(str);

Java ==
String str = new String("Hello World");
int length;
length = str.length();

---

### Post by pmasiar on 2007-05-14
> **slavik said:**
> actually, MIT starts teaching programming by using Scheme. :)

The point about Scheme not having loops was because in the two 99 bottle examples you provided, python used loops, which make certain things much simpler.

I agree 100% that Python makes certain (even many!)  things much simpler than Scheme - that's why I suggested Python in the first place :-)

But your MIT info is slightly obsolete: FYI, [MIT is switching from Scheme to Python](http://www.amk.ca/diary/2006/11/mit_to_try_python_for_introduc.html) :guitar:

---

### Post by raul_ on 2007-05-14
I never tried Python, but being an OO language, i think it's easier to start with something else, and then grab OO, than to start working with objects, and then change to something else.

---

### Post by pmasiar on 2007-05-14
> **raul_ said:**
> I never tried Python, but being an OO language, i think it's easier to start with something else, and then grab OO, than to start working with objects, and then change to something else.

Well, you rather obviously never tried Python. :-)

Unlike Java, where OO is forced on you from the day 1, Python does not force you into single paradigm. Beginner can easily program in simple procedural style, occasionally using existing OO methods, but without defining own objects. Many months later, when ready, you can take on OO.

Python is OO-optional language. :-)

---

### Post by foxmulder881 on 2007-05-14
I know it's Microsoft, but have you considered Visual Basic? It's pretty, well, basic to learn for a newbie.

---

### Post by raul_ on 2007-05-15
> **pmasiar said:**
> Well, you rather obviously never tried Python. :-)

Unlike Java, where OO is forced on you from the day 1, Python does not force you into single paradigm. Beginner can easily program in simple procedural style, occasionally using existing OO methods, but without defining own objects. Many months later, when ready, you can take on OO.

Python is OO-optional language. :-)

That's nice. I've been curious for a while, but with all the work I have, I really don't have the time to try another language. It's in my list though

---

### Post by lunamystry on 2007-10-27
I bought my first ever PC a couple of months ago so I knowabsolutely nothing about programming.
I  want to learn programming and a friend of mine who is a fan of JAVA said he would lend me one of his books on it so i can try out programming. I will have C++ next year in software development so i think i'll buy books then. 

Now I downloaded two bin files i think have the complier thing. How do I install them? Do I need them?

---

### Post by pmasiar on 2007-10-27
Python is better start than Java. Is already installed on your Ubuntu, and plenty of free online books - links in my sig.

---

