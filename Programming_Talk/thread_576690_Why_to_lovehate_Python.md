---
title: "Why to love/hate Python"
date: 2007-10-15
forum: Programming Talk
---

### Post by pmasiar on 2007-10-15
To avoid shifting threads off-topic by responding to relative merits of Python (which is my preferred language), I decided to start this thread. If we can have sticky about such personal preference as IDE is, why not this, right? Selecting proper language seems to me deeper question.

Bunch of links to get context why I love Python:

[LIST]
[*][Freedom languages vs. safety languages](http://www.journalhome.com/codecraft/9003/) comparing languages in what is central: power and productivity of individual programmer, or checkpoint to secure communication between modules.
[*] [Why I love Python (zip)](http://mindview.net/FAQ/FAQ-012) - slides by famous Java/C++ expert Bruce Eckel, author of [Thinking in...](http://www.mindview.net/) series
[*] "Readability counts". In other languages, (yes, Perl, I am looking at you! :-) ) it is very hard to read code of people who use different coding standards. By making indent rules part of the standard (and btw it is normal coding practices, as you would do anyway), code of all people becomes readable. See also [Myths about Indentation](http://www.secnetix.de/~olli/Python/block_indentation.hawk) and how[Eric Raymond got scared by it at first](http://www.linuxjournal.com/article/3882), but "Python's use of whitespace stopped feeling unnatural after about twenty minutes" and now he prefers Python over Perl for any code above 100 lines.
[*] Edit: Please do not whine about tabs and spaces. Any decent editor can convert tabs to 4 spaces for you, and if it cannot, it is good enough reason to dump it and use real editor which can. It was unusual for me to, but after couple of minutes, it is normal, and no problem at all.
[*] People who need to code only occasionally prefer Python, because it is forgiving and simple to remember. And because non-professionals are 90% of the market, Python is not hype, but [language for next 100 years](http://www.paulgraham.com/hundred.html)
[*] Bruce Eckel explains [dynamic (latent) typing](http://mindview.net/WebLog/log-0051), also in [artima blog](http://www.artima.com/forums/flat.jsp?forum=106&thread=7590&start=0&msRange=15), [how to argue about it](http://mindview.net/WebLog/log-0052), and [why he is over](http://mindview.net/WebLog/log-0053)  with static typing.  Bruce's [view about Python](http://mindview.net/WebLog/log-0036)

[/LIST]

This hopes be **discussion on facts, not flamewar**. So I try my best, but cannot be hold responsible for others. It is also possible that this will earn me  ban.  We will see.

---

### Post by pmasiar on 2007-10-15
(In response from [post about C](http://ubuntuforums.org/showthread.php?p=3537968&posted=1#post3537968)
[C/Java has more resources than Python online]
One of the reasons (at least for python and for me) might be that I needed substantially less resources to get started with Python than with Java. Java is just so byzantine complicated. My "Java in a nutshell, 1.3" has 646 pages of standard format, "Python pocket reference" (2.4) has 148 pages, and pages are half the size. You need many more books to get reasonable comprehension of Java than for Python.

---

### Post by Wybiral on 2007-10-15
I like Python because I came into it from the world of Assembly, C, and C++. After that, you can really appreciate the beauty and simplicity of Python and you will notice a remarkable increase in your productivity. Another thing I like about Python is that you don't have to spend hours searching the web for libraries, Python comes with almost everything, and what it doesn't come with is always easy to find.

An even bigger reason why I'm so interested in Python is that my goal is to be hired at a smart and productive company like Google, who uses Python in applications such as Google Maps, Gmail, YouTube, and even in parts of its search engine. If the geniuses at Google think it's a good language, then it's probably a good language.

---

### Post by Unterseeboot_234 on 2007-10-15
This thread shouldn't be so prickly. I can only offer you an opinion. After 10+ years with all the Java updates, I can tell you I found Python very refreshing getting back to modules. Java is monolithic. We can make java code work and then discover it was a freak that the code was working. With java it could mean a total redesign of legancy code to  bridge into new java APIs. I got tired about that part. Java is template coding. Set up a template, customize it, set up a template, customize it, set up...

Python, on the other hand, and as far as I'm concerned, never was documented. The O'Reilly series of Python titles come a long way showing pieces of interesting cause and effects. The code in the books make perfect sense. And then you discover how tricky dynamic typing can be doing your own stuff. What works as a Python module takes a lot more thought when you convert such code into a class. 

The most wonderful discovery for me about Python was making the Linux terminal echo commands from Python statements. I found an easy way to process hundreds of digital photos using Python with ImageMagick (and I don't have to use ImageMagick's internal script engine). Ubuntu has capabilities like ImageMagick already built into it. Starting a discussion about Python using those capabilities would be useful. Very userful.

Java with its JRE can enhance Linux. Linux can NOT do audio without add-on hardware. So, as I make more progress with Python, I plan to see what Jython can do with Java ME2, and Java Media Framework.

So, Python. If it's just for fun.

---

### Post by AntiRush on 2007-10-15
> **pmasiar said:**
>  My "Java in a nutshell, 1.3" has 646 pages of standard format, "Python pocket reference" (2.4) has 148 pages, and pages are half the size.

To be fair you cannot compare those two books.  Java in a Nutshell is a book meant to teach Java and goes into a lot of depth.  Python Pocket reference is just that - a reference not meant to teach but to be used as a resource.

In fact, Python in a Nutshell has 654 pages.  

Don't get me wrong, I use both python and java quite often and like bits of both languages.  It's just not a fair comparison.

---

### Post by CptPicard on 2007-10-15
Nothing wrong with Python per se really, I use it actively myself... but I am not a true believer. Python has this perpetual feel of enforcing training wheels on you, while for some reason it is called a "freedom language". The fact and the way that Python enforces style seems to fly in the face of the idea that "programmers are consenting adults".

Now... style is a good thing, and I am slightly partial to languages that are "pure" stylistically as that often produces a kind of economy into the language. You know how things work because things are consistent. It's just that Python seems to enforce stuff in the wrong places, and sometimes the wrong way, despite supposedly being flexible. It's hard to put my finger on it what it is about, but sometimes Python feels petty for no reason :)

Of course, my primary complaints are the old ones... semantic whitespace is still awful, some syntactic constructs are missing or have to be implemented in an ugly way just because "they can be done otherwise", Python's classes feel a bit like an afterthought... yes, I don't like explicit self. I never rename "this" in other languages either. I'm sure the idea behind this is the ability to more easily just tack a function onto an object, or something like that... but Python's classes are so amorphous already that soon we'd just as well move back to procedures manipulating tuples :)

But, they are of course nitpicks. Fun ones, for sure, programming language differences are wonderful fodder for religious disputes... ;)

---

### Post by pmasiar on 2007-10-15
> **AntiRush said:**
> Java in a Nutshell is a book meant to teach Java and goes into a lot of depth.  


My copy is "desktop quick reference", and has very little of explanation: just mentions classes and methods, one per line. Maybe you confuse it with some kind of much thicker books, like Java Bible, Shipping Weight: 3.8 pounds? 

To be fair, I never seen any "pocket size" reference book for java. ;-)

P-N book has much more detailed info that J-N (I just opened in via Safari), with details and comments, multiple lines per item. Big part of P-N is just reprint of standard docs, thats why I like "pocket" book more, because lot of thought went in to compressing the info, make it more succinct, without withholding important parts.

---

### Post by mjwood0 on 2007-10-15
To be fair, though I'm really more into C due to my job relying on it, I really am interested in learning Python.  In fact, I've downloaded some reference manuals and the Dive into Python book from the documentation thread and am planning on looking at it tonight.

I don't expect it to replace C for me, but I really am looking for an easy to use scripting language.  I've tried to learn Perl hundreds of time it seems.  While I always end up with something that works, I think the old acronym for perl (Perl = Pathologically Eclectic Rubbish Lister) is somewhat true.  I can never actually wrap my head around it enough to not have to go back to basics every time I go to maintain one of the scripts I've written in it.  From what I've seen of Python, it's the perfect fit for this task.

I do have to say though -- the use of syntactic whitespace scares me just a little...

---

### Post by Wybiral on 2007-10-15
> **mjwood0 said:**
> I do have to say though -- the use of syntactic whitespace scares me just a little...

It scared me too, but now when I have to program in C or C++ I'm always thinking "What? You mean I actually have to type all these stupid semicolons and brackets?". Indentation is a must for good code anyway, just think of Python as not having semicolons or brackets.

---

### Post by mjwood0 on 2007-10-15
> **Wybiral said:**
> It scared me too, but now when I have to program in C or C++ I'm always thinking "What? You mean I actually have to type all these stupid semicolons and brackets?". Indentation is a must for good code anyway, just think of Python as not having semicolons or brackets.

Fair... but I usually let XEmacs handle all the indentation.  Guess I'll have to get used to doing it manually...

---

### Post by CptPicard on 2007-10-15
> **mjwood0 said:**
> Fair... but I usually let XEmacs handle all the indentation.  Guess I'll have to get used to doing it manually...

Actually, having a good editor that handles your indentation for you is ever more a must with Python. It indents your block for you after, say, an "if", and gives you ways to manage the blocks when you need to reindent... without a tool, managing the whitespace is annoying, and even more so as not managing it correctly on every line is a bug.

An editor will not, however, be able to *completely* automate Python code indentation though, because of the very reason that the whitespace is significant... the editor would have to "understand" your code in order to do it all, which it can't. But having a tool to support you in managing the invisible beast is valuable. :)

---

### Post by pmasiar on 2007-10-15
... and of course never mix tabs and spaces. Set your editor to "repace tab with 4 spaces". What, your editor cannot do it? Get real editor, they are free! :-)

---

### Post by Jessehk on 2007-10-15
One thing I hate about Python is the indentation-level-as-control structures thing. I don't mind it at all when I'm writing code, but when copy/pasting (or doing something similar) a bug caused an indentation error can be very hard to find and is extremely annoying.

---

### Post by mjwood0 on 2007-10-15
> **pmasiar said:**
> ... and of course never mix tabs and spaces. Set your editor to "repace tab with 4 spaces". What, your editor cannot do it? Get real editor, they are free! :-)

Haven't used actual tabs in year...

The first thing I do when there's crap (tabs) in a file:

```

META+X - untabify
```

---

### Post by CptPicard on 2007-10-15
Don't do that... you're losing information, sort of. Tab is a special character meant for the sole purpose of expressing indentation, so why not make use of it?

---

### Post by Wybiral on 2007-10-15
I never use tabs, only 4 spaces. I've noticed a lot of programming projects and standards use that convention, and I agree with it. It eliminates the risk of mixing tabs with spaces and it ensures the indentation will always look the same.

---

### Post by mjwood0 on 2007-10-15
> **CptPicard said:**
> Don't do that... you're losing information, sort of. Tab is a special character meant for the sole purpose of expressing indentation, so why not make use of it?

Tabs have no place in portable code.  Different editors treat them all differently and it makes for sloppy code.  Plus, it's against every coding standard I'm required to follow for work.

Tabs should be replaced by spaces in the editor.  Depending on the standard you're following, anywhere from 2 to 4 spaces seems the norm.

---

### Post by CptPicard on 2007-10-15
> **mjwood0 said:**
> Tabs have no place in portable code.

Why? Whatever the editor does with a tab is completely irrelevant to the code's portability from compilation perspective. Spaces, on the other hand, are redundant, you need to be counting them a lot more while writing (yes, an editor takes are of most of it), and actually the risk that you're accidentally having something like 7 spaces for two indents -- essentially making your source's text *different* is much greater than you having an inequivalent number of tabs, if you really need to insist on keeping your amount of whitespace strictly correct (which is of course desirable although, syntactically insignificant in most languages).

The good point about a tab is exactly the fact that it's more portable as an information carrier in your code even though you might prefer to actually work with a different visual indentation width from your coworkers. I can understand that you're made to follow your company's standards, but if I had a company, I honestly could not care less how my employees prefer to *view* their code as long as the code itself is according to some standard that avoids *incompatibilities* and *miscommunication*.

Sorry for the rant, whatever floats your boat, but the portability argument is just wrong :)

---

### Post by Wybiral on 2007-10-15
Well, some standards also suggest that each line be limited to 80 characters, you can't very well do this with tabs because it can be 4 spaces in your editor, 8 in another, and 2 in another. It gives you some perspective on when to wrap things like parameters. With spaces this is never a concern. Everyone can use the editor of their choice. Also, good editors treat your 4-space tabs like tabs anyway, when you press tab or backspace the result is usually the same.

---

### Post by CptPicard on 2007-10-15
Certainly if this is the case, then a good editor will make you wrap at 80 characters' physical width even when you use tabs, no? :)

---

### Post by mjwood0 on 2007-10-15
> **CptPicard said:**
> 
The good point about a tab is exactly the fact that it's more portable as an information carrier in your code even though you might prefer to actually work with a different visual indentation width from your coworkers. I can understand that you're made to follow your company's standards, but if I had a company, I honestly could not care less how my employees prefer to *view* their code as long as the code itself is according to some standard that avoids *incompatibilities* and *miscommunication*.

Sorry for the rant, whatever floats your boat, but the portability argument is just wrong :)

I gather from this statement that you're not a Solaris user.  UNIX text files treat tabs as 
```
^t
```

Having this all around your code when using a UNIX compliant editor is just a nuisance.  Same with things such as the carriage return / line feed issue of having
```
^M
```
at the end of every line.

Try ftping a file from a wondows editor to a unix editor and you'll soon see why many windows editors are despised by UNIX programmers (Microsoft's builtin editor in their visual studio is a good example).

Also, we have the 80 character limit, as well as the 5 nesting levels and a cyclomatic complexity of under 10.  Makes for fun coding...

---

### Post by Wybiral on 2007-10-15
> **CptPicard said:**
> Certainly if this is the case, then a good editor will make you wrap at 80 characters' physical width even when you use tabs, no? :)

No, it will simulate the 80 character wrap, but it can't wrap it because the tabs will be different in other editors. You're arguing against a very common coding standard... Most of the software projects I've seen that have a coding standard use this convention, I see no reason not to.

---

### Post by CptPicard on 2007-10-15
Mmmkay, I stand corrected. Got to admit that I still wouldn't use such standards myself because of the tabs' virtues -- character encoding issues ought to be solved by standardizing on UTF8, Solaris should be on its way out and tab width/80 character issues can be standardized on on their own without resorting to spaces, and the "editor will do it" argument goes IMO more the tabs' way ;)

(Yes yes.. I'm arguing for the sake of it...)

Just got Gutsy running btw. First time got Ubuntu upgraded without any immediately apparent breakage... is this thing really this much faster on desktop or am I imagining things?

---

### Post by slavik on 2007-10-16
> **mjwood0 said:**
> To be fair, though I'm really more into C due to my job relying on it, I really am interested in learning Python.  In fact, I've downloaded some reference manuals and the Dive into Python book from the documentation thread and am planning on looking at it tonight.

I don't expect it to replace C for me, but I really am looking for an easy to use scripting language.  I've tried to learn Perl hundreds of time it seems.  While I always end up with something that works, I think the old acronym for perl (Perl = Pathologically Eclectic Rubbish Lister) is somewhat true.  I can never actually wrap my head around it enough to not have to go back to basics every time I go to maintain one of the scripts I've written in it.  From what I've seen of Python, it's the perfect fit for this task.

I do have to say though -- the use of syntactic whitespace scares me just a little...
Perl is not an acronym (can you tell by it not being all caps?). Perl in fact was meant to be "pearl" but there was a language with that name at the time so Larry removed the 'a'. Also "Perl" is the language and "perl" is the interpreter. :)

As for my stance towards Python, I feel that it is being overhyped. I also haven't met a problem that Python solves that can't be solved in Perl, so I don't really have a reason for learning Python or Ruby for that matter.

---

### Post by mjwood0 on 2007-10-16
> **slavik said:**
> Perl is not an acronym (can you tell by it not being all caps?). Perl in fact was meant to be "pearl" but there was a language with that name at the time so Larry removed the 'a'. Also "Perl" is the language and "perl" is the interpreter. :)

This was supposed to be a joke...  I understand the fact that perl is an interpreter and everything.  But in my opinion, it's defiantly eclectic...

> **slavik said:**
> As for my stance towards Python, I feel that it is being overhyped. I also haven't met a problem that Python solves that can't be solved in Perl, so I don't really have a reason for learning Python or Ruby for that matter.

You may be right.  For me, the jury is still out.  Since I am really not good with Perl, I figured perhaps I'd give Python a try.  So far, aside from the syntactic whitespace, I'm finding it's quite powerful without being difficult to learn.  The real test for me will come when I try to do something useful.

---

### Post by Wybiral on 2007-10-16
> **slavik said:**
> As for my stance towards Python, I feel that it is being overhyped. I also haven't met a problem that Python solves that can't be solved in Perl, so I don't really have a reason for learning Python or Ruby for that matter.

Turing completeness means nothing, as we've established in other threads (BrainFuck is turing-complete). Development time, support, ease of use, and maintainability mean everything. Perl code is notoriously cryptic whereas Python is meant to be working pseudo-code.

---

### Post by LaRoza on 2007-10-16
> **slavik said:**
> 
As for my stance towards Python, I feel that it is being overhyped. I also haven't met a problem that Python solves that can't be solved in Perl, so I don't really have a reason for learning Python or Ruby for that matter.

I take it you know Perl very well? I never saw a task I Perl can solve, but can be done in Python. Obviously, I know Python better than Perl.

The "reason" you don't see a reason, is because you know Perl very well (it seems), not everybody will have this reason or background,

---

### Post by pmasiar on 2007-10-16
> **mjwood0 said:**
> I do have to say though -- the use of syntactic whitespace scares me just a little...

I understand that position, it scared me to.

