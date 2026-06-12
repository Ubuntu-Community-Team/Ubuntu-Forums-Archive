---
title: "What can be done to improve the language you work with?"
date: 2007-12-18
forum: Programming Talk
---

### Post by Majorix on 2007-12-18
Simple, what can be done to improve your programming language?

I have once seen the creator of the most famous Python IDE (SPE if you have to know) writing in these forums (he replied in one of my topics) and who knows, maybe the authors of Perl, Ruby, Python and other languages which are still being developed are browsing these forums too.

Even if they don't, it would be nice to hear what are the downsides to each of the languages from their experts. Don't you think?

Please be objective in your comments and don't bash the language. Or I am sure some heavy fan of it would bash you in turn.

So please give it a go.

---

### Post by Fixman on 2007-12-18
Well, I use C pretty often, and think how nice would be the world if all the functions from LIBM would be in LIBC...

---

### Post by tyoc on 2007-12-18
I not think the author of SPE is an author of the lang that is supporting his IDE.

You can't "improve a lengauge" without modify it internally.

Instead you can improve the other tools, libs, etc that surround it, and in fact your programming skill will also help.

---

### Post by Majorix on 2007-12-18
@tyoc:
I didn't say he was, did I? I was just giving an example of how famous software devs visit these forums. We don't have access to the internal code so we can't improve it, but you have to know some people do and that they could be accessing these forums. Maybe, who knows; but like I said, even if they don't it is still nice to see the downsides listed here for newbies to see.

---

### Post by LaRoza on 2007-12-18
> **Majorix said:**
> @tyoc:
 We don't have access to the internal code so we can't improve it, but you have to know some people do and that they could be accessing these forums. Maybe, who knows; but like I said, even if they don't it is still nice to see the downsides listed here for newbies to see.

For most things, you do have access.[http://www.python.org/download/](http://www.python.org/download/)

As for "downsides" it is likely this will only result in syntax discussions, which are pointless.

---

### Post by slavik on 2007-12-18
Perl5.8 OO is not as nice as in most languages :(

---

### Post by Majorix on 2007-12-18
> **LaRoza said:**
> For most things, you do have access.[http://www.python.org/download/](http://www.python.org/download/)

As for "downsides" it is likely this will only result in syntax discussions, which are pointless.

Yes you do, but its not like you are in their team, so you have to do all the optimization on your own, which is quite unrealistic; if it was so easy one could do on his own they would have implemented it already.

And I hope this doesn't degenerate into a pointless discussion, but so far it's nice. Don't be too pessimistic.

@slavik:
The thing is that Perl doesn't claim to be "fully" OO like for example Ruby does. But it would still be nice for Perl to be fully OO too, it is a nice thing :)

---

### Post by tyoc on 2007-12-18
that was not mean for you Majorix, if I write something to specific people I write the nick, like this time.

I mean by "you", anyone who is reading the post, if all people that is reading the post answer to me specifically, thus I will get at less 35 answers or more.

There no exist such thing as "improve a language" from outside, proof? there is already a link to some code of a lang (the lang at end will depend in the implementation and choices, like compiled, interpreted, executed in a VM, etc etc).

I still

>  You can't "improve a lengauge" without modify it internally.
 
Instead you can improve the other tools, libs, etc that surround it, and in fact your programming skill will also help.Yes, for clarify, "you" mean any person reading that.

---

### Post by pmasiar on 2007-12-18
> **Majorix said:**
> Simple, what can be done to improve your programming language?

To improve language syntax, you need to be brilliant and know about language design and implementation a lot, then join developer's mailing list. And be prepared to implement what you propose, even before it was accepted, so learn language internals first.

Simple thing to do is to read the documentation and suggest improvements - I did :-)

To improve language usefulness is **much** simpler than changing the syntax, just write and share  code which does something useful. It does not have to be new library module: learn to write tests and add some tests. Report a bug, if you know how, fix it. Again, improve documentation for some library you use. Translate docs to another language. BTW Google started new projects for that, easy to earn google t-shirt for students before college.

Even simpler is to help people learn the language by gathering good links on your website (or wiki), respond to questions on forums - learning of the language will be improved, one person a a time :-)

> maybe the authors of Perl, Ruby, Python and other languages which are still being developed are browsing these forums too.

I hope they don't - (way too much noise here) -  a do something more productive instead with their time :-) Less skilled people (like me) can answer the questions and link to proper pages.

> Even if they don't, it would be nice to hear what are the downsides to each of the languages from their experts.

Experts publish thoughts on their blogs, usually they don't have to troll forums for feedback.

So ie Guido posted regrets he has about decision made for Python years before he started working on Python 3000 for real, just check his blog. I am not aware about blog posts/info with regrets by designers of Perl or java tho... maybe they claim MSFT defense: "it is not a bug, it is a feature" :-p

BTW Syntax of Python 3.0 was closed and fixed, but new discussion was started about Python 4.0, so if you want to, get involved. :-)

And to improve it, you first need to understand it, and understand consequences of other options. For me, it is simpler to trust the experts doing it right :-)

---

### Post by jespdj on 2007-12-19
I'm a Java software developer. Last week I was at [JavaPolis]("http://www.javapolis.com"), the largest Java conference outside the USA.

There's a lot that can be improved in Java and a lot of smart people are constantly busy inventing improvements and new features for Java.

A lot could be improved in Java's standard library. For example, the library could be partly rewritten to take advantage of generics as much as possible (generics is a feature added in the language with version 1.5). But it's not really possible to do this without breaking backward compatibility. Likewise, there is some deprecated stuff in the library that won't be removed because it would break backward compatibility.

What I would like is a literal syntax for Maps and Lists in Java.

After seeing at JavaPolis to what kind of horrible code closures can lead in Java, I'm against adding closures to Java (at least in the form as currently is proposed).

---

### Post by Wybiral on 2007-12-19
IMO syntax is a much harder thing to improve, and with the variety of syntax styles out there, you can probable find one that you're comfortable with. After you find the syntax you like, extending the language is just a matter of finding and writing libraries to do what you want.

---

### Post by pmasiar on 2007-12-19
Instead of Java with generics, you can use Jython. Use all Python syntax (2.3 IIRC, not the most recent yet) and flexibility, and all Java libraries. You get more flexible exceptions for free :-)

---

### Post by pmasiar on 2007-12-20
[How Does a Programming Language Stagnate?](http://www.oreillynet.com/onlamp/blog/2006/06/how_does_a_programming_languag.html) - interesting post about how language is being evolved, by chromatic, well known Perl guru. How improving libraries is different from improving core language.

This is IMHO area where Python's way of evolving is superior. Pushing non-fundamental features of language into external libraries, it allows to evolve those libraries at faster rate than core language - and after they mature, include these libraries as standard modules. Putting too much of functionality into core language makes it stagnate - as developers of new libraries cannot use new language feature because users might not upgraded yet. This is engineering, fine balancing of 'pro' and 'con'.

Big part of it is 'taste'. Or, as Python zen says: "Never is sometimes better than right now" :-)

Edit: Further following links from [this perlmonks discussion](http://www.perlmonks.com/?node_id=561229)  pointed me to [http://en.wikipedia.org/wiki/Sapir-Whorf_hypothesis](http://en.wikipedia.org/wiki/Sapir-Whorf_hypothesis) : "particular language's nature influences the habitual thought of its speakers". Language we use determines how we think about the world, and how we interact with it (and solve tasks). So this meme is even deeper, and has name. :-)

---

