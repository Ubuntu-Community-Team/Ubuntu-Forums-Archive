---
title: "Assembly and Linux"
date: 2009-07-28
forum: Programming Talk
---

### Post by EagerNewbie on 2009-07-28
Hi, I am 15 years old and a complete newbie to programming, etc.  My goal is to become a great programmer / hacker.  I got inspired after watching movies like Wargames, sneakers, and Hackers.  I REALLY want to do this but I don't really know where to start.  I mean, I know that I should just start anywhere... But what would be "thee" place to start.

This question brought me to this book:

"Programming from the Ground Up" By Jonathan Bartlett

Have you read it, do you think it's a good idea?

The thing is, I don't want to start something that will end up being a waste in the long run.  So, any recommendations, opinions, tips, strategies, etc... Are all welcome.

Thanks for the help, I need it!

---

### Post by credobyte on 2009-07-28
Thread title differs from what you are asking, so .. Assembly and Linux: [http://asm.sourceforge.net/](http://asm.sourceforge.net/)

---

### Post by sam191 on 2009-07-28
My friend... I was just in the exact same position not too long ago ;)

Read this:

[http://lambdagrok.wikidot.com/forum/t-172028/python-a-toy-language]("http://lambdagrok.wikidot.com/forum/t-172028/python-a-toy-language")

And here is the tutorial I am doing, it is very good:

[http://homepage.mac.com/s_lott/books/nonprog/htmlchunks/index.html]("http://homepage.mac.com/s_lott/books/nonprog/htmlchunks/index.html")

Since I am too a beginner, this is all I can tell you :)

Others who are far more experienced can give you some great advice, but the above is what I recommend. 

Good luck ;)

---

### Post by Simian Man on 2009-07-28
[LIST=1]
[*]Read [this]("http://catb.org/~esr/faqs/hacker-howto.html")
[*]Learn Python
[*]Write programs you find interesting
[*]Stay away from assembly for a long, long time (if not forever)
[/LIST]

---

### Post by EagerNewbie on 2009-07-28
To everyone, thanks for all the help!

Question...

...Why is it wrong for a newbie to learn Assembly?  Some say it's a good idea.  Why is it a bad idea?  Please, I need more info.

---

### Post by OutOfReach on 2009-07-28
> **EagerNewbie said:**
> To everyone, thanks for all the help!

Question...

...Why is it wrong for a newbie to learn Assembly?  Some say it's a good idea.  Why is it a bad idea?  Please, I need more info.
Well, in Assembly you basically have to deal with almost everything yourself, memory management, etc etc. and if you don't have any previous programming experience there might be some concepts that you may not understand. I think it would be better to learn a higher level language (such as Python). No one really programs desktop applications in Assembly these days.

---

### Post by CptPicard on 2009-07-28
Another take on assembly can also be that it's actually so basic as to not really tell you much anything about programming as it is generally done. It's just manipulation of stuff in a limited number of registers using basic set really rudimentary commands, plus shoving stuff between those registers and RAM, plus messing with the stack. This produces lots of work, with little enlightenment.

In particular anybody who believes that that is, for a beginner, a way to learn programming "from the ground up" and that a beginner would become good at constructing program abstractions (which the language itself in no way suggests) out of nothing, has lost some of his marbles...

However, at some point it becomes beneficial to understand how it works, so you can read compiler output and perhaps manipulate it at critical points. This is how it works for me; I've never really written more than a few inline asm routines in C myself, and this was in the 90s...

---

### Post by JordyD on 2009-07-28
It's not fun, either. That's my main purpose, so I avoid it.

---

### Post by anzac1942 on 2009-07-28
I've just started learning Assembly myself, and I'm 16. It isn't proving to be too hard so far, but I've only seen the tip of the iceburg.  However, having previous programming experience, I would definitely recommend that you start with a higher level language. You don't necessarily have to start with python, although it is a good starting place. For example, C++ was my first language, which I also found to be a good starting point. If you really want to continue pursuing assembly right now, I would recommend this book: [http://reversengineering.wordpress.com/2008/05/15/professional-assembly-language/ ]("http://reversengineering.wordpress.com/2008/05/15/professional-assembly-language/")

This is the book I've been using to learn from, and I've found it quite helpful. No matter what you decide to learn though, good luck with it!

