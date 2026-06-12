---
title: "Need some programming language insight."
date: 2008-08-13
forum: Programming Talk
---

### Post by fatmarik on 2008-08-13
So this year I just finished a year of AP Computer Science at my high school. The class taught us Java. And now my question is whether I should continue with Java or learn a different language like C or C++. I would like to major in Computer Science in college, so which will help me more along my path. Also what is the difference between C and C++, and will I be able to run C++ GUI applications on Ubuntu? Or should I choose a different language like Perl etc..

P.S - The reason for me not leaning towards Java is because I found it a little too simple for me, and that it runs slower than C++, and I want to be able to code GUI applications that aren't too resource intensive.

P.P.S :) - Thanks for taking the time and replying to this.

---

### Post by kknd on 2008-08-13
Hi,

Taking GNOME applications for example, most of them are made with C, Python and C++ (more or less in ths order). They all use GTK for the interface.

Check the other posts (theres a fixed topic on the top of the main programming forum) for more info!

---

### Post by fatmarik on 2008-08-13
Thanks.:)

---

### Post by KWM987 on 2008-08-13
The quick answer is learn as many as you can.  

I also took all the computer programming/science classes my highschool had to offer, they changed the language 3 times before settling in with Java as the new standard they teach-- started with VB, then 2 years of C++, and finally Java when I got to AP, but by that time the lower classes were also on it.  

Much of this is personal preference as to what to learn, but I can say form experience, that C (your linux kernel is written in C), C++, Python (C++ and Python are popular for programs in Gnome), Perl, Python, Ajax, PHP, MySQL, HTML, XML, JavaScript and others (those I listed I use the most, because I can remember them all off the top of my head) are what I have found I need most in my work, particularly for those trying to maintain an Open Source platform-- though this changes depending on client, business, and employer, since you may find yourself forced to use the tools that get provided to you.  I did an internship for 3 years while in highschool with my town's IT department and for a good portion of the time was forced to use proprietary programs and languages like Cold Fusion, ASP, .NET, etc.  and only after I showed them the versatility of the other languages first hand did they start to make a move to these other options. 

One word of advice is to familiarize yourself with building web based applications, this is a trend alot of places are starting to use because of flexibility and versatility, and one thing I don't think the schools are with yet.

I have not really found a good use for the Java classes I was put through which is somewhat sad to say, it does not offer as much as the other alternatives do, aside from being easy to transition across platforms.


I hope that's helpful, it's a somewhat difficult question to answer directly, I would further you to read about the different languages a bit on wikipedia and familiarize yourself to how they are used and what they are about before you start heavily investing time into learning just one.  More often than not, you'll gain better experience building programs that use more than one, with different elements geared towards different strengths.

---

### Post by pmasiar on 2008-08-14
> **fatmarik said:**
> my question is whether I should continue with Java or learn a different language like C or C++. I would like to major in Computer Science in college,

If you want to go for CompSci, you need to expand your brain: learn more different languages. 

- Dynamically typed language like Python (my choice), Ruby or even Perl (which is becoming obsolete)
- low-level language like C and possibly ASM for some CPU
- Functional language, like Lisp, 
- logical language like Prolog
- Later in college you should try even stranger languages, like Forth, Haskel, etc.

C++, C# and friends are so close to Java that you will not learn much new. You need to learn different approaches to programming, to see which part of complexity in your solution is related inherently to the problem and which part is just specifics of the language used to solve it.

Language is a tool: you need to get feel of couple of them to understand which one is best fit for the job. And you may want to try solving problems in different areas: programming web-based frontend for a database is very different to a desktop image viever.

---

### Post by CptPicard on 2008-08-14
Search the forums, we have had loads of threads on this matter, even sometimes with something interesting having been said.

> **fatmarik said:**
> And now my question is whether I should continue with Java or learn a different language like C or C++.

Nothing wrong in continuing with Java, it is an ok language among languages of its kind, C++ in particular being a similar language. Then again this question is a bit moot if you're going to study computer science... you want to be competent enough to be able to familiarize yourself with a lot of languages, and preferably lots of *different* kinds of languages.

Your next step should probably be Python or C, or both. The best part about the duo is that you can write your speed-critical parts in C and use them from Python, which gives you speed of development plus nice high-level constructs.

> Also what is the difference between C and C++

C++ is an attempt to bring object-orientedness to C, and you will find there are varying opinions as to how successfully it did it. They are similar yet rather different in the way you code in them (in particular if you do C++ right, which is a black art).

> and will I be able to run C++ GUI applications on Ubuntu?

Yes, if you specifically code against Linux libraries. Qt+KDE are nice, so if you're so inclined, go for it.

> Or should I choose a different language like Perl etc..

You want Python for your higher-level "scripting" needs... it binds nicely to GUI libs as well.

> 
P.S - The reason for me not leaning towards Java is because I found it a little too simple for me

I would like to hear you elaborate on this. In what respects do you feel Java is too "simple", and what in your experience has made you believe so?

IMO language complexity is not a measure of its merit or "power". C++ is an extremely complex language but I still steer clear from it. C in comparison is a very simple language, but I mostly steer clear from it as well because I have to build everything from scratch. Lisps are very simple languages syntactically, but have lots of expressive power in competent hands.

I have a feeling you are not yet experienced enough to *really* be missing features Java doesn't have... ;) In particular C++ and Java are both statically typed object-oriented languages so I consider them very similar, but with the distinction that Java manages to be economical while C++ is a bloated monster of a language that forces you to do a lot of work just to manage the language itself.

> and that it runs slower than C++

I write CPU-intensive parallelized number crunchers in Java and it's fast enough. I cannot justify the step down to C from Java because of the added complexity of developing with threads etc.

Anyway, I am going to again advice you against the typical beginner drive to move towards the "low level" instead of the "high level". The fun stuff is in the high level languages unless you want to hack the kernel or hardware. If you do want low level, use C, it's at least a fairly minimal language.

For your future education in computer science, do check out some Lisp, such as Scheme.

---

### Post by Reiger on 2008-08-14
Java is a fine language. Indeed adverts about most high-level (Uni) programming jobs I see from time to time often mention they're looking for "Functional Designers" and "Java/J2EE developers". The former alludes to working with Haskell; the latter needs no explanation...

And there's good reason for that: Java may not neccesarily be as fast as C or C++; Java does develop & maintain a LOT faster what with being portable across most major platforms of today... Including but not limited to the rapidly expanding area of 'mobile devices'.

---

### Post by lordhaworth on 2008-08-14
> KWM987 Re: Need some programming language insight.

--------------------------------------------------------------------------------
The quick answer is learn as many as you can. 
 

Its important that you actually learn a language though, obviously you will be familiar with some aspects of programming so can probably "have a go" at most languages, but to be truly good at programming you should know at least one language in depth - something which can take years. Certainly look around at what there is to offer its certainly useful to know whats available!

---

