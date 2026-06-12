---
title: "Mono on ubuntu"
date: 2008-07-13
forum: Programming Talk
---

### Post by hoboy on 2008-07-13
Maybe this is not the right forum forgive me.
I have started to use ubuntu 6-7 months ago,now I just don't want to use windows unless I have to, my problem is that I have to develop some applications in .Net/asp2.0, I am trying mono, but it doesn't seem to have any visual design, or I am wrong ?
any help is welcome

---

### Post by sonicb00m on 2008-07-13
As far as I know you can't do windows form design with it, no. I've actually had ZERO success compiling any of the VB projects we made and they are not complicated at all, using only standard VB components and the MySQL connector. The only thing Mono has been handy for is the readability of VB code while converting it to Java.

You can use glade and GTk+ instead.

I have decided to start using Java and Swing for this very reason.

---

### Post by Kikuta on 2008-07-13
How do you install mono?

---

### Post by Vadi on 2008-07-13
You can find mono in add/remove. Also, check out this ([click]("http://www.mono-project.com/Start")). I think mono does have a GUI designer, but I forget it's name.

That said, while mono is certainly a helpful tool, it's encouraged that you make use of other technologies when you can :/

---

### Post by sakabato on 2008-07-14
> **sonicb00m said:**
> As far as I know you can't do windows form design with it, no. I've actually had ZERO success compiling any of the VB projects we made and they are not complicated at all, using only standard VB components and the MySQL connector. The only thing Mono has been handy for is the readability of VB code while converting it to Java.

You can use glade and GTk+ instead.

I have decided to start using Java and Swing for this very reason.

Incorrect. Mono has a windows form designer
[http://www.mono-project.com/WinForms_Designer](http://www.mono-project.com/WinForms_Designer)

This thread does not mention about VB. You can safely develop sophisticated applications with C#. You can use GTK#*as well. Note that, ubuntu comes with  out of box C# gui application called Tomboy.

---

### Post by Xealot on 2008-07-14
The development IDE is called Monodevelop, comes with a GUI designer and all that. :)

---

### Post by sonicb00m on 2008-07-15
Wow. I stand corrected.

Is the Ubuntu repo extremely out of date with Mono then? I've found it impossible to compile even basic VB applications. Even after installing necessary dependencies and installing the RPM version of VBNC it still never manages to find the system references.

I know mono C# is more developed than the VB but unfortunately, I've no wish to convert or write C# code at this stage.

---

### Post by LaRoza on 2008-07-15
> **sonicb00m said:**
> 
Is the Ubuntu repo extremely out of date with Mono then? I've found it impossible to compile even basic VB applications.

VB(.NET) is a Microsoft technology and isn't standardised (open standard). Have zero expectations with using it.

---

### Post by Mickeysofine1972 on 2008-07-15
The only thing I ever got compiled with Mono that was made for window .NET was the opensource version of the SecondLife SIm Server

But that was a terminal program and had no forms.

Mike

---

### Post by cybergal on 2008-07-27
I am a user, not a programmer, and hope that someone will answer this question for me:

 Is MONO affiliated in any way with Microsoft when installed in Linux, i.e., money going to Microsoft?  If so, can MONO be disabled? I'm running Ubuntu 6.06 LTS, which I understand doesn't have MONO installed, and am planning to upgrade soon to 8.04 LTS, which I read somewhere does come with MONO.

TIA

---

### Post by Kadrus on 2008-07-27
You can install mono from synaptic,Mono is an open source project
[Mono Home page]("http://www.mono-project.com/Main_Page")
Go to their website and read more about it.And install it from synaptic if you want to use it.

---

### Post by Vadi on 2008-07-27
No, nobody is paying Microsoft for this and Mono is an open-source project.

---

### Post by cybergal on 2008-07-27
Thanks, guys, for your quick responses.

---

### Post by neighborlee on 2008-08-05
> **Vadi said:**
> No, nobody is paying Microsoft for this and Mono is an open-source project.

No proof on point #1, but #2 is def. not true at all, because of a few things : the patent agreement is not OSS ( rand etc.,) and also redhat has proved already that they never got any patent agreement from M$ about .NET, that and now fedora has removed mono from livecd. I dont have url's atm here in linux, but I can get them if anyone wants them.

Java is free now in case anyone missed it.

cheers
nl

---

### Post by cybergal on 2008-08-06
This link answers many questions and shows that the association with Microsoft is too close for [my] comfort:

