---
title: "Please share your programming technic with us"
date: 2010-08-13
forum: Programming Talk
---

### Post by hoboy on 2010-08-13
Hello guys 
This is a great forum.I have been impressed by the answers I have got to my questions.
I am not learning syntax anymore, but looking at the shoulders of the Maestros to learn, believe me they are many of them in this forum.
Questions.
when you have a complexed requirements from client, what is your approach/ technique of divided and conquer ? ooooook how do you prepare yourself mentally ? I mean what is your best secret for problem solving ? do you find class,methods ?, data domains ? 
How did you master of having the overview, but not loosing the small details ?
mmmmmmm we always hear practice, I am interested in the mental work, before writing the code.
Thanks

---

### Post by agnes on 2010-08-13
[http://en.wikipedia.org/wiki/Unified_Modeling_Language]("http://en.wikipedia.org/wiki/Unified_Modeling_Language") lets you model the program beforehand, with various sorts of paradigms.
There are lots of tools for modeling with UML.
I don't make large programs myself so I hardly use it, but I had to learn/use it in a Java course; it appears to be widely used.

---

### Post by hoboy on 2010-08-14
> **agnes said:**
> [http://en.wikipedia.org/wiki/unified_modeling_language]("http://en.wikipedia.org/wiki/unified_modeling_language") lets you model the program beforehand, with various sorts of paradigms.
There are lots of tools for modeling with uml.
I don't make large programs myself so i hardly use it, but i had to learn/use it in a java course; it appears to be widely used.

bump

---

### Post by simeon87 on 2010-08-14
1. Write down the problem.
2. Think really hard.
3. Write down the code.

---

### Post by howlingmadhowie on 2010-08-14
> **simeon87 said:**
> 1. Write down the problem.
2. Think really hard.
3. Write down the code.

ah, the feynman problem solving algorithm :)

---

### Post by nvteighen on 2010-08-14
Abstraction!

Ok, seriously: people are different and specially when it comes to rational thinking. What I mean is that what's the most natural way to solve a problem for one certain programmer may not be the one for another programmer.

For me (consider that I'm a hobbyist), it's an "abstraction escalation" approach: I start writing something... then I notice I can make it more generic and I rewrite it... and then I see that well, I can make it even more generic and rewrite it again. Usually, this takes me two iterations, but I've got to do this four times (if you carefully think about it, it's actually because the initial code was crap).

:P

---

### Post by GregBrannon on 2010-08-14
Since programming is part art, this question might be partially equivalent to asking an artist where their inspiration comes from.  For example, popular song writers are often asked, "How do/did you write music?"  Have you ever heard an answer to that question that someone else could use to write a song?  I haven't.

Communicating to others how our brains work, how we *think* to organize what we know into a possible solution to something we don't know, is a difficult thing to do, maybe impossible for some.

---

### Post by Puzzled Guy on 2010-08-14
Break the task down into steps
write code for each step, no matter how crude
debug it
rewrite the crude code into a professional program
debug it
leave it on your HD to collect dust

---

### Post by hoboy on 2010-08-14
Thanks guys.

---

### Post by trent.josephsen on 2010-08-14
> **Puzzled Guy said:**
> Break the task down into steps
write code for each step, no matter how crude
debug it
rewrite the crude code into a professional program
debug it
leave it on your HD to collect dust

Usually for me it's more like

Break the task down into steps
write code for each step, no matter how crude
debug it partially
leave it on your HD to collect dust

;)

---

### Post by bcz on 2010-08-15
Theory says

Design it
Dot the i's and t's
Code it
Test it

The above is almost guaranteed to fail, but the cost is great.  Very suitable for government work

This works:

1. Get a basic design and timeframe
2. Code a bit of it and debug it
3. Review the basic design/timeframe in light of what was learnt in stage 2
4. Decide what to do next
5. Go to step2

This approach gets results almost immediately and costs are controlled

---

### Post by hoboy on 2010-08-15
> **bcz said:**
> Theory says

Design it
Dot the i's and t's
Code it
Test it

