---
title: "no mono by default"
date: 2007-12-08
forum: Recurring Discussions
---

### Post by garba on 2007-12-08
just curious, what do you think about this spec?

[https://wiki.ubuntu.com/No-Mono-by-Default](https://wiki.ubuntu.com/No-Mono-by-Default)

---

### Post by bobbocanfly on 2007-12-08
I support it. F-Spot and Tomboy aren't exactly the most used applications and could be easily replaced by better alternatives (Zim for notes etc.). Also with all the rubbish Microsoft is coming out with about Patents, the last thing anyone needs is a lawsuit stealing all of Canonicals funds.

---

### Post by saulgoode on 2007-12-08
I agree with the points presented. No animosity towards the Mono project's developers but it is not a good solution for FLOSS. 

I do, however, think the memory savings issue (48Mb, uncompressed) is less important than whatever (compressed) space the package occupies on the distribution CDs.

---

### Post by Lster on 2007-12-08
I don't use either application, so I would quite like it removed, but I feel others may object. Rather, I would prefer an option in the installer that asks you what applications you would like to install. A simple list where you can select the packages you want could save disk space and installation time (I would guess?). That would keep (just about) everyone happy.

---

### Post by K.Mandla on 2007-12-08
Mono feels creepy to me. I'd be a fan of losing it. I don't know much about it aside from what I read on Wikipedia, but I just get that dirty feeling like I used to have back when I used Windows. 

:lolflag:

---

### Post by smartboyathome on 2007-12-08
> **garba said:**
> just curious, what do you think about this spec?

[https://wiki.ubuntu.com/No-Mono-by-Default](https://wiki.ubuntu.com/No-Mono-by-Default)

I don't think the reasons for taking mono out are good enough, and let me explain why.

It has NEVER broken a single patent, and the project is very careful about that. I think that this is just an argument by people who want to purge microsoft from Linux.

Mono is not a bad language for the reasons you give. If Microsoft decides to expand on .NET, then let them, and Mono will take over the stuff Microsoft abandoned (thus allowing for compatibility with old programs), and start in on the new stuff. I quote from Mono's FAQ:
> What is the difference between Mono and the .NET Initiative?
The ".NET Initiative" is a somewhat nebulous company-wide effort by Microsoft, one part of which is a cross-platform development framework. Mono is an implementation of the development framework, but not an implementation of anything else related to the .NET Initiative, such as Passport or software-as-a-service.
So you see that Mono is NOT the Mono standard, but the development framework. It also doesn't make a dependancy on a bad competitor unless Novell became a bad competitior, because Mono is not part of Microsoft in any way, the only connection being they develop a framework which Microsoft uses. If it is provided on the desktop CD, more SOFTWARE will be migrating from Windows to Linux, as it will be cheaper to develop.

It will also not take much less space on the CD, 48.6 mbs compressed is not very much compaired to the whole install of a CD (which is around 2 GB).

Overall, this is nonesense. People just want to purge Microsoft from Ubuntu, it sounds like. I **really** think this should be made for Gobuntu instead.

---

### Post by Solver on 2007-12-08
As an alternative perspective, you can say this is just anti-Microsoft sentiment and fearmongering. First, to get it out of the way, Mono hasn't been shown to infringe on any patents so far, and Microsoft hasn't complained, either.

Now, I firmly believe that what's important for the growing popularity of Linux/Ubuntu are primarily practical, not ideological, considerations. If you're talking about getting Ubuntu "on the desktop" and moving average users to it, you have to realize that the average user won't care too much about the ideology behind the software and all that. The average user cares about software quality. Even many Linux geeks care about software quality above the ideological issues.

And that's the important part for Mono. Mono allows the creation of quality software just because .NET/Mono are powerful platforms and fairly easy to code for. I only started really developing something for .NET last year but I was immediately pleasantly surprised to see how much easier it sometimes is than Visual C++ with MFC that I had used before for some applications. This is not to say that all applications should be written for .NET on Windows or Mono on Linux - choosing the right tool and development environment is highly important. But there are applications that are good to develop for these platforms.

---

### Post by fwilliams on 2007-12-08
I do not see why people insist on leaving it in by default.  I am not opposed to people using it, I just do not want it installed by default.

It will always lag behind .NET and there are better cross-platform languages out there.  If people want to code .NET and use .NET then use Windows!

How about silver light?  An application written with .NET being ported to mono that has patented code purchased by Microsoft so it can be included.  Is that OK also?  How many of these mono applications are going to have similar issues?

Please do not include mono by default.

I like Ubuntu very much and would prefer not to find another distribution.

If Ubuntu decides to keep mono, please recommend a Debian based distribution with Gnome.  Thanks.

---

### Post by maniacmusician on 2007-12-08
> **smartboyathome said:**
> I don't think the reasons for taking mono out are good enough, and let me explain why.

It has NEVER broken a single patent, and the project is very careful about that. I think that this is just an argument by people who want to purge microsoft from Linux.

Mono is not a bad language for the reasons you give. If Microsoft decides to expand on .NET, then let them, and Mono will take over the stuff Microsoft abandoned (thus allowing for compatibility with old programs), and start in on the new stuff. I quote from Mono's FAQ:

So you see that Mono is NOT the Mono standard, but the development framework. It also doesn't make a dependancy on a bad competitor unless Novell became a bad competitior, because Mono is not part of Microsoft in any way, the only connection being they develop a framework which Microsoft uses. If it is provided on the desktop CD, more SOFTWARE will be migrating from Windows to Linux, as it will be cheaper to develop.

It will also not take much less space on the CD, 48.6 mbs compressed is not very much compaired to the whole install of a CD (which is around 2 GB).

Overall, this is nonesense. People just want to purge Microsoft from Ubuntu, it sounds like. I **really** think this should be made for Gobuntu instead.
Ditto, good post.

---

### Post by igknighted on 2007-12-08
> **smartboyathome said:**
> I don't think the reasons for taking mono out are good enough, and let me explain why.

It has NEVER broken a single patent, and the project is very careful about that. I think that this is just an argument by people who want to purge microsoft from Linux.

Mono is not a bad language for the reasons you give. If Microsoft decides to expand on .NET, then let them, and Mono will take over the stuff Microsoft abandoned (thus allowing for compatibility with old programs), and start in on the new stuff. I quote from Mono's FAQ:

So you see that Mono is NOT the Mono standard, but the development framework. It also doesn't make a dependancy on a bad competitor unless Novell became a bad competitior, because Mono is not part of Microsoft in any way, the only connection being they develop a framework which Microsoft uses. If it is provided on the desktop CD, more SOFTWARE will be migrating from Windows to Linux, as it will be cheaper to develop.

It will also not take much less space on the CD, 48.6 mbs compressed is not very much compaired to the whole install of a CD (which is around 2 GB).

Overall, this is nonesense. People just want to purge Microsoft from Ubuntu, it sounds like. I **really** think this should be made for Gobuntu instead.

Great points.  I agree with you that this might get railroaded out simply because of an irrational fear/hate of everything related to microsoft.  Microsoft supports mono for pete's sake (moonlight anyone?)!

All that said, I think there are some very reasonable reasons to avoid mono on Ubuntu, and that is the preponderance of apps written in python/GTK.  Everything else in Ubuntu is already python, so to add the mono libraries just for a couple apps may not be the best use of space.  This is assuming you can find a good photo management app to replace fspot (nothing comes to mind).

---

### Post by hanzomon4 on 2007-12-08
I love tomboy and F-Spot.. Not to mention Banshee. But really when did the foss world turn into a bunch of scaredy cats that abandon good software without proof it infringes on anything?

---

### Post by Fonon on 2007-12-08
I think we should keep it by default.  It's not really hurting anyone, and if it allows more programs to be used on linux, that's only good!

---

### Post by Mr. Picklesworth on 2007-12-08
I personally think F-Spot, Tomboy, Banshee and MonoDevelop (as a C IDE) are all awesome, but I would prefer to see them ported over to a language like Python. I'm not against the whole .Net thing, but Mono feels, to me, like quite a waste. Mono is a lot of library for what is and always will be a very small chunk of the applications on the Ubuntu desktop. It's a bit like Java, in that respect, with the catch being that Java still exists as well. If Java finally went away and died (except for playing a role in databases, where it belongs) I would be much happier about Mono.

I do not feel that Mono should be dropped just because it seems scary (really, it isn't that bad, and the MS .Net following can end quite happily at any time), but it strikes me as something that could probably be replaced by another, lighter platform.
It must be wondered why it is that all this great software is written in Mono. Something about this platform is attracting a lot of creativity and solid work, and it isn't just that great IDE.

F-Spot blows gThumb out of the water (don't even mention Picasa...). Zim and Tomboy are really quite different, but if we were to compare the two head-on, I would say Tomboy is a nicer program for more uses because it instantly starts working, and adding a note takes seconds. It can sit quietly in the background, always ready for instant access.

---

### Post by fwilliams on 2007-12-08
I found a solution on a blog that worked like a charm:

sudo apt-get remove mono-common

---

### Post by Serenitude on 2007-12-08
Mono/Silverlight/etc... hasn't been collected on by Microsoft **yet**. This is not to say that it **won't**. Mono and silverlight are both patent encumbered. Neither is "free" in any sense of the word. Anyone remember when MP3 fees were collected, but only after they waited until it had become wide enough in usage?

Reference bug #1. Reference that Linux is not Windows. Many, myself included, use Linux precisely **because **we do not want to use Windows. Why needlessly include patented Windows technology by default? 

de Icaza has recently stated he is being paid by Microsoft to implement Silverlight in Windows. This is not a conspiracy theory, ignorant rambling, or "fear-mongering". These are his own words. Why would you want that in your OS? Mono, moonlight, etc... are only helping MS "IP" FUD have an air of credulity. 

Given this, is there a compelling reason to force-feed it down the throat of the average Ubuntu user, who is likely looking for a Microsoft/Windows free alternative? 

And why would this be a "Gobuntu issue"? As if the desire for a patent, MS IP-free desktop environment became an extremist issue suddenly? By reverse logic, why then not force-feed a qemu image of Vista on average Ubuntu users, demean them as fear-mongers when they raise concern, and relegate the argument to a "Gobuntu issue"?

---

### Post by fwilliams on 2007-12-08
I can see some of you truly love Microsoft.

What about moonlight, should that be included as well.  Novell, Microsoft readying Moonlight.

Posted Sep 7, 2007 3:02 UTC (Fri) by tetromino (subscriber, #33846)
In reply to: what about windows media support? by undefined
Parent article: Microsoft delivers Silverlight 1.0, extends support to Linux

IIRC, Microsoft promised to provide downloadable binary codec plugins (x86 and x86_64 only). The rest of the framework will be done by Novell and under the GPL.

---

### Post by jrusso2 on 2007-12-09
The problem I have with Mono is that its supposed to be cross platform but where is the cross platform apps?

Take for example paint.net which is a really nice .Net open source windows application that would be nice to have on Linux

But why isn't it available when mono is available on Linux?

I have not seen this used to provide cross platform with windows apps.

---

### Post by smartboyathome on 2007-12-09
> **Serenitude said:**
> Mono/Silverlight/etc... hasn't been collected on by Microsoft **yet**. This is not to say that it **won't**. Mono and silverlight are both patent encumbered. Neither is "free" in any sense of the word. Anyone remember when MP3 fees were collected, but only after they waited until it had become wide enough in usage?

Reference bug #1. Reference that Linux is not Windows. Many, myself included, use Linux precisely **because **we do not want to use Windows. Why needlessly include patented Windows technology by default? 

de Icaza has recently stated he is being paid by Microsoft to implement Silverlight in Windows. This is not a conspiracy theory, ignorant rambling, or "fear-mongering". These are his own words. Why would you want that in your OS? Mono, moonlight, etc... are only helping MS "IP" FUD have an air of credulity. 

Given this, is there a compelling reason to force-feed it down the throat of the average Ubuntu user, who is likely looking for a Microsoft/Windows free alternative? 

And why would this be a "Gobuntu issue"? As if the desire for a patent, MS IP-free desktop environment became an extremist issue suddenly? By reverse logic, why then not force-feed a qemu image of Vista on average Ubuntu users, demean them as fear-mongers when they raise concern, and relegate the argument to a "Gobuntu issue"?

Mono won't impliment stuff that is patented by Microsoft (like I said before, they are very careful about that).

Mono isn't FUD, it is a port of a good language to Linux which will help devs port programs to Linux. You want it to grow, don't you?

The average user is not going to be looking for a Microsoft/Windows free alternative, and even if they were the .NET platform (as stated in the previous quote from the Mono FAQ) is a development platform which happens to be used by Microsoft.

Mono isn't ANYTHING like forcing a vista qemu image to new users. New users won't even know it is on there unless they go looking for it, in which case they are LOOKING for something to complain about.

---

### Post by smartboyathome on 2007-12-09
> **jrusso2 said:**
> The problem I have with Mono is that its supposed to be cross platform but where is the cross platform apps?

Take for example paint.net which is a really nice .Net open source windows application that would be nice to have on Linux

But why isn't it available when mono is available on Linux?

I have not seen this used to provide cross platform with windows apps.

Actually, Paint.NET is being developed for Linux, but there are quite a few features which use Windows libraries and need to be reconstructed from scratch in order to work on Linux.

---

### Post by jrusso2 on 2007-12-09
> **smartboyathome said:**
> Actually, Paint.NET is being developed for Linux, but there are quite a few features which use Windows libraries and need to be reconstructed from scratch in order to work on Linux.

Doesn't this go against the whole theory of .NET and Mono being cross platform?

How is that cross platform?

---

### Post by smartboyathome on 2007-12-09
> **jrusso2 said:**
> Doesn't this go against the whole theory of .NET and Mono being cross platform?

How is that cross platform?

It doesn't because the .NET portions of Paint.NET are ported, but the windows-only portions arent (yet).

---

### Post by kurros on 2007-12-09
Looking at [popularity contest votes]("http://popcon.ubuntu.com/by_vote"),

#416 mono-jit
#417 mono-common
#506 f-spot (
#518 mono-runtime
#565 tomboy
#872 beagle
#1282 banshee
#1863 monodevelop

This is out of 66,869 packages, btw. And only measures the users who have opted into popcon.

So your "Assumptions" are invalid.

---

### Post by igknighted on 2007-12-09
> **Serenitude said:**
> Given this, is there a compelling reason to force-feed it down the throat of the average Ubuntu user, who is likely looking for a Microsoft/Windows free alternative? 

And why would this be a "Gobuntu issue"? As if the desire for a patent, MS IP-free desktop environment became an extremist issue suddenly? By reverse logic, why then not force-feed a qemu image of Vista on average Ubuntu users, demean them as fear-mongers when they raise concern, and relegate the argument to a "Gobuntu issue"?

Why not give the users the very best free and open source applications available?  Isn't that really what we want?  Well, in certain cases (tomboy and Fspot), mono/C# apps are the best we have.  So if you don't like it, go build your own.  Not to mention, how is making apps cross-platform bad for linux?  People would be far less afraid of switching if they had familiar apps to use, and having a C# implementation can only help that.

And on the Vista qemu image, I am going to have to put this very politely: <snip>.  Nothing about mono has ANYTHING to do with Vista, or including an image of it.  The only thing you could be hoping to gain is to scare people on to your side with phrases like that... man, you might as well go work in redmond if you like those tactics.  Look at the facts.  Mono is NOT patent encumbered, it is NOT proprietary, and it is a good thing for linux.

Oh, one further point on silverlight/moonlight: Not only did microsoft actually help develop the moonlight plugin for linux (tacitly condoning the existance of both moonlight and mono), but they've done a lot more to make sure silverlight is truely cross platform than its rival adobe has done with flash.  We all hate flash so much, and when a better, more linux friendly alternative comes out we rip it for being made by the wrong company... for shame.

> Looking at popularity contest votes,

#416 mono-jit
#417 mono-common
#506 f-spot (
#518 mono-runtime
#565 tomboy
#872 beagle
#1282 banshee
#1863 monodevelop

This is out of 66,869 packages, btw. And only measures the users who have opted into popcon.

So your "Assumptions" are invalid.

I'm surprised Banshee is that low... it really is an awesome music player.

---

### Post by Mr. Picklesworth on 2007-12-09
Thanks for the statistics, kurros!

People are really overreacting to Mono. It's a free implementation of what is ultimately a Good Idea. Many people that do not believe Mono to be a good idea have probably not attempted to build and run a Mono application from source. Upon doing that, I am sure its usefulness will become clear.
...It's *instant!*. That is why Mono (or, rather, .Net) is considered good at being platform independent. Configuring and compiling can be done on the fly, right on the end user's computer, without significant slowdowns. -- And that is just one of many things that make this an awesome direction to move in.
This is a type of functionality we usually only see in Python or Java, which are usually slow interpreted languages. Especially Java, on that latter point.

As for wanting to never have Mono touch your computer, I have to say I consider that sentiment rather crazy. Restricted file formats I can understand, but Mono is by no means illegal and has as much a right to exist as Python or Java. A lot of effort has been put in to the project, and, like it or not, it has resulted in a lot of momentum.
I could say the same ills about Java. I think OpenOffice should be dropped from the default install because of its dependency on Java. Takes up a lot of memory and storage space, ultimately achieves nothing more than we get from Mono (for desktop applications). In addition, Sun seems to keep Java very close to their own chest, which is a behaviour that reminds me of none other than Microsoft and .Net.
Finally, Java has yet to deliver any particularly great desktop applications. Even now, with thousands of desktop applications written in Java, there is surprisingly little (particularly in Ubuntu's default install) that makes the Java runtime a must-have for desktop users. Just about the best use it has for the end user here is web plugins, and those tend to feel dated as well, since good AJAX design is successfully blowing it out of the water in a much more integrated and cross-platform manner.

Flash, as has been mentioned, can be nicely easily compared to .Net and Mono. I guess the difference is that Flash is not included by default, but how about Gnash? Gnash is an implementation of Flash, much like Mono is an implementation of .Net (with the major difference being that Flash is, and always has been, a terrible idea that nobody should care about anyway). Shouldn't we be worried of evil Adobe chasing us down for using Gnash?

---

### Post by fwilliams on 2007-12-09
C# is just Microsoft's version of Java.  I am glad there are so many people using it, we just do not want it included in the base Ubuntu build.  Start a distro called MSbuntu, but please get it out of Ubuntu.

That way all the people clamoring to get away from Microsoft, just so they can use Microsoft can use MSbuntu.

Or maybe these developers should try using a cross-platform language, instead of something that will always lag behind and need extensive modification to work on Linux, like paint.net.

---

### Post by fwilliams on 2007-12-09
Almost forgot, we will have to follow Microsofts rules as well.  But that should not concern anyone.

From Miguel's blog:

[B]Microsoft will make the codecs for video and audio available to users of Moonlight from their web site. The codecs will be binary codecs, and they will only be licensed for use with Moonlight on a web browser (sorry, those are the rules for the Media codecs[1])

The binary codecs will initially support x86 and x86-64, with other platforms supported on an as-needed basis.
[/B]


I hope Microsoft will continue providing up to date specifications, otherwise people would to possibly switch to a different OS so they can run the applications they became dependent on.  Also from the blog:

[B]Microsoft will give us access to the Silverlight specifications: details that might be necessary to implement 1.0, beyond what is currently published on the web; and specifications on the 1.1 version of Silverlight as it is updated.

Microsoft benefits by making Silverlight reach the Linux and BSD spaces.[/B]

---

### Post by Serenitude on 2007-12-09
<snip>

> **"igknighted"]Nothing about mono has ANYTHING to do with Vista,[/quote]

Maybe, just maybe, if you parse your definition carefully enough, you are correct. However, even then, I was not referring to Vista in particular  said:**
> or including an image of it.  The only thing you could be hoping to gain is to scare people on to your side with phrases like that... 

I was using the absurd extreme as an example. <snip>

> **"igknighted"]man, you might as well go work in redmond if you like those tactics.[/quote]

Says the person defending Microsoft in Ubuntu  said:**
> it is NOT proprietary,

Quite true. The tech it trojan horses into Linux is proprietary, however. Oh, outside of the nice RAND "covenant" that says "We probably won't sue. Maybe."

[quote="igknighted"]and it is a good thing for linux.[/quote]

Yes, if you like your Linux mixed with Microsoft tech, it is a very good thing for GNU/Linux. Horrible for FLOSS. Go figure.

[quote="igknighted"]Oh, one further point on silverlight/moonlight: Not only did microsoft actually help develop the moonlight plugin for linux (tacitly condoning the existance of both moonlight and mono), but they've done a lot more to make sure silverlight is truely cross platform than its rival adobe has done with flash.  We all hate flash so much, and when a better, more linux friendly alternative comes out we rip it for being made by the wrong company... for shame.[/quote]

Microsoft is funding the implementation of silverlight into Linux. A good or bad thing, depending on your point of view. However, you are mistaken. Microsoft did NOT develop the moonlight plugin. Novell is doing that. Have your facts straight, <snip> ;-) And can you give me a reason why having unneeded MS tech cross-platform is a good thing?


To the rest in general, I'm sorry for the tone of this post. I'm responding to one individual, and not the consensus of the other side. <snip>

---

### Post by fwilliams on 2007-12-09
Seems like igknighted is just a Microsoft fanboy.  Oh, well every forum should have at least one.

---

### Post by dbera on 2007-12-09
> **Serenitude said:**
> 
Do I REALLY have to produce the copious and easily available amounts of evidence that even Google can produce quickly on this one? Are you really actually going to press this issue?

I loose to my pals everytime I try to take this route without any evidence ... so, if anyone has any evidence that Mono has violated MS patents or MS IP, then please share or drop me a personal note. As you guessed, the links I get from Google are either FUDs (without actual evidence) from Linux users or FUDs (again without evidence) from MS executive (usually Balmer) - it feels very similar to the SCO FUD that it owns Linux ... claims without any actual evidence that I can use to win bets (free beer actually) against my pals :)

Thanks in advanc ;-)

---

### Post by Mateo on 2007-12-09
> **Solver said:**
> As an alternative perspective, you can say this is just anti-Microsoft sentiment and fearmongering. First, to get it out of the way, Mono hasn't been shown to infringe on any patents so far, and Microsoft hasn't complained, either.

Now, I firmly believe that what's important for the growing popularity of Linux/Ubuntu are primarily practical, not ideological, considerations. If you're talking about getting Ubuntu "on the desktop" and moving average users to it, you have to realize that the average user won't care too much about the ideology behind the software and all that. The average user cares about software quality. Even many Linux geeks care about software quality above the ideological issues.

And that's the important part for Mono. Mono allows the creation of quality software just because .NET/Mono are powerful platforms and fairly easy to code for. I only started really developing something for .NET last year but I was immediately pleasantly surprised to see how much easier it sometimes is than Visual C++ with MFC that I had used before for some applications. This is not to say that all applications should be written for .NET on Windows or Mono on Linux - choosing the right tool and development environment is highly important. But there are applications that are good to develop for these platforms.

Good post, most PC users are not religious fundamentalists and those are the people who should be pampered to.  Also, to what someone else said, there are no good alternatives to FSpot, at least not for Gnome.

---

### Post by fwilliams on 2007-12-09
What would this mean:

From [http://www.linux-watch.com/news/NS2927608517.html:](http://www.linux-watch.com/news/NS2927608517.html:)

"Under the patent agreement, customers will receive coverage for Mono, Samba, and OpenOffice, as well as .NET and Windows Server."

---

### Post by bapoumba on 2007-12-09
I've edited a couple posts in this thread. Please keep the personal attacks out of the way, thanks.

---

### Post by fwilliams on 2007-12-09
Whether or not Microsoft actual specifies a patent, they may continue to infer patents are being infringed.
 
Mono is chasing .NET, it will always be chasing .NET, which means that new features, functionality and programs will also be lagging those that run on Microsoft's OS.

As I stated before I do not mind if people use it, I just do not want it installed by default.

According to Jeff Waugh Gnome is not currently dependent on Mono except for libbeagle which is written in 100% C.

I was able to remove mono-common using apt-get without any adverse side effects.

Other collaborations between Microsoft and Novell are bringing a Flash like utility to Linux.  It contains binary codecs from Microsoft with the stipulation that those codecs can only be used by a browser.

From Miguel's blog:

"Microsoft will make the codecs for video and audio available to users of Moonlight from their web site. The codecs will be binary codecs, and they will only be licensed for use with Moonlight on a web browser (sorry, those are the rules for the Media codecs[1])"

"The binary codecs will initially support x86 and x86-64, with other platforms supported on an as-needed basis."

I hope Microsoft will continue providing up to date specifications, otherwise people would to possibly switch to a different OS so they can run the applications they became dependent on. Also from the blog:

"Microsoft will give us access to the Silverlight specifications: details that might be necessary to implement 1.0, beyond what is currently published on the web; and specifications on the 1.1 version of Silverlight as it is updated."

"Microsoft benefits by making Silverlight reach the Linux and BSD spaces."

---

### Post by smartboyathome on 2007-12-09
> **fwilliams said:**
> C# is just Microsoft's version of Java.  I am glad there are so many people using it, we just do not want it included in the base Ubuntu build.  Start a distro called MSbuntu, but please get it out of Ubuntu.

That way all the people clamoring to get away from Microsoft, just so they can use Microsoft can use MSbuntu.

Or maybe these developers should try using a cross-platform language, instead of something that will always lag behind and need extensive modification to work on Linux, like paint.net.

You act like everyone who switches to Linux doesn't want to do anything with Microsoft and hates them with a passion. Not all of them do, though, and those that do probably have the ability to get rid of it themselves.

Seriously, just because Microsoft uses it, it is evil? Why don't we just get rid of window lists, Compiz Fusion because of it's vista-like effects, and menus for that matter, as Microsoft uses *them*?

---

### Post by Fonon on 2007-12-09
Just because Microsoft has it, doesn't mean its automatically bad.  .NET is a very good framework to code for, and some of its applications are really good (paint.NET, anyone?).  Seeing as you can remove it at anytime, and the common user might like the applications Mono brings without knowing its Mono, it shoudl stay.

Or, better yet, make two install CDs - one with mono, and one without mono.

---

### Post by smartboyathome on 2007-12-09
> **Fonon said:**
> Just because Microsoft has it, doesn't mean its automatically bad.  .NET is a very good framework to code for, and some of its applications are really good (paint.NET, anyone?).  Seeing as you can remove it at anytime, and the common user might like the applications Mono brings without knowing its Mono, it shoudl stay.

Or, better yet, make two install CDs - one with mono, and one without mono.

Making two install CDs would probably have to be the last thing we would want to do.

I would say making mono easier to remove would be better.

---

### Post by Fonon on 2007-12-09
Perhaps there could be an option in the installation?  Like, before you hit "install" there could be a checkbox called "install mono?".

---

### Post by popch on 2007-12-09
> **smartboyathome said:**
> Making two install CDs would probably have to be the last thing we would want to do.

Call one ***Ubuntu mono*** and the other one ***Ubuntu stereo***?

---

### Post by Kernel Sanders on 2007-12-09
I get the impression that most of this "anti mono" crap is more "anti microsoft" crap than anything else.

The only reason for excluding it is for that very reason. It doesn't hurt in the slightest, and in fact has some very clear positives.

---

### Post by ruibernardo on 2007-12-09
I just use mono with Tomboy, which I find very useful. Tomboy comes installed with Ubuntu Desktop by default since Edgy. , I think that's why mono is installed.

Like I said, I find tomboy very useful and I like it. If tomboy was removed now and an alternative program was used, in the next release of Ubuntu, a sort of import procedure would be needed to import my actual notes from tomboy to that new program, if any is like tomboy...

Since mono is GNU/GPL and is multiplatform, it's good to have it, more compatibility with other systems. It wouldn't be the case if it was useless or no projects used it, but it is supported by Novell and is becoming [more important and with more projects]("http://www.mono-project.com/news/index.html") as time passes.

If mono can be removed without much trouble why should mono be removed by default?

-1 for mono removal.

---

### Post by igknighted on 2007-12-09
> **Serenitude said:**
> Says the person defending Microsoft in Ubuntu ;-) I'd like my life and computing experience Redmond free, thank you.

Quite to the contrary, I am defending an excellent open source project while you are fear-mongering because there is a tie to microsoft.  I disagree with absolutely everything else in your post as well, but for the sake of keeping this thread alive and in positive discussion I am not going to respond.

---

### Post by Mr. Picklesworth on 2007-12-09
> I would say making mono easier to remove would be betterHow would that be, and, further, why? It would not be user friendly to place a library in gnome-app-install's list of things, since that application has done well only listing programs that matter to the end user. In addition, since dependencies would cause the disappearance of any mono-reliant applications, having it there would likely not work, anyway, and even if it did, it would cause a lot of trouble.
In general, the people who care about this matter know quite well how to open Synaptic Package Manager, search by name for "mono" and remove the packages.

> Perhaps there could be an option in the installation? Like, before you hit "install" there could be a checkbox called "install mono?".Potentially, in a vaccuum, a sound suggestion. However, if these types of suggestions ("just add an option!") were taken into account as often as they are mentioned, Ubuntu's installer would be looking worse than KDE, with enough options to confuse and terrify everyone.
*Nobody* wants software that needs their guidance to work properly. They would rather it just works for them, how they 'probably' want it (which software can be surprisingly successful at guessing, when it tries), without any need to fuss over buttons and dials. Having even that single option in the installer would look very out of place and be extremely confusing for anyone who does not know what "mono" is other than a physical disease or the bad kind of sound output, prompting them to uncheck it. That type of form would damage the thing's usability and chase away potential new users who are still under the belief that Linux is too technical for them.


Speaking of Microsoft chasing, Mono is always free for splitting. While I somewhat agree to this being a great platform, I also agree that chasing Microsoft is very silly -- particularly considering their legacy of drunken software design. Nicely, a new, superior project can be broken away without the Microsoft ties, and it could even maintain compatibility until people start to see the light...

---

### Post by Mateo on 2007-12-09
Anyone who's a big enough tech guru to have some philosophical problem with mono probably doesn't have a problem doing a simple "apt-get remove mono".

---

### Post by fwilliams on 2007-12-09
Mono will always LAG, this is not an anti Microsoft reason.

Embrace, extend and extinguish is.  I have been using Microsoft for 26 Years and am still using it for some legacy applications.

Try not to tie it to closely to gnome in case in the future you realize it is not needed.

---

### Post by Serenitude on 2007-12-09
I'm not against people using Mono if they choose - that's what I love about Open Source AND Free Software (two different things). 

However, I am against having to use it, as it is obviously a hot-button topic for good reason, when I don't want to. 

I would be willing to bet that, all things explained, alot of new Ubuntu users would rather not use it as well. 

"Simply" anti-Microsoft? Well, many of us found GNU/Linux after tiring of MS practices, too numerous to list here. So, naturally, we'd rather not have MS Linux. I don't want to bash them. I want to be done with them.

I've completely stripped Mono and glade without any adverse system effects. Had to remove Tomboy, which I never used (I don't use notepads in general, not just Tomboy in specific), but that's it. 