[Myths about Indentation](http://www.secnetix.de/~olli/Python/block_indentation.hawk) and [Eric Raymond got scared by it at first](http://www.linuxjournal.com/article/3882), but "Python's use of whitespace stopped feeling unnatural after about twenty minutes"

I updated main post with these links too.

---

### Post by xtacocorex on 2007-10-16
What's wrong with whitespace?  All code should be indented when possible.  Python forces you to use it, which is good programming practice anyway; teaching new users not to be incompetent dolts.  I can't begin to tell you how many codes I've debugged in FORTRAN where people didn't indent and it bugged the hell out of me and pushed me to the point of not helping them anymore.
 
Python is good because it allows you to program faster.  I do wish numPy and all the other math based libraries would become part of the base, then I could easily develop cross-platform apps without the need for the user to install extra stuff.  I still get a little confused about Lists and that sort of stuff when I try to do multi-dimensional matrices out of them.

---

### Post by pmasiar on 2007-10-16
> **slavik said:**
> I also haven't met a problem that Python solves that can't be solved in Perl, so I don't really have a reason for learning Python or Ruby for that matter.

I found Perl rather unforgiving, if you want to use it only casually. It is full of quirks and tricks (scalar vs list context? wtf?) which you need to get just right, or Perl would bite you. Perl's animal is camel (or alternatively "swiss army chainsaw"), and for good reason: camel is hardy and can do what most animals cannot, but is not easy to master.

I added link to main post about Eric Raymond experience how and why he moved from Perl to Python, and it exactly matches my own: Once my code grows over 10K, it was increasingly harder and harder to maintain it in Perl. Not so in Python.

So it seems to me that you are longtime Perl hacker who knows it through and out, and hacks Perl every day to keep in shape - it is like juggling running chainsaws :-D This might be reason why people who need to code only occasionally prefer Python, and not Perl. And because non-professionals are 90% of the market, Python is not hype, but [language for next 100 years](http://www.paulgraham.com/hundred.html)

---

### Post by slavik on 2007-10-16
> **pmasiar said:**
> I found Perl rather unforgiving, if you want to use it only casually. It is full of quirks and tricks (scalar vs list context? wtf?) which you need to get just right, or Perl would bite you. Perl's animal is camel (or alternatively "swiss army chainsaw"), and for good reason: camel is hardy and can do what most animals cannot, but is not easy to master.

I added link to main post about Eric Raymond experience how and why he moved from Perl to Python, and it exactly matches my own: Once my code grows over 10K, it was increasingly harder and harder to maintain it in Perl. Not so in Python.

So it seems to me that you are longtime Perl hacker who knows it through and out, and hacks Perl every day to keep in shape - it is like juggling running chainsaws :-D This might be reason why people who need to code only occasionally prefer Python, and not Perl. And because non-professionals are 90% of the market, Python is not hype, but [language for next 100 years](http://www.paulgraham.com/hundred.html)
I wish I was, but I doubt I could even be considered intermediate.

some unreadable Perl constructs are like commands in a terminal, you have to just know them.

---

### Post by mjwood0 on 2007-10-16
> **slavik said:**
> some unreadable Perl constructs are like commands in a terminal, you have to just know them.

While my language of choice is C since it's what I know best and use daily, this is the one downside to it.  There are some things you just have to "know".  

For beginners, this is far from ideal.  For those who have learned it inside and out, it becomes second nature.  That doesn't make it correct and I see beginners struggle with it daily.

But at least it's not Jovial...

---

### Post by slavik on 2007-10-16
> **mjwood0 said:**
> While my language of choice is C since it's what I know best and use daily, this is the one downside to it.  There are some things you just have to "know".  

For beginners, this is far from ideal.  For those who have learned it inside and out, it becomes second nature.  That doesn't make it correct and I see beginners struggle with it daily.

But at least it's not Jovial...
I also see people who yell that GUI should be the only way to do anything.

"Knowledge is power" ... is it not?

---

### Post by pmasiar on 2007-10-16
> **slavik said:**
> I also see people who yell that GUI should be the only way to do anything.

"Knowledge is power" ... is it not?

There is one aspect of user interface, could be called "discoverability" - how easy is to find where it is and what it does. The problem with commandline it, it has zero discoverability.

---

### Post by slavik on 2007-10-16
> **pmasiar said:**
> There is one aspect of user interface, could be called "discoverability" - how easy is to find where it is and what it does. The problem with commandline it, it has zero discoverability.
so do ALL LANGUAGES (computer or natural)

---

### Post by pmasiar on 2007-10-16
> **slavik said:**
> so do ALL LANGUAGES (computer or natural)

Well, in Python, ie looping throught very different "containers" has same syntax:
[php]
lst = [1, 2, 3, 4, 5] # list
for x in lst:
    print x

dct = dict(a=1, b=2, c=3, d=4) # dictionary = assoc. array
for k in dct:
   print k, 'is mapping to', dct[k]

infile = open('path/to/file', 'r') # open a file
for line in infile:
    print line
[/php]
So it is "discoverable" because similar object can be handled by similar syntax. And it is easier to remember this way.

You, from all people, should know that natural languages like Russian DOES have this discoverability: you CAN create new words easily. :-)

---

### Post by slavik on 2007-10-16
> **pmasiar said:**
> Well, in Python, ie looping throught very different "containers" has same syntax:
[php]
lst = [1, 2, 3, 4, 5] # list
for x in lst:
    print x

dct = dict(a=1, b=2, c=3, d=4) # dictionary = assoc. array
for k in dct:
   print k, 'is mapping to', dct[k]

infile = open('path/to/file', 'r') # open a file
for line in infile:
    print line
[/php]
So it is "discoverable" because similar object can be handled by similar syntax. And it is easier to remember this way.

You, from all people, should know that natural languages like Russian DOES have this discoverability: you CAN create new words easily. :-)
I replaced the symbol/variable names with Perl sigils :)

Python: for $ in @
Perl: foreach @

as for Russian, making new words is not easy. For example: database. In Russian it is literally 2 words (base of data) (in Russian, you can conjugate words to give them possessive form). not only that, to make something plural, there are 4 endings, in English there are 2 and a special case (word ends with y), but all 3 have rules. But one thing that is truly interesting in the Russian language is being able to take any word (or almost any word) and make it into an adjective, or diminutive.

It's also easy to make new words in English if you have a good Latin/French/German base knowledge :)

---

### Post by pmasiar on 2007-10-18
OK, example of Python "discoverability": I wanted to join two lists, and instead of reading docs, I just experimented in Python shell:

[php]
>>> l1 = [1, 2, 3, 4]
>>> l2 = ['a', 'b', 'c']
>>> b = (l1, l2)
>>> b
([1, 2, 3, 4], ['a', 'b', 'c'])
# this is tuple of two lists - no good. Let's force list?
>>> b = list(l1, l2)
Traceback (most recent call last):
  File "<pyshell#5>", line 1, in -toplevel-
    b = list(l1, l2)
TypeError: list() takes at most 1 argument (2 given)
>>> b = list([l1, l2])
>>> b
[[1, 2, 3, 4], ['a', 'b', 'c']]
# list of lists: no good.
>>> b = list((l1, l2))
>>> b
[[1, 2, 3, 4], ['a', 'b', 'c']]
# still no good. But Python should be simple. 
# What is simplest way to add one thing ot another? +?
>>> b = l1 + l2
>>> b
[1, 2, 3, 4, 'a', 'b', 'c']
# BINGO!
[/php]
With no reading of docs.

---

### Post by slavik on 2007-10-18
that's because you know that + is overloaded (or you have some understanding of overloading). :)

---

### Post by pmasiar on 2007-10-18
No 'understanding' of overloading is needed to use it. All you need to know is, you can apply + to all sorts of objects.

---

### Post by mjwood0 on 2007-10-18
> **pmasiar said:**
> No 'understanding' of overloading is needed to use it. All you need to know is, you can apply + to all sorts of objects.

I see your point, but it's greatest strength (heavy overloading) is also somewhat dangerous if people don't really understand what it's doing.

You can't write efficient code if you don't understand what's going on behind the scenes...

---

### Post by Wybiral on 2007-10-18
> **mjwood0 said:**
> I see your point, but it's greatest strength (heavy overloading) is also somewhat dangerous if people don't really understand what it's doing.

You can't write efficient code if you don't understand what's going on behind the scenes...

The point of a good HLL is to not have to deal with what's going on behind the scenes. IMO Python does a great job at implementing genericness, especially with its "__iter__", "__str__", and it's operator overloads. Reusability is really easy because objects can be supplemented and changing an object's used in a module doesn't usually require a total rewrite of that module.

Iterators and generic container classes are what make the STL so useful in C++, in Python they have constructs supported by the language itself.

---

### Post by pmasiar on 2007-10-18
> **mjwood0 said:**
> I see your point, but it's greatest strength (heavy overloading) is also somewhat dangerous if people don't really understand what it's doing.

You can't write efficient code if you don't understand what's going on behind the scenes...

If you write code in Python, you care about effective use of developer's time more that about CPU. Either you don't care, or you are not pro enough to care. And you always can use C libraries for speed if crucial. 

In most cases, we have plenty of CPU cycles to burn - is your desktop used for more that 10%?

---

### Post by mjwood0 on 2007-10-18
I guess I just can't fathom not caring about frame times and such.  I've spent too long in the RTOS world to not worry about optimization and speed.

For desktop applications, I see everyone's point.  It's really not that harmful if a few more cycles get used.  But in the embedded world, speed is crucial.  

To be fair, I really don't think Python was ever designed for embedded work.  That's what C is for and probably another one of those things that I'm just going to have to get used to as I attempt to expand my knowledge base back into the desktop world.

---

### Post by pmasiar on 2007-10-18
I do care about the speed sometimes. But because I write mostly web front-end for a database, where about 80% of the time is spent on data access, best return on my time optimizing app is proper database design. Programming in any low-level strictly typed language like C or Java is just waste of efforts.

I guess "it depends", like always... :-)

---

### Post by aks44 on 2007-10-18
As a followup to [this post]("http://ubuntuforums.org/showpost.php?p=3560232&postcount=8") I'll chime in for a few remarks / questions.


> **pmasiar said:**
> [php]
>>> l1 = [1, 2, 3, 4]
>>> l2 = ['a', 'b', 'c']
>>> b = l1 + l2
>>> b
[1, 2, 3, 4, 'a', 'b', 'c']
[/php]


Maybe I'm too used to static typing (oh well, forget "maybe" ;)) but... how the hell are you gonna do something useful with a heterogenous container?

Granted in this very example, if you treat the contents as characters, the numbers will automatically be casted to chars according to their ASCII code, and if you treat the contents as numbers the characters will be casted accordingly. So far, so good.

But now if you do that with objects of totally distinct classes??? To me it doesn't have any advantage, just one BIG inconvenient: you won't catch the (unavoidable) error until runtime, and it may be quite hard to debug.

IMHO the dynamic typing "advantage" quickly turns out to be a hindrance, it requires way more attention from the programmer than static typing. "Robot"-coding (those bad days when you slept 3 hours and have a hangover) is just not allowed, even for routine tasks...


Oh well, I guess I just can't wrap my head around this way of thinking, but I'm really curious... What am I overlooking? Please enlighten me. :)

---

### Post by Wybiral on 2007-10-18
> **aks44 said:**
> but... how the hell are you gonna do something useful with a heterogenous container?

If they all share a method then it's easy. As an example, suppose you have to update a list of objects (maybe a game where models/sprites/ai all need updated). Instead of calling a bunch of loops with various conditions to verify which need updated (or having several containers to keep track of the ones that need updated) you could just have a "objects that need updated" list and use:

```

for obj in objects:
    obj.update()

```

Dynamic typing like this really comes in handy when you want to write generic code.

---

### Post by aks44 on 2007-10-18
> **Wybiral said:**
> If they all share a method then it's easy. As an example, suppose you have to update a list of objects (maybe a game where models/sprites/ai all need updated). Instead of calling a bunch of loops with various conditions to verify which need updated (or having several containers to keep track of the ones that need updated) you could just have a "objects that need updated" list

Again don't get me wrong, I guess I'm just too used to static design, but the first thing that comes to my mind is: if they share a common method, that method should be part of a common base class (and probably **virtual** too, in C++ terms).


I may be dense on this one, but I still don't see any advantage to dynamic typing, only problems. What if a totally unrelated object slips into the container (because of human error)? :?

---

### Post by Wybiral on 2007-10-18
> **aks44 said:**
> Again don't get me wrong, I guess I'm just too used to static design, but the first thing that comes to my mind is: if they share a common method, that method should be part of a common base class (and probably **virtual** too, in C++ terms).


I may be dense on this one, but I still don't see any advantage to dynamic typing, only problems. What if a totally unrelated object slips into the container (because of human error)? :s

In Python inheritance doesn't have to be so strict. Why should they all inherit from a base when they are completely different and only need that one method in common? Python does support inheritance BTW, but you don't have to restrict the list to a type so there's no need to use a base.

If an unrelated object slips in, then the interpreter gives you an error. But this kind of negligence will cause errors in any language. And proper testing is obviously a key in developing with dynamic languages (as it should be for all languages).

EDIT:

Oh yeah, and all of the objects members are virtual in Python. They can also be tacked on later if need be.

---

### Post by pmasiar on 2007-10-18
> **aks44 said:**
> how the hell are you gonna do something useful with a heterogenous container?

Oh, i never would. That was just random idea, to get two obviously different lists. I could have 11, 12, 13, and 21, 22, 23.

> Granted in this very example, if you treat the contents as characters, the numbers will automatically be casted to chars according to their ASCII code

No, they would not. Numbers will stay numbers and I would have to cast them to str(). I never planned to use those lists, I just wanted to merge them.

> Oh well, I guess I just can't wrap my head around this way of thinking, but I'm really curious... What am I overlooking? Please enlighten me. :)

You are missing how easy is to play with Python in its shell. I don't have to whip a page of code just to try a function call. So I can do it without much thinking about consequences, about how I would use it later. I wanted to join two lists, find out how WITHOUT READING ANY DOCS, and used the trick in my real code.

---

### Post by pmasiar on 2007-10-18
> **aks44 said:**
>  I guess I'm just too used to static design, 

yes, obviously :-)

> but the first thing that comes to my mind is: if they share a common method, that method should be part of a common base class ... I still don't see any advantage to dynamic typing, only problems. What if a totally unrelated object slips into the container (because of human error)? :?

Dynamic typing  (in fact 'latent' or late binding) allows to pass object which is NOT subclass. It just happens to have method with same name. All other methods (which I don't use) might not exist, I don't care.

It is also called "duck typing": [http://en.wikipedia.org/wiki/Duck_typing](http://en.wikipedia.org/wiki/Duck_typing) if it walks as a duck and quacks as a duck, as far as we care it IS a duck. No need of elaborate byzantine class hierarchies: life is simple and flat.

---

### Post by aks44 on 2007-10-18
I'll try to make my POV more clear about this matter...


I guess noone here will argue against the fact that code factorization is a must. Code duplication is the root of all evil, it just makes your code unmaintenable. Such factorization is expressed by functions / methods.


Now, from a pure design POV... not only code factorization is good, but also concept factorization. Such factorization is expressed by (multiple?) inheritance.
Back to Wybiral's example, anything that can be updated would in fact be Updatable (with a single pure virtual method, "update").

Currently there is no way to enforce code factorization, but IMO static typing is a very good tool to ensure design factorization.


That's why I have so much trouble understanding the point of dynamic typing. Why use a tool that allows you to break sane rules?


As a side note, you could bring the same kind of issue (but in the opposite way) when it comes to indentation. Indentation is A Good Thing too, so why use a tool that allows free indentation?
Funny that two languages (Python / C++) have exactly the *same* caveats even though not about the same features... ;)
However to be honest, to *me* indentation matters much less that proper design, just because there are tools to take care of that...

I hope you get my point. :)


> **pmasiar said:**
> if it walks as a duck and quacks as a duck, as far as we care it IS a duck.

It is at the same time a duck, a bird, an animal, a living being and a thing.


> **pmasiar said:**
> life is simple and flat.

Like the earth? :p (j/k dude)

---

### Post by smartbei on 2007-10-18
To be fair aks44, from my recent experiance with c++ I conclude that static typing does indeed take more time and thought for the programmer, though perhaps this is because of my inexperiance. Especially when working with pointers of various sorts it can get somewhat hairy.

So while there is a point in that there is no usual (I'm sure there are cases...) need for generic containers which can take several different object types, that does not mean that it is necessarily detrimental that they exist. As you point out, you do lose the type-safety, but you gain quite a bit in usability and simplicity I think.

Just BTW - pmasiar, you are aware that the "language for next 100 years" that the author of that article intended is probably Lisp, right?

---

### Post by aks44 on 2007-10-18
> **smartbei said:**
> from my recent experiance with c++ I conclude that static typing does indeed take more time and thought for the programmer

Again, I don't have much experience with dynamic typing (apart from PHP) so I won't argue with that. Looks like neither of us know the "other side" enough to be totally objective. :)


> **smartbei said:**
> Especially when working with pointers of various sorts it can get somewhat hairy

Strange, I just *never* deal with (raw) pointers, only with objects (at least when it comes to ownership problems, honestly the other cases don't matter)...
Most of the time I allocate them on the stack, and for the rest I use RAII wrappers. No headaches this way. :)

---

### Post by Wybiral on 2007-10-18
> **aks44 said:**
> I hope you get my point. :)

I do get your point. And I used to fear the same thing about Python before I started using it myself (that dynamic typing was risky and prone to error or that it didn't reduce development time). But after having used Python for a while, I find it to be incredibly comfortable and so far haven't made any mistakes in regards to dynamic typing.

It completely changes the way you look at objects and their relationship with each other. Also, the development time boost is incredibly noticeable. All the cool generic tricks you can do in C++ to reuse code are useless in Python because they're mostly part of the language.

You seem to think it's crazy to not just use a base class for implementing inheritance in Python, but once you get used to not needing to do things like that (though you can, Python does have constructs for inheritance) you wonder why anyone would go through the hassle of setting that up.

Back to the game example, my update objects can all be thrown in a list and "update()" can be called and my visible objects can be tossed in another list and "render()" can be called. Not all of them should inherit from a base (static scenery models don't need updated, and things like AI don't need rendered). Sure, I could implement some multiple inheritance for stuff like this, but why bother? I save the code by using generic loops like that and I also save the code by not having to define all of this virtual multiple inheritance. That's a really trivial example, but I'm sure you can imagine more useful situations if you think about it.

I will also add that  Python does have a function "isinstance(object, type)" that can determine if an object is an instance of a particular class, "type(object)" that returns the type of an object, and "hasattr(object, 'attribute')" which can tell you if an object possesses that attribute. So if you're really worried about misuse, you can make sure.

---

### Post by pmasiar on 2007-10-18
> **smartbei said:**
> 
Just BTW - pmasiar, you are aware that the "language for next 100 years" that the author of that article intended is probably Lisp, right?

It was keynote talk on Python conference PyCon 2003, so I would assume that it is Python :-) Lisp is language for expert hackers, Python (or another dynamically typed language like that) is language for unwashed masses for next 100 years.

Also, point is that NO WAY the solution is Java, but something else.

---

### Post by aks44 on 2007-10-18
> **Wybiral said:**
> so far haven't made any mistakes in regards to dynamic typing.

What bothers me most isn't that I *may* make mistakes (I'm pretty sure I wouldn't, I'm way too defensive), but that such mistakes are just *possible*. This makes me wonder about the pertinence of dynamic languages design decisions.


> **Wybiral said:**
> Also, the development time boost is incredibly noticeable. All the cool generic tricks you can do in C++ to reuse code are useless in Python because they're mostly part of the language.

Looks interesting if it really keeps those promises...

But again, those "tricks" are not only good to reuse code, but also to explicitely *share concepts*.


> **Wybiral said:**
> You seem to think it's crazy to not just use a base class for implementing inheritance in Python, but once you get used to not needing to do things like that (though you can, Python does have constructs for inheritance) you wonder why anyone would go through the hassle of setting that up.

I'll state it again: concept factorization is as important as code factorization.
To me, what you're advocating here is the design-wise equivalent of code duplication: an heresy... ;)


Oh well, call me old-school... I'm really having hard time wrapping my head around that...


> **Wybiral said:**
> Python does have a function "isinstance(object, type)" that can determine if an object is an instance of a particular class, "type(object)" that returns the type of an object, and "hasattr(object, 'attribute')" which can tell you if an object possesses that attribute. So if you're really worried about misuse, you can make sure.

And C++ has dynamic_cast (granted, it doesn't cover "hasattr", only the two others).



> **pmasiar said:**
> NO WAY the solution is Java

At least we agree on something. :D

---

### Post by pmasiar on 2007-10-19
> **aks44 said:**
> What bothers me most isn't that I *may* make mistakes (I'm pretty sure I wouldn't, I'm way too defensive), but that such mistakes are just *possible*. This makes me wonder about the pertinence of dynamic languages design decisions.

Bruce Eckel writes about strong testing being better than strong typing. I finally found again his old blog posts [here](http://mindview.net/WebLog). I will put selection of them to original first post.

---

### Post by LaRoza on 2007-10-19
> **pmasiar said:**
> I so I would assume that it is Python :-) Lisp is language for expert hackers, 

Why is Lisp for experts? I was able to learn the basics (Common Lisp), and write programs in it, granted, they weren't all that complicated, as I had only a few resources, and didn't have access to the internet, but it wasn't any harder than learning NASM or Fortran.

---

### Post by pmasiar on 2007-10-19
At least in mind of Paul Graham Lisp is for elite hackers. I was responding to suggestion that Lisp is language for next 100 years. I think Python is.

Read other graham's essays, interesting reading (he has liberal arts degree, not comp sci).

---

### Post by cwaldbieser on 2007-10-21
> **pmasiar said:**
> There is one aspect of user interface, could be called "discoverability" - how easy is to find where it is and what it does. The problem with commandline it, it has zero discoverability.

In the examples you give later on, you show that you can experiment in the python shell to figure out how the language works without having to read documentation.  I don't understand why you can't do the same thing with a shell like bash.  I am not sure I am understanding how "discoverability" applies to python but not the command line in this case.

