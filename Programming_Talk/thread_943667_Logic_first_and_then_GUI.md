---
title: "Logic first and then GUI?"
date: 2008-10-10
forum: Programming Talk
---

### Post by nuclearj on 2008-10-10
When developing a program is it best to develop the logic and code and then the GUI, or is it better to develop both simultaneously?  I am using Python by the way.

---

### Post by stevescripts on 2008-10-10
From my personal experiences, it tends to vary.

There are times when the GUI is clearer in my mind, and I do it first...

There are times when the logic and code is clearer, then it tends to get done first ...

In *most* cases however, the code and GUI tend to grow more or less together.

Just my personal $.02 - others probably have other experiences...

BTW, the language/toolkit being used doesn't have much effect in this area.

Caveat - Higher level languages, such as python, will allow the programmer to develop his applications quicker, usually ... ;)

Steve

---

### Post by Tomosaur on 2008-10-10
Depends what the program is supposed to do really.

Generally speaking if you think of the design as MVC (Model - View - Controller), then you can pretty much do everything at once. GUI code is generally capable of being built whenever - only the actual event listeners and such may depend on therest of the program functioning correctly.

---

### Post by themusicwave on 2008-10-10
I think the biggest reason programs fail or end up ugly in the end is that not enough upfront thinking happened before programming.

When I set out to build a program, I always start out with either a notebook and pencil or a word processor.  The very first thing I do is try to write down all the things I want it to do.  I sit there and I wrestle over it until I am fairly sure I have it all down.

Then I think about what structure the program should take to accomplish these things.  If needed, I lay out my various modules and what they need to do.  I lay out how I think they should interact on a high level.  

After this, I focus on each specific module.  What pieces are inside it, how do they interact.  This usually involves making some UML diagrams.  Once I flush all that out I look over the whole thing and try to see any possible problems or mistakes.

Once I have flushed out my idea.  Then I start to write the code.  

Now, my design will always change.  There will always be a mistake or something I didn't think of at first or other issues.  That's ok though, the point of the design process isn't to get it 100% right in the design phase.  It's to force myself to think about the program indepth before I even begin to code.

Even if the design gets totally scrapped when I try to implement it(which almost never happens), I still gain a lot for the design process.

I think a major reason I do this is that I was forced to in all my Software Engineering classes.  It stuck with me...

---

### Post by era86 on 2008-10-10
> **themusicwave said:**
> I think the biggest reason programs fail or end up ugly in the end is that not enough upfront thinking happened before programming.

When I set out to build a program, I always start out with either a notebook and pencil or a word processor.  The very first thing I do is try to write down all the things I want it to do.  I sit there and I wrestle over it until I am fairly sure I have it all down.

Then I think about what structure the program should take to accomplish these things.  If needed, I lay out my various modules and what they need to do.  I lay out how I think they should interact on a high level.  

After this, I focus on each specific module.  What pieces are inside it, how do they interact.  This usually involves making some UML diagrams.  Once I flush all that out I look over the whole thing and try to see any possible problems or mistakes.

Once I have flushed out my idea.  Then I start to write the code.  

Now, my design will always change.  There will always be a mistake or something I didn't think of at first or other issues.  That's ok though, the point of the design process isn't to get it 100% right in the design phase.  It's to force myself to think about the program indepth before I even begin to code.

Even if the design gets totally scrapped when I try to implement it(which almost never happens), I still gain a lot for the design process.

I think a major reason I do this is that I was forced to in all my Software Engineering classes.  It stuck with me...

+1

The majority of your time when developing software IS NOT implementation.  It is DESIGN.  Those who can code effectively and elegantly make really great "hackers" (hate using the term), but if they lack design knowledge, the software will always be flawed.  In testing, most errors observed are from design flaws.

Sit and think about the logic of your program with the knowledge that you will implement the GUI later.  Make sure your design models exactly what you want.  Then, code.

Goodluck!

---

### Post by lisati on 2008-10-10
Both logic and the user-interface (graphical or not) are important. 

The UI is what the person sees, and is usually the main way the person interacts with the software. However, a nice elegant appearance means little if the program doesn't deliver the results.

---

