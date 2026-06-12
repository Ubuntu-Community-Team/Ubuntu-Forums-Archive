---
title: "Entry Point into Open Source Development"
date: 2008-08-07
forum: Programming Talk
---

### Post by xnevermore on 2008-08-07
No, this isn't a "how do I learn to program" thread. Well... not really.

I currently have a general understanding of programming in C, C++, Ruby and Perl. What I want to do next is learn more about these languages, the tools and procedures behind open source development using a "hands on" approach while contributing back to the community at the same time.

The problem is: I don't know how to go about doing this.

There a lot of resources out there for how to use gcc, how to use automake, how to use cvs, etc. However, there aren't nearly enough explaining the general theory behind becoming a contributing member of the open source community.

Obviously, I wouldn't want to start by jumping into the Linux kernel source code. Not only is my experience not mature enough to start writing kernel patches, but when trying to understand something like the kernel by looking at the source, I'm frightened by the immensity of it and don't know where to begin. Besides, writing your own code is one thing, but reading and understanding someone else's (someMANYs, actually) code is something entirely different, for which I have very little experience.

So, how would you guys recommend entering the world of open source development? And by that, I don't mean migrating from closed source to open source, but rather, starting out as someone who knows a bit about programming and wants to know more and contribute to the open source community as well.

I hope all of that was understandable enough.

---

### Post by mssever on 2008-08-07
You can start by finding a project that interests you, and submitting patches to fix bugs.

---

