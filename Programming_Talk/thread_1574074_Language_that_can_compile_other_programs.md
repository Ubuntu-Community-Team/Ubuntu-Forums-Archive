---
title: "Language that can compile other programs"
date: 2010-09-13
forum: Programming Talk
---

### Post by BandeAli on 2010-09-13
Hey, I was recently intrigued by the concept of an 'evolving' program. For that I was going to write a program that writes another program and compiles it and checks the result and it keeps doing that till it writes the 'correct' program. 

I have a good understand of basic programming concepts and I have some experience in C but I guess that is no where close to being enough to answer my question. 

So my main question is what language can write a basic text file, compile the file into a program, and then call the program? I did some Google searching but I didn't know what to search for. 

Thanks for your help.

---

### Post by Bachstelze on 2010-09-13
I don't think it makes a lot of sense to talk of a "language" that can "compile a file into a program". A source file is compiled by a compiler, not a language. A compiler is a program just like any other, and can be written in any language.

---

### Post by eeperson on 2010-09-13
I would suggest using a [homoiconic]("http://en.wikipedia.org/wiki/Homoiconicity") language such as Lisp. This will make it much easier to write a program that writes a program.  Also you can use an [eval]("http://en.wikipedia.org/wiki/Eval") function to run your new program on the fly rather than having to write it out to a file and then compile it.

Homoiconic languages are(or at least were) popular in AI research for this very reason.  See also [meta-circular evaluation]("http://en.wikipedia.org/wiki/Meta-circular_evaluator")

---

### Post by BandeAli on 2010-09-13
thanks eeperson!

I was looking for a reason to start messing around with perl and now I guess I found it.

---

### Post by GenBattle on 2010-09-13
I think what's you're referring to is [Genetic Algorithms]("http://en.wikipedia.org/wiki/Genetic_algorithm") and Evolutionary Agorithms; using a program to cultivate an optimal solution to a problem from several generations of sub-optimal solutions.

The main thing to understand is that this sort of process is not restricted to certain languages. Most languages are capable of some form of self-compilation (for C programs you could call GCC on the command line after writing a text file of code, and in python you can use "eval()" to run strings as code). The important thing in this sort of programming is thinking about how you are going to cultivate the solutions from code; what areas of the algorithms will be variable? which will be set? how will you judge the optimal result?

I would recommend finding a good book on the subject, or maybe something on the web which explains it. Possibly even talk to your lecturer.

---

### Post by lisati on 2010-09-13
The [halting problem]("http://en.wikipedia.org/wiki/Halting_problem") might be an interesting one to resolve. *shudder*

---

### Post by Wybiral on 2010-09-13
> **lisati said:**
> The [halting problem]("http://en.wikipedia.org/wiki/Halting_problem") might be an interesting one to resolve. *shudder*

Indeed :)

But I've implementing algorithms like this (evolving Lisp and Forth code to produce working functions) and one solution is to cap any function execution to a certain amount of time. If the function doesn't evaluate in X number of seconds, kill it and consider it unfit for reproduction.

OP: I'd just forgo the entire writing to text file and compiling part. The amount of time and resource usage, especially with a large enough population, would be way unreasonable. For small enough bits of code (writing individual functions or algorithms) I'd use an interpreter that can be embedded in your source language. Or even implementing a domain-specific language that your program executed.

I've done this with both Forth (very simple, stack-based language that's easy to interpret/compile and works well as "genetic" code) and Lisp (also easy to interpret/compile and also does well as "genetic" code, although your generation/mutation/crossover functions get a bit trickier with trees).

---

### Post by amanjsingh on 2010-09-14
I loved your answer.

---

### Post by amanjsingh on 2010-09-14
Can programs understand programs? Or rather can a program understand itself? I think former can be done but not latter.

---

### Post by [h2o] on 2010-09-14
That would depend on how you define "understand".

---

### Post by Ferrat on 2010-09-14
Understand in the sence that it might be able to guess the purpose of the program, could be done I guess but it would probably be extremly difficult and it would need a massive referense archive and be able to memories all the programs that it has created as well as get a discription of them. Still it wouldn't be able to guess at new work that it doesn't have any reference to, for ex. if you've used it to create calculators and then try a 3D rendering engine it wont be able to guess what it is since it's never seen one before. 

Understand in the way of "Who am I? What am I doing here? What is my purpose?" don't get your hopes up :P We can't even always answer those ^^

---

