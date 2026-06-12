---
title: "exciting stuff happening with moonlight / linux"
date: 2007-09-05
forum: Programming Talk
---

### Post by triptoe on 2007-09-05
check it out 

[IMG]http://primates.ximian.com/~miguel/pictures/small-screenshot46.png[/IMG]

[http://tirania.org/blog/](http://tirania.org/blog/)

> Today we are formalizing a collaboration between Microsoft and Novell with the explicit purpose of bringing Silverlight to Linux and do this in a fully supported way. The highlights of this collaboration include:

The highlights of the collaboration are:

    * Microsoft will give Novell access to the test suites for Silverlight to ensure that we have a compatible specification. The same test suite that Microsoft uses for Silverlight.
    * Microsoft will give us access to the Silverlight specifications: details that might be necessary to implement 1.0, beyond what is currently published on the web; and specifications on the 1.1 version of Silverlight as it is updated.
    * Microsoft will make the codecs for video and audio available to users of Moonlight from their web site. The codecs will be binary codecs, and they will only be licensed for use with Moonlight on a web browser (sorry, those are the rules for the Media codecs[1]).
    * Novell will implement Silverlight 1.0 and 1.1 and will distribute it for the major Linux distributions at the time of the shipment. We will offer some kind of one-click install for Linux users (no "Open a terminal and type su followed by your password..." as well as RPM and DEB packages for the major distros and operating systems. 

---

### Post by Tomosaur on 2007-09-05
Good news, but tainted by the apparent resignation to using binary, proprietary codecs. Why can't the Moonlight developers just use some of the existing open-source codecs for proprietary formats? I hope they also build in support for purely open-source media, there's no reason why people should HAVE to use proprietary media if they object to it.

---

### Post by pmasiar on 2007-09-05
Scary. AFAIK there is no independent standard, so Linux to be compatible will be forced to do all the jumps and headstands MSFT will decide to do.

Even scarrier is, that this is interesting technology, and many will be tempted to use it regardless of the dangers. Looks like smart way to wedge a split between free software and open source.

---

### Post by triptoe on 2007-09-05
At the end of Miguels blog entry it says this: 

[1] Currently Moonlight video support has been prototyped using the fabulous and LGPLed ffmpeg engine for video and audio. We are unable to redistribute this code commercially due to licensing conflicts.

i don't think there is anything to worry about... .net and moonlight will be more open than the flash implementation is client side at least.

---

### Post by pmasiar on 2007-09-05
but flash is not open either. :-/ 

Saying "more open" is like "more pregnant". It either is open and free, or not, IMHO.

... "but Novel's jail cell has air-conditioner". So what?

We need independent open standard, managed by body independent of any single vendor. Until then, it is just picking what poison you like better.

---

### Post by Sun_Wukong on 2007-09-05
Well, it may be good for inter-operability but having such a Microsoft binary blob in a Linux distro stinks a little bit (Media Codec). I daily use the NVidia driver blob without any bad thought (and will probably switch to the Free driver when it's fonctionnal) but this is here the entry point for DRM in Free Software. And personnaly, I don't like it.

Furthermore, MS seems to be … euh… say "open" with this left hand, but in the right hand, the weaponry is quite heavy (the SCO FUD, the 235 so-called patent-violations, the hooligan way MS is pushing for OOXML to be accepted as an ISO standard, …). I don't trust this rattlesnake since a long time now.

---

### Post by triptoe on 2007-09-05
Mono is simply an implementation of an open specification...

Mono is no more in danger of patents than the kernel itself.. or any other open source software.. at least that is what I have garnered.

> Seth has raised some valid points  on the patent problem, as it related to Mono.

A big problem with everyone raising potential patent problems with Mono is not that they are wrong in any way, but there are a few problems with it:

    * Not using Mono in any shape or form is not a blank waiver against patents. That means that even if you choose to stick to your beloved C, Python, C++ or anything else, for any new software you write, you are likely to infringe on someone else's patents (or even the same ones that Mono could potentially infringe).
    * Patents can be: declared void with prior art showing that such invention did exist in the past. Alternatively, you can route around it by using a different technique than the one described in the patent to provide the same feature (or something close) to avoid infringing on a patent.
    * Most people have no idea of what a patent is, or how it works. The actual invention is the claims bit. Not the introduction, not the summary, not the background, not the references and not the drawings. They help in making the claims, but they are not the patent itself. If you want to play patent-lawyer on Internet, you should at least familiarize yourself with the process. 

Now, it is hard to argue with the nay-sayers about routing around the patent for two reasons: we do not know what might be patented and valid (ie, no prior art can be found or properly articulated) and most importantly for any given topic we can engage in weeks of discussion on what-if scenarios.

We do not plan on infringing patents, and if were to infringe on patent, we will either find prior art that renders that particular claim invalid, or rewrite the code to work in a different form. We do not like software patents, but we will abide by the legal rules.

If you can not think of a different way of running a C# program than the one that exists today, you are not a very imaginative/innovative programmer. The worst possible scenario is not `They will stop distribution forever'. The worst possible scenario is `They can stop distribution until we find a workaround'.

And again, remember, the software patents problem is not limited to the specific instance of Mono. Everything Seth said applies equally well to every bit of our open source stack today: do we infringe on a Microsoft patent? Do *you* know for sure you do not? Have you performed a patent search? On every possible bit?

Red Hat has chosen to adopt Java (despite the same potential problems with patents) and has decided that it is in their interest not to use C#/Mono. Like Red Hat's Seth states: this is self inflicted damage on their part, and they will not be able to ship any of our leading edge GPL code (Simias, iFolder, F-Spot or any of our future development tools).

Red Hat could either stop whining, and have their developers work in Mono and use Mono, and help us fight bogus patents or route around them, or they can keep posting to their blogs more fear-mongering. 

---

### Post by William the Conquerer on 2007-09-05
I wanna try it out!!  Anybody know any easy way to test it?

---

### Post by triptoe on 2007-09-05
Here is another update:

> Update: Some comments indicate that people would like to use GStreamer as the media backend (as GStreamer already has licensed codecs and some people might have purchased them already). We would be glad to merge any patches that people send us (copyright assignment required) to add support for GStreamer.

> Update: Some folks are asking whether they could use OGG for the video rendering in Moonlight. Today this is already possible because the media engine we use to prototype is ffmpeg which has support for this. From the standpoint of a desktop developer this might be enough, but for the web, the problem becomes an issue of compatibility with the Microsoft Silverlight implementation.

> t is released under LGPLv2.   As I mentioned on my blog entry, you can use
ffmpeg if you want to use a  100% open source solution on your desktop.   We
are just unable to redistribute that ourselves.

Miguel. 

---

### Post by pmasiar on 2007-09-05
> **triptoe said:**
> Mono is simply an implementation of an open specification...

Question is not C# language, but libraries.

>We do not plan on infringing patents, 

This is reassuring: willful infringement means triple the damages :-)

> and if were to infringe on patent, we will either find prior art that renders that particular claim invalid,

But it does not happen automatically: it's a judge's decision. So you still need to pay a lawyer to represent you.

> or rewrite the code to work in a different form. 

... which will cost time, effort, and possible may result in losing compatibility?

> We do not like software patents, but we will abide by the legal rules.

Why to stick your head into wasp nest? What is so special in Mono that you have to have it at any price?

---

### Post by triptoe on 2007-09-05
> **pmasiar said:**
> Question is not C# language, but libraries.

>We do not plan on infringing patents, 

This is reassuring: willful infringement means triple the damages :-)

> and if were to infringe on patent, we will either find prior art that renders that particular claim invalid,

But it does not happen automatically: it's a judge's decision. So you still need to pay a lawyer to represent you.

> or rewrite the code to work in a different form. 

... which will cost time, effort, and possible may result in losing compatibility?

> We do not like software patents, but we will abide by the legal rules.

Why to stick your head into wasp nest? What is so special in Mono that you have to have it at any price?

But all of that you just mentioned can apply to any open source software.

Here is a post on slashdot that sums it up:

> They aren't trying very hard. Java has a 15-year head-start on .NET. Meanwhile, .NET is vastly superior and is mopping the floor with Java. Why? Because Java sucks. Why should I have to mess with a classpath when I can just include references in a build file or dump a binary into a "magic" directory? Flexibility is no excuse for stupidity. This extends to the rest of the Java vs. .NET issue. Java is flexible but clunky and stupid. .NET lacks a tiny amount of that flexibility in a compromise to ease of use.

Basically, Microsoft finally got something right. That's not to say they didn't take some lessons from Java, but the fact is .NET is way nicer than Java.

I just hope the Mono guys make hay while they can and get Mono up to a fully-usable state before MS decides they've given enough engineering support to the Linux-support guys. I'd love to use .NET to make cross-platform apps that work as well as .NET on Windows does now.

---

### Post by pmasiar on 2007-09-05
Of course I would **never** suggested anyone to use crap as Java. Use Python for apps or C for libraries instead! :-)

