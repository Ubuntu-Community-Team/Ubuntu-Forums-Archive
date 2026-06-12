---
title: "Good Cross Platform Language?"
date: 2010-09-01
forum: Programming Talk
---

### Post by asddf on 2010-09-01
I was wondering what language would suit?

Fully cross platform.
High Level.
OOP.
Good, large standard library?

---

### Post by dv3500ea on 2010-09-01
I would recommend [ruby]("http://www.ruby-lang.org/en/").

Others will recommend [python]("http://www.python.org/") or [perl]("http://www.perl.org/").
They are all good languages that are high level, interpreted and cross platform.

Ruby is the most OO though; everything in ruby is an object (even a class).

---

### Post by endotherm on 2010-09-01
in the long run, there isn;t one, at least not one that runs locally. 
java was designed to be "write once, run everywhere", but it really turned out to be "run once, debug everywhere". Java is probably your best bet, but i haven't tried ruby as the lst poster suggested. python runtime configuration is a PITA in windows.

---

### Post by worksofcraft on 2010-09-01
C++

---

### Post by worseisworser on 2010-09-01
Split things in two then you do not have to compromise when dealing with the tricky (non-client) parts at all:

[LIST]
[*]Client-side: the W3C platform; some compromises; portable.
[*]Server-side: anything you want; no compromises; doesn't have to be portable.
[/LIST]

..and W3C as a client-side UI platform(#1) has less and less compromises; check out Chrome; it's plenty fast and as an implementation it is portable in turn.

Perhaps a silly example, but I think this shows how fast some of the stuff on the W3C platform is now:
  [http://mrdoob.com/projects/chromeexperiments/ball_pool/](http://mrdoob.com/projects/chromeexperiments/ball_pool/)


[INDENT]#1: I say "UI platform" because I like to handle all model or business logic type stuff on the server-side where I am in more control, even though this is not an explicit requirement; JavaScript can handle some or perhaps even most of these tasks if you'd prefer that.[/INDENT]

---

### Post by lukeiamyourfather on 2010-09-01
> **asddf said:**
> I was wondering what language would suit?

Fully cross platform.
High Level.
OOP.
Good, large standard library?

That's a pretty subjective question that will return some pretty subjective answers. I'd say Python because it fits your criteria and I like Python. :)

---

### Post by juancarlospaco on 2010-09-01
You are describing Python. :)

---

### Post by dv3500ea on 2010-09-01
I wouldn't consider C++ or Java to be high level. I would say Java is sort of medium level but C++ is definitely low level (not as low as C or Assembly though).

Also, C++ has a rather limited standard library compared to ruby, python, perl or java.

Python is good though and is very popular. An advantage of python over ruby is many more open source programs are written in it, meaning it could be easier to contribute.

Personally I find python a bit counter intuitive and the OO (as with perl) seems a bit bolted on.

Ruby feels very natural to me meaning I don't have to look up documentation as much but this is different for each person.

If you have the time and patience, try all of these languages to see which you prefer. This will also enable you to think about problems in different ways.

---

### Post by DangerOnTheRanger on 2010-09-01
Python all the way!

I can personally profess the power of Python, as I've made/trying to finish(:D) a complete networked game development framework with it. 

How's that for size and complexity?

---

### Post by KdotJ on 2010-09-01
*wades his way through the python lovers..*

Java.
It's platform independent and has its own GUI toolkit

---

### Post by worksofcraft on 2010-09-01
> **dv3500ea said:**
> I wouldn't consider C++ or Java to be high level. I would say Java is sort of medium level but C++ is definitely low level (not as low as C or Assembly though).


IMO this is a common misconception. In reality C and C++ provide practically ALL the libraries that the other languages piggy-back off.

Reason for above incorrect perception is because C++ **allows** you to access very low level facilities, but it also offers very high level things e.g. in the form of Standard Template Library.

Now tell me, can Ruby, Perl or Python provide support for templates like that? Will they let you do your own memory management to suit your application? Can Java pass parameters by value... and so on...

Just because it allows you to do things at a low level doesn't mean it isn't a high level language.

15 years ago I wrote some high level stuff that ran under Windows and compiled with Borland, Symantec or Watcom C++... recently I ported it to Linux... all I had to change were some include statements because the libraries had been rearranged over the years.

You can look at the code and decide for yourself if it was low or high level [http://ubuntuforums.org/showthread.php?t=1563342](http://ubuntuforums.org/showthread.php?t=1563342)

I would actually really appreciate if someone can explain how *their* choice language would be *more* high level in implementing either of those two application that my chapters conclude with ):P

---

### Post by schauerlich on 2010-09-02
This discussion again...

I'll save everyone the trouble: "Low level" is everything below my preferred level of abstraction. "High level" is my preferred level of abstraction (unless I like bit-twiddling C or assembly, in which case low level is the One True Way). Anything above my preferred level of abstraction is just weird and useless.

/thread

---

### Post by shadylookin on 2010-09-02
> **dv3500ea said:**
> I wouldn't consider C++ or Java to be high level. I would say Java is sort of medium level but C++ is definitely low level (not as low as C or Assembly though).

Also, C++ has a rather limited standard library compared to ruby, python, perl or java.

Python is good though and is very popular. An advantage of python over ruby is many more open source programs are written in it, meaning it could be easier to contribute.

