---
title: "C or C++?"
date: 2007-01-24
forum: Programming Talk
---

### Post by erikcw on 2007-01-24
Hi all,

I'd like to learn C and/or C++, but I'm not sure which one I should go with.  Does it make more sense to gain proficiency with C first and then move onto C++, or the other way around?  By learning C++ will I be learning C at the same time?

Thanks!

---

### Post by Wybiral on 2007-01-24
Actually, it's kindof awkward to jump between C/C++... They have a different way of doing things, but the language is so similar that I often mix stuff up if I have to jump too much. I would say to pick one for now, worry about the other later.

---

### Post by kj1h234lkj1234 on 2007-01-24
Once you know one well, "learning" the other is trivial.

I learned C++ first, and it only took a few days of reading to learn the different ways that C does things.

Feel free to see which you'd prefer first:

[C in 21 days](http://www.utdallas.edu/~mdg061000/)

[C++ in 21 days](http://newdata.box.sk/bx/c/index.htm)

Good luck!

---

### Post by ssalman on 2007-01-24
Learning C is a prerequisite of learning C++ as the C is a subset of C++.... You can of course jump right into C++, but anyway you do it, you'll be learning C basics first, weather you know it or not  ;)

However, learning C only will not get you anywhere in C++. For small projects and things requiring "raw" speed use C, for medium to large projects... and to make your program a little bit more organized, use c++.

hope this helps.

---

### Post by Wybiral on 2007-01-24
I don't think you need to learn C first at all... I learned C++ first. But, after having the luxuries of C++ (mostly classes, classes are a beautiful thing) it was hard to shave that off and start learning C. But, then again... If I learned C first, it would probably be hard to break it's habits too.

I guess my point is that you can learn either, but I would only worry about one of them. Worry about learning the other later...

> For small projects and things requiring "raw" speed use C, for medium to large projects... and to make your program a little bit more organized, use c++.

I agree with this statement... I wish I were better at large projects in C, but C++ makes things much easier to read/manage/organize... But, C compiles much cleaner/smaller and generally runs a bit faster.

---

### Post by maxamillion on 2007-01-24
> **ssalman said:**
> Learning C is a prerequisite of learning C++ as the C is a subset of C++.... You can of course jump right into C++, but anyway you do it, you'll be learning C basics first, weather you know it or not  ;)

However, learning C only will not get you anywhere in C++. For small projects and things requiring "raw" speed use C, for medium to large projects... and to make your program a little bit more organized, use c++.

hope this helps.

C is not a subset of C++, Against popular belief, the two languages are completely separate. There are many similarities between the two because C++ was derived from C with an object oriented implementation. [http://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B](http://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B)

I recommend C, but at the same time I don't ... there is more room for you to shoot yourself in the foot because of the way it does (or actually doesn't) do things like type casting. It also will allow you to reference a memory address of the stack from within a function and therefore referencing a local variable with global scope which will provide interesting results...

for example:
```
int *x;

void f(){
int y = 1;
x = &y;
}

void g(){
int y = 400;
}

void main(){
f();
printf("%d \n", *x);
g();
printf("%d \n", *x);
}
```


... anyways, C is a very good and powerful language that I think every programmer should learn but there are also data structures and certain characteristics of the system that should also be understood by the programmer.

I guess the point of this is ... learn C, learn it well ... you will thank yourself for it later.

</rant>

---

### Post by ssalman on 2007-01-24
> **maxamillion said:**
> C is not a subset of C++, Against popular belief, the two languages are completely separate. There are many similarities between the two because C++ was derived from C with an object oriented implementation. [http://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B]("http://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B")


I don't mean to be a troll ;)

but the link you provided confirms exactly what I have said, and does not support your statement above! ... here is the quote "The [C]("http://en.wikipedia.org/wiki/C_programming_language") and [C++]("http://en.wikipedia.org/wiki/C%2B%2B") [programming languages]("http://en.wikipedia.org/wiki/Programming_languages") are closely related. C++ grew out of C and is mostly a _***superset ***_of the latter"

again, not trolling... but want to clarify the difference...


[edit]

let me clarify even more, what I'm disagreeing on is the "C is not a subset of C++" statement, I actually agree with maxamillion that C and C++ are completely separate languages.

---

### Post by lnostdal on 2007-01-24
..then again "mostly" is not the same as "not at all" or "completely"..

Especially C99 has a couple of things not part of C++.

edit:
To the OP: Learn C. When high-level requirements turn up use something else than a hybrid like C++. Use something that is cleaner. It is easy to interface with C from a high-level language, the same can not be said about C++ at all. You'll have both the clarity of a proper, non-hybrid high-level language and the speed of C whenever it is needed.

---

### Post by Wybiral on 2007-01-24
> **lnostdal said:**
> ..then again "mostly" is not the same as "not at all" or "completely"..

Especially C99 has a couple of things not part of C++.

edit:
To the OP: Learn C. When high-level requirements turn up use something else than a hybrid like C++. Use something that is cleaner. It is easy to interface with C from a high-level language, the same can not be said about C++ at all. You'll have both the clarity of a proper, non-hybrid high-level language and the speed of C whenever it is needed.

Actually, (I'm not trying to prove you wrong or anything)... But some HL languages are easier to interface with C++ than C... The prime example that comes to mind is python, C++ and Python were meant for each other... They can even trade objects/class between one-another at runtime. But generally, yeah, most libraries/modules for HL languages are written in C... Heck, most HL languages are written in C.

C++ may be a "hybrid" but I think it shares quite a large number of traits with python.

---

### Post by lnostdal on 2007-01-24
Erm .. just no -- I find what you say very hard to believe. Python has better support for interfacing with C++ than C? .. No way.

I don't know about the "mostly" when it comes to what HLLs are written in either; a lot of the ones I've used (hum, well - mostly Lisp .. but most of the implementations then) has maybe had a small core written in C with the rest written in the HLL itself. Python has different implementations using different languages besides the standard one which is written in C (well; some standard libraries are written in Python itself I think).

---

### Post by Wybiral on 2007-01-24
> Erm .. just no -- I find what you say very hard to believe. Python has better support for interfacing with C++ than C? .. No way.

The *support* is the same... Exactly the same, they use the same library. But the language similarities between C++ and Python are closer than C and Python. C has no class structures to interface with, whereas C++ does, and you can actually share class structures/operator overloads with a proper C++/Python interface. I'm not saying the actual support for C++ is greater, I'm saying that the languages have more in common and it's much easier to communicate objects between them.

EDIT:

> I don't know about the "mostly" when it comes to what HLLs are written in either; a lot of the ones I've used (hum, well - mostly Lisp .. but most of the implementations then) has maybe had a small core written in C with the rest written in the HLL itself. Python has different implementations using different languages besides the standard one which is written in C (well; some standard libraries are written in Python itself I think).

You just said that the *core* of most lisp was written in C?
And the standard python?
And *most* of it's modules?
I didn't say *all* HLL's I said MOST, as in, large percentage wise...
Look some of them up, I wasn't kidding, a lot of them were written in C.

---

### Post by jblebrun on 2007-01-24
> **Wybiral said:**
> The *support* is the same... Exactly the same, they use the same library. But the language similarities between C++ and Python are closer than C and Python. C has no class structures to interface with, whereas C++ does, and you can actually share class structures/operator overloads with a proper C++/Python interface. I'm not saying the actual support for C++ is greater, I'm saying that the languages have more in common and it's much easier to communicate objects between them.



Are you talking about using SWIG/SIP to interface Python and C++?

---

### Post by Wybiral on 2007-01-24
No, I was talking about plain old "python.h"
I've messed with boost, not SWIG/SIP
But python.h gives you access to the python dictionary where you can remove and alter objects in the python interpreter that is running (dynamically). Including "globals" or objects shared throughout the script, and yes... Even class objects.

---

### Post by jblebrun on 2007-01-24
> **Wybiral said:**
> 

I agree with this statement... I wish I were better at large projects in C, but C++ makes things much easier to read/manage/organize... But, C compiles much cleaner/smaller and generally runs a bit faster.

In my experience, large projects written *well* in C are just as easy to manage as those written *well* in C++.

---

### Post by jblebrun on 2007-01-24
> **Wybiral said:**
> No, I was talking about plain old "python.h"
I've messed with boost, not SWIG/SIP
But python.h gives you access to the python dictionary where you can remove and alter objects in the python interpreter that is running (dynamically). Including "globals" or objects shared throughout the script, and yes... Even class objects.

I was looking in the Python docs for examples of passing C++ objects to and from Python, but the python.org docs that I can find are not very informative. Do you know any good tutorials/howtos on this?

---

### Post by nenetwork on 2007-01-24
I have been using the Microsoft training, it costs about $30 for a months pass to download the training videos and its well worth it.

---

### Post by lnostdal on 2007-01-24
lol .. hilarious .. I'd rather kill myself than interface with C++ at a level above simple functions using extern "C". It's way painful enough to interface with plain C. Your wasting peoples time by telling them interfacing with C++ is actually something that is feasible or "easier because C++ and Python has more HL features in common than C" ("hey; that seems to make sense -- i'll say it!") and adding to it saying that it's easier than interfacing with C.

If your C has gone C++ and now has started overlapping what you'd want in your cleaner HLL you've already gone to far with the C++-part and should have switched to your HLL wayway earlier (I'd say as soon as your C started going C++) while you had the chance to interface properly.

STFU and/or get out of my face; your naivety and babbling annoys me.

---

### Post by pmasiar on 2007-01-24
> **lnostdal said:**
> (...)  most of the implementations then) has maybe had a small core written in C with the rest written in the HLL itself. Python has different implementations using different languages besides the standard one which is written in C (well; some standard libraries are written in Python itself I think).

Python has implementation on top of C, java (Jython), and .NET (IronPython). Experimental implementation on top of (subset of) Python -  [PyPy]("http://en.wikipedia.org/wiki/Pypy") is financed by EU as research project - but they say that having thing implemented in Python allows for simpler experimenting with internals.

---

### Post by Wybiral on 2007-01-24
> **jblebrun said:**
> In my experience, large projects written *well* in C are just as easy to manage as those written *well* in C++.

I'm not doubting you... It's just that certain things are much easier for *me* to handle in C++
First example that comes to mind is a 3d vector class...

```

class vec3 {
    float v[3];
    vec3(float x, float y, float z){
        v[0] = x;
        v[1] = y;
        v[2] = z;
    }
    vec3 operator+(vec3 b){
        return vec3(v[0]+b.v[0], v[1]+b.v[1], v[2]+b.v[2]);
    }
...
};

```

So, in C++, using operator overloads and user defined objects I could say...

myVec = crossProduct(aVec + bVec, bVec * 0.5);

But in C, I would have to use structures and it would probably not be nearly as readable or manageable...

myVec = crossProduct(VecVecAdd(aVec, bVec), VecFloMult(bVec, 0.5));

You get the picture... And that's just a light version of an equation using user object types. Wait until you start throwing matrices in the mix... You will realize why C becomes slightly more challenging to read/manage... With classes/operator overloads you can view the objects as text-book math... You can check the equation much easier for flaws/bugs/optimizations.

But yeah... If you are more efficient in C, probably more power too you. C compiles much cleaner, if you've ever had to look at an assembly dump you will know this...

This makes optimizing easier. It also compiles slightly smaller, and I personally feel that it's even slightly faster... This is an opinion, I am not saying 100% that it is. I think it's because C doesn't have as much baggage/overhead as C++

---

### Post by Wybiral on 2007-01-24
> **lnostdal said:**
> lol .. hilareous .. I'd rather kill myself than interface with C++ at a level above plain functions/extern "C". It's way painfull enough to interface with plain C. Your wasting peoples time by saying that interfacing with C++ is actually something that is trivial and adding to it saying that it's easyer than interfacing with C.

STFU and/or get out of my face; your naivety annoys me.

lmao!

It is trivial... You don't even need extern "C"

If you're writing a python module, you just have to compile it as a shared object... Nothing special. And the code isn't special either.

Look lnostdal, I don't know what your problem is with me, but it seems like you automatically get all huffy out when I bring up somewhat of an opposing point (this time it wasn't even OPPOSING, I was just adding to the thread by mentioning that with some languages it's easier/just as easy). I don't see how I'm "in your face"... This is a public forum and I was just saying that it isn't hard to interface C++ with python... Cry about it.

There is a good example of class interfacing here, but it's with boost...
[http://www.codesampler.com/python.htm](http://www.codesampler.com/python.htm)

But, I can assure you it is 100% possible, I've seen it done simply through dictionary modification.

Anyway, embedding/interfacing/module writing with python is EXTREMELY easy... Even without Boost/swig. Python.h offers you a great interface for C/C++ and thats not even with a library like the ones mentioned which make it even easier!

I know Boost can easily interface classes with python, but I have seen it done, I just don't remember exactly how to do it... But you can create sortof replica's of C++ classes that are usable in python.

But... Regardless, even without class interfacing it's just as easy to interface languages like python/lua/ruby/perl/Javascript in C++ as it is C.

I'm just saying that C isn't _easier_ to interface than C++ (most of the time)

BTW, I posted some examples of C++/Python interfacing a while back as a joke... [http://ubuntuforums.org/showthread.php?t=324544&highlight=c+met+python](http://ubuntuforums.org/showthread.php?t=324544&highlight=c+met+python)
You will notice the this requires no extra code than it would in C...

---

### Post by jblebrun on 2007-01-24
> **Wybiral said:**
> 
BTW, I posted some examples of C++/Python interfacing a while back as a joke... [http://ubuntuforums.org/showthread.php?t=324544&highlight=c+met+python](http://ubuntuforums.org/showthread.php?t=324544&highlight=c+met+python)
You will notice the this requires no extra code than it would in C...

None of these examples show any objects being passed back and forth between C++ and Python... they all just call functions just as you could do in C. The Python objects are still received as structs, not C++ objects. 

Also, I took a look at your viper code. I changed the "g++" to "gcc" in your compile script, and it compiled perfectly as is.  So this is just C code with a .cc suffix. 

So, still waiting for an example of "trivial" interfacing of C++ objects and Python objects, using only Python.h.

---

### Post by lnostdal on 2007-01-24
Post some real examples, wyb. Interface with C++ libraries that require you to subclass to define behaviour .. something that requires/uses template meta programming for the same reasons ... whatever .. use your friggin imagination, you're supposed to be a programmer. You're missing so many details I don't know where to begin. You've only got a superficial knowledge of things and quote the feature-lists of something you've read as facts without having any deeper insight. Don't expect me to provide it for you; instead read what I say and think "hmm - k" (even regard me as a fool if you like; I do not care what you think) then post your opinion to the OP while disregarding mine. Even if a solution is provided in C++ ("omg - the feature lists!") I know what they imply in practice and it does not deliver what is promised for its given price in some blabla context. I'm so certain of this that I can predict with 100% certainty this for all future in context with the C++-world. It's like math -- the core of the calculation is flawed and thus _anything_ you add to it will just accumulate and add to what in the beginning was a wrong.

_Nothing_ you're saying is new to me or is an opinion or thought I've not once used to have my self! In short; I .. do .. not .. care! You are boring the cræp out of me!

I'd rather not waste any more time on your boring, stupid and plain wrong babbling -- but your stupid sh1t annoys me like nothing else when you're quoting me. Quote the OP and answer him/her and stay the hell out of my view of things.

---

### Post by LordHunter317 on 2007-01-24
> **erikcw said:**
> I'd like to learn C and/or C++, but I'm not sure which one I should go with.I'd learn C++ personally, but do what you will.

> Does it make more sense to gain proficiency with C first and then move onto C++, or the other way around?  By learning C++ will I be learning C at the same time?No, no, and no.  The only carryover is some syntax, which is rather useless.

[quote=Wybrial]But, C compiles much cleaner/smaller and generally runs a bit faster.[/quote]Actually in many cases it's slower because of the limited expressiveness and the inability for the compiler to make the same optimizations.

>  But some HL languages are easier to interface with C++ than C... The prime example that comes to mind is python, C++ and Python were meant for each other... This is almost universally false.  C++ is the hardest language to interface with naything else.  C is probably the easiest.

C and Python link together quite well, given the main python interpreter is written in it.

---

### Post by ansi on 2007-01-24
> **jblebrun said:**
> In my experience, large projects written *well* in C are just as easy to manage as those written *well* in C++.

Not agree. I'm not a fan of C, but I very like it, sometimes more than C++ ;). And I do not agree about easy managing C-written projects. In C++ when you have a commented tree of classes, it is easy understandable than the same tree, but for C program. IMO.

And, I believe, that good or bad project managing depends on good SRS's, described usecases etc., and as late as depends on chosen language.

---

### Post by Wybiral on 2007-01-24
> **lnostdal said:**
> Post some real examples, wyb. Interface with C++ libraries that require you to subclass to define behaviour .. something that requires/uses template meta programming for the same reasons ... whatever .. use your friggin imagination, you're supposed to be a programmer. You're missing so many details I don't know where to begin. You've only got a superficial knowledge of things and quote the feature-lists of something you've read as facts without having any deeper insight. Don't expect me to provide it for you; instead read what I say and think "hmm - k" (even regard me as a fool if you like; I do not care what you think) then post your opinion to the OP while disregarding mine. Even if a solution is provided in C++ ("omg - the feature lists!") I know what they imply in practice and it does not deliver what is promised for its given price in some blabla context. I'm so certain of this that I can predict with 100% certainty this for all future in context with the C++-world. It's like math -- the core of the calculation is flawed and thus _anything_ you add to it will just accumulate and add to what in the beginning was a wrong.

_Nothing_ you're saying is new to me or is an opinion or thought I've not once used to have my self! In short; I .. do .. not .. care! You are boring the cræp out of me!

I'd rather not waste any more time on your boring, stupid and plain wrong babbling -- but your stupid sh1t annoys me like nothing else when you're quoting me...

hmm - k :KS

In regards to the original post...
There's really nothing wrong with C++, I use it, I know a ton of people who use it's not hard to learn. I can assure you that HLL interfacing isn't any harder in C++ than in C (they generally use the same libraries... The same commands...) Actually, I've never seen a post by lnostdal regarding C++ when he wasn't blatantly crapping on it for no reason. More often than not, C++ offers a good enough STL and structure in-and-of itself to not need to interface a HLL.

C is good too... It's certainly worth learning as it's used CONSTANTLY for low level stuff and number crunching routines... As a matter of fact, most of the linux executables that come with Ubuntu were written in C. ls, cd, pwd, all of these basic programs. C programs compile very cleanly and generally more optimized than C++, (yes I can show you some assembly dumps to prove that C compiles cleaner)

I probably shouldn't say nice things about compiled programs in these forums though (a lot of people on these forums are anti-compile evangelists) even while probably more than 90% of the beautiful, fast, nicely working, memory managing system they are using at-this-moment was written in C and compiled.

---

### Post by Mirrorball on 2007-01-24
> **jblebrun said:**
> Also, I took a look at your viper code. I changed the "g++" to "gcc" in your compile script, and it compiled perfectly as is.  So this is just C code with a .cc suffix.
This is because gcc detects the .cc suffix and compiles the file as C++ code.

---

### Post by jblebrun on 2007-01-24
> **ansi said:**
> Not agree. I'm not a fan of C, but I very like it, sometimes more than C++ ;). And I do not agree about easy managing C-written projects. In C++ when you have a commented tree of classes, it is easy understandable than the same tree, but for C program. IMO.

And, I believe, that good or bad project managing depends on good SRS's, described usecases etc., and as late as depends on chosen language.

Well, I've spent a lot of time digging around in the code for Gaim. It's written completely in C... and I've never had trouble understand the flow, organization, or what the programmers were trying to accomplish. That's the main grounds on which I make my claim.

---

### Post by jblebrun on 2007-01-24
> **Mirrorball said:**
> This is because gcc detects the .cc suffix and compiles the file as C++ code.

Really? Because if I call gcc on a .cc file, I get errors left and right. There must be more to it than that...

But ok. I changed the extension to .c -- that did produce some errors: had to change the "bools" to chars,  and trues and falses. to 1s and 0s. So, it's still basically C code.

---

### Post by maxamillion on 2007-01-24
> **ssalman said:**
> I don't mean to be a troll ;)

but the link you provided confirms exactly what I have said, and does not support your statement above! ... here is the quote "The [C]("http://en.wikipedia.org/wiki/C_programming_language") and [C++]("http://en.wikipedia.org/wiki/C%2B%2B") [programming languages]("http://en.wikipedia.org/wiki/Programming_languages") are closely related. C++ grew out of C and is mostly a _***superset ***_of the latter"

again, not trolling... but want to clarify the difference...


[edit]

let me clarify even more, what I'm disagreeing on is the "C is not a subset of C++" statement, I actually agree with maxamillion that C and C++ are completely separate languages.

For C to be a subset of C++ that would make C++ come first .... C++ is a superset of C, completely different. You basically made a statement equal in logic to "Debian is derived from Ubuntu" ... not to be a troll, but simply to clarify why I posted what I did.

---

### Post by hod139 on 2007-01-24
> **LordHunter317 said:**
> I'd learn C++ personally, but do what you will.

Nice, glad to see you back LordHunter, I've always liked your input on these forums.

As for the OP, my vote is also for C++, the STL makes a lot of stuff much easier.  Of course it all depends on what you want.

---

### Post by runningwithscissors on 2007-01-24
Learn C.

It is nice, small, fast and easy.

C++ is big, complicated, and has everything including the kitchen sink in it (except a thread library. Yes, yes, I know Boost provides a good implementation).

---

### Post by pmasiar on 2007-01-24
> **Wybiral said:**
> 
I probably shouldn't say nice things about compiled programs in these forums though (a lot of people on these forums are anti-compile evangelists) even while probably more than 90% of the beautiful, fast, nicely working, memory managing system they are using at-this-moment was written in C and compiled.

This is BS. Compiled programs have *very important*  place in the world, and interpreted too. Anyone is very welcome to do all his/her programming in C/ASM/binaries if copious amount of such pain is desired. :-)

I just will not stand silent when some people express opinions like the only measure of "quality" of a programming language  is execution speed of code it creates. I want my operating system and my python compiled, thank you. :-) But most of *application software* could be done in dynamically typed languages without any noticeable difference. OK let me get flame-resistant underwear -  someone is coming to claim that OO.org is "application" and I am wrong. :-)

My wild guess is that for at least 80% of the code made by this forum participants is not performance-critical, and if they do it in C/C#/C++/Java, they do it because one of: 
1) they can and like challenge 
2) ignorant PHB selected that language for no business reasons 
3) they are naive in their strive for raw execution speed. 

I might be wrong, of course - some kernel hacker might be lurking :-)

