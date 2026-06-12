---
title: "&quot;power&quot; of a language"
date: 2007-09-03
forum: Programming Talk
---

### Post by slavik on 2007-09-03
what do you look at when comparing two languages which is more powerful of the two?

IMO, the more powerful language does more with less syntax, for example:
perl is more powerful than C because of regex and literally 1 line of code to open a socket.

---

### Post by Mirrorball on 2007-09-03
It depends on what kind of power you want. You could also say that C is more powerful than Perl because it's faster and has access to low level resources.

---

### Post by angryfirelord on 2007-09-03
It really depends on your needs. Do you want a language that's very flexible? Do you want a RAD language? 

IMO, the key choice would be portability. Can your program run on Linux as well as Windows? Java & C++ (with QT for GUIs) are very good at this.

---

### Post by ryno519 on 2007-09-03
It's hard to compare to languages with the intent of declaring one better or more powerful than the other. I think the power of a language has more to do with the programmer than the language being used. A programmer can be excellent with one language and absolutely horrible with another.

So I think it has less to do with the clarity of syntax than the experience and knowledge of a programmer. Other factors include support, such as the amount of libraries and shared code which can be used with that language. That being said, if you know what you're doing you can get just about any language to do just about anything you want.

---

### Post by Wybiral on 2007-09-03
I generally define the "power" by what I intend to use the language for... As Mirrorball mentioned, languages like perl may be more compact, but perl has nothing on C in terms of speed and memory use because C is so low level.

If I know I'm going to write a mathematically intensive, graphical, or anything that just generally needs speed (such as a game), I will use C or C++ depending on the level of abstraction I think I'll need.

For games that don't require as much power, Python will do great.

If I'm going to write some kind of clientside web application that requires me to handle DOM objects... I will probably use Javascript.

If I'm going to write a serverside application that requires me to communicate with a database, I'd probably opt for PHP and SQL.

But even these are just my preference... Not really a measure of power.

---

### Post by slavik on 2007-09-03
umm, my question is exactly what YOU consider to be "power" when speaking about "power" of a language.

---

### Post by ssam on 2007-09-03
as a physicist i'd say power is easy to define. work/time. :-)

as a programmer i'd say that something like javascript is not very powerful. because it can only be used for a very small set of tasks eg manipulating a webpage.

next would be scripting languages like bash. useful for fairly advanced tasks, or very simple applications.

python/perl etc is pretty powerful, it can be used to write almost any sort of application.

c is very powerful. can be used to write an operating system, or program a PIC, aswel as applications.

---

### Post by aks44 on 2007-09-03
I sorta agree with Wybiral.

However to answer your question the way you intend it: to me "power" is a matter of *what the language allows you to do*, no matter verbosity, time spent etc.


So I guess I'd elect C++ as the most powerful language I know of, as it can do very low level stuff (including inline ASM) as well as very high level stuff (even though it sometimes requires quite some effort, but way less than C anyway). Once you get to know it correctly, you can really get whatever you want out of it, most of the time quite easily.

---

### Post by lisati on 2007-09-03
As well as all that has been already been said, there's the question of how much reliance on pre-written libraries you are comfortable with. The one line of code to open a socket usually represents a certain amount of work by one or more software develepers somewhere, even if the details are hidden from the programmer. And what if your program needs something slightly different to what was assumed by the developers of the language you happen to be using?

---

### Post by aks44 on 2007-09-03
> **lisati said:**
> The one line of code to open a socket usually represents a certain amount of work by one or more software develepers somewhere, even if the details are hidden from the programmer. And what if your program needs something slightly different to what was assumed by the developers of the language you happen to be using?

Good point, flexibility is also a good metrics for a language's "power".

---

### Post by Wybiral on 2007-09-03
> **slavik said:**
> umm, my question is exactly what YOU consider to be "power" when speaking about "power" of a language.

And what I was saying is that sometimes I need a different type of "power".

There's no such thing as a generically "powerful" language.

You can break it down and say that abstraction and one-liners make a language powerful, but in those cases, power is taken from flexibility and low-level efficiency. If you gauge a language by raw low-level power, then power is taken from portability and development time.

If someones goal was to open sockets, I could write a language to open a socket with a one character command... But it would hold no power at all if you tried to use it for writing something like a game.

Power is a measure of how efficient that language will be for your specific goal... In smaller non-speed-critical applications, power is probably in development time and built in libraries... In applications that require maximum efficiency, low-level optimization might be more important then development time and portability..

