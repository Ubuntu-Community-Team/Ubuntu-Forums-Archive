---
title: "Launchpad code uploads"
date: 2010-01-17
forum: Programming Talk
---

### Post by k64 on 2010-01-17
How do I upload code onto Launchpad with Bzr? Here's the error that I get:
"bzr: ERROR: Not a branch: "/home/kenny/linux-kernel/devicematic""

Any idea HOW to get my branch configured under Bzr first?

My Launchpad project branch that I recently created is here:

[https://launchpad.net/devicematic/](https://launchpad.net/devicematic/)

[https://code.launchpad.net/~mango-k/devicematic/files/](https://code.launchpad.net/~mango-k/devicematic/files/)

I have two files that I want to upload (that I created) to start the project: "search.cpp" and "structs.h".

I was thinking this will help get the project going. And yes, it's a total of about 60-70 lines of code.

Note: My goal is for this to be as portable as possible. Across multiple GUIs (KDE, GNOME, XFCE...), that is. I *DO* already have a Rectangle struct defined, so really, I helped ease the process.

-Kenny Strawn

---

### Post by matmatmat on 2010-01-17
[http://www.justuber.com/blog/2007/04/25/how-to-use-bazaar-and-launchpad-for-hosting-your-code/]("http://www.justuber.com/blog/2007/04/25/how-to-use-bazaar-and-launchpad-for-hosting-your-code/")

---

### Post by k64 on 2010-01-17
One more question: How do I check my SSH version? I tried uploading the key file only to get an "Invalid public key" error message.

---

### Post by k64 on 2010-01-17
Thank you guys for all your help. Here's the code:

[http://bazaar.launchpad.net/~mango-k/devicematic/files/files](http://bazaar.launchpad.net/~mango-k/devicematic/files/files)

Note: These files are quite long and (somewhat) well-coded. This is a total of 103 lines to get the project started.

---

### Post by CptPicard on 2010-01-17
What language is this in? And where's all the functionality that might be of any use? :confused:

---

### Post by nvteighen on 2010-01-17
What the hell is this???

---

### Post by schauerlich on 2010-01-17
> **k64 said:**
> [http://bazaar.launchpad.net/~mango-k/devicematic/files/files](http://bazaar.launchpad.net/~mango-k/devicematic/files/files)

It burns! It burns us!

> Note: These files are quite long and (somewhat) well-coded. This is a total of 103 lines to get the project started.

Sigh.

---

### Post by k64 on 2010-01-17
> **CptPicard said:**
> What language is this in? And where's all the functionality that might be of any use? :confused:

It's in C++, if you want to know the language.

As for the functionality? It's designed to improve hardware support by grabbing functions from the Linux Kernel API and using them to enable scanned hardware and the subhardware involved in its functionality.

---

### Post by phrostbyte on 2010-01-17
I'm not sure what your code tries to accomplish, but you seem to be inventing some kind of closure syntax to accomplish whatever you are trying to do which is simply not supported in C++. Your code will not compile under GCC or pretty much any C++ compiler.

---

### Post by CptPicard on 2010-01-17
> **k64 said:**
> It's in C++, if you want to know the language.

Certainly not any kind of C++ I've ever seen.

> It's designed to improve hardware support by grabbing functions from the Linux Kernel API and using them to enable scanned hardware and the subhardware involved in its functionality.

Wow. That would be extraordinary if there was anything to that effect in the code...

---

### Post by Sinkingships7 on 2010-01-17
While I truly admire your ambition, this really isn't a beginner-level task. Not even intermediate. If you want to hack for the kernel, you should start by learning how to write a module; preferably something new that you can submit to the kernel devs. Also, you're most likely going to want to be using C: C++ is not used in the kernel.

[SIZE="1"]If you can call that C++...[/SIZE]

---

### Post by CptPicard on 2010-01-17
> **Sinkingships7 said:**
> While I truly admire your ambition, this really isn't a beginner-level task. Not even intermediate.

It is not even in any sense a *possible to accomplish* task...

---

### Post by k64 on 2010-01-17
You probably viewed the structs header. Look at the "search.cpp" file and you'll probably find that there is the "main()" function, void classes, and plenty of functions used. Almost all of my code, however, is defined in the structs header (structs.h).

---

### Post by phrostbyte on 2010-01-17
> **CptPicard said:**
> It is not even in any sense a *possible to accomplish* task...

It's *possible* to accomplish. His problem is a artificial intelligence problem, and one that has been considered in the past (self writing software). However this field has thus far only limited success. It really isn't a beginner problem. If you don't know anything about machine learning you shouldn't be attempting something like this at all. 

And even if you did, you probably should attempt easier things like helping cure cancer. :D

---

### Post by Simian Man on 2010-01-17
I'm not going to be too negative or sarcastic, because your posts smack of wide-eyed optimism and a desire to help, and I can't fault you for that.

But honestly you are so, so, so very far from being able to help with the state of device recognition software on Linux, that it's not even funny.  Honestly my cat has a better chance of figuring out how to order and pay for pizza than this project has of any success.

Take a step back and learn how to actually write code (allow *at least* six months).  Write some simple programs like a hangman game, or tic-tac-toe.  You still won't be able to undertake something like this after that (actually nobody could), but you will at least have a little perspective.

---

### Post by schauerlich on 2010-01-17
> **k64 said:**
> You probably viewed the structs header. Look at the "search.cpp" file and you'll probably find that there is the "main()" function, void classes, and plenty of functions used. Almost all of my code, however, is defined in the structs header (structs.h).

What is this I don't even.

Have you even tried compiling this?

---

### Post by CptPicard on 2010-01-18
> **phrostbyte said:**
> It's *possible* to accomplish. His problem is a artificial intelligence problem, and one that has been considered in the past (self writing software). However this field has thus far only limited success.

No, seriously, if device drivers do not suddenly turn into a strictly limited subset of all possible programs in the computability theory-sense, it is an impossible task :) So is automatic debugging and so on in the general case... halting problem says so :)

---

### Post by nvteighen on 2010-01-18
> **k64 said:**
> You probably viewed the structs header. Look at the "search.cpp" file and you'll probably find that there is the "main()" function, void classes, and plenty of functions used. Almost all of my code, however, is defined in the structs header (structs.h).

Do you realize that your code isn't C++? "Void classes" don't exist in any language (there are virtual classes and it's something else); there are no functions declared nor used, as it's all bad syntax... and the Rectangle Area (Areas?) is useless for GUI programming. And most important of all: There's no code (not even conceptually) that does something.

All you're doing is demolishing your own image by trying to convince us that you wrote something senseful. For instance, nobody will ever take you seriously after looking at the code you've wrote, which you consider to be "long and well-coded"... (when it actually isn't either of both), but nobody will even give you the chance to take you ever seriously even if you become a serious programmer until you don't recognize your mistakes. Recognizing one's faults is the first step to start learning and improving.

---

### Post by CptPicard on 2010-01-18
Well, he's 16 and obviously clueless so don't be too hard on him :) But I must admit that this stuff is pretty epic... ;)

---

### Post by phrostbyte on 2010-01-18
> **CptPicard said:**
> No, seriously, if device drivers do not suddenly turn into a strictly limited subset of all possible programs in the computability theory-sense, it is an impossible task :) So is automatic debugging and so on in the general case... halting problem says so :)

I'm not sure why you bring up the halting problem. The halting problem should not be an issue in such a program. 

But let's assume the statement is true... We must take into account that **computational complexity theory holds for ALL real things which are capable of computation.**

We can then assume that the human brain is not somehow exempt from the halting problem, and yet humans can write drivers just fine! Surely the halting problem is not an issue in writing drivers for the Linux operating system. 

But this brings a bigger observation into the picture: **anything a human can do, a machine could theoretically do**. 

Contending that the human brain is supernatural is more of a religious statement then a scientific one. General or "hard" AI is a difficult computer science problem, but an intractable problem it is not.

---

### Post by CptPicard on 2010-01-18
Seems like you are much more of a strong-AI believer than I am... :)

