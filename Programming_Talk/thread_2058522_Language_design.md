---
title: "Language design"
date: 2012-09-15
forum: Programming Talk
---

### Post by Mikeb85 on 2012-09-15
So I'm pretty much a newb when it comes to programming (although I've always followed tech and have been around Linux for years), but I'm curious about something from the pros here.  

Do you guys believe it is possible to have a 'best' multipurpose language, is there 1 you spend most of your time using?  Do you believe languages are **inherently** limited, or limited only by usage and libraries?  

Also, if you do use multiple languages for various purposes, how many and for what?  

And note - I don't mean this thread to be a this vs. that thread, but rather a discussion about the nature of programming languages.  And if the question is silly tell me too, but no versus arguing...

---

### Post by josephmills on 2012-09-15
I use C++/QT A lot now-a-days it seems I am moving more and more away from python and C, I also Use a lot of QML which need's Javascript, and also because I do some web-based stuff with qml a lot api work as of the late also. 

In my spare time I am trying to learn D and GO better then I know them

---

### Post by satsujinka on 2012-09-16
I usually reach for Go or Haskell first. Lately, it's been Go for most things, but I really like Gtk2hs so I use Haskell whenever I'm doing GUI work.

I also occasionally write C...but Go's taken over that role for the most part.

---

### Post by Wybiral on 2012-09-16
I don't know about "best", I feel that's far-fetched. Higher level data abstractions lead to a distance from the direct communication with the machine (and theoretically less efficient performance). But overly machine-dependent languages lead to a distance from the natural human representation of the problem.

I think it boils down to what your intentions are. I use C for machine level numerical stuff. Python for abstracted "human-level" stuff. And Javascript when I need a web interface. Which is another issue...

Personally, I'd prefer a Python syntax for web development (even if the standard library were stunted) but since Javascript is so widely adopted, I deal with it for the ease of distribution...

So, the "optimal" language would need to be abstracted, but only when needed, high level, but capable of machine-level control when needed, and widely adopted. And then comes the linguistic needs of terseness, simplicity, and the concept of it being obvious how to say what you want to say... And then accept the fact that new academic branched will want to say something in their own way...

All of that considered, I'm probably better off learning a few languages. The best skill a programmer can acquire (beyond rudimentary computer science skills) is the ability to adopt new languages.

---

### Post by Scott Harrison on 2012-09-16
> **Wybiral said:**
> I think it boils down to what your intentions are. I use C for machine level numerical stuff. Python for abstracted "human-level" stuff. And Javascript when I need a web interface. Which is another issue...
Exactly this^.

Different languages have different uses and perform different tasks. I don't think any can be named the "ultimate" language, as each have their own strengths and weaknesses. Take each as it comes and be able to adapt to different languages, to further expand your skills as a programmer.

---

### Post by CptPicard on 2012-09-16
> And if the question is silly tell me too, but no versus arguing...

You have no idea how not-silly this question is, it has probably been the most heatedly argued issue here during my roughly six years of partipating in the forum.

It usually starts from the "what programming language should I start with" and after that people start debating the relative merits of learning one language first, which then determines the learning curve to other languages. This is the first time this question gets asked so directly for what it is though.

There are various schools of thought to this, but generally it seems like it boils down to the high-level vs. low-level language crowd.

> **Mikeb85 said:**
> 
Do you guys believe it is possible to have a 'best' multipurpose language, is there 1 you spend most of your time using?

While in practise I of course use which language fits the actual problem best, in a more theoretical sense I do believe that there are at least "better" multipurpose languages than others. It is easy to see that this kind of an ordering exists; after all, we have the languages in common usage and then we have esoteric joke languages like Malbolge, that are intended to be impossible to use. Yet you could use them to write anything, as they are Turing-complete.

I am a big Lisp proponent for this theoretically-best general purpose language: it consists of a small core set of powerful language features, that when put together, let you "write any other language" with relatively little effort. This means that as far as language design goes in making a language better, Lisp occupies a nice, generic middle ground from where it is easy to move conceptually into other directions.

