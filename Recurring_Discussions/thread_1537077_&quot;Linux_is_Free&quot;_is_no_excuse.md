---
title: "&quot;Linux is Free&quot; is no excuse"
date: 2010-07-23
forum: Recurring Discussions
---

### Post by chessnerd on 2010-07-23
Every once and a while, I'll see a post about a problem in Linux and the person will express their frustration with Linux as a whole and openly question why they even use it. We've all seen those.

Then, invariably, there will be a response that basically goes like this:
> Hey, Linux is free, so don't complain.

But, is "Linux is free" a valid excuse? 

I don't think so. To use an excuse like that is to say "you get what you pay for" and since you pay nothing, that implies that you get nothing.

A big part of the "free and open source software" movement is supposed to be that it's method is superior to that of the closed-source model. According to its proponents, free/libre software isn't supposed to be a cheap knock-off or a "free alternative". It is supposed to be better.

But apparently it isn't, and other excuses like lack of commercial hardware support are only a part of the problem. Lucid has problems with my older desktop's nVidia Riva TNT2 graphics card, even though it worked fine in Jaunty. That isn't a fault of the hardware company, that's a regression. 

Then there are things that are just embarrassing, like that we still have clipboard issues. I always need to open up gedit and paste there so that I know my text won't get lost in the black hole that is Linux clipboard support, which it does at least 50% of the time. I had this happen when using my computer with my sister once and she laughed out load at the stupidity of it.

We can't keep saying "well, Linux is free" like that makes the problems go away. Either Linux is worthy of being a desktop OS or it isn't. Price doesn't matter.

I could post a list of my ideas of what Linux needs. I could post a string of demands for the Ubuntu devs. But I won't. 

All I ask is that people on this forum stop trying to use this lame excuse. It isn't constructive and just makes Linux look bad. 

If you disagree with me, and still think that "Linux is free" is a perfectly valid excuse, fine. But I'll tell you this: My opinions are free...

---

### Post by V for Vincent on 2010-07-23
Kind of agree - but I do feel it works both ways. We should retain high standards, but if you do have an issue, you should do whatever you can to help fix it, rather than just complain. "I'm not a programmer" isn't always an excuse, either.

---

