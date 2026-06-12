---
title: "What is the best programming language FOR"
date: 2009-11-17
forum: Programming Talk
---

### Post by akvino on 2009-11-17
What is the best programming language FOR Linux system and application programming. So it has to be fast, it has to be readable, it has to be able to GUI from time to time, it has to be able to program web, it has to be able to execute scripts, it has to be good with ascii files?

---

### Post by jpeddicord on 2009-11-17
I'm going to say Python - but "best" is really subjective, and everyone has their own preferences.

I say Python because you mention scripting -- C/C++/Mono/Java must be compiled before being used, where as Python can be interpreted directly.

Take a look at a few languages and see what you like best. Check out the stickies in this forum for more info.

---

### Post by Arndt on 2009-11-17
> **akvino said:**
> What is the best programming language FOR Linux system and application programming. So it has to be fast, it has to be readable, it has to be able to GUI from time to time, it has to be able to program web, it has to be able to execute scripts, it has to be good with ascii files?

Is any language bad with ASCII files?

---

### Post by akvino on 2009-11-17
Some are better than others.

---

### Post by lukeiamyourfather on 2009-11-17
> **akvino said:**
> What is the best programming language FOR Linux system and application programming. So it has to be fast, it has to be readable, it has to be able to GUI from time to time, it has to be able to program web, it has to be able to execute scripts, it has to be good with ascii files?

Python can do all you have mentioned. Like others have said, "best" is based on opinion so not everyone will agree. Cheers!

---

### Post by MindSz on 2009-11-17
I love programming in C, but I've found the GUI stuff a little too complicated compared to other languages.

For down and dirty programming it's great tho

---

### Post by matthew.ball on 2009-11-17
If you're interested in systems development (especially GNU/Linux!), and application development, you'll probably be interested in C:

GTK+ is primarily C, correct? (Yes there are libraries for other languages).

C is a pretty simple language, it's fairly easy to grasp, and if you're dedicated you can really learn it.

General Information - [http://en.wikipedia.org/wiki/C_(programming_language](http://en.wikipedia.org/wiki/C_(programming_language))
Great Book - [http://en.wikipedia.org/wiki/The_C_Programming_Language_(book](http://en.wikipedia.org/wiki/The_C_Programming_Language_(book))
Good Tutorial - [http://www.iu.hio.no/~mark/CTutorial/CTutorial.html](http://www.iu.hio.no/~mark/CTutorial/CTutorial.html)

I strongly recommend using gcc with emacs - learn what the compiler is doing.

If you're going into systems development, you'll be getting into the small details so it could be good preparation :)

Then, if you want to get into scripting, web development and application development, Python is probably the most flexible here:
General Information - [http://www.python.org/](http://www.python.org/)
- [http://en.wikipedia.org/wiki/Python_(programming_language](http://en.wikipedia.org/wiki/Python_(programming_language)
Good Tutorial - [http://www.greenteapress.com/thinkpython/thinkpython.html](http://www.greenteapress.com/thinkpython/thinkpython.html)

You can get toolkits for writing GUI's with GTK+, Qt and wxWindows.

I would recommend again to start with a basic editor (maybe Geany) to write your Python files, but compile from a terminal (Geany has an integrated terminal), once you're comfortable working the compiler, add some key-bindings to Geany to compile the project on F5 or something.

Enjoy! :)

---

### Post by phrostbyte on 2009-11-17
> **akvino said:**
> Some are better than others.

It's completely subjective though. There have been similar threads to this in the past (also "what is the best IDE") and they are rarely conclusive.

Python is a good general purpose language though, especially for new programmers because it doesn't require understanding pointers or memory management, and IMO it's standard library/API is very simple to use and understand.

---

### Post by -grubby on 2009-11-17
> **matthew.ball said:**
> Python files, but compile

What?

---

### Post by matthew.ball on 2009-11-17
s/compile/interpret

---

### Post by shadylookin on 2009-11-17
> **akvino said:**
> What is the best programming language FOR Linux system and application programming. So it has to be fast, it has to be readable, it has to be able to GUI from time to time, it has to be able to program web, it has to be able to execute scripts, it has to be good with ascii files?

most system/application programming is done in c/c++. web programming is done in a variety of things. Scripts are usually perl or python and nothing that I'm aware of is bad with ascii files. 

With the exception of system programming Ruby is used for all that.

---

### Post by CptPicard on 2009-11-18
> **lukeiamyourfather said:**
> "best" is based on opinion

> **phrostbyte said:**
> It's completely subjective though.

The issue is nuanced, not subjective. :)

Most of the time your technical/practical needs for some given task will override other considerations. However, I find it very difficult to believe that there would not be any objective general-purpose programming qualities in different languages; otherwise all  the thinking that has gone into them would have been in vain and we'd all be hacking by flipping bits.

Of course, if there was a clear "best" language we'd be using it by now. The question of bestness is ill-defined, but there are very good arguments to be made as to why people in general find clear, conceptually powerful yet economical languages whose design allows for generic recombination of language constructs and ideas in arbitrary ways to be "powerful" languages.

Then, there's the raw speed crowd, but I never got the impression they actually have genuinely thought about the issue of why some languages have the things they do ;)

---

### Post by grayrainbow on 2009-11-18
As most people will say - it's subjective...BUT...what's the best language to read Terry Pratchett book? Of course you have to know that language to read it :)
And if you remember, mathematicians use specific notations for different categories of math, and only in child form they use something really close to natural language(english, german, french, etc). Simply putted there's no such a thing as really general purpose language. 
1)There is hardware close - C/C++(and no matter that I prefer C++ usually really low level programmers prefer C), most powerfull ones, they give programmer the power to control the machine.
2)There is library based - Java/C#(they are usually also platform specific and run only on something like VM, but eventually could be compiled), which give programmers the power to not care of some stuff and easily import other people solutions in their domain of problems.
3)There's scripts which are defined to run only on specific platform(their interpreter) - JavaScript/Scheme/Lua/Python, used mostly for security(you are limited of system access by interpreter), and readability in sense that they are not so mathematical as syntax, and for hobby projects(that's related to readability), here are also some business scripts like microsoft excell scripts.
4)And there are some really specific languages - mathlab/octave, some music languages, SQL, etc, used from professionals in specific categories(engineers, architects, economyst, etc).

