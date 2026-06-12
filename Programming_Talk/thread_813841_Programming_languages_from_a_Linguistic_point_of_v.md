---
title: "Programming languages from a Linguistic point of view"
date: 2008-05-31
forum: Programming Talk
---

### Post by nvteighen on 2008-05-31
Motivated by pmasiar in another thread ([http://ubuntuforums.org/showthread.php?t=752513&page=8#post5081429](http://ubuntuforums.org/showthread.php?t=752513&page=8#post5081429)), let's discuss some features programming languages have in contrast to natural languages!

I've been doing some informal observations on how programming languages reflect features present in natural languages. And also how programmers sometimes end up discussing Linguistics without noticing it (as I said in the other thread, the "best programming practices" are pragmatical discussions).

A topic I'm very interested currently on is where does "meaning" rely on programming languages. Using the same example I used in the other thread, for the C statement **while(1)**, what does define its meaning: The letters w-h-i-l-e (we can't speak of phonemes here as in natural languages)? The word "while"? The whole statement "while(1)"? Or is it the whole while-loop it declares?

For the English word "while" you have two layers of undivisable units that mark semantic differences (Saussure's "Double Articulation" principle): 1) the phonemes: if you just shorten the /i/, you get "will", another different word! (forget spelling, focus on pronounciation). 2) The monemes: in this case, the whole word "while" which undoubtly also is a unit in its own compared to e.g. "sadness".

But in programming languages, you have a problem. Python's **print "A"** does mean something by its own, but neither "print" nor "A" really mean something by themselves separated. And you could theorically declare a variable **pront = 8**, where **print pront** does make sense, but **pront "A"** doesn't, no matter how valid information "pront" (if properly declared) actually is for the Python interpreter.

So, are we humans which finally give meaning to programming languages from the outside? But the interpreter/compiler does have a part on this, of course... that would mean the language retains meaningful structures by itself... If so, where is the meaning?

Any thoughts? (If you actually understood anything of this... Maybe I'm being more esoteric than Lisp-hackers?? :p)

---

### Post by days_of_ruin on 2008-05-31
ooookay>.>

---

### Post by Lau_of_DK on 2008-05-31
Ehm - So for the slow student in the class: What type of responses to your post are you looking for? :)


/Lau :popcorn:

---

### Post by Majorix on 2008-05-31
Me iz confuzed :confused:

---

### Post by nvteighen on 2008-05-31
Any coherent thought is accepted! :) 

(This thread is the result of a rainy and grey saturday...)

Actually, I'm looking forward any contrast between natural and programming languages... Not restricted to the semantic issue I described (I may be wrong, of course).

For example, Lisp people may be interested on this, as you can program the language itself with it. What common patterns are used for that, for example? Does the result resemble a natural language?

Or how much does one's native language determine the way you program?

---

### Post by Npl on 2008-05-31
W T H?

Are you implying we should analyse programming languages by the phonetical sound of its words ? Because thats the only argument i can get from your post.

The building "grammatical" blocks of languages (eg types, variable names, for, do-while, blocks, etc)are defined in their specifications and it doesnt make sense to go lower than that.

---

### Post by Lau_of_DK on 2008-05-31
Oh I see what you mean. 

Yea actually in Lisp the result is often programs that are almost fully readable in english - or at least I thought so myself until I showed a program to someone who wasn't familiar with ((((lisp syntax)))). But anyway, something like this

```

(loop 
  for x from 1 to 10
  when (prime? x)
  collect x)

```

this would output: (1, 2, 3, 5, 7) which are all primes from 1 to   10. And I think if you would write that loop in english, it would be

```

loop 
x from 1 to 10 
and collect x when x is prime

```

Almost the same thing? :)

/Lau

---

### Post by nvteighen on 2008-05-31
> **Npl said:**
> The building "grammatical" blocks of languages (eg types, variable names, for, do-while, blocks, etc)are defined in their specifications and it doesnt make sense to go lower than that.

You understood more than what you think!

The issue is that **for** does has "some" meaning for a human ("here begins a for-loop"), and the "o" letter (there are no phonemes here...) may actually making the difference to a variable called "fur". But **for** is useless for a C compiler, which understands **for(i=0;i<333;i++)**. So what is actually the first meaniningful level? The human's or the compiler/interpreter's?

I believe we can go lower level... (interesting way to express it).

---

### Post by Wybiral on 2008-05-31
I think I read things conceptually. When I see cout/print/printf/puts/echo I don't think about the word or letters. I just look at it, access my hashtable/dict/map of programming concepts and they all map to practically the same thing to me. If a new language used "pront", I would adjust very quickly once I added that to my hashtable :)

Like, I don't program in C++, but just looking at something like this, my brain puts the pieces together without thinking based on my conceptual knowledge of the information.
```

ixt mxxn(ixt axxc, cxxr** axxv)
{
    cxxt << "Hxxxo wxxxd!" << exxl;
    rxxxxn 0;
}

```

So with all concepts that languages share, typically being some kind of input and output concepts that most languages have in common, it all looks and even "feels" the same to me, it's only the unique concepts that I tend to "feel" different about. Like lambdas, or Lisp macros... Those concepts are essentially 100% non-existent in languages like C and C++, nothing in them semantically feels anything like lambdas or macros, and probably never will.

Even though C macros are called "macros", they have a completely different meaning from Lisp macros, despite being conceptually similar (altering the source code at some "compile time"), the key factor in that Lisp code is also Lisp data, and "compile time" is also runtime.