---

### Post by JordyD on 2009-07-28
> **anzac1942 said:**
> I've just started learning Assembly myself, and I'm 16. It isn't proving to be too hard so far, but I've only seen the tip of the iceburg.  However, having previous programming experience, I would definitely recommend that you start with a higher level language. You don't necessarily have to start with python, although it is a good starting place. For example, C++ was my first language, which I also found to be a good starting point. If you really want to continue pursuing assembly right now, I would recommend this book: [http://reversengineering.wordpress.com/2008/05/15/professional-assembly-language/ ]("http://reversengineering.wordpress.com/2008/05/15/professional-assembly-language/")

This is the book I've been using to learn from, and I've found it quite helpful. No matter what you decide to learn though, good luck with it!

I've heard it's not too hard. But still, I don't think it's *fun*. Regardless, others might, so I'd say if you think it may be fun, or it's important to you, go for it.

---

### Post by Cyanidepoison on 2009-07-28
Assembly is not the way to start programming.

Assembly is only particularly useful in odd cases of extreme optimization and in reverse engineering.  Everything else could be written in another language and the effort to results ratio would be a lot better.

I do a bit of reverse engineering, so I know a good deal of both x86 assembly and ARM assembly.  I never actually need the speed factor that assembly provides (which is becoming less and less needed as C compilers become better and machines become faster), so writing assembly is pretty much useless to me.

Learning the instruction set for a new architecture is fun and all, but it isn't practical and you probably will never use it again.

---

### Post by soltanis on 2009-07-29
Assembly is the farthest thing from hard; Actually, I find it the easiest thing to understand, theoretically speaking, because its basically a description of what the 'metal' is doing.

At the same time, there are simply no abstractions in assembly code. Everything is done by hand -- and almost no one writes applications in it.

If you are interested in the hacker mentality I can understand why you'd want to learn it. Assembly programming is vital in some aspects of subverting programs; especially in reverse engineering, decompiling, stack smashing + remote code execution, etc.

If you are really interested in learning about what's going on while retaining some sanity, I suggest you learn C. It's close enough to the metal where you gain some of that understanding, but also abstracts enough of it for you to really learn about the essence of programming.

If you are going to write applications, I suggest python or another high-level language, and come back to C later.

---

### Post by aesis05401 on 2009-07-29
Hrm.. So a kiddo asks for hacking advice and we make it to page 2 without anyone mentioning 2600?  

Always remember a hacker does not need a computer to hack - just a brain.  And BTW, those movies have a special place in many hearts, but mostly because they can be good for a laugh ;)

Learning how to question in both insightful and quiet ways takes restraint... So clear any hacking materials with your legal guardian before bringing them into your house.  If there is resistance, then prove to everyone involved that you are going to be an adult about pursuing your passion and be patient.  Instead of breaking any rules in your household show that you can bide your time in a responsible manner.  This will be important later in life when you realize you can do things that other people cannot - or things that you do not believe other people will find out about.  It is much easier to make bad decisions when you have already disappointed everyone who trusted you - so don't start out on a bad foot !

With 2600 it is usually easy to get parent approval - just let the parent or legal guardian read some of Emmanuel's editorials from the front of an issue.  They are typically of the very responsible sort.

Edit: I should mention I own all the movies you mentioned - in case you found my previous statement demeaning :)

---

### Post by lisati on 2009-07-29
> **Cyanidepoison said:**
> Assembly is not the way to start programming

I agree. Although it can be fun and interesting to learn assembly, and occasionally useful, it often requires a more intimate knowledge of the workings of the computer system(s) you'll be writing for than is absolutely necessary. 

For everyday programming, a higher-level programming language is usually sufficient. A number of languages seem to be popular here at the forums: these include C, C++, and Python.

---

### Post by MythAaron on 2009-07-29
> **aesis05401 said:**
> Hrm.. So a kiddo asks for hacking advice and we make it to page 2 without anyone mentioning 2600?
That is the problem with using the them "hacker."  It has those 2 definitions that are of equal weight.  I hope EagerNewbie means "hacker" in the generic way as opposed to the sinister one.

I messed around with assembly when I was 15, but that was back when 64K of memory was impressive and assembly made sense.  After all, it was either assembly or peeking and poking with Commodore BASIC V2.  :)