So...since Linux is operating system(kernel actually, but anyhow), every single language of these are supposed to work under it :)

---

### Post by CptPicard on 2009-11-18
> **grayrainbow said:**
> As most people will say - it's subjective...

In my view those "most people" who believe it is completely subjective are just the ones who seem to be unable to identify the discriminating features, so for them there is no substantial difference. Which would probably indeed be most people ;)

> 
And if you remember, mathematicians use specific notations for different categories of math

There are specific notational devices for some particular objects, but otherwise mathematical notation strives for commonality, consistency, clarity and economy. Then there is the fact that it's the semantic, conceptual stuff behind the syntax that matters... in particular, the idea of everyone having their own subjective mathematical language would result in disaster. Same thing with programming languages.

> 
and only in child form they use something really close to natural language(english, german, french, etc).

Yes, they do try to use abstract, concise language that communicates. I should hope programming languages would be the same, being a subset of mathematical notation, namely, for recursively enumerable languages.

> 
 Simply putted there's no such a thing as really general purpose language.

As long as it's Turing-complete, there have been numerous attempts at approaching one. I don't quite think that the effort has been pointless because would be no such thing...

> 
1)There is hardware close - C/C++(and no matter that I prefer C++ usually really low level programmers prefer C), **most powerfull ones**, they give programmer the power to control the machine.

I thought it was subjective and that there is no such thing as the most powerful language... ;)

Programming languages are formal, symbolic definitions of a computable function -- and most importantly the languages to be used to describe that part of the problem that is not trivially offloaded to the computer. Therefore, the human abstraction is the important part, and the conceptual devices we can create to aid that. See the prior discussion about mathematical notation.

I have quite rarely had to "control the computer" and when I have to, that part is the uninteresting, yet heavy on work part.

> 4)And there are some really specific languages - mathlab/octave, some music languages, SQL, etc, used from professionals in specific categories(engineers, architects, economyst, etc).

Interestingly, when these domain-specific languages become specific enough, they tend to lose their Turing-completeness -- that is, their general-purposeness -- or it becomes so obscure that proving it is a task. In the latter case you may theoretically be able to use the language as a general-purpose language, but those solutions become contrived.

I would posit that this does extend to the other direction as well... you can try to find a Turing-complete programming language that, as elegantly as possible, describes all those languages that are computable by a Turing machine. Which is anything we'll ever be able to hope to do on a computer anyway. :)

---

### Post by grayrainbow on 2009-11-18
CptPicard, I'm not sure that Turing complete matter so much, it's quite old concept and with multiprocessor/multicore machines there is possibility for something new emerge. After all many purely mathematical problem nowadays are solved with computers help. But even that possibility left aside - most systems are written in C, and I'm sure you already know one of the reasons for that, you also know and the reason corresponding to that what I wrote about Terry Pratchett.

> I thought it was subjective and that there is no such thing as the most powerful language... :wink:
It's subjective, which mean that was my opinion(and probably the opinion of every system programmer as well, see previous paragraph). And surely it depends of how you define the word "power" ;)


> Programming languages are formal, symbolic definitions of a computable function -- and most importantly the languages to be used to describe that part of the problem that is not trivially offloaded to the computer. Therefore, the human abstraction is the important part, and the conceptual devices we can create to aid that. See the prior discussion about mathematical notation.
I thing you looking too much from yours point of view(which is much better word than abstraction when you use it to describe programming language ;) ) you miss one simple thing...let say that writing a device specific driver is...well, human specific job(ever heard of the phrase "general abstract nonsense"?).

P.S. CptPicard, I'm sorry to disappoint you, but everyone has his/her subjective language, even his/her natural language, and everything that comes from that. If you really want to investigate - try some library/bookstore for stuff like Freud, Adler and Jung.

---

### Post by Arndt on 2009-11-18
> **akvino said:**
> Some are better than others.

Give an example of what you mean.

---

### Post by CptPicard on 2009-11-18
> **grayrainbow said:**
> CptPicard, I'm not sure that Turing complete matter so much, it's quite old concept and with multiprocessor/multicore machines there is possibility for something new emerge.

Don't be so cavalier with the fundamentals of what we know of "mechanical" computation. It sounds rather extreme to suggest that Turing machine's properties somehow diminish in significance with time.

The core points of TMs that are relevant to the discussion are that they bound what is doable with *any* equivalent machine, and that all equivalent machines are exchangeable. In programming language terms, and most relevantly for this question we have here, you can interpret one language in terms of another. It is this exchangeability that leaves us the freedom to find the most suitable representation for humans (the "general purpose programming langauge"), *as long as we keep it Turing complete*.

Multicore processing is still clearly, comfortably keeping within the theoretical model, there is nothing special there (and will not be, it's known). The efficiency/pragmatic questions of parallel processing do not deal with the fundamental computational ability of the system -- or its exchangeability with something else.

Of course, we may need to consider the implications of parallel processing to the languages we use. Pure-functionality is a very interesting example of this that actually tackles parallelism with fundamental properties of language (when there is no state, sharing state is no problem), instead of writing some "concurrency libraries" and nice but needless syntactic sugar for using them.

> After all many purely mathematical problem nowadays are solved with computers help.

The whole deal of characterization and analysis of computable functions that was done by Church/Turing has to do with which mathematical problems are "mechanistically" solvable -- and if all mathematical statements are mechanistically provable -- they're not.

All the mathematical problems we're solving nowadays by computer that we may not have been solving by computer 50 years ago are still clearly Turing-machine solvable. That barrier hasn't gone anywhere. Someone may have figured out a (faster) algorithm (perhaps due to some mathematical insight), or the computer got faster, but the fundamental issues remain there.

> 
 But even that possibility left aside - most systems are written in C

Yes, I did actually state that "most of the time technical/practical considerations decide choice of language", I do not take issue with *that*... :)

> 
It's subjective, which mean that was my opinion(and probably the opinion of every system programmer as well, see previous paragraph). And surely it depends of how you define the word "power" ;)

Okay, so it was not to be taken as a categorical statement. Fair enough. I guess if you define "power" as runtime speed or hardware access, then that is quite true. 

For me, if the question of programming language qualities is to be meaningful, the computer essentially has to be a black box of which we know that it just executes a language with a definition that is executable by Turing machine (which is, according to the rather reasonable assumption of the Church-Turing thesis, the definition of "capable of being physically executed in general"). As such, there is no "preferred" interface to the machine simply by virtue of the machine "internally operating" in terms of it.