---

### Post by pmasiar on 2007-10-21
> **cwaldbieser said:**
> Ihow "discoverability" applies to python but not the command line in this case.

OK, show me example how you can "discover" something in bash command line.

---

### Post by btdown on 2007-10-21
I hate python because its object oriented and tabs matter.

Why cant we have a language that normal people can program?

---

### Post by LaRoza on 2007-10-21
> **btdown said:**
> I hate python because its object oriented and tabs matter.

Why cant we have a language that normal people can program?

Don't take the bait people....

---

### Post by pmasiar on 2007-10-21
> **btdown said:**
> I hate python because its object oriented and tabs matter.

Just interesting, what language would self-proclaimed "normal" OOP-hater would recommend?

And you are completely misguided, TABs do not matter - proper code structure does. 

But if you hate proper code structure and OO, I feel only pity for you. What language is left for you? Obfuscated Perl? :-)

---

### Post by hecato on 2007-10-21
> **pmasiar said:**
> Bruce Eckel writes about strong testing being better than strong typing. I finally found again his old blog posts [here]("http://mindview.net/WebLog"). I will put selection of them to original first post.

Perhaps you refer to the "oldest" post there, perhaps this?
[LIST]
[*][http://mindview.net/WebLog/log-0051](http://mindview.net/WebLog/log-0051)
[*][http://mindview.net/WebLog/log-0052](http://mindview.net/WebLog/log-0052)[/LIST]And in the last part of the second post (thought I havent readed it all) I found this

> 
[FONT=verdana,tahoma,arial,helvetica,sans]**[FONT=verdana,tahoma,arial,helvetica,sans]We're really talking about testing[/FONT]**


[/FONT]
In the end, these are all just different kinds of tests.

Also that make me remember a video I see about Haskell little time ago [http://www.haskell.org/haskellwiki/Video_presentations](http://www.haskell.org/haskellwiki/Video_presentations) in a taste of Haskel there are 2 videos (Simon Peyton-Jones, OSCON, July 2007.), in one of those 2 videos it show testing of Haskell, and from what I remember is marvellous and easy (I think is in the second video), but yes, at the end all that "hipe about types, cast, bla bla" are only about test in some things about the programm (writing, execution, semantics, blah).

---

### Post by cwaldbieser on 2007-10-22
> **pmasiar said:**
> OK, show me example how you can "discover" something in bash command line.

```

$ for name in a b c d; do echo $name; done
a
b
c
d
$ for name in "a b c d"; do echo $name; done
a b c d

```
By experimenting in the shell I can discover how quoting affects the output without needing to refer to the documentation.

---

### Post by hecato on 2007-10-22
Blah...

In a lot of things you can "discover" by try an error, and remembering (yea use of the green, gray or red cells in the head, watever).

Also you can discover what you can not do, or the clasicall errors **that almost all (or all without exception to the rule) can find more fast than something usefull by try and error**.


I guess always is better know before hand what you can and cant do with some extend. Do try and errors, learning all that let them for more important things.

-- I mean, if you will experiment all posible options, why not include some bash code in python and run it or the other way?
-- your answer: Are you crasy that will not work!
-- O yea, I see in you previous experience.
-- What is the point?
-- Only that, normally you repeat yourself, I mean, if with some little knowledge of the language you try to see how things change or how a comma or [] or {} affect certain output is because you already know something of the language and some of the previous work you have... and
-- thus I dont get your point?
-- Simple, go with your mom, or capture a person out there... there are millions in the worl, sure you can grab 1
-- but that is...
-- that is my point, put it in front of your prefered wawa thing (or your prefered editor) and say "program for me whatever you can with try and error", go out, take a cofee, met some 1 new, return and see what the persona have for you ;).
-- blah
-- yea, I say that to... blah, blah, blah or wawawa :P.


haha, that was a quasi conversation with myself in this topic, sure you can discover things, but at less you need to know that somethings about, like some things are in english (you know if you take a person in México probably will try to write it completely in spanish) and are called keywords, some of those are called vars (or "things that change in time", whatever), there should be some type of jump or branching... but ey!!! we call that "structured programming", perhaps math operations, a way to call a certain piece by a name (functions, objects??) and execute it in some way (call by reference, with a table, other).


Perhaps you will argue that is more easy  to a person that as no interest in programming and computers and related things to programm in Python than in bash or viceversa. But that is only argee, because perhaps you can find 1 that does the contrary of what you say and even only 1, that break the rule (at less matemagically... ops matematically).

------

I also prefer tabs for reduce space, but I like more that space of tabs are imposed for use the "structured programming" part, because at less for noobs they can blame those errors (or in copying), but I have readed code of people that write like

```
int main() { exp1; if (exp2) { exp3;
 exp4;
 if (exp5)
            { some;
    }
bla1; bla2 () { .... 
                                 bla bla bla      }
    }
                    }

```
In fact my way of think dont know if I have put the correct close braces, and doesnt know at first sigh to put the else of the first if without take care of count... yea, I have seen lot of people dont know about "guidelines" or best practices... even there enter documentation, comentation et all that.

And the thing is that they programs "work", I havent seen that in python (but I also know less people that know that lenguage compared to C, C++, java and all the others). If you dont have correct identation, then it will not work "magically" because I really dont know how that people can read their own code... **lol**.

------

By the way, you can write all with def without define a class (yes you will need perhaps to use some objects here and there), being more like C at less in style, without being the so called IIRC "lava code anti-pattern" that some non OOP people do when they have no OO background and knowledge of the usage in the language, and they write all inside a big class that do all, "methods" used like "funcions in C" or some like that, because at less in diference to java and others, you dont need to write def (or the equivalent) always inside a definition of a class.

---

### Post by hecato on 2007-10-22
Only for be more rough about the point of discovery.. and perhaps passing the line a little, but anyway.

You can discover things about your body, if you take enough time. Also can discover things about the body of your girlfriend if see lets you, lol.

The point of discovery, is related to what is there and some previous knowledge of related things (experimentation, try  and error, scientific method, etc?) (sometime not much, but related by a thin line), you can discover a new smell convening others smells or components, or a new food doing it different. The point is that you are also restricted by the environment of the "discovery", I mean I do not know of a discover of the whole without take in care the little parts of it,because you can say "this is the whole" if you are not sure you have all parts of it.

If you dont get the "environment" part, I mean like this, there will be no discover that can not happen in the nature, because we are surrounded by it, and if you think there is a discovery that is outside the nature, thus we can argee "that" is also part of it even that at first sight not. There will be no teleportation if it cant happen in nature.

"That" that is not part of the nature, will be like "break" the nature of the things, but if something can be breaked, then "that break" is also part of his nature ;), haha :P.

How this relate to the anterior programming talk?, simple, the grabed random person without previous knowledge of programming languages (major part of the in english, with some Influence of structured programming and other paradigms like, procedural, OO, etc), probably will not be able to discover anything of bash or python (or the new language for the next 100 years... without know a little of this before*), no matter how a programmer can "discover" by try and error in a new language on in an already semi-know 1, with all this previous information that a programmer know about such matters ;).

* I have a rough example, but not this time... lol, if a person ask you to run and catch, you will probably know how to run and catch, but the other person hasnt say you will need to catch a car :P, like you see, you can have a little previous experience or knowledge, but you are not sure that knowledge will always work for all, you react (or the called adapt)... thus after that perhaps you will be able to run and catch a car (not a ball of x game like you know before), returning to "you need previos knowledge or experience", say to a little baby of 1 month run and catch (even that you now specify that it will catch a car, the baby will not able even to understand you, or know that perhaps is listening sounds, and that some of those are words in X language, because the baby has only started with what is basicall to interact, the senses, muscles and specially the brain).

---

### Post by Wybiral on 2007-10-22
> **cwaldbieser said:**
> ```

$ for name in a b c d; do echo $name; done
a
b
c
d
$ for name in "a b c d"; do echo $name; done
a b c d

```
By experimenting in the shell I can discover how quoting affects the output without needing to refer to the documentation.

I think the point is that Python is generic enough for many of its elements to be used interchangeably. BASH, aside from its basic rules, is really just a system of executing programs with parameters, but there is no real convention between these programs (making discover-ability difficult).

> **hecato said:**
>  ... 

> **hecato said:**
>  ... 

WTF?

---

### Post by cwaldbieser on 2007-10-22
> **Wybiral said:**
> I think the point is that Python is generic enough for many of its elements to be used interchangeably. BASH, aside from its basic rules, is really just a system of executing programs with parameters, but there is no real convention between these programs (making discover-ability difficult).


Well, "uniformity" might have been a better way to describe it.  Even though the basic python language attempts to be very consistent, I find I still have to read the documentation to figure out how many of the standard library modules work.

To me, this seems somewhat similar to how in shell scripting, the basic rules and conventions are pretty much established, but the behavior of individual programs may vary.

Both environments make getting help easier with commands/functions like "help", "man", and "apropos", so quickly looking up what a program/module is supposed to do does not seem like a big deal.

---

### Post by mjwood0 on 2007-10-22
> **Wybiral said:**
> I think the point is that Python is generic enough for many of its elements to be used interchangeably.

Are we all convinced that this is a good thing?  Something that is too generic seems bound to have flaws.  Then again, perhaps it *is* good...

I really think that discoverability is nice BUT I think we're oversimplifying here.

There was an example of someone doing the following in C:
```

if (string == "Hello World")
{
  ...
}
```

Obviously, this didn't work.  Are we now saying that it should?  Personally, I like that strings are different than integers are different than structures.

Just my $0.02...

---

### Post by Wybiral on 2007-10-22
> **mjwood0 said:**
> Are we all convinced that this is a good thing?  Something that is too generic seems bound to have flaws.  Then again, perhaps it *is* good...

I really think that discoverability is nice BUT I think we're oversimplifying here.

There was an example of someone doing the following in C:
```

if (string == "Hello World")
{
  ...
}
```

Obviously, this didn't work.  Are we now saying that it should?  Personally, I like that strings are different than integers are different than structures.

Just my $0.02...

I'm not sure I see your point. C isn't object oriented, so it can't have a string class with an overloaded "==" operator. In Python and C++, you can overload the "==" operator, so when "a == b" is used, it's similar to calling "strcmp(a, b)" in C. Operator overloading is just a convenient way to make code look familiar:

```

mov_vec3(vector1, vector2);
add_vec3(vector1,  vector3);
scale_vec3(vector1, 0.5);
mult_vec3_mat4(vector1, matrix1);

```

VS

```

vector1 = matrix1 * ((vector2 + vector3) * 0.5);

```

IMO, the second looks much more natural and mathematic. With proper labeling and documentation there really is no risk in using them. Obviously only when it's appropriate (such as math and comparative operators).

So yes, I do think "==" is appropriate for comparing two strings (or any two objects of the same type for that matter).

---

### Post by mjwood0 on 2007-10-22
> **Wybiral said:**
> 
So yes, I do think "==" is appropriate for comparing two strings (or any two objects of the same type for that matter).

I would agree that it's okay if they are the same type.  However, then you get people who try the following:

```

if (string == 4)

```

and are confused.

You are also going to get people who do this:
```

char *string = "0";
if (string != 0)
{
  ...
}
```
and then wonder why they get into the if statement...

Having clearly defined operations for string, numbers, vectors just makes things harder to screw up.

---

### Post by pmasiar on 2007-10-22
> **mjwood0 said:**
> 
```

if (string == 4)

```
and are confused.


In Python, they are not confused, they got plain error, with stack trace. As the "Zen of Python" says: "In face of uncertainty, refuse temptation to guess". Yes indeed.

---

### Post by Wybiral on 2007-10-22
I don't see why those same people wouldn't try:

```

if (!strcmp(string, 4))
if (strcmp(string, 0))

```

They would have similar problems.

---

### Post by hecato on 2007-10-22
> WTF?

I have guess that people not will be able to grasp beforehand what I say... lol.
--------
For all you points I will reference my 2 posts.

In fact all of that you are argee is based on prior and actual knowledge of something, or "related metaphors" for call them in some way.

If you read those 2 post and are able to get what Im writing, then you will be able to see why your argumentations about "discoverability" or "why they dont try this instead of that" not depend on the language itself, but in the person that do it.

I quote myself


>  -- I mean, if you will experiment all posible options, why not include some bash code in python and run it or the other way?
-- your answer: Are you crasy that will not work!
-- O yea, I see in you previous experience.
-- What is the point?
-- Only that, normally you repeat yourself, I mean, if with some little knowledge of the language you try to see how things change or how a comma or [] or {} affect certain output is because you already know something of the language and some of the previous work you have... and
-- thus I dont get your point?
-- Simple, go with your mom, or capture a person out there... there are millions in the worl, sure you can grab 1
-- but that is...
-- that is my point, put it in front of your prefered wawa thing (or your prefered editor) and say "program for me whatever you can with try and error", go out, take a cofee, met some 1 new, return and see what the persona have for you .
-- blah
-- yea, I say that to... blah, blah, blah or wawawa :P.


Yes, go, take your mom in front the computer or a grandfather or a unknow people that doesnt have interest in computers, languages and related. Then put it to "discover" the language without giving guides, books or internet access. If is a person that doesn't know English, that would be also perfect ;).


Now say me, how many of the "discoverability" is intrinsic to the language and how many to the person? lol.

---

### Post by Wybiral on 2007-10-22
> **hecato said:**
>  ...
Now say me, how many of the "discoverability" is intrinsic to the language and how many to the person? lol.

I'm sorry, I still don't have a clue what you're saying. The point was that some languages, Python being one of them, are naturally more "uniform" (to steal the description from cwaldbieser). The objects seem to inherit from a common base so it's easy to exchange them and make educated guesses as to how a particular object is to be used (without having to constantly run to a reference).

Of course you need a reference when you're learning any language, but languages where the functionality or the standard library have a well thought out convention will be easier to extrapolate your knowledge.

Back to your point about Python code not working with messed up indention, despite C still working. What happens when you mess up the open and close brackets in C? The same thing that happens with the indentation in Python, so that really doesn't make any point.

---

### Post by hecato on 2007-10-22
A yea, I guess uniform is more to what you are trying to say, but discoverability is bit different, but both of them are bound to persons not to things, we are the ones discovering (or watching more carefully), not the things saying to us "ey see me here!".


"will be easier to extrapolate your knowledge", only if you know enough of it to explore it. People have knowledge of what language mean, but programming language has other context and connotations.

Uniformity for a person that is inside the  programming world would be very nice (less things to learn, with great range of applications, using different things the same way). Though this concept has no sense for a "normal person" I ask again to take your mother, father, grandfather, etc (poeple that dont know or are not interested in the subject matter), you will see that discoverability or being "more specific less rough" uniformity only have sense to persons that already know programming concepts and programming languages.

There will be no 1 language that is uniform or discoverable enough for an not versed person in some programming  language or concepts, that will let them do programms (even that for programmers those or that language have such properties).

That is what Im saying, this is subjetive and thus pertinent to each **different** person. Yes there are people that is more easy to learn bash to python, or C++ to java, etc, but there is also people that doesnt know nothing of those languages and all properties that others (us programmers) see in them have no sense for those people (they should become programmers or versed in some concepts for see what we are trying to argue about language properties that **versed people** can see in them).

But say me, if a property depend in if you are or not versed in something, is really a property or is something subjetive?, or that depend in knowledge?, thus that "property" have only usage sense if you know what you are talking about.

Yes it can continue being a property of the language, but has no usage if you are not versed.

---

### Post by pmasiar on 2007-10-22
> **hecato said:**
> I have guess that people not will be able to grasp beforehand what I say... lol.


If you think twice as much as you type, and type  half as much as you think, it will be easier to understand. :-) I admit I just skipped over your posts after the first one  - it does not make much sense to read it, so I did not wasted my time.

---

### Post by Wybiral on 2007-10-22
> **hecato said:**
>  ... 

Once again, I'm sorry, but I don't understand what you're saying. I'm especially sorry if you aren't a native English speaker, I'm trying to get your point.

My point is that programmer or not, Python has a clean standard for its objects. For instance, the "==" operator means "equal to", so why should it not be able to compare two strings? Or any object instances (of the same type) that need to be compared?

By doing this you can safely assume that when you need to compare two instances of the same class, you can use the "==" operator. And you didn't even have to look at a reference!

You can use "print" to print the string representation of an object (because the string representation is overloadable in Python, just like the "==" operator). This is a good thing because you don't have to look for a manual and find that you need to use a "print_integer". You just use "print".

Python has native support for iterators... So when you're trying to iterate over a container of objects, chances are a simple "for obj in objects:" will work. No need to consult a reference.

---

### Post by hecato on 2007-10-22
> For instance, the "==" operator means "equal to", so why should it not be able to compare two strings? Or any object instances (of the same type) that need to be compared?

Im not talking about that.

>  And you didn't even have to look at a reference!
Yea, but we are programmers, I have tried with the persons that I have at hand (not programmers), and asked them to write a Python program and a Bash program that do whatever they want.

The answer of 1 of that persons say me 

> wtf are you talking about!, I dont know that, even I dont know the word "Python", I dont know of what you are talking... is like if I ask you "how many sandbags can make the cast of that column?" is like if there come a doctor and he ask you how to remove the apendix? or ask you about how many vertebrae your spine has and how they are classified.

See, the properties that "we" argee can be more clear in one or other programming language or designed for that, but we can see them because we are inside the whole, they are not general properties that any1 can use/see...

haha, even the person doesnt know what mean "python" or "bash", this person also dont know that for example keywords are in english (even know that programming languages use keywords and has sintaxis...), and this person also dont know what we understand be variable or object.

A foreing person will not be able to guess that a "hello world in python" would be some like

print "hola"

Even that is as easy as that. They doesnt know or have any significant idea what we know like "hello world programme", but a programmer perhaps can test by try and error things that he know or taking a brief look at a reference.

And also will not be able to "discover" loops or generators (or see that they are unified in the design of iterators),  (or know that this way of programming is the imperative way). 

> 
My point is that programmer or not, Python has a clean standard for its objects.

Yes you are right, the language itself is designed like that.

But my point is not that, is about the argee "if this is more discoverable than the other" (taht depend on the person, not in the design of the language, because different concepts impact in different ways persons): those concepts we argee only has **sense of usage** for a versed person, and thus depend in the own person "how to get it". You know if you dont have good handling of OO, you will fail in use an OO language (doesnt matter you are using C++, java, Python, PHP or even some macros in asm for support OO, or even try to use C like in GTK and other projects).

---

### Post by pmasiar on 2007-10-22
seems to me we found yet another kind of troll

---

### Post by Wybiral on 2007-10-22
> **hecato said:**
> See, the properties that "we" argee can be more clear in one or other programming language or designed for that, but we can see them because we are inside the whole, they are not general properties that [COLOR="Red"]any1[/COLOR] can use/see...

haha, even the person [COLOR="Red"]doesnt[/COLOR] know what mean "python" or "bash", this person also [COLOR="Red"]dont[/COLOR] know that for example keywords are in english (even know that programming languages use keywords and has [COLOR="Red"]sintaxis[/COLOR]...), and this person also [COLOR="Red"]dont[/COLOR] know what we understand be variable or object.

A [COLOR="Red"]foreing[/COLOR] person will not be able to guess that a "hello world in python" would be some like

print "hola"

Even that is as easy as that. They [COLOR="Red"]doesnt[/COLOR] know or have any significant idea what we know like "hello world programme", but a programmer perhaps can test by try and error things that he know or taking a brief look at a reference.

I'm not arguing that programming can instantly be figured out be a non-programmer. I don't get the point of this. It doesn't prove that some languages naturally have more consistency between features.