### Post by CptPicard on 2010-09-14
Just look at the [Universal Turing Machine]("http://en.wikipedia.org/wiki/Universal_Turing_machine") to get an idea what this "programs understanding programs" deals with. The halting problem is a very fundamental problem in this regard; this is why there are no automated debuggers, and probably no automated programming either.

What this says about the possibilities of for example artificial intelligence is interesting; if brains and computers are equivalent, it is a bit strange that a computer will end up stuck in an endless loop while trying to simulate it, while we can just "see" it is an endless loop... then again it is possible that the Gödel sentences of the human mind simply are not the same ones as those of computers.

---

### Post by ian dobson on 2010-09-14
Hi,

Maybe do a google search for "genetic programming", I think there's an interesting python project out there.

Regards
Ian Dobson

---

### Post by worksofcraft on 2010-09-14
One successful approach to making software that learns and adapts from experience is to simulate Neural Networks.

This is based on our understanding of biological systems such as the human brain. In these networks the "neurons" are all organised in layers. Each layer connecting every neuron to every neuron in the next layer and then the weightings of these connections are tweaked by training them.

Typical application would be in automatic cash handling: A neural network is trained to visually recognize bank note denominations. Another application might be in speech recognition systems.

---

### Post by CptPicard on 2010-09-15
The issue with neural networks would be that they're general function approximators that work nicely for data sets for which the function is relatively well-behaved (smooth, "makes sense") between data points. If the function is more discontinuous, you start needing more and more a pure lookup table (more and more nodes) which is of course not good. I really can't see how something as discrete as a mapping of all programs to correct and incorrect ones would be a good application.

They work well on some problems, but are not a panacea.

---

### Post by worksofcraft on 2010-09-16
> **CptPicard said:**
> The issue with neural networks would be that they're general function approximators that work nicely for data sets for which the function is relatively well-behaved (smooth, "makes sense") between data points. If the function is more discontinuous, you start needing more and more a pure lookup table (more and more nodes) which is of course not good. I really can't see how something as discrete as a mapping of all programs to correct and incorrect ones would be a good application.

They work well on some problems, but are not a panacea.

Neural networks can get stuck in local optimimums when the dataset has discontinuities. One way to get them out of it is to deliberately throw in random noise.

In the hitchiker's guide to the galaxy a computer named "deep thought" optimized the total mapping of all programs and I think it eventually discovered the result was 42. That is the kind of scenario you get when your neural networks hasn't got enough neurons ;)

---

### Post by ssam on 2010-09-17
If you are interested in this sort of thing then you will like the book Gödel, Escher, Bach: An Eternal Golden Braid by Douglas Hofstadter.

---

### Post by KdotJ on 2010-09-17
This reminds me of a project I did in uni where we wrote a text parade that took in a txt file and made sure it conformed to our predefined language (which syntax we made up). Didn't actually compile it though....

---

### Post by Some Penguin on 2010-09-17
For more general purposes, using a neural network or genetic programming system buys you pretty much nothing, because you still need to do all the work of figuring out what features might be important and how to encode them.  This is often not that hard for machine vision, where you're probably just making a call on which convolutions to run, what resolution to use and whether to e.g. switch to HSV or use one of those three components.  This is where a lot of magic lies for many other problems.

---

### Post by phrostbyte on 2010-09-17
> **CptPicard said:**
> Just look at the [Universal Turing Machine]("http://en.wikipedia.org/wiki/Universal_Turing_machine") to get an idea what this "programs understanding programs" deals with. The halting problem is a very fundamental problem in this regard; this is why there are no automated debuggers, and probably no automated programming either.

What this says about the possibilities of for example artificial intelligence is interesting; if brains and computers are equivalent, it is a bit strange that a computer will end up stuck in an endless loop while trying to simulate it, while we can just "see" it is an endless loop... then again it is possible that the Gödel sentences of the human mind simply are not the same ones as those of computers.

The halting problem does not apply when you say "given any algorithm that can fit in less then 100 TB of memory" or "given any algorithm that will ever be written in the next 100 billion years". 

It's: "given ANY algorithm" (notice the boundless possibility). That's a fundamental part of the halting problem. Only in the face of the infinite does the halting problem apply. It means that the halting problem is not a practical limitation - all I have to do is set some kind of upper bound (ie: programs smaller then the known quantum state of the Universe :)). 