---

### Post by lnostdal on 2007-01-25
> **Wybiral said:**
> I probably shouldn't say nice things about compiled programs in these forums though (a lot of people on these forums are anti-compile evangelists)

FYI I'm using "compiled languages" and developing "compiled software" (native machine language) exclusively. Your consistent and continuing effort to not making any sense, contradicting yourself and drawing weird/wrong conclusions to troll baffles me. You're wasting peoples time including your own.

I'm gonna pretend that you where argumenting against HLLs regardless of whether they where compiled or interpreted (compare with interpreted LLLs if you want; fairness by sticking HLLs and LLLs within the same "domain" is the point)  for a moment here and give an example of something LordHunter mentioned that is very true and proves another point. When solving HL problems, a LLLs will _restrict_ your ability to express optimal algorithms and solutions _so much_  - that the result will run slower in practice than if the same solution was expressed in a HLL. The example here is Perls REGEX-library which is written, optimized and maintained over years now in a LLL called C. Overall it runs slower than another REGEX-library called [cl-ppcre](http://weitz.de/cl-ppcre/) which is written completely in a HLL. The only exceptions is when the REGEX-task is sequential, read: simple -- and I believe the benchmarks is from an old version of CMUCL seeing as a date like 2002 is mentioned.

> **Edi Weitz - about cl-ppcre]It is fast. If compiled with CMUCL, it outperforms Perl's highly optimized regex engine (written in C) which to my knowledge is faster than most other regex engines around.[/quote]

