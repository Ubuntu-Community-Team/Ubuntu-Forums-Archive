---
title: "is it just me or linux is hostile to new developers?"
date: 2006-04-26
forum: Programming Talk
---

### Post by macxek on 2006-04-26
Before becoming slightly negative, perhaps I should start with saying that I've been using Ubuntu for a few months now and I love it. I also am the kind of person who like to see stuff work (especially free software) so I thought that being a (java) developer myself, giving a bit of my time to the open source community would be great.

So I started looking around, trying to find my way through and get started on something. After some time, I just thought to myself "what an hostile environment". All I see everywhere is RTFM, "if you want to start hacking then blah blah", etc.

I don't want to hack! I want to write software! I'm looking for a door that (it seems) doesn't exist. I've been looking around (not very hard though) on Launchpad for the so-called MOTUs and seen zippo. Where are the trainers that will help a newbie linux developer get started? I'm pretty sure I'm not the only one who feels lost, sitting alone in front of his computer with all the best intentions in the world but no help from the community...

I just wish there was a door where I could just knock and someone would answer and show me all the right directions. Perhaps it is time for a 'ubuntu dev coaching program'?

Any thoughts?

---

### Post by hagen00 on 2006-04-26
> Perhaps it is time for a 'ubuntu dev coaching program'?

Isn't that a bit broad? Dev in what? For what purpose, with what language. There are literally 1000 different options you have for developing in Linux. 

You say you want to learn java? Maybe not the answer you wanted to hear, but if you google "Java tutorial beginners" or something like that, you'll be sure to get some good stuff....What was your question again??

---

### Post by rejser on 2006-04-26
Find something you feel is missing, pick a language and get some books on the language an solve the problem. Upload it to sourceforge and maybe other have missed the same thing and download it

---

### Post by macxek on 2006-04-26
1) I've no intention to learn java since I have many years of experience in that language.

2) THAT is exactly what I'm talking about. I don't want to start sh*t, but you guys kind of confirm my impression: the answer I get all the time is "grab a book and get started by yourself".

I don't need to learn to program guys, I know how already. I just hoped someone would give me some advices to get started on a project and learn the things that are very specific to ubuntu and linux in general. Like, what are the libraries, what are they used for, what are the basic coding conventions, how to setup an IDE or whatever you guys use (in Java I use Eclipse, but CDT is very immature unfortunately...).

Anyway, I believe that many linux newbies could contribute if the path was easier to walk. I just hope that the linux world will get "less geeky" in the future so it can develop much faster.

---

### Post by nocturn on 2006-04-26
The thing I would recommend to you is find an area that you would like to participate in (like Gnome) and mail the development team.

The problem might be the language though, Java is not compatible with the GPL so it is not a language that is used very often.  If you join an existing project, chances are that it's going to be in C or Python.

---

### Post by Darkness3477 on 2006-04-26
I feel that out of the Linux Os's (And FreeBSD), that ubuntu is the least geekiest of them all. 

Everything about Ubuntu seems (to me, atleast) fairly easy as soon as you get you're head around a few things. Mostly using the Terminal for alot of things that Windows has a GUI for (Like installing stuff). 

As for java libraries...I only know a little bit about java (done a few tuts, and read a little bit of a book), so I cannot really help you. But I would think there are very similar libraries out there for Ubuntu as there is for Windows. Possible even better ones. Or perhaps the same, as Java is OS independant. 

Although, I do agree with you that it would be good for an online Ubuntu user group that is set up specifically for newbies. 
This forum is great for that kinda thing, but as so many people post and start new threads, a lot of the most simple ones get lost, and people like me (A reletively new person to Ubuntu) cannot find them. Maybe a board should be set up here specifcally to archive all the GOOD (As in topics and posts that would be seriously useful for a newbie) . Something like that would be very useful, rather then people asking the same sort of questions every couple of days or so. I would, at least, find it helpful.

Sorry if these seems blotchy, unorganised and that my grammar and spelling are off, but I just got home from drinking with some mates.

---

### Post by macxek on 2006-04-26
Thanks to all for your replies.