So, an alternate question to why, then, has become, as the OP stated, why not?

---

### Post by tageiru on 2007-12-09
> **Serenitude said:**
> I've completely stripped Mono and glade without any adverse system effects.

What's wrong with glade?

---

### Post by blastus on 2007-12-09
I guess the questions are...

1. Is GNOME dependent on Mono right now and to what extent is it dependent on Mono?

2. If GNOME is dependent on Mono, does this dependency include Windows-specific technology such as ADO.NET, ASP.NET, and Windows.Forms where the right to freely use the covering patents has not been granted?

3. What's the contingency plan if and when Microsoft decides that Mono violates its IP? What if Microsoft someday decides that Mono has grown bad for their business and finds a way--through some obscure legal or patent loophole somewhere--to revoke the grant to implement the core .NET framework on Linux?

.NET is Microsoft's core strategy for Windows. It would be stupid not to realize that they do not want the .NET framework to be truly cross-platform with Linux as that would reduce dependency on Windows. It would be extremely ignorant not to realize that there are valid patent concerns here about Mono's development.

---

### Post by bobbocanfly on 2007-12-09
Im pretty sure GNOME (The core DE) is not dependent on Mono. I ran 'sudo apt-get remove libmono*' and GNOME is still running fine. Mono hasnt exactly been widely adopted.

---

### Post by smartboyathome on 2007-12-09
> **blastus said:**
> 1. Is GNOME dependent on Mono right now and to what extent is it dependent on Mono?

No, Mono is not GNOME dependant, though it was during GNOME 2.16.

> **blastus said:**
> 2. If GNOME is dependent on Mono, does this dependency include Windows-specific technology such as ADO.NET, ASP.NET, and Windows.Forms where the right to freely use the covering patents has not been granted?

No. Mono does not include patented items in it's implimentation of the .NET framework.

> **blastus said:**
> 3. What's the contingency plan if and when Microsoft decides that Mono violates its IP? What if Microsoft someday decides that Mono has grown bad for their business and finds a way--through some obscure legal or patent loophole somewhere--to revoke the grant to implement the core .NET framework on Linux?

Mono has been very careful, and Microsoft will have to look hard to find a patent infringement for Mono. What if Microsoft decides to come after Linux for including the double-click as an option? They have the right to do that since THEY patented it.

> **blastus said:**
> .NET is Microsoft's core strategy for Windows. It would be stupid not to realize that they do not want the .NET framework to be truly cross-platform with Linux as that would reduce dependency on Windows. It would be extremely ignorant not to realize that there are valid patent concerns here about Mono's development.

Such as? I haven't seen any patents it infringes on yet. I think that people are worried that it may SOME DAY infringe on patents.

---

### Post by fwilliams on 2007-12-09
So, it seems to be settled.

Gnome should not become dependent on Mono, but Mono should be left there for certain applications.

This would allow the tech savvy to do an "sudo apt-get remove mono-common" which also removes Tomboy and F-spot.

While allowing the C# programmers to help write applications for Linux.

That way everybody wins.

No need to thank me, just trying to do my small part for humanity.

---

### Post by original_jamingrit on 2007-12-09
I've been reading the mono faqs ([general]("http://www.mono-project.com/FAQ") and [licensing]("http://www.mono-project.com/FAQ:_Licensing")) , there's nothing to indicate that they use anything but non-proprietary stuff.  The only licenses involved are the GPL, the LGPL(for runtime libraries), and the MIT X11 license, all of which are open source.

Mono implements both the .NET framework as well as some other stuff that is not related to microsoft at all.  All of it is legitimately open source.

RTFM, stop spreading FUD.

That being said, I do also agree with the modularity of being able to remove mono if you'd like.  Just... don't uninstall it for the wrong reasons, that's when things just get silly.

---

### Post by emperon on 2007-12-10
Stop spreading FUD. Learn the facts.** C# and Core library of .NET framework is not a property of Microsoft**. The only patented technologies are Windows Forms , ASP.NET and ADO.NET. You can definitely develop applications without those. And as long as you don't use these you are 100% safe.
And finally Mono is Open Source , Java is NOT (Java 7 has not been released which will then later be named Open Java or Open JDK and sun will also promote its own Java version )

taken from : [http://www.mono-project.com/FAQ:_Licensing](http://www.mono-project.com/FAQ:_Licensing)
[SIZE=4]**Could patents be used to completely disable Mono?**[/SIZE]

First some background information.

The .NET Framework is divided in two parts: the ECMA/ISO covered technologies and the other technologies developed on top of it like ADO.NET, ASP.NET and Windows.Forms.

Mono implements the ECMA/ISO covered parts, as well as being a project that aims to implement the higher level blocks like ASP.NET, ADO.NET and Windows.Forms.

The Mono project has gone beyond both of those components and has developed and integrated third party class libraries, the most important being: Debugging APIs, integration with the Gnome platform (Accessibility, Pango rendering, Gdk/Gtk, Glade, GnomeUI), Mozilla, OpenGL, extensive database support (Microsoft only supports a couple of providers out of the box, while Mono has support for 11 different providers), our POSIX integration libraries and finally the embedded API (used to add scripting to applications and host the CLI, or for example as an embedded runtime in Apache).

The core of the .NET Framework, and what has been patented by Microsoft falls under the ECMA/ISO submission. Jim Miller at Microsoft has made a statement on the patents covering ISO/ECMA, (he is one of the inventors listed in the patent): here ([http://web.archive.org/web/200304241.../msg00218.html](http://web.archive.org/web/200304241.../msg00218.html))

Basically a grant is given to anyone who want to implement those components for free and for any purpose.

For people who need full compatibility with the Windows platform, Mono's strategy for dealing with any potential issues that might arise with ASP.NET, ADO.NET or Windows.Forms is: (1) work around the patent by using a different implementation technique that retains the API, but changes the mechanism; if that is not possible, we would (2) remove the pieces of code that were covered by those patents, and also (3) find prior art that would render the patent useless.

Not providing a patented capability would weaken the interoperability, but it would still provide the free software / open source software community with good development tools, which is the primary reason for developing Mono.

The patents do not apply in countries where software patents are not allowed.

For Linux server and desktop development, we only need the ECMA components, and things that we have developed (like Gtk#) or Apache integration.
With the new Novell/Microsoft agreement, will the patent policy change?

Mono is a community project, and as such, we will continue to implement the policy of not integrating knowingly infringing code into Mono.

And we will continue to follow the steps outlined in the previous topic if code that potentially infringes is found: finding prior art, finding different implementation techniques, or if none of those are possible, removing the code from Mono.

---------------------------------------------------------------------------------------
Programming languages are tools. And they give us some abstraction level. I would classify :

Language....................... Abstraction Level

Machine Lang........................ 0
Assembly.............................. 1
C/C++ ................................... 2
Java/C# .................................3
Python, Ruby .........................4
LISP ...................................infinity

We choose a language according the to task and level of abstraction we require. Writing an operating system with LISP is pointless where as, writing an ERP with assembly is pointless as well.

Most Projects fall into the category between level 4 and 3. The main difference between level 4 and 3 is about statically typing or dynamic typing.

With statically typed languages you have compiler as a cop , that checks your code for preliminary compile time mistakes. This is more useful when the project is very large and iti hard to maintain and/or the developers are novice.

With dynamic languages, the language gives the developer more power (at the cost of Performance) , so it is more suitable for when developers are smarter and/or Project is not very large to maintain.

What .NET brings table, this is highly personal. Mono (and not .NET) is the best of the best of all development environments FOR ME. because of the following reasons:

[SIZE=4]**Why use Mono at all ?**[/SIZE]

**1-)** You have bunch of languages with dynamic and static typing that can interop: C#, VB.NET(it sucks I know), Boo (a statically typed language allowing dynamic typing), IronPyton, IronRuby(alpha available),Ruby.NET (Beta availbale), F# (first class functional language) and a lot of less popular ones like nemerle, lispdotnet, prolog.net...

**2-)** .NET framework is available in windows and gnome by default. Have you ever tried to deliver a python application to your customer who knows nothing about computers ? You cannot instruct them to install python easily. Even if you can sometimes deployment of 1000 computers are problematic. Most XP and all Vista computers already has .NET framework so it is easier to deploy cross platform applications

**3-)** java is the most popular language now according to TIOBE index: [http://www.tiobe.com/tpci.htm](http://www.tiobe.com/tpci.htm) But popularity does not make a language good (For eg. VB). Although .NET especially c# is highly inspired of java ( the reason C# was born because sun sued Microsoft for Visual J++), for many years, Sun's over protective behavior of java, damaged java community a lot. If you check the bug list of java you will see there are 3 - 4 years standing bugs. GUI development with java sucks.Although Sun recenlty Open sourced java recently , as everything Sun did so far, it is too little and too late. Java is destined to go where PHP and Cobol lies now

**4-)** Web Development with mono is breeze. What other choices we have ?
Java based framworks (look at item 3), PHP (is already dead), Ruby on Rails (this is a very nice framework but sorry not suitable for large applications, No unicode, no multithreading), Pythonic Frameworks like Django and Turbo Gears, these are also very nice but they are even worse than RoR. Still very nice for small to medium web development

5-) .NET library is large. Python library is also large, and available C librarires are huge. But with .NET you got all in one
** [Cross Platformity]**
6-) You've got the power of frameworks written for windows, like nhibernate, spring.net, db4o, nunit, Rhno mocks, Reflector

7-) You've got the power of Java frameworks via IKVM. IKVM is a Java VM which can run on mono

Although it is Alpha, we've got Silverlight/moonlight: [http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight)


Note that I am not claiming Mono is better than Python.
These are my opinions what for Mono brings to the table

[SIZE=4]**Does Mono Really Lag Behind .NET ?**[/Size]

Currently MS Released .NET 3.5 let's compare how much mono lags:

**Lastest Version of C# 3.0**: Fully Supported by Mono (LINQ is in Beta Stage)

**.NET 3.0 Additions (WPF , WF, WCF):** Available on Mono Olive

**ASP.NET:** Including ASP.NET AJAX and AJAX Control Toolkit and ASP.NET Futures it is fully working. Missing parts are: WebParts, 2 New Controls Coming with ASP.NET 3.5