> **phrostbyte said:**
> I'm not sure why you bring up the halting problem. The halting problem should not be an issue in such a program.

As far as I have understood it, automated programming does not exist because of problems like the halting problem, into which the related problems reduce to. Similar problems are for example the verification of the equivalence of functions. If those are not tractable, it makes it at least very difficult to envision a program that programs (there is certainly not a program that recognizes a faulty program); but of course then we get to the issues you're bringing up... ;)

> 
But let's assume the statement is true... We must take into account that **computational complexity theory holds for ALL real things which are capable of computation.**

Admittedly it's been a long time since I actually took a look at all the complexity classes, but the relevant point is that the Church-Turing thesis hasn't actually been proven; we just assume that all a Turing machine can compute all that is physically computable.

> 
We can then assume that the human brain is not somehow exempt from the halting problem, and yet humans can write drivers just fine! Surely the halting problem is not an issue in writing drivers for the Linux operating system. 

Humans are remarkably good at just "seeing" stuff that trips up mechanical symbolic-manipulation systems such as computers. There just seems to be something pathological about them -- think about what Gödel had to say about incompleteness, which is of course where the reasons to the limits of computability seem to lie. It is of course an interesting question to ask whether the brain has "Gödel sentences" and is equally incomplete, but particularly the reasons that make AI "hard" -- the fact that so far it still seems happily oblivious to the semantics of the symbols it's mangling, and that's where a lot of the actual meaning seems to be -- just leaves me the impression that there's more to it, or at least we really need to explain stuff a bit better.

