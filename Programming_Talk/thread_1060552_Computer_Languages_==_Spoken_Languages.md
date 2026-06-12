---
title: "Computer Languages == Spoken Languages"
date: 2009-02-04
forum: Programming Talk
---

### Post by Fosfate on 2009-02-04
I think workable knowledge of C++ is equal to a language like Spanish or French.

Why I am posting this randomly? I'm justifying the time I spend learning C to equal that of the time another person will spend learning French or German.

Thus, a computer language is a real language.

You guys agree with this? (I hope you all do)

---

### Post by Xcmd on 2009-02-04
Yes and no. More yes than no. Yes because it's learning how to think in a way contrary to your normal thought-processes (although if you do it long enough your thought processes make this thinking pattern normal) and no because programming languages are task-specific.

It's more like learning how to speak Spanish in the narrow scope of Food Ordering. Or Japanese only in the narrow scope of Business. You're learning task-specific things.

But in programming there's very little to do with tenses and while there is some flexibility, if you screw up what you're saying, your target audience (the parser) is going to throw a fit and refuse to hear you out. Language is more flexible and error is more forgivable. If you accidentally say "I to airplane go", when you mean to say "I'm going to the airport", we get the gist of what you meant.

In programming if you say "if x = y:" and you're supposed to be saying "if x == y:" then you're boned.

So while both use similar portions of the brain and thought processes and are, at first blush, very similar... they're not quite the same. They're achieving different goals, but the learning process is much the same and the end result is similar.

Yes, they're the same. And no, they're not.

---

### Post by Fosfate on 2009-02-04
I have to disagree on the task specific thing... you can write a complex program in C, I'm pretty sure you could write a complex program in a different category.

While I can't write a business plan, I could research how to write one and then write one in my own way.

This is a tough analogy to make, but I'm trying to make it haha...

---

### Post by cabalas on 2009-02-04
I agree on the task specific thing, while you can code most programs in most languages there are usually those that are better suited for the task than others.

As for the original question I think it's less like learning a different language rather more like learning the customs of a different culture.  You learn to work in an environment in such a way to achieve the best result.

---

### Post by shadylookin on 2009-02-05
not really, for one thing programing languages aren't spoken

for another you can't really express the range of things you can with spoken languages

---

### Post by haemulon on 2009-02-05
Spoken language is amongst the most important functions of the human body.  

We express ourselves, wants, needs, art, etc through the spoken language (at least if we have that ability).  If through a physical disability we cannot actually speak we will still do it by sign language, writing etc., but we've lost some part of having a full range of expression.  

Programming languages are tools to help solve problems and build things that are useful to people.

Most people don't know a programming language and they've not lost part of the human function of language or had it diminished. 

The two are quite different.

---

### Post by CptPicard on 2009-02-05
No, spoken (natural) languages and Turing-complete languages are quite different. There is most importantly the problem of ambiguity where meaning depends on external context that just is somehow "obvious" to the communicators.

Natural languages really are much more complex and messy than formal ones which are limited by the computability requirement and can be designed for purpose. Of course, the discussion on whether "it's all just binary anyway" or whether there are qualitative differences in the way different languages "communicate about programs" within the class of Turing-complete languages often turns into a hot topic :)

Where's nvteighen when you need him...

---

### Post by nvteighen on 2009-02-05
Both are particular cases of the general linguistic ability the human has. Both serve to communicate abstracted ideas about some reality... the issue is that natural languages (spoken or not) are able to describe the real world, but programming languages are not.

There are a lot of differences. 

1. **A programming language has very little lexical entities:** You don't learn more than keywords + standard functions... and the need of learning them depends on what you are doing, too. This is because programming languages are more suited towards creating new "words" (functions, classes, etc.) rather than make you work with a fixed lexicon. In natural languages, the productive amount of word creation is a lot less and you're limited by pragmatical issues (if I create the verb "to usagize" (< "usage"), it will be succesful only if people realize what meaning am I giving to that word... and of course, soon they'll realize it's redundant as "to use" already exists).