[http://www.theopensourcerer.com/2008/08/04/how-to-remove-mono-m-from-ubuntu-hardy-heron/](http://www.theopensourcerer.com/2008/08/04/how-to-remove-mono-m-from-ubuntu-hardy-heron/)

---

### Post by true_friend on 2008-08-07
Java is open source after 15+ years of its creation, let .net at least 15 years you'll see better opensource .net then.

---

### Post by sakabato on 2008-08-09
Fedora contains Gnome. Gnome contains Mono. Mono does not contain the patented parts of .NET.Mono belongs in Fedora. Period

---

### Post by neighborlee on 2008-08-18
> **sakabato said:**
> Fedora contains Gnome. Gnome contains Mono. Mono does not contain the patented parts of .NET.Mono belongs in Fedora. Period

What makes you so sure mono belongs in gnome; on what basis are you making that statement ?

First off, no fedora does not contain mono , not the core or any of the mono apps and part of that is because redhat never recieved any patent 'grants' to  use it which is why it must only be downloaded from Novel. It has been going since Fedora 9, and is also not there in 10.

If you dont believe it, ask on forums or try livecd for yourself.

It is nice to see Redhat/fedora looking out for the community ;)

cheers
nl

---

### Post by LaRoza on 2008-08-18
It is free software: [http://en.wikipedia.org/wiki/Mono_(software)#License](http://en.wikipedia.org/wiki/Mono_(software)#License)

It follows the ECMA standard.

---

### Post by cybergal on 2008-08-18
FWIW:  [http://www.gnome.org/~seth/blog/mono](http://www.gnome.org/~seth/blog/mono)

---

### Post by neighborlee on 2008-08-20
> **LaRoza said:**
> It is free software: [http://en.wikipedia.org/wiki/Mono_(software)#License](http://en.wikipedia.org/wiki/Mono_(software)#License)

It follows the ECMA standard.

Even from M$ employee own lips, mono is not free unlike supposedly Moonlight:

[http://talkback.zdnet.com/5208-10535-0.html?forumID=1&threadID=47762&messageID=889966&start=0](http://talkback.zdnet.com/5208-10535-0.html?forumID=1&threadID=47762&messageID=889966&start=0)

[http://www.digitalmajority.org/forum/t-54546/reasonable-and-not-non-discriminatory](http://www.digitalmajority.org/forum/t-54546/reasonable-and-not-non-discriminatory) < and this if you care to read it.

[http://www.microsoft.com/interop/collab/xandros/definitions2.aspx#clone](http://www.microsoft.com/interop/collab/xandros/definitions2.aspx#clone) < then there is this lovely bit of information,,oops you might have missed that.

All in all, it is clear that the ECMA/.Net/Mono patent conditions are far from either &#8220;reasonable&#8221; or &#8220;non-discriminatory".

Why people are so quick to trust 'promises' from those whom have clearly indicated that they see linux as a 'cancer' is  illogical and should be scrutinized by anyone that cares about FOSS.

cheers
nl

---

### Post by alternatealias on 2008-08-21
> **neighborlee said:**
> Even from M$ employee own lips, mono is not free unlike supposedly Moonlight:

[http://talkback.zdnet.com/5208-10535-0.html?forumID=1&threadID=47762&messageID=889966&start=0](http://talkback.zdnet.com/5208-10535-0.html?forumID=1&threadID=47762&messageID=889966&start=0)


So a Microsoft employee spreads FUD and you take the bait. Grats for being a sucker.

It's in Microsoft's best interest to shroud Mono in FUD (just like it's in their best interest to FUD Linux and other Free Software), but they can't do jack about it because:

1. Core Mono implements ECMA 334 and 335 which are under RAND-Z terms - therefor Microsoft has given up their rights to sue over patent infringement.

2. If Mono's Windows.Forms infringes on patents, then so does DotGNU's implementation as well as WINE. WINE has existed for a decade and Microsoft hasn't sued and WINE is far more widely depended on than Mono's Windows.Forms will ever be.

Contrary to what a lot of the Mono-Haters/FUDers like to tell you, Windows.Forms is not a core component of Mono nor is it required to write GUI apps under Linux or MacOS (or even Windows). Nor is it even used to write any of the current Mono apps under Linux.

3. ASP.NET: More-or-less in the same boat as Windows.Forms. If Mono's ASP.NET infringes on patents (even those not maintained by Microsoft), then it is very likely that PHP also infringes upon said patents.

4. There exists the OIN to counter any IP attacks against many Free Software projects... INCLUDING Mono.

Let's also not forget that Microsoft has a huge plethora of patents - many of which very likely /are/ infringed by Free Software. Other than a few idle threats, Microsoft hasn't done anything about it. Why not? Because it would destroy them - either in a patent nuclear war or else it would be hit with more anti-compete law suites.

> **neighborlee said:**
> 
[http://www.digitalmajority.org/forum/t-54546/reasonable-and-not-non-discriminatory](http://www.digitalmajority.org/forum/t-54546/reasonable-and-not-non-discriminatory) < and this if you care to read it.


Bravo for finding a clueless document and pointing to it as fact.

You see, you failed to realize that ECMA 334 and 335 are not under RAND, they are under RAND-Z - e.g. Reasonable and Non-Discriminatory; Zero-cost.

As the article states, RAND means "we apply a uniform fee", which in this case is $0. How does that ban Free Software from implementing it? It doesn't. RAND does, but only if the cost is > $0 (and even then it doesn't "ban" Free Software implementations, it just means there is a cost).

RAND-Z is as reasonable and non-discriminatory as you can get.

> **neighborlee said:**
> 
[http://www.microsoft.com/interop/collab/xandros/definitions2.aspx#clone](http://www.microsoft.com/interop/collab/xandros/definitions2.aspx#clone) < then there is this lovely bit of information,,oops you might have missed that.

All in all, it is clear that the ECMA/.Net/Mono patent conditions are far from either &#8220;reasonable&#8221; or &#8220;non-discriminatory".


Okay... so Xandros doesn't get to call Mono as a "Cone Product" in their deal with Microsoft. Whoopty-doo (ok, so it affects Xandros - but it doesn't affect the rest of us).

This document does not prove that Mono infringes any patents or that Microsoft will sue, it just means that Microsoft wasn't willing to include Mono in their deal with Xandros. Just like they didn't include OpenXchange or OpenOffice/StarOffice.

Should we all stop using those products now too?

Your logic is hilarious.

> **neighborlee said:**
> 
Why people are so quick to trust 'promises' from those whom have clearly indicated that they see linux as a 'cancer' is  illogical and should be scrutinized by anyone that cares about FOSS.

cheers
nl

I don't blindly trust any promises from Microsoft, but in the case of Mono - it's not the promise I trust, it's the fact that Microsoft is in a position which disallows them from attacking Mono over patents (or at least the core components of Mono) and the fact that it is very unlikely they'd sue over the non-core components.

In other news... SecondLife is rolling out Mono-based servers:

[http://blog.secondlife.com/2008/08/20/mono-launch/](http://blog.secondlife.com/2008/08/20/mono-launch/)

---

### Post by neighborlee on 2008-08-21
> **alternatealias said:**
> So a Microsoft employee spreads FUD and you take the bait. Grats for being a sucker.

It's in Microsoft's best interest to shroud Mono in FUD (just like it's in their best interest to FUD Linux and other Free Software), but they can't do jack about it because:

1. Core Mono implements ECMA 334 and 335 which are under RAND-Z terms - therefor Microsoft has given up their rights to sue over patent infringement.

2. If Mono's Windows.Forms infringes on patents, then so does DotGNU's implementation as well as WINE. WINE has existed for a decade and Microsoft hasn't sued and WINE is far more widely depended on than Mono's Windows.Forms will ever be.

Contrary to what a lot of the Mono-Haters/FUDers like to tell you, Windows.Forms is not a core component of Mono nor is it required to write GUI apps under Linux or MacOS (or even Windows). Nor is it even used to write any of the current Mono apps under Linux.

3. ASP.NET: More-or-less in the same boat as Windows.Forms. If Mono's ASP.NET infringes on patents (even those not maintained by Microsoft), then it is very likely that PHP also infringes upon said patents.

4. There exists the OIN to counter any IP attacks against many Free Software projects... INCLUDING Mono.

Let's also not forget that Microsoft has a huge plethora of patents - many of which very likely /are/ infringed by Free Software. Other than a few idle threats, Microsoft hasn't done anything about it. Why not? Because it would destroy them - either in a patent nuclear war or else it would be hit with more anti-compete law suites.



Bravo for finding a clueless document and pointing to it as fact.

You see, you failed to realize that ECMA 334 and 335 are not under RAND, they are under RAND-Z - e.g. Reasonable and Non-Discriminatory; Zero-cost.

As the article states, RAND means "we apply a uniform fee", which in this case is $0. How does that ban Free Software from implementing it? It doesn't. RAND does, but only if the cost is > $0 (and even then it doesn't "ban" Free Software implementations, it just means there is a cost).

RAND-Z is as reasonable and non-discriminatory as you can get.



Okay... so Xandros doesn't get to call Mono as a "Cone Product" in their deal with Microsoft. Whoopty-doo (ok, so it affects Xandros - but it doesn't affect the rest of us).

This document does not prove that Mono infringes any patents or that Microsoft will sue, it just means that Microsoft wasn't willing to include Mono in their deal with Xandros. Just like they didn't include OpenXchange or OpenOffice/StarOffice.

Should we all stop using those products now too?

Your logic is hilarious.



I don't blindly trust any promises from Microsoft, but in the case of Mono - it's not the promise I trust, it's the fact that Microsoft is in a position which disallows them from attacking Mono over patents (or at least the core components of Mono) and the fact that it is very unlikely they'd sue over the non-core components.

In other news... SecondLife is rolling out Mono-based servers:

[http://blog.secondlife.com/2008/08/20/mono-launch/](http://blog.secondlife.com/2008/08/20/mono-launch/)

Why reinvent the wheel, when you can share ;

Perhaps the better question to ask is why Novell, after performing a legal assessment early in 2006, deemed it unsafe to implement Mono without entering into a Patent Covenant with Microsoft later that year?

Even if RedHat deemed Mono safe -- feel free to provide a reference supporting that, as RedHat doesn't include Mono -- nowhere have I seen that it was based upon RAND promises from Microsoft. If anything (and again RedHat doesn't include Mono), comments from RedHat personnel (in an unofficial capacity) indicate that any "safety margin" is based upon Mono being included in the Open Invention Network. Likewise, none of the comments from Mark Shuttleworth cite hypothetical RAND licenses from Microsoft as being behind Ubuntu's decision.

So none of this supports the assertion from the Mono Project that Mono is indemnified by Microsoft.

cheers
nl

---

### Post by pmasiar on 2008-08-21
> **alternatealias said:**
> So a Microsoft employee spreads FUD and you take the bait. Grats for being a sucker.

It's in Microsoft's best interest to shroud Mono in FUD (just like it's in their best interest to FUD Linux and other Free Software), but they can't do jack about it because:

It's foolish give legal advice or accept it over internet.

GPL is free from this problems (until next attack), and software produced in a shadow of convicted monopolist should be used only after advice of legal advisor you (or company) hired to take care of your interests.

For a free software developer, choice between free and suspicious is clear enough: little to gain and much to lose. For a commercial, it's different, that's why your company has a lawyer.

---

### Post by alternatealias on 2008-08-21
> **pmasiar said:**
> It's foolish give legal advice or accept it over internet.

GPL is free from this problems (until next attack), and software produced in a shadow of convicted monopolist should be used only after advice of legal advisor you (or company) hired to take care of your interests.

For a free software developer, choice between free and suspicious is clear enough: little to gain and much to lose. For a commercial, it's different, that's why your company has a lawyer.

Deciding to not use a piece of software and bad-mouthing it are two totally different things.

Since it is obvious that Neighborlee is clueless about Mono, he shouldn't be bashing it - even if he disagrees with its usage.

I'll choose to continue using Mono in my company and in any new side projects I start because the likelyhood of me or any of my users getting sued is next to 0.

---

### Post by alternatealias on 2008-08-21
> **neighborlee said:**
> Why reinvent the wheel, when you can share ;

Perhaps the better question to ask is why Novell, after performing a legal assessment early in 2006, deemed it unsafe to implement Mono without entering into a Patent Covenant with Microsoft later that year?


Have any proof that that was the reason behind their deal? If not ,then you are just assuming... and you know what assuming says about you, right?

Something about you being an ***.

[> **neighborlee said:**
> 
Even if RedHat deemed Mono safe


If RedHat deemed it safe, why did Novell not deem it safe?

RedHat isn't in the habit of deeming something safe that isn't. Their lawyers err on the side of caution, so if they deemed it safe then for all practical purposes, it likely is (for at least the reasons I explained above).

> **neighborlee said:**
>  -- feel free to provide a reference supporting that, as RedHat doesn't include Mono


Originally RedHat did not include Mono until their lawyers had time to evaluate it.

They do now include Mono (starting with Fedora 8 I believe?). I've heard rumors that Mono packages were removed from the Live CD, but that's the Live CD which you likely want to keep as a minimal desktop since it has to run on a ramdisk.

The Fedora packager for Mono contacted the Mono mailing-list the other day asking about the --with-moonlight configure option for Mono 2.0, so it sounds to me like they are still packaging it.

The packager for F-Spot and Banshee recently stepped down, so that may be another reason why no Mono apps are on the Live CD - you can't assume that just because they are no longer on the Live CD that the RedHat lawyers have suddenly deemed Mono "unsafe". More than likely it's because the packages for F-Spot and Banshee are broken and so not included on the preview CDs.

You Mono-Haters really like to draw conclusions from insufficient information, don't you?

It seems to be a trend with you guys.

> **neighborlee said:**
> 
 -- nowhere have I seen that it was based upon RAND promises from Microsoft.


You can request that information from ECMA, or I'm sure the Mono and/or DotGNU developers could confirm it.

> **neighborlee said:**
> 
If anything (and again RedHat doesn't include Mono), comments from RedHat personnel (in an unofficial capacity) indicate that any "safety margin" is based upon Mono being included in the Open Invention Network.


That is certainly one of the reasons it is "safe", yes.

> **neighborlee said:**
> 
Likewise, none of the comments from Mark Shuttleworth cite hypothetical RAND licenses from Microsoft as being behind Ubuntu's decision.


There you go assuming again...

Have you asked about it specifically? If not, then how can you assume that it is not part of the equation?

RAND-Z is mostly only interesting to developers of the technology anyway, since it is typically them (or the distributor) who worries about licensing any patents involved (which is why non-zero-cost RAND terms are not Free Software friendly, because it is unclear who pays the licensing fees).

Since it is RAND-Z, most people don't care (and thus don't bother to look for) which patents Microsoft may have on ECMA 334 and 335 (because it's irrelevant).

For all you know, there aren't any patents that apply - maybe /that's/ the reason Mark Shuttleworth hasn't listed RAND-Z as a reason that Mono is "safe". You simply don't know.

Since you don't know, you can't draw your conclusion from what Mark Shuttleworth has stated.

I suggest you attend a few logic courses at your local community college, you'll learn a lot and might start to make much less confused/illogical arguments.

---

### Post by pmasiar on 2008-08-21
> **alternatealias said:**
> Since it is obvious that Neighborlee is clueless about Mono, he shouldn't be bashing it - even if he disagrees with its usage.

I'll choose to continue using Mono in my company and in any new side projects I start because the likelyhood of me or any of my users getting sued is next to 0.

I am not ready to invest time to evaluate any of you: Neighborlee might be wrong or right, and you too. Way too much trouble, but summary is obvious: it is far from pristine clean.

For your company, lawyer and top brass made the decision that risk is worth the reward, and even you admit risk is not 0. If I was FOSS developer, why I spend hours researching claims of both of you guys, and then take even minimal financial risk, if I know for sure I will not have any financial reward ever?

---

### Post by alternatealias on 2008-08-21
> **pmasiar said:**
> I am not ready to invest time to evaluate any of you: Neighborlee might be wrong or right, and you too. Way too much trouble, but summary is obvious: it is far from pristine clean.

For your company, lawyer and top brass made the decision that risk is worth the reward, and even you admit risk is not 0. If I was FOSS developer, why I spend hours researching claims of both of you guys, and then take even minimal financial risk, if I know for sure I will not have any financial reward ever?

I'm not arguing that you should use Mono - use whatever you deem appropriate.

Just be aware that no matter what language/tools you choose, there is ALWAYS some risk.

It is impossible to not infringe on patents when writing software.

I know this from personal experience as a professional software developer.

The question is how high is the risk of getting sued, not whether you infringe or not.

---

### Post by neighborlee on 2008-08-22
> If RedHat deemed it safe, why did Novell not deem it safe?

One company decided to make their business model revolve around M$, the other has stayed clean.

> 
Originally RedHat did not include Mono until their lawyers had time to evaluate it.

They do now include Mono (starting with Fedora 8 I believe?). I've heard rumors that Mono packages were removed from the Live CD, but that's the Live CD which you likely want to keep as a minimal desktop since it has to run on a ramdisk.

Wrong; Redhat has 'never' included mono, and they never will.

> 
The Fedora packager for Mono contacted the Mono mailing-list the other day asking about the --with-moonlight configure option for Mono 2.0, so it sounds to me like they are still packaging it.

THey are free to package it,,but its not included by default on livecd ;)

> 
The packager for F-Spot and Banshee recently stepped down, so that may be another reason why no Mono apps are on the Live CD - you can't assume that just because they are no longer on the Live CD that the RedHat lawyers have suddenly deemed Mono "unsafe". More than likely it's because the packages for F-Spot and Banshee are broken and so not included on the preview CDs.


see above :)

> 
You Mono-Haters really like to draw conclusions from insufficient information, don't you?

It seems to be a trend with you guys.


Where have I indicated hate to you?

> 
You can request that information from ECMA, or I'm sure the Mono and/or DotGNU developers could confirm it.

Darn,  I was hoping , that since you brought this  clincher-deal up , you already had direct links , my bad.



> That is certainly one of the reasons it is "safe", yes.


Where, on this OIN page does it state mono is covered; I looked many times and have yet to find it.


> RAND-Z is mostly only interesting to developers of the technology anyway, since it is typically them (or the distributor) who worries about licensing any patents involved (which is why non-zero-cost RAND terms are not Free Software friendly, because it is unclear who pays the licensing fees).
Since it is RAND-Z, most people don't care (and thus don't bother to look for) which patents Microsoft may have on ECMA 334 and 335 (because it's irrelevant).

If its of only interest to developers, then I guess it does not apply to this conversation of mono's legality; thanks for clearing that up.

> 
For all you know, there aren't any patents that apply - maybe /that's/ the reason Mark Shuttleworth hasn't listed RAND-Z as a reason that Mono is "safe". You simply don't know.

You bear the burden of proof, not me, in showing that its a safe technology, when all 'reasonable' signs indicate is   definitely is not ;) M$ is a convicted monopolist who sees linux as a Cancer , so if you  really feel comfy in using their stuff, go right ahead, but the rest of us who love FOSS will avoid its less than pristine nature Im sure.


> 
I suggest you attend a few logic courses at your local community college, you'll learn a lot and might start to make much less confused/illogical arguments.

You are free to resort to attacks like this, but it wont win anyone over, and likely you will lose many; a sign of desperation , as it just shows  your lack of character.

cheers 
nl

---

### Post by alternatealias on 2008-08-22
> **neighborlee said:**
> One company decided to make their business model revolve around M$, the other has stayed clean.


That doesn't answer the question.

> **neighborlee said:**
> 
Wrong; Redhat has 'never' included mono, and they never will.


Wrong. Fedora has shipped Mono by default.


> **neighborlee said:**
> 
THey are free to package it,,but its not included by default on livecd ;)


Have any links to support this claim?

> **neighborlee said:**
> 
see above :)


Indeed, see above. You keep insisting that Red Hat is not allowed to ship Mono packages but fail to provide any links.

I'll tell you what, I'll fire off an email to Tom "Spot" Calloway from Red Hat Legal and get his opinion on the matter.


> **neighborlee said:**
> 
Where have I indicated hate to you?


Are you not spreading fear, uncertainty and doubt about whether or not Mono is reasonably safe from patent attacks from Microsoft?

I believe you are. That indicates hate.


> **neighborlee said:**
> 
Darn,  I was hoping , that since you brought this  clincher-deal up , you already had direct links , my bad.


I had evidence in my Inbox a few years ago, but company policy is to delete mail older than a few months.

It would be trivial to send a query to a Microsoft or ECMA representative yourself if you really cared to know (which I suspect you don't, hence why you haven't actually done it but yet insist that Mono does not fall under RAND-Z terms).

> **neighborlee said:**
> 
Where, on this OIN page does it state mono is covered; I looked many times and have yet to find it.


You might check the following link by [email]gdk@redhat.com[/email]:

[http://gregdek.livejournal.com/4008.html](http://gregdek.livejournal.com/4008.html)


> **neighborlee said:**
> 
If its of only interest to developers, then I guess it does not apply to this conversation of mono's legality; thanks for clearing that up.


I never said that. If you had bothered to read what I stated, you'd have seen that what I said was that it is mostly only of interest to developers/distributors because it is typically those guys who end up paying the licensing fees (when there are fees).

However, in the case of Mono - there are no fees.

> **neighborlee said:**
> 
You bear the burden of proof, not me


No, you are making a straw-man argument here.

You cannot prove that Mono is risk-free, just like you can't prove that Java or OpenOffice or Pidgin or Ubuntu or Linux are risk-free.

> **neighborlee said:**
> 
, in showing that its a safe technology, when all 'reasonable' signs indicate is   definitely is not ;)


At least Red Hat, Ubuntu and Linden Labs have deemed Mono reasonably safe, so what are these signs you speak of?

> **neighborlee said:**
> 
M$ is a convicted monopolist who sees linux as a Cancer


And this proves Mono is unsafe...how?

If this is your strongest argument (and it appears that it is based on how often you fall back to this argument), then your position is pretty weak.

> **neighborlee said:**
> 
 , so if you  really feel comfy in using their stuff, go right ahead,


Thanks, I'm glad you feel that way - so stop trying to force your way on me by demanding that Ubuntu drop Mono.

> **neighborlee said:**
> 
but the rest of us who love FOSS


I love F/OSS too. Luckily, even by Richard Stallman's definition, Mono is F/OSS.

> **neighborlee said:**
> 
will avoid its less than pristine nature Im sure.


How do you define pristine? "Not in any way related to Microsoft"?

If that's your definition of "pristine", I suggest you audit your system - odds are incredibly high that you have Microsoft influenced technologies on your system.

If you define "pristine" as "risk-free from patents" then I suggest you uninstall your entire system right now because I guarantee software you run infringes someone's patents somewhere.

> **neighborlee said:**
> 
You are free to resort to attacks like this, but it wont win anyone over,


It wasn't an attack, it was a suggestion. You kept drawing conclusions from insufficient data and obviously failed to even realize it, so I was suggesting that you do some learning about logic such that you could make better arguments in the future.

Meanwhile, I see that you ran to the BoycottNovell IRC channel and got Roy's help to publicly attack me on his website.

Real mature.

---

### Post by pmasiar on 2008-08-22
> **alternatealias said:**
> Are you not spreading fear, uncertainty and doubt about whether or not Mono is reasonably safe from patent attacks from Microsoft?

How you can prove Mono is safe? And for what value of "reasonable"? Mono was not attacked yet, because it was not in interest of MSFT. Will it be attacked? Who knows? My bet would be not (because convicted monopolist must "behave" or else), but MSFT proved than no lawyer's dirty trick is too dirty for them (Bill Gates studied Law in Harvard, not CompSci, IIRC).

For some people risk makes sense, for some not. Ask your lawyer if it makes sense for you, don't get advice from internet. Flamewars are fun but you hardly are going to change people's mind by flaming them.

---

### Post by neighborlee on 2008-08-22
> **alternatealias said:**
> That doesn't answer the question.



Wrong. Fedora has shipped Mono by default.




Have any links to support this claim?



Indeed, see above. You keep insisting that Red Hat is not allowed to ship Mono packages but fail to provide any links.

I'll tell you what, I'll fire off an email to Tom "Spot" Calloway from Red Hat Legal and get his opinion on the matter.




Are you not spreading fear, uncertainty and doubt about whether or not Mono is reasonably safe from patent attacks from Microsoft?

I believe you are. That indicates hate.




I had evidence in my Inbox a few years ago, but company policy is to delete mail older than a few months.

It would be trivial to send a query to a Microsoft or ECMA representative yourself if you really cared to know (which I suspect you don't, hence why you haven't actually done it but yet insist that Mono does not fall under RAND-Z terms).



You might check the following link by [email]gdk@redhat.com[/email]:

[http://gregdek.livejournal.com/4008.html](http://gregdek.livejournal.com/4008.html)




I never said that. If you had bothered to read what I stated, you'd have seen that what I said was that it is mostly only of interest to developers/distributors because it is typically those guys who end up paying the licensing fees (when there are fees).

However, in the case of Mono - there are no fees.



No, you are making a straw-man argument here.

You cannot prove that Mono is risk-free, just like you can't prove that Java or OpenOffice or Pidgin or Ubuntu or Linux are risk-free.



At least Red Hat, Ubuntu and Linden Labs have deemed Mono reasonably safe, so what are these signs you speak of?



And this proves Mono is unsafe...how?

If this is your strongest argument (and it appears that it is based on how often you fall back to this argument), then your position is pretty weak.



Thanks, I'm glad you feel that way - so stop trying to force your way on me by demanding that Ubuntu drop Mono.



I love F/OSS too. Luckily, even by Richard Stallman's definition, Mono is F/OSS.



How do you define pristine? "Not in any way related to Microsoft"?

If that's your definition of "pristine", I suggest you audit your system - odds are incredibly high that you have Microsoft influenced technologies on your system.

If you define "pristine" as "risk-free from patents" then I suggest you uninstall your entire system right now because I guarantee software you run infringes someone's patents somewhere.



It wasn't an attack, it was a suggestion. You kept drawing conclusions from insufficient data and obviously failed to even realize it, so I was suggesting that you do some learning about logic such that you could make better arguments in the future.

Meanwhile, I see that you ran to the BoycottNovell IRC channel and got Roy's help to publicly attack me on his website.

Real mature.

> 
Are you not spreading fear, uncertainty and doubt about whether or not Mono is reasonably safe from patent attacks from Microsoft?

I believe you are. That indicates hate.

You are free to believe what you wish, no matter that its very wrong ;)

I am doing nothing, but spreading information, and if by its very nature, you feel it directly attacks your position, then fine that is your prerogative ;)

Where I run to, or don't is of little concern to you , but I truly am sorry if it offends you so.<hm>

> At least Red Hat, Ubuntu and Linden Labs have deemed Mono reasonably safe, so what are these signs you speak of?

You keep spewing this, but I see no links to it; oh wait there are none ;)

nuff said.

cheers
nl

---

### Post by alternatealias on 2008-08-22
> 
You keep spewing this, but I see no links to it; oh wait there are none ;)


I provided you a link to Red Hat's reasons for accepting Mono as "reasonably safe" in my last post, it's not my fault if you don't read it.

I also provided a link the other day in this thread pointing to the fact that Linden Labs is rolling out their servers to use Mono starting this week.

It's also quite obvious that Ubuntu deems Mono "reasonably safe" because they ship Mono and Mono apps by default.

You, on the other hand, have provided no evidence that says otherwise.

Since you insist on giving Ubuntu and other people legal advise about staying away from Mono, the burden of proof is on you.

---

### Post by neighborlee on 2008-08-22
> **alternatealias said:**
> I provided you a link to Red Hat's reasons for accepting Mono as "reasonably safe" in my last post, it's not my fault if you don't read it.

I also provided a link the other day in this thread pointing to the fact that Linden Labs is rolling out their servers to use Mono starting this week.

It's also quite obvious that Ubuntu deems Mono "reasonably safe" because they ship Mono and Mono apps by default.

You, on the other hand, have provided no evidence that says otherwise.

Since you insist on giving Ubuntu and other people legal advise about staying away from Mono, the burden of proof is on you.

Redhat does not ship mono, I have no idea where you got that information, but here:

[http://www.internetnews.com/dev-news/article.php/3644981](http://www.internetnews.com/dev-news/article.php/3644981)

-or here-

[http://news.cnet.com/8301-10784_3-6025387-7.html](http://news.cnet.com/8301-10784_3-6025387-7.html)

Now in addition to that, I shall remind you that fedora no longer has mono, at least on liveCd10alpha, nor did it on livecd9.

cheers
nl

---

### Post by pmasiar on 2008-08-22
Please gods close this useless flamewar, they are not going to change each other minds, and just continue war started elsewhere.

---

### Post by neighborlee on 2008-08-22
> **pmasiar said:**
> Please gods close this useless flamewar, they are not going to change each other minds, and just continue war started elsewhere.

It is not a flame, or a war , it is but a debate that I thought was fair to have. IF that is not the case, fine close it but I see no reason to considering the forum it is taking place in. If you percieve it as such a flame/war, then filter it.


cheers
nl

---

### Post by alternatealias on 2008-08-22
> **neighborlee said:**
> Redhat does not ship mono, I have no idea where you got that information, but here:

[http://www.internetnews.com/dev-news/article.php/3644981](http://www.internetnews.com/dev-news/article.php/3644981)

-or here-

[http://news.cnet.com/8301-10784_3-6025387-7.html](http://news.cnet.com/8301-10784_3-6025387-7.html)

Now in addition to that, I shall remind you that fedora no longer has mono, at least on liveCd10alpha, nor did it on livecd9.

cheers
nl

I have to ask... did you actually READ the first link you pasted? Because it contradicts what you've been saying all along.

You claimed that Red Hat finds Mono to be legally unsafe, yet the following paragraph pasted below is taken from the very article you linked to:

> 
Berman noted the technical limitations of Mono as the reasons why Red Hat won't include Mono in RHEL 5. 


Berman then goes on to explain that their customers are not demanding Mono for their RHEL servers (their customers happen to prefer Java). He also notes that Mono applications are for the desktop and RHEL is not targeted at desktop users.

Fancy that. They're not including Mono because there's no reason for them to do so. It has nothing to do with legal risk.

I also have to ask:

If Mono wasn't included on LiveCD 9 but it /was/ included in the installed version, then how does the lack of Mono in LiveCD 10 prove that it won't be in the final installed version of Fedora 10?

Your logic eludes me.

---

### Post by neighborlee on 2008-08-22
> **alternatealias said:**
> I have to ask... did you actually READ the first link you pasted? Because it contradicts what you've been saying all along.

You claimed that Red Hat finds Mono to be legally unsafe, yet the following paragraph pasted below is taken from the very article you linked to:



Berman then goes on to explain that their customers are not demanding Mono for their RHEL servers (their customers happen to prefer Java). He also notes that Mono applications are for the desktop and RHEL is not targeted at desktop users.

Fancy that. They're not including Mono because there's no reason for them to do so. It has nothing to do with legal risk.

I also have to ask:

If Mono wasn't included on LiveCD 9 but it /was/ included in the installed version, then how does the lack of Mono in LiveCD 10 prove that it won't be in the final installed version of Fedora 10?

Your logic eludes me.

Where did I say it was included in the installed version ? ;)

Also, the fact that mono wont be included  in rhee ( whatever the reason ), and that its not in livecd or installed version of fedora 9 and 10 is plenty of reason I think to avoid it isn't it ; at least to me, feel free whomever to make their own judgement. Its not like M$ isn't a convicted monopolist, so you will forgive me if I remain distrustful .

taken from URL #1:
"  During the press conference to announce the deal with Novell, Microsoft CEO Steve Ballmer warned the Linux community that the patent deal was only with Novell and that others would still be at risk.  ""

That says enough to me.

cheers
nl

---

### Post by alternatealias on 2008-08-22
Fedora doesn't ship FlightGear (or a whole army of other Free Software applications) either, so should I be avoiding it/them? Does that mean it/they is/are legally unsafe to use?

Again, your reasoning is ilogical.

---

### Post by alternatealias on 2008-08-25
FWIW, it should be noted that gNewSense 2.1 includes Mono.

Since gNewSense is an FSF sponsored Linux distribution which only includes kosher packages, one must logically conclude that Mono is, in fact, kosher.

---

### Post by Ole Juul on 2008-11-17
Thankyou alternatealias and neighborlee for the informative discussion - a lot of work went into those posts! You've both made it clear to me why I personally shouldn't use mono. :)

---