> 
I thing you looking too much from yours point of view(which is much better word than abstraction when you use it to describe programming language ;)

I just want to get rid of elements in the language that are implementation- or too problem-domain specific or, worse yet, just cause internal conflicts inside the language (this is often sign of bad design). They should describe computational abstractions that are as general as possible (think mathematics, it also abstracts like this), so that they will then be generically applicable to problems by putting them together as problem domain dictates. I guess this is the sort of general purpose programming language I am talking about. 

>  that writing a device specific driver is...well, human specific job

I would respond that I can imagine writing a specific device-driver-writing programming language, with all machine-related issues down just right, that would suck for any other task :)

> 
P.S. CptPicard, I'm sorry to disappoint you, but everyone has his/her subjective language, even his/her natural language, and everything that comes from that. If you really want to investigate - try some library/bookstore for stuff like Freud, Adler and Jung.

No disappointments here, I'm still unmoved as always :p

I can well understand that natural mother tongue is a very subjective language. Debating betterness of natural languages is genuinely a losing proposition. The really nice thing about programming languages that IMO helps their objectivity is the fact that they *must* specifically, formally, correctly, describe an exact computable function (or process, in imperative ways of thought). They must also be able to communicate this exactness efficiently. IMO that gives us much more ground to stand on when considering why we have Lisp instead of bits in a hex editor, for instance... if someone tells me they prefer the latter in terms of informativeness, I would be prone to call the bluff... :)

EDIT: About general abstract nonsense... yes, there may be that risk. However, the reason why I've found the more abstract languages so informative in general in my own learning-about-programming is exactly because they carry the general ideas, not necessarily some implementation-specific instantiation of those ideas. You get to apply the idea somewhere else then once you recognize what you're dealing with... in programming there is perhaps less possibility to this than in mathematics, but the phenomenon exists.

---

### Post by akvino on 2009-11-18
> **Arndt said:**
> Give an example of what you mean.

Eh...
I programmed in C, C++, Java, PHP, some Perl and multiple shells.

C and C++ - are good for processing files but bad in simplistic approach to execute shell script, take info from shell and use it in the web, or GUI. So it is not just simple, process the file and do something with it, it is more like process the file, take info, use it in GUI or WEB, change system configuration based up on the input, output or something else.

PHP does web stuff well but forget about system stuff.

Java - eh where do I begin, I would rather program in C++.

Perl - strict good Perl is good, but it doesn't lay well simply since it is not strict all the time. I don't want to go through someone's code and 'guess' what they wanted to do, not everyone had Software Engineering classes.

Python - I never used. Which might be my nest endeavour.

Shell - good for plain simple stuff, but not so good for large scale applications.

---

### Post by Arndt on 2009-11-18
> **akvino said:**
> Eh...
I programmed in C, C++, Java, PHP, some Perl and multiple shells.

C and C++ - are good for processing files but bad in simplistic approach to execute shell script, take info from shell and use it in the web, or GUI. So it is not just simple, process the file and do something with it, it is more like process the file, take info, use it in GUI or WEB, change system configuration based up on the input, output or something else.

PHP does web stuff well but forget about system stuff.

Java - eh where do I begin, I would rather program in C++.

Perl - strict good Perl is good, but it doesn't lay well simply since it is not strict all the time. I don't want to go through someone's code and 'guess' what they wanted to do, not everyone had Software Engineering classes.

Python - I never used. Which might be my nest endeavour.

Shell - good for plain simple stuff, but not so good for large scale applications.

Well, I referred solely to that "ASCII file" thing.

---

### Post by grayrainbow on 2009-11-18
CptPicard, what's the "best" random generator you know?(just curious).
A bit of randomness.
Honestly...I'm not sure where the OS ends. Is window manager go in the system programming part? Baicaly every desktop got one, so it's should be part of the OS just like every browser got javascript interpreter(I believe most people think video processing as obligatory for browsers as well).

> Okay, so it was not to be taken as a categorical statement. Fair enough. I guess if you define "power" as runtime speed or hardware access, then that is quite true.
Ooo, I'm really categoric about that :D : most power in language mean that you can implement every other language in the power one(with respect of resources you have) + access to every functionality of the hardware(and this phrase with respect to what you mention in your first post on the subject).

> I just want to get rid of elements in the language that are implementation- or too problem-domain specific or, worse yet, just cause internal conflicts inside the language (this is often sign of bad design). They should describe computational abstractions that are as general as possible (think mathematics, it also abstracts like this), so that they will then be generically applicable to problems by putting them together as problem domain dictates. I guess this is the sort of general purpose programming language I am talking about.
Hmm...and what in mathematical terms that mean "S->M" it's probably mean "I'm out of my context" but you'll get the idea. You can not get rid of ambiguity(btw, what closure mean, and should it be idempotent? :) ) and domain specification, and trying to do it is veeery dangerous for the human race [http://en.wikipedia.org/wiki/Tower_of_Babel]("http://en.wikipedia.org/wiki/Tower_of_Babel") :)

But actually I find it useful ["general abstract nonsense"]("http://en.wikipedia.org/wiki/Category_theory")

---

### Post by nvteighen on 2009-11-18
> **akvino said:**
> What is the best programming language FOR Linux system and application programming. So it has to be fast, it has to be readable, it has to be able to GUI from time to time, it has to be able to program web, it has to be able to execute scripts, it has to be good with ascii files?

What you seem to want is almost the perfect programming language... Probably Python is close to what you want, though it's not the fastest language you can get. If you want speed, C, C++, but then you lose the ability to script and all web development will have to be coded through third-party libraries. Perl is the best to use with text files, IMO... but you'll accept Perl is a bit difficult to use in large projects... etc... etc... etc... Lisp wouldn't be fast, but it would be the most readable thing (no irony).

In the words of The Rolling Stones: "You can't always get what you want" :)

---

### Post by akvino on 2009-11-20
> **nvteighen said:**
> What you seem to want is almost the perfect programming language... Probably Python is close to what you want, though it's not the fastest language you can get. If you want speed, C, C++, but then you lose the ability to script and all web development will have to be coded through third-party libraries. Perl is the best to use with text files, IMO... but you'll accept Perl is a bit difficult to use in large projects... etc... etc... etc... Lisp wouldn't be fast, but it would be the most readable thing (no irony).