Personally I find python a bit counter intuitive and the OO (as with perl) seems a bit bolted on.

Ruby feels very natural to me meaning I don't have to look up documentation as much but this is different for each person.

If you have the time and patience, try all of these languages to see which you prefer. This will also enable you to think about problems in different ways.

What makes you believe that java is less of a high level language than python? I mean java forces object oriented programming, whereas python you can write everything procedurally.

---

### Post by kahumba on 2010-09-02
Go for assembly, it's the best high-level, cross-platform, OOP language in the world!

---

### Post by worksofcraft on 2010-09-02
> **kahumba said:**
> Go for assembly, it's the best high-level, cross-platform, OOP language in the world!

Lol - wut?

Prolog is the best... and assembly... WELL YES... you CAN code it ALL by hand!

---

### Post by Tracy177 on 2010-09-02
> **asddf said:**
> I was wondering what language would suit?

Fully cross platform.
High Level.
OOP.
Good, large standard library?


English ?

---

### Post by kahumba on 2010-09-02
> **worksofcraft said:**
> Lol - wut?
Prolog is the best... and assembly... WELL YES... you CAN code it ALL by hand!
> 
**Assembly language** is an esoteric high level computer programming language which can directly access the computer hardware, for example, the [Microsoft]("http://uncyclopedia.wikia.com/wiki/Microsoft") Excel On Board DRM .  Some programmers swear by it, others swear at it. 
According to elite programmers such as [Bill Gates]("http://uncyclopedia.wikia.com/wiki/Bill_Gates"), [Linus Torvalds]("http://uncyclopedia.wikia.com/wiki/Linus_Torvalds"), and [Samuel L Jackson]("http://uncyclopedia.wikia.com/wiki/Samuel_L_Jackson"), There are several reasons to use assembly:  
1. Being l33t, and avoiding bugs, or mistakes in the code. 2. Fixing uncontrollable diarrhea. 3. The ability to access constucts such as for, and while. 4. Ease of use when accessing complex data structures. 5. Ensuring maximum portability of code. 
[http://uncyclopedia.wikia.com/wiki/Assembly](http://uncyclopedia.wikia.com/wiki/Assembly)

---

### Post by Shippou on 2010-09-02
> **Tracy177 said:**
> English ?

:lolflag:

Even English is not cross-platform. There are dialects. And by population alone, Chinese would be the number one cross-platform language.

Anyway, back to topic.

I do believe there is no such thing as "completely portable". Heck, even in Java you have to sometimes consider portability issues, especially if your application uses special libraries. The Java Media Framework easily comes to mind.

Anyway, I think it all boils down to machine support: if there are compilers that are built for a specific machine, and other things. BTW, in the end, all high-level languages are translated into assembly or machine code, which is, by nature, NOT portable.

As said by the other posters, this is a very subjective topic that will bring subjective answers. An evidence alone is the proliferation of Python vs Java vs C++ cs [your language here] ... posts. 

I do also think that it all boils down to what platform you plan to support, because I believe that a very portable language is somewhat useless if you only plan to support, say, Linux. Anyway, I think you get my point.

But if you insist, you can try these languagesL
1. Java
2. Ruby
3. PHP
4. C
5. Fortran

I gave those languages, because, guess what: I know them.

Anyway, what's important in the end is that YOU KNOW HOW TO CODE, not you know how to code in [insert language here].

Sorry for the long post.

P.S.&#65306; I do believe any language can be portable, as long as you do not use features specific to a platform.

---

### Post by Some Penguin on 2010-09-02
> **Shippou said:**
> 
P.S.&#65306; I do believe any language can be portable, as long as you do not use features specific to a platform.

This is practically impossible with certain languages.  C, for instance, is highly platform-sensitive even with respect to the number and ordering of the bytes in primitive types.  Structure layout is influenced by architecture as well.  Even basic 'char' types are not of guaranteed size.

It's easier in languages like Java, but it's still quite possible to see platform-specific behavior.

---

### Post by ccc123 on 2010-09-02
I mean java forces object oriented programming, whereas python you can write everything procedurally.hahahaha

---

### Post by ssam on 2010-09-02
> **Some Penguin said:**
> This is practically impossible with certain languages.  C, for instance, is highly platform-sensitive even with respect to the number and ordering of the bytes in primitive types.  Structure layout is influenced by architecture as well.  Even basic 'char' types are not of guaranteed size.

in most cases the same C source code will work the same on any platform.

when you do
```

char a[10];
a[5] = 'a';

```
you dont have to care how big a char is. the compiler just makes it work.

if you are communicating with binary data between 2 different CPU architectures it may get more complex. but often you can just use ascii instead.

where you do need to watch out is things like path handling (useful to have a [library]("http://docs.python.org/library/os.path.html") that can do this) and GUI (if you need it).

and i propose
flicking switches - very low level
assembly -low level
fortran - medium level
c - high level
c++ - very high level
java - super high level
python - uber high level

---

### Post by dv3500ea on 2010-09-02
> **worksofcraft said:**
> IMO this is a common misconception. In reality C and C++ provide practically ALL the libraries that the other languages piggy-back off.

Reason for above incorrect perception is because C++ **allows** you to access very low level facilities, but it also offers very high level things e.g. in the form of Standard Template Library.

Now tell me, can Ruby, Perl or Python provide support for templates like that? Will they let you do your own memory management to suit your application? Can Java pass parameters by value... and so on...

Just because it allows you to do things at a low level doesn't mean it isn't a high level language.

15 years ago I wrote some high level stuff that ran under Windows and compiled with Borland, Symantec or Watcom C++... recently I ported it to Linux... all I had to change were some include statements because the libraries had been rearranged over the years.

You can look at the code and decide for yourself if it was low or high level [http://ubuntuforums.org/showthread.php?t=1563342](http://ubuntuforums.org/showthread.php?t=1563342)

I would actually really appreciate if someone can explain how *their* choice language would be *more* high level in implementing either of those two application that my chapters conclude with ):P

It seems to me that the C++ standard library provides features that are generally built in to the higher level languages (not as part of a library). The data structures, for example, are implemented as the inbuilt types hash/dict and array/list in ruby, perl and python.

Compare the [C++ standard library]("http://ruby-doc.org/stdlib/") to the [ruby standard library]("http://ruby-doc.org/stdlib/"). The ruby standard library is much bigger with more features.

I consider C++ and Java to be low level because you must declare the type of a variable or function. C is low level because you have to manage your own memory (I'm not sure whether you do or not in C++). In dynamic languages you don't have to worry about any of this. C/C++ are good if you need to manage your own memory or access lower level features (or if you just need a bit more speed) but I think ruby/perl/python are better for implementing your program logic. Handily, all of these languages have an interface to C so that libraries can be implemented in C with a higher level interface in ruby/perl/python.

Your C++ lottery program would look something like this in ruby:
```

balls = ([color=orange]1[/color]..[color=orange]48[/color]).[color=purple]to_a[/color]
[color=blue]puts[/color] [color=orange]"Press enter to make the draw"[/color]
t = [color=green]Thread[/color].[color=purple]start[/color] [color=red]do[/color]
    balls.[color=purple]sort![/color] { ([color=blue]rand[/color]*[color=orange]2[/color]-[color=orange]1[/color]).[color=purple]round[/color] }
    [color=blue]sleep[/color] [color=orange]0.1[/color]
[color=red]end[/color]
[color=blue]gets[/color]
[color=green]Thread[/color].[color=purple]kill[/color] t
[color=blue]puts[/color] balls[[color=orange]0[/color]..[color=orange]5[/color]].[color=purple]sort[/color].[color=purple]join[/color]("\t")

```
This, to me, is higher level and simpler. Note none of the standard library is [color=red]require[/color]d for this; it is just using inbuilt constructs.

---

### Post by Shippou on 2010-09-02
> **ccc123 said:**
> I mean java forces object oriented programming, whereas python you can write everything procedurally.hahahaha

:lolflag:

Procedural programming is also possible in Java: don't include methods, define all in main, and don't use other classes than the one where the main is. :P

---

### Post by endotherm on 2010-09-02
a lot of my concern is client dependency deployment and configuration. java is my recomendation because the jre is easy to install, auto-updating, and the ui toolkit is built in, unless you're an swt guy. the last java applet i wrote seriously was cross platform, though some of the calculations I was using to determine the size of graphical objects within the form returned differently between winXP, winVista, and Ubuntu, so I could never really get it to look right on all apps. 

I love python, but I only tend to use it on *nix systems, because the windows deployment is a right pain. and then you have to lay a ui framework on it. just seems like dependency hell all over again.

---

### Post by KdotJ on 2010-09-02
Plus, the look and feel of java's swing can be changed to match the system. I have a program I wrote when run under Linux, the look and feel is gtk, and honestly it's pretty much bang on. Run that same program in windows, and it looks like winforms.

---

### Post by Simian Man on 2010-09-02
> **worksofcraft said:**
> IMO this is a common misconception. In reality C and C++ provide practically ALL the libraries that the other languages piggy-back off.

Just because it allows you to do things at a low level doesn't mean it isn't a high level language.
Yes it does.  In C++ you can try to ignore the fact that it is a low-level language by using the STL, RAII, templates and so on, but the low-level stuff will *always* bite you in the *** at some point, given a large enough project.  I use C++ extensively and have taught it at the university level, and it's a good language, but it is *not* high-level.  High-level languages shield you much more effectively from the minutia of memory allocation, are more portable because you don't have to worry about the details of the machine (ie how big an integer is), and give you large standard libraries.  C++'s standard libraries bandages up some of the most glaring defects of the language, but it is nothing to the standard libraries of Python or Java.

> **shadylookin said:**
> What makes you believe that java is less of a high level language than python? I mean java forces object oriented programming, whereas python you can write everything procedurally.
High-level does not mean "forces you to use objects".  Many extremely high-level languages such as Scheme and Prolog have no concept of objects at all.

I think Python is really the best choice because it is high-level, has a great standard library, is very portable, and can be used for a wide variety of programming styles.

---

### Post by nvteighen on 2010-09-02
> **Simian Man said:**
> Yes it does.  In C++ you can try to ignore the fact that it is a low-level language by using the STL, RAII, templates and so on, but the low-level stuff will *always* bite you in the *** at some point, given a large enough project.  I use C++ extensively and have taught it at the university level, and it's a good language, but it is *not* high-level.  High-level languages shield you much more effectively from the minutia of memory allocation, are more portable because you don't have to worry about the details of the machine (ie how big an integer is), and give you large standard libraries.  C++'s standard libraries bandages up some of the most glaring defects of the language, but it is nothing to the standard libraries of Python or Java.


+1

That's because no matter what you do, C++ doesn't have a metalinguistic device that can turn your language into another. In the end, it's all still C++... and therefore, everything still applies.

Actually, the only two languages I know of that can be turned into different ones by themselves are Lisp and Forth (because of Lisp's influence).

---

### Post by schauerlich on 2010-09-02
> **Simian Man said:**
> High-level does not mean "forces you to use objects".  Many extremely high-level languages such as Scheme and Prolog have no concept of objects at all.

Objects are just a poor man's closure. :)

---

### Post by juancarlospaco on 2010-09-02
*Yep, Oracle&#8482; Java&#8482; is good to make Oracle&#8482; Java&#8482; apps, ask to Google*

---

### Post by worksofcraft on 2010-09-02
> **dv3500ea said:**
> It seems to me that the C++ standard library provides features that are generally built in to the higher level languages (not as part of a library). The data structures, for example, are implemented as the inbuilt types hash/dict and array/list in ruby, perl and python.

Yes, thank you for that illustration of the lottery program in Ruby :)

OK so what what you are saying is that C++ uses libraries like STL to implement things that are an integral part of Ruby. I don't know if that makes Ruby language "higher" level though. It merely limits your options to those that were built in.

I don't know Ruby and only just learn Python. All this "the compiler handles the data types and memory for you" reasoning sounds good but recently I ran into something that put me right off Python...
> **worksofcraft said:**
> I tell Python interpreter that my ETC class derives from the dictionary class **dict** which is a built in type... and then I call the constructor of that dict base class. I never suspected it would be turning it into a string behind my back :shock:
 
You can read more about that here:
[http://ubuntuforums.org/showthread.php?t=1561024&page=3](http://ubuntuforums.org/showthread.php?t=1561024&page=3)

---

### Post by worksofcraft on 2010-09-02
> **Simian Man said:**
> ... but the low-level stuff will *always* bite you in the *** at some point, given a large enough project.  I use C++ extensively and have taught it at the university level, and it's a good language, but it is *not* high-level.  High-level languages shield you much more effectively from the minutia of memory allocation, are more portable because you don't have to worry about the details of the machine (ie how big an integer is), and give you large standard libraries.  C++'s standard libraries bandages up some of the most glaring defects of the language, but it is nothing to the standard libraries of Python or Java.


The philosophy of C++ is different. It provides less as a standard and more as flexibility, thus there are many 3rd part libraries and much more variety available... precisely why things like Python use C/C++ to implement their built in features.

Now most languages have limits on their size of integers. e.g. I think Java has 32 bit word size. Just because it doesn't offer a choice of shorts and longs, signed and unsigned... hardly makes it a better language. Access to low level is a privilege for people who know what they are doing and only a problem for those who abuse it.

Things like garbage collection certainly shield the novice programmer from understanding about scope of their variables, but could the garbage collector be implemented in their high level language? There is nothing to stop you from using a garbage collector with C++ IMO if you really feel you need one.

---

### Post by worseisworser on 2010-09-02
You guys keep talking about different things or past each other all the time. I'm sick as a dog at the moment, but I'm going to try to be very clear, direct and explicit about this so we can end or conclude this for good somehow.

Ruby is a higher-level language than C++ because its primary(#1) mode of operation is that of which is still further away from the machine or low-level issues(#2) than both ASM, C or C++ and in general closer to the problem domain, worksofcraft. Fact. End of story and that discussion.

The same applies to Python.

Also please try to think of these things not in relation to what you're doing with your own current code or projects; this is not interesting or relevant or related at all.

This stuff is so simple and so basic, and no one should have any personal or "religious" issues with these things *once they understand them*; it is just some of those things "everyone"(..sigh..) agrees on. Low-level and high-level *just is* -- there is _nothing_ interesting or magical about either thing. People who do not agree to this should have the decency to just go away or shut up and do something else (read a book; whatever), then come back when they no longer will confuse themselves and others about these things any more.

edit: ..this might sound harsh, but if you instead think of this as a room filled with people, perhaps a classroom or a family dinner or something like that. In particular, as the number of people in some context grows -- each person has got to be very careful about what his or her output is because the amount of noise and repetition of previous mistakes can become very confusing and downright annoying in the long run especially when you have people new to some subject absorbing the same wrong or confused ideas and thoughts over and over again. It is your duty to try to do the right thing, and when you cannot say "anything nice" (the right thing) -- just shut up and make a Note to Self about what to study next; or ask a question.

Now, what people do not agree on is what one should compromise on and when, and compromise is what one do all the time when programming regardless of the level of abstraction and other issues. This is why some people call programming an art; it involves taste and some sort of fuzzy subjective intuition type thing there. This is however *totally independent* of the *definition* of a high-level language as opposed to a low-level language.


[INDENT]
#1: ..and perhaps only; I honestly do not know if Ruby can do low-level  unsafe stuff when needed, but that is not the main point. The main point is that when you really are working in a true high-level context on some perhaps sub-task you really are 100% free from low-level issues at all times; this does not hold for e.g. C++. There is absolutely no way of escaping some of the low-level issues that exist in C++ *no matter how hard you try* and no matter what libraries you use. It can never be as high a level language as Ruby or Python or Lisp for this reason.

#2: You need to figure out what "low-level issues" means if you do not already know, and you need to understand that many of these issues can be removed by adding some missing language or run-time construct (not library) when you feel that this is appropriate or useful to do.
[/INDENT]

---

### Post by hakermania on 2010-09-02
java

---

### Post by GenBattle on 2010-09-02
> **worseisworser said:**
> You guys keep talking about different things or past each other all the time. I'm sick as a dog at the moment, but I'm going to try to be very clear, direct and explicit about this so we can end or conclude this for good somehow.

Ruby is a higher-level language than C++ because its primary(#1) mode of operation is that of which is still further away from the machine or low-level issues(#2) than both ASM, C or C++ and closer to the problem domain, worksofcraft. Fact. End of story and that discussion.

The same applies to Python.

Also please try to think of these things not in relation to what you're doing with your own current code or projects; this is not interesting or relevant or related at all.

This stuff is so simple and so basic, and no one should have any personal or "religious" issues with these things *once they understand them*; it is just some of those things "everyone"(..sigh..) agrees on. Low-level and high-level *just is* -- there is _nothing_ interesting or magical about either thing. People who do not agree to this should have the decency to just go away or shut up and do something else (read a book; whatever), then come back when they no longer will confuse themselves and others about these things any more.

edit: ..this might sound harsh, but if you instead think of this as a room filled with people, perhaps a classroom or a family dinner or something like that. In particular, as the number of people in some context grows -- each person has got to be very careful about what his or her output is because the amount of noise and repetition of previous mistakes can become very confusing and downright annoying in the long run especially when you have people new to some subject absorbing the same wrong or confused ideas and thoughts over and over again. It is your duty to try to do the right thing, and when you cannot say "anything nice" (the right thing) -- just shut up and make a Note to Self about what to study next; or ask a question.

Now, what people do not agree on is what one should compromise and when, and compromise is what one do all the time when programming regardless of the level of abstraction and other issues. This is why some people call programming an art; it involves taste and some sort of fuzzy subjective intuition type thing there. This is however *totally independent* of the *definition* of a high-level language as opposed to a low-level language.


[INDENT]
#1: ..and perhaps only; I honestly do not know if Ruby can do low-level  unsafe stuff when needed, but that is not the main point. The main point is that when you really are working in a true high-level context on some perhaps sub-task you really are 100% free from low-level issues at all times; this does not hold for e.g. C++. There is absolutely no way of escaping some of the low-level issues that exist in C++ *no matter how hard you try* and no matter what libraries you use. It can never be as high a level language as Ruby or Python or Lisp for this reason.

#2: You need to figure out what "low-level issues" means if you do not already know, and you need to understand that many of these issues can be removed by adding some missing language or run-time construct (not library) when you feel that this is appropriate or useful to do.
[/INDENT]

Agreed 100%

I also get sick and tired of C++ devotees professing that their language is, in fact, high level. 

It was developed a very long time ago as a "high-level" language, but the definition of high-level has shifted significantly in the last 20 years. Ask anyone and they will tell you any application will take far longer to code in C++ than Java/C#/Python/Ruby/etc. C++ has its roots in C, it is a low level language with higher level bits tacked on so you can use it as you would use a high level language. This does not make it a high level language.

No language is perfectly cross-platform. Java has a nice cross-platform GUI toolkit (it is also faster than Python or Ruby). I would still pick python, but that is my personal preference (for usability reasons, i like using it).

---

### Post by schauerlich on 2010-09-02
[I'm just going to leave this here.](http://ubuntuforums.org/showpost.php?p=9795676&postcount=12)

---

### Post by worksofcraft on 2010-09-02
> **GenBattle said:**
> 
I also get sick and tired of C++ devotees professing that their language is, in fact, high level. 


Roflmao :D  Reading this threads I got the impression there were an awful lot more Python devotees professing their creed than  "tiresome C++ zealots who should just go away".

Now I quite like Python but I think you need to keep things in perspective.

By your reasoning if we strip all the low level capabilities out of C++ and eliminate the programmers choice of libraries by building specific ones into the language then that *would* make it a higher level language?

... so like ditch all the integers and pointers and just have pass by reference and all numbers floating point and one flavor of string class and one list class and one map class... and perhaps  we should call it --C, in recognition that we've taken a lot out before we even started... oh oops my bad it's already been dubbed **Java** has it not? :popcorn:

---

### Post by worseisworser on 2010-09-02
> **schauerlich said:**
> [I'm just going to leave this here.](http://ubuntuforums.org/showpost.php?p=9795676&postcount=12)

This actually brings the discussion back to the start.

I.e., you are here talking about preferences and compromises in Actual Programming; not considering the definition of low-level vs. high-level *independent of this*.

---

### Post by worseisworser on 2010-09-02
> **worksofcraft said:**
> Roflmao :D  Reading this threads I got the impression there were an awful lot more Python devotees professing their creed than  "tiresome C++ zealots who should just go away".

Now I quite like Python but I think you need to keep things in perspective.

By your reasoning if we strip all the low level capabilities out of C++ and eliminate the programmers choice of libraries by building specific ones into the language then that *would* make it a higher level language?

... so like ditch all the integers and pointers and just have pass by reference and all numbers floating point and one flavor of string class and one list class and one map class... and perhaps  we should call it --C, in recognition that we've taken a lot out before we even started... oh oops my bad it's already been dubbed **Java** has it not? :popcorn:

This is just more noise ...

---

### Post by GenBattle on 2010-09-02
You can take away all of the low level programming language constructs of C++ but then it isn't C++, is it? If you can only justify your argument that it is a high level language by removing features and integral parts of the language, then surely the language (as it stands) is not high level? You're focusing too much on the language. Java is different from C++ not just because of language features. C++ code cannot be compiled to cross-platform bytecode as Java can.

And no one is eliminating choice. Languages like python and ruby have more built in, sure, but they haven't magically removed all traces of an "include" mechanic from the language. Importing an external library is just as easy in Python as it is in C++ (i would argue, easier), but in most cases you won't have to even go through that much trouble because, hey, what do you know, it's already built in.

C++ has its uses; it is very fast and very adaptable to just about any sort of project or scale. The problem is that, for the purposes of this thread, it is neither high-level nor cross-platform. GNU/Linux salts will often cry out "of course C++ is cross platform!", but you still have to compile a different binary for each platform/architecture combination you want to support. That is not cross-platform. With Java/Python you can ship source and run it directly (with minimal compilation done automatically on run), or precompile to an intermediate bytecode. Compiled binaries are not cross-platform.

That said, i think people place too much emphasis on languages being "cross-platform" (myth?). The use only cares about how hard it is to install and get running, which all comes down to packaging and distribution. In reality you should pick a language which has enough cross-platform features to make multi-platform support easy (C++ #ifdefs are great for this) and that suits your particular application and problem.

---

### Post by worksofcraft on 2010-09-02
> **GenBattle said:**
> Java is different from C++ not just because of language features. C++ code cannot be compiled to cross-platform bytecode as Java can.

Hum... well I got the impression that Java can only be compiled to run on a Java virtual machine... so isn't that more like a total of **one** target platforms?

However that said, yes, I am totally convinced by your statement that the user only cares about the logistics of installing and running the applications.

> **GenBattle said:**
> 
Importing an external library is just as easy in Python as it is in C++ (i would argue, easier)..


That is good :)
I'm hoping to import a totally awesome and revolutionary new library I'm developing into Python and as I'm still a total noob with the logistics of Pythonics I may be needing some knowledgeable input on that soon!

---

### Post by schauerlich on 2010-09-02
> **worseisworser said:**
> This actually brings the discussion back to the start.

I.e., you are here talking about preferences and compromises in Actual Programming; not considering the definition of low-level vs. high-level *independent of this*.

My point was that low vs high is largely a pointless distinction, no matter how interesting or useful the different features of various languages are. A rose by any other name...

---

### Post by fct on 2010-09-03
java.

---

### Post by CptPicard on 2010-09-03
> **worksofcraft said:**
>  precisely why things like Python use C/C++ to implement their built in features.

No, not really. And not everything in Python is "built in" in the language sense strictly speaking; the standard library just happens to be large. Of course though native code has benefits in execution speed and the code just happens to be available, so there's no reason not to write bindings for Python in that case. It's not really a language design issue per se.

> 
Now most languages have limits on their size of integers. e.g. I think Java has 32 bit word size. Just because it doesn't offer a choice of shorts and longs, signed and unsigned... hardly makes it a better language. Access to low level is a privilege for people who know what they are doing and only a problem for those who abuse it.

Thinking that trivialities like integer size and the low level details actually matter only for those who "know how to use them" is a pretty good tell in my books that the guy making those kinds of statements does not really think of programming much in the abstract -- like, abstract concepts put together to perform a certain function in a thoughtful, elegant way. Most of the low-level is drudgery that can be dealt with, but I have always had issues believing it is any kind of a decent measure of programmer maturity.

I would be prone to comparing low-level programming to a specialist field like J2EE programming. Both have their particular idioms and tricks, but there we're talking "expertise" in a particular field, not general programming competence. That kind of insight only comes from exposure to a lot of patterns of different kinds, algorithmics, so on...


> 
Things like garbage collection certainly shield the novice programmer from understanding about scope of their variables

The novice programmer will learn the concept of scope soon enough, and manual memory management is not a requirement for that. However, any programmer, particularly the novice one, will learn much more interesting programming ideas much faster without having to consider the pointer-tracking, the idea of which, again, is relatively trivial.

> 
 but could the garbage collector be implemented in their high level language?

Well, yes. I can write some kind of heap simulator in Java that implements a garbage collector. It's perfectly doable.

Likewise, I can quite easily write a simple CPU emulator in Python that picks instructions from a list and alters states accordingly. The idea is still there, although the language is Python.

> There is nothing to stop you from using a garbage collector with C++ IMO if you really feel you need one.

But there is nothing in the world that will allow you to use closures in C++ no matter how hard you wanted to, short of implementing a garbage collector and a language interpreter that actually runs some different language than C++.

---

### Post by qalimas on 2010-09-03
I know a little C, a little Java, some Python, some C#, but my main focus is on Ruby (mostly on Rails).

Just because I didn't see anyone else mention it, there is another choice.  I'm not suggesting it is the best or is what you are looking for, but all anyone can do is give you the options, you have to pick.  Thus, it is fair you have them all :P

I've started learning "C#" again using Mono.  With Mono, you have the choice of C# or VB (both .NET).  It uses GTK# as the GUI.  It will compile into executables for the big three.  It, like Java and the real .NET) requires the Mono runtime installed on the user's machine.  It's not a huge download, so it isn't much of an issue.


I hope you find what language suites you best :D


PS: My vote is to give Ruby a go.

---

### Post by worksofcraft on 2010-09-04
> **CptPicard said:**
> 
Thinking that trivialities like integer size and the low level details actually matter only for those who "know how to use them" is a pretty good tell in my books that the guy making those kinds of statements does not really think of programming much in the abstract -- like, abstract concepts put together to perform a certain function in a thoughtful, elegant way. Most of the low-level is drudgery that can be dealt with, but I have always had issues believing it is any kind of a decent measure of programmer maturity.


Well you may not have noticed, but the person that I was responding to said "...shield you much more effectively from the minutia of memory allocation, are more portable because you don't have to worry about the details of the machine (ie how big an integer is)..." and says he **teaches extensively at university level**.

Personally I have never have problems with the number of bits in my integers. I study my problem domain and choose appropriate sized entities to represent them. I don't have to. I could use double precison floating point for them all. Problem solved?

Oh... mysteriously loops won't terminate because they check for floating point equality... on Python's "shielded from trivial minutiae" universal number system :shock:
... z0mg surely I shouldn't have to consider low level implementation details in such a "high level" language... or should I?

---

### Post by worseisworser on 2010-09-04
You're not really responding to what CptPicard is saying, worksofcraft.

While I'm not sure what Python does, a HLL could switch from integers to bignums on overflow instead of rolling around:

```

CL-USER> (typep  most-positive-fixnum 'fixnum)
T
CL-USER> (typep (+ most-positive-fixnum 1) 'fixnum)
NIL
CL-USER> 

```

(.. *fixnum* is the "same as" *int* in C/C++ ..)

What you say about floating point is just embarrassing and silly; I have no comment, though, a way of dealing with this sort of thing(#1) might be to use ratios instead of floats -- then coerce to float on output to user; or as late as possible. I guess you knew that already ...


[INDENT]#1: ... ignoring for a moment the obvious *user* mistake of using an equality test in the termination clause of a *for* loop given the likely context ...[/INDENT]

---

### Post by worseisworser on 2010-09-04
> **schauerlich said:**
> My point was that low vs high is largely a pointless distinction, no matter how interesting or useful the different features of various languages are. A rose by any other name...

I'm not sure I understand your point or whether I agree with this.

As you move further and further away from the machine you need an increasingly better compiler. I'm not sure there is a "point" to knowing this; it just is.

---

### Post by worksofcraft on 2010-09-04
> **worseisworser said:**
> You're not really responding to what CptPicard is saying, worksofcraft.


He was quoting from what I wrote, but what he then responded seemed to have little to do with what I was discussing.

> **worseisworser said:**
> 
While I'm not sure what Python does, a HLL could switch from integers to bignums on overflow instead of rolling around:


Should it? I don't think Java does. IMO programmers should learn to think about normalizing the quantities in their problem domain and to avoid ill-conditioning of their solutions.

They should also think about how data propagates through their system where it comes from where it gets used and it's authenticity accuracy and reliability... all strongly linked with understanding their memory management strategy.

Anyway I don't really care as I think this has gone way off topic.

---

### Post by worseisworser on 2010-09-04
> **worksofcraft said:**
> Should it?

Ok, see? You are thinking compromises and actual programming as if this had anything to do with the definition of HLL's "vs." LLL's in isolation again.

..but see #1..


> **worksofcraft said:**
> IMO programmers should learn to think about normalizing the quantities in their problem domain and to avoid ill-conditioning of their solutions.

They should also think about how data propagates through their system where it comes from where it gets used and it's authenticity accuracy and reliability... all strongly linked with understanding their memory management strategy.


Yes, but why do you think this? Is it to avoid some set of resulting problems that cannot be dealt with in *any* other way, or is it for when you need to do manual optimization and/or tinker with compiler/run-time internals so that the same optimizations can, perhaps, be applied automatically?

Skip back a bit to what I said about C++ never being able to *escape* some of its "low-level things" by the way.



[INDENT]#1:
Note that some HLL's allow you to optimize *when* needed; e.g. you can state that some variable will always be a *fixnum*, or *int* -- and no run-time (compile-time is still done if a ftype decl. is around) automatic checking of overflow and conversion to bignum will be done.

```

CL-USER> (defun normal (x)
           (declare (fixnum x))
           (+ x 1))
NORMAL

CL-USER> (normal most-positive-fixnum)
1152921504606846976

CL-USER> (typep (normal most-positive-fixnum)
                'fixnum)
NIL


CL-USER> (defun fast-and-unsafe (x)
           (declare (fixnum x))
           (the fixnum (+ x 1)))
FAST-AND-UNSAFE

CL-USER> (fast-and-unsafe most-positive-fixnum)
-1152921504606846976

CL-USER> (typep (fast-and-unsafe most-positive-fixnum)
                'fixnum)
T


CL-USER> (disassemble 'normal)
; disassembly for NORMAL
; 0438D6D3:       488D4201         LEA RAX, [RDX+1]           ; no-arg-parsing entry point
;       D7:       486BD008         IMUL RDX, RAX, 8
;       DB:       710E             JNO L0
;       DD:       488BD0           MOV RDX, RAX
;       E0:       4C8D1C250C060020 LEA R11, [#x2000060C]      ; ALLOC-SIGNED-BIGNUM-IN-RDX
;       E8:       41FFD3           CALL R11
;       EB: L0:   488BE5           MOV RSP, RBP
;       EE:       F8               CLC
;       EF:       5D               POP RBP
;       F0:       C3               RET
NIL


CL-USER> (disassemble 'fast-and-unsafe)
; disassembly for FAST-AND-UNSAFE
; 044591BF:       4883C208         ADD RDX, 8                 ; no-arg-parsing entry point
;       C3:       488BE5           MOV RSP, RBP
;       C6:       F8               CLC
;       C7:       5D               POP RBP
;       C8:       C3               RET
NIL
CL-USER> 

```


(..I've set a compiler/run-time policy that states that safety should be 0 here..)
[/INDENT]

---

### Post by CptPicard on 2010-09-04
> **worksofcraft said:**
> 
Personally I have never have problems with the number of bits in my integers. I study my problem domain and choose appropriate sized entities to represent them. I don't have to. I could use double precison floating point for them all. Problem solved?

Mere integer size is such a triviality regarding what *truly interesting* "appropriate entities" can be in a program is that frankly a programmer who takes that as an example of how thoughtful and diligent he is probably has only been exposed to integer size and that kind of stuff as his *alternatives*... really, read Graham's "Beating the Averages". Great essay about this kind of mental imprinting. Then go try read SICP, hack some Scheme, and think about what you're writing. Fascinating stuff.

> 
Oh... mysteriously loops won't terminate because they check for floating point equality...

Well, floating-point representations and why they don't compare for equality is really basic CS that is valid for all computer languages, as you only have a finite amount of bits for all the points of the real line...

> 
 on Python's "shielded from trivial minutiae" universal number system :shock:

I suppose the Python you've written so far has been very basic, no? Really, the interesting stuff is in the overall design ideas of the language, higher-order functions, the way it does object-orientation a bit differently from C++/Java-style languages... all the while managing to maintain the amount of required basic concepts to a mercifully small number. This is generally a good design characteristic.

> **worksofcraft said:**
> 
IMO programmers should learn to think about normalizing the quantities in their problem domain and to avoid ill-conditioning of their solutions.

Sorry, how do you mean again? 

Yes, you need to know how to put the correct pieces together in any language and not to have the wrong assumptions about it. The latter is most interestingly demonstrated in Haskell -- functional programming tends you to force to think about your problem's structure right from the start, because you can't just hack together any random crap and then debug it, like you can do in a typical imperative language.


> They should also think about how data propagates through their system where it comes from where it gets used and it's authenticity accuracy and reliability... all strongly linked with understanding their memory management strategy.

"Data propagation" can be a much more deeply interesting subject, by the way (see "data flow programming") than I guess you appreciate. This is the sort of abstraction level I prefer to think on -- all the while "thinking about how data propagates through the system..."

I would, however, suggest that in a lower level language the risk of your data getting corrupted midway processing is much higher than in a higher level language, exactly because typing may not be enforced and memory access gives you much more potential for corruption, simply because of the way the language works. This is IMO just simply a negative, as it doesn't "force" the programmer to think any "better" about the problem at hand itself.  That is, the memory management strategy is just an *independent* liability of the implementation that may lead to issues if done wrong; but "having to do it" does not contribute in any way to programming the actual solution better. It's just an implementation issue forced by the memory management.

---

### Post by Some Penguin on 2010-09-04
> **CptPicard said:**
> Mere integer size is such a triviality regarding what *truly interesting*

Well, floating-point representations and why they don't compare for equality is really basic CS that is valid for all computer languages, as you only have a finite amount of bits for all the points of the real line...

...and even aside from that, the results of floating-point math are not guaranteed to be the same across architectures even of the same bit size and ordering.  This has consequences that are quite important if, say, you're writing a real-time game that isn't based upon a central server controlling all game state, because you have to worry about synchronization problems.  People who'd work in this field should know that.

Ditto for threads and scheduling, only even more so.

---

### Post by schauerlich on 2010-09-04
> **worseisworser said:**
> I'm not sure I understand your point or whether I agree with this.

As you move further and further away from the machine you need an increasingly better compiler. I'm not sure there is a "point" to knowing this; it just is.

What I meant was, you could call assembly a "green" language and Haskell a "red" language, but that makes no difference in their expressiveness or utility in given situations. It's just semantics.

---

### Post by CptPicard on 2010-09-04
> **schauerlich said:**
>  but that makes no difference in their expressiveness or utility in given situations. **It's just semantics.**

Come again? You're saying the LLL vs. HLL distinction is a matter of mere semantics?

---

### Post by schauerlich on 2010-09-04
> **CptPicard said:**
> Come again? You're saying the LLL vs. HLL distinction is a matter of mere semantics?

The labels we apply to them, yes. Just because a language is put in the high-level or low-level grouping does not make it inherently more useful in any given situation. That doesn't mean there's not a whole lot of important differences between Haskell and C. I meant semantics as in arguing over definitions of words, not from a programming perspective. 

I'm arguing the semantics of "semantics"... this just got a bit too meta for me. :)

---

