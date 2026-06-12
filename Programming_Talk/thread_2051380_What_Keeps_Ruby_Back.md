---
title: "What Keeps Ruby Back?"
date: 2012-09-01
forum: Programming Talk
---

### Post by Majorix on 2012-09-01
I am reading the PickAxe after years of keeping it there on the e-reader.

I have always been willing to learn and use Ruby, and since I am reading the book now, I am having a lot of fun. I mean I have been programming in different languages (C, C++, C#, VB, VB.NET, Python, Java, PHP, X86 Assembly) for almost 10 years now and never had so much fun!

So this makes me think: What makes Ruby less popular?

One reason I am thinking is the introduction of blocks. A different way of thinking for older, traditional developers. I must say it got me thinking for a while to understand the theory, but once you grasp it, it provides a new and fun way of using the language.

What do you think the reason might be? (Please don't start a language war :) )

---

### Post by trent.josephsen on 2012-09-01
I have Perl for quickie scripts and heavy text processing tasks. I have Python for longer scripts that demand a little more structure. I don't feel a compelling need to learn another scripting language.

```
$perl->age() > python.age() > ruby.age
```
Could it be as simple as that?

Edit to be clear: I picked on Perl and Python because, based on my experience, they most directly compete with Ruby on all points; other languages like C, C#, Java, and PHP might well be found in the same environments for one reason or another, but the overlap is less complete.

---

### Post by ratcheer on 2012-09-01
I can't answer your question because I also feel that Ruby is the best thing going right now. I have been an OO programmer for quite a while (mostly Smalltalk and c++) and when I started looking for the "best" language for my wants and needs, it came down to Ruby.

But 95% of everybody always says Python.

Different strokes for different folks, I guess.

Tim

---

### Post by Majorix on 2012-09-01
> **trent.josephsen said:**
> ...
```
$perl->age() > python.age() > ruby.age
```
Could it be as simple as that?
...

That would hold right if C# was older than Ruby, since it is quite more popular than Ruby. And in turn, Ruby is more popular than older ones like the ancient Lisp-based languages.

---

### Post by diesch on 2012-09-01
[LIST]
[*]For quite a lot of people Ruby is Ruby on Rails. They do not know that you can use it for anything but web programming
[*]Ruby doesn't have officially supported bindings for Gnome
[*]Ruby doesn't have the simple syntax of Python or the speed of C or C++, isn't as quick'n dirty as Perl or PHP and isn't backed by a large company like Java.
[/LIST]

---

### Post by Mikeb85 on 2012-09-01
Speaking of what holds Ruby back, does anyone know of any good GUI frameworks for Ruby for creating desktop applications?  Gnome and QT bindings seem to be very out of date...

---

### Post by Majorix on 2012-09-01
> **diesch said:**
> [LIST]
[*]For quite a lot of people Ruby is Ruby on Rails. They do not know that you can use it for anything but web programming
[*]Ruby doesn't have officially supported bindings for Gnome
[*]Ruby doesn't have the simple syntax of Python or the speed of C or C++, isn't as quick'n dirty as Perl or PHP and isn't backed by a large company like Java.
[/LIST]

2nd point:
What do you mean by "officially supported"? As long as the bindings exist (and they do) and they work (they do), I am not bothered :)

3rd point:
Ruby has its strong sides too, just like those languages you named. Built-in regex support, block theory, complete OO, many ways to do something are just the ideas that pop to my mind.

---

### Post by trent.josephsen on 2012-09-01
> **Majorix said:**
> That would hold right if C# was older than Ruby, since it is quite more popular than Ruby. And in turn, Ruby is more popular than older ones like the ancient Lisp-based languages.
C# and Ruby don't directly compete for all the same roles and it's not meaningful to compare their popularity as a scalar.

---

### Post by diesch on 2012-09-01
> **Majorix said:**
> 2nd point:
What do you mean by "officially supported"? As long as the bindings exist (and they do) and they work (they do), I am not bothered :)


It's not listed at [http://developer.gnome.org/references#api-bindings](http://developer.gnome.org/references#api-bindings) and [http://www.gtk.org/language-bindings.php](http://www.gtk.org/language-bindings.php) doesn't look that promising either.