---

### Post by Mirrorball on 2007-09-03
> **slavik said:**
> umm, my question is exactly what YOU consider to be "power" when speaking about "power" of a language.
Languages are like super heroes, they have different powers and abilities. Do you want speed? C. Clean code? Python. Portability? Java. Do you want it to run on browsers? Javascript. Obscurity? Brainfuck, whitespace.

---

### Post by Note360 on 2007-09-03
I only see a flame war.

---

### Post by ghostdog74 on 2007-09-03
> **Note360 said:**
> I only see a flame war.

what you can do is just ignore this thread. read(or not), and move on.

---

### Post by Fbot1 on 2007-09-03
"power" is a cool why to say it's good.

---

### Post by AusIV4 on 2007-09-03
In my Comparative Programming Languages course, my professor defined the power of a language to be based on the number of symbols needed to express an action. He cited APL ("A Programming Language") from 1961 to be the most powerful language. Indeed, very complex ideas could be expressed with very few characters, but it could not be easily read (or learned) and had to be deciphered by someone knowledgeable in the language.

---

### Post by tgbrowning on 2007-09-03
I dunno -- this kind of reminds me of a conversation I had with a friend a number of years ago. I was learning assembly language at the time and since this  one guy knew more about every bloody language I'd ever heard about, his views had a bit of heft to them. 

The guy's name was Bud Rasmussen and he was a real old timer -- worked originally on mainframes before going to PCs (in the last all assembler shop working for the state of Oregon). His view was the language HAD to be suited to the task. Period.  

You don't use a hammer to peel potatoes. It's not a good idea to use an .45 on field mice.

I took his advice to mean that it was kind of a waste of time to write assembly language databases, and probably not a good idea to write device drivers in something like Cobol or Fortran. 

Browning>>>
[ Bud also used to say C was for programmers who didn't have the balls to do assembly language, too, so the guy wasn't perfect. Just very, very good.]

---

### Post by pmasiar on 2007-09-03
> **slavik said:**
> IMO, the more powerful language does more with less syntax, for example:
perl is more powerful than C because of regex and literally 1 line of code to open a socket.

You need to distinguish "less syntax" and "less characters to type". Language like Lisp or Forth don't have much syntax to talk about. They are kinda similar, but Lisp is much more wordy because of all parentheses. Does number of characters to type tell us something about the power? Yes it does. Is it main or leading criteria? You are kidding, right?

More important than syntax is the concepts which language supports. Can you pass function as parameter? Can object find out if it had needed method (introspection)? Can object add methods and attributes at runtime ("monkey-patching")? And if it can, how hard it is to use, and how error-prone?

All languages are compromise between competing and excluding goals: Java decide to skip over multiple inheritance (M.I.) and operator overloading, because it was considered "confusing" in C++. So Java lost M.I. (which is used extremely rarely anyway) and gained some simplicity. Was it good trade-off? It depends if your code needs M.I. - if not, you lost nothing and gained simplicity. :-)

Forth has extremely simple and powerful syntax, and code is extremely compact. It comes for the price: Compiler does not shield you from type errors, and syntax is postfix ( even condition is <test> IF ... ELSE ... THEN ). Is it worth? Forth gurus say, absolutely, but Forth is not for everyone. 

APL was mentioned as even more terse language: like beyond terse. One-liner can take hours to decipher and understand. Is it sign of power?

Languages are like cars: For most people Honda Accord or Toyota Camry is just fine... Of course, unless you need to commute 3 hours one way daily, or compete in NASCAR, or need to haul tomatoes from California, or need dirt cheap vehicle to travel to California like Borat did :-)

Programming is engineering task: optimizing solution between competing goals. Until you tell us what are restriction of the project, and what are preferences, any guess would be just wild guess with no resemblance to optimal solution.

It is so boringly obvious, it is not even worth flamewars :-)

---

### Post by samjh on 2007-09-03
For me, the power of a language is measured by how well it is able to do what I need it to do.

As people have said over and over again in these forums and elsewhere, programming languages are tools.  A means to an end.

If I need to a good multitool, I will choose a good quality genuine Leatherman tool, instead of a cheap Chinese imitation.  I know the genuine Leatherman tool will have more tools, is more reliable and robust than an imitation.

Pmasiar mentioned cars.  If I'm to compete in a gravel rally event, I will choose a Subaru Impreza WRX, not a Ferrari Enzo.  But put me in a tarmac circuit-racing event, and I will choose the Enzo instead.

