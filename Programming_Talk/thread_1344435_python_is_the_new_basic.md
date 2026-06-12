---
title: "python is the new basic"
date: 2009-12-02
forum: Programming Talk
---

### Post by openuniverse on 2009-12-02
.

---

### Post by Can+~ on 2009-12-03
Python is sure a game changer in terms of the other languages out there. It may not be the fastest language, it may have some discrepancies here and there (namespacing is kinda awkward), but it's syntax is crystal clear, and the library support is fantastic, the [standard library is already huge]("http://docs.python.org/library/index.html"), and portable.

In fact, the thing I appreciate in python, is that it was the first language that introduced me to the functional paradigm. I never understood the big point of it with Lisp or Haskell, until I tried python's "hybrid" approach.

---

### Post by CptPicard on 2009-12-03
I'll forgive the BASIC comparison, but otherwise the sentiments are very much correct IMO ;)

Python is awesome because of the design elegance. It's "orthogonal" and generic, meaning that the design elements work right and make sense when combined with other design elements. That is, there are no weird exceptions and gotchas when doing some particular combination of functionality.

This is a result of there being an economical number of core concepts, which are thought out "right" from the beginning. Languages that have conceptual mismatches in their design tend to end up as a humongous collection of special cases and tricks. But when things just work right even in surprising directions, it is very pleasant.

Python also demonstrates a very nice integration of all kinds of advanced programming language design concepts such as closures, map/filter/reduce kind of data manipulation without being tough to grasp for a beginner. In particular for a learner, it is interesting to consider that Python trivially contains a language like C (that is, basic control structures) without one having to resort to a debugger at error, while seamlessly integrating and scaling up to OOP, FP, so on... it is all in the integration of ideas.

---

### Post by openuniverse on 2009-12-03
.

---

### Post by nvteighen on 2009-12-03
You're quite right. Of course Python is much more powerful than BASIC because of many features, but essentially Python has taken over that same niche BASIC had before: being a suitable first language. Ok, BASIC was not even near to be a good programming language, but some implementations did a special effort to make it a bit better and introduced functions and structured programming constructs... It still lacked a decent environment and system interface (well, QBASIC had the CALL ABSOLUTE/CALL INTERRUPT thing...). and worse, it was a non-standarized language.

But of course Python is a much more mature language, with a well-planed design and much better primitives.

---

### Post by openuniverse on 2009-12-03
.

---

### Post by nvteighen on 2009-12-04
> **openuniverse said:**
> well, i won't rush to basic's defense on any of that, because everything you said is true in some context, but be careful before you end up in an argument with someone (else) prepared to defend basic. they've been trashing it for years and frankly a lot of the arguments against it (especially dijkstra's) are outdated. my problem with basic is that i really think there are too many people (creating new dialects) who sort of understand what basic is, but only a little about why it was great.

python (2.5+.x and 3+) strikes a good balance between standards, core concepts, and progress, balance you won't find in 95% of newer basic dialects- which are a mess. most of them look like basic-plus-author's-favorite-langauge combined higgledy piggledy. i'm not a purist, but languages if combined, should be combined with care and good knowledge of the benefits of each. python does that, modern basic rarely does. i'm glad more than one person got my original point though, and even said it better. basic filled a niche i care about a great deal, which python is filling outstandingly.

BASIC's greatness was its simplicity, but it was born as a terribly outdated language. A language that in the 1960s didn't support structured programming was already behind FORTRAN II or Lisp, both from the 50s. The thing is that there was a great "2nd generation BASICs" which adopted these features and became really usable languages. Another completely different thing is that it was true that most BASIC programmers were terribly bad and didn't even care to use those features, leading to really bad code.

But I can assure that code written in QuickBASIC with subroutines/functions, no GOTOs and even C-like OOP (create a data structure and functions associated to it) was quite feasable.

In some way, all languages aiming to beginners take the risk of suffering misreputation because of their own newbie coders. The more bad code you see written in language X, the easier it is to blame it to the language. I see the "Python is a toy language" critique as one of these cases; also the "Perl is unreadable" could be considered this way too.

Visual Basic pre-.NET was terribly wrong. It had to create lots of weird constructs on top of QuickBASIC in order to keep being BASIC-alike (?) and still support the complex WinAPI. Its OOP was pretty limited, the way code was organized by the IDE... everything was quite wrong and lead to the really bad habit of coding just to make a UI work (a really bad interpretation of what "top-down" programming is).

---

### Post by openuniverse on 2009-12-04
.

---

### Post by lisati on 2009-12-04
> **nvteighen said:**
> B.. everything was quite wrong and lead to the really bad habit of coding just to make a UI work (a really bad interpretation of what "top-down" programming is).

+1. Why should I be forced to focus on the UI when it's only PART of the overall process?

