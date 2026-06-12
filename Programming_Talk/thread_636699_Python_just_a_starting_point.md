---
title: "Python just a starting point?"
date: 2007-12-10
forum: Programming Talk
---

### Post by Majorix on 2007-12-10
I hear it being said to starters, "start with Python, it is a good place to start, then you can learn other languages like C/C++ or Java"... How correct of a saying is this? Should one really start with Python and then they have to jump to some other language? Can't they just stick to Python? Is it really a weak language developed with only starters in mind?

I am saying these about Python, but the same goes for Ruby.

The poll question should be clear I hope. Please drop your vote.

---

### Post by Modred on 2007-12-10
I don't believe the members stating "start with Python, it's good for learning to program, then learn C/C++/Java/whatever" mean that Python is a weak language.  Rather, I think it's directed to the common "I want to program, so I must learn C/C++/Java/whatever" mentality that wannabe programmers tend to exhibit.  By directing new programmers to Python, the hope is that they learn some good programming practice in a relatively easy to learn language.

The point being that this advice centers on the belief that Python is easier to learn, not that it is more or less powerful than another language.  After learning *how to program*, picking up another language if the need arises isn't overly difficult.  But for general programming, Python can do more with less code than C/C++/Java most of the time.

Ruby's quite powerful, too, but it has some of Perl's "magic" feeling to it, so it might not be as well suited to new programmers (at least the easily confused ones).

---

### Post by CptPicard on 2007-12-10
Sorry, but that's an outright dumb poll that very well illustrates the typical beginner's fear of "choosing the wrong language" and the desire to be intellectually lazy. A competent programmer will know many languages and will be able to choose the best tool for the job. It is impossible to choose either of your false dilemma options.

Python is a great starter language because of its simplicity, and it's a great language for implementing all sorts of things I don't want to use C/C++ or Java or Scheme or whatnot for. You can implement all sorts of serious things in Python, just not all of them... just like you would be an idiot writing everything in C just as a matter of principle, as in *theory* "you can write everything in C". It's just that you shouldn't.

---

### Post by LaRoza on 2007-12-10
The poll could have any language besides what was listed. One could easily ask if one could do serious programming in VB, or C and the answer would be "yes", but a programmer have such a restriction and would know many languages of more than one paradigm.

If you have no serious interest in programming, and only want to know enough to do little programs for personal use, then Python (or any other high level language) is enough. However, if your goal is to become a serious programmer learning Assembly, C, Python, Haskel, Lisp, Java, PHP, Ruby, etc is your future even if you don't use each language for your programs, knowing them is an invaluable learning experience.

---

### Post by Majorix on 2007-12-10
> **LaRoza said:**
> The poll could have any language besides what was listed. One could easily ask if one could do serious programming in VB, or C and the answer would be "yes", but a programmer have such a restriction and would know many languages of more than one paradigm.

But do you ever see any statements like "I want to learn Python because I will use it in my job" or "I am going to learn Python since they teach us that in school"? I am a software engineering student, and they teach us VB in the school, next year we will learn C; and we will use either one at work and not Python or Ruby.

And thanks to the poster above LaRoza for being so kind and calling the poll "outright dumb". Thanks to gods, Ubuntu community doesn't have many people like him.

---

### Post by LaRoza on 2007-12-10
> **Majorix said:**
> But do you ever see any statements like "I want to learn Python because I will use it in my job" or "I am going to learn Python since they teach us that in school"? I am a software engineering student, and they teach us VB in the school, next year we will learn C; and we will use either one at work and not Python or Ruby.


Google hires Python programmers, in fact, I think they hired the creator of Python.

MIT teachers Python as a first language.

They teach you VB and next year C, I have taught myself, all the languages on my wiki, to various degrees. The learning of the syntax is very easy, learning programming is hard. Data structures, algorithms, project management, and such are where a professional programmer should focus. 

One should never ask "should I learn", yes you should. Learning is good.

---

### Post by Majorix on 2007-12-10
I knew about Google hiring Guido van Rossum. But I didn't know about MIT teaching Py as the first language (do you mention that they learn it in the first year or as the main language throughout the course?), my friend studying computer engineering (that is one of his 2 majors) in the US learns Java.

And to clarify a few things, I AM using Py and have already read its tutorial twice, so there is no thing like me asking if I should learn Py or not.

---

### Post by xlinuks on 2007-12-10
The truth is, python is just as good as you don't need extra speed. It's good at creating applications, working with databases and alike.
But if speed is critical for you, then you should consider some other solution like C/C++ or Java.
IMHO if a block of code executes in C within 10 seconds, then the average execution time for a similar block of code in the corresponding language would be the following:
Java - 11-20 seconds (50% more slowly)
C++ - 9-12 seconds (almost same speed)
Python - 30-70 seconds..
Of course it depends on exactly what type of code block is executing and on the version of the compiler/platform, here's a short benchmark for Java6 vs Python (Choose Python vs C or other lang if you find it interesting)
[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=java&lang2=python]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=java&lang2=python")

---