In the words of The Rolling Stones: "You can't always get what you want" :)

SO would there be a way to call C++ from Python and receive some sort of input... In essence interact two different languages.

---

### Post by nvteighen on 2009-11-20
> **akvino said:**
> SO would there be a way to call C++ from Python and receive some sort of input... In essence interact two different languages.

I'm not quite sure... Python can easily call C (using the ctypes standard module), but I'm not sure how this can be done with C++. Curiously, C++ can call Python via the Python API.

---

### Post by TheStatsMan on 2009-11-20
> **akvino said:**
> SO would there be a way to call C++ from Python and receive some sort of input... In essence interact two different languages.

Yes, it is fairly easy to call C++ from python. Probably depends on what you are doing what is the best way. If you just want to be able to use a c++ class in python then swig makes this fairly easy.

---

### Post by neerajadsul on 2009-11-20
Yes, C++ functions can be called from python. In fact that's one of the most commonly used feature of python. You can extend you python programs by including complied C/C++ extensions for the part of the code which you want to run extremely fast (e.g. FFT Calculation ).

There is wonderful documentation about how to do it here
[http://docs.python.org/extending/extending.html](http://docs.python.org/extending/extending.html)

And for building C/C++ extensions and using them - 
[http://docs.python.org/distutils/index.html](http://docs.python.org/distutils/index.html)

Initially took some time and patience for me to understand and make it work. (about 8 hrs since I was new to Python). But works perfectly.

---

### Post by TheStatsMan on 2009-11-20
It is also worth mentioning that it is extremely easy (could not be easier) to link fortran to python using f2py. This is an extremely good combination for numerical computing. Fortran is far easier than C/C++ and is just as fast (in some cases faster), but arguably lacks the language features of C/C++, however python has the language features, just not the speed. Kind of makes Python and Fortran best friends.

---

### Post by A_Fiachra on 2009-11-21
> **akvino said:**
> What is the best programming language FOR Linux system and application programming. So it has to be fast, it has to be readable, it has to be able to GUI from time to time, it has to be able to program web, it has to be able to execute scripts, it has to be good with ascii files?

There's tcl and bash.

Don't forget Lisp, Eek and R.

Perl, Python, Ruby, Java, C, C++ have their strengths.

Erlang, Lua and Scala are good.

Algol, AP/L, COBOL, Basic, Forth, Fortran, Scheme and Prolog had there day.

Then again, there's A+, Kylix, Limbo, Pike, B, D, J, K, REXX, Joy, Factor, Cat, Pico, T, SNOBOL, Alice, Caml, F#, SETL, ABC, Boo, Eiffel, Ubercode, Tea, Curl, lo, Smalltalk, Simula, Mercury, Clojure, Guile, Turing+, Modular 3, J#, D--, Ada, S2 and JCL.

Then there are LOTS of exotic languages!

:-)

---

### Post by nvteighen on 2009-11-21
> **neerajadsul said:**
> Yes, C++ functions can be called from python. In fact that's one of the most commonly used feature of python. You can extend you python programs by including complied C/C++ extensions for the part of the code which you want to run extremely fast (e.g. FFT Calculation ).

There is wonderful documentation about how to do it here
[http://docs.python.org/extending/extending.html](http://docs.python.org/extending/extending.html)

...


That link shows something different: how to extended the Python interpreter, not how to use the Foreign Function Interface.

It's much simpler than that... Look at [http://docs.python.org/library/ctypes.html](http://docs.python.org/library/ctypes.html) 

Say we have this C shared library:

```

/* hello.c */

#include <stdio.h>

void hello(char *str)
{
    (void)printf("Hello %s from C!\n", str);
}

```

Compile it with:
**gcc -fPIC -shared -o libhello.so hello.c -Wall**

And then, this Python module which takes the shared library and uses it:
```

# hello.py

import ctypes

def main():
    libhello = ctypes.CDLL("./libhello.so")
    
    # Prototyping libhello.hello: void hello(char *)
    libhello.hello.argtypes = [ctypes.c_char_p]
    libhello.hello.restype = None

    libhello.hello("Python")

if __name__ == "__main__":
    main()

```

Again, this works for C. I doubt C++ has something like this available because of name mangling...

---

### Post by CptPicard on 2009-11-21
> **nvteighen said:**
> Again, this works for C. I doubt C++ has something like this available because of name mangling...


One probably has to provide a C interface via "extern C" declared functions... which is somewhat of a pity, having C++ objects in Python wouldn't be all that bad :)

---

### Post by maximinus_uk on 2009-11-21
> **grayrainbow said:**
> most power in language mean that you can implement every other language in the power one (with respect of resources you have) + access to every functionality of the hardware

Then assembly is the best language. It's Turing complete (as they almost always are) and you get full hardware access.

Wait - you don't agree? Surely it's C then? Mmmm... perhaps some machines don't look like C at the hardware level - [http://en.wikipedia.org/wiki/Lisp_machine]("http://en.wikipedia.org/wiki/Lisp_machine")?

I'm also longing to know as to what "every functionality of the hardware" I'm not currently getting in my Python, Perl or Scheme programs? Maybe you just mean 'harder and therefore must be more l33t'? That's what most C++ programmers seem to mean. "Dang, using this language is TOUGH, so I must be a better programmer than you!"

---

### Post by CptPicard on 2009-11-21
> **maximinus_uk said:**
> "Dang, using this language is TOUGH, so I must be a better programmer than you!"

The most interesting feature of this "out of all Turing-complete formalisms, hardware operations are *special*" position is that it seems to come from people who do not seem to have a very good idea as to why other programming languages have incorporated the approaches into them that they have, and what they are good for. Therefore it becomes easy to assume that HLLs simply provide cop-out crutches for the lazy bum programmer and that in particular, they somehow "ride on top of" a supposed lower-level "host language" (which is of course quite wrong an assumption -- there is no hierarchy, there is only *translation* between equivalent formalisms).

There is of course a more valid "making a certain kind of physical machine go" vs. "providing a computable description of a solution to a problem" philosophical difference that seems to divide "engineers" and "computer scientists"... but even the engineers I know tend to become "lispers" when their understanding of the abstract, mathematical structure of computational problems grows ;)

---

### Post by akvino on 2009-11-23
> **CptPicard said:**
> The most interesting feature of this "out of all Turing-complete formalisms, hardware operations are *special*" position is that it seems to come from people who do not seem to have a very good idea as to why other programming languages have incorporated the approaches into them that they have, and what they are good for. Therefore it becomes easy to assume that HLLs simply provide cop-out crutches for the lazy bum programmer and that in particular, they somehow "ride on top of" a supposed lower-level "host language" (which is of course quite wrong an assumption -- there is no hierarchy, there is only *translation* between equivalent formalisms).

There is of course a more valid "making a certain kind of physical machine go" vs. "providing a computable description of a solution to a problem" philosophical difference that seems to divide "engineers" and "computer scientists"... but even the engineers I know tend to become "lispers" when their understanding of the abstract, mathematical structure of computational problems grows ;)

