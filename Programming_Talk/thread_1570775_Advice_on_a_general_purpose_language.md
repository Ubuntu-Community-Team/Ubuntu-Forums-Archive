---
title: "Advice on a general purpose language"
date: 2010-09-08
forum: Programming Talk
---

### Post by holocene on 2010-09-08
Hello,

I am interested in a programming language that can implement these kinds of solutions:

[LIST]
[*]Provide a GUI interface to the user, [and a console interface if possible].
[*]Solve problems on the desktop that are largely non-internet connected. From one off type things to larger applications. I realize that the one-off requirement may be a problem.
[*]Solve problems on the desktop that involve the internet, principally, database access, like MySQL. In a browser and not.
[*]Useful for server side coding.
[*]Lead to a career.
[/LIST]
Initially, I thought that Ruby might fill the bill, but I have a suspicion that Ruby might be really unsuitable [or a weak choice] for GUI. Or, maybe I should say there might be better choices... 

From my reading, I believe Java might fill the bill on most of these points. However, I've read that, like Ruby, Java may be "weak" as a GUI tool.

My background is mostly SQL and database operations, with some c. Though lately I have spent a lot of time on Ruby, and am a OOP convert. From browsing the Java tutorials, I see strong similarities to Ruby and c (c for {} and that kind of thing). My gut feeling on Java is that it looks good, those verbose compared to Ruby.

Any tips or comments appreciated. 
Steve.

---

### Post by ibuclaw on 2010-09-08
I think C++ makes a good general purpose language, so long as you keep it simple and don't use any of it's inane features (outside of classes, class inheritance, and operator overloads). But hey, I'm biased. ;)

---

### Post by GenBattle on 2010-09-08
The number of jobs for C++ web programmers these days is basically a rounding error. Don't get me wrong, it's a handy language to know for server-side programming, but it is very large and cumbersome for small one-off jobs.

Languages like Ruby and Python are much faster to develop with and have greater utility, but there are far fewer jobs for them at the moment (at least in my country). Personally i would promote python as a good in-between language for mixed desktop/server/internet/non-internet work, especially if you can learn to write C/C++ modules to speed up certain functions and processes.

Java is one of the best general-purpose languages out there. There is a range of desktop and server applications that use it, some very successful. It is much more structured and verbose than scripting languages like python/ruby, but it runs faster and there are many more jobs for it.

.NET based languages will usually allow you to create a project that defaults to a generated GUI, but any non-ms language has far less emphasis on gui design through graphical tools. Java is one of the better languages in this respect with libraries like Swing, and python with it's tk-based interfaces, but both are a long way from Visual Studio.

It reality as programmers we have to accept that there is no "ultimate language" or single tool for any job. The best way to improve yourself as a programmer is to have knowledge of several tools which each have different strengths, and which you can use for different applications. For this reason i would recommend all of the above tools; learn some C/C++ so you can plug it into Java/Python/Ruby/etc. if you need to increase the speed of an application, learn Java so you have a commonly used enterprise language under your belt, and learn Ruby/Python/Perl/PHP/LUA/something else to give you a high-level tool to hack little scripts together with. Each tool has its own advantages and disadvantages.

---

### Post by worseisworser on 2010-09-08
> **holocene said:**
> 
[LIST]
[*]Lead to a career.
[/LIST]


It doesn't really matter; or it depends on where you're applying. 

So instead, learn to produce the results you've listed up in any set of language/environment of your choosing and you'll be OK. Learning a new language takes a few months; it is not a problem in comparison.

If you really "do not care" or would like to start in a so to say different end, simply do a search as to what local businesses are looking for; it varies depending on what your location is on the globe.

---

### Post by nvteighen on 2010-09-09
> **holocene said:**
> 
[LIST]
[*]Lead to a career.
[/LIST]


This isn't a technical criterion (as the others were), so depending on how much weight you place to this one, the results will be different.

If you're interested in making this a job, I'd possibly go for Java, it fits your citeria. You already have some programming experience, so you should be able to understand it.

---

### Post by ChurroLoco on 2010-09-09
Although I am a C++ programmer and have been working as a Java programmer for a while I recently starting using C# in Linux for fun.  This is possible using the [Mono framework]("http://www.mono-project.com/Main_Page").  I had always thought Mono was some half-rate implementation of the MS CLR, but since I have started using it, I actually prefer it.

The reason I really like Mono is that:
1.) It supports C# a very clean language in my opinion well suited for personal applications and web/server applications.

2.) The mono frame-work does a good job of imitating and improving the MS .net library which has many toys for doing all sorts of applications.

