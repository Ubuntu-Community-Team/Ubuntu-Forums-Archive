---
title: "Suggestions on learning a new multiparadigm language"
date: 2009-07-08
forum: Programming Talk
---

### Post by prvteprts on 2009-07-08
When browsing Linux stuff, I often encounter things relating to Python. Sometimes I see some comparisons to Ruby or Perl. I have done some background checking and I found out these fall under the multiparadigm category somewhat. These have aroused my curiosity, and at the same time I want to learn a new language for the following reasons:

- to expand my knowledge (I feel like I'm getting stale)
- to be involved in the Linux or FOSS programming community

I decided to go along the lines of Python and Ruby because they seem to be the "in" thing in the FOSS world and perhaps in the industry as well. I want to contribute something to the community but I don't have enough time to be a kernel programmer or something like that... you know what I mean? But maybe I could help open-source projects even by just simply inspecting or contributing bits of higher-level code. Also I want to learn something licensed under GPL or a GPL-compatible license which Python and the like fall under.

I would be glad to get suggestions from the community. About me, I have a CS degree and I'm part of the academe. I mostly program in Java, but I also know C, C# - mostly procedural and object-oriented. I only have theoretical background knowledge on functional paradigm languages. I'm also open to learning more than one, but for now what could be the one that I could

- easily transition to
- understand recurring concepts surrounding these languages; and 
- learn first so learning the others in the future (even LISP) would be smoother?

Thanks! By the way, I found the stickies helpful, but I just hope to receive more suggestions specific to my situation.

---

### Post by fr4nko on 2009-07-08
Hi,

I believe that the some of the best skills to better contribute to the open source software development are python and C programming skills.

You should learn python because it is a powerful, very well designed and multiparadigm programming language. With python you can easily write complex programs that would be painful to write with some other programming language like C or C++. Most of the time you will find that programming in python is a pleasure.

Being multiparadigm python allows you to write code in a functional fashion and this often results in much more elegant and compact code. You have also the powerful concept of generators that is absent in most other programming languages. Generators are in many ways similar to coroutines and allows you to write, in some cases, a very elegant code but often you have to change the way you think since most programmers are not used to think in terms of coroutines.

For the other side I believe that to have a good skill in C is very important because some tasks need to be coded in C because python would be too much slow. Also many FOOS are using C as main programming language.

Talking about improving you knowledges I strongly advise you to learn ocaml. It is a powerful, high-level, functional programming language of the ML families. It does have a strong typing systems and the code it produce is as fast as C because, differently from python, if can compile to highly optimised machine code. Personally I don't like the object orientation in ocaml and I advise you to never use it, ocaml is a wonderful programming language without object orientation.

Probably you could also be interested in learning LISP, you know the acronym means Lot of Insipid Stupid Parenthesis :-)
in this case I cannot say a lot because I need to learn it myself :-)

Also, in my personal point of view there is no interest in Java. The code you write in this language is ugly and the programs that you obtains are always bloated but this is just my personal feeling.

I hope that helps,
Francesco

---

### Post by prvteprts on 2009-07-11
Thanks for the reply. I have borrowed books for Python and Ruby, and "The MINIX book" from the library. I'm trying to learn Python first and the syntax seems very easy to grasp. I'll try Ruby after around 2 weeks. The MINIX book I borrowed so I could learn how C is used as a systems language and also have a better understanding of the internals of an operating system. I haven't tried looking for resources for Ocami yet, but eventually I'll do.

---

### Post by fr4nko on 2009-07-11
That seems to be a nice program to improve you programming knowledges. Just one little remark, be aware that the MINIX book can be a little bit out to date, even the C language has evolved since the epoch the book was written ! :-)

Francesco

---

### Post by prvteprts on 2009-07-11
Well, the MINIX book is already in its third revision which is exactly what I borrowed. This also means that MINIX itself is in its third incarnation; and the authors have stated that MINIX 3 is built from scratch as opposed to an update to MINIX 2. By out-of-date, I hope you were referring to the 1st edition and not the 3rd edition because its publishing year is 2006. Or else... :shock:

---

### Post by fr4nko on 2009-07-11
> **prvteprts said:**
> Well, the MINIX book is already in its third revision which is exactly what I borrowed. This also means that MINIX itself is in its third incarnation; and the authors have stated that MINIX 3 is built from scratch as opposed to an update to MINIX 2. By out-of-date, I hope you were referring to the 1st edition and not the 3rd edition because its publishing year is 2006. Or else... :shock:

well... actually... I was thinking to the first book... to be honest I was not aware that MINIX was still alive... :-\"

probably it is a good reading, never mind!

Francesco

---

### Post by jimi_hendrix on 2009-07-11
lisp, it does it all (common lisp that is)

---

### Post by nvteighen on 2009-07-11
Seriously, Python + Ruby + C is a good decision... maybe Ruby is too similar to Python and you may change it for some kind of Lisp. jimi_hendrix suggested Common Lisp, though I would recommend Scheme before as an introduction to Lisp, although it's less practical that Common Lisp... but it's simpler to grasp. After having learned Scheme, Common Lisp will be very easy to deal with.

Or you can check Forth too... but be prepared for a hard-to-knock language. I myself haven't achieved anything with it... but I still try! :p

---

### Post by prvteprts on 2009-07-12
Whoa, it seems Lisp is pretty tough to deal with. How can you describe the differences between the various Lisp dialects? Do they differ mostly in syntax?

---

### Post by nvteighen on 2009-07-12
> **prvteprts said:**
> Whoa, it seems Lisp is pretty tough to deal with. How can you describe the differences between the various Lisp dialects? Do they differ mostly in syntax?

The different Lisp dialects differ in philosophy. The syntax is pretty much the same in all of them. What differs are the basic constructs available, preference towards recursion or iteration, trying to be simple or trying to be complete (though complex)... But there's a base Lisp philosophy common to all dialects, so learning one immediately opens you the doors to learn any other one.

That's why I think Scheme is better to introduce oneself into Lisp, because it's one of the "Keep it simple" Lisps.

---

### Post by prvteprts on 2009-08-17
I am currently reading "Simply Scheme" and I feel that I am grasping things pretty quickly. As you guys have suggested, it seems that indeed Scheme is a good introduction to Lisp.

nvteighen: From browsing the different literature on functional programming, I can now understand your avatar image somewhat :D

---

