---
title: "Getting back into programming..."
date: 2007-06-19
forum: Programming Talk
---

### Post by Mr_J_ on 2007-06-19
I know Pascal basics and a bit of C.

I'd like to get back into programming as I've been away for years and I'd like a few recomendations as to a programming language I can learn in Ubuntu and Windows XP.
Preferably the same IDE...

I remember i liked doing that more than gaming so what do you recomend?

Need something to pass the time... ;) Migh as well make it usefull... :D

Thanks in advance!

P.S. : Is there a language that has a definite future nowadays?

---

### Post by LaRoza on 2007-06-19
Try Python. check my sig for resources.

It works in Linux and Windows, requires no compiling, is powerful, and is easy to learn.

[http://www.activestate.com](http://www.activestate.com) for ActivePython for Windows.

The thread in my sig is difficult to follow, go to post 26 for an easier time.

You can use any editor, and there are IDE's, but I recommend using whatever you prefer, I use GEdit and Crimson Editor. They both have syntax highlighting.

---

### Post by pmasiar on 2007-06-19
hey, see also *my* sig for Python links! :-)

Python has simple cross-platform IDE, called IDLE. Another more rich good crossplatform IDE is SPE (Stani's Python Editor).

And Python definitely has the future: Google uses it a lot, and read also [Hundred-year language](http://www.paulgraham.com/hundred.html) - essay about future language evolution.

---

### Post by samjh on 2007-06-19
C++
Python
Java
Ruby
C#

...all have strong futures.

Python and Ruby will grow, but growth has declined somewhat for both languages since the dynamic languages gaga of 2005-2006.  Nonetheless, they will continue to grow, especially in the server-side enterprise sector, and in some niche desktop applications.  Ruby already has a small but strong foothold in the web services sector.  Python has a strong hobby following among computer enthusiasts and the scientific community, but hasn't really penetrated other niches as deeply as Ruby has penetrated the web services market.  However, languages like these tend to rise and fade quickly, as evidenced by the success and following obscurity of Lisp, Lua, and Scheme, and the successful niche occupations of JavaScript and some BASIC variants.

Java will remain steady for at least another decade, and then decline gradually over a period of another couple of decades.  It is still growing rapidly as an embedded devices platform for mobile phones and portable computers (and surprisingly, the gaming and military industries), and a lot of enterprise projects continue start new projects using Java.  I'd say it will remain a strong platform, and will be influential even after it has faded away, much like COBOL.  It probably has another two or three decades of useful significance.

C++ has already started to decline quite sharply since the introduction of Java and .NET, but will still be a strong desktop applications and system programming language for another couple of decades before fading into obscurity.  It will probably end up something like Fortran - popular in some small niches, but largely ignored.  But the time it will take to reach that stage will be very long: give it at least another two decades before becoming completely obscure.

C# depends on the lingering threats posed by Microsoft's patents on some of its language features and the .NET infrastructure.  But until anything drastic happens, it will probably be a strong language for the Windows platform for another decade.  But its future afterwards remain tied with the future of Microsoft (a lot can happen in 10 years).  I don't see C# penetrating too deeply into the UNIX/Linux world.

---

### Post by Smygis on 2007-06-19
I started programing with C and then i moved on to C++. But i just did not have that fun.  But then about a year ago i decided to try Python. And dude, Its an awsome language. Easy to learn, And fun to use.

Creating cross-platform apps is simple using wxPython.

Try Python, Its the language that made me like programming a lot.

---

### Post by LaRoza on 2007-06-19
> **pmasiar said:**
> hey, see also *my* sig for Python links! :-)

Python has simple cross-platform IDE, called IDLE. Another more rich good crossplatform IDE is SPE (Stani's Python Editor).

And Python definitely has the future: Google uses it a lot, and read also [Hundred-year language](http://www.paulgraham.com/hundred.html) - essay about future language evolution.

My sig includes your sig, on post 26, I made a simple index of the posts, and yours is there.

---

### Post by vexorian on 2007-06-19
I would never have as much fun coding in any language that is not C++.

---

### Post by LaRoza on 2007-06-19
> **vexorian said:**
> I would never have as much fun coding in any language that is not C++.

Try Whitespace, it looks fun.

---

### Post by pmasiar on 2007-06-19
I agree with 90% of what you said about Java == Cobol++, C++ as new Fortran, etc (and trimmed it out). But .... (you knew there will be a but, right? ;-) ):

> **samjh said:**
>  dynamic languages gaga of 2005-2006.

I strongly disagree with the "gaga". IMHO Java developers realized, that since 90% of the response time of a web-based appliation is consumed by database query anyway and out of programmer's control, you can do remaining 10% in a dynamic language (even if 30-50% slower) and have almost the same response time, but substantially lower development cost.

> However, languages like these tend to rise and fade quickly, as evidenced by the success and following obscurity of Lisp, Lua, and Scheme, and the successful niche occupations of JavaScript and some BASIC variants.

Just read the "hundred-year language" link in my previous post.

Microsoft hired key JPython and JRuby developers to implement Ruby and Python for .NET. Looks like they are first to realize that if you use dynamic language as glue for statically-compiled library calls, you can have best of both worlds: agility and dynamic speed of development and runtime speed of static compiled languages.

Statically typed languages are following assembler code: special niche for speed.

> Java will remain steady for at least another decade, ... enterprise projects continue start new projects using Java. 

Agree. Keyword is "enterprise". And question is, do you want to program for a company of 600 Dilberts and Wallys, run by PHB. :-)

How many startups use java? java is solid but boring. Python is fun and agile.

---

### Post by vexorian on 2007-06-19
It is likely python and ruby won't survive this decade, recently you just see hype and whatnot. I don't really find it substantially easier than any alternative and there are better languages at exploiting dynamism.

---

### Post by samjh on 2007-06-19
> I strongly disagree with the "gaga".It was a gaga.  Lots of people talked about Ruby and Python, and there was a lot of experimentation going on with the two languages.  Sounds like gaga to me.  Maybe you take "gaga" with a different meaning.

> IMHO Java developers realized, that since 90% of the response time of a web-based appliation is consumed by database query anyway and out of programmer's control, you can do remaining 10% in a dynamic language (even if 30-50% slower) and have almost the same response time, but substantially lower development cost.Correct.

> Microsoft hired key JPython and JRuby developers to implement Ruby and Python for .NET. Looks like they are first to realize that if you use dynamic language as glue for statically-compiled library calls, you can have best of both worlds: agility and dynamic speed of development and runtime speed of static compiled languages.

Statically typed languages are following assembler code: special niche for speed.Essentially what I was saying.  Languages like Python and Ruby are niche languages.  They rise up quickly, and then fall into a niche, rather than staying on as a general-purpose language like C++ has.

> Keyword is "enterprise". And question is, do you want to program for a company of 600 Dilberts and Wallys, run by PHB. :-)

