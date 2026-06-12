---
title: "Clarification on the Mono and MS .NET issue"
date: 2008-04-02
forum: Recurring Discussions
---

### Post by randomstuff on 2008-04-02
Since there seems to be a lot of confusion on the issue of mono and .NET I want to make things a bit clearer:

1) Microsoft created a standard called .NET. This standard describes how a .NET implementation should work and is available to anyone. Anyone may use these standards documents to create a piece of software based on this standard. This does not make the software proprietary or controlled by MS.

2) Microsoft created their own implementation of this standard called the .NET framework. This piece of software is proprietary and not open in any way.

3) Novel also created their own implementation of this standard which they call mono. This piece of software is not proprietary but is completely open. There are no patent issues or any other problems because it is developed from scratch and is not based on Microsofts own .NET implementation. 

Because mono is based on the .NET standard it works almost the same as Microsofts own implementation and is very, but not completely, compatible. Since the standard itself (the documents, not the software) can be used by anyone and is open itself, this does not make mono proprietary in any way.

You can compare mono with wine. Wine is free and open source software not tied to Microsoft in any way but it allows you to run windows programs. Mono is similar, only it covers .NET programs instead of windows programs.

I have tried to explain this in terms that non-developers will also understand, so please forgive me if I am using slightly inaccurate terms.



Edit: If you really need citations, here is a [clarification]("http://lists.ximian.com/archives/public/mono-list/2004-March/019042.html") from Miguel de Icaza, the man behind mono.

> [B]There is nothing in Java that makes it any safer than Mono at this
point[/B].  We do not have any guarantees, any written statements, any
guarantees that Java on Linux will not be sued under certain
conditions.

[B]Microsoft has granted RAND+Royalty Free licenses to any patents they
might own that are required to implement the ECMA 334/335 standards. [/B]
So at least our core VM, classes and compilers are safe from any
litigation from *Microsoft*.

AFAIK the patents he is talking about are granted to anyone implementing said ECMA standards, this means that the ECMA compliant parts of mono - which are fully functional on their own - are absolutely free of patent issues (from MS at least).

also, a quote from [wikipedia]("http://en.wikipedia.org/wiki/Mono_%28software%29#Mono_and_Microsoft.E2.80.99s_patents"):

> The base technologies submitted to the ECMA, and therefore also the Unix/Gnome-specific parts, may be non-problematic. **The concerns primarily relate to technologies developed by Microsoft on top of the .NET Framework**, such as ASP.NET, ADO.NET and Windows Forms, i.e. parts composing Mono&#8217;s Windows compatibility stack. These technologies are today not fully implemented in Mono and **not required for developing Mono-applications**.



To the moderators: I know that this is a recurring discussion, so feel free to move it to that board. I just want to make sure that there is a topic readily available and properly named so that anyone in doubt can quickly find out the truth about mono. I apologize in advance if this creates additional work for you, but I felt it was necessary because there is so much misinformation going around.


-

---

### Post by LaRoza on 2008-04-02
It would be nice if you were able to link to hard information, otherwise, it is just an opinion (even if it were true)

It will be moved probably.

You forgot to mention that a large part of the API is not part of the standard. Microsoft plays with it you know. They submit some of the information, but keep parts for themselves.

---

### Post by klange on 2008-04-02
All very good points, which is why I feel no shame in having MonoDevelop installed, but the version in Ubuntu is extremely outdated and lacks all the amazing improvements that have been added recently. It definitely needs to be bumped to 1.0. I'll also add that installing from source does not work due some weird things with the packages in Ubuntu, and that even if it did, the Mono installations are notorious for screwing with a lot of libraries.

---

### Post by randomstuff on 2008-04-02
> **LaRoza said:**
> It would be nice if you were able to link to hard information, otherwise, it is just an opinion (even if it were true)

I've added some links from a quick search on google. You should note, however, that it is other people spreading false information about mono that should cite sources. It is comparable to accusing someone (wrongly) of committing murder and then asking him to cite sources that say it did not happen. Pretty difficult (or at least it can be).

> **LaRoza said:**
> You forgot to mention that a large part of the API is not part of the standard. Microsoft plays with it you know. They submit some of the information, but keep parts for themselves.

No, I left it out because it is not relevant. It matters not how much MS develops on top of the .NET standard, because the intention behind mono is to stick to the standard. Adding compatibility with MS is a bonus, but not an essential feature. The default installation of mono only comes with the standard compliant part of mono AFAIK, and this part is completely free of legal issues as much as any piece of software is nowadays.

The compatibility layer might have more legal issues, but they are not important because they are not required for a working mono installation. So everyone is fine as long as ubuntu sticks to the standard compliant part of mono.

---

### Post by LaRoza on 2008-04-02
> **randomstuff said:**
> I've added some links from a quick search on google. You should note, however, that it is other people spreading false information about mono that should cite sources. It is comparable to accusing someone (wrongly) of committing murder and then asking him to cite sources that say it did not happen. Pretty difficult (or at least it can be).


I know, I wanted your statements to be less prone to flames :-)

