---
title: "What are your programming/app dev flaws?"
date: 2008-07-09
forum: Programming Talk
---

### Post by skeeterbug on 2008-07-09
Title says it all, what are your programming/app development flaws?

I will start. :D

Mine tend to be around commenting/documentation. Also, my code can get a bit inconsistent if I am in a hurry (naming and such). In C#/Visual Studio I use the code analysis add-on to address these issues. I am thinking about writing something to check PEP 8 rules in PyDev.

---

### Post by lisati on 2008-07-09
I tend to code linearly and end up with the equivalent of just C's main() and few (if any) other routines, e.g. check command line, open file(s), a loop to process the file(s), close files, done!

---

### Post by shifty2 on 2008-07-09
Look up pylint - it checks your code based on pep8 rules. You can also customise it to suit how you would ideally like your code to be as well. I imagine there would be a simple way of incorporating that  into pydev

---

### Post by skeeterbug on 2008-07-09
> **shifty2 said:**
> Look up pylint - it checks your code based on pep8 rules. You can also customise it to suit how you would ideally like your code to be as well. I imagine there would be a simple way of incorporating that  into pydev

Very nice. I was hoping someone would comment on that. Keep the flaws coming. :)

EDIT*
Looks like PyDev supports PyLint, but it is disabled by default:
[http://pydev.sourceforge.net/pylint.html](http://pydev.sourceforge.net/pylint.html)

---

### Post by kknd on 2008-07-09
I try to optimize too early (before doing tests to discover the best strategy to optimize) and sometimes I don't program a "feature" fearing for a bad performance (that maybe would not occur).

---

### Post by BwackNinja on 2008-07-09
Terrible naming of variables (if I'm feeling really lazy and will get a program done all at one time, I use one-letter variable names).

Copying and pasting subroutines and modifying them a bit for a slightly different purpose rather than making one method to do it all cleanly.

Complete lack of comments. The only time I use them is when I don't want to delete a chunk of code but I don't want it used either.

---

### Post by tinny on 2008-07-09
Nothing im prefect... haha

My first problem is that I am human and therefore inherently handicapped to program.

FYI
[http://javasoapbox.blogspot.com/2008/03/good-programmers-have-small-brains.html]("http://javasoapbox.blogspot.com/2008/03/good-programmers-have-small-brains.html")

My major flaw would probably be a tendency to be a Architecture Astronaut. (Something I am trying to rectify)

A good quote from pmasiar.
> **pmasiar said:**
> 
If you do generalizations too soon, you are something Joel Spolsky calls [Architecture Astronauts](http://www.joelonsoftware.com/articles/fog0000000018.html), who use so high abstractions that they run out of oxygen :-)

---

### Post by CptPicard on 2008-07-09
I have always sucked in the design sense, especially when it comes to object-orientedness. Ever since I was an undergrad I felt like there has to be something badly wrong with all this UML and requirement to become an Architecture Astronaut before you can actually accomplish something in OOP-obsessed languages such as Java or C++.

I am much more of an algorithms guy and therefore I have always found the "software engineering" side to be a horribly mind-numbing exercise in bureaucracy. This is why I have never really bothered even at trying to become better at creating OOP-abstractions... I hate having to fight the type system when I know exactly what I want to achieve, but the language won't let me.

That said, for me systems like Common Lisp's CLOS and Python's genericness are a godsend. If only CL-style multiple dispatch was more prevalent... it really is "object-orientedness done right".

---

### Post by tinny on 2008-07-09
> **CptPicard said:**
> I have always sucked in the design sense, especially when it comes to object-orientedness. Ever since I was an undergrad I felt like there has to be something badly wrong with all this UML and requirement to become an Architecture Astronaut before you can actually accomplish something in OOP-obsessed languages such as Java or C++.

I am much more of an algorithms guy and therefore I have always found the "software engineering" side to be a horribly mind-numbing exercise in bureaucracy. This is why I have never really bothered even at trying to become better at creating OOP-abstractions... I hate having to fight the type system when I know exactly what I want to achieve, but the language won't let me.

That said, for me systems like Common Lisp's CLOS and Python's genericness are a godsend. If only CL-style multiple dispatch was more prevalent... it really is "object-orientedness done right".

haha :)

(Set the scene) Job interview...

Interviewer: So Philip, what would you say is your biggest weakness?

Philip: Id say my biggest weakness is that I work too hard.

You cheated CptPicard :)

---

### Post by CptPicard on 2008-07-09
Yeah, well, I know that just saying bluntly that I suck at design and am fairly contemptuous of it is probably not such an impressive thing to say at an interview but at least I'm honest ;)

(Which is why I'm glad I consult for someone who honestly doesn't care what the code looks like as long as it does what is expected, and can use languages like Lisp if I want to...)

---

### Post by scragar on 2008-07-09
Mines that I tend not to back things up.

That and I have a tendency to charge in, whip up something that works perfectly, then check the specs to find that I have to redo half of the code to get what was asked for. This is also a bit of an advantage, in that I don't need to spend long times planning, because of my nature I've very good at seeing what will need to be done and anticipating flaws without having to worry about planning.

Oh, and my comments tend to be a little sporadic, which is not to say that I use too few, just that they tend to be grouped around the intresting code and ignore the boring stuff.

---

### Post by bruce89 on 2008-07-09
> What are your programming/app dev flaws?

Everything aside big ambitions.

---

### Post by pmasiar on 2008-07-09
1) Analysis paralysis: I am tempted to research too long when sometimes would be more appropriate to dive in and figure it out. 

2) I get really annoyed when good coding practices are not followed, to the point I am frustrated and not effective: wasting time on trying to redesign the code (do it right) instead of just fixing it. Problem is, I have couple of really smart code cowboys who can whip and copy/paste huge amounts of code doing something - and they are even capable to maintain it, sometimes. I am tempted to refactor it all the time.