The above is almost guaranteed to fail, but the cost is great.  Very suitable for government work

This works:

1. Get a basic design and timeframe
2. Code a bit of it and debug it
3. Review the basic design/timeframe in light of what was learnt in stage 2
4. Decide what to do next
5. Go to step2

This approach gets results almost immediately and costs are controlled

Good point oif view

---

### Post by SledgeHammer_999 on 2010-08-15
I do some of the things others mentioned here, but:

> **nvteighen said:**
> 
For me (consider that I'm a hobbyist), it's an "abstraction escalation" approach: I start writing something... then I notice I can make it more generic and I rewrite it... and then I see that well, I can make it even more generic and rewrite it again. Usually, this takes me two iterations, but I've got to do this four times (if you carefully think about it, it's actually because the initial code was crap).
:P

OMG, get out of my head :p

---

### Post by shadylookin on 2010-08-15
Get very specific requirements from client/boss and develop use cases

analyze these requirements determine feasibility and what frameworks to use.

design the software

implement the design

test the implementation


It depends on the project just how much you put into each area

---

### Post by StephenF on 2010-08-16
Think about the data you need at a particular juncture.
Think about the steps that would get you that data as informed by the language in use. Try to do so without adding to the dependency list.

The above can be done away from the computer.

Sleep on it.
If it still seems like a good idea then write it.

At each stage test. Think what the corner and edge cases would be.

Move on to the next phase.

At each stage you'll need data from the previous one so add code that can be tested in place or you'll be spending as much effort on unit tests for code that may later be dropped.

Edit: I should clarify I'm working on a GUI project at the moment which has a lot of event driven and callback stuff.

---

### Post by Barrucadu on 2010-08-16
I prefer the top-down approach - I'll first create the 'main' procedure which works by calling various functions. Then I'll write the functions it calls. Then I'll write the functions *they* call, and so on.

---

### Post by velle frak on 2010-08-16
I used to spent much time on writing the specifications, then do the analysis to find the solutions, together with the UML diagrams, rethink that over for a while and only then start coding. I usually created a test scenario using the specifications from step 1.

I think most people start writing code very soon in the proces of developing software. 

I always write my code in the second half of the development proces.

---

### Post by kalaharix on 2010-08-16
Interesting thread!

'Get very specific requirements from client/boss....'. You must be joking. :)

The dire state of Public Sector IT projects here in the UK suggests that bcz's ideas are good. I also like the top-down approach of Barrucadu.

The problem I find is that, having programmed a 'function', I then find I need a more generalised version somewhere else in the main 'procedure' (Barrucudu's terms). So I tend to spend a lot of time broadening the scope of subsidiary modules. It can be a bit of a pain.

---

### Post by hoboy on 2010-08-16
> **Barrucadu said:**
> I prefer the top-down approach - I'll first create the 'main' procedure which works by calling various functions. Then I'll write the functions it calls. Then I'll write the functions *they* call, and so on.

If you work on a large project it can be difficult to see what is the main procedure

---

### Post by hoboy on 2010-08-16
Ok you are doing test driving development ?

---

### Post by hoboy on 2010-08-16
mmmmmmmmmmnnnnnn you have a good point

---

### Post by shadylookin on 2010-08-16
> **kalaharix said:**
> Interesting thread!

'Get very specific requirements from client/boss....'. You must be joking. :)


True it's almost an impossibility for management types to commit to specifics. However it's in your best interest to get as specific as you can especially for the features they want that make your software unique to all the other software out there. Then fill in the blanks with your own specifications.

---

### Post by nvteighen on 2010-08-17
> **SledgeHammer_999 said:**
> 
OMG, get out of my head :p

Lol... :D

---

### Post by velle frak on 2010-08-17
> **kalaharix said:**
> Interesting thread!

'Get very specific requirements from client/boss....'. You must be joking. :)



:lolflag: Indeed, you're right. Most of the time, that particular step is the weak link. Sadly, most of the time it's the analyst/programmer who gets the blame.

---