2. **Limited pragmatics:** Natural languages are embedded into a culture and sometimes you have to say things in a certain way just because it is said that way. For example, in English you say "Thank you", even if "#I give you thanks" is syntactically correct but nobody says that... though that is what we may say in Spanish: "Te doy (las) gracias" (which is pragmatically correct... though not the only possible way). This implies to memorize a lot of fixed stuff you just can't "construct" when speaking. Programming langauges don't have this: if the code works, then it's valid. But, it's true that there are "good practices" or that we sometimes say "this is code is not Pythonic" (a C-like Python code)... these are pragmatic issues that sometimes arrive because we use programming languages also to communicate between humans, but as you see, a non-Pythonic Python code is still valid Python, so pragmatics have a secondary and limited role in programming.

3. **Language "design":** A programming language is supposed to be designed to be the best solution for some programming problem. A natural language is just there and it's not designed to solve anything... actually, they aren't even designed and can have incoherences within their system (though all are logically explainable). So, in a programming language you can learn a lot of stuff with just deducing it after you have become familiar with its design principles. In a natural language, you are more likely to guess and fail (irregularities, pragmatical issues, etc.).

These are some of the most basic differences I can think of. There are certainly more, but they'll require a bit more technical Linguistics jargon... so, "as proof a button" (pragmatically incorrect translation from Spanish saying "para muestra un botón" :))

---

### Post by maximinus_uk on 2009-02-05
I'd have to say that learning real languages is much much harder, mainly (for me) because they are not logical and also because they require another skill - that of listening to a native speaker. You also need to learn at least 1000 words before you can hold a simple conversation. Even Lisp isn't that big!

I've studied Dutch, which is the closest language to English, and Chinese - which may be the furthest. With the latter I can now hold (very) basic conversations after 2 years of study. (&#25105;&#24819;&#20013;&#25991;)

Compare that with learning Lisp. It took me about a year to finally 'get' Lisp, and read other peoples code (and write my own), and that was maybe only a few hours a month of trying it out.

---

### Post by howlingmadhowie on 2009-02-05
as heard on comp.lang.forth, if you're not writing machine code, you're writing comments. 

one way to look at a computer language is as a way to generate new words to best suit the task you want to carry out. the object-oriented programmers would have said in the 90s that object-orientation enables you to model the real world in a computer simulation. back then they were big on examples with class definitions for cars and houses and trees and stuff. doubtless the tree would have a method grow() or photosynthesize(). 

one of the big problems with computer languages is that they really have to be unambiguous, even when the result is independent of any ambiguity. an example:

```
x = 2 + 3 + 4;
```

the big problem is, how do you make a parse tree of this? is this to be read as (2+3)+4 or as 2+(3+4)? to solve this, languages define things such as left associativity, and a lot of a language definition deals with stuff like this. 

so basically i would say that there are huge similarity. both human and computer languages involve tokens which have a certain syntactic and semantic meaning. both often include things like nouns and verbs. prepositions (and not in the sense of phrasal verbs) tend to be lacking from computer languages, unless you look at smalltalk, where you could define a function as

```
behitonthehead by: fred with: a_hammer from: behind
```

otherwise the order of passed arguments is used to fake prepositions.  

just some thoughts.

---

### Post by tturrisi on 2009-02-05
There are similarities, differences and identities between spoken languages and computer languages.  However, the spoken language contains a variable that programming languages do not contain; the intention behind the spoken word.

A spoken word is only a symbol for an object or action.  An intention is the "what the originator wants the recipient to receive so as to bring about understanding".

Any words can be used to effect a communication so long as the intention is received and duplicated by the recipient, resulting in an understanding.  To easily demonstrate this, watch a foreign movie and there will be scenes that you understand even though you don't know the meaning of the spoken words.  Same when talking to someone who is using a foreign language.

Add emotion to the spoken word, voice inflections and physical mannerisms, and spoken language far exceeds any programming language.  In that light, computer language can be considered as very primitive.

---

### Post by NathanB on 2009-02-05
C++ is a **subset** of natural language.  It consists of only *imperative* statements much like the recipe a cook would follow.  Each statement changes the state of the system.  It is a domain-specific language in that it can only address issues that fall within a computing domain.  Only computers and detail-oriented people use C++ as a communication medium.  All entities outside the computing domain communicate by using a much larger subset of natural language.