### Post by lisati on 2010-07-23
/me resists urge to do a rant about people not wanting to put "code(s)" into the terminal..... :D (Most of the time they're talking about commands, not escape sequences or writing a program)

---

### Post by chessnerd on 2010-07-23
> **V for Vincent said:**
> Kind of agree - but I do feel it works both ways. We should retain high standards, but if you do have an issue, you should do whatever you can to help fix it, rather than just complain. "I'm not a programmer" isn't always an excuse, either.

Agreed, and I do try to do whatever I can to help others with it. I've filed bug reports about issues and try to post help on the forums as much as I can.

From my research into my graphics problem, the issue is that the newer versions of X.org break compatibility with nVidia legacy cards, so I don't really see too many options there.

As for the clipboard, I have no idea what the problem is, but I've heard of others with the same issue. I've read articles like this - [http://www.linux.com/archive/articles/123462](http://www.linux.com/archive/articles/123462) - and have decided that it really isn't worth my time to fiddle with a bunch of clipboard alternatives. What I ask for is only what Windows has: a clipboard that can hold text, images, or files until I paste those appropriately into the application of my choosing. An OS-based clipboard. The default clipboard(s) set-up is fine as long as you paste right away. The issues come when you wait more than a minute to paste, or close the wrong application in the process. I know that coding such a thing is harder than it sounds, and my coding skills are very limited, but it just doesn't seem like that much to ask...

---

### Post by numinous on 2010-07-23
Are you using the NVIDIA driver for your graphics card?

In Linux if you put something to the clipboard within an application and that application gets closed or terminated for some reason those clipboard items are no longer on the clipboad , just something to be aware and careful about when using the clipboad.

---

### Post by chessnerd on 2010-07-23
> **numinous said:**
> Are you using the NVIDIA driver for your graphics card?
The proprietary driver doesn't work. For one, the proper driver module no longer exists in the repositories. When I've forced the use of the proprietary nVidia driver by removing the Nouveau driver the system would show Plymouth, but wouldn't load X.org. 

I tried to install the driver from nVidia's website, but it said that it was incompatible with my current version of X.org.

The Nouveau driver sort of works, but it is very buggy. The mouse is constantly flickering, windows will some times vanish and then reappear, and it takes a minute for graphics changes to load on the screen after minimizing or moving a window.

EDIT: this is the driver I would need to work - [http://www.nvidia.com/object/linux_display_ia32_71.86.13.html](http://www.nvidia.com/object/linux_display_ia32_71.86.13.html)

> **numinous said:**
> In Linux if you put something to the clipboard within an application and that application gets closed or terminated for some reason those clipboard items are no longer on the clipboad , just something to be aware and careful about when using the clipboad.
That seems like a design flaw to me. Ah well, gedit manual clipboard it is...

---

### Post by mcduck on 2010-07-23
> **chessnerd said:**
> 
That seems like a design flaw to me. Ah well, gedit manual clipboard it is...
Not a design flaw, there actually is no clipboard. (If there was one, and it behaved like this, it would of course be a flaw).

If you want a clipboard, you have to install one yourself (there are several very good ones available in the repositories). Otherwise copy/paste is just handled directly from source to destination, without any actual clipboard in between (much in the same way as the traditional copy/paste method in Unix/linux, the primary selection.)

edit: what comes to the "it's free" argument, even though the people who use it probably use it in the "you get what you pay for"-sense, I prefer interpreting the "free" as in freedom. So, "it's free, don't complain" would mean that "if you don't like it, you are free to fix it".

---

### Post by numinous on 2010-07-23
> **mcduck said:**
> Not a design flaw, there actually is no clipboard. 
  you have to install one yourself (there are several very good ones available in the repositories). 

Thanks this is good to know.

It feels like there is a clipboard since I can select text and paste it into other apps.

Maybe distros such as Ubuntu should include a default clipboard program,  users can easily get confused about what is really going on in with this behaviour.

---

### Post by chessnerd on 2010-07-23
> **mcduck said:**
> Not a design flaw, there actually is no clipboard. (If there was one, and it behaved like this, it would of course be a flaw).
Alright, well I installed Parcellite (Glipper didn't seem to work) and set it up to run at startup with the no icon setting. So far, it works as I expected. If I ever remixed my own distro, it would include a clipboard manager. I'm surprised that Ubuntu doesn't already...

> **mcduck said:**
> edit: what comes to the "it's free" argument, even though the people who use it probably use it in the "you get what you pay for"-sense, I prefer interpreting the "free" as in freedom. So, "it's free, don't complain" would mean that "if you don't like it, you are free to fix it".
I can see that to a certain degree. You certainly don't have that option with Windows. However, I think that the "you can code it yourself" argument misses the point. Ubuntu isn't supposed to be a "code it yourself" solution. If it is, Canonical should advertise it as such, not as "Linux for human beings" which implies that normal people can use it.

When I wanted a way to make multi-image desktop backgrounds, I coded a program myself, GUI and all, in Java that auto-writes the XML file. That is beyond most and is about the limit of my abilities. I can't re-code a driver or fix bugs in Firefox. (Maybe someday, but not now).

---

### Post by mcduck on 2010-07-23
I've always interpreted the Ubuntu being usable by everyone to mean that there are no language, legal, technical or other restrictions stopping anybody from using Ubuntu, but you still might need to learn how to use it. If you don't want to, that's your fault, not the operating system's. 

That being said I'm not against making things easy to learn, at least as long as it doesn't make things less powerful. My point is simply that being able to use something and being able to use something without having to learn anything are two different concepts.

Also doing something about the problems doesn't always mean that you should learn to program and fix it yourself. You can also find somebody else to do it for you, or contact the developer and ask for a fix, or really anything other than just complaining and expecting that somebody else does this for you.

---

### Post by chriswyatt on 2010-07-23
But "Linux is free" is a good excuse for not getting angry, I've seen a few angry threads from frustrated users.  You tried it out, you didn't like it, you delete the partition and resize your Windows partition to fill up the hard drive again, what's there to get angry about?  It seems silly to get frustrated over a free piece of software.  I had a hard time getting Ubuntu to work when I first installed it but I didn't get angry, it's not like it broke my PC as I could still easily boot back into Windows again.  Took me a while to get everything sorted out and I needed lots of help from the forums but I never made an angry post about how Ubuntu is rubbish and can never be adopted by the mainstream.  I often wonder if it's frustrated Ubuntu users or if it's trolls posting these sorts of threads.

I guess the thing is, some people install Ubuntu as more of a project to check it out (like me), others expect it to be the be-all and end-all and solve all their computing needs!  These people often end up disappointed because they expected too much from it.  So I can understand why people reply with "Linux is free", I think it's a good point.

I think the trouble is some people forget all the hard work that goes into making an OS and expect it to just work.  With all the different hardware configurations out there I'm not surprised that Ubuntu doesn't work 100% of the time.

---

### Post by Nick_Jinn on 2010-07-23
"Its free" is definitely a bull shyte response to criticism....it kinds of demeans the open source community even more than the agro poster when you use that as a rebuttal. Its not a good response. 

On the other hand, I dont agree that open source isnt better.....Admittedly there are bugs and areas that are less polished, but there is also things I can do in linux that I could never do in Windows or even OSX. Linux is better looking than Windows and can do more out of the box from the default installation than Windows 7 Ultimate. OSX is decent competition, but I dont like the hardware monopolizing. That is a pretty significant limitation. I guess its easier to make a Hackintosh these days, but I still prefer Linux.


Isnt there a program that lets you install the drivers, not from Synaptic or install drivers, but lets you use the disk or the driver from the website and install it manually? I did that and it cleared up my graphics problems.

---

### Post by everytimeref on 2010-07-23
> **chriswyatt said:**
> But "Linux is free" is a good excuse for not getting angry, I've seen a few angry threads from frustrated users.  You tried it out, you didn't like it, you delete the partition and resize your Windows partition to fill up the hard drive again, what's there to get angry about?  It seems silly to get frustrated over a free piece of software.  I had a hard time getting Ubuntu to work when I first installed it but I didn't get angry, it's not like it broke my PC as I could still easily boot back into Windows again.  Took me a while to get everything sorted out and I needed lots of help from the forums but I never made an angry post about how Ubuntu is rubbish and can never be adopted by the mainstream.  I often wonder if it's frustrated Ubuntu users or if it's trolls posting these sorts of threads.

I guess the thing is, some people install Ubuntu as more of a project to check it out (like me), others expect it to be the be-all and end-all and solve all their computing needs!  These people often end up disappointed because they expected too much from it.  So I can understand why people reply with "Linux is free", I think it's a good point.

Excellent point. It's like when you get a mate to do your plumbing, you get it for free, so when there's a problem you have to ask nicely for more help, not automatically expect it to be fixed like you would if you'd paid for it.

---

### Post by Nick_Jinn on 2010-07-23
Im not sure I agree. People invest a lot of time into their OS. Its not totally free. Shuttleworth might break even on the OS or take a small hit, but makes up for it by selling Cloud services and also makes some money off Google and searches. They do make some gross profit on us as users though there might not be a lot if any net. We are both a testing ground and the funders of a project that supports a lot of industry that relies on Ubuntu in their servers. We are kind of important.


Just talking crap isnt the best way to get help, but I cant help but feel that the free argument is kind of insulting to open source, like you are expecting it to not be as good as something you pay for. While you could make the argument that people shouldnt be mad over the quality of free software, and they do, I think its kind of like saying......"dont complain about the taste of your lunch. Your mother made it. What do you expect".....Wouldnt you find that kind of insulting to your mother? Well, its kind of a backhand against the open source community, even if you feel like you are defending it from hecklers. Its a misguided response.

---

### Post by prodigy_ on 2010-07-23
> **chessnerd said:**
> Either Linux is worthy of being a desktop OS or it isn't.
It isn't. It's a good server/workstation OS though.

/thread

---

### Post by Trinexx on 2010-07-23
> **mcduck said:**
> Not a design flaw, there actually is no clipboard. (If there was one, and it behaved like this, it would of course be a flaw).

If you want a clipboard, you have to install one yourself (there are several very good ones available in the repositories). Otherwise copy/paste is just handled directly from source to destination, without any actual clipboard in between (much in the same way as the traditional copy/paste method in Unix/linux, the primary selection.)

edit: what comes to the "it's free" argument, even though the people who use it probably use it in the "you get what you pay for"-sense, I prefer interpreting the "free" as in freedom. So, "it's free, don't complain" would mean that "if you don't like it, you are free to fix it".
I'm ashamed to admit that I never knew that, despite using Ubuntu for about three years now.

---

### Post by Nick_Jinn on 2010-07-23
I like it as my desktop OS. Its prettier than Windows 7, and meets all of my needs with the exception of gaming.

It may not support as much hardware and may give problems to more users, but it works just fine for a lot of peoples desktop needs. I find it easier to get Ubuntu going, add medibuntu or just start off with Mint, than to get all the apps I need for Windows.....sure if you have hundreds of programs you paid for you can just install them with disks, but even that is way more time consuming than Synaptic or add remove programs.

---

### Post by kennedyvelez on 2010-07-23
> **mcduck said:**
> Not a design flaw, there actually is no clipboard. (If there was one, and it behaved like this, it would of course be a flaw).

If you want a clipboard, you have to install one yourself (there are several very good ones available in the repositories). Otherwise copy/paste is just handled directly from source to destination, without any actual clipboard in between (much in the same way as the traditional copy/paste method in Unix/linux, the primary selection.)

edit: what comes to the "it's free" argument, even though the people who use it probably use it in the "you get what you pay for"-sense, I prefer interpreting the "free" as in freedom. So, "it's free, don't complain" would mean that "if you don't like it, you are free to fix it".


good point. the _free _in "linux is free" is FREEDOM... FREEDOM TO DO WHAT YOU WANT... WITH LINUX/UNIX...

---

### Post by mickie.kext on 2010-07-23
Find another solution with same price tag and then compare.

---

### Post by clanky on 2010-07-23
> **chessnerd said:**
> 

But, is "Linux is free" a valid excuse? 

I don't think so. To use an excuse like that is to say "you get what you pay for" and since you pay nothing, that implies that you get nothing.

I couldn't agree more.  It bugs me that the same people who claim that Linux is perfect and way better than Windows are usually the ones who excuse faults with "well it's free".  Linux will never progress until it can compete on a technical level with proprietary OS's to the point where 99% of computer users no longer choose to pay for Windows / OS X rather than use Linux for free.

Granted, downloading a free OS does not give you the right to demand that everything should work in the way that you want them to, however when the Linux community ignore / excuse issues which users are having rather than addressing those issues then Linux will never advance.

It is all very well saying "you have the source code fix it", but for the vast majority of users (usually including those saying it) that is just not an option, if people who have issues with Linux are told that they are stupid / they are lying / they are M% employees spreading FUD / it's free stop complaining then those issues will not be resolved and Linux will not improve.

The biggest single issue holding back Linux is the fanboy culture which surrounds it.

---

### Post by Telengard C64 on 2010-07-23
Free Software is superior.  Even when Free Software development lags behind the proprietary models, I will still believe in the superiority of Free Software. If you don't agree, I'm not about to persuade you otherwise.

I do agree that saying things like "Linux is free" is not an excuse for misbehaving, underdeveloped software. The fact is that lots of software makes it into distros without sufficient development and testing to make it useful for all users. Other OSes may have the luxury of taking all the time they need to get their stuff working in every possible case, but Linux developers' time is far too valuable to take such an approach. We are not Windows, Mac, or Solaris. We are Gnu/Linux.

I think we all must have had embarrassing moments when trying to show off Ubuntu to friends and relatives. It happens. If they can't see the big picture, the true value of Ubuntu and Gnu/Linux, then its their loss. Don't let it bother you too much.

I used to get furious about the same clipboard problems that you are suffering with. Then I discovered Klipper (KDE user here). Klipper automatically remembers the last 15 text snippets I copied from any application. I just press ctl+alt+v and select which one I want to paste. Brilliant! Doesn't something equivalent exist for the Gnome side?

---

### Post by clanky on 2010-07-23
> **Telengard C64 said:**
> The fact is that lots of software makes it into distros without sufficient development and testing to make it useful for all users. Other OSes may have the luxury of taking all the time they need to get their stuff working in every possible case, but Linux developers' time is far too valuable to take such an approach. We are not Windows, Mac, or Solaris. We are Gnu/Linux.

What the...

I don't even...

How can a Linux developers time be too valuable to make a system which doesn't have buggy software?

How can it be OK for Linux to not be as good as Windows, OS X, or Solaris and still expect to compete with them?

---

### Post by aysiu on 2010-07-23
I wrote about this a couple of years ago in a blog entry called [The Linux community’s mixed messages](http://www.psychocats.net/ubuntucat/the-linux-communitys-mixed-messages/)

Here's an excerpt: > **Free has to be worth something or nothing – make up your mind**
I see a lot of Linux users say that there is a popular misconception that free means lesser in quality. The basic idea is that people are skeptical of free products, but we know free products can be of very high quality. 

But if someone complains about Linux, then all of a sudden Linux users say “Why don’t you ask for refund?” or “It’s free. How can you complain about something that’s free?”

---

### Post by Goolie on 2010-07-23
You know, I always wondered why copy-paste didn't work.  I figured it had something to do with me closing the program i copied from!

I'm sure glad that got brought up here.  Personal SOLVED here!

Haha!

I see alot of people have problems, but after 4 PC's fresh installs of Ubuntu I have yet to have any serious problems.

=\

---

### Post by doublewitt on 2010-07-23
> **clanky said:**
> The biggest single issue holding back Linux is the fanboy culture which surrounds it.

If I installed Ubuntu and literally had only a couple of minor issues with it AND I am happy with my new OS, and then decide to "say so" on forum threads, why should I be tagged into a silly fanboy culture? When you are happy/satisfied with a product or service (paid or free), it's normal for clients to express thier "satisfaction" without being branded as a fanboy. Are you trying to stop people from expressing their positive viewpoint...? Just what are you getting at? After a couple of issues, as I mentioned, I did read comments that "it works for me!" and this does not hinder me or frustrate me but rather encourages me to plunge on as I realize that it works for others - so _there must be a solution for me_. That stimulates more motivation on my part to keep looking for the answer... Personally, I see the accused "fanboy club" as a positive resource. I'm glad it's there. I tend to look at people's motives and objectives behind the posts... Could you imagine getting on the forum and seeing nothing like that, that would be discouraging... anyways, I firmly *disagree* with the above statement... Ubuntu's "fanboy club" is made up of "people helping people" and Ubuntu's forum has an extremely good reputation for helping others. I don't agree with people who look for opportunities to make "public broadcasts" and attack the Linux or Ubuntu project. There's not much sense to that. It's a clear waste of time... especially considering the fact that when these rambling complainers make their claims, they completely forget how much pain it was with the Windows platforms over the years. Now you can look at hundreds or even thousands of websites with "bug reports" and you can visit Microsoft.com's endless bugs lists and if that doesn't exasperate you, then why should the relatively short bug list with Linux or Ubuntu bother you...? They constantly compare the OS with Microsoft or Mac but always forgetting about the exhaustive issues over the past years... that's rather strange! It sounds like we're attacking Ubuntu's fan club to promote another one...! Seems like we're playing a game...

---

### Post by Telengard C64 on 2010-07-23
> **clanky said:**
> How can a Linux developers time be too valuable to make a system which doesn't have buggy software?

Microsoft and Apple invest tons of money and years of time into each OS release, and they still don't get it right much of the time. You can't hold Linux developers to the same standard because most of them don't work like that. I honestly believe Gnu/Linux users are better of because our developers do not follow the same development model.

> How can it be OK for Linux to not be as good as Windows, OS X, or Solaris and still expect to compete with them?

How can it possibly be a problem? I think too many people have impossible expectations for the magical Linux desktop to appear and solve all problems. It won't happen. And really, I don't want Linux to compete with Windows, Mac, and Solaris. I want Linux to be Linux, and let the distros and users customize it however they like.

---

### Post by endotherm on 2010-07-23
> **chessnerd said:**
> Every once and a while, I'll see a post about a problem in Linux and the person will express their frustration with Linux as a whole and openly question why they even use it. We've all seen those.

Then, invariably, there will be a response that basically goes like this:

But, is "Linux is free" a valid excuse? 

I agree, it's a lame cop out, but at the same time, it is a 100% legitimate response to someone coming here to our hangout, and telling us that it can't possibly work, and that we must be daft to use it. matches the tone and tenor of the op precisely. if they wanted to learn an answer they'ed research the question. if they want to force _**us**_ to answer to them as to why they are having trouble though, like it's our personal responsibility to make ubuntu work for them, then that would be the most favorable response they'd get from me.

if someone asks me the question earnestly, I will give an earnest answer based on my personal situation and preferences. if they just want to vent frustrations, troll, or tell us in no uncertain terms "how it should be" though, I am not nearly so cooperative. why feed the trolls?

---

### Post by bigboy_pdb on 2010-07-23
When you think about it, people should attempt to avoid using the terms "free" or "freedom" since they have different meanings depending on the context. That's one of the general problems with Linux communities. People use language that generates an emotional response without agreeing on the meanings of the words they're using.

With respect to the response that "the software is free" in this context clearly it would mean that it doesn't cost any money. To the end user that doesn't matter since it consumes time, which can be more valuable than money. If you're a business and you're using poorly developed free software, it costs both time and money.

I agree that this isn't an excuse, but at the same time you have to consider the other side. Developing software, well or poorly, consumes a lot of time for the developers. Think about the release cycles between software within proprietary companies where that's many people are developing one product every day for a living. Anyone who is developing free software is donating a lot of their time away. Many people are using it in order to save money and they don't usually care about the alternate meanings of freedom.

On the other hand there are problems with the quality of free software in many projects. It doesn't just stem from lack of time though. A lot of it comes from the "freedom of choice" that communities value. There are so many duplicated projects where people do the same work as others because of disagreements.

When you consider the extreme pride, prejudice, and fanaticism that can come from people within Linux communities (as well as other communities), you can see why it is difficult for people to cooperate. Until we can make people more critical and less verbose, the best advice would be for people avoid posting unless you have helpful information that you would like to be given or unless you're being asked for help in a way that you would like to be asked. Some other good advice would be for people not to use words and phrases that aren't universally understood (such as freedom) or intended to needlessly generate emotional reactions (such as trolling, newbie, stupid).

---

### Post by clanky on 2010-07-23
> **doublewitt said:**
> If I installed Ubuntu and literally had only a couple of minor issues with it AND I am happy with my new OS, and then decide to "say so" on forum threads, why should I be tagged into a silly fanboy culture? When you are happy/satisfied with a product or service (paid or free), it's normal for clients to express thier "satisfaction" without being branded as a fanboy. Are you trying to stop people from expressing their positive viewpoint...? Just what are you getting at? After a couple of issues, as I mentioned, I did read comments that "it works for me!" and this does not hinder me or frustrate me but rather encourages me to plunge on as I realize that it works for others - so _there must be a solution for me_. That stimulates more motivation on my part to keep looking for the answer... Personally, I see the accused "fanboy club" as a positive resource. I'm glad it's there. I tend to look at people's motives and objectives behind the posts... Could you imagine getting on the forum and seeing nothing like that, that would be discouraging... anyways, I firmly *disagree* with the above statement... Ubuntu's "fanboy club" is made up of "people helping people" and Ubuntu's forum has an extremely good reputation for helping others. I don't agree with people who look for opportunities to make "public broadcasts" and attack the Linux or Ubuntu project. There's not much sense to that. It's a clear waste of time... especially considering the fact that when these rambling complainers make their claims, they completely forget how much pain it was with the Windows platforms over the years. Now you can look at hundreds or even thousands of websites with "bug reports" and you can visit Microsoft.com's endless bugs lists and if that doesn't exasperate you, then why should the relatively short bug list with Linux or Ubuntu bother you...? They constantly compare the OS with Microsoft or Mac but always forgetting about the exhaustive issues over the past years... that's rather strange! It sounds like we're attacking Ubuntu's fan club to promote another one...! Seems like we're playing a game...

I'll cut you a deal, if you edit that with some punctuation and formatting so that I can actually read it then I will answer it.

---

### Post by Telengard C64 on 2010-07-23
> **bigboy_pdb said:**
> When you think about it, people should attempt to avoid using the terms "free" or "freedom" since they have different meanings depending on the context.

This seems like a reasonable criticism. Would you be more satisfied if people referred to [_Free Software_](http://www.gnu.org/philosophy/free-sw.html) (with a link to the definition) instead?

---

### Post by clanky on 2010-07-23
> **Telengard C64 said:**
> Microsoft and Apple invest tons of money and years of time into each OS release, and they still don't get it right much of the time. You can't hold Linux developers to the same standard because most of them don't work like that. I honestly believe Gnu/Linux users are better of because our developers do not follow the same development model.



How can it possibly be a problem? I think too many people have impossible expectations for the magical Linux desktop to appear and solve all problems. It won't happen. And really, I don't want Linux to compete with Windows, Mac, and Solaris. I want Linux to be Linux, and let the distros and users customize it however they like.

I still don't understand how you can claim that free software is superior and then say that it is OK for Linux developers to allow buggy software to be included.

I do however agree with you on the magical expectations bit. Personally I don't think Linux will ever be more than a niche OS in desktop terms and for me that is OK, Linux should concentrate on being a good Linux system and not on trying to create a Windows / OS X clone, you never win the race by trying to keep up with the leader.  My issue is with those who try to push Linux as a replacement for Windows and then make lame excuses when it doesn't perform as well.

---

### Post by doublewitt on 2010-07-23
> **chessnerd said:**
> But, is "Linux is free" is no excuse.

There is an obvious difference between "Linux is free" and "Windows - you pay for" statements or policies. "Paid for" services usually have loads more "development" resources while "free" usually implies people working in their spare time and out of goodwill with no renumeration. And yes, realistically speaking, you cannot have the same expectations from both. I think that's just common sense. Why debate the issue? Anyways, when someone posts something that's not helpful or relevant, I just overlook it and move on...

---

### Post by clanky on 2010-07-23
> **Telengard C64 said:**
> This seems like a reasonable criticism. Would you be more satisfied if people referred to [_Free Software_](http://www.gnu.org/philosophy/free-sw.html) (with a link to the definition) instead?

In the context of this thread, both definitions are equally valid, while the freedom (speech) of Linux is fantastic and its freeness (beer) is fantastic, neither excuse poor technical performance and neither will bring the popularity that so many seem to want.

---

### Post by clanky on 2010-07-23
> **doublewitt said:**
> There is an obvious difference between "Linux is free" and "Windows - you pay for" statements or policies. "Paid for" services usually have loads more "development" resources while "free" usually implies people working in their spare time and out of goodwill with no renumeration. And yes, realistically speaking, you cannot have the same expectations from both. I think that's just common sense. Why debate the issue? Anyways, when someone posts something that's not helpful or relevant, I just overlook it and move on...

The major Linux distros are not created by volunteer coders doing stuff out of the kindness of their hearts.

Ubuntu is created by Canonical who's business model is to give the software away for free and to charge businesses who use it for support, as such they rely on the many home users to effectively test run their software for them.

RedHat do the same thing with fedora, although in that case they actually release the testing version as a separate distro, but in both cases the OS's are created by paid professional developers and as they are both advertised as being suitable for business use then IMHO, yes, you can expect the same standards, if you argue that Linux users should somehow accept lower standards then you cannot argue that Linus is on a par with other OS's

I firmly believe that Linux has the potential to compete on the desktop, but that it never will until people stop making excuses for the problems and start addressing them.

---

### Post by doublewitt on 2010-07-23
Honestly, I don't think anyone on this forum uses the "free Linux" statement as an excuse. Those statements tend to be misinterpreted by "frustrated" people and so they fail to see the motives and objectives behind such posts. In many cases, people come on the forum expecting/demanding exactly the same as Windows or other and that's why these "freedom" statements are posted. You have to give consideration to the fact that "freedom" implies less resources. But nonetheless, while we talk about "Free Linux", I think that the current development trend is outstanding. Ubuntu has replaced my traditional OS on many computers with wonderful success!

---

### Post by marshmallow1304 on 2010-07-23
> **clanky said:**
> I'll cut you a deal, if you edit that with some punctuation and formatting so that I can actually read it then I will answer it.

Hey, the post was free...

---

### Post by doublewitt on 2010-07-23
> **clanky said:**
> The major Linux distros are not created by volunteer coders doing stuff out of the kindness of their hearts.

Ubuntu is created by Canonical who's business model is to give the software away for free and to charge businesses who use it for support, as such they rely on the many home users to effectively test run their software for them..
True to some degree - but Microsoft "resources" are far greater - more developers - more money,  more power and so on... it's obvious enough isn't it? You want to compare Goliath to David? There are also freewill contributions alongside and especially for softwares...

Perhaps I should have specified between OS and software developments...

[COLOR="Blue"]Just a comparison:
[/COLOR]Can you expect the same results from a 2-man company compared to another with 3 thousand men? C'mon...

---

### Post by clanky on 2010-07-23
I agree with the bit about demanding exactly the same as Windows, but I have seen the "it's free, don't complain" nonsense used as a comeback when people complain that sound doesn't work or that their keyboard suddenly stopped working after a new release.

There have been several Linux bugs which, had they happened in Windows, would have had the fanboys screaming from the rooftops about how this is going to be the end of Micro$haft, but when they happen in linux they are either denied or trivialised, this is what I meant about the fanboy culture holding back Linux development.

---

### Post by clanky on 2010-07-23
> **marshmallow1304 said:**
> Hey, the post was free...

/winthread

---

### Post by Telengard C64 on 2010-07-23
> **clanky said:**
> I still don't understand how you can claim that free software is superior and then say that it is OK for Linux developers to allow buggy software to be included.

As I said, I'm not trying to persuade you into believing as I do. My faith in [_Free_](http://www.gnu.org/philosophy/free-sw.html) and open source development is a built on a foundation of years of frustration with proprietary/closed software. In other words, it is a personal journey which led me to this faith, and I don't expect any one else's journey to be the same.

I will try sharing an anecdote with you which may enlighten or entertain you. This actually happened some months ago and my memory fades rather quickly nowadays. Feel free to laugh or criticize as you wish.

I was having problems with a certain program, and went to the project's IRC channel on Freenode. I posted a description of the problem and idled several hours until one of the devs dropped in to answer.

He explained that the Linux version had been largely unmaintained since it was ported from the Windows source years before. At this point he was the only maintainer of the Linux port and I got the feeling he had only recently joined the project. He also stated that he was working to bring the Linux version up to par with the Windows version.

He asked me which version I had and how I had installed. After I explained that I had gotten it from Ubuntu's repos he asked which version of Ubuntu and I told him Kubuntu Hardy 8.04. He was able to reproduce the problem and concluded that I needed newer versions of certain libraries to fix the bug.

He helped me update my libraries and set up my build environment, SVN I think, and download the latest development source. When I tried to build there were some errors, again related to libraries.

Over the course of about a week we worked together over in the channel to isolate the cause of problems and improve the build process until it finally worked.

That is the Gnu/Linux development model. It works, and I like it that way. Thank goodness we don't have to blindly accept whatever garbage some monolithic corporate entity imposes on us. We are free to choose our own software, participate in development, and create for ourselves the solutions which best suit our needs.

---

### Post by doublewitt on 2010-07-23
> **clanky said:**
> I agree with the bit about demanding exactly the same as Windows, but I have seen the "it's free, don't complain" nonsense used as a comeback when people complain that sound doesn't work or that their keyboard suddenly stopped working after a new release.
I have seen it also, it's true, and yes, some misuse the quoted statement, but many forum members have developed this reaction because of people posting with a negative slant... complaining won't get the help one requires... many come with their problem with a hard "complaining" tone - and what do you expect? And so, when answers like "don't complain" appear, it implies more like "search and discover"... there is a philosophy behind the Linux world - it's not the same as the big "M". It's an entirely different approach. It's true that an answer like that is way too short and the meaning is often misunderstood or unperceived but - just move on - get what you need - jump the hurdle, keep going... that's the best advice I can give you (if you don't mind)...

---

### Post by bigboy_pdb on 2010-07-23
> **Telengard C64 said:**
> This seems like a reasonable criticism. Would you be more satisfied if people referred to [_Free Software_](http://www.gnu.org/philosophy/free-sw.html) (with a link to the definition) instead?

It's entirely up to you, but if it can be worded in another way then it's better to use different words. For example, instead of saying, "the software is free", you could make a better point with a few more words by saying, "Volunteers spend a lot of their limited extra time writing the software. Proprietary software is written by development teams who write code almost every day." The first statement is directed at the individual, implying that he/she has the problem and should accept the software as it is. The second indicates that human resources are limited and gives a hidden implication that help is needed. This is less likely to offend someone and more likely to attract help.

Another problem that I didn't mention can be seen within this thread and relates back to emotions, pride, and fanaticism. It shouldn't be hard to see why this is problematic.

[LIST]
[*] Tell as many people that you can that Linux is better than anything else.
[*] Make everyone want to use Linux.
[*] Some new people try Linux and are having problems.
[*] Linux cannot fail because it is superior. The user is the problem. Make that clear to them.
[*] Repeat as necessary.
[/LIST]

---

### Post by endotherm on 2010-07-23
> **bigboy_pdb said:**
> ...

Another problem that I didn't mention can be seen within this thread and relates back to emotions, pride, and fanaticism. It shouldn't be hard to see why this is problematic.

[LIST]
[*] Tell as many people that you can that Linux is better than anything else.
[*] Make everyone want to use Linux.
[*] Some new people try Linux and are having problems.
[*] Linux cannot fail because it is superior. The user is the problem. Make that clear to them.
[*] Repeat as necessary.
[/LIST]


your point is valid, and those are definetly negative side affects. at the same time however, I'm sure you can see why OSS and Linux would be impossible without pride and emotional attachment. what some might call zealotry others might call passion and drive. obviously it took a lot of passion and drive to develop an OS and ecosystem the way the linux foundation have. OSS is an ideology after all. some people just take it further than others. also some people can't accept that they aren't objectively right in regards to subjective concerns, and will argue until blue in the face.

---

### Post by Lucifer The Dark on 2010-07-23
I'd rather have "Free & not exactly perfect" than "Damn expensive & total shiite" Linux beats Windows & yes I've used EVERY version of Windows.

---

### Post by Telengard C64 on 2010-07-23
> **bigboy_pdb said:**
> you could make a better point with a few more words by saying, "Volunteers spend a lot of their limited extra time writing the software. Proprietary software is written by development teams who write code almost every day."

Entirely too wordy to be useful in everyday conversation.

---

### Post by bigboy_pdb on 2010-07-23
> **endotherm said:**
> I'm sure you can see why OSS and Linux would be impossible without pride and emotional attachment

Actually neither is necessary. Many people support organizations without being prideful about it. I've volunteered in a number of organizations without boasting. When the organization has meaning, most people support it not so that they can boast, but because it gives their life meaning and it makes them happy to know that they are doing good works. Emotional attachment is not necessary either, but it does make a difference in morale and the progress individuals make.

There are better arguments to promote free software than because of the "freedom". One is because it can provide advantages to people who are disadvantaged, such as people who are impoverished. Another is that small organizations that have purpose can put donations or other money to better use. Yet another, is that it promotes education in a number of ways.

The problem is that the "freedom" concepts that many people rally around don't have concrete agreeable meanings and when they do, their worth is arguable. There are far more important things that can be done than writing or supporting free software for the sake of "freedom".

---

### Post by Telengard C64 on 2010-07-23
> **bigboy_pdb said:**
> The problem is that the "freedom" concepts that many people rally around don't have concrete agreeable meanings and when they do, their worth is arguable. There are far more important things that can be done than writing or supporting free software for the sake of "freedom".

My [_freedoms_](http://www.gnu.org/philosophy/free-sw.html) are by far the most important and compelling reasons why I choose to use Gnu/Linux systems.

---

### Post by RiceMonster on 2010-07-23
> **bigboy_pdb said:**
> there are far more important things that can be done than writing or supporting free software for the sake of "freedom".

+9001

One of the things I dislike about Linux is all the moralistic BS some people surround it with. It's just an OS already.

---

### Post by endotherm on 2010-07-23
> **RiceMonster said:**
> +9001

One of the things I dislike about Linux is all the moralistic BS some people surround it with. It's just an OS already.
welcome to the concept of "subjectivity". some things are to you, differant than they are to others. to me Linux is both a kernel and a manifestation of a philosophy I hold. i don't hold it as tightly nor as loosely as others. to you it is just an os, and that is fair. it doesn't make it BS that it is differant to me however

---

### Post by RiceMonster on 2010-07-23
> **endotherm said:**
> welcome to the concept of "subjectivity". some things are to you, differant than they are to others.

Thanks for sharing. I had no idea.

Welcome to the concept of "subjectivity", in which I am allowed to think what I want of other view points.

---

### Post by endotherm on 2010-07-23
> **bigboy_pdb said:**
> Actually neither is necessary. Many people support organizations without being prideful about it. I've volunteered in a number of organizations without boasting. When the organization has meaning, most people support it not so that they can boast, but because it gives their life meaning and it makes them happy to know that they are doing good works. Emotional attachment is not necessary either, but it does make a difference in morale and the progress individuals make.

There are better arguments to promote free software than because of the "freedom". One is because it can provide advantages to people who are disadvantaged, such as people who are impoverished. Another is that small organizations that have purpose can put donations or other money to better use. Yet another, is that it promotes education in a number of ways.

The problem is that the "freedom" concepts that many people rally around don't have concrete agreeable meanings and when they do, their worth is arguable. There are far more important things that can be done than writing or supporting free software for the sake of "freedom".

pride in your accomplishments != arrogance or boasting.

tell me that you can write 50k lines of code and see it deployed around the world without being proud of code and getting a little attached to it. that is true both in the open and closed source world. the differance is that pride is held internally (like the code) , in a closed environment, but with direct open access to the developers as OSS does it, there isn;t the sheild of PR and Marketing.

---

### Post by bigboy_pdb on 2010-07-23
> **endotherm said:**
> pride in your accomplishments != arrogance or boasting.

Boasting is a consequence of pride. Pride affects how you act in every way and I often find people's actions as a result of it are negative. Anything good that can come out of being prideful could easily be done without it as well.

> **endotherm said:**
> tell me that you can write 50k lines of code and see it deployed around the world without being proud of code and getting a little attached to it

Being momentarily and unintentionally prideful is different from encouraging people to be prideful. Also, who cares about the number of lines? How long will it last for? What good lasting effects can be expected from it? In the abstract case, none that you could have foreseen. That doesn't mean that in every case writing code doesn't matter, but that coding for the sake of coding, for general human use, or even purely for enjoyment doesn't have the same substance as doing it with intention for a worthwhile cause (such as fixing software that you know a charity is using and having problems with).

---

### Post by libssd on 2010-07-23
I don't think the "Linux is Free" argument is why a gap remains between Linux and commercial OS's like OS X and Windows. Market share is a much bigger driver.

In the case of Apple, the same company makes both the OS and the hardware, so they damned well better work well together. I still remember the chaos of the days when Apple licensed their OS to makers of Mac "clones". There were **always** compatibility issues.

In the case of Windows, if MS has 90% share of the desktop market, there is a huge motivation for hardware manufacturers to work closely with Microsoft to make sure their hardware works well with Windows. During development, the manufacturers can provide feedback to Microsoft, and vice versa. 

At least with Linux, if I have a problem, I can get knowledgeable help (and usually a solution -- or several) from an informed user community, rather than entering the hell of customer support.

---

### Post by uRock on 2010-07-23
There are lots of programmers out there that will code for money. If free stuff doesn't work, then feel free to pay for something that does. Not everyone expects free to be perfect, though ubuntu is very close to it for me.

So, why did you do away with Nouveau? It works great with my nVidia cards.

---

### Post by bigboy_pdb on 2010-07-23
I want to put this thread back on track.

> **endotherm said:**
> ... with direct open access to the developers, as OSS does it, there isn't the sheild of PR and Marketing

The PR and Marketing that some FOSS community members use is: when something is free, it's flaws are acceptable and it's not what's free that should be changed but you if you have a problem with it. Clearly, whether or not that's true is case dependant and those people shouldn't be taking it upon themselves to market something that doesn't belong to them, especially since many people who write free software, have completely different beliefs from them. If you were really to take those beliefs into consideration, you'd have far more licensing agreements than what are currently out there (such as GPL, LGPL, MPL, EPL, BSD License, etc.).

As a developer, I would prefer to know about the flaws in my software, but I would want to be told in an appropriate manner. Also, even if the original developer doesn't want to know about the problems in his/her program, another developer who is willing to fix them may want to know.

---

### Post by endotherm on 2010-07-23
> **bigboy_pdb said:**
> 
As a developer, I would prefer to know about the flaws in my software, but I would want to be told in an appropriate manner. Also, even if the original developer doesn't want to know about the problems in his/her program, another developer who is willing to fix them may want to know.
on that we can agree.

---

### Post by Nick_Jinn on 2010-07-23
I might be ok with purchasing proprietary software for Ubuntu from the Ubuntu web-store, to support Ubuntu and other developers....I wouldnt want the OS to become commercial and riddled with advertisements, but as long as most stuff was free I wouldnt mind paying to support a few polished programs or games if I could afford it....but if I felt like there was an attempt to hide the free stuff, I would probably walk away. 

There really isnt a huge amount of stuff I need really besides maybe some games....so it would be a tough market to sell in. Free stuff works great. The companies who produce it also get to use it free of charge, based on free technology. Its not all charity, though it ends up being charity. People benefit from the open source arrangement, especially people in poorer countries as well as people who just like freedom.

Linux makes a lot of money with their search engine though, and perhaps by offering support for certain services. Ubuntu created the market for UbuntuOne and the music store.....so that with Google revenue and the time I have invested, I do kind of expect something that at least lives up to the hype....and for me it does, though I know it can be buggy on some hardware.

---

### Post by WinterMadness on 2010-07-25
may new linux users end up with disapointment because many long time linux users often make exaggerated claims about what linux is.

using linux is sometimes like dumpster diving. Were all asking for the handouts from corporations, since much of the linux development comes from them. We are hypocrites if we speak of community.

Corporations cannot operate on a business model that foss users demand. They are just not built for it. On top of that we preach about community, so why dont we actually develop a unity and actively solve problems democratically?

---

### Post by SunnyRabbiera on 2010-07-25
Well I surely buy the excuse, considering that linux is independently funded and its support is mostly under the table, whie not 6the best excuse it certainly feels better for me to use a OS that I know has its drawbacks and accept the flaws as opposed to using a $200 OS that has simular bugs and wont fix them

---

### Post by uRock on 2010-07-25
> **WinterMadness said:**
> may new linux users end up with disapointment because many long time linux users often make exaggerated claims about what linux is.

using linux is sometimes like dumpster diving. Were all asking for the handouts from corporations, since much of the linux development comes from them. We are hypocrites if we speak of community.

Corporations cannot operate on a business model that foss users demand. They are just not built for it. On top of that we preach about community, so why dont we actually develop a unity and actively solve problems democratically?

I tell people all the time that I can do anything with Ubuntu that they can do with Windows, except for watching Netflix. 

Comparing Linux to dumpster diving is total B.S. I have reported bugs and beta tested and I am not employed by Canonical, which clearly labels me as community. Look in the [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310") sub-forum and you will see a lot of community people doing testing and creating fixes, so to say there is no community is telling a lie.

---

### Post by Nick_Jinn on 2010-07-25
The thing is Linux really CAN do everything people say it can.....the problem is that the noobs cant make it do all that, at first.


If you want people to be happy with Linux, do them a favor and install it for them.....I dont just mean run the installer for them, but enable the cool effects, Medibuntu, all the software appropriate for their interests, the drivers, give them some extravagant custom themes and eye candy, show them how a few things work.....trust me, they will be thriled.


If you just show them a link and say 'fend for yourself', they wont be happy.....even expecting them to trouble shoot on the forums is a bit much for all at once.



I do custom installations of linux for $40, and save peoples files when Windows gets a virus making their system unusable.....people are THRILLED, and I keep getting business based on word of mouth......Do you know why? Because I know what people like and I took the time to configure it for them instead of just handing them the default installation.

---

### Post by WinterMadness on 2010-07-25
> **uRock said:**
> I tell people all the time that I can do anything with Ubuntu that they can do with Windows, except for watching Netflix. 

Comparing Linux to dumpster diving is total B.S. I have reported bugs and beta tested and I am not employed by Canonical, which clearly labels me as community. Look in the [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310") sub-forum and you will see a lot of community people doing testing and creating fixes, so to say there is no community is telling a lie.

your bug reports are equivalent to a dumpster diver telling the chef his food could be better.

We are all looking for handouts from corporations trying to monetize linux, which is a fundamentally broken idea. This is why I suggested a democratic approach to linux, which would be far more effective.

---

### Post by Nick_Jinn on 2010-07-25
You can watch netflix on linux.

---

### Post by aysiu on 2010-07-25
> **Nick_Jinn said:**
> You can watch netflix on linux.
Streaming, not DVDs.

---

### Post by uRock on 2010-07-25
> **WinterMadness said:**
> your bug reports are equivalent to a dumpster diver telling the chef his food could be better.

We are all looking for handouts from corporations trying to monetize linux, which is a fundamentally broken idea. This is why I suggested a democratic approach to linux, which would be far more effective.
I am not expecting something for nothing. Windows has hired testers. And I don't think a chef would give a pooh if a dumpster diver complained. Most Linux distributors try to fix bugs that are reported.

I think you are speaking for yourself when you say "We are looking for handouts," because I give back to the community with time and time is money."

What would a democratic OS do? Force those with high end CPUs to give processes to those with cheap CPUs?

---

### Post by Nick_Jinn on 2010-07-25
> **aysiu said:**
> Streaming, not DVDs.


I watch DVDs on Ubuntu. Just install Medibuntu or use Mint.

---

### Post by SunnyRabbiera on 2010-07-25
> **aysiu said:**
> Streaming, not DVDs.

Thats the other way around, DVD yes, streaming no...
Unless someone knows how to get streaming working.

---

### Post by Nick_Jinn on 2010-07-25
I do a search and apparantly somebody claims to have done it. I think there is a youtube video for it....it didnt look simple though.

Watching commercial DVDs is simple with Medibuntu and automatic in mint.

---

### Post by aysiu on 2010-07-25
> **SunnyRabbiera said:**
> Thats the other way around, DVD yes, streaming no...
Unless someone knows how to get streaming working.
Sorry. My phrasing was bad. What I meant to say was that I was *talking about* streaming (not working), not talking about DVDs (which do work).

---

### Post by SpyderBite on 2010-07-25
Setup Windows FireFox in Wine and you can watch Netflix streaming just fine.

---

### Post by aysiu on 2010-07-25
> **SpyderBite said:**
> Setup Windows FireFox in Wine and you can watch Netflix streaming just fine.
If so, that's the first I've heard of it. Care to put together a step-by-step HowTo?

From [How to almost get Netflix Watch Instantly to work in Linux](http://linuxphilia.blogspot.com/2010/03/how-to-almost-get-netflix-watch.html): > It's about here that you'll notice a crash. Firefox in WINE doesn't like it when the Silverlight plugin tries to install and fails. When you repeat step 8, you'll notice that you actually get to the page where the video ordinarily plays, but the image is scrambled and Firefox soon crashes.

---

### Post by aysiu on 2010-07-26
Yeah, just tried Firefox in Wine to stream Netflix. Didn't work, as I knew it wouldn't. Got as far as prompting me to install the Silverlight plugin. When I tried to install Silverlight with Wine... nothing.

If you're going to claim you can get Netflix streaming on Linux to work, you have to provide a step-by-step tutorial and someone else (not you) has to use that tutorial and verify that it works.

Otherwise, it didn't happen.

---

### Post by uRock on 2010-07-26
Thankfully Netflix made a loadable disk to watch on the Wii. Saves me from booting Windows as often.

Off topic for sure, but hopefully with the Novell Windows deal going on they might be nice enough to help moonlight get the job done. I am not holding my breath.

---

### Post by bigboy_pdb on 2010-07-26
Linux distributions cannot do everything that Windows variants can. For example, there is a large amount of software that cannot be run on Linux distributions including many video games, which can be run on Windows.

Also, there's no such thing as a superior OS. What you find better is based on what you want to do. If I were a gamer and didn't need anything more than what Windows offers, I'd probably find Windows better because it would do everything that I need well. As a developer and someone who writes a lot of scripts, I find Windows doesn't handle these tasks as well as Ubuntu so I consider Ubuntu to be better.

It seems that a lot of people have missed the general point of the thread. It was that making excuses that are [red herrings]("http://en.wikipedia.org/wiki/Red_herring_%28logical_fallacy%29#Red_herring") for valid problems in any Linux distribution deters those problems from being fixed. It's a valid point and a lot of the responses are also [red herrings]("http://en.wikipedia.org/wiki/Red_herring_%28logical_fallacy%29#Red_herring").

---

### Post by Nick_Jinn on 2010-07-26
> **aysiu said:**
> If you're going to claim you can get Netflix streaming on Linux to work, you have to provide a step-by-step tutorial and someone else (not you) has to use that tutorial and verify that it works.

Otherwise, it didn't happen.


I dont have to do anything. Its not my prerogative to convince you either.

However, if you are curious, here is a how to.

[http://www.youtube.com/watch?v=ZuyPJFhVTxQ](http://www.youtube.com/watch?v=ZuyPJFhVTxQ)




And you are confused. You claimed DVDs dont work in Ubuntu....well, most of us use Medibuntu and watch all the DVDs and MP3s we want.

---

### Post by Nick_Jinn on 2010-07-26
> **bigboy_pdb said:**
> Linux distributions cannot do everything that Windows variants can. For example, there is a large amount of software that cannot be run on Linux distributions including many video games, which can be run on Windows.

Also, there's no such thing as a superior OS. What you find better is based on what you want to do. If I were a gamer and didn't need anything more than what Windows offers, I'd probably find Windows better because it would do everything that I need well. As a developer and someone who writes a lot of scripts, I find Windows doesn't handle these tasks as well as Ubuntu so I consider Ubuntu to be better.

It seems that a lot of people have missed the general point of the thread. It was that making excuses that are [red herrings]("http://en.wikipedia.org/wiki/Red_herring_%28logical_fallacy%29#Red_herring") for valid problems in any Linux distribution deters those problems from being fixed. It's a valid point and a lot of the responses are also [red herrings]("http://en.wikipedia.org/wiki/Red_herring_%28logical_fallacy%29#Red_herring").




Have you considered that there are reasons for using open source technology above and beyond doing whatever works best for your needs?

There is the issue of corporate control, the absurdity of patenting 'methods' as the fundamental technology, and the implications of  supporting alternatives under the General Public License vs the existign corporate hedgemony......a lot of people dont care about all that, but maybe we should. It could have a very real impact on what kind of future we will end up living in.....an egalitarian society based on free exchange between individuals and the sharing of knowledge, or a society where only a handful of powerful elite holds the 'rights' to do just about anything practical, and nobody can do anything without their permission or paying them a tax.

I posted a good documentary about this under the title "A patent on Math".

---

### Post by aysiu on 2010-07-26
> **Nick_Jinn said:**
> I dont have to do anything. Its not my prerogative to convince you either. I wasn't talking to you. I was talking to SpyderByte, who said [i]Setup Windows FireFox in Wine and you can watch Netflix streaming just fine.[/u] That is simply not true.

> However, if you are curious, here is a how to.

[http://www.youtube.com/watch?v=ZuyPJFhVTxQ](http://www.youtube.com/watch?v=ZuyPJFhVTxQ) Has nothing to do with watching Netflix streaming using Wine in Ubuntu. That's Netflix streaming in XP in VirtualBox.

> And you are confused. You claimed DVDs dont work in Ubuntu I did no such thing. I said Netflix streaming does not work in Ubuntu, but Netflix DVDs do.

---

### Post by the8thstar on 2010-07-26
"*Linux is free*" is not "*Linux is freedom*" nor it is "*Linux will set you free*" or even "*Linux is sugar-free*" (for the calorie conscious out there) or "*Linus Torvalds is free*" (like out of jail).

My first reaction when I read the motto "*Linux is free*" was to think "OK, that will cost me no money". To me it didn't imply my freedom as a person.

If the expression refers indeed to the users' freedom, someone please change it to make it grammatically acceptable.

---

### Post by uRock on 2010-07-26
> **bigboy_pdb said:**
> Linux distributions cannot do everything that Windows variants can. For example, there is a large amount of software that cannot be run on Linux distributions including many video games, which can be run on Windows.

It does everything I need, except Netflix. When I wanna game, I turn on one of the many game stations I own. When there is something I need to do using my PC, I can do it with a Linux application. There are free softwares for Linux that cost an arm and leg for Windows and the Linux versions work just as well. (I am not knocking Windows, because I have Windows installed as well.)

> Also, there's no such thing as a superior OS. What you find better is based on what you want to do. If I were a gamer and didn't need anything more than what Windows offers, I'd probably find Windows better because it would do everything that I need well. As a developer and someone who writes a lot of scripts, I find Windows doesn't handle these tasks as well as Ubuntu so I consider Ubuntu to be better.

I agree with Linux being easier for writing scripts. I haven't written anything major, but I have made a few little applications combining Linux utilities to do an easy task my way. The batch files I made in Windows were nowhere near as good.

> It seems that a lot of people have missed the general point of the thread. It was that making excuses that are [red herrings]("http://en.wikipedia.org/wiki/Red_herring_%28logical_fallacy%29#Red_herring") for valid problems in any Linux distribution deters those problems from being fixed. It's a valid point and a lot of the responses are also [red herrings]("http://en.wikipedia.org/wiki/Red_herring_%28logical_fallacy%29#Red_herring").

An easy comparison, when my wife bought a Hyundai I expected problems on a regular basis. When I bought my V-Dub, I expected quality engineering. Both were perfect expectations that have proven true in my experience. With Linux on the other hand, I have higher expectations for Linux or more importantly Ubuntu than I do for Windows, because Ubuntu is growing and it has an awesome design team that is working to make Ubuntu a great alternative to Windows. Sure, there are things that need tweaking yet, but they can't make everyone happy.

As far as people arguing with aysiu over petty stuff like DVD playback, we know aysiu has made major contributions to include pages explaining how to set up the system with Medibuntu and such. Let's give a bit over credit where it is due.

Cheers & Beers,
uRock

---

### Post by WinterMadness on 2010-07-26
> **uRock said:**
> I am not expecting something for nothing. Windows has hired testers. And I don't think a chef would give a pooh if a dumpster diver complained. Most Linux distributors try to fix bugs that are reported.

I think you are speaking for yourself when you say "We are looking for handouts," because I give back to the community with time and time is money."

What would a democratic OS do? Force those with high end CPUs to give processes to those with cheap CPUs?

Exactly, a chef wouldnt care, just like a corporation who cant really monetize what their product is.

No, a democratic linux  OS would give focus to the OS, and give it a clear direction. This way, user needs and desires are as clear as they can be. Executives shouldnt be deciding things for communities just like a dictator shouldnt be deciding things for people.

Sure we can beg Canonical to do things our way, maybe theyll listen sometimes. But if you think they are going to be putting all of our needs before trying to make money youre kidding yourself.

---

### Post by uRock on 2010-07-26
> **WinterMadness said:**
> Exactly, a chef wouldnt care, just like a corporation who cant really monetize what their product is.

No, a democratic linux  OS would give focus to the OS, and give it a clear direction. This way, user needs and desires are as clear as they can be. Executives shouldnt be deciding things for communities just like a dictator shouldnt be deciding things for people.

Sure we can beg Canonical to do things our way, maybe theyll listen sometimes. But if you think they are going to be putting all of our needs before trying to make money youre kidding yourself.

They are building Ubuntu to fit my needs. They can't cater to everyone's needs because everyone has different needs. **_Democracy doesn't work._** Mark is developing the company to which he is funding the way he wants to. If it isn't your bowl of soup then create and finance your own OS and build it to what the small group of voters needs. Or just move the buttons back to the right like many other users have.

Ubuntu does have a direction. It is the future. They are boldly doing what no other Linux has done. They are creating their own OS that isn't replicating Windows and they are doing a damn good job with it. Sometimes I have to play the role of a fan boy.

---

### Post by WinterMadness on 2010-07-26
> **uRock said:**
> They are building Ubuntu to fit my needs. They can't cater to everyone's needs because everyone has different needs. **_Democracy doesn't work._** Mark is developing the company to which he is funding the way he wants to. If it isn't your bowl of soup then create and finance your own OS and build it to what the small group of voters needs. Or just move the buttons back to the right like many other users have.

Ubuntu does have a direction. It is the future. They are boldly doing what no other Linux has done. They are creating their own OS that isn't replicating Windows and they are doing a damn good job with it. Sometimes I have to play the role of a fan boy.


No they arent building for your needs theyre building it the way they want to. Which is why democracy is needed, to focus on what the most common needs are

Actually Democracy works just fine, its capitalism that fails every single test thats thrown at it.

I use KDE, why would I need to do that?


Ubuntu really isnt that bold, its not very daring, and its not *_that_* different from debian.

---

### Post by uRock on 2010-07-26
Firefox                Yes
Thunderbird         Yes
OpenOffice.org     Yes
Rhythmbox          Yes
AppArmor            Yes
IP Tables             Yes
IRC-Chat             Yes
VBox                   Yes
Pidgin                  Yes
My Printer            Yes
GIMP                   Yes
Wireshark, Snort, Zenmap, and everything else I need is here or easily installed.

Mark lead the way with setting up a great distro.

Kudos!
uRock

---

### Post by Yes on 2010-07-26
So that's your definition of a distro boldly doing what no other distro has done?  Just including a ton of programs with the default install?

---

### Post by uRock on 2010-07-26
> **Yes said:**
> So that's your definition of a distro boldly doing what no other distro has done?  Just including a ton of programs with the default install?
There is the ayatana project along with many other innovations. If you don't like Ubuntu, then don't use it. Most of those I listed aren't default, but are easily installed.

---

### Post by Nick_Jinn on 2010-07-26
> **uRock said:**
> They are building Ubuntu to fit my needs. They can't cater to everyone's needs because everyone has different needs. **_Democracy doesn't work._** Mark is developing the company to which he is funding the way he wants to. If it isn't your bowl of soup then create and finance your own OS and build it to what the small group of voters needs. Or just move the buttons back to the right like many other users have.

Ubuntu does have a direction. It is the future. They are boldly doing what no other Linux has done. They are creating their own OS that isn't replicating Windows and they are doing a damn good job with it. Sometimes I have to play the role of a fan boy.




Actually, Ubuntu is highly democratic....however, Linux does not practice "Democratic Centralism". Democratic centralism is not the only kind of democracy.

There is a type of Paticipatory democracy which is decentralized.....it was used by the Syndicalist unions during the Spanish civil war, and is also used by the Mondragon Corporation....This is the kind of democracy that most closely resembles linux.....linux is a federation of desktop unions.

---

### Post by WinterMadness on 2010-07-26
> **uRock said:**
> There is the ayatana project along with many other innovations. If you don't like Ubuntu, then don't use it. Most of those I listed aren't default, but are easily installed.

Whats the point of going to another distro when all of the majorly supported ones are ran by corporations with their own self interest in mind?

Whether you like it or not, the point of linux is community. If we dont like something WE are supposed to change it, even if its a corporations distro.

the problem is that we as a community are very poorly organized.

linux is about people, not profits.

---

### Post by uRock on 2010-07-26
> **WinterMadness said:**
> Ubuntu really isnt that bold, its not very daring, and its not *_that_* different from debian.
Debian is very bold. They don't have software that makes it really easy to install drivers. Firefox is not in their Synaptic. Chromium is not in their Synaptic. Their desktop is as ugly and old aged as it can possibly get.

I don't have anything against Debian. It works for their users (hopefully.) And Ubuntu is built off of it, but Ubuntu adds much of the usability that many are looking for. If you want stability with out dated applications, they have it.

---

### Post by WinterMadness on 2010-07-26
> **uRock said:**
> Debian is very bold. They don't have software that makes it really easy to install drivers. Firefox is not in their Synaptic. Chromium is not in their Synaptic. Their desktop is as ugly and old aged as it can possibly get.

I don't have anything against Debian. It works for their users (hopefully.) And Ubuntu is built off of it, but Ubuntu adds much of the usability that many are looking for. If you want stability with out dated applications, they have it.

the only distro that can really claim to have truly up to date software is arch.

Ubuntu is Debian with a few default software changes.

big whoop honestly.

---

### Post by uRock on 2010-07-26
> **WinterMadness said:**
> Whats the point of going to another distro when all of the majorly supported ones are ran by corporations with their own self interest in mind?

Whether you like it or not, the point of linux is community. If we dont like something WE are supposed to change it, even if its a corporations distro.

the problem is that we as a community are very poorly organized.

linux is about people, not profits.
What is it about ubuntu that you don't like so much that you think it needs to be voted out? Put some messages on Mark's blogs and tell him what you want. He reads his blog replies.

---

### Post by uRock on 2010-07-26
> **WinterMadness said:**
> the only distro that can really claim to have truly up to date software is arch.

Ubuntu is Debian with a few default software changes.

big whoop honestly.
You are obviously trolling. You say you want a democratic distro, but you haven't said what it is that they are doing wrong.

---

### Post by WinterMadness on 2010-07-26
> **uRock said:**
> What is it about ubuntu that you don't like so much that you think it needs to be voted out? Put some messages on Mark's blogs and tell him what you want. He reads his blog replies.

Obama reads his emails too.
Bush read his mail, he certainly knew his poll numbers.
CEO's occasionally read customer feedback

the point is, linux was MADE for community.
individuals with power have their own ideas and want to see them before others. its the nature of the beast.

democracy works better.

---

### Post by WinterMadness on 2010-07-26
> **uRock said:**
> You are obviously trolling. You say you want a democratic distro, but you haven't said what it is that they are doing wrong.

I didnt know you asked. MOST of my arguments tend to be linux centric rather than ubuntu only

1. Kubuntu needs to be cleaned up
2. Sound management needs to be better, when I hold in the volume up button it causes nasty freezing (in gnome only, this may have been fixed)
3. Disabling plymouth is risky
4. We need a better version of firefox for linux, and yes i know thats not ubuntus fault, or even linux's. but linux developers could fix its problems, and its not like we havent started, epiphany is far less buggy and uses the same engine
5. Numerous complaints about the x server
6. we need better 64 bit 
7. we can make linux more user friendly without sacrificing anything by making a few minor changes. all user permission requests should be done via gui in all major DE and WM
8. Gnome 3 is drawing harsh criticism, some people dont like KDE. We need to build them the way the community expects them to be.
9. We could vote for standardized package management without ruining all of the packages that are currently online. We can also make it easier to create rpms and deb files (or what have you)
10. Gimp isnt as powerful as it needs to be. We arent getting photoshop, and photoshop is over priced and proprietary.We have a fantastic starting point and we should pursue it
11. Better video/music editing software thats made with serious artists in mind. Linux actually has this already but the average linux user has no legal way of acquiring it. Not without hacking major studios anyway

just off the top of my head. even if you like some of these things youd be hard pressed to say they wouldnt be better off moving forward

---

### Post by Nick_Jinn on 2010-07-26
We could always make a democratically run distro of Ubuntu. Build in tools that do more to engage the community and to let them decide.

---

### Post by yester64 on 2010-07-26
> **chessnerd said:**
> Every once and a while, I'll see a post about a problem in Linux and the person will express their frustration with Linux as a whole and openly question why they even use it. We've all seen those.

Then, invariably, there will be a response that basically goes like this:


But, is "Linux is free" a valid excuse? 

I don't think so. To use an excuse like that is to say "you get what you pay for" and since you pay nothing, that implies that you get nothing.

A big part of the "free and open source software" movement is supposed to be that it's method is superior to that of the closed-source model. According to its proponents, free/libre software isn't supposed to be a cheap knock-off or a "free alternative". It is supposed to be better.

But apparently it isn't, and other excuses like lack of commercial hardware support are only a part of the problem. Lucid has problems with my older desktop's nVidia Riva TNT2 graphics card, even though it worked fine in Jaunty. That isn't a fault of the hardware company, that's a regression. 

Then there are things that are just embarrassing, like that we still have clipboard issues. I always need to open up gedit and paste there so that I know my text won't get lost in the black hole that is Linux clipboard support, which it does at least 50% of the time. I had this happen when using my computer with my sister once and she laughed out load at the stupidity of it.

We can't keep saying "well, Linux is free" like that makes the problems go away. Either Linux is worthy of being a desktop OS or it isn't. Price doesn't matter.

I could post a list of my ideas of what Linux needs. I could post a string of demands for the Ubuntu devs. But I won't. 

All I ask is that people on this forum stop trying to use this lame excuse. It isn't constructive and just makes Linux look bad. 

If you disagree with me, and still think that "Linux is free" is a perfectly valid excuse, fine. But I'll tell you this: My opinions are free...

I think you ask the wrong questions.
Linux is a evolving project where people fulltime working on it and continually working on it.
Linux does not supposed to be better per se. It has a different approach to deliver.
And, there is not just one headquarter with one Bill Gates or Steve Jobs who tell everyone where the wagon goes.

For the most part, Linux works just fine.
Most important to me is the fact, that it is an operation system that is available to people all over the world for free, so that they can participate in global communication over the web.

How long do you expect to work with a hardware that was produced a decade ago.
There can be many problems i don't know. Hardware conflicts or simply support.
Its not an excuse but there might be reason i can not fathom right now.
Besides everyone can contribute to the developers by submitting a suggestions, bugs etc..
Or better, to participate on the beta's (which i never do).

After all, its a community project regardless which distro you use.

---

### Post by yester64 on 2010-07-26
> **aysiu said:**
> Yeah, just tried Firefox in Wine to stream Netflix. Didn't work, as I knew it wouldn't. Got as far as prompting me to install the Silverlight plugin. When I tried to install Silverlight with Wine... nothing.

If you're going to claim you can get Netflix streaming on Linux to work, you have to provide a step-by-step tutorial and someone else (not you) has to use that tutorial and verify that it works.

Otherwise, it didn't happen.

No, i don't think it will work.
So far i think there are API's missing to get it work. I did succeed once to install silverlight, but i wasn't able to play anything.
Even if your firefox says its internet explorer.
Maybe you need .NET installed. Haven't tried that.

---

### Post by Nick_Jinn on 2010-07-26
The guy in the video got it working.....maybe you just dont have the right hardware or configuration for it? What are you running? An atom processor? What video card do you have?

---

### Post by yester64 on 2010-07-26
> **Nick_Jinn said:**
> The guy in the video got it working.....maybe you just dont have the right hardware or configuration for it? What are you running? An atom processor? What video card do you have?

That was Virtual Box. I was talking about native running without Windows. I don't need it at the moment, but its a way to do.

---

### Post by WinterMadness on 2010-07-26
> **Nick_Jinn said:**
> We could always make a democratically run distro of Ubuntu. Build in tools that do more to engage the community and to let them decide.

personally i think if this forum had a vote at the end of every month or so and actually decided the fate of ubuntu, it would accelerate linux growth.

we can take a top down approach, whatever is demanded most gets fixed first, then we look at whats second etc.

we can even vote on brand new things.

---

### Post by Chronon on 2010-07-26
> **Nick_Jinn said:**
> 
And you are confused. You claimed DVDs dont work in Ubuntu....well, most of us use Medibuntu and watch all the DVDs and MP3s we want.

You still seem confused even after Aysiu clarified the meaning of the prior post.

The youtube video you linked requires you to run Windows inside of a VirtualBox. This isn't streaming Netflix in Ubuntu at all.  It's streaming it in Windows running as a guest in a virtual system.

---

### Post by Brannyh on 2010-07-26
I don't really believe in the cost free philosophy, i think it should be a muti-billion dollar cooperation like Apple and Microsoft and to cost money so it would have more support and more users.

---

### Post by RevengeOfTheToxicRodent on 2010-07-26
> **chessnerd said:**
> Every once and a while, I'll see a post about a problem in Linux and the person will express their frustration with Linux as a whole and openly question why they even use it. We've all seen those.

Then, invariably, there will be a response that basically goes like this:


But, is "Linux is free" a valid excuse? 

I don't think so. To use an excuse like that is to say "you get what you pay for" and since you pay nothing, that implies that you get nothing.

A big part of the "free and open source software" movement is supposed to be that it's method is superior to that of the closed-source model. According to its proponents, free/libre software isn't supposed to be a cheap knock-off or a "free alternative". It is supposed to be better.

But apparently it isn't, and other excuses like lack of commercial hardware support are only a part of the problem. Lucid has problems with my older desktop's nVidia Riva TNT2 graphics card, even though it worked fine in Jaunty. That isn't a fault of the hardware company, that's a regression. 

Then there are things that are just embarrassing, like that we still have clipboard issues. I always need to open up gedit and paste there so that I know my text won't get lost in the black hole that is Linux clipboard support, which it does at least 50% of the time. I had this happen when using my computer with my sister once and she laughed out load at the stupidity of it.

We can't keep saying "well, Linux is free" like that makes the problems go away. Either Linux is worthy of being a desktop OS or it isn't. Price doesn't matter.

I could post a list of my ideas of what Linux needs. I could post a string of demands for the Ubuntu devs. But I won't. 

All I ask is that people on this forum stop trying to use this lame excuse. It isn't constructive and just makes Linux look bad. 

If you disagree with me, and still think that "Linux is free" is a perfectly valid excuse, fine. But I'll tell you this: My opinions are free...

Yes, yes and *yes*. 
I think you have reached the stage I hit about a year ago. Once you get past the 'zomg! this so awesome coz it aint Winblow$' thing, the flaws start to smack you in the face hard. The GNOME clipboard issue is a classic case. One of the main reasons I switched to KDE for a while is because it has a dementia-free clipboard.
The often quoted 'power of open source' actually turns out to be pretty hollow. On the software side, only really Firefox, OpenOffice, VLC, and to a degree GIMP show any real 'power'. Don't get me wrong: There is still a lot of Linux software that I like, but most of it lacks feature parity with its Windows equivalents (and sometimes version(s) ). 

I think I'll leave it at that before it starts to sound like an anti-Linus rant.

---

### Post by uRock on 2010-07-26
The percentage of people who actually come here looking for news and looking to participate in these conversations is small. We see a lot of people coming and going to get help from the support sub-forums, but not many of them sift through the forums to see what else is going on.

Canonical has a plan and I look forward to their innovations. They are getting ever so closer to making the perfect Netbook OS that stands a chance of taking market shares in that industry. It is just the matter of time and trial and errors.

> 1. Kubuntu needs to be cleaned up They have had a team working on this for some time. I am not sure of their progress as I have no use for eye candy when I am the only user on my system.
> 2. Sound management needs to be better, when I hold in the volume up  button it causes nasty freezing (in gnome only, this may have been  fixed)There is a bug report on this, which is taking a long time to get closed, but I think it is much less glitchy than it was when Lucid came out.
> 3. Disabling plymouth is risky Plymouth is a work in progress and the only way it would ever get worked out is if they put it out there and forced the reworking of the code. They aren't going to spend the money to develop Plymouth to work if it isn't being implemented enough to get the feedback that they need. I know it is buggy and yes it does give me grief from time to time.
> 4. We need a better version of firefox for linux, and yes i know thats  not ubuntus fault, or even linux's. but linux developers could fix its  problems, and its not like we havent started, epiphany is far less buggy  and uses the same engineI haven't had any problems with Firefox. I think the Linux version looks much better than the Windows version, though it could be due to default fonts.
> 5. Numerous complaints about the x server I have had no problem with it.
> 6. we need better 64 bit With flash, yes we need much better 64bit flash, but that is on Adobe.
> 7. we can make linux more user friendly without sacrificing anything by  making a few minor changes. all user permission requests should be done  via gui in all major DE and WMI disagree. With a few minutes of reading, permissions are really easy to understand. I am taking an Intro to Unix/Linux class and I skipped through the permissions chapter only stopping to read the three digit chmod commands to see how the numbers worked. I plan to search for and if needed create a howto on perfecting permissions.
> 8. Gnome 3 is drawing harsh criticism, some people dont like KDE. We  need to build them the way the community expects them to be.Ubuntu only alters the DEs a little. Ubuntu doesn't have to integrate GNOME3 if the devs find it to be crappy.
> 9. We could vote for standardized package management without ruining all  of the packages that are currently online. We can also make it easier  to create rpms and deb files (or what have you)The coding to do these tasks are beyond my knowledge, but I think that it could be plausible.
> 10. Gimp isnt as powerful as it needs to be. We arent getting photoshop,  and photoshop is over priced and proprietary.We have a fantastic  starting point and we should pursue itI may be wrong, but I think that GIMP is not altered by the Canonical teams other than possibly smoothing out dependency packages.
> 11. Better video/music editing software thats made with serious artists  in mind. Linux actually has this already but the average linux user has  no legal way of acquiring it. Not without hacking major studios anyway. I know a few people, including my wife, who mix music for performances. Two use Audacity in Ubuntu and the rest use proprietary Windows compatible programs.

I would love to see all of these things get tweaked and/or fixed. Expecting Canonical to do the work is unrealistic. They would have to hire a lot more developers to work on upstream projects. Plymouth and PulseAudio are the only things that I feel Canonical is responsible for.

---

### Post by WinterMadness on 2010-07-26
not to sound like a ****, but youve demonstrated a fundamental misunderstanding of what ive said. I am not asking canonical to do these things i am asking the community to do it, through better organization. The fact that people come here, and run into errors means they at the very least can offer a vote.

> **uRock said:**
> The percentage of people who actually come here looking for news and looking to participate in these conversations is small. We see a lot of people coming and going to get help from the support sub-forums, but not many of them sift through the forums to see what else is going on.


im not asking for only the people who come here to vote. It also does not mean we cannot advertise it greatly. If many people choose not to vote on linux issues then so what? Nobody expects all voters to turn out, and you shouldnt use that as an argument against my idea, because ive never heard of 100% voter turn out.
> 
Canonical has a plan and I look forward to their innovations. They are getting ever so closer to making the perfect Netbook OS that stands a chance of taking market shares in that industry. It is just the matter of time and trial and errors.

Netbooks are niche and theres no guarantee they will remain, especially with smart phones getting better all the time. Not to mention NBR is pretty irritating in my opinion.

> 
 They have had a team working on this for some time. I am not sure of their progress as I have no use for eye candy when I am the only user on my system.

So youre admitting the majestic company that you love so dearly has yet to get a solution to this problem? Seems like we need a new option here.

> 
There is a bug report on this, which is taking a long time to get closed, but I think it is much less glitchy than it was when Lucid came out.

Bug reports, while important havent been getting the job done. End user priority needs to be the most important thing
> 
 Plymouth is a work in progress and the only way it would ever get worked out is if they put it out there and forced the reworking of the code. They aren't going to spend the money to develop Plymouth to work if it isn't being implemented enough to get the feedback that they need. I know it is buggy and yes it does give me grief from time to time.

So youre admitting the limited ability of a company? 

> 
I haven't had any problems with Firefox. I think the Linux version looks much better than the Windows version, though it could be due to default fonts.


Performance issues on the linux version are widely known, and we still have the memory leak issue which is the main problem that the firefox team has yet to fix, which is why we must use the linux community to develop it correctly.

> 
 I have had no problem with it.
With flash, yes we need much better 64bit flash, but that is on Adobe.

Nope, plenty of software that linux users have grown accustomed to dont work well in 64 bit environments. In fact, canonical even said recently to not use 64 bit ubuntu.
> 
I disagree. With a few minutes of reading, permissions are really easy to understand. I am taking an Intro to Unix/Linux class and I skipped through the permissions chapter only stopping to read the three digit chmod commands to see how the numbers worked. I plan to search for and if needed create a howto on perfecting permissions.

Thats not the point. Many people dont have interest in computers but still want a safe and reliable system. And guess what? It can be done, quite easily. We are the ones trying to make linux more popular and WE have a logical obligation to do whats necessary, assuming it doesnt contradict any fundamental views we have.
> 
Ubuntu only alters the DEs a little. Ubuntu doesn't have to integrate GNOME3 if the devs find it to be crappy.

Again, thats not the point. Not implementing things and sticking with the current gnome is going to hurt linux(well, gnome mostly, because the kde team isnt afraid of thought out progress). Could you imagine 2020 and people are still using gnome as it is now? Linux NEEDS to have better DE integration in order to be more stable for most end users. So when you say "Ubuntu only alters the DEs a little." not only are you directly avoiding the whole point of my argument(that being democratic control of linux), youre resorting to an appeal to authority, the very authority in which i claim cannot meet the demands of its user base. I am not asking canonical to do these things or hire developers. I am asking the LINUX COMMUNITY to vote on priorities and develop.


> 
I may be wrong, but I think that GIMP is not altered by the Canonical teams other than possibly smoothing out dependency packages.

Point being? the gimp argument was not even directed at canonical.
> 
 I know a few people, including my wife, who mix music for performances. Two use Audacity in Ubuntu and the rest use proprietary Windows compatible programs.
That does not mean that true professionals(as in those who can earn income and support themselves on music alone) are going to use it, andthey dont. They use pro tools mostly.

> 
I would love to see all of these things get tweaked and/or fixed. Expecting Canonical to do the work is unrealistic.

thats why i dont want them to. Thats why i believe in democratic control of linux, as i stated originally.

> 
 They would have to hire a lot more developers to work on upstream projects.no they wouldnt.

---

### Post by uRock on 2010-07-26
Nevermind, I have nothing else to say on this matter. Democracy= Failure

---

### Post by overdrank on 2010-07-26
> **uRock said:**
> Nevermind, I have nothing else to say on this matter. Democracy= Failure

On that note, thread closed.

---