### Post by LaRoza on 2007-12-10
> **xlinuks said:**
> The truth is, python is just as good as you don't need extra speed. It's good at creating applications, working with databases and alike.
But if speed is critical for you, then you should consider some other solution like C/C++ or Java.
IMHO if a block of code executes in C within 10 seconds, then the average execution time for a similar block of code in the corresponding language would be the following:
Java - 11-20 seconds (50% more slowly)
C++ - 9-12 seconds (almost same speed)
Python - 30-70 seconds..
Of course it depends on exactly what type of code block is executing and on the version of the compiler/platform, here's a short benchmark for Java6 vs Python (Choose Python vs C or other lang if you find it interesting)
[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=java&lang2=python]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=java&lang2=python")

What about C modules used in Python? Or Python byte code? Or Python compiled to executable? The most expensive time to waste, programmer time?

---

### Post by xlinuks on 2007-12-10
I mean that for everything you do you have to pay a price. In C one generally gets nice speed by default, while such langs as JavaScript, PHP, Java or Python (especially Java) suffer from memory overhead, performance and startup time issues (again - it's critical for Java not as much for Python). What's true is true, you might choose to spend less of your time and thus make more money, but the bigger the project the more you have to think whether C/C++ would be a smarter choice, those who have to create apps for managing server side heavy system loads know what I'm talking about. I'm myself a Java programmer, but I know it's price, for instance ask yourself why such games like Doom3 or alike aren't written in Java or Python (and won't likely be written anytime soon).

---

### Post by Majorix on 2007-12-10
> **xlinuks said:**
> ...here's a short benchmark for Java6 vs Python (Choose Python vs C or other lang if you find it interesting)
[http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=java&lang2=python]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=java&lang2=python")

Thanks for the interesting link, I was looking for something like this.

---

### Post by LaRoza on 2007-12-10
> **xlinuks said:**
> I'm myself a Java programmer, but I know it's price, for instance ask yourself why such games like Doom3 or alike aren't written in Java or Python (and won't likely be written anytime soon).

Oblivion and many games use Python. They are mosty written in C, but Python is also used.

---

### Post by ThinkBuntu on 2007-12-10
Python is a bit for amateurs, and I've heard of some small groups that use Python pretty often, although you may or may not have heard of them: NASA, BitTorrent, and YouTube. One does some space thing, the other supposedly accounts for the greatest share of all internet traffic, and the last one made its founders some pocket money when this indexing company bought 'em up. Oh, and [the indexing company has been known to do business pretty well too]("http://www.google.com/url?q=http://finance.google.com/finance%3Fclient%3Dob%26q%3DGOOG&sa=X&oi=stock&ct=title&usg=AFQjCNFLCLl1IPgu4gTQrJlJOkDUaokQvQ").

</joke>
Just get into it and learn it. Very powerful, fairly simple, can be used on the web, for the desktop, in a shell, or whatever else you may desire. You really can't go wrong. I continue to see Python as a more mature, more accessible Ruby that's really proven itself. Granted, [Ruby has its adherents as well]("http://www.yellowpages.com/")...

---

### Post by xlinuks on 2007-12-10
IMHO in other words more than 95% of cutting-edge games use C, and partly assembly where there's a need to do matrix-translations to make the persons 'move' and 'jump'. I used to praise assembly in the past, then Java, but in the end one realizes that there's no such thing like a Holy Grail (not for now at least). If you want to be a professional you will have to use different languages.
BTW when it comes to creating apps for Linux it's IMHO much better to use Python for that reason than Java, it would take too long to tell why.

---

### Post by tyoc on 2007-12-10
I guess is good to have nice memories of your first lang.

My first lang was Pascal and I "hate it" I dont like that lang, has some contradictions from my POV even when I was begginer, havent seen sense for example in the procedure/function (i)rrationale, I almost fail the subject even that in the introductory curse of pseudocode and some structured programming introduction with flow diagrams I was very good. By fact, I hope I never touch again Pascal or related :P.

After that I learn C, almost by myself (I read like the middle of the enciclopedy of C or some like that, a white book with a big blue C in the cover, and with that was more than enought), in fact is the lang that I consider my first real lang.

And thought that I have read and sometimes learn more than 1 lang (sometimes 2 or more at the same time), the times that I have been hired, was for work with C.

----
And by fact I cant answer the poll because there is no option that I like :P. Is a good starting point, more if you find the "way" or porpuose, but programming is more than a good start.

---

### Post by pedrotuga on 2007-12-10
yay! a "is this language good?" thread!

Mate, python is a modern language, it's dynamic typed which i think it's cool, it has a f'king awesome syntax and because of that and a few other characteristics it gets really simple.

Just learn it, later you can learn others and have your own opinion. for a beginner i think it can be cool to have a fast learning curve, python has it. PHP is IMHO even easier to learn but it targets more web aplication development.

About ruby i can't say anything... i never heard about it before rails came into the scene.

---

### Post by pmasiar on 2007-12-10
> **xlinuks said:**
> IMHO in other words more than 95% of cutting-edge games use C, and partly assembly where there's a need to do matrix-translations to make the persons 'move' and 'jump'. 

Or more correctly: 95% of time-constrained code is in C. This is fine with Python, it also uses C libraries for speed. The only difference is, why waste time on coding in C what is not time-constrained? Why not code it in Python?

It seems to me that free software zealots refuse to be pragmatic, unlike commercial companies: ie MSFT is working on Python implementation (IronPython), and hired smart free software developers to make .NET 3.0 more friendly for dynamically typed languages. IronPython in some test it 2 times faster than C-Python. They even have automatic translation from  IronPython to JScript (JavaScript.NET). So while C zealots flame Python newbies about speed of C code, MSFT is concerned (correctly) about speed of development, and uses IronPython to ducktape apps together from C# libraries.

If we assume that 5% of low-level code is responsible for 80% or runtime (stats out of thin air :-) of course) then it does not matter how fast is the remaining 95% of the code and might be as well done in Python with negligible impact on overall app speed.