### Post by nuclearj on 2008-10-11
WOW!  Thanks for all the great input.  I actually did write out some notes the other week.  I guess I'm on the right track.  I'll find them and keep working on them.  Any good books on software design and implementation?

Bigups to musicwave and era86!

---

### Post by era86 on 2008-10-11
> **nuclearj said:**
> WOW!  Thanks for all the great input.  I actually did write out some notes the other week.  I guess I'm on the right track.  I'll find them and keep working on them.  Any good books on software design and implementation?

Bigups to musicwave and era86!

I would check out the wikipedia first: [http://en.wikipedia.org/wiki/Software_development_process](http://en.wikipedia.org/wiki/Software_development_process)

This gives some good info on basic/general software development processes.  When you're ready to learn different methods such as Agile Dev Procs and Extreme Programming, you can look into this book:

Software Engineering: A Practitioners Approach by Roger Pressman

This is a textbook that some colleges use in their classes.  Have a look.  Goodluck!

---

### Post by irrdev on 2008-10-11
Depends on the project. If your GUI interface is going to be a frontend to a server, for example, then building the server first is obviously the best approach. However, if you are creating a window-based application, creating the GUI first is usually necessary, as you need to place your logic code inside event handlers/messaging loops. Generally speaking, therefore, GUI first is the easiest and most practical route, but this isn't always the case.

---

### Post by nvteighen on 2008-10-11
What I do is usually bottom-up programming, from the lowest to the highest level and piling one layer of abstraction upon the latest (either in "tower" or "pyramid"). That way, I code everything as a library for the next higher level and when I get to the "surface" (the user-interface), I have a whole library API to which, if everything has been coded correctly, I should be able to plug in any interface I want

That way, I usually code interfaces at last... well, usually I don't code interfaces at all, as I like to write libraries :)

---

### Post by mike_g on 2008-10-11
> What I do is usually bottom-up programming, from the lowest to the highest level and piling one layer of abstraction upon the latest (either in "tower" or "pyramid"). That way, I code everything as a library for the next higher level and when I get to the "surface" (the user-interface), I have a whole library API to which, if everything has been coded correctly, I should be able to plug in any interface I want

That way, I usually code interfaces at last... well, usually I don't code interfaces at all, as I like to write libraries 
From my experience that works well, but only in certain cases. If you can design an app to run from the command line then you can pretty much chuck any GUI on top of it with total decoupling.

On the other hand some applications are pretty much bound to the GUI and attempting to seperate them only results in: Redundant data being passed around and updated everywhere, more code and more overhead, yet if you wanted to program it to work with another GUI it would be so much hassle that its simply not worth it.

---

### Post by pmasiar on 2008-10-11
It depends on what you code, of course.

Design before coding is obvious: the sooner you start hacking code, the later you finish :-)

User-facing systems (applications) are better coded top-down. Infrastructure kind of systems (operating system, game library, database system) are better done bottom-up.

There are many ways to design a user-facing software system. For big interactive systems which have multiple kinds of users (so need to be more flexible) the [http://en.wikipedia.org/wiki/Use_case](http://en.wikipedia.org/wiki/Use_case) is common way to gather relevant info: because as you write up use case, you have better mental picture of what user would expect from the system.

Next step is [http://en.wikipedia.org/wiki/Paper_prototyping](http://en.wikipedia.org/wiki/Paper_prototyping) of user interface, and using MVC pattern for UI. Of course this assumes that you are confident you can solve any low-level problems. So if you know about some show-stoppers, you want to solve those first (but not all low-level coding), because you have to have those right before investing time in big project.

So my order (when dealing with big project, multiples of dozens or man-monts) would be:
- showstoppers
- written requirements and use cases
- paper prototyoping
- coding using MVC, which allow to separate view (GUI) and model (data representation).

For a really big project, add simplified prototype. As Brooks says: plan to throw one version away, because you will anyway.

Read [http://en.wikipedia.org/wiki/Mythical_man_month](http://en.wikipedia.org/wiki/Mythical_man_month) book - the only computer book which is as fresh and relevant after 33 years as if was when first printed in 1975.

---

### Post by GavinZac on 2008-10-12
With web development or other GUI-based user tools, I always try to lay things out first; Essentially, mapping out the functionality I have to achieve. I guess in some ways its my "todo list".

---