---

### Post by Fosfate on 2009-02-05
Wow!

Surprised most people here are thinking that a computer programming language is not equivalent to a spoken foreign language. I thought everyone here would be of my mentality going "yes it is the equivalent, these are the languages of the future."

---

### Post by Reiger on 2009-02-05
Hey, this dicussion reminds me of another one, just one page back.

> **maximinus_uk said:**
> I've studied Dutch, which is the closest language to English, and Chinese - which may be the furthest. With the latter I can now hold (very) basic conversations after 2 years of study. (&#25105;&#24819;&#20013;&#25991;)

And how about the former. :) Actually, Dutch isn't the closest to English, Frisian is closer.

---

### Post by nvteighen on 2009-02-05
> **Reiger said:**
> Hey, this dicussion reminds me of another one, just one page back.



And how about the former. :) Actually, Dutch isn't the closest to English, Frisian is closer.
Actually, Danish is even closer...

---

### Post by haemulon on 2009-02-05
Maths, programming and writing are similar.  The essence is the expression of a process and a creative activity.

Music is a bit closer to the spoken language than maths or writing.  Spoken language and music can put the listener under a light trance but they all have the capability.

They are languages but have many features unlike the spoken language because that often involves human interaction (that is person to person).

Rarely have I heard a beautiful speech or words.  More often I've seen beautiful maths and heard beautiful music and read beautiful words.

Programming, music, math and good writing for all their technical requirements are still very much art forms  (music being the most artistic and sublime).

Speech is a bodily function of prime importance but need not ever be artistic.

---

### Post by Ferrat on 2009-02-05
> **haemulon said:**
> Maths, programming and writing are similar.  The essence is the expression of a process and a creative activity.

Music is a bit closer to the spoken language than maths or writing.  Spoken language and music can put the listener under a light trance but they all have the capability.

They are languages but have many features unlike the spoken language because that often involves human interaction (that is person to person).

Rarely have I heard a beautiful speech or words.  More often I've seen beautiful maths and heard beautiful music and read beautiful words.

Programming, music, math and good writing for all their technical requirements are still very much art forms  (music being the most artistic and sublime).

Speech is a bodily function of prime importance but need not ever be artistic.

What have you been smoking and can I have some? :P 

No but on topic, mathematics are the one true denominator if any to all languages that have some logic etc to them (which most do with some sort of grammar), music falls under this as well since music strives for harmony (with some exceptions:P) and have a close relationship with math, specially high-dimensional geometry according to experts :)

---

### Post by CptPicard on 2009-02-05
> **haemulon said:**
> 
Speech is a bodily function of prime importance but need not ever be artistic.

Try telling [Cicero]("http://en.wikipedia.org/wiki/Cicero") that... :)

---

### Post by haemulon on 2009-02-05
> **Ferrat said:**
> What have you been smoking and can I have some? :P 

sure it's called Ubunut, you can have all you want...

actually I don't smoke :P


> **Ferrat said:**
> 
No but on topic, mathematics are the one true denominator if any to all languages that have some logic etc to them (which most do with some sort of grammar), music falls under this as well since music strives for harmony (with some exceptions:P) and have a close relationship with math, specially high-dimensional geometry according to experts :)

It does seem so, I don't remember who said it about music being the highest form of mathematics.

...we'll have to discuss the issue about wether 1 is a prime number or not sometime.  It's been on my mind so much lately :P

---

### Post by howlingmadhowie on 2009-02-05
> **haemulon said:**
> 

...we'll have to discuss the issue about wether 1 is a prime number or not sometime.  It's been on my mind so much lately :P

i thought 1 was by definition not a prime number.

---

### Post by waspbr on 2009-02-05
spoken languages are spoken to people and programming languages to computers, while that is obvious, the suddle difference is that languange in its basic form is only a way of interchanging information, while every computer is going to respond in a similar manner to every input, the same cannot be said for humans. 

aside from that languages conduct moods, tones and whatnot... so no programming languages are not equal to spoken languages.

---