Mind you, this completely ignores any problem-specific considerations; some low-level programming fan would say that C is the ultimate general purpose programming language because it is closer to the hardware in needed and always faster. But in a language design sense, C is rather trivially included in Lisp if you want to write "C-like code".

> Do you believe languages are **inherently** limited, or limited only by usage and libraries?

I think we should always separate libraries from this discussion... the interesting part here are core language features. Libraries can always be written, and this "library" can be a whole interpreter for some other language. If core language features are expressive, writing libraries is easy; but by writing libraries you can't get new core language features -- if you did, it would no longer be the same language you are processing with your library.

Turing-complete languages are not inherently limited (in the abstract), but for humans we certainly want certain kinds of languages preferably to a raw stream of bits.

---

### Post by trent.josephsen on 2012-09-16
> **CptPicard said:**
> <lots of smart things>
Welp, nothing to do here...

---

### Post by Wybiral on 2012-09-17
CptPicard, you surely have a way with words in these issues. I agree that this is a central issue brought up in this forum, but expressed in a more rational way than has been usual for the past few years. Also, my current stance is jaded by a need to implement things outside of my control of the language.

I love lisp and find it less work to implement a solution to most problems in. Unfortunately when it hits the bottleneck of needing to implement it for X system, I find translating it to whatever language X uses to be extra work compared to writing it in X to begin with. But I do strongly agree that my internal representation is MUCH closer to lisp than what X uses.

---

### Post by CptPicard on 2012-09-18
> **Wybiral said:**
> CptPicard, you surely have a way with words in these issues.

As you always have had as well. :) It's just a result of revisiting the issue over and over again for a long time; see how the post is actually mercifully short and to the point this time ;)

> 
I love lisp and find it less work to implement a solution to most problems in. Unfortunately when it hits the bottleneck of needing to implement it for X system, I find translating it to whatever language X uses to be extra work compared to writing it in X to begin with.

Yes, this is the "horses for courses" view, and it is just a fundamentally different issue than what I have in mind. I am an Enterprise Java monkey at work these days, so certainly when dealing with JavaEE, you write in Java. Of course the low-level guys add to this the idea that being closer to the hardware has a privileged position... but in any case when considering programming languages from their design perspective, pretty much all considerations like this need to be excluded, although of course in reality, they are relevant.

---

### Post by ibuclaw on 2012-09-18
> **Wybiral said:**
> Also, my current stance is jaded by a need to implement things outside of my control of the language.

Or if you're like me, you go off on a tangent and write your own language. :)

If you are interested in language design, go off and get friendly with communities around developing languages. I would be biased to name D and Rust, though there's a wealth to pick from.

---

### Post by satsujinka on 2012-09-18
I keep meaning to relearn a lisp (MIT Scheme was my first functional language,) but I just never get around to it. Part of it is because I have so many other things I want to do and part of it is that I'm just not sure what there is to offer.

I mean, I know Haskell (and love it) so what would lisp add to that? Macros? I mean it's not like I didn't like Scheme, I just don't know what problems lisp would solve for me (especially, considering I learned one once and it didn't really stick.)

---

### Post by Wybiral on 2012-09-19
Yes, linguistically, if you've already tackled functional programming in Haskell, learning the magic of macros and the fusion of code and data would still be useful. The notion that an addition is just a cons-list of the plus function and two other syntax trees is a useful concept to grasp. Understanding how it all unwinds and how it can be manipulated before it unwinds... Definitely worth the experience IMO.

---

### Post by satsujinka on 2012-09-19
> **Wybiral said:**
> Yes, linguistically, if you've already tackled functional programming in Haskell, learning the magic of macros and the fusion of code and data would still be useful. The notion that an addition is just a cons-list of the plus function and two other syntax trees is a useful concept to grasp. Understanding how it all unwinds and how it can be manipulated before it unwinds... Definitely worth the experience IMO.
Which still doesn't answer the question of what it does for me.