Now, I'm getting back into programming and am enjoying being the the gray area between beginner and intermediate on Python (I can write list comprehensions and map statements now, yippie!).

---

### Post by shadylookin on 2009-07-29
I don't really think assembly would be a good starting point. Humans tend to think at higher levels so I would start with a high level language. In my experience people can wrap their minds around objects better than bytes. I can also assure you despite some people's misconceptions using assembly will not make you more manly than if you used python, ruby, java, c#, or any other high level language.

---

### Post by aesis05401 on 2009-07-29
> **MythAaron said:**
> That is the problem with using the them "hacker."  It has those 2 definitions that are of equal weight.  I hope EagerNewbie means "hacker" in the generic way as opposed to the sinister one.


This is a good point.  

Of course, for all we know the two definitions of hacker that EagerNewbie is pondering are: 

"hacker" in the Angelina-Jolie-is-gonna-think-I'm-hot way; 
"hacker" in the Ally-Sheedy-is-not-a-bad-backup-plan-in-case-things-don't-work-out-with-Angelina way.

;)

---

### Post by EagerNewbie on 2009-07-29
Fine, I've decided not to start out with ASM.  My plan:  C++, Linux OS (how it works, commands, etc), and then, maybe, ASM.  Anyway, that's my plan for now.  

Isn't "some" real life hacking like the movies?  So far, that's the only thing motivating me.  None of my friends program.

By the way, I really appreciate all this help.  Thank you!

---

### Post by JordyD on 2009-07-29
> **EagerNewbie said:**
> Fine, I've decided not to start out with ASM.  My plan:  C++, Linux OS (how it works, commands, etc), and then, maybe, ASM.  Anyway, that's my plan for now.  

Isn't "some" real life hacking like the movies?  So far, that's the only thing motivating me.  None of my friends program.

By the way, I really appreciate all this help.  Thank you!

Well, hacking in the 'open source programming' sense is not quite as exciting as the movies. Hacking in the other sense is not something I have experience with.

---

### Post by lisati on 2009-07-29
> **EagerNewbie said:**
> Isn't "some" real life hacking like the movies?  So far, that's the only thing motivating me.  None of my friends program.

"Hacking" as presented in the movies doesn't always match up with reality too well. Take, for example, the scene in "[Ferris Bueller's Day Off]("http://www.imdb.com/title/tt0091042/")" where he dials into the schools computer to change his grades. It's unlikely that he would have been able to do that, because at the time the movie was made, the school's computer system is likely to have been a stand-alone system, self-contained locally - the internet as we know it today didn't exist.

---

### Post by MindSz on 2009-07-29
About the starting point I think C++ is a nice way to start. You can find tons of material to help you with it.

As for "hacking" like they do in the movies ... well, not so much.

You can start out trying to become proficient at programming and then see where you want to go with it. 

I hope that once you start programming you find, as I have, that creating new stuff (or just doing some cool stuff in the computer) with your code can be awesome as long as you're having fun with it.

I believe I started out thinking like you, but I stopped half-way there and thought "I think this is where I want to be" ... no Angelina tho, but wifey would tell you she's 10 times better ;)

Good luck with programming and HAVE FUN!!

---

### Post by CptPicard on 2009-07-29
> **EagerNewbie said:**
> 
Isn't "some" real life hacking like the movies?  So far, that's the only thing motivating me.

No, it's not like the movies, sorry. :) If that's your only motivation, I really doubt you'll be into this :D

---

### Post by soltanis on 2009-07-29
It is like the Matrix though. Well, kind of. Actually, only in that part from Reloaded where Trinity roots the city power grid computers using nmap and the SSH1 CRC exploit.

That sequence takes up a glorious 3 seconds of the movie.

Most hacking in real life (hacking as in exploiting programs) is sitting there, pondering how a program works, trying to figure things out.

Look up the hacker war game called 'semtex'. If you are really interested in this kind of work (and it is work -- it's called security auditing, not rooting people's boxes for fun/profit) you should look it up. _After_ you have learned basic programming skills, which you will need if you want to get anywhere in those challenges.

PS -- It'll also teach you a thing or two about assembly.