**Windows Forms :** Windows Forms 1.1 is complete. Windows Forms 2.0 is mostly complete. Yes! Windows forms applications are cross platfrom too!

**ADO.NET** : %99.9 complete


__________________

---

### Post by igknighted on 2007-12-10
thank you emperon, that was a great post.

---

### Post by Bruce M. on 2007-12-10
Not being a programmer, I have no comment!

However!

Last week I bought a Linux magazine and with it came:

Mono LiveCD - Monoppix 1.1.8.0

Anyone want it?

First person to send me a private message asking for it, gets it.

I will come back and edit this post when, or if, it goes!

---

### Post by Erunno on 2007-12-10
> **emperon said:**
> For people who need full compatibility with the Windows platform, Mono's strategy for dealing with any potential issues that might arise with ASP.NET, ADO.NET or Windows.Forms is: (1) work around the patent by using a different implementation technique that retains the API, but changes the mechanism; if that is not possible, we would (2) remove the pieces of code that were covered by those patents, and also (3) find prior art that would render the patent useless

It is my understanding that (1) falls more into the category of copyright. I don't think patents can be circumvented by changing the implementation details. Also, if ASP.NET, ADO.NET and Windows.Forms were to be removed due to some legal pressure from Microsoft Mono would simply die as a cross-platform platform .NET implementation as Microsoft's own implementation is the standard against all other implementations will be measured due to the extremely high market share. Although I reckon it would affect it less as a platform for non-Windows development. (3) makes the impression of betting to me and not very assuring because it is probably accompanied by years of processing against Microsoft.

---

### Post by Mateo on 2007-12-10
Good post emperon.

The one bad thing about mono/C# is that it's a resource hog.  Tomboy is a note-taking application and takes up about 10-15 megabytes of ram.  That's more than Evolution, a full-featured mail and PIM client.

I'm not a very good programmer, but it seems if you can program in c# then you're only a small step from being able to program in c or c++ so you might as well go there.

The one advantage to C# is that it is used a lot in the corporate world so if you want to get paid, it's good to know.

---

### Post by SuperMike on 2007-12-10
I agree. Mono can stuff it.

---

### Post by samjh on 2007-12-10
While Mono is a good project, I'd rather Ubuntu not become dependent on it.  It already is dependent, but only a few packages actually make use of it, with almost all of those dependent packages having completely FOSS alternatives.

Some people here have suggested that Mono doesn't include patented items.  This is quite misleading.  The Mono project includes Windows Forms, ADO.NET, and ASP.NET, among other copyrighted and patent-encumbered technologies.  Mono's libraries in the System namespace are safe, but those other libraries which are not part of the CLI and C# standards are NOT SAFE.

Yes, the Mono project tries very hard to avoid patent problems.  But when you're implementing identical technologies as IP-protected products of another vendor, you're bound to hit snags.

Then there is the issue of Ubuntu's #1 bug.  Take a look at it in the Launchpad, and you'll see that Ubuntu's aim is to defeat Microsoft's domination on the desktop.  How we'll do that by promoting a pretender to Microsoft's best development platform is beyond me.  This isn't blind MS-bashing, but a cold, hard look at the long-term consequences of becoming dependant on a platform that essentially tries to mimic Ubuntu's chief competitor.

In summary:

For Mono:
- Technically good
- Developed with good intentions
- Benefits Linux by enhancing interoperability with .NET

Against Mono:
- Not free from risk of patent action
- Unnecessary for use cases currently covered by dependent applications
- Related to previous point, adds unnecessary bloat to default Ubuntu installation
- Defeats Ubuntu Bug # 1

---

### Post by igknighted on 2007-12-10
> **samjh said:**
> While Mono is a good project, I'd rather Ubuntu not become dependent on it.  It already is dependent, but only a few packages actually make use of it, with almost all of those dependent packages having completely FOSS alternatives.

Mono is FOSS, go to their site and download the code.

> **samjh said:**
> Then there is the issue of Ubuntu's #1 bug.  Take a look at it in the Launchpad, and you'll see that Ubuntu's aim is to defeat Microsoft's domination on the desktop.  How we'll do that by promoting a pretender to Microsoft's best development platform is beyond me.  This isn't blind MS-bashing, but a cold, hard look at the long-term consequences of becoming dependent on a platform that essentially tries to mimic Ubuntu's chief competitor.

Who said anything about dependance?  Just because we use a couple apps that happen to be the best at their job doesn't make us "dependent".  We're simply using the best software available.  If you choose you can change whatever software you like,  Think of the many that object to using Firefox as default, or OO.o when there are lighter and in some cases better choices.  Or why is ekiga there?  Who actually uses that?  The fact of the matter is something happens to be default.  If the majority feels that fspot and tomboy are the best apps available for the job, there's nothing wrong with using them, and we are in no way becoming "dependent".

EDIT: And I don't think it strenthens microsoft's grip, if anything it weakens it.  Think about it.  If people can use familiar apps they will be more likely to switch.  And microsoft doesn't make money because you use .net, they get money because you had to buy windows to use ,net.  Having an open-source implementation allows .net programmers to NOT be trapped into using windows, how is that a bad thing?

---

### Post by Polygon on 2007-12-10
i say keep it in. I live by tomboy, and a few other apps i use (handbrakegtk) require mono, so i say just leave it in by default. This is ubuntu, meant for the masses. Most people dont give a care about 'the legalities of mono in the future'. Its FOSS now, and thats all that matters.

---

### Post by fwilliams on 2007-12-10
To the few people who  tried discourage the use of mono.  Shame on you.  It is better to let them poke them self in the eye with a pointed stick, instead of telling them it may hurt.

---

### Post by Serenitude on 2007-12-11
From the official Liscensing FAQ, as posted. Forgive me if I mentioned patent when I should have simply mentioned ownership, or copyright, etc... IANAL.

Anyhoo, the quotes:

"...as well as being a project that aims to implement the higher level blocks like ASP.NET, ADO.NET and Windows.Forms."

"The core of the .NET Framework, and what has been patented by Microsoft falls under the ECMA/ISO submission."

(My note - remember that ECMA submission does not make it legal ;-) )

"Basically a grant is given to anyone who want to implement those components for free and for any purpose."