On a more practical level and why programmers are not unemployed yet; surely it is an issue if you want to write a program that writes the driver, because there is no way to recover from a possible infinite loop that might be introduced... I guess your program just has to write a perfect driver to begin with. I find it difficult to assert that the fundamental problem in "programs dealing with other programs" would not be relevant to the "general automated programming problem".

> 
But this brings a bigger observation into the picture: **anything a human can do, a machine could theoretically do**. 

Only if we strictly believe that the Turing machine indeed computes anything that can be computed, and that the human brain is equivalent to the Turing machine (or worse!).

> 
Contending that the human brain is supernatural is more of a religious statement then a scientific one.

I do not dispute the physical basis of the mind's workings, but it just needs to be shown that it solves a broader class of problems than those of the Turing machine (btw, ever read Emperor's New Mind? :) ).

---

### Post by phrostbyte on 2010-01-18
> **CptPicard said:**
> 
As far as I have understood it, automated programming does not exist because of problems like the halting problem, into which the related problems reduce to. Similar problems are for example the verification of the equivalence of functions. If those are not tractable, it makes it at least very difficult to envision a program that programs (there is certainly not a program that recognizes a faulty program); but of course then we get to the issues you're bringing up... ;)

Well that's simply not true. A compiler is no different from what you call an automated program generator. It takes in input of a certain language and generates output based on the input.

Who is to say that a spec sheet couldn't be input to such a compiler, and the driver being the output? This is significantly more difficult then writing a C++ compiler for instance, but *impossible*? No. It's still fundamentally a compiler, one that works on a more complicated language.

As far simplifying the concept of software development is considered, there is talk of the so called "DSL" or domain specific language, which a driver declaration language (ie. a spec sheet) could be considered. There is work on DSL compilers, ones which can dynamically mold themselves to new domain specific languages without help of a software developer. There is a current research in this field, interestingly Microsoft Research is particularly active this field with their Project Oslo and Semantic Engine.

> **CptPicard said:**
> 
Humans are remarkably good at just "seeing" stuff that trips up mechanical symbolic-manipulation systems such as computers.

Actually machines have gotten a lot better at this too. Computer vision is probably one of the more developed fields in AI. In some cases, machines could react and act to visual cues in a much more robust and complex way then human can, for instance, tracking and responding to several dozen things in a scene at once. This is something a human can not easily do.

---

### Post by CptPicard on 2010-01-18
> **phrostbyte said:**
> A compiler is no different from what you call an automated program generator. It takes in input of a certain language and generates output based on the input.

Oh, they are two totally different things! The translation from one *given and already correct* Turing-complete language formulation of some solution to some other Turing-complete language is a relatively trivial problem in comparison to actually providing the initial solution to begin with.

A compiler (as we generally understand them) does not actually *produce* a solution, which is what a program-generator would do. That's also why I am unimpressed by the claims of the low-level language people to the effect that the compiler/interpreter would somehow contain some particular "magic" that is "intellectually essential" to the solution. Once you have the solution in one computable form, you can translate at will by machine.

> 
Who is to say that a spec sheet couldn't be input to such a compiler, and the driver being the output? This is significantly more difficult then writing a C++ compiler for instance, but *impossible*? No. It's still fundamentally a compiler, one that works on a more complicated language.

This kind of thinking quickly over-trivializes things like natural language recognition, which is also one of these "hard AI problems" that seems to be hard because general AI is somehow fundamentally hard. You are correct in the sense that there is some linguistics in the problem, certainly... we'll run into semantic ambiguity and all that fun stuff.

> 
As far simplifying the concept of software development is considered, there is talk of the so called "DSL" or domain specific language, which a driver declaration language (ie. a spec sheet) could be considered. There is work on DSL compilers, ones which can dynamically mold themselves to new domain specific languages without help of a software developer.

