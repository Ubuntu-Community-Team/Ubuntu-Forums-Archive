---
title: "Make a living with Ubuntu (as a programmer/consultant)?"
date: 2007-03-17
forum: Programming Talk
---

### Post by moephan on 2007-03-17
Hello,

I am on the verge of quiting my job at a very large ISV company in the Seattle area. However, I have not decided exactly what to do next, but I am pretty certain that I would like Ubuntu to be central to my efforts. I was thinking that this forum might be able to provide some guidance and feedback to help me think about my next steps.

I currently take home about good money in salary, stock, and bonuses. If possible, I'd like to maintain a similar level of income as I am the sole bread winner for my wife and two kids. My degree is in cognitive psychology, and my experience over the last nine years is in usability and program management for developer tools, though I did have a one year stint on a large scale web project, which included a javascript api. I can write .NET code, and have taught myself Python and RoR. I am not the fastest coder, and my code is not necessarily the  most functional and elegant, but I do flatter myself thinking that I am able to identify the real user value in a program, and design and implement a user interface (or API in the case that developers are the users) that very much suits the needs of the user.

So, here are some of my ideas:

1. Create a consultancy that trains Visual Studio dependent developers how to do application development using Ubuntu. I could introduce them to the OS, Python, Glade, RoR, etc... I have in depth knowledge of how they use Visual Studio and how they approach programming, so I think that I could really help them adapt to application development using a new platform.

2. Consult with companies to help them migrate to Linux, specifically focused on the user issues (as apposed to the IT issues). I could examen what software the users use, and how they use it, and create a transition plan to help the users adapt to Linux after their IT department rolls out Linux. I could similarly help developers adapt as per #1.

3. Just write applications as a consultant or vendor using Gtk/Python and/or RoR.

4. Build and sell computers and periferals with Ubuntu pre-installed. Probably get a store front and also a web page. 

5. Try building web site with RoR that I think could make some money via Google Ads.

6. Others ... ?

What do you all think? Do I stand a chance? Is there anything I'm missing? Does anyone make their living with Ubuntu?

Thanks.

Cheers, Rick

---

### Post by Poisson_Pilote on 2007-03-17
I do not know if things in the US are much different, but here in France it would be very difficult to make your living with Linux. Most companies are just stuck to Microsoft, and when a consultant tries to speak about something new, they just run away.

---

### Post by pmasiar on 2007-03-17
> **moephan said:**
> I am on the verge of quiting my job at a very large ISV company in the Seattle area. However, I have not decided exactly what to do next,(...)I currently take home about $112K plus $25K in stock and bonuses per year. 

I would start with *not* quitting your job. :-)

I assume you want to stay in the Seattle area? Get in touch with free software support companies. Google is your friend: [http://www.python.org/community/jobs/](http://www.python.org/community/jobs/) , many companies at PyCon 2007 were hiring (but you should be aware about it if you follow  Python, right? So if you don't and missed PyCon 2007 you may be *not* as advanced Python hacker as your salary requirements would suggest? :-) ) If you are lucky, get hired by Google - they use Python and they may use expert on usability.

You are aiming for extremely narrow niche: Linux/Ubuntu with Python or RoR. Many companies may use one but not the other.

Try to build yourself some portfolio of results in FOSS. Find some projects interested in your expertize, and contribute. You gain name recognition, and better feeling what market is. With luck and lots of good karma for good volunteer work, who knows, Canonical might hire you as usability expert - check their website.

---

### Post by moephan on 2007-03-17
Thanks for the advice. I do understand and appreciate that I am reasonably well paid now. However, I am NOT looking for a new job. I plan to quit and start making money for myself, rather than for a company that I work for. I am looking for feedback more on business ideas rather than how to get a job.

I guess I should have called the thread something more like "starting a Ubuntu based business" or something.

Thanks.

Cheers, Rick

---

### Post by newlinux on 2007-05-07
Moephan, how is this going? Are you still thinking about this? I'm considering the some similar consulting , but  on a part time basis at first (don't want to quit my job yet).

---

### Post by cwaldbieser on 2007-05-09
> **moephan said:**
> Hello,

I am on the verge of quiting my job at a very large ISV company in the Seattle area. However, I have not decided exactly what to do next, but I am pretty certain that I would like Ubuntu to be central to my efforts. I was thinking that this forum might be able to provide some guidance and feedback to help me think about my next steps.

I currently take home about good money in salary, stock, and bonuses. If possible, I'd like to maintain a similar level of income as I am the sole bread winner for my wife and two kids. My degree is in cognitive psychology, and my experience over the last nine years is in usability and program management for developer tools, though I did have a one year stint on a large scale web project, which included a javascript api. I can write .NET code, and have taught myself Python and RoR. I am not the fastest coder, and my code is not necessarily the  most functional and elegant, but I do flatter myself thinking that I am able to identify the real user value in a program, and design and implement a user interface (or API in the case that developers are the users) that very much suits the needs of the user.

So, here are some of my ideas:

1. Create a consultancy that trains Visual Studio dependent developers how to do application development using Ubuntu. I could introduce them to the OS, Python, Glade, RoR, etc... I have in depth knowledge of how they use Visual Studio and how they approach programming, so I think that I could really help them adapt to application development using a new platform.

2. Consult with companies to help them migrate to Linux, specifically focused on the user issues (as apposed to the IT issues). I could examen what software the users use, and how they use it, and create a transition plan to help the users adapt to Linux after their IT department rolls out Linux. I could similarly help developers adapt as per #1.

3. Just write applications as a consultant or vendor using Gtk/Python and/or RoR.

4. Build and sell computers and periferals with Ubuntu pre-installed. Probably get a store front and also a web page. 

5. Try building web site with RoR that I think could make some money via Google Ads.

6. Others ... ?

What do you all think? Do I stand a chance? Is there anything I'm missing? Does anyone make their living with Ubuntu?

Thanks.

Cheers, Rick

These are observations from my own place of business.  I hope they will help you.

In the "old days" our flagship software ran on VAX.  Later, the software was migrated to UNIX and given a real database back end (Informix).  With the populatiry of the web, it was perceived that the software, while functional, was just not attracting customers because it hadn't made the leap to the browser.  This led to development of the new software on a Microsoft IIS/VB6/ASP platform.  The UNIX customer base still exists, but most new development is geared toward MS platforms.