After all this is a very good thread... I think I know my answer now, and I am very happy with the outcome......  I feel new New Year's resolution coming soon....  Any recommendation on good Python literature from Amazon.com is welcome....:popcorn:

---

### Post by grayrainbow on 2009-11-23
> **maximinus_uk said:**
> Then assembly is the best language. It's Turing complete (as they almost always are) and you get full hardware access.

Wait - you don't agree? Surely it's C then? Mmmm... perhaps some machines don't look like C at the hardware level - [http://en.wikipedia.org/wiki/Lisp_machine](http://en.wikipedia.org/wiki/Lisp_machine)?

I'm also longing to know as to what "every functionality of the hardware" I'm not currently getting in my Python, Perl or Scheme programs? Maybe you just mean 'harder and therefore must be more l33t'? That's what most C++ programmers seem to mean. "Dang, using this language is TOUGH, so I must be a better programmer than you!"
On one thread about game programming I pointed exactly to the same link as example of what toys people were using. But putting toys aside...take your PC, trow it through window, and start using lisp machine. Btw, that's not bad thing, who knows you may become gazilionaire :popcorn:
I'm sorry if I hurt your feelings but...are you able to read? Did you read my first post in the thread?

---

### Post by 0cton on 2009-11-23
There is no best.
Depends on what you are trying to do, and most of the time most applications require more than one language anyway.

---

### Post by matthew.ball on 2009-11-23
> **maximinus_uk said:**
> Then assembly is the best language. It's Turing complete (as they almost always are) and you get full hardware access.

Wait - you don't agree? Surely it's C then? Mmmm... perhaps some machines don't look like C at the hardware level - [http://en.wikipedia.org/wiki/Lisp_machine]("http://en.wikipedia.org/wiki/Lisp_machine")?

I'm also longing to know as to what "every functionality of the hardware" I'm not currently getting in my Python, Perl or Scheme programs? Maybe you just mean 'harder and therefore must be more l33t'? That's what most C++ programmers seem to mean. "Dang, using this language is TOUGH, so I must be a better programmer than you!"
*Reductio Ad Absurdum.*

---

### Post by maximinus_uk on 2009-11-24
> **grayrainbow said:**
> On one thread about game programming I pointed exactly to the same link as example of what toys people were using. But putting toys aside...take your PC, trow it through window, and start using lisp machine. Btw, that's not bad thing, who knows you may become gazilionaire :popcorn:
I'm sorry if I hurt your feelings but...are you able to read? Did you read my first post in the thread?

OK, I didn't mean to appear rude, and I did read your first post. But it annoys me that people think that C++ has MAGIC RAINBOW POWER DUST because it is *so close to the hardware*. Whereas I think C++ SUCKS BIG TIME because it's big, bloated and complex. And very hard to use, as well, although people seem to think that part is some kind of badge of honor.

See, in your first post, you stated:

[QUOTE=grayrainbow]There is hardware close - C/C++(and no matter that I prefer C++ usually really low level programmers prefer C), most powerfull ones[/QUOTE]

I utterly fail to see how 'hardware close' is more powerful. Otherwise, like I said, you be using assembly. I'm a weird freak who thinks 'easier to write an algorithm' is more powerful. And then you said:

[QUOTE=grayrainbow]There's scripts which are defined to run only on specific platform(their interpreter) - JavaScript/Scheme/Lua/Python, used mostly for security(you are limited of system access by interpreter), and readability in sense that they are not so mathematical as syntax, and for hobby projects(that's related to readability)[/QUOTE]

When you say 'hobby projects' it's like a mild put-down. Your saying "Well, C/C++ has real power, but you *could* use Python for a 'hobby' project". Well, I'm sorry if I disagree.

---

### Post by akvino on 2009-11-24
> **maximinus_uk said:**
> OK, I didn't mean to appear rude, and I did read your first post. But it annoys me that people think that C++ has MAGIC RAINBOW POWER DUST because it is *so close to the hardware*. Whereas I think C++ SUCKS BIG TIME because it's big, bloated and complex. And very hard to use, as well, although people seem to think that part is some kind of badge of honor.

See, in your first post, you stated:



I utterly fail to see how 'hardware close' is more powerful. Otherwise, like I said, you be using assembly. I'm a weird freak who thinks 'easier to write an algorithm' is more powerful. And then you said:



When you say 'hobby projects' it's like a mild put-down. Your saying "Well, C/C++ has real power, but you *could* use Python for a 'hobby' project". Well, I'm sorry if I disagree.

For your information C++ is fast, and if you need to execute complicated computation, you are best off using C++. On top of it all, C++ got math library refresh not too long ago.

---

### Post by CptPicard on 2009-11-24
> **akvino said:**
> For your information C++ is fast

So? Plenty of languages are plenty fast enough, and after that, other considerations really should come into play unless speed is a problem (and even then an algorithmic solution should take precedence), which is what maximinus is talking about...

> 
and if you need to execute complicated computation, you are best off using C++.

In a lot of ways, I'd much rather model genuinely complicated computations and in particular "systems" in a high-level, flexible language. It helps you manage the complexity and even often model in terms of things that are a better fit.

By the way, what do you base this opinion on? What is your experience using in particular languages that are not your typical C++/Java/C# fare?

> C++ got math library refresh not too long ago.

So they're better than math routines in ... where? :)

---

