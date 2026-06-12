---
title: "[SOLVED] Perl or Python? General purpose."
date: 2009-01-03
forum: Programming Talk
---

### Post by whiteychs on 2009-01-03
Ok, I've been researching this topic for quite some time now.

I've been basically through every Google search result that deals with python and perl in detailed comparison.

I've seen the TIOBE report but that's mostly based on hype, right? I don't care about which is the most talked about, I want a language that's functional and gets the job done and that will continue to be supported well into the future!

I'm dead set on learning Perl or Python - which is what's killing me.
Note: I'm more software oriented as opposed to sysadmin work, but I'd like a multipurpose language that is adept at both.

My Needs:

    * General purpose scripting / programming
    * Most popular (not as in cool but as in employability)
    * Small apps somtimes utilizing a GUI.
    * Embedding
    * Help me learn more about *NIX mechanisms
    * Overall fun but still having a dept in syntax


My thoughts -
**Python:**
I've had much experience in OOP (C++, VB, Java), and I've read (and experience in what little code I've written) that Python is much better in this regard. Function and class creation seems much more intuitive to me than in Perl 5. The syntax overall is much cleaner and more structured and therefore easier to read. It's future seems bright with Google's backing (since Guido works there) and the reliability of their release cycle (e.g. Py3k).
** The forced white space and lack of C based braces and semicolons are kind of off putting and makes it seem almost "kiddy" to me. What are your thoughts on this? I realize it makes code easier to read, but at what price?

**Perl:**
Perl **appears** to be a much more mature language. Perl is much different than what I'm used to in syntax and thinking patterns, but is that a bad thing? I think Perl has a better lesson to teach me about different ways to program, but that comes at a steep learning curve and an uncertain future - namely Perl 6 and how it will be received.


So I guess what I'm asking is: Which has the best future? I believe, Perl is at the moment more employable (??), but will that change? With Python's corporate backing and Perl 6 close to vaporware, would my time best be spent learning Python? Will Perl 6 be a home-run with its vast improvements? Also consider i want a more general purpose language that allows me to hack up quick progs.

---

### Post by jmartrican on 2009-01-03
I can only give my experience with Perl.  In the software eng group I work in we use a lot of Perl.  We use it for little things, i.e. alarming and monitoring scripts, and we use it for big things, i.e. massive web services and a custom framework (a portal that encapsulated various engineering tools).

We also use it to collect massive amounts of logs over the network and store them in to a massive DB... a lot of throughput.

We have had no problems, except one which I'll point out, and this is mostly because we are always able to find a library some where that does exactly what you need.  My only gripe is that I have heard negative thigns about its threading capabilities... maybe this has been fixed recently. 

With little to no experience I quickly wrote a syslog server with accompanying front-end in Perl and it was rolled out into production and used for a few years before we replaced it with a faster more scalable one.  It handled thousands of devices and with hundreds of users accessing the website.  It was pretty stable, fast, but the code was ugly due to it being my first program.

One last thing, you can also run C code with Perl.

---

### Post by jmartrican on 2009-01-03
Oh yeah all that stuff I mentioned I do not think none of it used OO.  SO I cannot speak for Perl's OO capabilities.  I know there is a text book out there that focusses on Perl and OO.  So if anything you know you got a whole book on the topic.

---

### Post by pmasiar on 2009-01-03
You will invariably get many opinionated answers (you basically ask, which child is the pretty one :-) ) but you seems to be able to evaluate opinions, so all is not lost. For sure also read "Why I love/hate" series in stickies, even if many arguments pro and con would be repeated here by me and by other posters. It's kinda FAQ you know? :-)

and yes, I do have experience with both Perl and Python, I was regular as PerlMonks at 2001 - and I am scared that someone will ask me to maintain app I did when I was learning Perl :-)

> **whiteychs said:**
> I've seen the TIOBE report but that's mostly based on hype, right?

No, they base it on search engine result, you may want to read up the methodology. BTW Python won "language of 2007" award, IIRC I started a thread about it :-) 

whiteychs> I don't care about which is the most talked about, I want a language that's functional and gets the job done and that will continue to be supported well into the future!

Either one fits the bill

whiteychs> I'm more software oriented as opposed to sysadmin work, but I'd like a multipurpose language that is adept at both.

Perl is closer to sysadmin tools, focused on couple of lines of throw-away scripts. Many (not all) people consider Perl ill suited for big projects, I recall at least one project  (IRRC bugzilla or something) switching away from Perl because of poor maintainability.

whiteychs>  * Most popular (not as in cool but as in employability)

Perl is past it's prime. Because there are enough old-timers who know Perl, you may have more luck on growing Python market. Also, Python is becoming more popular for web applications: stealing ideas from Ruby on Rails, Django and Turbogears are quite neat frameworks. Perl community was never able to focus around just few frameworks (TIMTOWDI all over again), is quite more dispersed. One of reasons is that it is simpler to share Python code because style is more similar, another reason is that Python's culture is more about deciding on best library for a task and adding it into the core - Perl never was like that, CPAN is total anarchy.