I agree totally that Ubuntu is the least geeky of all distros out there. Mark Shuttleworth and the community are working their *** real hard to make Ubuntu the best distro for the end-user.

I guess you're right and the best way to get started real quick is to get on the mailing list of a team...

As to Java, I know it's not the best option for linux because, like you said, it's not GPL'd. I got back into C/C++ lately on windows and expect to make the transition to linux soon, but I'm afraid the walk will be hard. Wish me luck!

---

### Post by sphinx on 2006-04-26
As a Java developer, I too have looked around for a project to contribute to. Although the path I took was to look for project that I felt strongly about, and improve it. Admittedly, I've yet to come across something I really like.

The trouble is, as was metioned above, Java isn't very common in the Linux realm due to (anal IMHO) legal issues. So an area that could use a helping hand is one of the projects aiming to provide an open source JVM implementation. As far as I know none of them are anywhere near Java 5 compatabillity. Not that I have looked recently.

So what are the free Java projects? Well I dont really know as I havent look into them for a while but the name 'Kaffe' rings a bell, as does 'classpath' from GNU. I know there are others, and at the risk of offending you, a quick web search should uncover more information on these projects and projects like these.

That way your helping Java become more popular in the Linux community and increase the choice of projects you can work on in the future.

I hope I've been helpful. Now at the risk of offending (more), personally it really gets my goat how people take offence to a suggestion of finding information for themselves. What on earth is wrong with receiving a suggestion to "grab a book and get started by yourself"? If you dont want to then fine, its only a suggestion.

By the way, I think your idea of a 'dev coaching program' is a fantastic one. It would certainly make joining in much easier. However, there is nothing like that currently. I too hope that such a program happens at some point, but untill then, I'll "grab a book and get started by myself" and make do without.

---

### Post by nocturn on 2006-04-26
[QUOTE=sphinx]As a Java developer, I too have looked around for a project to contribute to. Although the path I took was to look for project that I felt strongly about, and improve it. Admittedly, I've yet to come across something I really like.

The trouble is, as was metioned above, Java isn't very common in the Linux realm due to (anal IMHO) legal issues. 
[/QUOTE]

The legal issues are very serious.  If you distribute the non-free Sun JVM, you have to agree not to ship any alternatives, which is very restrictive.

Currently, the best bet for Java on Linux is the GNU Java Compiler (GJC).  But I really wish Sun would open up theirs.

---

### Post by sphinx on 2006-04-26
[QUOTE=nocturn].... not to ship any alternatives ...[/QUOTE]

I stand corrected. Not so anal legal issues.

---

### Post by macxek on 2006-04-26
Thanks Sphinx for your reply. And don't worry about it, I need more to be offended :) 

I don't think that contributing to an alternate JVM would help the community that much though... Although Sun's JVM isn't open source, it's still free, and all the best tools for Java also are.

What I'd really like to do is work on a C/C++ project for linux that is *at least* slightly organized and is run by a cool team that won't ask you to RTFM on every question. So far I read a few tutorials including the Debian Maintainer Guide, and to be honest I still don't know where to start!

I believe there are many people out there that know how to program and could help but, like me, are looking for an easy path to get started and just don't find anything so they give up. What a waste of potential manpower!

---

### Post by lnostdal on 2006-04-26
i think you need to figure out what you really want to do for _yourself_ ..   what do _you_ need?   (no, not from others .. but from your computer and its software)

if you do you need help from others getting started with coding; a book _is_ the best resource..  they are written by people who make a living out of helping others getting started, right? and they contain more information than could ever be put into a forum or an irc-conversation

if you feel you're having a hard time getting "into" a project, do this: 
* download the source-code from cvs (or svn, darcs or whatever) and compile and run to make sure you're working on the latest version

* join a mailinglist .. and check out the bug- and missing features-list (both often in the same tool) ..    

* communicate: "hello - i'd like to add feature or fix bug X, is anyone currently working on this?"

now, if you combine these things; there is nothing stopping you! :D

relations between people build from there on based on common needs and dependencies between goals in the project