[https://github.com/mvz/ruby-gir-ffi](https://github.com/mvz/ruby-gir-ffi) isn't easy to find and it's not clear how stable it is and what the plans for the future are.

That's just not what I would choose as a base for a new project.


> **Majorix said:**
> 
3rd point:
Ruby has its strong sides too, just like those languages you named. Built-in regex support, block theory, complete OO, many ways to do something are just the ideas that pop to my mind.

Of course Ruby has its nice sides, too. But they aren't as obvious as for some other languages.

---

### Post by Lux Perpetua on 2012-09-02
> **Mikeb85 said:**
> Speaking of what holds Ruby back, does anyone know of any good GUI frameworks for Ruby for creating desktop applications?  Gnome and QT bindings seem to be very out of date...I've generally found Ruby's GTK2 bindings to be pretty painless to use. Surely that isn't considered out-of-date?

---

### Post by Majorix on 2012-09-03
> **trent.josephsen said:**
> C# and Ruby don't directly compete for all the same roles and it's not meaningful to compare their popularity as a scalar.

I don't believe in the "roles" of languages. Any language can do anything on any platform as long as you know what you are doing.

> **diesch said:**
> It's not listed at [http://developer.gnome.org/references#api-bindings](http://developer.gnome.org/references#api-bindings) and [http://www.gtk.org/language-bindings.php](http://www.gtk.org/language-bindings.php) doesn't look that promising either.

[https://github.com/mvz/ruby-gir-ffi](https://github.com/mvz/ruby-gir-ffi) isn't easy to find and it's not clear how stable it is and what the plans for the future are.

That's just not what I would choose as a base for a new project.




Of course Ruby has its nice sides, too. But they aren't as obvious as for some other languages.

I don't know what happened to the old Gnome bindings for Ruby. I remember installing them quite some time ago. I don't really do any GUI job though, so cannot say more.

Also, Ruby has "obvious" strong sides too, one being the "everything is an object" theory, which I haven't seen implemented anywhere else. Correct me if I am wrong.


And another reason Ruby is kept back is that nobody cares lol, this thread has been up for 2 days and did not get many replies really.

---

### Post by Some Penguin on 2012-09-03
> **Majorix said:**
> I don't believe in the "roles" of languages. Any language can do anything on any platform as long as you know what you are doing.


Memory efficiency and threading support really, really beg to differ.

If a language's interpreter has a single global lock, it's not likely to scale efficiently to applications where e.g. 8 CPU / 60+ GB RAM / gigabit+ network to nearby fast RAID arrays are normal.   Running multiple interpreters can be extremely heavyweight relative to running multiple threads depending on the duration of tasks.

Likewise, if you're firing up a full JVM to do a trivial text-manipulation that a scripting language can do very simply, you're doing it wrong.

---

### Post by trent.josephsen on 2012-09-03
> **Majorix said:**
> I don't believe in the "roles" of languages. Any language can do anything on any platform as long as you know what you are doing.

Well sure. I didn't say that Ruby or C# would be *inadequate* for any particular "role", just that they don't *directly compete* for the same roles. I wouldn't use VHDL to design a Web server and I wouldn't use PHP to write a kernel module; if you agree, then you have at least some idea of what "roles" different languages excel in.

C# excels particularly in the "role" of application-development-language-for-Windows. "For Windows" is an important part of that particular role and C# wouldn't be where it currently is in terms of popularity if it weren't. I'm not trying to say that's the only "role" that C# plays, but it's a role that C# puts particular emphasis on, whereas Ruby doesn't. That's all I'm trying to say by "they don't directly compete".

> Also, Ruby has "obvious" strong sides too, one being the "everything is an object" theory, which I haven't seen implemented anywhere else. Correct me if I am wrong.
I've heard this touted several times as a "unique" strength of Ruby but I really don't understand how it's different from Python's model. I'd also like to be corrected on that point.

---

### Post by xytron on 2012-09-04
There just isn't  anything innovative about Ruby. 

It's more a matter of preference of syntax.

It's not a bad programming language.  A good choice for web applications but as a general purpose programming language it's just another dynamically typed programming language.

---

### Post by ratcheer on 2012-09-04
> **Majorix said:**
> 

Also, Ruby has "obvious" strong sides too, one being the "everything is an object" theory, which I haven't seen implemented anywhere else. Correct me if I am wrong.



**Smalltalk**, certainly. I'm pretty sure there are others.

Tim

---

### Post by durdenstationer on 2012-09-04
> **Majorix said:**
> I don't believe in the "roles" of languages.

So then you think Ruby is appropriate for writing kernels and real-time operating systems?

> **Majorix said:**
> Any language can do anything on any platform as long as you know what you are doing.

Not really true.  Ruby doesn't allow me to do raw memory-mapped variables like I can do in C in this way:

> #define PORTBASE 0x40000000
unsigned int volatile * const port = (unsigned int *) PORTBASE;


Ruby may be Turing complete, but the definition of Turing completeness does not mean what you think it does.

---

### Post by trent.josephsen on 2012-09-04
> **durdenstationer said:**
> Not really true.  Ruby doesn't allow me to do raw memory-mapped variables like I can do in C in this way:

I agree with what you say in principle, but I think this is a weak argument. Memory mapping could easily be modeled in most "higher level" languages as a simple array of bytes; it's not done that way **because** people don't use HLLs for memory mapping, not the other way around. Weak typing might be a stronger argument, but that's something that is often better avoided even on the low level.

I think *expressiveness* is really the issue: how closely a statement in Ruby or whatever correlates to a machine instruction, or to put it a different way, how many machine instructions can be replaced by a single statement in a HLL. Consider the following statement:

```
foo.bar();
```

That could be C or Java. (Could also be Python, come to think of it.) But in C which version of "bar" is called is determined at compile time based on the declared type of "foo". In Java it may instead be determined at run time based on the content of the memory referred to by "foo". The C version correlates to a few dozen cycles, max; the Java version might take hundreds, because it's doing a more complex (and more expressive) operation.

Expressiveness is an obstacle, though, when you're writing low level stuff, which I imagine is what you were really trying to get at. As far as that goes, we're in agreement.

---

### Post by durdenstationer on 2012-09-04
Sure an HLL **could** allow you to do something similar, but many don't especially Ruby. So one cannot really say you can do everything in one langauge you can in another. Statments like this come from a flawed understanding of what Turing completeness means.

---

### Post by Mikeb85 on 2012-09-06
Well, I'm a newb programmer (learning it for fun, and to create some scripts to help me analyze equity markets), and Ruby is what I chose after a bit of 'research' (ie. looking for newb-friendly and powerful language).  Gems make adding libraries incredibly easy, the syntax is very easy to read and understand, and there's a great amount of gems to choose from.   Of course, most of the libraries seem to revolve around Rails, I haven't seen too many desktop applications made in Ruby, it's a shame, it seems like it would be great for quick development.  Then again, I'm a complete newb, maybe I missed something...

---

### Post by CptPicard on 2012-09-07
> **durdenstationer said:**
> Statments like this come from a flawed understanding of what Turing completeness means.

Or perhaps your understanding what the other guy means by references to Turing completeness is flawed.

Underlying architecture specifics are assumed to be irrelevant (as they are in the end) when making references to "you can do anything in some language that you can do in any other language". Of course, in practice and even in my "architecture does not matter but some languages are better than better than others in some abstract way" sense that kind of a statement is close to being unhelpful, as it so general that it does not really allow to make distinctions between languages.

---

### Post by trent.josephsen on 2012-09-07
@durden, if you're talking to me, I didn't say anything about Turing completeness. I was talking about language features and noted that it's a fallacy to say that HLLs aren't used for low-level work because they don't provide direct memory mapping. Instead, HLLs don't provide memory mapping because they aren't used for low-level work. I could write a library that allows access to memory in the same way your C program does; it would be pretty simple, almost trivial. But I'd have kind of a hard time figuring out what to do with it that wouldn't be better done in C in the first place.

---

### Post by CptPicard on 2012-09-07
+1000 trent.josephsen, that is exactly the core point that we have been making for years here in the high vs. low-level languages discussion. It does not matter whether a language so-called actually does memory mapping down to some relatively arbitrary "closer to hardware level"; semantically speaking, the HLLs still do things that are conceptually exactly equivalent to what memory mapping is. And that is what is sufficient for the purposes of the discussion.

---