Note that SBCL generally generates somewhat faster code than CMUCL btw. .. which would prove the point even further.

[quote=Wybrial]There's really nothing wrong with C++,[/quote]
A lie. Every competent C++ programmer knows that C++ has a lot of flaws. I really have no further comments on this.

[quote=Wybrial] I use it, I know a ton of people who use (it)[/quote]
Not an argument at all. Even I use C++. Unlike you I would never criticize something I know nothing about. C++ is what eventually nearly killed my interest in programming and computers _totally_. After listening to bozos like you recommending it above anything else then spending years (nearly 10 years now) of my life on it I nearly totally gave up on the belief that it would be possible to create software that was both beautiful on the inside and outside -- all the way out. I was angry, stunned and sad said:**
> I can assure you that HLL interfacing isn't any harder in C++ than in C
Another lie. Nothing further to add besides that readers should not think what Wyb is saying is the truth of things because he has the "last word" in his frantic babbling sessions.


[quote=Wybrial] it's not hard to learn.[/quote]
Still more lies. Everyone who truly know C++ knows that it is a gigantic task to learn it and maintain software written in it. The reason for this is basically because it has too many backward- and sideway-compatible concerns padded onto it as an afterthought to be able to maintain its sanity. It's similar to the broken Win32 world/API even though they are at least finally _trying_ to move on with things like C# and .NET. C++ is designed or manufactured to be popular instead of intelligent and smart; that's its goal -- just like friggin Britney Spears.