I'm not sure what you mean by "automatic debugger", but I know there is nothing stopping you from writing software that finds bugs. There is actually a really popular program for Java called FindBugs which does just that. It will find subtle bugs that software engineers don't always easily find, and that is what makes it incredibly useful.

---

### Post by CptPicard on 2010-09-17
> **phrostbyte said:**
> People really seem to confuse the halting problem. It fundamental attribute is it's input has infinite possibility: it puts no bounds on the type or complexity of a input algorithm. 

The underlying theory of the halting problem is Gödel's incompleteness theorems, and that is where the interesting questions lie. Gödel says that for any given mechanistic symbolic manipulation system you have an infinite number of sentences that are true but unprovable within the system.

The interesting part is that humans are generally able to appreciate the proof of this general incompleteness. Yet it seems like that for any physical computing system (according to the Church-Turing thesis) will have these logical sentecnes that demonstrate that the system is incomplete.

So.. the strong, physical, materialistic AI advocates generally resort to claiming that understanding incompleteness in general does not mean that the mind understanding this is not subject to restrictions of incompleteness, yet. That is, the mind is capable of understanding incompleteness, but it can still full well have constructed Gödel sentences that are not provable within its model. And most importantly, the sentences proving incompleteness are obviously not within that set.

It really is an open question that depends on how you feel about materialism and the state of the art of mathematical logic...

---

### Post by phrostbyte on 2010-09-17
> **CptPicard said:**
> The underlying theory of the halting problem is Gödel's incompleteness theorems, and that is where the interesting questions lie. Gödel says that for any given mechanistic symbolic manipulation system you have an infinite number of sentences that are true but unprovable within the system.

The interesting part is that humans are generally able to appreciate the proof of this general incompleteness. Yet it seems like that for any physical computing system (according to the Church-Turing thesis) will have these logical sentecnes that demonstrate that the system is incomplete.

So.. the strong, physical, materialistic AI advocates generally resort to claiming that understanding incompleteness in general does not mean that the mind understanding this is not subject to restrictions of incompleteness, yet. That is, the mind is capable of understanding incompleteness, but it can still full well have constructed Gödel sentences that are not provable within its model. And most importantly, the sentences proving incompleteness are obviously not within that set.

It really is an open question that depends on how you feel about materialism and the state of the art of mathematical logic...

I think it's an open question like evolution vs creation is an open question - ie. an open question outside of the realm of science. There is nothing mystical or supernatural about the human mind that would make it immune to fundamental laws of computer science and mathematics.

---

### Post by CptPicard on 2010-09-17
> **phrostbyte said:**
> I think it's an open question like evolution vs creation is an open question - ie. an open question outside of the realm of science.

Yes, indeed it is an open question but I personally hope it does not quite mean the natural vs. supernatural distinction that evolution vs. creation represents. It's just a remarkably interesting question regarding the materialism of mind's relation to fundamental mathematical logic that needs a more specific answer.


> 
 There is nothing mystical or supernatural about the human mind that would make it immune to fundamental laws of computer science and mathematics.

Which would mean that there are Gödel sentences of the mind that still allow for the mind to understand the concept of Gödel sentences of physical symbol-manipulation systems *in general*. For the strong-AI materialist advocate this is a no-brainer (that is, they are totally separate logical systems with separate weaknesses); for the others, it means the mind is categorically stronger than any symbolic logic system.

---

### Post by worksofcraft on 2010-09-21
That conversation sort of lost me somewhere, but the great thing about neural networks is you don't have to understand the problem:

The weightings on neural connections are adjusted by training. e.g. you present it with many, very many, valid images and tell it what each one is and it will home in on whatever features it can find to distinguish between them. Sure... later you can analyse the weightings and be totally amazed at what teh difference between a $5 bill and $1 bill is... but you, as the programmer, do not have to work this out... it's all to do with so called "fuzzy logic" theory.

Now what I find even more interesting is the potential of creating a quantum computer.

In a nut shell, you know how at a quantum physics level they discovered that a single particle propagates trough all possible paths to it's destination, creating interference patterns that could not be explained with traditional physics? Well with quantum computers we will use "qubits" to hold our data at a quantum physical level and these will simulatneously propagate through all the legitimate possibilities set by the program to instantaneously produce the correct results.

Ultimately I envisage it as being programmed in something like Prolog, but the inference engine never has to iterate thru different possibilities because teh qubits implicitly home in on the end solution through the quantum "gates" that the program sets up.

It's really fascinating stuff and not just science fiction anymore, as I'm sure a quick Google will tell you!

---

