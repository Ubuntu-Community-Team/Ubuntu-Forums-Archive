---
title: "Clash of the titans : Java vs. Python"
date: 2005-07-27
forum: Programming Talk
---

### Post by dmccarney on 2005-07-27
Now I know this may seem a bit redundant with all of the posts about the strenghts of Python and the comparisons drawn towards Ruby etc but I've found that there is little to no comparison to Java.

I have about 3 years casual experience with Java and with all of the Ubuntu hype about Python and I'm considering investigating it as an alternative.

Both are interpreted instead of compiled and everyone seems to point towards Python being much easier and more productive/time-saving but I've yet to see many concrete examples of this,

I've found the provided Java classes to be excellent in speeding up development of many hobby projects so perhaps someone could mention the pros/cons of the Python libraries in comparison?

Now without breaking into a flame-war could someone provide some examples of the benifits of using Python as compared to Java? I realize it would probably also depend alot on what you are trying to do with each, but perhaps someone could list a project that they would prefer to use Java for and a project they would prefer to use Python for and the reasoning?

Has anyone used Jython? Anything to say about that? Combining the two languages sounds interesting but is it really worth it?

One limitation: I'd prefer if the discussion was just limited to Python+Jython and Java , I realize there are a lot of other languages floating about and I'm sure alot of people would be gung-ho about recommending C, C++, LISP, Scheme, Assembler, whatever, but this is a post regarding Java and Python.

I hope I'm not asking too much of the Programming Talk community ;)

---

### Post by NoTiG on 2005-07-27
Speaking as a programming newb... From what i have read the advantages of using Java over Python would be that java is more suited to do web programming. I think a more relevant comparison to Java would be mono... or more specifically C# or Ironpython. Im not really sure though.......

---

### Post by dataw0lf on 2005-07-27
Let me say beforehand that I don't have much experience with programming in Java.  I tried, and tried, and tried to use it, but I just can't get over numerous things about the language.  So I'll just make a single argument here that I think is the most important one.

Python allows both functional and object orientated programming;  Java forces OOP onto you.  Don't get me wrong;  I use OOP quite a bit.  However, OOP is a design methodology;  it's not the answer for everything.  This alone turns me off of Java.  Python's freedom of 'purity' and willingness to compromise is one of it's best features.       Python's features all make sense;  the developers don't shoot themselves in the foot by adhering to one methodology.  

That's my spiel. People who know Java better can likely make a clearer, better argument, but this is one of the major reasons why I love Python.

Python Uber Alles!

---

### Post by dmccarney on 2005-07-27
I've never had much of a problem with the OOP Paradigm since I've never done much programming that wasn't OOP. I'm accustomed to it now so I'd probably struggle switching to procedural programming now. 

As for Java being primarily a web programming language, I think that in today's Computer Science world that isn't very true at all. Back in the day sure Java Applets were at the forefront of the World Wide "Interweb". Today however I think that most of things Applets did well Flash has replaced.

Java Server Pages is quite useful in terms of web programming but that's more of an extension of Java (in my opinion).

I've never worked with C# but I would still imagine it is more comparable to C or C++ and neither of those are really web-programming languages either.

When I think web-programming language I think ASP/ASP.net, PHP, etc...

Thank's for the input though guys. Especially you Datawolf. I didn't even realize that Python allowed for procedural programming.  :)

---

### Post by LordHunter317 on 2005-07-27
> **dmccarney]Both are interpreted instead of compiled[/quote]Careful here.
Python  can be both source interperted (meaning, the code your write) and bytecode interpreted (meaning the source is compiled into a bytecode that isn't the machine language, that's then translated to machine code at runtime).  Java can only be bytecode interpreted.

I can actually think of an exception of that for Java (beanshell), but it's not useful for general use.

> and everyone seems to point towards Python being much easier and more productive/time-saving but I've yet to see many concrete examples of this,Depends on what you're trying to do.  Python's generally considered quicker for prototyping.

[quote=dataw0lf]Python allows both functional and object orientated programming said:**
> And procedural ;)

Java supports a form of functional programming, but functions aren't first class, so it's not a functional language.  But you can do similiar things, at a much higher and complicated level, unfortunately.

> Python's freedom of 'purity' and willingness to compromise is one of it's best features.If you're trying to imply Java is a pure language (I'm not sure if you are, but if you are...) it's not.  While the language itself is reasonably pure OOP, the standard API that comes with it is probably how to write the book on how to break OOP practices and principles, and the value of compromise.  And consdiering just the language isn't useful in any practical terms, unless you intend to provide a completely different standard API.

Really.  The collections is a perfect example of this.  It's not really OOP (classes aren't required to meet the promises they make), and you have behavior that doesn't make any sense on certain classes: linked lists aren't indexed, so I shouldn't be able to do indexed lookup, yet such behavior is part of the List interface.

[quote=dmccarney]As for Java being primarily a web programming language, I think that in today's Computer Science world that isn't very true at all.Yes, it is.  It's used primarily on the server side.  Ever see a site with a .jsp or .do extension?  That's using Java on the server load to generate the pages you see.

The J2EE standard is largely about creating server-side web applications.  Most of the rest is connecting those web applications to other parts of an application: the database, other web applications, etc.  The rest is well, crap (*cough* EJBs *cough*).

> ava Server Pages is quite useful in terms of web programming but that's more of an extension of Java (in my opinion).It's not an extension, it's part of the offical J2EE standard.  It's offically part of Java.  It's not part of the Java you'll see installed on an end-user's desktop, but it doesn't have to be, either.

> ve never worked with C# but I would still imagine it is more comparable to C or C++ and neither of those are really web-programming languages either.C# has more in common with Java than it does with C or C++.

> When I think web-programming language I think ASP/ASP.net, PHP, etc...ASP is an API; it's written in VBscript.  ASP.NET is also an API, and you can write ASP.NET pages in any CLI language, including VB.NET and C#.

---

### Post by DirtDawg on 2005-07-28
I'm not the sharpest tool in the shed, but Python is fairly easy to learn. Maybe give Jython a shot for like a week and see how you like it? I know Python but always wished I knew Java because from my understanding, Jython allows full use of Java libraries with the easy syntax of Python.

---

