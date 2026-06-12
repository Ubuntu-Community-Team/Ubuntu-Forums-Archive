---
title: "Visual Basic? Need it for a c++ project"
date: 2007-03-02
forum: Programming Talk
---

### Post by Tag_yer_dead on 2007-03-02
hey guys, 
ive been looking around for a Visual Basic compiler because i need to add in a vb form to a c++ project (dont ask lol).  Does any one know any places i can find an exact Visual Basic clone, not those "Oh were almost visual basic!" things?

Thanks

---

### Post by Tag_yer_dead on 2007-03-03
no ideas?

---

### Post by joselin on 2007-03-03
Check this out:

[http://www.mono-project.com/Visual_Basic](http://www.mono-project.com/Visual_Basic)

---

### Post by pmasiar on 2007-03-03
> **Tag_yer_dead said:**
> ive been looking around for a Visual Basic compiler because i need to add in a vb form to a c++ project (dont ask lol).  Does any one know any places i can find an exact Visual Basic clone, not those "Oh were almost visual basic!" things?

Let me explain some background first.

[Visual Basic]("http://en.wikipedia.org/wiki/Visual_basic") is a proprietary language (owned by Microsoft), running on top of proprietary API .NET, which has only one implementation - Windows. IIUC, VB was not submitted to any standard, the only "standard" is what MS says it is. To implement it, you need to reimplement VB for Windows, including all warts, quirks and bugs, and without any API  documentation. Sound like a fun? Not for me.

[ximian]("http://en.wikipedia.org/wiki/Ximian") is a company which decided to implement .NET for Linux anyway - it is called [Mono]("http://en.wikipedia.org/wiki/Mono_%28software%29") and they got bought by old MS enemy, Novell. MS won the LAN OS wars, Novell made peace and in controversial move, bought rights to use in Mono any "intellectual property" (patents) MS might have in .NET, and MS promised not to sue Novell Linux Mono users. Do you fell safer yet?

From the point of free software developer reimplementing VB does not make any sense - it is not a language significantly better than any other existing free language (in fact, VB sucks), and using it on any other distro platform except paid-for Suse is invitation to MS to sue you.

Free software works best if every developer solves an itch he needs to solve for herself, and shares the results. You have the itch, you have to pitch sweat equity to solve it. And even if you do, not many other developers will be interested for reasons I explained above.

You get yourself trapped in vendor lock-in trap. Either get comfortable in your jail cell and pay for code you use, or get out and use free software, like C++. I do not think any exact VB clone is going to be created - there is no free software itch to do it. Just the opposite - is better to steer away from .NET patents. Check Suse and Mono, maybe you have some luck.

---

### Post by daniel of sarnia on 2007-03-03
> **pmasiar said:**
> Let me explain some background first.

[Visual Basic]("http://en.wikipedia.org/wiki/Visual_basic") is a proprietary language (owned by Microsoft), running on top of proprietary API .NET, which has only one implementation - Windows. IIUC, VB was not submitted to any standard, the only "standard" is what MS says it is. To implement it, you need to reimplement VB for Windows, including all warts, quirks and bugs, and without any API  documentation. Sound like a fun? Not for me.

[ximian]("http://en.wikipedia.org/wiki/Ximian") is a company which decided to implement .NET for Linux anyway - it is called [Mono]("http://en.wikipedia.org/wiki/Mono_%28software%29") and they got bought by old MS enemy, Novell. MS won the LAN OS wars, Novell made peace and in controversial move, bought rights to use in Mono any "intellectual property" (patents) MS might have in .NET, and MS promised not to sue Novell Linux Mono users. Do you fell safer yet?

From the point of free software developer reimplementing VB does not make any sense - it is not a language significantly better than any other existing free language (in fact, VB sucks), and using it on any other distro platform except paid-for Suse is invitation to MS to sue you.

Free software works best if every developer solves an itch he needs to solve for herself, and shares the results. You have the itch, you have to pitch sweat equity to solve it. And even if you do, not many other developers will be interested for reasons I explained above.

You get yourself trapped in vendor lock-in trap. Either get comfortable in your jail cell and pay for code you use, or get out and use free software, like C++. I do not think any exact VB clone is going to be created - there is no free software itch to do it. Just the opposite - is better to steer away from .NET patents. Check Suse and Mono, maybe you have some luck.

I am sure C# and I think .NET is an ISO stander, Mono is open source and does not infringe on any M$ IP no matter what they want people to think. 

LIKE hell if mono was .net pushed though a decompiler and ported to linux that would be one thing, but that's not the case at all. Mono is a ground up open source implementation of an ISO standard, it doe NOT infringe on M$ IP. If they tried to sue they'd lose.  

But VB does suck. lol

---

### Post by pmasiar on 2007-03-03
> **daniel of sarnia said:**
> I am sure C# and I think .NET is an ISO stander, Mono is open source and does not infringe on any M$ IP no matter what they want people to think. 

It might be just me - if I am not sure about some basic fact, i go and check Wikipedia. Both .NET and C# is mentioned as ECMA standard, now *I* am *more* sure than you :-) that they *are* standards. 

But having a standard does not mean anything. Most prominently, it does not mean that .NET libraries can be reimplemented as free software without regards of any possible patents. Patent lawyers have the term for it: something like "equal and nondiscriminatory access" - which means everyone has to pay same amount for using patent, but it does *not* mean it is free. 

> LIKE hell if mono was .net pushed though a decompiler and ported to linux that would be one thing, but that's not the case at all. Mono is a ground up open source implementation of an ISO standard, it doe NOT infringe on M$ IP. If they tried to sue they'd lose.  

IMHO you are confusing two terms mixed in "intellectual property" (IP) laws:
- *copyright* law (where ground-up independent writing of Mono is relevant) 
- *patent* law (where it is not). 

These are very different concepts, limiting different activities by different mechanisms for different timeframes, and that is the reason why "IP" is meaningless term used to obscure problems and not to clarify them. "IP" also includes trademark law - yet another different animal.

A [patent]("http://en.wikipedia.org/wiki/Patent") is a set of exclusive rights granted by a state to a patentee (the inventor or assignee) for a fixed period of time. patent provides the right to *exclude others* from making, using, (...) the patented invention. It means exclude even if 3rd party reinvented patented issue independently - independent reinvention is just not relevant for patent law. 

Sadly, independent development of Mono clears the copyright issue, but is totally irrelevant for any patent litigation - and this is exactly why patenting software is wrong, and copyrighting should be enough.

If you do not believe me or want to learn more, spend couple of afternoons at groklaw website. It is written by law expert, paralegal, not by programmer hackers.

And this is one of the law traps which is GPL version 3 supposed to solve.

---

### Post by Tag_yer_dead on 2007-03-04
lol yes i agree that visual basic is an obsolete language, however i need to implement a visual basic code into C++.  Long story dont worry lol, just need to find out how to use it

---

### Post by Tag_yer_dead on 2007-03-04
hey guys sorry for double post and i realize i soudn like a noob lol, but which version do i need?  Im running Ubuntu 6.10.  Thanks guys lol.

---

### Post by Tag_yer_dead on 2007-03-04
ne one?

---

### Post by daniel of sarnia on 2007-03-04
> **pmasiar said:**
> 

IMHO you are confusing two terms mixed in "intellectual property" (IP) laws:
- *copyright* law (where ground-up independent writing of Mono is relevant) 
- *patent* law (where it is not). 

These are very different concepts, limiting different activities by different mechanisms for different timeframes, and that is the reason why "IP" is meaningless term used to obscure problems and not to clarify them. "IP" also includes trademark law - yet another different animal.

A [patent]("http://en.wikipedia.org/wiki/Patent") is a set of exclusive rights granted by a state to a patentee (the inventor or assignee) for a fixed period of time. patent provides the right to *exclude others* from making, using, (...) the patented invention. It means exclude even if 3rd party reinvented patented issue independently - independent reinvention is just not relevant for patent law. 

Sadly, independent development of Mono clears the copyright issue, but is totally irrelevant for any patent litigation - and this is exactly why patenting software is wrong, and copyrighting should be enough.

If you do not believe me or want to learn more, spend couple of afternoons at groklaw website. It is written by law expert, paralegal, not by programmer hackers.

And this is one of the law traps which is GPL version 3 supposed to solve.

Good thing I'm not going into law I guess, But .net is an ecma standard as well as just being made an iso standard according to recent podcast i heard miguel on. Until it goes to court and loses I wouldn't worry. I not using it much yet think it's a good technology from what I've seen and I have to be able to trust miguel de icaza he started gnome and is just a really smart guy. He is a huge in open source, and has been a developer of gpl'ed software much longer then you or I. Basically I am just saying I don't think he'd steer us wrong and I know I nor a number of other people that are criticizing his work are in much of a position to do so.     

I just trust miguel because he's been around so long and the work going into mono looks really good. I really don't think it's realistic that M$ is going to go around suing everyone even if they had a case, which is not so likely in itself. At then end of the day I just trust miguel de icaza more they you (no disrespect intended). Maybe if someone like RMS or Eben Moglen speaks out ageist it I'll start to worry...

---

### Post by daniel of sarnia on 2007-03-04
> **Tag_yer_dead said:**
> hey guys sorry for double post and i realize i soudn like a noob lol, but which version do i need?  Im running Ubuntu 6.10.  Thanks guys lol.

[http://www.mono-project.com/Visual_Basic](http://www.mono-project.com/Visual_Basic)

All you have to do is apt-get mono from the repos and that should do it.

---

### Post by Dylnuge on 2007-03-04
Mono is open-source and built from the ground up...that does not cut it. A patent works differently. Lets say I build a device. I copyright the "code" for this device-the software components that make it work. Someone else can build a similar device if they design it from the ground up. Lets say I patent the device (before someone else starts construction of a similar device). I can patent methods. I patent the method that the device functions in-what it does, how it works, etc. No one can build a similar device-they must completely reinvent the wheel.

Microsoft's patents make it illegal to build a device (lets call .NET and Mono devices fo now) that provides a platform for Microsoft Patented Languages-VB, C#, etc. Mono is legal on SUSE Linux, because Novell worked out the details. It is not legal on Ubuntu.

Now, there is no need for the .NET platform. It has tons of fallbacks. Here are some:
1. It is single platform.
2. It is proprietary.
3. It is expensive. Ever hear of a programming language you have to pay for? (Express Editions remove this Cavet somewhat, but they remove IDE features that don't exist elsewhere).
4. It is a Microsoft-style removal of compititon.

Some people hate Microsoft. I hate them for some things, but not all. One of these things is standards-tweaking. Microsoft does not operate on standards-they operate on a lack of them. Can't get Java? Build J. Make VB and C#, so that people feel compelled to use non-standardized software which literally **requires** an expensive IDE to compile. C++ too standardized to change? Build a very popular IDE for it, and build a brand new platform which de-standardizes it. That is why .NET exists. It has some features-but it primarly removes standards from standardized languages like C++.

Programming is complex. Everyone says to use a different language. [Phoenix]("http://www.janus-software.com/phoenix_features.html") is a nice VB equivalent, but no .NET platform. That and Mono are as close as you will ever get in Linux.

Sorry if this does not cut it for you. If you need VB, you need Windows.

---

### Post by pmasiar on 2007-03-04
> **daniel of sarnia said:**
>  I just trust miguel de icaza more they you (no disrespect intended). Maybe if someone like RMS or Eben Moglen speaks out ageist it I'll start to worry...

Eben Moglen says that GPL v3 will be specially changed to NOT allow patent protection for some GPL users and not for others - the patent protection trick which Novell uses now (and per Moglen, is legal for GPL2). 

It is up to you to use Mono - or avoid it. I use daily another Miguel project - mc (Midnight Commander), clone of Norton Commander. He is smart guy I agree. But Miguel is hacker, not a lawyer - I will ask him for advice on how to code, but not about patent law.

---

### Post by Pietr The Engineer on 2007-04-04
I'm afraid I can't talk about the legal niceties, Tag, and you probably are wondering why on earth nobody has answered.
Today I re-installed Mono, version 1.2.3.1_2, the one which is supposed to work with VB.NET.
Guess what?
I get an error that stops it from even compiling(in any rejigged form with any combination of 'references' to internal packages)any kind of simple 'Hello World' VB project.
My guess is that this 'nearly' version is designed to work wiht Debian but doesn't extend to Edgy.(Which I am also using).
On the plus side, the C# part of mono appears to work, so you might be able to port your project to that.
Also if I remember from my VS2005, there are commands in C# specially for importing MFC-type functions in C++(I know, no MFC)to C#.
Sorry I can't help.
I was looking for definitive advice myself.
It's a pity, as I was hoping to run up a ASP.NET website on Linux.

---

### Post by ZakSmith on 2007-04-05
I'm taking a Visual Basic class (required for my degree), so what I did was download VMware's Workstation for Linux 30-day-trial(it's like Virtual PC from Microsoft, just the other way around) and installed a copy of Windows XP that I bought years ago but haven't used in a while. Now I have an Ubuntu 6.10 system with a virtual Windows XP system inside. I use the Windows VPC just for school without dual booting, I wouldn't recomend this for gaming though, to slow. Maybe this course of action could help.

[http://www.vmware.com/download/ws/](http://www.vmware.com/download/ws/)

---

