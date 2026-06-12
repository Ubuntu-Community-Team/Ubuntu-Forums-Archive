---
title: "questions and concerns"
date: 2009-12-27
forum: Programming Talk
---

### Post by ivh90 on 2009-12-27
hello there 

I am a second year  computer engineering student and i have been using ubuntu for about 2 years now ... and I like it a lot.

I took programming courses in both C and java which have similar syntax, 
and i am thinking about learning Python ... but i have some questions and concerns

1) can python be as good as java ? if not what do you recommend ?
2) is it better for a programmer to be good in one language or be familiar with different languages ?

i am really interested in your opinions 

thanks

---

### Post by maximinus_uk on 2009-12-27
> **ivh90 said:**
> 1) can python be as good as java ? if not what do you recommend ?
2) is it better for a programmer to be good in one language or be familiar with different languages ?

Your first question is flame-war territory but I would say Python is a *better* language than Java.

Second, it is better for a programmer to be fluent in more than one language. This is because different languages suit different applications, and you shouldn't keep applying the same hammer to every job you get. With that in mind, I would suggest the following:

[LIST]
[*]Make sure you are happy with C. It's a simple language and a lot of other languages are based on it.
[*]You should learn an OO language, either Ruby or Python is best.
[*]You should learn a scripting language such as Perl, Python or Ruby
[*]You should learn a 'strange' language - I suggest scheme.
[/LIST]

C is the 'lingua franca' of Linux. OO is an established paradigm that you need to understand when reading other peoples code. Scripting languages are good for whipping up quick and dirty code (and for structured, well written code as well!). Scheme will blow your mind.

Other will have their own opinions, but it's important to realize that actually some languages are very similar - Ruby / Python / Perl aren't  structurally that different - think of them as different types of Pizza - and similarly Java and C++ are very similar in a conceptual way. Some languages like Scheme or Haskell are really very different and they will provide a good insight to computer theory even if you never use them on a day-to-day basis.

Whatever you do, have fun! :)

---

### Post by CptPicard on 2009-12-27
You know, this is something that has been discussed to death here... :)

> **ivh90 said:**
> 
1) can python be as good as java ?

How do you measure whether something is "as good as Java"? What does that mean? I personally find Python to be a much more flexible, faster to develop in language that allows for a lot of really nice things that are either impossible in Java or require some nasty hacks (anonymous inner classes plus "final" object wrappers for data items in "closure"), but the downside is that it is slower than Java, and in particular the heaviest-intensity code in Python can be prohibitively slow.

Then again, Python interfaces to a C module quite nicely, so if you can isolate the intense bits, they can be moved over there. It is exactly this kind of development model that seems to be slowly taking over from Java in my own coding, because Java the language has mostly been stagnating all decade.


> 2) is it better for a programmer to be good in one language or be familiar with different languages ?

In my book, someone who is only very good at one language is not yet even much of a programmer... more like a trained code monkey. The interaction of programming and language is interesting... most of the problems are actually in many ways language-independent, but as the late great computer scientist E. Dijkstra said, *"tools influence our thinking"*. Different programming languages offer different approaches to formulating solutions to problems, so it is worth spending the time to learn a couple of languages that are sufficiently different (that is, I don't think that most C-derivative languages, C/C++/Java/C#... offer much differentiation amongst themselves). 

Getting familiar with some of the ideas in higher-level languages in general (usually in combination with some math/algorithm/parsing/interpreter theory) will help you apply the gained insights in particular, often in any language.

In that sense, Python is very nice... it is very approachable, and borrows a lot of interesting ideas... in some parts it almost has a Lisp feel to it :) Besides, it's quite easy to learn to begin with, so you're not losing much if you do learn the basics to start using it. Having less cumbersome scripting language than Java in your toolbox is a good thing.

---