Ie you may get a job in many Python startups, but I would run away from Perl-based startup :-)

whiteychs>  * Small apps somtimes utilizing a GUI.

Python's EasyGUI is the simplest GUI on the market: again, focus on sharing libraries, unlike Perl

whiteychs>  * Help me learn more about *NIX mechanisms

Perl is closer to *nix shel tools

whiteychs> * Overall fun but still having a dept in syntax

Python fits my brain better: Perl is full of quirks, and if you don't "sacrifice to the Perl gods" weekly, you forgot them, and they will  bite you.


whiteychs>** The forced white space and lack of C based braces and semicolons are kind of off putting and makes it seem almost "kiddy" to me.

I understand your uneasiness - it is **exactly** as I felt about significant whitespace, and I started with Python 2 years later because of that. But relax: after 15 minutes it is not a problem - and common code style **does** improve code sharing. After a while, you miss that in other languages - and after all, it is just plain old structure which you should do anyway, no big deal.

whiteychs> Perl **appears** to be a much more mature language. 

Perl is little older but it's design process was more chaotic - and it's promotion was blessed with really talented speakers and writers, which made the difference when in .com boom everybody was looking for a duck tape to fix internet.

For old projects now, there is little reason to switch from Perl, but for new projects, there is little reason so start in Perl, Python (or possibly Ruby) is clearly better future-proof.

whiteychs> Perl is much different than what I'm used to in syntax and thinking patterns, but is that a bad thing? 

Yes. And other people thing differenly in Perl, and you will be puzzled by their code.

There are two jokes comparing Perl and Python:

"Perl is executable line noise. Python is executable pseudocode". You cannot write  poetry in Python, Perl has competition in haiku and in golf ("accomplish task in less amount of characters of code").

"Perl is proud on  [TIMTOWDI](http://en.wikipedia.org/wiki/There_is_more_than_one_way_to_do_it). Python approach is "there should be one obvious way to do it right" which fits brains better.

whiteychs> I think Perl has a better lesson to teach me about different ways to program, 

not necessarily so. Learn Lisp, Forth, Erlang and Prolog for that. Perl shamelesly adds features but they don't mesh with each other. Python is the only language I know which abandoned features when found better expressions for them.

whiteychs> namely Perl 6 and how it will be received.

Most people stopped caring cople of years ago. Also, they wasted a lot of time for universal runtime engine able to support multiple languages - but I don't see any stampede to switch working runtime for it, not for Python and neither Ruby. Why would they?

whiteychs> Which has the best future? I believe, Perl is at the moment more employable (??), but will that change? 

Current situation depends on exact market where you are, but with django-based applications like [http://en.wikipedia.org/wiki/Satchmo_(online_store](http://en.wikipedia.org/wiki/Satchmo_(online_store)) Python popularity will grow faster, and learning it is much better investment of time, IMHO.

Perl will be around for a long time, but it says little - COBOL is still around :-)

---

### Post by ghostdog74 on 2009-01-04
> **whiteychs said:**
> 
I'm dead set on learning Perl or Python - which is what's killing me.
why fret so much? Just learn both, since you only have 2 choices. Also, both languages are similar in what they can do, whether its for sysadmin or what. Stop worrying about which is more employable. By learning both, YOU are more employable.  In programming, you can't be stuck knowing just 1 language.  That's my standard answer to you.

---

### Post by slavik on 2009-01-04
everyone else has covered Perl5 vs. Python quite well, I'll cover the bits I know about Perl6. But one thing is that Perl's threads are kernel threads, whereas Python threads are userspace threads living in the interpreter (look for "Python GLobal Interpreter Lock")

as far as perl6 ... I've been playing around with it and it is a lot of good stuff. So far, there are already OpenGL bindings and some more often used libraries like getopt. Perl6 is also being designed from the "write language spec first, imterpreter second" type of approach. This allows you to have multiple "official" Perl6 interpreters (as long as they pass the spec tests).

regular expressions have been changed and the new grammars are really nice. grammars are like backus-naur form on steroids and then some.

---

### Post by efexD on 2009-01-04
Learn both, the more you know, the better! :P

---

### Post by Greyed on 2009-01-04
FWIW like pmaiser I too have programmed both in Perl and Python.  Perl professionally from 1996 to approximately 2003.  Python as a hobbyist for most of the past decade and semi-professionally for two years now.

> **whiteychs said:**
> I want a language that's functional and gets the job done and that will continue to be supported well into the future!

I'm dead set on learning Perl or Python - which is what's killing me.
Note: I'm more software oriented as opposed to sysadmin work, but I'd like a multipurpose language that is adept at both.

Both are equally adept at this niche to a point.  Perl is a hair stronger on the sysadmin work while Python is better at the large-project general purpose software area.  However I don't see those two as being equal.  IE, the gains you get from Perl on the sysadmin side are smaller than the gains you get out of Python on the general purpose software side.  