DSLs and these hypothetical spec sheets usually restrict the problem domain heavily; generally we no longer are even talking about any kind of general programming problem in that case, as the generated programs are a well-known small subset of all possible programs. "Boilerplate code generation" is not really automated programming...

I also do produce code from Lisp macros that form DSLs all the time, but the theoretically relevant problem-solution part really  comes from me alone.

> 
Actually machines have gotten a lot better at this too. Computer vision is probably one of the more developed fields in AI.

I really was talking more in general terms, as in recognizing the relevant semantics of, say, expressions in formal logic that would be out of reach of a purely symbolic-manipulation system. More generally in AI, the frame problem is a killer. I'm not sure if you've ever seen the proof about the existence of Gödel sentences, but if you haven't, it's a great example. Its relevance to human cognition is of course debated by a lot of really smart guys; if we could come to a conclusion about it here, we should rather be writing academic papers... :)

Of course, in AI, many previously hard, specific problems have found interesting solutions in the past decade or two, often due to statistical techniques. I don't think they have yet answered the rather fundamental issues that genuine strong general AI has to deal with. Whether AI just *is* a collection of solutions to specific problems is once again debatable...

> This is something a human can not easily do.

My computer can compute pi to a lot of decimals very fast, which is something I can not easily do...

---

### Post by phrostbyte on 2010-01-18
> **CptPicard said:**
> Oh, they are two totally different things! The translation from one *given and already correct* Turing-complete language formulation of some solution to some other Turing-complete language is a relatively trivial problem in comparison to actually providing the initial solution to begin with.

A compiler (as we generally understand them) does not actually *produce* a solution, which is what a program-generator would do. That's also why I am unimpressed by the claims of the low-level language people to the effect that the compiler/interpreter would somehow contain some particular "magic" that is "intellectually essential" to the solution. Once you have the solution in one computable form, you can translate at will by machine.

This kind of thinking quickly over-trivializes things like natural language recognition, which is also one of these "hard AI problems" that seems to be hard because general AI is somehow fundamentally hard. You are correct in the sense that there is some linguistics in the problem, certainly... we'll run into semantic ambiguity and all that fun stuff.


They are not completely different. C++ is a language, and just like any language has a vocabulary and a grammar and can be studied in a formal manner. But the English language also made up the same formal parts as C++, it has a vocabulary and could to some degree be defined by a grammar. That is why it is called a "language", obviously.

Obviously there is a difference between C++ and English. C++ was designed outright to be interpreted by a computer, in a way it's a DSL in that is was designed for a specific purpose (systems programming). We don't see many novels written in C++, for instance. English well really wasn't designed at all. That makes English far harder to interpret and derive meaning from, but my no means impossible. 

None the less, deriving meaning from natural language is an important problem in computer science with many practical applications. Many people work in this field, some who are not even researchers. For instance, Google's search engine involves this field. Although it's still a new field, we have learned that deriving meaning from a natural language not an impossible problem by any means and we use a lot of NLP technology daily.

> **CptPicard said:**
> 
DSLs and these hypothetical spec sheets usually restrict the problem domain heavily; generally we no longer are even talking about any kind of general programming problem in that case, as the generated programs are a well-known small subset of all possible programs. "Boilerplate code generation" is not really automated programming...

Well looks like we are arguing about different things. I am not interested in debating the meta-computability of the human brain. I am arguing nothing about semantics of what "automatic code generation" or "boilerplate code generation" means either. I am considering the feasibility of a system which generates drivers based on data generated from reverse engineering tools or spec sheets. Disregarding k64's naive explanation, I don't understand why you consider this a totally *impossible* problem. Within computer science, impossibility tends to be well defined.

---

### Post by CptPicard on 2010-01-19
> **phrostbyte said:**
> They are not completely different. C++ is a language, and just like any language has a vocabulary and a grammar and can be studied in a formal manner. But the English language also made up the same formal parts as C++, it has a vocabulary and could to some degree be defined by a grammar. That is why it is called a "language", obviously.

Which is insufficient to capture the important distinctions between programming languages and natural language -- talk to anyone who actually works with natural language recognition. Issues like resolving semantic ambiguity (and by extension, the general frame problem of AI) are much more serious than I think you appreciate.

In any case, a programming language compiler is a specific one-off solution to a single problem (a translation from a known, easily processable language to another). I still maintain that this is a completely different problem from production of solution that would require solving major open problems.

