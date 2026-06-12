---
title: "want to learn new programming language, advice?"
date: 2009-06-06
forum: Programming Talk
---

### Post by rocketflame on 2009-06-06
I already know some Java, but wanted to learn a second one, more powerful. I was thinking C or C++. Does anybody know any good resources to start learning? any other advice (ex. good IDEs, etc.)?

any help would be appreciated :KS

---

### Post by hessiess on 2009-06-06
C++ isn't that differnt to java, you just have to manage your memory manually, and depending on the libs you are using, you may also need to use pointer math sometimes, which can be a little confusing.

Anouther language which I personally like is Lisp, simple and productive.

IDE's are bloatwere and overcomplicate everything, just use and editor like GEdit, Vim, Emacs etc.

---

### Post by jbruced on 2009-06-06
I found the tutorial at cplusplus.com very thorough.

btw, I got the Qt sdk and IDE for cross platform uses, and it's extensive libraries.

GL
Bruce

---

### Post by jimi_hendrix on 2009-06-06
As suggested above, common lisp.

it is very powerful and easy to use once you get the syntax down

---

### Post by kvarley on 2009-06-06
If you want to learn C++ you may want to consider learning the fundamentals of C as this will help you understand the base of the language.

Common lisp as suggested is also good.

---

### Post by Can+~ on 2009-06-06
> **rocketflame said:**
> ... more powerful. ...

Define "powerful".

Going low-level doesn't give you more power, it reduces your expressiveness as more instructions are needed to accomplish the same task.

Not saying that you shouldn't learn something new, but I'd be relieved to know that you are learning because you really want to, and not because "it's popular", "it's faster", "it's more manly to allocate your own memory", etc.

---

### Post by Mirge on 2009-06-06
Wouldn't bother with C unless you really wanted to or your project required it. I'd use C++. Also, I recommend using Geany for an IDE, very lightweight & productive. Absolutely love it.

Check out "Accelerated C++" if you choose C++. Highly recommended. Expert C Programming book just arrived... loaned out my first copy & never got it back. It's also a fantastic read, imo, if you are already using C.

---

### Post by simeon87 on 2009-06-06
> **Can+~ said:**
> Going low-level doesn't give you more power, it reduces your expressiveness as more instructions are needed to accomplish the same task.

I think you mean productivity rather than expressiveness here. The higher a programming language is, the less expressive it is as it limits the validity of sequences of statements. For example, suppose you have a low-level language with statements A, B and C and a high-level language that has statements C and D but D is actually a sequence of A and B. In the high-level language, you can now only write CDCDCDDDCCD and similar programs. Translated to the low-level language, you can only express sequences of A and B in order (when writing a D statement). But in the low-level language, you can also write B and A. This may not do anything useful but it's still possible which makes the low-level language more expressive than the high-level language. The high-level concepts simply predefine sequences of actions to allow you to reason at a higher level.

---

### Post by rasmus_ on 2009-06-06
I would recommend Eclipse CDT for C++ development. A small tip is using a separate workspace for each project. It has lots of nice refactoring features and great auto-complete.

I sometimes have to work in both Windows and Linux on the same project. Since Eclipse is supported by both platforms it gives me consistency. It also supports your Java projects ;)

I would also recommend using valgrind to check your programs memory management. It can easily be integrated with Eclipse.

---