---

### Post by cellfish on 2007-01-25
Ive heard a lot of people say C is faster, however  something i realized is that C is not always faster! Sorting a list in C for example will usually require you to write your own sort code, and Pythons sort routine is almost certainly faster than anything you will come up with as a beginner. And its in C...

Similarly using regular expressions can be very difficult and slow in C since it depends on the library you use and many standard C regex libraries are less efficient than the
Python re module.

So it depends on what you are doing whether C will even be any faster.

---

### Post by utab on 2007-01-25
[C in 21 days](http://www.utdallas.edu/~mdg061000/)

[C++ in 21 days](http://newdata.box.sk/bx/c/index.htm)

These references are the worst references for these languages. If you are really serious:

for c++ : start with Accelerated C++, move to C++ programming language by Straustrup
for c:     The C programming language (the only source you need)

---

### Post by Wybiral on 2007-01-25
> **pmasiar said:**
> This is BS. Compiled programs have *very important*  place in the world, and interpreted too. Anyone is very welcome to do all his/her programming in C/ASM/binaries if copious amount of such pain is desired. :-)

I just will not stand silent when some people express opinions like the only measure of "quality" of a programming language  is execution speed of code it creates. I want my operating system and my python compiled, thank you. :-) But most of *application software* could be done in dynamically typed languages without any noticeable difference. OK let me get flame-resistant underwear -  someone is coming to claim that OO.org is "application" and I am wrong. :-)

My wild guess is that for at least 80% of the code made by this forum participants is not performance-critical, and if they do it in C/C#/C++/Java, they do it because one of: 
1) they can and like challenge 
2) ignorant PHB selected that language for no business reasons 
3) they are naive in their strive for raw execution speed. 

I might be wrong, of course - some kernel hacker might be lurking :-)

Whao, why does everyone jump to the attack when I make a comment. I wasn't saying anything bad about interpreted/non-compiled languages! You know I'm also a firm python user/lover. I don't have a problem with them at all. But you can't deny that a ton of people on these boards spend their time downsizing and crapping on compiled languages. That's all I meant. No offense to non-compiled languages! BUT, I do need maximum speed because I do a lot of 3d graphical stuff... I would use another language, like python or something... But I need something a little faster. C/C++ are what I use... But still, that was not meant as an attack against non-compiled languages.

> **lnostdal]FYI I'm using "compiled languages" and developing "compiled software" (native machine language) exclusively. Your consistent and continuing effort to not making any sense, contradicting yourself and drawing weird/wrong conclusions to troll baffles me. You're wasting peoples time including your own.[/QUOTE]

Um... I never said anything about you. What are you getting to?

[QUOTE=lnostdal]
> 
Originally Posted by Wybrial
There's really nothing wrong with C++,


A lie. Every competent C++ programmer knows that C++ has a lot of flaws. I really have no further comments on this.[/QUOTE]

Yes lnostdal, obviously because you don't like a language makes my statement a lie... I'm sorry I ever had an opinion when I was amongst such a wise man.

[QUOTE=lnostdal]
> 
Originally Posted by Wybrial
I use it, I know a ton of people who use (it)

Not an argument at all. Even I use C++. Unlike you I would never criticize something I know nothing about. C++ is what eventually nearly killed my interest in programming and computers _totally_. After listening to bozos like you recommending it above anything else then spending years (nearly 10 years now) of my life on it I nearly totally gave up on the belief that it would be possible to create software that was both beautiful on the inside and outside -- all the way out. I was angry, stunned and sad said:**
> 

Calm down... I wasn't saying it is or should be the language above all... I firmly believe that's up to the programmer. I use python, all the time... I like it a lot. I like C++ TOO!!! I seriously have no idea where you are coming from anymore...

[QUOTE=lnostdal]
> 
Originally Posted by Wybrial
I can assure you that HLL interfacing isn't any harder in C++ than in C

Another lie. Nothing further to add besides that readers should not think what Wyb is saying is the truth of things because he has the "last word" in his frantic babbling sessions.

lnostdal... Dude, they almost always use the same libraries... lol... The same functions I use to embed/interface python in C, I use in C++!!! I've also interfaces lua in C AND IN C++ and there was hardly a difference... lnostdal is just an anti C++ evangelist!

[QUOTE=lnostdal]
> 
Originally Posted by Wybrial
it's not hard to learn.

Still more lies. Everyone who truly know C++ knows that it is a gigantic task to learn it and maintain software written in it. The reason for this is basically because it has too many backward- and sideway-compatible concerns padded onto it as an afterthought to be able to maintain its sanity. It's similar to the broken Win32 world/API even though they are at least finally _trying_ to move on with things like C# and .NET. C++ is designed or manufactured to be popular instead of intelligent and smart; that's its goal -- just like friggin Britney Spears.[/QUOTE]

Ok... You're right, no one can learn C++ because it is SO gigantic and hard to learn. And no one can possibly maintain software written in it... Despite all of the projects that exist right now. And all of the people who know C++... It took me a month to get the basics down, another month or so to learn to STL... A don't think a couple of months is too bad at all. BUT, then again I am not a master like lnostdal, so I probably don't know what I'm talking about... And better yet, everything I say is probably a lie because lnostdal says so and he is so all knowing...

Give me a break.

---

### Post by pmasiar on 2007-01-25
> **Wybiral said:**
> Whao, why does everyone jump to the attack when I make a comment. I wasn't saying anything bad about interpreted/non-compiled languages! 

You expressed many strong opinions recently.  I had gut feeling that many are not 100% correct - but I am not expert in C++ so I left to experts to argue with you. They did, but (again IMHO) you did not listen to their arguments as carefully as I would. lnostdal sounds like he knows what he is talking about (again, I am not expert in C++ and interfacing Python), although he could have used less inflamatory language. nah, we all like inflamatory language - so we better be prepared to get flamed :-D

This is what you get when you mess with a man whose middle name is "Rune" :-)

Another misunderstaning might be that you said what is good for *you* and lnostdal responded what might be good practices for average user.

> You know I'm also a firm python user/lover. 

Yes I know so I was surprised why you needed to suggest exestence of some "anti-compile mafia". ("*I probably shouldn't say nice things about compiled programs*")There isn't any such mafia., and if it was, you would be part of it, wouldn't you? :-)

No hard feelings, all in family. Nothing more to see here, lets move on. I only hope you will not go and edit/delete out your old postings. :-)