For writing a device driver, I will choose C instead of Python.  But for scripting an annoyingly repetitive task quickly, I'd rather choose Python.  If I need to write avionics or life-support software, I'll choose Ada.

The analogies and examples can be endless.

---

### Post by slavik on 2007-09-04
> **pmasiar said:**
> Forth has extremely simple and powerful syntax, and code is extremely compact. It comes for the price: Compiler does not shield you from type errors, and syntax is postfix ( even condition is <test> IF ... ELSE ... THEN ). Is it worth? Forth gurus say, absolutely, but Forth is not for everyone.

guess I suck at explaining my question. When you say "powerful syntax" what exactly goes through your mind when you say powerful?

also,with analogies, it seems that some have mistaken "power" for "proper application"

bringing back the cars: if a truck and a sedan/coupe have the same engine power (measured in horsepower), the truck is usually considered "more powerful" because of its higher torque. to restate my question: What talking about the "power" of the language (not in a specific situation) what exactly do you think when using that word?

---

### Post by tgbrowning on 2007-09-04
Okay, I'll give it a shot but I doubt if it's going to be what you.

For me, power is programmer control over the environment in which he works/writes programs. For me, the language needs to be able to do the job I want, help me to find and exterminate bugs that inevidibly creep in, have enough clarity in structure for me to be able to come back to a project a year later and still be able to follow what I was doing. The language should encourage internal documentation if it can (assembly can be very well documented, if one works at it-- but assembly doesn't lend itself, naturally, to self-documentation). The language should be consistent and stable, meaning that legacy programs do not get completely disemboweled by changes in the language.  

You'll find parts of any langauge that can be extremely powerful -- in assembly langauge, for example, you can set up translation tables with the xlat command that knock your socks off -- blindingly fast, easy to understand, easy to modify and adapt. In C, you can pack a number of operations into one single line of code that's clear and runs like a rabbit. In pascal, you can do recursion till the cows come home and see very little waste in memory or speed. Even bloody old-fashioned Basic had string functions that were great -- miles ahead of C -- and the garbage collection was, in general, completely transparent. C often is horrible for garbage collection and if you've ever been a beta tester for one of the big companies on a compiler project, you know that memory leaks can kill you suddenly and without warning.

Browning>>>

---

### Post by slavik on 2007-09-04
I think I came up with a very good exmple:

operator/function overloading, it is very powerful, no matter the language :)

---

### Post by xtacocorex on 2007-09-04
> **slavik said:**
> operator/function overloading, it is very powerful, no matter the language :)
I agree, but there are limitations.  FORTRAN 90/95 allows you to only create operators with the dot notation, so if I wanted to create a function and an operator to do x-roots, I'd have to name it (operator) .XROOT. and call it like this:
```
MYROOT = XVAL .XROOT. 4
``` to get the 4th root of a number.  That's almost the same as writing
```
MYROOT = XROOT(XVAL,4)
```
, which would make the code more readable, especially since most people haven't caught on to the fact that you can do operator overloading in FORTRAN.

If you notice, both examples use the same number of columns, so which one is better?  Granted I could change .XROOT. to .XRT., but then you'd confuse new users to the program if they saw that syntax.

You can only overload +,-,*,/,**(power) and keep those symbols, so if I wanted to make a shortcut to the MOD() function in FORTRAN and use % as in other languages, it wouldn't be possible - I've tried.

I have only dabbled in operator overloading, so I'm not an expert, but I know it to be less limited in C++ and expect it to be farily easy in Python.

---

### Post by Wybiral on 2007-09-04
> **slavik said:**
> I think I came up with a very good exmple:

operator/function overloading, it is very powerful, no matter the language :)

Operator overloading is another one of those things that depends on the task.

Some tasks will become more readable with operator overloading, such as vector and matrix mathematics, while some tasks would become less readable (and completely unnecessary) such as low-level driver code.

So once again, it depends on the task at hand. Power is not a general measure in programming languages.

---

### Post by bogolisk on 2007-09-04
> **slavik said:**
> I think I came up with a very good exmple:

operator/function overloading, it is very powerful, no matter the language :)

Hmm, in most large-scale (100 sw desgners) C++ projects I've worked on, operator-overloading were all **banned** and function overloading are frowned upon!:)