What has happened, though, is that through attrition, a lot of the UNIX/Informix knowledge has been lost.  A Linux server was introduced, but no one person in the organization even knows how to get Informix up and running on it.  Through the efforts of several individuals and some company folklore, we do have a working Informix server on Linux, but the old UNIX admins never seemed to have really made the leap as to what it means to maintain the Linux server since it seems to crash at least once a week.

Most of the people who maintain the old software have no idea that graphical tools exist on our UNIX or Linux servers, and command line skills are very basic (cd, ls, vi, some commands specific to informix).

I am guessing that my business is not terribly unique in this regard.  I would think that there would be some kind of profitable way to offer "refresher" courses on "legacy systems" if it were shopped around in a way that appealed to the business decision makers.

---

### Post by siiib on 2007-05-09
well they'll get it soon enough when the bottom line feeders (accountants) find that linux is available as a free download.. imo linux actually isn't that free at the moment for business use cos you have to pay someone with quite a lot of computer expertise to administer the thing to a reasonable (usable ) level.. obviously this will change.. people always follow the path of least financial resistance ime.

just my 0.02

---

### Post by slavik on 2007-05-10
> **siiib said:**
> well they'll get it soon enough when the bottom line feeders (accountants) find that linux is available as a free download.. imo linux actually isn't that free at the moment for business use cos you have to pay someone with quite a lot of computer expertise to administer the thing to a reasonable (usable ) level.. obviously this will change.. people always follow the path of least financial resistance ime.

just my 0.02

You still have to pay the Windows admins, too.

---

### Post by pmasiar on 2007-05-10
> **slavik said:**
> You still have to pay the Windows admins, too.

...And you spend on Winadmins more: they waste more time patching viruses, and are able to manage less servers per admin, and less work can be done remotely.

---

### Post by skeeterbug on 2007-05-11
> **pmasiar said:**
> ...And you spend on Winadmins more: they waste more time patching viruses, and are able to manage less servers per admin, and less work can be done remotely.

What data do you have to back this up? One could easily say Linux admins spend more time re-compiling the kernel and editing config files. What more can be done remotely in Linux vs Windows? Have you ever even used remote desktop?

My website is a linux box, and I also manage about 10 other 2k3 boxes via remote desktop. I have a toolbar on my task manager to easily connect to any of them via remote desktop.

---

### Post by Hendrixski on 2007-05-11
I'd say go for it.  There is an i ncreasing business need for Linux.  You'll just have to specialize in something.  like let's say business intelligence, or servers, or whatever.

It's a lot of work but it pays off.  I'm in the process of doing tihs now.  Getting investors for new technology, is actually not that hard. 

If you odn't do it, you'll regret it for the rest of your life

---

### Post by pmasiar on 2007-05-11
> **skeeterbug said:**
> What data do you have to back this up? 

TOC study by some australian company, read couple months ago on LWN. I am not going to argue with you, use what you want.

> One could easily say Linux admins spend more time re-compiling the kernel

but you don't *have* to recompile the kernel if you don't want to.

I am not pro admin, but keeping my ubuntu patched is *much* simpler than my windoze box.

---

### Post by slavik on 2007-05-13
> **pmasiar said:**
> ...And you spend on Winadmins more: they waste more time patching viruses, and are able to manage less servers per admin, and less work can be done remotely.
Linux needs to be patched for vulnerabilities, too.

---

### Post by foresth on 2007-05-13
> **moephan said:**
> Hello,

I am on the verge of quiting my job at a very large ISV company in the Seattle area. However, I have not decided exactly what to do next, but I am pretty certain that I would like Ubuntu to be central to my efforts. I was thinking that this forum might be able to provide some guidance and feedback to help me think about my next steps.

I currently take home about good money in salary, stock, and bonuses. If possible, I'd like to maintain a similar level of income as I am the sole bread winner for my wife and two kids. My degree is in cognitive psychology, and my experience over the last nine years is in usability and program management for developer tools, though I did have a one year stint on a large scale web project, which included a javascript api. I can write .NET code, and have taught myself Python and RoR. I am not the fastest coder, and my code is not necessarily the  most functional and elegant, but I do flatter myself thinking that I am able to identify the real user value in a program, and design and implement a user interface (or API in the case that developers are the users) that very much suits the needs of the user.

So, here are some of my ideas:

1. Create a consultancy that trains Visual Studio dependent developers how to do application development using Ubuntu. I could introduce them to the OS, Python, Glade, RoR, etc... I have in depth knowledge of how they use Visual Studio and how they approach programming, so I think that I could really help them adapt to application development using a new platform.

2. Consult with companies to help them migrate to Linux, specifically focused on the user issues (as apposed to the IT issues). I could examen what software the users use, and how they use it, and create a transition plan to help the users adapt to Linux after their IT department rolls out Linux. I could similarly help developers adapt as per #1.

3. Just write applications as a consultant or vendor using Gtk/Python and/or RoR.

4. Build and sell computers and periferals with Ubuntu pre-installed. Probably get a store front and also a web page. 

5. Try building web site with RoR that I think could make some money via Google Ads.

6. Others ... ?

What do you all think? Do I stand a chance? Is there anything I'm missing? Does anyone make their living with Ubuntu?

Thanks.

Cheers, Rick

Any news..? I am interested in your progress..

---

### Post by thelinuxguy on 2007-05-13
I am interested in your progress as well. In my part of the world, Ubuntu is yet to make it to the workplace on a daily basis. Barring *very* few open source companies, companies here mostly use Microsoft products.

---

### Post by moephan on 2007-07-01
A few people on the thread asked for an update, so here goes:

1. I gave notice at my current job that I will be leaving in September. This works out for me financially and personally in a few ways.

2, I am not 100% certain what I am going to do for a living. Short term, I have a few partially implemented web apps and web sites, so I am going to see if I can generated some income off of those.

3. I have three ideas for specializations where I think think I can make a living:
a. Train Windows developers to program on Linux (A web site would go with this). This would be very focused on mapping the Windows programming ways of thinking onto Linux programming in a very practical way.

b. Consult with companies on API design. I don't think many people focus on user-centered design for users who are developers, and there may be a niche there.

c. Help companies plan for and migrate end users to Linux. There seems to be a lot more attentioned paid to migrating apps and servers. Maybe there is a need to assess how workers are using Windows, and help them make the switch to Linux in a human sense.

4. I am planning to go down to Ubuntu Live and walk around and talk to people to get more ideas.

So in short, I am committed, but I'm not certain to what yet :)

Cheers, Rick

---