---

### Post by grayrainbow on 2009-12-04
> **lisati said:**
> +1. Why should I be forced to focus on the UI when it's only PART of the overall process?
Given relatively similar working part, UI is what actually matter and will have most part of the users choice.

Anyway, nice ease from OP :) I just have the feeling that what make BASIC BASIC somewhere slipper outside of OP mind during writing it ;) In order to get good view to some language one should look it "from outside", which generally mean that one need good experience at least in C, Lua, Scheme, and forget for all his/her feeling to the language been reviewed(generally just like Linux distro review).

---

### Post by openuniverse on 2009-12-04
.

---

### Post by grayrainbow on 2009-12-05
> **openuniverse said:**
> no, it only looks like i just said a lot of things about python because i did; i was talking pretty much exclusively about the aspects of python that remind me of basic. there's a lot of terrible oop implementations in modern basic dialects, so that was about basic too. but then as the title suggests, it really is about python. (and how it compares to basic.) i just stopped being explicit about it very quickly.

i'm sure that's good advice. i got a book on c and tried to learn it for a while, i just can't stand lua and i've been toying with the idea of scheme, actually. well, actually i found an interesting book on lisp a month ago and i've always been very curious about the language, i was looking at guile and gnu robots today. (i'd rather use a scheme interpreter, but i wondered if there's a simple interface for guile.) 

i don't think you need all these languages to appreciate basic though. the idea of using what you like to use may be overrated by a few people, but it seems to be underrated by even more. i always tell people "learn python." if they say "blah blah blah whitespace" i say "oh, it's really not so bad" but i don't twist their arm because hey- people will use what they like. and why the heck not? unless they must for something.
Hmm, probably there are some good OO BASIC implementations, but OOP in BASIC is just not my taste, you are in same position as well.
To be more explicit then previous time - you should remember that BASIC is actually quite old, and should remember it's history, how and why it evolves, and you'll probably won't going to compare it to python after that :)

I've just gave "simplest" examples of different kind of language(couse that what one need to use a bit if one is interested in language comparisons). Well, Lua is maybe not in "simplest" group couse it's also functional, with proper tail calls, and with good mechanism for programmer to build object system himself/herself. But if one doesn't like it, one could learn some(or two) other language/s instead(if one going to learn a lot of languages).

---

### Post by openuniverse on 2009-12-05
.

---

### Post by nvteighen on 2009-12-05
> **openuniverse said:**
> 
python meets all of those guidelines, just as well as any classic version of basic. most modern basics do for about 5 minutes and then become a mess.

I'm looking at you VB6...

---

### Post by grayrainbow on 2009-12-05
> **openuniverse said:**
> in general, if i could compare modern basic to python, i wouldn't need a "new basic." i'd just use basic. there are very few really good implementations of basic in my opinion, most are hackish chimera's thrown together by madmen, which is why the oop in basic is so bad. i consider these things to define basic pretty well:

[LIST=1]
[*]Be easy for beginners to use.
[*]Be a [general-purpose programming language]("http://en.wikipedia.org/wiki/General-purpose_programming_language").
[*]Allow advanced features to be added for experts (while keeping the language simple for beginners).
[*]Be [interactive]("http://en.wikipedia.org/wiki/Interactive").
[*]Provide clear and friendly [error messages]("http://en.wikipedia.org/wiki/Error_message").
[*]Respond quickly for small programs.
[*]Not to require an understanding of computer hardware.
[*]Shield the user from the operating system.
[/LIST]
python meets all of those guidelines, just as well as any classic version of basic. most modern basics do for about 5 minutes and then become a mess.