I can read S-expr. just fine. I understand reflection. As far as I can tell, lisp macros are really the sole defining feature that I'm missing. The problem is that I don't know what I'd do with them.

---

### Post by spjackson on 2012-09-19
> **satsujinka said:**
> Which still doesn't answer the question of what it does for me.

I can read S-expr. just fine. I understand reflection. As far as I can tell, lisp macros are really the sole defining feature that I'm missing. The problem is that I don't know what I'd do with them.
I wouldn't normally take part in a "my language is better than yours" type of debate, but if you did want to try a Lisp again, I would recommend [Clojure]("http://clojure.org/"). The few paragraphs on the home page describe what it gives you. There's rather more detail in the [Rationale]("http://clojure.org/rationale"). If you want great detail, then there's [The Joy of Clojure]("http://www.manning.com/fogus/"). A few of Rich Hickey's video talks sit somewhere in between.

---

### Post by Mikeb85 on 2012-09-19
Thanks for all the replies (and continue the discussion).  Definitely some cool stuff in this thread, some languages I haven't heard much about.  

Part of my reason for starting this thread is that I started learning Ruby, love it, but there's a lot of people who associate it solely with Rails and web development.  Part of my reason for learning to program is to create my own scripts to help me sort through equities listed on various stock markets - which would involve data mining, charting and predictive analysis - from what I hear R language is perfect for this, so I started to learn it as well (but it's not as much fun as Ruby).  I do know that both languages CAN do what I need, but 1 is geared more towards that task (R), and the other seems a bit more expressive and general purpose (Ruby).  

So I guess part of my personal dilemma is whether to keep at Ruby (which I do enjoy), or switch to R (which most people would agree is a little more useful for what I want to do).  Of course I could use R bindings in Ruby, which I may very well do, but that does complicate things slightly.  Decisions...  

And of course part of the dilemma is that most languages are turing complete, but with obvious biases, hence my original question.  One interesting little thing I came across is that IBM's Watson uses alot of Prolog, a language I'd never heard of, apparently one of the first computer languages...  I've always been fascinated by these things, only recently have I become interested in actually messing with them.

---

### Post by Wybiral on 2012-09-19
If all you want to do is data analysis, statistics, and plotting, then R or Octave/Matlab are better equipped. Ruby has libraries to do all of those things, but it will be clunkier than R or Octave (where the languages themselves were designed for those needs).

I'm not saying don't learn Ruby... I'm saying learn R or Octave if all you want to do is analysis. But you should learn Ruby just to familiarize yourself with another tool.

---

### Post by mevun on 2012-09-19
People talk about using the language (with its libraries) that make sense.  As you (Mikeb85) mentioned, there are often cross-language interfaces.  Sometimes they are very good/complete and sometimes they are limited because the two languages are too different.  You can always write your own "interface" which could be just a file if that is sufficient rather than trying to do actual language binding/invocation.

It is hard to predict how much time would be spent on development using language A, language B, both languages with an interface, etc.  If your goal is not necessarily fastest implementation time, then just pick what interests you in terms of learning.

I  don't know either R or ruby, but obviously RoR will help you create a  web-based GUI.  Once you add a web interface, you can use javascript as well.  There are some very nice javascript graphing libraries that can provide interactive charts which you may ultimately want.  Or maybe not.

---

### Post by satsujinka on 2012-09-19
@Mikeb85
I feel that you should use what's best suited for the task at hand. For what you describe that should be R. If later you find that you're doing multiple things, some of which R is good at and some it's not, then look into writing those sections R isn't good at in a different language.

@spjackson
I think you've misunderstood. I **like** lisp. I **want** to relearn one.

The issue is motivation. I don't know what lisp would make significantly easier.

That said, Clojure is not a possibility. I don't have a jvm installed and I'm not going to install one. I do enough with Java at work that I really don't want anything to do with it at home.

---

### Post by Mikeb85 on 2012-09-19
> **Wybiral said:**
> If all you want to do is data analysis, statistics, and plotting, then R or Octave/Matlab are better equipped. Ruby has libraries to do all of those things, but it will be clunkier than R or Octave (where the languages themselves were designed for those needs).