### Post by akvino on 2009-11-24
> **CptPicard said:**
> So? Plenty of languages are plenty fast enough, and after that, other considerations really should come into play unless speed is a problem (and even then an algorithmic solution should take precedence), which is what maximinus is talking about...



In a lot of ways, I'd much rather model genuinely complicated computations and in particular "systems" in a high-level, flexible language. It helps you manage the complexity and even often model in terms of things that are a better fit.

By the way, what do you base this opinion on? What is your experience using in particular languages that are not your typical C++/Java/C# fare?



So they're better than math routines in ... where? :)

Write DES3 + RSA algorithm for "on demand, streaming" application usage. Tell me which one you prefer:
C
C++
C#
Perl
Python
Shell Script
PHP
Java

I'll go with C++, now your turn!

---

### Post by nvteighen on 2009-11-24
> **akvino said:**
> Write DES3 + RSA algorithm for "on demand, streaming" application usage. Tell me which one you prefer:
C
C++
C#
Perl
Python
Shell Script
PHP
Java

I'll go with C++, now your turn!

C++!? I'd go for C, no doubt. I honestly don't see where OOP can fill into DES or RSA... (unless you write C using a C++ compiler... but that's C). And of course, this is a heavily loaded application where speed *is* critical and maybe . A higher-level language would perform very bad at this.

But, the user interface could be written in Python.

Heck... The issue is that heavy number-crunching are a small subset of programming. That kind of programming can be achieved by just having a small set of mathematical operations and an arbitrary-length integer structure (I'd use GMP). You can do this in C, C++, Python or Lisp and the algorithm will be the same because there's almost no abstraction issues; the difference will be at performance speed, of course. In other words: you're using your computer more as a calculator rather than a logic-solving machine. (BTW, your computer can work as a calculator because it's a logic-solving machine).

When you get into logical-based programming task, you get into formalism and, therefore, into abstraction. Then C and C++ have a lot to lose against Python, Lisp, Perl, etc. You have to devise "forms" into which you conceptualize entities from reality... The best example is writing a card game: You've got to somehow write about cards, players, to deal (notice: a verb), bets, score, scoring and implementing the rules of the 
card game. There you want a language which allows you to talk about all this things in the most expressive way.

Each language has its task, of course.

---

### Post by Can+~ on 2009-11-24
> **akvino said:**
> Write DES3 + RSA algorithm for "on demand, streaming" application usage. Tell me which one you prefer:
C
C++
C#
Perl
Python
Shell Script
PHP
Java

I'll go with C++, now your turn!

I somehow feel that this degraded into a pissing contest. But ok, let's say:

[PHP]sudo apt-get install python-crypto[/PHP]

[PHP]import Crypto.Cipher.DES3[/PHP]

Oh wow, did I just installed the encryption algorithm on a single line? Yeah, because it's a known algorithm, done pretty much on every language, and what's best, is that this python module is C compiled, so I won't have to care much about penalties.

Also, my boss will probably say "great job", because I actually solved the problem, instead of wasting a work day while translating the wikipedia algorithm to C++.

I'm just that awesome. (In fact, I'll guess that C# and Java also have this libraries already done and optimized).

And if the algorithm weren't availabe, I would probably code it on C and plug it to the corresponding higher-level language. Why? Because, even the most speed-needy applications, it makes sense to write the "fast gears" on the fast language, and the other (possibly 90%) on the slow but with fast development time language.

---

### Post by CptPicard on 2009-11-24
Not complex enough. Number-crunching algorithm implementations can be relatively straightforward implementation-wise. Sounds like C, in a little library. On the other hand I see no reason why the entire streaming application, regardless of what it streams could not find a nice implementation in Lisp. Even the encryption part should be quick enough when written in a more imperative style and type assertions. If that fails, I'll just use that library of mine, called from Lisp. Or even Python ;)

In particular, my implementation language will most definitely not be C++ because C++ essentially tends to force everything else to be C++ -- linking to C is far easier.

IMO I made a perfectly good reservation for the speed requirement in my statement earlier to account for something like this, anyway.

I do not believe in tossing around individual examples in this manner though; they are too specialized. You can always find some particular niche to push for something. You can't write J2EE applications in anything else than Java, for example. You can't write Linux kernel source in anything else but C, because it is already all C, and that in kernels, pointer arithmetic is actually of conceptual relevance.

In general, though, I fully sympathize with maximinus' remark about the imaginary "magic dust"... I share the frustration, and wonder how to communicate better about an issue that seems intractable to the low-level crowd. I've been here for years, and this topic pops up every now and then, with the exact same content... and it just leaves me with the impression that some people simply do not "see" why certain programming language designs are the way they are, and why they are conceptually very interesting, because their only metric is "does it go fast?". (Admittedly sometimes I would like to just conclude that they are talking about languages/ideas they do not know, but I give benefit of doubt :) -- anyway, [read this]("http://www.paulgraham.com/avg.html") )

I am fully willing to hack up something in C when the need arises, but it does not make the language any more interesting than a bunch of control statements, basic data types and a function call mechanism (the minimalism is actually a strength wrt. C++).

**EDIT:** Oh yeah, it was my turn. Here is the task.

Devise a client-server application framework that can, for example and as an initial implementation, support web-based front ends. The browser-side should be an AJAX/Comet implemented GUI. 

The idea is to create a system where the application itself is written in the language of choice, without clearly separated "html view" and the request/response cycle to server side code. You must abstract the request/response away completely using AJAX. The GUI widgets on the browser must be represented as objects in the application development language. Think your usual GUI widget set in a desktop app.

Of course, the browser is immaterial, it can be replaced later with Silverlight or XUL or whatever. Interface to app stays the same.

The application must support real-time, simultaneous views of the same data from arbitrary numbers of clients. The model of the data must be implemented in terms of a software transactional memory that must be transparent, again in the application development language and API. Also, the same model data objects must be mapped on the fly to a database so they keep persistent.

Excluding the database or memory transactions or heavy processing in the app, the thing should support maybe 20,000 simultaneous clients on typical perhaps ca. 2005 commodity desktop hardware.

This needs to be written and maintained by one guy.

(This thing actually exists...)

---

### Post by akvino on 2009-11-24
> **CptPicard said:**
> Not complex enough. Number-crunching algorithm implementations can be relatively straightforward implementation-wise. Sounds like C, in a little library. On the other hand I see no reason why the entire streaming application, regardless of what it streams could not find a nice implementation in Lisp. Even the encryption part should be quick enough when written in a more imperative style and type assertions. If that fails, I'll just use that library of mine, called from Lisp. Or even Python ;)

