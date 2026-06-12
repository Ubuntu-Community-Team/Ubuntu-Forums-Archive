---
title: "C++ or C?"
date: 2007-02-27
forum: Programming Talk
---

### Post by tehturkey on 2007-02-27
hey

which language is better c++ or c? and please give reasons :D
i am planning on learning one of them languages :P

thanks very much people.

---

### Post by drfalkor on 2007-02-27
C is kind of Low-level, C++ is to. But C++ is more complex, and its faster than C when it is compiled.
So, I would go for C++, because when you know C++, you sure gonna know how to program in C.

I would go for something easy first, like python. ( Its good to combine some python and C++.. Python for simple big stuff, and C++ for more detailed main stuff with details etc ).. you are gonna need Python in the future :P

Python tutorial: [http://www.ibiblio.org/obp/thinkCSpy/](http://www.ibiblio.org/obp/thinkCSpy/)

C++ tutorial: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

Learn Python first, then C++ and last.. C :)

---

### Post by tehturkey on 2007-02-27
well i know php,html pretty good made a few good sites with it. i think i'll go straight to c++ :p

why would i learn c last? lol if c++ is better?

thanks again

---

### Post by drfalkor on 2007-02-27
C++ is more complex, and it has better memory managment :) +its faster

EDIT: Oh, and its OO( Object Oriented )

---

### Post by slimdog360 on 2007-02-27
From what Ive experienced c is more for embedded programming, like microprocessors, the linux kernel etc. Where c++ being object oriented is better for desktop applications and the like.

So I guess you have to ask yourself, are you going to be developing an operating system or the next Openoffice.org?

---

### Post by runningwithscissors on 2007-02-27
> **drfalkor said:**
> C++ is more complex, and it has better memory managment :) +its faster
It's only faster in very few cases.

> **drfalkor said:**
> EDIT: Oh, and its OO( Object Oriented )
Which counts for nothing.
Not to mention, the OO implementation isn't exactly brilliant on C++.
For decent OO, stick to stuff like Ruby.

---

### Post by tehturkey on 2007-02-27
c++ it is then :P

thanks very much. any links for info about the STL? and programming for linux in c++?

thanks again.

---

### Post by Lster on 2007-02-27
> C++ is more complex, and it has better memory managment  +its faster

That depends on the C/ C++ compiler. Comparing GCC and G++ indicates that there is very little difference between the two.

Look at [http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=gcc&lang2=gpp]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=gcc&lang2=gpp").

---

### Post by g3k0 on 2007-02-27
C++ is basically C with classes.  You can do any C command in c++.  You are less susceptible to buffer overflows in c++ and passinig by reference is nicer and and and and.... 
C should have been retired long ago.

---

### Post by hod139 on 2007-02-27
> **g3k0 said:**
> C++ is basically C with classes.  You can do any C command in c++.  
Not really true.  For example, here is a line in C that won't compile in C++:
```

int class;

```C++ is now also a lot more than C with classes (e.g. generics)

> 
You are less susceptible to buffer overflows in c++
Not true.

> 
 and passinig by reference is nicer
While I personally agree that it is nicer, this is not a globally true statement.

> 
C should have been retired long ago.Why?  Use C when appropriate and C++ when appropriate.

As for the OP's question, I would suggest C++ if only for the STL.

---

### Post by pmasiar on 2007-02-27
> **tehturkey said:**
> which language is better c++ or c? 

better for what? 

- Kernel hacking? C is it
- GUI app for Gnome/KDE? C++
- web applications? Python/ruby on server, maybe AJAX/javascript on client, etc.


I can give you easier question: Which car is better: Toyota corolla, or 18 wheeler truck?

If you say corolla, i will laugh at you: bring some strawberies from california to New York in it, and you will be bankrupt at the end of the week.

if you say truck, I have last laugh again: I want to see you commuting to school/work in it - and how the hell you are going to park it?

See my point now?

---

### Post by g3k0 on 2007-02-27
> **hod139 said:**
> Not really true.  For example, here is a line in C that won't compile in C++:
```

int class;

```C++ is now also a lot more than C with classes (e.g. generics)


Rather then arguing, this is what I "meant."  From the words of Bjarne Stroustrup, the orinal implementer of c++ 
> Is C a subset of C++?
In the strict mathematical sense, C isn't a subset of C++. There are programs that are valid C but not valid C++ and even a few ways of writing code that has a different meaning in C and C++. However, C++ supports every programming technique supported by C. Every C program can be written in essentially the same way in C++ with the same run-time and space efficiency. It is not uncommon to be able to convert tens of thousands of lines of ANSI C to C-style C++ in a few hours. Thus, C++ is as much a superset of ANSI C as ANSI C is a superset of K&R C and much as ISO C++ is a superset of C++ as it existed in 1985. 

> C++ is now also a lot more than C with classes (e.g. generics)

I was refencing the original design idea and former name.  I do realize that more is added.  Which is a good thing.  From Bjarne again,
> I wanted to write efficient systems programs in the styles encouraged by Simula67. To do that, I added facilities for better type checking, data abstraction, and object-oriented programming to C. The more general aim was to design a language in which I could write programs that were both efficient and elegant. Many languages force you to choose between those two alternatives. 
The specific tasks that caused me to start designing and implementing C++ (initially called "C with Classes") had to do with distributing operating system facilities across a network. 