that is the key to Open Source IMHO ..  because even if "everyone" do it because they need the thing/feature themselves - they share the code for others to use and improve ..   this way, everyone wins - and the quality improves because you wouldn't want to use something if it sucks

hey, ubuntu is fixing bug #1 ( [https://launchpad.net/distros/ubuntu/+bug/1](https://launchpad.net/distros/ubuntu/+bug/1) ) right now - isn't this great?

edit:
oh, and if you're starting your own project: you've got to prepare to work alone for a looong time most likely; before people start using it - that is, before people that can program like you start using it

---

### Post by LordHunter317 on 2006-04-26
[QUOTE=macxek]So I started looking around, trying to find my way through and get started on something. After some time, I just thought to myself "what an hostile environment". All I see everywhere is RTFM, "if you want to start hacking then blah blah", etc.[/quote]You're looking in the wrong places then.

> I don't want to hack! I want to write software! I'm looking for a door that (it seems) doesn't exist. I've been looking around (not very hard though) on Launchpad for the so-called MOTUs and seen zippo. Where are the trainers that will help a newbie linux developer get started?Uhh, here, but you're not a Linux developer, you're a Java one, which is a totally different world.
> I just hoped someone would give me some advices to get started on a projectIn Java?  I don't know any of value for Linux or Ubuntu.

> and learn the things that are very specific to ubuntu and linux in general.That's rather contradictory to your current language choice, which is probably why you're encountering such resistance.  Java is its own special world.

> Like, what are the libraries, what are they used for, what are the basic coding conventions, how to setup an IDE or whatever you guys use (in Java I use Eclipse, but CDT is very immature unfortunately...).None of those are relevant to a Java programmer, though.  Not a one.

[quote=nocturn]The problem might be the language though, Java is not compatible with the GPL so it is not a language that is used very often.[/quote]No, this is wrong.

> If you distribute the non-free Sun JVM, you have to agree not to ship any alternatives, which is very restrictive.I don't remember that restriction in the JRE license.  What it does forbid is repackging the JRE in any form, which is why most distributions won't ship it.

> Currently, the best bet for Java on Linux is the GNU Java Compiler (GJC). But I really wish Sun would open up theirs.No, it isn't.  Sun, IBM's or BEA's JDKs are the best bets.  All the OSS alternatives are utter crap if you want to build Java applications.

[quote=sphinx]The trouble is, as was metioned above, Java isn't very common in the Linux realm due to (anal IMHO) legal issues.[/quote]Java is incredibly common on Linux.  What it isn't common on is the Linux desktop, because Java isn't common on the desktop, period.  OS has little to do with that

[quote=macxek]What I'd really like to do is work on a C/C++ project for linux that is *at least* slightly organized and is run by a cool team that won't ask you to RTFM on every question.[/quote]Pick a project that interest you and ask them if they need help, or find a problem that needs solving on it's own and solve it.

Despite your impression, there is no real organization between development camps (or even within, sometime).  There are plenty of problems to be solved if you just use your system for a while. Some problems people are working on; some are not.

But this isn't a job.  No one is going to tell you, "Go work on this, this is where the most work is needed."  You're supposed to work on what interests you, and you haven't told anyone what that is.  You're being told to go figure it out yourself because that's all anyone can tell you based on what you've told us.

---

### Post by slushy77 on 2006-04-26
I dont think that linux is hostile to new developers, but the attitude of a small minority of users (both expert and newb). I've been using linux for 7 years and i think it is getting easier to use with each release. With Kubuntu 5.10, I didn't have to configure any of my hardware (even digital camera and graphics card :)  ), and tools like an email client, webbrowser, text-editor and an office suite were installed automatically. 

Due to the nature of open-source development, updates to software and documentation are made when someone has time to make the fix. Which is where forums such as this come in - someone has done the work and is prepared to publish the steps they took. 

Although RTFM is the worst response, it should sometimes be expected, especially if the answer being sought is well documented. 

If you want to get involved in an open source project, have a look at the following sites [ubuntu developers page]("http://www.ubuntu.com/developers"), [sourceforge]("http://sourceforge.net"), [the free software foundation]("http://www.fsf.org/") or [mozilla]("http://mozilla.org"). There are many more opensource sites, but these should give you an idea of what projects there are