### Post by rjack on 2009-06-06
[http://htdp.org/](http://htdp.org/)

---

### Post by Can+~ on 2009-06-06
> **simeon87 said:**
> I think you mean productivity rather than expressiveness here.

[http://en.wikipedia.org/wiki/Comparison_of_programming_languages#Expressiveness](http://en.wikipedia.org/wiki/Comparison_of_programming_languages#Expressiveness)

Expresiveness is not "how many tools do I have", is "how many things I can do with a each tool". (Although there isn't a consensual definition of "expresiveness" on a programming language)

Say you want to bubblesort, in assembly, this would take N lines. In C this would take a smaller number, and Python/Java/Perl, probably will be done in a few lines.

---

### Post by CptPicard on 2009-06-06
> **simeon87 said:**
> The higher a programming language is, the less expressive it is as it limits the validity of sequences of statements.

An interesting take on the meaning of expressiveness that I haven't heard before... well, I guess I just have to disagree with this here ;) If this were true, it would mean that just simple random binary sequences would be the most expressive, as they can theoretically express anything, but most of the sequences would of course be meaningless.

Of course, for the human reader, the binary sequence, valid or not, does not really express anything. I really much more prefer a high-level language that describes the program in more meaningful (hence, "expressive") terms.

> The high-level concepts simply predefine sequences of actions to allow you to reason at a higher level.

This is the "they are just library calls" argument. It really is not so... although all programming languages are theoretically equally powerful, some languages genuinely define concepts that require much more back-end machinery than just "predefined sequences of actions" and that represent ideas that are much "stronger" as general building blocks than just calls to some subroutine. Think higher-order functions and lambdas here in particular...

---

### Post by simeon87 on 2009-06-06
> **Can+~ said:**
> [http://en.wikipedia.org/wiki/Comparison_of_programming_languages#Expressiveness](http://en.wikipedia.org/wiki/Comparison_of_programming_languages#Expressiveness)

Expresiveness is not "how many tools do I have", is "how many things I can do with a each tool". (Although there isn't a consensual definition of "expresiveness" on a programming language)

Say you want to bubblesort, in assembly, this would take N lines. In C this would take a smaller number, and Python/Java/Perl, probably will be done in a few lines.

That's also a way to view it. You can express more per line in a high-level language so in that respect the expressiveness is higher. It's just how we define 'expressiveness' in the end. Any sufficiently complex language is equally expressive as other languages in terms of what it can compute (a definition of the word 'expressive' in this sentence would involve Turing completeness of course).

> **CptPicard said:**
> An interesting take on the meaning of expressiveness that I haven't heard before... well, I guess I just have to disagree with this here ;) If this were true, it would mean that just simple random binary sequences would be the most expressive, as they can theoretically express anything, but most of the sequences would of course be meaningless.

That's what I intended to say: high-level languages are a subset of the set of languages as they place constraints on the sequences of statements that you can write.

Also, the meaningfulness of a sequence just depends on how you define what a sequence means: if you give a meaning to every possible sequence, then each sequence can be used to express something. But I would agree that most binary sequences, in practice, don't correspond to any sentence in an existing language.

> **CptPicard said:**
> Of course, for the human reader, the binary sequence, valid or not, does not really express anything. I really much more prefer a high-level language that describes the program in more meaningful (hence, "expressive") terms.

I'm not arguing to use a low-level language as I wouldn't wanna miss the ideas from functional programming :)

> **CptPicard said:**
> This is the "they are just library calls" argument. It really is not so... although all programming languages are theoretically equally powerful, some languages genuinely define concepts that require much more back-end machinery than just "predefined sequences of actions" and that represent ideas that are much "stronger" as general building blocks than just calls to some subroutine. Think higher-order functions and lambdas here in particular...

Well, I wasn't thinking of library/subroutine calls when I wrote it (though what I wrote indeed leads one to read it that way). Even these ideas from functional programming ultimately result in sequences of statements, perhaps very complex and interleaved with statements from the program but nonetheless they result in sequence(s) of statements of a lower level language. A simple high-level language would give names to a group of low-level statements and make these names available as statements in the high-level language. In an advanced high-level language, it may be tricky to determine how to get from the abstract ideas and concepts to the sequence of instructions that the computer should execute but the same principle still holds.

---

### Post by rocketflame on 2009-06-07
alright, c++ seems to be the the most popular, though i'll check out lisp as well. thanks for the advice! but as i said, i am just learning, so the second half of this thread is beyond me... oh well. one day.

---

### Post by Nemooo on 2009-06-07
Coming from Java you want gain a lot from learning C++ besides new syntax, as it's a language encouraging OOP, (although it strictly speaking is a multiparadigm programming language) just as Java.

If you want to learn C++, because of low level programming, you would be better off with C, as it's low level all over, not trying to be both high and low at the same time (like C++). Plus it's imperative instead of OO.

Lisp like languages will be much more of an eye opener than C and C++, as they're typically encouraging a functional paradigm, which requires a new and in a sense a more pure way of programming. In strictly functional programming (like Haskell), functions can't have [side effects]("http://en.wikipedia.org/wiki/Side-effect_(computer_science)").


C++ is of course a good choice, as it's widely used, but seen from an educational point of view, you'd get more out of learning a different paradigm.

---

### Post by CptPicard on 2009-06-07
Hmm, first of all what we must do is just get out of the Turing tarpit -- all Turing-complete languages can be used to produce sequences of whatever symbols they contain to compute and emulate any other language. So in that sense it is really important to note that you can indeed trivially express, say, a CPU emulator for some simple machine code in a functional-programming language, and I that emulator is probably much briefer and clearer than a FP-language written in machine code.

IMO the Turing-completeness argument in itself is such an "obvious" point that not much can be gained in the expressiveness discussion by making use of it. We are talking about those things in the language that interface with the human programmer at the parts of the program which are *not* "machine-handleable" according to the Turing-completeness language equivalence principle. It is the "what the machine can't do" that we are interested in handling by the programming language -- the "how to inject the human thought into this.." part.

I have always failed to see something like assembly as anything else than just another program description formalism -- and a fairly non-descriptive one at that. You really need to run it in your head to get a picture of what the program is. It does happen to run on the hardware but from the program perspective this is not meaningful (see Turing-completeness, again).

Languages need to be seen for what they are, independently, instead of in implementation terms as some sort of layers on top of hardware. And the "sequences of actions" view is just way too procedural-imperative for my taste... we could think of this humongous library that contains all the possible programs in the world (ok, it would be an infinite library) with a subroutine for everything. I would fail to see this as "expressive" even though certainly programs would be one-liners.

I think Can+~ put it best... it is not the amount of explicitly defined stuff, it the stuff you can do with a hopefully minimal yet powerful (in the sense you don't need a million of them for everything, and a special recombination for all cases) set of recombinable primitives that brings expressive power.

Lisp comes to mind again but I guess I would come across as drooling a bit too much... ;)

---

### Post by Can+~ on 2009-06-07
Well, I'm done with the "expresiveness" subject, onto the OP:

I say, instead of C++, go for C.  C++ is a mix of Object Oriented with Imperative programming, but the mixture is so awkward that you'll probably screw up a lot because you come from Java.

For instance, C++ has all this OOP features, but has no Garbage Collector, so you'll run into memory leaks without anybody telling you about them. Having "pointers" presented the first time is confusing, and having your abstract knowledge of classes onto the mix is no help at all.

On the other hand, C will teach you pretty much everything you need to know about C++ "Imperativeness" without those mind clashes.

Too bad that you ended up choosing by popularity.

---

### Post by soltanis on 2009-06-07
Not to mention C is a language you could reasonably expect to know the entirety of. Not true of C++.

---

### Post by Mirge on 2009-06-07
> **soltanis said:**
> Not to mention C is a language you could reasonably expect to know the entirety of. Not true of C++.

Why could one not know the entirety of C++? Not arguing, just wondering.

C++'s syntax, reserved words, etc seems relatively small... you don't HAVE to memorize the entire STL, etc.

---

### Post by soltanis on 2009-06-07
Libraries aside (which in C are pretty consistent and not difficult to memorize), C++ has a load of other features people don't know exist. Most C++ books don't teach you the whole language; most people who use C++ actually only use a small subset of it.

Especially with the much anticipated C++0x with the apparently ten thousand new features it's adding, it seems pretty evident that no one is going to understand every cobwebbed corner of this overgrown language in the future.

---

### Post by rocketflame on 2009-06-08
so now i'm hearing a lot more "C", but if C is better/easier to learn, and not confused about what it wants to be, why is c++ more popular?

Without saying "well M$ windows is more widely used then *NIX" or "Mcdonalds is really popular" please :)

---

### Post by JordyD on 2009-06-08
> **rocketflame said:**
> so now i'm hearing a lot more "C", but if C is better/easier to learn, and not confused about what it wants to be, why is c++ more popular?

Without saying "well M$ windows is more widely used then *NIX" or "Mcdonalds is really popular" please :)

Probably because C++ is more object-oriented and C is more procedural (just guessing here). Object oriented languages (or so I hear) are easier to maintain when you have larger projects than procedural, but they run slower than procedural. C++, though, doesn't force you to use object oriented features, it just provides them. Besides that, C and C++ are about the same in terms of speed, according to benchmarks I've been reading lately.

---

### Post by Mirge on 2009-06-08
Eh I dunno, I am familiar with C more than I am C++ (which doesn't say a whole lot to be blatantly honest... I'm not EXPERIENCED with either, I'm a web-developer)...

But what turned me onto C++ was seemingly more resources & documentation readily available... and the ease of use / development time.

Also, the problem of buffer overflows seems to constantly come up wtih C. Well not really come up, but you REALLY have to watch for it. I guess because C is lower level than C++... many things are very abstract in C++, which to an extent I do appreciate and enjoy.

string some_string;
getline(cin, some_string);

Awesome... automatically handles the length for me.

char some_string[100];
scanf("%s", some_string);

If person enters a string over 99 characters long (can't forget the \0)... unexpected results can happen.

---

### Post by rocketflame on 2009-06-08
really? thats a pain! so if you are taking some kind of user input, how are you supposed to know how long the string is? you cant just make it 999999999999999999999...

sorry- just noticed, strings are arrays of chars in C? thats... not exactly a string...

---

### Post by Mirge on 2009-06-08
> **rocketflame said:**
> really? thats a pain! so if you are taking some kind of user input, how are you supposed to know how long the string is? you cant just make it 999999999999999999999...

sorry- just noticed, strings are arrays of chars in C? thats... not exactly a string...

Well, those are C strings... and there are functions that can limit the user input to a safe (ie: allocated) amount.

fscanf() being one of them I believe.

But yeah, that's an example of why I enjoy C++ moreso than C. Some hardcore C users may frown upon that, but that's just how I feel. C++ offers me more than C does... which really IS a double edged sword. C syntax can be learned extremely quickly because it's a relatively small language... but you find yourself writing functions for stuff that C++ offers (likely in a better fashion than your user-created functions) right from the get-go. Just my .02 cents.

FYI, if you need more space, you can use malloc() to dynamically attempt to allocate more memory in C.

---

### Post by JordyD on 2009-06-08
> **rocketflame said:**
> really? thats a pain! so if you are taking some kind of user input, how are you supposed to know how long the string is? you cant just make it 999999999999999999999...

sorry- just noticed, strings are arrays of chars in C? thats... not exactly a string...

Actually, it is exactly a string. Even in C++ it's a string, they just have a nice new name for it.

And if you make a string with the length of 9999999999999999999..., then your program will take up a ton of RAM. It has to allocate memory for things, which is why you declare variables in the first place. C++ just has some behind-the-scenes management for it's string (class, is it?).

---

### Post by Mirge on 2009-06-08
> **JordyD said:**
> Actually, it is exactly a string. Even in C++ it's a string, they just have a nice new name for it.

And if you make a string with the length of 9999999999999999999..., then your program will take up a ton of RAM. It has to allocate memory for things, which is why you declare variables in the first place. C++ just has some behind-the-scenes management for it's string (class, is it?).

I assume string is a class, it has methods associated with it (ie: string foobar = "yadda yadda"; cout << foobar.length() << endl; -- .length() being an alias of .size()).

I've heard "template" being tossed around with strings too, but I don't honestly know enough to know better.

And yeah, definitely do NOT create an array of characters with that many elements haha.

---

### Post by rocketflame on 2009-06-08
> **Mirge said:**
> 
FYI, if you need more space, you can use malloc() to dynamically attempt to allocate more memory in C.

you can "attempt"??

is there stability problems, or is it just lower-level with less **** automatically built in?

now i'm just getting confused... do one of the languages really have any advantages over the other, or is it just preference? :o

BTW thanks for everybody's help, I really appreciate the input. :)

---

### Post by Mirge on 2009-06-08
Yes, attempt. You're not guaranteed memory when you call malloc()... RAM is not an infinite source of memory.. there's a limit. Some will have less than others.

As a (poor) example, if your computer has 512MB of RAM, and you're using 511.9MB... and you are trying to allocate more RAM than is available, it could fail. So you should always check the return value of malloc() in C.

Getting a straight answer for C vs C++ is not really as "easy" as it might seem. A lot depends on the project you're working on, or projects you will be working on.

If you aren't going to be working on something that is built with C or will be heavily involving C, my personal preference is C++. If you were going to go diving into the Linux kernel, scrap C++ and learn C.

---

### Post by JordyD on 2009-06-08
> **rocketflame said:**
> you can "attempt"??

is there stability problems, or is it just lower-level with less **** automatically built in?

now i'm just getting confused... do one of the languages really have any advantages over the other, or is it just preference? :o

BTW thanks for everybody's help, I really appreciate the input. :)

It's mostly preference. But I think as a beginner you would prefer C++. It manages strings behind-the-scenes, while C doesn't.

Also, I'd say that higher level languages are easier to deal with than lower ones, and C++ can be either of those.

---

### Post by rocketflame on 2009-06-08
sounds good... i dont have loads of java experience either, so this will make for an *educational* summer break, once my exams are done

~Thanks again, C++ it is

---

### Post by CptPicard on 2009-06-08
> **JordyD said:**
> 
Also, I'd say that higher level languages are easier to deal with than lower ones, and C++ can be either of those.

The issue is that C++ is both at the same time, and in particular makes you do OOP in an essentially low-level language context... and that it's not all that high-level in a lot of ways anyway.

HLLs may be easier to deal with in the pure manual-labour sense, but they also come with a lot of interesting concepts that are easier to approach as you don't have to write an interpreter to get them... for example, Scheme is trivial to "use", but very flexible to actually code in...

---

### Post by HavocXphere on 2009-06-08
I'd suggest starting by figuring out how critical raw processing speed is in whatever it is you will be coding.

Raw speed important -> C, C++, ASM etc
Ease of use & productivity important -> Python, Java, Ruby etc

Trying to code a main loop of the GFX engine in Python is suicide. On the other side programming a massive financial app in ASM is also suicide.

I'd suggest going for something fairly high-level, but making sure that the language makes it easy to do the sections where speed is needed in something else (Either directly in ASM, or via DLLs).

EDIT: I see you've chosen C++. :)

---

### Post by CptPicard on 2009-06-08
> **HavocXphere said:**
> 
I'd suggest going for something fairly high-level, but making sure that the language makes it easy to do the sections where speed is needed in something else (Either directly in ASM, or via DLLs).


Interestingly, this would probably be Common Lisp. Very high-level and abstract language, but lets you actually exercise fairly fine-grained control over the generated machine code if you so choose.

It should be noted though that the "w00t, write raw asm for speed!!1" argument usually comes from speed kiddy n00bs. Compilers do a great job at code generation and optimization, and the lowest you generally need to go is C unless you're writing something very device-specific.

---

### Post by Mirge on 2009-06-08
> **CptPicard said:**
> Interestingly, this would probably be Common Lisp. Very high-level and abstract language, but lets you actually exercise fairly fine-grained control over the generated machine code if you so choose.

It should be noted though that the "w00t, write raw asm for speed!!1" argument usually comes from _**speed kiddy n00bs**_. Compilers do a great job at code generation and optimization, and the lowest you generally need to go is C unless you're writing something very device-specific.

[IMG]http://i20.tinypic.com/106x6vc.jpg[/IMG]

---

### Post by Can+~ on 2009-06-08
> **rocketflame said:**
> sorry- just noticed, strings are arrays of chars in C? thats... not exactly a string...

Strings are array of chars in every language, the only difference is that any decent high level language worth it's salt will has a "String" class which handles common tasks.

---

### Post by Sinkingships7 on 2009-06-09
> **Can+~ said:**
> Strings are array of chars in every language, the only difference is that any decent high level language worth it's salt will has a "String" class which handles common tasks.

I advise everyone to read this three times and take a bit with breakfast.

There is no spoon.

To the OP: I recommend avoiding C++ like the plague. The effort you put into it probably won't be worth the results you get out of it. On the other hand, if you're young, learning it now could get you a nice, high-paying job maintaining and porting it in the future. ;)

---

### Post by Mirge on 2009-06-09
> **Sinkingships7 said:**
> I advise everyone to read this three times and take a bit with breakfast.

There is no spoon.

To the OP: I recommend avoiding C++ like the plague. The effort you put into it probably won't be worth the results you get out of it. On the other hand, if you're young, learning it now could get you a nice, high-paying job maintaining and porting it in the future. ;)

Why should you avoid C++ like the plague? Just curious.

---

### Post by Sinkingships7 on 2009-06-09
> **Mirge said:**
> Why should you avoid C++ like the plague? Just curious.

C++ is what many people consider to be a "hybrid" language. It attempts to mix low-level features and mid/high-level features. In its endeavor to be the one-language-to-rule-them-all, it manages to be too low-level to be easy to read and write, and provides sad wannabe high-level functionality. It gives you just enough rope to hang yourself with and not enough common sense to decide against it.

C+~'s signature puts it nicely: "C++: an octopus made by nailing extra legs onto a dog."

If you give this website a good look, it can tell you exactly what I mean: [http://yosefk.com/c++fqa/](http://yosefk.com/c++fqa/)
If you're too lazy to read the site, just take a good glance at this page: [http://yosefk.com/c++fqa/picture.html](http://yosefk.com/c++fqa/picture.html)

---

### Post by CptPicard on 2009-06-09
That said, C++ has its place, if not only for the reason that it still is used a lot and in many cases it's a tool that gets your job done, if not in utopian, perfect way. 

On this forum however a lot of the questions are of the form "how do I learn to be a better programmer", and I strongly feel there are better answers to that than C++... with C++ you learn "how to use C++" and the general programming enlightenment can end up being secondary...

---

### Post by Mirge on 2009-06-09
Ok thanks for the explanations. I'll keep those in mind moving forward. :)

---

### Post by rocketflame on 2009-06-10
yup, thanks from me as well.  Never thought it would turn into a *near* language flame war

---

### Post by Mirge on 2009-06-10
Oh btw, sorry rocketflame, I didn't mean to kinda hijack your thread lol...I sent you a PM btw.

---