(My note - why the RAND if the "IP" issue of Mono is just FUD? And the RAND doesn't guarantee you much if you read it carefully.)

"...and also (3) find prior art that would render the patent useless."

(My note - why this line? Aren't there people who are accusing those of us who don't like Mono of today's catchphrase, FUD? Why a strategy to deal with patents if there ARE not patents?)

"The patents do not apply in countries where software patents are not allowed."

(My note - wait. People here are rudely stating "RTFM - there are no patents!" And then quoting this page. It looks like someone may have forgotten to tell the Mono project this. The best information says there ARE patents, but that Microsoft has issued a completely non-binding "pledge" not to sue...)

I think the people who knee-jerk with the answers of "Stop spreading FUD!" (today's answer to any position you don't agree with), or "RTFM!", should take a step back and realize the issue is more complicated than "It's all safe and everyone can use it without worry".

That said, I am not against it's existance. I am merely against it's conclusion by default ;)

---

### Post by Mr. Picklesworth on 2007-12-11
> **samjh said:**
> While Mono is a good project, I'd rather Ubuntu not become dependent on it.  It already is dependent, but only a few packages actually make use of it, with almost all of those dependent packages having completely FOSS alternatives.I can assure you, Tomboy and F-Spot are both free and open source. Try "apt-get source f-spot", for example. It's as open as open source needs to be. By claiming that those programs are not freely available and open, you are denying the hard work and generosity of a lot of people.

> **samjh said:**
> Some people here have suggested that Mono doesn't include patented items.  This is quite misleading.  The Mono project includes Windows Forms, ADO.NET, and ASP.NET, among other copyrighted and patent-encumbered technologies.  Mono's libraries in the System namespace are safe, but those other libraries which are not part of the CLI and C# standards are NOT SAFE.By this logic, one could say the same of any Linux distro the moment it is used to access a patent-encumbered web site. Actually, he should throw his computer out the window as soon as a non-free program is installed, since it has once accessed that bit of information!
In other words, Mono (and, therefore, Mono software) is not *always using* Windows forms or ASP.NET; it only uses them when you use a program that uses them. It is up to the program itself to use or not use those libraries. I have yet to encounter any program in Ubuntu that does. Even then, accessing the libraries is permitted quite happily by their licenses and does not break the freeness of the program using them.

Okay, I agree, there is some worry about Microsoft and their crazy patents. However, you guys should really be debating the existence of "more than 228" other chunks of code that are likely included by default, which are not just in fear of being attacked, but *have* (almost) been attacked.

On the topic of bloat, as emperon quite nicely put it, if people are going to be bothered by any software platform over here it should be Java, which is not only a less powerful platform than Mono, but also *not even trying* to be free.

As for Mono being a bit of a resource hog at the moment, I agree. It will be cool when the Mono contributors stop having to dodge FUD every five minutes (I honestly don't know how they put up with it) and start getting some constructive interest from those who want it to be more efficient.
Just because it's a bit clunky today does not mean that it's doomed to that fate!

---

### Post by fwilliams on 2007-12-11
Leave mono where it is.

Avoid making Gnome or KDE dependent on it

Jeff Waugh said Gnome is not currently dependent on it.

Pretty simple, the people who want to use it can use it.

The people who do not, can "sudo apt-get remove mono-common" and safely clean there system.

---

### Post by phrostbyte on 2007-12-11
I would like Mono to go byebye and be replaced by IcedTea as the RAD environment of choice. Mono is basically like a Wine, it really shouldn't be included by default.

Perhaps someone can make a distro like Slax "Kill Bill" Edition that includes Wine/Mono by default or what not.

---

### Post by tehkain on 2007-12-11
'Mono/.NET success is not beneficial for free software'

Could you be anymore wrong? I am not sure. A free implementation of almost any platform is massive win for free software. What about Gnash? When it becomes usable should it be shelved? A portion of C# is atleast an ISO standard while flash is entirely not. The worse thing we can do is target mono because of microsoft while not holding others to these same standards. 

I support the removal of Mono from the ubuntu base install for technical reasons but I agree with stallman about supporting this free implementation of the platform. The LiveCD should gain another 100mb worth of room during hardy with the removal of winfoss. I support the removal of mono if we can replace tomboy and fspot with software with a __near equal__ feature set and quality. This will save some room on the disk allowing us to included another set of features.

I do agree that patent risk exist but any large program or implementations infringes on a large number of patents that belong to people far more evil minded then microsoft(see patent trolls). I for one thank those who have created and use mono because it allows the possibility of many more corporate desktop users to move to our platform. This is essential to bringing the home user to free software.

---

### Post by igknighted on 2007-12-11
> **phrostbyte said:**
> I would like Mono to go byebye and be replaced by IcedTea as the RAD environment of choice. Mono is basically like a Wine, it really shouldn't be included by default.

Perhaps someone can make a distro like Slax "Kill Bill" Edition that includes Wine/Mono by default or what not.

Actually, mono is almost exactly the same situation as Icedtea... and open-source implementation of a proprietary environment that implements everything it can, but falls short in some areas.  Even when java is "fully open sourced", Sun will continue to distribute a proprietary version with additional features.

EDIT: As far as patent risk is concerned, I think OO.o is far riskier with its implementation of MS-Office file formats and almost identical look & feel.  Microsoft has been making thinly veiled threats about this and no one is jumping to remove OO.o, so why should we be so frightened about mono?  As I said before, mono only boosts open source software.  Instead of trapping .net programmers on windows, it lets them use linux as well.  it also brings people's familiar apps to linux, making the transition easier.  I 100% agree that we cannot become dependant on it, but I do not see that becoming the case.

As for default inclusion in Ubuntu, I think it comes down to apps and space.  I think sticky notes could replace tomboy (not as feature-rich, but usable), but what replaces f-spot?  The only real linux alternatives I am aware of are Picasa (proprietary, cannot be included) and DigiKam (KDE app - KDE libraries would take up far more space than the mono ones, yes?  Plus f-spot is in Gtk#, while digikam would be qt and therefor not look natural).  So as long as these are the only options for photo organization, I think you have to leave mono.  Unless you want to remove that tool from Ubuntu completely.

---

### Post by fwilliams on 2007-12-11
From an article off of Linux Today, by Bruce Byfield:

# DotGNU:
GNU/Linux already has a partial implementation of Microsofts .NET (AKA C#) language in the Mono Project. However, many people in free software are concerned that Mono could face patent attacks from Microsoft. Just as importantly, some view Mono with suspicion, especially since it is sponsored by Novell, Microsoft's chief partner in the community. DotGNU is an effort to provide a technical and political alternative.

DO YOU GET IT YET!  IT SHOULD NOT BE INCLUDED BY DEFAULT!

---

### Post by JohnPhys on 2007-12-11
I support the "no mono by default" idea.  

While I understand the position many are taking in the thread, that including Mono by default should be ok because Mono has not yet been shown to infringe on any patents, and that the developers are very careful to avoid implementing anything that would infringe on a patent, it still leaves me very uneasy.  Mono is an implementation of MS's .NET framework, which it controls, which I think leaves the door much more open to claims of patent infringement than other claims MS has made (and never explicitly disclosed).

This seems a reasonable course of action to me, not as something that is "anti-Microsoft", but something that is "pro-freesoftware".  Why should Ubuntu include any programs that depend on a language/framework that might be subject to patent fees at some point in the future?  While they very well may not ever be subject to these fees, I think it is wiser in the long run to take a cautionary approach, no matter how good the .NET and Mono technologies are.  

This is not to demean, diminish, belittle, or disrespect the developers (or their effort) of programs such as beagle, banshee, fspot, and tomboy.  On the contrary, they should be commended since many people enjoy using these specific programs.  I think it that in keeping the entire user experience in mind, we might realize what is being risked when a program depends too strongly on potentially non-free (or at least potentially patent-encumbered) components.

Personally, I avoid using tomboy, beagle, fspot, and banshee not because of anything affecting my user experience now, but because I don't want to have to switch programs later if these projects can no longer be maintained due to Mono being affected by patent restrictions in the future.  One of the reasons I made the switch to Linux and free software was because I could count on the programs I knew how to use always beng around when I needed them.  I have made a nearly 100% switch away from MS and proprietary programs because I got sick of paying upgrade fees every few years just to make sure my software was "up to date", in terms of compatibility, security, and advances in the user experience.  To me, and I would say every user of software, having unrestricted access to the programs we know how to use is essential.  Any step taken that could affect this should be approached with extreme caution.

Once again, this is not about being anti-Microsoft, but about being pro-user and pro-freesoftware (and pro-ubuntu).

Might I be wrong, and missing out on some great programs?  Possibly.  I still think it is worth preparing for the worst, as we have seen some very questionable behavior from MS relating to OOXML and it's certification as a "standard".  If Eben Moglen (sp?) were to come out and bless Mono, then I'd have far fewer concerns about using it, however that is not yet the case.

---

### Post by fwilliams on 2007-12-11
I agree with igknighted wrote:

As for default inclusion in Ubuntu, I think it comes down to apps and space. I think sticky notes could replace tomboy (not as feature-rich, but usable), but what replaces f-spot? The only real linux alternatives I am aware of are Picasa (proprietary, cannot be included) and DigiKam (KDE app - KDE libraries would take up far more space than the mono ones, yes? Plus f-spot is in Gtk#, while digikam would be qt and therefor not look natural). So as long as these are the only options for photo organization, I think you have to leave mono. Unless you want to remove that tool from Ubuntu completely.

---

### Post by screaminj3sus on 2007-12-11
Besides ridiculous idealogical reasons, removing it would be pointless alot of good apps use it and some included in ubuntu by default.

---

### Post by fwilliams on 2007-12-11
Correction.  I believe it should be available for people to use, but not by default.  That way people who want f-spot can apt-get it.

---

### Post by TeraDyne on 2007-12-11
> **fwilliams said:**
> I agree with igknighted wrote:

As for default inclusion in Ubuntu, I think it comes down to apps and space. I think sticky notes could replace tomboy (not as feature-rich, but usable), but what replaces f-spot? The only real linux alternatives I am aware of are Picasa (proprietary, cannot be included) and DigiKam (KDE app - KDE libraries would take up far more space than the mono ones, yes? Plus f-spot is in Gtk#, while digikam would be qt and therefor not look natural). So as long as these are the only options for photo organization, I think you have to leave mono. Unless you want to remove that tool from Ubuntu completely.

gThumb is a perfectly usable GTK alternative. It's what I use on a GNOME desktop, though I personally prefer DigiKam and KDE.

---

### Post by bruce89 on 2007-12-11
If only someone would rewrite F-Spot and Tomboy et. al. in [Vala]("http://live.gnome.org/Vala"), then we'd been all fine.

Vala is similar to C# code wise, but it is converted into C to be compiled with GCC.

---

### Post by emperon on 2007-12-12
> **bruce89 said:**
> If only someone would rewrite F-Spot and Tomboy et. al. in [Vala]("http://live.gnome.org/Vala"), then we'd been all fine.

Vala is similar to C# code wise, but it is converted into C to be compiled with GCC.

You don't even now what you are talking about , do you

---

### Post by rikhard.fsoss on 2007-12-12
> **screaminj3sus said:**
> Besides ridiculous idealogical reasons, removing it would be pointless alot of good apps use it and some included in ubuntu by default.

i don't know if you are new to the concept of GNU/Linux and FLOSS, but this kind of software IS idealogical.

I like the spirit, the philosophy behind FLOSS, it's FLOSS strength.

the creator of ubuntu is a VERY intelligent man, he refused the deal with m$, like novell, xandros, and others did, so would be quite stupid now for ubuntu be held illegal with all that patents crap from m$.

even mr RMS says so about gnome...

[http://www.mail-archive.com/foundation-list@gnome.org/msg02760.html](http://www.mail-archive.com/foundation-list@gnome.org/msg02760.html)
[http://www.gnu.org/software/dotgnu/danger.html](http://www.gnu.org/software/dotgnu/danger.html)

Call to Remove Mono/.NET/Patent Mess from Ubuntu GNU/Linux
[http://groups.google.com/group/comp.os.linux.advocacy/browse_thread/thread/e58e3be8245b22a3#1314c1fc809d130d](http://groups.google.com/group/comp.os.linux.advocacy/browse_thread/thread/e58e3be8245b22a3#1314c1fc809d130d)


lot's of information about mono, gnome and the CLOSED m$-ooxml format.
[http://boycottnovell.com/2007/12/11/ooxml-mono-ubuntu/](http://boycottnovell.com/2007/12/11/ooxml-mono-ubuntu/)

RJ

---

### Post by Polygon on 2007-12-12
except right now there are no current patent issues. From what i understand, the only thing that MIGHT cause issues is winforms, and that is a seperate ubuntu package (mono-winforms), so wouldent just pulling that if any patent issues were brought up do the trick?

---

### Post by saulgoode on 2007-12-12
> **emperon said:**
> You don't even now what you are talking about , do you
What would make you think that? 

What are the benefits in having a CIL interpreter running pseudo-code instead of compiling the source directly to native executables? Both F-spot and Tomboy are open source GNOME projects, so why place a burden of cross-platform support on the users who already have cross-platform support by the inherent nature of the code being Open Source?

---

### Post by rikhard.fsoss on 2007-12-12
> **Polygon said:**
> except right now there are no current patent issues. From what i understand, the only thing that MIGHT cause issues is winforms, and that is a seperate ubuntu package (mono-winforms), so wouldent just pulling that if any patent issues were brought up do the trick?

patents are a great concern, even here in Europe, although there aren't software patents in the EU, there is a patent office, that is why m$ got a great victory in all this EUvsm$ mess.

FLOSS software like  SAMBA is still prisoner of m$.

but besides patents, what are the advantages of mono in a kind of software like FLOSS where everything is open source and where you have the ability and the tools to implement it in every language possible, like java, python, ruby, c, c++ etc.

and why bother with m$? the best proprietary OS, MacOSX is FreeBSD based, it's unix, we have already the tools to buil everything open, standard and portable, why bother with m$, why?

it's m$ that have to be interoperable with the others not the way around, we already comply.

RJ

---

### Post by hanzomon4 on 2007-12-12
Come now, let's not do the whole m$ thing... it's tacky 

Also Mono is oss so it only adds to the languages available to coders(I'm not one)

---

### Post by DoctorMO on 2007-12-12
Despite what people are saying about legals; Mono is a bad library to include by default right now. bloated and not used by any core applications. We would do ourselves a favour by saving the space for more drivers, inkscape and maybe even a video editor. Why people need a photo organisation tool or a sticky notes program installed by default is beyond me.

---

### Post by rikhard.fsoss on 2007-12-12
> **DoctorMO said:**
> Despite what people are saying about legals; Mono is a bad library to include by default right now. bloated and not used by any core applications. We would do ourselves a favour by saving the space for more drivers, inkscape and maybe even a video editor. Why people need a photo organisation tool or a sticky notes program installed by default is beyond me.

well you're right about mono, but a good notes program is cool, and a photo org too, but good ones don't need mono.

i'm using both gnome and kde, and kde has a brilliant prog for notes, basket, but i guess knotes is the default, for photos, hummmm i just ness gwenview, or gqview, or the great imseek.

rj

---

### Post by Luggy on 2007-12-12
I don't think it's a big deal.

If a patent issue arises it wont hurt Ubuntu, it will only hurt the devs behind F-Spot, Tomboy and the like as (worst case scenario ) MS will go "all ur codez are belong to us"! And how much would that bother most people? Everyone is already saying there are alternatives, they may not be quite as nice but it's not like we are loosing something important like the kernel.

The other reasons on the Wiki are laughable.
> Providing Mono on the Default Ubuntu Desktop CD helps Mono become more popular as more people will use it by default.
HOLY CRAP! Don't implement mono because then people might use it! *shockandterror* :o

If devs are going to write something with mono, they are going to install it anyway.

My old roommate only took C# in school, if he were to switch to Linux and want to write some code he would probably want to use mono. 

Will MS constantly change the format?
Sure that sounds right up their ally. 

How much is it going to matter for people writting apps for Linux?
Since the mono team is not going to break backwards compatibility I don't see the guys behind F-Spot or Tomboy getting worried so neither should you.

---

### Post by bruce89 on 2007-12-12
> **emperon said:**
> You don't even now what you are talking about , do you

I don't know what the point of insulting me is.

---

### Post by JohnPhys on 2007-12-13
I agree with the sentiment of a few people that including a sticky notes program by default seems a bit much, but a photo manager/editor seems essential nowadays, I just wish it was one that didn't depend on mono (see my post earlier in this thread for why).

I completely support including inkscape on a default install, as I think it compliments the gimp quite nicely.

---

### Post by hanzomon4 on 2007-12-13
> **JohnPhys said:**
> I agree with the sentiment of a few people that including a sticky notes program by default seems a bit much, but a photo manager/editor seems essential nowadays, I just wish it was one that didn't depend on mono (see my post earlier in this thread for why).

I completely support including inkscape on a default install, as I think it compliments the gimp quite nicely.

Folks tomboy is in the default Gnome, K? Case closed

---

### Post by saulgoode on 2007-12-13
> **hanzomon4 said:**
> Folks tomboy is in the default Gnome, K? Case closed

Read your sig. :)

---

### Post by smartboyathome on 2007-12-13
> **JohnPhys said:**
> I agree with the sentiment of a few people that including a sticky notes program by default seems a bit much, but a photo manager/editor seems essential nowadays, I just wish it was one that didn't depend on mono (see my post earlier in this thread for why).

I completely support including inkscape on a default install, as I think it compliments the gimp quite nicely.

[off-topic]I would say that Inkscape wouldn't be used by the average user (versus GIMP), as it doesn't edit the average format of images.[/off-topic]

I agree with what both emperon and Luggy said. What people are saying is just FUD. If Microsoft said they wouldn't jump off a cliff, would you, just because you want to be different from them? Think about it.

---

### Post by hanzomon4 on 2007-12-13
> **saulgoode said:**
> Read your sig. :)

Why?

Tomboy is default gnome, Ubuntu didn't put it there and Ubuntu doesn't really break from the default gnome apps. So all of this talk about Ubuntu not needing a note taking app and should remove it from the disk is quiet pointless.

---

### Post by DoctorMO on 2007-12-13
> Tomboy is default gnome, Ubuntu didn't put it there and Ubuntu doesn't really break from the default gnome apps. So all of this talk about Ubuntu not needing a note taking app and should remove it from the disk is quiet pointless.

Dogma, ubuntu doesn't have to follow gnome, nor should it in cases where it doesn't make sense to. Gnome are quietly digging themselves a grave with Miguel de Icaza at the fore; constantly trying to force pragmatism and ending up in a new kind of pragmatical religion, which ironically isn't pragmatic at all.

---

### Post by hanzomon4 on 2007-12-13
Well Ubuntu does follow gnome, but that's beating a dead horse. How is Gnome digging it'self a grave?

---

### Post by Mr. Picklesworth on 2007-12-13
> Gnome are quietly digging themselves a grave with Miguel de Icaza at the foreIcaza is not on the GNOME Foundation board of directors!
As for being GNOME's president, he (officially) resigned at a meeting around November 15, 2007. (Causing very little disturbance in the force; Miguel starts things, and gradually moves so that other people can take over. In many ways, that's a good thing since it means that nobody with a huge feeling of ownership dominates the project, the end result of which would be that everything goes straight downhill if he stopped working on it. Miguel's projects end up much more democratically run than many others).
[This article](http://www.linux.com/feature/121930) on GNOME's stance on OOXML clears the matter one up fairly well, I think.

That's what people are talking about when they call this whole kerfuffle "spreading FUD".

---

### Post by igknighted on 2007-12-13
> **smartboyathome said:**
> I agree with what both emperon and Luggy said. What people are saying is just FUD. If Microsoft said they wouldn't jump off a cliff, would you, just because you want to be different from them? Think about it.

Haha, +1

---

### Post by JohnPhys on 2007-12-13
> [off-topic]I would say that Inkscape wouldn't be used by the average user (versus GIMP), as it doesn't edit the average format of images.[/off-topic]

I don't think it's completely off topic, as part of the discussion is "what would replace mono & mono apps on the default cd?", since one of the points made is the amount of space mono takes up.

That being said, rather than inkscape, how about some more documentation?  I know the GIMP doesn't come with most (if not all) of its help documentation installed, and I don't think OpenOffice does either.  That could actually be a really good use of space on the cd, especially for programs as large and complex as GIMP and OpenOffice.

---

### Post by bruce89 on 2007-12-13
> **hanzomon4 said:**
> Folks tomboy is in the default Gnome, K? Case closed

And yet Ubuntu has Firefox, not Epiphany as default.

> **JohnPhys said:**
> That being said, rather than inkscape, how about some more documentation? [...] and I don't think OpenOffice does either.

It does.

---

### Post by emperon on 2007-12-13
People who want to see how much space mono takes can check here 
[http://www.viraptor.info/repo/pool/contrib/m/mono/]("http://www.viraptor.info/repo/pool/contrib/m/mono/")

My estimation would be all default installed mono + tomboy + etc takes about 20-25  MB maximum. Yet the space issue is another FUD. People talk about 73 MB. Blah

And note that you are not sacrificing  25 mb of your CD for only tomboy. You also allow .NET based and mono based applications run on your computer out of box. That's huge bonus at the cost of 25 MB.

---

### Post by igknighted on 2007-12-13
> **bruce89 said:**
> And yet Ubuntu has Firefox, not Epiphany as default.

At least until hardy... word on the street is that the new webkit-based epiphany will replace FF (personal note: thank god, it's about time).

---

### Post by bruce89 on 2007-12-13
> **igknighted said:**
> At least until hardy... word on the street is that the new webkit-based epiphany will replace FF (personal note: thank god, it's about time).

It will do in Debian, Ubuntu's too switcher friendly.

I personally think that having Firefox just because Windows people will be used to it is silly. All the other programs are different, so why should Firefox be different?

I also think OO.o should be removed, its Linux support is awful.

I look forward to the day when this can happen:
```

bruce@Scooby-Dum:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox
bash: firefox: command not found
```

---

### Post by Andrewie on 2007-12-13
all these stupid mono threads should be sent to Recurring Discussions. When they remove vitual desktops from KDE and Gnome then they can remove mono.

How come no one is crying about mono in KDE 4 (C# support).

---

### Post by DoctorMO on 2007-12-13
I have to wonder how far the developers are quickly leaving the rest of us users by going off on their weirdness. Have the .Net framework available by default is disadvantageous not an advantage, only shills and x windows developers think otherwise.

You keep on saying that it's good to get windows developers, developing for linux by proxy and yet I don't believe a word of it. It's a focus on developers instead of users that hurts a distribution. You could create a new distro for developers if you wanted, but you don't want that, you just want your own personal libs installed that make _you_ happy, nothing to do with real users at all.

---

### Post by bruce89 on 2007-12-13
> **DoctorMO said:**
> Have the .Net framework available by default is disadvantageous not an advantage, only shills and x windows developers think otherwise.

I assume you mean ex-windows, not X Windows, which is quite different.

> **Andrewie said:**
> How come no one is crying about mono in KDE 4 (C# support).

Probably because people don't know about it.

---

### Post by Andrewie on 2007-12-13
> **bruce89 said:**
> 
Probably because people don't know about it.

I probably shouldn't tell them about DotGNU and Portable.NET :lolflag:

---

### Post by Luggy on 2007-12-13
> **Andrewie said:**
> all these stupid mono threads should be sent to Recurring Discussions. 

Agreed.

I'm tired of all the FUDMuffins here on the forums.

---

### Post by bruce89 on 2007-12-13
> **Andrewie said:**
> I probably shouldn't tell them about DotGNU and Portable.NET :lolflag:

That's fine, it's a GNU thing. Novell are the villains of the piece.

/me gets an idea of what to say next time people go on about how they're going to move to KDE4 thanks to its anti-MS stance.

---

### Post by emperon on 2007-12-13
> **DoctorMO said:**
>  Have the .Net framework available by default is disadvantageous not an advantage, only shills and x windows developers think otherwise.



Can you give any specific and concrete reasons for this statement ?

---

### Post by saulgoode on 2007-12-13
> **bruce89 said:**
> I assume you mean ex-windows, not X Windows, which is quite different.
I assume you mean X Window System, not X Windows.

---

### Post by bruce89 on 2007-12-13
> **saulgoode said:**
> I assume you mean X Window System, not X Windows.

Touché.

---

### Post by smartboyathome on 2007-12-13
> **DoctorMO said:**
> You could create a new distro for developers if you wanted, but you don't want that, you just want your own personal libs installed that make _you_ happy, nothing to do with real users at all.

At this point, it sounds like you are trying to force your views on everyone else. Why would someone want to create a new distro because they want Linux to grow? Tell me that.

And it WOULD help developers port applications to Linux, since they wouldn't have to teach their devs as much to get it ported, and wouldn't have to spend the time teachign the devs.

---

### Post by bruce89 on 2007-12-13
Most mono depending apps are written by Novell. 'Nuff said.

---

### Post by igknighted on 2007-12-13
> **DoctorMO said:**
> I have to wonder how far the developers are quickly leaving the rest of us users by going off on their weirdness. Have the .Net framework available by default is disadvantageous not an advantage, only shills and x windows developers think otherwise.

You keep on saying that it's good to get windows developers, developing for linux by proxy and yet I don't believe a word of it. It's a focus on developers instead of users that hurts a distribution. You could create a new distro for developers if you wanted, but you don't want that, you just want your own personal libs installed that make _you_ happy, nothing to do with real users at all.

So if we re-phrased it as, "It would be good to have popular apps be cross platform so that USERS can keep their favorite apps when switching to linux", would this be agreeable to you?

I still don't see what it is that you find objectionable about mono.  Is it the size?  For what you could add in its place, this isn't very significant.

Is it the microsoft connection?  We need to grow past our irrational fear/hatred of everything microsoft.

Is it the concern that using mono you are strengthening microsoft by using mono?  Again, as I have said before, using mono weakens microsoft, by taking its platform and developers - and yes, that means end user applications - and making them available to linux users.  It breaks down barriers to adoptation.

So please, can you explain (in a reasoned response backed up by some facts, not one where you're evidence is "only shills and x windows developers would think otherwise") why you think mono is so bad for linux?

---

### Post by igknighted on 2007-12-13
> **bruce89 said:**
> Most mono depending apps are written by Novell. 'Nuff said.

Actually, more accurately, most mono depending apps are written by F/OSS developers who are on novell's payroll.  It also happens that large chunks of gnome, KDE and the linux kernel are written by employees of novell... perhaps we should boycott these as well?

---

### Post by fwilliams on 2007-12-13
Jeff Waugh
November 27th, 2007 at 1:21 am

It’s totally easy to remove all of the Mono stuff on most distros. It’s effortlessly easy on Ubuntu, for instance. The only thing you’ll be left with that has a Mono “scent” is libbeagle, which is 100% C and 0% Mono anyway. It’s just an adapter such that GNOME software can use Beagle but not depend on Mono. You won’t need to build anything.

---

### Post by fwilliams on 2007-12-13
Could mono please be excluded from the Ubuntu base?

It could then be added to other distributions based on Ubuntu for those who want it.

---

### Post by igknighted on 2007-12-13
> **fwilliams said:**
> Could mono please be excluded from the Ubuntu base?

It could then be added to other distributions based on Ubuntu for those who want it.

Why though?  What is your reason for wanting that?  No one can seem to come up with a legitimate reason that does not involve "because it implements something microsoft created", so I fail to see a reason to take away some perfectly good applications that many people use.

---

### Post by Incense on 2007-12-13
> **bruce89 said:**
> Most mono depending apps are written by Novell. 'Nuff said.

You may also be interested in boycotting (among other things)

Gnome
KDE
Evolution
NetworkManger
WINE

right along with Mono, f-spot, banshee, tomboy, beagle. 

[http://en.opensuse.org/Novell_Supported_Projects]("http://en.opensuse.org/Novell_Supported_Projects")


I really think this whole thread is a bit silly. If you don't want Mono, A:Remove it yourself post install, B: use a distro that does not include mono be default.

---

### Post by emperon on 2007-12-14
> **Incense said:**
> You may also be interested in boycotting (among other things)

Gnome
KDE
Evolution
NetworkManger
WINE

right along with Mono, f-spot, banshee, tomboy, beagle. 

[http://en.opensuse.org/Novell_Supported_Projects]("http://en.opensuse.org/Novell_Supported_Projects")


I really think this whole thread is a bit silly. If you don't want Mono, A:Remove it yourself post install, B: use a distro that does not include mono be default.

Well said !

---

### Post by saulgoode on 2007-12-14
> **Incense said:**
> You may also be interested in boycotting (among other things)

Gnome
KDE
Evolution
NetworkManger
WINE

right along with Mono, f-spot, banshee, tomboy, beagle. 

[http://en.opensuse.org/Novell_Supported_Projects]("http://en.opensuse.org/Novell_Supported_Projects")

Gnome, Evolution, and NetworkManager are all GNOME projects. The GNOME foundation's charter clearly commits their activities to be in support of Free Software.

KDE has made their commitment to Free Software very clear and continually seems to make statements expressing and take steps exhibiting this. The company behind the QT libraries has setup a [a foundation](http://www.kde.org/whatiskde/kdefreeqtfoundation.php) (much like Canonical provides the Ubuntu Foundation) securing the availability of the core libraries for the continued development of Free Software.

Mono is NOT a GNOME project and does not seem to have a charter expressing its commitment to remaining free.  Furthermore, the company behind its development (Novell) has promoted the existence of a patent indemnity "covenant" which covers Mono as an exclusive benefit not available to users of other Linux distributions (this includes Xandros and Linspire, whose "covenants" specifically designated Mono as NOT being indemnified).

WINE would seem to be a fairly close comparison to MONO in its desired goal of cross-platform compatibility and the fact of it currently being Open Source. I am unable to find where WINEHQ makes a specific commitment to its continued development always remaining under the Free Software philosophy, but nor has the company shown any evidence of being willing to subvert that philosophy. Furthermore, I would point out that WINE is not included with a default Ubuntu install (which is what is being proposed in this thread).

This is NOT a silly discussion. In fact, the GNOME Foundation's defense of projects such as F-Spot, Beagle, and Tomboy has been that distributions are provided the option of excluding them should they wish. I agree with this and I think that all distributions **should** be making that decision (just as they do for any inclusion/exclusion of other software). 

Personally, I think it is fine to include GNOME projects such as F-spot and Tomboy in a GNU/Linux distribution -- but I am opposed to inclusion of Mono.

---

### Post by cab0san on 2007-12-14
I am a developer of business applications. I use .NET. 

Leaving the Mono libraries as part of the base OS will make the Ubuntu more attractive to developers and businesses. It will not be seen as an "add-on" , but rather a fully compatible piece of the package. 

If I were to recommend any Linux platform to a business, it would be one that included Mono, making easier to find software, developers and support. It's an easier sell.

It's another door open for Ubuntu. Another way for this OS (an incredibly stable, fast, and easy to use operating system IMO) to differentiate itself from others.

---

### Post by 23meg on 2007-12-14
[QUOTE=saulgoode]In fact, the GNOME Foundation's defense of projects such as F-Spot, Beagle, and Tomboy has been that distributions are provided the option of excluding them should they wish.
[/QUOTE]

Could you link to where this was said?

---

### Post by DoctorMO on 2007-12-14
> No one can seem to come up with a legitimate reason that does not involve "because it implements something microsoft created", so I fail to see a reason to take away some perfectly good applications that many people use.

It's big, not mature enough, isn't nice and friendly and not well supported. We're putting things like mono into ubuntu so certain developers can be all religiously pragmatic instead of fair minded to what users could do with having in a default install. There are more important things to have in the _default_ install than tomboy and f-spot.

---

### Post by hanzomon4 on 2007-12-14
> **DoctorMO said:**
> It's big, not mature enough, isn't nice and friendly and not well supported. We're putting things like mono into ubuntu so certain developers can be all religiously pragmatic instead of fair minded to what users could do with having in a default install. **There are more important things to have in the _default_ install than tomboy and f-spot**[color=blue]**[SIZE="3"](?)[/SIZE]**[/color].

Like what?

---

### Post by saulgoode on 2007-12-14
> **23meg said:**
> Could you link to where this was said?

It was on the Gnome mailing list. If I recall correctly, it was in [this thread](http://www.mail-archive.com/foundation-list@gnome.org/msg02625.html) (I believe the author was Jeff Waugh). Sorry for lack of a more precise link but I have a meeting to attend. (Note: I did not intend for "defense" to mean anything pejorative, merely that the choice was there to exclude Mono.)

---

### Post by Incense on 2007-12-14
> **saulgoode said:**
> Gnome, Evolution, and NetworkManager are all GNOME projects. The GNOME foundation's charter clearly commits their activities to be in support of Free Software.

KDE has made their commitment to Free Software very clear and continually seems to make statements expressing and take steps exhibiting this. The company behind the QT libraries has setup a [a foundation](http://www.kde.org/whatiskde/kdefreeqtfoundation.php) (much like Canonical provides the Ubuntu Foundation) securing the availability of the core libraries for the continued development of Free Software.

Mono is NOT a GNOME project and does not seem to have a charter expressing its commitment to remaining free.  Furthermore, the company behind its development (Novell) has promoted the existence of a patent indemnity "covenant" which covers Mono as an exclusive benefit not available to users of other Linux distributions (this includes Xandros and Linspire, whose "covenants" specifically designated Mono as NOT being indemnified).

WINE would seem to be a fairly close comparison to MONO in its desired goal of cross-platform compatibility and the fact of it currently being Open Source. I am unable to find where WINEHQ makes a specific commitment to its continued development always remaining under the Free Software philosophy, but nor has the company shown any evidence of being willing to subvert that philosophy. Furthermore, I would point out that WINE is not included with a default Ubuntu install (which is what is being proposed in this thread).

This is NOT a silly discussion. In fact, the GNOME Foundation's defense of projects such as F-Spot, Beagle, and Tomboy has been that distributions are provided the option of excluding them should they wish. I agree with this and I think that all distributions **should** be making that decision (just as they do for any inclusion/exclusion of other software). 

Personally, I think it is fine to include GNOME projects such as F-spot and Tomboy in a GNU/Linux distribution -- but I am opposed to inclusion of Mono.

My post was pointing out that those projects were supported by Novell, in response to the posters statment that mono should be removed for the very reason that Novell supported it. The discussion in general is not a silly one, and I support those looking for a completly free distro. The apps are very usefull, and are really without alternitive on the gnome side. What would replace f-spot if you removed mono? I would argue that digiKam is a better photo program, but it's KDE and they don't seem to put KDE programs in Gnome. I just don't see any real problem with Mono, and removing something that most people don't care about, or find usfull just does not make sense to me. I think the Ubuntu devs were just looking for the best free apps out there to include in the distro, and f-spot and tomboy make sense. I don't think they were trying to make a political statement, and since mono is GPL, it's all good IMO. Of course I use OpenSUSE, and support Novell with a sled subscription, so maybe I'm the wrong guy.

---

### Post by igknighted on 2007-12-14
> **DoctorMO said:**
> It's big, not mature enough, isn't nice and friendly and not well supported. We're putting things like mono into ubuntu so certain developers can be all religiously pragmatic instead of fair minded to what users could do with having in a default install. There are more important things to have in the _default_ install than tomboy and f-spot.

No, mono is included because it is needed by f-spot and tomboy, which were deemed worthy.  I don't think Ubuntu really gives a damn about the reasons you mentioned.  As incense said, if you have an alternative we can weigh the pluses and minuses of removing fspot/tomboy and adding what you suggest, but I haven't seen anything yet that would be more valuebale that these two.

---

### Post by Mr. Picklesworth on 2007-12-14
Furthermore, Mono is necessary for a web technology that should, rightfully, take over from Flash and Java applets. I strongly believe that it will, at least in open source-oriented sites. Having said that, there has been really nice movement lately towards Javascript; flashy web sites keep surprising me by *not* being powered by Flash. Sadly, Javascript continues to be comparable to PHP in terms of having a bloated and indecisive design; I would be delighted to see C# (with a few libraries) take over for the entire client-side end of web sites, some day. At this point, especially considering how complicated it has become, there is absolutely no justification for the direction in which web technologies are used. (With the biggest exceptions being XML and communicating with the server). This stuff is abstracted to the point that people do not *want* the abstraction, such that designing web sites is more a game of tricking the different web browsers into behaving how the designer really wants them to behave. If we could just talk to the underlying renderers manually, this stuff would be a hundred times easier than that excessively assumptive standard CSS. (Not that the stlye sheets are a bad idea; just the way that browsers automatically handle the properties of objects. They all suck at it; I would rather they left it to me, the designer who knows precisely how my web site *should* be rendered).


Err, that's really a thought for another place. Back on topic:


Having neat applications in by default *is* necessary. This is thanks to the LiveCD installer; it is Ubuntu's chance to really impress someone with nice software, which is a big factor in their decision for whether or not to actually install the thing. Without Tomboy, F-Spot, or any other fun apps like that, we have a system that is functional and nothing more. To the curious, slightly uncertain user, that just would not cut it. Need an example? Look at the included software on an iMac.

Sure, programs can be installed in the Live CD, but we must think of this from the "switcher's" perspective: he has no swap partition!  Every time something is installed, the system loses a ton of memory. Moving all those programs off the CD and into a download may sound like a trivial "those who want it can still get it" sort of thing, but we have to consider what these trivial but awesome little tools mean to someone just looking in to Ubuntu, who does not know such software is available. I know Tomboy was a big decider in me upgrading to Edgy, and also is the reason why I decided to install Ubuntu on a more powerful computer. It is a completely unique application that does not exist in Windows, and F-Spot is ingeniously streamlined by using tags and only tags to arrange photos. It continues to amaze me how well that works, while other programs struggle with complex divisions between Events, Albums and Photos, then struggling to fit "one of those new-fangled tagging things" into a corner somewhere. F-Spot is one of very few programs to do it right, in accepting the idea that tags (and key/value pairs like them) can serve as every piece of arbitrary data we currently have littering interfaces, (Evolution, I'm looking at you!), instead making it all user-controlled while maintaining - nay, improving! - sanity and usability. In addition, that type of streamlined design encourages much smarter underlying code and leaves the door open for all manner of neat additions in the form of external software.

Such obviously unique every-day software, Mono or not, is tricky to find elsewhere on the Live CD -- particularly when the default web browser is Firefox (a very Windows-oriented program, likely already known of by switchers, thus providing little interest) and the office suite is OpenOffice (which integrates terribly with Ubuntu).

---

### Post by kfries6 on 2007-12-14
Mono is also needed for Beagle which is installed by default, and supported by everyting on the planet.

---

### Post by JohnPhys on 2007-12-17
I messed up the quote for this reply, but it's in response to the "it does" response about openoffice or gimp including documentation by default.  I think I have it fixed now.


> [QUOTE]Originally Posted by JohnPhys View Post
That being said, rather than inkscape, how about some more documentation? [...] and I don't think OpenOffice does either.
It does.
______________[/QUOTE]

Which "it", gimp or openoffice?  Just the other day I had to install gimp-help-en and gimp-help-common, so at least as of feisty those packages were not installed.

---

### Post by banjobacon on 2007-12-18
> **kfries6 said:**
> Mono is also needed for Beagle which is installed by default, and supported by everyting on the planet.

Incorrect. Ubuntu installs Tracker by default.

---

### Post by hanzomon4 on 2007-12-18
Which does not use mono

---

### Post by chandru.in on 2008-01-05
Posted it as a [URL="http://ubuntuforums.org/showthread.php?p=4076671"]separate post
[/URL]

---

### Post by lingnoi on 2008-02-29
I haven't read the thread because I don't really care about people's opinions on the subject.

Looking at the spec I am not satistifed with the Goal of replacing F-spot with GThumb.

I would feel much happier to replace f-spot with something which provides the same functionality better then f-spot does.

I have 2409 photos in f-spot (2.2 Gig) and I have the following problems:
- It's slow
- It crashes when adding photos sometimes
- It takes too long to load up
- It messes up the photo meta data putting the date on photos taken in 2006/07 as 1980s

I am 100% sure that the first two problems are related to Mono, after updating Mono, f-spot starting working much better. 

To me this indicates that if the quality of the program depends on your version of Mono, then we need to stop providing Mono programs by default as it will ruin the reputation of Ubuntu as a stable system (plus I don't want the risk of losing my photos or the date they were taken).

I don't care about if people want to use Mono on Ubuntu or not. f-spot just isn't really that great to begin with, but I do love the user interface. I hope there will be a better competitor in the future.

---

### Post by neighborlee on 2008-02-29
> **lingnoi said:**
> I haven't read the thread because I don't really care about people's opinions on the subject.

Looking at the spec I am not satistifed with the Goal of replacing F-spot with GThumb.

I would feel much happier to replace f-spot with something which provides the same functionality better then f-spot does.

I have 2409 photos in f-spot (2.2 Gig) and I have the following problems:
- It's slow
- It crashes when adding photos sometimes
- It takes too long to load up
- It messes up the photo meta data putting the date on photos taken in 2006/07 as 1980s

I am 100% sure that the first two problems are related to Mono, after updating Mono, f-spot starting working much better. 

To me this indicates that if the quality of the program depends on your version of Mono, then we need to stop providing Mono programs by default as it will ruin the reputation of Ubuntu as a stable system (plus I don't want the risk of losing my photos or the date they were taken).

I don't care about if people want to use Mono on Ubuntu or not. f-spot just isn't really that great to begin with, but I do love the user interface. I hope there will be a better competitor in the future.

 To think I was considering trying fspot to verify posters statements that its either  stable or it is not. I dont know how many others are having the trouble you are, but I guess we would know if everyone sends in the crash reports..assuming MONO apps are tied into ubuntu's crash handler ...

I think everyone is tired of having the endless discussion but if  everyone elses experiences mirror yours on any  level then including MONO and fspot blah ad nauseum is clearly fair to characterize as on the edge of questionable judgement and I gotta wonder how many testers were in place and the length of time they tested . 

And what about diigikam was any thought give to it considering its feature page is rather what..extensive,or is that a no go since its a kde application .

@lingnoi : I am curious did you get the new MONO lib  via updates or did you seek it out yourself wondering if updating it would help any..

 I also have to wonder, was beagle removed in favor of tracker due to it being a badly written mono app or that mono did not lend itself well to a app like beagle ??

I have zero desire to run the risk of losing any of my photos either , and I thank you very much for taking the time to post this. 

Thanks for the warning and for being a voice of reason.

cheers
nl

---

### Post by 23meg on 2008-02-29
[QUOTE=neighborlee]I also have to wonder, was beagle removed in favor of tracker due to it being a badly written mono app or that mono did not lend itself well to a app like beagle ??[/QUOTE]

Beagle has never been included by default in Ubuntu.

Reminder to those experiencing (meta)data loss / corruption: The thing to do about an app as obviously misfunctioning as F-Spot in this case is to file a bug report and try to determine the cause of the problem.

---

### Post by igknighted on 2008-02-29
> To me this indicates that if the quality of the program depends on your version of Mono, then we need to stop providing Mono programs by default as it will ruin the reputation of Ubuntu as a stable system (plus I don't want the risk of losing my photos or the date they were taken).

How is this different than any other language?  The quality of your java apps will depend on your java version, same with Python and even C/C++ depending on compiler version.  Mono is a younger technology, so it is developing quite rapidly and you will see larger differences from version to version than you see in C or C++, but go back and compare GCC version one to today, and notice the difference.

As for your issues, most are probably related to simply poor programming.  FSpot, like mono, is fairly new.  I too have noticed it messes up dates on my photos, to be honest I could care less, but I see why others might care.  But to damn a whole platform just because one app had some (in the grand scheme of things) relatively minor bugs is rather hasty.

---

### Post by Polygon on 2008-03-01
IGK has a point

and maybe beagle using mono was part of the decision to make tracker default on ubuntu, but honestly, as a user of both, tracker is much much much better. Uses a fraction of harddrive space compared to beagle as well.

---

### Post by neighborlee on 2008-03-01
> **igknighted said:**
> How is this different than any other language?  The quality of your java apps will depend on your java version, same with Python and even C/C++ depending on compiler version.  Mono is a younger technology, so it is developing quite rapidly and you will see larger differences from version to version than you see in C or C++, but go back and compare GCC version one to today, and notice the difference.

As for your issues, most are probably related to simply poor programming.  FSpot, like mono, is fairly new.  I too have noticed it messes up dates on my photos, to be honest I could care less, but I see why others might care.  But to damn a whole platform just because one app had some (in the grand scheme of things) relatively minor bugs is rather hasty.

Then I recommend you doing this: 

apt-get install MONO fspot tomboy..is that too hard..and just let the default install use ONLY apps that are tested and stable period.

THis might be FOSS, but can't it also be stable and predictable..or do I have too high of expectations..is mac software also this unreliable ?

cheers
nl

---

### Post by chandru.in on 2008-03-01
It is really sad  While Mono which is a free implementation of a technology from a FOSS unfriendly company has a place in the default install of Hardy, GIJ which is a free implementation of a technology from a FOSS friendly company is removed.

---

### Post by Mr. Picklesworth on 2008-03-01
> **lingnoi said:**
> 
To me this indicates that if the quality of the program depends on your version of Mono, then we need to stop providing Mono programs by default as it will ruin the reputation of Ubuntu as a stable system (plus I don't want the risk of losing my photos or the date they were taken).

Actually, one of the good points of a platform like Mono (or Java or Python, for that matter) is that the end user applications can gain those performance improvements without needing to think about it. What you have witnessed is a program becoming noticeably more efficient, even though the developers of said application did not have to do anything -- it could very well have been unsupported. Furthermore, that improvement was set across the board as soon as you upgraded Mono.


I feel I should get this out of the way, too: **[COLOR="DarkRed"]Tomboy is NOT a generic "sticky notes" application[/COLOR]**. It is a full-fledged non-linear mind mapping tool specialized for note-taking (think lecture notes). It and the Sticky Notes applet have entirely different scopes. Zim is not an alternative because its interface demands complete attention; it works more like a word processor that sits in the foreground above everything else.

---

### Post by igknighted on 2008-03-01
> **neighborlee said:**
> Then I recommend you doing this: 

apt-get install MONO fspot tomboy..is that too hard..and just let the default install use ONLY apps that are tested and stable period.

THis might be FOSS, but can't it also be stable and predictable..or do I have too high of expectations..is mac software also this unreliable ?

cheers
nl

If the alternative at this point is no photo management app or one with a few minor bugs, I'd rather leave it in personally.  That's a gaping hole to just have nothing.  FWIW, the only mono app I use is Banshee.  I used F-spot for a while, now I use Picasa.  I don't use tomboy.  I do, however, think it is valuable to leave in, even though it doesn't affect me at all.

---

### Post by igknighted on 2008-03-01
> **chandru.in said:**
> It is really sad  While Mono which is a free implementation of a technology from a FOSS unfriendly company has a place in the default install of Hardy, GIJ which is a free implementation of a technology from a FOSS friendly company is removed.

Because GIJ is worthless.  Try running any java application and see how far you get.  Also, with the exception of frostwire (which has great alternatives anyways), what java apps are there that should be included?  After all, the only reason to include the libraries is if there is an application that needs them.

Once IcedTea and the official open sourced java runtime/sdk comes out you might see it included because it would add value (like a java browser plugin), but not until.

---

### Post by chandru.in on 2008-03-01
> **igknighted said:**
> Because GIJ is worthless.  Try running any java application and see how far you get.

How many modern .Net apps can run on Mono without any modification?

> **igknighted said:**
> Once IcedTea and the official open sourced java runtime/sdk comes out you might see it included because it would add value (like a java browser plugin), but not until.

Gij was included till Edgy but for Hardy it has suddenly been removed.

---

### Post by igknighted on 2008-03-01
> **chandru.in said:**
> How many modern .Net apps can run on Mono without any modification?



Gij was included till Edgy but for Hardy it has suddenly been removed.

There are plenty of modern Mono apps... forget the fact that it offers the cross platform aspect it is still useful.

---

### Post by chandru.in on 2008-03-01
> **igknighted said:**
> There are plenty of modern Mono apps... forget the fact that it offers the cross platform aspect it is still useful.

Hey you are the same person who stated GIJ's incompatibility with mainstream Java as the reason for its removal.

> Because GIJ is worthless. Try running any java application and see how far you get.

---

### Post by Mr. Picklesworth on 2008-03-01
*Sigh*

The bottom line is: The day *you* create (or help create) a photo manager and non-linear thought jotter on par with F-Spot and Tomboy is the day Ubuntu no longer needs Mono. Gthumb, being a rather pointless and ugly program, has in fact been removed from Hardy's default installation and replaced entirely with F-Spot. I think that serves as a fine reminder that Ubuntu cares about the end user experience as opposed to developer FUD.

Until then, saying "remove Mono" is about as ignorant a request as saying "remove the Linux kernel", "remove libc" or "remove Python". These things are requirements; means to an end. If you really care, and if you really want to see this change, fix the end. Otherwise, such efforts are completely irrelevant and will never come to fruition. I have elected not to post the many links to people starting to do this and failing / disappearing / losing interest minutes later, in part because that's a common thing to have happen with a project and in part because I am not trying to discourage this effort. I, for one, would not like to see all the work people have put into endlessly ranting this opinion go to waste. It would be a horrible way to go for a lot of bandwidth, time and brain cells.

---

### Post by bruce89 on 2008-03-01
> **chandru.in said:**
> GIJ which is a free implementation of a technology from a FOSS friendly company is removed.

The only program that needs GIJ was OO.o Base, which they removed as no-one needs it usually, not because it was bad in any way.

Anyway, the normal JDK is now FOSS (icedtea-java7-jdk).

For the record, I'd like to see F-Spot get folder watching, as I like making my own hierarchy of folders.

---

### Post by neighborlee on 2008-03-03
> **igknighted said:**
> If the alternative at this point is no photo management app or one with a few minor bugs, I'd rather leave it in personally.  That's a gaping hole to just have nothing.  FWIW, the only mono app I use is Banshee.  I used F-spot for a while, now I use Picasa.  I don't use tomboy.  I do, however, think it is valuable to leave in, even though it doesn't affect me at all.

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/34074](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/34074)

You can call it minor if you wish, but if it happens to someone else, it all of a sudden takes on a different tone doesn't it ;)

It's been a year almost since the last post on that bug thread and its still not  a 'fix committed'.If ubuntu wants to include fspot/mono as default in the install thats their perogative apparantly, but dont do it  at my expense please, because even though it might not occur for most users, you have no way of knowing that it wont ever occur for a small perctage and therefore you've made a incorrect decision.  I realize what follows may be 'well dont use ubuntu then' and you know thats fine; I'll make that decision myself.   

The bug  'might'have a low possibility of occuring ( do we know how many users have small harddrives and use them to max ? )  but I hardly think it merits low priority given the possible effect if it does.

I wonder sometimes what  happened to QA in linux as it seems every distro is marred with similar issues [ not that windows is perfect either ] , and we are therefore all left finding a suitable OS where the risk seems the lowest , and  Im really not sure where that is atm .

):P

cheers
nl

---

### Post by graabein on 2008-03-03
I read it and support it. Those who want F-Spot, Tomboy and Banshee (all good programs) can get them from the official repositories no problem. 

By default Ubuntu should support open languages and not something that's in the hands of 1-2 companies.

---

### Post by Andrewie on 2008-03-03
> **graabein said:**
> I read it and support it. Those who want F-Spot, Tomboy and Banshee (all good programs) can get them from the official repositories no problem. 

By default Ubuntu should support open languages and not something that's in the hands of 1-2 companies.

the problem is C# is an open language.

---

### Post by neighborlee on 2008-03-03
> **Andrewie said:**
> the problem is C# is an open language.

[http://boycottnovell.com/2007/08/07/embrace-to-confuse/](http://boycottnovell.com/2007/08/07/embrace-to-confuse/) < not url I had in mind but close enough I think.

Yes, this is a old'ish article by now, but it also seems to show that even OSI has not yet endorsed MONO;  at least not that I could find but if you can find where they did please update this thread ( or some other url showing where this is relevant ).

oh btw: [http://tirania.org/blog/archive/2005/Sep-06.html](http://tirania.org/blog/archive/2005/Sep-06.html) < even miguel himself here admits that M$ BLOCKS mono , so its not just some linux people not liking the idea apparantly M$ doesn't like it either so what does that say about how pure their 'opening up MONO' really is ? 

cheers
nl

---

### Post by fwilliams on 2008-03-31
Mark Shuttleworth has already made his comments about the subject very clear.  He wants mono to be part of Ubuntu, because he does not believe people should be worried about some possible IP infringements.

Very sad to include such highly controversial programs in the base Ubuntu distribution.  I do not need mono.  All I was trying to get across to people was that it should not be part of the base distribution.  Let someone create a distribution based on Ubuntu for those that want it.  Please keep Ubuntu clean.

C# is nothing more then Microsoft's attempt to pollute Java.  It's to bad the people who wrote tomboy and F-Spot could not have learned a real language.

---

### Post by randomstuff on 2008-03-31
I disagree with this proposal. If you read the entire thing, basically all of the objections have been countered, including:

- patent issues - they don't exist
- dependency on MS and the MS implementation - mono only depends on the spec, and provides compatability with MS .NET as a bonus.

Mono is also cross platform just as much as java (or at least close), because mono runs on windows and AFAIK mac as well, even if MS' own .NET implementation is windows only.

C# makes me about ten times more productive than C++, and still a bit more than java. We have been programming in C/C++ for so many years now, it's time to move to a better language, and C# is certainly a step in the right direction. For applications where pure performance is important use C/C++ by all means, but there is no reason not to use .NET for everything else.

Yes it is true that mono is not completely mature yet, but you have to start somewhere. The only reason you guys think that mono is "dangerous" is because it is vaguely related to MS. But in truth the mono implementation is completely independent and provides a very nice development platform.

---

### Post by Mateo on 2008-03-31
> **fwilliams said:**
> Mark Shuttleworth has already made his comments about the subject very clear.  He wants mono to be part of Ubuntu, because he does not believe people should be worried about some possible IP infringements.

Very sad to include such highly controversial programs in the base Ubuntu distribution.  I do not need mono.  All I was trying to get across to people was that it should not be part of the base distribution.  Let someone create a distribution based on Ubuntu for those that want it.  Please keep Ubuntu clean.

C# is nothing more then Microsoft's attempt to pollute Java.  It's to bad the people who wrote tomboy and F-Spot could not have learned a real language.

```
sudo apt-get purge mono
```

problem solved.

---

### Post by Mateo on 2008-03-31
> **randomstuff said:**
> I disagree with this proposal. If you read the entire thing, basically all of the objections have been countered, including:

- patent issues - they don't exist
- dependency on MS and the MS implementation - mono only depends on the spec, and provides compatability with MS .NET as a bonus.

Mono is also cross platform just as much as java (or at least close), because mono runs on windows and AFAIK mac as well, even if MS' own .NET implementation is windows only.

C# makes me about ten times more productive than C++, and still a bit more than java. We have been programming in C/C++ for so many years now, it's time to move to a better language, and C# is certainly a step in the right direction. For applications where pure performance is important use C/C++ by all means, but there is no reason not to use .NET for everything else.

Yes it is true that mono is not completely mature yet, but you have to start somewhere. The only reason you guys think that mono is "dangerous" is because it is vaguely related to MS. But in truth the mono implementation is completely independent and provides a very nice development platform.

good post, you make good points. people should just use ruby though, IMO.

---

### Post by cardinals_fan on 2008-03-31
Mono doesn't feel creepy to me, it just feels **SLOW**.  And **BUGGY**!

---

### Post by Mr. Picklesworth on 2008-03-31
> **cardinals_fan said:**
> Mono doesn't feel creepy to me, it just feels **SLOW**.  And **BUGGY**!

That there is fixed :)
(No, really; you will be delighted come April 25th. Being run via a VM, Mono can be optimized outside of programs using it, and quite visibly so. Apparently, memory management had a lot of problems which have been triumphed over in the past 6 months).

Mono is a bit like Python in that it really encourages highly extensible design, which is perfect for open source software that strives for large-scale collaboration. For example, Banshee has recently had a complete video component added in a very short chunk of time thanks to its design, and this type of tidiness is not unusual for Mono apps. The fact that people are creating such good code with it tells me something: the *language* is good.
On the other hand, [if people were writing programs with this thing](http://lolcode.com/), those programs would not be able to raise an open source community. Even if said program could calculate Pi to a billion places on the snap of a finger just because the user wished it so in his head, if the program was tough to contribute to, it would be forgotten.

---

### Post by jfbilodeau on 2008-04-02
> **randomstuff said:**
> 
- patent issues - they don't exist
- dependency on MS and the MS implementation - mono only depends on the spec, and provides compatability with MS .NET as a bonus.

Mono is also cross platform just as much as java (or at least close), because mono runs on windows and AFAIK mac as well, even if MS' own .NET implementation is windows only.


I have to strongly disagree. I work in Java and C#.

The patent issues does exist, and the OSP is one of Microsoft's most dangerous weapon. Amongst other reasons, please see:
[http://www.softwarefreedom.org/resources/2008/osp-gpl.html]("http://www.softwarefreedom.org/resources/2008/osp-gpl.html")
[http://www.fsfla.org/svnwiki/stdlib/offdoc/mision]("http://www.fsfla.org/svnwiki/stdlib/offdoc/mision")

C# is 'standardized' with ECMA. However, what about VB.NET? What about the CLR? What about .NET 2.0? 3.5?

Furthermore, saying that .NET is cross-platform is bull****. I'm not attacking what you said. I'm attacking what Microsoft is saying.

Here's some example of .NET's platform 'neutrality'.
[LIST]
[*]Assemblies are compiled to a Windows .exe or .dll (which contains both MS-DOS & Win32 code ;)).
[*]The System.Windows namespace is riddled with Win32 api stuff like [Handle]("http://msdn2.microsoft.com/en-us/library/system.windows.forms.control.handle.aspx") and [DefWndProc]("http://msdn2.microsoft.com/en-us/library/system.windows.forms.form.defwndproc.aspx")
 that ties any code that uses it to a particular platform.
[*]Absolute positioning is encouraged on forms instead of layout managers -- the end product will look great on Windows, but like **** on other platforms like the Mac, GTK or KDE.
[*]Plenty of enumerations and [attributes]("http://msdn2.microsoft.com/en-us/library/system.runtime.interopservices.comvisibleattribute.aspx") that exists only to expose COM and Win32 APIs.
[/LIST]
And the list goes on...

.Net is not enterprise ready.
[LIST]
[*]Have to use specialized database classes instead of interface (a-la Java)
[*]No equivalent to EJBs
[*]No application container (IIS is the closes thing there is, and that's an application, not a standard)
[*]Poor/Non-existent support for best practices & design patterns like MVCs.
[*]No built-in Javadoc equivalent (Sandcastle is just starting to see the light of day)
[*]No equivalent to the Java Community Process.
[/LIST]
And the list goes on...

Finally, Microsoft is the *only* entity that controls .NET. Mono will forever play catch-up to Microsoft. Do you really want this?

---

### Post by geoken on 2008-04-02
> **randomstuff said:**
> I disagree with this proposal. If you read the entire thing, basically all of the objections have been countered, including:

- patent issues - they don't exist
- dependency on MS and the MS implementation - mono only depends on the spec, and provides compatability with MS .NET as a bonus.


Can you please explain to me how the objections have been countered? All I see is people in support of Mono claiming there are no patent issues while ignoring all links which describe patent threats.

I also see the Mono project FAQ, which makes clear references to patents, being totally ignored. Here's the important part of the FAQ

[B]The core of the .NET Framework, and what has been patented by Microsoft falls under the ECMA/ISO submission. Jim Miller at Microsoft has made a statement on the patents covering ISO/ECMA, (he is one of the inventors listed in the patent): here ([http://web.archive.org/web/200304241.../msg00218.html](http://web.archive.org/web/200304241.../msg00218.html))

Basically a grant is given to anyone who want to implement those components for free and for any purpose.[/B]

Basically, a completely non-binding grant is given for patents. Why is this grant given if said patents don't exist? Furthemore, it probably wouldn't be too hard to question the indemnitiy that said grant bestows seeing as how the only link the Mono project could find on it points to an archived webpage and not an existing, active document.

---

### Post by saulgoode on 2008-04-02
> **geoken said:**
> Basically, a completely non-binding grant is given for patents. Why is this grant given if said patents don't exist? Furthemore, it probably wouldn't be too hard to question the indemnitiy that said grant bestows seeing as how the only link the Mono project could find on it points to an archived webpage and not an existing, active document.

Actually, Jim Miller's letter stated that a grant "**will be available**". That was three years ago -- if such grant has since been made available, why doesn't the Mono FAQ reference* it*? If the royalty-free and non-discriminatory terms Mr Miller stated would be forthcoming have not yet been granted, why does the Mono FAQ indicate that the grant has already been given?

---

### Post by geoken on 2008-04-02
I also wonder why the Mono FAQ has been completely stripped of any information regarding to patents? Seems pretty strange for them to remove the most frequently asked question from their frequently asked questions page.

---

### Post by neighborlee on 2008-04-02
> **geoken said:**
> I also wonder why the Mono FAQ has been completely stripped of any information regarding to patents? Seems pretty strange for them to remove the most frequently asked question from their frequently asked questions page.

I was not aware of this, but I'm glad I found this thread.

Thx for making this known, maybe this will open up some peoples eyes finally to what I and others have been saying for so long now.

cheers
nl

---

### Post by 23meg on 2008-04-02
[QUOTE=geoken]I also wonder why the Mono FAQ has been completely stripped of any information regarding to patents?[/QUOTE]

[QUOTE=neighborlee]I was not aware of this, but I'm glad I found this thread.

Thx for making this known, maybe this will open up some peoples eyes finally to what I and others have been saying for so long now.[/QUOTE]

[What?]("http://www.mono-project.com/FAQ:_Licensing")

---

### Post by filipf on 2008-04-03
I find this whole argument silly.
First of all, let me state that I'm a C++ developer and I personally find C# much easier and efficient for application making. It let's me do in a few hours what would normally consume a week in C++. 

Anyway, to the point - why on earth would we remove applications that our users are accustomed to from the default install? Come on! Give me a break! I just introduced my parents to Ubuntu (believe me, it wasn't easy) and showed them how to go about their normal tasks. What do you think will happen when the next version comes out and the defaults are gone? What if they want to spread the word only to discover that their favorite apps are gone?

If Ubuntu is to be a serious user-oriented desktop Linux, then why mess with the very people whom we are trying to appeal to?

---

### Post by filipf on 2008-04-03
> **jfbilodeau said:**
> 
C# is 'standardized' with ECMA. However, what about VB.NET? What about the CLR? What about .NET 2.0? 3.5?

Last time I checked the ECMA specs have been updated to include 2.0 types. Besides, it's really misleading to say .NET 2.0, 3.0, 3.5 - the runtime is the same (2.0) only extra libraries have been added, many of which are Windows-specific.

> **jfbilodeau said:**
> 
Furthermore, saying that .NET is cross-platform is bull****. I'm not attacking what you said. I'm attacking what Microsoft is saying.

Again, the intermediate language is definitively system independent. I can write a library on Windows, and then use it in Linux, Solaris, or a Mac. No problem. Of course if my library references functions that exist only on a given operating system, then the library won't be portable. It's that simple. Ultimately, it's up to the developers to decide where their code will run.

> **jfbilodeau said:**
> 
Absolute positioning is encouraged on forms instead of layout managers -- the end product will look great on Windows, but like **** on other platforms like the Mac, GTK or KDE.

Maybe in Windows.Forms. Microsoft has since learnt its lesson, and the next-generation windowing toolkit (Windows Presentation Foundation) is all vector graphics, resolution independent, and can be defined using XML files with layout managers. They whole thing is rendered using hardware acceleration. It simply kicks ***. 

> **jfbilodeau said:**
> 
Plenty of enumerations and [attributes]("http://msdn2.microsoft.com/en-us/library/system.runtime.interopservices.comvisibleattribute.aspx") that exists only to expose COM and Win32 APIs.

Just like Mono exposes bunch of Posix API functions. It's just system-specific  libraries.

I also disagree with the statement that .NET is not enterprise ready. Be realistic - there is a huge market for .NET developers! Try this Python or C++. Not so great...

Also, ultimately software is all about end users. And they want features, they want eye candy, they want reliability and they want it fast. Writing software is all about developers. And Microsoft seems to understand that. They do provide fantastic tools and frameworks which make programming more efficient and pleasant. Why deny that to Ubuntu developers?

---

### Post by fwilliams on 2008-04-03
Is there somewhere I can offer a reward, so someone will convert tomboy and f-spot to Java?  Maybe then we get get rid of mono and stop all these silly posts.

Stop using mono and get a life!

---

### Post by Mr. Picklesworth on 2008-04-03
> **fwilliams said:**
> Stop using mono and get a life!

Stop complaining about Mono and get a life? apt-get remove mono-common and get a life? Seems like a considerably easier feat.

About converting Tomboy or F-Spot to Java, there is (thank God!) no such money pool. I think the reason is fairly obvious: Java is no different than .Net, being controlled very closely by Sun. Further... does Java have GTK bindings? I have yet to see any Java program that integrates into this desktop environment, or really *any* desktop environment. As John Carmack says, it is a really nice language... **for databases.**
Oh, and that adds an unnecessary dependency on a very ugly and obtrusive VM which happens to add its 95% of the time unused "JDK  Policy Tool" (double spaces as written) to the menu.
Now, doing those with Python may make a bit of sense since it's a nice language with all the right bindings and community support, it is not ugly, and doing so would add no dependencies. Oh, and such a change would have a chance of actually making it upstream. However, I think it's worth noting that one of the benefits of Tomboy, for example, is the fantastic contributions by a small number of people who take their time to work on it. I doubt that they would appreciate switching over to Python just because somebody else rewrote it as such, so you can assume no direct support from those very innovative thinkers. In short, why not just write a new Wiki-like notes app in a different language? (And no, a text field with autosave does not come anywhere close to Tomboy).

As for attempts to do it, take a look at the F-Spot and Tomboy mailing lists. Someone comes in complaining about Mono and loudly trying to gather a force of magical code converters on a monthly basis. Nothing has come of it yet, and nothing ever will, because the maintainers of those projects (eg: The folks who know what they are doing and where they are doing with the concept) chose Mono for a reason.

Having said that, good luck to anyone who tries. Tomboy and F-Spot are really very unique with their simple-yet-powerful designs, and it wouldn't hurt to have a few more like them bouncing around. They are very inspiring applications, and a lot of neat ideas could happen if one was to start from scratch...

---

### Post by neighborlee on 2008-04-03
> **filipf said:**
> Last time I checked the ECMA specs have been updated to include 2.0 types. Besides, it's really misleading to say .NET 2.0, 3.0, 3.5 - the runtime is the same (2.0) only extra libraries have been added, many of which are Windows-specific.


Again, the intermediate language is definitively system independent. I can write a library on Windows, and then use it in Linux, Solaris, or a Mac. No problem. Of course if my library references functions that exist only on a given operating system, then the library won't be portable. It's that simple. Ultimately, it's up to the developers to decide where their code will run.


Maybe in Windows.Forms. Microsoft has since learnt its lesson, and the next-generation windowing toolkit (Windows Presentation Foundation) is all vector graphics, resolution independent, and can be defined using XML files with layout managers. They whole thing is rendered using hardware acceleration. It simply kicks ***. 


Just like Mono exposes bunch of Posix API functions. It's just system-specific  libraries.

I also disagree with the statement that .NET is not enterprise ready. Be realistic - there is a huge market for .NET developers! Try this Python or C++. Not so great...

Also, ultimately software is all about end users. And they want features, they want eye candy, they want reliability and they want it fast. Writing software is all about developers. And Microsoft seems to understand that. They do provide fantastic tools and frameworks which make programming more efficient and pleasant. Why deny that to Ubuntu developers?

So this all means that the novel/M$ settlement has no bearing whatsoever on mono then right ?

What about the fact that Redhat seemingly atm anyway will have nothing to do with mono, is it like how gtk compared to qt or what exactly..I did ask a few times on fedora forum, but one of the head devs said 'you'll have to ask Redhat'. I dont know entirely how I feel about Redhat but they were the first on the block with support for linux in any meaningful way and the OS itself is free ( unless you want paid support), so it really does beg the question why   a free OS is staying away from mono doesn't it ?

Now we have something called silverlight ...if  M$ isn't trying to takeover the internet , and seeminlgy leave linux on the sidelines, then why didn't they release silverlight , ready to work in the big  3 OS's sametime ?

What was all that about ooXML again ?:

[http://arstechnica.com/news.ars/post/20070829-linux-foundation-says-ooxml-not-ready-to-become-an-iso-standard.html](http://arstechnica.com/news.ars/post/20070829-linux-foundation-says-ooxml-not-ready-to-become-an-iso-standard.html)

[http://www.noooxml.org/](http://www.noooxml.org/)

There have been numerous 'patent' questions asked on this forum, and everyone here that seems to have a stake in what happens at ubuntu on the dev level is ignoring most of them, and I find that highly undesireable of a free OSS OS; I would ask they all be answered, which if your goal is mono inclusion in linux for the betterment of all , it would seem a perfectly reasonable thing for you to want to do.

Also, if mono in ubuntu is horribly in need of updating, then  what promted its early inclusion; what was the hurry since its not like linux is void of applications that mirror the abilities of said mono apps, or that  could have been made  to ( and in some cases have features they dont ) .


cheers
nl

---

### Post by igknighted on 2008-04-03
> **neighborlee said:**
> So this all means that the novel/M$ settlement has no bearing whatsoever on mono then right ?

What about the fact that Redhat seemingly atm anyway will have nothing to do with mono, is it like how gtk compared to qt or what exactly..I did ask a few times on fedora forum, but one of the head devs said 'you'll have to ask Redhat'. I dont know entirely how I feel about Redhat but they were the first on the block with support for linux in any meaningful way and the OS itself is free ( unless you want paid support), so it really does beg the question why   a free OS is staying away from mono doesn't it ?

I don't think novell/microsoft agreements have bearing on Mono, at least directly.  If novell is distributing source for mono then they are putting themselves outside any pact which involves SLED/SLES.  Therefor either the pact protects all users from something, or Novell themselves are at risk.

As for Red Hat, isn't this obvious?  Red Hat uses Java and JBoss to compete directly with Mono/.NET.  Why would they distribute software they directly compete with?  And I think it is perfectly relevent to mention that Fedora distributes Mono on the default live spins.  As someone who follows the Fedora mailing lists fairly closely, everything in Fedora has to be approved by Red Hat's legal department, so even though Red Hat isn't distributing it with RHEL, their legal team is OK'ing it.

> **neighborlee said:**
> Now we have something called silverlight ...if  M$ isn't trying to takeover the internet , and seeminlgy leave linux on the sidelines, then why didn't they release silverlight , ready to work in the big  3 OS's sametime ?

Is this any worse than Adobe?  At least microsoft is throwing linux a bone right from the beginning and aiding with moonlight development.  That's more than we ever got from Adobe with Flash.  Besides... moonlight is an open source implementation, correct (i could be wrong, I don't know much about it)?  We can patch our own bugs and not have flash-based security holes that we can't do anything about.  This sure looks like an improvement to me.

> **neighborlee said:**
> What was all that about ooXML again ?:

[http://arstechnica.com/news.ars/post/20070829-linux-foundation-says-ooxml-not-ready-to-become-an-iso-standard.html](http://arstechnica.com/news.ars/post/20070829-linux-foundation-says-ooxml-not-ready-to-become-an-iso-standard.html)

Again, people are going to use what Microsoft Office defaults to no matter what.  I'd rather see OOXML be not perfect, but better for cross platform use then for microsoft to give us the middle finger and do their own thing like they have in the past.  Besides, the EU is already forcing them to release more info on this stuff, if the format truly isn't implementable they will wind up in a court that has shown that they will play hardball.

> **neighborlee said:**
> There have been numerous 'patent' questions asked on this forum, and everyone here that seems to have a stake in what happens at ubuntu on the dev level is ignoring most of them, and I find that highly undesireable of a free OSS OS; I would ask they all be answered, which if your goal is mono inclusion in linux for the betterment of all , it would seem a perfectly reasonable thing for you to want to do.

Also, if mono in ubuntu is horribly in need of updating, then  what promted its early inclusion; what was the hurry since its not like linux is void of applications that mirror the abilities of said mono apps, or that  could have been made  to ( and in some cases have features they dont ) .


cheers
nl

No one wants mono as default becuase they love mono (aside from maybe novell cause they develop it... but that has nothing to do with ubuntu).  The call for mono is because no one has yet built applications that are as good as the mono ones.  Sure they aren't perfect, and mono in Ubuntu is horribly outdated, but there aren't great alternatives.  I am a pragmatist, I use the applications I feel are best.  If that means mono (and in some cases now it does) then I use mono, if it doesn't I use something else.  But why restrict a development choice.  I think it should be available for those who want to use it, and I think Ubuntu should keep the libraries current for that reason.  I also think that when someone writes an app that is the best at what it does, regardless of the language used, it should be considered.

Please, this whole discussion is so old... can we at least merge this to the super thread in the recurring discussions forum?

---

### Post by klange on 2008-04-03
If you ask me, .NET was the best thing MS ever did. It's simply, relatively speedy, easy to use and expand, and as Mono has shown, portable. I don't know whether it should be in by default, but it's not my decision. Personally, I don't use any .NET applications except ones I may write myself. I need a .NET language to compete in an upcoming programming competition, so for me, Mono is a must-have.

---

### Post by jfbilodeau on 2008-04-05
> **filipf said:**
> Also, ultimately software is all about end users. And they want features, they want eye candy, they want reliability and they want it fast. Writing software is all about developers. And Microsoft seems to understand that. They do provide fantastic tools and frameworks which make programming more efficient and pleasant. Why deny that to Ubuntu developers?

I can't disagree with the wants of the user. However, I refuse to rely on a 'standard' that is controlled by Microsoft. No matter what they are saying, Linux is they main competition right now, and anything they throw at us is not out of goodwill.

Take the following statement:
> Unable to offer developers a cross-platform development alternative to WLM, Apple wants to make sure that WLM-based applications take the best possible advantage of unique Mac OS features (such as Apple Guide, PowerTalk, QuickDraw GX, etc.). Apple hopes that this will prevent the Mac from becoming awash with WLM-based apps that treat the Mac as a least- common-denominator platform, which would just speed the demise of the Mac OS.

We don't care whether Apple succeeeds in its attempt or not. Their endorsement of the Win32 API on the Mac effectively ensures that ISVs write their apps first for Windows; that the resulting apps work best on Windows; and that the MacOS is the recipient of second-class, ported apps.

While the availability of WLM will cause many apps that might otherwise have stayed Windows-only to support the Mac too, each of these ported apps strengthens the WLM standard – which in turn increases the attractiveness of writing to Win32, and hence writing first and best for Windows.  (WLM = 'Windows Layer for Mac' [source: Gloklaw]("http://www.groklaw.net/article.php?story=20071023002351958"))

and s/MacOS/Linux/; s/WLM/.NET/

That's what scare me with Mono. .Net is not an open standard. I see no reasons to support Microsoft's agenda.

---

### Post by smartboyathome on 2008-04-05
Actually, Mono *does not break* any patents in Ubuntu. You can install the libraries, but those aren't included by default (I think this was different for Novell). Thus, Ubuntu really doesn' have anything to be worried about when it comes to MS playing the patent card. Then again, MS patented the double click, should we take that out as well?

---

### Post by neighborlee on 2008-04-07
> **smartboyathome said:**
> Actually, Mono *does not break* any patents in Ubuntu. You can install the libraries, but those aren't included by default (I think this was different for Novell). Thus, Ubuntu really doesn' have anything to be worried about when it comes to MS playing the patent card. Then again, MS patented the double click, should we take that out as well?

I'm afraid it doesn't matter what your claims are, its the facts that back them up, and atm everything one reads these days seems to be about the M$ machine stomping out competition in favor of 'their' agenda  in lieu of the greater community,  and if you missed the latest ooXML mess , well here it is:

[http://www.noooxml.org/](http://www.noooxml.org/)

[http://ooxmlisdefectivebydesign.blogspot.com/](http://ooxmlisdefectivebydesign.blogspot.com/)

this last url isn't a quick read but it seems objecvtive and well done so draw your own conclusions I guess.

The 'patent' story is ANYthing but clear considering the Novel/M$ mess, I dont think we need to revisit that  :)

Regarding the double click; do two wrongs make a right, that only muddies the water even further.

To the user above saying Redhat stays with Java , well maybe thats a good idea. Just because they stay with Java does not mean mono isn't a bad idea.

cheers
nl

---

### Post by smartboyathome on 2008-04-07
> **neighborlee said:**
> I'm afraid it doesn't matter what your claims are, its the facts that back them up, and atm everything one reads these days seems to be about the M$ machine stomping out competition in favor of 'their' agenda  in lieu of the greater community,  and if you missed the latest ooXML mess , well here it is:

[http://www.noooxml.org/](http://www.noooxml.org/)

[http://ooxmlisdefectivebydesign.blogspot.com/](http://ooxmlisdefectivebydesign.blogspot.com/)

this last url isn't a quick read but it seems objecvtive and well done so draw your own conclusions I guess.

The 'patent' story is ANYthing but clear considering the Novel/M$ mess, I dont think we need to revisit that  :)

Regarding the double click; do two wrongs make a right, that only muddies the water even further.

To the user above saying Redhat stays with Java , well maybe thats a good idea. Just because they stay with Java does not mean mono isn't a bad idea.

cheers
nl

They *can't* "stomp out" Ubuntu because of Mono, because if you check in the repos, the non-free portions are under a different package which isn't installed by default.

I know about the OOXML becoming the new standard, and I don't agree with it, but .doc has basically been a standard for a while, and if we go against it to the point of eliminating everything that has anything to do with MS, then you are eliminating a large portion of your user base (including me, since I need to be able to read/write .doc, and will soon have to do .docx). At this point, we have to give a little to get more users, unless Linux wants to revert back to having only a handful of users.

---

### Post by geoken on 2008-04-07
> **smartboyathome said:**
> They *can't* "stomp out" Ubuntu because of Mono, because if you check in the repos, the non-free portions are under a different package which isn't installed by default. 

I think the main argument here is that even the 'free' portions are patent encumbered. I personally could care less who developed a technology. I think MTP is a good protocol, and there are several other Microsoft creations which I have no problem with. 

My only fear is that Mono app's will become dominant in several key aspects of the OS (ie. F-Spot), and developments of alternatives will become stagnant. Then we'll be in a position where having the mono rug pulled out from under is will cause us o loose several key apps, and by extension make the DE seem outdated in comparison to alternatives (both free and non-free).

I think we should try and keep these debates more civil and realize that mono supporters think it's a good language, and can help the desktop while mono detractors think it's a patent encumbered language that can hurt the OS (if it gains popularity). It's not an argument between people who hate free software and people who blindly hate microsoft. Both sides have valid points, we should try to restrain ourselves from making brash accusations (something I'm guilty of as well) about people arguing the other side.

---

### Post by saulgoode on 2008-04-07
> **smartboyathome said:**
> They *can't* "stomp out" Ubuntu because of Mono, because if you check in the repos, the non-free portions are under a different package which isn't installed by default.

Isn't [this a listing of the components of the Mono package in Main](http://changelogs.ubuntu.com/changelogs/pool/main/m/mono/mono_1.2.6+dfsg-6ubuntu3/) and aren't 'libmono-winforms1.0-cil' and 'libmono-winforms2.0-cil' two of the technologies which MS claims to have claims on?

---

### Post by smartboyathome on 2008-04-07
I have not touched mono, so anything that is installed or uninstalled is default for Ubuntu. Anyway, those aren't installed by default for Ubuntu. Because they aren't installed, the most Microsoft can do is have Ubuntu remove those from the repos. I don't think any Ubuntu user is in any danger from mono, nor is Canonical.

---

### Post by Andrewie on 2008-04-07
Do you people actually think you're smarter then all the law experts at Red Hat, Novell, Canonical, KDE, and Gnome?

---

### Post by saulgoode on 2008-04-07
> **smartboyathome said:**
> I have not touched mono, so anything that is installed or uninstalled is default for Ubuntu. Anyway, those aren't installed by default for Ubuntu. Because they aren't installed, the most Microsoft can do is have Ubuntu remove those from the repos.

If the Mono package ships with Ubuntu, it does not matter whether or not it is installed by default -- assuming that some non-free components are part of the package (and that Ubuntu ships to or provides repo mirrors in a country where those patents might be enforced). As long as the package is on the ISO, Canonical would still be delivering infringing software.

> **smartboyathome said:**
> I don't think any Ubuntu user is in any danger from mono, nor is Canonical.

If components of Mono were found to be infringing upon patents, anyone in the applicable jurisdiction who has possession of the software would be at risk. Canonical might not be at risk owing to it being located outside that jurisdiction, but its users would be.

Personally, I do not recognize software patents. Though I live in the U.S., I will with clear conscience use FFMPEG, LIBLAME, JPEGs, GIFs, or whatever other allegedly patent-encumbered software is available under a Free License. I feel software patents are unconstitutional and would welcome the opportunity to denounce them as such in court. But that is my personal choice, and one for which I'm willing to suffer the consequences.

When I am presented with Free Software, I do not expect that it should be completely risk-free. What I *do* expect is for the person providing it to be honest about the risks involved -- and preferably that I am placed at no greater risk than they are. Neither of these two expectations are met by the Mono project.

---

### Post by smartboyathome on 2008-04-07
Canonical doesn't live in a country where it is inforced (they are on the Isle of Man). Mono does state that you can compile it to make it not at risk for patents (like Ubuntu has done) but there are patent-infringing portions in their faq (at least, I remember reading that, I can't find it right now).

---

### Post by saulgoode on 2008-04-08
> **smartboyathome said:**
> Canonical doesn't live in a country where it is inforced (they are on the Isle of Man). Mono does state that you can compile it to make it not at risk for patents (like Ubuntu has done)...
I just provided a link that indicates that Mono's [System.Windows.Forms](http://www.mono-project.com/WinForms) is included in Ubuntu's Mono package. One might wish to argue the applicability of [Microsoft's U.S. patent #20020059425](http://appft1.uspto.gov/netacgi/nph-Parser?Sect1=PTO1&Sect2=HITOFF&d=PG01&p=1&u=/netahtml/PTO/srchnum.html&r=1&f=G&l=50&s1='20020059425'.PGNR.&OS=DN/20020059425&RS=DN/20020059425) to the technology contained in System.Windows.Forms, but it DOES present some level of risk. 

In other words, I disagree that Ubuntu has compiled Mono "to make it not at risk for patents".

---

### Post by original_jamingrit on 2008-04-08
I agree, that it may be at risk for patent infringement.  But the risk is reasonably small.  Ubuntu already employs the msn protocol (pidgin) and ms word writing through OO.o.  While they're all arguably at risk for patent infringement, it's still all currently free software, it is not currently patent encumbered.

Were it to become non-free, it would go against what Ubuntu is supposed to stand for: providing an almost completely free OS.  If for some reason Mono was no longer considered free software, the worst that could happen is that version 8.04.2 would just have to come out a little early, sans a few apps.

So, it may or may not be an issue in the future, but as far as Hardy development goes it probably just isn't that important.

---

### Post by phil_white99 on 2008-08-24
"No mono" people - you just killed the Linux project at my company.

My team had convinced management that putting a 40-machine, wireless networked department on Linux should be tried.  We demo'd OpenOffice and Firefox to them and they saw the potential.

We started with Fedora and then OpenSuse, but their latest versions do not work with our WPA-PSK TKIP wireless standard - Network Manager is broken!  Management started to get impatient as another demo milestone date passed.  Next we got excited about Ubuntu.  Dell seemed to be liking it, and all 40 machines are Dell D600 laptops.  AND Ubuntu worked in our wireless environment!  The final stage of our demo:  Showing the corporate WinForms data apps working without modifications on Linux!  We had already done it on Fedora and OpenSuse and it was awesome on those distros!

Uh oh - "no mono" reared its ugly head.

We missed another deadline and scrambled to get the appropriate packages on Hardy - but then we found this "no mono" crap.  Even if we can tweak the OS to get our apps working, we started losing faith in Ubuntu.

We reported this to management and they gave up.  In the last meeting the CTO said, "You mean you haven't been able to find a single distro that does these simple things out of the box?"  No, we replied.  "But you said that Ubuntu showed promise."  Yes, but then we showed them the "No Mono" statements on this web site.  "You mean they are trying to force us to convert all of our WinForms apps to something like Java?"  Apparently.  "See, gentlemen, this is what is wrong with Linux today.  You still can't get a solid distro without tweaking it.  I consider this effort closed.  Maybe we'll revisit it summer 2010."

---

### Post by cardinals_fan on 2008-08-24
> **phil_white99 said:**
> "No mono" people - you just killed the Linux project at my company.

My team had convinced management that putting a 40-machine, wireless networked department on Linux should be tried.  We demo'd OpenOffice and Firefox to them and they saw the potential.

We started with Fedora and then OpenSuse, but their latest versions do not work with our WPA-PSK TKIP wireless standard - Network Manager is broken!  Management started to get impatient as another demo milestone date passed.  Next we got excited about Ubuntu.  Dell seemed to be liking it, and all 40 machines are Dell D600 laptops.  AND Ubuntu worked in our wireless environment!  The final stage of our demo:  Showing the corporate WinForms data apps working without modifications on Linux!  We had already done it on Fedora and OpenSuse and it was awesome on those distros!

Uh oh - "no mono" reared its ugly head.

We missed another deadline and scrambled to get the appropriate packages on Hardy - but then we found this "no mono" crap.  Even if we can tweak the OS to get our apps working, we started losing faith in Ubuntu.

We reported this to management and they gave up.  In the last meeting the CTO said, "You mean you haven't been able to find a single distro that does these simple things out of the box?"  No, we replied.  "But you said that Ubuntu showed promise."  Yes, but then we showed them the "No Mono" statements on this web site.  "You mean they are trying to force us to convert all of our WinForms apps to something like Java?"  Apparently.  "See, gentlemen, this is what is wrong with Linux today.  You still can't get a solid distro without tweaking it.  I consider this effort closed.  Maybe we'll revisit it summer 2010."
Sorry to hear that.  However, I don't think that we all need to use bloated and unnecessary software just because you need it.

---

### Post by Polygon on 2008-08-24
why does it matter if people dont want mono to be installed by default? you can just install it manually by yourself.

not to mention window doesn't do any of that stuff 'off of the box'. you have to install drivers...programs...

---

### Post by hanzomon4 on 2008-08-24
Why won't this thread die!!!!

---

### Post by Mr. Picklesworth on 2008-08-24
Sorry to be popping back in again, but I feel this must be repeated.

Mono is a Runtime Environment. It Does Not Get In Your Way Unless You Are Using It; it just exists on your hard drive, no more present than a photo collection sitting on a shelf.

The problem here is about support. The default apps are not just about convenience. It is about whether we can expect them to be bullet proof because testers are likely to have seen them.

To work in production environments, this needs to happen.
To be respectable, Ubuntu needs to work in production environments.
To continue being useful, Ubuntu needs to be respectable.


Edit:

Understood, dmizer. Thanks for the heads up :O
Also, to make matters worse, I even facepalmed the wrong message. Deep apologies, Polygon. I will hand in my image card and my quoting card.
To clarify, that was aimed at a more general belief that Mono was consuming actual active resources (yet somehow I managed to write that over a quote template off of Polygon's post... I was probably supposed to write something actually constructive and got lost along the way).


Edit Edit:

I officially declare myself vacated from this topic. My Mono note in Tomboy now contains these words: "Do not discuss except in emergency" and further explains that Mono is an inferior method of audio output. The other one I will forget about completely and leave to go its own way while I happily poke around in Python and Vala. Just so long as I still have a notes program called Tomboy, a good photo manager that never loses my existing photo database and a solid IDE with a cool interface (and those neato toolbars that can push against each other), I will be happy and will hopefully never think of this again.

Bottom line for my disappearance from threads tagged Mono: Just _do the right thing_ and make sure we don't get any regressions :)
Ta!

---

### Post by Dremora on 2008-08-24
I saw in that "blueprint" a lot of rabid anti-Microsoft crap that doesn't mention Microsoft is working with Novell to build Mono and has publicly committed itself to not sue anyone that uses it.

If Microsoft changes the specs, it will be to build upon what they have, this happens all the time with most software.

Ubuntu wouldn't be "Depending" on anything from a competitor (Microsoft), because most of the Mono spec that actually is important, is ECMA or ISO standards, it's no different than GNU project building their own C compiler while AT&T still owned all the IP behind C through UNIX Systems Lab.

That whole blueprint is crap, Mono is easily removed if you don't want it, and some very nice apps are written in C# that perform much better than anything written in JAVA is capable of.

---

### Post by cardinals_fan on 2008-08-24
> **Dremora said:**
> 
and some very nice apps are written in C# that perform much better than anything written in JAVA is capable of.
...such as?  I can't think of a single Mono app that I like.

---

### Post by Polygon on 2008-08-25
mono is still default though. I have looked through teh features of ibex, and it says nothing of removing tomboy and fspot, which means mono must be installed by default.

so by your point, it will still be bug tested by users, and be 'usable' in a production environment.

the guys post who i was responding too said that ubuntu didn't do everything it asked out of the box, but since mono was installed by default it does....yet he said the reason they didnt use it cause you cant use it without tweaking it......which i was confused about cause mono is installed by default, no tweaking is required.

i only said 'why does it matter if its not default' because the CTO or whatever seemed to only care if ubuntu worked out of the box with 0 tweaking, even if its to install mono to make winforms stuff work. he doesn't understand that the only reason some programs are default over others is that you cant physically fit more programs on the cd......

also,  dont tell me you dont have to tweak windows in some way to get it to work. claiming windows can work in a production enviroment "out of the box" is just a lie. Just installing one driver means it doesn't work 'out of the box".

---

### Post by Redache on 2008-08-25
> "No mono" people - you just killed the Linux project at my company.

My team had convinced management that putting a 40-machine, wireless networked department on Linux should be tried. We demo'd OpenOffice and Firefox to them and they saw the potential.

We started with Fedora and then OpenSuse, but their latest versions do not work with our WPA-PSK TKIP wireless standard - Network Manager is broken! Management started to get impatient as another demo milestone date passed. Next we got excited about Ubuntu. Dell seemed to be liking it, and all 40 machines are Dell D600 laptops. AND Ubuntu worked in our wireless environment! The final stage of our demo: Showing the corporate WinForms data apps working without modifications on Linux! We had already done it on Fedora and OpenSuse and it was awesome on those distros!

Uh oh - "no mono" reared its ugly head.

We missed another deadline and scrambled to get the appropriate packages on Hardy - but then we found this "no mono" crap. Even if we can tweak the OS to get our apps working, we started losing faith in Ubuntu.

We reported this to management and they gave up. In the last meeting the CTO said, "You mean you haven't been able to find a single distro that does these simple things out of the box?" No, we replied. "But you said that Ubuntu showed promise." Yes, but then we showed them the "No Mono" statements on this web site. "You mean they are trying to force us to convert all of our WinForms apps to something like Java?" Apparently. "See, gentlemen, this is what is wrong with Linux today. You still can't get a solid distro without tweaking it. I consider this effort closed. Maybe we'll revisit it summer 2010."

And Windows is 100% able to do this from a fresh install as well. I've had enough of reading that Linux doesn't have all of the functionality of Windows "Out of the Box" when it has more if you do it on an application by application basis (Linux tends to have a hell of a lot more). 

Of course Windows has it "out of the box" it's a Windows technology for christ sake. What would happen if people started whining that Windows doesn't have an Office suite "out of the box", absolutely nothing, people accept it. 

As far as I know Ubuntu still has Mono included so I don't see the issue here at all. 

Ok, to prove me wrong. Install a fresh copy of Windows, do NOT install drivers and compare functionality "out of the box".

---

### Post by frankhevans on 2008-08-25
I think the original poster was a little confused on the specifics of mono/ubuntu, but in a broader sense I agree that mono-paranoia is hurting Linux. Its more about perception.

---

### Post by alternatealias on 2008-08-25
even gNewSense 2.1 includes it by default on their LiveCD along with F-SPot and Tomboy - I just discovered it this morning when trying it out.

So much for the "Mono isn't pristine F/OSS software!" argument. That just got thrown right out the window.

---

### Post by neighborlee on 2008-09-06
> **alternatealias said:**
> even gNewSense 2.1 includes it by default on their LiveCD along with F-SPot and Tomboy - I just discovered it this morning when trying it out.

So much for the "Mono isn't pristine F/OSS software!" argument. That just got thrown right out the window.


That means nothing.

People do and use things all the time, no matter that its legal or patented.

Two wrongs ( of course, not from your perspective , being a,,  programmer ) certainly do not make a right . People make political decisions all the time, its nothing new and your naive if you think people aren't aware of these things ;)

It would seem poll wize that the commuity is very split on this, so it would seem logical to not make it default and let people decide on their own whether or not to install Mono, instead of having it _***forced***_ on them out of the box. Most wont need it , as no applications that come with ubuntu atm are mandatory for its inclusion. If you doubt the validity of that statement you are free to ask users of both RHEE and Fedora how they manage without them.

It's not just me either; I have good friends that wont use mono ( and are even rethinking using ubuntu as a result) because at least in part they know its coming from a entity that considers linux a threat. This secretive pact between you-know-who, does nothing to change that perception, and in a Microsoft engineers own words must be downloaded from Novel to even use it and whom  forbid programmers to even look  at certain code and the list keeps giving.

[http://www.gnome.org/~seth/blog/mono](http://www.gnome.org/~seth/blog/mono)

"  The ECMA RAND promise covering .Net, is about as trustworthy as Ballmer himself (define "Reasonable"), and has already been broken anyway, with the exclusive "protection" afforded to Novell in their pact with Microsoft. IOW the RAND "promise" is neither reasonable nor non-discriminatory. It is nothing more than a farce, and coming from liars like those at Microsoft ("Red Hat customers owe us money"), isn't worth the paper it's written on.  "   :  [http://uk.youtube.com/watch?v=5B0GTYfPoMo](http://uk.youtube.com/watch?v=5B0GTYfPoMo)

"  GNU/Linux has software that "clones" proprietary technology from other companies too, so why *insertnamehere* be so obsessed with the encumbered technology coming from just one company, Microsoft? It is simply because none of those other companies operate an illegal global monopoly, are guilty of anti-trust crimes on at least two continents, or behave like thugs and gangsters by spreading FUD about GNU/Linux ("Linux is a cancer"); sabotaging charities like the OLPC; and bribing Nigerian officials to dump Mandriva for Windows. Their corruption over OOXML is also well documented, bribing Swedish voters with promises of "market subsidies" in exchange for votes.  "

cheers
nl

---

### Post by smartboyathome on 2008-09-06
From the polls I have seen, it shows that the community is basically 50-50 on this. Because of that, I think that a decision either way would upset the community. No matter what, someone's going to be upset with the decision.

---

### Post by Canis familiaris on 2008-09-07
Did anyone read this?
> By the way this blueprint does not imply removal of existing mono applications. The aim on this blueprint is simply to not provide any mono library and application by default (i.e. ubuntu-desktop does not depend on mono). Until any threats came along the user will be able always granted the right to install his favorite mono app. through Applications Add/Remove.
Mono wouldn't be totally removed. Mono Programmers and Mono Application users would still be able to use it even if not included by default.

---

### Post by smartboyathome on 2008-09-07
Yes, but the Ubuntu devs have already said that they are keeping the default mono apps which are included in Ubuntu. It was decided last release and this release has already had feature freeze. I doubt that the devs will change next release either.

---

### Post by karellen on 2008-09-07
honestly I couldn't care less :)

---

### Post by neighborlee on 2008-09-08
> **smartboyathome said:**
> Yes, but the Ubuntu devs have already said that they are keeping the default mono apps which are included in Ubuntu. It was decided last release and this release has already had feature freeze. I doubt that the devs will change next release either.

It's really a shame the OSS community can't come together on this issue. Given Microsofts record I just find it really surprising anyone would  trust using any of their software in Linux, let alone their Opearting System at all, but then hey atm many have little choice on the XP side ( though I am working diligently at removing that dependency too ), but plenty of choice on the Linux side.

I guess users have a choice of staying with ubuntu, or using rhee or fedora where mono doesn't live,  and atm due to ubuntu's stance on this, the latre is where Im feeling the most secure. I admire both of them for different reasons obviously, but atm I feel cleaner and safer on the other side as do my friends.

If you are curious about their reasons feel free to come to
#lemmings which is on same server #ubuntu is.


cheers
nl

---

### Post by smartboyathome on 2008-09-08
You *can* remove Mono rather easily, neighborlee, using synaptic. Ubuntu distributes an old Mono package which is based on the ECMA standards (nothing patented), so there is nothing to be afraid of imo. Just because some of the people using Ubuntu are scared that Microsoft could be doing something illegal going against the ECMA standards (it would be illegal, since ECMA standards are just that, standards; they can't be patented over), doesn't mean that everyone feels that way. It even shows in the many polls that have been run concerning Mono that the community is split right down the middle, meaning if the devs side with you, then the other half of the community would argue that mono should be included.

---

### Post by neighborlee on 2008-09-09
> **smartboyathome said:**
> You *can* remove Mono rather easily, neighborlee, using synaptic. Ubuntu distributes an old Mono package which is based on the ECMA standards (nothing patented), so there is nothing to be afraid of imo. Just because some of the people using Ubuntu are scared that Microsoft could be doing something illegal going against the ECMA standards (it would be illegal, since ECMA standards are just that, standards; they can't be patented over), doesn't mean that everyone feels that way. It even shows in the many polls that have been run concerning Mono that the community is split right down the middle, meaning if the devs side with you, then the other half of the community would argue that mono should be included.

1) removing by synaptic: old reasoning ; It's like saying, well I have cancer, but oh btw it can be treated, but sorry to say mortality rate is terribly high so the risk remains. You stop the risk by healthy living etc.; and oh btw if you missed it, linux has been referred to AS as a cancer.

2) " The ECMA RAND promise covering .Net, is about as trustworthy as Ballmer himself (define "Reasonable"), and has already been broken anyway, with the exclusive "protection" afforded to Novell in their pact with Microsoft. IOW the RAND "promise" is neither reasonable nor non-discriminatory. It is nothing more than a farce, and coming from liars like those at Microsoft ("Red Hat customers owe us money"), isn't worth the paper it's written on. " : [http://uk.youtube.com/watch?v=5B0GTYfPoMo](http://uk.youtube.com/watch?v=5B0GTYfPoMo) < that addresses your ecma remarks

3) What part of 'we are a cancer', and the infamous novel pact and Microsofts all too obvious record of being a convicted monopolist gives any reason to feel secure about adopting any of its offerings ? ;)

We could give a pass on them in lieu of 'they have changed', but the latest OOXML fiasco alone, should be indication to any logical analysis that the change message is total folly. 

cheers
nl

---

### Post by cardinals_fan on 2008-09-09
> **neighborlee said:**
> 1) removing by synaptic: old reasoning ; It's like saying, well I have cancer, but oh btw it can be treated, but sorry to say mortality rate is terribly high so the risk remains. You stop the risk by healthy living etc.; and oh btw if you missed it, linux has been referred to AS as a cancer.

Wow.  How does the mortality rate remain terribly high when it comes to removing Mono?

---

### Post by neighborlee on 2008-09-10
> **cardinals_fan said:**
> Wow.  How does the mortality rate remain terribly high when it comes to removing Mono?

You would have gotten the inference if you had concentrated on the point I was making, but since you are clearly not doing that, I will conclude here by saying that having to remove it , IS the problem because having it there is a cancer, for all reasons stated in quotes I offered from the URL posted. M$ considers us a cancer, has taken steps against us at every turn ( remember the ballmer redhat comment ? ), and while many households depend on windows OS for  many things, this is only a temporary stranglehold it has , and we are all going to be so better off in the future when  free software ( like patents should not exist, as in freedoms; as if our VERY existence isn't owed to a  higher entity so you could argue that we own nothing therefore patents are immoral and ridiculous ) is the standard everywhere. That is why those here have a dream and are against all of this because it threatens free software and free OS's that they run on, and you  have only to look here to verify the threat:

[http://boycottnovell.com/2007/05/22/gplv3-study/](http://boycottnovell.com/2007/05/22/gplv3-study/)

cheers
nl

---

### Post by smartboyathome on 2008-09-10
Just because Balmer says something means we follow it? I think not! Mono produces some great programs imo, and as I have said before, Boycott Novell isn't a site to use as reference, as they are very blatently biased at trying to get rid of anything Microsoft. Microsoft could potentially attack us for other features as well, you know. NTFS support anyone? They could attack us for that. Samba/ Same. So, if we must get rid of one Microsoft spawned technology, get rid of them all.

If Open Source software is to suceed, though, then it must step on a few toes, show it is not afraid of Microsoft, and will stand up to them. The Mono in Ubuntu *isn't* the same as on the site (as said before), and that no sue agreement wouldn't apply to Linux as much since Linux is so hard to get at. Canonical is safe, and Microsoft doesn't have enough influence over the U.S. (yet) to make Linux illegal to use. If they even tried to sue us, the EU would go after Microsoft, as MS is already in hot water with the EU.

---

### Post by neighborlee on 2008-09-10
> **smartboyathome said:**
> Just because Balmer says something means we follow it? I think not! Mono produces some great programs imo, and as I have said before, Boycott Novell isn't a site to use as reference, as they are very blatently biased at trying to get rid of anything Microsoft. Microsoft could potentially attack us for other features as well, you know. NTFS support anyone? They could attack us for that. Samba/ Same. So, if we must get rid of one Microsoft spawned technology, get rid of them all.

If Open Source software is to suceed, though, then it must step on a few toes, show it is not afraid of Microsoft, and will stand up to them. The Mono in Ubuntu *isn't* the same as on the site (as said before), and that no sue agreement wouldn't apply to Linux as much since Linux is so hard to get at. Canonical is safe, and Microsoft doesn't have enough influence over the U.S. (yet) to make Linux illegal to use. If they even tried to sue us, the EU would go after Microsoft, as MS is already in hot water with the EU.

I am fine with getting rid of them ALL,  but we can start with the simple things, like not including things we can 'easily' do without. A world without patents is ideal, but hm good guess on that one ;)

Fear of M$ isn't the issue , but due diligence in all areas of life is never unwarranted, that is what those against mono are offering.

There are many more instances of threats from M$ than not, and the last url I just posted serves as clear evidence that they consider linux and the gpl its based on ( and the much superior, TEETHy new gpl3) as a major threat {cancer} .

We are taught from birth how to avoid danger; you avoid the risk factors and use clean free alternatives, which now clearly are in place :) ( fedora and redhat have made that committment firm if you aren't aware of it )

If you missed the seth url, it's a good read.

cheers
nl

---

### Post by cardinals_fan on 2008-09-10
> **neighborlee said:**
> You would have gotten the inference if you had concentrated on the point I was making, but since you are clearly not doing that, I will conclude here by saying that having to remove it , IS the problem because having it there is a cancer, for all reasons stated in quotes I offered from the URL posted. M$ considers us a cancer, has taken steps against us at every turn ( remember the ballmer redhat comment ? ), and while many households depend on windows OS for  many things, this is only a temporary stranglehold it has , and we are all going to be so better off in the future when  free software ( like patents should not exist, as in freedoms; as if our VERY existence isn't owed to a  higher entity so you could argue that we own nothing therefore patents are immoral and ridiculous ) is the standard everywhere. That is why those here have a dream and are against all of this because it threatens free software and free OS's that they run on, and you  have only to look here to verify the threat:

[http://boycottnovell.com/2007/05/22/gplv3-study/](http://boycottnovell.com/2007/05/22/gplv3-study/)

cheers
nl
Your explanation still makes no sense.  How is a cancer that can be removed anything like Mono included in Ubuntu?  If you remove Mono, it's gone.  That's that.

---

### Post by neighborlee on 2008-09-10
> **cardinals_fan said:**
> Your explanation still makes no sense.  How is a cancer that can be removed anything like Mono included in Ubuntu?  If you remove Mono, it's gone.  That's that.

I shouldn't even reply to this, so I 'll make this the last one, but I will do so by reiterating , that those in favor of mono never want to address the issues as they are brought up, but instead try to divert the discussion to immaterial things and its clear that is your attempt ;)

Address the issues I laid out, if you can because that is the important matter at hand, instead of distraction on irrelevance ;  substance, not things superfluous.

So go ahead address the things said in the seth url if there is a reply at all, then we can talk; else I figure this thread is done and you should concede mono should go, and let those that want them there, install them. { you could even offer them during install phase: mono or no , or just not at all like fedora and rhee so confidently do }

cheers
nl

---

### Post by smartboyathome on 2008-09-11
This is starting to sound like a political campaign. Neighborlee, Cardinals_fan poses a valid question, because Mono *is* easily removed, whereas cancer isn't very easily removed without radiation treatment, etc. Its not like you have to keep Ubuntu tied down for a day or so while  you scrub it down.

But I don't think the Linux people will back down because we are called a cancer. The future of the OS is very much political, as well as how the features are laid out and how usable it is. Ballmer says that Linux is a cancer because he is trying to keep people from switching to Linux, that doesn't mean it is one. Microsoft tried the same thing when they said Linux was less secure and not as easy to use as Windows Server, and they had to take down the site not that long ago.

Now they are mainly going *after* Redhat because their the only major U.S. company which hasn't signed a deal with Microsoft, not Ubuntu. If Microsoft wanted to even go after Canonical, like I said, they would have to deal with the EU, which would most likely charge that $4 billion fine for being a monopoly, which Microsoft doesn't want, as it would actually hurt them.

---

### Post by xlinuks on 2008-09-11
I say remove Mono and replace those programs with lightweight ones. Who wants Mono will install it himself, just like Java. I think it's fair.

---

### Post by smartboyathome on 2008-09-11
> **xlinuks said:**
> I say remove Mono and replace those programs with lightweight ones. Who wants Mono will install it himself, just like Java. I think it's fair.

Java's not included because it is proprietary and the OSS version is not up to spec yet. Removing the programs and replacing them won't work, unless there is one that fits what these two programs are doing and which has the same features.

---

### Post by cardinals_fan on 2008-09-11
> **neighborlee said:**
> I shouldn't even reply to this, so I 'll make this the last one, but I will do so by reiterating , that those in favor of mono never want to address the issues as they are brought up, but instead try to divert the discussion to immaterial things and its clear that is your attempt ;)

Address the issues I laid out, if you can because that is the important matter at hand, instead of distraction on irrelevance ;  substance, not things superfluous.

So go ahead address the things said in the seth url if there is a reply at all, then we can talk; else I figure this thread is done and you should concede mono should go, and let those that want them there, install them. { you could even offer them during install phase: mono or no , or just not at all like fedora and rhee so confidently do }

cheers
nl
My question still hasn't been answered.  A "mortality rate" implies that there is a significant risk or danger in removing a cancer, or that such an operation might not succeed.  Removing Mono from Ubuntu is absolute, and carries no risk.  It's gone, and your system won't be hurt when you remove it.

Quite frankly, I agree that Mono should not be included by default, because it (and most related apps) are large and bloated.  However, telling me that I'm trying to "divert the discussion to immaterial things" is ridiculous when *you* are the one who threw this discussion off course with an inaccurate cancer simile.

Let's all try to keep an open mind and move forward with the issue at hand.

---

### Post by Canis familiaris on 2008-09-12
> **smartboyathome said:**
> From the polls I have seen, it shows that the community is basically 50-50 on this. Because of that, I think that a decision either way would upset the community. No matter what, someone's going to be upset with the decision.

I don't think so. If we find better non-Mono alternatives for mono programs like Tomboy and F-Spot, Mono would be removed and not for a political reason, so people wont be upset. And Mono would still be there, just not installed by default.

---

### Post by smartboyathome on 2008-09-12
> **Anurag_panda said:**
> I don't think so. If we find better non-Mono alternatives for mono programs like Tomboy and F-Spot, Mono would be removed and not for a political reason, so people wont be upset. And Mono would still be there, just not installed by default.

But if we replace either of those programs with others, no matter what those other programs are, someone will be upset. But there aren't any programs which are to the devs liking yet which will replace tomboy and F-Spot.

---

### Post by Canis familiaris on 2008-09-13
> **smartboyathome said:**
> But if we replace either of those programs with others, no matter what those other programs are, someone will be upset. But there aren't any programs which are to the devs liking yet which will replace tomboy and F-Spot.
Well any decision in the world will make someone upset. We can't ever have  universal view, can we?

---

### Post by EnGorDiaz on 2008-09-13
i agree with the developers i think mono should be a choice alot of things would be a choice others the dependance of the developers would have to go up alot more and thats alot of work for them and other open source developers

if its got a bad dependancy structure then yes they shouldnt

---

### Post by neighborlee on 2008-09-13
> **smartboyathome said:**
> But if we replace either of those programs with others, no matter what those other programs are, someone will be upset. But there aren't any programs which are to the devs liking yet which will replace tomboy and F-Spot.

[http://www.associatedcontent.com/article/727751/zim_a_free_note_taking_application.html](http://www.associatedcontent.com/article/727751/zim_a_free_note_taking_application.html) < from here it would seem its better than tomboy on some fronts, and according to zim website it has some plugins I think tomboy does not. I dont know about its stability compared to tomboy, but maybe someone else can comment on that.

[http://www.ubuntugeek.com/zim-a-desktop-wiki-for-ubuntu-linux.html](http://www.ubuntugeek.com/zim-a-desktop-wiki-for-ubuntu-linux.html) < here too

It's clear tomboy isn't the only option here for notes taking.

I wonder what you mean by  'to their liking', is this posted somewhere and has it been discussed adequately ?

There is nothing wrong with gthumb compared to fspot so that arguement is also quite moot I believe.

GIve users the choice at install time to accept the risk mono presents, or not; that is the ultimate offering if we truly believe in the freedom of OSS, and that ubuntu represents that cause as well.

cheers
nl

---

### Post by neighborlee on 2008-09-13
> **EnGorDiaz said:**
> i agree with the developers i think mono should be a choice alot of things would be a choice others the dependance of the developers would have to go up alot more and thats alot of work for them and other open source developers

if its got a bad dependancy structure then yes they shouldnt

Yes, giving users a 'well defined' choice would indeed be good start and discussion could go from there. Fedora removed it entirely ( not from repo I dont think, and thats totally fine. ) , but hey I dont think anyone would be against choice.  My friend brought up a good idea, whereby couldn't the restricted driver  script allow this choice and then let the installer when its invoked, take it from there...


cheers
nl

---

### Post by neighborlee on 2008-09-13
> **Anurag_panda said:**
> Well any decision in the world will make someone upset. We can't ever have  universal view, can we?


Yes, to make a decision on the view that someone is going to be 'upset' is totally without logic. It's a nice principle that no one wants to have to upset anyone, but not being able to agree on various subjects makes this a factor of life we can't always avoid :)

cheers
nl

---

### Post by smartboyathome on 2008-09-13
> **neighborlee said:**
> [http://www.associatedcontent.com/article/727751/zim_a_free_note_taking_application.html](http://www.associatedcontent.com/article/727751/zim_a_free_note_taking_application.html) < from here it would seem its better than tomboy on some fronts, and according to zim website it has some plugins I think tomboy does not. I dont know about its stability compared to tomboy, but maybe someone else can comment on that.

[http://www.ubuntugeek.com/zim-a-desktop-wiki-for-ubuntu-linux.html](http://www.ubuntugeek.com/zim-a-desktop-wiki-for-ubuntu-linux.html) < here too

It's clear tomboy isn't the only option here for notes taking.

I wonder what you mean by  'to their liking', is this posted somewhere and has it been discussed adequately ?

There is nothing wrong with gthumb compared to fspot so that arguement is also quite moot I believe.

GIve users the choice at install time to accept the risk mono presents, or not; that is the ultimate offering if we truly believe in the freedom of OSS, and that ubuntu represents that cause as well.

cheers
nl

Here are some links for you to read up on why the devs chose F-Spot over GThumb:
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003055.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003055.html)
Tomboy, on the other hand doesn't have much discussion on the mailing list, you might bring it up if it is a concern to you.

Also according to that, the linux kernel itself breaks patents (according to Microsoft), and theres probably some MS-spawned protocol support and such in there as well. Should we get rid of that then?

---

### Post by neighborlee on 2008-09-13
> **smartboyathome said:**
> Here are some links for you to read up on why the devs chose F-Spot over GThumb:
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003055.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003055.html)
Tomboy, on the other hand doesn't have much discussion on the mailing list, you might bring it up if it is a concern to you.

Also according to that, the linux kernel itself breaks patents (according to Microsoft), and theres probably some MS-spawned protocol support and such in there as well. Should we get rid of that then?

Everything mono related is a concern is it not ? ( just ask seth @gnome.org )

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003109.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003109.html) < and there is this.

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003103.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003103.html) < does fspot yet have this ?

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003105.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003105.html) < this seems to be a recurring theme with some of you, and I have a answer for this as well:

[http://yro.slashdot.org/article.pl?sid=07/05/15/203218&from=rss](http://yro.slashdot.org/article.pl?sid=07/05/15/203218&from=rss)

and there is this to make java enticing especially now with java being free:

[http://news.cnet.com/2100-7344_3-5296787.html](http://news.cnet.com/2100-7344_3-5296787.html) < maybe in part this is why RHEE/fedora find java so appealing ?

cheers
nl

---

### Post by cardinals_fan on 2008-09-13
> **smartboyathome said:**
> Here are some links for you to read up on why the devs chose F-Spot over GThumb:
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003055.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-January/003055.html)

That makes me wonder if any of the devs in question have ever actually used gThumb.  Nautilus and EOG do not "handle 95% of gthumb's
functionality".  Oh, but F-Spot has a "better user experience".  Who needs functionality when you have such a great "user experience"?

---

### Post by smartboyathome on 2008-09-13
The free Java isn't up to spec yet from what I understand.

Also, F-Spot isn't being used as a **video** organiser, it is being used as a **photo** organiser, which means that they won't be including that DVD plugin unless it is default in F-Spot itself.

That Slashdot article actually makes this discussion all bad. Microsoft probably does violate patents from us. Have Microsoft name the patents which the **_ECMA-based mono package included in Ubuntu_** violates, and the devs would be happy to correct them or eliminate Mono altogether.

---

### Post by karellen on 2008-09-13
> **cardinals_fan said:**
> That makes me wonder if any of the devs in question have ever actually used gThumb.  Nautilus and EOG do not "handle 95% of gthumb's
functionality".  Oh, but F-Spot has a "better user experience".  Who needs functionality when you have such a great "user experience"?

I'd choose gthumb anytime over F-Spot

---

### Post by bruce89 on 2008-09-13
> **smartboyathome said:**
> Java's not included because it is proprietary and the OSS version is not up to spec yet.

I'm afraid that's rubbish. I've been using OpenJDK for about a year now. Anyway, it'd wouldn't be "included" as it is too big.

---

### Post by zipperback on 2008-09-26
> **fwilliams said:**
> 
If Ubuntu decides to keep mono, please recommend a Debian based distribution with Gnome.  Thanks.

If you want a Debian based distribution but are uncomfortable with having mono included with Ubuntu, then install Debian.

Debian is an excellent distribution.

And if you feel you need a package, but it isn't in the available Debian repositories, it is a fairly simply process to build the required .deb package, and you could always let the community know that you've built the package and make it available for them too.

- zipperback
:popcorn:

---

### Post by directhex on 2008-10-08
[http://www2.apebox.org/wordpress/linux/51/](http://www2.apebox.org/wordpress/linux/51/)

On a related note, I have some packages ready for anyone who wants them:
```
directhex@mortos:~$ dpkg -l \*moon\* | grep ^ii
ii  libmoon-dev                                0.8.1+dfsg-1                                               open source clone of Microsoft Silverlight - development files
ii  libmoon0                                   0.8.1+dfsg-1                                               open source clone of Microsoft Silverlight
ii  moonlight-plugin-core                      0.8.1+dfsg-1                                               open source clone of Microsoft Silverlight - core plugin
ii  moonlight-plugin-mozilla                   0.8.1+dfsg-1                                               open source clone of Microsoft Silverlight - Xulrunner 1.9 plu
```

---

