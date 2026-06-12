---
title: "Newb Question, Python:How to await input while counting down with timert"
date: 2012-05-22
forum: Programming Talk
---

### Post by LearnAlways on 2012-05-22
edit: There is a typo in the title. The last word should be "timer" not "timert"


I know very little about programming. I've completed a few python tutorials several years ago, but I never stepped-up my knowledge. So I'm still a newb (actually I'm worse than a newb, but I know of no such term to designate that status). Frankly I have no aptitude for this, but I'm trying because programming knowledge is worthy of pursuit.

My current project, which is still in the conceptual stage, is a very simple game that will present the user with various scenarios and about 4 possible decisions per scenario (depending on the scenario). To add some excitement, I want there to be a countdown that will end the game if the user runs out of time without making a valid decision. 

There are two things that I need to know in order for me to move forward and implement the above:

1. I need to know the function (and, if applicable, the library I'll need to import in order to use it), that can cause a 1-second delay. I figure that I would use it in a loop to put a "halt" in the countdown. Of course it won't be exactly 1-second between numbers because of the execution time, but it's close enough for me.

2. I need to know how to allow this countdown to go forward, while, at the same time having the program "listen" for the user's selection. I have no idea how to accomplish this. I know only of raw_input, and that brings the execution sequence to a screeching halt so it can await the user's input.

Any suggestions?

Thanks in advance.

---

### Post by roelforg on 2012-05-22
I don't know python (i know 6+ other major languages though, excluding brainfuck and other esoteric/shady/vague languages).
But i'd say: MULTITHREADING

---

### Post by LearnAlways on 2012-05-23
Thank you for the suggestion. But I was hoping there was a simpler way to accomplish this than multithreading. I thought multithreading was a fairly new technology, and I know that simultaneously counting down while simultaneously awaiting user input (or at least appearing to simultaneously do both) has been possible for decades (e.g. I remember playing super mario bros. way back in the 80s. That timer kept counting down while I was pushing buttons on the controller, trying to get through the level. I died a lot :) )

If I try multithreading I'm afraid I'd be trying to "run" before I know how to properly "walk". Also, from what little I know of programming aesthetics, I think I'm supposed to seek out the most simple solution before trying something more complicated or advanced. Or maybe I'm supposed to use the best tool at my disposal? 

Is there any other approach that you or anyone else can recommend?

---

### Post by roelforg on 2012-05-23
> **LearnAlways said:**
> Thank you for the suggestion. But I was hoping there was a simpler way to accomplish this than multithreading. I thought multithreading was a fairly new technology, and I know that simultaneously counting down while simultaneously awaiting user input (or at least appearing to simultaneously do both) has been possible for decades (e.g. I remember playing super mario bros. way back in the 80s. That timer kept counting down while I was pushing buttons on the controller, trying to get through the level. I died a lot :) )

If I try multithreading I'm afraid I'd be trying to "run" before I know how to properly "walk". Also, from what little I know of programming aesthetics, I think I'm supposed to seek out the most simple solution before trying something more complicated or advanced. Or maybe I'm supposed to use the best tool at my disposal? 

Is there any other approach that you or anyone else can recommend?

Well, multithreading is what linux was designed to do.
I've got a pc from 1992 in my room (the thing still works) and it has a i386SX (yes, the real 80368 series) that can do multithreading (if a processor has task-switching, it can do multithreading and even that 20yrs old thing has it).

Just lookup a good tut on it, they're all over the web.

---

### Post by LearnAlways on 2012-05-23
I didn't know that multithreading went back that far. And I didn't know linux was designed for it. That's pretty cool. 

I still don't know if multithreading is the right choice for me, as a novice programmer. But if it's the only way to accomplish this, then I'll have to use it. I'll wait and see what other people suggest, and do some additional research. At this point though, it does seem as if your multithreading suggestion is my best bet. Thanks again.

---

### Post by Tony Flury on 2012-05-24
Anothe way of doing this would be a main loop - which says :

```

sleep for 0.5 seconds 
Look for input
revise countdown
Loop until time is up or input given

```

If you want a more responsive program reduce the amount that you sleep.

Multi threading is the preffered way to go though.

---

### Post by slavik on 2012-05-24
except threads in CPython are not truly concurrent.

---