### Post by ankursethi on 2007-07-02
Nice going. The migration business is quite hot right now, or will be in the future, as more companies are hearing about Linux and it's advantages. Although IP issues might pose a serious problem. My idea : keep that "training Windows devs and admins for Linux-oriented programming and administration tasks" job, and also develop replacements for Windows softwares critical to small businesses (or large businesses, whatever). This will (1) help you, because most companies refuse to move to Linux because the software is lacking in some way and (2) help the community because you will be writing code critical to the adoption of Linux on the enterprise level, and developing new enterprise specific applications. This job might give you enough insight into the needs of these companies, and tell you what the enterprises expect from Linux. That's some valueable expertise, and will probably be sought for should you join another company in the future.

I wonder if you can manage these two jobs at once, but I really don't know about you so I'm not the one to comment.

PS : keep informing of your progress and what happened at Ubuntu Live. I'm sure it will be helpful to others who might be interested in something similar.

---

### Post by Praill on 2007-07-02
I have to admit I feel nervous for you, but I admire your bravery. Most developers and techies love linux but would never leave their cushy, high paid, MS-based jobs... because its not worth the risk in such a brand new budding market.

My only advice would be to push a distro that has accountability, like Red Hat... unless can will provide support.. I dunno. The major fear companies have of using open source solutions is there's no one to hold accountable. If something isnt working a company likes to know they can call someone responsible for a solution.

---

### Post by elst on 2007-07-03
> **Praill said:**
> I have to admit I feel nervous for you, but I admire your bravery. Most developers and techies love linux but would never leave their cushy, high paid, MS-based jobs... because its not worth the risk in such a brand new budding market.


Likewise. Good luck.

> My only advice would be to push a distro that has accountability, like Red Hat... unless can will provide support.. I dunno. The major fear companies have of using open source solutions is there's no one to hold accountable. If something isnt working a company likes to know they can call someone responsible for a solution.

Canonical offer commercial support contracts:

[http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

They also have partner programmes for training providers and ISVs, which may be of interest:

[http://www.ubuntu.com/partners](http://www.ubuntu.com/partners)

They are a comparatively young company compared with Novell and Red Hat, so I would expect that these services are not as developed, but equally they may be keener, since they aren't yet an established player.

---

### Post by moephan on 2007-08-04
Here's the requested update.

First, I visited the Ubuntu Live booth area, but did not attend any of the sessions. It was free to visit the booths and talk to people. A couple of things struck me about the event.

1. very small! I'm used to massive Microsoft oriented events like Mix and PDC, etc... These are huge affairs with tons of booths and attendees. By contrast, I think there were around 10 booths at UL. However, about half of the booths had really interesting things going on. I left with the feeling that this year is the time to to get in on the ground floor of something very vibrant and exciting.

2. The community is made up of both smart and good people. And by good, I mean positive, friendly, and properly focused on making the world a better place. I didn't get the feeling like I get from places like Google that day "don't be evil" but are obviously hell bent on world domination and any cost. This felt more like people wanted to make a good living by improving the world. Kind of intangible, and hard to explain I suppose.

3. The Canonical employees were all friendly and accessible. They also seemed excited to be working with Canoncial. An interesting point was that I met people from all over Europe who worked for Canonical. 

4. It seemed that I think about developers as users differently than the canonical staff, and had a great conversation about how to continue the discussion in a productive way with the community. I'll pick up on that when I get back from vacation next week.

Still not sure what exactly I will do starting September 4th (my last day at current job is Sept 3rd), but I'm going to focus on getting my web sites functional and running before then. Maybe they can throw off enough cash to keep my family afloat while I figure out what I want to do when I grow up :)

Cheers, Rick

---

### Post by jenson on 2007-09-05
> **moephan said:**
> Here's the requested update.

First, I visited the Ubuntu Live booth area, but did not attend any of the sessions. It was free to visit the booths and talk to people. A couple of things struck me about the event.

1. very small! I'm used to massive Microsoft oriented events like Mix and PDC, etc... These are huge affairs with tons of booths and attendees. By contrast, I think there were around 10 booths at UL. However, about half of the booths had really interesting things going on. I left with the feeling that this year is the time to to get in on the ground floor of something very vibrant and exciting.

2. The community is made up of both smart and good people. And by good, I mean positive, friendly, and properly focused on making the world a better place. I didn't get the feeling like I get from places like Google that day "don't be evil" but are obviously hell bent on world domination and any cost. This felt more like people wanted to make a good living by improving the world. Kind of intangible, and hard to explain I suppose.

3. The Canonical employees were all friendly and accessible. They also seemed excited to be working with Canoncial. An interesting point was that I met people from all over Europe who worked for Canonical. 

4. It seemed that I think about developers as users differently than the canonical staff, and had a great conversation about how to continue the discussion in a productive way with the community. I'll pick up on that when I get back from vacation next week.

Still not sure what exactly I will do starting September 4th (my last day at current job is Sept 3rd), but I'm going to focus on getting my web sites functional and running before then. Maybe they can throw off enough cash to keep my family afloat while I figure out what I want to do when I grow up :)

Cheers, Rick

Hi Rick,

Great that I dug out this post today and I'm impressed by what you have said and are planning to do. Me, too, am looking for opportunities to learn and work on Linux, most likely Ubuntu, as I like Ubuntu so much.

I also hope that one day I can contribute back to the community by large. I don't really plan to open up a businesee based on Ubuntu yet, but would be great to work for a company that is based on Ubuntu platform.

I'm a windows programmer doing mainly .NET programming and web application. I only freelance in some small scare and simple development and customization on open source projects. I wish to get involved more.

Btw, I don't think my reply here is of much relevance to your topic. But what I really want to read is about your updates and progress. You've just inspired me! Yes, you are!

I've become more ambitious and motivated right now. Meanwhile, I'm promoting the adoption of Ubuntu among my friends and colleagues/ex-colleagues. Hopefully one day, we will all be working on Linux platform very soon as I'm sort of tired of programming on Windows platform now, especially .NET programming :mad:

I have to stay tuned! And hope to hear from you very soon =)

Wishing good luck and all the best here! ;)

Regards,
Jenson

---

### Post by moephan on 2007-09-05
Well, if you are interested in another update, then here it is.

In case it wasn't obvious, I was working at Microsoft for the last 10 years. Yesterday I had my exit interview, and now I am no longer an employee there. I quit in part because the open source world seems just so much more vibrant and interesting, and Ubuntu is just a cool thing from a technical, user, and business perspective.  There were other reason too, of course. I left in good standing, and timed my leaving with vesting some modest stock grants. I could imagine working there again some day.