In particular, my implementation language will most definitely not be C++ because C++ essentially tends to force everything else to be C++ -- linking to C is far easier.

IMO I made a perfectly good reservation for the speed requirement in my statement earlier to account for something like this, anyway.

I do not believe in tossing around individual examples in this manner though; they are too specialized. You can always find some particular niche to push for something. You can't write J2EE applications in anything else than Java, for example. You can't write Linux kernel source in anything else but C, because it is already all C, and that in kernels, pointer arithmetic is actually of conceptual relevance.

In general, though, I fully sympathize with maximinus' remark about the imaginary "magic dust"... I share the frustration, and wonder how to communicate better about an issue that seems intractable to the low-level crowd. I've been here for years, and this topic pops up every now and then, with the exact same content... and it just leaves me with the impression that some people simply do not "see" why certain programming language designs are the way they are, and why they are conceptually very interesting, because their only metric is "does it go fast?". (Admittedly sometimes I would like to just conclude that they are talking about languages/ideas they do not know, but I give benefit of doubt :) -- anyway, [read this]("http://www.paulgraham.com/avg.html") )

I am fully willing to hack up something in C when the need arises, but it does not make the language any more interesting than a bunch of control statements, basic data types and a function call mechanism (the minimalism is actually a strength wrt. C++).

**EDIT:** Oh yeah, it was my turn. Here is the task.

Devise a client-server application framework that can, for example and as an initial implementation, support web-based front ends. The browser-side should be an AJAX/Comet implemented GUI. 

The idea is to create a system where the application itself is written in the language of choice, without clearly separated "html view" and the request/response cycle to server side code. You must abstract the request/response away completely using AJAX. The GUI widgets on the browser must be represented as objects in the application development language. Think your usual GUI widget set in a desktop app.

Of course, the browser is immaterial, it can be replaced later with Silverlight or XUL or whatever. Interface to app stays the same.

The application must support real-time, simultaneous views of the same data from arbitrary numbers of clients. The model of the data must be implemented in terms of a software transactional memory that must be transparent, again in the application development language and API. Also, the same model data objects must be mapped on the fly to a database so they keep persistent.

Excluding the database or memory transactions or heavy processing in the app, the thing should support maybe 20,000 simultaneous clients on typical perhaps ca. 2005 commodity desktop hardware.

This needs to be written and maintained by one guy.

(This thing actually exists...)

I didn't intend for this to grow into pissing contest. I never used Python for instance, and as I said before in one of the posts, Python seems ideal for what I need it to do - that is everything. I also asked about C++ and C API since most of the programming will be done on Linux. If I need application to do something and do it fast, and by fast I mean fast, and there is API in Python, unless Python can do it faster (which I doubt) it would be easy to cross reference C/C++ executable and complete the task. 

All in all good discussion.

---

### Post by akvino on 2009-11-24
> **Can+~ said:**
> I somehow feel that this degraded into a pissing contest. But ok, let's say:

[PHP]sudo apt-get install python-crypto[/PHP]

[PHP]import Crypto.Cipher.DES3[/PHP]

Oh wow, did I just installed the encryption algorithm on a single line? Yeah, because it's a known algorithm, done pretty much on every language, and what's best, is that this python module is C compiled, so I won't have to care much about penalties.

Also, my boss will probably say "great job", because I actually solved the problem, instead of wasting a work day while translating the wikipedia algorithm to C++.

I'm just that awesome. (In fact, I'll guess that C# and Java also have this libraries already done and optimized).

And if the algorithm weren't availabe, I would probably code it on C and plug it to the corresponding higher-level language. Why? Because, even the most speed-needy applications, it makes sense to write the "fast gears" on the fast language, and the other (possibly 90%) on the slow but with fast development time language.

Never mind.

---