---

### Post by triptoe on 2007-09-05
But thats just it.. with silverlight/moonlight we will be able to use python! 

IMO Microsoft does have an agenda with this but it is not what everyone thinks... their ultimate goal is to sell their development tools that will be built around it.. By making it more open and usable on all platforms it will just make it more of a standard which can only benefit them... by relying on the quality of their tools to build such applications. IMO this is a genuine good thing for everyone... but most likely the de facto IDE tools for building the applications will be built by MS because they do create good software and that will keep some developers on windows... but with the help of mono maybe not so much. The clients (the users) will be unhindered

> As I said back when this was announced, I think Silverlight is going to be huge. It's going to change the web -- it enables the move past web2.0 limited by the abilities of JavaScript and HTML. It's no glorified Microsoft-branded Flash plugin; the ability to write managed .NET code that runs right in the browser brings the full power of desktop development, and the full .NET professional development community, to the web landscape for the first time. Browser applications, powered by a plugin even dialup users can handle at a few megabytes in size, can be as rich and performant as their desktop counterparts while maintaining all the benefits of hosted "software as a service". Even our less advanced AJAX apps can be improved as Silverlight penetration increases over time -- JavaScript run through Silverlight (which has full access to the DOM just like it does natively) runs many times faster than any major browser's JavaScript parser.

