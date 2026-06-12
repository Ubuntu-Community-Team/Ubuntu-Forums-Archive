---
title: "Looking for a nudge in the right direction regarding Java and Recursion"
date: 2009-01-11
forum: Programming Talk
---

### Post by stairwayoflight on 2009-01-11
Hello,

**I am looking for tips to make a recursive function yield an iterative process and use constant resources in Java.**

I wrote a mult-recursion program several times over, and each time it produced a stack overflow. I will describe it briefly in concept, but as I am not so much interested in getting it to work, I won't paste the actual code.

Assuming I want to recursively search through many possible solutions to find a "best" answer (eg. "backtrack" search I believe it is called), are there any "gotchas" to be aware of? I was thinking of a "stack" of choices of size 400, and a word list of arbitrary length (which would not change).

Thanks,
Stairwayoflight

For those interested:

In concept, the program keeps track of words that have been "chosen" as part of the solution. To add a word to the solution it is pushed onto the "stack" of choices; to backtrack it is "popped" and the state is incremented so the word is not tried in the same way.

At first I thought to avoid the overflow I simply had to avoid instantiating or changing the size of objects in (or as a result of) my recursive function, so I wrote that stuff out. Then someone told me passing primative types like int results in a *copy*, and so I took those out. I simulated the "stack" so I wouldn't have to have my ArrayList grow or shrink.

My program was intended to do an exhaustive search of all the possible crosswords which could be generated with a given word list. I had two ArrayList objects: one being the word list, the other being a simulated "stack" of choices.

---

### Post by andrewc6l on 2009-01-12
Java has a fixed stack size, specified by -Xss. It sounds like you want to develop a function that's tail-recursive, and thus won't take up additional stack space. My guess is the compiler you're using doesn't generate tail-recursive code by default. Other compilers (maybe the one in Eclipse or something like that?) might generate better code.

You can check the Java bytecodes using javap -private -c mypackage.MyClass to see what bytecode is being generated and if it's tail-recursive. If you really want to go insane, you can assemble the bytecode by hand using a tool like Harmony's VMTT ([http://svn.apache.org/repos/asf/harmony/enhanced/buildtest/trunk/tests/tools/vmtt/](http://svn.apache.org/repos/asf/harmony/enhanced/buildtest/trunk/tests/tools/vmtt/)).

---

### Post by CptPicard on 2009-01-12
> **andrewc6l said:**
> Java has a fixed stack size, specified by -Xss. It sounds like you want to develop a function that's tail-recursive, and thus won't take up additional stack space. My guess is the compiler you're using doesn't generate tail-recursive code by default. Other compilers (maybe the one in Eclipse or something like that?) might generate better code.

You're on the right track, but a compiler  can't just "generate" tail-recursive  code for you -- you need to explicitly write things in tail-recursive manner (when you can), and then the compiler, if it is capable of it, will compile this tail-recursive call into essentially what is a loop.

However, Java compilers don't do tail call optimization even if you did write a tail-recursion, unfortunately, as far as I know.

What you need to do here is to explicitly convert your recursion into a loop. First, I would suggest thinking of in terms of an explicit stack -- take a stack data structure and manipulate frames on top of the stack in a loop instead of using the implicit call stack. Now, try figuring out a way how to get rid of the stack... how to write the loop so that you no longer need the frames under the top of the stack, so that you can just forget about the stack completely?

---

### Post by stairwayoflight on 2009-01-15
Hmm,

Well I could rewrite it in a while loop for sure. But given the following, I don't know if my program didn't work because of a logic error (ie. I was creating objects when I thought I wasn't) or because the whole idea was wrong.

Lets say I have some object encapsulating the state in which a choice was made. It contains maybe 4 primitive types. Then I create a stack for these objects, which will have a maximum of 400 choice objects at any given time. Again suppose I added and removed objects to the stack not in a recursive call, but in a while loop which would run once. Assuming I don't have logic errors, is it reasonable to say that the garbage collector should have no problem freeing memory so that I will not get a stack overflow?

(I am having a really hard time visualizing a crossword-generating process that doesn't use a stack!)

**EDIT!** I have done a little experiment that doesn't solve the problem (ie. generate crosswords) but I think is an improved model for a process. I found that pushing/popping to/from a stack in a loop to work quite well. No matter how many times I repeated the process, java never exceeded 10% of my memory (according to top).

I was surprised to learn Java doesn't optimize recursive functions. I thought this would be trivial if the function's state were summed up in the variables passed to the next iteration. So problem solved, it seems.

Thanks for the help everyone.

---

