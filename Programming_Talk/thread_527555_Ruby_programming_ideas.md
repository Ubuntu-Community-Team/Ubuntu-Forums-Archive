---
title: "Ruby programming ideas"
date: 2007-08-16
forum: Programming Talk
---

### Post by mssever on 2007-08-16
I've been wanting to learn Ruby for some time now. I've read most of the pickax book and I really like the philosophy behind Ruby. But, I haven't really gotten my hands dirty yet. I've been casting about for ideas for a useful (i.e., not toy) **smallish** program I could write to learn Ruby. But so far, I haven't come up with anything interesting. I'm wondering if anyone has any suggestions. (Yes, I know this is lame.)

In addition, I don't think that I understand very well how to design programs in an object oriented way. Can someone recommend some resources on that? I'm basically a procedural programmer who looks enviously at OO code. OOP just seems to me to be so much more elegant and maintainable.

---

### Post by emperon on 2007-08-17
you will want to start from python. Ruby is more powerful meaning harder to learn  as a beginner. With OOP, there are plenty of books specialized on OOP. I would say learn OOP while you are learning python. 

btw, I learnt OOP from Bruce Eckel's free online Thinking in C++ book. It  was nice

---

### Post by Jessehk on 2007-08-17
> **emperon said:**
> you will want to start from python. Ruby is more powerful meaning harder to learn  as a beginner. With OOP, there are plenty of books specialized on OOP. I would say learn OOP while you are learning python. 

btw, I learnt OOP from Bruce Eckel's free online Thinking in C++ book. It  was nice

He has already learned Ruby. Why would he start from square one? Just because there are many Python advocates here (I like it too), it doesn't mean another technology is irrelevant.

---

### Post by LaRoza on 2007-08-17
> **mssever said:**
> 
In addition, I don't think that I understand very well how to design programs in an object oriented way. Can someone recommend some resources on that? I'm basically a procedural programmer who looks enviously at OO code. OOP just seems to me to be so much more elegant and maintainable.