---

### Post by LaRoza on 2008-07-09
My lack of caring I think.

I like to learn. I like to learn *anything*. In the end, I don't care what I am learning. This means I am not always continuous. I could be working on learning Haskell and then suddenly decide I am more interested in the history of the Spatha.

---

### Post by elithrar on 2008-07-09
Motivation; I have a lot of half-started projects that have some great front-ends (or the reverse, great foundations) but aren't complete. When it comes to code though, I'm fairly pedantic about comments, documentation & style - so what I do have looks great, haha.

---

### Post by kavon89 on 2008-07-09
> **elithrar said:**
> Motivation; I have a lot of half-started projects that have some great front-ends (or the reverse, great foundations) but aren't complete.

^ Exactly that, and my code usually has zero commenting so when I look back at it a month later or something, I have trouble figuring out whats going on.

I'm going to keep this in mind now that I've gone back thought about it. I'm going to go crazy with comments with a project I just started.

---

### Post by mssever on 2008-07-10
My biggest weakness is that I don't really care for reading other people's code, so I'm sure that I miss out on a lot of learning experiences. I tend to code mostly on my own.

---

### Post by Sockerdrickan on 2008-07-10
Well it used to be stupid conversion

return string(sstream.str());


> **BwackNinja said:**
> Terrible naming of variables
:) If I can't come up with a name I pick it with some kind of relevance...

```

void match(string yay) {
    cout<<endl<<target<<"\t\""<<yay<<"\""<<endl;
}

```

---

### Post by nvteighen on 2008-07-10
Excessive modularization: I scatter stuff into several files, as I write everything as if were libraries. Probably this makes me like an Architecture Astronaut (is I understood the term well)?

---

### Post by Tony Flury on 2008-07-10
Aside from the plethora of one character variable names littering my code (x,y, i & j) are common - i often try to re-invent the wheel, and end up using my code as opposed to the library.

Case in point : 
Instead of learning to use and love the C++ STL container templates, i have written my own (first as an exercise in template writing). My projects now use my versions (and not the STL) as i am familiar with how they work, and they fit in better with my programming style.

---

### Post by Lster on 2008-07-10
Motivation. But I have an excuse being the age I am! ;)

---

### Post by Wybiral on 2008-07-10
I suffer from the "build a framework just to say 'Hello world'" disorder. I also have too many ideas, which gets me in trouble because my new idea is always better than the last one (the one that I never finished).

---

### Post by nvteighen on 2008-07-10
> **Wybiral said:**
> I suffer from the "build a framework just to say 'Hello world'" disorder. I also have too many ideas, which gets me in trouble because my new idea is always better than the last one (the one that I never finished).
:lol:

---

### Post by skeeterbug on 2008-07-10
> **Wybiral said:**
> I suffer from the "build a framework just to say 'Hello world'" disorder. I also have too many ideas, which gets me in trouble because my new idea is always better than the last one (the one that I never finished).


That is another one of mine, fortunately I can pass it along to get finished by another member of the team though. :)

---