3.) Mono-Develop (The IDE) is very clean and easy to use.  You don't have to play around with the IDE to get a template project compiling. Also, syntax/error highlighting and auto completion are built in.  For GUI development it comes with GTK# tools.  Take a look [http://www.mono-project.com/GtkSharp]("http://www.mono-project.com/GtkSharp").

It certainly isn't the perfect language, but I seem to be very productive in it and I have seen many beginners also get a lot done.  For beginners I think it has a slight advantage over Java for the reason that there are some many way of doing things in Java it can be confusing.  Decisions like which IDE, packages, and tool to use can be difficult for beginners because there are so many in Java.
:KS

---

### Post by Some Penguin on 2010-09-09
Java is pretty good at certain of those (particularly server-side; JSPs, Tomcat servlets, lots of support for networking and data interchange, quite usable concurrent programming framework, multiple frameworks available for configuration e.g. Spring).  And it's pretty common (as in both supply and demand) in, say, Silicon Valley.

Can't speak much about GUI capabilities as those have zero interest for me.  I'm usually building systems that crunch gobs and gobs of data for which the direct users are other programs, not human beings.

Pare with various rameworks, and you have some semblance of functional programming as well -- no equivalent to 'eval' unless you're willing to play with bytecode, but e.g. passing around functions, composing them, lazily transforming an iterable with a function, interrogating an object or class to identify all its methods, and so forth.

JDBC would go well with your use of SQL.  It's sometimes useful to have Java code which creates PL/pgSQL functions which can be invoked by other Java code, heh (e.g. in the case of functions associated with dynamically created tables).

---

### Post by KdotJ on 2010-09-09
Although many people dislike java's swing (and AWT), and I agree it can be a pain sometimes, but I wouldn't call it a weekness of java. You can set it to match the look and feel of the platform it's running on, and they look pretty good. And not to mention java's server side web abilities... I'd say it's a good choice, but I'm biased too lol

---

### Post by ghostdog74 on 2010-09-09
> **holocene said:**
> hello,

[list]
[*]provide a gui interface to the user, [and a console interface if possible].
[*]solve problems on the desktop that are largely non-internet connected. From one off type things to larger applications. I realize that the one-off requirement may be a problem.
[*]solve problems on the desktop that involve the internet, principally, database access, like mysql. In a browser and not.
[*]useful for server side coding.
[*]lead to a career.
[/list]


php.

---

### Post by DanielWaterworth on 2010-09-09
> **ghostdog74 said:**
> php.
That's the funniest thing I've heard today.

---

### Post by ghostdog74 on 2010-09-09
> **DanielWaterworth said:**
> That's the funniest thing I've heard today.

what's so funny ? I am serious

> 
    * Provide a GUI interface to the user, [and a console interface if possible].

The only GUI the user need is the web browser. Nowadays, GUI is easily created with HTML. 

> 
    * Solve problems on the desktop that are largely non-internet connected. From one off type things to larger 
applications. I realize that the one-off requirement may be a problem.

PHP can also be used for scripting much like Perl/Python , not just web. 

> 
    * Solve problems on the desktop that involve the internet, principally, database access, like MySQL. In a browser and not.

PHP and MySQL is often widely used. 

> 
    * Useful for server side coding.

Need i say more?

> 
    * Lead to a career.

There are many who uses PHP. Need i say more?

---

### Post by ChurroLoco on 2010-09-09
And so the flame war starts! Ding Ding

:popcorn:

---

### Post by DangerOnTheRanger on 2010-09-09
Yep, here we go...

But if I may add my 2 cents(and I may:D), I must say that PHP is not for desktop scripting. That's not what it's intended for, and only poor, misguided souls do that.

But DanielWaterworth, I think you're wrong about PHP being the worst language ever:

