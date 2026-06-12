---
title: "What language should I learn? For games"
date: 2008-12-18
forum: Programming Talk
---

### Post by spajix on 2008-12-18
I've been intrested in proggraming for awhile now. And have learned a decent amount of python and pygame and made some almost done games... But with the hole python upgrading to 3.0 and 2.X code won't work anymore, I want to move to a new languge since the code I write now won't work soon. And I want to learn a languge thats better for making games anyways. 

I'm not sure if I'm ready for C++ yet... But maybe, possibly java, But I really like python's syntax over there's.

So is there any languge thats fast, and has good graphic libary's, with good clean syntax?

Maybe a languge made for starter game design? Any idea's?

---

### Post by jimi_hendrix on 2008-12-18
try C++...its not radically different or harder than python...just a LOT more errors and debugging...

not many languages with python like syntax...

for C++ if you like it i recommend using the SDL library and lazyfoo tutorial

if you want something simple there flash but you have to pay for (or pirate) it

if you have a windows partition check out C# and XNA (its basically java but microsoft only (for anything other than basics) and i dont know any good game libraries for java)

---

### Post by PmDematagoda on 2008-12-18
> **spajix said:**
> I've been intrested in proggraming for awhile now. And have learned a decent amount of python and pygame and made some almost done games... But with the hole python upgrading to 3.0 and 2.X code won't work anymore, I want to move to a new languge since the code I write now won't work soon. And I want to learn a languge thats better for making games anyways. 

I'm not sure if I'm ready for C++ yet... But maybe, possibly java, But I really like python's syntax over there's.

So is there any languge thats fast, and has good graphic libary's, with good clean syntax?

Maybe a languge made for starter game design? Any idea's?

So what's wrong with getting used to Python 3.0? If you are competent in Python, then a new version of Python shouldn't be able to defeat you:).

---

### Post by mssever on 2008-12-18
> **spajix said:**
> But with the hole python upgrading to 3.0 and 2.X code won't work anymore, I want to move to a new languge since the code I write now won't work soon.
What makes you think that your code won't work in Python 3.0? The Python website has instructions for porting your code to 3.0. Most of the work can be automated by a script.

This shouldn't be interpreted as trying to discourage you from learning another language. It's always good to know multiple languages. I'm not a gamer, so I can't make any recommendations.

---

### Post by spajix on 2008-12-18
It's nothing against python 3... Just as I said the other reason is the fact that python just isen't very fast. So I want to try something new.

And right now I'm trying to decide between C, C++, and java

And I already have adobe flash and I've check it out I didn't like it much
and I have a windows partion but I wouldn't like to get on there just to proggram. :)

So still looking for idea's or guiding words would be great.
And thanks for the lib suggestions

---

### Post by jimi_hendrix on 2008-12-18
> **spajix said:**
> It's nothing against python 3... Just as I said the other reason is the fact that python just isen't very fast. So I want to try something new.


wont matter unless your coding Quake 9, Fallout 7, or Call of Duty 10...
> 

And right now I'm trying to decide between C, C++, and java

C++ == C with classes...and a few slightly different functions in its standard library... (99% of C programs will compile in C++...)

java is a different beast that i dont like personally but its your choice (then you can put your games on a website with java...)
> 
and I have a windows partion but I wouldn't like to get on there just to proggram. :)

i know the feeling but check it out anyway...just more things on the plate to choose from
> 
So still looking for idea's or guiding words would be great.
And thanks for the lib suggestions

---

### Post by spajix on 2008-12-18
> **jimi_hendrix said:**
> wont matter unless your coding Quake 9, Fallout 7, or Call of Duty 10...

C++ == C with classes...and a few slightly different functions in its standard library... (99% of C programs will compile in C++...)

java is a different beast that i dont like personally but its your choice (then you can put your games on a website with java...)

i know the feeling but check it out anyway...just more things on the plate to choose from

You can tell python and pygame are pretty slow much quicker then that... But they work fine for small snes like games, and are simple to use atleast.

I knew they where much alike but I didn't know that close... I just knew C++ was C with OOP added basicly... 

and I'll have to look into java more still but thanks

---

### Post by Wybiral on 2008-12-18
> **spajix said:**
> It's nothing against python 3... Just as I said the other reason is the fact that python just isen't very fast.

Coding all of the low-level bits for a CPU intensive game might not work, but there are dozens of libraries out there to handle that kind of stuff for you (efficient sprite manipulation / physics simulation libraries) even complete game engines with bindings to Python.

The real question is, do you want to write games or write game development libraries / game engines?

---

### Post by spajix on 2008-12-18
> **Wybiral said:**
> Coding all of the low-level bits for a CPU intensive game might not work, but there are dozens of libraries out there to handle that kind of stuff for you (efficient sprite manipulation / physics simulation libraries) even complete game engines with bindings to Python.

The real question is, do you want to write games or write game development libraries / game engines?

hmm... Good question, and I want to write, design games, not the libary's or engines...