> **hecato said:**
> But my point is not that, is about the [COLOR="Red"]argee[/COLOR] "if this is more discoverable than the other" ([COLOR="Red"]taht[/COLOR] depend on the person, not in the design of the language, because different concepts impact in different ways persons): those concepts we [COLOR="Red"]argee[/COLOR] only has **sense of usage** for a versed person, and thus depend in the own person "how to get it". You know if you [COLOR="Red"]dont[/COLOR] have good handling of OO, you will fail in use an OO language ([COLOR="Red"]doesnt[/COLOR] matter you are using C++, java, Python, PHP or even some macros in asm for support OO, or even try to use C like in GTK and other projects).

I disagree. Some things are naturally easier to figure out because they follow a pattern or convention. You appear to be arguing otherwise.

PS: Sorry about the red, my spell-checker has been rather aggressive lately.

---

### Post by hecato on 2007-10-23
Yes, but you need at less be able to recognogize a part of the pattern, Im argueen about previous experience and actual knowledge. And from that saying that if the analisis or design point of language itself it can have certain propierties they can be verifiable. But others need at least some grasp of those concepts for they to be able to see them.

Example[LIST]
[*]Gravity: a lot of people have jumped before the "discover of gravity", the water flow, planets rotate around sun and all that, but until some1 was able to explain to us, we haven't see it before and thus being not able to see it. Even that nature have lots of patters and real intelligent things (a scientific can say you is marvellous world to discover), other people is not able to see it, until they grasp some concepts (doesn't matter the perfect a scientist can consider it or the perfect it is in fact).[/LIST]Im not argueen that some things have more or less patterns or similarities or uniformity, Im argueen that doesnt matter those things have it, if you don't understand it, then is like if they where not there for you.


By example, Im sure that persons at #bash can "discover" pretty things in his tries (if they try, because at less they have answered my noob questions when I have 1), but for me that really don't use that language, would be more hard to discover things that they can discover more easy.

At the end, properties of things are there and don't let the existence if some1 ignore it, but the perception of each person can take the concept different and in different time too. Thus the properties are not debatable. But say that the perception of all and each people about that would be the same or best than others, is a real hard thing to demostrate. For example, Im sure that for me was more easy grasp some C++ than some Java ;).

---

### Post by slavik on 2007-10-23
I still don't understand how anyone can argue that a language (programming or natural) can be "discoverable."

pmasiar, If I gave you Perl code, or Scheme code and explained some syntax about them, you would be able to read it, but if I told you to write a program in it, you'd have a hard time.

I was born in Ukraine and studied the ukrainian language in school (for 4 years). I can keep a conversation in ukrainian, but I can read it and understand it with little difficulty.

Same thing with Python. I can read the code effortlessly, but writing something would require me to go to google (or get a book).

Today for example, I read a tutorial on CSS, if I hadn't read it, I would not figure out that you can have something like this:
```

td { border: 10px; }

```
and when included into an html file properly, any <td> tag automatically takes that style (think of it as the browser merging the css file and the html file intelligently).

---

### Post by LaRoza on 2007-10-23
> **slavik said:**
> I still don't understand how anyone can argue that a language (programming or natural) can be "discoverable."

pmasiar, If I gave you Perl code, or Scheme code and explained some syntax about them, you would be able to read it, but if I told you to write a program in it, you'd have a hard time.



I am somewhat having trouble with this 'discoverable' concept also. Could an example be given?

@slavik I believe pmasiar has experience with Perl, and most likely Lisp - style languages, but I understand that reading and writing code are different.

---

### Post by hecato on 2007-10-23
> 
I still don't understand how anyone can argue that a language (programming or natural) can be "discoverable."

yes, 
[LIST=1]
[*]there are no persons that know certain "dead languages" (natural), but there are specialized people with investigation, observation I dont know in fact, that can translate some fragments. Thus languages can be discoverable.
[*]When a person born, he doesnt know is is in Italia, Africa, México, USA or any other place in the world, also doesnt know the environment (is learning to diference sounds, images, etc... senses), and they normally at end terminate learning it, and some times constructing sentences that they previously havent seen ;) (I consider that another proof). Learning has some discover in it (like learning practising), you cant really learn if you don't understand.[/LIST]The point here is if a language as or no properties (like unity, keywords, support for OO paradigm, ...), those properties are only visible for a versed person.

The real argue is about, how a not versed person become versed ;). You probably will say that Python is more easy than x lang and has more properties like uniformity, OO, etc. The point is that some people will find that x lang as easy as python ;).

> 
trouble with this 'discoverable' concept also.

I think that concept is relative to persons (see anterior paragraph) becoming from not versed to versed in that language, but that depend in the person more than the properties that versed persons can see, know or evaluate in them.

---

### Post by slavik on 2007-10-24
a 2 year old doesn't dicover the language, he analyses it.

if I give you two cubes of the same size but different colors and I call them differently, you can realise that I might be reffering to the color (or not).

if a child grows up hearing 2 languages, he will learn both. But show me a person who given a book in another language can learn the language from just that book and I will give you a million dollars (USD).

if I tell you that 'hello' is an array and tell you to access the 5th element, you giving me hello[4] would be valid in any language who's syntax resembles Algol. Read up on Algol 60 syntax, you will see something like an interesting mix of Python, PASCAL, C, even BASIC.

One line of the Algol syntax heritage: Algol -> BCPL -> B -> C (Algol also influenced PASCAL).

Anyone who knows either of those languages (Python, PASCAL, C, BASIC, or something resembling them) could and MUST understand the ALGOL code samples. It's like me reading a slavic language that uses the latin alphabet (polish and serbian come to mind, although serbian can be written in cyrilic, too).

---

### Post by pmasiar on 2007-10-24
> **LaRoza said:**
> I am somewhat having trouble with this 'discoverable' concept also. Could an example be given?

[post # 38](http://ubuntuforums.org/showpost.php?p=3558284&postcount=38) above

---

### Post by hecato on 2007-10-24
But you know beforehand what you want to show to us.

Sure, Python shell is nice to try and error (discoverability?).

But why if

```

l3-l1

```

That doesn't work... um why I can add, but not substract?, I have guess that + is the opposite of -, but the abstraction or relation with you can + all, doesn't fall with the complement - also know by all.


I will say that the shell is perhaps more easy and amigable for try and error (instead of use the term "discoverability").

---

### Post by pmasiar on 2007-10-24
> **hecato said:**
> But you know beforehand what you want to show to us.

I swear I did not know how to join two lists, and above is exactly (or close) what I did to find out. I never bothered to read docs where it is described, if any.

I still think it is remarkable I can do that (without reading the docs), and I don't know any other language which allows that. Yes I know it is possible with Ruby, but I didn't found any valid reason to learn Ruby yet :-)

Why not subtract? Maybe you **do** have to read docs sometimes? ;-)

---

### Post by aks44 on 2007-10-24
> **pmasiar said:**
> I swear I did not know how to join two lists [...] I still think it is remarkable I can do that (without reading the docs), and I don't know any other language which allows that

With any decent C++ IDE it is even easier: begin typing, wait for the auto-completion box to pop up (or activate it with a keybind), choose...  :p

Sorry I couldn't help, now I'm gonna hide myself. ;)

---

### Post by DavidBell on 2007-10-24
> **aks44 said:**
> With any decent C++ IDE it is even easier: begin typing, wait for the auto-completion box to pop up (or activate it with a keybind), choose...  :p

Maybe said in jest but that's exactly what I do. 

Include the library, type namespace then *doublecolon* to get the list of classes; type variable then *dot* to get a classes members; select the function then hit *openbracket* to get the arguments. At any point in the above hit **F1** to get docs (if it's a standard library).

Just wish I could find a linux IDE that does it as smoothly as MSVS.

DB

---

### Post by Acglaphotis on 2007-10-24
I like python for its simplicity and flexibility (import ANYTHINGIWANT).

I hate python because it doesn't have /* */ comments.

---

### Post by pmasiar on 2007-10-24
I use multiline string as multiline comment :-)

---

### Post by Acglaphotis on 2007-10-24
Docstrings?...its just not the same...

---

### Post by hecato on 2007-10-24
Or you can go to a forum or IRC and never see the docummentation :P, lol, or a search.

---

### Post by MacUntu on 2007-10-24
Add braces to python and I'll use it more often. This tabbing thing gives me the creeps... nothing against readable code, but forcing tabs is really a thing that pushes me away.

---

### Post by Wybiral on 2007-10-24
> **MacUntu said:**
> Add braces to python and I'll use it more often. This tabbing thing gives me the creeps... nothing against readable code, but forcing tabs is really a thing that pushes me away.

Forced braces creep some people out. :)

---

### Post by pmasiar on 2007-10-25
> **MacUntu said:**
> Add braces to python and I'll use it more often. This tabbing thing gives me the creeps... nothing against readable code, but forcing tabs is really a thing that pushes me away.

This is your loss. Here is what Python developers think about braces:
```

>>> from __future__ import braces
SyntaxError: not a chance (<pyshell#1>, line 1)

```
:-)

---

### Post by Anzan on 2007-10-25
The sense of humour "built-in" to Python is one of the reasons I like (learning) it.

---

### Post by hecato on 2007-10-25
> 
Add braces to python and I'll use it more often. This tabbing thing gives me the creeps... nothing against readable code, but forcing tabs is really a thing that pushes me away.


<sarcasm>I don't do poesy like [http://en.wikipedia.org/wiki/Sonnet](http://en.wikipedia.org/wiki/Sonnet) because all those not natural things imposed for write it... it limit my creativity, mmm and even it should rhyme!!!!!
</sarcasm>

One time you get used, you will get it.

Be fact, the first time I see this, I say o yea, This is very effective for not see crappy formatted C/++/java/bla bla from a beginner in this language.

---

### Post by red_Marvin on 2007-10-25
> **MacUntu said:**
> Add braces to python and I'll use it more often. This tabbing thing gives me the creeps... nothing against readable code, but forcing tabs is really a thing that pushes me away.

Maybe I'm taking your words too literally, but you are not forced to use tabs per sé, 1/2/4/... spaces are just as fine. 

What's important is to use consistent indentation, and that is something that's generally required even if not at the language level.

---

### Post by Mirrorball on 2007-10-25
I'm afraid of the answer, but... about people that don't like Python because it forces indentation, don't they indent the code they write in other languages?

---

### Post by Jessehk on 2007-10-25
> **Mirrorball said:**
> I'm afraid of the answer, but... about people that don't like Python because it forces indentation, don't they indent the code they write in other languages?

Yes, but errors in indentation don't cause errors in programs. These errors can occur when you accidentally mix tabs and spaces, when you're copying and pasting snippets, or in many other situations. I've never written anything even remotely big in Python (maybe 500 LOC at most), but I've already run into that problem.

---

### Post by LaRoza on 2007-10-25
> **Jessehk said:**
> Yes, but errors in indentation don't cause errors in programs. These errors can occur when you accidentally mix tabs and spaces, when you're copying and pasting snippets, or in many other situations.

Forgetting braces can cause errors also. In fact, such errors can be harder to find, if you have your braces indented, and one is in to far, you think it is closed, because it looks closed.

Use spaces, 4 for safety. You'll never have this problem then. Copying and Pasting can be an issue, but is bigger with tabs, not spaces.

---

### Post by Wybiral on 2007-10-26
> **Jessehk said:**
> These errors can occur when you accidentally mix tabs and spaces, when you're copying and pasting snippets, or in many other situations. I've never written anything even remotely big in Python (maybe 500 LOC at most), but I've already run into that problem.

Don't copy-and-paste code that uses tabs (and if you do, convert it). I think of this like using non-standard code from any language, or basically any code you pick up from the net and don't proof-read to make sure it's sane. Would you copy-and-paste random C code directly into a large C project without checking it and adjusting it to your standard / convention? But if you convert all the tabs to four spaces, you should never have a problem.

Also, using an editor with graphical whitespace helps. Most modern editors have an option to show tabs as arrows and spaces as dots. It's nearly impossible to miss a mix of them.

---

### Post by nanotube on 2007-10-26
> **LaRoza said:**
> 
Use spaces, 4 for safety. You'll never have this problem then. Copying and Pasting can be an issue, but is bigger with tabs, not spaces.

i'd say, use tabs, for safety. you'll never have this problem then. copying and pasting are not an issue either way, because i have never yet seen a clipboard that can hold spaces but not tabs (or vice versa). since it appears that your argument can be reversed without losing correctness, i'd venture to say that it has little validity. :)

(can you guess that i'm in the "use tabs" camp? :) cheers to fellow tab-user cptpicard! :) )

---

### Post by cellerit on 2007-10-26
you guys should try LUA. ( [www.lua.org](www.lua.org))
I use python too but still prefer lua to it, its constructs are even simpler than in python. The only thing it lacks compared to python is the many many libraries that ship with python. LUA is a bit better to be embedded inside another application i guess.
The thing is any object in lua is a table, yes even functions and integers. This makes callbacks really easy to implement.
For example:
random_function = function( a, b, c )
    dostuff()
end

a = someobject()
a.somecallback = random_function

voila.
to go through a dictionnary?
some_dictionnary = { a = "hello", b = 2345, c = random_function }
for kev, value in some_dictionnary do
    print( repr(value) )
end

Well my point of view. On the other hand you have to use nasty if then else end structures but at least blocks are explicit.

---

### Post by LaRoza on 2007-10-26
> **cellerit said:**
> you guys should try LUA. ( [www.lua.org](www.lua.org))
I use python too but still prefer lua to it, its constructs are even simpler than in python. .

This has nothing to do with the topic of this thread. Please don't hijack. You can create your own thread on Lua if you want, and maybe people will give input.

---

### Post by Wybiral on 2007-10-26
> **cellerit said:**
> you guys should try LUA. ( [www.lua.org](www.lua.org))
I use python too but still prefer lua to it, its constructs are even simpler than in python. The only thing it lacks compared to python is the many many libraries that ship with python. LUA is a bit better to be embedded inside another application i guess.
The thing is any object in lua is a table, yes even functions and integers. This makes callbacks really easy to implement.
For example:
random_function = function( a, b, c )
    dostuff()
end

a = someobject()
a.somecallback = random_function

voila.
to go through a dictionnary?
some_dictionnary = { a = "hello", b = 2345, c = random_function }
for kev, value in some_dictionnary do
    print( repr(value) )
end

Well my point of view. On the other hand you have to use nasty if then else end structures but at least blocks are explicit.

Those examples don't really show any reason why Lua would be preferable to Python:

```

def random_function(a, b, c):
    doStuff()

a = someobject()
a.somecallback = random_function

some_dictionary = { a : 'hello', b : 2345, c : random_function }
for (key, value) in some_dictionary.iteritems():
    print(value)

```

Python is also really easy to embed. Look at GIMP or Blender.

---

### Post by pmasiar on 2007-10-26
It is frustrating to answer to the same myths and misunderstanding again and again. "Myths about Indentation" in first post IMHO answers your misunderstanding about whitespace, did you read it? 

**consistent** indent in the whole block is all you need, so ie this is valid, even if ugly and not standard:

```

if x == 2:
                      print 'true'
else:
 print 'false'

```

> **Jessehk said:**
> Yes, but errors in indentation don't cause errors in programs. These errors can occur when you accidentally mix tabs and spaces

Of course. Errors can occur if you mix round and squiggly braces, too. Easy solution: Don't mix them. :-)

Seriously. All decent editors (hundreds of them) can be set to replace tab with certain number of spaces. Do it, and you are set. Case closed. 

I suspect that this is devious test: Guido dos not want users who are not trainable and refuse to adjust. If someone cannot learn using decent editor, let him code in C++ or PHP instead of asking stupid questions at Python forums :-D

>  when you're copying and pasting snippets

Listen, kid. Here is a penny, get a decent editor, and you will never have that problem again. Seriously. Decent editor can convert tabs to spaces for you, keep block indent level, and indent/dedent whole block of lines. If it is a big problem for you to learn using normal programmer's editor, and you insist on editing sources in notepad, I will feel much safer if your code is in PHP, so I can be sure I will never see it.

If you do not understand that it is **your loss** not to use decent tools to do your job correctly, talking about anything else hardly makes sense. Python makes harder to edit sources by couple bad tools not suited to it, when hundreds of good tools are available and free to use. Yes, I admit that. Please stop whining about it, and lets talk about real issues.

---

### Post by nanotube on 2007-10-26
> **pmasiar said:**
> 
Seriously. All decent editors (hundreds of them) can be set to replace tab with certain number of spaces. Do it, and you are set. Case closed. 
<snip>


i agree, and i think a coding editor is key to this. 

i think the argument is coming from the fact that in a "normal" editor created for text, whitespace has a special feature of being invisible, and thus harder to manipulate. use a coding editor, and whitespace characters become just like any others - easy to see, easy to manipulate. so use a coding editor, and the "special" invisibility feature of whitespace will disappear.

---

### Post by LaRoza on 2007-10-26
> **pmasiar said:**
> 
Listen, kid. Here is a penny, get a decent editor, and you will never have that problem again.

Not even a penny, the best are free.

---

### Post by pmasiar on 2007-10-26
You don't even have to see tabs and spaces, or care about the difference between them. If your editor can replace tabs with 4 spaces, use it. If it cannot, delete it and use one which can - it has also many other nice features which you will love.

[Python Style Guide](http://www.python.org/dev/peps/pep-0008/) says: 
"Tabs or Spaces?
**Never mix tabs and spaces.** ...  Code indented with a mixture of tabs and spaces should be converted to using spaces exclusively. ... When invoking the python command line interpreter with the -t option, it issues warnings about code that illegally mixes tabs and spaces"

Just accept the difference between [tab as character and result of pressing the TAB key](http://www.jwz.org/doc/tabs-vs-spaces.html).

In Python 3000 mixing tabs and spaces will be error: "E101 indentation contains mixed spaces and tabs", and tabs will generate warning: "W191 indentation contains tabs".

---

### Post by pmasiar on 2007-10-26
interesting discussion about User who likes Python, but significant whitespace is a problem for him, [because he is blind](http://groups.google.com/group/comp.lang.python/browse_thread/thread/80654a87bfa89e3b): As a solution for him (and for other Python haters) might be, as Alex suggested, pindent.py, which can add '# end' at the block ends. BTW included in standard distro.

---

### Post by pmasiar on 2007-10-26
and to switch discussion away from whitespace so something less whining and more about the substance: [How learning Python made me a better C++ programmer](http://www.ginstrom.com/scribbles/2007/10/05/learning-python-made-me-a-better-cpp-programmer/)

---

### Post by evymetal on 2007-10-31
I've been coding python at work for about 6 months for the kind of thing I would previously have used Perl / C for.

My Opinion:
For most software the 90-10 rule applies (10% of the code takes 90% of the time), and writing python is so damn quick that I would definately suggest it or Perl for 90% of your code.

If I am writing a text-processing module or something that only I am going to read then I write Perl - I love the way that you can write the same thing in 2,000 different ways, it lets you think about your code in completely different ways.

If someone else needs to read your code - don't use Perl! Obvious reasons apply.

Also, coming from a mathematical background, Python's syntax is just good for logical structure, and I have yet to come across a bug that was the result of using python's syntax incorrectly (as opposed to a design bug like using a function with a lock itteratively...). The one exception is the "".join method, which I really think should be a method of a list (returning a string) and not of string.

---

### Post by pmasiar on 2007-10-31
> **evymetal said:**
> The one exception is the "".join method, which I really think should be a method of a list (returning a string) and not of string.

All languages have idioms, and some are not as obvious  (unless you are dutch, of course :-) ). If you ask on python-devel list (or google it - it is so obvious question it was asked many times I guess) you will find that being able to apply this method on any sequence (including iterators), not only lists, makes it more flexible than as in your proposal. I don't know details, but experience suggests Guido had good reason do it that way.

---

### Post by CptPicard on 2007-10-31
IMO following the whitespace discussion and participating in it myself gives me the impression that Ockham's razor applies -- if whitespace needs to be defended at length with all kinds of "use a special editor" arguments, something is amiss...

---

### Post by pmasiar on 2007-10-31
If those cars after all those years still need special roads, maybe we need to abandon them too? :-)

---

### Post by red_Marvin on 2007-10-31
Or what about those curly braces? k&r/Allman/bsd/...?

Seriously though, I'd like to hear how the opposers (of syntactic whitespace) prefers to indent their code.

IMO there's no need for special editors to convert between tab/2spc/4spc indenting, in most cases a usual search and replace will do, -easier than converting between k&r and gnu style for c...?

(I might sound somewhat aggresive, but while I have my views set, I'm interested in the other side's arguments, and only debate for fun)

---

### Post by dataw0lf on 2007-10-31
Most arguments I've heard against enforced whitespace come from either people who haven't used Python, or those who've used Python for all of a week.  

I, too, hated enforced whitespace when I first started learning Python (2000, I think?), but it only took me a couple trivial scripts and I quickly came to love it.

---

### Post by evymetal on 2007-10-31
> **pmasiar said:**
> All languages have idioms, and some are not as obvious  (unless you are dutch, of course :-) ). If you ask on python-devel list (or google it - it is so obvious question it was asked many times I guess) you will find that being able to apply this method on any sequence (including iterators), not only lists, makes it more flexible than as in your proposal. I don't know details, but experience suggests Guido had good reason do it that way.

I think this is something that people just don't agree on, I've certainly heard pleanty of people call for it to be changed - but now it's there it would completely break compatibility to change it to the other way (since you can call the list methods on a string so your code wouldn't throw any exceptions if you ran it in a modified interpreter).

---

### Post by pmasiar on 2007-10-31
Plenty of people calling to remove whitespace to convey structure? Hell no! never! Not python programmers.

Whitespace annoys you for first 15 minutes. After that, all other languages are annoying, because they **don't** use witespace, and is easy to mess code structure.

OK, this is it. I refuse to talk about whitespace anymore - read links in original post, all myths are explained there.

You are of course free to ask for it, here or anywhere else. If you want answer, fire your python shell, and do:

```

from __future__ import braces

```

and read the answer.

---

### Post by tyoc on 2007-10-31
I love spaces from start, even before I know python... I think I was tidy about those things in my code... and dont like programms in C that has strange sintaxis by the way that they can obfuscate code (sometimes with a contest... but sometimes without they see it).

---

### Post by Tux.Ice on 2007-11-10
pythons good

---

### Post by shawnhcorey on 2008-02-15
> **pmasiar said:**
> I know Perl and CPAN. BTW, Python has CheeseShop :-)