I'm not saying don't learn Ruby... I'm saying learn R or Octave if all you want to do is analysis. But you should learn Ruby just to familiarize yourself with another tool.

I don't just want to do analysis, but I want the script to be able to make 'predictions' or at least sort the data a certain way so I can be alerted to certain stocks following certain patterns.  It seems to be do-able in R, I'm just not sure how that particular functionality compares to other languages.  I'm not too interested in analysis just for the sake of it, my stock broker's software can give me charts, financials, statistics, various ratios, etc...  

I did find a cool script in Ruby that uses the Nokogiri gem to download lists of every stock on a certain market, and sort them into a database, this is kind of what I'm going after.  I know R has a huge amount of libraries as well, but sorting through them seems a bit tougher - Github has a ton of Ruby resources, not too sure where to get the same kind of thing for R yet...  

For now I probably will look into both languages (R, Ruby,  and maybe a look at Octave), and try my best to evaluate how each suits my needs...  

It was a fun 'ah ha!' moment when I produced a stock chart on R the other day, until I realized that I could get the exact same thing off Yahoo's website...

---

### Post by Wybiral on 2012-09-19
R and Octave aren't typically used for long-running applications constantly polling data. They're most often used to explore a given dataset to find patterns or create charts / visuals.

R is closer to thinking about datasets and has lots of functionality for loading / saving data from various formats. It's more of a scientists tool.

Octave/Matlab can be used similarly, but they're more geared towards the mathematical side. Courses in machine learning usually use Octave/Matlab because they natively handle basic stats, linear algebra, and calculus.

Ruby would be more geared towards the automation process. It would be a more logical language to set up a server to dispatch the analysis / data mining algorithms at scheduled times and to create a summary of the current state (either web or local file).

---

### Post by Mikeb85 on 2012-09-20
> **Wybiral said:**
> R and Octave aren't typically used for long-running applications constantly polling data. They're most often used to explore a given dataset to find patterns or create charts / visuals.

R is closer to thinking about datasets and has lots of functionality for loading / saving data from various formats. It's more of a scientists tool.

Octave/Matlab can be used similarly, but they're more geared towards the mathematical side. Courses in machine learning usually use Octave/Matlab because they natively handle basic stats, linear algebra, and calculus.

Ruby would be more geared towards the automation process. It would be a more logical language to set up a server to dispatch the analysis / data mining algorithms at scheduled times and to create a summary of the current state (either web or local file).

Yeah, I was kind of thinking that about R, but it's nice to hear from someone else.

What you described is my end goal, I know it'll probably take me some time to get to that point, but I think with the available tools I can eventually get to that point.  

A pipe dream of mine would also be to mine data from Twitter, Reuters, etc..., and with some clever regex scripts try to gather news about various companies and incorporate that into my scripts (if the script could look for positive/negative connotations connected to various numbers that would be even better).  

For now I've got a few scripts to gather quotes that are fairly basic, but effective (and gather real-time quotes remarkably well - nice being able to quickly check on things from a console).

---

### Post by ofnuts on 2012-09-20
> **Mikeb85 said:**
> 
A pipe dream of mine would also be to mine data from Twitter, Reuters, etc..., and with some clever regex scripts try to gather news about various companies and incorporate that into my scripts (if the script could look for positive/negative connotations connected to various numbers that would be even better). 
I have worked with people doing just that... it requires a lot more than just "clever scripts" and regular expressions...

---

### Post by Mikeb85 on 2012-09-20
> **ofnuts said:**
> I have worked with people doing just that... it requires a lot more than just "clever scripts" and regular expressions...

I'm sure it does, hence the pipe dream stuff.  The difference between basic AI programs and IBM's Watson is hundreds of engineers and millions of lines of code, but it's the same basic idea.  

