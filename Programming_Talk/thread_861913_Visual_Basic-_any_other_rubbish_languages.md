---
title: "Visual Basic- any other rubbish languages?"
date: 2008-07-17
forum: Programming Talk
---

### Post by lordhaworth on 2008-07-17
Im only really familiar with C and Fortran90 so this may be part of the trouble...
But isnt visual basic (VB) (in conjunction with access) the worst thing in the world ever?

I need to write a load of queries-but dont want to make loads of individual ones, so i thought id make a module in access ok... so i make a case statement for each of the queries (triggered by users selection) and then wanted to paste the SQL that would be in each of the many queries into each case using DoCmd.RunSQL (Inserts SQL)
However who in their right mind designs a command the lets you do anything (Insert update delete) a structured query langauge can do except run a query (SELECT Command doesnt work). My simple program is now getting quite complicated as i, a VB noob, try to get it to perform a standard access operation.

Anyone got any ideas- im sure your probably above this language, but this forum is the best ive ever encountered for actually getting help and responses! 

If not, anyone got any other langauges they think are lacking something?

---

### Post by LaRoza on 2008-07-17
That is VBA (Visual Basic for Applications).

The BASIC's are RELICs now. 

Other rubbish languages would be [MUMPS]("http://thedailywtf.com/Articles/A_Case_of_the_MUMPS.aspx")

---

### Post by themusicwave on 2008-07-17
I really sympathize with that MUMPs guy....

Much like him I recently got my first programming job(last year) and I was really excited to be doing development.  I was a week out of college(B.S. in Software Engineering) and I took the job because it was one of a few offers that wasn't Application Analysis or Testing.

I was told it was primarily a C# position.  Not my first choice of language, but I knew it well enough so I took it.

Then I started and I was presented with this thing called [Indusoft]("http://www.indusoft.com").  It's a system to make creating applications for industrial environments easy!  Instead it makes them a nightmare.

There are two choices of language, their proprietary Indusoft script and VBScript, which is more powerful than theirs. That's right, VBScript is actually MORE powerful than something...

To make matters even worse it is actually a crippled form of VBScript that has to fit into their rules.  The rules are as follows:

[LIST=1]
[*]The only persistent variables you can create are int, string, float and bool.
[*]Persistent arrays may only be one dimensional.
[*]You may build structs, but they may only contain int, float, string and bool.  No they may not contain arrays or other structs.  However, you can make a 1 dimensional array of your struct type.
[*]Everything that is persistent is global.
[*]You get one and only one thread.  If an operation needs to  wait everybody waits. This includes the GUI.
[*]GUIs may only use bitmaps.  
[*]Only ODBC and ADO database connections are supported.  You need both because in some places only ODBC works in others only ADO works.
[*]The IDE does not have a find/replace function
[*]The IDE does not have a select all function
[*]The IDE's syntax checker never catches errors
[*]The IDE's runtime error reporting tells you there was an error, but not which line it is on or which one of the 500 scripts it occurred in.
[*]Several of the tools in the IDE don't really work, they just break things.
[*]You can only use their IDE.
[/LIST]

The list goes on, but lets just say it sucks.  There is no architecture to the system.  The last guy bailed after building 10 modules that were "80% done".  Which means I inherited a huge mass of non functioning buggy code that didn't work at all.

We are now in year 3 of what was supposed to be a 1 year project.  We are also over budget by a whole lot of money.  I'm the only developer left who knows the system and I have begged them to switch to something else like Java.  They keep putting it off and now I am thinking of leaving....

So add VBScript and Indusoft Script to that list...

Edit Forgot something:

The Script editor in the IDE is awful.  When editing some code you get nothing but a 20 character text box.  I have scripts that are about 15 lines long all compacted into one line and in a 20 character text box.  I edit them by pasting the contents into notepad, uncopacting it, editing it, re-compacting it and pasting it back in.  If I make a mistake I do it again and again...

So I get fun filled statements like this:

[PHP]if($variable[$othervariable]=$somevalue,if($variable[$othervariable]=$somevalue,if($variable[$othervariable]=$somevalue,1,0),0),0)[PHP]

Except it would be about 25 if statements nested....Their sytax for if is:

If(condition,then code,else code)  it gets fun when you nest them...

---

### Post by pmasiar on 2008-07-17
> **LaRoza said:**
> Other rubbish languages would be [MUMPS]("http://thedailywtf.com/Articles/A_Case_of_the_MUMPS.aspx")

[MUMPS](http://en.wikipedia.org/wiki/MUMPS) was excellent language allowing to solve real-world problems back in times where 300 baud modem was state of the art, and relational databases were academical theory.

If all you have is 300 baud, you do not want to pass something as verbose as java over the wires, or do you? Single - char abbreviations made perfectly sense for the environment back then. It does not make sense now of course - specifications changed, what else is new?

---

### Post by Felson on 2008-07-17
I would say that to flat out call anything a "rubish" language is a bad idea. Most languages "have there place". VB, for instance, is good if you need to write a very simple app with a GUI made for winblows. You can use it to bang out allot of really short simple apps in a short amount of time. If your program gets complex, then it is definitely not the tool for you. I personally learned to hate it right after I got out of collage. We built a system for controlling lumber drying kilns with it. It "worked" but was plagued with stupid things like randomly jumping to a different execution point in the code. But, even after that, I am willing to admit that it has it's place. A very small place, but it has one. :D

---

### Post by LaRoza on 2008-07-17
> **pmasiar said:**
> [MUMPS](http://en.wikipedia.org/wiki/MUMPS) was excellent language allowing to solve real-world problems back in times where 300 baud modem was state of the art, and relational databases were academical theory.

If all you have is 300 baud, you do not want to pass something as verbose as java over the wires, or do you? Single - char abbreviations made perfectly sense for the environment back then. It does not make sense now of course - specifications changed, what else is new?

"was". What about the people NOW that have to maintain it :-)

---

### Post by pmasiar on 2008-07-17
> **LaRoza said:**
> "was". What about the people NOW that have to maintain it :-)