### Post by nvteighen on 2009-02-06
> **waspbr said:**
> spoken languages are spoken to people and programming languages to computers, while that is obvious, the suddle difference is that languange in its basic form is only a way of interchanging information, while every computer is going to respond in a similar manner to every input, the same cannot be said for humans. 

Not really. The computer only understands binary... not even ASM. Programming languages were created for making humans' job easier, not the computer's. Of course there's some sort of communication with the computer (through the compiler/interpreter) but it all boils down to binary code... but a human cares about what language is more appropriate to do some task, which it suits better... even which he likes more, etc. And then you have "good practices" and discussions whether some code is "C-like" or if it's a "Perlism" to use regexps compusively in a Python code... All stuff the computer really doesn't care about, but we humans do.

About the issue that humans not necessarily respond the same way to the same sentence... Well, believe it or not, in the early XX century, there was the so called Conductivist Linguists who believed that people reacted the same way to the same linguistic factors... if they reacted differently, it's because the factors were slightly difference. It's true that we expect a certain kind of reaction when we tell something to somebody and that the reaction's range is a bit limited and predictable, but not 100% defineable as these people thought.

> aside from that languages conduct moods, tones and whatnot... so no programming languages are not equal to spoken languages.

That's true. Natural languages are non-specialized, so they let you do everything :)

---

### Post by pp. on 2009-02-06
> **nvteighen said:**
> The computer only understands binary... not even ASM.

I don't think so. A computer is some hardware plus some software. You can feed some COBOL or LISP or ASM into a computer which is suitably equipped and the computer will do as commanded by what you fed it. That's as close to "understanding" as it can get.

If you don't accept compilers and linkers and such as part of the computer, then you also can not accept some I/O routines, in which case it won't understand 'binary', either. Rather, it won't "hear" it.


> **nvteighen said:**
> Programming languages were created for making humans' job easier, not the computer's.

Feeding the computer higher level programs rather than the binary code can be said to make the computer's job easier: The binary representation of a program might be longer than the high level language representation, and I/O is much slower than processing by the CPU.

Also, processing "correct" programs makes the computer's job "easier", and people are better at producing "correct" programs when using higher level languages. Some languages, anyway.

> **nvteighen said:**
> Natural languages are non-specialized, so they let you do everything :)

Actually, the thread's title names "spoken languages" but not "natural languages". Hence, some of the arguments used in this thread do not really apply. How about Esperanto?

---

### Post by Mr.Macdonald on 2009-02-06
I agree and Lisp is the god language and is comparable to latin

---

### Post by Reiger on 2009-02-06
You mean lisp > latin? Because, for all its merits Latin really is quite ugly quite quickly. If we take a yardstick in how ugly PHP interspersed with HTML (preferably using shorthands) can get, well, Vulgar Latin of the Medieveal times takes it to a whole new level.

And Latin wasn't exactly the most elegant language to begin with, anyways -- but I digress (and that is to some extent a matter of taste).

---

### Post by nvteighen on 2009-02-07
> **pp. said:**
> I don't think so. A computer is some hardware plus some software. You can feed some COBOL or LISP or ASM into a computer which is suitably equipped and the computer will do as commanded by what you fed it. That's as close to "understanding" as it can get.

I see your point. I guess I'll have to take another look to my ideas :)

> 
Feeding the computer higher level programs rather than the binary code can be said to make the computer's job easier: The binary representation of a program might be longer than the high level language representation, and I/O is much slower than processing by the CPU.

Yeah, but look at interpreted languages... they do add an overhead because of the translation into binary.

> Actually, the thread's title names "spoken languages" but not "natural languages". Hence, some of the arguments used in this thread do not really apply. How about Esperanto?

Ok, I have digressed a bit in that sense. Artificial languages are specialized, of course. The difference between Esperanto and, say, C is much less.

---

### Post by pp. on 2009-02-07
> **nvteighen said:**
> The difference between Esperanto and, say, C is much less.

The difference may be less, but I doubt very much that programming languages and languages used among humans have much in common.

Programming languages are called "languages" because the "utterances" possible in a programming language consist of symbols, (usually) well defined rules for their arangement in a one-dimensional space, and rules which establish the meaning of said symbols (if any).