In the meantime, I am currently thinking that I will probably have a set of web sites or other projects, which taken together will hopefully keep my family afloat without forcing me to get another job. However, I have been applying for jobs that look interesting. 

My first web site is a [calorie tracking web site]("http://calorielookup.com"), using Ubuntu as my development environment and RoR. Still got a lot of work to do, but hoping I can get the site to throw off some revenue soon.

I'm also planning on putting together a .NET to Ubuntu class for Visual Studio programmers, and I have a lot of code for a web based video editing/mashup site that I will probably start working on soon as well.

Cheers, Rick

---

### Post by CptPicard on 2007-09-05
You're a brave one... I must admit that at first sight this reminds me of something...

[IMG]http://upload.wikimedia.org/wikipedia/en/d/dd/Gnomes_plan.png[/IMG]

1. Quit steady job at Microsoft to do something with Linux
2. ??
3. Profit!

;)

Independent consulting is tough, and doing migration consulting is going to be tougher still if you aren't really, really good at the technical details. Simple UI usability consulting is going to just force you into becoming an OpenOffice trainer, I'm afraid -- you're showing users where the button is now that they were used to pushing before.


> **moephan said:**
> 
2, I am not 100% certain what I am going to do for a living. Short term, I have a few partially implemented web apps and web sites, so I am going to see if I can generated some income off of those.

Web pages don't pay, unless you get a really brilliant, viral idea, or have content that people actually want to pay for. I maintain a site for friend that generates real honest money to its members, and even the traffic there wouldn't pay for hosting costs, if we did have ads. Which we don't. Because people pay a % for the money that is made for them.

> a. Train Windows developers to program on Linux (A web site would go with this). This would be very focused on mapping the Windows programming ways of thinking onto Linux programming in a very practical way.

Hmm. Are you such a great code jockey on both Windows and Linux that you have some actual insights as to where such differences are? Yeah, it might be good blog/column material if you've got zen-like insights, but otherwise I'd think that programming is programming, and the differences are rather easily manageable by any programmer who is serious about his profession.

> 
b. Consult with companies on API design. I don't think many people focus on user-centered design for users who are developers, and there may be a niche there.

You're approaching this from a UI cognitive psychology viewpoint, which is different from a programming API viewpoint. APIs are best designed by competent, insightful programmers who have an understanding of what works. They are the best "usability" experts as far as code elegance goes. Applying some sort of cognitive psychology analysis to this perceived elegance of code sounds like a topic for an academic thesis for you, but I'm not sure if you'll be able to really contribute unless you're a coder god yourself.

> c. Help companies plan for and migrate end users to Linux. There seems to be a lot more attentioned paid to migrating apps and servers. Maybe there is a need to assess how workers are using Windows, and help them make the switch to Linux in a human sense.

Here's a better idea really. Although I sense that the more competent user just needs to be encouraged to give it a try, after which they manage well on their own, and the less competent user needs to just learn the new button placements by rote as they always have.

Good luck, though. Don't want to discourage you :p

---

### Post by jenson on 2007-09-06
> **moephan said:**
> Well, if you are interested in another update, then here it is.

In case it wasn't obvious, I was working at Microsoft for the last 10 years. Yesterday I had my exit interview, and now I am no longer an employee there. I quit in part because the open source world seems just so much more vibrant and interesting, and Ubuntu is just a cool thing from a technical, user, and business perspective.  There were other reason too, of course. I left in good standing, and timed my leaving with vesting some modest stock grants. I could imagine working there again some day.

In the meantime, I am currently thinking that I will probably have a set of web sites or other projects, which taken together will hopefully keep my family afloat without forcing me to get another job. However, I have been applying for jobs that look interesting. 

My first web site is a [calorie tracking web site]("http://calorielookup.com"), using Ubuntu as my development environment and RoR. Still got a lot of work to do, but hoping I can get the site to throw off some revenue soon.

I'm also planning on putting together a .NET to Ubuntu class for Visual Studio programmers, and I have a lot of code for a web based video editing/mashup site that I will probably start working on soon as well.

Cheers, Rick

Hi Rick,

Sounds like you are having some progress on your big dream now. Glad to hear the updates from you. No matter what one does, it's definitely tough to embark on, unless he's so lucky that everything went on smoothly during the first time.

I'm not here to discourage you, and I really wish to see some real sounding example of people who are really showing people what they can achieve with Linux and how they can make a living with Linux. I'm looking forward for the day to come. However, I do hope to see more people coding in Ubuntu/Linux platform instead of common Windows platform like what it is now. 

It's a norm for people to code in Windows compared to other OS, I think maybe Java and other source language are the only exceptions here? In fact, there should be more people willing to try out and there must be a market for people to do so. By the way, if there are is a market but no one is daring enough to make the first step and open up the market and show the world, hey, this is the golden market waiting for us, but we waited so long until now just to reap profits from there, we should have done it earlier! 

I, myself, would like to see myself coding not only in Windows but in Linux too. I hope to make it a reality or a dream comes true! I have not been so excited before, the Windows coding though can be considered as a "matured" market now, but I'm getting tired of it, I want to do something different. But first of all, I must be a good programmer first I think? I'm yet to reach that stage yet. I want to be at least good at what I'm currently doing before I embark on really big changes. But at the same time I do hope to learn about other opportunities, which would allow me to make a quick switch in the future too!

But, all the best to you in your pursue of open source life! Great choice! Walk with care, but do remember, we, the open source and Ubuntu community are all behind you to support you! You won't go wrong from there ;)

Regards,
Jenson

---

### Post by jenson on 2007-09-06
> **CptPicard said:**
> You're a brave one... I must admit that at first sight this reminds me of something...

[IMG]http://upload.wikimedia.org/wikipedia/en/d/dd/Gnomes_plan.png[/IMG]

1. Quit steady job at Microsoft to do something with Linux
2. ??
3. Profit!

;)

Independent consulting is tough, and doing migration consulting is going to be tougher still if you aren't really, really good at the technical details. Simple UI usability consulting is going to just force you into becoming an OpenOffice trainer, I'm afraid -- you're showing users where the button is now that they were used to pushing before.




Web pages don't pay, unless you get a really brilliant, viral idea, or have content that people actually want to pay for. I maintain a site for friend that generates real honest money to its members, and even the traffic there wouldn't pay for hosting costs, if we did have ads. Which we don't. Because people pay a % for the money that is made for them.