### Post by Mickeysofine1972 on 2008-07-11
I tend to get really messed up when clients do U-turns on functional specs when I've written enough code to wrap several times around the earth.

This is bad because according to Joel Spolsky customers are notorious for this kind of thing. That means I'm doomed to a life of programming in a bad mood :lolflag:

On a more programming type context, I used to program in a very linear fashion due to my first programming lanuages being C/ASM. I recently remedied this and became a Abstraction Astronaut for a while :guitar:

I'm slowly getting better though as I progress through endless anoyances with customers and specs hehe

Mike

---

### Post by LaRoza on 2008-07-11
> **Mickeysofine1972 said:**
> 
This is bad because according to Joel Spolsky customers are notorious for this kind of thing. That means I'm doomed to a life of programming in a bad mood


That is common; which is what the waterfall method doesn't really work well most of the time.

---

### Post by tinny on 2008-07-11
> **Mickeysofine1972 said:**
> I tend to get really messed up when clients do U-turns on functional specs when I've written enough code to wrap several times around the earth.

This is bad because according to Joel Spolsky customers are notorious for this kind of thing. That means I'm doomed to a life of programming in a bad mood :lolflag:

Mike

Haha, so true!

The thing that keeps me sane is that ive slowly managed to convince myself that this sort of change is good because it keeps us looking busy and therefore employed. :)

---

### Post by skeeterbug on 2008-07-11
> **Mickeysofine1972 said:**
> I tend to get really messed up when clients do U-turns on functional specs when I've written enough code to wrap several times around the earth.

This is bad because according to Joel Spolsky customers are notorious for this kind of thing. That means I'm doomed to a life of programming in a bad mood :lolflag:

On a more programming type context, I used to program in a very linear fashion due to my first programming lanuages being C/ASM. I recently remedied this and became a Abstraction Astronaut for a while :guitar:

I'm slowly getting better though as I progress through endless anoyances with customers and specs hehe

Mike

Yeah my boss can't say "no" to a customer, so we are bloating the hell out of our code base right now. :(

---

### Post by CptPicard on 2008-07-11
> **Mickeysofine1972 said:**
> I tend to get really messed up when clients do U-turns on functional specs when I've written enough code to wrap several times around the earth.

Is this really this common? :)