---

### Post by Wybiral on 2007-01-25
I don't think lnostdal is the C++ expert he claims to be. Normally I wouldn't say that about someone, but since he has spent most of his time trying to downsize me... I feel no guilt.

I'm not a C++ expert either, but I know enough to get by. And I HAVE in fact done a lot of C and C++ interfacing with HLL and scripting languages... I can say from personal experience that it's almost the same... But, with C++ you can wrap your interfacing into a pretty little class and makes everything look much cleaner.

The only thing that bothers me about this entire post is how defensive he gets... It's like he's so paranoid that everything I say is about him that he snaps back accusing me of being a liar, when I wasn't even addressing him.

About the "anti-compile mafia"... lol, yes I know there is none. But every time I see someone defend compiling in a thread, every interpreted fan jumps out and flames them. I don't think it's a conspiracy or anything, but a C/C++ thread is the wrong place to have that take place.

Anyway... The things about C++ that usually don't sink in for most people are templates, classes, inheritance... I realize that at first it may seem very foreign... But eventually it makes sense, and when it does, it is very helpful... But the nicest thing about C++ is that you don't HAVE to use those things... You can just use the C style parts of the language until you are comfortable with the extra stuff. I just don't see why people think it's so hard to learn or so absurd to use.

To lnostdal...
I'm willing to let it go and forget about this thread, but for future reference, I don't like being called a liar... If you disagree with what I say... Fiine, disagree all you want, but that doesn't make me a liar.

---

### Post by lnostdal on 2007-01-25
> **Wybiral said:**
> 
  [quote=lnostdal][quote=wybiral]I probably shouldn't say nice things about compiled programs in these forums though (a lot of people on these forums are anti-compile evangelists)
  FYI I'm using "compiled languages" and developing "compiled software" (native machine language) exclusively.[/quote]
Um... I never said anything about you. What are you getting to?[/quote]

Stop playing games, troll. The now correct quoting explains what I'm "getting to" for most people.


> **Wybiral]Yes lnostdal, obviously because you don't like a language makes my statement a lie...[/quote]
It's not a matter of simple superficial "taste". Your comment is too stupid to even bother with a longer reply, really - I know where you're going.


[quote=Wybiral].. when I was amongst such a wise man.[/quote]
Thank you.


[quote=Wybiral]I wasn't saying it is or should be the language above all..[/quote]
No, but you've been saying other things (yup, lies) that indicate a similar attitude as people who do. This part of the rant from my side was partly meant as a FYI FYI (I thought this was obvious but, yeh) - seeing as you seem to enjoy your own babbling so much.


[quote=Wybiral]lnostdal... Dude, they almost always use the same libraries... lol... The same functions I use to embed/interface python in C, I use in C++!!! I've also interfaces lua in C AND IN C++ and there was hardly a difference... [/quote]
lol -- interfacing with software-libraries is not the same as embedding a friggin interpreter in an application. Please come back later when you even know what we are discussing here. Seriously said:**
> lnostdal is just an anti C++ evangelist!
You bet I am.

> **Wybiral] And all of the people who know C++... It took me a month to get the basics down, another month or so to learn to STL... A don't think a couple of months is too bad at all. [/quote]
These statements totally speak for themselves. "A couple of months" is _nothing_, mate. It's an insignificant piss in the ocean. You're confirming what I've stated about your personae and experience. You've just told me everything I need to know to confirm my mentioned (yes said:**
> so I probably don't know what I'm talking about... 
First thing you've gotten right in a while..

[quote=Wybiral]everything I say is probably a lie[/quote]
..you're onto a good streak here.

---

### Post by lnostdal on 2007-01-25
> **Wybiral said:**
> The only thing that bothers me about this entire post is how defensive he gets...
Well - educate me; how would you like me to respond? You are saying what I am saying is wrong even though I know it is not.


[quote=Wybiral]but a C/C++ thread is the wrong place to have that take place.[/quote]
Gawd, you're such a total moron. This is no "C/C++-thread". This is a programming thread  in a programming-forum. The OP wanted to know if he should go for C or C++ and I'm recommending he sticks to C (#1) and rather use something else than C++ when HL problems need to be solved seeing as C is way easier to interface with than C++.

You disagree. You believe C++ is just as easy to interface with, and you did mention easier if I'm not mistaken - which is just plain wrong and, yes a "lie".

Recommend C++ for its own reasons all you like -- I will not interfere. But it is not easy or easier to interface with C++ than with C. You are a liar!

[quote=wybiral]If you disagree with what I say... Fiine, disagree all you want, but that doesn't make me a liar.[/QUOTE]
..even when it's true?

edit:
#1: Simple thought through C++ that is possible to interface with is OK though. But this is rarely seen as people have a tendency to stick with C++ for too long as they approach the level where they should have switched to a HLL a long time ago. They fall for C++s false promises of HL gifts and thrills and end up in a tar pit trap of a hell hole they'll be wondering how to get out of.

---

### Post by Wybiral on 2007-01-25
You can use HLL to extend your C++ and C++ to extend you HLL just as easy as with C. That's what I meant by interfacing, NO, you did not specify anything else. Call me a liar, I don't even care any more... I can show you just how similar it is for more than a couple of languages.

Just what have I said that isn't true??? Show me an exact, non-opinion, lie that I have made. All you will find are opinions... And thats exactly what I'm talking about.

Even if YOU have problems with C++ doesn't mean that its TRUE. It doesn't mean that everyone does.

---

### Post by lnostdal on 2007-01-25
> **Wybiral said:**
> You can use HLL to extend your C++ and C++ to extend you HLL just as easy as with C. 

OK, listen; when interfacing with software libraries you're creating stuff like PyGTK and PyQT. Interfacing with software libraries written in HL C++ is way harder than interfacing with software written in C. It's a well known fact and I've experienced it myself and can confirm it. You denying this well known fact is the lie.

Simple enough?

edit (answering post below):
> **Wybiral said:**
> Ok, so you mean created modules for the HLL from C++ code?
Assuming you mean "creating", then yes.

[quote=Wybiral]Then I might agree. Simply because the HLL might not support all of the features that C++ does[/quote]
No, this is not the reason at all. It is not one simple isolated thing/reason or single problem that causes this. It is complicated and has a lot of details and reasons. I'm not going to bother with listing up all the reasons I can think of but I did mention some (not at all all) back in this thread somewhere.

[quote=wybiral]But, you never specified sofware libraries, [/quote]
It is pretty obvious. I remember at least one other person in this thread getting this. Here's an example: [http://pyopenssl.sourceforge.net/](http://pyopenssl.sourceforge.net/) .. you'll see "pyOpenSSL - Python interface to the OpenSSL library". "Interfacing" is the act of writing such an interface or communicating with the library from the language you're "interfacing from". Hey -- and I'm not even a native English speaker. You should spend two months learning Norwegian. :P

[quote=wybiral]I thought you meant simply communicating data and objects between the two[/QUOTE]
Of course not. Any IPC-method or whatever would do this.

---

### Post by Wybiral on 2007-01-25
Ok, so you mean created modules for the HLL from C++ code?
Then I might agree. Simply because the HLL might not support all of the features that C++ does and interfacing would be a little hard because you would have to find other ways of doing it. But, you never specified sofware libraries, I thought you meant simply communicating data and objects between the two, and in that case I would say that C++ is just as easy. Anyway, we should stop arguing about this here, it's really taking away from the OP's question.

---

### Post by jblebrun on 2007-01-25
> **Wybiral said:**
> Ok, so you mean created modules for the HLL from C++ code?
Then I might agree. Simply because the HLL might not support all of the features that C++ does and interfacing would be a little hard because you would have to find other ways of doing it. But, you never specified sofware libraries, I thought you meant simply communicating data and objects between the two, and in that case I would say that C++ is just as easy. Anyway, we should stop arguing about this here, it's really taking away from the OP's question.

Arguing about the ease of interfacing an HLL to C vs. interfacing an HLL to C++ is actually rather on topic, since it's comparing C and C++. 

Using python.h and the C-compiled python interface modules is not really interfacing C and C++, since if you actually want to communicate between C++ and Python using *C++ SPECIFIC* paradigms, you need to write that glue code yourself. All of the examples you've shown using Python.h have been C code embedded in a C++ program. That's not interfacing C++ with Python, that's writing C++ - Python glue code in C.

---

### Post by daniel of sarnia on 2007-01-25
> **pmasiar said:**
>  Experimental implementation on top of (subset of) Python -  [PyPy]("http://en.wikipedia.org/wiki/Pypy") is financed by EU as research project - but they say that having thing implemented in Python allows for simpler experimenting with internals.

I love it, that's the best thing I've herd all day, hahah python in python. That sounds like something fun to play with for a while :)

---

### Post by ssalman on 2007-01-26
> **maxamillion said:**
> For C to be a subset of C++ that would make C++ come first .... C++ is a superset of C, completely different. You basically made a statement equal in logic to "Debian is derived from Ubuntu" ... not to be a troll, but simply to clarify why I posted what I did.

point taken!! :)