Hmm. Are you such a great code jockey on both Windows and Linux that you have some actual insights as to where such differences are? Yeah, it might be good blog/column material if you've got zen-like insights, but otherwise I'd think that programming is programming, and the differences are rather easily manageable by any programmer who is serious about his profession.



You're approaching this from a UI cognitive psychology viewpoint, which is different from a programming API viewpoint. APIs are best designed by competent, insightful programmers who have an understanding of what works. They are the best "usability" experts as far as code elegance goes. Applying some sort of cognitive psychology analysis to this perceived elegance of code sounds like a topic for an academic thesis for you, but I'm not sure if you'll be able to really contribute unless you're a coder god yourself.



Here's a better idea really. Although I sense that the more competent user just needs to be encouraged to give it a try, after which they manage well on their own, and the less competent user needs to just learn the new button placements by rote as they always have.

Good luck, though. Don't want to discourage you :p

Hey CptPicard,

You sounds like quite well-versed and experienced in this, aren't you? Great to see some good replies here too. I think what you've just said  make sense to me. But I believe no pain no gain ;)

You have to make the first step, else you would never succeed. I think you are not discouraging him, but you are actually giving him some direction and things to look out for. This is good for Rick too! I'm sure he's also aware of some of them if not all of what you've mentioned. By the way, he is brave enough to make the first step out and to do something who has not did it before, by starting as the first one, I'm sure there wil be the second, third, and so on. There would be a lot of people following his steps very soon. This will be a good sign by then. I would love to see this kind of motivation blossom.

Btw, I really hope to keep this thread going and receive updates from Rick once in a blue moon ;)

I like the spirit of Ubuntu!

Regards,
Jenson

---

### Post by dempl_dempl on 2007-09-06
> **CptPicard said:**
>  ...Applying some sort of cognitive psychology analysis to this perceived elegance of code sounds like a topic for an academic thesis for you...

Orwell used to write about that kind of English... He called that article 
"The Modern English and Politics"  :-P  .  You should become at least a lawyer :) ...

moephan : I don't know anything about consultancy, but , if your project is good enough, you will make a decent living.

One more thing. Linux runs about 11% of the PC's in the world. 
That's around 66 000 000 computers.
60% of servers on this planet are Linux-powered.
If that's not large enough market for you in order make some kind of bussiness ... he he ...

---

### Post by zipperback on 2007-09-06
> **moephan said:**
> Thanks for the advice. I do understand and appreciate that I am reasonably well paid now. However, I am NOT looking for a new job. I plan to quit and start making money for myself, rather than for a company that I work for. I am looking for feedback more on business ideas rather than how to get a job.

I guess I should have called the thread something more like "starting a Ubuntu based business" or something.

Thanks.

Cheers, Rick

If it were me, this is what I would do.

I would start building up my client base before quitting my job in my spare time, and NEVER during my normal work time.

Then once I have an solid steady income that I could live off of from the work that I do from my client base, I would then give my current job a written 30 days (yes a full month) notice, to give them time to find a replacement person to take over the position and to train them if needed. Also, I would be VERY careful in regard to going into business for yourself, if the company you work for is also in a similar industry (programmer working for a software company for example).

Also, I would work with an attorney to get the company that I would be starting fully up and running and protect from any legal recourse from my current employer, and to consult with them regarding any advise they would have about a potential conflict of interest about the company I would be starting and the one I would be leaving. There are many things to consider. Did I sign a non-disclosure agreement with my employer? Did I sign a non-competition agreement? There are numerous things I would have to consider in regard to things like this.


I would consult with an attorney, and when it came to my leaving the current company I was working for, I would make it as painless for them and myself as possible. Leaving on good terms would allow me to possibly come back if my business venture failed, and also it might open up a possible additional revenue stream because I might be able to even get my ex-employer as a client!

I would consult with an attorney who specializes in Open Source companies. These are of course just my thoughts on the subject, and not intended to be legal advise to anyone else.


- Jack
- zipperback

---

### Post by pmasiar on 2007-09-06
> **dempl_dempl said:**
>  You should become at least a lawyer :) ...

I am not sure why. CptPicard sounds like smart guy, who knows a lot about programming, even if more interested in theoretical questions, and knows to write and communicate. Why would you want him to be a lawyer? Or is "lack of communications skills" a requirement for a good programmer? 

BTW I agree with CptPicard assessment: If you have to support family, it seems little irresponsible just disembark on "search of sense" like that, jumping without having idea where you will land. I would not dare doing that: I would start something small on side, and only when I can see it is "going somewhere", I would jump. Free country of course and I wish luck anyone daring to jump, but I would not. YMMV.

> moephan : I don't know anything about consultancy, but , if your project is good enough, you will make a decent living.

You may not believe it, but I **do** know something about consultancy, and it is extremely easy **not** make decent living, unless you are really, really good. "good enough" might be not enough :-)

> If that's not large enough market for you in order make some kind of business ... he he ...

hehe .... and part of those users have commercial support agreement with big companies. Big part of the rest rely on free help on forums and are not ready to pay for it. ooops!

---

### Post by dempl_dempl on 2007-09-06
> **pmasiar said:**
> I am not sure why. CptPicard sounds like smart guy, who knows a lot about programming, even if more interested in theoretical questions, and knows to write and communicate. Why would you want him to be a lawyer? Or is "lack of communications skills" a requirement for a good programmer? 


I meant on latin vocabulary ...  Politicians use that kind of vocabulary When they want to be unclear about something :) ..
That was just a joke ... Ok , maybe not the best joke you've ever heard...
You know, sometimes the word you say sound different that the word you write  :)...

About other things : well, if you try to do some decent job apart from consulting , you will have better luck. 
Ofcourse it's hard  make a decent living from saying to people what they already know, unless you're very good at it.

You can be consultatnt if you're **really** good at what you're doing, but that's usually in general programming area ( program design , AI , etc )  ,   not with the stuff like Linux.

---

### Post by CptPicard on 2007-09-06
> **dempl_dempl said:**
> Orwell used to write about that kind of English... He called that article 
"The Modern English and Politics"  :-P  .  You should become at least a lawyer :) ...

OT, but funny you should say that. :) My initial career plan was that of a lawyer, but I didn't get into law school, as I just couldn't handle the rote memorization requirements of the entrance exam books. So I drew my conclusions early enough, decided I would have been unhappy as a law student, didn't try again and turned to my interest in computers. I've been more of a language than math person all my life, but as I did take the tougher math requirements at school, all I needed was to sweat it a little more than usual in undergrad math classes... and I even turned out a bit of a theory geek.

