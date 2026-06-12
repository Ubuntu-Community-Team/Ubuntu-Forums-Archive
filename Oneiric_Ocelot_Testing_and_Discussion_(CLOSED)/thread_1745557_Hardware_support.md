---
title: "Hardware support"
date: 2011-05-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by teachop on 2011-05-01
Would like to see all the resources that went into a new desktop environment be put into stabilizing hardware support this cycle.  

The switch largely from proprietary to open driver for video and wireless may be the turning point, not sure, but while I had little issues with these areas a while back, now not a single laptop that I maintain is 100% functional.  Not out of the box, not after much tweaking of the geek kind.  There are glitches in video and/or wireless support on all.  The only "perfect" machine is a netbook that at present nobody wants to use anyway.

When I spend time in the forums, it hammers home that the killer feature for 11.10 should be to stabilize the underlying base functionality.

---

### Post by frup on 2011-05-01
I will stop using Ubuntu in 11.10 if I do not regain my ability to use multiple monitors. I can not do this in 11.04.

---

### Post by macroshaft on 2011-05-01
> **frup said:**
> I will stop using Ubuntu in 11.10 if I do not regain my ability to use multiple monitors. I can not do this in 11.04.

If that is such an issue then just stick with 10.10. Do you really have a valid reason to NEED 11.04 or 11.11?

---

### Post by teachop on 2011-05-01
> **macroshaft said:**
> Do you really have a valid reason to NEED 11.04 or 11.11?
I understand how you feel about that comment, but that wasn't really my original point in starting this thread.  People are going to download these versions and expect them to work, we want them to work out of the box.  All our efforts put into making Unity smooth or just the right size or some new theory of efficient window management doesn't cut it if wireless doesn't work or the laptop crashes with an external monitor.

Shuttleworth had that gag, remember, with the ice cream and the fly?  Well these things are not flies, to people trying to use Linux they are monsters, if the computer simply won't operate, off they go.

---

### Post by frup on 2011-05-01
> **macroshaft said:**
> If that is such an issue then just stick with 10.10. Do you really have a valid reason to NEED 11.04 or 11.11?

It's not going to stop me using 11.04 for now, but I will change to another distro if it doesn't get fixed by the next release. Interestingly enough since I posted that, I've experienced about 6 full x crashes. That means that since 11.04 was released I have experienced more problems than the last 3 months of using it as a development release. An amusing observation, not a criticism exactly.

---

### Post by macroshaft on 2011-05-01
> **teachop said:**
> I understand how you feel about that comment, but that wasn't really my original point in starting this thread.  People are going to download these versions and expect them to work, we want them to work out of the box.  All our efforts put into making Unity smooth or just the right size or some new theory of efficient window management doesn't cut it if wireless doesn't work or the laptop crashes with an external monitor.

Shuttleworth had that gag, remember, with the ice cream and the fly?  Well these things are not flies, to people trying to use Linux they are monsters, if the computer simply won't operate, off they go.

I entirely agree. I'm in the process of starting a company to re-work second hand computers and sell them on with linux installed. A big worry for me is how much trouble I might have on some machines due to linux un-friendly hardware.

It amazes me how linux can be so much better than windows in so many ways yet still struggles on the things windows finds so easy.

---

### Post by macroshaft on 2011-05-01
> **frup said:**
> It's not going to stop me using 11.04 for now, but I will change to another distro if it doesn't get fixed by the next release. Interestingly enough since I posted that, I've experienced about 6 full x crashes. That means that since 11.04 was released I have experienced more problems than the last 3 months of using it as a development release. An amusing observation, not a criticism exactly.

I have yet to re-install my system, it's been running since the start of Natty development and so naturally has a grumpy disposition. I'd like to think a re-install would cure that but I think Natty is going to turn out to have a bit of a bad attitude. What they have created really does need more than 6 months to develop.

---

### Post by as2000 on 2011-05-01
> **frup said:**
> It's not going to stop me using 11.04 for now, but I will change to another distro if it doesn't get fixed by the next release. Interestingly enough since I posted that, I've experienced about 6 full x crashes. That means that since 11.04 was released I have experienced more problems than the last 3 months of using it as a development release. An amusing observation, not a criticism exactly.

Why not try Kubuntu?

---

### Post by cariboo on 2011-05-01
> **frup said:**
> I will stop using Ubuntu in 11.10 if I do not regain my ability to use multiple monitors. I can not do this in 11.04.