### Post by Puzzled Guy on 2009-11-25
Perl is pretty good (I'm an amateur Perl programmer myself)

Perl is a high-level (meaning it is like english), multi-purpose programming language. It's sorta like Python.

By the way, in Ubuntu, Perl and Python are both included in the updates so it's easy to get it. If you have installed all possible updates up to now, you probably have one or both of them already!

If you want more information, you could Google it or send me a message

---

### Post by openuniverse on 2009-11-25
.

---

### Post by nvteighen on 2009-11-25
> **CptPicard said:**
> 
**EDIT:** Oh yeah, it was my turn. Here is the task.

Devise a client-server application framework that can, for example and as an initial implementation, support web-based front ends. The browser-side should be an AJAX/Comet implemented GUI. 

The idea is to create a system where the application itself is written in the language of choice, without clearly separated "html view" and the request/response cycle to server side code. You must abstract the request/response away completely using AJAX. The GUI widgets on the browser must be represented as objects in the application development language. Think your usual GUI widget set in a desktop app.

Of course, the browser is immaterial, it can be replaced later with Silverlight or XUL or whatever. Interface to app stays the same.

The application must support real-time, simultaneous views of the same data from arbitrary numbers of clients. The model of the data must be implemented in terms of a software transactional memory that must be transparent, again in the application development language and API. Also, the same model data objects must be mapped on the fly to a database so they keep persistent.

Excluding the database or memory transactions or heavy processing in the app, the thing should support maybe 20,000 simultaneous clients on typical perhaps ca. 2005 commodity desktop hardware.

This needs to be written and maintained by one guy.

**(This thing actually exists...)**

[http://gitorious.org/symbolicweb](http://gitorious.org/symbolicweb) in Common Lisp :)

---

### Post by myrtle1908 on 2009-11-25
> **CptPicard said:**
> Not complex enough. Number-crunching algorithm implementations can be relatively straightforward implementation-wise. Sounds like C, in a little library. On the other hand I see no reason why the entire streaming application, regardless of what it streams could not find a nice implementation in Lisp. Even the encryption part should be quick enough when written in a more imperative style and type assertions. If that fails, I'll just use that library of mine, called from Lisp. Or even Python ;)

In particular, my implementation language will most definitely not be C++ because C++ essentially tends to force everything else to be C++ -- linking to C is far easier.

IMO I made a perfectly good reservation for the speed requirement in my statement earlier to account for something like this, anyway.

I do not believe in tossing around individual examples in this manner though; they are too specialized. You can always find some particular niche to push for something. You can't write J2EE applications in anything else than Java, for example. You can't write Linux kernel source in anything else but C, because it is already all C, and that in kernels, pointer arithmetic is actually of conceptual relevance.

In general, though, I fully sympathize with maximinus' remark about the imaginary "magic dust"... I share the frustration, and wonder how to communicate better about an issue that seems intractable to the low-level crowd. I've been here for years, and this topic pops up every now and then, with the exact same content... and it just leaves me with the impression that some people simply do not "see" why certain programming language designs are the way they are, and why they are conceptually very interesting, because their only metric is "does it go fast?". (Admittedly sometimes I would like to just conclude that they are talking about languages/ideas they do not know, but I give benefit of doubt :) -- anyway, [read this]("http://www.paulgraham.com/avg.html") )

I am fully willing to hack up something in C when the need arises, but it does not make the language any more interesting than a bunch of control statements, basic data types and a function call mechanism (the minimalism is actually a strength wrt. C++).

**EDIT:** Oh yeah, it was my turn. Here is the task.

Devise a client-server application framework that can, for example and as an initial implementation, support web-based front ends. The browser-side should be an AJAX/Comet implemented GUI. 

The idea is to create a system where the application itself is written in the language of choice, without clearly separated "html view" and the request/response cycle to server side code. You must abstract the request/response away completely using AJAX. The GUI widgets on the browser must be represented as objects in the application development language. Think your usual GUI widget set in a desktop app.

Of course, the browser is immaterial, it can be replaced later with Silverlight or XUL or whatever. Interface to app stays the same.

The application must support real-time, simultaneous views of the same data from arbitrary numbers of clients. The model of the data must be implemented in terms of a software transactional memory that must be transparent, again in the application development language and API. Also, the same model data objects must be mapped on the fly to a database so they keep persistent.

Excluding the database or memory transactions or heavy processing in the app, the thing should support maybe 20,000 simultaneous clients on typical perhaps ca. 2005 commodity desktop hardware.

This needs to be written and maintained by one guy.

(This thing actually exists...)

I too have written and maintain precisely this (less Comet) and have done so for the last ten years.  We are on our fifth version.  In version four we rolled in AJAX and ExtJS and now have a nice "single-page" web based application which is very successful.  Basically it is JS->JSON->JEE->Business Logic normally 4GL eg. Progress->Database.  It is so beautifully generic that we can slap any old front end onto it with little to no effort.

---

### Post by grayrainbow on 2009-11-25
> **Can+~ said:**
> I somehow feel that this degraded into a pissing contest. But ok, let's say:

[PHP]sudo apt-get install python-crypto[/PHP]

[PHP]import Crypto.Cipher.DES3[/PHP]

Oh wow, did I just installed the encryption algorithm on a single line? Yeah, because it's a known algorithm, done pretty much on every language, and what's best, is that this python module is C compiled, so I won't have to care much about penalties.

Also, my boss will probably say "great job", because I actually solved the problem, instead of wasting a work day while translating the wikipedia algorithm to C++.

I'm just that awesome. (In fact, I'll guess that C# and Java also have this libraries already done and optimized).

And if the algorithm weren't availabe, I would probably code it on C and plug it to the corresponding higher-level language. Why? Because, even the most speed-needy applications, it makes sense to write the "fast gears" on the fast language, and the other (possibly 90%) on the slow but with fast development time language.

That summarize it all.

P.S. I'm curious what people mean by "fast language?".

P.P.S. Design a web page...oh! crap! This things are done by designers nowadays. So I better go and learn some What You See Is What You Get tool.

---

### Post by maximinus_uk on 2009-11-25
> **grayrainbow said:**
> P.S. I'm curious what people mean by "fast language?".

Don't know about you, but computer time is real cheap but my time is expensive, so a fast language is one that lets me get the job done as fast as possible.

I was a machine code freak until the mid-90's though ;) - times change!

---

### Post by Arndt on 2009-11-25
> **maximinus_uk said:**
> Don't know about you, but computer time is real cheap but my time is expensive, so a fast language is one that lets me get the job done as fast as possible.

I was a machine code freak until the mid-90's though ;) - times change!

Presumably the users' time is worth something too.

---

### Post by grayrainbow on 2009-11-25
> **maximinus_uk said:**
> Don't know about you, but computer time is real cheap but my time is expensive, so a fast language is one that lets me get the job done as fast as possible.

I was a machine code freak until the mid-90's though ;) - times change!
Times changed, people don't ;)
Btw, if you do code for a living what Arndt sad take preference.

Anyway, fast typing...when is more likely to make mistake in your code, when you try "speed" writing or when you put more effort in understanding what you actually type(assuming you don't do something trivial)? Otherwise I'm really fan of GUI tools, especially for code organization, in the same time I don't underestimate bash.

---

### Post by maximinus_uk on 2009-11-26
> **Arndt said:**
> Presumably the users' time is worth something too.

Exactly! They can't run my code until I've written it, so the faster I get it written the sooner they can use it and solve their problem!

While I understand that 'it must be fast' could a technical specification, almost all the bottlenecks today are in I/O of some sort, or - if they are complex - dependent on the library you are using (unless you REALLY suck at programming and adopt a 'not coded here' approach).

---

### Post by CptPicard on 2009-11-27
> **myrtle1908 said:**
> I too have written and maintain precisely this (less Comet) and have done so for the last ten years. ...  It is so beautifully generic that we can slap any old front end onto it with little to no effort.

Nice. I was suspecting that you could get close to SymbolicWeb using some kind of J2EE-ORM-whatever-flexible-clientside-solution. However, you can't integrate it as nicely to an "application writing language" as Lisp can, unfortunately -- J2EE thingies are very very verbose as you well know.

@akvino, I don't want this to be a pissing contest either. I just am sometimes a bit annoyed by the attitude of the low-level crowd that automatically assumes that my (or other high-level-language programmers') preferences are due incompetence, while it is not apparent to me that they actually understand what non-C-languages actually do, and why, and why that is interesting. For example the coder of SymbolicWeb beats pants off, on low level too, of any programmer I know, and he's a fanatical Lisper exactly because of that. And most of Lisp critics would totally suck at "formulating programs" against him in any language...

---