I mean... this is very typical: I write a nice object-oriented abstraction for something in my toolkit that is my main product. I try to make it generic in the sense that I abstract a lot of stuff away -- so that hopefully at the top level I am just calling stuff in general interfaces or top-level classes. Of course I do this in the orthodox hope that it will make my code more reusable and will allow for me to actually charge less in writing future extensions (one important customer retention policy is actually trying to think ahead for them in things they can't).

Ok... so... customer all of a sudden comes up with some new requirement that is essentially some kind of functionality "exception" for some particular subclass of my nice functionality hierarchy. *BANG* the design goes out the window because the *information simply is not there* at the top level!

At least Java has runtime instanceof so that you can create an ugly hack...

(And no, I can't use Lisp/Python, unfortunately... too slow)

---

### Post by nvteighen on 2008-07-11
I never have coded professionally... but I imagine you guys have not only a bad time fighting against the code but also against people who haven't ever touched a variable and still give you orders on what your program has to do.

Sincerely, you surely have to love what you do, otherwise you'd have already killed someone.

---

### Post by Mickeysofine1972 on 2008-07-11
Well the only way I can stop this happening is by getting the sales guys to make the new clients, (the old ones are under old contracts that let them get away with this, which is what is really getting on my nerves), and make them sign an agreement for the functional description to be signed and confirmed as correct from the start. 

Then also in the new contracts there is a clause to say that any further changes or additions to the spec will incur additional development costs. The thought of extra money payed out seems to put them off from being so 'full of great ideas' hehe!

The only problem I have left is that I still have to work with old projects with the old style contracts. I hope to put a stop to that by getting the sales guys to get those clients to sign off the projects as complete. Then we can bill them for any further U-Turns which will be met with maximum costs :lolflag:

Right now though I have one client that is really having a laugh and TBH I would love it if he would just go away :mad:

Mike

---

### Post by skeeterbug on 2008-07-11
> **nvteighen said:**
> I never have coded professionally... but I imagine you guys have not only a bad time fighting against the code but also against people who haven't ever touched a variable and still give you orders on what your program has to do.

Sincerely, you surely have to love what you do, otherwise you'd have already killed someone.

I do love coding and that is what keeps me going. I try to look at the feature requests as challenges we need to solve, rather than the pain in the *** that they truly are. The boss telling customers our product does something it doesn't is always fun too. Boss comes in after a demo - "Yeah, I told them the software does X, so could you look into it for me, thanks."

---

### Post by Mickeysofine1972 on 2008-07-11
LOL I think bosses are the same the world over!

Mike

---

### Post by CptPicard on 2008-07-11
I'm so glad I essentially have "stock options" so to speak in my product, so my client's feature requests may make me pissed off for a few minutes regarding why he didn't think to mention that beforehand but... it's for the better of both of us, so better just deal with it and get hacking, and try to think even further ahead in the future.

This is, interestingly, why I never recommend programming per se as a career -- people should become well-rounded people with wide understanding of all sorts of things, and preferably domain knowledge in what they are doing. This adds value to you as a developer, and you can get your foot in the door somewhere where those people who actually have capacity to make money need your computing skills...

---

### Post by pmasiar on 2008-07-11
> **LaRoza said:**
> That is common; which is what the waterfall method doesn't really work well most of the time.

This is not only common: it is **normal**. Users have **no other way** to comprehend your design than a program: so making a paper design interface (without any code), and then quick prototype is crucial, and thats why using dynamically typed languages (which allow for a quick prototype) is the only way to program and stay sane.

Users cannot predict which comments are important, which "little changes" will have big design consequences ("I did not want to confuse you with minor details first time around, but now I recall on rare occasion we have these different ways to handle it, and the are very important"). That's exactly the problem with programming: we are building cloud castles in our minds with abstractions, then want to pour concrete on it to show users how it looks.

Homework: re-read Dijkstra, "Humble Programmer" and subscribe to useit.com (and check popular old articles) and [http://en.wikipedia.org/wiki/Paper_prototyping](http://en.wikipedia.org/wiki/Paper_prototyping) :-)

---

### Post by skeeterbug on 2008-07-12
> **CptPicard said:**
> I'm so glad I essentially have "stock options" so to speak in my product, so my client's feature requests may make me pissed off for a few minutes regarding why he didn't think to mention that beforehand but... it's for the better of both of us, so better just deal with it and get hacking, and try to think even further ahead in the future.

This is, interestingly, why I never recommend programming per se as a career -- people should become well-rounded people with wide understanding of all sorts of things, and preferably domain knowledge in what they are doing. This adds value to you as a developer, and you can get your foot in the door somewhere where those people who actually have capacity to make money need your computing skills...

Yeah I have stock options too, but it is still annoying. Not long ago my boss was bitching because their was too much crap in the software now (a user was complaining it was too complex). Go figure, he rarely listens to my recommendations.

---

### Post by cycloptivity on 2008-07-12
> **kavon89 said:**
> ^ Exactly that, and my code usually has zero commenting so when I look back at it a month later or something, I have trouble figuring out whats going on.

I'm going to keep this in mind now that I've gone back thought about it. I'm going to go crazy with comments with a project I just started.

/me has tried this twice and yet still hasnt managed to fix the commenting habit :(

---

### Post by Mickeysofine1972 on 2008-07-12
> **pmasiar said:**
> This is not only common: it is **normal**. Users have **no other way** to comprehend your design than a program: so making a pater design interface (without any code), and then quick prototype is crucial, and thats why using dynamically typed languages (which allow for a quick prototype) is the only way to program and stay sane.


This is flawed thinking as you will quickly find that you actually start looking like you have done lots of work to start with, but then as the project starts to mature you then have the appearance as a developer who has stopped working as hard.

Its better to make your initial spec and agree it functionality without giving your client or bosses false horizons.

Mike

---

### Post by LaRoza on 2008-07-12
> **pmasiar said:**
> This is not only common: it is **normal**. Users have **no other way** to comprehend your design than a program: so making a pater design interface (without any code), and then quick prototype is crucial, and thats why using dynamically typed languages (which allow for a quick prototype) is the only way to program and stay sane.


I know, but I didn't want to assume. I am sure somewhere in history, it worked at least once.

> **Mickeysofine1972 said:**
> This is flawed thinking as you will quickly find that you actually start looking like you have done lots of work to start with, but then as the project starts to mature you then have the appearance as a developer who has stopped working as hard.

Give an example of specs not changing by the client?

---

### Post by Mickeysofine1972 on 2008-07-12
> **LaRoza said:**
> I know, but I didn't want to assume. I am sure somewhere in history, it worked at least once.


Give an example of specs not changing by the client?
Thats not the point I was making LaRosa, I was saying that presenting a program that has the look of the desired software but no code in it can often be like shooting yourself in the foot.

Mike

---

### Post by LaRoza on 2008-07-12
> **Mickeysofine1972 said:**
> Thats not the point I was making LaRosa, 

Hola! But I am not Latino ;) LaRoza for the Basque ;)

> 
I was saying that presenting a program that has the look of the desired software but no code in it can often be like shooting yourself in the foot.

I don't know. It seems the clients care more about the interface and it working. I doubt a presentation of the backend (which I would prototype first) would be successful. "Hello clients who may be paying me, let me explain a storage engine and my choice of using ORM instead of SQL!" instead of "This is what it would look like and when we are done it will do what you want".

You are right making a large complex featurefull looking mockup could be misleading, however, on thedailywtf.com, there was an article of a video game (from the 90's) and they were very far behind on the game. Planes (it was an arial combat game) had very unrealistic issues (bugs) and the funding was about to be yanked. You couldn't turn, shoot, or really do anything without something ridicoulous happening. A new programmer comes in to save the project and instead of fixing bugs (the project was going to be reviewed to see if it was worth it) he makes a third person cam to show things (you know, zoom out to see a plane crash, or a bomb drop or some other action). His code didn't help the game, which could be fixed in time, but it added a new feature. At the presentation of the game, the new guy was careful not to do anything that caused a bug, but showed of the new feature. They got the funding and the time to make a game which was very profitable.

---

### Post by Mickeysofine1972 on 2008-07-12
> **LaRoza said:**
> Hola! But I am not Latino ;) LaRoza for the Basque ;)

.

Oops! Sorry I typed s and not z! hehe! :lolflag:

Ok so thats good that the customers see some progress nearing the end of the project and as a result they got the time and funding.

But you did say that that was after the initial specification stage which is when its the worst time to show a client or boss a feature rich demo. They just don't really get it that the thing your showing them from the start is going to take a lot more time to develop functionality.

But, I have to say I like what that guy did in the end. It really saved a floundering project that just need a bit more time :)

