---
title: "State of Ubuntu Regarding 64 bit?"
date: 2007-11-23
forum: Recurring Discussions
---

### Post by thoughts on 2007-11-23
Hello,

I have an Intel Core 2 Duo system, and I want to run a 64 bit OS mainly because it'll allow me to use more RAM.  I have 4 gigs in my system, but under 32 bit OSes, only 3.3 gigs of that RAM is usable.  I've booted from the Ubuntu amd64 live CD and verified that it does in fact make all 4 gigs usable (well, 3.8 gigs -- close enough).

My RAM is always just about full, because I have lots of virtual desktops for various client work, and I run 2 VMware virtual machines all the time, in addition to Firefox and Thunderbird which are memory hogs, plus GIMP, Pidgin, and Amarok which can all be pretty memory-hoggy too.  So I'd really like to be able to put 6 gigs of RAM in here, so that my system stops using the swap partition so much.

My question is, what's the current state of 64 bit Ubuntu?  In searching these forums, I see lots of posts about program compatibility issues, or apps just not being available in 64 bit, etc.  I understand that you can run 32 bit apps under the 64 bit OS, but does that always work, or does the app have to be written/compiled with that capability in place?

Mac OS X Leopard was just released, and it's a single OS that runs on both 64-bit and 32-bit hardware.  That contrasts with Microsoft's approach of releasing entirely separate 64-bit editions, and that appears to be the Ubuntu approach too, right?  That makes me a little nervous since I'll no longer be using the main/most popular version of Ubuntu, and naturally the main version gets more TLC than any other versions.