### Post by Tomosaur on 2008-08-07
Well before you start any development using Ubuntu, you need to get the basic tools (Ubuntu is one of the few, if not the only mainstream distro which doesn't include build tools as part of its normal install):

```

sudo apt-get install build-essential

```Anyway, once that's taken care of - there's no real prerequisite to contributing. If you are interested, most projects are happy to let new people send patches and help out. It's not all programming - arguably one of the biggest 'non-programming' parts of any of the big open-source projects is documentation and translation.

If you just want to get involved with coding though, you need to find a project you like and have a few ideas for, and find out what its development process is like. Most use a version control system like CVS or SVN to allow people to download the current development trunk (i.e: the 'next version' to be released, as it's in development). Most projects have a web-page detailing how you can find the current source code.

Once you've downloaded the source, you can just get to work making the changes you'd like to see in the software. Then use the 'diff' tool to create a patch. If the project doesn't use something like launchpad.net which allows users to upload patches, it's usually necessary to send your patch as an attachment to the project's mailing list. It helps to make your e-mail subject line informative so that the right people will pay attention. If your patch fixes a known bug (Most bugs are assigned some kind of ID), say, Bug #41245 then your subject line might be '[PATCH] Bugfix for #41245 - <title of bug>'. If your patch is just some new functionality or whatever, your subject line should indicate this. Many projects (although not all of them) keep a 'wishlist' which for all intents and purposes follows the same format as the bug tracking system - you get a wish ID#, wish title, description etc.

Generally speaking there's no real formula for contributing - you just do what you can, when you can. Spend a while reading over your project's mailing-list archives (or forum, or wherever the developers congregate to talk) to get a feel of who's who and how things are done, then just get on with it when you're ready :). The beauty of open source is that you get to work on what you're interested in working, not being forced to do the stuff you don't care about. For this reason, you'll often find that developers tend to 'assign' themselves to certain areas of code in a project. Developer Jim might focus on developing the user interface, while Developer Jane might prefer hacking away at the network code. Try to find out who primarily works on the area of code you're interested in helping with, find out whether they're already working on the same problem you're trying to fix etc.

Remember that even if your patch fixes some bug, it may not get included for a while, or even ever. If the section of the code which the bug affects is going to be deprecated by something else anyway, then there's no real point chasing it up. This is why it's good to lurk around for a while, see where the project is going, what developers are trying to achieve with the new version etc. Don't feel bad if your patch doesn't get included - the devs will (mostly - there's always a few bad eggs!) be grateful that you're trying to help out, and it's all just practice anyway.

Most importantly - be patient. If you submit a patch and just don't hear anything for days, or even weeks - remember that most of the time the other developers just do this as a hobby, they're not getting paid to work on the project so they'll just come back to it when they feel like it.

---

### Post by elithrar on 2008-08-07
> **xnevermore said:**
> ...Ruby and Perl.

What experience have you had with these two languages? Their barrier to entry is fairly low - perhaps look at a few of the web frameworks or libraries written in these languages, and attempt to either extend, improve or re-factor them?

---

### Post by dwhitney67 on 2008-08-08
I hope that you are a competent s/w developer, not just someone who went through exercises in a book and now thinks he/she is capable of developing a 50-100K (or more) SLOC software application.

It takes more than just desire to begin developing applications that will be used in an either closed or open source environments.  Perhaps you can start by becoming a "black box" tester, then perhaps later delve into making bug fixes.

If you want to develop s/w, I would suggest that you look for a career in the field.  You might as well earn money while doing something you enjoy.  There are plenty of jobs, more than can be filled.

---

### Post by xnevermore on 2008-08-08
**@tomosaur:** Great post. I guess my point is just that the open source community needs to do more to recognize every user as a potential contributor and let users know that even if they don't know how to program, they can still file bugs, and then learn to triage bugs, then learn to package, then learn to fix bugs, then learn to add new features, then learn to start their own project, etc, etc. I mean, right now, Launchpad is reporting around 50,000 open bugs in Ubuntu. Meanwhile, the development documentation is a complete mess (scattered and incomplete). If it were possible to show users that they can make a huge difference in the software they love by showing them a clear path that they can see themselves taking, rather than scaring them with revision control systems and patch tools and IDES and compiler options, etc., then soon the developers might get the help they need in fixing a lot of those bugs and making Ubuntu even better than it already is.

Like I said, the linux kernel source code is daunting to me, but no one ever suggested, say something [like this]("https://wiki.ubuntu.com/MOTU/TODO?highlight=(CategoryMOTU\b)#MOTU%20Beginner%27s%20tasks") to get me acquainted with the open source world. They just said, "do what you can", which meant reading five books at once of theory, without real-world experience behind it.

**dwhitney67:** You're exhibiting a big part of the arrogance that I'm talking about. *Leave these things to the pros*, essentially. Well, like I said, every user is a potential contributor, and even a potential developer. And no, I don't think I can develop a hundred thousand line program. In fact, I pretty much said the complete opposite. That I was looking to start small and learn more about the languages while applying them for the benefit of the community. So maybe you should get your head out of your ***.

---

### Post by Tomosaur on 2008-08-08
> **xnevermore said:**
> **@tomosaur:** Great post. I guess my point is just that the open source community needs to do more to recognize every user as a potential contributor and let users know that even if they don't know how to program, they can still file bugs, and then learn to triage bugs, then learn to package, then learn to fix bugs, then learn to add new features, then learn to start their own project, etc, etc. I mean, right now, Launchpad is reporting around 50,000 open bugs in Ubuntu. Meanwhile, the development documentation is a complete mess (scattered and incomplete). If it were possible to show users that they can make a huge difference in the software they love by showing them a clear path that they can see themselves taking, rather than scaring them with revision control systems and patch tools and IDES and compiler options, etc., then soon the developers might get the help they need in fixing a lot of those bugs and making Ubuntu even better than it already is.

Like I said, the linux kernel source code is daunting to me, but no one ever suggested, say something [like this]("https://wiki.ubuntu.com/MOTU/TODO?highlight=%28CategoryMOTU%5Cb%29#MOTU%20Beginner%27s%20tasks") to get me acquainted with the open source world. They just said, "do what you can", which meant reading five books at once of theory, without real-world experience behind it.


Ubuntu is just one part of a very diverse ecosystem. As I said before, there is no 'right way' to help out, if that's what you want to do. Rather than saying 'do what you can', I should have said 'do what you want'. If you think the documentation is a mess - then why not do something about it? Open source is fundamentally different to traditional, 'corporate' development. Linux itself was first created as a learning exercise - a hobby. There is no overarching goal - in fact possibly the closest any distribution has really gotten to an overall target is Ubuntu Bug #1 - displacing Windows from the top spot. However, there is no real drive at the grassroots level to achieve this goal - developers just do whatever they feel like, when they feel like. Sure, most Linux distributions have a reason for being created - say, to develop a lightweight Linux system than can boot on your iPod, or whatever, but most do not set out saying 'In 10 years time, I want this project to have taken 50% of the market share from Windows and Apple'.

Anyway, what I'm trying to say is that the reason there's no big push to recruit open-source developers to help projects out is that most projects aren't trying to achieve anything in particular. There is no deadline, nothing to push against. One single developer would achieve the same as a group of 10 developers, it'll just take longer. If you **want** to help, then the onus is on you to take the initiative and do something about it. Most project websites will have instructions on how to download the source code, what their general system is for submitting code etc - but they're not going to sit around and actively try to recruit you. Occasionally people come along with their idea for a project and ask people if they're interested in helping out - but you won't see it listed on a job website or anything like that. **You** have to find out about the project(s) you want to help develop.

Do you see what I'm getting at? Why should open-source projects have this drive to make people aware that they want help? Most of them don't particularly **want** help, they're just grateful when it comes along. It's like if you were walking down the street and somebody decided to give you a sandwich You might not particularly want or need this sandwich, but it's nice that somebody wants to give it to you in the first place. I can kind of understand where you're coming from - but really it's just a matter of experience. Open-source developers tend to assume that everybody who wants to help out knows how to do so - after all, that's how they got involved. It just kind of comes with time. The kind of people who like getting involved with projects tend to be lurking on that project's mailing lists, forums etc long before they actually do anything to help.

**_tl;dr_** - if you want to help, you will find a way to do so. OSS developers aren't hiring you for a job, you can just do whatever you feel like.

---

### Post by dwhitney67 on 2008-08-08
> **xnevermore said:**
> 
**dwhitney67:** You're exhibiting a big part of the arrogance that I'm talking about. *Leave these things to the pros*, essentially. Well, like I said, every user is a potential contributor, and even a potential developer. And no, I don't think I can develop a hundred thousand line program. In fact, I pretty much said the complete opposite. That I was looking to start small and learn more about the languages while applying them for the benefit of the community. So maybe you should get your head out of your ***.
So you want to write code, eh?  If small applications are what you want, then go ahead.  Some other forum member is attempting to write a Black Jack game application.  Why don't you try that.  Provide a GUI front-end, and then when you are done post the application here on the forum for everyone to enjoy.

Still too big of an application for you??  Then stick to "hello world" applications because in the real world most useable applications are lot more complicated than even a "simple" card game as Black Jack.

For most projects, small and large alike, version control, collaboration between developers, documentation, and a strict drive towards maintaining the same development standards is essential, especially when multiple developers are involved.  You can't just let some newbie come in to start mucking with the process that is in place!

Anyhow, the comments I provided earlier were based on my opinion as professional software engineer.  I have been in this profession for the last 18+ years, working for some of the most well known companies/agencies.  So what have you been doing in the meantime??

Btw, the remarks you made earlier were uncalled for.  I am sorry if you are one those "sensitive" types that can't take critical comments from a peer.  All I can recommend is that you grow up.  Oops, I did it again.

---

### Post by Tomosaur on 2008-08-08
> **dwhitney67 said:**
> So you want to write code, eh?  If small applications are what you want, then go ahead.  Some other forum member is attempting to write a Black Jack game application.  Why don't you try that.  Provide a GUI front-end, and then when you are done post the application here on the forum for everyone to enjoy.

Still too big of an application for you??  Then stick to "hello world" applications because in the real world most useable applications are lot more complicated than even a "simple" card game as Black Jack.

For most projects, small and large alike, version control, collaboration between developers, documentation, and a strict drive towards maintaining the same development standards is essential, especially when multiple developers are involved.  You can't just let some newbie come in to start mucking with the process that is in place!

Anyhow, the comments I provided earlier were based on my opinion as professional software engineer.  I have been in this profession for the last 18+ years, working for some of the most well known companies/agencies.  So what have you been doing in the meantime??

Btw, the remarks you made earlier were uncalled for.  I am sorry if you are one those "sensitive" types that can't take critical comments from a peer.  All I can recommend is that you grow up.  Oops, I did it again.

Why all this talk of 'the real world'? In the real world you spend half of your time writing code for a project you don't care about, then the other half justifying your existence to people who don't understand what it is you even do in the first place. At least with open-source you can do it your way and there's no risk. The very worst that will happen is your patch gets rejected and you have another go. In 'the real world' - you mess up and you lose your job. Don't assume that everyone who wants to help out with a project wants to make software development their career.

The thing is, 99% of open source projects don't really have any design at all. A few don't even have documentation, never mind **developer** documentation. Sure, 'big' projects like 'Ubuntu' have ways of doing things - but the reality is that when you find a project you like, there's a good chance it will have no real coding standard. This is why the best thing you can do is just to lurk around a project. Get a feel for who does what, if there are any traditions that group of devs has etc. Most will have a similar method for submitting patches and stuff like that, but as far as actually writing code goes, don't be surprised if there's no strict style. The beauty is in the chaos, I find.

Oh, and software engineering != software development. FOSS projects are developer driven, not design driven, for the most part. Most of the time, the only goal is functionality.

---

### Post by dwhitney67 on 2008-08-08
> **Tomosaur said:**
> Why all this talk of 'the real world'? In the real world you spend half of your time writing code for a project you don't care about, then the other half justifying your existence to people who don't understand what it is you even do in the first place.
...
It seems that you have experience in the field.  Why would you accept a job position if you do not enjoy the work?  Are you not confident enough to hold out for the better job?  Or are you not capable of attaining a better job?  Perhaps you are located in an area where there is not many opportunities from which to choose.  Either way,the point is that if you do not enjoy your work, then it is time to find another job, perhaps in a different locale.

I'm so used to working on large projects ($100+ million contracts), that the company that is awarded the project has to mitigate any development issues by coming up with a solid design before one line of code is written.  They have a process in place that normally includes software standards.  If an employee can't/won't adhere to these standards, then they are shown to the door.

On open source, a developer can do whatever they want, but I guarantee that for the source to be accepted, it would have to be peer reviewed by others.  There is no damn way I would install an application on my system written by a mickey-mouse s/w developer.  For all I know the application includes a key-logger or other malicious piece of code!

Anyhow, developing software is no different than developing a sprocket.  Thought, design, and ultimately implementation must proceed in a rational order.

---

### Post by Tomosaur on 2008-08-08
> **dwhitney67 said:**
> It seems that you have experience in the field.  Why would you accept a job position if you do not enjoy the work?  Are you not confident enough to hold out for the better job?  Or are you not capable of attaining a better job?  Perhaps you are located in an area where there is not many opportunities from which to choose.  Either way,the point is that if you do not enjoy your work, then it is time to find another job, perhaps in a different locale.

I'm so used to working on large projects ($100+ million contracts), that the company that is awarded the project has to mitigate any development issues by coming up with a solid design before one line of code is written.  They have a process in place that normally includes software standards.  If an employee can't/won't adhere to these standards, then they are shown to the door.

On open source, a developer can do whatever they want, but I guarantee that for the source to be accepted, it would have to be peer reviewed by others.  There is no damn way I would install an application on my system written by a mickey-mouse s/w developer.  For all I know the application includes a key-logger or other malicious piece of code!

Anyhow, developing software is no different than developing a sprocket.  Thought, design, and ultimately implementation must proceed in a rational order.

Gotta disagree with you there, I'm afraid. Obviously I don't know your usage habits - but still, the vast majority of software available to you in the repositories is developed completely by volunteers. While many may well follow a traditional specification, design, implementation process - I feel pretty confident in saying that **most** of these don't. It is more akin to extreme-programming. There is a specification, then the design is pretty much skipped and it goes straight to implementation. While I was in university studying software development, we were always told to follow the traditional path, but the reality is that it just causes stress and deadlines begin creeping up. 

If you code smart, you get good results fairly quickly. A lack of design **can** be compensated for by using **good coding practices**. Obviously it takes time to get to know what these are, but the up-shot of it is that functionality is better than readability any day of the week. Your software can have designs for every function, but if it doesn't work, it's useless. Better to hack something together quickly and then make it look nice later on, in my opinion. I would rather have a hammer today than the blueprint for a hammer next week, if you catch my drift.

Obviously we're coming at this from two different viewpoints, and I doubt I'm going to make much of an impression on your opinion about the matter - but all I'm saying is that if you want to help out, you don't need to worry about the design. In a professional environment yes, you would need to worry about it - but with open-source, the only thing that should concern you is that your part works. You don't need to work on anything else, so as long as you are courteous and comment your code to make sure someone else can understand what you're doing, it should be fine. There's no risk, and nobody's going to die (well, hopefully :P) if you mess something up. Only concern yourself with what you need to need to be able to do your bit. There's no monthly code review, no deadlines, nothing to worry about except actually getting the thing working.

At the end of the day - if you want to help out, and can, then do it. Don't talk about it, or worry about whether your code meets some obscure standard for network communications - just get on with it. Problems can be dealt with later - the functionality is the most important part.

Design is only important if you have an obligation to ensure the software works. In open-source, there is no such obligation. If it works, brilliant. If it doesn't, just keep kicking it until it does. In my experience (no multi-million dollar contracts unfortunately!), worrying about design just slows everything down - and I usually come away with a design that looks remarkably like what I was intending to do anyway.

---

### Post by xnevermore on 2008-08-08
> **dwhitney67 said:**
> So you want to write code, eh?  If small applications are what you want, then go ahead.  Some other forum member is attempting to write a Black Jack game application.  Why don't you try that.  Provide a GUI front-end, and then when you are done post the application here on the forum for everyone to enjoy.

Still too big of an application for you??  Then stick to "hello world" applications because in the real world most useable applications are lot more complicated than even a "simple" card game as Black Jack.

Again, you are making assumptions. A black jack game is not beyond my abilities. A program like apache is. I never made any complaints about programming being too difficult. I'm saying that more needs to be done to get would-be developers to think within an open source framework and start contributing as soon as they can.

> For most projects, small and large alike, version control, collaboration between developers, documentation, and a strict drive towards maintaining the same development standards is essential, especially when multiple developers are involved.  You can't just let some newbie come in to start mucking with the process that is in place!
That's quite an elitist point of view. Of course all of those elements are involved, but while the main developers are busying implementing the next great feature, what's wrong with letting the new guy create some small overlooked bug fix to get a feel for the process?

> Anyhow, the comments I provided earlier were based on my opinion as professional software engineer.  I have been in this profession for the last 18+ years, working for some of the most well known companies/agencies.  So what have you been doing in the meantime??
Oh, give me a break! So you've got the authority to comment, but I don't!

> Btw, the remarks you made earlier were uncalled for.  I am sorry if you are one those "sensitive" types that can't take critical comments from a peer.  All I can recommend is that you grow up.  Oops, I did it again.
No need to comment.

---

### Post by mssever on 2008-08-08
If you want to contribute to my projects (see my signature), feel free. :) Even if you don't measure up to dwhitney67's standards, my only requirement is that you do good work that makes sense.

Note that developer documentation is pretty much non-existent. Contributions are welcome.

---

### Post by nvteighen on 2008-08-08
> **mssever said:**
> (...) my only requirement is that you do good work that makes sense.

That's a universal requirement expected at any work from anyone... isn't it? Or maybe is it just a very elegant (no kidding) way to say "any helpful idea is welcome"?

---

### Post by pmasiar on 2008-08-09
Both Tomosaur and dwhitney67 are right: different projects have different needs and requirements. But is is up to wannabe contributor to lurk at the project list and learn what rules are.

> **xnevermore said:**
> **dwhitney67:** You're exhibiting a big part of the arrogance that I'm talking about. *Leave these things to the pros*, essentially. Well, like I said, every user is a potential contributor, and even a potential developer. ... So maybe you should get your head out of your ***.

xnevermore, you are exhibiting a big part of the arrogance what kernel hackers are concerned. :-) Seriously, think yourself: if they will try to teach every wannabe kernel hacker up to speed, 99% of them will not be up to task, and they would do nothing but teach future failures. So they don't -- the only sane solution in their situation.