CS is essentially computational formal linguistics, so a skill in logically constructing your sentences goes a long way ;)  Most of the better hackers I know are very good at communicating a point.

Of course, English is not my native language and I've learned it mostly from books and computers (Sierra's and Lucasarts' old adventure games were great for that), so I must apologize if I come across as too erudite at times :p

---

### Post by dempl_dempl on 2007-09-06
No, I like using  "V for Vendeta" talk ( if you ever wacthed the movie you know what I'm talking about ) from time to time too.
As Edmund E. Black Adder would say:* I'm spaptic, frasmotic and even companctuos over those counterfibularities expressed in your vocabulary... :)*

---

### Post by moephan on 2007-09-06
In terms of this:
> 
You're approaching this from a UI cognitive psychology viewpoint, which is different from a programming API viewpoint. APIs are best designed by competent, insightful programmers who have an understanding of what works. They are the best "usability" experts as far as code elegance goes. Applying some sort of cognitive psychology analysis to this perceived elegance of code sounds like a topic for an academic thesis for you, but I'm not sure if you'll be able to really contribute unless you're a coder god yourself.


I spent nearly 10 years at Microsoft designing for developers, mostly working on Visual Studio, .NET, and related projects, but also on other projects throughout the company. I watched hundreds of programmers working in the usability lab, and in their offices. My designs and products have been very well received by the market place, so I do flatter myself to think I have some insights into the way Visual Studio developers think. 

I also worked with scores of teams, and found that *Some* developers are good at API design, but most aren't and know it. Having someone on the team who can code and design for the actual intended users adds tremendous value to teams designing platforms. Fortunately for me this value has been recognized, and I have been rewarded for it.

BTW, I agree with your South Park analogy, and think it's funny. However, when you work somewhere as intense as Microsoft, the idea of developing a business on the side is not realistic for all but the junior people, or the most checked out people. At least that's what I have found for myself, being a focused and intense worker. I knew that I would have to jump and assemble my parachute on the way down, or I would never leave. Some people are comfortable with that, and some people aren't.

On the other hand, referring back to the recognition and rewards point, I saved up a year's worth of salary, so the whole enterprise probably isn't as reckless as it appears to some. I feel that a little time dedicated to discovering what is possible, what works, and what my limits are will be time and money well spent if I am having fun and learning.

In the end, I could always go back to Microsoft or get a job at another company. In fact, a local FOSS-based company contacted me through a head hunter yesterday, so I'll be talking to them next week, you never know ...

Thanks to everyone for the thoughts and checking in. Interesting to see the different levels of risk tolerance and different views on the industry.

Cheers, Rick

---

### Post by pmasiar on 2007-09-06
> **moephan said:**
> I also worked with scores of teams, and found that *Some* developers are good at API design, but most aren't and know it. 

maybe you **are** API design god, and godspeed for you. But I found in my experience (and anecdotal evidence on blogs suggests) that test-driven development leads natural way to develop API for your code - so you can test it. Just a thought.

---

### Post by jenson on 2007-09-06
> **moephan said:**
> In terms of this:


I spent nearly 10 years at Microsoft designing for developers, mostly working on Visual Studio, .NET, and related projects, but also on other projects throughout the company. I watched hundreds of programmers working in the usability lab, and in their offices. My designs and products have been very well received by the market place, so I do flatter myself to think I have some insights into the way Visual Studio developers think. 

I also worked with scores of teams, and found that *Some* developers are good at API design, but most aren't and know it. Having someone on the team who can code and design for the actual intended users adds tremendous value to teams designing platforms. Fortunately for me this value has been recognized, and I have been rewarded for it.

BTW, I agree with your South Park analogy, and think it's funny. However, when you work somewhere as intense as Microsoft, the idea of developing a business on the side is not realistic for all but the junior people, or the most checked out people. At least that's what I have found for myself, being a focused and intense worker. I knew that I would have to jump and assemble my parachute on the way down, or I would never leave. Some people are comfortable with that, and some people aren't.

On the other hand, referring back to the recognition and rewards point, I saved up a year's worth of salary, so the whole enterprise probably isn't as reckless as it appears to some. I feel that a little time dedicated to discovering what is possible, what works, and what my limits are will be time and money well spent if I am having fun and learning.

In the end, I could always go back to Microsoft or get a job at another company. In fact, a local FOSS-based company contacted me through a head hunter yesterday, so I'll be talking to them next week, you never know ...

Thanks to everyone for the thoughts and checking in. Interesting to see the different levels of risk tolerance and different views on the industry.

Cheers, Rick

Cool, Rick. Looks like the snowball start rolling bigger and bigger. So there's a market out there, isn't it? Not being a good programmer, I do aware that some of my points are worthless or my opinions or point of view is irrelevant to the topic.

I do have some funny thoughts too, like horning my skills and knowledge on Physics and Maths like what I used to do it very crazily and wish to make a living with that. But after that, I turned to computing, which attract my interests most of the time, though I'm not that good at it, at least I've been earning a living with it ever since I graduated from a local Polytechnic, not a U grad! Gosh, but the life here is harsh but still manage to stay alive in the industry XD

I do have some ideas of running a start-up providing not only services in MS, but also in Linux and other OS or system. My current company is focusing mainly on MS products and solutions, which I cant stop making myself from predicting the future of it, which is the company will soon to die down in about 10 years time, if they are to continue competing with other solution provider who provide much wider range of services and solutions.

But as a hobby, I like to keep myself to Ubuntu Linux, and open source, of course a living with Ubuntu/Linux too! I don't mind learning to code and work in Ubuntu and ultimately become one of the Linux or FOSS developers. I wouldn't mind to contribute more to people from my other areas of interest too! Like Maths and Physics, audiophile, etc and etc. My native language or mother tongue is not English too, so please pardon me for my poor English and communication skills.

I always happy seeing people sharing thoughts and experiences here, as well as interacting and having discussion on one particular interesting or important topic.

This topic is worth pondering about and would definitely results in fruitful outcome, experience and thoughts from the discussions. Love to see that so many people are responding to the OP or thread owner's post. Why not keep this as a blog entry and update it regularly too? ;) Hehe...

Ever since I joined Ubuntu, I never regretted for a switch, though, in fact, I'm still dual booting with XP, but XP is mainly used for daily coding and stuff that still doesn't work well in Ubuntu yet.

Well, long live Ubuntu, it's community, and Rick too!

Regards,
Jenson

---

### Post by CptPicard on 2007-09-07
Nice to see you back, Rick...

It just hit me that may I have sounded a bit disrespectful of your work history at MSFT, it was not my intention.. I trust you know what you were doing there ;)