How many startups use java? java is solid but boring. Python is fun and agile.Solid is what matters in the real world.  Boring is irrelevant.

Startups do not make a language significant.  Mainstream adoption, and that usually means "enterprises", make a language significant and influential.

A lot of startups fail in the IT industry.  The few that succeed eventually end up "boring" anyway.

Being a pragmatic sort, I recognise that Python is a significant addition to a programmer's bag of tricks.  But in any critical environment, you go for the safest option, and that usually means a language or development platform that is popular in the industry, well-supported, and unlikely to fade away in the near future.  I think Python lacks strength in all those areas (except maybe the last), despite its technical merits.

I don't get the humour about wallies, dilberts, and pointy-haired bosses, purely because I've never read a Dilberts comic (notice that I've done enough research to know what they refer to :) ).  My experience is somewhat different.

---

### Post by pmasiar on 2007-06-19
> **vexorian said:**
>  there are better languages at exploiting dynamism.

Like what?

---

### Post by pmasiar on 2007-06-19
> **samjh said:**
> Languages like Python and Ruby are niche languages.  They rise up quickly, and then fall into a niche, 

If language is used for 80% of my code (everything except some libraries, written by experts for speed), it is not niche. *library* is the niche. :-)

> Solid is what matters in the real world.  Boring is irrelevant.

In real life, also productivity is relevant. if I can whip up app 5 times faster in dynamically typed language, it *is* relevant. IMHO. :-)

> Startups do not make a language significant.  Mainstream adoption, and that usually means "enterprises", make a language significant and influential.

Small companies and small project do not have to endure strict discipline and bondage required for huge projects. Being nimble and flexible is important competitive advantage for small companies against the big. Big company can afford from time to time be less than agile - but small company better should.

> A lot of startups fail in the IT industry.  The few that succeed eventually end up "boring" anyway.

Well, YouTube succeeded without being boring. And is *not* in java. :-)

> But in any critical environment, you go for the safest option, 

Oh, absolutely. No Python for nuclear powerplant of course. But there is a lot of programming opportunities where being fast (speed to market) and nimble is more important.

> because I've never read a Dilberts comic 