With this attitude, you would last about 5 nanoseconds on kernel or debian mailing list.

Nobody owes you anything beyond the free code. If you think you have right to request time from anyone because you need help - can I ask you to sandpaper my staircase, I want to paint it? :-)

For a famous and visible project, with legacy and goodwill to protect, you have to **earn the right to contribute**: because all those already contributing are extremely focused on maintaining that hard-earned trust, and last thing what can happen is to see random contribution from a nobody committed to important project without being thoroughly criticized by many people. Most developers are more interested in protecting stability and functionality of existing code that adding random patches (because existing code runs and fulfills a need, while new bad patch might break it).

read [ Homesteading the Noosphere](www.catb.org/~esr/writings/cathedral-bazaar/homesteading/ ) by ESR to understand what is going on (and while there, read other ESR's essays).

So you are much better off to try to build your reputation by contributing to a less visible project (or be ready to measure up to those highly-skilled experts, who are very interested on protecting own time, and do not care if they offend some noob wannabe - kernel hackers do not care about being nice to beginners and would laugh at ubuntu forum code of conduct: they need to protect their own productivity and not your feelings.

Imagine that you want to become a friend with existing project developers, to let them allow you to build skill set and reputation -- because be allowing your contribution, they are taking chances with the reputation of the project they already gained. Of course developers want someone help them: but will the newcomer be net asset or net gain, sucking more resources out than contributing in? How to tell?

But I am not sure you even appreciate this help here, you consider this a critique. But I genuinely want to help you and find a way how you can contribute - for me it would be much simpler just ignore you instead of explaining you your misconceptions and trying to beat some sense into you, and I know it will not win me friends with noobs. Read [http://en.wikipedia.org/wiki/Eternal_September](http://en.wikipedia.org/wiki/Eternal_September) to see what cultural problem it is...

Now, if you still want to contribute, and you understand you need to earn the right to commit to highly visible project, I can tell you how. But if not, I would not waste my advice on this thread :-)

---

### Post by mssever on 2008-08-10
> **pmasiar said:**
> Now, if you still want to contribute, and you understand you need to earn the right to commit to highly visible project, I can tell you how. But if not, I would not waste my advice on this thread :-)
I think that I already know the answer to this, but I'd be interested in reading your thoughts on this.

---

### Post by pmasiar on 2008-08-10
I was hoping for OP, but what the hell, others might learn as well, so here it goes:

Good way to become familiar with a project from developer's perspective is to start triaging/classifying bugs. Of course it is not exciting and frankly thankless work, but (1) it is not time-intensive (2) not a tragedy if you get bored and leave (3) you will become known to core developers as someone who asks and learns from answers, possibly also on IRC, (4) exactly your willingness to tackle the non-glamorous job will prove to developers that you are serious about learning the project innards and you have stamina to work on other parts - so it makes sense to invest time in your "getting up to speed". Developers would be happy to help you, and you will learn how parts of the project work together (and where the sharp edges are).

Later you can try fixing simpler bugs, and if your code will be up to sniff, your patches will be committed (after review by core developer), and after a while you will get commit rights and become developer. Specialize in some subsystem first, or loosely couple plugin, because you need to prove yourself in "periphery" before becoming "core" hacker, but it might depend on project structure and size of the core team.

---

### Post by pmasiar on 2008-08-13
freshly from the print machine: [How to Participate in the Linux Community](http://ldn.linuxfoundation.org/book/how-participate-linux-community)

Talks about the kernel, but is such interesting details, that it is a must-read for any aspiring hacker.

anothr good read: [Building an Open Source Community](https://fossbazaar.org/?q=content/building-open-source-community)

Both found at [http://lwn.net/](http://lwn.net/) , Linux Weekly News. You can read old articles for free, and subscription is very reasonable. Again, someone will tell that "knowledge should be free" but what are supposed to eat the people who produce that knowledge? Food is not free. LWN is kinda insider forum, many FOSS luminaries post there.

---