> C++ was designed outright to be interpreted by a computer, in a way it's a DSL in that is was designed for a specific purpose (systems programming). We don't see many novels written in C++, for instance. English well really wasn't designed at all. That makes English far harder to interpret and derive meaning from, but my no means impossible. 

Please nvteighen, do take over... ;)

> None the less, deriving meaning from natural language is an important problem in computer science with many practical applications.

It seems to me that the *very access to meaning* is that hard part in computation and artificial intelligence in general. I'm once again referring to Gödel (are you familiar with the concept and implications of incompleteness?). I mean, we are fully capable of understanding the meaning of the Gödel sentence proof, yet, symbolic systems get tripped up, in infinite ways, no less.

> 
Well looks like we are arguing about different things. I am not interested in debating the meta-computability of the human brain.

Well, if there was a general-purpose AI, then it could program. However, the automatic programmability by programs really runs into some very interesting problems sooner than "having to develop AI"...

> 
 I am arguing nothing about semantics of what "automatic code generation" or "boilerplate code generation" means either.

I am, and the distinction is important. Automatic programming is really a problem of its own, separate from some reduced "code generation from DSL" based stuff. I don't think that you can reduce driver programming into such a subset that it would no longer be the same thing as generally programming any program. (Well, if you can, go ahead... but that requires some external protocols or something).

> 
 I am considering the feasibility of a system which generates drivers based on data generated from reverse engineering tools or spec sheets.

Ok, if the behaviour of the hardware and the expected behaviour at interface is well defined, it may even be easy to generate some shuffling of bits between buffers or something. But in that case I am not sure why you'd bring it up as an artificial intelligence problem ;)

> 
 Disregarding k64's naive explanation, I don't understand why you consider this a totally *impossible* problem.

As Linux stands, I take it that writing drivers is the same as writing programs in general (as there is are no DSLs or spec sheets... the problem is quite unrestricted -- I can't understand why you couldn't find a piece of hardware that pretty much forces you to write "any code" to deal with it correctly).

> 
 Within computer science, impossibility tends to be well defined.

Certainly. As soon as you tell me how you plan on for example verifying that anything is generated actually does what it is intended, or that some piece of code is equivalent to some other piece of code, and why using a Turing machine to prove stuff about other Turing machines seems to impossible in many cases, we might be well on our way to generating programs that program... :) I personally do not like just hand-waving away what seem to me to be profound theoretical limitations, although I'm of course open to demonstrations that they are not significant...

---

### Post by nvteighen on 2010-01-19
> **phrostbyte said:**
> They are not completely different. C++ is a language, and just like any language has a vocabulary and a grammar and can be studied in a formal manner. But the English language also made up the same formal parts as C++, it has a vocabulary and could to some degree be defined by a grammar. That is why it is called a "language", obviously.

Obviously there is a difference between C++ and English. C++ was designed outright to be interpreted by a computer, in a way it's a DSL in that is was designed for a specific purpose (systems programming). We don't see many novels written in C++, for instance. English well really wasn't designed at all. That makes English far harder to interpret and derive meaning from, but my no means impossible.

> **CptPicard said:**
> 
Please nvteighen, do take over... ;)


I take over... :p

The issue is that the difference between a "verbal" language like English (or an artificial one like Esperanto) and a programming language is that the second ones are used for the creation of "ad hoc" semantical systems for a certain issue, while human language has a wide general semantical system already for usage plus built-in systems to extend the language within itself if something is detected to be lacking in the language.

In simple words, programming languages are formal languages, where human languages are substantial languages, we could say.

When writing in a programming language you start with a very narrow vocabulary... The only thing you've got is a set of syntactic and semantical rules that point to the production of new meanings. Ok, you get some basic data structures, which you can call the "basic vocabulary", but it's quite common that that alone isn't enough for creating something non trivial in any programming language. Just using primitive datatypes is analogous to just using primitive words in a text...

This is related to this thread's current discussion. I won't discuss the feasability of this project because I don't have any theorical base to judge that, but what I am able to distinguish is that this task is completely different to just compile a formal language into another formal one. Compiling from C++ into, say, valid Javascript is completely possible because you're working with context-free languages (therefore, unambiguous) that are constructed both with a regular set of rules (no matter how complex it is) and both refer, in the end, to the same reality: processes. Of course, the resulting Javascript will be very surely a very hard read for a human because the computer won't be able to do style modifications to make stuff psychologically clearer. But creating a driver will include having to analyze data that way that the computer inductively creates a set of rules in order to have a formalized abstraction of the device; that means you'll have to teach the computer how to "creatively" act with the data in order to make it more efficient.

---

