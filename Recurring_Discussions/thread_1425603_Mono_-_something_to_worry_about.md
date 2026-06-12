---
title: "Mono - something to worry about?"
date: 2010-03-09
forum: Recurring Discussions
---

### Post by svaens on 2010-03-09
Hi all, p

I have never been a fan of the idea of Mono. And I was just now doing some reading about Mono dependencies in Gnome. I thought i'd test that out myself, and look to see if mono was there on my machine. Sure enough, it was. So I decide i'd try and remove it. 

Looked like half of gnome was going with it!

At a time where corporations are going crazy with patents, and courts are hand in hand, isn't this a bad bad thing that a 'free' operating system like Ubuntu has Microsoft dependencies ? 

Why did we let this happen? 
Is it dangerous? Or is Richard Stallman just paranoid?

I would myself rather lean towards caution than take the risk, that is mono. 

What are other opinions out there?

Should we be working towards complete removal of mono from debian/Ubuntu ?

---

### Post by forrestcupp on 2010-03-09
Mono is not Microsoft.  It is a free and open source implementation of specs that are released for public use, and it has always been free.  They removed the offending windows.forms parts of it very early on, and there will be no trouble.

---

### Post by gnomeuser on 2010-03-09
[The official stance on Mono from the Ubuntu Technical Board](http://ubuntuforums.org/showthread.php?t=1200946)

So, no.

End of Thread

---

### Post by Queue29 on 2010-03-09
but wait, boycott novel says mono was sent by Satan himself to destroy open source, promote microsoft, and kill puppies.

---

### Post by svaens on 2010-03-09
@Queue29

Sarcasm? 

Yes I know. Exactly why I posed the question. I am not knowledgeable enough in terms of legal matters to know if this is all paranoia or anti-novell propoganda > mono was sent by Satan himself to destroy open source, promote microsoft, and kill puppies. or a real concern.

---

### Post by doas777 on 2010-03-09
mono is just about porting C# to non-ms systems. I really like C# as do many developers that write code that has been added to the ubuntu-desktop. asking ubuntu to remove mono, is like telling those developers what langague to work in.

I've said it before: i won't lobby to have Your runtime removed from ubuntu, if you will extend me the same courtesy.

also, gnome does not directly use mono, but the ubuntu version of gnome does. if MS were actually able to level a legal  claim against it's use (which would be hard, as it has been open sourced through the ECMA) we would just drop the apps that use it (like tomboy iirc).
[http://port25.technet.com/archive/2009/07/06/the-ecma-c-and-cli-standards.aspx](http://port25.technet.com/archive/2009/07/06/the-ecma-c-and-cli-standards.aspx)

MS bought into novell to give their "open initiatives" some credibility, so hopefully they will continue down that path.

---

### Post by Tibuda on 2010-03-09
> **svaens said:**
> At a time where corporations are going crazy with patents, and courts are hand in hand, isn't this a bad bad thing that a 'free' operating system like Ubuntu has Microsoft dependencies ? 
Are you talking about [those drivers](http://www.microsoft.com/presspass/features/2009/Jul09/07-20LinuxQA.mspx)? Because Mono has no Microsoft code.

> Why did we let this happen?
What, the drivers? My sig says what Linus said about those drivers.

> Is it dangerous?
What, Mono? No. Microsoft kernel drivers? Neither.

> Or is Richard Stallman just paranoid?
Yes.

> I would myself rather lean towards caution than take the risk, that is mono. 
There's no more risk in Mono than in Samba, Wine, FAT/NTFS modules, Ndiswrapper, and much more stuff out there.

> What are other opinions out there?
On Mono? It is a great development framework.

> Should we be working towards complete removal of mono from debian/Ubuntu ?
No. Let's not stop the progress because of paranoia. We better split Gnome from GNU/FSF.

---

### Post by fewt on 2010-03-09
> **svaens said:**
> Should we be working towards complete removal of mono from debian/Ubuntu ?

What a foolish idea.  The Microsoft community promise is legally binding.

---

### Post by svaens on 2010-03-09
> What a foolish idea.

It isn't my idea. I am just going on what i've read on various blogs and websites. There is real concern out there! Which is why I am here to ask the guys and gals that might know better than myself just what all this is about, and if there is anything in all this 'anti-mono' talk.

---

### Post by fewt on 2010-03-09
> **svaens said:**
> It isn't my idea. I am just going on what i've read on various blogs and websites. There is real concern out there! Which is why I am here to ask the guys and gals that might know better than myself just what all this is about, and if there is anything in all this 'anti-mono' talk.

That's the bigger problem. All this made up concern over nothing is really harming Mono which in effect harms all desktop distributions.

All this anti-mono talk is garbage.  Unfortunately to those that don't know better it is a really very believable story made up by the FSF.

---

### Post by Simian Man on 2010-03-09
I'm glad to see the people here are responding so intelligently to this.  Mono is not a legal threat at all as C# is an open standard and Mono is an open source implementation of that standard.  The minority who says it is are largely just upset at having something to do with Microsoft on their computer and like to make as much noise as possible over it.

---

### Post by forrestcupp on 2010-03-09
There is nothing in all the "anti mono" talk other than that a bunch of people are mad that Novell made an ip protection deal with Microsoft.  There is nothing wrong with mono and no one is ever going to get into any trouble over it.

---

### Post by svaens on 2010-03-09
Also, Though they have been far less than the 'nays', the 'yays' seem to leave their vote and run. Why is that? Could I hear some constructive argument to the positive ? Or are they afraid to discuss their paranoia ? I will be honest enough to say that the blogs I have read sparked my own concern, to the point where the first vote on this thread is mine. a 'Yes'. But I am willing to have you all inform me to the point where I would reconsider my previous uninformed stance.

---

### Post by mickie.kext on 2010-03-09
I did not voted a pool because my opinion does not match any of options. 

I think they wont sue, they have made a promise which they say it is legally binding.

They need Mono to compete with Java right now. .NET runs only on Windows, it is proprietary, and it has "vendor lock-in written all over it. Java is open source, and also have few independent open source implementations (Apache Harmony, GNU Classpath and other), it runs _everywhere_... So Microsoft needs Mono so it can say "Look, we are open". Not much developers are going to switch from Java to .NET, so they hope that some switch from Java to Mono and later maybe to .NET. 

So I think that patent lawsuit is not going to be a problem, but that does not mean that patents itself are not going to be a problem. Microsoft can continue to offer patent protection from themselves to big Linux users (like mafia boss), and now has more FUD material because Mono infringes their patents. Yeah, there is that promise which is legally binding which can be used against Microsoft in court. But thing is that nobody wants to get sued. So they forget about fact that Linux has nothing to do with Microsoft and sign a deal that says that Microsoft owns something related to Linux. 

But that is not fault of Mono, it is somewhat fault of Novell. Mono is good for Linux because some ISVs who use .NET will have Mono to use when they decide to port their software to Linux. But I think that distros should avoid to depend free software on Mono anyway.

---

### Post by fewt on 2010-03-09
> **mickie.kext said:**
> .NET runs only on Windows, it is proprietary, and it has "vendor lock-in written all over it.

Uhh its an ECMA standard platform and there is a toolchain for Linux.  I have myself written code in Mono that I have executed later on Windows, so I know that it isn't proprietary.


> **mickie.kext said:**
> Java is open source, and also have few independent open source implementations (Apache Harmony, GNU Classpath and other), it runs _everywhere_... 

Uhh when it runs?  Java is OK, no doubt but it has been a painful transition from closed to open source.  It suffers all of the same fundamental problems Mono does except that it didn't start as a Microsoft project.

> **mickie.kext said:**
> So Microsoft needs Mono so it can say "Look, we are open". No developer is going to switch from Java to .NET, so they hope that some switch from Java to Mono and later maybe to .NET.

This is a nice opinion, but I know a lot of developers that switched from Java to .NET and are playing with Mono personally.

> **mickie.kext said:**
> material because Mono infringes their patents

Mono has Microsofts blessing to use those patents, it was required for the ECMA approval if I remember correctly.

---

### Post by doas777 on 2010-03-09
> **fewt said:**
> 
This is a nice opinion, but I know a lot of developers that switched from Java to .NET and are playing with Mono personally.


<raises hand>Yo!</raises hand>

C# is java with hindsight. same type of language, just better object model, and fewer annoyances (string.equals(), I'm looking at you. WTH would I want to compare 2 strings for a common reference?).

---

### Post by mickie.kext on 2010-03-09
> **doas777 said:**
> <raises hand>Yo!</raises hand>

C# is java with hindsight. same type of language, just better object model, and fewer annoyances (string.equals(), I'm looking at you. WTH would I want to compare 2 strings for a common reference?).

That was my point. If there was no Mono, none of that would matter. C# would be a clone of Java which works only on Windows. With Mono, it works everywhere and can compete with Java. That is why I said MS needs Mono.

---

### Post by howlingmadhowie on 2010-03-09
> **doas777 said:**
> <raises hand>Yo!</raises hand>

C# is java with hindsight. same type of language, just better object model, and fewer annoyances (string.equals(), I'm looking at you. WTH would I want to compare 2 strings for a common reference?).

the real problem with String in java is that it's marked final.

---

### Post by doas777 on 2010-03-09
> **mickie.kext said:**
> That was my point. If there was no Mono, none of that would matter. C# would be a clone of Java which works only on Windows. With Mono, it works everywhere and can compete with Java. That is why I said MS needs Mono.

but why should a language be tied to a platform at all? the compiler implementation itself may be platform based, but the langague itself shouldn't be. 

additionally I see it the other way around. now that we have mono, why do we need to keep java? we have C# code in the ubuntu-desktop package, but I don't think there is any java. may be wrong there, but I can't think of any util that requires it.

---

### Post by tuddy666 on 2010-03-09
It's not really something to worry about from a legal perspective anymore, to my knowledge.

Then again, because of the way that Open Source Software works, it isn't mandatory. It's easy enough to remove mono from Karmic if you're not too comfortable with using an open implementation of C#.

---

### Post by mickie.kext on 2010-03-09
> **doas777 said:**
> but why should a language be tied to a platform at all? the compiler implementation itself may be platform based, but the langague itself shouldn't be. 

I did not say it should be. I just said that Mono is not going anywhere (as in, not going to be sued into oblivion or otherwise undermined by Microsoft) because Microsoft needs it. 

> **doas777 said:**
> additionally I see it the other way around. now that we have mono, why do we need to keep java? we have C# code in the ubuntu-desktop package, but I don't think there is any java. may be wrong there, but I can't think of any util that requires it.
Wow. So you think that Java should be removed from repositories because Mono exists? I hope I misread that. Please explain.

---

### Post by Simian Man on 2010-03-09
> **mickie.kext said:**
> I did not say it should be. I just said that Mono is not going anywhere (as in, not going to be sued into oblivion or otherwise undermined by Microsoft) because Microsoft needs it.
I don't understand your point here.  It's good for C# that there are multiple implementations especially open source ones.  And it's indirectly good for Microsoft to have developer buy in to C#, but so what?  What are you arguing?

> **mickie.kext said:**
> Wow. So you think that Java should be removed from repositories because Mono exists? I hope I misread that. Please explain.

I don't think it should be removed, but I can't think of a single reason to use Java for something other than existing code.  C# is Java Unretardified.

---

### Post by mickie.kext on 2010-03-09
> **Simian Man said:**
> I don't understand your point here.  It's good for C# that there are multiple implementations especially open source ones.  And it's indirectly good for Microsoft to have developer buy in to C#, but so what?  What are you arguing?
That nobody should worry about lawsuits, off course.

---

### Post by fewt on 2010-03-09
> **mickie.kext said:**
> That nobody should worry about lawsuits, off course.

++

Nobody should worry about Mono / C# lawsuits, the sky isn't falling today.

---

### Post by Dragonbite on 2010-03-09
If Mono is an issue for people there are alternatives. If I am remembering right, Fedora does not include Mono in their default installation and use gNote instead of Tomboy.  Or you can look at most KDE-distros, since it seems KDE doesn't use Mono much.

So it is possible for people who are afraid of Mono to run a Linux that does not include Mono.  Thus, if anything legal were to come along just look at one of these distros because that is what Ubuntu would become if it is so necessary.

The only thing I can see detrimental with Mono, at this time, is if Novell is bought by somebody and moves the Mono developers so there is nobody paid to develop it.

Or maybe Microsoft will take over as a corporate sponsor and pay the developers to develop it?

---

### Post by doas777 on 2010-03-09
> **mickie.kext said:**
> I did not say it should be. I just said that Mono is not going anywhere (as in, not going to be sued into oblivion or otherwise undermined by Microsoft) because Microsoft needs it. 


Wow. So you think that Java should be removed from repositories because Mono exists? I hope I misread that. Please explain.

not at all. remember the summation on my first post on this thread?:
> I've said it before: i won't lobby to have *Your* runtime removed from ubuntu, if you will extend *me* the same courtesy.

I don't think java should be removed (I code in it as well if the client wants it). I'm saying that having java does not eliminate the need for C# nor does C# remove the need for java. I would say, if we had to keep  just one though, java would lose in my book.

---

### Post by svaens on 2010-03-09
So, the topics that are interesting to me are;

1. Is it conceivable that Microsoft could later change its tune, and decide it wants to make use of its 'so called' patient rights after all, and sue users of (or distributions using) mono into paying some sort of fee ? 

or has it so obviously (and convincingly legallly) given away that possibility with its "Community Promise" ?

2. Were it to try to make use of its patent (as number 1 here asks) who (as in, which company? (Canonical?) or organisation (FSF?)) would be big enough (resources enough) to be able to answer Microsoft in the courts? 

So, in other-words, does Microsoft have enough money to get away with a change in tune if it felt like it, regardless of the 'legal issues' as we see them now ?

Whether or not mono is a useful or improved language, is to me besides the point here. I did not start the thread to discuss its merits as a development tool, but to ask questions about its legal future.

---

### Post by doas777 on 2010-03-09
I'm pretty sure that any judge would rule that we had good reason to believe that we can use any implementation of the ECMA spec, based on the "community promise". it may not be legally binding in the way that the GPL is (which is stallmans gripe), but at the same time, they can't try to argue that they never authorizes us to use it. a simple web query would prove otherwise. IANAL, but it would cast their promise as bad-faith, and make them actionable, not us.

---

### Post by Dragonbite on 2010-03-09
Could Microsoft change its heart? Probably, regardless of whether it would be effective.

Who would they sue for infringement? That's a good question. 

I'm not legal expert, but I have a feeling they've given enough of it away as well as working WITH the Mono group that they don't have much of a leg to stand on.

Mono, though, is not vulnerable to the Novell IP protection agreement because iirc, Mono is not listed in the agreement.  This could be because Mono is a totally different beast and Microsoft CANNOT offer "protection" for it because they have no control over it.

Of course Microsoft could turn around and develop .NET in a direction that is more closed, without any disclosure and make sure it doesn't work with Mono.  Then the Mono project would be at a crossroad (try reverse-engineering the new .NET, continue and basically build its own separate language, etc.), but it isn't worth speculating on it unless that happens.

Who knows, maybe by the time Microsoft does anything, Oracle's Java will be improved and people start jumping the .NET ship for it?

Anything is possible.

(I agree, this has been an interesting, thoughtful and education thread so far)

---

### Post by graabein on 2010-03-09
I don't think Stallman's paranoid. You have to be willing to stick to the principles and fight for them and he does that admirably. 

I wish GNOME took the hard line vs Mono and didn't include any dependencies on default apps...

---

### Post by Ric_NYC on 2010-03-09
Yes! Mono is a lawsuit waiting to happen!

---

### Post by Queue29 on 2010-03-09
> **graabein said:**
> I don't think Stallman's paranoid. You have to be willing to stick to the principles and fight for them and he does that admirably. 

And how exactly is Mono defying Stallman's principles?

> 
I wish GNOME took the hard line vs Mono and didn't include any dependencies on default apps... 

Yes, because giving developers better tools to work with is such an evil thing to do.

---

### Post by Simian Man on 2010-03-09
> **mickie.kext said:**
> That nobody should worry about lawsuits, off course.
Ah.  I thought you were arguing that Mono wasn't safe for some reason.

> **Ric_NYC said:**
> Yes! Mono is a lawsuit waiting to happen!
And your reasoning?

---

### Post by Ric_NYC on 2010-03-09
> **Simian Man said:**
> .


And your reasoning?


**Microsoft and Novell provide patent coverage _[B]for [U][COLOR="Red"]each others customers[/COLOR]_, giving customers peace of mind regarding patent issues**[/U]. Finally, under a business cooperation agreement, Novell and Microsoft are committing to dedicate marketing and sales resources to promote joint solutions.[/B]


[http://www.novell.com/linux/microsoft/faq.html](http://www.novell.com/linux/microsoft/faq.html)



**Microsoft and Amazon.com have reached an agreement that gives each company a license to the other's patent portfolio, in a way that could revive one of the Redmond company's longest-running controversies. That's because, as part of the deal, [B]Microsoft says it's [COLOR="Red"]granting Amazon patent-related "coverage" for its use of open-source and proprietary technologies in its Kindle e-reader, and its use of Linux-based computer servers[/COLOR]**.[/B]

[http://www.techflash.com/seattle/2010/02/microsoft_amazon_in_patent_deal.html](http://www.techflash.com/seattle/2010/02/microsoft_amazon_in_patent_deal.html)

---

### Post by Dragonbite on 2010-03-09
> **Ric_NYC said:**
> **Microsoft and Novell provide patent coverage _[B]for [U][COLOR="Red"]each others customers[/COLOR]_, giving customers peace of mind regarding patent issues**[/U]. Finally, under a business cooperation agreement, Novell and Microsoft are committing to dedicate marketing and sales resources to promote joint solutions.[/B]


[http://www.novell.com/linux/microsoft/faq.html](http://www.novell.com/linux/microsoft/faq.html)


> You are covered if you are doing non-commercial open source software development. This includes individual enthusiasts, such as a student or a developer who does work on his own time on a project of personal interest to him. If you are compensated for your development, then your activities are considered "commercial", and you would not be covered.

So if you are afraid of the patents AND you are making money from it you should use SUSE.  Otherwise if you are like 99% of Linux users and are just the end users using Mono-built programs, you don't have to worry.

---

### Post by doas777 on 2010-03-10
> **Ric_NYC said:**
> **Microsoft and Novell provide patent coverage _[B]for [U][COLOR=Red]each others customers[/COLOR]_, giving customers peace of mind regarding patent issues**[/U]. Finally, under a business cooperation agreement, Novell and Microsoft are committing to dedicate marketing and sales resources to promote joint solutions.[/B]


[http://www.novell.com/linux/microsoft/faq.html](http://www.novell.com/linux/microsoft/faq.html)



**Microsoft and Amazon.com have reached an agreement that gives each company a license to the other's patent portfolio, in a way that could revive one of the Redmond company's longest-running controversies. That's because, as part of the deal, [B]Microsoft says it's [COLOR=Red]granting Amazon patent-related "coverage" for its use of open-source and proprietary technologies in its Kindle e-reader, and its use of Linux-based computer servers[/COLOR]**.[/B]

[http://www.techflash.com/seattle/2010/02/microsoft_amazon_in_patent_deal.html](http://www.techflash.com/seattle/2010/02/microsoft_amazon_in_patent_deal.html)

the cross patent licensing deal with novell has absolutly nothing to do with teh community promise license for C#/CLI done through the ECMA. Novell only worked on mono because de icaza is into it, and they had a working relationship.

remember, De Icaza is a co founder of the gnome project. do we need to fear gnome as well?

---

### Post by fewt on 2010-03-10
> **Ric_NYC said:**
> **Microsoft and Novell provide patent coverage _[B]for [U][COLOR="Red"]each others customers[/COLOR]_, giving customers peace of mind regarding patent issues**[/U]. Finally, under a business cooperation agreement, Novell and Microsoft are committing to dedicate marketing and sales resources to promote joint solutions.[/B]


[http://www.novell.com/linux/microsoft/faq.html](http://www.novell.com/linux/microsoft/faq.html)



**Microsoft and Amazon.com have reached an agreement that gives each company a license to the other's patent portfolio, in a way that could revive one of the Redmond company's longest-running controversies. That's because, as part of the deal, [B]Microsoft says it's [COLOR="Red"]granting Amazon patent-related "coverage" for its use of open-source and proprietary technologies in its Kindle e-reader, and its use of Linux-based computer servers[/COLOR]**.[/B]

[http://www.techflash.com/seattle/2010/02/microsoft_amazon_in_patent_deal.html](http://www.techflash.com/seattle/2010/02/microsoft_amazon_in_patent_deal.html)

You really shouldn't take unrelated patent deals and try to shoe horn them to fit a discussion about Mono.  You just make the case that you don't really understand what you are arguing against when you do that. ;)

I suppose in the case of the Novell agreement it does make a statement about Mono:

"Q. What does the patent agreement cover with regard to Mono and OpenOffice?

Under the patent agreement, customers will receive coverage for Mono, Samba, and OpenOffice.org as well as .NET and Windows Server."

Lets cover that one though real quick:

"Q8. What does this mean for Mono and its inclusion in non-SUSE distributions? Does Mono infringe Microsoft patents?

We maintain that Mono does not infringe any Microsoft patents. This agreement does not impact the rights and abilities of other distributions to bundle and ship Mono."

[http://www.novell.com/linux/microsoft/faq_opensource.html](http://www.novell.com/linux/microsoft/faq_opensource.html)

---

### Post by svaens on 2010-03-10
That document is a very interesting document ([http://www.novell.com/linux/microsoft/faq_opensource.html]("http://www.novell.com/linux/microsoft/faq_opensource.html")).
One that I think should be made more available in all this noise against Novell. I certainly wish i'd read it before.

This assertion: "We maintain that Mono does not infringe any Microsoft patents." can't really remove the fears of future patient problems, because this is novells assertion. Not Microsoft. And until Microsoft assert that Mono does not infringe, then it is all still a bit in the air, isn't it?

However, the above document does clear many things up for me, regarding Novells position on any possible patient infringements. 

Particularly of interest are;

> Q2. Why did Novell make this deal with Microsoft? Was Microsoft threatening a lawsuit?

There was no threatened litigation.

Q3. Is this agreement an admission that Linux products from Novell infringe Microsoft patents?

No.

Patent concerns did not drive our entry into this agreement. Novell makes no admission that its Linux and open source offerings infringe on any other parties' patents. Our position has not changed as a result of this agreement.

You can't get much more clear than that.

---

### Post by doas777 on 2010-03-10
why are we talking about the novell cross licensing deal? this is the item in question:
[http://tirania.org/blog/archive/2009/Jul-06.html](http://tirania.org/blog/archive/2009/Jul-06.html)


> 
**It is important to note that, under the Community Promise, 	anyone can freely implement these specifications with their 	technology, code, and solutions.  	**
**You do not need to sign a license agreement, or otherwise 	communicate to Microsoft how you will implement the 	specifications.  	**
**The Promise applies to developers, distributors, and users of 	Covered Implementations without regard to the development 	model that created the implementations, the type of copyright 	licenses under which it is distributed, or the associated 	business model.  	**
**Under the Community Promise, Microsoft provides assurance that 	it will not assert its Necessary Claims against anyone who 	makes, uses, sells, offers for sale, imports, or distributes 	any Covered Implementation under any type of development or 	distribution model, including open-source licensing models 	such as the LGPL or GPL.**  	
You can find the terms of the Microsoft Community Promise 	[here]("http://www.microsoft.com/interop/cp/default.mspx").  	


and here are ECMA #334/335
[http://www.ecma-international.org/publications/standards/Ecma-334.htm](http://www.ecma-international.org/publications/standards/Ecma-334.htm)
[http://www.ecma-international.org/publications/standards/Ecma-335.htm](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

---

### Post by svaens on 2010-03-10
Yes, I agree. This looks pretty convincing.

---

### Post by pops-saito on 2010-03-27
Microsoft will go to great expense to crush their competition.  Based on Microsoft's history why would you trust them at all?

Ballmer said, “Linux is a cancer.”
 
Ballmer said, "Linux infringes our intellectual property."

If Microsoft will stop targeting Linux for destruction then it might make sense to include their intellectual property.  Ad kalendas graecas (will never happen).

So, please remove the Mono Gnome dependencies.  If you need Mono, nothing is preventing you from installing it.

Also, if you are being compensated by Microsoft, in some way or another, and arguing for Microsoft's position, then I feel sorry for you.  And hope that someday you regain your honor.

---

### Post by gnomeuser on 2010-03-28
Since people like to use year old statements by certain people within Microsoft to put words into their mouths about their current stanceon Open Source, here is Microsoft officially [stating how Open Source is part of their business plan](http://www.networkworld.com/community/node/59203).

They are in this to make money and Open Source is one way to do so, combatting it is simply not a good business model which is why they jumped on the bandwagon long ago.

---

### Post by Dragonbite on 2010-03-28
> **gnomeuser said:**
> They are in this to make money and Open Source is one way to do so, combatting it is simply not a good business model which is why they jumped on the bandwagon long ago.

Isn't this the same with Oracle, Novell, Red Hat, IBM, HP, and many, many more companies; open source is one way to make money.

Are they a business not allowed to act like a business?

---

### Post by swoll1980 on 2010-03-28
Why are we still talking about mono? This was last years stupid story of the the day, and here I am still seeing it. Mono is fine. It's no more illegal than taking a breath of fresh air. Can we leave it alone already?

---

### Post by Dragonbite on 2010-03-29
> **swoll1980 said:**
> Why are we still talking about mono? This was last years stupid story of the the day, and here I am still seeing it. Mono is fine. It's no more illegal than taking a breath of fresh air. Can we leave it alone already?

It's resurfacing because in an interview with Miquel, and that people jumped on the conspiracy band-wagon when they could not find the article.  You can read his response to all of this in his [_blog_]("http://tirania.org/blog/archive/2010/Mar-25.html").> There are certain areas that I do not quite like about .NET, they are not major issues as they can be either worked around or ignored (to some extent), but here are some. OMG! Like it isn't perfect? I wonder if the people that complain about it actually do any programming?> The most important part is that Microsoft has shot the .NET ecosystem in the foot because of the constant thread of patent infringement that they have cast on the ecosystem. Unlike the Java world that is blossoming with dozens of vibrant Java virtual machine implementations, the .NET world has suffered by this meme spread by Ballmer that they would come after people that do not license patents from them. Yeah, Microsoft missed a great opportunity with .NET and now they have to rely on Mono to counter Java's cross-platform-ism. Hey, guess what? Hindsight is 20/20, but it is still Hindsight!  Yet that was then, and this is now.> Had Microsoft been an open company in 2001 and had embraced diversity we would live in a different world. The awesome Mono team would probably be bigger, and the existing team members would have longer vacations.

But for everyone that missed the point, luckily, Microsoft has new management, new employees that know open source, fresh new ideas, is becoming more open and is working actively on interoperability with third parties. They even launched the CodePlex Foundation. 

So it seems people are blowing every little bit of the interview way out of proportion just to attack anything associated with Microsoft.

---

### Post by graabein on 2010-03-30
People still talk about the whole good versus evil and that freedom and democracy thing. And I do programming as a living. Read any history?

---

### Post by zekopeko on 2010-03-30
> **graabein said:**
> People still talk about the whole good versus evil and that freedom and democracy thing. And I do programming as a living. Read any history?

And your point is...?

---

### Post by swoll1980 on 2010-03-30
:popcorn:

---

### Post by oscalation on 2010-10-06
Microsofts track record for supporting FOSS should be warning enough.
Patent infringement has no statue of limitations, pre patent law.. etc etc

The mass discussion, valid or invalid, show concern from many communities raises yet another flag for concern 


the concern with Mono boils down to legalities, anyone familure with the legal system understands the complexity of such issues, and that a clear and easy to understand outcome is unreasonable. With that said, there have been notable bloggers, FOSS organizations with legal support  make arguments that to me show the risks outweigh the benefits. 

What is Novell's and Microsoft's plans with Mono?
Why is Microsoft pushing integration within the open source realm so hard? 

[http://www.webnotwar.ca/](http://www.webnotwar.ca/)
[http://www.codeplex.com/](http://www.codeplex.com/)
[http://www.microsoft.com/opensource/project-detail.aspx?pid=18](http://www.microsoft.com/opensource/project-detail.aspx?pid=18)
so on and so forth..

---

### Post by directhex on 2010-10-06
> **bigthinker said:**
> Why is Microsoft pushing integration within the open source realm so hard? 

Because it's 2010, they're losing mindshare fast, and they cannot be a profitable business whilst pretending Free Software doesn't exist. They need to adapt or die.

---

### Post by Dragonbite on 2010-10-06
Because Mono brings .NET to corners of the world Microsoft could not really do by themselves (iPhone, Linux, OS X, etc.).

---

### Post by Dragonbite on 2010-10-06
> **bigthinker said:**
> What is Novell's and Microsoft's plans with Mono?
Why is Microsoft pushing integration within the open source realm so hard? 

[http://www.webnotwar.ca/](http://www.webnotwar.ca/)
[http://www.codeplex.com/](http://www.codeplex.com/)
[http://www.microsoft.com/opensource/project-detail.aspx?pid=18](http://www.microsoft.com/opensource/project-detail.aspx?pid=18)
so on and so forth..

So, is there a purpose of these links other than to show that Microsoft is getting into Open Source.  Are they "damned because they don't and damned because they do?"

Microsoft has no "plans" with Novell regarding Mono, their deal is over iirc, and Mono wasn't even part of it.

What's the conspiracy theory about Sun open sourcing Java?  What's their plan?  And now it is in the hands of Oracle who is even more shady than Microsoft these days?!

---