I know I'm just rehashing the benefits we talked about back at MIX07, but I think this is something to watch. It'll take a while to pick up, like any new technology, but I think the web will be very different in 3 years and Silverlight will drive a lot of the innovation.

---

### Post by Tomosaur on 2007-09-05
It's true that Silverlight/Monolight looks like amazing technology, but the fact that Mono developers need to keep releasing statements regarding legal / licensing / patent issues is a little disconcerting. It's as if they're trying to make a philanthropic gesture about only tying **one** hand behind your back!

---

### Post by pmasiar on 2007-09-05
> **triptoe said:**
> But thats just it.. with silverlight/moonlight we will be able to use python! 


Not exactly: IronPython is close to CPython but not the same, and some core libraries are missing. It is wonderful and exciting and everything but it is **NOT** GPL code. For many people it is good enough (and IronPython license is rumored to be certified as Open Source soon), but for many other people, only GPL or Python (BSD-like) license will do, nothing less.

So this look like  an attempt to create small little incompatible garden and lock people in, again.

---

### Post by triptoe on 2007-09-06
.

> 
I'm going to be responding to the original premise of the thread--that Mono should be removed from Ubuntu, because it's an evil Microsoft product and because Novell is the devil. Reading the last page suggests that the argument has not changed significantly in the intervening 200 posts, and I doubt anyone will mind.

