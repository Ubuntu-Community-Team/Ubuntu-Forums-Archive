---
title: "programming hurdles"
date: 2008-01-27
forum: Programming Talk
---

### Post by rendon on 2008-01-27
What have been your biggest hurdles to overcome when learning programming?

I'm curious about what people think is the most difficult, time-consuming aspect of programming in general.

Before I knew what I was doing, I was digging deep into a C++ book that I bought from Barnes and Nobles back in 1999, I learned everything from loops and conditions to arrays and classes in that book, although I didn't understand what a class was and it took me a long time to understand why I would need classes to make a program...

About that same time, I met someone who said "reading, writing, and saving to a disk, that's all you need to know!".  And it dawned on me that I wasn't saving any info at that time, so I got into the exciting hobby of writing info to files, and recalling it the next time I ran the program.  But still didn't find this challenging!

After 8 years of programming, and now being a web-based developer for a small company with experience at creating 3 or 4 dynamic websites and managing a server (Ubuntu server btw :) ), I would say the following were my biggest hurdles to overcome to get me where I am in programming today:

1) anything dynamic!  classes, nodes, polymorphism, Java's inheritance, etc.  These these are not only big brain-teasers, but very difficult to put into a real-world situation until you are actually working with people together.  I think you either need to write the same function over and over a hundred times until you realize that  you can just store it in some type of class and call it, or, you need to be working for somebody who is constantly changing their mind about how they want things to work before you finally realize that you save time by doing things dynamically...

2) STRING PARSING!  got that database organized?  is your XML flawless?  no it's not!  because here comes Mr. Javascript!  He's going to change the encoding and capitalization of all your html without you knowing it!  And Mr. PHP doesn't like the & symbol input here and there, it will ruin the script!  did you know that PHP is going to automatically store that XML as utf-8?  Whatch out for Mr. Foreign Language!  He might visit your site and give your database a crash or two!  

String parsing has by far given me the most headache of my life.

Mind you that 8 years ago PHP and/or even Perl were a lot different than they are now.  And I believe even the structure of C++ has change a lot then.  I remember spending days trying to get C++ to take a string and turn it into what I wanted,...  perhaps only to find out that the compiler I was using wasn't good, then going on a mission of the quest for the ultimate compiler, only to end up back where I started! :)