---

### Post by hod139 on 2007-01-26
> **maxamillion said:**
> For C to be a subset of C++ that would make C++ come first .... C++ is a superset of C, completely different. You basically made a statement equal in logic to "Debian is derived from Ubuntu" ... not to be a troll, but simply to clarify why I posted what I did.

This logic does not seem correct to me.  I'm not disagreeing with the answer, C++ came after C and was originally designed to be a superset of C (C with classes).  However, the sub/super set definition pertains only to the elements or members of a set, not the time it was made.  Originally, C was a subset of C++ (things have slightly change now) since every element/member of C was also a member of C++.  Alternatively, anything you wrote in C would compile and run exactly the same in C++.

Calling C a subset of C++ is not the same as saying Debian is derived from Ubuntu.  If Debian contained every package that Ubuntu did, but Ubuntu had more packages in addition, then Debian would be a subset.  Conversely, if Ubuntu contained every package that Debian has, but Debian contains more, than Ubuntu would be a subset.  Since neither of these statements are true, you never hear Ubuntu called a subset (If you did then they are wrong).  You do here Ubuntu called a fork (though not by Debian), but this is not a subset.

---

### Post by LordHunter317 on 2007-01-26
> **Wybiral said:**
> I can assure you that HLL interfacing isn't any harder in C++ than in CYes, it is.  Lack of a stable ABI and name mangling are good starting reasons.

[quote=runningwithscissors]C++ is big, complicated, and has everything including the kitchen sink in it (except a thread library. Yes, yes, I know Boost provides a good implementation).[/quote]You've clearly never looked at the .NET or J2SE standard APIs then.  C++ is dwarfishly small (several orders of magnitude or more SLOC) than either.

C++ lacks any networking or IPC facilities beyond ANSI C signals (which aren't even really UNIX singals), for example.  It lacks threading and any concept of a thread.  It lacks any concepts of file or system management.

Remember, most of what UNIX gives you is OS-specific, it's not part of the language.

[quote=Inostdal]Now hardware and modern compiler technology is here and we're ready to take the path we really intended and wanted. [/quote]Modern hardware, yes.  Modern compiler tech?  Don't know what you're talking about.  Compilers haven't changed substantially in some time, except for some advances in code generations for VLIW platforms like Itanium.  Even the functional world hasn't shown massive advances, since most of the core optimizations were figured out ages ago (though the implementations have advanced some).

The bigger front is probably runtime stuff, like modern garbage collection that isn't wasteful and dynamic typing with less runtime overhead.

[quote=Wybrial]Yes lnostdal, obviously because you don't like a language makes my statement a lie...[/quote]The hugely massive syntax changes in TR1 and TR2, nevermind the fact most of it was community-initated requests, not committe ones, indicates that a lot of C++ programmers know that C++ has flaws.  Lots of them.

Some of them will be fixed.  Others will not.  Most of the crap that won't improve is runtime related, sadly.

> You can use HLL to extend your C++ and C++ to extend you HLL just as easy as with C. That's what I meant by interfacing, NO, you did not specify anything else. Call me a liar, I don't even care any more...But htat's not what you said.  You said I could use Python objects from c++ and c++ objects from Python.  Python.h does not provide such functionality.

Something like MS' COM provides this, and it's extremely bloody complicated.  Including require you to be very careful with your C++ code to not break it.

[quote=hod139]Originally, C was a subset of C++ (things have slightly change now) since every element/member of C was also a member of C++. Alternatively, anything you wrote in C would compile and run exactly the same in C++.[/quote]That was never true.  For example:```
int class;
```will never be legal C++.  It's always legal C.

---

### Post by Wybiral on 2007-01-26
Ok... I must have been wrong/confused/mislead about the python/C++ sharing class objects thing... Maybe it was a bogus example or some kind of hacky way of doing it, I don't remember (but I did see a couple of examples, I just don't have the links).

Anyway... You can avoid name mangling in C++ using extern "c", you can't use classes, so their isn't a 100% c++ support there, but no one said you had to use classes to write a c++ program (I know, I know... Why use C++? You can still use some of it's other stuff... But thats not the point...)

Also, just because you can't interface 100% of your C++ code in HLL's doesn't mean that it's harder... You can interface everything that C can, and still be able to use classes and C++ style code to simplify the process, which in my opinion makes it easier.

For instance, you can use C++ to simplify the process of interfacing with them using abstraction, like making a class to handle all of it. I wrote a small wrapper that does just this, it allows you to call python functions with arguments using a MUCH simpler interface then is provided by python.h

You can say...

```

voidPyFunc("myprint", argList() << "This is a normal string and the number: " << 20);

```

Because I wrote a simple class with overloads to accept the arguments of varying types, then it calls the python function "myprint" with the arguments "This is a normal string and the number: " and 20... Which equates to the python function call...

myprint("This is a normal string and the number: ", 20)

This would be a lot more difficult to accept varying object type arguments in C without overloads. It also uses a simple class to represent a sortof mock-dynamic object type in C++, and a C++ STL vector to hold the list to allow for varying sizes... All of which would be more difficult in C.

But, it still allows you to transfer info from C++ to python... With ease, in fact... Even easier than with C.

So, even if I was wrong about being able to 100% interface C++ objects with HLL's (and I am willing to accept that, I have to examples to prove otherwise)... My point is that it doesn't make it harder to interface with C++. Even if you can't interface classes... Neither can C (try not to say duh, it is a valid point).

I hope you understand where I am coming from...

It may not exactly be easier, I can accept that now... But that doesn't mean that it's harder.

I apologize if I used any misinformation, I thought I could find some examples to bring up and I can't.

However, the example above I can back up because I wrote it and it was also very easy to do.

---

### Post by LordHunter317 on 2007-01-26
> **Wybiral said:**
> Ok... I must have been wrong/confused/mislead about the python/C++ sharing class objects thing...It can be done.  But Python.h doesn't do it.  The Boost::Python stuff does, sort of.  It's really truly one way: it lets you transparently use some C++ objects from Python, but not really vice-versa.  The newest version does allow that, but has even more limitations going the other way, due to how Python represents things that are incompatible with how C++ does.

> Anyway... You can avoid name mangling in C++ using extern "c", you can't use classes,Which precludes sharing objects.  And that doesn't avoid all name mangling.

> You can interface everything that C can, and still be able to use classes and C++ style code to simplify the process, which in my opinion makes it easier.Yes, but you can't pass C++ classes back and forth trivally, which is vastly more desirable.  Passing back and forth C structures is trivial.  Callbacks between languages where one end is C is trivial.  It's non-trival when one end is C++.

> 
This would be a lot more difficult to accept varying object type arguments in C without overloads.No, that's what we have void* and varargs for, as poor as they are.  It's perhaps harder to do with type safety, but type safety frequently gets sacrificed at some point during cross-language work (hopefully at a level below the library user, though)

>  My point is that it doesn't make it harder to interface with C++.In a C++ specific manner?  Yes, it does.

> However, the example above I can back up because I wrote it and it was also very easy to do.Instead of creating examples, you'd do much better to just read the Boost.Python stuff.

---

### Post by hod139 on 2007-01-26
> **LordHunter317 said:**
> 
That was never true.  For example:```
int class;
```will never be legal C++.  It's always legal C.
Whoops,  missed the obvious!!!  All new keywords introduced in C++ when used in a C program would have this effect.  And of course things have only diverged more recently. Anyways, I will never again call C++ a superset of C, not even in its original days.  Thanks!

---

### Post by lnostdal on 2007-01-27
> **Wybiral said:**
> Anyway... You can avoid name mangling in C++ using extern "c", you can't use classes, so their isn't a 100% c++ support there, but no one said you had to use classes to write a c++ program (I know, I know... Why use C++? You can still use some of it's other stuff... But thats not the point...)

You can't use overloading, namespaces and a lot of other stuff either - pretty much not any of the stuff you'd want in a HL modern (C++) interface. This is basically what I'm at yes. Problem is many stretch their HL C++ too far. They fall for the false promises of simple low-cost (maintenance wise etc.) abstraction and generality and drown in the cruft and problems that eventually will show up. When they understand that they need to interface with what they have from a HLL to better cope they're fücked because it's too late. They should have switched a long time ago.

So I'm arguing that people stick with C in the first place and that C++ isn't really needed "in between" C and a HLL. Feel free to disagree with this method of solving software problems. To a certain degree I don't care about that, you're free to do what you want. But what I do care about is the false/weird statements mentioned related to or against the _reasons_ I have to look up on things in this way. Pretending like there are no issues or that they are trivial -- I guess this is what ticks me off. My reasons are perfectly real and valid no matter what method you choose to deal yourself and isn't a matter of "taste" or something like that, but again - compromise and deal as you wish. :)


> **Wybiral]Also, just because you can't interface 100% of your C++ code in HLL's doesn't mean that it's harder... [/quote]
Yes it does. Just because you might be able to interface with the "C parts" of a library doesn't mean you also have to interface with the "C++ parts" as a prerequisite for anything significant to work at all. 

You'll have to start writing wrappers around the library in either C or in C++ with extern "C" said:**
> It may not exactly be easier, I can accept that now... But that doesn't mean that it's harder.

haha - you seem desperate going out on limbs like these .. :}

