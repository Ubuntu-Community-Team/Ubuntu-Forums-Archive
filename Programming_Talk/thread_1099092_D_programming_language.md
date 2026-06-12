---
title: "D programming language"
date: 2009-03-17
forum: Programming Talk
---

### Post by soltanis on 2009-03-17
Recently, the a language called the D programming language has come to my attention. It's basically a descendant of C/C++ but without C++'s extra frills. It aims to be a systems-level language, fast and lightweight but powerful, like C before it.

I took a look, and I like the idea of it, but there's a lot of stuff in the language I don't like, for example, unlike nearly every other language I have ever seen, this is wrong in D:

```

if(var == null)

```

Rather, null is an object with no properties so you must do

```

if(var is null)

```

I can live with that (barely...it bothers me) but on top of that, the standard library is really...annoying (which is why I guess they wrote a new one, except that one caused even more problems with incompatibilities). It also has a bit of problems with exporting code (mostly with C++, it's pretty clean with C).

What's everyone else's opinion on this language? I'd really like to see it become mainstream -- it really seems to have a lot of potential -- but the evil C++ seems to be overshadowing it, and slow-as-hell VM languages (C#, Java) are crowding out the rest of the market. Who will give poor D a chance?

---

### Post by .Fuze on 2009-03-17
Why so hating on Java? :(

As much as I love C/C++, not only is Java more.. "2.0", languages such as D do not need a chance! I mean because C/C++ as well as Python are the most popular -- from what I've seen --, lesser-known-but-similar languages such as D are unnecessary.

but that's my opinion.

---

### Post by CptPicard on 2009-03-17
I have been looking at D with a lot of interest for a long while, and  hacking a little in it. I really like the potential, and actually am thinking of helping fill in the library gaps when I become fluent enough in it and things start to stabilize a little.

It is really nice how D manages to introduce some important modern stuff while still keeping the language pretty orthogonal and "clean". I don't feel like I need to be too mindful of the language itself while using it, and if, while coding, I can "forget about the language and just think in it", it's always a good sign.

Another contender for the "more high-level than C, more clear-cut than C++" position in my toolbox is currently objective-C, but we'll see about that... I am not yet convinced that the objC message dispatching system is actually fast enough, although I end up writing an ad hoc object system implementation most of the time when I'm writing anything nontrivial in C. Now, of course I usually don't put speed as the first requirement, but here in this niche of language-space it does matter...

---

### Post by simeon87 on 2009-03-17
> **.Fuze said:**
> As much as I love C/C++, not only is Java more.. "2.0", languages such as D do not need a chance! I mean because C/C++ as well as Python are the most popular -- from what I've seen --, lesser-known-but-similar languages such as D are unnecessary.

So popularity determines which languages should be used? That's an odd argument...

---

### Post by soltanis on 2009-03-17
> **.Fuze said:**
> As much as I love C/C++, not only is Java more.. "2.0", languages such as D do not need a chance! I mean because C/C++ as well as Python are the most popular -- from what I've seen --, lesser-known-but-similar languages such as D are unnecessary.

With C as baseline, Java takes around 1-6x as long to solve the same problems requiring usually about 20x the memory.

Python requires anywhere from 1-241x the time and 31x the memory usage.

C++ performs on-par with C in terms of speed, with its worst memory overhead at 8x that of C.

Objective-C takes 1-8x the time and 1-8x the memory (that dynamic memory dispatch carries some baggage with it).

Now, D takes 1-2x the time and 1-8x the memory as C, in other words, it lags slightly behind C++ in terms of performance. This is what I want to use D for; not because of fancy language features (even though those are really damn nice) but mostly because it's applicable, at least in theory, it seems, to speed-critical programming.

The GNU D compiler is, at least (the digital mars version doesn't seem to be as great).

CptPicard, how did you learn D? Finding resources that tell you about the language coherently is proving difficult for me.

---

### Post by cabalas on 2009-03-17
> **simeon87 said:**
> So popularity determines which languages should be used? That's an odd argument...

While an odd argument it is sadly the truth, especially in the corporate world, Paul Graham wrote an interesting essay about it a few years back I think this is the link to the right one but I'm unsure [http://paulgraham.com/avg.html](http://paulgraham.com/avg.html)

---

### Post by Can+~ on 2009-03-17
> **soltanis said:**
> With C as baseline, Java takes around 1-6x as long to solve the same problems requiring usually about 20x the memory.

CptPicard, how did you learn D? Finding resources that tell you about the language coherently is proving difficult for me.

So sheer speed is the main reason of your choice?

---

### Post by soltanis on 2009-03-17
I don't claim that D is blazing fast, but more or less, yeah. Speed, and lower memory usage (though 8x is still a lot of overhead...less than 20).

Java is consistently slow on startup. Even with JIT compilation, its still got those huge class libraries to load.

---

### Post by Ferrat on 2009-03-17
> **simeon87 said:**
> So popularity determines which languages should be used? That's an odd argument...

That's the way of the free market, doesn't matter what is better or has more of what you need and it might be sad but it's a fact. 
It's extremely rare for the public market to adapt the version/item/thing/etc. which is best at first take, often an inferior product is launched by someone that has more marketing and the better version dies due to the popularity of the other product killing it. 

This is also true when it comes to stuff like programming languages, C7C++, Java, Python and a few are the ones people use often because that is where the popular focus is. Many times people might use the "wrong" language for a problem just because that is the language they know, also C/C++ etc have set international standards that many people know of, have wide libraries and so on making them more attractive to users. 

Only if a language is so good, has something new that's needed and/or manages to attract a really dedicate group of users that evolve the language and add the libs etc then it might get picked up by the mainstream but often this isn't the case and even if it is, it often takes years. 

I'm not really agreeing with the statement that D is unnecessary but the fact remains that popularity dictates what will be used and what won't be. 

Practical example, take the Pandora hand-held that is due out soon, much more powerful than Nintendo DS and PSP, my guess is that won't matter for the mainstream, sure ppl will get the Pandora but PSP being inferior will still sell more units due to popularity and more games available, which resluts in less developed games for Pandora compared to PSP and so on. 

As for D itself seems interesting enough but right now I'm more looking to the end result of C++0x :)

---

### Post by CptPicard on 2009-03-17
> **soltanis said:**
> 
CptPicard, how did you learn D? Finding resources that tell you about the language coherently is proving difficult for me.

Yep, stuff is a bit hard to come by ... I am still quite the n00b myself, but I've mostly just been googling and gathering knowledge bit by bit. I wish something like "D" wasn't so hard to google for :)

How about [http://www.dsource.org/](http://www.dsource.org/) ?

---

### Post by soltanis on 2009-03-17
Seems like the best way to learn this language is by trial and error. Which isn't too bad (since things do what you expect).

---

### Post by Can+~ on 2009-03-17
> **soltanis said:**
> I don't claim that D is blazing fast, but more or less, yeah. Speed, and lower memory usage (though 8x is still a lot of overhead...less than 20).

Java is consistently slow on startup. Even with JIT compilation, its still got those huge class libraries to load.

Who cares about memory usage? Or sheer speed?

You'll soon find that Memory access speed or processing is rarely the bottleneck, the main bottleneck lies on the hard disk. So unless you have a particular reason to maximize performance, you should look for actual language features (like built-in library size, compatibility, etc) and not plain speed.

---

### Post by kjohansen on 2009-03-17
> **Ferrat said:**
> That's the way of the free market, doesn't matter what is better or has more of what you need and it might be sad but it's a fact. 
It's extremely rare for the public market to adapt the version/item/thing/etc. which is best at first take, often an inferior product is launched by someone that has more marketing and the better version dies due to the popularity of the other product killing it. 


this what us economists would call "network externalities", an initially inferior product becomes the preferred product because of a "network" of users add a "network" benefit.  

i can send my c++ or java code to practically any programmer and they can run and edit it. or i can hire a new person and expect them to carry on.  if you code in a niche language you dont have this benefit.

---

### Post by CptPicard on 2009-03-17
> **soltanis said:**
> I don't claim that D is blazing fast, but more or less, yeah. Speed, and lower memory usage (though 8x is still a lot of overhead...less than 20).

I don't know where you're getting these numbers from, but really, they're nearly as good as random. In particular that kind of differences in memory usage between D and, say, C, are almost certainly due to implementation, not language, differences.

---

### Post by monkeyking on 2009-03-17
> **soltanis said:**
> With C as baseline, Java takes around 1-6x as long to solve the same problems requiring usually about 20x the memory.

Python requires anywhere from 1-241x the time and 31x the memory usage.

C++ performs on-par with C in terms of speed, with its worst memory overhead at 8x that of C.

Objective-C takes 1-8x the time and 1-8x the memory (that dynamic memory dispatch carries some baggage with it).

Now, D takes 1-2x the time and 1-8x the memory as C, in other words, it lags slightly behind C++ in terms of performance. This is what I want to use D for; not because of fancy language features (even though those are really damn nice) but mostly because it's applicable, at least in theory, it seems, to speed-critical programming.

The GNU D compiler is, at least (the digital mars version doesn't seem to be as great).

CptPicard, how did you learn D? Finding resources that tell you about the language coherently is proving difficult for me.

Just out of curiosity how did you come across these numbers?

---

### Post by soltanis on 2009-03-18
The language shootout ([http://shootout.alioth.debian.org/);](http://shootout.alioth.debian.org/);) those particular benchmarks are on a Debian Sempron.

D has at most 3 implementations, and I was talking about GDC anyway.

Eh, it's sad but true; D probably doesn't have too much of a future.

---

### Post by jimi_hendrix on 2009-03-18
> **soltanis said:**
> CptPicard, how did you learn D? Finding resources that tell you about the language coherently is proving difficult for me.

same here...once i got past the official tutorial thing, which was brief, i couldnt find anything

---

### Post by igouy on 2009-03-18
> **soltanis said:**
> The language shootout ([http://shootout.alioth.debian.org/);](http://shootout.alioth.debian.org/);) those particular benchmarks are on a Debian Sempron.

All the programs show a "build & benchmark results" log - check the date - some of those Java programs on Sempron are mid 2007, and have been much improved since then, which of course gives [_a different impression when you compare with D_]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=java&lang2=dlang&box=1").

D is not included in the current benchmarks game measurements, but a D enthusiast has started [_a D benchmarking project_]("http://dbench.octarineparrot.com/").

---

### Post by CptPicard on 2009-03-18
I would be very, very surprised if a D-like language, after optimizing compilers have matured, would lag, say, C++ much in examples that do not, for example, force constant garbage collection or something.

---

### Post by rendon on 2009-03-18
The greatest words of wisdom I've heard in choosing a language to use is: *"Use the right tool for the right job"*

ergo, I wouldn't use PHP to make a 3d game, and I wouldn't use C++ to make a webpage.

After that's been settled, I might consider some of these:

1.  is it cross-platform?  I might need to switch OSes someday, or share with the user of a different OS

2.  how complex do I need to be?  if I can dumb it down I will.  I'm not going to use Java to get some info from a command line and store it in a file, that simple job takes 20 lines in Java and 2 lines in Python.

3.  Good documentation.  Good languages always have clear and easy to understand documentation.  how else can you learn it?

4.  Popularity does matter sometimes, I don't want think that a potential end-user has to download and install a compiler or runtime just for me, I'd hope they already have it.


just my 2 cents anyway... ;)

---

### Post by jimi_hendrix on 2009-03-18
> **rendon said:**
> The greatest words of wisdom I've heard in choosing a language to use is: *"Use the right tool for the right job"*

ergo, I wouldn't use PHP to make a 3d game, and I wouldn't use C++ to make a webpage.


is it even possible to write a page in C++

---

### Post by ZuLuuuuuu on 2009-03-18
> **Can+~ said:**
> Who cares about memory usage? Or sheer speed?

This is of course a strange statement. I am one of them, at least, who cares about memory usage and speed.

I started to learn D but stuck while reading the current documentation. I don't know much about C++ and the likes (C#, Objective-C...) so I needed a beginner book which is not present for D at that time. For example, the book "Learn to Tango with D" teaches you how to do exceptions in D but does not teach you what exceptions are (the subject "exceptions" might be a wrong example since I can't remember the book much, but you got the point). This might not be a problem for beginner subjects like for loops or if statements etc. but become a problem when you face with concepts belonging to this kind of languages; like "templates" or "generics", for example.

If this is still the case then the best way to learn it is, I guess, to learn C++ and then learn the differences between C++ and D.

---

### Post by sujoy on 2009-03-18
> **jimi_hendrix said:**
> is it even possible to write a page in C++

[http://www.gnu.org/software/cgicc/](http://www.gnu.org/software/cgicc/)

---

### Post by Habbit on 2009-03-18
Of course it is possible to "write a web page in C++". See [_Common Gateway Interface_]("http://en.wikipedia.org/wiki/Common_Gateway_Interface")

---

### Post by crazyfuturamanoob on 2009-03-18
Accident, sorry. The preview and submit post buttons are swapped in every forum.

---

### Post by rendon on 2009-03-18
As already mentioned, yes you can write pages in C++.  I'd also like to mention that you can write pages in ANY language, but the server has to be configured to allow it.

When a request is made to a folder in your public directory (such as public_html or /var/www) the server software (such as Apache) is given a set list of tasks to do depending on configuration.  Just as you can install and allow PHP to do:

```

print "<html>\n<body>\n";
print "Hello World!\n"
print "</body>\n</html>\n";

```

Thus you can also configure Apache to allow C++ to do something like:

```

cout << "<html>\n<body>\n";
cout << "Hello World!\n"
cout << "</body>\n</html>\n";

```

or python, or java, or whatever you want.

I imagine PHP just became more popular because it has a lot of fancy modules and functions to make webpage creation easier.  The fact that you can embed the PHP mixed into the raw HTML is probably the key factor that makes it the most convenient.

---

### Post by slavik on 2009-03-18
accessing DB in php is simpler as well.

---

### Post by monkeyking on 2009-03-19
> **Can+~ said:**
> Who cares about memory usage? Or sheer speed?

You'll soon find that Memory access speed or processing is rarely the bottleneck, the main bottleneck lies on the hard disk. So unless you have a particular reason to maximize performance, you should look for actual language features (like built-in library size, compatibility, etc) and not plain speed.

I care alot about speed,
and even more about memory.
In datamining this is essential features of a language.

It is true that harddisk io is alot slower than memory io.
Which again is alot slower than cache io, which again is alot slower that register io.

But generalizing this to "the main bottleneck" is wrong and over simplifying.

---

