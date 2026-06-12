---
title: "Languages in DEV"
date: 2008-11-18
forum: Programming Talk
---

### Post by slavik on 2008-11-18
So, let's attempt at talking about new language versions that are in development now and what significant changes they bring.

I am aware of the following:
Perl5 -> Perl6
Python 2.6 -> Python 3.0
Java6 -> Java7
C++ -> C++x0 (or w/e it is)

Here's what I know about them:
Perl6 has redone regex. regex is now a type like int or float. the whole regex engine is based around grammars. grammars are like classes (inheritance). they also look like the Backus Naur Form but with a lot of stuff (like asserting matches, like if a 5 digits are in some range or running subroutines based when something matches).

Python 3.0: range() is killed and xrange() is renamed into range(). in 2.5 (maybe 2.6 followed 3.0) range() generates a list, whereas xrange() generates one element at each iteration

Java7 will have measurements as types and seamless conversion between them (NASA lost a probe because two companies working on the same project used different measurement systems). so you will be able to say something like measure = 7 meters; and then print it in feet or w/e without having to do conversions (same with temps). this invalidates like 25% of beginning programming assignments. ;)

C++x0 Boost is now std. that means regex, threads, all the pointers and such. not exactly sure if it's all of boost or a subset.

Feel free to add more, code samples welcome (and encouraged!!!)

---

### Post by Cracauer on 2008-11-19
Some of the C++0x stuff looks really useful, although much of it is available in Boost right now.  I still want actual closures that capture static scope and I don't know why these people don't get that if you don't like runtime keyword arguments you can still have compile time arguments. Anyway, I'm exited about that one. In a puzzle kind of way.

Python, my heart is getting into cramps on the pure mention of any Python upgrade. I don't even care what they change, all I know is that it will be painful. Still no OS threads. More cramps.

Perl6, I have a friend who was in the development process but gave up. I'm really not sure it's gonna happen. Parrot itself is also in question, IMHO, and I would be surprised if they go through with the original plan to support Ruby, which means continuations.  

Even if they do a perfect implementation, I think it is questionable whether perl6 can gain a foothold. Commercial users switched to Python, and more will switch to Python instead of making the changes for Perl6. I think the market potential isn't there.

Java, don't care.

A language you didn't mention is Ruby. The new Ruby will have native OS threads and general light upgrades not requiring you to rebuild all your stuff. An upgrade more to my liking.

---

### Post by pmasiar on 2008-11-19
> **Cracauer said:**
> Python, my heart is getting into cramps on the pure mention of any Python upgrade. I don't even care what they change, all I know is that it will be painful. 

not sure why, py2.6 will warn you about suspicious constructs, and py2to3 should upgrade most of the code ... and many of projects will stay anyway for years on 2.6, 2.7, 2.8, until someone else will fix all the upgrade glitches ;-)

> Still no OS threads. More cramps.

because different people want them to work differently for different tasks?

Perl6 has chance in 2003, but now is too little too late IMHO. Old hands will stay with old code running old version 5.005 and new kids learn way cooler Ruby or Python.

---

### Post by Cracauer on 2008-11-19
I understand why Python people think they can't and don't need to move to actual threads (as in using CPU time from multiple CPUs, as opposed to just using it for concurrent I/O like they do now). 

It's just that I disagree. A language that doesn't make use of multi-CPU systems in 2008 has some priorities screwed up.

And the upgrade mess. What happens with all the gazillion python modules you have installed? If everything is managed to use the right one of multiple installed version Python chains like FreeBSD's port system does, fine, but for my own stuff?

I think I'll continue to avoid Python for my own stuff specifically so that I can have the packaged-up Phython stuff do it's own thing without nuking my own code.

---