---

### Post by geoken on 2008-04-02
> **randomstuff said:**
> 

AFAIK the patents he is talking about are granted to anyone implementing said ECMA standards, this means that the ECMA compliant parts of mono - which are fully functional on their own - are absolutely free of patent issues (from MS at least).


-

The patents permissions are granted under the RAND liscense. This means that at any time Microsoft can demand 'reasonable and non discriminatory' fees for the use of said patents. 

Read up on RAND here ( [http://en.wikipedia.org/wiki/Reasonable_and_Non_Discriminatory_Licensing]("http://en.wikipedia.org/wiki/Reasonable_and_Non_Discriminatory_Licensing"))

Here is a quote taken from the wikipedia entry "As the word "reasonable" is absolutely free in interpretation, standards of the RAND type can be used to keep small and mid-sized businesses away from the market. This can easily lead to oligopolies, where few big enterprises share the markets. Customers then have to pay inflated prices and technological and economical progress is decelerated."

---

### Post by Dekkon on 2008-04-02
Holy crap, I didn't know Microsoft actually made a standard. 

Thanks for this, I was completely wrong, I thought Mono was created by Microsoft with legal stuff tied in and it was made with novel and stuff like that.

---

### Post by saulgoode on 2008-04-02
> **randomstuff said:**
> Edit: If you really need citations, here is a [clarification]("http://lists.ximian.com/archives/public/mono-list/2004-March/019042.html") from Miguel de Icaza, the man behind mono.

[QUOTE="Miguel de Icaza"]There is nothing in Java that makes it any safer than Mono at this
point. We do not have any guarantees, any written statements, any
guarantees that Java on Linux will not be sued under certain
conditions.[/quote]

Since that claim was made back in 2004, [Sun has released much of Java under the GPL](http://www.sun.com/2006-1113/feature/story.jsp); and committed to releasing more components once they resolve copyright issues with third parties. Note that their release under GPL includes patent indemnity direct from them, the patent holders -- for all users, distributors, and developers (even if they don't obtain their code from Sun). 

Resistance against Java has historically run high within the Free Software community, and even still there is understandable reluctance for widespread adoption until Sun completes their expressed goal. Though I am not a fan of Java, Mr Icaza's statement is now outdated and, even if still true, does not suggest that Mono should be welcomed within the Free Software community.

> **randomstuff said:**
> [QUOTE="Miguel de Icaza"]Microsoft has granted RAND+Royalty Free licenses to any patents they
might own that are required to implement the ECMA 334/335 standards.
So at least our core VM, classes and compilers are safe from any
litigation from *Microsoft*.[/quote]
I would actually like to peruse where Microsoft makes this pledge. If the wording is anything like that of their [most recent patent pledge](http://www.microsoft.com/interop/principles/osspatentpledge.mspx) then it would not provide indemnity for the customers of any commercial enterprises (except for those companies which might have negotiated some sort of patent "covenant" on the side). 

And does the current bundling of Mono and its apps restrict itself to the ECMA base. It seems to me from the Mono FAQ that Mono already includes some non-ECMA components:
[QUOTE="[http://www.mono-project.com/FAQ:_Licensing](http://www.mono-project.com/FAQ:_Licensing)"]...Mono's strategy for dealing with any potential issues that might arise with ASP.NET, ADO.NET or Windows.Forms is: (1) work around the patent by using a different implementation technique that retains the API, but changes the mechanism; if that is not possible, we would (2) remove the pieces of code that were covered by those patents, and also (3) find prior art that would render the patent useless.[/QUOTE]

And if one suspects that Microsoft does not care whether Mono includes such "non-standard" niceties, reading [this Microsoft  developer's take](http://blogs.msdn.com/joestagner/archive/2004/11/02/251125.aspx) should leave little doubt that this is not the case. Note how his recommendation, made before the MS/Novell agreement, was that Novell needed to license those components from Microsoft. Is not that what happened in November of 2006? Is any other distribution covered by the Novell Mono patent covenant? NO.

---

### Post by LaRoza on 2008-04-02
> **Dekkon said:**
> Holy crap, I didn't know Microsoft actually made a standard. 

Thanks for this, I was completely wrong, I thought Mono was created by Microsoft with legal stuff tied in and it was made with novel and stuff like that.

They didn't make it, ECMA did.

---

### Post by smartboyathome on 2008-04-03
Mono should not be removed from Ubuntu if it only contains the ECMA portions. As said above, the non-ECMA portions aren't required.

---

### Post by saulgoode on 2008-04-03
> **smartboyathome said:**
> Mono should not be removed from Ubuntu if it only contains the ECMA portions. As said above, the non-ECMA portions aren't required.

According to [the Mono Project](http://www.mono-project.com/Roadmap), Mono already includes ADO.NET and ASP.NET; and development versions include Windows.Forms (is this an implementation of WinForms.NET?). Are these components being stripped out of the Ubuntu version of Mono? Are they not implementations of technologies that might read on Microsoft patent claims?

---

### Post by randomstuff on 2008-04-03
I want this topic to be completely objective, so I hope to update the original post later today with new citations and information from the above posts, but I have just gotten home from work and need to rest a bit.

---

### Post by smartboyathome on 2008-04-03
> **saulgoode said:**
> According to [the Mono Project](http://www.mono-project.com/Roadmap), Mono already includes ADO.NET and ASP.NET; and development versions include Windows.Forms (is this an implementation of WinForms.NET?). Are these components being stripped out of the Ubuntu version of Mono? Are they not implementations of technologies that might read on Microsoft patent claims?

They aren't implimented in Ubuntu, from what I understand. If they were, it wouldn't be able to be advertised as "completely free".

---

### Post by saulgoode on 2008-04-03
> **smartboyathome said:**
> They aren't implimented in Ubuntu, from what I understand. If they were, it wouldn't be able to be advertised as "completely free".

I have to disagree. Unless a distribution or an upstream provider has actually been successfully sued over a particular patent claim, they are well within their rights to choose whether or not to distribute that software based on their own interpretations of applicable law. Advertising slogans aside, there is always some level of risk of submarine patents surfacing and the best that can be hoped for is to not have that risk reach unacceptably high levels.

In the case of Mono, no distribution has yet been sued over patents, nor has the upstream provider; however, the provider of the package HAS negotiated a patent licensing deal which covers all of the patents in question, but this available only to themselves. While the fact that the developers of Mono sought patent coverage for their project does not *prove* that the patents are applicable, it does bring into serious question those patents' viability and presents a much higher level of risk to *other* distributors of their product.

If the Ubuntu packagers can assure that there are no implementations of non-ECMA/ISO covered .NET technologies in the Ubuntu Mono package, I would agree that the level of risk is greatly diminished. However, I don't accept the circular logic of "it's safe to include because it wouldn't be included if it weren't safe" -- and I don't accept Novell's assertion that it's safe for everyone after they took extreme and unprecedented measures to carve out a safe haven for themselves.

---

### Post by bruce89 on 2008-04-04
> **smartboyathome said:**
> They aren't implimented in Ubuntu, from what I understand. If they were, it wouldn't be able to be advertised as "completely free".

Ubuntu don't implement stuff.

Anyway, there is a package called libmono-winforms2.0-cil, but it's not used by anything apart from MonoDevelop and IronPython.

---

### Post by vexorian on 2008-04-04
> 1) Microsoft created a standard called .NET. This standard describes how a .NET implementation should work and is available to anyone. Anyone may use these standards documents to create a piece of software based on this standard. This does not make the software proprietary or controlled by MS.

The 'standard' does not cover the entire .net, parts implemented by MONO are not covered. (windows.forms?)


> 2) Microsoft created their own implementation of this standard called the .NET framework. This piece of software is proprietary and not open in any way.


3) Novel also created their own implementation of this standard which they call mono. This piece of software is not proprietary but is completely open.

If by completely open you mean, "subject to a patent deal to MS, Novell reserves the right to relicense all code contributed to MONO completely", you are right.

> 
There are no patent issues or any other problems because it is developed from scratch and is not based on Microsofts own .NET implementation.


And that was true until MS and Novell made a deal so MS can help MONO devs.

> There is nothing in Java that makes it any safer than Mono at this
point.Except that you can actually use Sun's OS implementation of Java. And it will be GPLed. Of course, it is not much better than MONO hence the reason we wouldn't want gnome growing a Java dependency either.


> Microsoft has granted RAND+Royalty Free licenses to any patents they
might own that are required to implement the ECMA 334/335 standards.
So at least our core VM, classes and compilers are safe from any
litigation from *Microsoft*.

Like I mentioned ECMA 334/335 don't cover all .net, hence Miguel's "at least"

The moonlight debacle should be enough to prove there are reasons to worry about MONO's so called openness and Novell: [http://boycottnovell.com/2007/09/10/moonlight-only-novell/](http://boycottnovell.com/2007/09/10/moonlight-only-novell/) (Short story: in order to use so called "open source" Moonlight you need to either pay for SLED or download it directly from Novell (Just like any proprietary market drug))




> You can compare mono with wine
Exactly the reason I want MONO away of ubuntu's default install.

>  it allows you to run windows programs. Mono is similar

Unless we remember most relevant .net apps use windows.forms, which as we know is not legal.

That's the problem with .net , it is barely **optionally-open**, MS has already exploited the system to bring us more optionally open standards, like OOXML (Guess what the double OO it really stands for), I shall warn that they will push even more for these lame things.

--
There are no patent issues at all with MONO, I guess this is the reason MS requires SLED users to give them among other things, a  fee for... using MONO.


--
Let's assume MONO was not a mine field for FLOSS, is it actually acceptable? MONO is forcing, gnome, for example to become windows-like, forcing silly windows things like .exe and .dll to all of us (and that's just the exterior) It looks to me that Novell is using Linux as a kernel that will be the base platform for their entirely MONO based OS that will most likely be just another windows clone at least that seems to be the long term plan.


--
Actually, regarding all the attempts to make Sun's products look the same as MS' attempts to lock everybody into them, I must say:

The day Microsoft releases office and .net using GPLv2 or higher (and no silly attempts to bypass it) I will begin to promote their "open" standards.

---

### Post by pshah.mumbai on 2008-04-04
> Microsoft has granted RAND+Royalty Free licenses to any patents they might own that are required to implement the ECMA 334/335 standards. So at least our core VM, classes and compilers are safe from any litigation from *Microsoft*.

And where does Microsoft publicly state that it has given Royalty Free licenses ??

I see only Miguel de Icaza telling us fairy tales about this issue.

There is no such statement from Microsoft to back it up till date.

:guitar:

---

### Post by saulgoode on 2008-04-04
> **vexorian said:**
> If by completely open you mean, "subject to a patent deal to MS, Novell reserves the right to relicense all code contributed to MONO completely", you are right.

This raises another question I have. If I recall correctly, about a year ago one could contribute to the Mono codebase by *either* releasing one's code under a MIT license *or* signing over one's copyrights to Novell. According to the Mono FAQ, releasing under a MIT license seems to have been removed as an option:

[From the Mono FAQ:](http://www.mono-project.com/FAQ:_Licensing)> **Why does Novell require a copyright assignment?**

When a developer contributes code to the C# compiler or the Mono runtime engine, we require that the author grants Novell the right to relicense his/her contribution under other licensing terms.

This allows Novell to re-distribute the Mono source code to parties that might not want to use the GPL or LGPL versions of the code.

Particularly embedded system vendors obtain grants to the Mono runtime engine and modify it for their own purposes without having to release those changes back. 

I am not sure if the policy has changed (or perhaps my recollection is in error), but as seems typical of responses from the Mono project, they don't really answer directly the question being asked. In this case, a MIT license would permit Novell to re-license the code for proprietary use; so there doesn't need to be a requirement for a re-assignment of copyright (which is what the question asked).

Clarification on this would be welcome.

---

### Post by anantshri on 2008-04-04
few things to be added in this from my side,

mono completely supports 1.1 framework based apps,

but a slightly edgy support for 2.0 apps.

also AJAX framework by M$ is not supported,

---

### Post by bruce89 on 2008-04-04
> **vexorian said:**
> The 'standard' does not cover the entire .net, parts implemented by MONO are not covered. (windows.forms?)

I'm afraid spelling it in capitals reveals your lack of understanding on the subject.

---

### Post by vexorian on 2008-04-04
> I'm afraid spelling it in capitals reveals your lack of understanding on the subject.

I am afraid what you mentioned is completely irrelevant and does not change the factual accuracy of the rest of my post, which is well founded by Novell's and "mono"'s own FAQs, except the moonlight stuff which comes entirely from public statements by Miguel Icaza and Novell.

I don't like to spell it "mono" because I speak Spanish and that translates to monkey, confuses my brain, sorry.

---

### Post by reverseblade on 2008-04-05
> **anantshri said:**
> few things to be added in this from my side,

mono completely supports 1.1 framework based apps,

but a slightly edgy support for 2.0 apps.

also AJAX framework by M$ is not supported,



This is completely wrong. ASP.NET AJAX and AJAX Control Toolkit and even ASP.NET Futures are fully supported

---

### Post by anantshri on 2008-04-12
> **reverseblade said:**
> This is completely wrong. ASP.NET AJAX and AJAX Control Toolkit and even ASP.NET Futures are fully supported

Well buddy, that was my inference after trying to get the heck in on a asp.net + ajax based application, and searching and researching on net as well as mono's official documentation that confirmed M$ AJAX / ATLAS support is not official their,


also ASP.net 2.0 application did caused a lot of error's on my test server.


so if you state that it is supported then please list some resources for me to check where i went wrong with configuration.

---

### Post by smartboyathome on 2008-04-12
> **anantshri said:**
> Well buddy, that was my inference after trying to get the heck in on a asp.net + ajax based application, and searching and researching on net as well as mono's official documentation that confirmed M$ AJAX / ATLAS support is not official their,


also ASP.net 2.0 application did caused a lot of error's on my test server.


so if you state that it is supported then please list some resources for me to check where i went wrong with configuration.

Did you do it on a vanilla Ubuntu? By default, it doesn't include all the windows files needed to run some of those apps. It includes the patent free libraries only.

---

### Post by anantshri on 2008-04-30
well i installed all what i can get from the  reposatories and then went straight to mono project side, and even compiled back from sources all the work.

but all in viens.


windows.form is supported at desktop.

but the problem is in the ajax extension on asp.net stuff.

that's where the problem is.

and i then checked all the wiki and other stuff i can , and all pointed only one thing, m$ ajax (atlas) is not yet supported.

---

### Post by sakabato on 2008-05-04
> **anantshri said:**
> well i installed all what i can get from the  reposatories and then went straight to mono project side, and even compiled back from sources all the work.

but all in viens.


windows.form is supported at desktop.

but the problem is in the ajax extension on asp.net stuff.

that's where the problem is.

and i then checked all the wiki and other stuff i can , and all pointed only one thing, m$ ajax (atlas) is not yet supported.

This is Mono's lead asp.net developer. He shows asp.net control toolkit works in his video. Note that it's months old. For wiki it's old

[http://grendello.blogspot.com/2007/09/ajax-control-toolkit-broken-samples.html](http://grendello.blogspot.com/2007/09/ajax-control-toolkit-broken-samples.html)

---

### Post by anantshri on 2008-05-09
thanks for pointing me to the link,

I will try to do the same again ata  different place hope it work's this time.

what's your suggestion should i go with vanilla pack or i go with ubuntu repo.

also please check the reason for the latest comment on the blog dated in late march and only says one thing which i was speaking of from the start.

I will put the screenshots with error as soon as i get time to reproduce it.

---

### Post by sakabato on 2008-05-11
> **anantshri said:**
> thanks for pointing me to the link,

I will try to do the same again ata  different place hope it work's this time.

what's your suggestion should i go with vanilla pack or i go with ubuntu repo.

also please check the reason for the latest comment on the blog dated in late march and only says one thing which i was speaking of from the start.

I will put the screenshots with error as soon as i get time to reproduce it.

Hi. For packaging my suggestion would be to use debian etch backports which are 1.9.1 level and works with ubuntu too.

Here's the repo:

deb [http://debian.meebey.net/etch-backports](http://debian.meebey.net/etch-backports) /

I personally tested the samples on november 2007 on mono/ubuntu with 1.2.6. And it was working at that time. If you need any help just write it to here

---

### Post by alternatealias on 2008-06-07
> **saulgoode said:**
> According to [the Mono Project](http://www.mono-project.com/Roadmap), Mono already includes ADO.NET and ASP.NET; and development versions include Windows.Forms (is this an implementation of WinForms.NET?). Are these components being stripped out of the Ubuntu version of Mono? Are they not implementations of technologies that might read on Microsoft patent claims?

yes, but they are not part of the core mono package - they are addons.

---

### Post by alternatealias on 2008-06-07
> **saulgoode said:**
> I would actually like to peruse where Microsoft makes this pledge. If the wording is anything like that of their [most recent patent pledge](http://www.microsoft.com/interop/principles/osspatentpledge.mspx) then it would not provide indemnity for the customers of any commercial enterprises (except for those companies which might have negotiated some sort of patent "covenant" on the side).


According to wikipedia, the ECMA portions of the .NET framework are available under RAND-Z (Reasonable And Non-Discriminatory; Zero-cost) terms.

This is also pretty well common knowledge at this point.

> **saulgoode said:**
> 
And does the current bundling of Mono and its apps restrict itself to the ECMA base. It seems to me from the Mono FAQ that Mono already includes some non-ECMA components:

While Mono *does* implement non-ECMA portions of the .NET framework, the core Mono framework is not tied to them in any way.

> **saulgoode said:**
> And if one suspects that Microsoft does not care whether Mono includes such "non-standard" niceties, reading [this Microsoft  developer's take](http://blogs.msdn.com/joestagner/archive/2004/11/02/251125.aspx) should leave little doubt that this is not the case. Note how his recommendation, made before the MS/Novell agreement, was that Novell needed to license those components from Microsoft. Is not that what happened in November of 2006? Is any other distribution covered by the Novell Mono patent covenant? NO.

"Those components" (referring to ASP.NET, ADO.NET and Windows.Forms) being the key phrase :)

Microsoft have never claimed that the core EMCA portions of Mono needed to be licensed.

---

### Post by alternatealias on 2008-06-07
> **vexorian said:**
> The 'standard' does not cover the entire .net, parts implemented by MONO are not covered. (windows.forms?)

That does not taint the whole of Mono, just the non-ECMA portions.

> **vexorian said:**
> If by completely open you mean, "subject to a patent deal to MS, Novell reserves the right to relicense all code contributed to MONO completely", you are right.

Same as Sun with Java and OpenOffice and a plethora of other projects (unrelated to Sun or Novell).

> **vexorian said:**
> And that was true until MS and Novell made a deal so MS can help MONO devs.

Wow, you really like to FUD, don't you?

This is completely irrelevant.

> **vexorian said:**
> Except that you can actually use Sun's OS implementation of Java. And it will be GPLed. Of course, it is not much better than MONO hence the reason we wouldn't want gnome growing a Java dependency either.

Like I mentioned ECMA 334/335 don't cover all .net, hence Miguel's "at least"

But it *does* cover all the important parts that any Linux-based .NET application might use.

No one is writing desktop Linux applications using ASP.NET, ADO.NET or Windows.Forms (which are the only parts not covered by the ECMA RAND-Z promise)

> **vexorian said:**
> The moonlight debacle should be enough to prove there are reasons to worry about MONO's so called openness and Novell: [http://boycottnovell.com/2007/09/10/moonlight-only-novell/](http://boycottnovell.com/2007/09/10/moonlight-only-novell/) (Short story: in order to use so called "open source" Moonlight you need to either pay for SLED or download it directly from Novell (Just like any proprietary market drug))

Same with Ubuntu's Netbooks - Ubuntu is licensing proprietary codecs (including Windows Media). Like Moonlight, you have to get Netbooks directly from Ubuntu.

> **vexorian said:**
> Exactly the reason I want MONO away of ubuntu's default install.

No, you want Mono removed from Ubuntu because you are in league with the BoycottNovell news site whom are on a crusade to destroy anything Novell-related.

You guys also frequently lie about many things in order to confuse the issue (just look at all your ranting above for proof of this).

> **vexorian said:**
> Unless we remember most relevant .net apps use windows.forms, which as we know is not legal.

There you go spreading false information again.

None of the Linux Mono applications use Windows.Forms, therefor none of the "relevant" applications use Windows.Forms. Certainly none that Ubuntu ships.

> **vexorian said:**
> That's the problem with .net , it is barely **optionally-open**, MS has already exploited the system to bring us more optionally open standards, like OOXML (Guess what the double OO it really stands for), I shall warn that they will push even more for these lame things.

I fail to see how OOXML is in any way related to this discussion. Just like Roy Schestowitz, whenever any of you hypocrites gets flustered you fall back to complaining about OOXML in order to rile people up as if it were somehow relevant.

It's not.

---

### Post by klange on 2008-06-07
The Mono package installed by default in Ubuntu - and the only one available in the repos - does not have the non-standards parts of Mono. That's why we get stuck at such an old version. There is absolutely nothing wrong with Mono just as there's nothing wrong with Wine.

(btw, there's a PPA on Launchpad called "mono-edge" that contains the newest Mono packages, with all the Windows.Forms and other things.)

---

### Post by saulgoode on 2008-06-07
> **alternatealias said:**
> [QUOTE="vexorian"]Except that you can actually use Sun's OS implementation of Java. And it will be GPLed. Of course, it is not much better than MONO hence the reason we wouldn't want gnome growing a Java dependency either.

Like I mentioned ECMA 334/335 don't cover all .net, hence Miguel's "at least"

But it *does* cover all the important parts that any Linux-based .NET application might use.

No one is writing desktop Linux applications using ASP.NET, ADO.NET or Windows.Forms (which are the only parts not covered by the ECMA RAND-Z promise)[/quote]

I don't see Mono (ECMA 334/335) mentioned [as being covered](http://www.microsoft.com/interop/osp/default.mspx). Where exactly might one find this "ECMA RAND-Z promise" of which you speak?

The Mono Licensing FAQ page states (with regard to the ECMA 334/335-covered components) that "**Basically a grant is given to anyone who want to implement those components for free and for any purpose.**"

No such grant has ever been made. Nothing exists on the web which suggests that such a grant has ever been made. 

The only thing that's changed since the ECMA standards were accepted is that an agreement was made between Microsoft and Novell whereby Microsoft indemnifies **Novell customers** from patent lawsuits with regard to .NET technologies -- not Ubuntu users, not Red Hat users, not Slackware users, not Mandriva users. Not even Linspire or Xandros customers are indemnified (though those two distros signed their own "covenants" with Microsoft, Mono was explicitly excluded from their patent agreements). 

The Mono project is lying when they assert that Microsoft has granted everyone a right to use MS .NET patented technology (ECMA or no) for any purpose, and for free. Such a grant only exists *for Novell customers*, and this exists because Novell makes royalty payments to Microsoft covering the possibility of infringement.

---

### Post by smartboyathome on 2008-06-07
And what I always say to this: If we get rid of that, we get rid of all possibly infringing code, including the double click and sudo, both of which have patents owned by Microsoft.

---

### Post by saulgoode on 2008-06-07
> **smartboyathome said:**
> And what I always say to this: If we get rid of that, we get rid of all possibly infringing code, including the double click and sudo, both of which have patents owned by Microsoft.
SUDO was created in 1980. Microsoft's first patent was in 1986. Microsoft's first software patent was in 1988.

---

### Post by smartboyathome on 2008-06-07
Yes, but sudo now conflicts with the patent by MS for the UAC. I dont know much about patents, though, so I might be misinformed.

---

### Post by vexorian on 2008-06-07
> **smartboyathome said:**
> Yes, but sudo now conflicts with the patent by MS for the UAC. I dont know much about patents, though, so I might be misinformed.
Yes, you are.

* UAC patents are much different.
* If they were the same, they can't sure for sudo, it would be a little suicidal to sue the very prior art...

* As a matter of fact, sudo now would protect anyone trying to implement something described by the UAC patent...

MONO is different for the fact its purpose is actually to implement patented specs...

---

### Post by saulgoode on 2008-06-09
> **alternatealias said:**
> >  Originally Posted by saulgoode:
According to the Mono Project, Mono already includes ADO.NET and ASP.NET; and development versions include Windows.Forms (is this an implementation of WinForms.NET?). Are these components being stripped out of the Ubuntu version of Mono? Are they not implementations of technologies that might read on Microsoft patent claims?yes, but they are not part of the core mono package - they are addons.

It does not really matter whether or not they are part of the "core mono package". What matters is whether they are [included in Ubuntu]("http://packages.ubuntu.com/search?keywords=winforms&searchon=all&suite=hardy&section=main").

> **alternatealias said:**
> According to wikipedia, the ECMA portions of the .NET framework are available under RAND-Z (Reasonable And Non-Discriminatory; Zero-cost) terms.

I don't see any mention of RAND-Z in the [Mono Wikipedia article](http://en.wikipedia.org/wiki/Mono_%28software%29). Perhaps you could cite an appropriate passage? 

What I do see states "*The base technologies submitted to the ECMA, and therefore also the Unix/Gnome-specific parts, **may be** non-problematic.*"

Not quite the grand assertion for which I was hoping.

> **alternatealias said:**
> This is also pretty well common knowledge at this point.

In other words, there are no actual facts which support your claim. 

> **alternatealias said:**
> Microsoft have never claimed that the core EMCA portions of Mono needed to be licensed.

Again, you are wrong. From [David Berlind's Reality Check]("http://techupdate.zdnet.com/techupdate/stories/main/0,14179,2887217,00.html").

> According to Microsoft's director of intellectual property Michele Herman, who I interviewed earlier this year, the answer is a qualified yes. "If someone implemented a product that conforms to the specification, we believe we have a patent or one pending that's essential to implementing the specification." Herman also cautions that "to the extent that other vendors that have developed other applications or middleware and have patents on them, those vendors could also choose to enforce those patents if the relevant intellectual property is essential to deploying an implementation of the CLI."

According to Herman, third parties will have to enter into a reasonable and non-discriminatory (RAND) license agreement with Microsoft."

I would recommend reading that article, or perhaps GNOME developer  [Seth Nickell's webblog]("http://www.gnome.org/~seth/blog/mono")
on the topic. Sure it was written back in 2004, **BUT NOTHING HAS CHANGED** -- (except for Novell negotiating an unreasonable and discriminatory licensing agreement with Microsoft).

More recently (about two weeks ago), Brian Goldfarb, the Lead Product Manager for Microsoft's Web Platform and Tools division [stated]("http://talkback.zdnet.com/5208-10535-0.html?forumID=1&threadID=47762&messageID=889966&start=0"), "Moonlight is usable for anyone on any distribution of Linux (redhat, ubuntu, etc.) -- it is not **limited just to Novell as Mono is**."


If the terms of this hypothetical RAND-Z license can't be examined, how are we to determine if GNU/Linux distros other than Novell's are covered by it?

---

### Post by geoken on 2008-06-09
I don't understand why people arguing that Mono has no patent problems continue to cite ECMA certification. 

RAND doesn't mean patent amnesty. I think it can be argued that what the Novell agreement has done is set the bar for what could be considered 'Reasonable and non discriminatory". Seeing as how RAND doesn't require a specific definition of what is reasonable or what is non discriminatory, all we would have to go by are past agreements (if they exist). In other words, if some team of devs were working on a Mono app and MS asked them for $164,000 could those devs really claim the liscensing terms were unreasonable or discriminatory (thereby violating RAND) given what Novell has paid for that patent amnesty. Likewise, would it be unreasonable for Microsoft to request 1 million from Canonical or Red Hat?

---

### Post by alternatealias on 2008-06-11
If Ubuntu ships the Windows.Forms addon, then that is a separate issue from whether or not core Mono is safe.

As far as a RAND-Z promise, talk to the GNU developers working on Portable.NET or send an email to Microsoft itself for confirmation.

Here is a quote from Jim Miller from the Microsoft .NET team:
> The ECMA process requires that all patents held by member companies that are essential for implementing its standards are available under "reasonable and non-discriminatory (RAND) terms" for the purpose of
implementing those Standards. This is the normal condition used in all
International Standards organizations, including both ECMA and ISO.

But Microsoft (and our co-sponsors, Intel and Hewlett-Packard) went
further and have agreed that our patents essential to implementing C#
and CLI will be available on a "royalty-free and otherwise RAND" basis
for this purpose.

From the ".NET Framework" wikipedia article:

> While Microsoft and their partners hold patents for the CLI and C#, ECMA and ISO require that all patents essential to implementation be made available under "reasonable and non-discriminatory (RAND) terms." In addition to meeting these terms, the companies have agreed to make the patents available royalty-free.

Satisfied?

---

### Post by saulgoode on 2008-06-11
> **alternatealias said:**
> If Ubuntu ships the Windows.Forms addon, then that is a separate issue from whether or not core Mono is safe.

As far as a RAND-Z promise, talk to the GNU developers working on Portable.NET or send an email to Microsoft itself for confirmation.


Here is a quote from Jim Miller from the Microsoft .NET team:
> The ECMA process requires that all patents held by member companies that are essential for implementing its standards are available under "reasonable and non-discriminatory (RAND) terms" for the purpose of
implementing those Standards. This is the normal condition used in all
International Standards organizations, including both ECMA and ISO.

But Microsoft (and our co-sponsors, Intel and Hewlett-Packard) went
further and have agreed that our patents essential to implementing C#
and CLI will be available on a "royalty-free and otherwise RAND" basis
for this purpose.

Satisfied?

Saying that the patents "will be available" is NOT the same thing as the licenses existing. 

If I write book and state that I will make that book available for anyone to read at no cost, that does not mean that Prentice-Hall or Barnes&Noble can just go ahead and print off a bunch of copies and give them away. **I** am the one who determines when and how those books are to be available for free reading. If you infer that my statement grants license to all publishers to print and hand out free copies, I must tell you, you are WRONG. I still retain the rights to negotiate the terms of how people get to read my book (at no cost). I might choose a different publisher or bookstore, or might give copies to libraries, or I might individually meet everyone wanting one and give them a handwritten copy. None of those things are specified in my statement and it would be completely misguided to suggest that I ever implied I was sacrificing such options.

THAT is precisely analogous to what has been uttered by every Microsoft employee (including Mr Miller) who has spoken on the topic of .NET's ECMA-covered patents over the last six years. Yes, Microsoft will make the patent licensing available, and not even charge you money. But you still need to negotiate your licensing with them. This is precisely what *Novell* has done, negotiated a license with Microsoft so that they themselves (Novell) can use that patented technology. That doesn't mean that everyone else falls under the same licensing agreement. 

And what I am discussing here is NOT limited to Windows.forms, ASP.NET, and ADO.NET. It is about the ECMA-covered technologies which everybody feels so damned confident about using because leaders of the Mono Project either can't parse simple English statements, or they are intentionally lying.

If you want to argue whether or not Microsoft patents are valid (such as Smartboyathome has suggested), I can accept that and would support anyone in their battle against any software patent. 

But when the Mono Project FAQ states that "*Basically a grant is given to anyone who want to implement those components for free and for any purpose*", **IT IS WRONG!**

---

### Post by alternatealias on 2008-06-12
> **saulgoode said:**
> But when the Mono Project FAQ states that "*Basically a grant is given to anyone who want to implement those components for free and for any purpose*", **IT IS WRONG!**

If they are so wrong, then why have Red Hat's and Ubuntu's lawyers (in addition to Novell's) all deemed it safe? Why, also, have the GNU lawyers deemed it safe to implement as part of DotGNU?

If the ECMA portions of the .NET Framework are *not* under RAND-Z, then DotGNU/Portable.NET must be breaking the law because they for sure have not paid Microsoft to license the technology ;-)

---

### Post by geoken on 2008-06-12
> **alternatealias said:**
> 





Satisfied?

I'll be satisfied if anything corroborating the above information is available on an official Microsoft site and stated in a binding manner, not just some dev's statements. To date, the closest thing I've seen to an actual link was on the Mono site where they dugg up some long deleted link (via the internet archive) to a single reply on some random mailing list. If that was the best the Mono team itself could do to produce a link detailing alleged patent amnesty, then I think it's safe to assume the patent amnesty isn't an official MS policy.

Here are the facts as I see them.

1.MS obviously holds patents over all of .net, even the ECMA standardized parts (under the terms of RAND)

2. Novel and others have paid MS for patent amnesty and MS has worked with them on Mono related stuff thereby establishing many precedents (most importantly, the RAND terms)

3. Claims of patent amnesty are extremely hard to corroborate and essentially amount people making unnoficial claims on random mailing lists. Even worse, the claims have since been deleted and are only available in archives.

In summary;

_Evidence that MS holds enfocable patents on all of .NET_
Extremely plentiful and easy to find through official channels

_Evidence that MS has granted amnesty on afformentioned patents_
Extremely hard to find (and even then it's people who have no official capacity to make such decisions speaking completely 'off the record') . Never officially stated. 



Just to set the record straight, I would love for you to prove me completely wrong. I'm no biased MS hater. I think it would be great if we could use mono (or any language that lets more devs work with Linux) without worrying about anything. In the end it means better software for all of us.

---

### Post by saulgoode on 2008-06-12
> **alternatealias said:**
> If they are so wrong, then why have Red Hat's and Ubuntu's lawyers (in addition to Novell's) all deemed it safe? Why, also, have the GNU lawyers deemed it safe to implement as part of DotGNU?

Perhaps the better question to ask is why Novell, after performing a legal assessment early in 2006, deemed it *unsafe* to implement Mono without entering into a Patent Covenant with Microsoft later that year? 

Even if RedHat deemed Mono safe -- feel free to provide a reference supporting that, as RedHat doesn't include Mono -- nowhere have I seen that it was based upon RAND promises from Microsoft. If anything (and again RedHat doesn't include Mono), comments from RedHat personnel (in an unofficial capacity) indicate that any "safety margin" is based upon Mono being included in the Open Invention Network. Likewise, none of the comments from Mark Shuttleworth cite hypothetical RAND licenses from Microsoft as being behind Ubuntu's decision. 

So none of this supports the assertion from the Mono Project that Mono is indemnified by Microsoft.

---