I don't believe that Mono should be removed from the basic Ubuntu installation, and I don't believe that the current demonization of Novell by the members of this forum is at all fair or accurate. Further, I would argue that several members of this forum have been spreading significant fear, uncertainty, and doubt (henceforth referred to as "FUD") about the products and players in question.

At its heart, Mono is simply a software implementation of certain standards and libraries. Most of these libraries were, admittedly, originally created by Microsoft and then published as ECMA standards, while a few remain non-standardized and a few are purely Mono creations. In this respect it is very similar to non-Sun open-source Java projects; both aim to create free software implementations of proprietary technologies (.NET and Java, respectively.)

So far as I can tell, however, there has not been any significant backlash toward the idea of using open-source Java in the Ubuntu desktop; indeed, I would not be surprised if at least a few of those involved with protesting the inclusion of Mono are using Azureus compiled with GCJ. This implies that the reason for distrust toward Mono is less on technical grounds, and more on distrust toward Microsoft, Windows, Novell, et al.

Now, I can certainly understand distrust toward Microsoft; they have not proven themselves to be terribly trustworthy players in the past, often suing companies over patented technologies or using anti-competitive tactics to force smaller vendors out of the market. I would even go so far as to say that Microsoft is not trustworthy, and that it's products should not be used. But we should be clear; *Mono is not a Microsoft product.*

The few aspects of Mono over which Microsoft could assert any control, however illusory or flimsy, are the reimplementations of certain non-standardized libraries such as Windows.Forms. These, because they are not part of the ECMA standards defining .NET, could theoretically be used for a patent infringement lawsuit against any company that sought to reimplement or redistribute them.

And yet Novell, Red Hat, Ubuntu, and the other distributions freely including Mono do not seem to be significantly worried. This is because, well, "they can play that game too." See, Mono (along with such potentially infringing technologies as "GNOME" and "KDE," if you've heard of them) are covered by a project of Novell, IBM, Red Hat, Philips, and Sony; the Open Invention Network (OIN.) The OIN holds a portfolio of patents, most notably the Commerce One patents on web services, which would be an enormous problem to Microsoft or virtually any other company. In this case, Microsoft would have significantly more to lose than Novell would by losing Mono, as their server products are reasonably successful. Add to this the problems Microsoft has with anti-monopoly organizations, and you have a situation where it would not be at all advantageous for Microsoft to sue.

With the legal problems sorted out, this comes down essentially to whether you want products with "Microsoft's hands in them." At this point, however, you're fighting a losing battle; concepts from Microsoft range across the entirety of Linux. It's impossible to find a computer today that doesn't have some debt toward Microsoft's innovations--one of the reasons they have so many patents to worry about.

And as for Novell, they have developers working full time on everything from the Linux kernel on up. You are very much using the wrong operating system if you want to abandon "all things Novell;" half of GNOME's developers probably work in the Ximian department, and significant numbers of KDE developers work in the SUSE areas.

So, really guys. Not to mention the many wonders Mono has to offer, I've just nullified the significant objections to it. Now can we **please** move on to more important things?

---

### Post by Tomosaur on 2007-09-06
Again, Microsoft's hand in Mono, however small - is not the point. Java is just as bad - perhaps even worse - the only reliable implementation of Java is Sun's own, whereas Mono is, as I've always said, very good at what it does, and it does it in an open way (whereas with Java, you're still locked out - but that is set to change). I am not against people using Mono / C# / .NET - indeed even I may find myself using it if I think it'll let me work on a particular project / problem better.

It's true that whichever way you turn you're going to have the same problems, if you concern yourself with licensing issues - and I feel that the easiest, and best, way to cope is to just ignore all patent issues and get on with it.

My problem with Mono is that, although it touts itself as free and open, it is knowingly implementing patented stuff which Microsoft has not explicitly given a universal royalty free license to. Mono is trying to have its cake and eat it. The Mono developers have, to their credit, stated that they are aware of MSs patents, and will try to work around them, find prior art to invalidate them, or just not implement them, if there is no other way. The problem here is that the ball is in Microsoft's court, thus, a company which almost exclusively deals in the business of proprietary software - of locking people out and controlling people's usage of that software - is influencing the development of a software project which is intended to be open and free to use, and is 'legally' limiting what people can do with that open source code (although I suspect most people just ignore Microsoft and do whatever anyway). This goes against the very definition of open-source and software freedom.