Languages used among humans have a much broader range of properties (as you're well aware, of course). Just some areas where I think the difference is glaring:

Have you seen any poetry in - say - C, Lisp or Python? "Human" languages are used routinely in ways which are based on the form of the statements as much or more as on their contents. (I am a declared fan of Dada).
When have you observed any conversations between two or more parties held in a programming language? 
How do you ask for or give advice concerning your love life in COBOL?

In short, I think "programming language" is something of a misnomer. "Programming formalism" or some such would be far less misleading but disappointingly honest.

---

### Post by nvteighen on 2009-02-07
> **pp. said:**
> 
Programming languages are called "languages" because the "utterances" possible in a programming language consist of symbols, (usually) well defined rules for their arangement in a one-dimensional space, and rules which establish the meaning of said symbols (if any).

In Linguistics, a "language" is whatever system/code of symbols. So, according to that, programming languages are languages. (Careful: I won't get into the discussion of what's a dialect and what a language... it's clear that a dialect is a language in the sense I described above).

> 
Languages used among humans have a much broader range of properties (as you're well aware, of course). Just some areas where I think the difference is glaring:

Have you seen any poetry in - say - C, Lisp or Python? "Human" languages are used routinely in ways which are based on the form of the statements as much or more as on their contents. (I am a declared fan of Dada).
When have you observed any conversations between two or more parties held in a programming language? 
How do you ask for or give advice concerning your love life in COBOL?

LOL. If we exclude the weird haikus in Perl, no.

And this is because these languages are specialized. But, careful: artificial languages are also specialized, but in another way. Think, for example, in Esperanto. Why would you use Esperanto to say something and not a natural language? IMO, because you want to contribute to Esperantism or mock Esperantism or whatever... not just communicate (something a natural language already does). Take Tolkien's poetry in Elvish languages: they're great, but their goal seems to be (I'm not Tolkien, of course) not only aesthetic pleasure but also give a better background to his literary works. And so on...

> In short, I think "programming language" is something of a misnomer. "Programming formalism" or some such would be far less misleading but disappointingly honest.

Hmm... Ok. But "formalism" is not contradictory to "language"... These are "formal languages": languages whose symbols are referred to form not to matter. But discussing nomenclature is a bit silly in most cases...

Curiously, in Spanish the misnomer, if it exists, is worse: "lenguajes de programación". The problem with "lenguaje" is that it means the same as French "language", i.e. "the ability of speech". It's possibly a mistranslation from English's "programming languages", as English doesn't have the classical distinction "language"/"langue" that made F. de Saussure famous. The translation I always defend is "lengua de programación"... but I'm digressing.

---

### Post by tturrisi on 2009-02-07
Philosophic Diatribe:

Computer language can never be as robust as human language.  Computer language is the language of machines, man made machines.  Machines will never actually think for themselves.  They will emulate human thought, but will never actually have their own thought. The only "thought" a machine can have is what it has been told to have, by humans, either the machine designer/programmer or the operator.

The human mind processes data, large quantities of data simultaneously, faster than any computer can ever handle.  Consider that there are about 50 some separate possible perceptions, many more than the 5-6 common talked about perceptions.  This includes temp, weight, humidity, gravity, poisition in space, etc. Many perceptions are recorded in a human mind, at about 25 frames/second.

The human mind can perceive and instantly compare the present to the past and at the same time envision a future.  Take a look around the room you are in right now, really nptice what's there.  The quantity of data your mind is processing is at a level no man made machine could possibly ever attain.

Machines cannot perceive.  They can record data, but that's not the same as perception.

> Thus, a computer language is a real language.

There's a contextual difference between computer language and human language, same word "language", different definitions.  Computer language boils down to nothing more than a set(s) of instructions & rules for their use (grammar), while human language has the purpose of communication between humans.

To understand this fully you need to understand the component parts of communication:

Cause (Source) ---- Distance ---- Effect (Receipt)

A person at Cause has his Attention on the person at Effect.   And Cause has Intention that pushes the communication particle(s) across a Distance to Effect.  Effect has Attention on Cause and Duplicates what has been communicated, which results in Understanding.  And Effect must Acknowledge that the communication has been received, which ends the cycle.  Reversed, this becomes two-way communication.

This cycle remains sane, as will people, so long as the components are all implemented. Interestingly, TCP/IP tries to adhere to this formula for communication. 

Inanimate objects, computers, cannot be cause, they cannot originate communication.  They can only be the effect of predetermined instructions given to them by a humans.  The idea of a computer originating communication is just an apparancy, not an actuality.

Throw a stone against a window.  We say, "the stone broke the window." An apparancy.  "Who threw the stone?" Is the actuality of it.

Corollary:

Programming languages are not real languages like human languages are real languages.

Corollary:

Programming languages will never replace human languages.

---

### Post by nvteighen on 2009-02-08
> **tturrisi said:**
> Philosophic Diatribe:

Computer language can never be as robust as human language.  Computer language is the language of machines, man made machines.  Machines will never actually think for themselves.  They will emulate human thought, but will never actually have their own thought. The only "thought" a machine can have is what it has been told to have, by humans, either the machine designer/programmer or the operator.

Hmm... Not sure if I get your point: Computer languages are also made by humans, so they're not the languages of machines... they're rather the languages made by human for machines.


And also, we have to take account on something else. Who reads the "texts" written in programming languages? Humans. The computer doesn't read them or at least is not the only one able to read them. I can write a Perl script in a piece of paper and give it to you; if you know Perl, you'll be able to understand what I "mean" without the need of a computer.

I think there's more "humanity" in programming languages than we notice at a first sight. Of course this doesn't mean I think a programming language is able to compete with a natural/spoken language.

> 
There's a contextual difference between computer language and human language, same word "language", different definitions.  Computer language boils down to nothing more than a set(s) of instructions & rules for their use (grammar), while human language has the purpose of communication between humans.

Again, what happens when two coders read their codes? Aren't programming languages also designed to be human-readable. IMO, programming languages are a weird mixture... an hybrid construct that does its job in a really good way.

But look at the case of Lisp. It was designed to be a human language for algorithms... but was implemented in a computer because of a "rebel" student of McCarthy. If you look at the minimalist Lisp dialects (those which try to keep up with the original Lisp), there is nothing referred to computers in them (maybe the cons-pair is an implementation detail that slipped away). It's a language meant for humans that need to describe algorithms.

> 
To understand this fully you need to understand the component parts of communication:

Cause (Source) ---- Distance ---- Effect (Receipt)

A person at Cause has his Attention on the person at Effect.   And Cause has Intention that pushes the communication particle(s) across a Distance to Effect.  Effect has Attention on Cause and Duplicates what has been communicated, which results in Understanding.  And Effect must Acknowledge that the communication has been received, which ends the cycle.  Reversed, this becomes two-way communication.

This cycle remains sane, as will people, so long as the components are all implemented. Interestingly, TCP/IP tries to adhere to this formula for communication. 

Inanimate objects, computers, cannot be cause, they cannot originate communication.  They can only be the effect of predetermined instructions given to them by a humans.  The idea of a computer originating communication is just an apparancy, not an actuality.


Yuck... you're really outdated (IIRC, that's Halliday's model). Roman Jakobson in 1957 postulated this model (in a really weird article called "Linguistics and Poetics"):
```

Source ---(Channel)--- Message ---(Channel)--- Recipient
                          |
                         Code
(Some context)

```

But your argument remains valid for the execution of some code. If we use Jakobson's "functions" (nobody knows what he meant under "functions"), a computer code... specially in imperative-style, is an "apellative text", as the message is not pointing to the surrounding context ("enunciative"), but to the very receipient (although... could we consider the recipient to be part of the context too?). Functional and declarative programming is possibly more "enunciative" as they're more descriptional and indirectly "apellative" (only in the case of a computer). Jakobson says he considers his six functions to be compatible among them, so nothing prevents a Perl code to be even "poetical" (message pointing to the message itself).

> 
Corollary:

Programming languages are not real languages like human languages are real languages.

Corollary:

Programming languages will never replace human languages.

+1 and +1

---

### Post by CptPicard on 2009-02-08
> **nvteighen said:**
> (maybe the cons-pair is an implementation detail that slipped away).

Actually the meaning of the cons pair is something I thought about some time ago -- it really is an example of a kind of bare-minimum data structure you can use to get everything else. At Lisp's level of abstraction, you need to be able to "keep two things together", after which you get lists, trees (and once you have that, the data structure you use to express lisp itself)... if you did not have that ability, I fail to see how you could do much anything (you might be able to "refer to something" but that still is not enough).

Mind you, a typical RAM machine with its pointer is syntactic sugar on top of that -- in that you already have the concept of an array which is n things kept together.

> Roman Jakobson in 1957 postulated this model (in a really weird article called "Linguistics and Poetics"):
```

Source ---(Channel)--- Message ---(Channel)--- Recipient
                          |
                         Code
(Some context)

```

[Claude Shannon]("http://en.wikipedia.org/wiki/Claude_Shannon") published something similar in 1948 :p

---

### Post by nvteighen on 2009-02-08
> **CptPicard said:**
> Actually the meaning of the cons pair is something I thought about some time ago -- it really is an example of a kind of bare-minimum data structure you can use to get everything else. At Lisp's level of abstraction, you need to be able to "keep two things together", after which you get lists, trees (and once you have that, the data structure you use to express lisp itself)... if you did not have that ability, I fail to see how you could do much anything (you might be able to "refer to something" but that still is not enough).

Mind you, a typical RAM machine with its pointer is syntactic sugar on top of that -- in that you already have the concept of an array which is n things kept together.



[Claude Shannon]("http://en.wikipedia.org/wiki/Claude_Shannon") published something similar in 1948 :p

Yes, Jakobson based his diagram on his, but Shannon didn't consider the context as he was an electrical engineer (Here's a link to his paper. The diagram is in page 1: [http://www.stanford.edu/class/ee104/shannonpaper.pdf](http://www.stanford.edu/class/ee104/shannonpaper.pdf)). And Jakobson's most important contribution was the link between the elements of communication and the "Acts of Speech Theory" (Pierce, Searle and co.).

---

### Post by CptPicard on 2009-02-08
> **nvteighen said:**
> Yes, Jakobson based his diagram on his, but Shannon didn't consider the context

Well, context is the random (or in some other way modelled) noise function if you will. :p

Now this is something I need to remember -- one of the girls I fancy is into poetry, and now I can tell her why I don't "get it" -- there's too much noise (context) introduced into the information in poetry so that the communication no longer makes any sense at my end :p

> "Acts of Speech Theory" (Pierce, Searle and co.).

The "Chinese Room" Searle?

(By the way that is an interesting argument regarding this thread and "understanding of language" in general)

---

### Post by tturrisi on 2009-02-08
> Again, what happens when two coders read their codes? Aren't programming languages also designed to be human-readable. IMO, programming languages are a weird mixture... an hybrid construct that does its job in a really good way.
Agreed.  But the script, or any other comp language code, will have to contain definitions of terms (declared variables) to be able to communicate  on the same level as spoken or written human words.

As for poetry, or any other human communication, the only thing that prevents understanding of what has been communicated is the terms themselves.  This complexity arises from the fact that one word can have multiple meanings.  The interpreted meaning is determined by the context of the communication, e.g. the words preceding a term and the words following the term.  And often, artistic communications such as lyrics or poetry, contain idioms, slang, esoteric usages of terms and/or obsolete uses of terms.

example:

I just ran away from home
Now I'm going to dizz knee land
I just crashed my car again
Now I'm going to dizz knee land
I just robbed a grocery store
I'm going to dizz knee land
I just flipped off President George
I'm going to dizz knee land.

The average listener to the above song wonders, "What's the big deal about going to Disneyland?".  In the context above, dizz knee land sounds like Disneyland == a mental institution.

example:

It was found that when the crepuscule arrived the children were quieter and when it was not present, they were much livelier. 

You think you do not understand the whole idea, but the inability to understand comes from the one word: crepuscule ==  twilight or darkness.

---

