---
title: "Javascript is hard to appreciate..."
date: 2011-09-18
forum: Programming Talk
---

### Post by pelle.k on 2011-09-18
I'm not a javascript guru, so perhaps i'm just looking at it wrong, but to me at least, it doesn't seem like a very nice language.
Coming from a pyhton/ruby background, i can't for the life of me understand why they chose javascript to be the engine that fuels client side scripting in web browsers. It would seem javascript is the standard though, and likely to be so for a foreseeable future.

Creating classes, and inheritance patters in javascript seem "half-baked" to me. You browse the internet for best practises, and there seems to be none really. People come up with boiler-plate code to do proper object inheritance (and other stuff we take mostly for granted in python/ruby) and such, but that seems strange to me. Shouldn't these things be built into the core language? Or is it that a prototype based languages (haven't studied it enough yet) isn't supposed to work like a classical oo language. Perhaps i'm doing it wrong?

Your thoughts on the matter, please?

---

### Post by N1GHTS on 2011-09-18
[Apples and Bananas.]("http://www.youtube.com/watch?v=N_QybpPmGRc")

That's the song that came to mind when I read your question. Ruby and Python is not Javascript. Yes, they are programming languages, and yes, Javascript was conceived after the advent of the other languages, but they are built for different things. 

Javascript was a Netscape invention allowing boring HTML pages able to do fancy things. It was made on purpose to be weakly typed, multi-paradigm, and dynamic. It was made to be simple, flexible, and designed to let little kids make web code that doesn't break people's computers by creating bad code.

It was a great strategy at the time, and still makes sense today, to let client-side web programming be easy so the internet can be accessible to all. "Grandpa made an internet's page!"

Since the early days of the web, web browsers have grown in size and complexity. The more people expect from websites, the more is added to the browsers to facilitate it. I remember a time when creating a web browser from scratch was actually easy and highly compatible with the web (I made one). Those times have changed. 

Javascript is the established standard for better or worse. Adding an option for other languages forces all browsers to add support for it, and inevitably increases the size of the browsers, making working with the web even more bloated than it is today. Not to mention the compatibility crisis that would also inevitably ensue.

So its not to say that Ruby or Python can't be used to replace Javascript, but they are made for [very different audiences]("http://www.lissaexplains.com/javascript.shtml"), and [its too late to change]("http://www.worldwidewebsize.com/").

:)

---

### Post by Paddy Landau on 2011-09-18
You betray your youth :)

There is no such thing as a "classical" OO language. OO programming is the new kid on the block.

Javascript began before OO was as popular as it is now.

---

### Post by Off Shore on 2011-09-18
Scripting is one of those things which, at least in the academic world, we seem a little embarrassed to talk about.

Java Script, as the last poster mentioned, was available at a time when OO script languages were just not available. It does rather a good job in my opinion and is a fairly gentle learning curve for people to acquire.

The Object Oriented paradigm, itself, has been with us since the 1970s. Messrs Kay, Ingalls and Goldberg were amongst the pioneers at Xerox Parc labs.
SmallTalk was the first tangible result of their work and it still remains unbeatable, in my opinion, for the purpose of teaching OO principles.

However, SmallTalk stayed in the academic domain, with people such as I,  for many years because it was so resource hungry it wasnt ready for Commercial uptake.

OO was and is a jolly good idea, years ahead of its time, but had to wait until such time as hardware was able to accomodate its demand for resources before it became viable for affordable commercial use.

Then and only then, the wonderful range of OO languages and frameworks burst on to a waiting world !

The majority of educational establishments teach java script and, if you are struggling, take a look at your local college of further education.Id be very surprised if you cant find a short course.

I hope you find this a little helpful. I am always surprised and impressed by the quality of the young people who post and ask questions on these forums.

---

### Post by ve4cib on 2011-09-18
> **pelle.k said:**
> I'm not a javascript guru, so perhaps i'm just looking at it wrong, but to me at least, it doesn't seem like a very nice language.
Coming from a pyhton/ruby background, i can't for the life of me understand why they chose javascript to be the engine that fuels client side scripting in web browsers. It would seem javascript is the standard though, and likely to be so for a foreseeable future.

Creating classes, and inheritance patters in javascript seem "half-baked" to me. You browse the internet for best practises, and there seems to be none really. People come up with boiler-plate code to do proper object inheritance (and other stuff we take mostly for granted in python/ruby) and such, but that seems strange to me. Shouldn't these things be built into the core language? Or is it that a prototype based languages (haven't studied it enough yet) isn't supposed to work like a classical oo language. Perhaps i'm doing it wrong?