I also recall trying to use Perl to get some POST or GET data, it was expected that you understand a line of REGEX to get rid of all of the erroneous data that came through the browser.  something that would look like (s/fgs(*&#$j43kl;.a/ss8349(*NF#$) was supposed to be the new EASY way to parse that line!  And just because it worked on one server didn't mean it would work on another one!

currently, my favorite (or most used) languages are: python, PHP, javascript, java, and Flash actionsript (although maybe not an official language, but you'd be surprised what you can do with it).

Please understand my complaining is also based on a large lack of education, I taught myself all of these things with nothing but books, tutorials, and forums.  So I suppose it's just me learning the hard way sometimes.

Anyway, I hope you can share some of your hardships here for venting or educational purposes!

I'm new to this forum, hope to stick around and become part of the community.  Been using Ubuntu for about 2 or 3 months now and enjoying the experience very much!

---

### Post by LaRoza on 2008-01-27
Besides the "normal" programming concepts (data structures, code, syntax, logic, etc), these are the hardest things for me:

* Comments, I do them when I can, but I write them for myself, so when I share code, I have to recomment or explain

* variable names, I have a consistant and logicaly way of naming variables which is usually forgotten in the early morning, when I have code with one letter variables not as counters

* function names, PHP has caused me to give functions weird names, which is a habit now.

* Once you learn that Wikipedia and google are there, most challanges in learning are solved.

Learning how to manage projects is a big thing, especially for self taught people like us.

---

### Post by pmasiar on 2008-01-27
> **rendon said:**
> 
String parsing has by far given me the most headache of my life.

Looks like XML parsing is the problem. Yes, hand-made XML parser is sucker's game, just say no. Python has very intuitive (IMHO) XML parser, ElementTree, which completely changed game for me. It just makes sense. Still, when I wanted to modify parsed tree, it was not easy and not worth the time. XML is simple but not easy, as any recursive data structure. 

> I also recall trying to use Perl to get some POST or GET data, it was expected that you understand a line of REGEX to get rid of all of the erroneous data that came through the browser.  something that would look like (s/fgs(*&#$j43kl;.a/ss8349(*NF#$) 

Seems like you are talking about handling "tainted" data in Perl. If fact, having that -T switch is great, and I miss it in Python. Of course regex syntax being that it is, regex expressions are notoriously hard to read. Goal was not readability but power.

> I'm new to this forum, hope to stick around and become part of the community.  Been using Ubuntu for about 2 or 3 months now and enjoying the experience very much!

Sure, welcome aboard. If you behave according to conduct rules, you will have no problems. If not, you will (as I learned :-/ )

Be careful with taking part in flamewars, they start almost innocent and then you are sucked in by your eagerness to explain your point better and make the other guy to understand and change his mind (it is always guys: I noticed that females are not as susceptible to this kind of ego trip). 

See also [Devil's dictionary](http://sunsite.berkeley.edu/Literature/Bierce/DevilsDictionary/A-E.html) 
DISCUSSION, n. A method of confirming others in their errors.

:-)

We are due for some flamewars soon, none was for quite a long time - almost suspicious :-)

---

### Post by scruff on 2008-01-27
Interesting thread. I would say for me, getting my head around true OOP was the biggest challenge. There's a lot of info to absorb, and most of the terms and theories seem completely cryptic until you've read/used them a hundred times or so.

Also, statically typed languages. I began with Perl 8 or so years ago. Since, I've used BASH, Python, C#, C++, PHP... My first foray into C was with the K&R bible, but it was tough to grasp coming from Perl. My job forced me into C# for one project so that was a nice in-between to help me with the jump to something like C or C++. C# is gentle enough that it was fun to learn, and enough like C or C++ to make that transition seem much less like work :)

---

### Post by LaRoza on 2008-01-27
> **pmasiar said:**
> Looks like XML parsing is the problem. Yes, hand-made XML parser is sucker's game, just say no. Python has very intuitive (IMHO) XML parser, ElementTree, which completely changed game for me. It just makes sense. Still, when I wanted to modify parsed tree, it was not easy and not worth the time. XML is simple but not easy, as any recursive data structure. 

Be careful with taking part in flamewars, they start almost innocent and then you are sucked in by your eagerness to explain your point better and make the other guy to understand and change his mind (it is always guys: I noticed that females are not as susceptible to this kind of ego trip). 

We are due for some flamewars soon, none was for quite a long time - almost suspicious :-)

You can also use the DOM (my preference for what I do) and SAX.

Flame wars will be more fun in the future, 

[quote="Megadeth"]
Tremble you weaklings,cower in fear
I am your ruler,land,sea and air
Immense in my girth,erect I stand tall
I am a nuclear murderer I am [color="red"]LaRoza[/color]
[/quote]

---

### Post by rendon on 2008-01-28
> **pmasiar said:**
> Looks like XML parsing is the problem. Yes, hand-made XML parser is sucker's game, just say no. Python has very intuitive (IMHO) XML parser, ElementTree, which completely changed game for me. It just makes sense. Still, when I wanted to modify parsed tree, it was not easy and not worth the time. XML is simple but not easy, as any recursive data structure. 


Well, that's just a recent problem, I've also spent years using sed in bash scripts and XML wasn't as popular or "common" back in the day when I was making my first website forum.  Although SQL was probably around, I didn't know it at the time and ended up making rather complex flatfile systems... usually separated by lines and keywords.  Now sometimes a line is \n and sometimes a line is \r, and sometimes I need to split a string to get info and so on...  a lot of languages don't have such wonderful string parsing tools and/or they are always just good enough up to a "certain point"...  an example would be the previously mentioned PHP dom, I've become very familiar with the simple xml dom, it's a handy little tool!  but seems to have some limitations.

Python IMO is the savior of this realm!  Python really gives access to just about every possible combination of string search, char search, and general manipulation of data as you need it on the fly.

Another string example would be my chinese english translation tools (brendon-art.com/china).  I spent a week trying to get PHP to separate the chinese into individual characters.  In the end the only work around I could find was using javascript to split the characters before submitting the post.  To this day I don't know why php can't do it.

anyway, trial and error... :)

---

### Post by walkingbeard on 2009-02-01
I know this an old thread but:

My number 1 programming problem is that I struggle to practice in a way which actually teaches me to programme.  I learned C and C++ several years ago, but programming something as simple as Tetris is a real headache for me and I struggle to visualise _the programme itself_.

I basically can't see the woods for the trees.  Source code that comes in twenty different files is too much for me - I just don't have the experience of programmes that large.

---

### Post by jimi_hendrix on 2009-02-01
OOP and string parsing + 1

while i understand the latter i am not good at it

---

### Post by sujoy on 2009-02-01
> **walkingbeard said:**
> I know this an old thread but:

My number 1 programming problem is that I struggle to practice in a way which actually teaches me to programme.  I learned C and C++ several years ago, but programming something as simple as Tetris is a real headache for me and I struggle to visualise _the programme itself_.

I basically can't see the woods for the trees.  Source code that comes in twenty different files is too much for me - I just don't have the experience of programmes that large.

same thing here. and i always thought moving higher up the abstraction ladder would help me somewhat, but starting with C, here i am at python and yet no clue whatsoever as to how to read those source codes. :(

---