As of right now though, data mining and sorting through small amounts of data is feasible for me, this is just a fun project, maybe in 5-10 years I'll have something useful?  I've been making good money trading sorting through everything myself, so I'm in no hurry.

---

### Post by CptPicard on 2012-09-20
> **Mikeb85 said:**
> basic AI programs and IBM's Watson is hundreds of engineers and millions of lines of code, but it's the same basic idea.  

I would say it is the different, much deeper ideas that make AI programs actually work where clever scripts and regexps never could :p

---

### Post by Mikeb85 on 2012-09-20
> **CptPicard said:**
> I would say it is the different, much deeper ideas that make AI programs actually work where clever scripts and regexps never could :p

Hmmm, it seems to me as though most AI programs involve sorting data into databases, creating associations, searching through terms that come up, and then making decisions based on a statistic associated with said term.  Or am I completely off-base?  Alot of my understanding of AI comes from what I learned as a kid from my dad (a programmer), reading about/watching a piece on IBM's Watson, and basic game AI examples...  

So as a most basic example, if I wanted a program to tell me if I should invest in stock A or B, I'd get the program to pull say, a set of historical quotes for both from the internet, maybe tell me what the % change is over 30 days, and pick the higher one...  Or maybe calculate the number of up/down days over a period of time, and pick the stock with the highest probably of being up tomorrow (based on criteria)?  Like I said, very basic...

And then it seems as though slightly more complicated AI is based around creating 'rules', based on mathematical equations such as: [http://en.wikipedia.org/wiki/Bayesian_inference](http://en.wikipedia.org/wiki/Bayesian_inference)  

Is this how the basic principles of AI work, or am I missing something?

---

### Post by vexorian on 2012-09-20
AI has multiple definitions, but AI algorithms typically are stuff in which a programmer does not really think of the logic. So you would rarely be  inventing your own regex for searches (that would mean natural intelligence using a computer). With a neuronal network, associations are rather made automatically and just depend on the input you give to the system rather than your own tweaks. Genetic programming is supposed to create programs automatically. And so and so. So often, AI is about using canned systems of inference that already exist but you spend more time "training" them and tweaking them. In this regards, the simplicity in code is not different than grabbing your Java and making it use a regex class. You can grab your Java and make it use a neuronal network class. 

There are usually hybrid systems. Specially in games. Things like pathing may be the product of genetic algorithms but basic sequences of actions might be hard coded. Etc.

But either way, you'd be surprised at how simple it is to code your own neuronal network or genetic algorithm. The real problems lie in finding good applications and in having a lot of patience in performing the training.

> **Mikeb85 said:**
> So I'm pretty much a newb when it comes to programming (although I've always followed tech and have been around Linux for years), but I'm curious about something from the pros here.  

Do you guys believe it is possible to have a 'best' multipurpose language, is there 1 you spend most of your time using?  Do you believe languages are **inherently** limited, or limited only by usage and libraries?  

Also, if you do use multiple languages for various purposes, how many and for what?  

And note - I don't mean this thread to be a this vs. that thread, but rather a discussion about the nature of programming languages.  And if the question is silly tell me too, but no versus arguing...
A language can be used for everything. But if that's the case, then everything you do with the language will look messy and complicated. Hence why I like C++.

Otherwise, if you want a language that would do what you want but very cleanly, then it is better to go with more specialized languages.

---

### Post by mevun on 2012-09-20
> **Mikeb85 said:**
> 

A pipe dream of mine would also be to mine data from Twitter, Reuters, etc..., and with some clever regex scripts try to gather news about various companies and incorporate that into my scripts (if the script could look for positive/negative connotations connected to various numbers that would be even better).  



You don't have to write the data mining yourself.  There's a company called AlchemyAPI which has a web interfaces for doing some of that, including "sentiment analysis".  They do provide free "developer" accounts which allows you a limited rate of interface calls.  I assume they have competitors, but I haven't really searched for any.  (The company is located in my hometown and I have met people from there.)

Of course, hedge funds already do what you suggest.  We just don't know how successful they are at it and how much human intelligence is still involved.

---