Your thoughts on the matter, please?

Javascript was, originally anyway, a functional language like LISP or Scheme.  Much of the more recent, "classical" inheritance that is doable in Javascript does feel hacky if you've grown up programming in nothing but C++ and Java.  But Javascript is a different language and does things differently.  Expecting it to be the same as other languages is naive at best.

Personally I like Javascript.  It's fast, it's fun, and there is LOTS of support and examples for it.  However, unlike most programming languages one could name (C, C++, C#, Java, Python, ...), Javascript is NOT the exclusive domain of programmers who have knowledge and experience of "best practices."  Javascript, because of its close ties to the web, is often used by professionals like web designers who often have more training on how to use Photoshop and design fonts than programming.  But they are expected to use JS plugins to make the sites they design look prettier, but lack the in-depth training that most programmers would receive in this matter.  This leads to a lot of messy examples online.

And to make matters even worse, programmers (possibly like yourself) approach Javascript expecting it to be exactly the same as other languages they've used, and therefore don't bother learning *why* Javascript does this differently.  Creating classes is a largely foreign concept to a prototypical language, but most universities and colleges don't teach programmers how to use a functional/prototypical language like Javascript.  The attitude seems to be "Javascript is easy; you can pick that up on your own."  This is unfortunate, because it leads to confusion on the part of under-educated programmers, frustration on the part of experienced JS programmers, and conflicting information being delivered to non-programmers who need to use JS snippets in their work.

---

### Post by pelle.k on 2011-09-18
Thankyou everyone!

> **ve4cib said:**
> Javascript was, originally anyway, a functional language like LISP or Scheme.  Much of the more recent, "classical" inheritance that is doable in Javascript does feel hacky if you've grown up programming in nothing but C++ and Java.  But Javascript is a different language and does things differently.  Expecting it to be the same as other languages is naive at best
Yes, perhaps i'm a bit naive. But that's why i'm asking. People don't bring this issue up very much on the internet. They seem to think it's better to argue on how to fit a square peg in a round hole (i.e. how to do oo in javascript, when it seems it wasn't built for it).

> **ve4cib said:**
> And to make matters even worse, programmers (possibly like yourself) approach Javascript expecting it to be exactly the same as other languages they've used, and therefore don't bother learning *why* Javascript does this differently.  Creating classes is a largely foreign concept to a prototypical language, but most universities and colleges don't teach programmers how to use a functional/prototypical language like Javascript.
Well, initially, i thought i should just give it time, then perhaps oo in javascript would seem as natural to me as in ruby/python, but then i came up with the bright idea to ask you people about it. It would seem it was a good idea indeed.
So i'm doing it wrong, i presume? I will take the time and read up on functional programming, and prototypes then. Perhaps javascript makes more sense when you do?
Thanks! :)

---

### Post by scitron on 2011-09-18
[URL="http://javascript.crockford.com/javascript.html"][SIZE=2]JavaScript:
The World's Most Misunderstood Programming Language[/SIZE][/URL]


Some interesting ideas on Javascript.

---

### Post by Dimarchi on 2011-09-19
The link scitron provides is mandatory reading about Javascript. :)

Doing it wrong? I would not go that far. Java is Java, C++ is C++, and Javascript is Javascript. All languages do things in their own way, and with our experience in other languages we grow to appreciate some things the way they do them, and abhor others. That then extends to other languages and we can not fathom why x is not done the way y does it, or why x could not be more like y, since it resembles it so much or something to that effect.

In the end, accept the way things are done, whatever the language in question. It is both maddening and fun. :)

Disclaimer: web developer attending C/C++/QT/Linux/Android programming course.

---

### Post by in·ter·punct on 2011-09-19
> **pelle.k said:**
> I'm not a javascript guru, so perhaps i'm just looking at it wrong, but to me at least, it doesn't seem like a very nice language.
Coming from a pyhton/ruby background, i can't for the life of me understand why they chose javascript to be the engine that fuels client side scripting in web browsers. It would seem javascript is the standard though, and likely to be so for a foreseeable future.

I'm not knowledgeable on the subject of programming, but JavaScript was created in a couple of weeks by one man. Which is pretty good, right? On the subject of creating, Google wants to replace JavaScript with a new web programming language called Dart developed by them. They'll be introducing it in October.

---