---

### Post by nvteighen on 2008-05-31
> **Lau_of_DK said:**
> 
```

(loop 
  for x from 1 to 10
  when (prime? x)
  collect x)

```

```

loop 
x from 1 to 10 
and collect x when x is prime

```

Almost the same thing? :)

Here is something really interesting! (to me, at least). In English "when..." could be placed elsewhere (before "loop" inclusive) and the whole sentence wouldn't be really affected. Human can process syntax between structures that are not in contact; computers can't, so the **when(prime? x)** must be before the **collect x**!

---

### Post by nvteighen on 2008-05-31
> **Wybiral said:**
> I think I read things conceptually. When I see cout/print/printf/puts/echo I don't think about the word or letters. I just look at it, access my hashtable/dict/map of programming concepts and they all map to practically the same thing to me. If a new language used "pront", I would adjust very quickly once I added that to my hashtable :)

So, in your opinion, it is the instruction and specification-construct which defines the most basic meaning... The same as NPL says. If a new specification is created where "pront" is used, you take it and process new information with that new "dict" entry...

> Like, I don't program in C++, but just looking at something like this, my brain puts the pieces together without thinking based on my conceptual knowledge of the information.
```

ixt mxxn(ixt axxc, cxxr** axxv)
{
    cxxt << "Hxxxo wxxxd!" << exxl;
    rxxxxn 0;
}

```

Yeah, but tell g++ to compile that and see what happens. There's the funny thing: the code is processed differently by a human than by a computer. And it's still the same language!

> So with all concepts that languages share, typically being some kind of input and output concepts that most languages have in common, it all looks and even "feels" the same to me, it's only the unique concepts that I tend to "feel" different about. Like lambdas, or Lisp macros... Those concepts are essentially 100% non-existent in languages like C and C++, nothing in them semantically feels anything like lambdas or macros, and probably never will.

Even though C macros are called "macros", they have a completely different meaning from Lisp macros, despite being conceptually similar (altering the source code at some "compile time"), the key factor in that Lisp code is also Lisp data, and "compile time" is also runtime.

And that's because C, C++, Lisp have been defined that way. Notice that you're relating different programming languages basing yourself on what differences they have. It's the same reasoning when you learn a foreign language: why does Spanish have a subjunctive tense and English not?

I'm taking notes (not literally!). I wanted to hear opinions and also see how programmers approach to these topics. I myself don't have a solid opinion, just a bunch of intuitions and loose ideas, all from a linguist-wannabe's point of view, not a programmer's.

---

### Post by LaRoza on 2008-05-31
> **nvteighen said:**
> So, are we humans which finally give meaning to programming languages from the outside? But the interpreter/compiler does have a part on this, of course... that would mean the language retains meaningful structures by itself... If so, where is the meaning?

Well, humans have designed computers to be binary based (it wasn't always like this, or even neccessary, just the easiest way).

Computer languages are just human abstractions on top of the computer, see CptPicard's sig (if he hasn't changed it).

The rules of a language can be very different. For example, in Haskell:
```

 z = y + 3
 y = 10

```

That makes sense in haskell, whereas the typical imperative programmer would say that doesn't make sense. 

In Fortran, a "while" loop doesn't exist (I am going by Fortran 77).

For a function I have in Fortran, I have:

```

 10   if (g .gt. 1) then
            i =  i * (g-1)
            g = g -1
            goto 10
        endif    


```

which is very different in many ways from other common languages.

In brainfuck, the entire language is a different concept. A while loop is just the openning "[} and is closed by "]" and it ends when the pointer equals 0.

In short, computer languages and even the hex codes and "1"s and "0"s are for humans. A computer represents data in ways with which humans can't really work.

---

### Post by Wybiral on 2008-05-31
> **nvteighen said:**
> Yeah, but tell g++ to compile that and see what happens. There's the funny thing: the code is processed differently by a human than by a computer. And it's still the same language!

Ok, well when we bring in the computer, it's like trying to communicate with other human beings. I can know that I like a certain shade of blue, but I can't necessarily convey that shade to you unless we have a common experience to work from. "int" is a common experience with the compiler, but that doesn't mean that I have to think the same thing as the compiler when I see "int", or that I have to call it "int" at all. The concept is important to me, but I see where you're going WRT the compiler... It's like trying to communicate with an idiot, you have to speak in terms they will understand (but that doesn't mean I have to think about my problem like an idiot).

> **nvteighen said:**
> And that's because C, C++, Lisp have been defined that way. Notice that you're relating different programming languages basing yourself on what differences they have. It's the same reasoning when you learn a foreign language: why does Spanish have a subjunctive tense and English not?