---

### Post by kaamos on 2006-04-26
If you are interested in Java gui apps, you should check out [java-gnome](http://java-gnome.sourceforge.net/). There are some projects listed on the site as well.

---

### Post by Kimm on 2006-04-27
I dont realy know how you came to that conclution...?
I never found linux devs hostile, not more then the Windows devs anyway.

What you realy need to do is look for a guide that describes programming in Linux, most of it is similar, but maby you want to learn a Linux Widgets system, Like GTK.

Java programming works just as well in Linux as windows, the programs dont even have to be recompiled.

Get out there, read! thats the way I learned to program, in any OS - Linux was no different.

---

### Post by macxek on 2006-04-27
Well, again thanks everyone for your input. You all contributed to convince me that it isn't really 'hostile', but simply a bit chaotic, not in a negative sense, but rather everyone work on their stuff and share it.

I did not know that there were projects in Java for linux, at least not desktop software... I might take a look at it, although I'm not very interested in programming in Java since that's what I do all day at work :) I'd rather learn a new language or just work in C/C++.

---

### Post by rplantz on 2006-04-27
As a retired computer science prof., I know that learning styles differ considerably. If you are one who takes to books, you may wish to take a look at "Beginning Linux Programming" by Stones and Matthew (Wrox). They have lots of practical examples. They start with an example to illustrate a concept, then critique their example. Then they add to it to improve it. Something like this might give you an overview from which you could find a focus.

[Edit] Oh, I have found that some Linux forums can be a bit "direct", but the Ubuntu forum seems to be especially friendly. It's one of the reasons I stay with Ubuntu.

---

### Post by Kimm on 2006-04-28
> 
I'd rather learn a new language or just work in C/C++.


C and C++ are great languages, both fast, portable and not to difficult. If you want GUI programming, I'd recomend C#, even though it is a Microsoft product, in my opinion its the only realy good thing that ever came from them (software wise), and GTK# is a realy good widget system.

---

### Post by Nolander on 2007-03-23
i agree with u in a way macxek,

there is no support for newbie developers.

my two cent,

Nolander

---

### Post by lnostdal on 2007-03-23
Uhuh .. and what is your actual problem, Nolander? Where are you stuck?

Stuff like this annoys me -- please give me something to work with here. Do you have any actual questions or are you here to insult us trying to help newbies (and others) by not even giving us a chance?

---

### Post by Nolander on 2007-03-23
i did not mean to offend i was just agreeing with macxek.
all the q?'s i ever asked have been answer but a lot of people are hostile and do tell u to **** of and read a book

i am sorry if i offended u

nolander

---

### Post by lnostdal on 2007-03-23
> tell u to **** of and read a book

If you keep experiencing people giving you that advice there just might be some truth in it, don't you think? Especially since they probably already know how to program and know how they themselves and everyone around them learned it -- all starting as newbies of course.

