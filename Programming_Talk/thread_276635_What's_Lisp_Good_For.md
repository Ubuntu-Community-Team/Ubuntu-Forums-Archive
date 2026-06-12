---
title: "What's Lisp Good For?"
date: 2006-10-13
forum: Programming Talk
---

### Post by Ubuntist on 2006-10-13
Having not done much programming for a long time, I recently wanted to learn some up-to-date programming techniques.  With some input from this forum, I've picked up Python and Ruby.  I like both, although I do have some reservations about dynamic typing, and I wish they ran faster (would it be that difficult to add the option of compiling? [I know that Python code can be "compiled", but, as the documentation explains, it's not really compiling in the usual sense of the term, and it doesn't do that much for execution speed]).

I've also had a look at Lisp.  I've seen incredibly compact Lisp code for handling idealized AI problems.  I'm OK with the  syntax.  But in trying to apply Lisp to practical problems, I've been disappointed that it never seems to be so wonderfully compact and expressive as it is for textbook problems.  For example, have a look at the benchmarks in the Computer Language Shootout: [http://shootout.alioth.debian.org]("http://shootout.alioth.debian.org")/  . The Lisp codes are fast -- usually much faster than Python or Ruby.  But the codes themselves are usually longer.  Or have a look at the code in *Practical Common Lisp* [http://www.gigamonkeys.com/book]("http://www.gigamonkeys.com/book").    As an example, it builds code for managing a music database, to prove that Lisp can be applied to practical problems.  Yet that code doesn't seem any shorter than the Ruby equivalent.

Had I written music database code in Lisp and found that it wasn't any more compact than equivalent Python or Ruby code, I'd have assumed it was because I didn't know Lisp well enough.  But *Practical Common Lisp* was written by an expert.

So what's the point?

---

### Post by Arndt on 2006-10-13
> **Ubuntist said:**
> 
Had I written music database code in Lisp and found that it wasn't any more compact than equivalent Python or Ruby code, I'd have assumed it was because I didn't know Lisp well enough.  But *Practical Common Lisp* was written by an expert.

So what's the point?

If Lisp had been shorter, would you then have asked what's the point of Ruby and Python?

---

### Post by theCore on 2006-10-13
Lisp is good for twisting your head.

If you really want to learn Lisp, I recommend that you start with Scheme, not Common Lisp. I like to compare Scheme to C. They are both simple and elegant languages. Common Lisp is a big hairy and ugly beast. Just as C++, Common Lisp has been designed for industrial purposes.

At the end, you will probably never directly use Lisp. However, all the techniques will learn will make you a more attentive programmer. You will start to see all sort of patterns in other languages that you will start to use and love.

Don't give up. Learning Lisp is difficult and long, but rewarding at the end.

A quick start:
$ sudo aptitude install mit-scheme
$ firefox [http://mitpress.mit.edu/sicp/full-text/book/book.html](http://mitpress.mit.edu/sicp/full-text/book/book.html)
$ scheme
1 ]=> (edit)

Enjoy!

---

### Post by Ubuntist on 2006-10-13
> **Arndt said:**
> If Lisp had been shorter, would you then have asked what's the point of Ruby and Python?

If the Lisp codes were generally shorter, I'd probably have said to myself "Ah, that must be a result of the sort of expressiveness and power that Lisp afficionados like to talk about."  But since the Lisp codes turn out to be, if anything, longer, I'm just wondering if the other languages have surpassed Lisp in this respect.

---

### Post by Ubuntist on 2006-10-13
> **theCore said:**
> Lisp is good for twisting your head.

If you really want to learn Lisp, I recommend that you start with Scheme, not Common Lisp. I like to compare Scheme to C. They are both simple and elegant languages. Common Lisp is a big hairy and ugly beast. Just as C++, Common Lisp has been designed for industrial purposes.

Actually, I *did* start with Scheme.  It is elegant and beautiful.  And *SICP* is a great text; as one reviewer says, there's more in its footnotes alone than in most books.  I wish I had learned Scheme before learning any other languages; then there'd have been fewer limitations and bad habits to unlearn when picking up other languages.

When I looked at doing some practical things in Scheme, it began to seem a bit cumbersome.  Message-based OO is possible, for example, but it's a bit of a pain, because you have to do it all "by hand".  That's what made me look at Common Lisp.

> 
At the end, you will probably never directly use Lisp. However, all the techniques will learn will make you a more attentive programmer. You will start to see all sort of patterns in other languages that you will start to use and love.

This resonates perfectly with my experience.  I'm glad I looked into Scheme and Lisp, but it looks like they're probably not worth pursuing further for my purposes.  But I will probably come back, especially to Scheme, from time to time just to see how things could be done.

---

### Post by nereid on 2006-10-14
> **Ubuntist said:**
> If the Lisp codes were generally shorter, I'd probably have said to myself "Ah, that must be a result of the sort of expressiveness and power that Lisp afficionados like to talk about."  But since the Lisp codes turn out to be, if anything, longer, I'm just wondering if the other languages have surpassed Lisp in this respect.

Grandfather Lisp still offers something that is not possible with other languages. In Lisp everything is a list as a result you can change everything. Add to this the functional programming paradigma and you've got a language to wrap your head around which is still awesome. There are some things you can do in Lisp which you wouldn't ever consider in C (yeah, you could do this or that also in C but, come on, why shoot yourself in the foot?).

---

### Post by ak70 on 2006-10-14
I think code in Practical Common Lisp was "verbose" just because it was written by an expert, take the music database code as an example, the author was trying to show us "how to program in a lisp style". In fact, the code was divided into different levels of abstraction. It was very well-structured and some functions and macros are quite generic. I don't know how short Ruby or Python can be, but I don't think lisp is more verbose in general.

---

### Post by slavik on 2006-10-16
From what I understand, it is also used in A.I.

Very often, in AI, you want to analyze data (the world) and a technique of achieving your goal. Lisp allows you to create a way of generating techniques instead of just going step by step and trying to match every situation that is possible.

NOTE: this is what I understand about the subject and MAY be wrong or incorrect.

---