Mike

---

### Post by LaRoza on 2008-07-12
> **Mickeysofine1972 said:**
> 
But you did say that that was after the initial specification stage which is when its the worst time to show a client or boss a feature rich demo. They just don't really get it that the thing your showing them from the start is going to take a lot more time to develop functionality.
I wish I could find the original. I can't search thedailywtf.com site because I keep getting side tracked...

---

### Post by pmasiar on 2008-07-12
> **Mickeysofine1972 said:**
> This is flawed thinking ...
Its better to make your initial spec and agree it functionality without giving your client or bosses false horizons.

It's a flawed thinking that client can understand what she signs in spec. You can wrestle her to paid for any changes after the specs are signed, but you will never get any repeat contract from her - and she will badmouth you as incompetent designer, and she will be 100% right.

And how you can divine right time estimate for code if you don't know if your imagined workflow even makes sense for a customer?

Paper design demo is exactly good because it is obvious that it is not program - it is just pages of paper, but you can test usability of your design without vomiting lost of bad code.

Of course unless you are such "expert" so you can defy  advice from people who get paid to train developers to design usable systems. You obviously never checked any article on useit.com, did you?

---

### Post by pmasiar on 2008-07-12
> **Mickeysofine1972 said:**
> I was saying that presenting a program that has the look of the desired software but no code in it can often be like shooting yourself in the foot.