> 
[quote]
You are less susceptible to buffer overflows in c++  

Not true.[/QUOTE]

Without the stl you are forced to do things like strcat and strcpy.  These are absolutely horrid.  It is difficult to use their counterparts strncat and strncpy correctly.  Dont even start me with gets.

---

### Post by hod139 on 2007-02-27
> **g3k0 said:**
> Rather then arguing, this is what I "meant."  

Your meaning wasn't clear from your first post.  I just wanted to emphasize that the two languages are not the same, and that not all (granted most) C code will compile in C++.

> 
I was refencing the original design idea and former name.  I do realize that more is added.  Which is a good thing.  

When you stated that C++ was C with classes, you never clarified that you meant original C++ and never said more was added.  I agree that more was added, I just wanted to point out that C++ (and btw C) have both evolved and further diverged from your first statement.

> 
Without the stl you are forced to do things like strcat and strcpy.  These are absolutely horrid.  It is difficult to use their counterparts strncat and strncpy correctly.  Dont even start me with gets.
When using C++ what's forcing me to use the STL?  As you pointed out C++ is a superset of C (using Bjarne's definition of superset) and as such all the bad C stuff comes with it.  I agree that strcat and strcpy are evil and should always be avoided, but there is nothing stopping a programmer from using them.

---

### Post by mavigozler on 2007-02-27
You should invest your time in C++.

The trend is to go to object-oriented languages.

I learned C about 20 years ago and was hesitant to try C++ or look at Java.  

There are great advantages to using C++.  Firstly the concept of classes helps you to organize data and your program execution more smartly.  Of course, C has the struct datatype to organize data, and these are essentially classes whose contents are "public" by default, but C is a procedural-based language which centers on the function in which functions may not really have any relatedness other than being placed within the same translation object (file).

With the class concept in C++, the data and the functions (methods) are grouped into a class to show their relatedness.

C++ also includes standard library functions and templates that help you to stop from stumbling into difficulties that often plague the developer, such as memory leaks and exceeding array bounds (if you use the vector template).  In many cases C++ features automatic memory allocation/deallocation mechanisms for objects (class instantiations) which you would normally to construct in a heap rather than on the stack.

If you want to program for a Windows environment (Visual C++), you would be very wise to learn C++.

In learning, you need to pick the right book.  I fist read the original book written by the developer of C++, Bjarne Stroustrup, in the 2nd edition in the late 1990s, and the first read through showed to me that C++ through so much as the C programmer (overloading of functions and operators! class derivation/inheritance, templates) that it did not seem like C at all.  Stroustrup's style is a bit blunt too, probably aimed at the computer engineer with advanced degree.  There are more gentle approaches out there.

If you want an excellent place to download and read PDFs or CHMs on C++, I suggest you get access to the Usenet and scan the headers in the 
[B]
        alt.binaries.e-book.technical[/B]

newsgroup.  There are a few posters who thankfully upload gigabytes of electronic books on a variety of subjects.  And you can download these.  If you find a book you like (it might also be in print at the bookstore), and if you read it and learn from it, and it is recently copyrighted, you can order the book from the publisher and that way its living author will likely benefit.  If the copyright is more than 30 years old or the book is out of print, your reading and use of it will probably have no benefit to the author, who may have passed on.  Right now, I am reading through a CHM of  H.M. Deitel, C++ How To Program, 5th Ed. (1536 pp).  It's not too bad as an introductory text.  I will be checking out other PDFs and CHMs and DJVUs I have on C++ later.

---

### Post by g3k0 on 2007-02-27
> **hod139 said:**
> 
When using C++ what's forcing me to use the STL?  As you pointed out C++ is a superset of C (using Bjarne's definition of superset) and as such all the bad C stuff comes with it.  I agree that strcat and strcpy are evil and should always be avoided, but there is nothing stopping a programmer from using them.
Nothing is forcing you to use stl.  C++ still holds things like strcpy and strcat.  But these arent often used with classes like the String.  Sure those problems still exist but c++ gives you an alternative.  That is why it is less susceptible to buffer overflows.

---

### Post by yaaarrrgg on 2007-02-27
C is not really designed for building apps, but a minimalistic language for interfacing with the lower level of the computer, for drivers, operating systems, etc.  To some degree, I think C will outlive C++ in terms of usefulness, since it's competitors are really the likes of HLA, assembly, and other low level languages.  

Although, most of the reasons that people give, or flaws with C could actually be fixed in my opinion, with better libraries.  If the string functions are bad, why not avoid the ANSI standard here?  Even a garbage collector could be added to C, or many of the same features we like about OOP.

The real criticism of C should be about the syntax, or the binary format (which is even worse in C++) ... most other problems are probably fixable.

C++ is really competing against, say, D, and in some respects Java, and C#.  While it's still incredibly popular, it is loosing popularity because many other languages can solve the same problems with less effort.  I think it's sinking faster than C:

