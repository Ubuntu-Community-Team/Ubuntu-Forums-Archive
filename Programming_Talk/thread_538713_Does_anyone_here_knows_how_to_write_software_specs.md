---
title: "Does anyone here knows how to write software specs?"
date: 2007-08-30
forum: Programming Talk
---

### Post by sapo on 2007-08-30
Hi,

I know that it may sound weird and even bureaucratic but we are trying to start writing specifications for our softwares, but we have several doubts about how to start.

My boss says that the spec can be written as a Help File (wich none of our softwares have), so we would be killing 2 habbits with one stick, but I disagree with that.

I think that the specs need to be something like a scratch, and the help has to be based on the specs and the software itself, so when writing the help you can read the spec, use the software, and after that write a better help.

In my POV the help needs to be written after the software is running, and the specs need to come first.

But the problem is that our software (on wich is 10 years old) doesn't have any spec whatsoever.

So, if anyone here works somewhere that really writes specs, please enlighten us with your experience.

Also, there is a doubt about where to store the specs, my boss says it HAS to be on the subversion along with the source code, but I disagree with that too, I would prefer storing it on Google Docs (we use the google apps for everything) because I think that the testers and the support people doesn't have to have the source code. what do you guys think about that too?

---

### Post by Tomosaur on 2007-08-30
What do you mean by 'specs'?

In software engineering, the specification comes before even a line of code is written. You don't HAVE to have a specification, but for large projects it can help a lot.

Or do you mean specification such as 'this is what you need to run the software'?

---

### Post by nanotube on 2007-08-30
> **sapo said:**
> ... because I think that the **testes** and the support people doesn't have to have the source code. what do you guys think about that too?

i think the testes don't need to have the source code. but then again, they don't need the documentation either. :)

in seriousness, spec are for before you write software, so that you know what you need to implement. once the software is written, what are you going to do with specs? all you need is documentation. if you are planning on modifying/extending the software, then two sets of docs - one for end users, one for coders.

---

### Post by pmasiar on 2007-08-30
> **sapo said:**
> I know that it may sound weird and even bureaucratic but we are trying to start writing specifications for our softwares, but we have several doubts about how to start.

Only weird thing is, you should have specs 10 years ago :-)

Here are bunch og good links about specifications: 
[http://c2.com/cgi/wiki?search=specification](http://c2.com/cgi/wiki?search=specification) .
Check "Formal Specification" "Difference Between Specification And Implementation" "Requirements Specification" "Technical Specification" "The Unit Test Is The Specification" (these are original XP (axtreme programming)  gurus after all!) "What Isa Specification Anyway"

[http://c2.com/cgi/wiki?ManualAsSpecification](http://c2.com/cgi/wiki?ManualAsSpecification) was about what you wanted, but it was "fried" **February 2, 1998)** - you might be looking on the oldest surviving wiki page in all internets! :-)

> My boss says that the spec can be written as a Help File (wich none of our softwares have), so we would be killing 2 habbits with one stick, but I disagree with that.

Maybe it is killing 2 rabbits :-)

You are right, having specs as help file makes little if any sense.

> I think that the specs need to be something like a scratch, and the help has to be based on the specs and the software itself, so when writing the help you can read the spec, use the software, and after that write a better help.

Yup, that's the idea

> In my POV the help needs to be written after the software is running, and the specs need to come first.

How else you would know if program works up to specs? :-)

> Also, there is a doubt about where to store the specs, my boss says it HAS to be on the subversion along with the source code, 

That's good idea - you want to see history of changes. But can have change history in shared docs too...

Very good system covering all what software development group need is [TRAC](http://trac.edgewall.org/) which has subversion, code viewer (changes in color!), bug tracker, and wiki for specs. I use another wiki for projectname-help for help. It is very impressive, when user asks for help, go and enter explanation to the page while on phone, and ask user if tried to read help, because answer is there! :-) Wiki used for help like this is rather effective [http://en.wikipedia.org/wiki/Lart](http://en.wikipedia.org/wiki/Lart)

---

### Post by xtacocorex on 2007-08-30
Specifications should not be a help file; you'd easily see that if you've ever read one.  A help file tells the user how to use the program and it's features; a spec defines what the program needs to do and there are usually many levels of spec's that drive into more detailed requirements.
 
Spec's come before the start of any project and provide a guideline of what to design to, no more/no less.
 
Version control is very important for specs, it will allow you to baseline the document tree and will show you where changes are made.  Spec's are binding documents, so having a revision history can be helpful.  I don't think storing it in the same directory as the source is good, but keeping it under some form of version control is necessary.
 
(Does it not show that I deal with spec's in my day job?)

---