You see; there is a border between users and developers. Users should not be expected to read (yes, the RTFM-thing *horrors* ..) or write(#3) anything at all, but as soon as that user wants to cross over to the "developer-side" there is a totally different perspective.

A developer _must_ read in the same way a writer _must_ read. He must read a lot. Coding is writing, and to write well one must do a _lot_ of reading and writing. 

There is absolutely no exception to this. Either deal with reality or get nowhere at all while at the same time having others suggesting time and time again that you Go Read a Book(#1). This is not hostility. It is an honest request or plea for you and every newbie to start dealing with reality as soon as possible instead of avoiding it or looking for a shortcut(#4).

If you by some totally broken or misunderstood way actually feel this is hostility, you do not have what it takes - and can never be a developer .. ever(#2).

Now; do you have any actual questions, or have you not even _started_ reading, studying and experimenting yet? :)


#1: ..or a tutorial, or an article -- anything. There are lots of free books, tutorials and resources out there. And by "resources" this forum is included of course.

#2: Isn't this the most inspiring, annoying and/or infuriating thing you've ever heard? Does it not make you want to prove me wrong _right now_? Does it not fill you with energy and the will to prove that you too can do this? Then c'moooon - do it! .. also see: [http://www.catb.org/~esr/faqs/hacker-howto.html#believe1](http://www.catb.org/~esr/faqs/hacker-howto.html#believe1) .. and go grab your nearest Python resource ( [http://wiki.python.org/moin/BeginnersGuide/NonProgrammers](http://wiki.python.org/moin/BeginnersGuide/NonProgrammers) ) and Python-environment so you can start interacting with it at once while you are reading.

#3: This is actually the key-connection between wanting to learn how to code .. and - well .. code requires, or _is_ writing and reading. It is so naturally connected; for a coder this is totally obvious. How can a coder not want to read? That just does not make sense!

#4: Which of course never actually exists; but every newbie spends some amount of wasted time looking for it. How much time do you want to waste?

---

### Post by pmasiar on 2007-03-23
Excellent - you like free software and the [gift culture](http://en.wikipedia.org/wiki/Gift_culture) what governs it, and want participate. As in any culture, you need to learn vocabulary and customs to "fit in" and don't be a [wannabe](http://www.science.uva.nl/~mes/jargon/w/wannabee.html). It is very tribal - what is perfectly acceptable for some tribes is a no-no for others.

First, clueless journalist started using [hacker](http://en.wikipedia.org/wiki/System_cracking) to mean "cracker", and world "hacker" is lost in the meaning used in [elder days](http://www.science.uva.nl/~mes/jargon/e/elderdays.html). But many hackers use it in old positive meaning - so if they used it with you, they expected you understand it in old meaning. If you did not, you sound like a wannabe, so don't complain about it. Between hackers of old school (not crackers), it is good.

RTFM, accompanied with reference what to read, is also good. In that case it stands for "Read a Fine Manual" :-) Reference is good. Worse might happen: your question is ignored. That said, here in Ubuntu the culture attitude is being more friendly to newbies than average forum: skip RTFM and just give a link. Result is the same, beginners are not offended. Oldtimers are not offended by RTFM and just follow the link.

> **Nolander said:**
> there is no support for newbie developers.

Software is free, but time is not. Support means time, and time costs real money - did you ever tried to call to say Dell support: how much time you listen to their "enthusiactic" music, annoyingly interspesed with "your call is important" and even worse - shameless advertisements? So you basically expect that people who can develop new software and fix bugs in existing, stop doing it and answer to your questions. Well, it does not work that way. They share sofware to solve own problems, and do mostly in own free time. There are hundreds of wannabees, and no way to find out which one can be usefull for the developer and which one will be just whiner. You need to prove yourself to developers. 

Sometimes people who have some knowledge, but are not full-fledged developers, are helping newbies to acclimatize in new culture. But even then - don't be a whiner. You have no right to anyone's time, you want to learn it by yourself, and other people are sometimes feel like they want to help you - be gratefull for every bit of help, because they might spent time on getting something important to "them" to get done, but instead thay are helping "you" to get done what "you" want. If that is not good enough for you, you can always pay for commercial support - it exists, but it is not free. Just for kickers try to call microsoft help support. :-)

There are many good resources on internet, and "Google is your friend". Sometimes people collect links to other resources. But it is your responsibility to find them. You may ask specific questions, and you *may* get specific answers. Whining "nobody loves me like my mom" does not get you anywhere - and it is even true, nobody does :-)

So, don't be a whiner. Nobody in free software owes you anything. You can always use it and you don't have to give back if you don't want. If you show attitude that want to learn, you will always find a teacher.  But of course someone who drains time of others, refusing to read the docs and taking responsibility to solve own problems, is not a wannabe or newbie - is leech and is ignored in disgust.

Summary: Ubuntu is more friendly to beginners than average (and we are proud on that distinction), show us you want to learn and you will be fine.

---

### Post by pmasiar on 2007-03-23
> **Nolander said:**
> there is no support for newbie developers.r

What do you want to develop? I bet I can google out couple of links for anything you can imagine.

BTW sorry I do not want to pick on you. Your post was easiest to quote, that's all. Thanks for summarizing it in one line :-)

---

### Post by Snowmayne on 2007-03-23
> **pmasiar said:**
>  First, clueless journalist started using [hacker](http://en.wikipedia.org/wiki/System_cracking) to mean "cracker", and world "hacker" is lost in the meaning used in [elder days](http://www.science.uva.nl/~mes/jargon/e/elderdays.html). But many hackers use it in old positive meaning - so if they used it with you, they expected you understand it in old meaning. If you did not, you sound like a wannabe, so don't complain about it. Between hackers of old school (not crackers), it is good. 

Lord, I remember the days when hackers and geeks were admired and crackers and phreaks were pariahs. (but that's a whole other thread about how things change over the years, I guess)

But I have to agree with pmasiar. It really IS a question of trying to fit into a new culture and having to learn how to fit in - something like moving to the middle of the Amazon and complaining that there's no poutine and michgan hot dogs around (i'm from montreal, so anyone not familiar with either of these staples drop me a line and I'll explain what they are ;) )

For me the hard part is that there's sometimes just too much choice available for the 'avg joe' coming over from that other OS to choose from. Example: most people a few years ago were still using IE6. Only other options were..... buggy netcape, buggy opera or rumours of firefox. How many browsers are there in Linux? I know I've got 4 on my linux partition (ff, opera, konquer & epiphany) and only 2 on my win partition (IE6 & ff). Another perfect example: plain text editors. How many are installed on a default windows box? 1 (notepad). How many on a default linux box? (someone please tell me 'cuz I still can't figure out which one to get comfy with)

Point is, macxek, is you've entered a wonderfully strange new world, but instead of enjoying the newness of it, you're complaining because you can't find a poutine stand anywhere. Get comfy in this new place and as you learn your way around, you'll find where you can best fit in.
):P

---

### Post by pmasiar on 2007-03-23
@ Nolander, macxek

Please don't feel bad for what you asked and what you said. **There are no stupid questions** - only stupid question is the one you wish you asked and you did not. I wrote my own posts and emails I wish I did not, as most members here would admit. We all make mistakes. Nobody expects from you to just come in and know how things work etc. 

Think about it as [http://en.wikipedia.org/wiki/Tough_love](http://en.wikipedia.org/wiki/Tough_love) . For anyone here would be much easier just ignore your post. The fact we responded and explained you how world of free software works means we want you guys (and gals) learn how to fit, became happy members, and contribute back according to your interests and abilities. Showing your Ubuntu to friends, how cool and easy is, also counts.

It might seem to you that you do not know much right now. **No problem!** Nobody was born with deep knowledge of kernel hacking - not even Linus :-) Learn all you can, one month from now, you will be 1 month ahead from people who just joined, and can help them. 

If you feel so, you can create a wiki with interesting links which were helpful solving some of your problems, like I do for people learning python: [http://learnpython.pbwiki.com/](http://learnpython.pbwiki.com/) You can get your own free wiki at pbwiki.com. It can be "your own beginner's guide to ubuntu". 

Cheer up! 

All hackers are aware of this phenomenon, it even has own name  [http://en.wikipedia.org/wiki/Eternal_September](http://en.wikipedia.org/wiki/Eternal_September) and [many](http://iexplor.blogspot.com/2007/02/september-never-ends.html) [posts](http://catb.org/~esr/jargon/html/S/September-that-never-ended.html) about it. You are not first and not last. In copule months it might be you showing the right way to next generation  :-)

---

### Post by HasratUSA on 2007-03-23
> **nocturn said:**
> The legal issues are very serious.  If you distribute the non-free Sun JVM, you have to agree not to ship any alternatives, which is very restrictive.

Currently, the best bet for Java on Linux is the GNU Java Compiler (GJC).  But I really wish Sun would open up theirs.

Disregard me and this post of mine if you want to, for I'm a complete newbie in the world of programming in general, languages and compilers, but if you fortunately don't want to disregard me and this post and instead want to enlighten a newbie, then please take the time to answer the following questions: 

1) Why are you calling Sun Java Virtual Machine 'non-free'? The last time I downloaded it (Java 5 JRE and yes I downloaded the JDK too, to compile java programs and applets) from java.sun.com, they didn't charge me a single penny.

2) For example I shipped to my customer a java jar program along with Sun's JVM/JRE on a CD. Legally speaking and according to you, I'm not allowed by Sun to include any other JRE/JVM alternatives. Now I don't see a valid reason behind why and how me and the customer would be benefitted by using another JVM/JRE that's not written by Sun. Sun and its developers took the time to develop the JRE and they are constantly optimizing it along with the whole language, compiler and everything. They are even coming up with new technology and solutions for cell phones. Sun's Java is being used in Nasa also, as far as I have heard. So, why is it so necessary for Java developers in Linux platform to really use a java compiler, jre and etc etc othat than the ones developed by Sun?

3) You might want to state that Sun hasn't open-sourced any of its products, but for your information they have been planning on going open-source for a considerable amount of time. Just because a product or its manufacturer isn't giving away their product entirely to some extent doesn't necessarily mean users of a free platform should go crazy and abandon the whole product, does it?

---

### Post by UK-sHaDoW on 2007-03-23
All I did was 

[LIST]
[*]Get Gcc
[*]Install Kdevelop
[*]Learned GTK

[/LIST]

And i was off...

Never read a book.  I now develop indie games using sdl for a hobby.

---

### Post by pmasiar on 2007-03-24
> **HasratUSA said:**
> 1) Why are you calling Sun Java Virtual Machine 'non-free'? ...they didn't charge me a single penny.