java is much more complicated then python...
It makes me unsure about learning it
And even more unsure of c/c++
But I'm gonna keep checking it out for now

---

### Post by pmasiar on 2008-12-19
> **spajix said:**
> I've been intrested in proggraming for awhile now. And have learned a decent amount of python and pygame and made some almost done games... 

You started language-hopping before mastering fists language. What makes you think that you can master second language if you did not mastered first? You learn more by becoming competent programmer in one language than skimming surface of many. Especially if you cannot master simple language, like Python.

Here is my advice: dive into C++. You will be back in Python quickly, and happy. :-)

> But with the hole python upgrading to 3.0 and 2.X code won't work anymore, 

You have it wrong. You don't have to upgrade untill pygame upgrades, it might take couple years. Then, your Py2.6 code can be checked and written in a way so you can upgrade it by running 2to3 convertor. Read up about upgrade process before spreading FUD and lies.

---

### Post by ankursethi on 2008-12-19
No need to move to Python 3 yet. The 2.x branch will be actively developed for a long time. Just keep an eye on the PyGame homepage to make sure *they* haven't moved to Python 3. If your library of choice upgrades, then I'm afraid you'll have to upgrade, too. The good news is that there aren't many differences between Python 2.x and 3.0 unless you're a very advanced programmer maintaining thousands of lines of code.

If you *really* want to get into something new, and game dev is what you want to do, then learn C++. Get "C++ Primer" or "C++ How to Program" and dive right in. SDL is a great library for gamedev (PyGame is just a Python wrapper for SDL). Learn SDL from LazyFoo's SDL tutorial (just Google LazyFoo).

---

### Post by Kazade on 2008-12-19
> **jimi_hendrix said:**
> try C++...its not radically different or harder than python...just a LOT more errors and debugging...


> 
C++ == C with classes...and a few slightly different functions in its standard library... (99% of C programs will compile in C++...)


I had to say something about this sorry :)

C++ is MASSIVELY CRAZILY INSANELY more complicated and difficult than Python. C++ is a multi-paradigm language it brings together OOP, Generic programming, elements of functional programming. Some stuff that you can do in C++ will make you go cross-eyed thinking about it (TMP for example). Seriously, I love C++ and I've been using it as my primary language for 8 years, and I still have masses to learn!

The main problem I find with C++ is people grasp the "classes" bit of it and see it is similar to C and think that's it, it's so so not. For example, even just using the "C with classes" part of C++ (ignoring the templates, STL etc.) you have so many things you need to worry about, just off the top of my head:

1. Do you need to declare a copy constructor and assignment operator? What should their prototypes be? If you don't specify them what's the default generated behaviour?
2. Should you declare your destructor virtual? Should you allow exceptions in a destructor?
3. Should your constructor be declared explicit? Should you use the initialization list and what order should you initialize the variables? Should it call a base class constructor?
4. Should your member functions be virtual? Should you follow the NVI idiom? What exception guarantee should it provide? Should you pass by value, reference or reference-to-const? Should the function be const? Should it be inline, explicitly or implictly?
5. Should the class inherit publicly? privately? Should it use multiple inheritance? In which case should it inherit virtually?
6. What operators should be defined? should they be members or non-member, not friend? Should the operators return a const value? Should they handle self assignment?
7. Should your members by private or protected? Should any of them be mutable or volatile? Should you use the PIMPL idiom? Should you use smart pointers? 

That's just off the top of my head the decisions you have to think about designing one class AND we didn't even get into the STL or generic programming or linking issues.

Basically, C++ is hard, if you want to learn to program it's NOT the best first language (Python is great for that) but properly learning and understanding C++ is one of the most rewarding and useful things you will ever do. C++ is not just C with classes, it's far far bigger than that.

P.S just for the curious:
1.a Situation specific, 1.b Situation specific, 1.c To copy on an element by element basis (e.g. does not do *deep* copies for pointers)
2.a If you intend the class to be inherited, 2.b No NEVER EVER
3.a If you don't want implicit casting of arguments, 3.b Yes and the order they are declared in the class declaration, 3.c Sitation specific.
4.a If you intend them to be overridden, 4.b Probably, situation specific though, 4.c The strongest it can (in order of declining strength: nothrow, strong, basic). Always at least basic. 4.d *Usually*: Value if it's a built in type and the original wont be altered, reference-to-const if it's a class that won't be altered, reference if you intend to alter it. 4.e If you don't alter any members. 4.f If it's a small, cheap function (1 or 2 lines) that is used a lot. You can inline it implicitly by defining it in the class, explicitly by putting "inline" in the prototype.
5. All situation specific
6.a Situation specific, 6.b. Non member if you want "classInstance * 2" and "2 * classInstance" to both work for example. 6.c Situation specific, 6.d Yes, if they are an assignment operator
7.a ALWAYS private (see Scott Meyers Effective C++), 7.b Mutable if you want to alter them in a const context. Volatile if they may be altered in a separate thread and you do want your compiler to over optimize and make them a constant (because they appear not to change to the compiler). 7.c Situation specific but can speed up linking, copying, etc. 7.d. Yes pretty much all the time.