In one project, the banned for operator-loading was banned after a guy overloaded the comma operator:
```

        x(), y(), z();

```
would schedule 3 functions (x,y and z)  in parallel on 3 cpu cores!:)

---

### Post by pmasiar on 2007-09-04
> **slavik said:**
> guess I suck at explaining my question. 

Sorry about that. I think everyone was just running to the trench scared that new flamewar is just going to erupt  :-) We should be smarter, we know you long enough that you are more thoughtful than that. **Of course** you are one of people saying "use right tool for the job" when some noob is asking for silver bullet. So your question is deeper.

And it really **is** a good question: when you are looking best tool for a job, how do tell if this tool is sharp and flexible? Thanks for asking. Not easy to answer, but good question to contemplate.

For me:

I like if language has small number of basic concepts which work good with each other. Like in Python, you can use for loop to iterate through a list, array, string, tuple, dictionary, or iterator expression. All of these are **very** different by themselves, but it makes sense to look at every item in them one by one, and **exactly same syntax** allows me to do that.

I like language which allows me to pass parameters in a flexible way, and make changes later, and still have it reasonably easy. What if I need to pass function as a parameter? What if I need to return more than simple scalar value from a function? What If this scalar returned here needs to become array? How many headstands and push ups  I need to do to make compiler happy?

I like language which lets me to use facilities accessible to it. If "they" can do it, I want be able to do it, when I need it. I remember PROGRESS database was able to make some operations on system data types which were not possible on my variables of same type. I forgot the details now, but I remembered how I was annoyed: they just decided that I am just a farmer in dirty boots and not smart enough to handle it, so I am not allowed to handle it. Yes, I like language to tread me as responsible smart adult, not as dumb relative who needs to be protected for his own good. Like operator overloading in java: they can do it for strings, but I cannot. Come on! If it is useful to you, it could be useful to me to!

I like language "to make simple things easy, and hard things possible". My first language with this approach was Perl, and I **loved** it. Duck-typing is so great, I could not believed how you can write code without fighting with compiler, and if you passed object done properly, it just works. So compiler might be your friend, not gestapo interrogator! What a concept!

Also, simple things should **look** easy. Like ZIP compression: if something is used often, add some syntax sugar so it **looks** easy. If something is dangerous, add some syntax vinegar to it so it looks scary. As I read some architect talking about "design patterns" and how to judge them: design pattern is good, if people use it right way intuitively, without thinking. Like push and pull doors: It is hard to pull on push side, and pull side just invites you to pull (and not push). I am not sure how doors are done in other (non-USA) countries tho :-)

So here is something to think about...

Good question, I will post more when I manage to verbalize it :-)

---

### Post by slavik on 2007-09-04
> **pmasiar said:**
> Sorry about that. I think everyone was just running to the trench scared that new flamewar is just going to erupt  :-) We should be smarter, we know you long enough that you are more thoughtful than that. **Of course** you are one of people saying "use right tool for the job" when some noob is asking for silver bullet. So your question is deeper.

And it really **is** a good question: when you are looking best tool for a job, how do tell if this tool is sharp and flexible? Thanks for asking. Not easy to answer, but good question to contemplate.

For me:

I like if language has small number of basic concepts which work good with each other. Like in Python, you can use for loop to iterate through a list, array, string, tuple, dictionary, or iterator expression. All of these are **very** different by themselves, but it makes sense to look at every item in them one by one, and **exactly same syntax** allows me to do that.

I like language which allows me to pass parameters in a flexible way, and make changes later, and still have it reasonably easy. What if I need to pass function as a parameter? What if I need to return more than simple scalar value from a function? What If this scalar returned here needs to become array? How many headstands and push ups  I need to do to make compiler happy?

I like language which lets me to use facilities accessible to it. If "they" can do it, I want be able to do it, when I need it. I remember PROGRESS database was able to make some operations on system data types which were not possible on my variables of same type. I forgot the details now, but I remembered how I was annoyed: they just decided that I am just a farmer in dirty boots and not smart enough to handle it, so I am not allowed to handle it. Yes, I like language to tread me as responsible smart adult, not as dumb relative who needs to be protected for his own good. Like operator overloading in java: they can do it for strings, but I cannot. Come on! If it is useful to you, it could be useful to me to!

I like language "to make simple things easy, and hard things possible". My first language with this approach was Perl, and I **loved** it. Duck-typing is so great, I could not believed how you can write code without fighting with compiler, and if you passed object done properly, it just works. So compiler might be your friend, not gestapo interrogator! What a concept!