### Post by juancarlospaco on 2011-09-19
> **pelle.k said:**
> 
Coming from a pyhton/ruby background, 

Your thoughts on the matter, please?

Then [this is for you]("http://jashkenas.github.com/coffee-script/"), JS more Python-like

---

### Post by pelle.k on 2011-09-19
If people wonder why i'm so picky about the language and it's features, then it's because i'm looking at rewriting an application (written in pyhton and pyqt) of mine in pure javascript and html5. Mainly for fun, but it also seems javascript and html5 is where the future is taking us, so i may just as well learn it right now.
If it was just a little DOM manipulation in some web page we were talking about, i might not be so hesitant, but when writing anything over 100 LOC, i want to know the language better.

> **juancarlospaco said:**
> Then [this is for you]("http://jashkenas.github.com/coffee-script/"), JS more Python-like

Hmmm. Interesting! Initially, i was looking at javascript compilers such as pyjamas, but apparently you can't use 3rd party js libraries like jquery then.
I prefer using the "real thing" if possible. We shall see what people have to say about coffescript.

Seriously though, it would be nice if all browsers had a VM instead, so that people could just drop in compiled byte code for languages that supported this VM, instead of supporting just this one language (javascript).

---

### Post by juancarlospaco on 2011-09-19
Such thing exist, google for HTML5 Native Client, anyways no Python bindings (yet?)

You can write the app on Python, and use HTML5 for the GUI, i use that.

---

### Post by Dimarchi on 2011-09-20
Server side, you can code in just about any language you like...client side...well, N1GHTS already told us everything we need to know. If that Native Client will be anything like Java VM, no thanks. That has left me a bad taste about VMs in general. A personal issue here. :)

---

### Post by pelle.k on 2011-09-20
> **juancarlospaco said:**
> You can write the app on Python, and use HTML5 for the GUI, i use that.

Hmm! Again, interesting. How do you achive that? I've looked into using PyQt4 and a webkit view for the GUI, manipulating the DOM via python. Also, i noticed pywebkitgtk is aiming to supply a webkit view with python support for client side scripting.

In the end though, i'll probably go with javascript, but it's nice to see alternatives forming on the horizon!

---

### Post by CptPicard on 2011-09-20
Crockford's "Javascript: The Best Parts" is also mandatory reading for those who want to understand what is good in the language and how to make use of that to avoid what is bad.

Javascript has some remarkably awful design decisions in it (just think of the scoping of "this"); fortunately, those can be offset by the really fortunate things such as functions as first class values, closures, the fairly flexible and simple object model and, yes, the prototypal inheritance once grasped for what it is. 

The ability to use Javascript much, much better in a conceptual sense by understanding for example the relationship between functional and object-oriented programming is one of the reasons why, mind you, I've always been a big proponent of higher-level languages ... they teach you useful ideas you wouldn't get from lower-level languages.

---

### Post by nvteighen on 2011-09-20
> **Paddy Landau said:**
> You betray your youth :)

There is no such thing as a "classical" OO language. OO programming is the new kid on the block.

Javascript began before OO was as popular as it is now.

Sure. OOP existed since we had data structures to which we semantically associate some behaivor... And we've been doing this since Lisp or any programming language that supports some aggregate-type mechanism... In C, that'd be struct... In Lisp, regular cons'ing... In C++, class, etc. What may be new is syntactic support for these things, but that's completely irrelevant.

About the topic:

I'm not very Javascript savvy, but IIRC, Javascript earns its bad reputation from the fact that it was overused and badly used by people with no programming experience in something as critical as web pages. It's critical because web browsing is possibly the most important usage of computers nowadays and people need sites that work... and those newbies' pages tended to not work.

But the language does have a couple of interesting features people have learned about... For example, the fact that you can use Javascript outside the browser or its functional programming features.

---

### Post by juancarlospaco on 2011-09-20
> **pelle.k said:**
> Hmm! Again, interesting. How do you achive that? I've looked into using PyQt4 and a webkit view for the GUI, manipulating the DOM via python. Also, i noticed pywebkitgtk is aiming to supply a webkit view with python support for client side scripting.

In the end though, i'll probably go with javascript, but it's nice to see alternatives forming on the horizon!

I use [http://bottlepy.org](http://bottlepy.org) and HTML5, HTML5 itself got Off-Line feature,
if i need to include an additional/optional window to display the app i use 
[http://code.google.com/p/devicenzo/](http://code.google.com/p/devicenzo/)  :)

---