I guess my overall question is, if I switch to the amd64 version of Ubuntu, am I setting myself up for lots of hassles and headaches, or does it pretty much just work?  Because that's what I love about Ubuntu: it does just work, and coming from Red Hat, then Slackware, then Fedora, then Gentoo, having a Linux distro just work has been wonderful.

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by logos34 on 2007-11-23
I'm running Ubuntu Studio AMD64 (along side Winxpx64 and x86 ubuntu gutsy) and am quite impressed.  No more struggling with flash or windows media codecs.  flashplugin-nonfree and w64codecs has solved all that.  Everything works except suspend and hibernate, but I may have messed something up when poking around in startup services.  A few little annoyances but at the very least I'll do all my audio editing stuff on it.  (it's got a low-latency kernel, and the 64-bit version cuts down encoding/transcoding times.)

---

### Post by Kilz on 2007-11-23
> **thoughts said:**
> Hello,

I have an Intel Core 2 Duo system, and I want to run a 64 bit OS mainly because it'll allow me to use more RAM.  I have 4 gigs in my system, but under 32 bit OSes, only 3.3 gigs of that RAM is usable.  I've booted from the Ubuntu amd64 live CD and verified that it does in fact make all 4 gigs usable (well, 3.8 gigs -- close enough).

My RAM is always just about full, because I have lots of virtual desktops for various client work, and I run 2 VMware virtual machines all the time, in addition to Firefox and Thunderbird which are memory hogs, plus GIMP, Pidgin, and Amarok which can all be pretty memory-hoggy too.  So I'd really like to be able to put 6 gigs of RAM in here, so that my system stops using the swap partition so much.

My question is, what's the current state of 64 bit Ubuntu?  In searching these forums, I see lots of posts about program compatibility issues, or apps just not being available in 64 bit, etc.  I understand that you can run 32 bit apps under the 64 bit OS, but does that always work, or does the app have to be written/compiled with that capability in place?

Mac OS X Leopard was just released, and it's a single OS that runs on both 64-bit and 32-bit hardware.  That contrasts with Microsoft's approach of releasing entirely separate 64-bit editions, and that appears to be the Ubuntu approach too, right?  That makes me a little nervous since I'll no longer be using the main/most popular version of Ubuntu, and naturally the main version gets more TLC than any other versions.

I guess my overall question is, if I switch to the amd64 version of Ubuntu, am I setting myself up for lots of hassles and headaches, or does it pretty much just work?  Because that's what I love about Ubuntu: it does just work, and coming from Red Hat, then Slackware, then Fedora, then Gentoo, having a Linux distro just work has been wonderful.

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

Firast off lets dispell a few myths
The first myth is that there is a "just works" version of Ubuntu or linux.  There isnt. If you need proof take a look [here]("http://ubuntuforums.org/forumdisplay.php?f=73") , or [here]("http://ubuntuforums.org/forumdisplay.php?f=132") , or [here]("http://ubuntuforums.org/forumdisplay.php?f=131"). 
In all these forum sections with thousands of posts each, they are discussing the 32bit version. Do you see all the issues and problems? 
The truth is that all installs of linux have issues of one kind or another. Dose the 64bit version have issues, well yes,  but every version has issues.

The next myth we will deal with is that something is missing. 
[Please visit here for i386 (32bit).]("https://launchpad.net/ubuntu/gutsy/i386") notice the number of packages available in the left had collum. Write it down, its  
Binary packages:  	23984
Source packages:  	13589

[Next look here]("https://launchpad.net/ubuntu/gutsy/amd64") for AMD64 (64bit)
Binary packages:  	23984
Source packages:  	13589

So according to the development site for Ubuntu (launchpad), the place it is built by the developers. The number of available applications listed for both versions is identical.
Might you have to follow a howto to make something work or read something if you have issues? Yes, but again look [here]("http://ubuntuforums.org/forumdisplay.php?f=73") , or [here]("http://ubuntuforums.org/forumdisplay.php?f=132") , or [here]("http://ubuntuforums.org/forumdisplay.php?f=131") and ask yourself if the 32bit version doesnt have similar issues. Not exactly the same, but read some posts, people are told to "visit this howto" "do this to fix the problem" "this is how you install this".

Now I have shot down the myths, if you have specific questions about specific applications, I'm sure that me or some other kind soul will be glad to help you find whatever answer you need. Thats another thing all versions of Ubuntu have in common.  :D

---

### Post by thoughts on 2007-11-23
> **logos34]I'm running Ubuntu Studio AMD64 (along side Winxpx64 and x86 ubuntu gutsy) and am quite impressed. No more struggling with flash or windows media codecs. flashplugin-nonfree and w64codecs has solved all that. Everything works except suspend and hibernate, but I may have messed something up when poking around in startup services. A few little annoyances but at the very least I'll do all my audio editing stuff on it. (it's got a low-latency kernel, and the 64-bit version cuts down encoding/transcoding times.)[/QUOTE]

Thanks for that info, that helps.  I'm glad to hear that your experience is mostly positive with it.

[QUOTE=Kilz said:**
> Firast off lets dispell a few myths
The first myth is that there is a "just works" version of Ubuntu or linux.  There isnt.


Actually, yes, there is, and it's Ubuntu.  It just works for me, as well as Windows and OS X just work.  That doesn't mean that it's perfect, but it has far fewer issues than any other Linux distro that I have used.

> **Kilz said:**
> The next myth we will deal with is that something is missing. 
[Please visit here for i386 (32bit).]("https://launchpad.net/ubuntu/gutsy/i386") notice the number of packages available in the left had collum. Write it down, its  
Binary packages:  	23984
Source packages:  	13589

[Next look here]("https://launchpad.net/ubuntu/gutsy/amd64") for AMD64 (64bit)
Binary packages:  	23984
Source packages:  	13589

So according to the development site for Ubuntu (launchpad), the place it is built by the developers. The number of available applications listed for both versions is identical.


If the numbers are literally identical, then that must mean that every package is automatically a member of both versions.  Is that really the case?

And if you look under the search box on those same pages, one page says "This archive currently contains 23455 software packages" but on the other page, that number is 23113.  So which numbers are the real numbers?

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by Kilz on 2007-11-23
> **thoughts said:**
> Thanks for that info, that helps.  I'm glad to hear that your experience is mostly positive with it.



Actually, yes, there is, and it's Ubuntu.  It just works for me, as well as Windows and OS X just work.  That doesn't mean that it's perfect, but it has far fewer issues than any other Linux distro that I have used.



If the numbers are literally identical, then that must mean that every package is automatically a member of both versions.  Is that really the case?

And if you look under the search box on those same pages, one page says "This archive currently contains 23455 software packages" but on the other page, that number is 23113.  So which numbers are the real numbers?

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

Even taking into account your numbers. It is less than 1%. This can be accounted for in difference of platforms.
But in the end I was being nice,[ instead of pointing out the very good sticky post]("http://ubuntuforums.org/showthread.php?t=368607"), you know the one that every user sees at the top of the forum.
In your rush to get information you must have overlooked the very post that answers all of the "32 bit vs 64bit " questions. 
If after reading all the links in it please feel free to ask specific questions, not general overall ones that lead us no place and end up rehashing the same old tired questions, feel free.

---

### Post by azbarcea on 2007-11-23
1. Mac OS is not free, vs Ubuntu free (open source)

2. If u have money and you do not want trouble (of anykind and want to be sure), don't think, go for MAC OS. Than u'll have someone to blame if it won't work. If u do not have money, why do you ask?

3. Ubuntu is not perfect. There are issues and we all try to help and make it better. 

What is that your really want to ask? If to use Ubuntu or buy a commercial version? Depends on many things ... and we can't make this analysis for you!

---

### Post by sethvath on 2007-11-23
> **azbarcea said:**
> 1. Mac OS is not free, vs Ubuntu free (open source)

2. If u have money and you do not want trouble (of anykind and want to be sure), don't think, go for MAC OS. Than u'll have someone to blame if it won't work. If u do not have money, why do you ask?

3. Ubuntu is not perfect. There are issues and we all try to help and make it better. 

What is that your really want to ask? If to use Ubuntu or buy a commercial version? Depends on many things ... and we can't make this analysis for you!
It doesn't always boil down to the free vs non-free argument azbarcea. Coming from a design background myself, I understand "thoughts"'s rationale for a "it just works" system compared to a hobbyist who has all the time tinkering to get a perfect system. When you charge your clients 800$ (arbitrary value) per hour, you start thinking every minute of my time is money and really I don't have that much time to fool around especially when it comes to clients who are doling out cash for your time. An analogy, NASA would never bet their rockets on untested technology even if its free. They need something tried and tested to just work, at least most of the time (think challenger). 

So thoughts, my suggestion to you is to make a list of all the software you require and do a search whether it works on x86_64. If its only 1 or 2 programs that might be problematic and you're up for some risk taking, take the plunge and go for 64bit. I've had my fair share of problems on amd64 but none too serious to warn others against. In the worst case scenario, compile everything from source for the architecture. 

Last but not least, testing clients' work on VMware for cross OS compatibility is not the ideal case. I use a variety of machines to test out sites and remember to back up your data on more than one machine. I've had nasty experiences losing clients' work.

---

### Post by Kilz on 2007-11-23
> **sethvath said:**
> It doesn't always boil down to the free vs non-free argument azbarcea. Coming from a design background myself, I understand "thoughts"'s rationale for a "it just works" system compared to a hobbyist who has all the time tinkering to get a perfect system. When you charge your clients 800$ (arbitrary value) per hour, you start thinking every minute of my time is money and really I don't have that much time to fool around especially when it comes to clients who are doling out cash for your time. An analogy, NASA would never bet their rockets on untested technology even if its free. They need something tried and tested to just work, at least most of the time (think challenger). 

So thoughts, my suggestion to you is to make a list of all the software you require and do a search whether it works on x86_64. If its only 1 or 2 programs that might be problematic and you're up for some risk taking, take the plunge and go for 64bit. I've had my fair share of problems on amd64 but none too serious to warn others against. In the worst case scenario, compile everything from source for the architecture. 

Last but not least, testing clients' work on VMware for cross OS compatibility is not the ideal case. I use a variety of machines to test out sites and remember to back up your data on more than one machine. I've had nasty experiences losing clients' work.

Come on , you cant expect someone to actually [do a search on the applications they use]("http://packages.ubuntu.com/"). You cant even expect them to read the top page of the forum. You cant expect someone to know what that strange box in the right hand corner of every page with GO beside it is.
Its much easier on them to post the same useless question over, and over , and over again. That way they know right where to look for it. After all they are paying for the support, right?

---

### Post by thoughts on 2007-11-23
> **Kilz said:**
> Even taking into account your numbers. It is less than 1%. This can be accounted for in difference of platforms.
But in the end I was being nice,[ instead of pointing out the very good sticky post]("http://ubuntuforums.org/showthread.php?t=368607"), you know the one that every user sees at the top of the forum.
In your rush to get information you must have overlooked the very post that answers all of the "32 bit vs 64bit " questions. 
If after reading all the links in it please feel free to ask specific questions, not general overall ones that lead us no place and end up rehashing the same old tired questions, feel free.

There's nothing wrong with general questions.  They don't "lead us no place;" the reply by logos34 was quite useful to me.  Is there a forum rule which states that high-level questions are bad and only very specific questions are good?

If you have some personal bias against high-level questions, that's fine.  But you could have simply read the title of my post, "State of Ubuntu" and seen that this was a high-level question rather than a specific one, and then ignored it, instead of coming in here and implying that I didn't read the sticky (I did) and accusing me of being in a "rush to get information" (I'm not).  I clearly stated in my original post that I had searched these forums and read posts about this topic.

Finally, a question about the state of Ubuntu with respect to 64-bit, though general in a way, is still pretty specific.  It's not as if I just came in here and said "is Ubuntu good" or something entirely vague like that.  I asked whether switching to 64-bit would entail lots of hassle and headache, as opposed to the 32-bit that I'm currently using, which as I said, just works.

> **azbarcea said:**
> 1. Mac OS is not free, vs Ubuntu free (open source)

2. If u have money and you do not want trouble (of anykind and want to be sure), don't think, go for MAC OS. Than u'll have someone to blame if it won't work. If u do not have money, why do you ask?

3. Ubuntu is not perfect. There are issues and we all try to help and make it better. 

What is that your really want to ask? If to use Ubuntu or buy a commercial version? Depends on many things ... and we can't make this analysis for you!

I can only assume that this isn't directed at my original post, because it's not really related to anything that I said.  I'm asking about the state of 64 bit Ubuntu, not about the merits of free vs not free, and I certainly didn't ask whether I should be using Ubuntu or a commercial OS (I use both).

> **sethvath said:**
> I've had my fair share of problems on amd64 but none too serious to warn others against. In the worst case scenario, compile everything from source for the architecture.

This comment is very useful; thanks.

> **sethvath said:**
> Last but not least, testing clients' work on VMware for cross OS compatibility is not the ideal case.

I run VMware for a few reason: having a running copy of Windows XP for when I need to do tech support for family & friends, plus having installations of IE6 and IE7 to test web applications in.  I don't do any actual client OS programming and the VMware setup has worked pretty well for me.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by John.Michael.Kane on 2007-11-23
Can we please keep this topic civil. 

Yes the questions have been asked time and time again. 

Sure there have been some who may have avoided the sticky or searching. 

This said.  Those of us who are veteran Forum, and 64bit Ubuntu users should simply be able to give the user with questions the answers needed in a way that does not come across as mean or tired of the same ol same ol. As this only leads to conflict where there should not be any, and a possibility of loosing a new Ubuntu user be it they choose 32 bit or 64bit.

To the OP you might want to beak down exactly what it is that you use your machine for, and your program requirements, As this will allow us to help find out if all the programs you need are readily available in the repos, You also might to give us your complete system specs as well.

---

### Post by Ehtetur on 2007-11-23
> **thoughts said:**
> I guess my overall question is, if I switch to the amd64 version of Ubuntu, am I setting myself up for lots of hassles and headaches, or does it pretty much just work?
The good news: Ubuntu x64 pretty much just works. If you don't need to use any 32bit-only apps, then it's a slam dunk. I've yet to have MAJOR issues with Gutsy x64. For issues I did have, the Ubuntu forums provided me with the answers.

The bad news: I need to run several 32bit-only proprietary apps at work, And for that reason, my personal desktop runs x64 and my business laptop, while it can run x64, only runs x86.

I found hacks here and in other forums to get some of the 32bit to work in x64, but I'm not gonna take a chance... Don't want the hacks to remind me that they're hacks at the worst possible time.

---

### Post by Kilz on 2007-11-23
> **SD-Plissken said:**
> Can we please keep this topic civil. 

Yes the questions have been asked time and time again. 

Sure there have been some who may have avoided the sticky or searching. 

This said.  Those of us who are veteran Forum, and 64bit Ubuntu users should simply be able to give the user with questions the answers needed in a way that does not come across as mean or tired of the same ol same ol. As this only leads to conflict where there should not be any, and a possibility of loosing a new Ubuntu user be it they choose 32 bit or 64bit.

To the OP you might want to beak down exactly what it is that you use your machine for, and your program requirements, As this will allow us to help find out if all the programs you need are readily available in the repos, You also might to give us your complete system specs as well.

When someone isnt even willing to read and ignores what is in front of their faces. Then they can expect to be shown exactly what they bypassed on the way to wasting everyones time. There are people that have real problems.

The person posting this has posted his business address, he is a coder and developer. Not some newbie that is clueless.

---

### Post by Kilz on 2007-11-23
> **thoughts said:**
> There's nothing wrong with general questions.  They don't "lead us no place;" the reply by logos34 was quite useful to me.  Is there a forum rule which states that high-level questions are bad and only very specific questions are good?
Common sense should stop people from wasting the time of people who volunteer their own free time to help those with real problems.

---

### Post by John.Michael.Kane on 2007-11-23
> **Kilz said:**
> When someone isnt even willing to read and ignores what is in front of their faces. Then they can expect to be shown exactly what they bypassed on the way to wasting everyones time. There are people that have real problems.

I completely understand where you are coming from.I know it can be hard to deal with the same question being hashed in a different manner,

This said one must understand that even when one reads the sticky thread or search for past threads that it can inevitably make that user have more questions which may not have been address in previous threads or the responses in those threads may not be very new user friendly. so you will almost certainly end up with users needing clearifacation.

---

### Post by thoughts on 2007-11-23
> **SD-Plissken said:**
> To the OP you might want to beak down exactly what it is that you use your machine for, and your program requirements, As this will allow us to help find out if all the programs you need are readily available in the repos, You also might to give us your complete system specs as well.

I gave a little of that in my original post, but really what I'm looking for are the kinds of responses provided by logos34, sethvath, and Ehtetur: they provided useful accounts of their overall impressions of 64-bit Ubuntu.  I'm not trying to pass off the work of looking up whether the particular packages that I need are available in 64-bit; I've been using Ubuntu on 4 different systems for 18 months, and other Linux distros for about 7 years, so I have no problem doing that myself.

> **Kilz said:**
> Common sense should stop people from wasting the time of people who volunteer their own free time to help those with real problems.

If this thread is such a waste of your time, then please just stop reading it and responding to it.  The rest of us are trying to have a useful discussion here; there's no need for you to keep injecting negativity into this.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by John.Michael.Kane on 2007-11-23
I can only vouch what i have done with the systems regarding other Linux distros, As well as Ubuntu. 

The machines i tested 64bit distros on be it Ubuntu or other, Under most cases anything I was able to accomplish under 32bit I was able to do with little to no effort under 64bit.

IMHO no distro is perfect, and there are bound to be problems some have simple fixes some require a bit of work. in the end the only way to know for sure is to run the software architecture in question for a while, and see if it fits the need.

---

### Post by Kilz on 2007-11-23
> **thoughts said:**
> I gave a little of that in my original post, but really what I'm looking for are the kinds of responses provided by logos34, sethvath, and Ehtetur: they provided useful accounts of their overall impressions of 64-bit Ubuntu.  I'm not trying to pass off the work of looking up whether the particular packages that I need are available in 64-bit; I've been using Ubuntu on 4 different systems for 18 months, and other Linux distros for about 7 years, so I have no problem doing that myself.
 Thanks for proving you are no newbie and should know where to find information. But I guess its just to easy to let others do it for you.

> **thoughts said:**
> If this thread is such a waste of your time, then please just stop reading it and responding to it.  The rest of us are trying to have a useful discussion here; there's no need for you to keep injecting negativity into this.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)I could suggest what you could do , or where you could go, but I have a feeling you already know what I would say. Just like you know everything now. You must be to used to running the show and expecting others to do your work.

---

### Post by thoughts on 2007-11-23
> **Kilz said:**
> I could suggest what you could do , or where you could go, but I have a feeling you already know what I would say. Just like you know everything now. You must be to used to running the show and expecting others to do your work.

And now you're launching baseless personal attacks on me.

As I've already stated -- and as everyone here clearly sees, except you -- I didn't ask for anyone to do any work for me.  I asked about the state of 64-bit Ubuntu, and the other people in this thread responded with useful anecdotes and opinions on that topic.

No one in this thread wants to read your personal attacks on me; but at least 5 people in this thread -- myself and the 4 people who provided helpful on-topic responses -- are clearly interested in discussing the state of 64-bit Ubuntu.  So rather than hijacking this thread in order to flame me, why don't you just stop reading and posting here, since you've already stated that it's a waste of your time?

I'm not telling you what to do, I'm simply suggesting that you back up your words with action: if it's a waste of time, then stop doing it.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by Kilz on 2007-11-23
> **thoughts said:**
> And now you're launching baseless personal attacks on me.

As I've already stated -- and as everyone here clearly sees, except you -- I didn't ask for anyone to do any work for me.  I asked about the state of 64-bit Ubuntu, and the other people in this thread responded with useful anecdotes and opinions on that topic.

No one in this thread wants to read your personal attacks on me; but at least 5 people in this thread -- myself and the 4 people who provided helpful on-topic responses -- are clearly interested in discussing the state of 64-bit Ubuntu.  So rather than hijacking this thread in order to flame me, why don't you just stop reading and posting here, since you've already stated that it's a waste of your time?

I'm not telling you what to do, I'm simply suggesting that you back up your words with action: if it's a waste of time, then stop doing it.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

Why dont you go blog about it? Of coarse you could continue on your wonderful walk into alternate reality.

---

### Post by dryte on 2007-11-24
i have an hp tx 1220 ca  laptop, it's running an amd 64 processor.
i am running 64 bit version of gutsy.
all of the problems that i have run into have been solved by finding quite simple solutions in the forums. . . with a little searching.
using flash with 32 bit firefox was even very simple once i found the correct solution.

i don't have any problems other than suspend freezes...hibernate works fine.

i also do not find that i lack any type of software that will run on 64 bit.

also 64 bit will become more popular and will have programs made for it as time goes by.
(things change very fast in the technology world :)  )

---

### Post by azbarcea on 2007-11-26
I won't quote here u' r entire post, but if u

> 
I run VMware ...


Come on, u're the guy that whatever we're saying here u'll test it by your own, and this degenerated in an endless discussion. 

I said very clear: What do you want? or Who are you? Want to try, if it works for you, want to test, can u test, are u a simple user that "just wanna work", Can u afford to be that user? How much "host wanna work?" because even MAc OS or Windows or whatever aren't bullet proof, etc. Be onest please, and try to understand what I said. If you don't want trouble, find someonoe to help you, want some trouble (define SOME) etc.

Be specific when u ask, and lets not make philosophy because otherwise will stuck in details.

---

### Post by azbarcea on 2007-11-26
Kilz, I agree with you:

> Common sense should stop people from wasting the time of people who volunteer their own free time to help those with real problems.

But some poeple can't understand ... So "keep going forward" :-)

---

### Post by fjgaude on 2007-11-26
> **thoughts said:**
> 
I guess my overall question is, if I switch to the amd64 version of Ubuntu, am I setting myself up for lots of hassles and headaches, or does it pretty much just work?  Because that's what I love about Ubuntu: it does just work, and coming from Red Hat, then Slackware, then Fedora, then Gentoo, having a Linux distro just work has been wonderful.

Well, I've had Ubuntu 7.10 64-bit running on about five different machines and I would say it works as well as 32-bit. Each have their issues depending on the chipset, motherboard, etc.

Right now I have 32-bit working fully with everything on my main box, an AMD 64 2X Asus MB. With 64-bit I haven't been able to get it to play DVD movies using libdvdcss or for it to completely play the videos on this site: [http://foodtv.com](http://foodtv.com). The 32-bit does. That site is my acid test for audio, video on the web.

If you go with 64-bit, install but don't use any 3rd party sites to get the codecs. Just click on a video and the OS will find and install any codecs it needs; the same for mp3 music. The only hole is the Hollywood DVDs (and foodtv.com), AFAIK at this time.

That's been my experience with 64-bit, and such has gotten better and better as time has gone by.

---

### Post by cow_racer on 2007-11-26
My laptop which has a core 2 duo doesn't support more than 3 G of RAM even under 64 bit Ubuntu.  You might want to be sure yours support 6 G RAM or more.

---