Also, simple things should **look** easy. Like ZIP compression: if something is used often, add some syntax sugar so it **looks** easy. If something is dangerous, add some syntax vinegar to it so it looks scary. As I read some architect talking about "design patterns" and how to judge them: design pattern is good, if people use it right way intuitively, without thinking. Like push and pull doors: It is hard to pull on push side, and pull side just invites you to pull (and not push). I am not sure how doors are done in other (non-USA) countries tho :-)

So here is something to think about...

Good question, I will post more when I manage to verbalize it :-)
QFT and I agree with everything you said. :) (Is this the first time we agree on something? ;))

---

### Post by CptPicard on 2007-09-04
Irrelevant. They're all TM-equivalent anyway, the rest is syntactic sugar that is more or less suitable for different tasks :p

(Ok, ok... so pmasiar is correct. Slavik, did you have to quote everything?)

Personally, I am really fond of Scheme. There are very few basic concepts, it's got first-class functions/closures out of the box and you can code in any style you like once you learn the idioms (you can even do OOP in functional style if you return message-receiving lambdas with their data in their own closure!) And continuations are just beautiful, although they scar your young mind forever once you grok them and start terrorizing your lesser fellow programmers with continuation-passing style programming that forces them to transform their code too if they want to interact with yours!

I should really do more in Scheme...

---

### Post by pmasiar on 2007-09-04
> **CptPicard said:**
>  (you can even do OOP in functional style if you return message-receiving lambdas with their data in their own closure!)

Doing OOP like that feels like industry-grade vinegar to me :-)

---

### Post by bogolisk on 2007-09-04
> **CptPicard said:**
> Irrelevant. They're all TM-equivalent anyway, the rest is syntactic sugar that is more or less suitable for different tasks :p

(Ok, ok... so pmasiar is correct. Slavik, did you have to quote everything?)

Personally, I am really fond of Scheme. There are very few basic concepts, it's got first-class functions/closures out of the box and you can code in any style you like once you learn the idioms (you can even do OOP in functional style if you return message-receiving lambdas with their data in their own closure!) And continuations are just beautiful, although they scar your young mind forever once you grok them and start terrorizing your lesser fellow programmers with continuation-passing style programming that forces them to transform their code too if they want to interact with yours!

I should really do more in Scheme...

Agree, call/cc is awesome. Once you mastered Scheme's continuations, Java/C++/Python exception handling would look so primitive. 

Back to original topic of best tool for task. Java is really a non-ideal language for XML parsing (compared to lisp dialects), but since it has impressive XML parsing libraries, many ppl use Java for parsing XML. Same for Perl5 wrt recursive-descent parsing (Perl6 fixed that). So the matter become much more gray: sometime a language is not ideal for the task, but its standard library is so convenient for the said task.

---

### Post by LaRoza on 2007-09-04
> **CptPicard said:**
> 
(Ok, ok... so pmasiar is correct. Slavik, did you have to quote everything?)


It was QFT, "Quoted for Truth".

---

### Post by CptPicard on 2007-09-04
> **pmasiar said:**
> Doing OOP like that feels like industry-grade vinegar to me :-)

If you think of it, that's what an object *is* -- a bunch of data items with associated code, which can be abstracted as a single function that takes the specific operation as a symbol parameter. If Python insists on passing "self", passing 'op_name as the first parameter can't be so bad ;)

Considering that Scheme is a functional language, I find it remarkable how naturally the concept of an object arises from the functional primitives. It's even duck typed -- as long as your lambda accepts a certain symbol, you're good to go, and "object hacking" to add functionality, or even overloading, is as simple as wrapping your lambda into another lambda that recognizes more stuff or handles old symbols differently :)

It's moments of illumination like this I get from Scheme are what make me like it. It might not be the language of choice for me to implement something big and fancy, but it certainly makes me a better programmer to know it. It's like academic Latin :p

> **bogolisk said:**
> Agree, call/cc is awesome. Once you mastered Scheme's continuations, Java/C++/Python exception handling would look so primitive.

Yeah, but on the other hand, exception handling is restricted the way it is because it's essentially an error reporting system, not a generalized control structure, and it works well for the purpose. Call/cc on the other hand can be used to implement exceptions, but it can be used to toss evaluation states around freely at will, which is of course to be handled with care, a bit like goto...