There is one good reason to avoid Perl: it's quirky syntax. See "Why I love/hate Perl" discussion for details.

And the URL for this CheeseShop?

Perl has its problems; Python has its problems.

```
$ python
Python 2.4.4c1 (#2, Oct 11 2006, 19:53:58) 
[GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 1/2
0
>>> 

```

Or shall I talk about something equally esoteric?  Like:

Perl:
```
0 .. n
```

Python:
```
0::n
```

What we were taught in grade school:
```
0,1,2,...,n
```

Neither language comes close.


Given the power and memory of modern computers, I think that they can cope with languages that are not totally efficient...provided that they are understandable.

I once was taught something called Polish notation.  That was when, in writing C, to lead your variables with a notation that indicates its datatype.  Like 'iCount' or 'szName'.  Most people think this is good.  But, in Perl, when I say '$Count' or $Person{name}' this is bad because we all know that '$%@' is cussing, and therefore is BAD PROGRAMMING (or the Devil will take your soul).

Grow up.  Perl is not perfect.  Python is not perfect.  You happen to like Python.  I happen to like Perl.

But I will not accept that your choice is better than Perl.  And if you post anything that makes that claim, I will argue the point.

---

### Post by LaRoza on 2008-02-15
[http://pypi.python.org/pypi](http://pypi.python.org/pypi)

That will change in Python 3000. The reason for it is because they are integers. (Try 1./2)

Grade school isn't a basis for programming. I was also taught "2 x 3", which I never use for anything.

That is "Hungarian Notation", Polish Notation is prefix notation. 

He is old (compared to me at least)

If you want to argue the point, use the threads dedicated to it.

---

### Post by shawnhcorey on 2008-02-15
> **LaRoza said:**
> [Why I love/hate Perl]("http://ubuntuforums.org/showthread.php?t=577596") for reference.

Again missing the point.

**ALL LANGUAGES ARE ESOTERIC.**

It just depends on what sort on lunacy makes you feel comfortable.  Arguments about it are between you and your god; with a possible laugh for the rest of us.

But Perl is my favourite language.  I will learn other languages; I have in the past:  one of my past favourite languages was 6502 Assembler.

The problem I have with Python advocates is that they think their language is "god-touched", it can do no wrong.  But it can:

```
$ python
Python 2.4.4c1 (#2, Oct 11 2006, 19:53:58) 
[GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 1/2
0
>>> 

```

I am tired of postings that promote Python as the ultimate answer:  it's not.

As far as the best language to first learn, I think it would be 6502 on a Commodore 64.  It would teach you a whole lot about limited resources and tight coding that modern languages cannot.

---

### Post by LaRoza on 2008-02-16
> **shawnhcorey said:**
> 
The problem I have with Python advocates is that they think their language is "god-touched", it can do no wrong.  But it can:

```
$ python
Python 2.4.4c1 (#2, Oct 11 2006, 19:53:58) 
[GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 1/2
0
>>> 

```

I am tired of postings that promote Python as the ultimate answer:  it's not.

As far as the best language to first learn, I think it would be 6502 on a Commodore 64.  It would teach you a whole lot about limited resources and tight coding that modern languages cannot.

pmasiar was a Perl user for a long time.

Try that in C:

[php]
#include <stdio.h>

int main(void)
{
    printf("%d\n",1/2);
    return 0;
}
[/php]

Python is strongly typed, and since the behavior of integer division is what you dislike, that will change in Python 3000, so find something else :-)

Note: Neither pmasiar nor I think Python is all powerful. He advocates the right tool for the job. Python's readability and other features make mainaining code easier than Perl in his experience as stated before (in other threads).

Your problem is with Python users, so it has nothing to do with the language. I don't like Scheme programmers in general, but I don't use that as a basis for not liking Scheme.

As for the "best" language, I would say Lisp.

---

### Post by shawnhcorey on 2008-02-16
> **LaRoza said:**
> [http://pypi.python.org/pypi](http://pypi.python.org/pypi)

That will change in Python 3000. The reason for it is because they are integers. (Try 1./2)

Grade school isn't a basis for programming. I was also taught "2 x 3", which I never use for anything.

That is "Hungarian Notation", Polish Notation is prefix notation. 

He is old (compared to me at least)

If you want to argue the point, use the threads dedicated to it.

Ooooh, wwoooooww.  You are speaking some sort of geek I don't understand.

As far as 1/2 is concerned, I have ask (non-geek) people what is "one divided by two" and most of them replied, "a half".  On occasion, I hear, "Zero point five."  I have never heard zero.

The point is (the same as before) ALL LANGUAGES ARE ESOTERIC.  It just depends on what lunacy you accept.

Oh, yes:  All the problems with Python will be fixed in 3000.  And all the problems in Perl with be fixed in Perl6.  Anyone can may promises.

BTW, datatypes were invented by compiler writers, to make they job easier; not to make programming easier.  Learn the difference.

---

### Post by LaRoza on 2008-02-16
> **shawnhcorey said:**
> Ooooh, wwoooooww.  You are speaking some sort of geek I don't understand.

As far as 1/2 is concerned, I have ask (non-geek) people what is "one divided by two" and most of them replied, "a half".  On occasion, I hear, "Zero point five."  I have never heard zero.

Oh, yes:  All the problems with Python will be fixed in 3000.  And all the problems in Perl with be fixed in Perl6.  Anyone can may promises.

BTW, datatypes were invented by compiler writers, to make they job easier; not to make programming easier.  Learn the difference.

Thanks for calling me a geek. (Really, I like being called a geek)

See my C example. Computers will give the answer "0".

Let me put it another way, you need 2 people to have 1 child. How many children will you get with 1 person?

Data types are part of processors. Also, I think that dynamic languages make programming much better, but I believe date typing should be strong.

Try this Perl code:
[php]
#! /usr/bin/perl
print(1 + "2");
[/php]

That is inexcusable in my opinion.

---

### Post by LaRoza on 2008-02-16
I think you didn't understand Polish notation, Polish notation (also called prefix notation) is:

```

+ 1 1

```

Instead of:

```

1 + 1

```

Reverse Polish Notation is:

```

1 1 +

```

The reason for such notation is that the order of operations is moot, and it is very easy to write a program to do such math.

Hungarian Notation is the way of naming variables.

---

### Post by pmasiar on 2008-02-16
> **shawnhcorey said:**
> And the URL for this CheeseShop?

Google is your friend: [http://www.google.com/search?q=python+cheeseshop](http://www.google.com/search?q=python+cheeseshop)

> Grow up.  Perl is not perfect.  Python is not perfect.  You happen to like Python.  I happen to like Perl.

But I will not accept that your choice is better than Perl.  And if you post anything that makes that claim, I will argue the point.

Well, maybe you need to grow up and learn use Google first, before giving lectures? :-) I used Perl for almost 5 years, and about dozen languages before that. Let me mention that from your confusion about Hungarian notation, you are quite far from expert opinion, IMHO at least.

But you don't have to accept anything, be happy with Perl if it suits you more. I have no problem with that, just sucks to be you but do what you want if you don't hurt others :-)

If you want to engage in discussion about Perl, please do it in appropriate thread. Read it first, so we don't repeat the same stale arguments. Then, check thread about Why I love Python (also linked from FAQs).

If you have something to add, please do (in those threads). Consider doing some research before posting, to avoid embarrassments tho. :-)

---

### Post by LaRoza on 2008-02-16
> **ghostdog74 said:**
> 
Last advice: Don't get distracted by the noises here.

Yes, sorry about that.

---

### Post by pmasiar on 2008-02-16
> **shawnhcorey said:**
> Again missing the point.

**ALL LANGUAGES ARE ESOTERIC.**


You are again confused and don't quite understand terminology you use: Neither Perl or Python are [http://en.wikipedia.org/wiki/Esoteric_languages](http://en.wikipedia.org/wiki/Esoteric_languages) :-) Maybe you don't understand the difference, but many people do and you are just making fool from yourself. Of course you are free to continue doing so, it was too quiet for some time :-)

> It just depends on what sort on lunacy makes you feel comfortable.  Arguments about it are between you and your god; with a possible laugh for the rest of us.

Well, I better will not argue with expert lunatic about what language god uses :-)

> But Perl is my favourite language.  I will learn other languages; I have in the past:  one of my past favourite languages was 6502 Assembler.

I prefer more "ortogonal" instruction set, like PDP/11. Minicomputers have in average better-thought instruction system, IMHO. YMMV of course. If you think I know only Python, let me mention that when I started programming 25 years ago, C was hot news... :-)

But I am not forcing my favorite "clever" language (Forth) to beginners, because beginners have different needs.

> I am tired of postings that promote Python as the ultimate answer:  it's not.

As far as the best language to first learn, I think it would be 6502 on a Commodore 64.  It would teach you a whole lot about limited resources and tight coding that modern languages cannot.

I am not sure where I said that "Python is ultimate answer". We were talking about best first language to learn programming, which is after long discussions in other threads (and poll), Python. If you think 6502 Assembler, it just shows how misguided your advice is. Much better tool to learn about limited resources is cross-platform C - as a second language of course.

Again, if you feel like arguing about that, please do so in appropriate thread (see sticky FAQ), **after reading previous discussion** - I doubt that someone with gaping holes in understanding of CompSci like you can add something new, but let's see.

And last:
```

print 1.0/2 

```
works correctly - and Guido considers integer division one of the blunders, was public about it for a long time, and it will be first thing changed in Py3K next year.

---

### Post by shawnhcorey on 2008-02-16
> **pmasiar said:**
> Well, maybe you need to grow up....

Same argument, yet again.  If you use Python, you are modern programmer.  If you use Perl, you are a dinosaur.

Sigh.

I am tried of hearing that Python is the perfect language.  And I am tired of hearing that any argument against it will be transfer to some backwater group that nobody looks at.

I will repeat myself:
**ALL LANGUAGES ARE ESOTERIC.**

Perl is just as good as other languages.  Well no, it's better.  That's because it has been around for far longer than Python or Ruby.  The problems they are coping with, it has already solved.

Just because you don't like its syntax, doesn't mean is bad.

BTW, when I followed your link, I got Google, not this fictionalistic "cheeseshop".

---

### Post by shawnhcorey on 2008-02-16
> **pmasiar said:**
> Well, I better will not argue with expert lunatic about what language god uses :-)

I prefer more "ortogonal" instruction set, like PDP/11. Minicomputers have in average better-thought instruction system, IMHO. YMMV of course. If you think I know only Python, let me mention that when I started programming 25 years ago, C was hot news... :-)

Yes, C was hot news back then.  That was because B was so buggered up.  Not sure, check your B manual.  Don't have one?  Well, I do.

I like 6502 Assembler because it forces you to think.  It is a small processor with limited resources.  To program in it, you have to shift things around; you have to plan ahead.  In other words, you have to think.

---

### Post by LaRoza on 2008-02-16
> **shawnhcorey said:**
> 
Perl is just as good as other languages.  Well no, it's better.  That's because it has been around for far longer than Python or Ruby.  The problems they are coping with, it has already solved.

Just because you don't like its syntax, doesn't mean is bad.

BTW, when I followed your link, I got Google, not this fictionalistic "cheeseshop".
I already posted link already for it (I googled it actually)

Python was developed by someone looking at the strengths of other languages, just like most languages. Ruby looked at Python and Perl (among others)

Each one reflects to a degree the preferences of the designer. Open a Python session, and type "import this".

I have a Fortran and Basic manual, do I win a prize?

Do you know Python? Did you have any problems with it?

I realize to someone who is happy with Perl, learning Python is probably useless as it has similar uses, but so many people seem to have opinions on languages they do not know.

---

### Post by shawnhcorey on 2008-02-16
> **LaRoza said:**
> I have a Fortran and Basic manual, do I win a prize?

No.

That's because it's BASIC (Beginner's All-purpose Symbolic Instruction Code) and FORTRAN.

You know, we have totally lost track of the OP; no that's not correct, I have lost track of the OP.  I was upset by other postings and took this thread off to tilt my own windmills.

I apologize to *mockdeep*.  I am really sorry that your request has gotten so far off track, mainly because of my actions.  Please accept my deepest apologies.  I am truly sorry.

---

### Post by ruy_lopez on 2008-02-16
> **shawnhcorey said:**
> 
You know, we have totally lost track of the OP; no that's not correct, I have lost track of the OP.

At least you are man enough to admit it.

---

### Post by LaRoza on 2008-02-16
> **shawnhcorey said:**
> No.

That's because it's BASIC (Beginner's All-purpose Symbolic Instruction Code) and FORTRAN.


You are behind in the times, read the first sentence of this article: [http://en.wikipedia.org/wiki/Fortran](http://en.wikipedia.org/wiki/Fortran)

Even the first manual for Fortran (in 1956) had it spelled "Fortran".

---

### Post by shawnhcorey on 2008-02-16
> **ruy_lopez said:**
> At least you are man enough to admit it.

No.  I do admit I messed up but I haven't apologized to everyone who has read this thread.

I have apologized to the OP in this thread and I have sent a PM to him with an apology.

But I have hijacked this thread to tilt at my windmills; and for that I apologize.

I am truly sorry for the pain I have cause anyone.  I was so caught up in my own feelings that I forgot yours.  Please accept this as an apology.  I am sorry to anyone who has read this thread and has been hurt by it.

The fault was mine.

---

### Post by LaRoza on 2008-02-16
> **shawnhcorey said:**
> No.  I do admit I messed up but I haven't apologized to everyone who has read this thread.

I have apologized to the OP in this thread and I have sent a PM to him with an apology.

But I have hijacked this thread to tilt at my windmills; and for that I apologize.

I am truly sorry for the pain I have cause anyone.  I was so caught up in my own feelings that I forgot yours.  Please accept this as an apology.  I am sorry to anyone who has read this thread and has been hurt by it.

The fault was mine.

Do you want me to move all of our OT posts to another thread?

---

### Post by ghostdog74 on 2008-02-16
even if you move to another thread, it will be pointless as well. I would suggest to delete those OT posts except those that are directed at OP.

---

### Post by LaRoza on 2008-02-16
> **ghostdog74 said:**
> even if you move to another thread, it will be pointless as well. I would suggest to delete those OT posts except those that are directed at OP.

I won't alter this thread without the permission of those that took part in it. It goes agains the UF Staff's general principle of moderating threads we took part it.

---

### Post by ghostdog74 on 2008-02-16
> **LaRoza said:**
> I won't alter this thread without the permission of those that took part in it. It goes agains the UF Staff's general principle of moderating threads we took part it.
Any principles for those starting flames?

---

### Post by LaRoza on 2008-02-16
> **ghostdog74 said:**
> Any principles for those starting flames?

I didn't see anybody flaming, if you feel a post was in violation of the UF Code of Conduct, you can report it. If the post is mine, the other staff will look at it, and the Admins will make the decisions.

---

### Post by ruy_lopez on 2008-02-16
> **LaRoza said:**
> I won't alter this thread without the permission of those that took part in it. It goes agains the UF Staff's general principle of moderating threads we took part it.

You have my permission.

---

### Post by LaRoza on 2008-02-16
> **ruy_lopez said:**
> You have my permission.

(It has been altered)

---

### Post by ghostdog74 on 2008-02-16
> **LaRoza said:**
> I didn't see anybody flaming, if you feel a post was in violation of the UF Code of Conduct, you can report it. If the post is mine, the other staff will look at it, and the Admins will make the decisions.
i should have said "flame-baits" . from the Ubuntu Code of conduct
> 
....
# If the thread is flame-bait (appears to be intended to start an argument or is likely to cause an argument rather than enhance discussion), it will be locked or removed without notice. Individual flame-bait may be deleted or edited at the moderators' discretion. Any users who continue to post in this manner or engage in other questionable practices, like trolling (posting in an attempt to engage people in arguments) may be subject to more serious sanctions.
# If the thread turns into an argument, it can be locked or removed without notice. Sometimes a moderator may split the thread or delete certain portions in order to keep the discussion going, but that is not always possible.
....


I especially want to focus on this one : 
> 
appears to be intended to start an argument or is likely to cause an argument rather than enhance discussion

So in your opinion, if I post things like 
"Use this language, it can do this and its nice to look at. Don't use this ....its ugly".... is it a flame bait ?

---

### Post by LaRoza on 2008-02-16
> **ghostdog74 said:**
> 

So in your opinion, if I post things like 
"Use this language, it can do this and its nice to look at. Don't use this ....its ugly".... is it a flame bait ?

I see your point.

The poster who recommended away from the OP's declaration of intent did so with a honest belief that the OP would benefit from it. That poster also referenced a thread which covered the debate (and I linked to it, because I had removed it from the sticky a while ago during an update and the poster didn't know that)

Although that post would most likely start a debate, it wasn't intended to in all likely hood. The OP didn't seem to have a particular reason for wanting to learn Perl, and that was just advice from a Perl to Python programmer. 

If you feel I am biased in any way (because I am a Python user more than a Perl user) you can report the post and another moderator will look into the issue.

You can report any posts you feel are against the CoC.

---

### Post by pmasiar on 2008-02-16
> **shawnhcorey said:**
> I am tried of hearing that Python is the perfect language.

You are the only one claiming it. Then, you fight with your own strawman.

>   And I am tired of hearing that any argument against it will be transfer to some backwater group that nobody looks at.

This thread about Python perfect place for it, don't you agree?

> 
I will repeat myself:
**ALL LANGUAGES ARE ESOTERIC.**


Repeating a lie thousand times does not make it true. You rely on some different definition of "esoteric" than rest of programming community. Which of course is your right, just don't be surprised you are misunderstood. 

> Perl is just as good as other languages.  Well no, it's better.  That's because it has been around for far longer than Python or Ruby.  The problems they are coping with, it has already solved.

According to your logic, Fortran is the best language available?

> Just because you don't like its syntax, doesn't mean is bad.

You disliked "print 1/2 " in Python. Do you seriously think that  "print '1' + 5 " makes more sense?

But if you want to discuss Perl, lets do it in Perl thread. Here just briefly:

Just if some people like you still like Perl, it does not mean that it ceased being moribund. Years ago, I followed Perl6 and was looking forward to it. These days, I do not care, Python serves same niche for me, and better. And quite a lot of people gave up on Perl6 and moved on. No big company supports Perl anymore. I know Perl has huge installed code base, but hardly any new development. That is fact. Facts are quite stubborn. :-)

Languages evolve. Perl is being replaced by Python and Ruby. People using Perl switch, or die out. I prefer to switch. :-)

