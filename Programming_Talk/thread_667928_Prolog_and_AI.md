---
title: "Prolog and AI"
date: 2008-01-14
forum: Programming Talk
---

### Post by slavik on 2008-01-14
Does anyone by chance have any nice books to recommend on Prolog and how it related to Artificial Intelligence?

---

### Post by CptPicard on 2008-01-14
I've got *Ivan Bratko: Prolog Programming for Artificial Intelligence*.

Unless you have an explicit need for some kind of clause satisfaction engine, I wouldn't bother with Prolog... you just end up with a bunch of contrivances and really weird-looking code trying to shoehorn everything into a guided depth-first search of possible solutions.

---

### Post by hod139 on 2008-01-15
I second CptPicard's advice on not using prolog for AI.  prolog is more useful for theorem proving (though I prefer the more lisp like syntax of [Athena]("http://www.cag.csail.mit.edu/%7Ekostas/dpls/athena/") to prolog).  For AI research stick with lisp, or lisp like (e.g. scheme, ml) languages.

---

### Post by slavik on 2008-01-15
Sorry, but it must be prolog.

What about Prolog's constraint programming? That's very nice, isn't it?

---

### Post by hod139 on 2008-01-15
> **slavik said:**
> Sorry, but it must be prolog.

What about Prolog's constraint programming? That's very nice, isn't it?

I don't know of any books, but you partially answered your own question.  Prolog is useful for a subset of AI research, logic programming.  As you said, this is basically constraint satisfaction programming.  You can probably write a good (but slow) sudoku solver in prolog.

---

### Post by public_void on 2008-01-15
Prolog is very powerful in expressing complex ideas in very few lines. To successful program using it forget everything you know about conventional programming. All you need to know is recursion.

As suggested, Ivan Bratko: Prolog Programming for Artificial Intelligence is a good book.

---

### Post by slavik on 2008-01-15
thank you guys for the book suggestion. when I searched google for "best prolog book" the amazon's page for the book comes up as first match. :)

EDIT: any recommendation on a Prolog interpreter? (I have SWIPL installed and was told that bProlog is also nice).

---

### Post by popch on 2008-01-15
> **slavik said:**
> any recommendation on a Prolog interpreter? (I have SWIPL installed and was told that bProlog is also nice).

SWI is very pleasant. It also has some very nice extensions such as constraint logic, with references to literature and research, as far as I remember.

The "beginner's" book on Prolog ([http://www.amazon.de/Programming-Prolog-William-F-Clocksin/dp/3540175393](http://www.amazon.de/Programming-Prolog-William-F-Clocksin/dp/3540175393) also offers some insights into AI.

Don't let yourself be misguided. You can do very valuable AI projects using just an inference engine. There are many kinds of AI. You can even do fuzzy logic in Prolog if you really want to.

Some time ago, the Japanese launched an AI initiative which was based on Prolog. I haven't any sources on that, but you might want to look in that direction, too.

---

### Post by pmasiar on 2008-01-15
Japamese 5GL was a failure by some definition: [http://en.wikipedia.org/wiki/5GL](http://en.wikipedia.org/wiki/5GL) and [http://en.wikipedia.org/wiki/Fifth_generation_computer_systems_project](http://en.wikipedia.org/wiki/Fifth_generation_computer_systems_project)

It might not be entirely true. I was lucky enough to be on a talk by some 5GL expert (name evades me) who claimed they (FGCS) set up task so complex that accomplishing even 10% would advance CompSci, what I believe they did.

---

### Post by popch on 2008-01-15
> **pmasiar said:**
> Japamese 5GL was a failure by some definition:(...)
It might not be entirely true. (...).

I think that the research alone is worth more than its cost, much in the way that the research invested into the moon landing project by some of the major nation was more worth than a few pounds of stones brought home from there.

---

### Post by RIchard James13 on 2008-01-18
I heard a slightly different story about the Japanese project than what is in the wikipedia article.

What I had heard was that although they could achieve many LIPS (Logical Inferences Per Second) they could still not solve the problems using Hard Logic. 

Later on I read an article in Scientific American where they said that the problem with Hard Logic is that we try to solve problems using a logical calculus but we disregard the need for knowledge in such endeavors. The article talked about frames for knowledge and Knowledge Based Systems.

Recently I saw an example of that in a Turing contest. The judge asked one question and that enabled them to distinguish between the Human and the Computers. The question was "what is larger your big toe or a jumbo jet?"

Many research projects have been spawned to fill this knowledge gap between the machine world and the human world but I don't know if any of them were successfully able to find ways of encoding concepts so that machines could understand them.

Personally I think the grand failure of the Japanese was they tried to do too much. No computer system can be an expert at all things, in fact no human is either. What they could have done is constrained any future research in specific areas of knowledge and worked on the encoding of knowledge.

And that is about the extent of my knowledge of AI.

---