but as to how long it's been around, python isn't exactly a spring chicken- it's merely up to date. c (1972) isn't much younger than basic (1964, but widespread by 
70's.) i'd rather use something that's been around for a decade anyway. anyway, there's nothing i needed basic for that i can't do almost or more easily with python- it's my new basic. i'd love to say that about freepascal or something, but python does beautifully.
What you mean with "Easy for beginners"? Are you aware of logo programming language? For most people Microsoft BASIC and Turbo BASIC were light years ahead of logo on easy of use(python is not in this category at all), and presenting programming to people, both languages also have different approach to their goal. That's make BASIC one of the big thing in "PC revolution". Then as I sad, now in bit different form - big programs in BASIC is not my taste.

P.S. One little clarification: IMHO if one is more than 15 years old, logo probably won't be the starting point, but it could be more of an interest from language design point of view.

---

### Post by openuniverse on 2009-12-05
.

---

### Post by grayrainbow on 2009-12-05
> **openuniverse said:**
> very: [http://activities.sugarlabs.org/en-US/sugar/addon/4027](http://activities.sugarlabs.org/en-US/sugar/addon/4027)

and here's the activity that introduced me to python: [http://activities.sugarlabs.org/en-US/sugar/addon/4041](http://activities.sugarlabs.org/en-US/sugar/addon/4041) although i prefer the console. 

i don't get the idea that python is much different than basic in terms of easy for beginners. the main difference between qbasic and pygame for me is that i haven't spent much time with pygame yet. the examples in pippy are most inviting. i think a child would have an easier time with pygame than using get and put to move sprites in qb or gw-basic. edit: read the bottom of this: [http://inventwithpython.com/](http://inventwithpython.com/) just linked to in another thread.
Quite a good links(considering the subject of the thread), plus I now understand little bit why you find "knowing hardware" so hard, apart from that as general different people are skilled in different fields. You may be interested to make little research what algorithm means.

P.S. What make logo suitable for kids is that it's actually design for that purpose, and as such have few stuff that are considered as bad thing in production languages.

---

### Post by openuniverse on 2009-12-05
.

---

### Post by grayrainbow on 2009-12-06
[http://en.wikipedia.org/wiki/BASIC]("http://en.wikipedia.org/wiki/BASIC") it's design for easy of use.
I wouldn't emphasize on easier of code, but more on easier of learn concepts, which usually mean - simpler is better(you know, don't put cart before the horse, first learn what's program, and after that what's program structure, abstraction, etc). In some very high level point of view assembly is not much different than BASIC.

---

### Post by Greyed on 2009-12-06
I was never really a fan of BASIC.  I got out of it prior to QBASIC really taking off.  I preferred Turbo Pascal at the time even though my brain was (and in some ways still is) resistant to the concept of data types.

For me what makes Python a suitable language for learning, whether one is a neophyte or old(er) hand at programming is the fact that I think it is fun to play in the language.  The interactivity coupled with introspection, clean syntax and concepts means that one is faced with unfamiliar territory one can learn by playing.  Open another window, twiddle with the concept, flip it around, poke at it with introspection, make a toy that solidifies the concept in your mind then slap that into the project at hand.

Python somehow enables that sense of joy and play in learning more than I found in any language I used before (BASIC, Turbo Pascal, 4DOS, 4OS/2, C, Perl) and after (PHP, Ruby, C (again)) Python.  Maybe it is a limitation of my mind but when I play in Python I feel that I am fighting *my limitations* and *my misconceptions* of how to do something instead of fighting *the languages limitations.*

---

### Post by openuniverse on 2009-12-06
.

---

### Post by Greyed on 2009-12-06
> **openuniverse said:**
> when i'm using a relatively easy language i feel like i'm playing with legos. not that this is necessarily the best paradigm for coding because legos are redundant... if i'm coding properly i'm not going to have 5 of the same lego, i'm going to have 5 different legos connect around to the same...

No, actually, legos are a great analogy for programming.  Anything you build out of legos are built out of small, discrete units.  The very uniformity and interchangeability of certain pieces is what makes them so adept at building complex and detailed 3-D representations of almost anything one can imagine.

This sounds paradoxical at first.  But think not of each block as a line of code but an execution of a function.  The design of the function doesn't change, nor does the shape of the lego block.  The interface doesn't change for either function or block.  But combining just a few basic functions/blocks in more complex designs and patterns results in new and interesting things.

To take that analogy further, C is like having a block of wood and a carving knife.  Sure you can make the blocks and then, from those blocks, form the same overall structure but who wants to whittle out the block first when you can just get a package of them from over there.  ;)

---

### Post by wmcbrine on 2009-12-06
> **openuniverse said:**
> there's nothing i wrote in basic before age 12 that isn't easier to code in python- except changing text colors in the term, which requires ansi escape sequences. however if you can do color fg, bg then print "\x1b[1;34;45m" is not insurmountable.There's always the "curses" module. It's still kind of a PITA, but perhaps easier than escape sequences.

BTW, I agree with your original post. Although I moved on from BASIC long ago, I'd been worried that there was no suitable modern replacement for the role it filled. Now I think there might be. I tell ya, it gives me hope for the future.

---

### Post by openuniverse on 2009-12-07
.

---

### Post by nvteighen on 2009-12-07
> **openuniverse said:**
> the curses lib is great. no idea why there's no windows port. why have a different lib for doing the same thing in windows? hurting the cross platform. interesting to note however that pythond (which is nicer in windows xp than it is in dosbox) has it so i think you can run python/curses scripts in windows that way.

Well... The CURSES standard is designed to work with UNIX/Unix-like terminals that support termios character manipulation... The MS-DOS/Windows shell is proprietary, so we don't know how it works...

NOTE: Don't use termios... it's too low-level... For the majority of cases ncurses is all you need.

---

### Post by openuniverse on 2009-12-07
.

---