[http://en.wikipedia.org/wiki/Esoteric_languages](http://en.wikipedia.org/wiki/Esoteric_languages)

But if I were to recommend a language to someone, I would say Python. It's many libraries are just staggering, and the syntax is very nice and easy to learn.

---

### Post by KdotJ on 2010-09-09
> **DangerOnTheRanger said:**
> 

But DanielWaterworth, I think you're wrong about PHP being the worst language ever:

[http://en.wikipedia.org/wiki/Esoteric_languages](http://en.wikipedia.org/wiki/Esoteric_languages)



Lol, I would like to see [LOLCODE]("http://en.wikipedia.org/wiki/LOLCODE") used more by companies hahaha...

---

### Post by ghostdog74 on 2010-09-09
> **DanielWaterworth said:**
> And they are distinctive because they are the brain damaged ones. php is, without exception, the very worse language ever conceived by any creature of any kind.

who are you to judge and call people "brain damaged" ? God?  

> 
 but for anything else it's like mixing cabbage and custard with a healthy side of twice baked sock. Sorry to burst your bubble.
Just because you don't find it tasteful, doesn't mean everyone else feels the same.

---

### Post by ghostdog74 on 2010-09-09
> **DangerOnTheRanger said:**
> 
But if I may add my 2 cents(and I may:D), I must say that PHP is not for desktop scripting. 
sure it does. Have you even tried ? If not, don't say it can't be done. If you have and still don't find it suitable, then you are most probably doing it wrong.

---

### Post by DanielWaterworth on 2010-09-10
> **DangerOnTheRanger said:**
> But DanielWaterworth, I think you're wrong about PHP being the worst language ever:

I stand corrected. PHP is the worst language ever conceived by any creature of any kind that was designed to be useful.

I think I was a little harsh though, there are good uses for php... just so long as you don't use the php tags.

---

### Post by ghostdog74 on 2010-09-10
> **DanielWaterworth said:**
>  PHP is the worst language ever conceived by any creature of any kind that was designed to be useful.


> 
.... there are good uses for php... 

Don't spew nonsense .If its not useful, nobody will use it for web development.

---

### Post by DanielWaterworth on 2010-09-10
> **ghostdog74 said:**
> Don't spew nonsense .If its not useful, nobody will use it for web development.

Market inertial is a powerful thing. That's why most people use qwerty when it's proven that better layouts exist.

---

### Post by clrg on 2010-09-10
Try Python. Its got a nice syntax, much cleaner than all the C++ like languages today. It will enable you to do complex things with just a third of the code compared to other languages.

---

### Post by holocene on 2010-09-10
I've read each of the responses carefully, and really appreciate the honest replies.

I think this discussion has borne out that there are multiple tools that can do any job, with greater or lesser utility.

That being said, my gut feeling is to focus on Java, especially concerning interaction with SQL databases. Plus, it is deployed nearly everywhere. 

I think the esoteric computer language discussion was valuable because illustrates how paradigms affect the way we view programming.  

Best Regards to all responders.
Steve.

---

### Post by KdotJ on 2010-09-10
> **holocene said:**
> I've read each of the responses carefully, and really appreciate the honest replies.

I think this discussion has borne out that there are multiple tools that can do any job, with greater or lesser utility.

That being said, my gut feeling is to focus on Java, especially concerning interaction with SQL databases. Plus, it is deployed nearly everywhere. 

I think the esoteric computer language discussion was valuable because illustrates how paradigms affect the way we view programming.  

Best Regards to all responders.
Steve.

I think Java is a good choice, not just because I use it myself, but because out of all the languages I have used, Java for me has been the easiest to deploy across different platforms

---

### Post by ghostdog74 on 2010-09-10
> **DanielWaterworth said:**
> Market inertial is a powerful thing. That's why most people use qwerty when it's proven that better layouts exist.
it doesn't matter. You can't hide the fact that all the points OP listed can be tackled using PHP (same applies to Python/Perl/Ruby etc). therefore, calling one language "inferior" or "worst" to another is not warranted here, since you would only become a flame baiter.

---

### Post by DanielWaterworth on 2010-09-11
> **ghostdog74 said:**
> it doesn't matter. You can't hide the fact that all the points OP listed can be tackled using PHP (same applies to Python/Perl/Ruby etc). therefore, calling one language "inferior" or "worst" to another is not warranted here, since you would only become a flame baiter.

Who here, except for ghostdog74, has ever decided to use php for desktop programming when they could have used another language, Python/Perl/Ruby etc, and enjoyed the experience?

If you could interface bf with c libraries then it would fulfil most of the points, but that doesn't make it a good choice.

---

### Post by ghostdog74 on 2010-09-11
> **DanielWaterworth said:**
> Who here, except for ghostdog74, has ever decided to use php for desktop programming when they could have used another language, Python/Perl/Ruby etc, and enjoyed the experience?
Its not a matter of whether i will choose PHP for desktop programming or not. The universal fact is, PHP can be used for desktop programming. If you can use pyGTK , or gtk2-perl, or Ruby/Gtk for desktop programming, then there's no reason you can't use PHP-GTK2 as well. Do you wish to deny the fact that there is PHP-GTK2 for [programming desktop applications with PHP? ]("http://php-gtk.eu/apps")

what about programming experience? Heck, some don't like Python, some don't like Perl and some don't like Ruby. What's there to talk about?

---

### Post by worseisworser on 2010-09-11
What about ASM, ghostdog74? It too can be used for desktop programming.

edit:
..but yeah; I suppose ASM is less general purpose than PHP. Still, there certainly are languages that because of language or library or both level issues are better suited at some things than others.

---

### Post by ghostdog74 on 2010-09-11
> **worseisworser said:**
> What about ASM, ghostdog74? It too can be used for desktop programming.
sure why not. People have done windows apps using assembly only. The question is , would you want to use it to create apps?

---

### Post by worseisworser on 2010-09-11
> **ghostdog74 said:**
> sure why not. People have done windows apps using assembly only. The question is , would you want to use it to create apps?

Yes, exactly, and while I have not paid too close attention to this discussion; can one not say the same thing about PHP *even* though it has Gtk+ bindings?

Perhaps the PHP + desktop combination is not as poor as the ASM + desktop combination, but yeah, I would certainly try to avoid it based on advice from others even though PHP was the only language I knew; at least if I was going to develop something non-trivial.

---

### Post by ghostdog74 on 2010-09-11
> **worseisworser said:**
> Yes, exactly, and while I have not paid too close attention to this discussion; can one not say the same thing about PHP *even* though it has Gtk+ bindings?

No, of course you can't say the same thing. That's apples and orange. Why don't you say the same about Python/Perl/Ruby as well since they also have GTK bindings ? PHP has similar bindings to GTK as do Python/Perl/Ruby so why can't one use PHP to do desktop applications using GTK, since they are similar ? Assembly just doesn't cut into this picture. (ie to say, you are way off in making relevant comparisons)

>  I would certainly try to avoid it based on advice from others even though PHP was the only language I knew; at least if I was going to develop something non-trivial.
Let me ask you. You took advice from others based on what they say, OR you took their advice based on your own verified experimentation/experience  ?

---

### Post by worseisworser on 2010-09-11
> **ghostdog74 said:**
> No, of course you can't say the same thing. That's apples and orange. Why don't you say the same about Python/Perl/Ruby as well since they also have GTK bindings ? PHP has similar bindings to GTK as do Python/Perl/Ruby so why can't one use PHP to do desktop applications using GTK, since they are similar ? Assembly just doesn't cut into this picture. (ie to say, you are way off in making relevant comparisons)

Because it's not really about the bindings.


> **ghostdog74 said:**
> Let me ask you. You took advice from others based on what they say, OR you took their advice based on your own verified experimentation/experience  ?

Both; people take advice based on the results of others' experiments and experiences presented in a way that makes sense for "outsiders"; using a common language sub-set or other things both parties already understand and agree on.

edit: Just to be clear; I have used PHP, and I did not enjoy it. Language level issues bothered me the most.

---

### Post by ghostdog74 on 2010-09-11
> **worseisworser said:**
> Because it's not really about the bindings. 
then what are you talking about? We are discussing using PHP for desktop applications. GTK bindings for PHP have been available for use to do that, same as those for Python/Perl/Ruby. Bringing assembly into the picture is irrelevant.!

> 
edit: Just to be clear; I have used PHP, and I did not enjoy it. Language level issues bothered me the most.
That's your choice, and i do not care. What i am emphasizing here is a fact, that PHP can be used to do desktop applications. That's all. Whether its suitable or not is secondary, since people's choices are all subjective.

---

### Post by worseisworser on 2010-09-11
> **ghostdog74 said:**
> then what are you talking about? We are discussing using PHP for desktop applications. GTK bindings for PHP have been available for use to do that, same as those for Python/Perl/Ruby. Bringing assembly into the picture is irrelevant.!


That's your choice, and i do not care. What i am emphasizing here is a fact, that PHP can be used to do desktop applications. That's all. Whether its suitable or not is secondary, since people's choices are all subjective.

Ok, I view it differently; he is (or we are) not looking for what is possible to do, but instead advice as to what is a good idea to do.

edit:
I don't agree on the subjective part, this isn't "magic" or something like that, but that's sort of another philosophical discussion type thing ..

---

### Post by Elfy on 2010-09-11
Why is it that any thread in this forum about a choice someone is trying to make ends up with pointless name calling.

Pack it in or I will close the thread.

---

### Post by nvteighen on 2010-09-11
> **forestpiskie said:**
> Why is it that any thread in this forum about a choice someone is trying to make ends up with pointless name calling.


Because people here have too strong opinions... I guess... and we prefer to lose our time discussing pointless stuff here instead of learning new things, code useful things and discuss interesting pointful (does that word exist?) topics... *sigh*

---