You are missing a lot. :-)

---

### Post by Smygis on 2007-06-19
> **samjh said:**
> Being a pragmatic sort, I recognise that Python is a significant addition to a programmer's bag of tricks.  But in any critical environment, you go for the safest option, and that usually means a language or development platform that is popular in the industry, well-supported, and unlikely to fade away in the near future.  I think Python lacks strength in all those areas (except maybe the last), despite its technical merits.

I dont think the guy/girl want to get in to the industry. Python is a strong langue growing fast now and has a wery nice community. And i have to strongly disagree with that it will fade away in say 10 years time.
Particualary in the OSS arena. Many linux distros are completly dependent on Python (Gentoo and to some extent Ubuntu. Gentoo is realy unusable without python). Python might slow down, But it wont stop.

---

### Post by vexorian on 2007-06-19
Perl used to be the OS OS (huh lame name) favorite child, but it did fade away didn't it?

---

### Post by LaRoza on 2007-06-19
Perl is still used.

By the way, can anyone get to [http://widget.free.bg/](http://widget.free.bg/) without trouble? Frame trouble

---

### Post by Smygis on 2007-06-19
> **vexorian said:**
> Perl used to be the OS OS (huh lame name) favorite child, but it did fade away didn't it?

Python replaced it, Yes.

I dont see anyone comming up with a language to replace Python. C# perhaps.
Well, Time will tell. Right now Python is a great language. Perhaps not in the big industry. But in the free/open software arena. And it will most likley stay that way for some time.

---

### Post by samjh on 2007-06-19
> **Smygis said:**
> I dont think the guy/girl want to get in to the industry. Python is a strong langue growing fast now and has a wery nice community. And i have to strongly disagree with that it will fade away in say 10 years time.
Particualary in the OSS arena. Many linux distros are completly dependent on Python (Gentoo and to some extent Ubuntu. Gentoo is realy unusable without python). Python might slow down, But it wont stop.

I wasn't really directing that comment at the OP.  It was at Pmasiar, hence my quoting him.

I don't think a language can ever completely "stop" without a very long time going past it.  How about Python slowing down after 10 years?

After all, Perl used to be huge, but it is now pretty much obsolete.  But no-one seriously challenged Perl with a new language when Perl was at its peak.  The same will happen to Python, IMHO.  It's a great language now, but sooner or later it will have a successor, and I think the history of interpreted script-like languages show that it will be sooner than later.  At least it will probably fade away before Java/C++/C# become really obsolete.

---

### Post by LaRoza on 2007-06-19
Seeing how Python changes and improves, it will take a lot to make it obsolete.

---

### Post by samjh on 2007-06-19
> **pmasiar said:**
> In real life, also productivity is relevant. if I can whip up app 5 times faster in dynamically typed language, it *is* relevant. IMHO. :-)But how significant is Python or Ruby's productivity on the whole?  I'm not talking about just server-side programming or web services here, but programming in general, including desktop client applications and even lower-level applications (not system software, but close to it).

Has anyone done quantitative research on the cost -vs- benefit of using Python, compared to Java, C#.NET, or C/C++?  What about Perl and PHP for server-side scripting and web applications?  How does Python compare on the whole, and in specialised fields?

I don't think any definitive research yet exists, and anecdotal evidence is scarce and unreliable, since very few large-scale projects have been completed using Python.

> Well, YouTube succeeded without being boring. And is *not* in java. :-)You mean YouTube doesn't LOOK boring.  The content of YouTube makes it fun.

I've read Google is a pretty cool place to work in, but not a whole lot different from other large tech companies, and worse in some cases.  You could even say Google and YouTube are boring in terms of corporate working environment, depending on your attitude and tastes. :)

> Oh, absolutely. No Python for nuclear powerplant of course. But there is a lot of programming opportunities where being fast (speed to market) and nimble is more important.True.  But there hasn't really been any proven "time to market" benefit for Python, except in relatively small applications.

Anecdotes for smaller projects indicate that benefits exist.  But how do they scale for larger projects, and for projects in widely divergent areas of development?  How good is Python for web services, compared to embedded applications, and desktop client applications?  Will programming an Office-like suite be better in Python or C++, and will the final product be more marketable if it is in Python or C++?  These are questions that should be answered, if Python is to be recognised as a strong language and development platform by the wider IT industry.

It's easy to point at YouTube and Google, and proclaim that Python is a fantastic language.  But both of those companies are web services companies.  In fact, Google's majority code base is C++, not Python, especially for its desktop application projects.  NASA occasionally gets brought up too, but keep in mind that NASA has been using Java for nearly 10 years, and in some very large and complex projects, such as the Hubble Space Telescope (remote control systems) and the Mars rover mission (image and terrain analysis).