I see what you're saying, but in verbal languages we can eventually reconstruct the concept in the other language (there's very little that can't be translated afaik). And it's true that you can reconstruct your program from Lisp in C, but it's not true that you can reconstruct the *concept* of a lambda or a macro in C... It doesn't posses the means of representing those concepts (and thus, while programming, it's impossible to think in terms of those concepts).

---

### Post by pmasiar on 2008-05-31
Kids, please go to another room to argue if C# is better than Java, or if scripting language are toy or real or something - adults will get glass of wine and talk about issues not for your ears :-) Your mind might hurt, so go, and close the door.

Thanks for starting interesting discussion, 
nvteighen. I am not sure how much CompSci education you have? Computer languages are context-free, unlike human languages, which have context. Remember grammars? Remember [http://en.wikipedia.org/wiki/Chomsky_hierarchy](http://en.wikipedia.org/wiki/Chomsky_hierarchy) of grammars?

'While' or any other term might be even consisting from other letters, or non-letters. [APL](http://en.wikipedia.org/wiki/APL_%28programming_language%29) was famously a language with many (way too many) special symbols. Another bad experience I had was MSFT Excel, for 'convenience' translated to another languages, including keywords in macros. Was supposed to be more user friendly, but was totally unusable and flop (ppl bought it only by mistake): people smart enough to be able to write macros, were smart enough to learn 30-50 English keywords, and most of them already knew them - and old macros, spelled in English, did not work at all.

It would be not too hard to program in a language where keywords would be in Hebrew, Chinese or Hindi. If they would be easy to distinguish, not a big deal after a week or so. Or did you ever heard of [Lingua  Romana Perligata](http://www.csse.monash.edu.au/~damian/papers/HTML/Perligata.html) - flavor of Perl in classical Latin?

Edit: Of course I should have mentioned [PerlMonks article about LRP](http://www.perlmonks.org/?node_id=253797). It shows how flexible Perl (or Latin) can be: 

> 
$var = 8; would be expressed as...

varo VIII da.    # or 'da varo VIII' or 'da VIII varo' or...

(or "meo varo VIII da." if you're using strict - guess what 'meo' is :)

Start reading and following links [http://en.wikipedia.org/wiki/Semiotics](http://en.wikipedia.org/wiki/Semiotics) - I'll be back :-)

---

### Post by CptPicard on 2008-05-31
this is a great topic that will get a long post from me tomorrow when i am at keyboard but can not type properly right now from phone. Watch this space.

---

### Post by LaRoza on 2008-05-31
> **CptPicard said:**
> this is a great topic that will get a long post from me tomorrow when i am at keyboard but can not type properly right now from phone. Watch this space.

There's his sig I was talking about. (Never knew it would have a fan though)

---

### Post by robheus on 2008-05-31
> **nvteighen said:**
> Motivated by pmasiar in another thread ([http://ubuntuforums.org/showthread.php?t=752513&page=8#post5081429](http://ubuntuforums.org/showthread.php?t=752513&page=8#post5081429)), let's discuss some features programming languages have in contrast to natural languages!

I've been doing some informal observations on how programming languages reflect features present in natural languages. And also how programmers sometimes end up discussing Linguistics without noticing it (as I said in the other thread, the "best programming practices" are pragmatical discussions).

A topic I'm very interested currently on is where does "meaning" rely on programming languages. Using the same example I used in the other thread, for the C statement **while(1)**, what does define its meaning: The letters w-h-i-l-e (we can't speak of phonemes here as in natural languages)? The word "while"? The whole statement "while(1)"? Or is it the whole while-loop it declares?

For the English word "while" you have two layers of undivisable units that mark semantic differences (Saussure's "Double Articulation" principle): 1) the phonemes: if you just shorten the /i/, you get "will", another different word! (forget spelling, focus on pronounciation). 2) The monemes: in this case, the whole word "while" which undoubtly also is a unit in its own compared to e.g. "sadness".

But in programming languages, you have a problem. Python's **print "A"** does mean something by its own, but neither "print" nor "A" really mean something by themselves separated. And you could theorically declare a variable **pront = 8**, where **print pront** does make sense, but **pront "A"** doesn't, no matter how valid information "pront" (if properly declared) actually is for the Python interpreter.

So, are we humans which finally give meaning to programming languages from the outside? But the interpreter/compiler does have a part on this, of course... that would mean the language retains meaningful structures by itself... If so, where is the meaning?

Any thoughts? (If you actually understood anything of this... Maybe I'm being more esoteric than Lisp-hackers?? :p)

The "meaning" of a "program" is defined by it's grammatical (and lexical) rules, which map a textual representation of the program onto the instruction set and other characteristics of the target computer on which the program runs.
You can't distinguish those two, neither as you could distinguish a binary representatio from it's context: the same sequences of bits have different meaning in different contexts (such as: a character, an integer, a instruction, etc.)

---

### Post by pmasiar on 2008-05-31
Hey guys, if you want to talk here with adults, don't behave like noobs :-) **If you quote, trim,** and leave only relevant parts of what you want to answer

---

### Post by nvteighen on 2008-06-01
...and after some struggling with my router... I'm back)

@CptPicard: I'll be watching for your post.

@pmasiar:
No formal CompSci, at all. I'm a Philology student, but of the Linguistics branch, not Litterature.

@all:
Reading your posts, I think there's an interesting point we agree on: That "meaning" in programming languages is dynamic and may be defined at coding time.

Programming languages (and maths as well), as pmasiar says, are context-free in the sense that there are no implicit external information that is used to actually interpret the code. That's why everything has to be declared somewhere.

Can we say, then, that those declarations do define a context? That would "solve" the case of a variable called "zzz" in a given program and another one where "zzz" is a function or another one where it simply doesn't exist and thus, means nothing.

That leads to the Perligata example, which is actually impressive; you must never forget that that's actually Perl, but you can redefine it "along the way" and make it look at that. If you try that into a 

As computers work on human abstractions, it is the abstraction performed which defines what is "able to have sense" and what not in a programming language. Some things have a meaning by their own (I'm thinking on reserved keywords, e.g.), but others seem to be defined by how sense (according to specification and context) does the use of that object make.

In C, you might declare a variable called "malloc" in a program where stdlib.h is not included. If you happen in that case to write **int *a = malloc(sizeof(int));**, that won't do any sense because *in this program* "malloc" is a variable, not a function, no matter how correct C syntax that is.

But, what serious programmer will call a variable "malloc"? Possibly no one, whether you had included stdlib.h or not, because in the "community", "malloc" is associated to the heap allocation function.

Anyway, you guys are better linguists than you even imagine!

---

### Post by LaRoza on 2008-06-01
> **nvteighen said:**
> 
But, what serious programmer will call a variable "malloc"? Possibly no one, whether you had included stdlib.h or not, because in the "community", "malloc" is associated to the heap allocation function.


After toying with the idea of keeping the entire quote just to see pmasiar's reaction, I decided against it.

I would. Actually, I wouldn't, but I almost always use variables named after functions in all my C programs. The variable is in the function whose name it shares and is the return value in many functions. This keeps multiple returns out, and easily followed logic in.

---

### Post by Bichromat on 2008-06-01
> **LaRoza said:**
> After toying with the idea of keeping the entire quote just to see pmasiar's reaction, I decided against it.

I would. Actually, I wouldn't, but I almost always use variables named after functions in all my C programs. The variable is in the function whose name it shares and is the return value in many functions. This keeps multiple returns out, and easily followed logic in.

This is exactly what happens when you define a fortran function :)

```

double precision function square(x)
double precision :: x

square = x**2

end function square

```

---

### Post by LaRoza on 2008-06-01
> **Bichromat said:**
> This is exactly what happens when you define a fortran function :)


I know, my email isn't "LaRoza77" for nothing (that is where the 77 originates)

---

### Post by nvteighen on 2008-06-01
> **Bichromat said:**
> This is exactly what happens when you define a fortran function :)

```

double precision function square(x)
double precision :: x

square = x**2

end function square

```

Never dealt with Fortran before... expect breakage :p

Here we get the same point, I think: the meaning of that makes sense in Fortran because the abstraction behind I guess is: "A function returns the value stored in it as variable" (or something like that; I repeat: never even saw Fortran before). So, the context of "square" (variable) is "square" (function)... in (Fortran's equivalent to) main(), you won't be able to use "square" for a variable, I guess.

The meaning of "square" in each case seems to be defined by the use, as the specification regulates what can be used and what not... and afterwards, if it compiled, that the code worked. Why it seems to me this not that different to what natural languages do?

---

### Post by LaRoza on 2008-06-01
> **nvteighen said:**
> Never dealt with Fortran before... expect breakage :p

Here we get the same point, I think: the meaning of that makes sense in Fortran because the abstraction behind I guess is: "A function returns the value stored in it as variable" (or something like that; I repeat: never even saw Fortran before). So, the context of "square" (variable) is "square" (function)... in (Fortran's equivalent to) main(), you won't be able to use "square" for a variable, I guess.

The meaning of "square" in each case seems to be defined by the use, as the specification regulates it... Why it seems to me this not that different to what natural languages do?

Fortran 77 is very simple. It uses pointers in a way that would confuse C programmers, because you don't have a choice. Everything is passed by reference, and the declared type of a function is also a variable that is returned (if you think about it, it makes sense. If you declare C's main() as int, but do not actually return an int, there is a problem logically)

---

### Post by Bichromat on 2008-06-01
> **LaRoza said:**
> I know, my email isn't "LaRoza77" for nothing (that is where the 77 originates)
Yes, I've seen some F77 codes from you (in the topic about factorialsfor example). Do you still code regularly in F77 ? If so, why not f90/95 ?

> **nvteighen said:**
> Here we get the same point, I think: the meaning of that makes sense in Fortran because the abstraction behind I guess is: "A function returns the value stored in it as variable" (or something like that; I repeat: never even saw Fortran before). So, the context of "square" (variable) is "square" (function)... in (Fortran's equivalent to) main(), you won't be able to use "square" for a variable, I guess.

Yes, it makes sense and it is a nice way to identify the return value. And you guessed right, you can't redefine "square" if it's already known to the program unit you're into (the main program, a module, a function, a subroutine).

---

### Post by LaRoza on 2008-06-01
> **Bichromat said:**
> Yes, I've seen some F77 codes from you (in the topic about factorialsfor example). Do you still code regularly in F77 ? If so, why not f90/95 ?


What is the point in using the oldest used language with modern features? Honestly. If I wanted all the new Fortran features, I wouldn't be using Fortran.

(Using/learning Fortran 77 was a learning experience of mine)

---

### Post by Bichromat on 2008-06-01
> **LaRoza said:**
> What is the point in using the oldest used language with modern features? Honestly. If I wanted all the new Fortran features, I wouldn't be using Fortran.

(Using/learning Fortran 77 was a learning experience of mine)
Because it is nicer to use. You learned it just for the sake of it, but when you want to do serious things in fortran, it's better to have while loops :D

---

### Post by LaRoza on 2008-06-01
> **Bichromat said:**
> Because it is nicer to use. You learned it just for the sake of it, but when you want to do serious things in fortran, it's better to have while loops :D

[http://www.pbm.com/~lindahl/real.programmers.html](http://www.pbm.com/~lindahl/real.programmers.html)

---

### Post by pmasiar on 2008-06-01
> **nvteighen said:**
> No formal CompSci, at all. I'm a Philology student, but of the Linguistics branch, not Literature.

You may not know that one of the titans of open source, creator of Perl language [Larry Wall](http://en.wikipedia.org/wiki/Larry_Wall) studied linguistic with goal to go to jungle, find unknown tribe, learn language and create writing system for it (and translate Bible). Maybe that's why Perl is so flexible (maybe too much) what you can write poetry and haiku in it.

Thinking about it, we have first original free language (not reimplementation of any old: Perl) and first high-level scripting language for serious applications, because Larry developed food allergy to eggs and wheat. What irony!

---

### Post by CptPicard on 2008-06-01
Ok, so now I'm back from my nice weekend at summer cottage... had some time to actually reflect on this topic while I was looking at the lake with beer in hand :)

10 years ago when I was wondering what to go study I was much more of a language and humanities geek than a mathematics geek. I ended up in CompSci by half-accident, which turned out to be a lucky accident... it was remarkable to over the years realize how deep the underlying concepts of CS go if you really think of them. Syntax vs. semantics, decidability of sentences, and the descriptive/operational nature of programming languages as mechanically manipulatable symbolic systems that map to real-life problem structures have required a lot of deep thought from a lot of really smart people over the years.

Programming languages are systems that either describe an abstract process (imperative languages) or the outcome of the process and the structure of its building blocks (declarative languages). Its roots are in logic, and the issue of "where does semantics reside" was, at the start of last century, a major issue. It was hoped that by mere syntactic manipulation by "mechanical" (read: algorithmic) means would yield a hands-off procedure for deciding the truth of any given sentence.

Of course, this wasn't doable. Remarkably, Gödel showed that there are sentences that are not provable in any resonably strong, consistent logical syntactic system, but which *we can still see to be true* (therefore, the system is necessarily always incomplete). This is a result that has deep implications for things like theory of mind and artificial intelligence... apparently it seems like the human mind has access to some sort of semantic information that is not inherent in the symbols themselves. Or, alternatively, the more hopeful strong-AI proponents suggest, there ARE Gödel sentences for the human mind, but we're still able to see the incompleteness of logics in general.

As far as theory of mind goes, there is something interesting to ponder for the naturalist... Gödel's result seems to apply to all "mechanically computed" (i.e. crunched by naturally occurring devices) logics. But then if the human mind is not a Turing machine, then what is exactly is there in the mind that allows us access to semantics that allow us to break free from the rather strong limitations that seem to be implied by Gödel's result and subsequent computability results by Turing?

To address the questions of the OP more directly... programming languages are ways to map problems into descriptions of machine-computable logic. Sometimes you can map symbols meaningfully to the problem so that you can get a result, sometimes you can't (see halting problem).

A charming feature is Turing-completeness... all the languages are equivalent as soon as they become strong enough. Interestingly, at the human-machine interface, this equivalence means that as far as the machine is concerned, it really doesn't care which representation you choose, but on the other hand, for the human mind, certain representations map the given problem in a more "natural" fashion. And this is where we get to the point I always preach to the "C is all you need because it's closest to the hardware" n00bs -- different representations give you different insights into possible descriptions of the problem, and *some of those descriptions show you more useful sides of the structure of the problem in question* in a way that your mind is able to apply itself to exploiting this said structure in finding a better algorithmic solution -- and this is where the mind really is often needed -- there is no general mathematical theorem prover, and there is no thus general automatized programming program.

You could brute-force program in assembly all your life and not make your mind see the actual problem through appropriate goggles that actually lets the "linguistic-rational" combination of your mind to speak to itself about it in terms that yield revelation.

So, I really prefer to take a very high level view of programming languages as various descriptions of processes and computable things. They allow you to put your mental finger on computability as an inherent part of the universe, for as deep as it goes... computability is out there in the objective reality as far as the old sort-of Newtonian deterministic-mechanistic picture of the universe goes, and that's a big part of it. Stephen Wolfram went crazy over cell automata as prititive Turing-complete computation devices and wrote a whole ranting book on hypothetically basing ALL science on them (A New Kind of Science). :)

The limits are somewhere there in external semantics, if any, (read about Searle's Chinese Room for a really good discussion of syntax vs. semantics), and as far as nature goes, determinism... (what are the implications of quantum computing? See Roger Penrose's "Emperor's New Mind" and "Shadows of the Mind").

---

### Post by maximinus_uk on 2008-06-01
Here I was about to give some nuanced inside look into the logical aspects of the Chinese language when CptPicard writes pretty much exactly the post I really wanted to write.

The only minor point I'd add is that human language is not expected to be True or False any any given point, whereas that is a standard which we enforce on our code. Programming languages exist to be precise, whereas human languages can be much less rigid since we know the listener really does have a proper AI to work out what we mean.

---

### Post by CptPicard on 2008-06-01
> **maximinus_uk said:**
> Programming languages exist to be precise, whereas human languages can be much less rigid since we know the listener really does have a proper AI to work out what we mean.

Some things that relate to this... as pmasiar pointed out, human language is context-sensitive, and our sensitivity to the "context" is indeed something that has to do with the external semantics that we have easy access to. In particular we seem to be almost magically able to tell what is relevant in some given context, but in AI logical inference systems, we run into nastiness such as the [frame problem]("http://en.wikipedia.org/wiki/Frame_problem").

Now, if we try to isolate stuff from external context as much as we possibly can, finally achieving complete substitutability, we get pure-functional programming, which has all kinds of nice properties as far as compilers and distributed and multithreaded computing goes, among other things.

---

### Post by Bichromat on 2008-06-01
Maybe programming languages are more comparable to constructed languages (Esperanto, Ido), as they are designed to keep exceptions to a minimum.

---

### Post by nvteighen on 2008-06-01
> **CptPicard said:**
> Ok, so now I'm back from my nice weekend at summer cottage... had some time to actually reflect on this topic while I was looking at the lake with beer in hand :)

That's life! Today I had to fight against my router, the most idiot device I ever met... it doesn't handle DNS queries as it should, so it gets quickly confused when more than one computer is connected. And then, struggled to install a bamboo-fence in my mother's garden, which probably won't stand the storm that is announced for this days.

> To address the questions of the OP more directly... programming languages are ways to map problems into descriptions of machine-computable logic. Sometimes you can map symbols meaningfully to the problem so that you can get a result, sometimes you can't (see halting problem).

(...). Interestingly, at the human-machine interface, this equivalence means that as far as the machine is concerned, it really doesn't care which representation you choose, but on the other hand, for the human mind, certain representations map the given problem in a more "natural" fashion. (...)

According to this, you could define two layers of communication when writing a code: the internal machine layer and the human-machine. It's pretty clear that for the machine, what it's important is to follow the instruction and spit out some result... maybe we can't call that communication... The human-machine, is the way we tell the machine to process the data, using a certain system of symbols (that's the formal definition of language for [Coseriu]("http://en.wikipedia.org/wiki/Eugenio_Co%C5%9Feriu")).

But also, we can add a third layer: human-human. Programming languages are written by humans for human use, and code is also read by humans... There we get standards, "best programming practices", etc. You can't (at least for now), load a C program into someone's brain and expect him to execute it... But, you can expect someone to understand what the code does.

What I'm ultimately concerned about is to describe that symbols for the human-machine and human-human interfaces in a non-language specific way.

This is being a very interesting thread... far more interesting than the overrepeated "Python vs. Perl vs. Assembly vs. XHTML" ones :p.

---

### Post by CptPicard on 2008-06-01
> **nvteighen said:**
> And then, struggled to install a bamboo-fence in my mother's garden, which probably won't stand the storm that is announced for this days.

Such is nature. We had to unfortunately struggle for survival with birds who had decided to build a total of three nests right on top of the beam that supports the cottage's roof over our terrace. Fortunately they didn't have eggs in yet, because, obviously, they lost. :)

We also have a [Common Merganser]("http://en.wikipedia.org/wiki/Common_Merganser") (had to look that one up) [living with its kids]("http://ubuntuforums.org/album.php?albumid=218") right at the water's edge... it's a small miracle she doesn't just sink when all of the kids are trying to hitch a ride on her back at once... :)

But that's OT, just thought to post the pics.. ;)

> According to this, you could define two layers of communication when writing a code: the internal machine layer and the human-machine. It's pretty clear that for the machine, what it's important is to follow the instruction and spit out some result... maybe we can't call that communication...

Yes... and the really great part is that, fortunately, the machine really doesn't care. You can't make it "go any faster" in principle by switching representations, and any comfortable representation for *you* the human can always be made processable by the computer.

I wish more people really appreciated the fact that algorithms are separate from the machine except in the very abstract sense...


> But also, we can add a third layer: human-human. Programming languages are written by humans for human use, and code is also read by humans...

This is one of the guiding principles of Python actually... to make the code readable for humans, both for others than the coder and the coder himself 3 years from now.

It all boils down to seeking to express the abstractions relating to the problem in a human-brain-comfortable way... and I have this sense, being the sort of Platonist regarding mathematics that I am, that there is also something inherently correct then in the way it not only fits the brain, but the problem too. After all, it is then in a form where the brain is able to do its magic, tweaking the problem into a more tractable form...


> 
What I'm ultimately concerned about is to describe that symbols for the human-machine and human-human interfaces in a non-language specific way.

Your non-language specific way is probably found somewhere in a way to describe algorithmic processes, then, in a most generic way possible. Discrete mathematics comes to mind. :)

> This is being a very interesting thread... far more interesting than the overrepeated "Python vs. Perl vs. Assembly vs. XHTML" ones :p.

Yeah, considering it's obvious that Emacs and Lisp win... ;)

---

### Post by Lau_of_DK on 2008-06-01
> 
This is being a very interesting thread... far more interesting than the overrepeated "Python vs. Perl vs. Assembly vs. XHTML" ones . 
> **CptPicard said:**
> 
Yeah, considering it's obvious that Emacs and Lisp win... ;)


Haha, its funny cause its true! An instant classic.


/Lau

---

### Post by slavik on 2008-06-01
Question to the OP, are you trying to compare languages specifically created to be translated by humans into binary logic of which none is over 50 years old to languages that have evolved and changed over centuries?

Here's an easy one: English. English is a German and Latin base with lots of Greek, Spanish, Italian and French thrown in. The language used by Shakespeare in 1600 is modern English (I am sure there more of a dialect difficulty than actual language difficulty when Americans read Shakespeare and also he extensive use of metaphors). If you want to see Old English, read Beowulf, the original transcription. The writing used there is pretty much the writing I remember using in school (in Ukraine) to write down pronunciation of English words.

The only natural language that was specifically invented by people is Esperanto.

If you want to compare a computer language versus a natural language, you might want to pick up some Esperanto. Not only that, you also have to understand that programming languages are written so that they could be parsed by binary logic in which we use a yet another language which ultimately boils down to logic gates.

Before you were talking about what 'while(1)' means. Let's for a moment change that '1' to 'work needs to be done.' Now, imagine that somewhere in the middle of the loop, all work is done, in a natural language, you would follow the instructions and check whether there is work that needs to be done after every step of the instructions. In computers though, it will carry on until the end of instructions and then check if there is works that needs to be done. There are also those time when we understand what the person wants without him saying it. (Do what I mean, not what I say). Think of every time you discussed a pretty girl you were next to with your friends using your own language without telling your friend what you are saying and him (or her) understanding you without you telling your friend what is going on.

Computers cannot and will never be able to intelligently infer context (we might be able to write software that will be able to do it, but putting that on a circuit board will be impossible IMO).

---

### Post by LaRoza on 2008-06-01
> **slavik said:**
> 
The only natural language that was specifically invented by people is Esperanto.


(About english, don't forget the one Finnish word that is used, Sauna)

Sorry to burst your bubble: [http://en.wikipedia.org/wiki/List_of_constructed_languages](http://en.wikipedia.org/wiki/List_of_constructed_languages)

---

### Post by slavik on 2008-06-01
> **LaRoza said:**
> (About english, don't forget the one Finnish word that is used, Sauna)

Sorry to burst your bubble: [http://en.wikipedia.org/wiki/List_of_constructed_languages](http://en.wikipedia.org/wiki/List_of_constructed_languages)
I stand corrected, but I do not really count languages created for entertainment. I would change that sentence to major natural languages in the wikipedia list to which a link has been kindly provided by LaRoza. :)

The main point still stands though. :)

---

### Post by LaRoza on 2008-06-01
> **slavik said:**
> I stand corrected, but I do not really count languages created for entertainment. I would change that sentence to major natural languages in the wikipedia list to which a link has been kindly provided by LaRoza. :)

The main point still stands though. :)

I just misread your statement "I do not really count languages created for entertainment". I read it as meaning you don't actually think it is entertaining to count created languages, and thought you were saying I do...

Well, we all know that if we can nitpick at trivial matters, it will discredit the entire point.

---

### Post by pmasiar on 2008-06-01
> **slavik said:**
> The only natural language that was specifically invented by people is Esperanto.

You might be interested in [http://www.slovio.com/](http://www.slovio.com/) - which is much easier to learn for non-Slavic people than any other "natural" Slavic language, and trivial to understand for Slavic people without learning.

---

### Post by slavik on 2008-06-01
> **pmasiar said:**
> You might be interested in [http://www.slovio.com/](http://www.slovio.com/) - which is much easier to learn for non-Slavic people than any other "natural" Slavic language, and trivial to understand for Slavic people without learning.
Holy crap!!! I was reading that page (the Slovia part) as if it was Polish/Serbian ^^

---

### Post by Verminox on 2008-06-02
Well I am rather confused by the Original Post but all I have to think about it is.... Programming languages are context free, and all their behaviour is (mostly) well defined, because they were created to serve an unambigious purpose. On the other hand, many natural languages are contexual, and they have been formed from years of usage of various vocabulary by different types of people, each person with his/her own characteristics and own views on what should be added to the language. In the end, natural languages are often much more confusing and harder to learn or extract meaning from than programming languages, which were created by humans (often one human, or a team of humans with similar mindsets) with the sole purpose of allowing the user of the language to convey meaning to a computer (or compiler or interpretter).

Now what is this meaning that is conveyed to the computer? That was your original question I believe.... According to me, a major difference is who the meaning stems from. 

In natural languages, it is the *observer* who has the job of extracting meaning. The observer can extract the same meaning from two tottally different sentences or extract different meanings from the same one. Also, it depends on the ability of interpretation, mindset, context and linguistic knowledge of the observer.

In computer languages, it is the *programmer* who has the job of getting the meaning right. The observer, that is, the computer, has a well defined set of rules to respond to messages (commands). If the programmer misunderstands the programming language or forgets the syntax it is his/her fault that the message was not sent correctly.

Well, my thoughts are mainly focused on the communication part of languages, so it may be different from what you were expecting.

---

### Post by ankursethi on 2008-06-02
They might not be perfect, but AI systems do exist which can, given a sentence, parse it and infer some meaning from it (provided the input is grammatically correct and does not make use of metaphors or other figures of speech).

So, one could probably replace :
*File = open("1337.txt")*
by the more easily understood :
*Open the file named "1337.txt" and call it "File".*

An advanced AI system would probably be able to understand it. But does it know "how" to open the file? Probably not, so it would have to be trained to do so. Now look at this :
*Open file "1337.txt". Find the serial number for "Microsoft Windows Vista Ultimate" and E-mail it to Wendy on her GMail address.*

Now the AI is stumped because it doesn't know what a serial number is. Even if it did know what it was, it would have to infer from context the particular serial number for WinVista. What if in 1337.txt, the serial number was written as :
*d00dz!! teh serail 4 Vista is xxxx-xxxx-xxxx-xxxx!*
A human can infer it, but an AI can't. And what about Wendy's email? Is it in the address book? In the user's GMAil contacts? Stored in a text file somewhere on disk?

Now, let's talk about a 10 year old. I was going to say a 6 months old baby, but that would be too unrealistic. You tell the kid to burn an Ubuntu ISO then create a new XFS partition for /home and a ReiserFS partition for /, install the system, update it, install the drivers and be back in an hour to do another machine. Everyone here (I presume) knows how to do this. But a 10 year old might not.

So, neither the AI nor the 10 year old can do what it/he doesn't know how to. The 10 year old's powers of inference, too, are useless here. But if you tell this kid to read and understand the following sentence :
yo!1! i haz nu dvb. mah place at 7. popcorn.
he would probably be able to decipher it.

How? From context, you say. Very true. But then why couldn't he decipher the Ubuntu deal?

I suppose a programming language is simply a compromise between a human and a computer. We teach the computer a couple of basic things ("behaviours"), and then piece them together as a program. We could, in theory, teach the computer an unlimited number of things such that it can find the Vista serial number in 1337.txt, but in reality that would not be possible. The task is inefficient and cumbersome (for some people) and prone to design errors (since what we are doing is pretty much like making a Lego building). But it helps us communicate with the computer.

I don't thing a computer language has a liguistic element to it. It's simply a notation that depends on the designer's fancy. Some notations may be more flexible than others. Some may have a larger set of "behaviours" for the computer to respond. But, in the end, it's all a compromise. In C, you might not be able to find out whether a function is defined or not, but in Ruby you can do "defined? VARNAME".

(Sorry if all that didn't come out very well. I don't have CS education, nor linguistic education. I'm just out of high school and, 3 months back, I didn't even know what a Turing machine *is*.)

---

### Post by Wybiral on 2008-06-02
> **ankursethi said:**
> ...

I'm afraid it goes beyond that... There's way too much ambiguity in human languages to trust a computer to do something with it. How many times have you heard "oh, I thought you meant..." or "oh, I'm sorry, I misunderstood you..."

It's common, because our languages are vague. A classic example in the field of translation (and AI comprehending human language is a form of translation)

[URL="http://en.wikipedia.org/wiki/Literal_translation#Mistranslations"]"The spirit is strong, but the flesh is weak"
Translated to Russian, then back to English:
"The vodka is good, but the meat is rotten"
[/URL]

Interestingly, the problem isn't the technology... The problem is our languages!

---

### Post by pmasiar on 2008-06-02
Interesting insight what Guido van Rossum (creator of Python) had was: 

1) programs are for communication between people at the first place, and computers only at second place. So it should be optimized for humans, not computers.

2) Program code is much more often read than written, so it should be optimized for reading, not writing.

Interesting that it took almost 50 years of creating programming languages to get that insight :-)

---

### Post by slavik on 2008-06-02
> **pmasiar said:**
> Interesting insight what Guido van Rossum (creator of Python) had was: 

1) programs are for communication between people at the first place, and computers only at second place. So it should be optimized for humans, not computers.

2) Program code is much more often read than written, so it should be optimized for reading, not writing.

Interesting that it took almost 50 years of creating programming languages to get that insight :-)
and yet, you still have to put comments into Python code ...

What you are missing is that when we read code, we are trying to understand the writer's thought process, what he wrote is not as relevant. "Do what I mean, not what I say."

---

### Post by nvteighen on 2008-06-02
> **slavik said:**
> Question to the OP, are you trying to compare languages specifically created to be translated by humans into binary logic of which none is over 50 years old to languages that have evolved and changed over centuries?

Yes and no. Trying to compare to specific languages is absurd: what is valid in English may not be valid in Polish. I want to see how much does "general linguistics" fit in programming languages, caring in the "human language" not in "tongues" (French: "language" vs. "langue"; standard English "language" is too ambiguous).

> The only natural language that was specifically invented by people is Esperanto.

It's absolutely artificial, non-sensical, absurd,... You may never hear me flame against a programming language, but yes against Esperanto and other similar constructs. ;)

> Before you were talking about what 'while(1)' means. (...)

Computers cannot and will never be able to intelligently infer context (we might be able to write software that will be able to do it, but putting that on a circuit board will be impossible IMO).

That's right. I think we all seem to agree on how the computer interprets the code (the "machine interface"); I'm mostly focused on the "human-machine".

> **ankursethi said:**
> 
Now, let's talk about a 10 year old. I was going to say a 6 months old baby, but that would be too unrealistic. You tell the kid to burn an Ubuntu ISO then create a new XFS partition for /home and a ReiserFS partition for /, install the system, update it, install the drivers and be back in an hour to do another machine. Everyone here (I presume) knows how to do this. But a 10 year old might not.

So, neither the AI nor the 10 year old can do what it/he doesn't know how to. The 10 year old's powers of inference, too, are useless here. But if you tell this kid to read and understand the following sentence :
yo!1! i haz nu dvb. mah place at 7. popcorn.
he would probably be able to decipher it.

Today, we've seen some of these in class. There we get on Grice's maxims, but I really don't fully understand them yet. The basic idea is that any information given to someone implies some cooperation principles; a 10-year old can't cooperate on that... a computer can (tell gparted to create a ReiserFS partition, mount it to /, etc...)

> I don't thing a computer language has a liguistic element to it. It's simply a notation that depends on the designer's fancy. Some notations may be more flexible than others. Some may have a larger set of "behaviours" for the computer to respond. But, in the end, it's all a compromise. In C, you might not be able to find out whether a function is defined or not, but in Ruby you can do "defined? VARNAME".

Well, if they're languages, they should have a linguistic element! The formal definition of language is "any system of signs" (damn, I don't have my bibliography at hand). A notation system tries to represent something, so it has signs. "Mesa" in Spanish refers to the same as "table" in English. Natural languages refer to objects in reality (may it be material or abstract); computer languages refer to objects in the computer... But they still, 

> (Sorry if all that didn't come out very well. I don't have CS education, nor linguistic education. I'm just out of high school and, 3 months back, I didn't even know what a Turing machine *is*.)

I don't have any CS education, so don't worry :)!

---