> ** The forced white space and lack of C based braces and semicolons are kind of off putting and makes it seem almost "kiddy" to me. What are your thoughts on this? I realize it makes code easier to read, but at what price?The price?  Easier to **write** code.  Seriously.  This isn't just easier to read but easier to write.  Most people who hear about significant white space feel that they are constrained on the structure of their code.  Fact of the matter is that Python is quite sensible in where significant white space is required.

Sensible in that if you're identing your code properly in the first place then you will have no problems identing code in Python.

Sensible also in that Python is smart enough to know that there are places you might want a tad more freedom on your spaces and makes allowances for those cases.  Opening braces, parens and quotes lift the whitespace requirement while closing braces, parens and quotes put it back in place.

[php]
def spam(a_long, list_of,           # Note whitespace matters here for the def
         variables, spread, across, # but not here for the variables
         three,lines):              # nor here because they are inside parens
    if a_long > list_of:                            # indention needed here but you
        do_something_here(variables, across, lines) # would indent these anyway.
[/php][php]
spamdict = { key_a : "Value A", # This line would have to be indented if part of a block
             key_b : "Value B", # this one is lined up with the key_a portion above
             key_c : "Value C"  # and Python doesn't care since it is in braces.

}
[/php]IE, Python enforces whitespace where you should (and often are) using it anyway and does not enforce it where you often break indention rules for other purposes.  The end result is no need for block delimiters and semicolons and thus code that is easier to write because you're formatting it once for programmer and computer instead of once for the programmer (indention) and a different way for the computer (braces).

> Perl **appears** to be a much more mature language. Perl is much different than what I'm used to in syntax and thinking patterns, but is that a bad thing?In general, no.  But the caveat there is provided that the language is consistent in how it goes about things.  Perl revels in the fact it is inconsistent.  It has 4 ways to do a simple if statement, 3 of which are bad for maintainabilty.  BTW, it is this case which is why I no longer program Perl and switched off to Python.

> I think Perl has a better lesson to teach me about different ways to program, but that comes at a steep learning curve and an uncertain future - namely Perl 6 and how it will be received.I don't believe that is the case.  At least not when comparing Perl to Python.  IE, any programming patterns you would find in Perl either are present in Python or aren't present for good reason.  ;)

> So I guess what I'm asking is: Which has the best future? I believe, Perl is at the moment more employable (??), but will that change?I think it has changed.  The metric I watch for this is Ohloh.net's language comparison tool.  The caveat being that Ohloh is only tracking open source projects which use CVS or SVN repositories.  IE, it's a fair barometric of how much languages are getting used but not a direct measure across all FOSS projects nor closed source projects.

[Here's the chart for Python, Perl, PHP and Ruby]("http://www.ohloh.net/languages/compare?commit=Update&l0=python&l1=perl&l2=php&l3=ruby&l4=-1&measure=contributors&percent="). Note that Ruby on Rails provided a good level of employability but at no time has Ruby's popularity in the FOSS arena surpassed Python's.  Also note that when I was employed professionally as a Perl hacker Perl enjoyed 4.5% to 5% usage of projects in repositories.  It has since slipped to a hair over 2%.  Meanwhile Python and PHP have both surpassed Perl and gone on to greater heights.  If you flip over to values instead of percentages you'll see that the number of projects for Perl has clearly grown in the past decade but Python and PHP both surpass Perl by a wide margin.  So if we can draw a nominal corrilation between percentage of FOSS projects using these languages (or absolute number) and employability then Python comes out way on top.  Of course that corrilation is a topic of a different debate.  ;)

Also note that Perl, percentage wise, has been declining for about 5 years now.  Ruby peaked and is declining.  PHP and Python are still increasing.  So if you're worried about future proofing your choice that might suggest learning Python over Perl.

> With Python's corporate backing and Perl 6 close to vaporware, would my time best be spent learning Python? Will Perl 6 be a home-run with its vast improvements? Also consider i want a more general purpose language that allows me to hack up quick progs.

I have made my choice.  That choice is Python.  I believe that between the two languages, Python is the better choice for people who are considering a start in one or the other.  I can go on at length on why I prefer Python over Perl but the "Why I love/hate" topics for both Python and Perl cover than quite enough.  But at the same time it is clear I am biased precisely because I have made my choice.  The best I can do is assuage any concerns you might have about Python or address misconceptions about the language.  But in the end the choice does rest with you.

---

### Post by whiteychs on 2009-01-04
I want to thank everyone who responded.  I read each post and found that they all were very relevant to my interests and aided my decision.

I've decided to progress with Python for now. I wouldn't call myself a 'Pythonista' just yet, but I'm certainly willing to give it my all.

As stated in the responses, Python is very orderly. I'm positive that Python's clean syntax and uniform ways will help me understand programming on a deeper level than I ever could have with Perl.

That said, I'll be sure to keep an eye out on Perl 6 and maybe add it to my toolbox at a later time.

Thanks again!

Edit:
As a first time poster, I feel obliged to say that I'm impressed with the community here. Top notch. :)

---