### Post by safecracker on 2005-07-28
Take a look at [http://www.ferg.org/projects/python_java_side-by-side.html](http://www.ferg.org/projects/python_java_side-by-side.html) it makes some decent points.

The Java and Python devs have different mindsets, this has lead us to have two extremely different programming options. This guy basicly outlined my view on things: [http://hathawaymix.org/Weblog/2004-06-16](http://hathawaymix.org/Weblog/2004-06-16)

---

### Post by jerome bettis on 2005-07-28
python owns

[http://www.artima.com/intv/aboutme.html](http://www.artima.com/intv/aboutme.html)

that's a pretty good article, read the other parts too.  the one point that i remember and is relavent to this discussion, is what he says about file input.  how do you do file input in java?? i've done it about a dozen times, but each time i've had to google it to see an example.  random access file, buffered reader etc etc etc etc.  really just a bad design decision in java (one of many)

i've been messing around with python for just a few weeks and i know how to do file input.

```
f = file("filename", r)
for i in f:
    print i
```

for me to do that in java would require a trip to google and a lot more typing.  if i thought a little harder i could probably come up with some other things that are complicated in java (everywhere else too?) but real simple and clean in python.  just thought of keyboard input ....

also i hate how everything has to be in a class - this is rediculous but i understand why they did it.

and don't even get me started on swing ...

---

### Post by thumper on 2005-07-28
I think that a lot of the impetus in language choice comes down to a few points:
[list=1]
[*]What are you tring to do
[*]Who are you doing it for
[/list] 
Often language choice is driven by your employer.  There are not may companies out there (at least in the UK) that are using python for their main development.  Java is still considered a primary choice for server development (along with C++).

This isn't necessarily because Java is better than Python, but Sun has a lot of marketing people.

For my own general development I use Python where available.

---

### Post by charlieg on 2005-07-28
[QUOTE=dmccarney]Both are interpreted instead of compiled[/QUOTE]
That's really misleading, and technically incorrect.

Java bytecode is interpreted.  However, Java must be compiled into Java bytecode.  Java is not an interpreted language.

---

### Post by NoTiG on 2005-07-28
[QUOTE=dmccarney]

When I think web-programming language I think ASP/ASP.net, PHP, etc...

[/QUOTE]

I think thats because your looking at the wrong market sector... Here is what Miguel de Icaza [said](http://www.itwriting.com/monointerview.php) 

> .The hole that Mainsoft’s product fills is one that Microsoft has not been able to penetrate with ASP.NET, and we very much doubt it will be able to penetrate it. There is a segmentation of the application server space, which is the high-end market, the mid-market, and the low market. The low market is anything that costs less than $200,000 to develop and deploy. It includes every technology that you’ve heard of. Then you’ve got the high market, which is any project where the cost of deployment is over two million dollars, and in that market J2EE is firmly entrenched. There is no other technology considered today in that application space. In part that’s because people need to have multiple vendors providing the same solutions, so they like the fact that there’s BEA and there’s IBM and there’s Sun. There’s different J2EE providers. There’s also different hardware providers. So that market is very hard for Microsoft to penetrate.

"That leaves the mid-market, which today is about 50% Java, with the other 50% made up of ASP.NET, and a couple of other proprietary frameworks." 

Btw as for no companies using python... I read somewhere that Google requires alot of it's employees to know it.

---

### Post by thumper on 2005-07-28
[QUOTE=NoTiG]Btw as for no companies using python... I read somewhere that Google requires alot of it's employees to know it.[/QUOTE]
I didn't say **no companies** I said not many.
 :)

---

### Post by LordHunter317 on 2005-07-28
[QUOTE=safecracker]Take a look at [http://www.ferg.org/projects/python_java_side-by-side.html](http://www.ferg.org/projects/python_java_side-by-side.html) it makes some decent points.[/quote]That article has so many factual errors it's not worth reading.

[quote=jerome bettis]how do you do file input in java?? i've done it about a dozen times, but each time i've had to google it to see an example.[/quote]That doesn't make Java worse than Python in any way.

> random access file, buffered reader etc etc etc etc. really just a bad design decision in java (one of many)While there are issues with Java I/O, seperating the different types of I/O into different classes is not one of them.

As far as Miguel de Izaca's comment is concerned, most people at the high-end are locked into their J2EE vendor and don't care about Java's portability.  This is because they use features their vendor provides that the others do not (e.g., BEA tuxedo).  And the number of valid high-end system choices is precious few.  You essentially have UltraSparc from Sun, and POWER and S/390 from IBM.

---

### Post by Hanj on 2005-07-28
>  random access file, buffered reader etc etc etc etc. really just a bad design decision in java (one of many)Java IO used to be a pain in the *ss, but since version 1.5, you have the class Scanner to make life a LOT easier.

I should probably not get into this discussion too deeply though, as I haven't tried Python at all.

---

### Post by jdonnell on 2005-07-28
I do a lot of python at work, and in college we primarily used java and I like them both. I feel. no empirical evidence, that I can produce the same functionality in less time with python. Because of this I would choose python over java for most projects, but I wouldn't hate it if I were forced to use java. I would hate it if I were forced to use VB! 

Note: For web applications I'd use ruby on rails.

---

### Post by jerome bettis on 2005-07-28
[QUOTE=LordHunter317]That doesn't make Java worse than Python in any way.[/quote]

the hell it doesn't.  do you think it makes it better or something???  how does having to do a whole bunch of stuff not worse than having to do something very simple to accomplish the same thing?  i'd rather use c++ than java for a lot of things because well .. java f'ing sucks.  i'm tempted to say i'd rather use C but ugh C or java what a lousy decision.

> While there are issues with Java I/O, seperating the different types of I/O into different classes is not one of them.

i see why they did it.  it does make sense from a design perspective, but come on don't forget about the person who has to use these things.  what issues are you referring to here?

i just like the clean simplicity of python a lot.  instead of struggling with features of the language, my ideas just turn in to working code rather quickly.  with java i end up spending a decent amount of time on suns website looking stuff up (not really i guess), with c++ i spend LOTS of time knee deep in cryptic compiler errors, and then after that it's a few more pointer / memory errors.  with C well you guys know about C.

one gripe i have with python is when you do something wrong it just says "invalid syntax" and nothing else.  it would be nice to get some more information sometimes.  also since it's open source it has the problems that oss has and something like java doesn't.  sometimes i feel like it's just a little disorganized and hacked together, but it works ok enough for me.

---

### Post by charlieg on 2005-07-28
Anybody who thinks they can produce Python code quicker than Java hasn't used Eclipse 3.1 properly.

With an advanced IDE like Eclipse, the time saved with code generation, live code checking, and immediate function reference (like valid contructors etc) you can hammer out craploads of _working_ code like there's no tomorrow.  With Python you have to test and run your code before you know it works.

Give me an equivalently amazing IDE for Python then you'll be able to argue it's concisor syntax wins over.

A workman is only as good as his tools.  The programming language is but one tool in the box.  Most good tools come in combinations and Java + Eclipse, .NET and Visual Studio are two great examples.  Does Python have a suitable great tool other than an incredibly well set-up vim or Emacs (and even then they still fall short).

---

### Post by jerome bettis on 2005-07-29
ide's are gay but this is not what we're talking about.  the syntax checking is nice but i've gotten in the habit of looking over every line after i write it.  this keeps it correct and i'm 100% sure i know what's going on the first time around.  this is not as easy to do with C++ / java as it is in python.  but i'm not arguing, syntax checking is nice, i wish vim had it.

but i still say i can spit out java code FASTER with vim and makefile than i can eclipse, which i used for 2 1/2 years.  i can use the keyboard a lot faster than a mouse.  i think firefox is really the only thing i use a mouse in at all lol

---

### Post by LordHunter317 on 2005-07-29
> **jerome bettis]the hell it doesn't.  do you think it makes it better or something???[/quote]No, but you can't say, "Because I had to look something up in  language A and not in B, therefore B is better than A."

By your standard, Python is no better than Java in my perspective, because I'd likely have to look it up for  both in either case.

>  how does having to do a whole bunch of stuff not worse than having to do something very simple to accomplish the same thing?Because in this specific case, the Java solution is more extensible?  Extensibility is a good thing, even if it sometimes makes common tasks hard.

> what issues are you referring to here?The fact non-blocking I/O wasn't supported until Java 2, and you have to use a whole different set of classes to do it.  The File class handles more than files, it really should be a FilesystemObject class that's been further subclassed.  

The constructor's ability to throw exceptions mean you have to write your code like this:```
try {
   FileReader reader = new FileReader("foo") said:**
> Anybody who thinks they can produce Python code quicker than Java hasn't used Eclipse 3.1 properly.Or they have and realised Eclipse is utter crap. ;)

> With an advanced IDE like Eclipse, the time saved with code generation,Eclipse's automatic code generation features are largely useless.  Wow, I didn't have to write the class shell for my application.  

There are tiny little bits that are useful, but the refactor abilities are far more useful than the code generation, in terms of time saved.  

> you can hammer out craploads of _working_ code like there's no tomorrow.No, you mean you can hammer out craploads of *compilable* code.  Just because code compiles doesn't mean it works (i.e., bugfree, feature-complete), and there's nothing inherent about developing in eclipse that reduces problems of the latter class.  Yeah, it makes it much eaiser to correct syntax errors when you make them, but it doesn't help you if the syntatically correct code doesn't do what you want.

[quote=jerome bettis]ide's are gay but this is not what we're talking about.[/quote]That's a pretty enlightened view to take.  :roll:  Really, IDEs are quite a valuable tool and can save a devloper tons of time.  If only because they handle lots of the orginizational/CM issues that most developers don't handle very well.

That's ignoring the value of features like IntelliSense, which is essential for working with any large API (includes Python).  Not because it saves you typing, but it means you don't have to stop coding to look up exactly how a method name is written.

> the syntax checking is nice but i've gotten in the habit of looking over every line after i write it. A human is quite incapable of manually verifying every line as correct, 100% of the time.  OTOH, a computer is, and in fact, must do that before it can even use the code.  So why not let the computer do it, as it's clearly superior for this task?

> but i still say i can spit out java code FASTER with vim and makefile than i can eclipse, which i used for 2 1/2 years.In the real world, the speed at which you spit out code is mostly irrelevant.   It's long been an accepted fact that on average, a programmer writes around only 100 lines of code a day.  That's regardless of what tools they have to do speed up the *code generation* process.

Tools that help correct logic errors in code, and improve the process of maintaining and correct existing code, are invaluable.  And this is where a good IDE is worth it's weight in gold.

---

### Post by jerome bettis on 2005-07-29
> **LordHunter317]No, but you can't say, "Because I had to look something up in  language A and not in B, therefore B is better than A."

By your standard, Python is no better than Java in my perspective, because I'd likely have to look it up for  both in either case.

Because in this specific case, the Java solution is more extensible?  Extensibility is a good thing, even if it sometimes makes common tasks hard.[/quote]

well put, i stand corrected but in my perspective python is still better :-P 

```
try {
   FileReader reader = new FileReader("foo") said:**
> (*,)  also i think you need to wrap the FileReader within a BufferedReader ... but who cares, we agree java has it's flaws.  i used to like it until i used it a lot and was made aware of it's short comings.  apparently there's still quite a few that i don't know about. 

> Or they have and realised Eclipse is utter crap. ;)

Eclipse's automatic code generation features are largely useless.  Wow, I didn't have to write the class shell for my application.  

There are tiny little bits that are useful, but the refactor abilities are far more useful than the code generation, in terms of time saved.

agreed, it's not too time consuming to write the skeleton of everything - copy and paste goes a long way.  i'll admit i will fire up eclipse when i need to refractor a few things that would take a while by just editing it myself.

[quote]That's a pretty enlightened view to take.  :roll:  Really, IDEs are quite a valuable tool and can save a devloper tons of time.  If only because they handle lots of the orginizational/CM issues that most developers don't handle very well.
the only ide's i've used are eclipse 3.1, netbeans 3.0 (SLOW), and visual c++ 2 from way back.  i think if i used one i liked and just use vim for editing i wouldn't say things like that.  now that i think about it i do miss an integrated debugger, but i've come to like gdb.  there's also a lot of other things i don't realize i miss, like you said intellisense etc.  i might check out anjuta and see what that's about.

---

### Post by LordHunter317 on 2005-07-29
[QUOTE=jerome bettis]
this is exactly what i'm talking about.  i've written that every time i've done any file operations in java, but if you wouldn't have posted that, i'd have no idea you need to do that.[/quote]Well, you don't necessarily have to, if you don't care about propogating the IOException upwards.  If you don't care about propogating it, then you can remove the outer try/catch block, and declare the method to throw IOException.

But if you don't want to throw the exception, you have to use a double try/catch block, or you have to initialize the FileReader to null, which violates RAII and can lead to problems later in life.

>  also i think you need to wrap the FileReader within a BufferedReader ...Only if you want buffered access, which was my point above about the multiple classes.

> agreed, it's not too time consuming to write the skeleton of everything - copy and paste goes a long way.While I don't think the code generation features save a ton of time, they are better than copy and paste in any case.

>  now that i think about it i do miss an integrated debugger, but i've come to like gdb.I don't see how you can use gdb on the command line unless you're not doing complicated debugging.  You just can't see enough information at once.

>  there's also a lot of other things i don't realize i miss, like you said intellisense etc.People don't realise they miss it usually until they use it a lot.   For Java or C#, Intellisense is indespensible.

---

### Post by jdonnell on 2005-07-29
[QUOTE=charlieg]Anybody who thinks they can produce Python code quicker than Java hasn't used Eclipse 3.1 properly.

 With Python you have to test and run your code before you know it works.
[/quote]

And you don't java? The logic is tested far more than the syntax unless your making really trivial programs. Python is far faster in this regard (no compilation). Even with eclipse you have to write more code in java that in python. Often times a lot more code. In python I can make a function that accepts any object that responds to a call to a speak() method. In java you can't do this. You have to make an interface, and if your using containers you have to cast every damn thing. Bottom line is that python or ruby require far less code than java and can be tested much faster because of the compilation step that is repeated over and over again in java. But, by all means, continue using java if you want. I hope that all my competitors do  ;-)

---

### Post by jerome bettis on 2005-07-29
[QUOTE=LordHunter317]I don't see how you can use gdb on the command line unless you're not doing complicated debugging.  You just can't see enough information at once.[/quote]

i use the ddd front end :cool:

---

### Post by Mobus on 2005-07-29
I really don't like either of them, JAVA is compiled and THEN interpreted, which defeats the purpose of both, yet Python is a very show-offy language ("Hey looky here! I made a p2p client in 15 lines of python! OMG).

I'd actually have to chalk the point up to Python because I think its a little more useful, and also that <JULIUSCEASAR character="Brutus">Its not because I love JAVA less, its that i love PYTHON more </JULIUSCEASAR> (but not by much).

---

### Post by LordHunter317 on 2005-07-29
[QUOTE=Mobus]I really don't like either of them, JAVA is compiled and THEN interpreted, which defeats the purpose of both,[/quote]No.  This statement shows you don't understand the value of bytecode interpretation, or what compiling vs. interpreted means.

---

### Post by jdonnell on 2005-07-29
[QUOTE=Mobus]I really don't like either of them, JAVA is compiled and THEN interpreted[/QUOTE]

those .pyc files you see are python code compiled into bytecode.

---

### Post by Mobus on 2005-07-29
ok yeah, you compile halfway, and then do the other half at destination. yet, as easy as it may seem, if you want to intepret an interpreted language, you have to have the interpreter.  That defeats protability right there. there are people like my mother out there who are complete computer idiots,  and thus the chance of them getting the interpreter on their system would be more than unlikely.  Yes, you could include the interpreter in the install package, but that dowesn't always work for every OS. Compiled languages relieve us of that determent, yet you hsave to compile it once per OS, which if you find that a major setback, you don't deserve to be a programmer.   Basically, Java compiles it halfway to "make it faster upon interpretaion" but in all actuality, it does little.  And you still have to have the Java interpreter (cleverly disguised as a "runtime environment"), which is often a hassle to install for normal people, let alone people like my mom.  So basically, :

Java:

Normal advantages of normal compiled languages:
Fast
Don't need to carry around an interpreter with you
handles large projects easier

Normal Disadvantages:
Not very "Portable"
often more "complivated"

Normal advantages of interpreted nlanguages:
More "Portable"
sometimes less complicated

Disadvantages of interpreted languages:
Have to carry around interpreter
Perl: not everyone's perl.sh is in the same folder (#!/usr/bin/perl)
slower
stupider


Java:
Retains complexity of compiled languages, retains the must of carryinfg around an interpreter, retains slowness of interpreted languages, retains stupidity of interpreted languages.


Any questions?

---

### Post by LordHunter317 on 2005-07-29
> **Mobus] if you want to intepret an interpreted language, you have to have the interpreter.[/quote]No, it doesn't.   Your application is still portable to whatever platforms have an interperter.

The fact the interpreter has to be installed beforehand doesn't change that.  That's true of *all* languages, compiled to machine language or interpreted from source or bytecode.  The only execption is languages that allow you to compile all code statically and even then, that isn't always a possibility with some codebases. 

>  Yes, you could include the interpreter in the install package, but that dowesn't always work for every OS.Yes, it does.  Plenty of people manage to do it without any trouble.

> Compiled languages relieve us of that determent,No, they don't necessarily do so.

> yet you hsave to compile it once per OS, which if you find that a major setback, you don't deserve to be a programmer.:roll:  People who make statements like this clearly haven't do configuration management on huge codebases before, or dealt with per-operating system issues before.

Porting code from VMS to UNIX isn't as simple as recompile.  Heck, porting code between different flavors of UNIX is rarely as simple as a recompile.

OS issues can be a very big deal, and they're always a pain to deal with.

> Basically, Java compiles it halfway to "make it faster upon interpretaion"That's not actually why it's done, but is an occasional, incidental benefit.

> And you still have to have the Java interpreter (cleverly disguised as a "runtime environment"),Which includes all the standard libraries as well.

Which you have to do for any dynamically linked C or c++ application on your system.  If you write a KDE application, It won't run unless Qt and the KDE libs are installed first.  And you can't statically compile those libraries into the codebase: the design of KDE makes it impossible said:**
> Normal advantages of normal compiled languages:
Fast
Don't need to carry around an interpreter with you
handles large projects easierNone of these are necessarily true, except the interpreter part.  And that doesn't matter if you're dependent on code other than your own, the dependency issue is the same.

> Disadvantages of interpreted languages:
Have to carry around interpreter
Perl: not everyone's perl.sh is in the same folder (#!/usr/bin/perl)
slower
stupider:roll:  Wow.  I'd love to see you defend that last point.

And oh, dealing with the perl binary being in different paths is as simple as:```
#!/usr/bin/env perl
```and telling the user to make sure perl is in their PATH first.  Not hard.  Solution's been around almost as long as UNIX has.

> Any questions?Yeah, do you like to troll?  Really.  You may not like Java or the fact it's bytecode interpreted, but it's one thing to provide reasons why, and another to provide useless blanket statements like, "All interpreted languages are stupid."

Kindly grow up, and debate on a reasoned level, please.

---

### Post by Mobus on 2005-07-29
> No, it doesn't. Your application is still portable to whatever platforms have an interperter.

so in order for the interpreter to be able to interpret the program, it needs to be there, right? and if its not there, either you have to get it, or you're screwed.  Most people CAN get it, but there are certain people (people who's intellect is EVEN worse than those who use interpreted languages for non-web associated applications) who would just be screwed.  Yes, I believe Interpreted languages are best for web apps, I'd hate to do CGI in c, although it CAN be done.  

> Yes, it does. Plenty of people manage to do it without any trouble.


ok, lets say you made the program in Linux, but you don't qute have an interpreter to give to those on BSD, or WIndows for example?

> 
No, they don't necessarily do so.

oh so you're telling me that compiled languages still make us have to have the "DETREMENT" of having to have an interpreter? I'd like to see you argue that point.


> People who make statements like this clearly haven't do configuration management on huge codebases before, or dealt with per-operating system issues before.

Porting code from VMS to UNIX isn't as simple as recompile. Heck, porting code between different flavors of UNIX is rarely as simple as a recompile.

ok, so there's a few discrepancies (ahem... conio.h to curses.h) and I didn't say it resolved ALL problems, but I think porting it would be easier than expecting a (windows) user to put perl in the right spot, (not a problem with UNIX users, or even mac users, but windows is stupid like that)

> 
That's not actually why it's done, but is an occasional, incidental benefit

OK OK it helps with "Portability", and i never said that was the main reason why bytecode is used


> Which includes all the standard libraries as well.

Which you have to do for any dynamically linked C or c++ application on your system. If you write a KDE application, It won't run unless Qt and the KDE libs are installed first. And you can't statically compile those libraries into the codebase: the design of KDE makes it impossible; the application simply will not run correctly, if at all.

So no, there's nothing inherent about compiled languages that make them better in this regard. You still have the same problem: you need some other code installed first. The fact it's a shared library instead of an interpreter really doesn't matter.


Which is why GNOME r0xx0rs over KDE :smile: 

-which is also why GNOME users are more  (dare I say it) 1337, because we actually are intelligent enough to handle that extra bit

and still, runtime environment is a lame cover up for an interpreter, you HAVE to agree with that one



> None of these are necessarily true, except the interpreter part. And that doesn't matter if you're dependent on code other than your own, the dependency issue is the same.

OK I'm sorry, a hello world app that's interpreted will run faster than a compiled DOOM3.  You got me.


> Wow. I'd love to see you defend that last point.

lets find the average IQ of all Interpreted language user, and the average IQ of all compiled language users, and see which sample has a higher mean (which could easily be calculated on a compiled language, I suggest C++)


> 
and telling the user to make sure perl is in their PATH first. Not hard. Solution's been around almost as long as UNIX has.


Users don't listen to anything you say. You can tell the to put it in their PATH and they still won't listen


> Yeah, do you like to troll? Really. You may not like Java or the fact it's bytecode interpreted, but it's one thing to provide reasons why, and another to provide useless blanket statements like, "All interpreted languages are stupid."

Kindly grow up, and debate on a reasoned level, please. 

I didn't just give a blanket statement that said  cout << "All interpreted languages are stupid"; , I gave cout << "This is what's cool about compiled languages, and what's not cool about interpreted languages. Any Questions?"; cin >> questions.


And as for the grow up part, I only have one thing to say to you GROW UP! interpreted languages are for babies, compiled languages are for real adults.

And arguing that compiled languages are better than interpreted is a good reason to argue no matter what.  And hey. at least /I actually KINDOF know what I'm talking about, not some idiot who decides to say interpreted languages are better because they can be done in an "Active" state.

---

### Post by LordHunter317 on 2005-07-29
> **Mobus]so in order for the interpreter to be able to interpret the program, it needs to be there, right? and if its not there, either you have to get it, or you're screwed.[  Most people CAN get it, but there are certain people (people who's intellect is EVEN worse than those who use interpreted languages for non-web associated applications) who would just be screwed [/quote]**No, this is why you *provide* the intrepreter as part of your application.**

This is what Oracle does, for example, even though their installer is a beast written entirely in Java.  They just simply include the JRE as part of their installer.

> ok, lets say you made the program in Linux, but you don't qute have an interpreter to give to those on BSD, or WIndows for example?Then they won't be running it at all.  It stands to reason if you cannot provide them with one, they cannot get one either.

> oh so you're telling me that compiled languages still make us have to have the "DETREMENT" of having to have an interpreter?Yes, because the issues **isn't** that the language is interpreted.

The issue **is** that your code depends on more than itself.  Compiled languages don't inherently solve the external dependency problem.

> ok, so there's a few discrepanciesIt's not a few, they're quite substantial.  You obviously never done any porting work of a large application.

If you don't believe, go browse the Apache 1.3 source and see what kind of an utter mess it is, largely in part due to it's need to be portable to many different platforms.  

> but I think porting it would be easier than expecting a (windows) user to put perl in the right spot,No, not in the least.  Porting an application can take thousands of man-hours or more.  I've been involved in such efforts before, I know first hand.

>  and i never said that was the main reason why bytecode is usedWhat other meaning am I suspposed to take from this statement:> **Basically,** Java compiles it halfway to **"make it faster upon interpretaion"** but in all actuality, it does little.(emphasis mine).  You were implying the main reason for bytecode compiliation is performance, which really doesn't make sense at all.

> Which is why GNOME r0xx0rs over KDE Not in the least.  The configuration mangement issue is small.  I'm not sure all GNOME applications could actually be safely statically compiled either, I suspect some of the libraries have the same issues.  Even if they could, you wouldn't want to.

> and still, runtime environment is a lame cover up for an interpreter, you HAVE to agree with that oneIt is nothing of the sort.  The need for an interpreter is ***irrelevant*** if your software depends on other code.

What's the difference between telling the user:[list][*]You need to have the python interpreter installed,[*]or telling them they need to have the GTK+ library installed?[/list]To the user: it still means that have to install something else first: *what* that something else is doesn't matter.

> Users don't listen to anything you say. You can tell the to put it in their PATH and they still won't listenThe point is, there are many valid solutions for the issue of locating the interpreter on a system.  It's not a hard thing to do.

> I didn't just give a blanket statement that said  cout << "All interpreted languages are stupid" said:**
> Then what is the meaning of this:[quote]**Disadvantages of interpreted languages:**
Have to carry around interpreter
Perl: not everyone's perl.sh is in the same folder (#!/usr/bin/perl)
slower
**stupider**(emphasis mine).  Sure seems like a blanket statement that interpreted languages are dumb to me.  

[quote]And as for the grow up part, I only have one thing to say to you GROW UP! interpreted languages are for babies, compiled languages are for real adults.Which is exactly why Microsoft is moving **away** from compilied languages to bytecode interpreted ones, with .NET.

Hrm.  Obviously, either MS thinks all of their developers are babies, or there's more to this interpretation thing than you think.

> And hey. at least /I actually KINDOF know what I'm talking about,No, that's not apparent in the least.

You still haven't explained how compiled lanaguges solve the external dependency problem interpreted languages have.  

>  not some idiot who decides to say interpreted languages are better because they can be done in an "Active" state.If you're talking about me, I said nothing of the sort.

---

### Post by jdonnell on 2005-07-29
[QUOTE=Mobus]...  there are certain people (people who's intellect is EVEN worse than those who use interpreted languages for non-web associated applications)[/QUOTE]

This is the stupidest thing I've seen in a long time. Why would anyone use a language that takes longer (ie more money) to develop in if there is no reason to, and there is no reason in most situations? Most programs that are created are either web based or aren't distributed to users. Every application I have every worked on professionally has been used internally or by a small set of clients. It would be stupid to increase development costs by using a language like C unless you absolutely needed to use C.

---

### Post by Mobus on 2005-07-30
> No, it doesn't. Your application is still portable to whatever platforms have an interperter.

so in order for the interpreter to be able to interpret the program, it needs to be there, right? and if its not there, either you have to get it, or you're screwed.  Most people CAN get it, but there are certain people (people who's intellect is EVEN worse than those who use interpreted languages for non-web associated applications) who would just be screwed.  Yes, I believe Interpreted languages are best for web apps, I'd hate to do CGI in c, although it CAN be done.  

> Yes, it does. Plenty of people manage to do it without any trouble.


ok, lets say you made the program in Linux, but you don't qute have an interpreter to give to those on BSD, or WIndows for example?

> 
No, they don't necessarily do so.

oh so you're telling me that compiled languages still make us have to have the "DETREMENT" of having to have an interpreter? I'd like to see you argue that point.


> People who make statements like this clearly haven't do configuration management on huge codebases before, or dealt with per-operating system issues before.

Porting code from VMS to UNIX isn't as simple as recompile. Heck, porting code between different flavors of UNIX is rarely as simple as a recompile.

ok, so there's a few discrepancies (ahem... conio.h to curses.h) and I didn't say it resolved ALL problems, but I think porting it would be easier than expecting a (windows) user to put perl in the right spot, (not a problem with UNIX users, or even mac users, but windows is stupid like that)

> 
That's not actually why it's done, but is an occasional, incidental benefit

OK OK it helps with "Portability", and i never said that was the main reason why bytecode is used


> Which includes all the standard libraries as well.

Which you have to do for any dynamically linked C or c++ application on your system. If you write a KDE application, It won't run unless Qt and the KDE libs are installed first. And you can't statically compile those libraries into the codebase: the design of KDE makes it impossible; the application simply will not run correctly, if at all.

So no, there's nothing inherent about compiled languages that make them better in this regard. You still have the same problem: you need some other code installed first. The fact it's a shared library instead of an interpreter really doesn't matter.


Which is why GNOME r0xx0rs over KDE :smile: 

-which is also why GNOME users are more  (dare I say it) 1337, because we actually are intelligent enough to handle that extra bit

and still, runtime environment is a lame cover up for an interpreter, you HAVE to agree with that one



> None of these are necessarily true, except the interpreter part. And that doesn't matter if you're dependent on code other than your own, the dependency issue is the same.

OK I'm sorry, a hello world app that's interpreted will run faster than a compiled DOOM3.  You got me.


> Wow. I'd love to see you defend that last point.

lets find the average IQ of all Interpreted language user, and the average IQ of all compiled language users, and see which sample has a higher mean (which could easily be calculated on a compiled language, I suggest C++)


> 
and telling the user to make sure perl is in their PATH first. Not hard. Solution's been around almost as long as UNIX has.


Users don't listen to anything you say. You can tell the to put it in their PATH and they still won't listen


> Yeah, do you like to troll? Really. You may not like Java or the fact it's bytecode interpreted, but it's one thing to provide reasons why, and another to provide useless blanket statements like, "All interpreted languages are stupid."

Kindly grow up, and debate on a reasoned level, please. 

I didn't just give a blanket statement that said  cout << "All interpreted languages are stupid"; , I gave cout << "This is what's cool about compiled languages, and what's not cool about interpreted languages. Any Questions?"; cin >> questions.


And as for the grow up part, I only have one thing to say to you GROW UP! interpreted languages are for babies, compiled languages are for real adults.

And arguing that compiled languages are better than interpreted is a good reason to argue no matter what.  And hey. at least /I actually KINDOF know what I'm talking about, not some idiot who decides to say interpreted languages are better because they can be done in an "Active" state.

---

### Post by Mobus on 2005-07-30
[QUOTE=jdonnell]This is the stupidest thing I've seen in a long time. Why would anyone use a language that takes longer (ie more money) to develop in if there is no reason to, and there is no reason in most situations? Most programs that are created are either web based or aren't distributed to users. Every application I have every worked on professionally has been used internally or by a small set of clients. It would be stupid to increase development costs by using a language like C unless you absolutely needed to use C.[/QUOTE]


I must say, if what you quoted was the stupidest thing you ever saw,. then your comment on that quote must be the 2nd stupidest.  WHY WOULD YOU USE A COMPILED LANGUAGE ON THE WEB?! cgic.h is probably the closest thing to something actually worth using.  I don't see how using an interpreted language would cost money on the web.

Plus, you ask why you would use c/c++? well, lets look at a few examples.  I know that DOOM was written in C, then DOOM3 i'm sure used C++, those are the only ones that I know for sure used C/C++, although most any program that you buy uses C/C++, including most of the programs in synaptic.  when you type in the terminal: ./configure && make && make install, that a good peice of evidence that what you are installing was written in C/C++.  Don't tell me that C/C++ is a bad idea.  Its a good one.  If you want to use an interpreted language, use if for the web, and keep for the web.

---

### Post by Mobus on 2005-07-30
> No, this is why you provide the intrepreter as part of your application.

This is what Oracle does, for example, even though their installer is a beast written entirely in Java. They just simply include the JRE as part of their installer.

Yeah, it can be done, and it could relieve SOME back-breaking, but why do most big software companies (id for example) still use compiled languages? hm?

> 
Then they won't be running it at all. It stands to reason if you cannot provide them with one, they cannot get one either.

but if they can't get an interpreter, then why not make it a compiled language and not make them do the work?

> 
Yes, because the issues isn't that the language is interpreted.

The issue is that your code depends on more than itself. Compiled languages don't inherently solve the external dependency problem.


ok a disadvantage, but it still doesn't weigh more than the advantages of compiled languages.  I didn't say comiled languages DIDN'T have their own set of disadvantages, I just said its disadvantages weigh less over its advantages than interpreted languages weight over their advantages.



> It's not a few, they're quite substantial. You obviously never done any porting work of a large application.

If you don't believe, go browse the Apache 1.3 source and see what kind of an utter mess it is, largely in part due to it's need to be portable to many different platform


ok, its less work for an interpreted language, but an interpreted language still has its share or porting problems

> 
No, not in the least. Porting an application can take thousands of man-hours or more. I've been involved in such efforts before, I know first hand.


That's about as exxagerated as when my band director claims she can "Walk to the other end of the school, up 3 floors, carrying a huge stack of books, and use the bathroom on the way, all in 5 minutes". 'nuff said.
> 

What other meaning am I suspposed to take from this statement:

well, did you see an "only" in that whole statement? i don't think so.


>  Even if they could, you wouldn't want to.

yeah we do


> It is nothing of the sort. The need for an interpreter is irrelevant if your software depends on other code.

What's the difference between telling the user:

    * You need to have the python interpreter installed,
    * or telling them they need to have the GTK+ library installed?

To the user: it still means that have to install something else first: what that something else is doesn't matter.


yeah, but you only have to have GTK+ installed once, you have to have a different interpreter for each interpreted language. The exxence of a compiled language is that when the building is done, it can be done a little more universally.


> The point is, there are many valid solutions for the issue of locating the interpreter on a system. It's not a hard thing to do.


Neither is just making an install package with a compiled language.


> Sure seems like a blanket statement that interpreted languages are dumb to me.

one statement out of the rest of them... still seems like I've got more info than blanket staements.



> Which is exactly why Microsoft is moving away from compilied languages to bytecode interpreted ones, with .NET.

Hrm. Obviously, either MS thinks all of their developers are babies, or there's more to this interpretation thing than you think.


Do you mean that you can actually look at me with a straight face and say that Microsoft isn't a bunch of big babies?  If you really think you can, then why do you even have linux on your computer?



> No, that's not apparent in the least.

You still haven't explained how compiled lanaguges solve the external dependency problem interpreted languages have.

ok, you can find one thing that you think I kinda don't know about.  But I explained that in this post anyway.


>  If you're talking about me, I said nothing of the sort.


Again, you're putting words into my mouth.  I never said I was reffering to you on that.  You may have implied that I implied it, but no.  I'm talking about the fact that I saw some dude on a python tutorial boasting about that "really cool option!"

---

### Post by safecracker on 2005-07-30
[QUOTE=LordHunter317]That article has so many factual errors it's not worth reading.
.[/QUOTE]

I agree it has errors but it is still worth reading, it is one thing to say something has errors but it is useless to do so if you do not point them out. You may ask why, the reason being that someone A) has to take you at your word or B) read the article to find out for themselves therefore defeating the purpose of your comment.

My point was that it made "some" good distinctions but others being based on older java implementations or misinformation.

The bottom line is always what the task is and the fact that each language will have strong and weak points. One language will never be the perfect solution for the market it was designed to be used in nor will one language fit everyones programming style. The main issue with most programmers is the lack of understanding when it comes to concept and theory. If you understand the  basic concepts of programming, language of implantation becomes a minor issue.

Anyway thats a whole other topic in its self.

[QUOTE=Mobus]Do you mean that you can actually look at me with a straight face and say that Microsoft isn't a bunch of big babies?  If you really think you can, then why do you even have linux on your computer?[/QUOTE]

That comment seems a lil strange to me. Their are several reasons to run Linux, it shouldn't be about your hate for MS practices. Most ppl I know running Linux do it due to the flexability and speed it provides not because they just feel MS are a bunch of babies. I think MS are quite smart they have held a Desktop market share for an extremely long time and will do what is within their power to continue it. I may not be a Microsoft fanboy but I do know they have smart ppl working for them. Honestly alot of MS employees are interested in Linux as well.

---

### Post by Mobus on 2005-07-30
> but others being based on older java implementations


ACtually, you could be right about that.  I must admit now that you mention it, the lastest version I've really looked at was like Java 2.0.  My bad.


About Microsoft being babies, alright.  I'll take that back.  I will put in its place "Money sucking pigs".  Are we happy now?

---

### Post by safecracker on 2005-07-30
[QUOTE=Mobus]ACtually, you could be right about that.  I must admit now that you mention it, the lastest version I've really looked at was like Java 2.0.  My bad.


About Microsoft being babies, alright.  I'll take that back.  I will put in its place "Money sucking pigs".  Are we happy now?[/QUOTE]
 yes we are happy now, when you say big babbies I think of ppl who just bitch and moan who have no clue about the biz sector in which they work. When you say money sucking pigs, if speaking about the MS executives I tend to agree and find it hard to contend.

The real truth though is that when we try to pit 1 language against another their will never be a clear winner especially when they both get used for similar purposes.

"There are only two kinds of programming languages: those people always bitch
about and those nobody uses." (Bjarne Stroustrup)

---

### Post by Mobus on 2005-07-30
That's kind of why I said I'd rather user an interpreted language for web use (scripting mostly) and compiled languages for the non-web apps.  app_LETS_ should use JAVA or other compiled (or half compiled) languages.  And of course, I find interpreted languages easier to learn programming with (especially learning how to use the terminal).  I would have no clue how to do anything in the terminal if it wasn't for me learning Perl.   \\:D/  \\:D/

---

### Post by LordHunter317 on 2005-07-31
> **Mobus]IPlus, you ask why you would use c/c++? well, lets look at a few examples.  I know that DOOM was written in C, then DOOM3 i'm sure used C++, those are the only ones that I know for sure used C/C++,[/quote]So?  Games are special purpose applications that need special purpose things, including performance that *tradationally* could only be provided by languages that are compiled to machine language.  They're not good examples because they're hardly indicative of common applications.


>  when you type in the terminal: ./configure && make && make install, that a good peice of evidence that what you are installing was written in C/C++.No, it isn't in the least.  GNU autoconf is used by multiple applications, as is make.  I've seen projects that use autoconf with Java source code.

Oh, mono uses GNU autoconf too, and *most* of their code is written in C#, not C or C++.  Only the VM has any C or C++ in it.  

> If you want to use an interpreted language, use if for the web, and keep for the web.Once again, you're making blanket statements you have no way of defending.  Interpreted languages are used everywhere, and are integral for any's system operation.

You don't think your init scripts and shell scripts should be compiled, should you?  Yet, I think you'll find if you go through /usr an incredible amount of shell and perl code, both of which are interpreted.  Both of which your system would not be able to run without.  

So maybe there's a lot more to this whole interpreted language thing than it seems.  Especially when the future of the entire Microsoft platform is bytecode-interpreted (.NET).

> Yeah, it can be done, and it could relieve SOME back-breaking, but why do most big software companies (id for example) still use compiled languages? hm?They umm, don't.  And id Software is an absoutely tiny software company in the scheme of things.

Oracle provides Oracle Application Server, which is Java.  Java is a core part of the Oracle Database proper said:**
> but if they can't get an interpreter, then why not make it a compiled language and not make them do the work?Because it doesn't remove any work, necessarily.  

> ok a disadvantage, but it still doesn't weigh more than the advantages of compiled languages. I didn't say comiled languages DIDN'T have their own set of disadvantages, I just said its disadvantages weigh less over its advantages than interpreted languages weight over their advantages.The problem is that this disadvantage is the **same disadvantage interpreted languages have**, furthermore, **it's was the only valid advantage you gave to compiled languages**.  Only now we find it's not really an advantage at all, so what are these advantages of compiled languages you speak of?

> That's about as exxagerated as when my band director claims she can "Walk to the other end of the school, up 3 floors, carrying a huge stack of books, and use the bathroom on the way, all in 5 minutes". 'nuff said.No, it isn't.  The application in question was a ~million lines of legacy VMS code.  Almost 80% of it would have to be rewritten because it was completely dependent on VMS ways of doing things that didn't have good UNIX analogs.  The port wasn't even considered because the project time investment was too large to be worth it.

Really.  If I wasn't under NDA, I'd show you the figures.  Porting applications can be quite an expensive proposition, especially when your code is highly platform dependent to begin with.

> well, did you see an "only" in that whole statement? i don't think so.I noted you were implying it was the **main** reason, not the **only** reason.  And it's false in either case.

> yeah we doNo, you don't.  Statically compiling most GNOME applications would boost your memory usage by about 10-20MB, *per application*.  Your system would literally be unusable unless you threw multiple gigabytes of RAM at it.

Supporting static compliation for an application of any size is generally a silly investement, if it's even possible.

Look at the VM numbers for common processes in /proc, if you don't believe me.  Pay especially close attention to the VmLib number.  You'd esentially be giving that much up for a  statically compiled process.

> yeah, but you only have to have GTK+ installed once, you have to have a different interpreter for each interpreted language.So?  It's no different: **you still have to have *something else* installed *first***  The problem is the exact same thing, even if what you have to install first changes.

> The exxence of a compiled language is that when the building is done, it can be done a little more universally.What?  No.  This is a non-sequitur, and even if it wasn't, I'm not sure what you're trying to say.  That compiled languages can be universally built?  No, I don't think so.  Windows code isn't going to build on a Linux toolchain.

> Do you mean that you can actually look at me with a straight face and say that Microsoft isn't a bunch of big babies?Yes, I can.  Certain divisions of Microsoft produce topnotch software, including, but not limited to: Office, SQL Server, Visual Studio, and the .NET group.

SQL Server is a superior product to the OSS databases in quite a few ways.  OpenOffice.org, despite it's best efforts, can't mimic Office in usability; I don't even bother trying to use it anymore.  OO.org 2 may be better, but I'm not planning on uninstalling Office 2003 anytime soon.  Let's not even go into the topic of IDEs.  Even Eclipse is a pale candle to VS.NET.

> If you really think you can, then why do you even have linux on your computer?Because Linux generally serves my computing needs better?  I have no politcal reasons for running Linux, I could really care less about "Free as in freedom".  My decisions for choosing software are almost always technical or business releated, never political.  That's both professionally and personally.


> Again, you're putting words into my mouth. I never said I was reffering to you on that.The problem was, it wasn't clear in context who you were referring to at all.  Hence my response.  Wasn't trying to twist your words in anyway, but your comment was more than ambiguous w.r.t to who you were responding too.

> **safecracker]I agree it has errors but it is still worth reading,[/quote]No, the errors are substantial enough to make the article's value zero.

> but it is useless to do so if you do not point them out.If you really want me to, I can.  I didn't, because pointing out all the errors would be quite a post in and of itself, and it's not fully germane to the topic here. 

> My point was that it made "some" good distinctions but others being based on older java implementations or misinformation.No, they really don't have anyhting to do with newer Java implementations.  It has several factual errors about statically typed languages that apply to any version of Java, even Java 1.0.
Consider:>  There is, however, one related topic that is virtually impossible to avoid. Python is a dynamically-typed  language, and this feature is an important reason why programmers can be more productive with Python said:**
> It's not 100% clear what type of overhead we're dealing with here (ain't ambiguity wonderful?) but static typing has *less* runtime overhead than dynamic typing, *more* compile overhead than static typing, and *not necessarily* any more overhead w.r.t. programmer productivity.  He even provides later examples of languages that are statically typed that manage to to type deduction in most cases.  So I'm not sure what point he was trying to make, but he's wrong in almost any case, I think.

[quote]When you retrieve an object from a container, it doesn't remember its type, and must be explicitly cast to the desired type.This also isn't technically correct.  The object remembers it's type just fine: it's type is Object.  The problem is, when you inserted the object into the container, you threw away the type information you really wanted: that it's also an Integer as well.  But saying that it doesn't remember it's type is just plain wrong, it must remember it's type, by definition of static-typing.  The problem is that you had to *throw away* type information, not that the type information isn't known.

By explictly or implictly casting a object to class Object in Java, you're throwing away all other type information.  That's true of any statically-typed, object-oriented  language: when you move up the class hiearchy, you throw information away.

There, enough support now?  I could go further, but you get the idea. ;)

[quote]
The bottom line is always what the task is and the fact that each language will have strong and weak points. One language will never be the perfect solution for the market it was designed to be used in nor will one language fit everyones programming style. The main issue with most programmers is the lack of understanding when it comes to concept and theory. If you understand the basic concepts of programming, language of implantation becomes a minor issue.I agree with this 100% and my intent wasn't ever to imply one language was better than another, even in general terms.

I program Java every day, even though it's flaws are many and numerous, and I can enumerate whole lists of them.  That's because *suprise* technical decisions, like the best language to use, have no bearing on business decisions.  And in a good business, the latter wins over the former every time.  And so, I'm stuck programming Java, because Java programmers are easy to find.

---

### Post by Mobus on 2005-07-31
ok, can we settle it then? Each language has its ups and downs, and neither is better than the other.


GOSH! Was it really that hard?

---

### Post by jwenting on 2005-07-31
[QUOTE=dmccarney]Now I know this may seem a bit redundant with all of the posts about the strenghts of Python and the comparisons drawn towards Ruby etc but I've found that there is little to no comparison to Java.

I have about 3 years casual experience with Java and with all of the Ubuntu hype about Python and I'm considering investigating it as an alternative.

Both are interpreted instead of compiled and everyone seems to point towards Python being much easier and more productive/time-saving but I've yet to see many concrete examples of this,

I've found the provided Java classes to be excellent in speeding up development of many hobby projects so perhaps someone could mention the pros/cons of the Python libraries in comparison?

Now without breaking into a flame-war could someone provide some examples of the benifits of using Python as compared to Java? I realize it would probably also depend alot on what you are trying to do with each, but perhaps someone could list a project that they would prefer to use Java for and a project they would prefer to use Python for and the reasoning?

Has anyone used Jython? Anything to say about that? Combining the two languages sounds interesting but is it really worth it?

One limitation: I'd prefer if the discussion was just limited to Python+Jython and Java , I realize there are a lot of other languages floating about and I'm sure alot of people would be gung-ho about recommending C, C++, LISP, Scheme, Assembler, whatever, but this is a post regarding Java and Python.

I hope I'm not asking too much of the Programming Talk community ;)[/QUOTE]
 Java is NOT interpreted.
That's an old misunderstanding about what happens.
Java is compiled into a binary format which is then executed (with runtime compilation into platform native code) by the JVM.
Python OTOH IS interpreted by nature, though optionally can be compiled into an equivalent system of Java bytecode.

Having tried both, I see Python as having a place to replace Perl for shellscripting and things like that. Java OTOH is a complete platform well suited for enterprise level applications for delivery to customers.

---

### Post by safecracker on 2005-07-31
LordHunter317 you make many good points and I appreciate programmers such as yourself taking the time to post on this forum. On review of that article I tend to agree, I had read that article at about 3am after reviewing a few thousand lines of C for the previous 3 hours so I must not have been all their at that time.

"but others being based on older java implementations or misinformation." was towards not just the article but some posts in this thread as well. 

Just remember that python and java can play nice togather, example being jython.

---

### Post by yaaarrrgg on 2005-11-30
When I first started programming, I loved the loose-n-groovy languages like Perl, where you could do fairly complex task in just a few lines.  At the time, I didn't see much point to stricter, more verbose languages like C, or Java.  Although, I've learned that one of the biggest advantages to those sorts of languages is that the compiler will typically catch 99% of the bugs for you.  Whereas in Perl, I spent more time debugging and maintaining code than writing it, because the loose-n-groovy code creates more opportunity for runtime bugs, and other wierdness.  In Java, on the other hand, if a program compiles, then that is typically a good indicator that your code is correct.   I rarely spend much time debugging the Java code I write,  (If there are bugs, it's usually either null pointers, or blantent logic errors).

Python is great for smaller projects, but could easily become a nightmare to maintain a larger project...especially if you have several programmers hacking together code willy nilly.  Easy syntax is not always good.  If so, BASIC might win as the best langauge.  Or if you want a succinct language, Perl might win.  Java works will when creating a large project written and maintined by several different programmers.  Java imposes more engineering contraints on the programmer ... which enables a program to grow in complexity without turning into a giant hacked up mess of buggy speghetti code.  I don't care how small a Python program can be... the problem is how large it can be?

---

### Post by thumper on 2005-12-01
I'd say that any probject can easily become a nightmare with several programmers hacking together code willy nilly.

Python is quite capable of producing large systems in a proper development process, as is almost any other language.

---

### Post by yaaarrrgg on 2005-12-01
I'm not saying it's impossible to write a large Python system.   Nor is it impossible to write bad Java code.  The difference though is that Java actively imposes more structure on the programmer (which is why most people dislike it).  But in my experience, I've found the annoying verbosity and structure of a strongly typed language like C or Java ends up helping in long runs... if you factor in testing and debugging.  

A good combination is to use Python as a "glue" language, and a language like C/C++ to do the heavy lifting.  Of course, C isn't always very portable, which brings us back to Java.  Java was intended to be a cleaner and more portable C++.  It runs on the server, client, and even embedded devices like cell phones.  A lot of the verbosity came from having to provide a single abstract wrapper to so many different cases (character encodings, locales, file formats, databases, operating systems, etc).  The rest of the verbosity came from its C heritage.

---

### Post by thumper on 2005-12-01
<cough>Bollocks</cough>

C is more portable than Java, except as source not a binary.  Also, I don't believe that Java was intended to be a cleaner and more portable C++. Nor do I believe that the verbosity came from C heritage.  Most C is much more terse than Java.

There is no arguing that Java runs on the server, client and embedded devices, but so does C, C++ and Python.  Admittingly you need to compile the C and C++ prior to deployment, but how often are the same Java applications deployed to server, client and embedded?

What Java does have is an extensive library that comes as part of the language.  Python also has many modules.

---

### Post by LordHunter317 on 2005-12-01
[QUOTE=yaaarrrgg]The difference though is that Java actively imposes more structure on the programmer (which is why most people dislike it).[/quote]Not especially.  The type system of Java is hardly strong enough and must be broken so often to call it an active imposition.

What is true is that some parts of the JCL are very imposing upon the programmer to follow a defined structure, or are setup in such a way that only one solution is effectively correct.

[quote=thumper]C is more portable than Java, except as source not a binary.[/quote]Sure, if we limit ourselves to ANSI C, which doesn't give us:[list][*]Define sizes of any variable, except char == 1 byte (and we don't know how many bits in a bit except through a constant *sigh*)[*]Any networking I/O[*]GUI[*]Proper filesystem support or anythign resembling it[*]Threading[*]Terminals[*]You get the picture[/list]Then yeah, it's more portable, sure.

We already had this discussion, and in this thread no less.  C is not very portable, unless you're talking about ANSI C, which is useless.  And not even the whole set is portable, realistically.  Some stuff, like the minimal signal handling provided by C, doesn't function on say VMS, as you might expect.

---

### Post by Jengu on 2005-12-01
[QUOTE=thumper]I didn't say **no companies** I said not many.
 :)[/QUOTE]

The number of companies that use Python in some way is rather sizeable. It's been used in commercial games, obviously Canonical uses it because it's used for many Ubuntu apps, Redhat's installer is written in it, and google uses it. Zope is also commercial. It's growing.

[QUOTE=LordHunter317]That article has so many factual errors it's not worth reading.[/QUOTE]

You should backup claims like that.

[QUOTE=charlieg]Anybody who thinks they can produce Python code quicker than Java hasn't used Eclipse 3.1 properly.[/quote]

You don't think it should count against Java that you can't be productive in it without knowing a complicated IDE inside and out?

> 
With Python you have to test and run your code before you know it works.


That's the worst argument against a programming language I've ever heard. You *never* know your code is going to work in *any* language until you run it. And in Python, you have the interpreter close by so you can quickly type in code to experiment with. If I want to know how some new library works, I just open the console and type in a few calls. In Java, I'm going to have to setup a project, write a class, and compile. It's just less effort.

> 
Give me an equivalently amazing IDE for Python then you'll be able to argue it's concisor syntax wins over.


How about.... [eclipse](http://pydev.sourceforge.net)?

[QUOTE=jwenting]
Python OTOH IS interpreted by nature, though optionally can be compiled into an equivalent system of Java bytecode.[/quote]

Python's compiling into bytecode isn't at all like Java's compiling into byte code. Java's compiling actually serves to speed up execution to be faster than just interpretation would. Python's byte code compiling just makes imports go faster -- that's it. And the compilation to bytecode happens by default -- when you run a .py script it creates a .pyc file and from then on uses that.

> 
Having tried both, I see Python as having a place to replace Perl for shellscripting and things like that. Java OTOH is a complete platform well suited for enterprise level applications for delivery to customers.

I wouldn't be so quick to pigeon hole python. Python is more of a moving target than Java. It undergoes pretty rapid development and is constantly getting new features. In a few versions it's going to have optional static typing, one of the things that's holding it back from enterprise.

---

### Post by LordHunter317 on 2005-12-01
[QUOTE=Jengu]You should backup claims like that.[/quote]:rolleyes :If you read the entire thread instead of cherry-picking points you don't like, you'd  know I did.



> You don't think it should count against Java that you can't be productive in it without knowing a complicated IDE inside and out?:rolleyes: I think:> You should backup claims like that.  



> In Java, I'm going to have to setup a project, write a class, and compile. It's just less effort.Or, you know, read the documentation. And I don't have to setup projects to write my code.


> Python's compiling into bytecode isn't at all like Java's compiling into byte code. Java's compiling actually serves to speed up execution to be faster than just interpretation would.No, it's not really different at all.  

> And the compilation to bytecode happens by default -- when you run a .py script it creates a .pyc file and from then on uses that.Which contradicts your first two statements.  You haven't provided proof, because you don't have a python runtime that does pure source-interpretation.

---

### Post by cwaldbieser on 2005-12-02
[QUOTE=LordHunter317]
Yes, I can.  Certain divisions of Microsoft produce topnotch software, including, but not limited to: Office, SQL Server, Visual Studio, and the .NET group.

SQL Server is a superior product to the OSS databases in quite a few ways.[/QUOTE]
As someone who uses MS SQL Server every day, I would not be inclined to describe SQL Server 2000 as a "topnotch" product.  Don't get me wrong, it gets the job done, but its behavior is often quirky, and some of the associated tools could have used a lot more polish.  I like using query analyzer, but some of the modal dialogs in enterprize manager drive me nuts.  And DTS could have been a really topnotch tool if the user interface wasn't so crummy and the behavior so quirky.

I guess I can see where it is a superior product to OSS databases in some ways, but I can also flip it around and see where different OSS databases are superior to it in some ways, too.

I'm crossing my fingers that SQL Server 2005 is a little more fun to work with.

---

### Post by LordHunter317 on 2005-12-02
[QUOTE=cwaldbieser]As someone who uses MS SQL Server every day, I would not be inclined to describe SQL Server 2000 as a "topnotch" product.[/quote]Compared to what?  DB II?  Oracle?  Unless your needs are highend or very specific, it's got a significantly better price/performance ratio than either, and is much eaiser to work with than either of them too.

>  Don't get me wrong, it gets the job done, but its behavior is often quirky,Compared to?  All databases are quirky, none behave remotely consistently.

---

### Post by cwaldbieser on 2005-12-02
[QUOTE=LordHunter317]Compared to what?  DB II?  Oracle?  Unless your needs are highend or very specific, it's got a significantly better price/performance ratio than either, and is much eaiser to work with than either of them too.

Compared to?  All databases are quirky, none behave remotely consistently.[/QUOTE]
I wasn't really comparing it to any other database system.  I am just saying it does not seem to be a topnotch product in my opinion as someone who works with it on a regular basis.  I mean, the basic engine works fine.  And the I said I liked using Query Analyzer.  It is much nicer than using, say isql for an Informix DB.  There are several positives.  But there are also negatives to the product suite that make it seem kind of shoddy or like a rush job.

I already mentioned that I think some of the modal dialogs make the user interface painful to use.  I really don't have anything nice to say about the built in editor for stored procedures.  I hate how enterprize manager wants to rewrite my SQL statements when I run them to test them out.  The only gripe I have about query analyzer is that the stored procedure debugger seems a bit flaky-- on some installs, it doesn't seem to want to work.  On others it works most of the time but every once in a while doesn't want to run.

Also, I think DTS needs a major overhaul.  It seems like there ought to be some extra conditions you should be able to use to direct the workflow.  The DTS packages that import data from Excel spreadsheets get confused really easily if the columns get reordered (even if the headings are kept the same) and sometimes the import just doesn't seem to wwant to behave well at all.  The interface needs to be made a little less obtuse.  The packages shouldn't be so tempermental about trying to change the data sources, and there should be some easy way to share your configurations across machines.

Its just that there are a lot of little annoying things about the suite that prevent me from giving it a 5 star rating.

---

### Post by LordHunter317 on 2005-12-02
[QUOTE=cwaldbieser]I wasn't really comparing it to any other database system.  I am just saying it does not seem to be a topnotch product in my opinion as someone who works with it on a regular basis.[/quote]Go use just about any other commerical database heavily and you'll change your tune.

Yes, the flaws in SQL Server 2K are many or numerous.  It's still generally better than all of its competition, even today, for most tasks.

> I hate how enterprize manager wants to rewrite my SQL statements when I run them to test them out.Running SQL in EM it didn't write isn't smart -- that's why you have query analyzer.

> Its just that there are a lot of little annoying things about the suite that prevent me from giving it a 5 star rating.I still think you'd change tune heavily if you took it from the perspective of, "We'll use SQL Server or something else" instead of looking at it by itself.  The former is a more realistic view.

I know if I'm targeting a Windows platform up until recently when PostgreSQL 8.0 was released, SQL Server was always my first choice.

---

### Post by cwaldbieser on 2005-12-02
[QUOTE=LordHunter317]Go use just about any other commerical database heavily and you'll change your tune.

Yes, the flaws in SQL Server 2K are many or numerous.  It's still generally better than all of its competition, even today, for most tasks.

Running SQL in EM it didn't write isn't smart -- that's why you have query analyzer.

I still think you'd change tune heavily if you took it from the perspective of, "We'll use SQL Server or something else" instead of looking at it by itself.  The former is a more realistic view.

I know if I'm targeting a Windows platform up until recently when PostgreSQL 8.0 was released, SQL Server was always my first choice.[/QUOTE]

All I'm saying is that if you are at the top of the ratpile, you're still a rat.  Maybe you are right and all other comercial DBs do suck.  I am not in a good position to comment as Informix is the only other comercial engine I have used semi-regularly.  And I will be the first to say the MS SQL Server stands head and shoulders above it.

In fact, I would be willing to say that for many applications out there, MS SQL Server is probably *the* best product available at the time.  However, it is still a far cry from what I expect in a polished, professional application from a major software vendor.  A lot of the annoying things I mentioned give me the impression that some aspects of the product suite were some guy's internal tools that were sold in a beta state.

I will acknowledge Microsoft is a market leader in their DB niche, but I still see a whole lot of room for improvement.  And if no one complains about the problems, there is no incentive on their part to correct the behavior.

---

### Post by LordHunter317 on 2005-12-02
[QUOTE=cwaldbieser]All I'm saying is that if you are at the top of the ratpile, you're still a rat.  Maybe you are right and all other comercial DBs do suck.[/quote]All DBs suck in their own unique ways.  But in terms of accessiblity and ease-of-use, every other commercial DB I've developed for (Sybase, Oracle) has been far, far, worse.

Well, Objectivity was pretty easy to setup.  But it's an OODBMS, and it's management is non-existant, so it's not a fair comparsion.

> However, it is still a far cry from what I expect in a polished, professional application from a major software vendor.I think you'll find your expectations shattered in a lot of arenas then.  Most "enterprise" grade software isn't waht you'd expect.  DBMS?  No.  J2EE Application Servers?  No.  IDEs?  No.  You get the picture...

> I will acknowledge Microsoft is a market leader in their DB niche, but I still see a whole lot of room for improvement.Well, obviously.  No software is perfect.

>  And if no one complains about the problems, there is no incentive on their part to correct the behavior.Well, people did, and 2K5 was released ;)  I'm just pointing out why I say SQL Server is an excellent product: a lot of it has to do based on everything else it competes with.

---

### Post by [2]BoxingFiend on 2005-12-03
most of my programming needs now include java for work and python for school.. so i said what the hell and now learning jython.  best of both world for me.  you loose some with the merge, but i am gaining so much more speeds with python syntax over the long and tedious java syntax

---

### Post by Jengu on 2005-12-04
[QUOTE=LordHunter317]:rolleyes: I think:  [/quote]

Um, what claim is it you think I'm making that needs backing up? The poster was claiming that if you used Eclipse, a huge IDE (I assume you agree that Eclipse is not notepad) you could write Java code faster than Python. An IDE naturally entails a learning curve. In Python there isn't a lot of extra structure code like there is in Java (in Java to make Hello World you need to define a class for example) so an IDE to automatically type it for you isn't as necessary.

> 
Or, you know, read the documentation. And I don't have to setup projects to write my code.


When the documentation matches implementation, and when the documentation actually exists, sure. And admittedly Java is better about that than Python because Python is just now getting a good equivalent of Javadoc.

BUT, I wasn't thinking so much about APIs as I was how more basic facilities of the language work. In Python for example, I might not remember if there's a difference between the operations "3 + [1, 2]" and "[3] + [1, 2]". I can very quickly type both into the interpreter to find out. In Java, even if I don't have  to setup a project (which AFAIK is the case if you're using Eclipse) I am going to have to write a surrounding class and function, save it to a file, and call java on the file. The interpreter lowers the laziness threshold for me to experiment if I'm a newbie.

More than that, with the interpreter I can see what a command did, and then choose what I want to do next based on that relatively easily. In Java I'm going to have to go back and edit the file and run it all over again. Python's interpreter encourages more 'code play.' And as a debugging tool, I can jump from mid-execution of my python script to the interpreter, enter a few statements, and then resume execution. AFAIK Java cannot do that at all.

> 
No, it's not really different at all.


My technical understanding is that JVM is just that -- an actual virtual machine. The python interpreter is not. I don't see how they could be the same.

> 
Which contradicts your first two statements.  You haven't provided proof, because you don't have a python runtime that does pure source-interpretation.

No it doesn't. I'm drawing a distinction between execution speed and load time. Python's byte code only speeds up the latter.

---

### Post by LordHunter317 on 2005-12-04
[QUOTE=Jengu]Um, what claim is it you think I'm making that needs backing up?[/quote]That one *must* use a complicated IDE to program Java.

> The poster was claiming that if you used Eclipse, a huge IDE (I assume you agree that Eclipse is not notepad) you could write Java code faster than Python. An IDE naturally entails a learning curve. In Python there isn't a lot of extra structure code like there is in Java (in Java to make Hello World you need to define a class for example) so an IDE to automatically type it for you isn't as necessary.This is a non-sequitur, because it has nothing to do with what you were talking about.  You claimed one *must* use an IDE to develop Java code, which is patently false.  There was no discussion of whether an IDE makes you faster or not.

>  I am going to have to write a surrounding class and function, save it to a file, and call java on the file. The interpreter lowers the laziness threshold for me to experiment if I'm a newbie.Nope.  Eclipse has a scratchpad feature that lets you interpret Java on the fly, and there's always BSH, which can do Java interpretation.

>  AFAIK Java cannot do that at all.Yes you can.  Java debuggers exist which support edit-and-continue type functionality.

> My technical understanding is that JVM is just that -- an actual virtual machine. The python interpreter is not. I don't see how they could be the same.That's not what I was referring to.  You were talking about the reason for bytecode interpretation to be different: that Java does it to speed up execution, and python only does it to speed up loading.

The problem is, you *cannot* prove the former because you don't have a python interpreter that doesn't convert source to bytecode first.  So you can't measure the difference in execution time.

And I'm 99.9% positive that speeding up loading time isn't the only reason python's bytecode compiled internally.  I'm sure it's at least in part because the bytecode execution is much faster than run-time source interpretation, which isn't fast as a rule.

> No it doesn't. I'm drawing a distinction between execution speed and load time. Python's byte code only speeds up the latter.*You have no proof of that last statement*.

---

### Post by stormcoder on 2006-02-08
[QUOTE=LordHunter317]Careful here.
Java supports a form of functional programming, but functions aren't first class, so it's not a functional language.  But you can do similiar things, at a much higher and complicated level, unfortunately.
[/QUOTE]

This is incorrect. Python functions are first class and there are also higher order functions like map and reduce. So Python is fully functional.

---

### Post by LordHunter317 on 2006-02-08
[QUOTE=stormcoder]This is incorrect. Python functions are first class and there are also higher order functions like map and reduce. So Python is fully functional.[/QUOTE]No, it isn't, seeing as I wasn't talking about Python but **Java**.  I have no qualms with the idea Python is functional because well, it is.

---

### Post by Jessehk on 2006-02-08
In my experience, Python is a problem-solving language. The pseudo-code-like syntax allows the programmer to think about the problem, rather then the rules and syntax (like in Java, and especially C++). 

Java is used by thousands of companies around the world. 

One thing I don't like about Python is that it doesn't have public/private properties. 

What if I need a field to be private? the __*var-name* trick is just a hack. I really feel the private fields are an essential aspect of OOP.

Keep in mind I could be completely wrong, that was the information I had gathered.

---

### Post by David Marrs on 2006-02-09
> What if I need a field to be private? the __var-name trick is just a hack. I really feel the private fields are an essential aspect of OOP.
Why are they just a hack?

---

### Post by LordHunter317 on 2006-02-09
[QUOTE=David Marrs]Why are they just a hack?[/QUOTE]Because there is no enforcement, it's just a convention.

And yes, smalltalk-based OOP is not ideal here.

---

### Post by Retrix on 2006-02-09
> Because there is no enforcement, it's just a convention.

To be honest, its a little more than a convention (although not much more). Python (AFAIK) will name-mangle the variable when accessed from outside the class. It is not strictly private though, as the name-mangled version is easy to get access to.

Similarly a single underscore prefix makes a member protected through name-mangling.

---

### Post by awi on 2006-02-09
I do not know very much about python, but if I know Java enough to speak for it, so please don't think at my post as a try to flame anybody or anything, just declaring my ignorance about Python, here I go:

In order to understand better J2EE, I recommend to consult the FAQ: [http://java.sun.com/j2ee/faq.html](http://java.sun.com/j2ee/faq.html) 
I have not heard of such a similar standard for python. 
JSP is not part of the J2SE (java standard), it is a new technology, it has its
own separate standard, based on j2se but it is not part of it.
I can say that it is hard for me to think about 5 big projects written in Python (it comes to my head the Mailman and Zope), and by "big" I mean about maturity level, how popular it is,  and if it is a reference to other companies to jump  into the python's train to make a new product or application.
In my opinion, the popularity of Java does not have to do, indeed, with its curve of learning, or just with the quantity or quality of  projects that are built
with it, but with the great variety of environment where it is used: socket server, desktop, Web (jsp and applet), mobile edition, database, java card, etc.
All the technologies requiere its training, but they do not take too much time, once you get to know the basic of the languaje and the API usage, plus they are relatively easy to integrate and to reuse the code among them.
Speaking of that, in answer to the post which mentioned the use of java's I/O system and said that it had to write it several times the same lines, I think the person who wrote that should have to read a little on Design Patterns, and code reusability. :)
The fact that something allows me to make small projects quickly, in no way should be an indicator of which a language is better than another one (IMHO).
What language allows you to deploy without installing absolutely nothing else than  your code (compiled or not)?
The amount of compiled applications is being reduced, it will be difficult to see them disappear, because speed will always be a must in some tasks, but I think that the trend is towards programming languages that have tools to help you be more productive, can escalate easily and help you save time (a.k.a. money :)  )  on average projects.

---

### Post by LordHunter317 on 2006-02-09
[QUOTE=awi]JSP is not part of the J2SE (java standard), it is a new technology, it has its
own separate standard, based on j2se but it is not part of it.[/quote]No, but it is part of the **J2EE** standard, which includes the J2SE standard and other standards (including JSP) for enteprise application development.

> All the technologies requiere its training, but they do not take too much time, once you get to know the basic of the languaje and the API usage, plus they are relatively easy to integrate and to reuse the code among them.No, they do take significant time to train in based on the fact most colleges are now just Java farms.

And no, code reuse isn't high, depending on the two technologies you're talking abou.

> Speaking of that, in answer to the post which mentioned the use of java's I/O system and said that it had to write it several times the same lines, I think the person who wrote that should have to read a little on Design Patterns, and code reusability. :)No one said that.

> What language allows you to deploy without installing absolutely nothing else than  your code (compiled or not)?Several, if you know what you're doing.

> The amount of compiled applications is being reduced,Not especially, unless you exclude bytecode-compliation, which is nonsensical.

---

### Post by awi on 2006-02-10
> **LordHunter317]
No, but it is part of the J2EE standard, which includes the J2SE standard and other standards (including JSP) for enteprise application development.
[/QUOTE]
It is a separate standard, is a part of J2EE, right, but it does not depend on it.
Maybe is just semantic and we are talking about the same, I just wanted to make clear that JSP has its specification separately from J2SE and from J2EE.
[http://java.sun.com/products/jsp/reference/api/index.html](http://java.sun.com/products/jsp/reference/api/index.html)
> J2EE 1.4 SDK contains an implementation of the JSP 2.0 specification.
J2EE SDK 1.3.1 contains an implementation of the JSP 1.2 specification.

and so forth.

[QUOTE=LordHunter317]No one said that.
[/QUOTE]

I was refering to this post: 

[QUOTE=jerome bettis]

this is exactly what i'm talking about.  i've written that every time i've done any file operations in java, but if you wouldn't have posted that, i'd have no idea you need to do that.   ](*,)  also i think you need to wrap the FileReader within a BufferedReader ... but who cares, we agree java has it's flaws.  i used to like it until i used it a lot and was made aware of it's short comings.  apparently there's still quite a few that i don't know about. 
[/QUOTE]

[QUOTE=LordHunter317]Several, if you know what you're doing.
[/QUOTE]
Really? Platform independent? I love reading, and whenever I can, participate said:**
> Not especially, unless you exclude bytecode-compliation, which is nonsensical.

I was refering to the platform dependent, machine code binarys. I should have been more clair on that, my mistake.

---

### Post by LordHunter317 on 2006-02-10
[QUOTE=awi]It is a separate standard, is a part of J2EE, right, but it does not depend on it.[/quote]**No, J2EE depends on it.**  You cannot have a complaint J2EE Web container server without implementing the JSP specification, along with a few others.

It's impossible.  You won't be certified.  Your own quote supports my statements.  To be certified J2EE X complaint, you have to implement the matching JSP specification.  It's not optional.

The fact Sun has the standard in a seperate document means nothing.  They do that for lots of Java technology.

> Maybe is just semantic and we are talking about the same, I just wanted to make clear that JSP has its specification separately from J2SE and from J2EE.Which doesn't change the fact it is a J2EE standard.

> Really? Platform independent?Yes, you can sometimes go static, or you can ship any dependent binaries as part of your application.  Windows applications do this all the time; for cross-platform examples, look at GAIM, VMWare, GIMP, and a few others.

---

### Post by awi on 2006-02-10
> **LordHunter317]**No, J2EE depends on it.**  You cannot have a complaint J2EE Web container server without implementing the JSP specification, along with a few others.
[/QUOTE]
I mean to say JSP does not depend on J2EE, I'm sorry if my english is not too good, it is not my native language.

JSP is build upon J2SE
J2EE is build upon JSP and the few others as you say.

I never say JSP was optional, I put the link to the JSP standard, I never get into the details of J2EE, or server compliant, or anything like that. I know the J2EE standard, and what it complies.  

[QUOTE=LordHunter317]
Yes, you can sometimes go static, or you can ship any dependent binaries as part of your application.  Windows applications do this all the time said:**
> 
Or you can just give away a DVD with every possible library  that your application might need, for every invented platform out there, plase, this is really a cheap get away.
I did not say cross-platform.
I wrote Platform Independent applications. I don't know  any binary executable of the apps you listed that can run on any platform, I'm talking about the same executable.
[QUOTE=LordHunter317]
Supporting static compliation for an application of any size is generally a silly investement, if it's even possible.

---

### Post by LordHunter317 on 2006-02-10
>  I don't know  any binary executable of the apps you listed that can run on any platform, I'm talking about the same executable.POSIX binaries compiled to iCBS2 will run on multiple UNIX platforms.  They're also very limited.

Binary platform-independence isn't interesting anyway.  It's much eaiser to push that to a central server, if you need to support multiple clients and make the code on the clients as small as possible.

It's only a distribution problem

---

### Post by Viro on 2006-02-10
[QUOTE=LordHunter317]
Binary platform-independence isn't interesting anyway.  It's much eaiser to push that to a central server, if you need to support multiple clients and make the code on the clients as small as possible.

It's only a distribution problem[/QUOTE]

Agreed. I used to be sold on the concept of Java, write once, run anywhere. Of course, this is true to a certain extent. Java applications usually run without any major changes on Linux, Windows, and the Mac (platforms I've run on). Nowadays, I'm far more hot on writing once, compiling anywhere. At least, my applications don't feel so out of place, something that plagues most Java Swing apps.

---

### Post by awi on 2006-02-10
[QUOTE=LordHunter317]POSIX binaries compiled to iCBS2 will run on multiple UNIX platforms.  They're also very limited.

Binary platform-independence isn't interesting anyway.  It's much eaiser to push that to a central server, if you need to support multiple clients and make the code on the clients as small as possible.

It's only a distribution problem[/QUOTE]
I never said I was interested on binary platform-independence, and I was not talking about a client/server or similar arquitecture for the application, I simply said that your listed application have not such feature (platform independent).
IBCS2, as far as I know, are emulations and restricted to Unix and Intel, and have to do with binaries, I thought we were discussing programming languages here.

---

### Post by LordHunter317 on 2006-02-10
[QUOTE=awi]I never said I was interested on binary platform-independence,[/quote]Seeing as you were talking about not having to install platform-dependent files, I have no clue what you were takling about then.

---

