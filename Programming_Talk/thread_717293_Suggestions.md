---
title: "Suggestions?"
date: 2008-03-06
forum: Programming Talk
---

### Post by nateperson on 2008-03-06
So I'm working on learning Perl for use in bioinformatics.  I've been reading online doc's and have ordered O'Reilly's "Beginning Perl for Bioinformatics" and "Learning Perl".  

And I'm looking for other suggestions or warnings/pitfalls  that'll help a inexperienced programmer such as myself, learn Perl.

Thanks.

Nate

---

### Post by LaRoza on 2008-03-06
You will find Perl to be very powerful, but very easy to write messy code.

I suggest you take more time to study how to write things in a way that you can understand later. 

Also, comments will come in handy, especially for compact statements.

---

### Post by pmasiar on 2008-03-06
- Check perlmonks.org website with the best experts. 
- Be very careful about writing maintainable code - Perl is jokingly called "write-only" language, because is easy (without efforts to do opposite) to write hard to read code.  As Larry Wall said, Perl gives you enough rope to hang yourself.
- Learn (google) for Perl idioms and best practices  - Perl is very idiomatic language.
- Read also books about coding style, data structures, and about unit testing. Syntax is not all the problems in programming.
- Read forum's sticky FAQ: you will need to ask more questions later, and you need to learn how to ask questions smart way (it is obvious from post title that you did not :-) )

---

### Post by nateperson on 2008-03-06
> - Read forum's sticky FAQ: you will need to ask more questions later, and you need to learn how to ask questions smart way (it is obvious from post title that you did not  )
I know, and I know I know better, but sometimes the difference between knowing and doing can be pretty big some times... Classes were cancelled today cause of weather, mid terms just ended and spring break starts tomorrow... full mental processing has been hit or miss much of the day... 
Not an excuse, just a happy fact...  :)
Thanks again,

Nate

---

### Post by naugiedoggie on 2008-03-06
> **nateperson said:**
> So I'm working on learning Perl for use in bioinformatics.  I've been reading online doc's and have ordered O'Reilly's "Beginning Perl for Bioinformatics" and "Learning Perl".  

And I'm looking for other suggestions or warnings/pitfalls  that'll help a inexperienced programmer such as myself, learn Perl.

Thanks.

Nate

Speaking as one who started on perl, my advice would be "don't."  But that's probably not best advice. ;-)

It's very hard to write legible, maintainable code in perl because it's built very much like a human language -- idiomatic in ways specific to the individual programmer.  It does so much under the hood that it is all too easy to become used to taking advantage of side effects in ways that are not obvious to anyone but you.

That said, my advice would be to take an oath that you will learn to write properly structured code, using modules, subroutines and code blocks.  And keep that oath.  Unfortunately, if you don't already know how to do that (from knowing another language), then you will have to study existing perl applications and modules, in order to see what good code looks like.  That's more work for you.  But I believe you will see the payoff later.

Perl is cool.

Thanks.

mp

---

### Post by pmasiar on 2008-03-07
Another option is to learn Python instead :-) Perl has more legacy books and maybe modules, but Python has the future - and is readable and clean.

As they say, Python is executable pseudocode, Perl is executable line noise :-)

---

### Post by LaRoza on 2008-03-07
> **pmasiar said:**
> Another option is to learn Python instead :-) Perl has more legacy books and maybe modules, but Python has the future - and is readable and clean.

As they say, Python is executable pseudocode, Perl is executable line noise :-)

It was bound to happen ;)

@OP The sticky has two threads **Why To Love/Hate [Perl|Python]**, read them.

You might want to look at Python, Perl, Ruby and Tcl just to see what they are like, as they are often used for the same purposes and each have a lot of users that prefer them over the others.

---

### Post by nanotube on 2008-03-07
> **LaRoza said:**
> It was bound to happen ;)


hehe yea, i was reading the thread just waiting for the "python" suggestion to float up :)

---

### Post by LaRoza on 2008-03-07
> **nanotube said:**
> hehe yea, i was reading the thread just waiting for the "python" suggestion to float up :)

Well, the OP has a specific purpose and it doesn't seem to be text processing, so other languages might be of interest.

---

### Post by nanotube on 2008-03-07
> **LaRoza said:**
> Well, the OP has a specific purpose and it doesn't seem to be text processing, so other languages might be of interest.

i didn't say it's bad that it was suggested (being a fan of python myself). :)

indeed, it seems that there are some bioinformatics-specific resources for python, as a web search for "python bioinformatics" reveals. 
specifically the following may be of use:
[http://www.onlamp.com/pub/a/python/2002/10/17/biopython.html](http://www.onlamp.com/pub/a/python/2002/10/17/biopython.html)
[http://biopython.org/wiki/Main_Page](http://biopython.org/wiki/Main_Page)
[http://www.dalkescientific.com/writings/NBN/](http://www.dalkescientific.com/writings/NBN/)

---

### Post by LaRoza on 2008-03-07
This seems to be an interesting site (For Perl and bio) [http://www.bioperl.org/wiki/Main_Page](http://www.bioperl.org/wiki/Main_Page)

---

### Post by Can+~ on 2008-03-07
I started with... actionscript! *gasp*, but that was long time ago, and I remember, that I wondered how everything works, why magically doing a "a = new Object()" filled a with all sorts of functions and properties.

Later, I entered University and we got started with C, and the beauty of C is that it teaches you how every other language is based, the idea of pointers, structures, etc.

Now I got started with Python, and I'm loving it. with the mixed knowledge from C that makes me understand how things work under the hood and on top.

Anyway, my point is, that any language is a point of entry to programming, but the things you'll learn on your first language, will be dragged to future ones. I would suggest anyone to learn python because it's easy, and teaches you good practices like indentation (which is compulsory in python, but optional on most { } languages) and maybe start with OOP, but if they want to know what really makes things work go learn C (I would say assembler, that's another story)

---

### Post by nateperson on 2008-03-08
Thanks ya'll.

For now I'm stuck learning Perl.  Thats what the Lab I'm doing my summer internship with is using.  Probably using the BioPerl that LaRoza suggested.  I know I've seen other Lab postings that say they want C/C++ and Java so I'll probably be working on those next.

---