It's business decision: what makes more sense: reprogram say 40MLOC (which work) or add a little patch? Exactly like with COBOL. Nothing personal. People who know how to maintain it can ask for market rate salary. I am still asked to return back to PROGRESS4GL - and I may prefer it over Java, if I have to return to industry.

---

### Post by lordhaworth on 2008-07-17
The problem i have with VB (VBA) and im assuming i would have with some other object oriented programming languages is that if i want to do something id rather just build it myself now. In my brief experience the online help is naff for VBA- its full of people asking the same questions as me with no response! 

I guess ill have to get used to it

---

### Post by themusicwave on 2008-07-17
> **Felson said:**
> I would say that to flat out call anything a "rubish" language is a bad idea. Most languages "have there place".

Well said, most langauges do.  Even my awful Indusoft Platform does.  It would be useful for a small application.  It also already includes all the networking drivers so that would save some time.

The problem is when people apply the wrong language to the task.  Our system is not small, it is an unholy mess that is huge.  The platform was never meant to handle that.  Last time I called their tech support, the tech actually said "Wow I didn't know you could have that many scripts!  I've never heard of a system so big!"  That's when you know you chose the wrong tool.

VBA is the same way, for some things it is an ugly monster, but for a small subset of applications, it actually makes sense.

If the tool is sized to the task it can never be rubbish.  Although some tools are much better than others.

---

### Post by stevescripts on 2008-07-17
> 
The problem is when people apply the wrong language to the task.


@themusicwave ... Well said

Steve

---

### Post by LoneWolfJack on 2008-07-17
um.... Python? ;)

As for VB and while I would be the last to stand up for Microsoft it has it's pro's. If you understand programming in general and need to build a quick&fast solution that doesn't need to work for more than a fist full users, it can save you a lot of development time.

Now if VB .NET wasn't OO, I would almost consider to continue offering VB programming...

---

### Post by LaRoza on 2008-07-17
> **LoneWolfJack said:**
> 
As for VB and while I would be the last to stand up for Microsoft it has it's pro's. If you understand programming in general and need to build a quick&fast solution that doesn't need to work for more than a fist full users, it can save you a lot of development time.


I have said on this forum that VS and VB.NET are highly advanced tools for experienced programmers.

---

### Post by Mickeysofine1972 on 2008-07-17
[LEFT]I think PYTHON is the new Visual Basic for linux! 

Just kidding peter you can relax......or am I?:)

Mike
[/LEFT]

---

### Post by StOoZ on 2008-07-17
there are NO rubbish languages , each languages has its own task, and you choose the languages by the project and not vice versa.

---

### Post by drubin on 2008-07-17
Take a look through some of these :)
[http://ubuntuforums.org/showthread.php?t=497579](http://ubuntuforums.org/showthread.php?t=497579)

---

### Post by lordhaworth on 2008-07-20
Yeah you all have valid points, even i am now getting used to VBA.
I think what i found was that I had come from languages where if i want to do something i just build it myself. Although when VBA works its great, i dont really like searching for a command that will let me do what i know what i want to do, and then have to search (often longer) for the correct syntax etc. 

However... once you know those commands everything does work very well, so rather than knocking VBA, I am now just knocking its online texts and tutorials - because so far the only way ive solved most of my problems is through a forum, (credit to those at VBForums)

---

### Post by techmarks on 2008-07-20
> **Felson said:**
> 
I would say that to flat out call anything a "rubish" language is a bad idea. Most languages "have there place".:D

There's the totally useless and rudely named Brainf***, what gets me is some people actually take this useless and offensive joke of a "computer language" seriously, you know what PT Barnum said about certain types being born every minute.

---

### Post by knalle on 2008-07-20
Java :-)

When it first came out it was pretty lacking, falling between JavaScript and C. Nobody took it serious either (some still don't), not before Servlets came along. And Applets :-) ah, I remember Applets...

---

### Post by rabatitat on 2008-07-20
Aaaah... VB...

Quick and easy... That's about it.

I wouldn't use it for anything more than user input/output though... Which, for me, is what it is most suited for...

I agree with languages having their own purposes.

Would you use a wrech to drive nails if you had a hammer lying around?

---

### Post by pmasiar on 2008-07-20
> **techmarks said:**
> There's the totally useless and rudely named Brainf***, what gets me is some people actually take this useless and offensive joke of a "computer language" seriously, 

Joke is on you.

There is whole group of [http://en.wikipedia.org/wiki/Esoteric_languages](http://en.wikipedia.org/wiki/Esoteric_languages) created to be confusing - for fun, and because hackers can.

---

