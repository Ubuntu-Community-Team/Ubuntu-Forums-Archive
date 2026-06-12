---
title: "Why the C Family?"
date: 2009-08-13
forum: Programming Talk
---

### Post by MuteClown on 2009-08-13
What makes the 'C family' (C,C++,C#,Java) so good?
Pretty much every programmer i talk to either doesn't know anything but programming languages fromt the 'C family' or never use anything else, Why is this? 
So what is so wrong with other languages like pascal or scheme, what makes people not choose these?

---

### Post by Mirge on 2009-08-13
Popularity plays a factor I'm sure. People wanting to get involved with existing projects can find themselves needing to use one of the mentioned languages to do so.

Other than that, I'm not really convinced that other languages are as under-used as you seem to be implying.

---

### Post by Can+~ on 2009-08-13
Obligatory read: [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html) (if you're on a hurry, jump to "The BLUB paradox")

If you read the text, you don't just "program" in a paradigm, you start thinking with the paradigm. People who is spoon-fed with C/C++/C#/Java at school (because these languages are popular) never think outside of that box.

---

### Post by MuteClown on 2009-08-13
> **Can+~ said:**
> Obligatory read: [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html) (if you're on a hurry, jump to "The BLUB paradox")

If you read the text, you don't just "program" in a paradigm, you start thinking with the paradigm. People who is spoon-fed with C/C++/C#/Java at school (because these languages are popular) never think outside of that box.

WOW, thank you!!
It was a really amazing read:KS

---

### Post by doas777 on 2009-08-13
most would refer to that as the pascal family, since C derived from it. 
that said, there is a lot to be said for uptake and consistency. if you are developing in java, and every other developer in your shop is working in C#, then there is a problem there, and it is likely you. every time you need a new interpreter, you increase administration overhead, and the cost of support for deployment.

---

### Post by Reiger on 2009-08-13
> **doas777 said:**
> most would refer to that as the pascal family, since C derived from it. 

I have heard of the Algol family. But Pascal family? That is new to me.

---

### Post by MuteClown on 2009-08-13
yeah, im pretty sure C and Pascal where derived from ALGOL not C from Pascal, and C was influenced also by B where Pascal stuck closer to ALGOL.

---

### Post by kieransimkin on 2009-08-13
I think the main reason people like C syntax is because it's basically a de-facto standard now... and there's nothing seriously wrong with it. When you know one thing and it works well for you, why change it just for the sake of it? (This is one of my main annoyances at Python is they've changed everything just for the sake of it; or, as it says in the documentation 'because Guido says it's best').

---

### Post by Mirge on 2009-08-13
> **kieransimkin said:**
> I think the main reason people like C syntax is because it's basically a de-facto standard now... and there's nothing seriously wrong with it. When you know one thing and it works well for you, why change it just for the sake of it? (This is one of my main annoyances at Python is they've changed everything just for the sake of it; or, as it says in the documentation 'because Guido says it's best').

:popcorn:

Gettin ready for it...

---

### Post by days_of_ruin on 2009-08-13
> **Can+~ said:**
> Obligatory read: [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html) (if you're on a hurry, jump to "The BLUB paradox")

If you read the text, you don't just "program" in a paradigm, you start thinking with the paradigm. People who is spoon-fed with C/C++/C#/Java at school (because these languages are popular) never think outside of that box.

> **kieransimkin said:**
> I think the main reason people like C syntax is because it's basically a de-facto standard now... and there's nothing seriously wrong with it. When you know one thing and it works well for you, why change it just for the sake of it? (This is one of my main annoyances at Python is they've changed everything just for the sake of it; or, as it says in the documentation 'because Guido says it's best').


...

---

### Post by JordyD on 2009-08-13
> **days_of_ruin said:**
> ...

Very true.

---

### Post by kieransimkin on 2009-08-13
Mmm I didn't mean to start a holy war, guess I've been out of the opensource community too long. 

Actually I did read the text, and I would agree that confining yourself to only learning one language is a bad thing (and let's just heap java, C, C++, PHP, ECMAScript etc all into one language). However, as someone who has tried various different boxes on for size, including most recently, Python.. I still prefer the C 'box' - I've been outside of it - into other boxes, and I just don't like them. This is coming from someone who has just started a company to develop a product almost entirely written in Python. That was the language that was chosen because it was the best fit to our product, I just don't like it, sorry. 

The approach I see in the essay is familiar to me - I see it as basically saying "my language is better than yours and the reason you don't see it is because you're stuck thinking the old-fashioned way". I don't think that's really true. I think that to learn to program you have to have an inquisitive mind and most programmers that I know at least are always open to learning new things. The fact that they may learn them and not like them is almost incompresensible to those who've already bought into the emperor's new clothes. 

I learned Python, and I use it, and I don't see what all the fuss is about. All the way through I was looking for my wings and I never found them. This isn't because I haven't fully grasped the language - believe me, I get it. Python is just another programming language, similar to pretty much every other language, it has some nice syntax but nothing really revolutionary and in some ways it's missing some features that I've become accustomed to in other languages. 

The point I'm really trying to make is that I think it's dangerous to believe that there is in some way a heirarchy of languages and that one is inherantly better than another. Because you may have discovered a new language and I may still prefer the one I've been using for a while - that doesn't mean your language is better than mine or that mine is better than yours - perhaps it just means that they're suited to different usage scenarios, or different mindsets. A cobbler doesn't fix shoes with a screwdriver and a network technician doesn't normally fix a network with a hammer. Just because someone has a different opinion to you doesn't make them wrong. In fact, you're probably both wrong.

Actually the thing that really put me off Python was this:
--------
**[4.1   Why does Python use indentation for grouping of statements?]("http://www.python.org/doc/faq/general/#id31")**

 Guido van Rossum believes that using indentation for grouping is extremely elegant and contributes a lot to the clarity of the average Python program.  Most people learn to love this feature after awhile.
---------

My first thought was 'who the hell is Guido and why do I care what he thinks?' and 'didn't we burn him at the stake for treason?'. 
That wording occurs a lot throughout the Python docs.. 'because guido thinks it's best', 'because guido says that'. Anyone would think he was the second coming ffs. I refer to him as 'the prophet guido'

---

### Post by Can+~ on 2009-08-14
> **kieransimkin said:**
> The approach I see in the essay is familiar to me - I see it as basically saying "my language is better than yours and the reason you don't see it is because you're stuck thinking the old-fashioned way". I don't think that's really true.

And it isn't true. Nowhere in the text specifies that a way of thinking is "old-fashioned", or that it's wrong. The whole point of the article is to state that "I can think in A, and only on A". And this is sad, the brain is capable of much more; you could suddenly see how things can be solved by another paradigm easily once you dominate many as there is no one correct way of doing things.

The point that days_of_ruin made by puting your comment next to that link was to show that, yes, you are inside a C-like box. And there's no such thing as a "de-facto standard" (which would translate more accurately [from latin]("http://en.wikipedia.org/wiki/De_facto") to "a convention", which, oddly, sounds less powerful now).

> **kieransimkin said:**
> I learned Python, and I use it, and I don't see what all the fuss is about. All the way through I was looking for my wings and I never found them. This isn't because I haven't fully grasped the language - believe me, I get it. Python is just another programming language, similar to pretty much every other language, it has some nice syntax but nothing really revolutionary and in some ways it's missing some features that I've become accustomed to in other languages.

That's because it doesn't enforce you to use the "other" things. I've seen people moving from C/C++ to Python and produce C-like code in Python. In fact, I've seen people moving from pretty much any language to another (except for completely different changes like C -> LISP) and drag their way of coding and replicate it into their new host.

It's a fine language indeed, but you only start appreciating the differences once you start venturing outside of the classic safe zone you impose. What happens if I return a function? (*gasp* a closure!?), what if I overload the [FONT="Courier New"]next[/FONT] method of a class? What if I try to add a method to an instance on runtime and then just try to call it? (duck typing)

The thing is that you don't realize that you've been inside a box until you're out of it. And I'm not saying that just by reading the pydoc will kick you out of it, in fact, it won't. You need to venture by yourself and try other languages that enforce you to think differently (Scheme and friends).

> Actually the thing that really put me off Python was this:
--------
**[4.1   Why does Python use indentation for grouping of statements?]("http://www.python.org/doc/faq/general/#id31")**

 Guido van Rossum believes that using indentation for grouping is extremely elegant and contributes a lot to the clarity of the average Python program.  Most people learn to love this feature after awhile.
---------

And right after that sentence (which, I will admit, sounds totally out of place) it's justified why it is that way and why they do it.

Really, as I said on the first quote-answer, there's no "one correct way of doing things", as everything in our field, everything has it's up and downs. How many times we need to say something like "Doing that, this way, will reduce the amount of ____ needed but at the cost of ____"? 

This is just one of that choices, and if you don't like it, well, I don't like how in Java you need to type [FONT="Courier New"]<type-class> variable = <class>();[/FONT] (disclaimer: the use of <> has nothing to do with [Generics]("http://en.wikipedia.org/wiki/Generics_in_Java")), because it's totally redundant, but I just go with it, as it's how the language is.

Btw, there's an interesting read on this (uploaded to my dropbox):
[http://dl.getdropbox.com/u/850314/programming_paradigms.pdf](http://dl.getdropbox.com/u/850314/programming_paradigms.pdf)

(Why I'm posting it: Because it shows how being able to think different yields better results).

---

### Post by Wim Sturkenboom on 2009-08-14
> **MuteClown said:**
> What makes the 'C family' (C,C++,C#,Java) so good?
Pretty much every programmer i talk to either doesn't know anything but programming languages fromt the 'C family' or never use anything else, Why is this? 
So what is so wrong with other languages like pascal or scheme, what makes people not choose these?
First of all, the main advantage of C (not its derivates). It's the **most universal language** as it's available for about every processor/microcontroller in the world from e.g. the small Microchip PIC family with 1k code memory and 128 bytes of data memory to PCs with GB's of memory to mainframes etc. That is for me what makes C so good.

Next is that, what you call the 'C family', is basically tought in secondary and/or tertiary education. So if that can do the job, why learn another language. One needs a good motivation to change.

---

### Post by CptPicard on 2009-08-14
+1 Can... I so want to post but I am in hospital with broken leg and have just a phone for surfing. How annoying :D

---

### Post by nvteighen on 2009-08-14
This is a really interesting discussion to see from my always-annoying-for-programmers "linguistic watchtower"... A good excuse to discuss language evolution and other stuff :D

FORTRAN influenced ALGOL; ALGOL begat CPL; CPL begat BCPL at AT&T/Bell labs; BCPL begat B; B begat NB, which later was to be known as AT&T C. And AT&T C wrote UNIX and hence it grew up in knowledge and strength, becoming years later the language known as K&R C, from which ANSI C was born. :) (ph34r, writers of the Book of Mozilla!)

Ok, that (bad) King James's Bible-style paragraph hints something you guys are all forgetting about C. C was created almost by accident and by trial-and-error during the development of UNIX. It was a language that was designed at the very same time the OS, so there was mutual contribution between both projects. C got its features and design from the empirical experimentation and experience of the needs for programming an operating system. C was created from a *real project* and not from an abstracted thought on "what a system programming language should look like" (like, e.g., C++). The result of this is quite obvious: C is just a perfect (if not the best) language for system programming. (Besides note: A similar story occured with Objective-C, which was created during NeXTStep's development... Try it and you'll see what I mean).

That's why C became a standard and a model to follow. Ok, all of us know C's limitations, but it became a model. And so people started to modify it... The problem is that they pushed the model beyond its scope and began to apply it to places in which C is not a model, e.g. high-level programming. Best example: Java. They took C's model (maybe actually indirectly by passing through C++) and pushed it to a place where it doesn't work well. But the (true) feeling that C is a model is that strong that language designers seem to prefer to "stick to the model" instead of saying "ok, we've got this great language... let's use it as a reference alongside others". Best example of this... Perl. 

Yes, Perl. It uses C as one of its effective models and not the only one: you've got awk, sed, C, etc. and a conceptual twist about programming (the morpho-semantic "paradigm"; form and context as the keys to interpret words)... sadly, at the cost of readability... But it's a good example on how they took C as a model, but complementing its failures for high-level tasks with other models.

But again, I think it's C's history which has determined this situation. Sadly, Lisp hadn't had this evolution; in that case, nobody would be nowadays saying that Lisp is weird and it has too much parentheses. Or take Forth... We're that used to C and C++ being "the" system languages, that we forget Forth exists.

Yup, "used to"... Languages are all the same (in the case of programming languages this is only true if they're Turing-complete), but subject to human perception. I'm a native Spanish speaker, fluent in several Indoeuropean languages... but give me Chinese or Swahili and I'll certainly, inconsciously, classify it as "weird". And actually, none of those are weird, but we humans certainly are :D

---

### Post by Copernicus1234 on 2009-08-14
> **Can+~ said:**
> Obligatory read: [http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html) (if you're on a hurry, jump to "The BLUB paradox")

If you read the text, you don't just "program" in a paradigm, you start thinking with the paradigm. People who is spoon-fed with C/C++/C#/Java at school (because these languages are popular) never think outside of that box.

I agree. Ive found that since exploring python and javascript, my programming has improved _significantly_ compared to what Ive learned in the university (mostly C and Java).

Also I dont see the point of reinventing the wheel all the time as you do with C. Its good for low level stuff where you need custom code, but today its better to use a high level tool for basically almost everything. At least in my field of work. Perhaps if you are programming micro circuits, things will be different. :)

> **Wim Sturkenboom said:**
> 
Next is that, what you call the 'C family', is basically tought in secondary and/or tertiary education. So if that can do the job, why learn another language. One needs a good motivation to change.

Because you become a better programmer in C if you are good at several other languages as well.

---

### Post by SunSpyda on 2009-08-14
Actually, for my eyes, Lisp and Python have the nicest syntax. With python, there isn't (much) unnecessary syntax. It reads like a well structured, strict pseudo code. Just enough syntax to know what it's doing.

And Lisp, I can see what the code is doing, and there aren't pitfalls or bizarre syntactical exceptions or precedence order. The parentheses make a intention of the code very clear, and I like that. Very simple rules.

Also, I really like Lisp's consistency and simplicity. And Python's for that matter as well. When I say Lisp, I'm referring to CL and Scheme.

But, I code in C languages far, far more than either of them two (It may change as I embrace Python more). Yes, C syntax has a minefield of syntactical screwups that aren't with Lisp or Python, and yes, it contains a lot of syntactical garbage that doesn't serve much use in modern day contexts. But I use it for the sole reason that *it's the standard*.

As it stands, the C syntax is my "programming mother tongue" (C++ was my first language), but I can still, even with rubbish knowledge of Lisp and Python, quite often, read Lisp and Python better! (Standard libraries notwithstanding - I'm talking about program structure here.)

When I use new languages, I go by their way, not the way I have been using on other languages. I seem to be able to code better in *all* my languages when I do this. I like to keep a reasonable knowledge of a wildly different range of wacky languages, as I usually can code overall better when I do this.

EDIT - I'm one of the only people I know who *wants* python style indenting in C! It ain't gonna happen though. Also, If I were to reinvent C, I would strip those ; out. EOL should be enough, unless you are using multiple statements on one line.

*ANTI-C-USERS FLAME SHEILD ON*

---

### Post by myrtle1908 on 2009-08-14
> **SunSpyda said:**
> If I were to reinvent C, I would strip those ; out. EOL should be enough, unless you are using multiple statements on one line.

Dear god no.  I would waste so much time re-training my fingers ;)  I would hit backspace more than any other key!

---

### Post by Cyanidepoison on 2009-08-14
> **myrtle1908 said:**
> Dear god no.  I would waste so much time re-training my fingers ;)  I would hit backspace more than any other key!
This is so true.  I do it all the time when I'm using Python.

---

### Post by soltanis on 2009-08-14
> **CptPicard said:**
> +1 Can... I so want to post but I am in hospital with broken leg and have just a phone for surfing. How annoying :D

T Picard, it's okay, I just got out of the hospital with a broken jaw. Sounds like everyone is having a fun time all around (and the pain meds are still making my head spin).

Anyway, why is C so popular, or its spawn so popular? Probably because in the beginning, ALGOL was popular. When C came along, it had some pretty similar syntax, and people just happened to jump on that bandwagon. The fact that UNIX was rewritten in it and distributed in an open fashion probably really helped with C's uptake, since to hack at the UNIX codebase you would've had to know C.

Plus C itself was a language that by virtue of a vague specification could basically be implemented on any sort of machine, important, considering that back then there was a huge variety in machine architectures and implementations. Consider reading an article online about a guy who built his own computer, managed to port a C compiler to it, and just like that (well, mostly) got the thing to run Minix with a TCP/IP stack. That's what C portability means.

The other languages earn popularity points just by being spin-offs of C.

To be honest, I see nothing too particularly wrong with favoring C syntax (honestly it's easier for me that way when I'm learning a new language to not have to deal with what Guido or whoever thinks is the best way for me to program by just jumping into familiar formatting and styles), except in cases where it's truly unnecessary -- and so far only one language has really convinced me of this, and that would be Lisp (& friends).

---

### Post by days_of_ruin on 2009-08-14
> **kieransimkin said:**
> 
My first thought was 'who the hell is Guido and why do I care what he thinks?' and 'didn't we burn him at the stake for treason?'. 
That wording occurs a lot throughout the Python docs.. 'because guido thinks it's best', 'because guido says that'. Anyone would think he was the second coming ffs. I refer to him as 'the prophet guido'

Every language does has conventions that are there because the language creator likes it that way, at least the python docs are honest. I think Guido wrote a lot of the docs so it's probably just tongue-in-cheek.

[COLOR="Green"][SIZE="7"]LIGHTEN UP![/SIZE][/COLOR]

---

### Post by MuteClown on 2009-08-15
I kinda see that Lisp got overlooked due to people just sticking with similar languages ALGOL then C then (insert C derivative here). But if people started to use C because its like ALGOL what about Pascal? Pascal and ALGOL seem to have more in common than ALGOL and C. I know Pascal is probably in more use via Delphi in windows than Lisp, but yet i haven't seen many Pascal programmers.

---