PSS -- I hope I need not mention how illegal it is to break into computers without permission, and I really hope that I need not insert this entire disclaimer, but let me put it this way -- learning this kind of stuff is like learning to pick locks. You could either use that knowledge as a locksmith to build a better lock, or you could use that knowledge to do all sorts of not-lawful things, get yourself in trouble, then make the computer-savvy community look bad in general. If you can't figure out which one of those things is ethically correct, don't bother going any further.

---

### Post by lisati on 2009-07-29
> **CptPicard said:**
> No, it's not like the movies, sorry. :) If that's your only motivation, I really doubt you'll be into this :D

I concur that Hollywood's version of "hacking" doesn't match up with reality too well. The movie makers often take some liberties in the interests of crafting a story that people will pay money to see. It can be fun, however, watching such stories and looking out for bloopers.

---

### Post by aesis05401 on 2009-07-29
EagerNewbie:

If your hacking career is exciting you are doing it wrong.  Insight and foresight go hand in hand ;)

And on another note - the most important part of owning a lock-pick is knowing who knows you have a lock-pick.  Same goes for any weapon or knowledge.  

Finally, the moments most like a Hollywood movie are usually social moments.  As you get older you will find that there are actually meeting places for hacking communities all over the place including the standard 2600 meetings, parties organized by freetekno people, etc.. 

Be sure you have your head on straight about the type of *human* you want to be *before* you start going to functions to learn more about being a hacker.

In the meantime, it is not all screen after screen of code.  Get yourself a book or two on reading body language and go down to the local mall or hangout.  Find yourself an out of the way place and people watch for a while.  You will be amazed at the things you will pick up on after a few sessions.

---

### Post by mmix on 2009-07-29
learn mmix or simple 8-bit and 16-bit asm emulator or yasm.

[http://www-cs-faculty.stanford.edu/~knuth/mmix.html](http://www-cs-faculty.stanford.edu/~knuth/mmix.html)
[http://www.tortall.net/projects/yasm/](http://www.tortall.net/projects/yasm/)

[http://www.dcemu.co.uk/vbulletin/showthread.php?t=17984](http://www.dcemu.co.uk/vbulletin/showthread.php?t=17984)

HTH

---

### Post by shadylookin on 2009-07-29
> **EagerNewbie said:**
> Fine, I've decided not to start out with ASM.  My plan:  C++, Linux OS (how it works, commands, etc), and then, maybe, ASM.  Anyway, that's my plan for now.  

Isn't "some" real life hacking like the movies?  So far, that's the only thing motivating me.  None of my friends program.

Well first you should ask yourself is anything like it is in the movies? No of course it isn't because no one would pay 8 dollars to go see 2 hours of mundane normal life. 

If you're planning on being a hacker as in breaking into computer systems I would encourage you to drop these ambitions.

---

### Post by Cyanidepoison on 2009-07-29
Look at it this way:

Hacking in the movies is like trying to break into a Windows 98 box without a firewall.  It takes a couple of minutes at most.

Hacking in real life is staring at IDA for hours on end until you can reconstruct it all in your head enough to take an action upon the knowledge.

*This is talking about hacking outside the realm of hacking in the programming sense, the gray-area stuff.  My experience comes from the iPhone world.

---

### Post by Nemooo on 2009-07-30
I don't know whether I should post this link or not. The site's fine legally and is perhaps more what you seek. Try browsing a little around.

[http://hackthissite.org/](http://hackthissite.org/)

---

### Post by asbuntu on 2009-08-03
Interesting thread - hacking and assembly code - hmmmm...

As I recall, a hacker was a person that took the time to learn how the computer worked at a very fundamental level.  Typically, he/she built the computer from scratch, wrote the monitor program, and played with some LED's or whatnot.  No floppy.  No hard drive.  No terminal.  Best you could hope for was a serial cassette or eight track interface.  (Actually, best you can hope for is to die in your sleep -- oops, isn't that in a song by someone???)   :-)>

This definition of "hacker" is a very good designation, as opposed to the evil connotation associated with the term today.  I equate it with someone that knows how things work.  (Sounds like an engineer, doesn't it?)

While we are talking about assembly code, one poster noted the desire to get down to bare metal and understand things.  Wonderful.  How about machine code??????  Don't even bother with assembly code.  Besides, in the beginning there was only the console with some switches and some lights...

---