I am more interested learning a language which might replace Python in some future, than clinging to Perl. :-)

---

### Post by popch on 2008-02-17
> **pmasiar said:**
> You rely on some different definition of "esoteric" than rest of programming community. Which of course is your right, just don't be surprised you are misunderstood.

You rely on insider slang, while **shawnhcorey** uses the term 'esoteric' within its usual meaning.

> **Esoteric** knowledge is that which is specialized or advanced in nature, available only to a narrow circle of "enlightened", "initiated", or highly educated people.

(Wikipedia def will do until someone cites a better source).

Besides, **shawnhcorey**used the phrase 'all programming languages are esoteric' which is not the same as saying 'all programming languages are Esoteric Programming Languages'.

---

### Post by pmasiar on 2008-02-17
> **popch said:**
> You rely on insider slang,

I rely on wikipedia :-)

> Besides, **shawnhcorey**used the phrase 'all programming languages are esoteric' which is not the same as saying 'all programming languages are Esoteric Programming Languages'.

Sorry but I am not a lawyer. :-)

If we use your/shawncorey "usual" definition of esoteric, not related to programming languages, than I do agree that Perl is esoteric: It does rely on initiated people who continually practice the craft. 

But Python is not, or in substantially lesser degree, "esoteric" in that sense. It just plan works, that is exactly why is easier to learn and use (and not forget), compared to Perl.

---

### Post by red_Marvin on 2008-02-17
How could I miss this?

shawnhcorey: I have yet to see someone claim python as the ultimate language in this thread.

pmasiar: I am pretty confident that shawncorey meant "all languages are esoteric" as in all languages requires some abstraction and adaption of the idea of what the program is supposed to do into a formal language that can never be as natural to the mind as the original idea.

---

### Post by pmasiar on 2008-02-18
> **red_Marvin said:**
> I am pretty confident that shawncorey meant "all languages are esoteric" as in all languages requires some abstraction and adaption of the idea of what the program is supposed to do into a formal language that can never be as natural to the mind as the original idea.

"Esoteric" in context of programming languages has rather different meaning, as I linked above. When shawncorey decides to ignore this meaning, possibly substituting ans popch suggested, "standard" meaning, it does not help to clear misunderstanding - it creates new interesting ones :-)

Of course you cannot program in natural languages - they are not logical enough. It is common knowledge, I do not see how it advances our understanding. I am looking forward to be enlightened :-)

---

### Post by Xavieran on 2008-02-18
Where do I find a summary of changes to python in python 3?

And in reply to a previous post, Perl is better because is older,is not really that true ,python has been around since the early nineties...:)

---

### Post by pmasiar on 2008-02-18
Perl **is** older than Python, but so what? Maybe language designers did learn something since then, and possibly avoided some Perl pitfalls? Fortran and Cobol are older that Perl, does it mean they are better? More mature, yes; better, not for what Perl is being used.

Python is being used in exactly same niche as Perl, and Python is continuously gaining popularity despite Perl being older - so it looks like it is better. Of course for old Perl gurus Python is not better - they already know all Perl tricks and quirks, and learning Python will not make their life too much easier. But for aspiring programmers, it is easier to get into Python than Perl: Perl has many, many quirks. See [Why I love/hate Perl ](http://ubuntuforums.org/showthread.php?t=577596)

See [http://en.wikipedia.org/wiki/Py3k#Features](http://en.wikipedia.org/wiki/Py3k#Features) but detailed info about Python features is in PEPs - [http://www.python.org/dev/peps/pep-3000/](http://www.python.org/dev/peps/pep-3000/)

---

### Post by LaRoza on 2008-02-18
> **Xavieran said:**
> Where do I find a summary of changes to python in python 3?


<edit> 
I guess I should have viewed the next page before responding.
</edit>

---

### Post by slavik on 2008-02-18
Python being good where it is used? FORTRAN is still a better functional language than Python could ever hope to be. ;)

Mathematicians think in terms of functions and symbols, not in terms of variables and modules (ie: numpy does not make Python better than FORTRAN).

"Like a person for their positive qualities and love them for their negative qualities." Not sure the exact phrase or who said it. :)

---

### Post by LaRoza on 2008-02-18
> **slavik said:**
> Python being good where it is used? FORTRAN is still a better functional language than Python could ever hope to be. ;)

Mathematicians think in terms of functions and symbols, not in terms of variables and modules (ie: numpy does not make Python better than FORTRAN).

"Like a person for their positive qualities and love them for their negative qualities." Not sure the exact phrase or who said it. :)

Fortran is only good at functional programming...

The original specification didn't even have functions. (1954 - 1956)

(Note, I use Fortran 77)

While we are on the subject, what would be the recommended language for a mathematician? (Along with Fortran)

---

### Post by popch on 2008-02-18
> **LaRoza said:**
> While we are on the subject, what would be the recommended language for a mathematician? (Along with Fortran)

Wouldn't that depend a bit on the field of expertise? If you're in - say - topology, you would find Lisp and/or Prolog much more useful than anything in the Algol family. If you're in anything related to OR, you would possibly prefer something to do simulations with, such as Simula or Smalltalk.

Anyway, I would expect that rather more engineers than mathematicians use Fortran.

---

### Post by LaRoza on 2008-02-18
> **popch said:**
> Wouldn't that depend a bit on the field of expertise? If you're in - say - topology, you would find Lisp and/or Prolog much more useful than anything in the Algol family. If you're in anything related to OR, you would possibly prefer something to do simulations with, such as Simula or Smalltalk.

Anyway, I would expect that rather more engineers than mathematicians use Fortran.

I don't know, it isn't my field...

Thanks.

There was a reason for this, I am writing a small website that will help people select which language to learn. Such a thing was proposed once, and I have time to mess around. One of the options is to specifiy a specific purpose for learning, and Math and Engineering was an option.

Once I get the site functional I will post it, so everyone take a crack at it and tell me how to improve it.

---

### Post by slavik on 2008-02-18
So is Perl and Tcl, look at Pidgin ... (I hope you get my point). Lua is easy to embed, too, look at World of Warcraft ...

Just because something has been done, does not mean it is easy (99 bottles using brainfuck).

"Perl makes easy things easier, difficult things not impossible." - Larry Wall (and I agree with him).

as for a good language for a mathematician to go along with FORTRAN ... I'd have to say Haskel and whatever Maple/Mathematica understand. ;) (btw, FORTRAN is still used when calculating big things on large clusters).

As for 1954-56 not having functions ... people back then didn't think of storing programs in memory ;) (today we say "it's all 1s and 0s", back then it wasn't).

---

### Post by pmasiar on 2008-02-18
> **slavik said:**
> Python being good where it is used? FORTRAN is still a better functional language than Python could ever hope to be. ;)

I am not sure which definition of [http://en.wikipedia.org/wiki/Functional_programming](http://en.wikipedia.org/wiki/Functional_programming) do you use, but by wikipedia, Fortran is definitely NOT a functional language. 

Compared to that, **Python does have functionality usually associated with functional programming**, like lambda, map, list processing, etc.

So I am not sure on what facts you based your hope :-)

Maybe you confused it with [http://en.wikipedia.org/wiki/Imperative_programming](http://en.wikipedia.org/wiki/Imperative_programming) ? because Fortran is imperative language, IMHO.

> Mathematicians think in terms of functions and symbols, not in terms of variables and modules (ie: numpy does not make Python better than FORTRAN).

Better for what?

If all you need is to parse couple input files and glue together couple calls of numpy functions, it will be simpler to do in Python than trying to subdue obsolete Fortran text parsing. Maybe it improved since I looked last 15 years ago - I hope for the sake of people still using Fortran for it's excellent numerical libraries :-)

Of course if your needs are not easily satisfied by numpy calls, numpy is not a good solution (but programming it in C and adding it to numpy might be) :-)

> "Like a person for their positive qualities and love them for their negative qualities." Not sure the exact phrase or who said it. :)

Not sure how this is related to anything. Maybe you wrote it too late and too drunk? :twisted:

---

### Post by pmasiar on 2008-02-18
> **slavik said:**
> 
"Perl makes easy things easier, difficult things not impossible." - Larry Wall (and I agree with him).

I googled for the phrase and found:

[Larry Wall says](http://lambda-the-ultimate.org/classic/message1154.html)  that he designed Perl to make the easy things easy while making the difficult things possible... On the other hand, Perl makes a lot of things weirder.

[url=http://www.la-acm.org/Archives/laacm0112.html]
Perl 5[/url] did easy things easily and made impossible things doable, but hard. Perl 6 should make easy things easier and hard things easy

but only, of course, it will be ever implemented. Implementation is going strong for like 6 years now, with no clue when it will be finished, at least last time I checked. I admit I stopped checking monthly 3 years ago.

BTW I would **strongly** prefer to continue talk about Perl in it's own "Perl love/hate" thread, as I mentioned above.

> (today we say "it's all 1s and 0s", back then it wasn't).

Just curious, what it was back then, if not 0s and 1s?

---

### Post by Fbot1 on 2008-02-18
> **LaRoza said:**
> ...While we are on the subject, what would be the recommended language for a mathematician? (Along with Fortran)

As someone said, it depends. I'd say APL, C, or Fortran.

edit: Matlab and others like it too

---

### Post by Wybiral on 2008-02-18
> **Fbot1 said:**
> As someone said, it depends. I'd say APL, C, or Fortran.

C?

---

### Post by CptPicard on 2008-02-18
APL is an interesting idea, but too "strange"... C is way too low-level, Fortran is more for engineering-style number-crunching. I really think some kind of a Lisp would be a mathematician's language... Scheme, probably.

---

### Post by Fbot1 on 2008-02-18
> **Wybiral said:**
> C?

Ya, proving stuff by computer can take a while (years sometimes).

> **CptPicard said:**
> APL is an interesting idea, but too "strange"... C is way too low-level, Fortran is more for engineering-style number-crunching. I really think some kind of a Lisp would be a mathematician's language... Scheme, probably.

I actually can't think of any case were lisp was use.

---

### Post by pmasiar on 2008-02-18
> **LaRoza said:**
> While we are on the subject, what would be the recommended language for a mathematician? (Along with Fortran)

You, as forum mod, starting such off-topic discussion in a thread linked from FAQs? :roll: That is IMHO definitely off-topic here, and created dozen off-topic comments, polluting this thread supposedly about **Python** 	](*,)

---

### Post by CptPicard on 2008-02-18
> **Fbot1 said:**
> Ya, proving stuff by computer can take a while (years sometimes).

If you need that kind of speed, you're going to be using a specialized theorem prover written by someone else. Even then, it's likely to incorporate some kind of a high-level scripting interface for actually expressing your problem.

> I actually can't think of any case were lisp was use.

Like, most of it through 50s-70s when Lisp was supposed to be the holy grail of AI research, which is closely related to things like theorem proving? (Then they figured out that choice of language does not actually make such a huge difference...)

Lisps express functional concepts very economically... I can't think of any case where that would not be a Good Thing for a mathematician.

---

### Post by imdano on 2008-02-18
> **CptPicard said:**
>  I really think some kind of a Lisp would be a mathematician's language... Scheme, probably.I don't think Scheme gets used much aside from being an educational tool.  Too minimalist, I think.

edit: To say something on-topic, I'm a big python fan.  Only started using it about 8 or 9 months ago, but it's quickly become my favorite language to code in.  Very readable, very quick to write.

---

### Post by Fbot1 on 2008-02-18
> **CptPicard said:**
> If you need that kind of speed, you're going to be using a specialized theorem prover written by someone else. Even then, it's likely to incorporate some kind of a high-level scripting interface for actually expressing your problem.


Yes but those are not always appropriate (cryptanalysis for example). 

> **CptPicard said:**
> Like, most of it through 50s-70s when Lisp was supposed to be the holy grail of AI research, which is closely related to things like theorem proving? (Then they figured out that choice of language does not actually make such a huge difference...)

More so Prolog but, yes. I'm just saying what I know. I don't see Lisp very often.

> **CptPicard said:**
> Lisps express functional concepts very economically... I can't think of any case where that would not be a Good Thing for a mathematician.

That's usually when APL is used. Also, state isn't necessary bad.

---

### Post by slavik on 2008-02-18
> **pmasiar said:**
> Just curious, what it was back then, if not 0s and 1s?

It was, except at the time when memory was a dollar per byte, nobody thought of storing programs in memory, IOW load the program into memory and run it in there instead of reading from tape ...

---

### Post by CptPicard on 2008-02-18
> **imdano said:**
> I don't think Scheme gets used much aside from being an educational tool.  Too minimalist, I think.

Scheme is actually a great Lisp exactly because of the minimalism. I tried to get into Common Lisp some time ago, and just found out it's mostly a bunch of syntactic sugar on top of weaker language primitives -- for example, no fully re-entrant continuations and an unnecessarily weird lambda syntax. The only fundamental thing CL wins on is dynamic-scoped variables. Everything else you can build yourself in Scheme.

And when you consider a mathematician who is more of a user than coder, simplicity is a positive...

> **Fbot1 said:**
> Yes but those are not always appropriate (cryptanalysis for example).

Why not? Matlab/Mathematica does your cryptanalysis for you just fine. You're using a special case to argue a general point here... I would probably never put a mathematician into a position of having to code C for general purpose work...

> More so Prolog but, yes. I'm just saying what I know. I don't see Lisp very often.

Prolog is a relatively late development (1972), but yes, it was supposed to solve all problems too, which it didn't. Lisp was used much earlier, during a time when mathematicians would define their functions on pencil and paper and then send that to be compiled manually into machine code for execution...

> 
That's usually when APL is used. Also, state isn't necessary bad.

I've never heard of APL actually being used anywhere -- it's a completely fringe curiosity language as far as I know -- and I'd be surprised if someone actually chose it over Lisp for general-purpose work in mathematics. Lisp is not *quite* so functionally pure as APL, and even doesn't introduce so much weird syntactic elements...

And no, state isn't bad. That's why Lisp lets you have state when you want it.

---

### Post by Fbot1 on 2008-02-18
> **CptPicard said:**
> 
Why not? Matlab/Mathematica does your cryptanalysis for you just fine. You're using a special case to argue a general point here... I would probably never put a mathematician into a position of having to code C for general purpose work...

I forgot about Matlab-like software. Ya, those would be used most of the time but C is used too.

> **CptPicard said:**
> 
I've never heard of APL actually being used anywhere -- it's a completely fringe curiosity language as far as I know -- and I'd be surprised if someone actually chose it over Lisp for general-purpose work in mathematics. Lisp is not *quite* so functionally pure as APL, and even doesn't introduce so much weird syntactic elements...


It's mostly use by actuaries.

> **CptPicard said:**
> 
And no, state isn't bad. That's why Lisp lets you have state when you want it.

Then what's the importance of the ability to make functional code?

---

### Post by CptPicard on 2008-02-18
> **Fbot1 said:**
> 
Then what's the importance of the ability to make functional code?

As I said, you can have your state if you need it. Functional code doesn't necessarily need to be pure-functional. I fail to see why the ability to use state would negate the fact that Lisp gives you a pretty straightforward functional perspective into programming which would make sense for a mathematician.

If you argue for APL, you certainly must see the point, as APL's "put arrays through functions" is certainly not very far from Lisp's "put lists through functions"...

---

### Post by Joeb454 on 2008-02-18
Why To Love Python?     -        Why not?


Why To Hate Python?      -        Why not?


That's what I think :) If you like it, you like it, if not, you don't

---

### Post by Fbot1 on 2008-02-18
> **CptPicard said:**
> ...I fail to see why the ability to use state would negate the fact that Lisp gives you a pretty straightforward functional perspective into programming which would make sense for a mathematician.
Because a "functional perspective" isn't important. Even if it was, they wouldn't use Lisp because it doesn't enforce functional programing and Haskell is closer to Lambda calculus.

> **CptPicard said:**
> If you argue for APL, you certainly must see the point, as APL's "put arrays through functions" is certainly not very far from Lisp's "put lists through functions"...

You're right, it isn't very different but, APL is still used more often then Lisp.

---

### Post by pmasiar on 2008-02-18
Guys can you **please** start your own thread to discuss APL and Lisp? This thread is linked from stricky and as such might be held to higher standards - especially from regulars, who should know better.

---

### Post by Fbot1 on 2008-02-18
> **pmasiar said:**
> Guys can you **please** start your own thread to discuss APL and Lisp? This thread is linked from stricky and as such might be held to higher standards - especially from regulars, who should know better.

sure

---

### Post by slavik on 2008-03-09
I was trying to check some things in python ... it is not very discoverable-friendly ...

I tried the following:
```

if (x==5)
  print yes
else
  print no

```

since indentation is Python's thing, why the hell do I have to put a colon at the end of the if and else lines? WTF?!

---

### Post by Wybiral on 2008-03-09
> **slavik said:**
> I was trying to check some things in python ... it is not very discoverable-friendly ...

I tried the following:
```

if (x==5)
  print yes
else
  print no

```

since indentation is Python's thing, why the hell do I have to put a colon at the end of the if and else lines? WTF?!

That's not really a discover-ability issue, the language is consistent with this throughout. Also, you don't have to put the parenthesis around the condition in the "if" statement, this would do:

```

if x == 5:
    print yes
else:
    print no

```

I'm honestly not sure why the semicolon is there (maybe just to visually "punctuate" the line) but it's so consistent throughout the language that it's not going to cause you any problems (it's the same with classes, function definitions, conditions, loops, ...)

---

### Post by popch on 2008-03-09
> **Wybiral said:**
> I'm honestly not sure why the semicolon is there (maybe just to visually "punctuate" the line) but it's so consistent throughout the language that it's not going to cause you any problems (it's the same with classes, function definitions, conditions, loops, ...)

Presumably it's there in order to tell the parser that the condition is done and over. Otherwise, it could be continued on the next line, I think.

---

### Post by slavik on 2008-03-09
then give me blocks and parenthesis ...

---

### Post by ruy_lopez on 2008-03-09
> **Wybiral said:**
> 
I'm honestly not sure why the semicolon is there . . . 

This ':' is a colon. This ';' is a semi-colon. :)

---

### Post by slavik on 2008-03-09
what about \n representing the end of the statement?

---

### Post by pmasiar on 2008-03-09
\n cannot do, you can have boolean stretched expression over multiple lines:

[PHP]if (x1 and x2 and x3
       and x4 and x5):
   pass[/PHP]

I know it hurts someone used to Perl syntax, but some languages do have simple syntax, : starts block.

If it helps you to like Python, you can use shebraces like this:

[PHP]if x: #{
   pass
#}[/PHP]

:-)

---

### Post by Wybiral on 2008-03-09
> **ruy_lopez said:**
> This ':' is a colon. This ';' is a semi-colon. :)

lol, nice catch :)

---

### Post by slavik on 2008-03-09
> **pmasiar said:**
> \n cannot do, you can have boolean stretched expression over multiple lines:

[PHP]if (x1 and x2 and x3
       and x4 and x5):
   pass[/PHP]

I know it hurts someone used to Perl syntax, but some languages do have simple syntax, : starts block.

If it helps you to like Python, you can use shebraces like this:

[PHP]if x: #{
   pass
#}[/PHP]

:-)
there goes using indentation for block definition ...

---