[http://www.tiobe.com/tpci.htm](http://www.tiobe.com/tpci.htm)

So, C is probably a better language to know, IMO, between the two.

---

### Post by RedSquirrel on 2007-02-27
> **drfalkor said:**
> C++ is more complex

Fortunately, one can still write *simple* programs with it when they're just starting out (setting aside a lot of the additional syntax and of course the OO concepts).

---

### Post by RedSquirrel on 2007-02-27
> **mavigozler said:**
> 

There are great advantages to using C++.  Firstly the concept of classes helps you to organize data and your program execution more smartly.  Of course, C has the struct datatype to organize data, and these are essentially classes whose contents are "public" by default

And structs cannot have methods. IMO, the *contrast* works better the other way around: classes are like structs except you can have methods as well as data and there are new keyswords: public, private, protected.

---

### Post by RedSquirrel on 2007-02-27
I think the advantage of learning C first is that it's a small language and you can get your mind around the basics pretty quickly. Later, when you go to learn C++, you have a base to work from. If you learn C++ first and then C, you have to "unlearn what you have learned" (yes, I'm quoting Yoda here). I know, you have to unlearn some things if you learn C first and then C++, but not as much.

This is just my opinion, and learning either one first is going to be OK.

As far as which one is "better" overall, that question cannot be answered since it depends on what you're trying to accomplish (as others have said).

---

### Post by lnostdal on 2007-02-27
my vote: learn c and skip the ugly hybrid c++ using instead languages like ruby, python and lisp

---

### Post by g3k0 on 2007-02-27
> **RedSquirrel said:**
> Fortunately, one can still write *simple* programs with it when they're just starting out (setting aside a lot of the additional syntax and of course the OO concepts).

which looks more complex?

printf("Hello %d Doo de dah %f",operatorNum,myVariable);

cout << "Hello" << operatorNum << "Doo de dah" << myVariable;

> And structs cannot have methods. IMO, the contrast works better the other way around: classes are like structs except you can have methods as well as data and there are new keyswords: public, private, protected.

Umm.. I use ...methods. in structs... especially contructors ... havnt tried it in C though.. should work.... I think....

> I think the advantage of learning C first is that it's a small language and you can get your mind around the basics pretty quickly. 

heh heh unless you want to do things correctly

ps.  Did you really need three posts?  Go beans..

P.Sp.s.  If you are just learning I dont think you will be playing with low level programming

p.sP.S.p.s look at this

```

  int  a, b;
  double  d;
  char  str[20];

  cin >> a;  // equivalent to scanf("%d", &a);
  cin >> b;  // equivalent to scanf("%d", &b);
  cin >> d;  // equivalent to scanf("%lf", &d);
  cin >> str;  // equivalent to scanf("%s", str);

```

---

### Post by yaaarrrgg on 2007-02-27
> **g3k0 said:**
> which looks more complex?

printf ( "Hello %d Doo de dah %f" , operatorNum , myVariable );

cout << "Hello" << operatorNum << "Doo de dah" << myVariable;



They look about the same to me (I spaced the first for you).  :)

Operator overloading is probably the more complex between the two, since the meaning of the symbols are constantly changing.  Especially, since the use of shift operators '<<'  and '>>' really makes no sense here.   

In terms of verbosity, there's not a lot of difference.  Personally, I prefer printf, since the other intermixes the presentation format with the data more.

---

### Post by Mirrorball on 2007-02-27
> **lnostdal said:**
> my vote: learn c and skip the ugly hybrid c++ using instead languages like ruby, python and lisp
I disagree. For games and simulations and general number crunching, C++ is better than C, even though it is an ugly hybrid. It has OO features, less memory management, and more libraries (because C libraries are usually available too).

P.S.: Structs in C don't have methods.

---

### Post by Wybiral on 2007-02-27
> **yaaarrrgg said:**
> They look about the same to me (I spaced the first for you).  :)

Operator overloading is probably the more complex between the two, since the meaning of the symbols are constantly changing.  Especially, since the use of shift operators '<<'  and '>>' really makes no sense here.   

In terms of verbosity, there's not a lot of difference.  Personally, I prefer printf, since the other intermixes the presentation format with the data more.

I love operator overloads... Especially for mathematics. I use a lot of vector and matrix math in my programs (especially for graphical stuff)

Without overloads I would have to use something like this:

MulMatVec(MulMatMat(mA, mB), ScaleVec(AddVecVec(vA, vB), 0.5))

With overloads I could use...

(mA * mB) * ((vA+vB) * 0.5)

Which is much easier to read... It looks like math!

However, I will agree that the use of bitshift operators for streams was a pretty bad decision. But, you get used to it, and eventually accept it... No language is without it's flaws.

---