Read [http://en.wikipedia.org/wiki/Paper_prototyping](http://en.wikipedia.org/wiki/Paper_prototyping) before offering advice like you know what are you talking about.

---

### Post by BwackNinja on 2008-07-12
Wow, this has also made me realize that I do absolutely no planning...ever. I don't even shell my code. Its a wonder that I can even magick my way through the problems I've made for myself. I make stuff work, then I make the code pretty :D

---

### Post by Lacrimstein on 2008-07-12
My flaws are that I never comment my code and use lots of unsafe shortcuts with pointers

---

### Post by descendency on 2008-07-13
My biggest flaw. . . program design.

I spend 90% of my time designing on the fly, which works ok since the applications I write are purely for myself. I think it does hurt in the long run though, because it takes time trying to rethink failed designs.

Honestly, the answer could be "everything" (I don't document, I don't pre-design, I don't code for readability, I don't code well with others, etc) but I'm sure I do something right. . . or I wouldn't have made it this long.

---

### Post by skeeterbug on 2008-07-13
> **descendency said:**
> My biggest flaw. . . program design.

I spend 90% of my time designing on the fly, which works ok since the applications I write are purely for myself. I think it does hurt in the long run though, because it takes time trying to rethink failed designs.

Honestly, the answer could be "everything" (I don't document, I don't pre-design, I don't code for readability, I don't code well with others, etc) but I'm sure I do something right. . . or I wouldn't have made it this long.

My friend tends to over design. I go with one design and start working on it (it can be adjusted in later versions). I have been at my current job three years now, he has not release his software yet, we are on version 3 now (two major products).

EDIT*
Our design goes through several reviews by myself (lead dev), product manager, owner, and the project manager.

---

### Post by boblemur on 2008-07-13
i neva comment my code.... i find my comments make it hard to read the actual code ( i guess thats the art of writing good comments though)

:P and if you get the module right... why do you need comments??

i dono if it would be a flaw :P but i write functions for even the tinys jobs... so my code is like heaps of lil programs...

also i tend to spend like hrs trying to work out the fastest way to impliment some tiny lil peice of code thats run once... and then dont get around to finishing the program itself

also my spelling kills me :D 90% of my syntax errors are cause i cant spell words like 'if' 'for' and 'while' :P :p

---

### Post by nvteighen on 2008-07-13
> **LaRoza said:**
> Hola! But I am not Latino ;) LaRoza for the Basque ;)


Agur!! Euskalduna zara?? :)

> **boblemur said:**
> i neva comment my code.... i find my comments make it hard to read the actual code ( i guess thats the art of writing good comments though)

:P and if you get the module right... why do you need comments??

I invite you to do this experiment: write some complex code without comments. Open it only one year later and see if you still understand it :p

Comments also help other people to read your code. You may know what's going on at a first glance, but someone else may not and, without any comment, he/she may never know what you are doing.

> i dono if it would be a flaw :P but i write functions for even the tinys jobs... so my code is like heaps of lil programs...

Not a flaw. It's actually the recommended way to do things; that way, your program are much easier to mantain and also extend. Repeat with me: "Everything should work as a library".

> also i tend to spend like hrs trying to work out the fastest way to impliment some tiny lil peice of code thats run once... and then dont get around to finishing the program itself

Don't be blinded by the power of execution speed!

---

### Post by CptPicard on 2008-07-13
> **nvteighen said:**
> Don't be blinded by the power of execution speed!

Speed kiddies always will... :( they think it makes their pointers bigger and as a plus, it allows them not to bother with all that nasty math and difficult algorithmics ;)

---

### Post by Mickeysofine1972 on 2008-07-13
> **pmasiar said:**
> It's a flawed thinking that client can understand what she signs in spec. You can wrestle her to paid for any changes after the specs are signed, but you will never get any repeat contract from her - and she will badmouth you as incompetent designer, and she will be 100% right.

Really? is that why I have repeat customers for over 10 years?


> **pmasiar said:**
> 
Paper design demo is exactly good because it is obvious that it is not program - it is just pages of paper, but you can test usability of your design without vomiting lost of bad code.

Oh PAPER!?!?!?! I wondered what on earth a pater design was LMAO! your old post now makes more sense.!

> **pmasiar said:**
> 
Of course unless you are such "expert" so you can defy  advice from people who get paid to train developers to design usable systems. You obviously never checked any article on useit.com, did you?

Oooooow thats sounds like flaming to me. Please see section 1 point number 1 of the Ubuntuforums.org CoC, "You obviously never checked any article on " the CoC " did you?"

Mike

---

### Post by LaRoza on 2008-07-13
> **Mickeysofine1972 said:**
> 
Oh PAPER!?!?!?! I wondered what on earth a pater design was LMAO! your old post now makes more sense.!
The really is no better way to get design ideas from customers. For web sites, it is so much easier to get and give pencil sketches of designs before coding.

---

### Post by pmasiar on 2008-07-13
> **Mickeysofine1972 said:**
> 
Oh PAPER!?!?!?! I wondered what on earth a pater design was LMAO! your old post now makes more sense.!

Sorry for the typo - but if you tried to understand instead of dismissing anything what I ever write, you could get a hint - I linked Paper Prototyping in wikipedia.

Loss is completely yours.

Have a nice day.

---

### Post by Mickeysofine1972 on 2008-07-14
I honestly did not connect pater with paper, i am truly sorry

Mike

---