### Post by pmasiar on 2008-03-09
> **slavik said:**
> there goes using indentation for block definition ...


Excuse me? Joke is on you, those are just plain comments, and the code in the block needs be properly intended. This is also valid:

[PHP]if x: #BEGIN
   pass
#END

if x: #FOO
   pass
#BAR

if x: #nachalo
   pass
#konec
[/PHP]

---

### Post by Wybiral on 2008-03-09
> **slavik said:**
> there goes using indentation for block definition ...

No, because the condition doesn't end until the colon, THEN the block begins (and it begins at it's own indentation). It's really not as complicated as you're making it.

---

### Post by lnostdal on 2008-03-09
guys .. why not make it simple; just wrap everything in ( and ) .. ok? .. lol .. =)

edit:
sorry for being off-topic .. i'm bored and too tired to do any hacking atm. :}

edit2:
great .. rofl @ LaRoza .. (post below) .. add some xml and it would be "enterprise" :P

---

### Post by LaRoza on 2008-03-09
> **lnostdal said:**
> guys .. why not make it simple; just wrap everything in ( and ) .. ok? .. lol .. =)

edit:
sorry for being off-topic .. i'm bored and too tired to do any hacking atm. :}

Great, we will have {} () and : for blocks.

[php]
(while (True)):({
(print ("this is true"))
})
[/php]

But seriously, we all indent anyway no matter why language we are using (mostly, in general, and most of the time), so it is quite simple.

---

### Post by slavik on 2008-03-09
```
if (blah == glah
  and something_else == other)
  do stuff here
else
  do stuff elsewhere
```

if colon denotes the end of the condition, note that there is no condition for else ... and if there is, it becomes an else if, elif or elsif (depending on which language you want to take it out of) which is utter rubbish, sorry.

---

### Post by LaRoza on 2008-03-09
> **slavik said:**
> ```
if (blah == glah
  and something_else == other)
  do stuff here
else
  do stuff elsewhere
```

if colon denotes the end of the condition, note that there is no condition for else ... and if there is, it becomes an else if, elif or elsif (depending on which language you want to take it out of) which is utter rubbish, sorry.

I don't understand what the problem is, what is rubish?

---

### Post by Wybiral on 2008-03-09
> **slavik said:**
> ```
if (blah == glah
  and something_else == other)
  do stuff here
else
  do stuff elsewhere
```

if colon denotes the end of the condition, note that there is no condition for else ... and if there is, it becomes an else if, elif or elsif (depending on which language you want to take it out of) which is utter rubbish, sorry.

It's like that to make things more uniform. If "if" had a colon and none of the rest of them did, it wouldn't make any sense. Uniformity is good in a language. It sounds to me like you're just being nitpicky :)

---

### Post by LaRoza on 2008-03-09
Colons are used for many things:

```

def function():
class Class:
for i in range(x):
if condition:
elif condition:
else:

```

After each one of these, there is an indented block. Simple and easy to read.

---