---

### Post by Wybiral on 2007-12-10
lol at the one person who voted yes!

To anyone who doesn't think python is capable of 3d games, check out Soya3d, the blender game engine, PyOpenGL, PyGame, and PyODE. Only crazy people write their own Dynamics/Physics engines, the rest of us use ones that have been tested and developed by others. The good ones have Python bindings so it's not different. If you ARE crazy (or you're more interested in engine development) you can write them in C and use SWIG/Pyrex to make a Python module from them... Then you develop your game in Python.

---

### Post by CptPicard on 2007-12-10
> **Majorix said:**
> And thanks to the poster above LaRoza for being so kind and calling the poll "outright dumb". Thanks to gods, Ubuntu community doesn't have many people like him.

You're welcome. Things have differing amounts of objective intellectual merit, and I'm glad to be of assistance pointing it out. I'm just afraid a popularity contest is not going to make the poll not exclude the middle by making people choose from two very strong and contrary statements, something knowledgeable people will not do. It seems like it's just trolling out for viewpoints of extremists, and thus seeking  validation for outcomes of some kind of... frustrations. Answering to the poll, either the Python proponents must be stuck to their language forever (which is impossible or at least painful for any language and easily refutable), or they must admit Python is useless :)

> But do you ever see any statements like "I want to learn Python because I will use it in my job"...

This is partly because Python is still fairly young in the industry. It will catch on as the young Python hackers mature -- someone always has to lead the way in industry acceptance.

An interesting feature of Python from my point of view that it is a remarkably "good enough jack of all trades" language, although I would not consider myself a Python evangelist. I have my pet peeves about the language, but I'll give it its dues. What I mean is... it gives you a fairly painless middle ground to achieve a lot of things, and you tend to need a *specific* reason to migrate away from it as your requirements dictate. Because it interfaces  nicely to C, performance issues are not.. really issues, because you don't need to write *everything* in C, which would, again, make it all painful.

(Yes pmasiar, I am slowly turning a believer from a sceptic, I must admit...)

This is also why "well 3D engines aren't 100% written in Python" arguments are pointless. Of course they aren't, but you can optimize the bits that you need to, and then comfortably glue your game together with, say, Python. Or script high-level object behaviour easily.

When it comes to Java, its biggest drawback is bad integration of JVM memory management with OS memory management. But this is a general issue with VMs, and not Java-specific. As long as you keep somewhat conservative with how much little temporary objects you spam around in your code, your memory management overhead can be minimized. Newer JVMs are even better at all this because of smarter garbage collection strategies.

I write quite a lot of CPU-intensive code, and Java has pretty much always surprised me with how little point there is in porting to C/C++ if you're just running algorithms implemented with due diligence... JIT compilation is better than people think.

---

### Post by Wybiral on 2007-12-10
> **CptPicard said:**
> Because it interfaces  nicely to C, performance issues are not.. really issues, because you don't need to write *everything* in C, which would, again, make it all painful.

The best part about this is that there are tools like SWIG and Pyrex that basically do all of this work for you. I've been playing with SWIG and Pyrex both and I have yet to run into any of my old C or even C++ code that wasn't more than a few minutes worth of setup to integrate into Python. It's beautiful!

As far as Pythons use in the industry... Google... Look how successful they are and how rapidly they develop applications. They almost exclusively program in C++, Java, and Python which IMO is probably all you really need these days. Not that other languages are bad, but with just those three you can tackle about any problem, and they each have their place depending on your goal. Google == smart, NASA == smart.

---

### Post by slavik on 2007-12-11
> **Majorix said:**
> I hear it being said to starters, "start with Python, it is a good place to start, then you can learn other languages like C/C++ or Java"... How correct of a saying is this? Should one really start with Python and then they have to jump to some other language? Can't they just stick to Python? Is it really a weak language developed with only starters in mind?

I am saying these about Python, but the same goes for Ruby.

The poll question should be clear I hope. Please drop your vote.

well, if you want to simulate the power consumption of US, I doubt the 1% performance hit that Python gives you would be considered negligible. You can't always buy more RAM or faster processors.

---