---

### Post by AnRa on 2008-12-19
For a simple game you should take a look at [LÖVE](http://love2d.org/).

---

### Post by CptPicard on 2008-12-19
> **Kazade said:**
> I had to say something about this sorry :)

I also have to say something about this, sorry. This was such a "I love punishment and I'm proud of it!" post ;)

> 
C++ is MASSIVELY CRAZILY INSANELY more complicated and difficult than Python.

Which is why it is an abomination...

> 
 C++ is a multi-paradigm language it brings together OOP, Generic programming, elements of functional programming. Some stuff that you can do in C++ will make you go cross-eyed thinking about it (TMP for example).

Any language that doesn't have closures and functions as first-class objects and lambdas doesn't deserve to have "functional" mentioned in the same sentence with it.

C++ makes you go cross-eyed simply because the language is complex. Compare to Lisp where you have more powerful primitives and a very simple base syntax, letting you do stuff that make you go cross-eyed simply because of the conceptual challenge involved (and even then, the language tries its best to make the concept transparent and easier to understand). TMP, for what it's worth, loses totally to Lisp macros :)

> 
 Seriously, I love C++ and I've been using it as my primary language for 8 years, and I still have masses to learn!

Man... 8 years and still learning the language? Get a life and a better tool...

> you have so many things you need to worry about, just off the top of my head: .... That's just off the top of my head the decisions you have to think about designing one class AND we didn't even get into the STL or generic programming or linking issues.

Right! Thanks for reminding me why I don't do C++ ;)

> 
Basically, C++ is hard, if you want to learn to program it's NOT the best first language (Python is great for that) but properly learning and understanding C++ is one of the most rewarding and useful things you will ever do.

Seriously... the stuff you learn from C++ is... "how to program in C++". IMO the rewards to be derived from knowing the technical minutiae of some specific language are questionable.

---

### Post by Kazade on 2008-12-19
Thanks, but I'm well aware of the problems with C++ and I don't use it as my only language, I'm perfectly fluent in C, Python, Java and D also. Right tool for the job and all that (and 95% of the time it isn't C++). I was just pointing out that saying C++ isn't harder than Python is silly.

---

### Post by jimi_hendrix on 2008-12-19
well technically one could write a game in BF...

and you could learn anything if you have the will and patients to learn...and you should probably stick with python...

---

### Post by pmasiar on 2008-12-19
> **Kazade said:**
> C++ is MASSIVELY CRAZILY INSANELY more complicated and difficult than Python.

But of course it is: read this [interview with Bjarne Stroustrup](http://www-users.cs.york.ac.uk/susan/joke/cpp.htm) where he "confessed" C++ was invented to be so insanely complex to keep C++ programmer's salaries high. Now you know why!

Edit: **of course** I know it is a joke. The link I provided says it in first paragraph, no? Do you think I link to an article I have no clue it is about? I did read it - that's why I linked it.

---

### Post by mike_g on 2008-12-19
> But of course it is: read this interview with Bjarne Stroustrup where he "confessed" C++ was invented to be so insanely complex to keep C++ programmer's salaries high. Now you know why! 
Erm, you do know thats a joke right?
> And yes, it is a spoof, obviously. That is obvious from its content alone, and it follows a long tradition of similar spoofs. However, enough people must have fallen for it

---

### Post by linux_tech on 2008-12-19
C programming (good base language), Ruby/Ruby on Rails, Python 3

---

### Post by ankursethi on 2008-12-19
C++, like Perl, is a sort of pick and choose language (more so now than before, thanks to the absurd syntactical whatsits they're adding in C++0X). Before sitting down to code, just take a paper and write down : *I pledge I will **not** use templates in any form today. Amen.*.

There. You're good to go :)

Not that I know much about templates. I've chosen to not learn them until absolutely required. For the most part, I use C++ like "C with classes".

---

### Post by Kazade on 2008-12-19
> **ankursethi said:**
> C++, like Perl, is a sort of pick and choose language (more so now than before, thanks to the absurd syntactical whatsits they're adding in C++0X). Before sitting down to code, just take a paper and write down : *I pledge I will **not** use templates in any form today. Amen.*.

There. You're good to go :)

Not that I know much about templates. I've chosen to not learn them until absolutely required. For the most part, I use C++ like "C with classes".

yeh definitely, i think it's a good idea to use a subset. however i wouldn't avoid the standard containers, they save you a lot of pain :)

---

### Post by christhemonkey on 2008-12-19
> **jimi_hendrix said:**
> if you want something simple there flash but you have to pay for (or pirate) it

I disagree, if you want to try developing flash, you can do so with haXe:
[http://haxe.org/](http://haxe.org/)

It's somewhere in between Java and Python language-wise.

---