> Same for Perl5 wrt recursive-descent parsing (Perl6 fixed that). So the matter become much more gray: sometime a language is not ideal for the task, but its standard library is so convenient for the said task.

Good example... if there is anything that is second nature to Lisp-like languages, it's got to be recursive descent parsing...

---

### Post by pmasiar on 2007-09-04
> **slavik said:**
> Is this the first time we agree on something? ;)

I have no idea, I don't keep the count. :-) Do you? :twisted: I recall you as a guy who prefers Perl, so you are mostly friend in a big battle against statically typed languages - you've seen the light! :-) Other that that, I try comment on the post as I understand it without relying on personality of the poster - I don't see point in joining a clan to beat up another clan. 

I am trying to show people that raw CPU power is not the only criteria, "speed to market" is IMHO most important speed in software development, and Python is really nice little language. When time will be ripe, I fully expect to convert **you** to Python, too :-)

---

### Post by slavik on 2007-09-04
> **pmasiar said:**
> I have no idea, I don't keep the count. :-) Do you? :twisted: I recall you as a guy who prefers Perl, so you are mostly friend in a big battle against statically typed languages - you've seen the light! :-) Other that that, I try comment on the post as I understand it without relying on personality of the poster - I don't see point in joining a clan to beat up another clan. 

I am trying to show people that raw CPU power is not the only criteria, "speed to market" is IMHO most important speed in software development, and Python is really nice little language. When time will be ripe, I fully expect to convert **you** to Python, too :-)
only as much as perl6 will be like python. honestly, perl and C do everything I need. There isn't a use for which I found for python to be better than perl. keep in mind that I would have to learn the syntax and the absence of clearly defined blocks (with braces at both ends) still puts me off.

---

### Post by Wybiral on 2007-09-05
> **slavik said:**
> keep in mind that I would have to learn the syntax and the absence of clearly defined blocks (with braces at both ends) still puts me off.

The syntax is simple and the blocks are clearly defined, by indentation.

---

### Post by slavik on 2007-09-05
indentation != braces

---

### Post by Wybiral on 2007-09-05
> **slavik said:**
> indentation != braces

I didn't say it did, I was just saying that indentation can "clearly defined blocks" without needing braces. You do get used to it (I'm a C programmer too, but I'm pretty familiar with the Python style now).

---

### Post by LaRoza on 2007-09-05
> **slavik said:**
> indentation != braces

Do you usually indent? (Not an argument, just wondering, I wish that Python had {}, but "from __future__ import braces" didn't work.)

---

### Post by pmasiar on 2007-09-05
Indent vs braces is a strawman argument.

If you indent correctly, your C indent should have exactly same structure as Python indent.

If your eyes desire so, you can add braces like this:

```

if x == 1: #{
   code
#} end if

```

:-)

> **LaRoza said:**
> Do you usually indent? (Not an argument, just wondering, I wish that Python had {}, but "from __future__ import braces" didn't work.)

Yes, it **does** work, and expresses position on braces as easter egg:

```

>>> from __future__ import braces
SyntaxError: not a chance (<pyshell#0>, line 1)

```

But as I said, braces are strawman.

---

### Post by daveshields on 2007-09-05
The power I want is "expressive power," by which I mean the programming language doesn't get in the way when I'm trying to set down an algorithm.

If you haven't yet tried Python, you're in for a treat.

Another important point is readability. You want a programming language that lets you write code you can read and comprehend months after you have written it. Languages such as perl and apl are neat but can be difficult to follow, even if you wrote the code yourself.

---

### Post by CptPicard on 2007-09-05
> **pmasiar said:**
> Indent vs braces is a strawman argument.
If you indent correctly, your C indent should have exactly same structure as Python indent.


I know this is a point that has been argued ad nauseam everywhere, but I am not really convinced of braces being superfluous... I just know that I make indentation-related structure errors in Python far more than in other languages, and I'm not really sure what this bondage and discipline feature is supposed to accomplish ;)

Because indentation has to hold the same information as the braces, editors will of course recognize the structure as you go just as well as a C-editor, but I find myself counting whitespace way too much for comfort. And because it's whitespace, it's hard to count. When you edit, you spend way more time actually actively understanding the semantics of your code in relation to the big picture so that you don't break things... braces actually act as tokens up there and down there that carry the structural meaning, without the meaning being on the line you're editing, on a per-line basis, in the form of already realized whitespace. Once you've edited, you just hit M-q or whatever to reflow your code, and if your syntactic tokens match up, all is well and your code is automagically pretty even locally, and you don't really care how many levels deep you actually are. Python, on the other and forces you to restate your semantic intent on every single line, using the most difficult markup to quickly visualize...

---

### Post by Wybiral on 2007-09-05
> **CptPicard said:**
> And because it's whitespace, it's hard to count.

Your modules shouldn't be going so deep that you have difficulty counting the whitespace (I've never actually counted whitespace in python, it's almost always clear just by looking). Python encourages you to modularize your code and break things into more convenient chunks, not throw everything into one chunk and go seven or eight levels in... That's just bad practice anyway. If you use something like the four space tab (real spaces, not tab) rule, then you should have no trouble at all distinguishing between levels.

---

### Post by pmasiar on 2007-09-05
> **CptPicard said:**
> counting whitespace 


If you used editor better that notepad, with syntax setting supporting python, all would happen automagically - no counting, no problem.

Of course you have right to insist on using notepad. You  also have right to shoot yourself to the foot. :-)