---

### Post by Wybiral on 2007-01-27
OK, then it strongly depends on what you want to interface... Anything you can interface in C, you can in C++ so in my opinion, it's not harder at all...

Even if you can't wrap your classes and stuff into it, as I said... You can still use C++ to help with the actual interfacing itself using abstraction and wrapping things into pretty manageable objects, which maybe not to everyone, but it makes it easier for me.

So, it's an opinion, I think it's usually easier... You may not. That's cool, I don't see why we aren't allowed to disagree. Just because you do disagree doesn't make me a liar and it doesn't make you right. That's all I'm saying...

But, once again, I think we are taking emphasis away from the OP, so we should try to drop it out of common decency. If you REALLY want to continue it, feel free to PM me or something, but I would like to keep it civil and stop with the "you're a moron" and "you're a liar" stuff... So please don't PM me if that's all you have to say. It's not in any way helpful or on topic for this post at all.

OK?

Thanks.

---

### Post by WebDrake on 2007-01-27
> **hod139 said:**
> Whoops,  missed the obvious!!!  All new keywords introduced in C++ when used in a C program would have this effect.  And of course things have only diverged more recently. Anyways, I will never again call C++ a superset of C, not even in its original days.  Thanks!
There are other examples.  The one I always remember is this:
```

int *a;
a = malloc(10*sizeof(int));

```
This is legal in C but C++ won't accept it; you have to cast it,
```

int *a;
a = (int *) malloc(10*sizeof(int));

```

Of course, you're not meant to use malloc() in C++, but it's a clear example of how C++ is not a strict superset.

On the other hand, I believe Objective-C is a strict superset, and I have read (though have no experience) that in many ways its object-oriented syntax and implementation is superior to C++.  Can anyone comment?

---

### Post by LordHunter317 on 2007-01-27
> **Wybiral said:**
> OK, then it strongly depends on what you want to interface... Anything you can interface in C, you can in C++ so in my opinion, it's not harder at all...To interface at **the level of C**.

The fact you still don't grasp the difference between interfacing at the level of C and the level of C++ is disheartening.

> Even if you can't wrap your classes and stuff into it, as I said... You can still use C++ to help with the actual interfacing itself using abstraction and wrapping things into pretty manageable objects, which maybe not to everyone, but it makes it easier for me.Not especially, no.  You can for some things, but the biggest advantage is the better type safety.

> Just because you do disagree doesn't make me a liar and it doesn't make you right.You have been lying though.  You've misrepresented your position several times.

[quote=WebDrake]
On the other hand, I believe Objective-C is a strict superset, and I have read (though have no experience) that in many ways its object-oriented syntax and implementation is superior to C++. Can anyone comment?[/quote]If by better you mean butt-ugly.  It features less stuff so it lacks for example, the mess related to templates.  It's implementation is dynamically-typed, so it's not even really worth comparing.

---

### Post by WebDrake on 2007-01-27
> **LordHunter317 said:**
> If by better you mean butt-ugly.  It features less stuff so it lacks for example, the mess related to templates.  It's implementation is dynamically-typed, so it's not even really worth comparing.
As I said, I have only *read*. ;-)  I think the point of interest was indeed about dynamic typing.  Can you clarify what the issue is here?

---

### Post by Wybiral on 2007-01-27
> **LordHunter317 said:**
> ...You have been lying though.  You've misrepresented your position several times...

I was wrong about the class sharing thing... That's it.

But it doesn't make me a liar.

Now my point is that you can still interface the same stuff that C can... So it isn't harder.

I know that it's not FULL interfacing with C++ you can calm down... I understand that. But you can write your code to cope with that, I don't see how that makes it any harder. That's like saying that C is harder than C++ because it doesn't have classes... And we all know it's not because you can write your C code with that fact in mind. (Go ahead misinterpret that statement too...). What I mean, basically is that you can still do all of your communicating with the HLL just as easy.

Also, the word "interface" was all that was used... And it has a rather broad definition... It can also be used to define the interfacing between embedded interpreters and calling internal or external HLL code from within C++... It doesn't strictly mean library interfacing... So I still don't think anything I've said is a lie.

And it's still a matter of opinion... I don't think it's difficult, you do... That IS, in fact, an opinion. You aren't the supreme judge of things, people actually do have a right to an opinion. Your difference in opinion does not make me a liar.

EDIT:

Also, I want to stress the fact that I said "communicating" 
You maybe can't use all of the C++ features while communicating with the HLL...
You can still use them in your program... So communicating is still as easy in C++ as C...
...In my opinion... I'm not saying it's a fact, but it is my opinion.

---

### Post by LordHunter317 on 2007-01-27
> **Wybiral said:**
> But it doesn't make me a liar.The way you represented your position does, however.  You tried to claim something different from what you said you could and refused to admit to that, and then ran around it when confronted.

You may not have meant to do it, but you certainly did.  No one's mad, but get over it.

> Now my point is that you can still interface the same stuff that C can... So it isn't harder.**That part isn't, * but that isn't interesting***.

> I know that it's not FULL interfacing with C++ you can calm down... I understand that.But you don't.  That statement above proves you don't.  You're taking a conditional statement and making it absolute.  If you said, "That **part** isn't harder", you would be ok.  But you're not doing that, you're saying just "so it isn't harder," which has vastly different meaning.

> Also, the word "interface" was all that was used... And it has a rather broad definition...Occasionally, but not in the context you were suggesting.

> And it's still a matter of opinion... No, it isn't.  If that were true, then 2+2=4 is also an opinion.  You can't say that without totally removing fact, so that doesn't fly.

---

### Post by Wybiral on 2007-01-27
> The way you represented your position does, however. You tried to claim something different from what you said you could and refused to admit to that, and then ran around it when confronted.

What did I do this with? I'm not doubting you... How did I run around it?

As I said... If this is still about the class sharing thing... Fine, that was wrong. But it wasn't a lie, I've seen examples of sharing object's from C++ to python... Maybe I misinterpreted it, but that doesn't make me a liar.

