---
title: "newbie in programming - help needed :)"
date: 2006-01-13
forum: Programming Talk
---

### Post by wizzkid on 2006-01-13
I wanted to learn programming, after my research about which programming langauage should I study and practice, i ended up deciding to go with C (not C++ or C#) just a plain jane C, guess C++ will be follow afterwards. But my problem is I dont know where should I start (i know a basic c) but where can I get materials or some sort of ebooks of c for dummies or learn c in 24hours etc. 

Also, can I created MS Windows Xp application such as accounting system or payroll system through linux desktop os? and how to compile them for windows use and linux use. 

Does Eclipse with CDT is good enough? or Kdevelop? 

Thanks.

---

### Post by overcast on 2006-01-13
Personally i recommend Kdevelop but it is having trouble with installation under Kubuntu operaing system.
Anyway you can install glade under ubuntu.Tell me if it works under ubuntu.

---

### Post by wizzkid on 2006-01-13
Thanks. I was able to make run of kdevelop in my kubuntu. After installing the KDE 3.5 my kdevelop was messed up, all I did was run this commend in terminal

ln -s /usr/bin/kdevelop3 /usr/bin/kdevelop
this makes /usr/bin/kdevelop point to /usr/bin/kdevelop3

and now its working again :)

---

### Post by mvaniersel on 2006-01-13
There are a lot of online books on the subject, the trick is of course to distinguish the junk from the good stuff. A quick google turned up this "[Programming in C]("http://www.cs.cf.ac.uk/Dave/C/CE.html")".

Of course you should bookmark the [GNU libc reference manual]("http://www.gnu.org/software/libc/manual/index.html")

There is the possibility of cross-compilation (meaning compiling a windows binary on linux or the other way around), but I've personally never looked into that. I just use MinGW (=windows gcc port) to compile the program on my  windows laptop, and gcc to compile it on my linux workstation. There are libraries for cross-platform GUI applications, such as  [wxWidgets]("http://www.wxwidgets.org") edit: I forgot to mention that wxWidgets is C++

---

### Post by LordHunter317 on 2006-01-13
Buy the book *The C Programming Langauge* by Brian W. Kernighan and Dennis M. Ritchie.  And if you're doing this on a path to learn C++, don't.

---

### Post by otake-tux on 2006-01-13
I cant understand why you would want to learn C over C++.  If you learn C++ you get a lot of C stuff plus object oriented programming.  There are also more tutorials around for C++.

I, unfortunatly have done both.  I did data structures in C (horrible) and I did the same data structures in C++ (a lot nicer).  one is horrible and one is nicer becuase of the object oriented paradign.  For example, in C if I want to design a Queue data sracture I make a struct called queue and then declare my variable

queue myqueue;

that doesnt initialize my structure. I need to create a seperate of funtion that actually creates the queue and invoque it. so it goes
queue myqueue;
creat_queue (myqueue);

in c++ you just make a constructor and when you type queue myqueue it get created.

thats just a very short example of the benefits of C++ over C.they are both the same when you are starting over, but when you get into data structures it gets diffrent.  I recommend C++. [tutorials]("http://www.cprogramming.com/tutorial.html")

---