Anyway, you got me quite intrigued by the idea that a cognitive psychologist is able to divine proper *API* design by watching programmers work.. :) Now, I do realize that usability design regarding programmers' work habits and tools is crucial in particular when you're working on, say an IDE... but I wonder how you do usability studies of programming interfaces? Do you measure the amount of cursing emanating from the programmer when he is unable to make a library do his bidding the way he would intuitively expect it should work? :)

I still prefer to believe that the best developers are the best API designers. They have complete mastery of the language, which is the first requirement for meaningful API design. They use code, so when writing libraries, they hopefully know how to make their own code usable. Programming itself is nothing more than putting together internal APIs, and API design for the external ones is just a matter of placing the demarcation line appropriately. In order to evaluate the cognitive needs of a programmer, you need to be one and have the mind of one. Anything else sounds like either design by committee or the unleashing of intrinsically perfect things from Heaven upon unsuspecting poor developers. :)

If you're interested in differences between FOSS developers' mindset and that of the corporates', there just might be one, then. FOSS programming tools and libraries have evolved out of a state of creative anarchy, and the end result is a functional and flexible, yet sometimes quirky and occasionally inconsistent platform. It might require a bit more of competence to get started, but I would bet you're a better person for it after you've mastered it.

Most developments in the FOSS programming world are initially born out of an idea of a solution for a genuine problem someone is having. It typically is the brainchild of a single individual. If the solution really is good, it will gather mindshare. This holds particularly well for libraries and programming tools, as programmers will gravitate to and develop further what initially works for them.

It really is the cathedral vs. the bazaar phenomenon... I suspect a lot of people in the FOSS community would be suspicious of the MSFT approach, if it is what I gather ;)

---

### Post by moephan on 2007-09-07
lol ... yeah I've seen a lot of really mad coders in my usability lab studies. We developed a lot of great methods for usability testing APIs, and significantly improved them between iterations. In fact, I had a recent experience where we iterated on the API between each usability participant and ended up with an awesomely easy to use API by the end of the week. If you want to learn a lot more about API usability, Google Steven Clarke. You'll find methods and concepts that are battle tested and have proven quite effective in practice.

Also, in terms of "the best developers" through rigorous psychology testing I have calculated that nearly half of the developers are below average. Unfortunately it turns out that the same principle applies to cognitive psychologists too, so you have to be careful who you work with. I wonder if some kind of underlying principle is effecting these finding? :) 

Finally, I love the bazaar model for development. In fact, I think one of the things about FOSS that drew me out of Microsoft is that you don't "live off of FOSS", you contribute to it. Furthermore, you can contribute in your own quirky way. However, it also seems that the vast majority of open source projects fail. That's just part of life in the bazaar. I'd like to think that by approaching design of everything, including developer tools, APIs, and other platform components in a user-centered way, even the best developers can improve their chances of success.

As you can see I am very passionate about user-centered design for developers :) I think that I can make a real contribution by helping Visual Studio programmers get a real toe hold onto Ubuntu, and hopefully make a little money along the way. FWIW, Visual Studio programmers do pay for training, classes, certification, etc... so taking a one day training (using their company;s training budget most likely) to learn a bit about programming on Ubuntu wouldn't be a weird thing for them to do. Don't forget, these people already know and love the Microsoft, so I have the opposite concern. I see Visual Studio developers come to these forums and ask pretty simple question, and I can't help imagining they feel a little alienated from the community when their questions about the right GUI toolkit spawns flame wars about the merits of c++ versus python.

Cheers, Rick

---

### Post by jenson on 2007-09-07
Two great minds are sharing thoughts and ideas here, surprises and sparkling outcome would be the result!

Cool to see how great you are think and work, and to realize how small I am in IT industry.

I totally have no idea how MSFT culture's like. I only know some prefer MSFT culture, while some others prefer Google style. I have no particular preferences. In fact, I like the way MS has made the Visual Studio but I don't like it's too resource-hungry. I would prefer to have something less resource intensive, and I would love it to be more powerful as I think VS 2005 is on the right track, not sure about how VS 2008 will turn out to be.

Talking about API, I've yet learn much about it yet, nor do I have chance to see or learn how can I code my own API and make the best out of it. My company's policy is quite different, they don't really sponsor us for training if we are not those who has been working with them for at least 4 to 5 years. And none of them know about API programming too. 

I'm always told about learning to code or make use of API is the best way for me to move on from there, but without guidance or any useful resources, I always found myself ended up getting lost and have to give up on that.

But at least I still try to horn my skills .NET and how to improve the usability of my codes, and possibilities of future integration or implementation of new modules and functions, as well as, easy-to-understand codes and simple and nice to use program with good back-end supports.

Two great minds here did inspired me a lot =) Thanks for making this thread come back alive once again, I really feel great that I've found this thread :)

---

### Post by pmasiar on 2007-09-07
> **moephan said:**
>  I have calculated that nearly half of the developers are below average. Unfortunately it turns out that the same principle applies to cognitive psychologists too, so you have to be careful who you work with. I wonder if some kind of underlying principle is effecting these finding? :) 

you are joking, right? Basic statistics: 50% of anything is at 50% of it or less :-) That's how average is calculated. :twisted:

---

### Post by pmasiar on 2007-09-07
> **jenson said:**
> Talking about API, I've yet learn much about it yet, nor do I have chance to see or learn how can I code my own API and make the best out of it. ... those who has been working with them for at least 4 to 5 years. And none of them know about API programming too. 

API is **not** rocket science: create code what you can use somewhere else, and you have API to your custom library. Of course creating **good** API **is** rocket science, and is harder. :-)

> I'm always told about learning to code or make use of API is the best way for me to move on from there, but without guidance or any useful resources, 

You do write code, right?

If you cannot get any usable advice at work, join some (if possible relevant) free project. Plenty of code to learn from!

---

### Post by CptPicard on 2007-09-07
> **pmasiar said:**
> you are joking, right? Basic statistics: 50% of anything is at 50% of it or less :-) That's how average is calculated. :twisted:

Bzzzt, wrong. In the set {1, 1, 1, 10} average is 3,25 and 75% are below average. You're thinking of the median here where by definition 50% is at or below it. Now you don't get a :KS :(

Then again, 50% of developers being below average would be evidence for a Gaussian distribution of developer ability, which wouldn't surprise me at all.  A lot of measures like that are distributed that way.

---

### Post by moephan on 2007-09-07
> **pmasiar said:**
> you are joking, right? Basic statistics: 50% of anything is at 50% of it or less :-) That's how average is calculated. :twisted:

Yes, I was joking

---

### Post by jenson on 2007-09-09
> **pmasiar said:**
> API is **not** rocket science: create code what you can use somewhere else, and you have API to your custom library. Of course creating **good** API **is** rocket science, and is harder. :-)

> I'm always told about learning to code or make use of API is the best way for me to move on from there, but without guidance or any useful resources, 

You do write code, right?

If you cannot get any usable advice at work, join some (if possible relevant) free project. Plenty of code to learn from!

Hi pmasiar,

Hey great reply, I wonder any link that you can point me to for more on what you have mentioned in your post? :)

I would love to learn more and perhaps start writing good API for myself and try to influence the rest to learn how to do it too. Meanwhile I hope to learn more on it first before I join any project?

Yes, I write codes everyday, but they are .NET codes.

**EDIT: I work as a programmer working primarily on Visual Studio 2005 IDE with VB as the language though I do hope that I can do some Java and PHP programming there, most likely has to keep them as my hobbies during free time now :(**

Regards,
Jenson

---

### Post by pmasiar on 2007-09-10
> **jenson said:**
>  any link that you can point me to for more on what you have mentioned in your post? :)
Meanwhile I hope to learn more on it first before I join any project?
Links to any project? It is **you** who knows best what your interests are.

If you want some interesting project as a hobby, don't bother with Java or PHP. Take a look at pygame: great API to write games. This sounds more like a fun hobby project!

They have game repository with sources, so you can find a game which you like, and learn how it was done. Python is great language, can used instead of PHP for web apps, or instead of Java anywhere :-) There is even Jython, Python implemented on top of JVM. Wiki in my sig has plenty of links.

Edit: Interesting reading ironPython for .NET:
[Silverlight - scriptable in Python](http://www.voidspace.org.uk/python/weblog/arch_d7_2007_09_08.shtml#e818) and [Chapter 1 "IronPython in Action"](http://www.manning.com/foord/meap_foordch1.pdf) explaining IronPython history, hot it fits in .NET, DLR, and why it is exciting. Good read.

---

### Post by Uncle Che on 2007-09-10
> **moephan said:**
> 

What do you all think? Do I stand a chance? Is there anything I'm missing? Does anyone make their living with Ubuntu?

Thanks.

Cheers, Rick

Move someplace else. Seattle is expensive. Move to a place like the Philippines, Thailand or someplace in South America, your expenses will drop by a lot and you can easily make do on a lower salary level.

---

### Post by jenson on 2007-09-11
> **pmasiar said:**
> Links to any project? It is **you** who knows best what your interests are.

If you want some interesting project as a hobby, don't bother with Java or PHP. Take a look at pygame: great API to write games. This sounds more like a fun hobby project!

They have game repository with sources, so you can find a game which you like, and learn how it was done. Python is great language, can used instead of PHP for web apps, or instead of Java anywhere :-) There is even Jython, Python implemented on top of JVM. Wiki in my sig has plenty of links.

Edit: Interesting reading ironPython for .NET:
[Silverlight - scriptable in Python](http://www.voidspace.org.uk/python/weblog/arch_d7_2007_09_08.shtml#e818) and [Chapter 1 "IronPython in Action"](http://www.manning.com/foord/meap_foordch1.pdf) explaining IronPython history, hot it fits in .NET, DLR, and why it is exciting. Good read.

Hi Pmasiar,

No, I mean learning resources for API, since you also mentioned in your reply for learning from pygame as practices for writing API, so I think I don't need to ask the second time again =)

Why Java and PHP is less useful in API programming compare to Perl? Hmm..please enlighten me on that =)

**EDIT: And sorry Moephan, for hijacking your thread a bit :p**

Regards,
Jenson

---

### Post by pmasiar on 2007-09-11
let's move someplace else. If you want to discuss in deep how to create API, and compare languages, ask it in details in separate thread. This thread is interesting, let's keep it clean

---

### Post by jenson on 2007-09-11
Yes it is. I'll be keeping this thread clean enough and wait for updates from Moephan ;)

It's a good working model for us to learn from him too ;) :popcorn:

---

### Post by moephan on 2007-11-22
Thought I'd drop a quick update on what's happened to me since September.

I spent the first two weeks after leaving my old job kind of knocking around the house and recharging. I needed to recharge a little.

Then I dove deep into working on my web site ([http://calorielookup.com](http://calorielookup.com)). I spent two weeks working 6-10 hours per day on it. I discovered a couple of things:
1. Making money off of the web site would require a marketing effort and a cash outlay. I gathered enough trend data to project out into various scenarios and could see that there was a good chance of making a bit of living, but a good chance I would run out of all of my savings before profits kicked in, if ever. Typical stuff. Business is risky.
2. Working alone day after day makes me crazy. All I could think about was my code, and I ended up in a weird haze.
3. There are tons of great jobs in the Seattle area for someone with experience in the tech industry.

So after 2 months I accepted what seems to be a really great job, but in a really small place. The developers I work with are very talented (I'm not a developer in this role, and the devs are much more talented than I am, especially the lead developer, like a couple of planes above me in raw talent, not to mention experience). I've been there a few weeks now, and it seem to be working out. I'm pretty psyched and feel incredibly lucky to be in the right place at the right time kind of thing.

The shop is "mostly" Linux based, and Ubuntu is commonly used by technical and non-technical staff. Our server infra-structure is also mixed, for the time being. So I did get my wish of moving out of a Windows based environment, and working in a smaller environment as well.All in all, things worked out really well for me, though I didn't have the staying power to pull off working for myself in a Linux focused manner.

Cheers, Rick

---

### Post by Odin25 on 2007-11-27
Hi Rick and all contributors!

I just read the whole thread.

Awesome, thanks for sharing! 
It shows what a great community, expertise and spirit is around here

I think it is a great development: you made a decision and went for it with all those ups and downs and little hangups and arrived at a new place. 

Who knows, maybe it's just a step on your way further to your goal ("...working for myself on a Linux focused manner...") if it is still the land where you want to see yourself sometime.

And hey, you are a lucky guy having such a great family supporting you on your quest.

Thanks again, good luck, may your path/and goals become even more clearer in the new environment!

Odin @  walhalla :-)

---

### Post by jespdj on 2007-11-27
Congratulations with your new job! :)

---