Making threats is not the way to get a problem fixed, where is your thread asking for help to solve your problem, where is the link to a bug report? Where are the details of your setup?

In my experience, dual monitors work out of the box on the three different systems I have tried it on. It doesn't work the way I expected, but it does work.

---

### Post by ronacc on 2011-05-01
I can sympathize with the way he feels , naked newt managed to break hardware  that had been stable for years and as of release still had not gotten 2 out of 3 fixed on my test box , I did a fresh install of NN release and changed my source list and am hoping obnoxious orc  can get the other two working .

---

### Post by cariboo on 2011-05-01
I'm fortunate enough that almost 100% of my hardware is well supported. The only piece of hardware I bought recently that wasn't supported was a USB wireless device, that will only work on 32-bit using ndiswrapper. I've tried giving it away, but it keeps coming back, as it doesn't work on Windows very well either, as it's only supported in Vista/Win 7.

---

### Post by ronacc on 2011-05-02
That is what is so disheartening to me , as I said the things that broke had been 100% reliable for many iterations . My wireless is realtek 8185 and has given no problem since gutsy , with natty it started not connecting automaticly and required a bizzare sequence of actions to get working on each and every boot , it was fixed briefly ( a couple of days ) tword the end but went south again by release and continues into the orc . My printer , a brother MFC7440n has worked flawlessly since I bought it during jaunty and since the start of natty hasn't printed a single character either wired or wirelessly .

---

### Post by gsmanners on 2011-05-02
I've become spoiled using the 2.6.32 kernel for a year now. It's very smooth and reliable compared to my experience with the 2.6.38 kernel. I tried Natty on this system, but it just hammers on the hard drive way too much, and I hear it has problems with wasting energy. Maybe what we really need is to take a step backward with the kernel.

---

### Post by teachop on 2011-05-02
Wireless needs some of that good Canonical attention to detail.

---

### Post by ronacc on 2011-05-02
I think what wireless and several other things need is for canonical to quit messing with things that are working perfectly all for the sake of ooh shiny . my wireless problems started when they merged nm-applet into that abomination indicator applet .

---

### Post by teachop on 2011-05-02
I put 11.04 on my main computer at work today.  Total video disaster when running Unity as a laptop, works perfect in the configuration I upgraded in, external monitor and laptop screen both active.  Have not had time to sort it out, am a bit afraid to break the normal case working on the busted one.

My contention, concern, is these hardware problems are seeming worse then they have been in years (at least for me) and Unity or no, Dash or no, they will bring a screeching halt to things.

---

### Post by frup on 2011-05-03
> **cariboo907 said:**
> Making threats is not the way to get a problem fixed, where is your thread asking for help to solve your problem, where is the link to a bug report? Where are the details of your setup?

In my experience, dual monitors work out of the box on the three different systems I have tried it on. It doesn't work the way I expected, but it does work.

It's not a threat, it isn't addressed to anyone, it's more just a statement, that if unity continues not to allow me to do simple things like that, I will not continue to use it. I hadn't even done any research in to the whole multiple monitor issue as because of unities state I just figured a) it would be widely known, b) be solved eventually anyway... there are far more interesting things for me to do right now. It does not change the fact that it is a regression, plain and simple. I have intel hardware, which provides me with all open source drivers and usually I do not have any problems at all. It's something I consider myself very fortunate of because I never experience all the problems many other people do.

Now is an interesting time, we have the choice of Gnome, Unity or KDE as fairly well supported mainstream desktop environments. It's all well and good to suggest that people shouldn't make threats and should submit bug reports, but the fact of the matter is that requires some form of allegiance or good will. I'm no unity hater, in fact it is somewhat interesting, but when changes are made that seem almost reckless or merely for the sake of change and those changes stop things from working, the last thing some people are going to want to do is help solve problems in the changes they never even asked for. Anyway I'm going to continue reading a book, I'm rather bored of my computer at the moment.

---

### Post by vanquishedangel on 2011-05-03
Ok this is my 2 cents, alot of people with issues with things are running development releases or updating to the new release as soon as it comes out, UM.............

1. if the computer is work related or very important didn't they warn us not to install it? I remember that somewhere it said to stick with the LTS.

2. Well if you use a development release you get what you get, same with a newly released, people using computers that are important like that should use LTS with better support.

3. Completely shocked at the amount of "blah blah blah I am leaving" from people, it reminds me of being 5 yrs old and saying "I am gonna tell mom!".

4. I for one am very happy with natty, I like the improved open source drivers, ATI drivers suck lol I love the new distro and it is working quite well, but I HATE unity, so i just installed another desktop. I like LXDE way better anyway.