### Post by derelict on 2006-01-13
Take a look at these e-books: [http://oopweb.com/CPP/Files/CPP.html](http://oopweb.com/CPP/Files/CPP.html)


[QUOTE=otake-tux]
thats just a very short example of the benefits of C++ over C.they are both the same when you are starting over, but when you get into data structures it gets diffrent.[/QUOTE]
One being OO and the other not is quite a difference. You should actually know some OO design before getting into the OO features of a language, as there's more to it than just constructors, interfaces and inheritance. But anyway, if the goal is to learn C++, I also don't think there's much point in starting with C, just go for C++.

---

### Post by LordHunter317 on 2006-01-13
[QUOTE=otake-tux]I cant understand why you would want to learn C over C++.  If you learn C++ you get a lot of C stuff plus object oriented programming.  There are also more tutorials around for C++.[/quote]Because they're two entirely different languages.

> they are both the same when you are starting over, but when you get into data structures it gets diffrent.No, they're not.  If they look the same, then you're not really learning C++, you're learning C in the guise of C++.

---

### Post by mvaniersel on 2006-01-13
I disagree. C++ is C with a set of extra features. OOP is one of them. Exceptions another. Operator overloading. Templates. STL. etc. etc.

A method is really a function that implicitly takes a this pointer as its first argument. 
A class is simply a struct with the members defaulting to private instead of public

The nice thing is that you can pick features as you need. Don't see a need for operator overloading? Then don't use it! I've never thrown a single exception in my life, but I make heavy use of templates and STL.

---

### Post by mvaniersel on 2006-01-13
edit: removed double post, sorry for that :oops:

---

### Post by LordHunter317 on 2006-01-13
[QUOTE=mvaniersel]I disagree. C++ is C with a set of extra features. OOP is one of them. Exceptions another. Operator overloading. Templates. STL. etc. etc.[/quote]No, it isn't.  Best practices in C++ not only don't have trivial analogues in C, they're often *impossible to write in C*.

More over, best practices in C are often worse practices in C++.

They're different languages.  Even if the syntax is similar, the way you go about solving problems in each language is totally different, both by convention and mere practicality.  Nevermind what the language limits you to.

> A method is really a function that implicitly takes a this pointer as its first argument. No, it's not, it's more complicated than that.

> A class is simply a struct with the members defaulting to private instead of publicIn C++, yes.  Between the two languages no, it's more complicated than that.

---

### Post by nonemlinus on 2006-01-13
wizzkid, it sounds like you want to write a cross-platform accounting
application, in a language that would be easy to write.  

If you are just starting to program, I think C and C++ are difficult
(but not impossible) languages to start with.  There are a lot 
of nuances to each, all of which can take a long time to 
learn. And an accounting application, cross-compiled for
windows from linux, sounds like a daunting task.  I recommend 
using a kinder language than C/C++.

Think of preparing for a marathon.  Nobody just starts running.
Ideally there should be months of training, starting with
small, easy to do runs, followed by gradual increase
in difficulty.  Eventually, the marathon becomes the
next 'do-able' task.  Programming, and most things
that are hard to master, is just like that.

For your accounting application, perhaps python or a similar
language would be a quicker way to develop your app.
Python specifically is nice to work with (you don't need to worry about
pointers, memory management, file handlers, ...; like Ubuntu, it usually 'just works) 
and you can express yourself in most of the 
ways people have mentioned in this thread (object-orientation, 
functional programming, ...).  It has gui libraries available 
to it (Tcl/Tk, or many others...you can even find Python bindings
for Qt3).  And you can even, eventually, turn your app into a full blown
C++ (or C...) application with something like Boost.Python once
you have things working for your target platform so, your 
effort spent in development doesn't have to be completely
rewritten or scrapped.  The point is that you can have
an easier time learning to program AND you can be productive
too.

Java could be another place to start with the same advantages.

My point isn't to praise a particular language, my point
is that if you're going to invest a lot of time in building, 
and if you're interested in really learning to program, 
look into other languages.  I love C (...and C++, and Python, 
Lisp, Ruby, Perl, ...Java is growing on me I guess) but, using
C/C++ in this situation, IMHO would be a frustrating task.  
Ultimately, it's not the language that matters but, how
you are expressing your ideas with it.

I hope that helps.  Also, there is a ton of great
advise on programming around.

Here are two of my favorites; the authors
do a much better job of conveying these ideas:

[http://www.catb.org/~esr/faqs/hacker-howto.html#attitude](http://www.catb.org/~esr/faqs/hacker-howto.html#attitude)
[http://www.paulgraham.com/articles.html](http://www.paulgraham.com/articles.html)

Good luck with your project; hope you keep at it.

---

### Post by rolfotto on 2006-01-13
[QUOTE=wizzkid]I wanted to learn programming, after my research about which programming langauage should I study and practice, i ended up deciding to go with C (not C++ or C#) just a plain jane C, guess C++ will be follow afterwards. But my problem is I dont know where should I start (i know a basic c) but where can I get materials or some sort of ebooks of c for dummies or learn c in 24hours etc.[/quote]

If you are going to learn C - don't buy Kernighan & Ritchie's C book.  Everybody will recommend it because that's what their college professor gave them - and, oddly enough, it sucks for the beginner.  It's only a decent book **after** you learned C because it's very terse.

For learning C: the book "Pointers on C" is much better, covers most every aspect of the C language, and really teaches you POINTERS (and arrays, etcetera) - in every aspect of the language.  Because that's where the power of C comes from, but also are the source of 90% of the security problems and bugs (not features) of C-written software.  K&C glosses over this, "Pointers on C" lets you master them.

[http://www.amazon.com/gp/product/0673999866/sr=1-1/qid=1137197881/ref=pd_bbs_1/103-9447992-5694265?%5Fencoding=UTF8](http://www.amazon.com/gp/product/0673999866/sr=1-1/qid=1137197881/ref=pd_bbs_1/103-9447992-5694265?%5Fencoding=UTF8)

It's expensive, but you can find good used copies cheaper.  C in 24 days and other various books are superficial primers and you end up having to get a better book anyway, thus spending more money or living with an incomplete understanding of the subject.

As for a second language, perhaps you might go with C++.  But that's not the best choice in a lot of areas, C++ is not the cleanest language out there.  My suggestion would be Lisp (there are many free books on the web I can point you to), but if I were you, investigate the possibilities.  C# and other C "sucessors" may be better than C++ for what you need it for, in the C family of languages.  Or a different language may be called for.  Someone also mentioned Python which may not be a bad idea....

---

### Post by LordHunter317 on 2006-01-13
[QUOTE=rolfotto]If you are going to learn C - don't buy Kernighan & Ritchie's C book.  Everybody will recommend it because that's what their college professor gave them - and, oddly enough, it sucks for the beginner.[/quote]I recommend it because out of all the books I've read/seen/heard recommended, it has the least number of errors.

---

### Post by wizzkid on 2006-01-14
Guys, the you so much for your post and recommendation. I am a poragrammer wannabe, I want to learn programming years back, but because of my tight schedule  in my work as systems engineer and netwrok administrator, and recent became a managing director of a company. thus my time for studying programming lessen. I've been thru pascal, foxpro and C/C++ back in college, but its long time ago, i forget those already and I wanted to learn programing again. 

Now, its confusing me which language should I study, I want something that powerful and I am not just going to program account system or payrol system, i want also to program something like utilities, web browsers, chat software like kopete and gaim... (I am ambitious alright.. hehehehe) and thought of C/C++ is more on that field. I also consider python but need to learn more on that aspect. I have a Glade Interfaces designer, Kdevelop3 installed. does glade is suffecient already? can I code a program on glade? or its just a simeple drag and drop program?

As far as c books, a guys recommended  C++ Programming: Program Design Including Data Structures by D.S Malik, does this book good for a beginner? and I am looking at C unleashed and pointers on C.

Once I leared python, a learning curve to C++ or D is easy? :-)

now at least I already draw my card, which langauge do you think suited for me? C++ or Python?

more comments?

---

### Post by David Marrs on 2006-01-14
C++ or Python?

I think it depends more on why and what you want to program. If you want to write apps quickly then python's the best way to go. It automatically takes care a lot of caretaking tasks for you. However, if performance is a critical factor (most of the time it isn't) then C++ is going to be better.

On the other hand, C's nice from an academic point of you because, by having to build your own data structures etc., you can see more clearly what's going on at the machine level. So from that point of view, it could be worth learning at some point. I presume the same is also true of C++ to a certain degree.

Btw, if you're a newbie then python :p

---

### Post by Jessehk on 2006-01-14
I am programming as a hobby at a novice level. 
I first was excposed to it by learning TI Basic on my graphing calculator. 

Wanting to move to bigger things, I bough a book on C (C for dummies, which despite the name, I found to be very good), and then moved on to C++, which I am currently learning (gotten past OOP, inheritance, templates, exceptions, etc, and am now trying to learn more about the STL).

C++ is a very complicated language. There are many things to remember, and in my experience, it is very easy to write bad code. 

There have been advantages though. I have looked (just a bit more advanced then simple classes) at Java, C#, and python, and making the transition to these languages has been **very** easy. 

It is almost like after the initial challenge, everything is smooth sailing.

In my opinion, if you want to learn programming concepts quickly (such as creating classes, using loops, and conditional statements) then python would be the way to go. If you have an interest in making a program that you can be proud of, then I would recommend C++.

But that is just my (a beginner's) opinion. By no means should you take it very seriously.

---

### Post by zappa86 on 2006-01-14
Learn C (maybe not first but soon); it is simpilly the most badass programming language ever. It is quite hardcore and you can take you skills with C and programming a varity of things from low level drivers, heigher level applications with GTK widgets, and embedded microcontrollors. With C however you have to manage your own memory and other stuff, its not like Java where it will do it all for you. If you know what your doing you can get great speed out of C. Over time, you will learn tricks with that language that you can only do in C (or asm). I would recomend the O'Reilly books to learn anything about computers. Steve Oualline is a great author and his books are quality. I know sever people who wanted to learn a language and then learn the basics syntax and commands (such as printf, sscanf, malloc, free, and etc...) however they don't know what they can "do" with the language. People are intersted in applications. The biggest problem I have with the CS department at my school is they just program stuff to learn fundementials (such as a bubble sort, linked lists, B-trees), and worry about O() (big O notation). Therefore I would look at applications that you use commonly such as GAIM, or Mozilla, and write a plugin that can do something that you've always wanted to be done. Start small and go from there. You can look at tons of source for GAIM plugins and such. I learned howto program from making mods and scrips for a game called Tribed 2 (which its scripting language was similar to c++). Also you may find PHP intersting as well. If you like dyanmic webpages and such you could create a module (or plugin) for something. I just hope you will start by programming something that you are intersted in and not worry about all algorithms and classroom stuff initally and just have fun with programming. Enjoy being in control of the computer and telling it what to do. :)

---

### Post by LordHunter317 on 2006-01-14
> **zappa86]Learn C (maybe not first but soon) said:**
> I would love to see you support htis.

> It is quite hardcore and you can take you skills with C and programming a varity of things from low level drivers, heigher level applications with GTK widgets, and embedded microcontrollors.I can do that with a host of languages, besides C.  These aren't things that are unique to C, nor necessarily make C desirable to learn.

[quote] I would recomend the O'Reilly books to learn anything about computers. Steve Oualline is a great author and his books are quality.Blanket recommendations are a poor idea; most of O'Reilly's C++ books are crap.

> The biggest problem I have with the CS department at my school is they just program stuff to learn fundementials (such as a bubble sort, linked lists, B-trees), and worry about O() (big O notation).That's because Computer Science is a divison of math, and has little to do with actual application writing.  If you want to learn to write practical programs, become a software engineering.  The division between CS and engineering is no different from physics and engineering.

---

### Post by Azion on 2006-01-14
C++ is one of the most standard, but I suggest something like Python first to get used to the progamming thinking

---

### Post by rolfotto on 2006-01-15
[QUOTE=LordHunter317]I recommend it because out of all the books I've read/seen/heard recommended, it has the least number of errors.[/QUOTE]

Well, I wasn't trying to single your post out - when C comes up, somebody always bring up K&C.

My professor in our first year programming class (80% of the students had no programming experience whatsoever) made it his text and I remember the horror of trying to learn from it.  Everybody had it dutifully on their desks come class times, but nearly no one was using it as their text to learn from.  Hidden in their bookbags were "Pointers on C" (another Professor's text) or something like "C in 21 days", either of which was much easier to parse - though the 21 days books aren't indepth enough.

I don't know if it because K&C wrote Unix and invented C that their text is so recommended?  But it really is better for those who know C already than it is for someone trying to learn it.

---

### Post by wizzkid on 2006-01-15
Thanks so much for your suggestions. Okay, I want to learn python. but where i could find the ebooks for that subject? i want something for begginer.  I went to bookstore but I couldnt find python programming and c are very few, im in the philippines, and purchasng a book in amazon became too expensive because of the frieght charges.

Hope I could find ebooks for python.  

I already have glade interface designer installed and playing with it.. then gnu emacs for text editor... is that sufficient already? what else I need to install before i can get python going? i was able to run this [http://www.arson-network.com/index.php?class=tutorial&subargs=430](http://www.arson-network.com/index.php?class=tutorial&subargs=430)   so I think i have all the neccesary program to run python...  let me know what else should i install.

Thanks so much for all your help!

---

### Post by wizzkid on 2006-01-15
is a wrox book good? it seems that wrox is popular in programming books. I have 2 wrox book php and asp, but havent read that much. just wondering if this book is really good, and was planning to buy beginning python (WROX)

Comments? suggestions?

---

### Post by nonemlinus on 2006-01-15
start here: [http://www.python.org/doc/2.4.2/](http://www.python.org/doc/2.4.2/)  they're free! :)

go through the docs; mess around with things; try stuff out...

once you get to the end you'll have a better
idea of the range of books available and of what book 
may suite your particular needs.

---

### Post by mvaniersel on 2006-01-15
Which is the best programming language? Good luck getting a clear-cut answer to that question.

But if you can't find out which is the best, go for the most popular one. There was a poll: [programming language poll]("http://www.ubuntuforums.org/showthread.php?t=22481").

---

### Post by rolfotto on 2006-01-15
[QUOTE=wizzkid]is a wrox book good? it seems that wrox is popular in programming books. I have 2 wrox book php and asp, but havent read that much. just wondering if this book is really good, and was planning to buy beginning python (WROX)

Comments? suggestions?[/QUOTE]

I don't like recommending an entire line at once - usually it depends on the author and the individual books.  I find the reviews up at amazon.com helpful for individual books (though sometimes not critical enough....)

---

### Post by wizzkid on 2006-01-15
Thanks again guys... thanks for all your suggestions :)

God bless.

---

### Post by purpleturtle on 2006-02-02
Was is Bjarne Stroustrup that said (along the lines of):

"It's easy to shoot yourself in the foot programming in C. With C++ when you shoot yourself in the foot, you blow your whole leg off".

  :) 

Personally I have enjoyed writing C++ in the past, but I absolutely dread having to support other peoples C++ projects.  Even coming back to my own C++ after a year or two, I wonder what the hell I was doing at the time. It just seems the simplest of tasks are achieved in the most obscure, overcomplicated ways..

Eric Raymond's book "The Art of Unix Programming" has a good piece on this.  (A very good book incidentally.. Although keep a dictionary to hand when you're reading it..)

---