---

### Post by Mirrorball on 2007-09-05
> **LaRoza said:**
> Do you usually indent?
In my innocence, I thought everyone indented their code. I always do it (or rather my text editor does it). My C++ code looks like my Python code with braces and semicolons added, so I think getting rid of them makes perfect sense. In any case, isn't it a lot easier to recognize code blocks by indentation than by counting braces?

---

### Post by Wybiral on 2007-09-05
> **pmasiar said:**
> Of course you have right to insist on using notepad. You  also have right to shoot yourself to the foot. :-)

Actually, I only use Gedit  even for Python code and I can still clearly see the indentation. I don't think it's any more difficult then seeing it in C or C++ code.

---

### Post by pmasiar on 2007-09-05
> **Wybiral said:**
> Your modules shouldn't be going so deep that you have difficulty counting the whitespace.

You are so right. Too deep indent is one of basic code smells: in [wikipedia](http://en.wikipedia.org/wiki/Code_smell) and in [design pattern wiki](http://c2.com/xp/CodeSmell.html) (the original wiki - I cannot recommend this site high enough :-) )

---

### Post by slavik on 2007-09-13
in any case, when I say "power" of a language, I mean that it allows me to do things with less code (not library related).

for example: a language with regex is more powerful than one without (if all else is the same).

---

### Post by pmasiar on 2007-09-13
> **slavik said:**
> a language with regex is more powerful than one without 

What if language has regex module, technically outside of language itself? Does it count?

because having it in library has many positives:
- can be developed and stabilized independently (new releases can be made available for same release of language, if API is stable)
- if beginner is not interested in regex for now, she does not need to learn part of the language dealing with it
- language parser is simpler

This particular Perl misfeature is, IMHO, better solved as re library in Python. Just IMHO, YMMV.

---

### Post by pmasiar on 2007-09-15
I just wanted to share link to interesting Spolsky's article [The Perils of JavaSchools](http://www.joelonsoftware.com/articles/ThePerilsofJavaSchools.html) where he claims Java is not hard enough to weed out wannabes from real programmers who can handle poitners without melting the brains.

Interesting take at the language power: to **increase** drop-out rates from CompSci courses! Spolsky's articles  are always a good read. Enjoy!

Bonus link: [Teach Yourself Programming in Ten Years](http://norvig.com/21-days.html) - making fun of "teach yourself X in N days" books, and how you can **really** learn programming (in 10 years) :-)

---

### Post by CptPicard on 2007-09-15
Joel is right, but it's not about Java vs. C. I don't think it's the toughness of the language. I think the language that is taught as the first language should be relatively easy -- like Java -- so that you can then actually start implementing the actual, real stuff. But, I also agree that CS degrees are horribly dumbed down...

I fortunately took a pretty old skool kind of CS degree, where indeed the weedout classes were the undergrad "introduction to models of computation" (finite state automata, stack automata, pre-TM-stuff) and Data Structures. I actually took Data Structures six months early from the usual curriculum, and managed to take a more hands-on version of it... lecturer's preference was to focus more on making students implement stuff in Java. The one I should have taken if I hadn't been early, was mostly about proving running times and using pencil and paper, and the dropout rate was truly impressive I hear :)

In CS you shouldn't get too bogged down in choice of language etc... then again any student worth anything is going to be able to pick up a dozen languages on his own. It's the ideas that matter, and standards should be kept high there.

---