5. I would like to say great job to the ubuntu team, it is hard when faced with all this drama when you try something new, reading these forums is far better than going to the theater at these times lol. All things must evolve to stay alive this includes Ubuntu, sometimes it works, sometimes it doesn't, and most of the time you never really know lol.

---

### Post by teachop on 2011-05-03
> **vanquishedangel said:**
> I remember that somewhere it said to stick with the LTS.
Do you know where that comes from?  When I go to the main web site, click on Ubuntu for Business "Secure, Reliable", it takes me to a download page that defaults to 11.04 Natty, just the same as the main download button does.

---

### Post by vanquishedangel on 2011-05-03
sure, I havent found the exact page page but on this site

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

it says:
Our long-term support (LTS) releases are supported for three years on the desktop. Perfect for organisations that need more stability for larger deployments.

and here it talks of more stability on the LTS

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

and here is another post about it and one of them has a good answer

[http://askubuntu.com/questions/19234/should-i-choose-10-04-lts-or-10-10](http://askubuntu.com/questions/19234/should-i-choose-10-04-lts-or-10-10)

---

### Post by teachop on 2011-05-03
> **vanquishedangel said:**
> sure, I havent found the exact page page but on this site

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

it says:
Our long-term support (LTS) releases are supported for three years on the desktop. Perfect for organisations that need more stability for larger deployments.

and here at the bottom it talks of more stability o n the LTS

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

and here is another post about it and one of them has a good answer

[http://askubuntu.com/questions/19234/should-i-choose-10-04-lts-or-10-10](http://askubuntu.com/questions/19234/should-i-choose-10-04-lts-or-10-10)
Yes, good point.  LTS is indeed available for a reason.  Good advice and links.

The LTS isn't the recommended download for Ubuntu presently.  I started this thread because it is important that the recommended download for both individuals and business (Natty 11.04 32bit) be reliable on a larger range of hardware.  Thought that worth discussion early in the cycle when priorities are set for development.

---

### Post by Harry33 on 2011-05-03
This is the development (Oneiric Ocelot) Forum.
How does it relate to this forum to say that LTS versions are very stable?
We are here to test the dev phase and to discuss the issues related to that.

The thing here is to make distros better by testing and providing answers, by asking questions, by expressing views and opinions.

---

### Post by gsmanners on 2011-05-03
> **Harry33 said:**
> This is the development (Oneiric Ocelot) Forum.
How does it relate to this forum to say that LTS versions are very stable?
We are here to test the dev phase and to discuss the issues related to that.

The thing here is to make distros better by testing and providing answers, by asking questions, by expressing views and opinions.

Comparisons are data. In case you hadn't noticed, data is necessary in the troubleshooting process. It tells the devs where there are problems, so they know where to look to solve them. Mindlessly testing everything without comparison is prohibitive to progress.

---

### Post by Harry33 on 2011-05-03
> **gsmanners said:**
> Comparisons are data. In case you hadn't noticed, data is necessary in the troubleshooting process. It tells the devs where there are problems, so they know where to look to solve them. Mindlessly testing everything without comparison is prohibitive to progress.

Basically yes, but comparing Lucid (10.04) to Oneiric (11.10) does not help much.
Not even in finding bugs better.

---

### Post by vanquishedangel on 2011-05-03
> **Harry33 said:**
> Basically yes, but comparing Lucid (10.04) to Oneiric (11.10) does not help much.
Not even in finding bugs better.

Actually if there is a bug in the new one and not the old that means there is a difference and maybe through the change log of something they can find it and fix the bug. And people that do most of the complaining aren't helpful in many cases so to make things clearer in this forum, it should be known that that if your computer is important you shouldn't try the dev. this way it clears the forum for the real deal about testing.

---

### Post by cariboo on 2011-05-04
> **vanquishedangel said:**
> Actually if there is a bug in the new one and not the old that means there is a difference and maybe through the change log of something they can find it and fix the bug. And people that do most of the complaining aren't helpful in many cases so to make things clearer in this forum, it should be known that that if your computer is important you shouldn't try the dev. this way it clears the forum for the real deal about testing.

Doing a direct comparison between Lucid and Natty isn't going to work very well because the components of the two are totally different. Just off the to of my head, Xorg-xserver, graphics drivers, compiz and the DE are totally different from the version 10.04 uses.

I intend on putting up some stickies when I have time, as real life is getting in the way of things on the forum for me.

---