I can take being wrong... But calling me a liar is flat-out unnecessary here. If I misunderstand something, then point it out to me, don't just call me a liar... That's not productive at all.

> Occasionally, but not in the context you were suggesting.
I never suggested a context.. Most of the HLL interfacing I do is for scripting engines or embedding the interpreter... That's what I though lnostdal meant too, I was wrong... He meant interfacing with libraries and I assume writing modules... But as I said, the word interfacing is broad, so it was just a misinterpretation.

> No, it isn't. If that were true, then 2+2=4 is also an opinion. You can't say that without totally removing fact, so that doesn't fly.
It still isn't the same... If a 3-year-old said 2+2=4 is hard for them... I wouldn't call them a liar, I would just accept the fact that it's different for me than them. But saying that it's harder and that it isn't true are two different things. You guys are saying that interfacing HLL's is harder (and I admit there has been some confusion with the definition of interfacing here, and that I used an example without looking further into it... Which was dumb of me and I take that back) and I'm saying it's not... I don't see how that isn't an opinion.

BTW, I wasn't comparing you guys to a 3-year-old, I just wanted to use 2+2=4 as an example of what I mean, that wasn't meant to sound like I was relating it to you... I wasn't.

So I retract any of my statements that said "it's easier" that was wrong... I can admit that. But I don't retract my statements that say "it isn't harder"

---

### Post by LordHunter317 on 2007-01-27
> **Wybiral said:**
> As I said... If this is still about the class sharing thing... Fine, that was wrong. But it wasn't a lie, I've seen examples of sharing object's from C++ to python...The lie was claiming python.h was such an example and then claiming you never offered to show examples of sharing classes.  You claimed you always ment to show what you show.

>  If I misunderstand something, then point it out to me, don't just call me a liar... That's not productive at all.It is when you are actually lying.  The issue isn't just that you misunderstood something, it's that you continue to delibrately misrepresent your claims.  Both are bad behavior.  You're still refusing to even acknowledge the latter.

> I never suggested a context..Yes, you did.  You have to, it's the glory of the English Language.

> It still isn't the same... If a 3-year-old said 2+2=4 is hard for them... I wouldn't call them a liar, I would just accept the fact that it's different for me than them.Total non-sequitur.  Go back and re-read what I said.

> So I retract any of my statements that said "it's easier" that was wrong... I can admit that. But I don't retract my statements that say "it isn't harder"But you have no proof, so you better.  And I have proof and reasoning.

---

### Post by Lux Perpetua on 2007-01-27
> **erikcw said:**
> Hi all,

I'd like to learn C and/or C++, but I'm not sure which one I should go with.  Does it make more sense to gain proficiency with C first and then move onto C++, or the other way around?  By learning C++ will I be learning C at the same time?

Thanks!C is a lot simpler and smaller than C++, a lot older, and less carefully designed in several ways. I personally find it easier to learn something easy and simple-minded first, experience its frustrations, and then move on to something bigger and better than to start with the latter and subsequently try to learn the simpler thing, experiencing full-on the shock of having my favorite features removed. 

That only applies if you intend to learn *both* C and C++; for example, there's no need to learn C just because you want to learn C++ later. However, if you're new to programming, I'd probably suggest going with C, since as I said, it's a simpler language. (By that I mean that it's easier to understand, not easier to program in. The features that make C++ complex also make programming in it easier.)

---

### Post by phossal on 2007-01-27
> **Lux Perpetua said:**
> C is a lot simpler and smaller than C++

It really is *smaller*. The core language can be sufficiently broken down in a few hundred pages. Compared to "Learning Java" - an intro to a language I love - a decent book on C is like a pamphlet. My perception of C is that it's beautiful for its relative simplicity. Pointers? Awesome. Bit operations? Packed structures? All entirely practical? No. Beautiful? Absolutely. And, it *is* older. It's a legend, if not always the easiest and most practical tool anymore.

I *love* C. For me, it's romance.

---

### Post by chipmonk010 on 2007-01-30
Well, first off id like to say that I found this thread to be helpful. I'm just really starting out when it comes to programing so i rarely post in this forum although i do alot of lurking. 

Anyway ive been reading about and playing with python mostly and i really like the language but ive been looking for something to compliment it, something with a little more power say C/C++. Now I have a rather poor book on C++ that i began reading through (C++ in 24 hours by sams pub.) but after messing with that and reading this thread im gonna go get "The C programing language" and start with that.

I think it will be less confusing to deal with two languages that are rather simple to start with. I will use python to get my feet wet with OOP and C for things that require speed and also so i can mess with the kernel, drivers, a majority of the open source projects etc. 

Also it seems like python and C will compliment each other nicely and i can use libraries i write in C with python. 

So anyway i thought other new comers to programing might find this helpful since much of the talk in this thread has been somewhat advanced. Also if i have said anything that is incorrect please correct me as i dont want to send other noobs a stray.

---

### Post by Claus7 on 2007-01-31
I didn't believe six days ago, when I first saw your post, that it would have so many answers. And the most important thing is that they have variety, as they ought to have. 
It took me at least an hour to find this post, cause no matter how many times I typed C or C++, the search results were absolutely disappointing. The only thing I remembered was that your post took place 6 days ago as we speak.
As you may have figured out your question was one of my queries these days as well.
From the answers I have read up to now I make out generaly the following :
       [LIST]
[*]there is no universal language
[*]         c seems to be simpler than C++
[*]         what you have used to do plays an important role
[*]        needs are always different
[/LIST]

So, what I propose you is learn a language while having in mind that this will aid you to solve certain aspects that you have in mind. For example, problems that have to do with object oriented programming seems to be better handled by C++. The good thing about these two languages is that they have many similarities, something that will help you if you come across with the one you know less. 
May be the
differences that they have will guide you to the best answer to your question. The general experience says that if you learn something very good, then it's easy to switch to something similar (and in our case not only C/C++, but also Fortran for example).

May take the best decision and one that it will give you the best joy while learning and solving problems.
Regards!

---

### Post by Lux Perpetua on 2007-01-31
> **Claus7 said:**
> So, what I propose you is learn a language while having in mind that this will aid you to solve certain aspects that you have in mind. For example, problems that have to do with object oriented programming seems to be better handled by C++. Maybe this is what you meant, but problems don't have to do with object-oriented programming; solutions do.> 
May be the
differences that they have will guide you to the best answer to your question. The general experience says that if you learn something very good, then it's easy to switch to something similar (and in our case not only C/C++, but also Fortran for example).From personal experience, I can say that it is not easy to move from C to Fortran (77). It is comparatively a breeze to move from C to a host of other languages, though (including C++, Java, PHP, and Perl).

---

### Post by erikcw on 2007-01-31
Wow, this thread has grown!  When I first posted I didn't think it would take on a life of it's own like this!

Since posting, I've read a copy of K&R C 2nd Ed.  Since I'm already a PHP programmer everything was familiar except pointers, memory management, and static typing (and I don't know how I'm going to get by without associative arrays/hash tables - maybe struct?).  I'm looking forward to digging into some code and really starting to learn!

I've also snagged copies of the C++ book recommended in this thread and plan to read them once I get some experience with C.

Thanks for all of your help!

---

### Post by jblebrun on 2007-01-31
> **erikcw said:**
> Wow, this thread has grown!  When I first posted I didn't think it would take on a life of it's own like this!

Since posting, I've read a copy of K&R C 2nd Ed.  Since I'm already a PHP programmer everything was familiar except pointers, memory management, and static typing (and I don't know how I'm going to get by without associative arrays/hash tables - maybe struct?).  I'm looking forward to digging into some code and really starting to learn!

I've also snagged copies of the C++ book recommended in this thread and plan to read them once I get some experience with C.

Thanks for all of your help!

The glib libraries have a decent hash table structure implementation (among other features)
[http://developer.gnome.org/doc/API/2.0/glib/glib-Hash-Tables.html](http://developer.gnome.org/doc/API/2.0/glib/glib-Hash-Tables.html)

---

