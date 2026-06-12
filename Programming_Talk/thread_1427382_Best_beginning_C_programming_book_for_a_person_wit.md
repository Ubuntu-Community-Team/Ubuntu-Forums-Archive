---
title: "Best beginning C programming book for a person with some programming experience?"
date: 2010-03-11
forum: Programming Talk
---

### Post by superarthur on 2010-03-11
I've searched the forum, read some of the posts on similar topics, but not satisfy with the answers they provide. I prefer a book that I can read, so I don't have to stare at the screen for too long.

I know Java and Perl (I am not an expert programmer, I just write simple programs to automate some tasks.) So I know a bit of programming, but not a lot.

Lots of people suggest The C Programming Language (2nd Edition). But isn't it a bit dated? And it only have 274 pages, isn't it a bit too thin? It's £22.25 on Amazon. I expected a thicker book for this price. And I afraid that it may be too hard.

Is C All-in-one Desk Reference for Dummies a good choice? Some people say it doesn't have enough depth, but I suppose 840 pages would contain more than enough information. I've also heard that there are lots of typos in the book. I don't want to start debugging before I learn the basics of the language. :P

Does anyone have better suggestions for someone at my level?
Thanks

---

### Post by ApEkV2 on 2010-03-11
It doesn't matter if k&r is old, C hasn't really changed since then.
And don't get a reference book to learn from.  k&r is probably what you need.
Also C isn't really the best language to automate tasks, it isn't a high level language.

---

### Post by Bachstelze on 2010-03-11
Go with K&R.

---

### Post by CptPicard on 2010-03-11
> **superarthur said:**
> 
Lots of people suggest The C Programming Language (2nd Edition). But isn't it a bit dated? And it only have 274 pages, isn't it a bit too thin? It's £22.25 on Amazon. I expected a thicker book for this price. And I afraid that it may be too hard.

Definitely get "K&R". It's not "thin", it is just concise and to the point... which is what you want; extra pages would be just fluff. And it's not dated; it's the same language as today (with minor changes in C99). I also would believe it's exactly on your level, and if it's not, it's about time you get used to that level ;)

---

### Post by Compyx on 2010-03-11
You can't go wrong with K&R2. Another good read is 'Expert C Programming - Deep C Secrets' by Peter van der Linden, describing some common pitfalls when it comes to C coding.

Under no circumstances touch the books by 'Herbert Schildt', avoid those like the plague.
I also have yet to see a half-decent 'dummies' book, so I'd avoid those too.

---

### Post by WebDrake on 2010-03-11
I got a great deal out of 'Programming in C' by Stephen Kochan.

---

### Post by superarthur on 2010-03-11
Thanks all. I will get the book from my uni's library.
I started with Java, and used a book from 2004, and some of the examples in the book was already outdated. (i.e. it doesn't compile with the newest JDK) That's why I am a bit sceptical about using a book older than me. lol
To ApEkV2: I started programming because I needed to automate some tasks. I just want to learn C for fun. ;) I also plan to learn ada (after reading the wikipedia page on Ada Lovelace lol), lisp (after reading xkcd :P), python (partly because of xkcd, but also because it's popular) and C++.

---

### Post by wmcbrine on 2010-03-11
K&R is a great book, a classic of the genre. Don't neglect it. But I have to confess, I learned C from... a Herbert Schildt book.

That was about 14 years ago. There were errors, like "void main", that I already knew about at the time, and other problems -- all obvious; I wasn't misled into any bad habits. But it also had a very lucid style, and it finally got me to actually learn C, after I'd made a half-hearted attempt at it with the K&R book. So I have a soft spot for this much-maligned author.

---

### Post by superarthur on 2010-03-11
btw, I actually thought that Java: A Beginner's Guide by Herbert Schildt was quite good
I love its layout and presentation. (words are big with quite a few pictures lol) I haven't spent a lot of time on it, because I was changing from Java to Perl at that stage. (and now Perl stay as my main programming language)

---

### Post by pbrane on 2010-03-11
One of the reasons the K&R book is "thin" is that C language consists only of its operators. C programming usually relies on standard ( and some non-standard ) libraies. The book has some great examples. And as was pointed out, it is concise.

---

### Post by superarthur on 2010-03-13
how to learn about the standard libraries?

---

### Post by rabidbadger on 2010-03-13
If you go with K&R (and you really should, IMHO), then [this]("http://c-faq.com/%7Escs/cclass/krnotes/top.html") is useful to read alongside it.

A nice, short, library (C89) reference can be found [here]("http://www.acm.uiuc.edu/webmonkeys/book/c_guide/index.html"). Also don't forget [the FAQ]("http://www.c-faq.com/index.html").

After the basics, *what* you intend programming will indicate what additional material you'll find useful; and, depending upon that, it's worth remembering that newer books are not necessarily going to be 'better' than older ones. For example, I still find [the old Stevens]("http://www.amazon.co.uk/Advanced-Programming-UNIX-Environment-APC/dp/0201563177/ref=sr_1_13?ie=UTF8&s=books&qid=1268489952&sr=1-13") so useful that I haven't felt the need to shell out for the 2nd ed.

---

### Post by gmargo on 2010-03-13
In addition to the classic K&R, I always liked "C: A Reference Manual" by Harbison & Steele.  I'm so old I have a first edition (currently the 5th edition is available: [http://www.careferencemanual.com/](http://www.careferencemanual.com/)).

---

### Post by superarthur on 2010-03-14
I've got K&R from the library, and some pages are falling apart.
Anyway, how do I compile? Do I need the build-essential package?
Does ">cc hello.c" works in ubuntu, or do I need to have the build-essential package and use ">gcc hello.c"?

---

### Post by wmcbrine on 2010-03-14
Yes, you need build-essential.

cc is an alias for gcc in Ubuntu. I don't think it makes any difference which you use.

---