It's high time that Python got picked up on some major large-scale projects to demonstrate that it is feasible to use Python for those kinds of ventures.  The Python website seem very good at publicising that sort of thing.  Then I'm sure Python will become a strong mainstream contender among programming languages and platforms.

---

### Post by LaRoza on 2007-06-19
In the book *Dreaming in Code*, the use of Python is used for a PIM. The project the book follows is located at:

[http://chandler.osafoundation.org/](http://chandler.osafoundation.org/)

---

### Post by pmasiar on 2007-06-19
> **samjh said:**
> How about Python slowing down after 10 years?

It's a great language now, but sooner or later it will have a successor, and I think the history of interpreted script-like languages show that it will be sooner than later.  At least it will probably fade away before Java/C++/C# become really obsolete.

Well, can you show me the language which will replace Python? I was looking hard and cannot find any. So IMHO your vision of Python slowing down is extrapolating past trends. Sure most startups fail, but some do make it to the very top? So IMHO Python is not in "pre-IPO" stage and very good bet. YMMV.

I see Python's acceptance steadily increasing, with **no reason to stop increasing**. IMHO Python developers (with Guido as BDFL) has enough experience and taste to feel what is important in new generation of languages: developers are more important than CPUs.

Python is first language (I know of and used in practical environment -- I never used Smalltalk) which places focus squarely on **productivity of developer and readability** above anything else. And as CPU power will keep increasing, we will have more and cheaper CPU cycles to burn on anything we want. Did you read the "hundred year language" I linked above? Which parts you disagree, if any?

If we can agree that Python is *the best* language for agile app development for next 10 years, it is good enough for me :-D (of course with some libraries in C/C++ for speed)

I have no problem with many languages in many niches (for legacy or some niche-specific features), but I strongly believe that (currently and in next 5-10 years) Python is best language for:
- beginner programmer, especially self-learner, as first language
- mainstream application development (except security apps, huge enterprise apps, and deep kernel where speed is important)
- mainstream web app development -- where is figting for mindshare with Ruby, which has earlier start, but less clean (more perlish) syntax

BTW I do like how this discussion, even if heated, is still based on facts and strongly felt opinions, not on baseless smear with no background info (except vexorian, but he is new here and apparently does not know any better :-) ).

---

### Post by samjh on 2007-06-19
> **pmasiar said:**
> Well, can you show me the language which will replace Python? I was looking hard and cannot find any. So IMHO your vision of Python slowing down is extrapolating past trends. Sure most startups fail, but some do make it to the very top? So IMHO Python is not in "pre-IPO" stage and very good bet. YMMV.I think it's safer to extrapolate on past trends, rather than trying to pull ideas out of thin air.

Yes, some startups do make it to the very top.  We can all point to the likes of Bill Gates, Steve J & W, the pair who founded Google (can't remember their names), etc.  But they all stand as corporate giants now, with the heavy momentum and conservative decision-making that comes with it.

> I see Python's acceptance steadily increasing, with **no reason to stop increasing**. IMHO Python developers (with Guido as BDFL) has enough experience and taste to feel what is important in new generation of languages: developers are more important than CPUs.Well, you can say that about the developers of almost every language.  If you look at the CVs of ISO standards panel members for C++, etc., you'll find they're no idiots.

James Gosling at Sun is no idiot, either.  In any case, Java, like Python, is developed in accordance with the wishes of the developer community.  But unlike Python, the community is many times larger, hence demand is great and development in comparison to demand is slow, but equally fast (if not faster) in magnitude.

Anders H of Microsoft has quite a healthy CV for his job as C# architect too.

> Python is first language (I know of and used in practical environment -- I never used Smalltalk) which places focus squarely on **productivity of developer and readability** above anything else. And as CPU power will keep increasing, we will have more and cheaper CPU cycles to burn on anything we want. Did you read the "hundred year language" I linked above? Which parts you disagree, if any?

If we can agree that Python is *the best* language for agile app development for next 10 years, it is good enough for me :-D (of course with some libraries in C/C++ for speed)I can only agree that Python is *the best* language for small-scale rapid application development in an open-source market, **at the moment**.

I do not agree that Python is a viable platform for application development in the proprietary, closed-source market.

I also do not wish to proclaim that Python will still remain the best in 10 years time.  C++ went from being a lab experiment to a full-fledged mainstream language in a space of only around 5 years.  Java went from first public release to mainstream in a space of less than 3 years.  Who is to say that a language being tinkered by a researcher at the moment will not suddenly spring forth and knock Python off in a few years time?

Unless Python gains mainstream acceptance with enterprises for new projects, it will be knocked off much faster than if it does have such acceptance.  So ultimately, it is my opinion that Python will be long-lived only if it becomes mainstream for large businesses, and its life will be as short as only 10 years if it only stays as a hobby/tinkering language for enthusiasts and small development workshops.

> I have no problem with many languages in many niches (for legacy or some niche-specific features), but I strongly believe that (currently and in next 5-10 years) Python is best language for:
- beginner programmer, especially self-learner, as first language
- mainstream application development (except security apps, huge enterprise apps, and deep kernel where speed is important)
- mainstream web app development -- where is figting for mindshare with Ruby, which has earlier start, but less clean (more perlish) syntaxI partially agree with the first point, but with the qualification that the learner is not learning for system-level programming.  In which case I think C is better.

I disagree with the second, because for me, you have excluded one large chunk of "mainstream", which are large-scale enterprise apps, and make no mention of commercial software, which forms another large chunk.

I will partially agree with the third, but I think your perception of Ruby is stilted by your personal dislike of Perl. ;)  But then my experience with developing web apps in almost zero. :o