### Post by lnostdal on 2007-02-27
The OO and "easier" memory management-features in C++ aren't required when you've got a combination of C(#1) and other language than C++. As an example take Crash Bandicoot; a game(#2) written using Lisp.


#1: Or you can just generate/inline assembly from/in the HL language!
#2: It was a significant game; it became the PS2/Sony mascot.

---

### Post by Wybiral on 2007-02-27
> **lnostdal said:**
> The OO and "easier" memory management-features in C++ aren't required when you've got a combination of C(#1) and other language than C++. As an example take Crash Bandicoot; a game(#2) written using Lisp.


#1: Or you can just generate/inline assembly from/in the HL language!
#2: It was a significant game; it became the PS2/Sony mascot.

Lisp isn't REQUIRED when you have other languages either...

EDIT:

Or, to rephrase that... C and some language other than C++ aren't required when you have the OO and "easier" memory management features in C++!

Basically, what I'm trying to say is that it's preference...

---

### Post by Mirrorball on 2007-02-27
> **lnostdal said:**
> The OO and "easier" memory management-features in C++ aren't required when you've got a combination of C(#1) and other language than C++.
But combining languages may be more trouble that just writing everything in C++. I was combining Python with C++ for speed, but why not just use C++ for everything? The problems that take me a really long time to solve are domain related and Python wouldn't help (or Lisp, or any other high level language). I wish Python were faster.

---

### Post by lnostdal on 2007-02-27
wybiral: of course not .. you're free to do whatever you want and vote on what approach you prefer .. you're even free to say that "lisp sucks" or whatever; i do not care

---

### Post by lnostdal on 2007-02-27
> **Mirrorball said:**
> But combining languages may be more trouble that just writing everything in C++. I was combining Python with C++ for speed, but why not just use C++ for everything? The problems that take me a really long time to solve are domain related and Python wouldn't help (or Lisp, or any other high level language). I wish Python were faster.

this is of course true .. you must hit a certain threshold to even bother moving from asm to c for instance - but when you do it is worth it

edit:
many HL compilers compile to native code .. SBCL for instance: [http://groups.google.com/group/comp.lang.lisp/msg/2bbc5591ad786777?hl=en&](http://groups.google.com/group/comp.lang.lisp/msg/2bbc5591ad786777?hl=en&) .. someone should really add native compilation to Python - that would be great :)

---

### Post by Mirrorball on 2007-02-27
> **lnostdal said:**
> this is of course true .. you must hit a certain threshold to even bother moving from asm to c for instance - but when you do it is worth it
I did move from C++ to Python, then a combination of Python and C++, then back to C++. C++ alone is faster than Python, simpler than Python and C++.

---

### Post by Wybiral on 2007-02-27
> **lnostdal said:**
> wybiral: of course not .. you're free to do whatever you want and vote on what you prefer .. you're even free to say that "lisp sucks" or whatever; i do not care

I don't think lisp sucks, I do think it's hard as f*ck to write anything useful in it... But I don't have much experience with it.

But... I don't think C++ is as bad as you say it is. I think it's OO and memory management features are just fine. Sure it's got little things that make you say "why the hell did they do that?" but I think almost every language has those little quirks.

IMO, the bottom line is: preference and needs. I prefer C++ over C most of the time (it's more readable to me, such as in my example above ^^^, and easier to manager as a result of it's OO features) and it suites my needs most of the time (I wont say ALWAYS though... Sometimes it makes more sense to use a small script then to type out a large monster in C++ and sometimes I need a lower level of control so I usually write in C then tune in assembly)

I don't think C sucks. I don't think lisp sucks. BUT, I also don't think C++ sucks, and I am better with it than C or lisp so I use it more.

---

### Post by lnostdal on 2007-02-27
> **Mirrorball said:**
> I did move from C++ to Python, then a combination of Python and C++, then back to C++. C++ alone is faster than Python, simpler than Python and C++.

right; you didn't hit the threshold then

---

### Post by lnostdal on 2007-02-27
> **Wybiral said:**
> I also don't think C++ sucks

well, i do .. that's why i consistently avoid it and never recommend it for anything .. deal with me answering the OP

---

### Post by Slim Odds on 2007-02-27
Originally Posted by **g3k0**                     [[IMG]http://ubuntuforums.org/images/uf/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=2221635#post2221635")                 
                 which looks more complex?

printf ( "Hello %d Doo de dah %f" , operatorNum , myVariable );

cout << "Hello" << operatorNum << "Doo de dah" << myVariable;

> **yaaarrrgg said:**
> They look about the same to me (I spaced the first for you).  :)

Operator overloading is probably the more complex between the two, since the meaning of the symbols are constantly changing.  Especially, since the use of shift operators '<<'  and '>>' really makes no sense here.   

In terms of verbosity, there's not a lot of difference.  Personally, I prefer printf, since the other intermixes the presentation format with the data more.


Oh ya, well try changing operatorNum from an int to long or a float or a string and see which code is simpler.

---

### Post by RedSquirrel on 2007-02-27
> **g3k0 said:**
> which looks more complex?

printf("Hello %d Doo de dah %f",operatorNum,myVariable);

cout << "Hello" << operatorNum << "Doo de dah" << myVariable;

When I provided tacit agreement for the statement that "C++ is more complex" I meant that, taken as a whole, C++ is more complex than C because of the OO aspects and the additional syntax. I really don't see how anyone could disagree with that.

Some specific little things in C++ may be less complex than C, and your example *may* be one of those things (some wouldn't agree with you).

My earlier comment was to point out that one can start learning some C++ without having to learn all the OO stuff first, that's all.


> 
Umm.. I use ...methods. in structs... especially contructors ... havnt tried it in C though.. should work.... I think....
IMHO, using methods in structs, even in C++, is just bad style. On the other hand, using them in C is just plain *not allowed*.

> 
heh heh unless you want to do things correctly
Well, you clearly don't like C very much, and that's fine. Some people find learning C proceeds very much in the manner I described. Others don't. This is nothing new.

> 
ps.  Did you really need three posts?  Go beans..
Are you joking here? I'm having trouble discerning the tone you were using when you wrote this.

I made the first post. A few more posts had arrived while I was creating my post, and then I wanted to quote mavigozler, which I did. The only mistake I made was that I suppose I could have added my thoughts (through an edit) to my second post, but I made the mistake of creating a third post. Terribly sorry for the clutter. If I could combine them easily into one post, I surely would. I think I'm stating the obvious when I say that it is a lot easier to comment on a thread when it has settled down a bit. If no one has posted to a thread in quite some time, then it is easier to read through the whole thing, consider what you've seen, and then add a reply. That simply wasn't the case when I was posting. Oh, and one more thing: if I had delayed each post a little more, then there would have been some other posts in between my three and it likely wouldn't have looked as bad. I admit, when I saw the three back to back, I said: "OOPS!" or words to that effect. :oops:

> 
P.Sp.s.  If you are just learning I dont think you will be playing with low level programming
I'm not sure what you mean. Even if one is "just learning", they can use C to create simple programs. Not every C program has embedded assembly in it.

> 
p.sP.S.p.s look at this
Why? It's sort of redundant, isn't it?

---

### Post by g3k0 on 2007-02-27
> **RedSquirrel said:**
> When I provided tacit agreement for the statement that "C++ is more complex" I meant that, taken as a whole, C++ is more complex than C because of the OO aspects and the additional syntax. I really don't see how anyone could disagree with that.
 
The ability to do more doesn't necessarily make something more complex.  C++ provides many things which make programming simpler.

> 
Some specific little things in C++ may be less complex than C, and your example *may* be one of those things (some wouldn't agree with you).

Well some dont, it was just the first thing that popped into my head.  Something very basic and common.

> 
IMHO, using methods in structs, even in C++, is just bad style. On the other hand, using them in C is just plain *not allowed*.
 
Which is why I said I hadn't tried it in C when I posted.  I disagree that it is bad style.  Contructors are a wonderful thing.  I have seen my datastructures professor do some beautiful things wiith structs. (Doing it his way cut my code in half).  It is certainly not "bad style."

> 
Well, you clearly don't like C very much, and that's fine. Some people find learning C proceeds very much in the manner I described. Others don't. This is nothing new.

I am hoping it will be replaced soon.  But I dont think it will be leaving for a long while.

> 
Are you joking here? I'm having trouble discerning the tone you were using when you wrote this.
 
It's easy to edit.  I do i all the time.

> 
I'm not sure what you mean. Even if one is "just learning", they can use C to create simple programs. Not every C program has embedded assembly in it.

I know.  That was more along the lines of people saying "if you are kernel hacking doo dee dah use C"
> 
Why? It's sort of redundant, isn't it?
Well technically no, I am doing the opposite. But I see what you mean.
I thought I would point out how in c++ you do the same thing every time.

The C equivalent changes every time.  First you have do know whether datatype of the variable and what stands for it in a print or scan.  Then you have to know that the method requires the address of the variable hence the & before the variable name.  Except you dont use one for the char array because you have to know that the char string is actually a pointer because of the brackets.  Not things a new programmer would typically know.

I thought this example magnified it a little.

---

### Post by RedSquirrel on 2007-02-27
> **g3k0 said:**
> The ability to do more doesn't necessarily make something more complex.  C++ provides many things which make programming simpler.


Well, there's more than a grain of truth to that.

 > 
Which is why I said I hadn't tried it in C when I posted.  I disagree that it is bad style.  Contructors are a wonderful thing.  I have seen my datastructures professor do some beautiful things wiith structs. (Doing it his way cut my code in half).  It is certainly not "bad style."
Fair enough. I respect your opinion and that of your prof; I just don't share it. ;)

> 
I am hoping it will be replaced soon.  But I dont think it will be leaving for a long while.
Yep, there's more than enough old stuff to be maintained, at the very least.

---

### Post by runningwithscissors on 2007-02-28
Wow, look at all the mud-slinging.

Well, I personally prefer C. It is smaller, nicer and easier, and you can do everything with it.

Besides, OOP sucks and is only useful in certain, very limited cases. And the C++ code police are practically in love with it.

---

### Post by lnostdal on 2007-02-28
> **runningwithscissors said:**
> Wow, look at all the mud-slinging.
lol  .. reminds me: [http://redwing.hutman.net/%7Emreed/warriorshtm/howlers.htm](http://redwing.hutman.net/%7Emreed/warriorshtm/howlers.htm) .. very funny site

---

### Post by tehturkey on 2007-02-28
hm...ok thanks for all the replys guys. well i want to program applications not anything really low level because thats to hard for me :P

so i'll learn c++ i think. thanks very much. Links to tutorials/books are very welcome :)

---

### Post by Docter on 2007-03-26
If you are making something with a well defined design then C++ will suit your needs well. I tend to start with an idea then get little bits of the application working before moving on; tidying up, commenting and testing as I go. C is well suited to this approach.

OO is good for collaborative projects as everyone is working with the same level of abstraction (public classes). It is also good for complicated projects (once it's up and running). I suppose I'm saying OOP is more restrictive than non-OOP but sometimes that restriction is good.

I would certainly suggest learning basic C before embarking on C++ in any case.

---

### Post by Poisson_Pilote on 2007-03-26
I would suggest learning C first. Once you know C, basically you just need to learn OO to have C++.

You can't say that one language is better than another. C is great for system programmation, while C++ is great for complex applications (such as video games, etc). It's to different way of programming: object oriented (C++) or functionnal (C).

But basically I would recommend C first. However, if you have never programmed before, begin with Python. You'll need it, and it'll be a great introduction to programming for you.

---

### Post by samjh on 2007-03-26
> **tehturkey said:**
> hm...ok thanks for all the replys guys. well i want to program applications not anything really low level because thats to hard for me :P

so i'll learn c++ i think. thanks very much. Links to tutorials/books are very welcome :)

Good choice, although choosing C would not have done any harm.  Both languages have their place.

Here are two websites I strongly recommend:
[http://www.cprogramming.com](http://www.cprogramming.com) (excellent tutorials for both C and C++, from basic to advanced features)
[http://www.cppreference.com](http://www.cppreference.com) (website for looking up standard C and C++ classes, functions, key words, etc.)

A book that I very strongly recommend:
Accelerated C++ by Koenig and Moo ([link]("http://www.amazon.com/Accelerated-C%2B%2B-Practical-Programming-Example/dp/020170353X/ref=pd_bbs_sr_1/103-5670020-7251855?ie=UTF8&s=books&qid=1174915801&sr=8-1")) - a comprehensive tutorial style book that focuses on practical C++ skills, rather than language features.

Good luck, padawan.

---

### Post by rickardg on 2007-03-26
Whooa, the Return of the Living Dead... (erm, I mean Thread)

> **Poisson_Pilote said:**
> It's to different way of programming: object oriented (C++) or functionnal (C).


While C is low-level enough to allow programming in a [functional style]("http://en.wikipedia.org/wiki/Functional_programming") (using function pointer as higher order functions and avoiding side effects) or even [object oriented style ]("http://en.wikipedia.org/wiki/Object_oriented_programming") (rolling your own object system) style, it's usually classified as a [procedural ]("http://en.wikipedia.org/wiki/Procedural_programming") or [structured]("http://en.wikipedia.org/wiki/Structured_programming") language.

---

### Post by Poisson_Pilote on 2007-03-27
Oh OK. I never was aware of that. Thanks ;)

---

### Post by slavik on 2007-03-27
C, then C++ ...

C is a very small language ...

the first C++ compiler was only a C++ to C translator. X is written in C, yet it is object oriented.

object orientation places emphasis on having a function call for everything, to the point where every function calls another function with slightly modified parameters.

---

### Post by g3k0 on 2007-03-27
Don't learn C first.  It is evil.

---

### Post by Wybiral on 2007-03-27
> **g3k0 said:**
> Don't learn C first.  It is evil.

I've actually become quite fond of C recently, more so then C++ (which is weird because I used to be a diehard C++ addict).

It does produce smaller executables and the assembly output is very clean and logical (unless C++'s which is often a mess).

---

### Post by lnostdal on 2007-03-27
> **g3k0 said:**
> Don't learn C first.  It is evil.

Whereas C++ pretends not to be. I'll take the honest evil ******* over the lying evil ******* any day.

---

### Post by thethawav on 2007-03-27
Definately C - faster and much more sufficient for smaller projects.
If it gets more complex you should stick with c++

---

### Post by silas_irl on 2007-03-27
It's down to a matter of choice really, huge projects can be written in C quite efficently.

However if you feel that you need the power of OO and the extra functionality of C++ then by all means use it.  I actually prefer C, I feel it's a nice language, it does exactly what it's supposed to do, and the generated code tends to be quite small and fast.

---

### Post by Wybiral on 2007-03-27
Keep in mind that up until doom 3, all of ID's game engines were written in C... And those are certainly not small projects. So C can definitely handle large projects if you're wise about your implementation.

---

### Post by silas_irl on 2007-03-27
> **Wybiral said:**
> Keep in mind that up until doom 3, all of ID's game engines were written in C... And those are certainly not small projects. So C can definitely handle large projects if you're wise about your implementation.I actually seen the source code to their original doom game engine, assembly and C. There was no OpenGL in them days, direct writes to the video buffer.

---

### Post by pmasiar on 2007-03-27
> **Wybiral said:**
>  So C can definitely handle large projects if you're wise about your implementation.

eh - let me think - large projects like kernel? Can C handle those too? :-)

"C is evil" is so obviously flamebait and bad advice - but troll won again.

---

### Post by g3k0 on 2007-03-27
> **pmasiar said:**
> eh - let me think - large projects like kernel? Can C handle those too? :-)

"C is evil" is so obviously flamebait and bad advice - but troll won again.

Kernel? Well yes C is used.  Here is an article that talks about openBSD and the vast amount of buffer overflow problems
[http://www.gratisoft.us/todd/papers/strlcpy.html](http://www.gratisoft.us/todd/papers/strlcpy.html)

C is evil. ;-)

Not to mention I have already posted many reasons why it is evil in earliier posts.  I chose to not repeat myself.

---

### Post by Wybiral on 2007-03-27
Other languages can have overflow problems too...

C is evil, compared to what?

---

### Post by g3k0 on 2007-03-27
Certainly, but the C language is by far the most susceptible.  Unless of course you are writing in assembly, but then thats not really a high level language and you have to tell it just about everything you want it to do....

As far as what is evil... All technology is evil, but C is the dictator over the evil empire.

---

### Post by Wybiral on 2007-03-27
Or you can just be careful and use strncpy instead of strcpy... And other methods of preventing overflow.

---

### Post by g3k0 on 2007-03-27
Strncpy is difficult to use correctly. It's not for the faint of heart.  That is why strlcpy was added as standard to OBSD.  The problem is that the c standard library is full of problems like this.  These are just the best example.  The only reason I mentioned it again is because I was accused of trolling even though I had already posted many reasons.  Plus I thought it would be effective to point out the problems with C since the kernel was a reason someone stated C is so great.

---

### Post by pmasiar on 2007-03-27
> **g3k0 said:**
> Strncpy is difficult to use correctly. It's not for the faint of heart. 

I agree. If you said "memory management in C is hard to use correctly" we would not have this useless discussion. But you choose to state "C is evil". It still looks like a flamebait to me, after all your explanations. After such comment, I classified you as a "flamebaiter with windows logo in avatar" and would be tempted to skip your comments. Maybe it was not just, but life is not just.

IMHO technology cannot be evil, it has no emotions. Might be hard to use, obscure, obsolete, whatever. C is best tool for some kind of jobs, I take Linus opinon over yours :-)

If my C code is simple and I do not have to juggle dynamic memory allocation, life with C is much simpler than C++, no? But I still prefer Python :-)

---

### Post by hod139 on 2007-03-27
> **g3k0 said:**
> Strncpy is difficult to use correctly. Difficulty is certainty no  not for the faint of heart.  That is why strlcpy was added as standard to OBSD. 
What is difficult about strncpy? Difficulty is not why strlcpy was added as a standard to OBSD.  It was added because 
1) strncpy does not NULL terminate the destination string, even though many programmers mistakenly think it does
2) If the number of chars to be copied is smaller than the size of the destination string, strncpy zeros out the remaining characters, which is a performance hit
3) The API is not consistent with other string functions, the size parameter passed to strncpy is not the size of the string, but the amount to copy.

To use strncpy correctly, just do
```

strncpy(dest, src, N ); // N is number of chars to copy, usually sizeof(dest)-1 but may be **smaller** if desired
dest[N] = '\0';  // Null terminate the dest string.  Note, the length of the string need not be the size of the array

```

---

### Post by Wybiral on 2007-03-27
The only thing you have to worry about with strncpy is the null terminator, so... Just make your buffer 1 byte bigger then you need for text and it's not a problem... At all.

There is also memmove and memcpy that are very similar and incredibly easy to use.

---

### Post by g3k0 on 2007-03-27
strncpy(path, homedir, sizeof(path) - 1);
path[sizeof(path) - 1] = '\0';
strncat(path, "/", sizeof(path) - strlen(path) - 1);
strncat(path, ".foorc", sizeof(path) - strlen(path) - 1);
len = strlen(path);

--------------------------------------------------------------------------------

strlcpy(path, homedir, sizeof(path));
strlcat(path, "/", sizeof(path));
strlcat(path, ".foorc", sizeof(path));
len = strlen(path);


All of the sizeofs in the first make me dizzy.  The fact that it doesnt match with the way the parameter is passed is a huge problem.  Users assume otherwise and create nasty bugs.     The null termination can easily be forgotten as well.  Because of this, it is difficult to use.  We are in agreement of why it was added.  I just classified it under difficult rather than listing.

I think the fact that you failed to ensure N is not greater than sizeof-1 shows that it is difficult to use. :)   And strncpy is the easier of the two to use. Why not use that instead it looks worse.

**But strcpy and strcat are still used like they are going out of style  Why is it part of the C standard liibrary?**

Arguing this is silly I provided a major example of where this occurred after it was used by someone else as a great C program example.  **It obviously occurs**.  Sure you can find ways around it, which are difficult.. Sure you can row a boat across the pacific ocean, but a yacht is nicer.  

P.S.  I actually dislike windows.  Ever heard dont judge a book by its cover?  I just like the avatar.  Not to mention it is a linux penguin who has the vista colors.  I did it in the spirit of vista when it came out.  I dont even own vista.  I generally boot up in linux unless I want to play a decent game.  But lets not get sidetracked shall we?  If anyone is flamebaiting it is your accusations and bringing my avatar into this.  

Maybe the penguin ate vista?

lol? C is the best language for some kinds of jobs? Sure but then again just about every programming language is the best language for some kinds of jobs.  I agree with good ol' linus.  Hes a good guy! He wrote what... 1% of the kernel?  just a guess..but im sure im close. 99.8% of statistics are made up on the spot!

Also perhaps I didn't mean evil literally? lol

---

### Post by Wybiral on 2007-03-27
Exactly what flawless languages do you suggest over C then?

Every language has their quirks, that doesn't make C evil. Very few languages can compete with C in terms of optimization and speed, so I'm willing to deal with those quirks.

And you pointed out... ONE problem with C which certainly does not justify it as evil. It's a commonly known fact that strcpy attributed buffer overflow is dangerous and C programmers don't just use it wildly. And if they do, then they are idiots, but that doesn't mean C is a bad language.

You could type "sudo rm /home" and lose all of your work... But that doesn't make Linux a bad OS. You just know not to do that, so you avoid it.

---

### Post by nfm on 2007-03-27
If it still matters to tehturkey,

I'm a high school student, I'm taking second semester of java programming class. I first came in contact with computers 5 years ago when I was about 13 years old. I was always interested in computers and I wanted to know how programming works, my main goal is to be in control of my PC, to know how this creature works. I'm a person who sees computers pointless when somebody does not know how to program anything, only he or she can click the mouse.  I started to learn C about 4 months ago, before that I written xhtml with css webpage, knew littlebit of cmd scripting. I bought "The C Programming Language 2nd Edition ANSI" book and I am on page 132. In addition I completed a C Programming Language video tutorial from [http://www.vtc.com/](http://www.vtc.com/) which took me three weeks.

The reasons I chose C is because:
- It is very fast, portable and relatively small.
- It is very dangerous when misused, which is what I like the most about C.
- I can play with RAM directly, C makes no restrictions, I can abuse it, crash other programs :\ this is very powerful, you also access for example your graphics's memory pointing to it with a pointer.
- I mastered use of pointers, pointers to functions and structures, pointers to pointers, pointers to array of pointers, I like it because it is something I never seen in Java, they make your code very efficient, allow you to modify parameters in functions.
- Pointers and arrays are interchangeable, this gives you power.
- Syntax is elegant, makes sense, pretty easy to remember, many language such as Java, PHP, C++ adopt C's style.
- There is very good documention on C, also gcc compiler is excellent.
- Large amount of libraries exists that can you use with your program, some of them that come as a feature of other languages such as C++, in that case you use extra libraries for something that hasn't been implemented in C.
- GTK+ is perfect for graphical interface if I ever wanted to create one.
- It's from 1972, OPP didn't exist then, and it's a good thing, OOP is a good way to waste memory
- Programs like ffmpeg, x264, mplayer, Linux Kernel are written in C, which is my main interest, I can't study those programs if I don't know C.

I have seen people saying that C is evil, I don't find using free() function or manipulating strings difficult in C. I never created a program that leaked any memory. It is a rule to free up memory that you dynamically allocated, if not then you're a bad programmer. It's not like the memory leaking is a feature of a C language, It's the stupidity of a programmer not doing what is supposed to be done. All that people say is a good pretext to support their sentence.

I'm pretty sure that this is the language I will stay with, my next goal will be to learn to use nasm, to be able to code simple straightforward loops, any type of heavy calculations that can be combined with C, which is what many encoders and decoders do.

This is all that I can tell you from top of my head, there are a lot of more great things about C and it's pretty ironic that I haven't pointed out any disadvantages of C, they don't exist to me :mrgreen:
So I would say, stick with C.

---

### Post by Wybiral on 2007-03-28
> **nfm said:**
> - I mastered use of pointers, pointers to functions and structures, pointers to pointers, pointers to array of pointers, I like it because it is something I never seen in Java, they make your code very efficient, allow you to modify parameters in functions.


I agree... Pointers are a force to be reckoned with! They hold some power in their hands.

---

### Post by angryfirelord on 2007-03-28
Hmm, I'm surprised no one has made a recommendation to Java. The whole intention of its invention was to greatly improve upon C. Plus, it's a little more cross-platform than C++ as long as each computer has a JVM installed.

At the console level, coding in C, C++, & Java look very similar but once you build gui apps, it gets a little finicky because there is no one standard gui tool for C or C++. Java uses Swing on any system.

---

### Post by samjh on 2007-03-29
> **angryfirelord said:**
> Hmm, I'm surprised no one has made a recommendation to Java. The whole intention of its invention was to greatly improve upon C. Plus, it's a little more cross-platform than C++ as long as each computer has a JVM installed.

At the console level, coding in C, C++, & Java look very similar but once you build gui apps, it gets a little finicky because there is no one standard gui tool for C or C++. Java uses Swing on any system.

This is a C and C++ thread.  Hence the reason why no-one had recommended Java. ;)

---

### Post by angryfirelord on 2007-03-29
> **samjh said:**
> This is a C and C++ thread.  Hence the reason why no-one had recommended Java. ;)
Well, I figured that since C, C++, & Java are so closely related that it would have sprung up somewhere but yes, I see. :oops:

---

### Post by Docter on 2007-04-02
Objective-C is pretty much ignored outside of Mac circles but it is a very nice OOP implementation. It is, in fact, what Java was based on.

If I went 'objective' I'd go for obj-c over c++... but that's just me I guess.

---