### Post by nvteighen on 2008-11-19
You forgot Clojure ([http://clojure.org](http://clojure.org)). This "Lisp on Java Virtual Machine" is an interesting project we should have keep an eye at. It's 1-year old and is getting a nice fashion.

It's still too young (specially in *ye ol' world of Lisp* :p), but it can get the best of Lisp together with the best of the JVM (cross-platform support, e.g.).

---

### Post by pmasiar on 2008-11-19
> **Cracauer said:**
> It's just that I disagree. A language that doesn't make use of multi-CPU systems in 2008 has some priorities screwed up.

And the upgrade mess. What happens with all the gazillion python modules you have installed?

Relax: 2.6 allows: [http://docs.python.org/whatsnew/2.6.html](http://docs.python.org/whatsnew/2.6.html) 
- per-user site-packages directory: do what you want or need
- multiprocessing: [http://docs.python.org/library/multiprocessing.html](http://docs.python.org/library/multiprocessing.html)

Now you need new better excuse to not use Python 8-)

SDTimes for nov/1 have article how upgrade is clean (not yet online tho)

---

### Post by jespdj on 2008-11-19
> **slavik said:**
> Java7 will have measurements as types and seamless conversion between them (NASA lost a probe because two companies working on the same project used different measurement systems). so you will be able to say something like measure = 7 meters; and then print it in feet or w/e without having to do conversions (same with temps). this invalidates like 25% of beginning programming assignments. ;)
It is not officially decided yet what will be in Java 7. What you mention here (measurements as types) sounds like a fringe thing that most likely is not going to make it into Java 7.

One of the biggest new features that is under discussion for a few years already is closures. There are a few different proposals for closures in Java, some more extensive than others. However, it's not even clear yet if closures are going to make it into Java 7.

Another thing that is probably going to be in Java 7 is a new date and time API, based on the well-known open source library Joda Time.

Another thing that's hot in Java-land is making the JVM more suited for other programming languages, in particular dynamic programming languages such as Ruby and Python.

If you want to know what's going on with the development of Java, have a look at the [Java Community Process](http://jcp.org) websites, where all the JSRs (Java Specification Requests) are being developed.

---

### Post by Cracauer on 2008-11-19
> **pmasiar said:**
> Relax: 2.6 allows: [http://docs.python.org/whatsnew/2.6.html](http://docs.python.org/whatsnew/2.6.html) 
- per-user site-packages directory: do what you want or need



That looks like it's gotta help.

> **pmasiar said:**
> 
- multiprocessing: [http://docs.python.org/library/multiprocessing.html](http://docs.python.org/library/multiprocessing.html)



No, as I said earlier, while Python does technically invoke OS threads it is only using them for I/O, not to gain CPU resources. If you blow CPU time in Python you can never use more than one processor at a time with their current threads. I don't think they plan to change that.

Perl doesn't do much better, but the new Ruby (in development) does.

> **jespdj said:**
> Another thing that's hot in Java-land is making the JVM more suited for other programming languages, in particular dynamic programming languages such as Ruby and Python.

They are going to give the JVM continuations? That would be a big deal but I don't think it's gonna happen. To my knowledge nobody ever figured out how to make a bytecode machine not suffer general performance problems when supporting continuations. The Parrot (Perl6) guys tried to do that, too, but that seems to have gone astray, too.

---

### Post by jespdj on 2008-11-19
> **Cracauer said:**
> They are going to give the JVM continuations? That would be a big deal but I don't think it's gonna happen. To my knowledge nobody ever figured out how to make a bytecode machine not suffer general performance problems when supporting continuations. The Parrot (Perl6) guys tried to do that, too, but that seems to have gone astray, too.
I don't know the details of what's happening in the JVM. One thing that I read about is the [invokedynamic](http://jcp.org/en/jsr/detail?id=292) bytecode (JSR 292) which is very useful for dynamic languages such as Ruby.

---

### Post by ZuLuuuuuu on 2008-11-19
A perl interest arised for me these days and because I'm a hobbyist coder and don't need a stable implementation, I'm following the Perl 6 development. Interesting thing is, the development process seems to be very active; Perl 6 irc channel has hundreds of online users (it usually has more active conversations then Ruby or Python channel) They constantly release new versions of Parrot and Rakudo, do weekly meetings on phone etc... Also Parrot roadmap is giving specific dates: [https://trac.parrot.org/parrot/wiki/ParrotRoadmap](https://trac.parrot.org/parrot/wiki/ParrotRoadmap) . I don't know, though, if they can achieve that dates.

---

### Post by slavik on 2008-11-19
this was intended to discuss language X 1.0 vs language X 2.0, not language X 2.0 vs. language Y 2.0 ... and also for more info on language features in 2.0 ...

---

### Post by Cracauer on 2008-11-19
> **ZuLuuuuuu said:**
> A perl interest arised for me these days and because I'm a hobbyist coder and don't need a stable implementation, I'm following the Perl 6 development. Interesting thing is, the development process seems to be very active; Perl 6 irc channel has hundreds of online users (it usually has more active conversations then Ruby or Python channel) They constantly release new versions of Parrot and Rakudo, do weekly meetings on phone etc... Also Parrot roadmap is giving specific dates: [https://trac.parrot.org/parrot/wiki/ParrotRoadmap](https://trac.parrot.org/parrot/wiki/ParrotRoadmap) . I don't know, though, if they can achieve that dates.

It is my understanding that Parrot development is actually making better progress than Perl6. I cannot find any references to continuations in that Wiki, though.

---

### Post by wmcbrine on 2008-11-20
> **slavik said:**
> Python 3.0: range() is killed and xrange() is renamed into range(). in 2.5 (maybe 2.6 followed 3.0) range() generates a list, whereas xrange() generates one element at each iterationThat's the least of the incompatible changes. The biggest one is that all strings are becoming Unicode, and you use a new type, "bytes", for 8-bit strings. I think it's the right thing to do, but it's a headache when porting code forward, and in many cases it means there's no way for code to remain compatible with both 2.x and 3.x. The 2to3 conversion tool doesn't even handle all the changes this entails.

Another favorite is that print becomes a function. But that's really pretty minor, since in many cases you can make the changes in a backwards-compatible way (just add parentheses). Similarly, you can just replace xrange with range and be backwards-compatible.

There's also a normalization of the standard library's module names (partly to follow PEP 8 ), so e.g. Tkinter becomes tkinter, BaseHTTPServer becomes http.server, etc. I assume there's a list of these mappings somewhere, but I haven't seen it yet.

---

### Post by Nemooo on 2008-11-20
I had high hopes for [Arc]("http://arclanguage.org/"), but its development is very slow. There is a community based distribution, though. But I think if Arc is going to succeed we need to see some action from PG.

It's a shame the development is so slow, because I really enjoyed using it. The syntax was incredibly simple and (almost) beautiful. Generally I liked the simplistic approach, which seems to be the goal. For now I've lost hope in it, but am hoping to pick it up again further down the road.

---

### Post by Cracauer on 2008-11-20
> **Nemooo said:**
> I had high hopes for [Arc]("http://arclanguage.org/"), but its development is very slow. There is a community based distribution, though. But I think if Arc is going to succeed we need to see some action from PG.

It's a shame the development is so slow, because I really enjoyed using it. The syntax was incredibly simple and (almost) beautiful. Generally I liked the simplistic approach, which seems to be the goal. For now I've lost hope in it, but am hoping to pick it up again further down the road.

I don't see it having any backing in the Lisp community. The Common Lisp crowd doesn't like it because it makes the syntax less compile-time computing friendly and of course it doesn't load any existing libraries or works with any IDEs. For the Scheme folks it isn't pure enough.

Even if you can iron out the language I don't see a good compiler for it coming out of nowhere.

---

### Post by slavik on 2008-11-20
> **Nemooo said:**
> I had high hopes for [Arc]("http://arclanguage.org/"), but its development is very slow. There is a community based distribution, though. But I think if Arc is going to succeed we need to see some action from PG.

It's a shame the development is so slow, because I really enjoyed using it. The syntax was incredibly simple and (almost) beautiful. Generally I liked the simplistic approach, which seems to be the goal. For now I've lost hope in it, but am hoping to pick it up again further down the road.
What are some features that make Arc stand out among the rest? Can you show us some neat sample code?

---

### Post by slavik on 2008-11-20
Below is a sample of Perl6 grammar in action. I am still tweaking it. The sad part is that assertions haven't been implemented yet so you can assert a match if it's made.
Example: (\d ** 1..3) <?{ 0 <= $0 <=255 }>
Translation: (match 1 to 3 digits) <is the matched number between 0 and 255?>

The actual assertion is ?{ }, but < > contains code, so you can have something like:
( (\w+?) '=' (\w+?) ';' ) < %symbol_table<$/[0][0]> = $/[0][1]; >

If the above is troubling you, it will match a C-like assignment statement and actually save the value of the variable in a hash.

grammars also make it easy to define your own language (it looks very similar to BNF) which is useful for a code editor ;) (did you invent a new language? create a grammar for it, define colors for various tokens and you're done.)

[PHP]slavik@slavik-desktop:~/code/perl6$ perl6 -v ; cat grammar.p6 ; perl6 grammar.p6 
This is Rakudo Perl 6, revision 32858 built on parrot 0.8.1-devel
for x86_64-linux-gnu-thread-multi.

Copyright 2006-2008, The Perl Foundation.

my $str = 'http://127.0.0.1:80/mod_rewrite/dir/date/etc/view.php?blah=glah&p00p=d00p&login=false&some=other';

grammar URL {
	rule TOP { <schema> '://' <server> [ ':' <port>]? <resource>? }
	token schema { \w+ }
	token server { <hostname> | <ip> }
	token port { \d ** 1..5 }
	token resource { '/' [ .* ]? }
	
	token ip { [<byte> \.] ** 3 <byte> }
	token hostname { \w+ [ '.' \w+ ]* }
	token byte { (\d ** 1..3) }
};

if ($str ~~ URL) {
	say "String: \t" ~ $str;
	say "Full match: \t" ~ $/;
	say "Schema: \t" ~ $/<schema>;
	say "Server: \t" ~ $/<server>;
	say "Port: \t\t" ~ $/<port>[0] if "" ne $/<port>[0];
	say "Resource: \t" ~ $/<resource>[0] if "" ne $/<resource>[0];
	my @list = split /\?/, ~$/<resource>[0];
	my $file = @list[0];
	my $get = @list[1];
	say "File: \t\t" ~ $file;
	say "GET: \t\t" ~ $get;
	my @pairs = split /\&/, $get;
	for @pairs -> $pair {
		for split /\=/, $pair -> $key, $value { 
			say "\t\t"~ $key ~ "\t=>\t" ~ $value;
		}
	}
}

String: 	http://127.0.0.1:80/mod_rewrite/dir/date/etc/view.php?blah=glah&p00p=d00p&login=false&some=other
Full match: 	http://127.0.0.1:80/mod_rewrite/dir/date/etc/view.php?blah=glah&p00p=d00p&login=false&some=other
Schema: 	http
Server: 	127.0.0.1
Port: 		80
Resource: 	/mod_rewrite/dir/date/etc/view.php?blah=glah&p00p=d00p&login=false&some=other
File: 		/mod_rewrite/dir/date/etc/view.php
GET: 		blah=glah&p00p=d00p&login=false&some=other
		blah	=>	glah
		p00p	=>	d00p
		login	=>	false
		some	=>	other
[/PHP]

---

### Post by giannisfs on 2008-11-20
If Java was an important language it would somehow support pointers.
But not only it does not allow direct acces in memory but it is slow and perhaps too slow.
I don't care that "plays" everywhere!! I am seek of it. actionscript also plays in mobile phones with flash lite. Does this makes actionscript something serious or just something PORTABLE?
Because portability is not equals usability at least not yet Java
is also a waste od cpu and as a result it is not ecology friendly.
It consumes a lot more resources in a computer rather than almost any other language.
Java was and is still the key that makes Big known companies to survive.
And I mean why there are not many computers unix-like out there?
Because some "duded" don't like open-source and ... you guess the rest...
**In conclusion Java exits because opensource is not yet the rule.**
If you don't understand this you will start working with the mono develop 
and projects like that(I don't blame them besides i admire the developers) .Linux-unix has a grate history of c,c++ languages
C is the only true high level language.
Sorry if i sounded little angry but when i see something about Java i always want to say my point of view (to tell the trouth)

---

### Post by jespdj on 2008-11-21
> **giannisfs said:**
> If Java was an important language it would somehow support pointers.
But not only it does not allow direct acces in memory but it is slow and perhaps too slow.
Double BS. It is absolutely nonsense that a language should support pointers to be "important". C#, Python, Ruby and many other programming languages do not support direct memory access, just like Java, and they are all very important programming language in industry.

Java is also not slow anymore. It was seven years ago, but currently the JVM has a very sophisticated and efficient JIT (just-in-time) compiler that converts your Java bytecode to native code on the fly, which makes Java programs run quite fast. (Don't use GNU Java, it's still slow).
> **giannisfs said:**
> **In conclusion Java exits because opensource is not yet the rule.**
I don't know what you mean by this, but Java *is* open source.
> **giannisfs said:**
> Sorry if i sounded little angry but when i see something about Java i always want to say my point of view (to tell the trouth)
Too bad your point of view is not based on the truth.

---

### Post by nvteighen on 2008-11-21
> **giannisfs said:**
> 
C is the only true high level language.


Of course, C is a high abstraction level language... compared  with respect to ASM.

---

### Post by directhex on 2008-11-21
> **nvteighen said:**
> Of course, C is a high abstraction level language... compared  with respect to ASM.

ASM is a high abstraction level language... compared with respect to machine code

10001010111010101110110101010101110101
10101111101101000010101111110010101010

---

### Post by mssever on 2008-11-21
> **giannisfs said:**
> If Java was an important language it would somehow support pointers.
Pointers are merely indices to an array. They treat memory as such. Of course, Java and other languages have arrays that you access by index. How's that different? Oh, yeah, because pointers give you direct access to memory, they allow you many opportunities to create memory leaks, overflows, etc.

For most tasks, directly accessing memory provides no advantage.

---

### Post by Sinkingships7 on 2008-11-21
> **giannisfs said:**
> If Java was an important language it would somehow support pointers.
But not only it does not allow direct acces in memory but it is slow and perhaps too slow.
I don't care that "plays" everywhere!! I am seek of it. actionscript also plays in mobile phones with flash lite. Does this makes actionscript something serious or just something PORTABLE?
Because portability is not equals usability at least not yet Java
is also a waste od cpu and as a result it is not ecology friendly.
It consumes a lot more resources in a computer rather than almost any other language.
Java was and is still the key that makes Big known companies to survive.
And I mean why there are not many computers unix-like out there?
Because some "duded" don't like open-source and ... you guess the rest...
**In conclusion Java exits because opensource is not yet the rule.**
If you don't understand this you will start working with the mono develop 
and projects like that(I don't blame them besides i admire the developers) .Linux-unix has a grate history of c,c++ languages
C is the only true high level language.
Sorry if i sounded little angry but when i see something about Java i always want to say my point of view (to tell the trouth)

It's times like these when I wish this forum had a "No Thanks" medal to click on... :roll:

---

### Post by slavik on 2008-11-22
Thread closed, it was going to turn into a flamewar.

---