Read definition of [free software](http://www.gnu.org/philosophy/free-sw.html) (really, do read it): "free" is related to freedom (4 basic user freedoms), not price. Think "free speech" not free beer. You can get paid for distributing source code of free software. Companies like Red Hat and Canonical made profitable business based on free software (they get paid for support).

You may want to read [another esay about software freedom](http://www.gnu.org/philosophy/linux-gnu-freedom.html) and why Linux should be called GNU/Linux (because Linux is just small part, kernel: rest is GNU).

> 2) For example I shipped to my customer a java jar program along with Sun's JVM/JRE on a CD. Legally speaking and according to you,... 

"according to you" is irrelevant. The only relevant opinion is what law says. You may be too small a fish, so Sun will not bother checking if you distribute code according to laws, but you bet any big company (with money in bank) could become a target for a lawsuit if it was breaking any laws.

> 3)... Just because a product or its manufacturer isn't giving away their product entirely to some extent doesn't necessarily mean users of a free platform should go crazy and abandon the whole product, does it?

You can do whatever you want in your free time (and if you break law and someone notices, you are responsible for your actions), but for company it does not make sense building a business on breaking law and on promises. If you still think it might be good idea, I have a [cheap bridge](http://en.wikipedia.org/wiki/Brooklyn_bridge#Cultural_significance) for you, really good deal. :-)

---

### Post by samjh on 2007-03-24
Actually, large portions of Sun's Java are already licensed under GPL v2 with Classpath Exception (hereon referred to as just "GPL"), as per their announcement on 13 November 2006.
[http://www.sun.com/software/opensource/java/project_overview.jsp](http://www.sun.com/software/opensource/java/project_overview.jsp)

As of 13 November 2006, the following components were released under GPL:
[LIST]
[*]The HotSpot Java Virtual Machine
[*]The javac compiler
[*]JavaHelp 2.0 extensible help system
[*]Java Micro Edition and Java ME Technology Compatibility Kit (GPL v2 only, no Classpath Exception)
[/LIST]

Java Enterprise Edition was already open-sourced since 2005, under the OSI-approved CDDL.

Fully-buildable, legally unencumbered source code of the Java SE SDK is due to be released before the middle of this year, with build scripts.

Now, since the HotSpot JVM's source code is downloadable and buildable (yes, it's GPL v2, I've checked), and the class libraries from JDK 6 and 7 early-access versions can legally be combined with the open-sourced HotSpot JVM ([https://openjdk.dev.java.net/hotspot/faq.html)](https://openjdk.dev.java.net/hotspot/faq.html)), the entire JRE is practically free and open-source.

---