Perhaps Mono does receive too much flak for it, there are countless other areas of Linux with the same, or similar problems - but I suspect that people point the finger at Mono because of what it is - an implementation of something which is more or less specifically designed to ease the development of software which runs on Windows AND Linux. Yes, I'm aware this is not the stated goal of Mono, and is not the only use of it, but it is the most obvious deduction when you see 'Implementation of .NET'. The MS / Novell patent deal has only pushed Mono into the limelight as 'public enemy #3' (After MS / Novell). I'm not saying it's right, or even accurate, but that is the perception, and Mono doesn't help itself when it says 'but we're not the only one!'. Everyone is well aware that there are similar issues elsewhere, and everyone is aware of the OIN - but the fact remains that all of this uproar and debate is over the simple truth that software patents are a terrible idea and should be abolished altogether. Mono and Novell are simply a high-profile and obvious way to protest software patents - Novell now has a direct relationship with MS specifically regarding software patents, and if people can show that they don't like such deals, be it by extending the deal to every single Linux user through the GPLv3, or by simply boycotting Novell, and, by extension, Mono, then I guess that is exactly what they'll do. A little drastic, yes, probably incredibly unfair, but an opportunity is an opportunity, and it will be seized upon.

My personal position is somewhere in-between. I knowingly use patented stuff all the time - it seems incredibly difficult not to. I don't LIKE software patents, but if everything is patented anyway, what choice do you have? Mono is, at the end of the day, a tool. If you use it, that's fine. You probably won't ever have to deal with legal problems in any case, unless you're making a lot of money from patented stuff. For me - the fact that we even have to debate it suggests that it is not just 'ok' to use Mono. Mono devs have to keep coming out and make excuses, or show how it's 'safe' to use Mono, because they can just find prior art or whatever. The problem is not Mono, .NET, Microsoft, or Novell - it is that there is an industry based around patents and stifling competition and innovation, and that is what people object to. Microsoft just happen to be a particularly big player in the patent industry, and Mono just happens to 'possibly, maybe' liable to Microsoft. Novell has not helped matters with its patent deals with Microsoft, which gave some credibility to the idea of software patents, and to make matters worse, Novell sponsors Mono. It could have been anyone, it **happens** to be those three. I'm hardly militant about the subject, unlike some I could mention - but I do feel strongly about freedom. Software patents, to me, stifle innovation, creativity, and competition, and reduce the opportunity of talented people to push the boundaries a little. It's a little hard for me to explain it - but I was brought up in a very socialist environment, with a strong emphasis on helping the people who can't help themselves. Computers play a massive, massive role in today's world, and it seems to me that software patents and restrictive licensing are designed specifically to protect money. They're just a small part of a big system which I personally feel could be used to a far greater, more benevolent purpose. The irony of the matter is that Bill Gates - one of the key people who helped bring about such a system, and who has benefited from it the most, is by all accounts a pretty benevolent person. He gives enormous amounts of money to worthy causes - but the nature of the current system means that, if you don't already have tons of money to get licenses for patents and whatnot - it's incredibly difficult to:
a) Help yourself, if you are in a position whereby computers and software are able to help you.
b) Help others, if that is what you want to do, and can do it through computers / software.
c) Create anything, improve anything, customise anything.

The only real solution at the moment is to just ignore patents altogether - you're bound to step on someone's toes no matter what you do. At the end of the day - Mono indirectly gives credence to software patents, and I think software patents are bad. I am not boycotting Mono, I recognise that most of the time there's no real choice but to play by the rules of the patent system. Until software patents are abolished altogether, I believe Mono and Novell will always be criticised. It may not be particularly fair, but that's just the way it is.

---