### Post by pmasiar on 2008-03-10
See also [Myths about Indentation](http://www.secnetix.de/~olli/Python/block_indentation.hawk) from the very first post. :-(

---

### Post by mssever on 2008-03-10
I think I read somewhere that colons in Python are a historical artifact. After all, the interpreter could easily be modified to not need them. However, they're so easy to get used to that if I spend a little time writing Python, I find myself typing colons in other languages. :) That's how I discovered one of Ruby's alternatives: ```
#conventional construction
run if foo
#also works
if foo: run
```For the case of single-line constructs, Python could use an optional colon in such a case.
```
if foo: run()
#but
if foo
    run()
```EDIT: This is probably heresy to Python-lovers, though.

---

### Post by slavik on 2008-03-10
> **Wybiral said:**
> It's like that to make things more uniform. If "if" had a colon and none of the rest of them did, it wouldn't make any sense. Uniformity is good in a language. It sounds to me like you're just being nitpicky :)
and there are people who claim that Perl is unreadable ;)

I ran across a Perl backup script where I could tell exactly what every line did, took me a while to understand what the pieces of code did, when I realised what was happenening, I re-wrote it ...

Perl is as readable as the logic behind it ;)

EDIT: about historical artefacts ... I remember the same complaints about Perl :)

---

### Post by LaRoza on 2008-03-10
> **mssever said:**
> 
```
if foo: run()
#but
if foo
    run()
```EDIT: This is probably heresy to Python-lovers, though.

Something about special cases I recall hearing....

Oh, yes, the Zen of Python!

[quote="Zen of Python"]
Special cases aren't special enough to break the rules.
[/quote]

---

### Post by Shadowmeph on 2008-08-29
Wow I read through about 14 pages and I have to say that this is quite infomative for a person ( like me) that loves to learn new things, a few months back I started to lear C++ from a book called C++ primer Third edition I bought from a second hand store but I was side tracked and seemed to have forgotten allot of what I had learn but after reading the posts in here I going to start with python it seems allot easier for me to learn ( for now) I am really glad I was pointed to this post :)

---

### Post by pmasiar on 2008-10-29
Recently I found: [http://code.activestate.com/recipes/384122/](http://code.activestate.com/recipes/384122/)

```

#definition of an Infix operator class
#  x |op| y
# or:
# x <<op>> y

```

Totally brilliant, and it was available in Python since 1.5!

---

### Post by sheto on 2008-10-29
I like Python for it's abundant use of whitespace (makes the code more readable) and also for it's simple syntax and ease-of-use. Also, the online documentation is quite good.

---

### Post by slavik on 2008-10-29
> **sheto said:**
> I like Python for it's abundant use of whitespace (makes the code more readable) and also for it's simple syntax and ease-of-use. Also, the online documentation is quite good.
I believe there was a user here who said that due to his condition, code with lots of spaces was not very readable ...

---

### Post by LaRoza on 2008-10-29
> **slavik said:**
> I believe there was a user here who said that due to his condition, code with lots of spaces was not very readable ...

Then don't put a lot of spaces.

---

### Post by pmasiar on 2008-10-29
> **slavik said:**
> I believe there was a user here who said that due to his condition, code with lots of spaces was not very readable ...

yes. he was blind, and his screen reader skips over whitespace, and I agree that **for that user** python is not a good match.

For everyone else, is 8-) at least IMHO

ahhh, those pesky details and unexpected special cases.... ;-)

---

### Post by LaRoza on 2008-10-29
> **pmasiar said:**
> yes. he was blind, and his screen reader skips over whitespace, and I agree that **for that user** python is not a good match.


Ah, that is indeed a special case.

---

### Post by cmay on 2008-10-29
i also have  lost trouble with the syntax since my eyes are operated.
i cant learn this language. at all. 
 [php]«« if a<=b:
    print "hello "[/php]this should be easy. it is not to me. thats is how far i got before finding out i do not have time to figure out what indention python complains  about. it would take me sometimes two hours to make a simple example using more than one if statement copy and pasted from a tutorial to work.

---

### Post by LaRoza on 2008-10-29
> **cmay said:**
> i also have  lost trouble with the syntax since my eyes are operated.
i cant learn this language. at all. 
 [php]«« if a<=b:
    print "hello "[/php]this should be easy. it is not to me. thats is how far i got before finding out i do not have time to figure out what indention python complains  about. it would take me sometimes two hours to make a simple example using more than one if statement copy and pasted from a tutorial to work.

Set your tab to the amount of spaces and use it. You can also have your editor show spaces and tabs.

---

### Post by nvteighen on 2008-10-29
> **cmay said:**
> i also have  lost trouble with the syntax since my eyes are operated.


Glad to hear you're better!

---

### Post by cmay on 2008-10-29
> **LaRoza said:**
> Set your tab to the amount of spaces and use it. You can also have your editor show spaces and tabs.
i use drpython. it helps a bit so i am pass the if statements now. but i must say i most at all  want to learn python since i learn c right now as you may know and just want to learn how to make c extentions to other languages as well. knowing python is a good idea then maybe.

> Glad to hear you're better!     thanks

---

### Post by fredscripts on 2008-10-29
> **Jessehk said:**
> One thing I hate about Python is the indentation-level-as-control structures thing. I don't mind it at all when I'm writing code, but when copy/pasting (or doing something similar) a bug caused an indentation error can be very hard to find and is extremely annoying.

Really true!! Indentation errors are really annoying!

IMO, things that I don't like in Python are:

1) Indentation errors
2) The fact that you have to put self as a first parameter to a method of a class.

```
class Foo:
   ...
   def do_sth(self, a,b,c...):

```

As I always forget to put that "self" as a parameter of the class method (probably because I'm used to Java).

3) I really like and use perl-like expressions such as:

```
print "$line" while (my $line = <>);
```

I mean putting the condition/loop after the statements. Something Perl has made me get used to and I really miss it.

4) The famous ?  operator:

```
foo = isGood ? "good" : "bad";
``` 

Something I got used to due to C which I miss.

5) Where's the ++/-- operator! And also the perl ".."? It would be a really useful shortcut of range function!

And , of course, things that I love in python:

1) The scipy and numpy packages!!! the way to interact with arrays and matrices is really gorgeous.

2) The third argument in range function (which can't be simulated a priori with the perl "..")

3) Overloading operators such as + for different data types.

4) The easy to document a function with starting """ help """

That's my opinion!

---

### Post by LaRoza on 2008-10-29
> **fredscripts said:**
> Really true!! Indentation errors are really annoying!

IMO, things that I don't like in Python are:

1) Indentation errors

Indentation errors are easy to find. Those pesky missing semi-colons are the worst errors ;)

> 
Something I got used to due to C which I miss.

5) Where's the ++/-- operator! And also the perl ".."? It would be a really useful shortcut of range function!

Of course, Python has so much more than those minor syntax embelishments. Like lambda's, lisp comprehensions, etc.

---

### Post by cl333r on 2008-10-29
> **pmasiar said:**
> (In response from [post about C](http://ubuntuforums.org/showthread.php?p=3537968&posted=1#post3537968)
[C/Java has more resources than Python online]
One of the reasons (at least for python and for me) might be that I needed substantially less resources to get started with Python than with Java. Java is just so byzantine complicated. My "Java in a nutshell, 1.3" has 646 pages of standard format, "Python pocket reference" (2.4) has 148 pages, and pages are half the size. You need many more books to get reasonable comprehension of Java than for Python.

I found a book on Python of only 74 pages, thus Python has become once again better! In fact there's a tutorial about Python on the web - it is about 2 pages, so.. since the Java book has 646 pages / 2 python pages = Python is 323 times better than Java! Can you imagine that?? It is so cool! I'm once again fascinated about Python!
Besides, I just love the fact that it's the ideal language for writing  all kinds programs and libraries (really!). Linus is considering Python for the 3.0 Linux kernel implementation, because he finally got to realize that speed doesn't matter (in fact C programs are much slower and take longer to startup and consume more memory), what matters is portability and productivity.
I also love that Python has built-in cross-platform support for fast graphics with antialiasing, true-type fonts, HD audio and video and most robust support for concurrency and networking. So unlike other languages you don't have to google for compatible libraries, they're already all there waiting for you!
The potential of Python is immense! That's why I love it.

---

### Post by mssever on 2008-10-29
> **LaRoza said:**
> Indentation errors are easy to find. Those pesky missing semi-colons are the worst errors ;)Amen. I wish semicolon languages would realize that \n is in most cases equivalent in meaning to a semicolon, and should be accepted as a substitute. Fortunately, missing semicolon errors are easy to find and solve.

> Of course, Python has so much more than those minor syntax embelishments. Like lambda's, lisp comprehensions, etc.
Python's list comprehensions (not lisp comprehensions, unless you know something I don't :)) are awesome, but Python's lambdas are a bit lame. If lambdas could be longer than a single expression, that would also be good. Also, since Python has first class functions, it would be nice to be able to create full-featured anonymous functions, like in JavaScript.

---

### Post by LaRoza on 2008-10-29
> **cl333r said:**
> I found a book on Python of only 74 pages, thus Python has become once again better! In fact there's a tutorial about Python on the web - it is about 2 pages, so.. since the Java book has 646 pages / 2 python pages = Python is 343 times better than Java! Can you imagine that?? It is so cool! I'm once again fascinated about Python!
Besides, I just love the fact that it's the ideal language for writing  all kinds programs and libraries (really!). Linus is considering Python for the 3.0 Linux kernel implementation, because he finally got to realize that speed doesn't matter (in fact C programs are much slower and take longer to startup and consume more memory), what matters is portability and productivity.
I also love that Python has built-in cross-platform support for fast graphics with antialiasing, true-type fonts, HD audio and video and most robust support for concurrency and networking. So unlike other languages you don't have to google for compatible libraries, they're already all there waiting for you!
The potential of Python is immense! That's why I love it.

I'm not sure what is post is about. Is it sarcasm, ignorance, or a joke?

No one claims Python is suitable for all things (for instance, Python and many of its modules are written in C)

---

### Post by LaRoza on 2008-10-29
> **mssever said:**
> 
Python's list comprehensions (not lisp comprehensions, unless you know something I don't :)) are awesome, but Python's lambdas are a bit lame. If lambdas could be longer than a single expression, that would also be good. Also, since Python has first class functions, it would be nice to be able to create full-featured anonymous functions, like in JavaScript.

It was my lisp that caused that, sorry.

I like ECMAScript's anonymous functions better to. Perhaps you could make them for Python?

---

### Post by curvedinfinity on 2008-10-29
I really love python from the language point of view. Its clean, lovely to write, and has a million well made libraries.

My big gripe with it is that its distribution template is not friendly to windows users. -- Its hard to distribute a Python app to Windows because you first have to get users to install Python. The extra step isn't a big deal for developers, but its a killer for the "basic" end user.

Sure, you can embed python in a compiled app, but that defeats the purpose of using an interpreted language.

... Considering all of that, I use Python in every application I make for myself and don't want to distribute. Its simply the best language from a productivity point of view.

---

### Post by jimi_hendrix on 2008-10-29
i find i actually code worse in python than a more C like language...but i realize how easy it is to learn and its grate for beginners

---

### Post by LaRoza on 2008-10-29
> **curvedinfinity said:**
> I really love python from the language point of view. Its clean, lovely to write, and has a million well made libraries.

My big gripe with it is that its distribution template is not friendly to windows users. -- Its hard to distribute a Python app to Windows because you first have to get users to install Python. The extra step isn't a big deal for developers, but its a killer for the "basic" end user.

Sure, you can embed python in a compiled app, but that defeats the purpose of using an interpreted language.

... Considering all of that, I use Python in every application I make for myself and don't want to distribute. Its simply the best language from a productivity point of view.

You can bundle the installer with it. Also, you can easily distribute Python apps in Linux (which is the platform that matters).

Also, installing ActivePython is very familiar to Windows users (although it would be a pain from a Linux point of view, all that clicking...)

---

### Post by curvedinfinity on 2008-10-29
> **LaRoza said:**
> ...in Linux (which is the platform that matters).

That's pretty zealous, don't you think? Linux is gaining market share, but the success hasn't come from exclaiming to everyone that they had it wrong all along. Linux's success has come from the idea that everyone, regardless of platform, ideology, race, or social status is important. 99.9% of the world only views technology as a means to an end, not something important in itself, like our subculture does. Thus, in terms of supporting these people, its important to make processes as simple and short as possible.

But I'll tell you what, in terms of Linux, I completely agree that Python apps are even easier to deal with than compiled apps. :)

---

### Post by LaRoza on 2008-10-29
> **curvedinfinity said:**
> That's pretty zealous, don't you think?

No. Linux is where open source development is at. Python, when used in proprietary applications, can afford to have the installer deal with all the dependencies.

---

### Post by curvedinfinity on 2008-10-29
> **LaRoza said:**
> No. Linux is where open source development is at. Python, when used in proprietary applications, can afford to have the installer deal with all the dependencies.

Zealotry and truthfulness aren't mutually exclusive. -- In other words, what you are saying is true, but its not the way to say it to have people listen. :)

---

### Post by unutbu on 2008-10-29
Hi [fredscripts]("http://ubuntuforums.org/showpost.php?p=6059214&postcount=218"), here is one less reason not to like Python:```


foo = isGood ? "good" : "bad"
```

in Python:```


foo = "good" if isGood else "bad"
```

---

### Post by pmasiar on 2008-10-29
> **curvedinfinity said:**
> Its hard to distribute a Python app to Windows because you first have to get users to install Python.

The only difference is that in Windows, .NET is already preinstalled. 

ActiveState Python MSI installer is exactly as trivial to use as any other Windows installer, granma can do it. Don't use python.org installer and your users are fine.

MSFT realized that dynamic languages on .NET can beat Java, they do lot of good work with IronPython, I expect IP be part of standard Win install in some near future.

---

### Post by pmasiar on 2008-10-29
> **fredscripts said:**
> Indentation errors are really annoying!

For me, even more annoying are errors (possible  in languages like C, Java etc with {} ) where whitespace indent does not match the indent given by {}. Hard to find, confusing like hell. 

I answered to your gripe about whitespace at the very first post: [Myths about Indentation](http://www.secnetix.de/~olli/Python/block_indentation.hawk) but you prefer myths? 

> 2) The fact that you have to put self as a first parameter to a method of a class.

Guido [answers](http://neopythonic.blogspot.com/2008/10/why-explicit-self-has-to-stay.html) . Can you do such neat tricks with decorators in Java? Why not? Because self is forced on you?

> 5) Where's the ++/-- operator! 

x+=1 is just one more character, and less confusing (farther from C where it makes sense).

> And also the perl ".."? 

When talking about it, why not add full [Periodic Table of the Operators](http://www.ozonehouse.com/mark/blog/code/PeriodicTable.html), including the non-ascii ones? 

Perl is called "executable line noise" for a reason. Think about it.

---

### Post by nanotube on 2008-10-29
> **pmasiar said:**
> Recently I found: [http://code.activestate.com/recipes/384122/](http://code.activestate.com/recipes/384122/)

```

#definition of an Infix operator class
#  x |op| y
# or:
# x <<op>> y

```

Totally brilliant, and it was available in Python since 1.5!

Very neat hack! Thanks for sharing :)

---

### Post by Delever on 2008-10-30
[PHP]
file = open('a.txt','r')

for line in file:
    print line
[/PHP]

I remember I started loving it the moment I saw this.

---

### Post by ghostdog74 on 2008-10-30
> **Delever said:**
> [PHP]
file = open('a.txt','r')

for line in file:
    print line
[/PHP]

I remember I started loving it the moment I saw this.

```

for line in open("file"):
  print line

```

---

### Post by slavik on 2008-10-30
> **ghostdog74 said:**
> ```

for line in open("file"):
  print line

```
I have to ask ... what exactly does this show?

---

### Post by ghostdog74 on 2008-10-30
> **slavik said:**
> I have to ask ... what exactly does this show?

this shows that Python's for loop
1) is optimized to loop over files and implicitly closing the file after end of iteration. 
2) that the default mode for opening file is "read" mode and open("file") is equivalent to open("file","r"),therefore, less characters to type.

---

### Post by slavik on 2008-10-30
hmm, implicit ... I love implicit things, except when I do implicit things, people call my code unreadable :(

---

### Post by nvteighen on 2008-10-30
> **fredscripts said:**
> 
(...)

1) Indentation errors

Yeah, exactly as annoying as any other syntax error in any other programming language. When you use a language, you accept to use its syntax.

> 2) The fact that you have to put self as a first parameter to a method of a class.

```
class Foo:
   ...
   def do_sth(self, a,b,c...):

```

As I always forget to put that "self" as a parameter of the class method (probably because I'm used to Java).

Actually, I like it. The idea is that only variables declared inside a function and the parameters of the function should be able to modify its behaivor. Explicit "self" is a way to express that without breaking the general Python syntax.

> 
3) I really like and use perl-like expressions such as:

```
print "$line" while (my $line = <>);
```

I mean putting the condition/loop after the statements. Something Perl has made me get used to and I really miss it.


Yeah, that's a nice feature of Perl (which can be summarized to "Flexible syntax").

> 
4) The famous ?  operator:

```
foo = isGood ? "good" : "bad";
``` 

Something I got used to due to C which I miss.


Python doesn't have it, but you can construct it:
```

foo = isGood and "good" or "bad"

```

> 5) Where's the ++/-- operator! And also the perl ".."? It would be a really useful shortcut of range function!

Maybe there's no ++/-- to avoid a C-like impression :)


> **mssever said:**
> Amen. I wish semicolon languages would realize that \n is in most cases equivalent in meaning to a semicolon, and should be accepted as a substitute. Fortunately, missing semicolon errors are easy to find and solve.

Yeah, the semicolon in CPL->BCPL->B->C was used as a line separator. And it's there just for backwards compatibility and to keep the language's look-and-feel.

But to see modern languages (i.e. Java) still using it seems to me really absurd.

---

### Post by ghostdog74 on 2008-10-30
> **slavik said:**
> hmm, implicit ... I love implicit things, except when I do implicit things, people call my code unreadable :(

what i mean by implicitly closing the file, ie you don't have to do this
```

f = open("file","w") # get a file handle
f.write("blah)
f.close()

```
Instead, very simply
```

open("file","w").write("blah")

```
opening a file and closing it after operation is such a standard step for file i/o that we can "skip" these steps and let the language take care of it. That's just my $0.02.

I am sorry that people call your code unreadable.

---

### Post by pmasiar on 2008-10-30
> Re: The famous ? operator:
> **nvteighen said:**
> 
Python doesn't have it, but you can construct it:


You are behind the times 8-) Python **does** have conditional expression since 2.5: [http://www.python.org/dev/peps/pep-0308/](http://www.python.org/dev/peps/pep-0308/) as was mentioned by someone already.

---

### Post by nvteighen on 2008-10-30
> **pmasiar said:**
> > Re: The famous ? operator:


You are behind the times 8-) Python **does** have conditional expression since 2.5: [http://www.python.org/dev/peps/pep-0308/](http://www.python.org/dev/peps/pep-0308/) as was mentioned by someone already.
Oh, I didn't notice that. Thanks!

---

### Post by pmasiar on 2008-10-30
> **slavik said:**
> hmm, implicit ... I love implicit things, except when I do implicit things, people call my code unreadable :(

Yeah, like implicit variable $_? Worst idea I ever seen. Sure way to make "write-only" code: So unreadable that even it's own author cannot read it 8-)

Python learned from unreadability of Perl code, has even rule about it: "Explicit is better than implicit".

Of course if you don't like it, feel free to use Perl: just don't ask **me** to maintain that code 8-)

---

### Post by fredscripts on 2008-11-02
> **unutbu said:**
> Hi [fredscripts]("http://ubuntuforums.org/showpost.php?p=6059214&postcount=218"), here is one less reason not to like Python:```


foo = isGood ? "good" : "bad"
```

in Python:```


foo = "good" if isGood else "bad"
```

Thanks! didn't know about that :), but in terms of typing time I prefer the ? operator :D

---

### Post by fredscripts on 2008-11-02
> **pmasiar said:**
> For me, even more annoying are errors (possible  in languages like C, Java etc with {} ) where whitespace indent does not match the indent given by {}. Hard to find, confusing like hell. 

I answered to your gripe about whitespace at the very first post: [Myths about Indentation](http://www.secnetix.de/~olli/Python/block_indentation.hawk) but you prefer myths? 

> 2) The fact that you have to put self as a first parameter to a method of a class.

Guido [answers](http://neopythonic.blogspot.com/2008/10/why-explicit-self-has-to-stay.html) . Can you do such neat tricks with decorators in Java? Why not? Because self is forced on you?

> 5) Where's the ++/-- operator! 

x+=1 is just one more character, and less confusing (farther from C where it makes sense).

> And also the perl ".."? 

When talking about it, why not add full [Periodic Table of the Operators](http://www.ozonehouse.com/mark/blog/code/PeriodicTable.html), including the non-ascii ones? 

Perl is called "executable line noise" for a reason. Think about it.

Hi! Thanks for the information!

I'm very open-minded in terms of programming languages. I think everyone should choose the right language for the right application.

I don't know if was a thing of IDLE when I started learning Python, but I remember that copying python source from any website to IDLE and then spend 10 minutes trying to indent all code properly so that I can run it without run-time errors. I hope this is solved at the present time because was really annoying.

I really like how Ruby copes with objects. It's really more intuitive, difficult-to-forge-self-stuff than Python.

Maybe I'm confused here, but I think that the ++ construction runs faster than any equivalent construction "i = i+1" , even i+=1. Though I'm not sure, it's clear that ++ is faster to type :D.

Of course I wouldn't choose Perl to write an application longer than 100 lines and where I wasn't the only programmer/maintainer of it.

---

### Post by LaRoza on 2008-11-02
> **pmasiar said:**
> 
Python learned from unreadability of Perl code, has even rule about it: "Explicit is better than implicit".

Of course if you don't like it, feel free to use Perl: just don't ask **me** to maintain that code 8-)

Interestingly, I was talking to a Perl fan on IRC and we were discussing operatings. He was pointing out all the benefits of them, and how þey are useful, and I pointed out þat Python can do all that, and be more explicit, and he said þat is why he didn't like Python.

So Perl seems like þe perfect tool to those who know it well, but it seems to be the learner and reader's bane in some ways. þose operators of Perl probably seemed like a good idea at the time, but I þink þey built way too much into the language and as symbols, which is not what we are used to reading.

---

### Post by Greyed on 2008-11-02
> **fredscripts said:**
> 1) Indentation errors

There are no indention errors, only operator errors.  Slap tab, all is well.

> 3) I really like and use perl-like expressions such as:

```
print "$line" while (my $line = <>);
```I mean putting the condition/loop after the statements. Something Perl has made me get used to and I really miss it.
Horrible mess, really.  This was one of the reasons I absolutely hated Perl.  It boiled down to the numerous cases of if.  Back when I last really hacked at Perl if could be expressed like so:

if cond {command}
command if cond
unless cond {command}
command unless cond

3 of those were utterly useless.  Why?  Because they weren't extensible!  You couldn't else the "command if cond" and "command unless cond" form.  So if you needed to elseif an if you had to rewrite it to the if cond {command} form.  Of course at the time unless couldn't have an elsif attached.  So if you needed to have multiple conditions on an unless you had to rewrite it to an if not cond {command} and attach the elseif to it.  The final form just has all the problems of the previous forms.

Note that I've not touched Perl code in about 5 years but a quick check of perl.org's docs shows that this problem still exists.  Know how I handled it in my Perl code?  I completely ignore the latter 3 forms and only use the first form.  IE, I did exactly what Python does.  I used the most sensible and extensible form to the exclusion of all others.  That way I didn't have to go digging for the condition because it always up front, not behind the command!  When I had to extend it I didn't have to rewrite it to the sensible form in the first place.

The problem is that every other half-assed Perl hacker out there would use the different forms willy-nilly just because they're there.  Yay!  My code was maintainable because I effectively limited myself to a narrow, sensible subset of the language.  A subset which pretty much maps to what Python uses.  I loathed touching anyone else's code because making the simplest of changes required far more effort and thought that was needed all because someone thought...

```
print "You have chosen... poorly." if (hp < -10)
```...was a keen idea until someone else wanted to hack in...

```

if (hp < -50) {
    print "You have chosen... extremely poorly."
}
elseif (hp < -10) {
    print "You have chosen... poorly."
}

```
> 4) The famous ?  operator:

```
foo = isGood ? "good" : "bad";
```Something I got used to due to C which I miss.Others have pointed out how this can be done.  Frankly, it suffers from the same problems as above.  What happens when you have 3 conditions insteat of 2?  Whoops, time to rewrite it.  Just write it in the normal form the first time and be done with it.  Not only is it easier to read and understand it is easier to modify.  There is simply no benefit to the above other than some misguided desire to shave a few keystrokes at the expense of mantainability.

> 5) Where's the ++/-- operator! And also the perl ".."? It would be a really useful shortcut of range function!I'm guessing the implcitness of ++/-- is why they are thankfully not present.  Remember kids, ++x and x++ are not the same!  As for .., is range() so hard to type?  Really?

I mean...

> 2) The third argument in range function (which can't be simulated a priori with the perl "..")You hit on the good part of range().  In fact, range() also allows us to normalize for/foreach into for.  foreach = for.  for = for x in range().

IE, all of the above really misses the underlying foundation of Python.  Put in the most common and normal way to do things and leave the edge cases out.  It is why Python has exactly 2 loop constructs while Perl has 4.... 5?  Yes, people who really, really are attached to do..until dislike the double initilization of while or while 1 the whole point is when you have just 2 loops to deal with you don't have to worry about the exact and slightly different semantics of different loops.  It's spelled out in the code.  Anyone who whinges about having to dig through a while 1 loop for the if break statement and pines for the day of do..until has obviously never met a do..until loop with an if break in the middle.  ;)

> **ghostdog74 said:**
> what i mean by implicitly closing the file, ie you don't have to do this
```

f = open("file","w") # get a file handle
f.write("blah)
f.close()

```Instead, very simply
```

open("file","w").write("blah")

```opening a file and closing it after operation is such a standard step for file i/o that we can "skip" these steps and let the language take care of it. That's just my $0.02

Problem is I don't see that as very extensible.  Sure, it's neat that Python does it but when you're probably going to be writing to a file several times closing/opening the file for each operation is just a waste of time.  Keep the darn file handle open until you're done with it already!

---

### Post by pmasiar on 2008-11-02
> **fredscripts said:**
> I remember that copying python source from any website to IDLE and then spend 10 minutes trying to indent all code properly so that I can run it without run-time errors. 

It cannot be solved in Python - website has to provide all whitespace correctly, and if sourse is properly formatted, it works.

> Maybe I'm confused here, but I think that the ++ construction runs faster than any equivalent construction "i = i+1" , even i+=1. Though I'm not sure, it's clear that ++ is faster to type 

Yes, you are confused. ;-)
Any trivial optimizing compiler can replace x = x +1 with x++ operation internally, and it does.

x+=1 is simpler to understand, especially for someone who does not program for living.

---

### Post by pmasiar on 2008-11-02
> **LaRoza said:**
> So Perl seems like þe perfect tool to those who know it well, but it seems to be the learner and reader's bane in some ways.

Exactly.

You need to give daily offerings to angry Perl gods, and if you don't, they will punish you: you will forgot the quirks, and they will bite you.

Python is for people who have other things to do in life than remember the language quirks.

---

### Post by Greyed on 2008-11-02
> **pmasiar said:**
> Python is for people who have other things to do in life than remember the language quirks.

Perl is Cockney.
Python is English.

---

### Post by pp. on 2008-11-02
> **Greyed said:**
> Perl is Cockney.
Python is Engish.

Smalltalk is Eng**l**ish.

---

### Post by LaRoza on 2008-11-02
> **pmasiar said:**
> Exactly.

You need to give daily offerings to angry Perl gods, and if you don't, they will punish you: you will forgot the quirks, and they will bite you.

Python is for people who have other things to do in life than remember the language quirks.

Interesting statements, but true :-)

It is like Devanagari and Nastaliq. In Devanagari, things are spoken as they are written (see title). If you know the script, you can say it properly.

In Nastaliq (a Persian script), they don't have vowels because it was designed with the assumption the person reading knew the language and would be able to read the words without them (Hebrew is like this...). This results in confusion for future generations who didn't grow up with the language and people learning the language.

---

### Post by cmay on 2008-11-02
> **pmasiar said:**
> Exactly.

You need to give daily offerings to angry Perl gods, and if you don't, they will punish you: you will forgot the quirks, and they will bite you.
  

  sweetgrass or sage ?

---

### Post by Greyed on 2008-11-02
> **cmay said:**
> sweetgrass or sage ?

Goat.

---

### Post by openuniverse on 2009-11-19
.

---

### Post by Noob64 on 2010-02-13
Yea, but I like C++ brackets better, then white space in python.

Its real funny that everyone says python  easier. I personally believe, that a language is 

only easy if you now how to use it.

 For me C++ is easier then python. I tried for a good week and still don't know how to call 


python function. but in a day I figured how to call  C++ function . 

Brackets are not that hard to deal with, if you know the fundamentals of what they do 

start and end a program.. 

In the long run python syntax is easy but to me feels less organized with out brackets.

personal for now I prefer  C\C++.

---

### Post by xieu90 on 2010-02-13
uhm...
python is my first language which i made my first program
then haskell (useless for me)
then i came to java and i like it, cause it has eclipse ^^

then i came back to python and yeah, i prefer java+ eclipse rather than python+ eclipse+ pydev
^^

python is beautiful, cause i dont have to add ; at the end of the line
if a==2 without () ^^
but there are only some tut online ... and python is slower than java (i heard so)

java+eclipse = best for me
without eclipse, java would be my worst nightmare 
System.out.print("something");
instead
print"something"
^^

---

### Post by nvteighen on 2010-02-14
Ok, these last posts are completely missing the point of the discussion... It's not about the syntax, it's not that much about the development tools, but about how the language copes with programming problems under which approach.

I do not care whether the ending semicolon is pretty/useless/l33t/whatever... to me it's as irrelevant as Python's colon. There are, of course, easier syntaxes than others, but that's not the point... at the end, you can learn the syntax but not understand the concepts the language operates with. That's something quite annoyingly recurrent on people learning C++ from a C background: they master the syntax but still write C code in C++.

What I do care about is how much language X allows me to do where.

---

### Post by CptPicard on 2010-02-14
You surely do not expect people to *actually read* the thread they're posting into, nvteighen... ;)

---

### Post by Vox754 on 2010-02-14
> **nvteighen said:**
> Ok, these last posts are completely missing the point of the discussion... It's not about the syntax, it's not that much about the development tools, but about how the language copes with programming problems under which approach. ...
I'm not criticising your point of view, I support high-level, but if there is a thread to nitpick on any aspect of the language, this is it.

This thread is one of the **Why to love/hate...** series, so I'd assume anything goes. Even meaningless issues like colons, in this thread, are valid opinions to **love** or **hate** the language.

---

### Post by nvteighen on 2010-02-14
> **Vox754 said:**
> I'm not criticising your point of view, I support high-level, but if there is a thread to nitpick on any aspect of the language, this is it.

This thread is one of the **Why to love/hate...** series, so I'd assume anything goes. Even meaningless issues like colons, in this thread, are valid opinions to **love** or **hate** the language.

Maybe... maybe... hm...

---

### Post by CptPicard on 2010-02-14
Well, there is nothing wrong at least suggesting to the two posters that they familiarize themselves with the depth of argument for their own education :p

---

### Post by TheStatsMan on 2010-02-14
> **Vox754 said:**
> 
This thread is one of the **Why to love/hate...** series, so I'd assume anything goes. Even meaningless issues like colons, in this thread, are valid opinions to **love** or **hate** the language.

I don't understand why people have such strong feelings about whether or not a line ends with semi-colons or an if/for statement has a colon after it. To me it is equivalent to the following scenario:

 (imagine an adult with an annoying whiny kids voice) "Mum, I don't want that maths book the authors names are printed above the title".

(Mum)  "It is the best linear algebra book there is"

(Annoying whiny person, almost a tantrum) "I don't care I want the calculus book at least the name is in the correct position"

(Mum) "But you are studying linear algebra, surely it would be a better book for the course"

(Annoying whiny person) "I hate the linear algebra book it is crap, I want the calculus book"

---

### Post by paxxus on 2010-02-15
I'm an old time Perl hacker and I've done some semi-large projects in Perl. Occasionally I'm away from the language for maybe up to a year and it can be pretty hard to get back in shape.

I'm looking into Python and so far I like it - seems more readable and easy to learn/remember compared to Perl. I've already done some neat classes for representing coding threes, the result was very nice IMO.

The indentation doesn't bother me at all since I indent already, so no biggie. However, what I really hate is that blocks just sort of end. If you're reading someone else's code it sometimes looks like some lines got deleted, suddenly a loop body etc. just stops and I'm sort of thinking "I guess this was the end then, let's see how the next line is indented after this comment block - yep that other line was really the last line of that loop body, nice to know." I like explicit [block end] instead of implicit.

Then there's stuff like:

```
>>> range(1, 10)
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```Uhm, OK. I guess that makes sense, kind of... sort of... I think...

Regular expressions are also a little more cumbersome to use in Python.

Anyway, I have only scratched the surface so far but I'm pretty sure I'm going to abandon Perl except for one-liners at the command prompt.

---

### Post by darsu on 2010-02-16
I'm in the middle of having to tackle some image analysis problems at work. I must be getting older and wiser because I balked at the thought of having to go to C++ again--so I rummaged the webnets to see if there are any toolkits/libraries for higher-level languages. I found OpenCV has a Python interface, and I've already implemented a third of the needed functionality, with a previous lifetime Python coding experience of perhaps 50 lines.

Python code looks dull as porridge.

---

### Post by CptPicard on 2010-02-16
Dullness can be good; it can mean the code is regular enough to be predictable. It is interesting how many pretty interesting constructs and ideas there still are in Python although not much meets the eye to begin with... it's all a sign of good language design IMO.

---

### Post by __jan on 2010-03-07
I've started with Python very recently (2 months) and so far I quite like it. My background (which I think is always determining in love/hate debates) is for the most part with statically typed and compiled languages, C++ and C# and way back a little bit of PHP.
This is what I like about Python:

[LIST=1]
[*]Productivity. I use Python for rapid prototyping and it's amazing in that role.
[*]Semantic whitespace. (Surprised? Rigid indentation is practically a requirement in enterprise scale use of C++/C#, so why not to go all the way long?)
[*]Django; add even more fuel to 1.)
[*]Lot's of thing ready to use in core library and not difficult to find.
[/LIST]
And this is what I hate about it:

[LIST=1]
[*]Python's OO capabilities feel like somehow crudely hacked into the thing as if they almost shouldn't be there.
[*]Superfluous use of *self*
[*]Non-existent scopes (name mangling would not do)
[*]Inability to explicitly declare property members (you just assign *instance.propName = value* and it pops into being, no warning)
[*]No interfaces (this is just would-be hate, because what I do in Python is  simple and nobody else needs to understand it and nobody will have to extend it, therefore me just crudely "duct taping" few things is in practicality no problem)
[*]I would use some type hinting/checking for method arguments. Maybe *optional *type hinting for arguments passing references of class instances like in PHP5.
[/LIST]
All in all, I like Python and I have found a use for it, though I would probably not use it for some large scale project. Maybe when I get more experience with it and my paradigms will shift I'll be willing to do even that.

---

### Post by CptPicard on 2010-03-07
> **__jan said:**
> 
[LIST=1]
[*]Python's OO capabilities feel like somehow crudely hacked into the thing as if they almost shouldn't be there.

It felt like that to be to begin with, too, but one just has to understand that Python's OOP is not Java's or C++'s OOP. Everything is an object, and user-defined classes are just a kind of blueprint namespace for the construction of objects...
 
> 
[*]Superfluous use of *self*

There is a good reason as to why the self is explicit ... the reason for that is that the connection between methods and classes is looser in Python than in compiled, static-typed languages. The idea is that a function can be a separate entity from a class, and/or it could be used from outside of an object on *any other* compatible object. You can even add functions to a class at runtime, as long as they take the appropriate object as their first argument.

> 
[*]Non-existent scopes (name mangling would not do)

Hmm... Python's scoping rules are good enough so that I don't think I've ever run into actual problems...

> 
[*]Inability to explicitly declare property members (you just assign *instance.propName = value* and it pops into being, no warning)

That's because objects are hashes. Either there is a value by that name or there isn't. :)

> 
[*]No interfaces

Interfaces in Python are implicit. This follows from the philosophy of duck-typing -- an object follows an "interface" by simply implementing it correctly. IMO, documentation is expected to be there anyway, and an example demonstrates just fine how it is supposed to work. Having a specific language mechanism for spelling out what it contains would be superfluous... of course, in a statically compiled language things are different.

---