> BTW I do like how this discussion, even if heated, is still based on facts and strongly felt opinions, not on baseless smear with no background info (except vexorian, but he is new here and apparently does not know any better :-) ).Well, I think it's quite a rational discussion.  A heck of lot better than the flamewars we get in this forum occasionally.  Much of our disagreement stems of our differing backgrounds, I think.  You are a web programmer, if I read you correctly; while I come from a desktop/firmware background.  And if my thoughts are correct, the web app/services industry are more friendly to using interpreted script-like languages such as Python, than desktop application or system development fields.

---

### Post by pmasiar on 2007-06-19
> **samjh said:**
>  Java went from first public release to mainstream in a space of less than 3 years.  Who is to say that a language being tinkered by a researcher at the moment will not suddenly spring forth and knock Python off in a few years time?

One big difference between Java and Python is, that Python has no corporate support until recently - and even now, it is dwarfed by Sun's push for Java. As a result, Python get to the position it has on it's own, on quality and convenience, promoted by word-of-mouth by hackers, without any marketing push. *This* is big difference between Python and competitors. BTW Ruby is being stampeded by former Java developers, fed by over-complicated Java web frameworks. They are going to be burned by it's perlishness. :-)

What would do this Python-killer language differently? We need dynamic memory allocation with GC, dynamic typing (late binding) and good introspection, vast library, and readability. The only incoming challenge I see is handling multicore CPUs. Parallel programming is rather different, let's hope Google will pay some Python hackers to steal good ideas from Erlang. :-)

> I will partially agree with the third, but I think your perception of Ruby is stilted by your personal dislike of Perl. ;)  But then my experience with developing web apps in almost zero. :o

Yes, I admit disliking Perl. Perl was breeze of freedom for me after years of developing database apps in compiled strongly typed languages. But after I suffered 4 years of famous Perl flexibility (TIMTOWDI) and when  looked up what is possibly coming as Perl 6 (see [url=http://www.ozonehouse.com/mark/blog/code/PeriodicTable.html]Perl's periodic table of operators[/ur] -- and it not a joke guys), I gave up. And also on Ruby - it is way too perlish for my taste.

> Much of our disagreement stems of our differing backgrounds, I think.  You are a web programmer, if I read you correctly; 

Agreed, and Yup.

>  web app/services industry are more friendly to using interpreted script-like languages such as Python, than desktop application or system development fields.

... because in web front-end for a database, we have 1-2 sec delay anyway, and no compilation will make it faster, so why not do our life easier and fun?

---

### Post by Ubuntist on 2007-06-21
> **Mr_J_ said:**
> I know Pascal basics and a bit of C.

I'd like to get back into programming as I've been away for years and I'd like a few recomendations as to a programming language I can learn in Ubuntu and Windows XP.
Preferably the same IDE...

I remember i liked doing that more than gaming so what do you recomend?

Need something to pass the time... ;) Migh as well make it usefull... :D

Thanks in advance!

P.S. : Is there a language that has a definite future nowadays?

As others have said, Python seems a good choice -- it's powerful, popular and I'm sure it will still be around in ten years' time. But if you want to stretch your brain out and have some fun, try Scheme. It will change your perspective on programming.

---

