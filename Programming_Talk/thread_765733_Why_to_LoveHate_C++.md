---
title: "Why to Love/Hate C++"
date: 2008-04-23
forum: Programming Talk
---

### Post by lnostdal on 2008-04-23
first of all .. posting; you're doing it wrong

.. you do not say "a ton of errors" and nothing else .. ever .. 

when it comes to compilers usually the first couple of lines are the most important, and the rest are followup errors caused by that initial error .....

but ok, try g++ instead of gcc

edit:
oh, and try something sane .. C++ is evil vile crap {situation needed? ..see  [http://yosefk.com/c++fqa/](http://yosefk.com/c++fqa/) }

* C
* Python
* Common Lisp
* Ruby

..are all good and sane languages

---

### Post by Natr0n on 2008-04-24
> **lnostdal said:**
> first of all .. posting; you're doing it wrong

.. you do not say "a ton of errors" and nothing else .. ever .. 

when it comes to compilers usually the first couple of lines are the most important, and the rest are followup errors caused by that initial error .....

but ok, try g++ instead of gcc

edit:
oh, and try something sane .. C++ is evil wile crap {situation needed? ..see  [http://yosefk.com/c++fqa/](http://yosefk.com/c++fqa/) }

* C
* Python
* Common Lisp
* Ruby

..are all good and sane languages

+10

---

### Post by tseliot on 2008-04-24
> **lnostdal said:**
> edit:
oh, and try something sane .. C++ is evil vile crap {situation needed? ..see  [http://yosefk.com/c++fqa/](http://yosefk.com/c++fqa/) }

* C
* Python
* Common Lisp
* Ruby

..are all good and sane languages
C++ is a sane language. Flame-baits are not welcome.

---

### Post by lnostdal on 2008-04-24
> **tseliot said:**
> C++ is a sane language. Flame-baits are not welcome.

Well, then we disagree. Flame if you want; I do not care. Heck -- I won't even respond.

edit: maybe you wouldn't care to comment if i said this "vs." a language like, say, any other .. think about it

---

### Post by samjh on 2008-04-24
Hmmm... comparing Brainfuck to C++ is stretching it. ;)

C++ is whatever you want it to be.  If you want to be insane with C++, it will oblige without question!  Frankly, I have little patience with it, but it is undoubtedly a very powerful language in the right hands, dangerous in the wrong hands.

---

### Post by lnostdal on 2008-04-24
> **samjh said:**
> Hmmm... comparing Brainfuck to C++ is stretching it. ;)

C++ is whatever you want it to be.


err, no .. c++ is like fighting windmills .. they never back down and do what i want them to do .. now why would i do such a crazy thing?

pffft..you'll never get it anyway .. and i'll turn out be a smug weenie no matter what i say .. so it's up to you and only you - like it was up to me back when i was confronted and determined to "prove them wrong" 

this reminds me of this btw.: "True, only the creatively intelligent can prosper in the Lisp world."
from: [http://wiki.alu.org/Pascal_Costanza%27s_Road_To_Lisp](http://wiki.alu.org/Pascal_Costanza%27s_Road_To_Lisp) .. from a collection of writings found here: [http://wiki.alu.org/The_Road_to_Lisp_Survey](http://wiki.alu.org/The_Road_to_Lisp_Survey)

here; remove the FOR keyword from c++ .. then try to implement it using templates or whatever .. (note; it must be _clean_, _sane_ and work in all situations .. and the code must be beautiful and simple) .. see how the language isn't what you want it to be?

here i do this in lisp, in ..uh.. like 1 effective line of code or so?

```

(defmacro for ((var initial-value pred update-value) &body body)
  `(do ((,var ,initial-value ,update-value)) ((not ,pred))
    ,@body))

```

..now, this is just a silly example (written in 2.5 seconds, on the go, just now) .. heck, maybe you're able to pull this off in c++ using the macro preprocessor or whatever .. but just add a tiiiny bit more complexity and you'd be stuck 

.. i do these kinds of things _all day long_ in lisp without even _thinking_ about it .. yes, it is (or could be, in your case) that easy; it is natural and "safe" .. it's not a "hack" .. 

i add new constructs .. new keywords .. extend the language .. it's a programmable programming language .. if lisp lacked OOP support? .. no problem, i'd just do this:

```

(defmacro defclass (..)
  ..)

```

..then i'd have a new keyword DEFCLASS that i could use to define classes .. but lisp already has _excellent_ OOP support via CLOS, which is included in Common Lisp .. it is way way beyond anything found in C++

"I invented the term Object-Oriented, and I can tell you I did not have C++ in mind." - (Alan Kay)

it can be whatever i want, and c++ can never come close to this .. at .. all

edit: oh, and this is compiled to native optimized machine language btw. .. SBCL is known to generate machine code that runs faster than C in some cases

> **samjh]
If you want to be insane with C++, it will oblige without question! 
[/quote]

oh, if this was true my views would maybe be somewhat different .. but this isn't true and never will be, so never mind

[quote=samjh]
Frankly, I have little patience with it, 
[/quote]

this should ring a bell or two said:**
> 
but it is undoubtedly a very powerful language in the right hands, dangerous in the wrong hands.


power and danger don't go together because if it really was powerful it would be possible to implement a "safe layer" on "top of it" .. but it isn't powerful, so this isn't possible ..

you are stuck with something that always "leaks" -- you will always be patching the holes that show up over and over again from the bottom layers of your application/library-code to the top .. you can never fix something "at the bottom" and be done with it once and for all

power is _worthless_ if you _cannot_ bind it down, control it and bend it to your will .. c++ is like the atom bomb concept of "power" .. it's just a huge release of _crap_ as it unexpectedly blows up in your face over and over again without any way of fixing the "internal leak" (whatever it might be; these leaks show up in other languages all the time ofc., with "leaks" i mean "general programming problems", but these languages provide the power to fix the leak at the core!) once and for all

.. if you've had enough of my ranting then simply ignore me and i won't "bother you" (this is how some of you people work, ain't it?) any more ..

---

### Post by samjh on 2008-04-24
> **lnostdal said:**
> err, no .. c++ is like fighting windmills .. they never back down and do what i want them to do .. now why would i do such a crazy thing?Obviously C++ doesn't work for you, but it works for a lot of other people.

> ..you'll never get it anyway .. and i'll turn out be a smug weenie no matter what i say .. so it's up to you and only you - like it was up to me back when i was confronted and determined to "prove them wrong" Get what?

Who are "they"?

Confronted?

This is one of the strangest replies I have seen around here. :confused:

> here; remove the FOR keyword from c++ .. then try to implement it using templates or whatever .. (note; it must be _clean_, _sane_ and work in all situations .. and the code must be beautiful and simple) .. see how the language isn't what you want it to be?If you remove FOR from C++, then you no longer have C++.  It's something like C++ without FOR. ;)

Seriously you use the tools that are available.  C++ has FOR, so if you need FOR, you use it.  Why do something crazy like removing FOR from C++?

> power and danger don't go together because if it really was powerful it would be possible to implement a "safe layer" on "top of it" .. but it isn't powerful, so this isn't possible ..C++ is not a safe language, but some people can use it with relative safety.

Not everyone can fly a fighter jet, drive a top-fuel drag racer, etc.  They are not "safe", in fact they are quite dangerous.  But they are very powerful machines.

> you are stuck with something that always "leaks" -- you will always be patching the holes that show up over and over again from the bottom layers of your application/library-code to the top .. you can never fix something "at the bottom" and be done with it once and for allUnfortunately, this is true.  But it is true for any programming language if you use it badly, or are not mentally suited for that language.

Obviously C++ doesn't jive well with your way of thinking.  Nothing wrong with that.  Some people can handle a tool better than another.  Lisp is very good for you, so that's what you like, while C++ doesn't work for you at all, it seems.

As I said, I have little patience with C++.  But I won't put it down as something absolutely worthless as you imply.  It is far too presumptuous to think that the many C++ programmers in the world are all idiots or crazy because they like C++. ;)

---

### Post by LaRoza on 2008-04-24
Thread Split

Enjoy.

---

### Post by samjh on 2008-04-24
> **LaRoza said:**
> Thread Split

Enjoy.

That's like handing someone a stick of dynamite and some matches, then saying, "Enjoy!".

:p

---

### Post by LaRoza on 2008-04-24
> **samjh said:**
> That's like handing someone a stick of dynamite and some matches, then saying, "Enjoy!".

:p

Yeah? So? 

This thread is in the Holy Wars of Programming thread (link in sticky)

I just have on thing to say about C++ (it being my first language, I feel I have a right to say this):

[img]http://www.freesmileys.org/smileys/violent069.gif[/img]

---

### Post by lnostdal on 2008-04-24
> **samjh said:**
> Obviously C++ doesn't work for you, but it works for a lot of other people.

Get what? Who are "they"? Confronted?


*sigh* .. the smug lisp weenies of course! .. i was "a C++ weenie" at the time


> **samjh]
If you remove FOR from C++, then you no longer have C++.  It's something like C++ without FOR.  said:**
> 

uh, yes .. is this so hard to imagine?

lisp doesn't have FOR, but i've added it .. there .. now try this in C++ .. name it FOR2 if you want so you do not create a conflict


[quote=samjh]
Seriously you use the tools that are available.  C++ has FOR, so if you need FOR, you use it.  Why do something crazy like removing FOR from C++?


the point was of course to _add_ FOR .. but ok, add a FOR2 instead that is exactly like the FOR already found in c++

*sigh* ..whatever works for you .. maybe i cannot explain this to you .. or?


> **samjh]
Unfortunately, this is true.  But it is true for any programming language if you use it badly, 
[/quote]

actually, no .. c++ lacks "the power" (to use these tired old words again) to fix things once and for all even if you "used it _perfectly_"

[quote=samjh]
or are not mentally suited for that language.
[/quote]

i would not find this insulting at all if said to me .. i'd take it as a compliment!

..in the same way i'd take a statement like "me not being mentally suited for <insert-some-shitty-mindless-job>" as a compliment (think of the most mentally destructive and degrading type of task you can imagine)


[quote=samjh]
Obviously C++ doesn't jive well with your way of thinking.  Nothing wrong with that
[/quote]

sure

[quote=samjh]
 Some people can handle a tool better than another.  
[/quote]

ah-ah, wait .. this tool cannot do what this other tool can do .. at .. all .. no matter how skilled one is

..so it is in fact, not as much about how one handle to the tool as you seem to think it is..

again said:**
> 
 It is far too presumptuous to think that the many C++ programmers in the world are all idiots or crazy because they like C++. ;)

i never said this; they are just all wrong .. nothing wrong or idiotic or crazy about that

edit: hah, i told you i'd end up as a smug lisp weeny =)

---

### Post by samjh on 2008-04-24
> **lnostdl]i would not find this insulting at all if said to me .. i'd take it as a compliment![/quote]It should be neither a compliment or insult.  Some people find some things easier and better than what others find.  Fact of life, really.

[QUOTE=LaRoza said:**
> Yeah? So? 

This thread is in the Holy Wars of Programming thread (link in sticky)

I just have on thing to say about C++ (it being my first language, I feel I have a right to say this):

[img]http://www.freesmileys.org/smileys/violent069.gif[/img]

Sigh... I have now become a war-monger, on a side I do not wish to fight for (C++).  Time for a strategic withdrawal and declaration of neutrality now. ;)

:popcorn:

---

### Post by LaRoza on 2008-04-24
> **samjh said:**
> Sigh... I have now become a war-monger, on a side I do not wish to fight for (C++).  Time for a strategic withdrawal and declaration of neutrality now. ;)

:popcorn:

You could find a smiley that can take that one on, but that would be futile (all resistance is), as I have the ultimate warrior. [img]http://www.freesmileys.org/smileys/alien003.gif[/img]

C++ is a somewhat useful static typed OO language with some compatibility of C and has some of its features, but it is, IMO, a language for a niche. It is low level enough to make things difficult, and high level enough to make low level programming harder. Using C++ well usually means using as few of its features as possible (no arrays, pointers, etc) and using the STL, Boost or QT. I think, from tseliot's posts, C++ and QT go together very well, so maybe that is one of its stronger points.

---

### Post by samjh on 2008-04-24
My only experience with C++ was just for familiarisation, and to see whether it is a language I wished to learn more about.  I decided it was just too much trouble.  I prefer C over C++ purely for its simplicity and transparency, along with other languages that are as efficient with less pitfalls than C++.

There are safety-critical implementations of C++ with so many features removed that it is not much different from C.  And then you've got libraries like QT which purists would not even consider as C++.

It's a convoluted language.  At least for me.  But not for all people, as I mentioned earlier.

---

### Post by CaptainLinux94 on 2008-04-24
It sounds like you think C++ is horrible and that you want everyone else to think it's horrible.

Tell that to all the professionals who swear to it.  There's a reason why most professionals use it, it's the fastest, efficient code out there.

But if you're not a professional striving to communicate the most efficiently with hardware, it's pointless...

**So please,** no flaming.

---

### Post by LaRoza on 2008-04-24
> **CaptainLinux94 said:**
> 
Tell that to all the professionals who swear to it.  There's a reason why most professionals use it, it's the fastest, efficient code out there.

But if you're not a professional striving to communicate the most efficiently with hardware, it's pointless...


Professionals should be more concerned with using the most efficient tool, rather than swearing by any language.

---

### Post by lnostdal on 2008-04-24
> **CaptainLinux94 said:**
> It sounds like you think C++ is horrible and that you want everyone else to think it's horrible.


oh, i don't give a rats *** about what "everyone else" thinks .. i can think for myself you know

..so, do you have this; an opinion of your own?


> **CaptainLinux94 said:**
> 
Tell that to all the professionals who swear to it.


sure thing .. this is the internet; they can already read what i've said (edit: not that i'd recommend them or anyone doing it though, it is a dirty quick rant ..) .. and i'd tell it to anyone face to face any day if they asked me about these things

..are you one of these "professionals"?


> **CaptainLinux94 said:**
> 
There's a reason why most professionals use it, 


*beep* .. wrong


> **CaptainLinux94 said:**
> 
it's the fastest, efficient code out there.


nonsense


> **CaptainLinux94 said:**
> 
But if you're not a professional striving to communicate the most efficiently with hardware, it's pointless...


oh, i do this every day .. but i don't need c++ for that tho .. and i hate labels, so you can just call me Lars and drop the "professional" thing

---

### Post by Wybiral on 2008-04-24
> **CaptainLinux94 said:**
> But if you're not a professional striving to communicate the most efficiently with hardware, it's pointless...

C is a much more logical language for that kind of low-level interfacing.

> **CaptainLinux94 said:**
> **So please,** no flaming.

You can't make claims like this and expect not to be flamed :)

---

### Post by Can+~ on 2008-04-24
> **CaptainLinux94 said:**
> ... it's the fastest, efficient code out there ...

](*,)

---

### Post by LaRoza on 2008-04-24
> **Wybiral said:**
> You can't make claims like this and expect not to be flamed :)

[img]http://www.mysmiley.net/imgs/smile/sign/sign0083.gif[/img]

---

### Post by daniel of sarnia on 2008-04-25
It's obvious C++ is not good for everything, it's likely not good for most things. What I just don't understand is how people can make such broad statements about how much it sucks when their are clearly large projects leveraging it quite well, like QT. If it's not right for you and or your project don't use it. Seriously, why so much hate, just use something else.

I mostly program in python btw.

---

### Post by lnostdal on 2008-04-25
yes, you're right .. lisp is the jazz and classical music of programming languages, dwithney67 .. no one listens to it

..know what sells? britney spears .. go figure

..and, yeah .. no one "gets jazz"

i'm a bit tired .. read this [http://www.paulgraham.com/iflisp.html](http://www.paulgraham.com/iflisp.html) .. mebbe i'll come back and rant more later .. x) .. but i'm done venting and ranting for now; i need to do some work - in lisp ofc.

---

### Post by LaRoza on 2008-04-25
> **lnostdal said:**
> i'm a bit tired .. read this [http://www.paulgraham.com/iflisp.html](http://www.paulgraham.com/iflisp.html) .. mebbe i'll come back and rant more later .. x) .. but i'm done venting and ranting for now; i need to do some work - in lisp ofc.

This is a very good article on Lisp: [http://www.defmacro.org/ramblings/lisp.html](http://www.defmacro.org/ramblings/lisp.html)

(Thanks to aks44)

---

### Post by tseliot on 2008-04-25
> **lnostdal said:**
> Well, then we disagree. Flame if you want; I do not care. Heck -- I won't even respond.
I'm not saying that you can't write horrible code in C++. If you use QT4 to replace the standard library C++ is a lot saner (but of course you're still do horrible things with it).

> **lnostdal said:**
> edit: maybe you wouldn't care to comment if i said this "vs." a language like, say, brainfuck .. think about it
Sorry but if you say that a language is "evil vile crap" when a user is asking for help then I call this flame-bait.

I can talk only about the languages of which I have experience. I've never tried brainfuck.

---

### Post by LaRoza on 2008-04-25
> **tseliot said:**
> I've never tried brainfuck.

You're better off.

---

### Post by Jessehk on 2008-04-25
> **tseliot said:**
> 
Sorry but if you say that a language is "evil vile crap" when a user is asking for help then I call this flame-bait.


Unfortunately, that seems to be the trend in this particular sub-forum. There is a mob-mentality surrounding what people feel are "correct" languages or ideas to have and those that argue otherwise or encourage discussion are quickly (and with various means of appeal to force) silenced. Whether others notice it or not, I **have** noticed it and find it very off-putting.

---

### Post by Zugzwang on 2008-04-25
> **lnostdal said:**
> err, no .. c++ is like fighting windmills .. they never back down and do what i want them to do .. now why would i do such a crazy thing?

So lnostdal, you are claiming that nobody can write C++ programs in a sane manner. There are so many people who do. Also the language has definitely its place in today's world. The concept of C++ mainly is: Use OOP but prefer speed against coding time/whatever at all choices. And this is good if you really have a problem you need speed & OOP at the same time. If the languages gets some pitfalls this way, this is up to the programmer. We're not talking about libraries here, just of plain C++. For example, consider the following applications:
[LIST=1]
[*]Scientific applications
[*]Games with some "artificially intelligence"
[/LIST]
In the first case, there are a lot of cases in which OOP comes into appearance in the computationally expensive "naturally". I myself recently wrote one and I'm glad that it only takes 3 days on a modern computer for it to run a single time. And no, the algorithm used is the best so far, if I had any better, this would be quite a remarkable theoretical result. And the implementation isn't too bad and well-profiled either.

In the second case, OOP also comes into appearance naturally. However the "artificial intelligence" of the computer-controlled entities can be quite complex to work well. And if they do, they often consume a lot of computation power. So we have OOP in the computationally expensive part.

Now this is point at which you might note that C++ is often slower because programmers use vectors, lists, whatever. Well, it's up to the programmer, that's not the fault of the language. 

All I wanted to say using this is that it's certainly untrue that it's impossible to program using C++ in a "sane" manner.

---

### Post by pedro_orange on 2008-04-25
> **LaRoza said:**
> Professionals should be more concerned with using the most efficient tool, rather than swearing by any language.

Time isn't always the biggest factor. I have a saying "It takes as long as it takes"
It's the Project Manager's job to watch the clock and count the beans. 
It's my job to write working code for the situation/scenario that fulfils the requirements of the customer. They don't care what it's written in. They want it to work. 

lnostdal:
[http://portal.acm.org/citation.cfm?id=43908.43909](http://portal.acm.org/citation.cfm?id=43908.43909)

Bon appetite.

---

### Post by Alasdair on 2008-04-25
C++'s idea of sane is often rather insane (see [here]("http://yosefk.com/c++fqa/index.html")). Anyway both those applications you mentioned, why not use lisp? It can be just as fast as C++ and it has OOP (CLOS is much more powerful than C++'s object system). Using C++ for speed is pretty much textbook premature optimization, deciding that you absolutely *must* have speed before you even start writing any code! Chances are your program will spend 90% of its time in 10% of your code, so why write the whole thing in C++ when you could write 90% in a clean high level language like python (or lisp, ruby...) and then re-write the performace critical 10% in C? Your program will be just as fast and it'll take vastly less time too write! C++ sits uncomfortably on the boundary between high and low level - it doesn't really know where it wants to be. It's in the unfortunate position where it tries hard to abstract away details, but it's low level nature means you *need* to understand it in detail, including the clunky abstrations it builds - that is why C++ is insane, in my opinion.

I only wish that when I started to learn programming people had told me to avoid C++; it almost killed any interest I had in programming. They told me that I needed C++ if I wanted to be a 'real' programmer, that it was needed if you want to do 'real' work. That's just not true.

---

### Post by LaRoza on 2008-04-25
> **pedro_orange said:**
> Time isn't always the biggest factor. I have a saying "It takes as long as it takes"
It's the Project Manager's job to watch the clock and count the beans. 
It's my job to write working code for the situation/scenario that fulfils the requirements of the customer. They don't care what it's written in. They want it to work. 


No, it isn't. I have zero time restrictions on my projects. I have the rest of my life to finish my system restore program (from the looks of it, it will take that long), but I see no reason to make things hard on myself.

"It's the Project Manager's job...". In my projects, I am the Project Manager, the Programmer, and the Client. I try to use the tools that allow me to focus on the problem.

---

### Post by mssever on 2008-04-25
> **pedro_orange said:**
> [http://portal.acm.org/citation.cfm?id=43908.43909](http://portal.acm.org/citation.cfm?id=43908.43909)

Care to summarize this? I can't access it due to a login requirement, and BugMeNot doesn't seem to know how to log in to that site.

---

### Post by lnostdal on 2008-04-25
> **Zugzwang said:**
> 
[quote=lnostdal]
err, no .. c++ is like fighting windmills .. they never back down and do what i want them to do .. now why would i do such a crazy thing?

So lnostdal, you are claiming that nobody can write C++ programs in a sane manner. There are so many people who do.
[/quote]

..i hope you did get the context of that response..

but, no, i use a lot of software written in c++ .. i'm typing this into a box that is "generated by" (on my end) an application written in c++

..but you must understand that this does not dispute my point or opinion of the language in any way..


> **Zugzwang said:**
> 
...
All I wanted to say using this is that it's certainly untrue that it's impossible to program using C++ in a "sane" manner.


yes, you restrict yourself to basically the C subset of C++ with some syntactic sugar for the OOP stuff to look nicer .. possibly some other things also; but in all only a significantly limited subset of the language

..does this make C++ "sane" or is it simply its user that is "sane"? 

oh, and check out what's being added to C++0x .. the language as a whole is not getting simpler, smaller or cleaner at its core

..but why is this so? is it not possible to have all these cool new(?) language features and still "maintain sanity"? .. yes, it is - but not in c++ .. and i, well, _need_ these cool features + simplicity/sanity/etc.! 

so no, i cannot have a high-level language where i must restrict myself to a subset that basically is C or something in-between C and "full C++" .. i'd rather just use C for the performance critical parts, and a "real" high-level language for the rest then

---

### Post by lnostdal on 2008-04-25
> **tseliot said:**
> Sorry but if you say that a language is "evil vile crap" when a user is asking for help then I call this flame-bait.

yeah, you're right

to be honest it was just a silly emotional kind of outburst added as an edit to a response that in fact did resolve the OPs problem 

.. to get an idea of what state i was in at the time; i did not even care to notice _which post_ (there where multiple c++ questions/threads at the time) to _which OP_ i edited .. heh .. it probably did not make much sense to the OP - so good thing the thread was split up the way it did .. (thank you for that LaRoza)

---

### Post by lnostdal on 2008-04-25
> **pedro_orange said:**
> 
lnostdal:
[http://portal.acm.org/citation.cfm?id=43908.43909](http://portal.acm.org/citation.cfm?id=43908.43909)

Bon appetite.

i cannot access this but based on the abstract text i can make a rough guess at its contents, and i can provide you with multiple sources that show an opposite result

.. if you insist i can dig these up for you ..

---

### Post by Wybiral on 2008-04-25
> **Jessehk said:**
> Unfortunately, that seems to be the trend in this particular sub-forum. There is a mob-mentality surrounding what people feel are "correct" languages or ideas to have and those that argue otherwise or encourage discussion are quickly (and with various means of appeal to force) silenced. Whether others notice it or not, I **have** noticed it and find it very off-putting.

Silenced? Like... By the men in black?

Maybe you feel like there is a mob because the majority just doesn't share your opinion? That sounds more likely than the men in black to me :)

---

### Post by LaRoza on 2008-04-25
> **Wybiral said:**
> Silenced? Like... By the men in black?

Maybe you feel like there is a mob because the majority just doesn't share your opinion? That sounds more likely than the men in black to me :)

Actually, it is true. I have been pruning the Java programming threads away.

.NET was done a while ago, and I am about to start on C++...

I can't do it all at once; that would arouse too much attention. Resistance is futile.

---

### Post by Can+~ on 2008-04-25
> **LaRoza said:**
> Actually, it is true. I have been pruning the Java programming threads away.

.NET was done a while ago, and I am about to start on C++...

I can't do it all at once; that would arouse too much attention. Resistance is futile.

Man, that's a load of [FONT="Courier New"]true information that can't be questioned, I salute the Ubuntuforums flag and embrace python[/FONT]

Hey, I didn't write th.. *user Can +~ is not part of ubuntuforums anymore*

-Big brother.

---

### Post by LaRoza on 2008-04-25
> **Can+~ said:**
> Man, that's a load of [FONT="Courier New"]true information that can't be questioned, I salute the Ubuntuforums flag and embrace python[/FONT]

Hey, I didn't write th.. *user Can +~ is not part of ubuntuforums anymore*

-Big brother.

[img]http://www.mysmiley.net/imgs/smile/sign/sign0024.gif[/img]

---

### Post by Can+~ on 2008-04-25
> **LaRoza said:**
> [img]http://www.mysmiley.net/imgs/smile/sign/sign0024.gif[/img]

[IMG]http://img.photobucket.com/albums/v517/CanXp/pyong/raposa-ani.gif[/IMG]

Boy, the forum smilies, do suck.

---

### Post by LaRoza on 2008-04-25
> **Can+~ said:**
> [IMG]http://img.photobucket.com/albums/v517/CanXp/pyong/raposa-ani.gif[/IMG]

Boy, the forum smilies, do suck.

[img]http://www.freesmileys.org/smileys/alien003.gif[/img]

[img]http://www.mysmiley.net/imgs/smile/sign/sign0106.gif[/img]

---

### Post by CaptainLinux94 on 2008-04-26
> **lnostdal said:**
> oh, i don't give a rats *** about what "everyone else" thinks .. i can think for myself you know

..so, do you have this; an opinion of your own?




sure thing .. this is the internet; they can already read what i've said (edit: not that i'd recommend them or anyone doing it though, it is a dirty quick rant ..) .. and i'd tell it to anyone face to face any day if they asked me about these things

..are you one of these "professionals"?




*beep* .. wrong




nonsense




oh, i do this every day .. but i don't need c++ for that tho .. and i hate labels, so you can just call me Lars and drop the "professional" thing

Hell no man,

I ain't no professional.

From what I've experienced with C++ and gathered from others in multiple forums across the internet C++ is aimed towards professionals.

I hate C++, and the closest to that I'll use is C (which I actually like).  There's people I hate in the world, but you don't see me complaining over the internet about them.  I confront the problem.  I think you should confront this issue maturely by choosing not to use C++ and getting on with your life.  Sheesh.

---

### Post by Wybiral on 2008-04-26
> **CaptainLinux94 said:**
> I hate C++, and the closest to that I'll use is C (which I actually like).  There's people I hate in the world, but you don't see me complaining over the internet about them.  I confront the problem.  I think you should confront this issue maturely by choosing not to use C++ and getting on with your life.  Sheesh.

Are you complaining on the internet because lnostdal is complaining on the internet? Wasting your own life to tell someone else to get on with their life? ORLY?

---

### Post by CaptainLinux94 on 2008-04-26
> **Wybiral said:**
> Are you complaining on the internet because lnostdal is complaining on the internet? Wasting your own life to tell someone else to get on with their life? ORLY?

](*,)
This is going no where.
Arguing on the internet is beneath me.
I refuse to post any longer in this thread.

---

### Post by dempl_dempl on 2008-04-26
First of all, I would like to say this is not some standard C++ vs. Java vs. Python flaming. I don't go too philosophical. It shows some features of C++ which many people didn't know there are.

I'm perfectly aware there are some problems which can be solved with Java , Python and C# a lot easier than in C++. 
I simply want to point out that you should not throw away C++ .
C++ is like math. You have to know it well if you want to be a good programmer. It doesn't matter if you work with it or not. 
There are many solutions/patterns/things which simply don't exist in other languages and you should know them in order to broad your mind. To see the ways problems can be solved. 

I've noticed  that most of Java ,Python and C# programmers often use some arguments against C++ , which simply are untrue. 
I believe they don't do that on purpose, that they simply don't know some things about C++ .
 
I've put a small list of those arguments here.


Let's start with some standard anti-C++ arguments :

** C++ lack of good type safety ** - Simply untrue. C++ is not C .


**No garbage collection** - **false;**

C++ has something even better. It's called **smart pointers**. C# , Java and Python don't have that. With smart pointers you have all the safety of Garbage collection, and extra control, which you don't have with any of those three. Extra control also provides extra speed over GC . 

**With C++ you don't have Reflection stuff **: Sorry - simply wrong.

And I don't mean RTTI, I'm talking about real stuff :) .

C++ is kinda open language. If there isn't something, we can put it there. Reflection is one of those things. 
Hence, C++ can't lack of features. 

**No foreach keyword** - nope, false again :) , same thing as with previous argument. 

**C++ does not have policy classes** - wait, Java , Python and C# don't have that. C++ has it :P . 

**Multiple inheritance is useless and only makes the code harder to read, use whatever** - Check the google for **policy classes **and think again.


**Inconsistency** - Java, Python and C# have them too.

** Too hard to use ** - Relative to observer. I find that Java , C# , and Python over-simplified, and that has a major flaw that some problems simply cannot be solved. Using a particular language becomes very hard when you can't solve a problem with it :D . 




Now, the following are the things which Java, Python and C# will never have. Most of Java, C# and Python  programmers have never even heard for the half of the stuff in the list.

- Tuples
- Type-lists
- Functor-containers
- Template Meta programming
- Multiple inheritance
- Operator overloading - so elegant.
- Generic Singleton
- Curiously recurring template pattern - very nice toy :)
- Good old stack usage - you know, the speed. 
- Destructors - used with smart pointers, can make code so nicer . **Destrutcs** :) the need for try-finally statements.
- Many of design patterns are very hard or impossible to produce in other languages. 


I believe that C# , Java and Python help in producing more and more programming technicians , while good C++ helps producing engineers. Someone who knows only C++, know a lot more about programming than someone knowing only Java or Python. 
How to explain what is stack , or pointer to someone using Python? They'll need that sometime. 

Computer Scientists, are of course, above all of that , and exception to any rule I've put here.

Again, we're all aware of C++ flaws, but this is pro-C++ thread :D , and there are a lot of anti-C++ sites there   .


Cheers!

Good reading / Usefull libs:

[Modern C++ design - generic programming and design patterns aplied]("http://alas.matf.bg.ac.yu/~mr06184/stosha.net/doc/modern-c++.tar.gz")
[Reflex - C++ reflection library]("http://seal-reflex.web.cern.ch/seal-reflex/")
[Loki - mutli-purpose generic library]("http://loki-lib.sourceforge.net/")
[Boost - no need for introduction]("http://boost.org/")

---

### Post by LaRoza on 2008-04-26
Merged. This thread is for all the C++ debates.

---

### Post by dempl_dempl on 2008-04-26
> **LaRoza said:**
> Merged. This thread is for all the C++ debates.

Ok. Tnx. Should not post it there anyways...

---

### Post by Can+~ on 2008-04-26
> - Tuples

a = (1, 2, 3)

Link: [Data Structures: Tuple and Sequences](http://docs.python.org/tut/node7.html#SECTION007300000000000000000)

> - Multiple inheritance

class a
class b
class c

class d(a, b, c)

...

Link: [Multiple Inheritance](http://docs.python.org/tut/node11.html#SECTION0011510000000000000000)

> - Operator overloading - so elegant.

Link: [Python: Operator Overloading]("http://docs.python.org/ref/numeric-types.html")
(I selected the numeric types since those are the most familiar, there are for attributes, constructor, etc).

> - Good old stack usage - you know, the speed. 

a = [1, 2, 3]
a.append(4)
a.pop()

Link: [Data Structures: Using Lists as Stacks](http://docs.python.org/tut/node7.html#SECTION007110000000000000000)

> - Destructors - used with smart pointers, can make code so nicer

del Variable

Can be overridden with __del__ inside a class.

Link: [del statement](http://docs.python.org/ref/del.html)

> Good reading / Usefull libs:

Modern C++ design - generic programming and design patterns aplied
Reflex - C++ reflection library
Loki - mutli-purpose generic library
Boost - no need for introduction

Useful Libs, all the things that are builtin:
[Python: Index of Modules](http://pydoc.org/2.5.1/)

Before posting things that "Other languages don't have", try reading what other languages have:
[http://docs.python.org/](http://docs.python.org/)

---

### Post by dempl_dempl on 2008-04-26
> **Can+~ said:**
> a = (1, 2, 3)

Link: [Data Structures: Tuple and Sequences](http://docs.python.org/tut/node7.html#SECTION007300000000000000000)



class a
class b
class c

class d(a, b, c)

...

Link: [Multiple Inheritance](http://docs.python.org/tut/node11.html#SECTION0011510000000000000000)



Link: [Python: Operator Overloading]("http://docs.python.org/ref/numeric-types.html")
(I selected the numeric types since those are the most familiar, there are for attributes, constructor, etc).



a = [1, 2, 3]
a.push(4)
a.pop()

Link: [Data Structures: Using Lists as Stacks](http://docs.python.org/tut/node7.html#SECTION007110000000000000000)



del Variable

Can be overridden with __del__ inside a class.

Link: [del statement](http://docs.python.org/ref/del.html)



Useful Libs, all the things that are builtin:
[Python: Index of Modules](http://pydoc.org/2.5.1/)

That's a very bad excuse for multiple inheritance. If that was C++'s inheritance, it wouldn't be much useful

This is a useful multiple inheritance:

template < typename PolicyA,typename PolicyB>
class MyClass: public PolicyA, PolicyB
{
};


Stack - not that stack. The program's stack :P

Cheers!

---

### Post by Wybiral on 2008-04-26
> **dempl_dempl said:**
>  ... 

lol, thank you :) This was the best example of a "blub programmer" I have ever seen. Most of the things you listed that C++ has, the other languages do, in fact, also have. Some of the things you listed aren't in the other languages because they aren't needed (C++ creates new problems that need to be solved, Python doesn't have smart pointers because it doesn't need them... That is all taken care of for you).

Name one feature of C++ that Python doesn't have?
One C++ feature that Lisp doesn't have?
Java? C#?

Have you even learned any other languages?

---

### Post by Wybiral on 2008-04-26
> **dempl_dempl said:**
> That's a very bad excuse for multiple inheritance. If that was C++'s inheritance, it wouldn't be much useful

This is a useful multiple inheritance:

template < typename PolicyA,typename PolicyB>
class MyClass: public PolicyA, PolicyB
{
};


Stack - not that stack. The program's stack :P

Cheers!

Care to explain why?

---

### Post by dempl_dempl on 2008-04-26
> **Wybiral said:**
> lol, thank you :) This was the best example of a "blub programmer" I have ever seen. Most of the things you listed that C++ has, the other languages do, in fact, also have. Some of the things you listed aren't in the other languages because they aren't needed (C++ creates new problems that need to be solved, Python doesn't have smart pointers because it doesn't need them... That is all taken care of for you).

Name one feature of C++ that Python doesn't have?
One C++ feature that Lisp doesn't have?
Java? C#?Goodbye. 

Have you even learned any other languages?

All of the other languages have SOME of the features.
C++ has ALL of them.

NONE of them have POLICY CLASSES.
NONE of them has TEMPLATE meta-programming ( note the word - template )

You CAN CHOOSE between "bald" and smart pointers in Python, right? Buhahahahaha... you're a blub :P


"Blub" ? Heh.. I like this thread.. I'll come here whenever I have a bad day :D


Cheers!

---

### Post by CptPicard on 2008-04-26
And Just C has RAW POINTERS!!11 Rawwwrrr..

---

### Post by dempl_dempl on 2008-04-26
> **CptPicard said:**
> And Just C has RAW POINTERS!!11 Rawwwrrr..


Where was this thread all my life? I'll definetley come ack whenever I have a bad day :D

---

### Post by Wybiral on 2008-04-26
> **dempl_dempl said:**
> You CAN CHOOSE between "bald" and smart pointers in Python, right? Buhahahahaha... you're a blub :P

... OMG ... You're right. In all my high-level smugness I never realize how inferior Python and Lisp really are. I mean... No pointers? How can I write any algorithms without pointers?!?! I don't even know what a pointer is...


lmao :)

Seriously though. Yes, Python (and Lisp, for that matter) do have pointers. For Python it's via the "ctypes" module. But you already knew that, right? Because you learned Python so well before learning C++, right?

---

### Post by dempl_dempl on 2008-04-26
> **Wybiral said:**
> ... OMG ... You're right. In all my high-level smugness I never realize how inferior Python and Lisp really are. I mean... No pointers? How can I write any algorithms without pointers?!?! I don't even know what a pointer is...


lmao :)

Seriously though. Yes, Python (and Lisp, for that matter) do have pointers. For Python it's via the "ctypes" module. But you already knew that, right? Because you learned Python so well before learning C++, right?

Ha ha .. still not the same :) .

I also believe you can have the five smart_pointer types as in C++ right?
 

I didn't wrote neither of this languages... and everybody wants to be the critics these days... And I don't even believe those folks who wrote any of them fight as much as we do...

Anyway.. I feel a lot better now... thanks guys.. you made my day slightly better :D .


Cheers!

---

### Post by gsmanners on 2008-04-26
:popcorn:

Never thought I'd see Python accused of lacking tuples. This thread really delivers.

---

### Post by LaRoza on 2008-04-26
> **gsmanners said:**
> 
Never thought I'd see Python accused of lacking tuples. This thread really delivers.

Yep. It was moved here to die actually.

---

### Post by Can+~ on 2008-04-26
> **dempl_dempl said:**
> That's a very bad excuse for multiple inheritance. If that was C++'s inheritance, it wouldn't be much useful

This is a useful multiple inheritance:

template < typename PolicyA,typename PolicyB>
class MyClass: public PolicyA, PolicyB
{
};

I still don't get why is supposedly better to do it on C++.

Programming languages are just like tools, there's tools for each situation, you can't say that your beloved C++ is the only one because it has a crapload of things. Python also has loads of things that C++ lack, just check the library of modules I posted before to get started.

So please, before you continue your defence, try other languages first.

And what's about that "Anyway.. I feel a lot better now... thanks guys.. you made my day slightly better"? Is somehow like "haha I like seeing you discuss". Really? You really need to start discussions and feel superior on internet to make your life better? You're... just wrong, trapped inside your own mentalism that c++ is the ultimate tool, when, no, other languages have a lot of stuff, there's a lot to learn.

... too bold?

---

### Post by Wybiral on 2008-04-26
> **dempl_dempl said:**
> Ha ha .. still not the same :) .

I also believe you can have the five smart_pointer types as in C++ right?
 

I didn't wrote neither of this languages... and everybody wants to be the critics these days... And I don't even believe those folks who wrote any of them fight as much as we do...

Anyway.. I feel a lot better now... thanks guys.. you made my day slightly better :D .


Cheers!

Not the same? I can use ctypes pointers to interface with _actual_ C functions :) If those aren't "C-style" pointers, what are?

Why does Python need five types of smart pointers? What's the benefit.

You do know that pointers are really just indices into a big array, right? Just a simple index into memory... An integer. Nothing that a normal array can't do. No magic... No need for them. Think about it, you'll get it one day.

---

### Post by mssever on 2008-04-27
> **dempl_dempl said:**
> NONE of them have POLICY CLASSES.
Well, Ruby has mixins which can easily accomplish the same thing. (Note that Ruby doesn't use multiple inheritance; mixins remove the need for multiple inheritance.) However, if you're using a sufficiently flexible language, policy classes no longer seem very beneficial.

And there's no need for templates in Ruby or Python. Why use templates when you can use duck typing--something C++ doesn't support?

---

### Post by Wybiral on 2008-04-27
> **mssever said:**
> And there's no need for templates in Ruby or Python. Why use templates when you can use duck typing--something C++ doesn't support?

That's a concept you can't explain to someone who doesn't know anything other than C++ :)

---

### Post by LaRoza on 2008-04-27
> **Wybiral said:**
> That's a concept you can't explain to someone who doesn't know anything other than C++

You don't know what you are talking about.

Templates are a great way to allow the same code to use more than one type. 

n00b!

---

### Post by pedro_orange on 2008-04-28
> **LaRoza said:**
> No, it isn't. I have zero time restrictions on my projects. I have the rest of my life to finish my system restore program (from the looks of it, it will take that long), but I see no reason to make things hard on myself.

"It's the Project Manager's job...". In my projects, I am the Project Manager, the Programmer, and the Client. I try to use the tools that allow me to focus on the problem.

That would be nice.
An ideal world some might say.
Well when you're working in the industry - all anyone (apart from other programmers) cares about what you're doing is if it is to spec and to budget. 
You can't quote someone X man-days to do a project and deliver it in X + 5 days. Thats over budget & we may have made a loss.
Every hour of my day must be booked towards a project, or support. If I don't book against chargable contracts, and the company starts losing money - They look to the ones booking to unchargeable contracts and axe them first.
It's a dog eat dog world.

---

### Post by LaRoza on 2008-04-28
> **pedro_orange said:**
> That would be nice.
An ideal world some might say.

Well when you're working in the industry - all anyone (apart from other programmers) cares about what you're doing is if it is to spec and to budget. 

You can't quote someone X man-days to do a project and deliver it in X + 5 days. Thats over budget & we may have made a loss.

It's a dog eat dog world.

A few issues with this:

[list]
[*] I am not in the industry, I am a hobbyist (downside: no money)
[*] Yes you can quote X man-days and deliver X + 5 days. MS does it by years! Look at longhorn, originally supposed to be out in 2003. It was released in 2007 with all the features missing! Late releases are typical and standard for corporate software production.
[*] I am not a dog, I am the Borg. I am also a vegan. 
[/list]

---

### Post by curvedinfinity on 2008-11-10
I don't know what all the rucus is about with C++. Especially concerning the idea that C is better. C++ is C, just with more features added -- you don't have to use any of the extra features. Hell, I don't use almost all of them, but I at least like having the option.

And about the "danger" of C/C++ -- I've never really understood that idea. There is a concequence to bad planning for all languages.

"Safe" languages are better because their results are more portable, but using one specifically for its safety is just using it as a crutch for bad programming practices. Good programming practices take all of the danger out of C++.

---

### Post by Bichromat on 2008-11-10
Bring out your dead! Bring out your dead! :)

---

### Post by nvteighen on 2008-11-10
> **curvedinfinity said:**
> I don't know what all the rucus is about with C++. Especially concerning the idea that C is better. C++ is C, just with more features added -- you don't have to use any of the extra features. Hell, I don't use almost all of them, but I at least like having the option.

No, C++ is not "C + features". It's a language with C-like syntax, but completely different semantics, a different programming style (what's "good practice" in C is not necessarily in C++ and viceversa), etc. Yes, C++ is backwards compatible with C, but that's intended for better interface with C programs, not for allowing you to do "C-like + some C++ stuff" code.

> And about the "danger" of C/C++ -- I've never really understood that idea. There is a concequence to bad planning for all languages.

"Safe" languages are better because their results are more portable, but using one specifically for its safety is just using it as a crutch for bad programming practices. Good programming practices take all of the danger out of C++.

C and C++ nowadays are rather "unsafe" than "dangerous"... but keep in mind that a C or C++ program in MS-DOS could harm the system very easily.

But these are languages, specially C, that are designed to gain a lot of control over the computer... by making almost everything to be controlled by hand. That's great for some stuff, but it gives you a big duty to deal with. That's why a C or C++ app is much likely to have a serious security hole than a Java one... (maybe the JRE may have a hole, but that's not your fault)...

---

### Post by jimi_hendrix on 2008-11-10
> **LaRoza said:**
> 
[LIST]
[*] I am not a dog, I am the Borg. I am also a vegan.
[/LIST]


what ever happened to your borg queen avatar...felt like something different?

anyway...i really see why C++ is so bad anyway...probably because i havnt used it enough, and pointers are a little confusing...but its not like im having my toenail ripped off, basted in butter, deep fried, and fed to me

---

### Post by samjh on 2008-11-10
Must... resist... urge... to...

Oh well.

[IMG]http://i50.photobucket.com/albums/f327/cesarhaha/forum%20replies/ThreadNecromancer.jpg[/IMG]

:p

---

### Post by jimi_hendrix on 2008-11-10
rofl

---

### Post by LaRoza on 2008-11-10
> **jimi_hendrix said:**
> what ever happened to your borg queen avatar...felt like something different?

That was gone a while ago ;) I have no avatar or custom title at the moment. I've forsaken everything but tech support on this forum.

> 
anyway...i really see why C++ is so bad anyway...probably because i havnt used it enough, and pointers are a little confusing...but its not like im having my toenail ripped off, basted in butter, deep fried, and fed to me

Pointers are nothing.

---

### Post by jimi_hendrix on 2008-11-10
> **LaRoza said:**
> That was gone a while ago ;) I have no avatar or custom title at the moment. I've forsaken everything but tech support on this forum.
why no avatar?  the borg thing was slightly intimidating...> 
Pointers are nothing.i recently mastered them (i think)

---

### Post by pavel989 on 2008-11-10
after about page 5, i got bored and came to this conclusion:

ABSOLUTLY NO ONE, !!!NO ONE!!!, CAN PROVE A LANGUAGE'S SUPERIORITY.

personally, i hate C++. its so ugly, and there are a lot of features that i dont understand uses of. Granted, I am a newb (or at least i think), but dammit, it can do just about anything.

I've fiddled with VB, C#, python, ruby, small amount of Java (very small, might come back to it...), BASIC, and C++.

I am not good at any of them, because I was using them only to learn, to find what language is ultimate. and to me they're all the same, except their usage;

im not using C++ for a web app, and im not using ruby for a game, but 5+5 works in either one of them.

But in my travels, the one question has always been speed. If you're programming, you can probably learn to get past syntax (I did...)


so for someone like me, it comes down to this:
what does lisp or C++ have over the other, that would make it so much better?
- so far, ive found that anything can be implemented in either, so it wouldnt matter which you use, so long as u can understand it.

---

### Post by pavel989 on 2008-11-11
bah

---

### Post by LaRoza on 2008-11-11
> **pavel989 said:**
> after about page 5, i got bored and came to this conclusion:

ABSOLUTLY NO ONE, !!!NO ONE!!!, CAN PROVE A LANGUAGE'S SUPERIORITY.
And yet, we can prove a language is inferior, when given the context.

---

### Post by CptPicard on 2008-11-11
> **pavel989 said:**
> 
ABSOLUTLY NO ONE, !!!NO ONE!!!, CAN PROVE A LANGUAGE'S SUPERIORITY.

In general terms, we can easily discuss a language's suitability to general problem-solving. The fact that people have been creating new languages that are progressively better (starting from wiring up their CPUs physically), shows that there indeed is some kind of continuum.

> 
personally, i hate C++. its so ugly, and there are a lot of features that i dont understand uses of. Granted, I am a newb (or at least i think), but dammit, it can do just about anything.

Likewise. It's ugly and has lots of features you have to "manage" and "know how to use". The general retort by (very skilled C++ hackers) that thing X is doable if <pages of explanation> is proof positive that C++ is relatively complex.

On the other hand I never felt like it really gave me anything substantial over many other languages. It can't "do just about anything" when I compare it to a lot of high-level languages. I miss my closures in particular...

> 
I am not good at any of them, because I was using them only to learn, to find what language is ultimate. and to me they're all the same, except their usage;

You've been fiddling mostly with languages of the same family... Ruby has potential to enlighten you of the real differences :)

> 
But in my travels, the one question has always been speed. If you're programming, you can probably learn to get past syntax (I did...)

So you're in the crowd who claims that all language differences are superficial and are just ways to write down syntax differently? As I said, with Java/C#/C++ you may come to such a conclusion, and there you would be mostly right (with the distinction that C++ is needlessly "hard").

Otherwise the claim is harder to defend... and because in more non-trivial cases such as using tail-recursion in Scheme to express loops, for example, of course the underlying computational concept is the same, but when you know how to use it in Scheme you also have learned an important lesson about computations in general -- it's not just typing up the loop differently (and if you claimed that, you don't understand the concept).


> 
what does lisp or C++ have over the other, that would make it so much better?

Lisp most importantly has a very minimal, homoinonic syntax expressed in the language's fundamental data structure -- list made up of cons pairs -- that allows for arbitrary code manipulation and usage of arbitrary native data structures as code (as long as they do represent valid code), runtime compilation, runtime evaluation (scripting), a REPL, a multiple-dispatch functional-object-system, closures, continuations (either natively in Scheme or through code transformer in CL), strong support for functional programming but also allowing for imperative-style parts where you want them...

C++ has nothing of these. Instead it has a rigid static type system that is mostly used to build OO architectures which require a lot of design just to get them off the ground :)


> 
- so far, ive found that anything can be implemented in either, so it wouldnt matter which you use, so long as u can understand it.

Only in theory... in practice, it's nicer to actually have languages that come half way in the human programmer's direction.

---

### Post by Sockerdrickan on 2008-11-11
I love c++ but I don't like GCC's way of telling me
```
/usr/include/c++/4.3/istream:123: note: candidates are: std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(std::basic_istream<_CharT, _Traits>& (*)(std::basic_istream<_CharT, _Traits>&)) [with _CharT = char, _Traits = std::char_traits<char>] <near match>
/usr/include/c++/4.3/istream:127: note:                 std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(std::basic_ios<_CharT, _Traits>& (*)(std::basic_ios<_CharT, _Traits>&)) [with _CharT = char, _Traits = std::char_traits<char>] <near match>
/usr/include/c++/4.3/istream:134: note:                 std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(std::ios_base& (*)(std::ios_base&)) [with _CharT = char, _Traits = std::char_traits<char>] <near match>
/usr/include/c++/4.3/istream:242: note:                 std::basic_istream<_CharT, _Traits>& std::basic_istream<_CharT, _Traits>::operator>>(std::basic_streambuf<_CharT, _Traits>*) [with _CharT = char, _Traits = std::char_traits<char>] <near match>

```

---

### Post by Kilon on 2008-11-11
You are not a real programmer until you master Assembly. :lolflag:

My problem was not to like C++, actually I do, however I did not like the lbraries for C++. And that is I believe something we do not take into account. For example , I loved C++ and I used for a few MSDOS programms but when I  made the jump to WINDOWS programming and I saw MFC I said deinetely no. Specially designing  GUI has a huge pain , alot of information which I do not want to use, to many step for doing the simplest thing. I really did not want to abandon C++ but I knew that MFC was a huge obstacle for me. The I Found Delphi , Delphi was not only an easier language , it had the best libraries and the best ide, it was the first language to support to OO in all his Stricture and some of the Best RAD tools. It is no Mistake that .NET and JAVA copy his well known VLC library. 

From there on I learned my lesson , a programming language is much more than simple syntax.

---

### Post by Sockerdrickan on 2008-11-11
> **Kilon said:**
> From there on I learned my lesson , a programming language is much more than simple syntax.
or complex syntax. :)

---

### Post by nvteighen on 2008-11-11
> **pavel989 said:**
> 
ABSOLUTLY NO ONE, !!!NO ONE!!!, CAN PROVE A LANGUAGE'S SUPERIORITY.


Yes we can, if the language is artificial and given a certain context. Why? Well, I'm writing a paper on this right now :p but my argument basically is the following: 

Artificial languages always have a function besides the language's general function of communication. For example, Tolkien's languages serve to communicate (in a fictional world) and also for improving his works aesthetically. C++ is there to communicate a certain algorithm between people and also to have an OOP, generic, low-level programming language etc.

So, you can compare that "second" function, as it is measurable whether the language does it well or not in some context; also, the general communication function is always acomplished when the language is a language (i.e. a **system** of signs), so it makes no sense to compare languages with respect to it.

Hope it makes sense to you.

---

### Post by pmasiar on 2008-11-11
> **Kilon said:**
> You are not a real programmer until you master Assembly.

that's nothing. In old days, to be considered expert you have to be able to write code in binary from panel (and debug it!), and read binary tape (tape --> hexcode --> opcodes). ASM was for weak, read [Story of Mel](http://www.cs.utah.edu/~elb/folklore/mel.html) [background](http://www.cs.utah.edu/~elb/folklore/afs-paper/node4.html)

Programming is not about pushing the bits around. My understanding of substance of programing was profoundly changed when I read [ACM Turing Lecture 1972  The Humble Programmer](http://www.cs.utexas.edu/~EWD/transcriptions/EWD03xx/EWD340.html) by Dijkstra.

---

### Post by pmasiar on 2008-11-11
> **pavel989 said:**
> after about page 5, i got bored and came to this conclusion:

ABSOLUTLY NO ONE, !!!NO ONE!!!, CAN PROVE A LANGUAGE'S SUPERIORITY.

Relax, you are wrong ;-)

> I've fiddled with VB, C#, python, ruby, small amount of Java (very small, might come back to it...), BASIC, and C++.

Try Lisp, Prolog, Forth, XSLT, haskel and Erlang to get wider perspective: languages you mentioned are almost identical from POV of the concepts they use.

> but 5+5 works in either one of them.

Try XSLT which lacks variables (because does not need them) and then come back. ;-)

> But in my travels, the one question has always been speed. 

Speed is not all programming is: read about speed kiddies and blub programmers to understand what perspective are you missing. See also my previous post.

> what does lisp or C++ have over the other, that would make it so much better?
- so far, ive found that anything can be implemented in either, so it wouldnt matter which you use, so long as u can understand it.

This is exactly blub logic, but you seems to be open to learning wrong of your ways: read [Beating the Averages](www.paulgraham.com/avg.html) - and then more of Graham's essays.

BTW please mods can you clean up the idiotic tags on this thread? And if possible teach a lesson to a person who added them, it is IMHO  obvious personal attack?

---

### Post by Majorix on 2008-11-11
I was wondering, what is up with the tags of this thread?

---

### Post by pavel989 on 2008-11-11
> **pmasiar said:**
> Relax, you are wrong ;-)

> But in my travels, the one question has always been speed. 

Speed is not all programming is: read about speed kiddies and blub programmers to understand what perspective are you missing. See also my previous post.

> what does lisp or C++ have over the other, that would make it so much better?
- so far, ive found that anything can be implemented in either, so it wouldnt matter which you use, so long as u can understand it.

This is exactly blub logic, but you seems to be open to learning wrong of your ways: read [Beating the Averages](www.paulgraham.com/avg.html) - and then more of Graham's essays.


seems to me like you're a veteran programmer. I'm not done fully reading the article, but i do find it interesting. reminds me of the Allegory of the Cave.


And about the whole blub paradox. If all programs are in the end, compiled to machine code, So long as you think in Blub, does it matter what Blub is?

I did check out those languages, almost make no sense to me, but they look kinda kool, however, I dont see how I could use them...

My main goal in programming, is to write games. And by all means, i am no where close to writing even simple 2D scrollers, but im learning. 

The reason i chose C++, was because i figured that there's a damn good reason why almost all games are written in either C++ or JAVA. I know that there are OpenGL bindings for, well, everything (I do plan on mostly using OpenGL. I know DirectX is probably easier/better, but its MS).

So, it comes down to this for me:

I can probably switch to Lisp, despite all my efforts in learning the dreaded C++, but would it be worth it?

---

### Post by CptPicard on 2008-11-11
> **pavel989 said:**
>  reminds me of the Allegory of the Cave.

It is an excellent allegory and very fitting... some languages let you get closer to what exactly is there, and not just the shadows.

> 
And about the whole blub paradox. If all programs are in the end, compiled to machine code, So long as you think in Blub, does it matter what Blub is?

In the end, everything is executed on the hardware. Yet, we aren't all electrical engineers designing custom chips for our algorithms.

This really is the really classic misunderstanding around here... programming languages are for the mind, and the machine underneath is, from the program's perspective, irrelevant -- actually you can't tell what you're running on, from inside the program, if you tried, because of Turing-completeness.

For you as the human programmer, you are mostly interested in both productivity and how the language itself allows you to express important concepts about the problem. Bit-shuffling is the easy part, although it may sometimes be necessary for performance reasons. These reasons are purely technical though.

> 
I did check out those languages, almost make no sense to me, but they look kinda kool, however, I dont see how I could use them...

Definition of blub: can't appreciate features of higher-level languages because one has never used them :)

For games, you may not move to Lisp, but if you want to enlighten yourself, you certainly should.

---

### Post by pavel989 on 2008-11-11
im interested in Lisp now, the Macro concept, i found, is brilliant. Would i benifet from learning it though? I mean like, (well first of, can macros like that be created in C++?) are there concepts in Lisp that would improve my performance as a programmer and the perforamce of my Apps/Games?

---

### Post by CptPicard on 2008-11-11
> **pavel989 said:**
> im interested in Lisp now, the Macro concept, i found, is brilliant.

Yes, it is indeed. It demonstrates very powerfully the relationship between computation and data structures.

> 
 Would i benifet from learning it though?

Yes, of course you would.

> I mean like, (well first of, can macros like that be created in C++?)

No, because C++ is not homoiconic by structure. The closest you could probably get would be to first print a temporary source file, then run g++ on that, and produce a dynamically linkable library as a result. But that would be a massive hack :)

> 
 are there concepts in Lisp that would improve my performance as a programmer

Of course. It improves you as a *thinker about problems*, making you a better programmer in any language as a result.

> and the perforamce of my Apps/Games?

Please do not be a such a [speed kiddie]("http://en.wikipedia.org/wiki/Speed_kiddie"). Improvements in your thinking will eventually realize themselves in improvements in algorithms, which result in improvements in speed.

---

### Post by LaRoza on 2008-11-11
> **CptPicard said:**
> 
Please do not be a such a [speed kiddie]("http://en.wikipedia.org/wiki/Speed_kiddie"). Improvements in your thinking will eventually realize themselves in improvements in algorithms, which result in improvements in speed.

It is still there, must have been accepted.

---

### Post by CptPicard on 2008-11-11
> **LaRoza said:**
> It is still there, must have been accepted.

Should the singular not be "kiddy" though? (pl. kiddies)

---

### Post by pavel989 on 2008-11-11
can C++ and Lisp be used in conjunction? somehow interlaced?

---

### Post by dribeas on 2008-11-12
> **pavel989 said:**
> well first of, can macros like that be created in C++?

> **CptPicard said:**
> No, because C++ is not homoiconic by structure. The closest you could probably get would be to first print a temporary source file, then run g++ on that, and produce a dynamically linkable library as a result. But that would be a massive hack :)

Or resort to template metaprogramming. (Yes, templates are not just glorified macros). Kristof Czarnecki and Ullrich Eisenecker billed as a complete Lisp implementation built out of C++ templates. They also wrote a book called [Generative Programming]("http://www.generative-programming.org/").

I am not implying that it is of much use, if you want to program lisp go to the source: CL, Scheme... but while functional programming can be seen as the shadow in the cave, so can be C++ (and for the sake of it, probably every other language in this kind of discussions)

---

### Post by drubin on 2008-11-12
> **Majorix said:**
> I was wondering, what is up with the tags of this thread?

Somebody seems to have fixed them.

---

### Post by pavel989 on 2008-11-12
anyone know of a Lisp for C++ programmers/users tutorial? i think im too used to CPP to understand many concepts in Lisp

---

### Post by jimi_hendrix on 2008-11-12
> **pavel989 said:**
> anyone know of a Lisp for C++ programmers/users tutorial? i think im too used to CPP to understand many concepts in Lisp

same...

---

### Post by samjh on 2008-11-13
If you are going to learn Lisp, then just keep in mind that everything is a list, and forget everything you know about programming.  Start with a clean slate in your brain. ;)

Start here: [http://en.wikipedia.org/wiki/Lisp_(programming_language](http://en.wikipedia.org/wiki/Lisp_(programming_language))

Then here: [http://en.wikibooks.org/wiki/Common_Lisp](http://en.wikibooks.org/wiki/Common_Lisp)

Or here: [http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/)

---

### Post by conehead77 on 2008-11-13
> **pavel989 said:**
> anyone know of a Lisp for C++ programmers/users tutorial? i think im too used to CPP to understand many concepts in Lisp

Not Lisp, but Haskell:
[_[COLOR="RoyalBlue"]Haskell Tutorial for C Programmers[/COLOR]_]("http://www.haskell.org/~pairwise/intro/intro.html")

---

### Post by nvteighen on 2008-11-13
Lisp crash course:

0. Syntax: (*procedure* *arg1 arg2 arg3 ...*).
1. EVERYTHING is a Lisp object. So, you can make procedures that return procedures or just the name (symbol) of a variable, generate arguments, etc. Even Lisp code is Lisp object.

There it is: that's Lisp. Now, you have to learn a Lisp dialect :)

Common Lisp and Scheme are the most popular, but they're quite opposite to eachother. Common Lisp is a language aimed to make Lisp a practical language, has built-in OOP, binding, etc. Therefore it offers more built-in stuff and a bigger Std. Lib.

Scheme is more academical, aimed to people interested on theory discussions on algorithms and such, so it has a very few stuff built-in though it's not useless... it's amazing how just using a little few built-ins you can do great stuff. Anyway, all Scheme implementations offer non-standard extensions. There's a standard (R5RS... R6RS approved this year), but a certain anarchy rules over Scheme... The best implementation, MIT/GNU Scheme (mit-scheme package in the repos... though the last time I saw, Intrepid had a broken dependency + the usual Low Memory bug from Hardy).

---

### Post by pmasiar on 2008-11-13
> **nvteighen said:**
> Lisp crash course:

0. Syntax: (*procedure* *arg1 arg2 arg3 ...*).

yes. Please note that there is **no difference** between language syntax for control structures and data structures: above call is just a list where head is function name, and tail is list of arguments. That is source of Lisp power (and source of many parentheses - average program starts with '(lambda' and ends with ')))))))' ;-)

---

### Post by nvteighen on 2008-11-13
> **pmasiar said:**
> yes. Please note that there is **no difference** between language syntax for control structures and data structures: above call is just a list where head is function name, and tail is list of arguments. That is source of Lisp power (and source of many parentheses - average program starts with '(lambda' and ends with ')))))))' ;-)
That's why any Lisp coder should use a decent editor with parenthesis matching :)

---

### Post by issih on 2008-11-13
Oh for *****s sake, languages are tools, let people use the tool they want, and leave them alone.

If people are curious about languages, they will investigate the different paradigms under their own steam far more effectively than they will under duress. If they just want to get something simple done, and for some reason have some expertise in language X, then help them in that language so they can get on with the rest of their life. If they are enquiring what to use for a certain job, then I pity them, because they will get a stream of advice based on not what they want or need, but the advisers own personal preference and prejudice.

I get so tired of people who think this stuff is a holy crusade. A language is a way to make your computer do what you want, thats all it is, nothing more or less than that. They all have their advantages and disadvantages, some are more readable, some more compact, some are more robust against lax programming and some make a better margarita.

Nothing is perfect because us imperfect little humans always get our messy little hands on it, and that is even more true of politics than anything else, and thats what most of this boils down to in the end.....

---

### Post by CptPicard on 2008-11-13
> **issih said:**
> If they are enquiring what to use for a certain job, then I pity them, because they will get a stream of advice based on not what they want or need, but the advisers own personal preference and prejudice.

Could you at all entertain the notion that in some cases just perhaps that advice and underlying preference is *not* based simply on blind prejudice?

As you said yourself, experience can tell that some languages are better at some jobs than others. Discussing this is perfectly viable, in particular if the person is not experienced enough yet to make the call himself.

Then there is the "general job" of a programming language of generally expressing computations, suitability for which, apart from purely technical specific requirements, can be discussed as well.

---

### Post by wrtpeeps on 2008-11-13
> **CaptainLinux94 said:**
> It sounds like you think C++ is horrible and that you want everyone else to think it's horrible.

Tell that to all the professionals who swear to it.  There's a reason why **most professionals use it**, it's the fastest, efficient code out there.

But if you're not a professional striving to communicate the most efficiently with hardware, it's pointless...

**So please,** no flaming.

Absolute rubbish.

Companies prefer using higher level languages than C++, as they are easier to learn, updated more regularly and don't waste valuable programmers time. 

There are few areas where c++ is necessary, however Game Development is one of them.

---

### Post by nvteighen on 2008-11-13
> **issih said:**
> 
I get so tired of people who think this stuff is a holy crusade. A language is a way to make your computer do what you want, thats all it is, nothing more or less than that. They all have their advantages and disadvantages, some are more readable, some more compact, some are more robust against lax programming and some make a better margarita.

Nothing is perfect because us imperfect little humans always get our messy little hands on it, and that is even more true of politics than anything else, and thats what most of this boils down to in the end.....

+1, except for the "A language is a way to make your computer do what you want"... The issue is that programming languages just happen to be runnable under a computer, but they are languages, so they primarily express knowledge... for a certain task. So, it's reasonable to question ourselves whether a language fulfills the tasks that is meant to fulfill.

Of course, people get annoyingly religious on this matter... and start mixing feelings with arguments and well... wars begin...

---

### Post by wrtpeeps on 2008-11-13
> **nvteighen said:**
> +1, except for the "A language is a way to make your computer do what you want"... The issue is that programming languages just happen to be runnable under a computer, but they are languages, so they primarily express knowledge... for a certain task. So, it's reasonable to question ourselves whether a language fulfills the tasks that is meant to fulfill.
[B]
Of course, people get annoyingly religious on this matter... and start mixing feelings with arguments and well... wars begin...[/B]


It's the "OMG I KNOW C++" attitude that makes me laugh the most. As if it's some sort of achievement.

---

### Post by issih on 2008-11-13
If this forum was populated with dispassionate, sanely reasoning robots who would actually discuss the relative merits of different languages in a manner pertinent to a posters original problem, then that would be fine. Sadly all we have is people, and people are not sane and are rarely rational. A quick glance at the many threads on these kind of topics on basically any internet forum will tell you just how pointless it is to ask the question, because unless you already know the answer, you'll never pick it out from the noise.

Some people, as always, are worth listening to, the trick is knowing who they are.

As for the languages being used to express algorithms or indeed being a linguistic definition of the algorithm. I'd argue that mathematical logic defines the algorithm and the language is merely an implementation of the algorithm within that specific syntax. The idea transcends the definition. Languages contain their own interesting syntactical quirks that allow interesting (actually often fascinating) differences in the nature of the implementation, to the extent that the line between definition and implementation gets blurry, but that is still the way I'd view it.

---

### Post by Cracauer on 2008-11-13
> **pavel989 said:**
> im interested in Lisp now, the Macro concept, i found, is brilliant. Would i benifet from learning it though? I mean like, (well first of, can macros like that be created in C++?) are there concepts in Lisp that would improve my performance as a programmer and the perforamce of my Apps/Games?

High-performance Lisp is hard. To reduce overhead compared to C++ to near zero you gotta use CMUCL or SBCL and really know what you are doing. Likewise, mixing in Lisp code into existing frameworks is annoying.

But learning Lisp and it's macros will change your thinking about programming forever. "Compile-time computing" is the keyword here. Avoid repetitive statements that encode the same thing twice in a program so that later changes to one, forgetting the other one, bomb.

You can do powerful compile-time computing with C++ templates, but it really breaks your head. Even if C++ template metaprogramming is your goal, learning compile-time computing in Lisp is going to help you to chop the complexility one by one.

---

### Post by wrtpeeps on 2008-11-13
Learning lisp absolutely melts my head.

---

### Post by Cracauer on 2008-11-13
> **pavel989 said:**
> anyone know of a Lisp for C++ programmers/users tutorial? i think im too used to CPP to understand many concepts in Lisp

Timothy Koschmann's book is the best starter, IMHO.

Paradigms of Artificial Intelligence Programming: Case Studies in Common Lisp by Peter Norvig is *the* book to read to learn the power of Lisp in context.

The most extensive book on crazy macro programming is Graham's "On Lisp", but unfortunately I don't like his style at all and can't really recommend it as an only book.

Start at Norvig. It also helps you wrap your head around some programming concepts other than just language details.

---

### Post by CptPicard on 2008-11-13
> **issih said:**
> 
As for the languages being used to express algorithms or indeed being a linguistic definition of the algorithm. I'd argue that mathematical logic defines the algorithm and the language is merely an implementation of the algorithm within that specific syntax. The idea transcends the definition.

Being a theoretical CS guy by education, I partially agree with you -- the algorithmic ideas are not syntax-bound. Most of my studies in algorithmics were done with pencil and paper, and I rarely actually did any programming. Certainly all Turing-complete languages are equally powerful in theoretical terms, and all that. But there is a reason why we do not program in Brainfuck even though it is Turing complete. :)

All syntactical differences are by no means just syntactic sugar which is a claim one sometimes hears here. There are substantial important language primitives, in particular lambdas, closures and higher-order functions, that really make some languages transcend other languages in expressiveness. Here we're not only talking about "writing the same thing slightly differently" but really introducing new *ideas* in the language. People who argue against this just simply to be betray the fact that they have never been exposed to these ideas, but just simply have just used C-derived languages...

> Languages contain their own interesting syntactical quirks that allow interesting (actually often fascinating) differences in the nature of the implementation, to the extent that the line between definition and implementation gets blurry, but that is still the way I'd view it.

Well, I think you're not giving enough credit to what you're saying here. They're not just "quirks". And by actually seeing that you end up often with different insights into the nature of the problem, you should recognize that.

For example, I like functional programming, with preferably minimal side-effects, because it allows me to work with substitutability in my code. I can easily break out expressions and reformulate them and consider what they actually "mean". It's a bit like working with math, where you replace subexpressions with theorems you know in the hope that something interesting shows up. Often, I find that this kind of rewriting produces "aesthetically pleasing" results, and that sometimes I discover something about my problem that I might not have thought beforehand... this is true in particular about problems that are not pure algorithmic in nature but are "real-world" problems where the problem is not yet fully known to me, and its algorithmic properties need to be discovered...

> **Cracauer said:**
> High-performance Lisp is hard. To reduce overhead compared to C++ to near zero you gotta use CMUCL or SBCL and really know what you are doing. Likewise, mixing in Lisp code into existing frameworks is annoying.

Well, you aren't always even looking to eliminate the overhead completely, SBCL is already fast enough generally. Although I must admit that the overhead from simply consing intermediate lists can sometimes be appalling.

> "Compile-time computing" is the keyword here. Avoid repetitive statements that encode the same thing twice in a program so that later changes to one, forgetting the other one, bomb.

... and if you combine this with an approach where you at least try to pretend you're pure-functional most of the time -- encapsulating state changes into functions and trying to make them always return the same data with same parameters -- you can be more sure that your macros are robust even at runtime...

> **wrtpeeps said:**
> Learning lisp absolutely melts my head.

That's the whole point ... then you know you're learning something. It is interesting in particular how Lisp lets you observe different approaches to your problem easily, and this has an influence in your programming in other languages as well... you kind of learn to "see" what kind of approach you want to take, based on the problem, and then bend the language to that.

---

### Post by pmasiar on 2008-11-13
> **issih said:**
> Some people, as always, are worth listening to, the trick is knowing who they are.

As always, 80% of anything is crap. But if experts will stay silent, only the morons will comment?

And how you propose to solve the trick?

BTW language is not only the tool. Language forms structures in your brain, in your thinking, so you think "in" language instaead of "using" language, and concepts not elegant it given language are avoided, even in next language (because your brain formed to reject them).

Example: everybody knows, that to grok levitation, you need to learn Martian: [http://en.wikipedia.org/wiki/Stranger_in_a_Strange_Land](http://en.wikipedia.org/wiki/Stranger_in_a_Strange_Land)

---

### Post by Cracauer on 2008-11-13
> **CptPicard said:**
> Well, you aren't always even looking to eliminate the overhead completely, SBCL is already fast enough generally. Although I must admit that the overhead from simply consing intermediate lists can sometimes be appalling.



Yeah, but on the other hand, if you create long lists in C++ you have malloc/free calls for all the list elements, too.

Memory allocation and free (GC) in SBCL can (rarely) be faster than malloc/free. It's a tossup when both use lists in the same situations.

The problem of course is that lists are so temping to use in Lisp, a nightmare in C and awkward in C++ so that C/C++ people usually try to use arrays instead.

> **CptPicard said:**
> 
... and if you combine this with an approach where you at least try to pretend you're pure-functional most of the time -- encapsulating state changes into functions and trying to make them always return the same data with same parameters -- you can be more sure that your macros are robust even at runtime...


Funny. I wouldn't say I do any functional programming.

What I say is that I try to keep functions "const" as much as I can. And I find the concept to be supported better in C++ than in Lisp, simply because there's no declaration like "const" on Lisp functions/methods that instruct the compiler to warn me. That's a real bummer for multithreading.

On the other hand, C++ should have two "const" keywords. "Const-const" meaning nothing changes (proven by the compiler) and "mumble-const" meaning the "mutable" keyword has been used and somebody *thinks* it's const on the outside.


> **CptPicard said:**
> 
That's the whole point ... then you know you're learning something. It is interesting in particular how Lisp lets you observe different approaches to your problem easily, and this has an influence in your programming in other languages as well... you kind of learn to "see" what kind of approach you want to take, based on the problem, and then bend the language to that.

Yeah. The more your head hurts from Lisp the more you needed to learn it in the first place.

Just do not try anything without an editor that matches the parenthesis for you and does indentation. Breaks your head.

---

### Post by CptPicard on 2008-11-13
> **Cracauer said:**
> 
Funny. I wouldn't say I do any functional programming.

I would say you do. :) Although Common Lisp of course is a much more multiparadigm language than other languages that are more clearly functional.

> 
What I say is that I try to keep functions "const" as much as I can.

Yes, so you minimize side-effects.

> That's a real bummer for multithreading.

Speaking of multithreading, it's interesting btw how strong pure-functionality as a concept is for parallelism... Haskell has trivial parallel-map because of that, and Clojure is looking really good with its persistent data structures...

---

### Post by nvteighen on 2008-11-14
> **CptPicard said:**
> Being a theoretical CS guy by education, ...

Being a General Linguistics guy by education, (:)) I've been always atracted to programming languages as (artificial) languages and, therefore, as vehicles of thought that also make communication of thoughts possible.

There's a huge breach between languages like C, C++, ASM and Python, Perl, etc. and another much bigger between those and Lisp. The difference IMHO, relies on the symbolic features. I mean, natural languages are able to communicate anything because they are absolutely abstracted from the objects they refer to. There's nothing of a table in "table".

Programming languages, of course, always will be "tied" to their task and the elements that task needs... otherwise, we would talk in Java :p. But, there is a huge difference between C (which is tied to the instrument's architecture...) and high-level languages, where they are just tied to their task... a task is not a concrete object, it's an abstracted thought, so those languages are in a sense more symbolic than the low-level ones...

But, only Lisp has a full-blown metalinguistic ability. In other words, it's the only language that is able to construct things based on language/symbolic realities (abstraction of abstractions), not just theorical ones. Lisp just needs to be untied from the "programming" part to be a human language... we'd just have to create some proper vocabulary and a pronounciation... but the system would be there and the "grammar semantics" are there. That's why I believe Lisp is special (not necessarily "superior"... as there are tasks in which it fails miserably).

Another language that's developing in an interesting way is Perl... As I said before, it's the only language that relies on morphology (sigils and the "different stuff has to look differently") and semantics (the "exceptions"... actually "do what I mean, not what I say") much more than on syntax... maybe that's why it is "weird" for CS people. This is another language that easily could get a really high-level of abstraction if its developers decide to.

---

### Post by issih on 2008-11-14
Languages are interesting, and there is a quote I once heard (relating to normal human langauge not computer ones, but it still applies)

"To lose a language is lose a unique way of viewing the world"

And that is true, languages allow unique ways of expression, and often expose the inefficiencies and contradictions in each other, because generally they provide a different view on the same problem, a new window if you will. My favourite example is that the direct translation of Russian for "black hole" is "frozen star"..which to my mind is far more beautiful and descriptive.

Nonetheless, I like all the windows, even the ones with all the mud on them near the ground, and I get tired of the arguments about which offers the best view.

I like this thread more now, we've hijacked it into being interesting...yay for us

---

### Post by pavel989 on 2008-11-14
> **issih said:**
> Languages are interesting, and there is a quote I once heard (relating to normal human langauge not computer ones, but it still applies)

"To lose a language is lose a unique way of viewing the world"

And that is true, languages allow unique ways of expression, and often expose the inefficiencies and contradictions in each other, because generally they provide a different view on the same problem, a new window if you will. My favourite example is that the direct translation of Russian for "black hole" is "frozen star"..which to my mind is far more beautiful and descriptive.

Nonetheless, I like all the windows, even the ones with all the mud on them near the ground, and I get tired of the arguments about which offers the best view.

I like this thread more now, we've hijacked it into being interesting...yay for us

i think its become more of a philosophical discussion, instead of an argument over whether C++ or Lisp is better.

---

### Post by CptPicard on 2008-11-14
> **pavel989 said:**
> i think its become more of a philosophical discussion, instead of an argument over whether C++ or Lisp is better.

The whole point is that fundamentally it *is* a philosophical discussion... at least for me it is. I am not necessarily arguing that Lisp is better than C++... although  I have a strong preference for some very strong reasons, which I insist on sharing whether people want it or not ;)

C++ may be better to achieve certain specific technical goals, but personally I just find it has way too much "language" and related dogma and tricks to learn to "use it right" compared to what it actually contributes in terms of meaningful primitives that can be used to compose programs... and *that* makes for interesting philosophical discussion. And this is also why I am not 100% convinced we could turn this into some kind of "pure-facts" based discussion that could be resolved on pure logic -- it really does take some serious bona fide communication to get even slightly vague points across.

---

### Post by scourge on 2008-11-14
> **CptPicard said:**
> C++ may be better to achieve certain specific technical goals, but personally I just find it has way too much "language" and related dogma and tricks to learn to "use it right" compared to what it actually contributes in terms of meaningful primitives that can be used to compose programs... and *that* makes for interesting philosophical discussion. And this is also why I am not 100% convinced we could turn this into some kind of "pure-facts" based discussion that could be resolved on pure logic -- it really does take some serious bona fide communication to get even slightly vague points across.

Very often we do have specific technical goals to achieve. I'm now at a point where I have a few languages in my toolbox (C, C++, Objective-C, Java and Python), and I just choose the best tool for the job, instead of the language that I like the most. Sometimes "best" is the fastest, sometimes it is the easiest language, but more often than I'd like it's about libraries, development/deployment tools and business decisions. Those may not be valid arguments in a debate about language features, but they are valid reasons for learning or using a language. Then again, I'm an engineer, not a linguist, so I care about results more than methods. :)

I started to prefer C++ over C only after I had some projects for which C++ was better suited. For example multi-threaded code became so much easier and safer when I could use idioms like RAII. I'd say that the only way to learn to love C++ is to actually use it.

---

### Post by Cracauer on 2008-11-14
> **scourge said:**
> I'd say that the only way to learn to love C++ is to actually use it.

Ah. Good. After how many decades does the effect kick in? :)

Still feels like a permanent job interview nasty backwards trick interrogation session after 20 years.

The only thing that's slowly kicking in is compile-time computing but yessus is it byzantine. And of course everybody bashes you because now you are the only one who has a clue what's going on. Where you have (macroexpand '(some obscure code)) in Lisp or even (macroexpand-all ...), and all on a single keystroke in ilisp or SLIME, and where you had "gcc -E" for the C preprocessor you have ... what in C++ to see templates expand step by step?

---

### Post by scourge on 2008-11-14
> **Cracauer said:**
> Ah. Good. After how many decades does the effect kick in? :)

Still feels like a permanent job interview nasty backwards trick interrogation session after 20 years.

I didn't claim everyone will like it. What I meant was that one has pretty much zero chance getting to like C++ just by reading about it. To appreciate its features one has to actually use it.

And C++ now is not the same thing as C++ 20 years ago. The language has evolved, and the compilers have gotten a heck of a lot better.


> The only thing that's slowly kicking in is compile-time computing but yessus is it byzantine. And of course everybody bashes you because now you are the only one who has a clue what's going on. Where you have (macroexpand '(some obscure code)) in Lisp or even (macroexpand-all ...), and all on a single keystroke in ilisp or SLIME, and where you had "gcc -E" for the C preprocessor you have ... what in C++ to see templates expand step by step?

I have to admit that I almost never write my own template classes or functions, but I do use a lot of them (stl, boost, etc.). Templates have their problems (increased compile time, hard-to-express data types, pages long error messages), but a lot of them will be eliminated by the next version of C++ (C++0x).

---

### Post by Cracauer on 2008-11-14
> **scourge said:**
> I have to admit that I almost never write my own template classes or functions, but I do use a lot of them (stl, boost, etc.). Templates have their problems (increased compile time, hard-to-express data types, pages long error messages), but a lot of them will be eliminated by the next version of C++ (C++0x).

But I'm bashing the debug facilities, not the compiler.

Will the next generation of C++ tools have a tracer that allows you to expand templates step by step, inspecting the intermediate results (such as in the Lisp examples I gave)?

As things are now, we don't even have the minimal capability, which is looking at the result after all template expansion, but before compilation from past-template C/C++ code to assembly.

Also, you can't even insert tracing "print" statements that would allow you to trace while things unfold. I'm not aware of any such facility, although I have to admit that I didn't troll all of boost for it.

In Lisp, you don't only have the macroexpasion debugging built in, you also have the full power of Lisp at compile time. The same language, all of the runtime features, are available at compile time.  Use print for (format t "~d foobar~%" blah fasel) all you like inside you macro and it will print at compile time, to stdout. In a recursive call (at compile time) it will follow nicely.

This is a major reason why C++ template metaprogramming kicked C++ into being liked by people like me, but makes it difficult to make use of at work or in OpenSource projects. It's just over the top difficult for "regular" programmers to grasp what is going on. Most of the time, when forced to understand what a wild piece of code is doing, programmers splatter "print" statements. In C++ you can do that for run-time computing, but not compile-time computing. In Lisp, no such difference exists, the runtime language is the same as and available at compile time.

---

### Post by scourge on 2008-11-15
> **Cracauer said:**
> But I'm bashing the debug facilities, not the compiler.

Will the next generation of C++ tools have a tracer that allows you to expand templates step by step, inspecting the intermediate results (such as in the Lisp examples I gave)?

Okay, now I know what you mean, and I agree that it would be neat if we could unfold templates. I've managed without template metaprogramming myself, so I can't help you much here. We don't yet know the full feature and tool set of C++0x, but a lot of work has been put into improving template metaprogramming.

---

### Post by CptPicard on 2008-11-15
> **scourge said:**
> What I meant was that one has pretty much zero chance getting to like C++ just by reading about it.

In higher-level languages it is equally true that if you do not use the language, you do not know what its features are good for. HLLs subsume -- in some sense conceptually contain -- lower-level languages, while often clarifying, unifying and generalizing those concepts... therefore I would suggest that taking this view the criticism of lower level languages such as C++ is founded very much on C++ just being comparatively more difficult to work with, and no amount of trying to learn to love it is going to help.

I mean, I know there are really skilled C++ hackers around, but the more they have to write pages and pages of explanations as to why I'm wrong -- often relying on very technical refutations on some very specific special cases, or the "you just need to know it, duh" -- just reinforces the point. It should not have to come to that you know ;)

> 
 To appreciate its features one has to actually use it.


What are these features you speak of? :confused:

Never came across them and I've used C++ all right. All of the stuff is found elsewhere, in a nicer package. Again, I make the exception for runtime speed and finer-grained resource control, but those are technical requirements, not language features... most importantly, they have nothing to do with language definition which we are discussing here -- there is no obstacle in the way the language is defined to create better and better compilers and runtime environments in, say, Lisp. C++ doesn't get any better in the sense that I am interested in by better compiler implementation because the definition of the language stays the same.

> but a lot of them will be eliminated by the next version of C++ (C++0x).

IMO the really important part is the addition of the lambda, but I have no idea how it will turn out...

---

### Post by nvteighen on 2008-11-15
> **CptPicard said:**
> 
C++ may be better to achieve certain specific technical goals, but personally I just find it has way too much "language" and related dogma and tricks to learn to "use it right" compared to what it actually contributes in terms of meaningful primitives that can be used to compose programs... and *that* makes for interesting philosophical discussion. And this is also why I am not 100% convinced we could turn this into some kind of "pure-facts" based discussion that could be resolved on pure logic -- it really does take some serious bona fide communication to get even slightly vague points across.

I actually think the same as you but exactly because of the opposite reason: C++ is too less "language" but just referencing to objects... like smoke refers to some fire... I mean, language means there's a "distance" between the meanings and the objects those meanings refer to. Otherwise, we'd have to always carry a bag of objects each time we want to refer to them (like in one of Gulliver's stories).

C and C++ are too bound to the objects they refer too... It obviously refers to them through meanings, but these are not sufficiently symbolic to reflect human's mind, but to reflect the computer's workings. This is not bad: it's determined by these languages' goals.

But the main critique against C++ seems to be that it constantly betrays itself by introducing very high level constructs in a language working at low level. It is a somewhat "broken" language, fragmented into several pieces that don't fit together into a unique uniformed system... this is reflected on the lots of particular syntax rules each new construct introduces, for example.

> **scourge said:**
> Very often we do have specific technical goals to achieve. I'm now at a point where I have a few languages in my toolbox (C, C++, Objective-C, Java and Python), and I just choose the best tool for the job, instead of the language that I like the most. Sometimes "best" is the fastest, sometimes it is the easiest language, but more often than I'd like it's about libraries, development/deployment tools and business decisions. Those may not be valid arguments in a debate about language features, but they are valid reasons for learning or using a language. Then again, I'm an engineer, not a linguist, so I care about results more than methods. :)

Linguists also care for results :)

Artificial languages, according to my very humble researches, seem to be defined by having a task besides the formalization/communication one. So, it's quite natural to choose the best artificial language for a certain task. If the language succeeds in achieving the task, it's fine; if not, there'll be someone working a new language to do it.

> **CptPicard said:**
> In higher-level languages it is equally true that if you do not use the language, you do not know what its features are good for. HLLs subsume -- in some sense conceptually contain -- lower-level languages, while often clarifying, unifying and generalizing those concepts... therefore I would suggest that taking this view the criticism of lower level languages such as C++ is founded very much on C++ just being comparatively more difficult to work with, and no amount of trying to learn to love it is going to help.


I'd rather try not to confuse the criticism against C++ with the one against using low-level languages for the high-level tasks. I mean, everything you're saying here is absolutely invalid for Forth, which is a low-level language... and doubtful even for C.

---

### Post by meson2439 on 2008-11-15
C++ syntax is one of those languages that have grown to be very complex. Not suprising considering that it has been growing for years and have incorporated many new features that are popular currently. Thus the complexity of c++ has increased, so we could understand the frustration of many c++ programmers with the langguage. 

Personally however, my only vendetta against c++ is the amount of code needed to be written compared with other modern langguages. Complexity however is not among the reasons to hate the langguage because it was not as if I need to use all of c++ features each and every time. Limiting oneself on some features only and maximize the potential of those few features is the key for sane programming. To be able to master the few features, enables one to easily identify bugs and errors it might produce because all the errors are felt similar. 

Unfortunately in the real world, programmers are being forced to use codes from others. Thus limiting oneself to only some features of c++ is out of the question. The pressure from the employer or client allowed little time for the programmer to learn new features. This leads to the negative feelings for the langguage and force them to leave it completely for a more manageable langguage.

C++ true advantage is the flexibility; at least for people who love to create their own library (though it might be a nightmare for others to understand it). C++ is the best langguage for those who wish to do a custom job on every component of their software, beaten only by assembly and machine code. For these category of programmers, the ability to produce a fully custom code is of the greatest enjoyment. 

Like all compiled langguage, executables created from c++ has a very fast execution speed and is less intensive on resources. In the user end, it is very important and so programmers pride themselves in creating the fastest implementation with as little resources possible. Beating 1/2 a second and using 1MB less memory is also a great source of enjoyment.

The flexibility of c++ and the pride of the programmers isn't the only reason for its popularity. The huge amount of work done in the langguage helps keep the langguage relevant.

In time however, the majority of us will definitely abandon c++, the same way most of us have abandon machine code, assembly and fortran (no offense to fortran, assembly and machine programmers intended). My only wish is for a new langguage that combines Matlab capablities of matrix and vector manipulation with python power but is still free of course:KS. Personally, I want to see less loops in the new implementation. I shake my head each time I compared how short and easy Matlab scripts compared with c++ especially on Math. Python also didn't improve in these respect. Disadvantages of Matlab, Scilab and Octave is their flexibility. Combining the best of Matlab and python is the future. If not, it's likely that we will need to know several different langguages just to create a decent software, the same way that is currently happening in web development.

---

### Post by CptPicard on 2008-11-15
> **meson2439 said:**
> My only wish is for a new langguage that combines Matlab capablities of matrix and vector manipulation with python power but is still free of course

Ever tried [SAGE]("http://www.sagemath.org/")?

It is a FOSS math toolkit integration project with Python has the glue language...

---

### Post by L-mental on 2008-11-15
> here; remove the FOR keyword from c++ .. then try to implement it using templates or whatever .. (note; it must be _clean_, _sane_ and work in all situations .. and the code must be beautiful and simple) .. see how the language isn't what you want it to be?

Here; remove a leg from a man... then try to make it run with his feets or whatever... (note: it must be __clean__, __sane__ and work in all situations... and the gait must be beautiful and simple)... see how the human being is NOT made for walking?

---

### Post by CptPicard on 2008-11-15
> **L-mental said:**
> Here; remove a leg from a man... then try to make it run with his feets or whatever... (note: it must be __clean__, __sane__ and work in all situations... and the gait must be beautiful and simple)... see how the human being is NOT made for walking?

(I'm not going to browse back to see from whom this came from but it really reads like lnostdal...)

The point apparently escapes you -- the Lisp macro system easily allows for implementation a "for loop" (or any looping construct -- the Common Lisp "loop" is a macro), while in the C++ template system it would be either ugly or impossible, and it needs to be implemented as a language primitive instead...

In addition one needs to recall that lisps in general manage just fine without a for keyword and use tail recursion in its stead, especially Scheme...

---

### Post by unutbu on 2008-11-15
I would like to understand more about lisp macros. 
I've read this interesting post: [http://lists.warhead.org.uk/pipermail/iwe/2005-July/000130.html](http://lists.warhead.org.uk/pipermail/iwe/2005-July/000130.html) which describes how lisp macros can be be used to deduce the value of x even when it was not explicitly set. 

And I'm tantalized by Graham's remark that no other language has a facility comparable to lisp macros, 
that 20--25% of his Viaweb app was macros and that his competitors had a hard time duplicating his development speed because their languages didn't have macros ([http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)). 
But I'm having a hard time imagining what those macros were doing.

Can anyone shed some light on this, and/or suggest other examples of when macros can solve a problem that would be much harder to solve in any other language?

---

### Post by Cracauer on 2008-11-15
> **unutbu said:**
> I would like to understand more about lisp macros. 
I've read this interesting post: [http://lists.warhead.org.uk/pipermail/iwe/2005-July/000130.html](http://lists.warhead.org.uk/pipermail/iwe/2005-July/000130.html) which describes how lisp macros can be be used to deduce the value of x even when it was not explicitly set. 

And I'm tantalized by Graham's remark that no other language has a facility comparable to lisp macros, 
that 20--25% of his Viaweb app was macros and that his competitors had a hard time duplicating his development speed because their languages didn't have macros ([http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)). 
But I'm having a hard time imagining what those macros were doing.

Can anyone shed some light on this, and/or suggest other examples of when macros can solve a problem that would be much harder to solve in any other language?

unutbu, I planto start a thread about compile-time computing to make this more clear, but I need some free time first.

However, you can read Paul Grapham's book "On Lisp" for free on the web. It is the most extensive work on what you can do with Lisp macros:
[http://www.paulgraham.com/onlisp.html](http://www.paulgraham.com/onlisp.html)

Now, as I said above, personally I don't like Graham's style and recommend the Norvig book (that you have to buy), but as a mind-opener "On Lisp" will certainly do. Macros start at page 82.

%%

As a high-level view, just imagine this: in C you can define your down functions like mysort(), myrand() and whatnot. You aren't stuck with the C-provided sort() and rand(). You then call them in language-provided control constructs like "for", "do", "while", "if" etc.

In Lisp, the same way that you aren't stuck with predefined functions you aren't stuck with predefined control constructs. In Lisp, you define your own "for", "do", "while", "if" etc. It's a programmable programming language.

In fact, all the loops and control constructs in your Lisp implementation *are* just macros. The compiler itself has no clue and no interest in what (dotimes, dolist, loop and all that is, it never sees them at all).

Not only that, Common Lisp's OOP extension CLOS, roughly the equivalent of what early C++ did for C (classes, inheritance), was implemented 100% in macros with no compiler changes whatsoever. Tell that to people who changed C compilers to do C++ :). Yes, you could have written your own OOP CL variant without compiler source code. In fact many people did because they don't like CLOS.

---

### Post by meson2439 on 2008-11-15
Never tried SAGE but from the website, I'm envisioning something more ambitious than what SAGE is currently offering. Scilab and octave is in the right direction, but unfortunately both are currently limited to Mathematics only. In other aspects of programming, both fails compared to python as a general purpose langguage. We need something new, none of the current spinoffs seems to meet this criteria. Let me rephrase this: we need a general purpose langguage with great math support, easy matrix manipulation, easy vector manipulation, reduced reliance on **for** by using vectors instead, but maintains the capability of python or java.

Anyway, the epicycles animation in SAGE website is great.

---

### Post by CptPicard on 2008-11-15
Well, for an interesting "math language" see Haskell, but it being pure-functional it imposes quite a lot of mindset shift in a lot of things -- it is not (immediately) as easy as Python, although it is syntactically certainly very easy :)

---

### Post by meson2439 on 2008-11-15
Haskell looks interesting. The way it handles sequence and logic is unique. Much more compact compared to c/c++. I might learn it, given some time but the gentle tutorial are not as simple as it could be. But still, matrix manipulation should be as easy as declaring a new number and matrix operation as simple as multiplication of two integers. Forgive me for whining about this. No need for you guys to concern about it since the matter is unrelated to the thread.Thanks anyway.

---

### Post by unutbu on 2008-11-15
> we need a general purpose langguage with great math support, easy matrix manipulation, easy vector manipulation, reduced reliance on for by using vectors instead, but maintains the capability of python or java.
Python with the python-scipy package installed satisfies this.

For example,
[PHP]#!/usr/bin/env python
import scipy
a=scipy.matrix([
        [1,1,1],
        [4,4,3],
        [7,8,5]
        ])
b=scipy.matrix([
        [-1,6,-3],
        [2,0,5],
        [1,7,1]
        ])
print a*b

# [[ 2 13  3]
#  [ 7 45 11]
#  [14 77 24]]
[/PHP]

See [http://www.tau.ac.il/~kineret/amit/scipy_tutorial/](http://www.tau.ac.il/~kineret/amit/scipy_tutorial/)

---

### Post by krzysz00 on 2008-11-15
please stop flaming
:(

---

### Post by meson2439 on 2008-11-15
impressive... from the tutorial it looks like it can do a lot of neat stuff. I think i'll try exploring it further before deciding if it's good enough for most purpose. Thanks

---