### Post by HowardJZ on 2009-03-12
> **triptoe said:**
> check it out 

[IMG]http://primates.ximian.com/~miguel/pictures/small-screenshot46.png[/IMG]



This is what I think of moonlight/silverlight.

[http://boycottnovell.com/2009/03/11/abolish-mono-and-moonlight/](http://boycottnovell.com/2009/03/11/abolish-mono-and-moonlight/)

Get it off of Ubuntu soon.
Re-issue as maintenance releases every package that depends on mono, really anything coming out of Novell.

---

### Post by directhex on 2009-03-12
> **HowardJZ said:**
> This is what I think of moonlight/silverlight.

[http://boycottnovell.com/2009/03/11/abolish-mono-and-moonlight/](http://boycottnovell.com/2009/03/11/abolish-mono-and-moonlight/)

Get it off of Ubuntu soon.
Re-issue as maintenance releases every package that depends on mono, really anything coming out of Novell.

Try explaining your own opinion, or quoting someone who doesn't view lying as a way of life. It'll help you to better argue your position.

---

### Post by WitchCraft on 2009-03-12
> **directhex said:**
> Try explaining your own opinion, or quoting someone who doesn't view lying as a way of life. It'll help you to better argue your position.

I wouldn't use mono/.NET for the same reason i wouldn't use Java.

Technically speaking, it's utter crap: it's slow as hell, requires RAM like hell, it adds another pointless VM, just like Java, you get version dependance instead of operating system dependance. Hell I installed a .NET CD image burner on windows, and it took 5 MINUTES to startup the program, then it crashed - out of memory... No problem with a good old-fashioned C/C++ based CD image burner on the same hardware - in 5 minutes, 4 CDs burned. Same can be said for a .NET driver for PINNACLE DVB-T. Even worse, there it crashes on installation, and once you figured out how to get it installed without crash, it will take 10 minutes for your computer to startup!!! 

It's funny to say that the Linux DVB-T driver works problem-free (no recognizable system slowdown) - far better than the one Pinnacle specifically built for windows using .NET ...

Legally speaking it's a hughe risk, as .NET is more than just a dll used, it's the runtime, like glibc for C programms. 
If they forbid you to use mono for patent infrigment, you cannot simply discard a dll and replace it with another one, you have to rewrite the ENTIRE program!

And the closed-source blob MSFT codecs are, as already said, the entry-ticket for DRM to Linux.
Like it or not, but that's a fact.

And you also have to install the .NET/MONO framework. That's several gigs of hard-drive space - and what for? You could deploy any program with a 5 MB statically linked libraries, and that would still make less than these gigs used for the "framework"...

Also, your .NET/Mono/Java programs are far easier to disassemble - if you are a fan of closed-source.


These are just 5 very good reasons why not to use .NET. They apply to Java, too. There are much more reasons why not to use mono/.NET/JAVA, but I think these five are the most important ones.

If I would issue a Linux distribution, I would make sure mono/.NET & moonlight, as well as flash, do NOT get into the distro - just to make sure that NOT A SINGLE DEVELOPER can use it. The same could be said about proprietary file formats (e.g. MP3, DOC), which are an even bigger danger than closed-source software.

And for the morons who still use Azureus: 
It's crap!
Use rapidshare! You get 300 to 400 Kilobytes per second... That's a hell of a lot faster than the 80 Kilobytes you get out of azureus (bot only in the best case)!

Also, file-sharing can get you into incredible legal problems. 
So you would like to have a filesharing client that encrypts transmission & transmission origin & transmission target, so your IP cannot get identified.
Azureus does NOT do that (properly). But there are programs out that do!

---

### Post by directhex on 2009-03-12
Tone down the hyperbole.

I don't see any point in taking your points on individually as i really doubt you're interested, but things like "And you also have to install the .NET/MONO framework. That's several gigs of hard-drive space" might do better without made-up numbers (for reference, the footprint of Mono on Jaunty is closer to 20-30M)

---