[http://www.computer-books.us/cpp_4.php](http://www.computer-books.us/cpp_4.php)

Ruby is entirely Object Oriented, so you might have a little trouble with it, but the above book (free) covers OOP using C++.

---

### Post by pmasiar on 2007-08-17
Everyone's favorite first project is text-based adventure game, like [original Adventure](http://en.wikipedia.org/wiki/Colossal_Cave_Adventure) - and it is lots of fun! My game engine (in Python) is about 1 page!

> **emperon said:**
> you will want to start from python. Ruby is more powerful meaning harder to learn  as a beginner. 

Although I am strong Python promoter, I don't see why experienced programmer should start with Python. Yes, Python is better and everything, but Ruby is about the same in expressiveness

I strongly disagree that Ruby is more powerful. Ruby code just looks more hackish (like Perl) and might be more terse - but again, you lose lines for closing braces, so it might be even longer afterwards.

So take look at Python, and decide if you want to switch - maybe hackers around you have some preferences. Because Python is not object-obsessed, you can mix procedural and OOP code easily. Python has also more libraries (that's for sure), and possibly more books. Community is larger, development mailing list is is in English (and noy japanase), perks like that, but no major differences like with Java/C#

It is close call, but sadly there is only one language to rule them all :-) (Yes it was a joke)

Yes, and book: best intro books to anything is O'Reilly's "head-first" series: [http://www.oreilly.com/catalog/hfobjects/](http://www.oreilly.com/catalog/hfobjects/) is very good.

---

### Post by mssever on 2007-08-17
> **LaRoza said:**
> [http://www.computer-books.us/cpp_4.php](http://www.computer-books.us/cpp_4.php)
Thanks for the link. I've started reading it.
> **pmasiar said:**
> Everyone's favorite first project is text-based adventure game, like [original Adventure]("http://en.wikipedia.org/wiki/Colossal_Cave_Adventure") - and it is lots of fun! My game engine (in Python) is about 1 page!Hmmm... I'm not much of a gamer, but thanks for the suggestion.

One of my reasons for wanting to learn Ruby is so I can compare it with Python more accurately. Python has some features that I don't particularly care for, such as its lack of braces and it's bolted-on and inconsistant OO--such as specifying ```
def foo(self):
``` and the fact that some part of the library is OO and some is procedural (reminds me a little of PHP's incredible inconsistancy, though PHP is much worse, of course). On the other hand, I'm sure that I'll find some things not to like about Ruby. I'm not trying to start a Python vs. Ruby debate. I'm looking to make a hands-on comparison. Oh, and Ruby's blocks look pretty cool.

Ultimately, I think that there's a lot to be learned about programming from exposure to various languages and the way they encourage you to approach a problem. So I imagine I'll eventually end up learning Python and Ruby reasonably well. (I'm not interested in anything like C/C++ at this point, though. Too low level for now.)

The reason that I'm interested right now in comparing Python and Ruby is because I've got a fairly large project in mind that I want to start. I've done most of the planning and specification already and I'm nearly ready to begin coding. Of course, before I can begin code, I need to choose a language, and I want some experience in both languages before choosing between Python and Ruby. Of course, around here the canonical answer is "choose Python." :)

---

### Post by pmasiar on 2007-08-17
I don;t want to argue with you, just explain:
> **mssever said:**
> Python has some features that I don't particularly care for, such as its lack of braces
Lack of braces has multiple positives:
- Code is always properly indented. Easier to quickly look through the code. 
- There are no multiple ways to place braces, and coding standard preferences: one simple standard, so anyone can read code of other people without problems. It leads also to easier code sharing
- saves one line for closing brace. :-) Seriously, every little line helps.

Many former C/Perl hackers, including me, are put off with significant whitespace. But after 15 minutes, it becomes not a problem.

If you don't trust me, maybe little [article ](http://www.linuxjournal.com/article/3882) from famous hacker [ESR](http://en.wikipedia.org/wiki/Eric_S._Raymond) will make you .... reconsider?

> and it's bolted-on and inconsistant OO--such as specifying ```
def foo(self):
``` 
It allows you to rename current instance to s or this or whatever you prefer. Other languages have reserved keyword for that, or magically add it. Python does not recognize need for magic: "Explicit is better than implicit" is common saying in Pythonland.

> I need to choose a language, and I want some experience in both languages before choosing between Python and Ruby. Of course, around here the canonical answer is "choose Python." :)

Well, not only here, but also in Google :-) and Canonical: Python is also preferred language of Mark Shuttleworth (made him $500M), Tim Berners-Lee ("can be learned on one set of batteries in a plane") and many other hackers: Python has bigger and more diverse community - way beyond web apps as Ruby niche is.

Of course compare all you want, and preferences of your friends and local gurus are also important. Just wanted to explain misunderstandings :-)

---

### Post by mssever on 2007-08-19
> **pmasiar said:**
> Lack of braces has multiple positives:
- Code is always properly indented.
I recently came across a Python program whose author chose to use single space indentation. There were no blank lines or comments, either. The result was more incomprehensible than your typical Perl program (though a bad Perl program is a lot worse). Indentation is only useful when it's applied intelligently. I always indent my code regardless of which language I'm using.
> Easier to quickly look through the code.Maybe once you get used to it. I sometimes have trouble in Python noticing where a block ends, because there's no strong visual cue; just a drop in indentation. For a fast glance through code, I like to see }.
> - There are no multiple ways to place braces This problem would be solved if everyone simply used the Only True Way to place braces. :)
> If you don't trust me, maybe little [article ]("http://www.linuxjournal.com/article/3882") from famous hacker [ESR]("http://en.wikipedia.org/wiki/Eric_S._Raymond") will make you .... reconsider?I'd read that article before, but it was a good re-read. Testimony from such hackers is good evidence of the strength of Python. But that makes me wonder: Is Python so much more popular than Ruby because it's superior or because Ruby is newer (and consequently has a smaller library) and until recently was only accessible to those who can read Japanese? After all, Python didn't gain its popularity in a day.
> It allows you to rename current instance to s or this or whatever you prefer.That's good to know.

---

### Post by pmasiar on 2007-08-19
> **mssever said:**
> I recently came across a Python program whose author chose to use single space indentation. 

It is hard to make idiot-proof programs, because universe keeps making better and better idiots all the time. :-)

single-space indentation is as stupid in Python as putting all Perl code into one line. It is valid but stupid. Best practices call for 4 spaces.

> Indentation is only useful when it's applied intelligently. 

Everything is better when applied intelligently. :-)

> I always indent my code regardless of which language I'm using.

But in many languages there are multiple standards, and code written by other standard than you are used to is rather incomprehensible (and you need to do mental adjustment all the time, or just go and reformat it). Python, by design, does not have this problem.

> Maybe once you get used to it. I sometimes have trouble in Python noticing where a block ends, because there's no strong visual cue; just a drop in indentation. For a fast glance through code, I like to see }.

If it will help you, you can add meta-syntactic end-comment "# } END" ;-)

>  This problem would be solved if everyone simply used the Only True Way to place braces. :)

Ask Linus :-)

> Is Python so much more popular than Ruby because it's superior or because Ruby is newer (and consequently has a smaller library) and until recently was only accessible to those who can read Japanese? 

OK, time for another link: [The hundred-year language](http://www.paulgraham.com/hundred.html)

I looked into Ruby after I was disgusted and burned by Perl, but Ruby is too much like Perl: too quirky, placing too much attention to save time on writing, disregarding readability. Python has one great insight: program is read **much** more often than written. Funny that not too much language designers pondered at that.

Ruby is OK. Comparing with other languages used for web apps developement, like VB/ASP or Java, Ruby is **much** better. It is quite better than Perl or PHP, that's for sure. I believe that Python has some slight edge over Ruby, but I know it is only slight edge. Ruby has Rails which is insanely great framework (especially compared to Java standard, Struts), and it was first such framework, Ruby was the king in his niche, so the spike in popularity. 

Python was used also outside of web, and in 2004 Guido even said (at Pycon, to boot!) that he does not use Python for web and does not care. At that time, joke was that Python has more web frameworks than keyword - and it was even not a joke but truth! Well, Guido got hired by Google and it changed his perspective! :-) Now Python community created couple of front-to-back web frameworks like Rails is (more programmers - more modules to pick from), but Django and TurboGears are indisputable leaders (optimized for slightly different use).

It will take 10 years to capitalize on slight advantage which Python has - but as you can see, Python is there for next 100 years, so we have time :-)

---

### Post by mssever on 2007-08-20
> **pmasiar said:**
> single-space indentation is as stupid in Python as putting all Perl code into one line. It is valid but stupid. Best practices call for 4 spaces.Incidentally, before I wrote my first Python program, I used two space indentation. Two spaces was a good idea back when I was using an 80 column terminal to write Java. But I independently realized that four spaces was much better for Python, and I now use four spaces for everything except HTML.
> I looked into Ruby after I was disgusted and burned by Perl, but Ruby is too much like Perl: too quirky, placing too much attention to save time on writing, disregarding readability.I took a look at Perl code and vowed never to touch that language! :)

Could you give an example of how Ruby is quirky? It seems rather straightforward to me. Actually, Python has a couple of features that seem a bit quirky to me.

One is the distinction between lists, tuples, and dictionaries. It would be nice if Python hid those details. (Ruby isn't perfect here, either.) Amazingly enough, PHP is the best in this area that I'm aware of. In PHP, there's really only one type of array: the associative array. But unlike Python dictionaries and the Ruby equivalent whose name I don't recall, the order of the elements is defined. That means that sorting the array is dead simple.

The other Python oddity that comes to mind is list comprehensions. It took me quite a lot of effort for me to figure out how to write one of my own. And they take a significant amount of time to parse (for me, at least)--nearly as long as a regular expression. But in Ruby, I could simply do something like ```
foo.each { |x|
    x = 'bar' unless x == 'baz'
}
```Of course, I could also write this on one line if I wanted to.

> Ruby is . . . quite better than Perl or PHP, that's for sure.At one time, I wondered why anyone could possibly want any language other than PHP for web use. Now, I wonder why I ever liked PHP. It certainly is well-optimized for web use, but it can easily become restricting and clumsy.

---

### Post by ankursethi on 2007-08-20
The Perl/Python/Ruby holy wars will continue forever. I've had a dip into Perl and Python and I must say that I put both of them on equal footing. While I haven't looked at Ruby much, I know a guy who programs in Ruby and seems to be loving it.

Given a choice, I would probably pick Python, but I disagree with the fact that any one of these languages is actually "better".

---

### Post by winch on 2007-08-20
> **mssever said:**
> One is the distinction between lists, tuples, and dictionaries. It would be nice if Python hid those details. (Ruby isn't perfect here, either.) Amazingly enough, PHP is the best in this area that I'm aware of. In PHP, there's really only one type of array: the associative array. But unlike Python dictionaries and the Ruby equivalent whose name I don't recall, the order of the elements is defined. That means that sorting the array is dead simple.

You can implement that sort of associative array in ruby pretty easily and no doubt it's just easy in python too.

```

a = [ ['name', 'steve'], ['food', 'chips'], ['money', 500] ]
a.assoc('name')
=> ["name", "steve"]

```

A [dictionary/hash]("http://en.wikipedia.org/wiki/Hash_table") is really a different beast.

---

### Post by pmasiar on 2007-08-20
> **mssever said:**
> One is the distinction between lists, tuples, and dictionaries. It would be nice if Python hid those details.

I **don't** think it is a good idea, they have completely different use. Tuple is good old C struct, where every item is different type, and not an expandable/shrinkable collection like array/list is.

For dict, it is substantial feature (for access speed: **just about everything** in Python is implemented as dictionary, and speed was **very** important) that values are unsorted, and can be of different types, which for list/array hardly makes a sense. And Python has also ordered dictionaries as specialty items, if you need them - hardly anyone does :-)

> list comprehensions. ...
```
foo.each { |x|
    x = 'bar' unless x == 'baz'
}
```

Ruby is more confusing (to me :-) ): You mean |x| is **not** the absolute value? It certainly looks like one. :-)

```

list_comprehension = [ f(x) for x in iterator_or_list]

```
I am not sure what you want to parse here :-) is there even any new syntax? same list literal syntax, same 'for' loop, just inside list literal.

Differences between Ruby and Python are slight, and certainly to learn something new you need to unlearn old, or at least realize that some aspect can be handled differently. It also helps to understand about what compromises were encountered, and what corners were cut... :-)

Then, there is another consideration: It takes substantial time to become if not expert, at least reasonably knowledgeable in a language, and after investing all that time, person might be reluctant to throw all this and dive into another language, only slightly different, with only slight advantages/disadvantages. 

I think that competition between Python and Ruby will be played on not on languages itself (they have mostly only style differences), but in libraries/application frameworks area. 

It will be interesting how much effort Sun will pour into JRuby (after they totally neglected Jython). Maybe they considered Python a competitor, so they let Jython die, but now they realized that java **direly needs** agile web app framework like Rails for JVM remaining relevant, and they decided to bet the farm on JRuby. And what will be consequences of Python replacing Lua as Mozilla extension language, and what will happen when $100 laptop students will start hacking 5-10 years from now.

Time will tell, for sure it will be fun to watch!

---

### Post by mssever on 2007-08-20
> **ankursethi said:**
> The Perl/Python/Ruby holy wars will continue forever. I've had a dip into Perl and Python and I must say that I put both of them on equal footing.I think that there's a difference between a holy war and a technical debate. By raising objections and seeing them answered, I learn more about a subject. Also, I think that if we could agree on a set of objective criteria, choosing the superior language would be fairly easy. However, since there is a broad range of sometimes-conflicting criteria, the real reason for using the right tool for the job rests in which criteria are important for a given task.

So, ultimately, I think it's possible to compare languages, and even assert that one is superior to another without descending into a holy war.

> **winch said:**
> You can implement that sort of associative array in ruby pretty easily and no doubt it's just easy in python too. Thanks for the tip. It's not as readable as native support, but oh well.

---

### Post by pmasiar on 2007-08-21
> **ankursethi said:**
> The Perl/Python/Ruby holy wars will continue forever. ... I disagree with the fact that any one of these languages is actually "better".

I would try to avoid Perl (once burned twice shy), but yes, after Python, Ruby would be my next choice. So I don't see any point in a religious war against Ruby.

But religious war against Java, that's completely different matter! That would be fun! :-)

---

### Post by mssever on 2007-08-21
> **pmasiar said:**
> But religious war against Java, that's completely different matter! That would be fun! :-)

But who would argue against you? We all know that Java is too verbose to be useful! :) <ducks>

---

