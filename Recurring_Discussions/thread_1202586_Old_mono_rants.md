---
title: "Old mono rants"
date: 2006-11-05
forum: Recurring Discussions
---

### Post by Xace123 on 2006-11-05
**This is the old ranting thread, if you wish to discuss mono , use the new thread [Monolith](http://ubuntuforums.org/showthread.php?t=1202591)**

I see that the ubuntu-desktop package depends on mono now. I'm investing heavily in Ubuntu and I think this is a bad decision, moreover when there are other alternatives.

Microsoft has already begin to threaten with lawsuits anyone not using their "Microsoft approved" Linux distribution, and it seems that in this new situation Novell is the new SCO. Microsoft's threats are unfounded but they have a lot of resource to invest in court, their objective is create [fear uncertainty and doubt]("http://en.wikipedia.org/wiki/Fear%2C_uncertainty_and_doubt") (FUD) about Linux.

Microsoft is already claiming that Linux distributions are infringing on their "intellectual property" (whatever that may be), but as with the previous SCO case they won't let anyone know what exactly that is. Their objective is to create doubt and fear, and there are hints that mono will play a big part in the future FUD strategy of Microsoft.

I think that people using Ubuntu has the right to choose whether they trust Microsoft and Novell not using mono to strong-arm Linux, or not. Now you can't use Ubuntu without using mono.

In this situation I do not want anything related to Microsoft or Novell in my systems because I do not trust Microsoft nor Novell.


I don't know if someone is working on this already but we need to get rid of the mono dependency in Ubuntu. Maybe include mono in an external repository.

---

### Post by cmost on 2006-11-05
Agreed!  By using Linux and open source, i've bid adieu to Microsoft for good!  I don't want anything to do with Microsoft, but now Mono now has a dotted line straight to Microsoft.  If supporting Ubuntu means indirectly supporting Microsoft-Novell, then I want no part of it.  Let users choose.

---

### Post by gummibaerchen on 2006-11-05
Why do you support MS when using Mono?

Try KDE, which does atm not use mono.

---

### Post by Xace123 on 2006-11-05
This thread comes from a "Help Forum", I think this topic is more appropriate here. (See my original post here: [http://www.ubuntuforums.org/showthread.php?p=1717673#post1717673](http://www.ubuntuforums.org/showthread.php?p=1717673#post1717673))

> **gummibaerchen said:**
> Why do you support MS when using Mono?

Try KDE, which does atm not use mono.

By using mono you support Microsoft because there is not a document where Microsoft explicitly says that holds no rights to any implementation of the .Net platform (which in essences is what mono is).

If we start using mono in Linux distributions, and Ubuntu in particular, to the point that it is an essential component then Microsoft could claim that all Linux distributions use "Microsoft intellectual property" and will begin to demand that enterprises and governments must pay a license to Microsoft to use Linux.


I have searched the forums but I have not found it being discussed. Maybe it was discussed in the mailing lists? Could anyone point me where to look at the discussion to include mono in Ubuntu (which are the advantages and disadvantages that mono brings)?

---

### Post by John.Michael.Kane on 2006-11-05
Theads merged...

---

### Post by kc8hr on 2006-11-05
Mono?

I am using Dapper, and there is no Mono on my system.

If it were, I would reformat and find a distro that does not use it. I haven't touched a M$ product in 8 years!

Tim

---

### Post by Kindred on 2006-11-05
I think it's in Edgy by default?  I haven't used any Mono apps and certainly wouldn't now, will be interesting to see what happens though.

---

### Post by Polygon on 2006-11-05
in dapper it doesnt appear to be installed by default, as i just reinstalled last-exit and i think it required mono so i had to go in synaptic and install it... so that only makes one program that uses mono on my system.

---

### Post by Wolki on 2006-11-05
Mono is protected by the Open Invention Network, so a patent suit would likely lead to the equivalent of a patent nuclear war - no one wants to do that. (see the discussion when Fedora started shipping mono, for example here: [http://gregdek.livejournal.com/4008.html](http://gregdek.livejournal.com/4008.html))

Mono is also largely based on open, standardized specifications. Parts of Windows.Forms (or somthing like that, the Windows GUI stuff) and other high-level stuff are patented, and mono implements them anyway, but they are done in a way so they can be very easily removed should the need arise. The stuff included with Ubuntu all use GTK# as their widget library, so it wouldn't affect them at all.

See also the Mono FAQ about licensing and Patents for more information. [http://www.mono-project.com/FAQ:_Licensing](http://www.mono-project.com/FAQ:_Licensing)

---

### Post by ComplexNumber on 2006-11-05
some default gnome apps use mono, so mono must be included. for example, tomboy is now part of gnome.

---

### Post by mostwanted on 2006-11-05
> **kc8hr said:**
> If it were, I would reformat and find a distro that does not use it. I haven't touched a M$ product in 8 years!

Mono is not a Microsoft product, it's an open source project primarily funded by Novell. The most useful parts of Mono (C# and the spec for the runtime) are ECMA standards which Microsoft officially has no control over; .NET is simply an implementation of said standards (even though Microsoft did invent the thing).

It's the same ordeal with JavaScript (Netscape's and now Mozilla's original implementation) and JScript (Microsoft's implementation). Both are implementations of an ECMA standard called ECMAScript.

The parts that are in the actual danger zone are the implementation of the non-ECMA parts of .NET (Windows-specific APIs like Windows Forms). Mono is basically in the same legal grey area as WINE here: it's an OSS implementation of a closed source, patented Microsoft API. The thing is, though, that those Windows-specific APIs are not used by Linux developers, but rather by Windows developers who want to easily port their applications to Linux. Removing these APIs from Mono would be no serious blow to adoption in the Linux world, it would just be a blow to attracting Windows developers.

---

### Post by Sushi on 2006-11-05
Off-topic, but... Miguel De Icaza is the #1 Microsoft-fanboy in the Linux-community. And no, it's not a case of him disliking MS less than most people do, he seems to be real fanboy.

---

### Post by Marthinus on 2006-11-05
I agree, Mono with the standard GTK# widgets is in no danger from M$. The Linux world should just stick to the ECMA .NET with added Gnome libs and it should be fine.

Dismmissing Mono because it is .NET is a mistake, and the panic relating to it is already the start of FUD but from the Linux community instead of the M$ community.

---

### Post by Synikk on 2006-11-05
I see problems ahead for Mono developers not under the protection of Novell/Microsoft, as well as distros shipping with Mono. I mean, Novell is now paying royalties to MS, as I understand it. What will this mean for other distros?

I don't have the best grasp on this situation, and I'm no patent lawyer, but the whole situation already stinks of deceit and ulterior motives. Balmer himself stated that MS was "open to talking with other distros," or something to that effect. To me, that smacks of "You either get approved by us or you get slapped with a lawsuit. Take your pick."

MS is not known for being very nice to its "partners."

---

### Post by Xace123 on 2006-11-05
The thing is do we really NEED to use mono? Do we really NEED to risk it? Microsoft is not only threatening with patents but with so called "intellectual property".

What makes mono so attractive for Linux? IMHO it makes sense in a Microsoft only environment to standardize all the pieces of the system. But I just don't see the benefits developing applications in a freedom of choice environment such as Linux.

If I have the freedom I choose not to use mono nor any product related to Microsoft or its ally Novell.

---

### Post by Synikk on 2006-11-05
> **Xace123 said:**
> If I have the freedom I choose not to use mono nor any product related to Microsoft or its ally Novell.

Exactly. The problem is, Ubuntu now ships with some Mono apps by default. Tomboy and F-Spot come to mind. I don't use either of those though. The only Mono app I currently use is Muine, which I use for throwing a quick playlist together.

---

### Post by Xace123 on 2006-11-05
> **Wolki said:**
> Mono is protected by the Open Invention Network, so a patent suit would likely lead to the equivalent of a patent nuclear war - no one wants to do that. (see the discussion when Fedora started shipping mono, for example here: [http://gregdek.livejournal.com/4008.html](http://gregdek.livejournal.com/4008.html))


Thanks for the link Wolki

The thing is, as I said do we really need to get entangled in a "patent war"?

And another interesting thing is, why are patents relevant for mono? Why do I need "insurance" from the OIN? I was led to believe that as mono only is an implementation of the ECMA/ISO specification it was alright.

---

### Post by mostwanted on 2006-11-05
> **Sushi said:**
> Off-topic, but... Miguel De Icaza is the #1 Microsoft-fanboy in the Linux-community. And no, it's not a case of him disliking MS less than most people do, he seems to be real fanboy.

Yet, he is also the founder of Gnome which was originally created as a GNU-endorsed alternative to then semi-proprietary KDE...

There's a difference between not hating someone uncontrollably and being a fanboy. Miguel likes C# and the CRL because it's good technology, not because he's a Microsoft fanboy.

---

### Post by ComplexNumber on 2006-11-05
>  There's a difference between not hating someone uncontrollably and being a fanboy.its doubtful if sushi is ever likely to see the difference.  in his eyes, anyone who doesn't hate something that he despises is a total fanboy. and of course, it applies to everyone else except him.

> **Synikk said:**
> I see problems ahead for Mono developers not under the protection of Novell/Microsoft, as well as distros shipping with Mono. I mean, Novell is now paying royalties to MS, as I understand it. What will this mean for other distros?

I don't have the best grasp on this situation, and I'm no patent lawyer, but the whole situation already stinks of deceit and ulterior motives. Balmer himself stated that MS was "open to talking with other distros," or something to that effect. To me, that smacks of "You either get approved by us or you get slapped with a lawsuit. Take your pick."

MS is not known for being very nice to its "partners."
actually, MS may have an ulterior motive. before novell signed the agreement with MS, MS couldn't have sued ALL linux distros using mono because, no matter how big MS is, it would have bitten off more than it can chew. and it would be seen as the bad guys, which, considering how hated MS are already seen by the public, they wouldn't have done themselves any favours.
but now that they've signed the agreement with novell and have welcomed other distros to do the same, they can now sue without being seen as being all that bad because they can turn around and say: "we actively encouraged other distros to do the same, but they metaphorically stuck 2  fingers up at us, so its not as if we are being unfair".

---

### Post by banjobacon on 2006-11-05
Saying Mono should be removed because it is "Microsoft-related" is a poor argument. If it's true that Mono does not infringe on patents, then there is no reason to remove Mono.

---

### Post by Wolki on 2006-11-05
> **Xace123 said:**
> 
The thing is, as I said do we really need to get entangled in a "patent war"?

And another interesting thing is, why are patents relevant for mono? Why do I need "insurance" from the OIN? I was led to believe that as mono only is an implementation of the ECMA/ISO specification it was alright.

No, we don't need to be entangled in a patent war. I personally think that software patents are a horrible idea, and think they shouldn't be done. But as we can't directly have abolish them ourselves, it's better to have some for protection.Even if Mono is just an implementation of a specification, there could still be some patents involved - if just for the fact that the patents are a mess and a lot of people got away with completely ridiculous patents. OIN serves as a deterrent here, in a similar way to how large patent portfolios work for large corporations.

---

### Post by DoctorMO on 2006-11-05
Tomboy and F-Spot are open source right? if you hate it that much fork them and rewrite them as C++ progs.

---

### Post by etelerro on 2006-11-05
I think it isn't a good idea to dump Mono in one day, but I think it is smart to slowly move away to other alternatives.

Of course the C# language is quite well, and together with GTK# it is a good platform to develop applications. But I think that when a company like Novell says that using Mono does no harm, and after that signing a devils-pact with Microsoft, it isn't a very good idea to trust Novell on their word, after all most Mono programmers work for Novell and creating new code under new licenses isn't so hard to do.

Though there are good alternatives, which aren't used enough I think. Next to PyGTK there are is also the wonderful Java GTK bindings.

I think that this "move away from Mono" doesn't have to come from the Ubuntu community, but more from the Gnome community.

---

### Post by pmj on 2006-11-05
Regardless of whether or not Microsoft will, or even can, sue makers of Linux distributions over mono, just the fact that we're having this argument is already hurting us. For that reason, I'm all in favor of getting rid of it. And it's better to do it now before too many applications depend on it.

And if someone could explain how to remove mono and all applications that depend on it without at the same time uninstalling most of my system, I'd be very grateful.

---

### Post by KaeseEs on 2006-11-05
One of the problems here is that unnecessary dependencies are taking away users' freedom.  It was a poor decision to make the ubuntu-desktop packages depend on Tomboy and FSpot.  If Gnome were installed on a clean system, for instance a fresh Slackware install, it would be perfectly possible to build Gnome from source without either program.  Thus, programs that are not necessary for another program to run (such as Tomboy and FSpot vis-a-vis Gnome & ubuntu-desktop) should be listed in the package as 'recommended' rather than required, so they can be uninstalled without hosing the 'main' program.

By the way, if there is a way to toss Fspot and Tomboy (which I have no use for) without waxing ubuntu-desktop, I'm all ears.

---

### Post by darkhatter on 2006-11-05
Microsoft could Sue every single Linux Developer on the face of the planet, and nothing would happen. Red Hat doesn't appear to be freaking out, why is everyone else doing it.

---

### Post by ago on 2006-11-05
I am in favor of getting rid of it. For one thing, it brings in quite a bit of dependencies. Moreover IF MS is going to sue, Novell will not be able to move a finger. And remember that MS does not need to sue, some FUD is enough to discourage several users. The fact that Novell is paying royalties corroborates such claims. And if we need to switch, the sooner the better. I look with great interest to XUL/XPCOM, it is a nice framework for several reasons (overlays, integration of remote and local apps, cross platform...). If we really need a new framework we should look more at Mozilla and possibly integrate it with python/parrot (pyxpcom is proceding slowly)...

---

### Post by Xace123 on 2006-11-05
> **DoctorMO said:**
> Tomboy and F-Spot are open source right? if you hate it that much fork them and rewrite them as C++ progs.

We are talking here about freedom of choice here, it's not about hate. I do not even know or care what Tomboy and F-Spot do, but I'm sure that there are other existing open source alternatives without the need to "rewrite them as C++ progs."

---

### Post by Xace123 on 2006-11-05
> **Wolki said:**
> ... there could still be some patents involved - if just for the fact that the patents are a mess and a lot of people got away with completely ridiculous patents....

You are right there Wolki, and that is the uncertainty in the Microsoft FUD against Linux.

My thinking is that it is a big mistake to embrace and make mono a cornerstone of Linux on the desktop, because it is uncertain whether Microsoft and Novell will claim ownership over it (or parts of it) later. Mono is "tainted".

---

### Post by JayTee on 2006-11-05
First they subtley infiltrate the OS of the opposition and then wait to strike when the timing is right. Sounds like plans for a coup 'd etat. I tried installing Mono on Dapper but it ran like crap and borked my keyboard settings so bad I had to remove it.

---

### Post by slimdog360 on 2006-11-05
mono - isnt that the kissing disease?

edit: yay 1000 posts. I must spend more time on these forums then I thought.

---

### Post by Synikk on 2006-11-05
> **slimdog360 said:**
> mono - isnt that the kissing disease?

Yeah, and now that Novell and MS are making out, Novell is going to end up spreading its disease all over the Linux community. Novell has its hands in Mono, and Mono has found its way into Gnome. We have a potential epidemic on our hands, to continue the analogy.

I'll bet you anything that within the next month or two we'll be seeing non-Mono clones of popular Mono apps popping up (Tomboy, F-Spot, Beagle).

---

### Post by Mr. Picklesworth on 2006-11-05
Yah, how about a .Net-inspired thing that is tailored toward Linux? (Not for running .Net applications and bothering me with the presence of .exes).
Besides, it's not like Tomboy runs on Windows...

It would be a much better use of resources, in my opinion, to build something fresh.

What *is* the point of it all anyway?
I know that Mono lets me run a "Hello World" program compiled on Windows via DSLinux... so I can understand its usefulness on a bigger computer as a more specific and detailed Wine sort of thing.
...But how is a .Net emulator (not really an emulator, I guess, but I can't quite put my finger on the right word) considered a viable platform to specifically develop for, contrast to regular code with a few helpful libraries?!


I also do not get it, and I want it to stop. Mono angers me; I have enough development libraries as it is (and even so, I am still unable to compile Tomboy stuff), and unless it replaces Java (which has been hideously misused to make ugly GUIs for ages) I see no point.

I think I've repeated myself 3 times now, so I should stop...

---

### Post by John.Michael.Kane on 2006-11-05
Has anyone been able to remove mono with out breaking the ubuntu install?

---

### Post by bikeboy on 2006-11-05
I think people are making a huge fuss about nothing. As has been stated, mono is not a microsoft thing, it's the Linux implementation of a standard, .Net is the Windows version. Whatever api's might be in there can be removed, so who cares if we're using something similar to .Net. There's a reason it's similar, they're based off the same thing.

Judging by the reaction in this thread it seems as though MS my be winning by the spread of FUD from within they Linux community. For once, they didn't even need to start the spread themselves. The best way to show MS that we have nothing to fear and that we're here to stay is to keep using whatever we want. Ditching mono means we have had some of our freedoms taken away from us. Is that not what Linux is about, freedom?

---

### Post by banjobacon on 2006-11-05
> **Mr. Picklesworth said:**
> I also do not get it, and I want it to stop. Mono angers me

Finally a good argument for the removal of Mono!

---

### Post by Mr. Picklesworth on 2006-11-05
> Finally a good argument for the removal of Mono!Hehe :b

Well, as I wrote, better that as a standard platform for everything than Java (which is, contrary to popular belief, very specialized).
I just think it works a bit weirdly, and the fact that Mono apps use .exes and .dlls kind of hurts the whole "Mono is not .Net" thing, even though it probably is completely true.

---

### Post by NoTiG on 2006-11-05
I like many of you also felt that mono was just an implementation of a standard. But if thats the case, then why would novell even accept something like this in agreement with microsoft to "not be sued" ? if there was no question about it whatsoever, then it would have been unnecessary and even unwanted IMO to "agree" to not be sued.

The fact that they now are "safe from being sued" actually makes me more nervous now because what other reason could there be for making such an agreement.

---

### Post by loell on 2006-11-05
i like c# and vb.net but my loyalty is to python, ruby and other gpl languages

i agree of getting rid of mono.

---

### Post by gnomeuser on 2006-11-06
The argument that we have protection under the OIN is flawed since that protection comes from Novells membership, they will however with this new deal not be able to enforce their obligations in the OIN to counter sue Microsoft if they attack vendors shipping Mono. 

We simply can't afford to ship Mono anymore, it's sad since I've grown to love Banshee, Tomboy and Beagle (and no Tracker doesn't come close to Beagle... yet) but in the interest of protecting Canonical and the Ubuntu Foundation it would be the only sane option.

---

### Post by Sushi on 2006-11-06
> **ComplexNumber said:**
> its doubtful if sushi is ever likely to see the difference.  in his eyes, anyone who doesn't hate something that he despises is a total fanboy. and of course, it applies to everyone else except him.

Dude, you are having some issues. Seriously. This is not the first time you have made your "comments" about me, so what exactly is your problem with me? Let's hear them. Do I need to take this up with the mods, because honestly, I'm getting sick and tired of this.

---

### Post by DoctorMO on 2006-11-06
Mono is an interesting platform but to be honest I don't care.

Novell has several things on Microsoft, and Microsoft has a number of thing on the entire comunity. it's a seperate thread about how much money it will cost MS to sue the entire world; I'm sure it'll make sense when the time comes.

But since I'm in Europe, software patents don't effect us here; you guys in the USA should really campain against them.

---

### Post by Shin_Gouki2501 on 2006-11-06
In my opinion Mono is very important for Linux/OS further Software developement. 
Maybe things will change when Java will go OS. But the concepts and benefits of VM based system is evident, especially under Linux..
wbr Shin Gouki

---

### Post by gerowen on 2006-11-06
I've got a bunch of the libmono packages installed, but Mono itself is not installed on my system, and I'm running Edgy.

---

### Post by ago on 2006-11-06
> **NoTiG said:**
> I like many of you also felt that mono was just an implementation of a standard. But if thats the case, then why would novell even accept something like this in agreement with microsoft to "not be sued" ? if there was no question about it whatsoever, then it would have been unnecessary and even unwanted IMO to "agree" to not be sued.

That is MS strategy, they make bilateral agreements "not to sue", the curious part is that NONE of the Linux companies/users can use ANY of those patents against MS, while MS can use ALL its patents against ALL of the linux companies/users/voluntaries except the people who signed agreements. In particular, any voluntary work (i.e. the heart of OSS) is fully exposed. So in practice, with each agreement the Linux community is giving up some retaliation weapon, while MS keeps its arsenal intact. Think of a country where individual divisions of the army make bilateral agreements with a not-so-nice neighbour and you get the idea... Dividi et impera...

---

### Post by ago on 2006-11-06
> **bikeboy said:**
> mono is not a microsoft thing, it's the Linux implementation of a standard

Yes it is. The standard was based on a Microsoft idea, other parties took part in the standardization process, but it is their baby, they have IP on it (whether they can enforce it or not).

Nobody denies it is a valid framework (they basically copied Java's framework and improved on it, which is not so tough after 5-10 years of experience and being able to afford a blank sheet with no issues about backward compatibility). But the point is that Microsoft is in the driving seat, they invented .Net, they decide about its development, they can push as many proprietary addons as they wish. Without those bits, you will be able to port some Mono apps to Windows, but not the other way around. Guess who gains from it. And please do not tell me that Mono is ever going to break away, because, particularly today, that is not going to happen. The best they can do is playing catch-up. Do you really want to build Linux Desktops on that? 

Moreover, Mono will help .Net become the dominant enterprise platform, adding "portability" and lowering geek resistance, but if .Net becomes the dominant enterprise platform do you think Linux is going to benefit from it? Will most companies be running .Net components on a Linux server using a crippled .Net implementation via Mono or on a Windows server using the "official" .Net framework? And if they use .Net what webserver do you think they will be running? What DB? You get the picture...

Unfortunately IMO we are in this situation because Java was not opensourced, which was a major mistake by Sun (and now they are paying the consequences...). But if we really have to pick a new framework, at the very least, we should get one where the community is in charge. And since we are moving toward a desktop which requires better integration of remote and local apps, web and desktop, we should look for a framework that is designed to do that. My best bet is a mix of XUL/XPCOM and a VM for language neutrality.

---

### Post by racoq on 2006-11-06
If u don't wan't to use mono, or feel unconfortable, u don't have to, unistall tomboy and f-spot, and mono, think its possible since only two applications in  Ubuntu use them, and install replacements like for instance the gedit (available in the repos) in place of tomboy.

A great alternative is to switch either to Kubuntu, or Xubuntu (my favorite option), since none of them use Mono, and They're latest releases are very stable (specially Xubuntu that i can say from my personal experience, besides u can gain a performance increase.

I think that Xubuntu and Kubuntu respect better the linux principles and licensing that the default Ubuntu distribution.

---

### Post by shining on 2006-11-06
> **Sushi said:**
> Dude, you are having some issues. Seriously. This is not the first time you have made your "comments" about me, so what exactly is your problem with me? Let's hear them. Do I need to take this up with the mods, because honestly, I'm getting sick and tired of this.

What about answering mostwanted comment ( #18 ) instead, and just ignoring ComplexNumber one?
That would be much more interesting.

---

### Post by Sushi on 2006-11-06
> **mostwanted said:**
> Yet, he is also the founder of Gnome which was originally created as a GNU-endorsed alternative to then semi-proprietary KDE...

He is, and I commend him for that. But that does not change the fact that he seems to be a MS-fanboy. Luckily GNOME has grown beyond De Icaza. Hell, De Icaza applied for a job at Microsoft in the past! Just because De Icaza started GNOME back then, does not mean that I should agree with him on everything. 

> There's a difference between not hating someone uncontrollably and being a fanboy. Miguel likes C# and the CRL because it's good technology, not because he's a Microsoft fanboy.

Microsoft has betrayed clients and partners. Repeatedly. Microsoft has a long trail of blood behind them. They supported SCO, they have done just about everything in their power to kill Linux. And now that they made a deal with Novell, De Icaza is bursting with joy. Has he forgotten history? Or is this a case of "THIS TIME it's going to be different! Honest!". De Icaza tells how good this is for Novell and Mono. Well, whooppee. But is this good for Linux as a whole? To me, this seems like a case of divide and conquer. I haven't seen any indication that MS has changed their ways, I haven't seen any indication that should make us trust Microsoft. Not one.

The SCO-case is not even over yet, and we are already making pacts with the "man behind the curtain". Is our memory REALLY that short? I wonder how the negotiations with MS went. Did MS say something like "um, sorry about that thing that happened short while ago. You remember? When we spead FUD about Linux, backed SCO so they could harm Linux as much as possible. When we did everything possible to harm Linux. Oh, sorry about Netware as well. But lets just forget all that. Here, sign this document. With your blood".

Those who do not learn from history are doomed to repeat it.

---

### Post by Sushi on 2006-11-06
> **shining said:**
> What about answering mostwanted comment ( #18 ) instead, and just ignoring ComplexNumber one?
That would be much more interesting.

done

---

### Post by forrestcupp on 2006-11-06
After all of the ideas that Microsoft stole, you all should be glad that someone is finally getting away with stealing a Microsoft idea.  If Mono is an opensource implementation of .NET, and all of the patented possibilities for trouble can be easily removed, I think we should embrace it.  Whether you like it or not, .NET is the way the world is going.

---

### Post by DoctorMO on 2006-11-06
C# was based on Java2, Microsoft just 'half inched' all the sun developers.

---

### Post by ago on 2006-11-06
The world will go where the most/best developers decide it to go. I am a developer and if I do not like it, I will not use it. It is as simple as that. I was in doubt until recently whether to move to Mono, now I have no doubt whatsoever. 

Not that the current tools are inadequate by any means, but I do not think that a full OSS framework is that far. Nice work is going on in the VM arena from LLVM to PyPy to Parrot, we have XUL, XPCOM and all sorts of libraries to cherrypick from. The only good thing about all this is that people will put more effort in our own garden...

---

### Post by boban on 2006-11-06
> **ago said:**
> The world will go where the most/best developers decide it to go. I am a developer and if I do not like it, I will not use it. 

That is not precisely true... If you mean OSS, then yes - its true... But when working for a company most of the time you spend coding in language that company has chosen, not you... :(

Btw. Do you know where can I find list of Novell's "products"? I want to get rid of everything that has to do with that company...

---

### Post by darkhatter on 2006-11-06
> **boban said:**
> That is not precisely true... If you mean OSS, then yes - its true... But when working for a company most of the time you spend coding in language that company has chosen, not you... :(

Btw. Do you know where can I find list of Novell's "products"? I want to get rid of everything that has to do with that company...

Novell works on too many projects, Gnome, KDE, mono....
if they double cross us with Microsoft its going to hurt bad.

---

### Post by boban on 2006-11-06
> **darkhatter said:**
> Novell works on too many projects, Gnome, KDE, mono....
if they double cross us with Microsoft its going to hurt bad.

I already installed XFce... List of Novell's software would be helpful - it's not that easy to find all "Novell dependencies" ;)

(and your warning should sound like this: "**when** they double cross us with Microsoft its going to hurt bad."... Microsoft have long history of betrayals)

---

### Post by DoctorMO on 2006-11-06
> if they double cross us with Microsoft its going to hurt bad.

The thing is, thanks to the GPL it's not going to hurt us, it's more likly going to hurt them badly.

Imagen if an EU judge or the US courts turn round as say that Novell can't distrobute Linux at all until they nullify their agreement with Microsoft because of the GPL. that would hurt a lot. although my bet is that it's either 1) completly ineffectual liceiencing or 2) expands to the entire community by proxy.

---

### Post by pitkali on 2006-11-06
Do you really think that not using mono will make you patent safe? Come on - even double click is patented.

---

### Post by darkhatter on 2006-11-06
> **pitkali said:**
> Do you really think that not using mono will make you patent safe? Come on - even double click is patented.

:confused: :confused: :confused: how can you patent that. I'm going to patent going to the bathroom using 2 hands :grin: .

---

### Post by luca.b on 2006-11-06
Mono was a bad idea from the start, because it's evident they would have ended up infringing patents (as mono doesn't implement only the ECMA standard). I strongly suspect the agreement was also partially due to the Ximian guys inside Novell (De Icaza in primis).

---

### Post by skymt on 2006-11-06
I support getting rid of mono, because I have an irrational fear of lawsuits. Despite the fact that it's simply an implementation of a standard, and Microsoft wouldn't have a leg to stand on if they decide to sue, I still think it's worse than, say, binary hardware drivers that violate the Linux kernel GPL.

Of course, Evolution is a Novell project, and connects to Microsoft Exchange servers, so we'll have to move to Thunderbird. Samba reverse-engineered Microsoft's SMB protocol, so it's obviously out.

Compiz is developed by Novell, so say goodbye to that, and Beryl along with it. XGL is obviously out, and AIGLX too, since it's often associated with XGL.

Firefox looks a lot like Internet Explorer, so they could probably hit us with a "look-and-feel" lawsuit there. So, elinks by default? Ditto Gnome and KDE. Did somebody say "taskbar"?

Let's not just worry about Microsoft. Apple is evil too, right? I mean, they make closed-source software, so they must be. Rhythmbox uses a library metaphor, which iTunes popularized. So, we should obviously bundle XMMS by default.

Let's all let fanaticism keep us from using useful technology. Great idea. Death to Microsoft!

---

### Post by ago on 2006-11-06
> **pitkali said:**
> Do you really think that not using mono will make you patent safe? Come on - even double click is patented.

Nope, I think that by not using mono I will not help MS expand its stronghold.

---

### Post by pitkali on 2006-11-06
Personally I think you're overreacting.

Regards,

---

### Post by darkhatter on 2006-11-06
> **skymt said:**
> I support getting rid of mono, because I have an irrational fear of lawsuits. Despite the fact that it's simply an implementation of a standard, and Microsoft wouldn't have a leg to stand on if they decide to sue, I still think it's worse than, say, binary hardware drivers that violate the Linux kernel GPL.

Of course, Evolution is a Novell project, and connects to Microsoft Exchange servers, so we'll have to move to Thunderbird. Samba reverse-engineered Microsoft's SMB protocol, so it's obviously out.

Compiz is developed by Novell, so say goodbye to that, and Beryl along with it. XGL is obviously out, and AIGLX too, since it's often associated with XGL.

Firefox looks a lot like Internet Explorer, so they could probably hit us with a "look-and-feel" lawsuit there. So, elinks by default? Ditto Gnome and KDE. Did somebody say "taskbar"?

Let's not just worry about Microsoft. Apple is evil too, right? I mean, they make closed-source software, so they must be. Rhythmbox uses a library metaphor, which iTunes popularized. So, we should obviously bundle XMMS by default.

Let's all let fanaticism keep us from using useful technology. Great idea. Death to Microsoft!

amen

---

### Post by ago on 2006-11-06
> Personally I think you're overreacting.

Maybe, but I prefer to be cautious today, rather than find out I was wrong tomorrow. And the more threats and FUD come out of ballmer mouth the more I am going to be determined to stay well away from anything he touches. Particularly since there are quite a few "safer" choices, that are no less promising or less effective, and differently from Mono, cannot possibly be piggy backed for other aims. Do I really NEED to use Mono (as a developer and as a user)? No I don't. Do I want to improve and foster Mono (and therefore .Net), or do I want to improve and foster one of the truly FREE and OPEN Source Software alternatives? It is a no brainer at this point for me, but feel free to make a different choice.

---

### Post by T_W on 2006-11-06
Microsoft has broad-based patent applications in for Mono.  

See:

[http://news.com.com/2100-1001-984052.html](http://news.com.com/2100-1001-984052.html)

> Microsoft is in the process of applying for a wide-ranging patent that covers a variety of functions related to its .Net initiative.

If approved as is, the patent would cover application programming interfaces (APIs) that allow actions related to accessing the network, handling Extensible Markup Language (XML), and managing data from multiple sources. APIs are the hooks in software that allow applications to work with another system.

The only thing that made Mono even a remotely mangeable risk was the OIN and supposedly the "CommerceOne patents" were the tactical Nukes of the OIN.

See:

[http://gregdek.livejournal.com/4008.html](http://gregdek.livejournal.com/4008.html)

> One of the biggest weapons in OIN is the set of Commerce One patents. Basically, Commerce One got lots of potentially scary patents on e-commerce stuff, and then they went bankrupt -- and the question "who's going to buy the Commerce One patents" was hot for a while. When a mystery buyer scooped them up, it was big news in certain circles.

Turned out that the buyer was Novell. And they turned around and contributed them to the OIN pool. Well-deserved kudos to Novell.

For those who prefer the "nuclear patent war" analogy: OIN is the NATO of software patents -- and the Commerce One patents are ICBMs.


The CommerceOne patents are owned by Novell.  Novell now has a covenant not to sue Microsoft.  Is the OIN worth anything anymore?

**[SIZE="4"]LOSE MONO!!![/SIZE]** Its not worth the risk for what ultimately amounts to: yet another photo app, yet another jukebox, yet another yellow stickies app and a port of Apache Lucene.

---

### Post by dca on 2006-11-06
Mono is just one facet.  M$ is going to go after the whole show...  They now have their in w/ Novell. The sad news, software patents will never go away in the US.  It's considered as to copyrighting 'War And Peace', copyrighting the next 'White Album', and copyrighting 'Star Wars'.  It's all intellectual property and if you had help writing it, it's intellectual property of the consortium or company who wrote it...  You can sell it, make money from it, the same way you make money from royalties, residuals, or just selling it in a boutique.  Protecting that is important.  You can't quash software patents because lines are blurred.  I mean, I know most people are bringing up the whole George Harrison's 'My Sweet Lord' being a rip-off of 'He's So Fine' would be a ridiculous contrast as to what M$ would do to the Linux community (Novell excluded, of course)...

---

### Post by ago on 2006-11-06
You can be wrong by not trusting Novell (and Mono) when they should be trusted, or you can be wrong by trusting them when they should not be trusted. The two errors are not symmetrical...

---

### Post by DoctorMO on 2006-11-06
bring it on I say.

---

### Post by bikeboy on 2006-11-06
> **skymt said:**
> Let's all let fanaticism keep us from using useful technology. Great idea. Death to Microsoft!

> **pitkali said:**
> Personally I think you're overreacting.


> **darkhatter said:**
> amen

> **DoctorMO said:**
> bring it on I say.

I absolutely agree with all of you. If worst comes to worst and MS sues, we simply remove the applications that are "offending". But it's hardly likely that if they finally decide to sue, they're going to get upset about mono and sue us all over that. They'll go after everything they can, by which time the mono issue will be a moot point. If that happens we'll get another sco, the Linux community will band together and hold firm, probably bringing down windows. The guys who are panicking over mono now will switch back to windows or go to mac and we won't have to listen to them again.

Meanwhile, I'll keep enjoying my Ubuntu the way I like it, F-Spot included.

---

### Post by ago on 2006-11-06
You only see Mono as a legal risk, but that is only part of the problem. Other aspects that you seem to ignore are:

[list]
[*]By fostering mono you help to spread .Net in the enterprise market, since you give .Net the "portability" seal. Do we really need another monopoly in the enterprise app market? 

[*] Enterprise apps easily leak to several server segments. Do we really need other monopolies in those segments?

[*]Unfortunately "portability" is unidirectional. Mono will help to port Linux apps TO windows, but windows will make sure that it is NOT possible to port apps FROM windows. And that can easily be done by adding all those nice proprietary add-ons that are NOT part of the standard, starting with windows forms... This will help reinforce the MS stronghold ALSO on the desktop market.

[*]The community has ZERO control over Mono direction, Microsoft sets the path, and Mono follows. That's it. The chances of Mono diverging are zero. Sure you can add one or two specific libraries, like GTK#, so what? They will simply be ported to windows... But you can bet that .Net3 features will be implemented, then .Net4, then whatever else MS decides. Not all of them, mind you, better to keep mono slightly crippled so that CIOs will have no doubt what server to install... Sure you can fork or go for gnu .net version, but we are talking about Mono in this thread... 

[*]Novell has entered into a bilateral patent agreement, and that is bad in itself, since all other Linux parties will not be able to take advantage either directly or indirectly of Novell patents in eventual litigations. Ballmer is giving the usual "with us or against us" speech. How can Novell expect to make the "with us" agreement pass as a progress for Linux is beyond me. Does that mean we have to boycott mono. YES. 

[*]To all of the above you have to add that you are using a product which involves a higher risk of IP litigations. IF you are lucky, it makes "only" a good argument for FUD. Why should you do so when there are several alternatives that avoid that problem at the root?[/list]

ANY of those by itself is a good enough reason to ditch mono...

---

### Post by KaeseEs on 2006-11-06
It seems to have been lost in the thread, but I and several others are still looking for a way to uninstall Tomboy, FSpot and the Mono libs without hosing other packages ( namely ubuntu-desktop ).  If anyone knows of a method to do this, it would be greatly appreciated.

    Also, if anyone knows of a way to set dist-upgrade to not install new apps, but just function as a - wait for it - distro upgrade, I'd much appreciate that as well.  Successive releases should get smaller on disk, not larger, dangit!

---

### Post by darkhatter on 2006-11-06
we could always push QT4...

---

### Post by pitkali on 2006-11-06
> **darkhatter said:**
> we could always push QT4...
Not until there's haskell support for it :P

> **KaeseEs said:**
> It seems to have been lost in the thread, but I and several others are still looking for a way to uninstall Tomboy, FSpot and the Mono libs without hosing other packages ( namely ubuntu-desktop ).  If anyone knows of a method to do this, it would be greatly appreciated.
Ubuntu desktop is just a meta-package. It contains only dependencies. Why object removing it?

> Also, if anyone knows of a way to set dist-upgrade to not install new apps, but just function as a - wait for it - distro upgrade, I'd much appreciate that as well.  Successive releases should get smaller on disk, not larger, dangit!
Remove packages such as ubuntu-desktop. I suppose the new apps you're writing about are new dependencies of that and other meta-packages.

BTW: I don't understand why should they be smaller. (And yet I do understand why do you object to them being larger.)

---

### Post by KaeseEs on 2006-11-06
I initially didn't want to wax ubuntu-desktop because there are some packages (ie ubuntu-usplash-artwork) that depend only on the meta-package, and thus get removed with it.  I solved this by making a list of everything aptitude wanted to kill and reinstalling those things that I wanted on their own.  

    As for why packages should get smaller over time:  that was partly tongue-in-cheek.  I should've used xml <curmudgeon> tags and made it explicit.  <dev>  Honestly though, if your package gets much bigger with time, it's probably a symptom of featuritis.</dev>  Or, you can be cool like the GNOMe folks and remove features and still make bigger packages](*,) 


PS - you were right about the new apps being mostly new dependencies of metapackages.

---

### Post by pitkali on 2006-11-06
> **KaeseEs said:**
> <dev>  Honestly though, if your package gets much bigger with time, it's probably a symptom of featuritis.</dev> 
Tell me about it ;) I agree they should not get bigger.

>  Or, you can be cool like the GNOMe folks and remove features and still make bigger packages](*,)
Good one :)

Regards,

---

### Post by forrestcupp on 2006-11-07
Give me a break, people.  An end-user's chance of getting sued for having mono on his computer is about the same as you getting sued for having downloaded mp3's on your computer.  They're not going to go after the end-user; they will go after the creators of mono.  MS won't do that anyway, they want to spread .NET anyway they can.  The argument against this is as bad as the argument against Adobe Flash.  Just because you don't like it doesn't change the fact that most websites out there use it.  Just because you don't like .NET doesn't change the fact that most businesses are going to .NET.  It's a waste of time to try to put out a forest fire with a garden hose.

I wonder if the Mono bashers have ever actually tried to program in C#.  It's a great language.

---

### Post by ago on 2006-11-07
> **forrestcupp said:**
> They're not going to go after the end-user; they will go after the creators of mono.

You got it all wrong. The creator of mono is Novell and MS cannot go against Novell according to their agreement. They will go against USERS and OTHER DISTRIBUTIONS that use Mono... Plus, as mentioned, the legal risks are only a part of the problem...


> The argument against this is as bad as the argument against Adobe Flash.
The difference is that by using Mono we help spread .Net. It is equivalent to complain about Flash and create Flash websites. That is not going to solve the problem, is it?

> I wonder if the Mono bashers have ever actually tried to program in C#.  It's a great language.
Nobody denies that.

---

### Post by boban on 2006-11-07
> **forrestcupp said:**
> Give me a break, people.  An end-user's chance of getting sued for having mono on his computer is about the same as you getting sued for having downloaded mp3's on your computer.  

RIAA... Does that name means anything too you? I don't mean to spread FUD - but think about it. A few sues against "normal" users can have impact on linux popularity... 
IMO one of big reasons for small popularity of linux is fear - fear of unknown (and whispers that linux is for geeks only). But every day new users are switching... And with every new user this fear is slowly fading away ("If he can install linux, I surly can too!").

On the other hand - all of this can have positive impact on linux and Microsoft this time won't play dirty... We can just hope for that...

---

### Post by T_W on 2006-11-07
> **forrestcupp said:**
> I wonder if the Mono bashers have ever actually tried to program in C#.  It's a great language.

Largely irrelevent to the discussion at hand, but yes I have programmed in C#.  A Java fork with operator overloading hardly justifies the risk involved.

---

### Post by boban on 2006-11-07
> **T_W said:**
> Largely irrelevent to the discussion at hand, but yes I have programmed in C#.  A Java fork with operator overloading hardly justifies the risk involved.

+1, but I would say that C# = Java + Visual Basic ;-) ... But IMO it has some great features (f.e. build in events and delegates).

---

### Post by DoctorMO on 2006-11-07
Bah you can do overloading in perl and events in python :twisted: 

But I agree with the consesus. the dangers outweigh the gains even though I don't think Microsoft will sue down this way.

---

### Post by darrenm on 2006-11-07
> **DoctorMO said:**
> bring it on I say.

Exactly. Microsoft could not risk any lawsuits against Linux for a number of reasons

1. Europe really hates Microsoft. The European courts are looking for anything anti-competitive to get Microsoft with. Microsoft slapping IP lawsuits against anything Linux would be like making a big line in the middle of the Atlantic. The patents wouldn't really work in Europe but would in the U.S. 

2. It's far too risky for them to do. All they have to do is lose 1 case in 1 country (and there are loads with relaxed rules and laws on this kind of thing) and it sets a precedent they couldn't hope to come back from. There are no such things as laws to a court, only precendents.

The best hope Microsoft have to stop the Linux "cancer" is to spread the FUD and the deal with Novell is purely to be able to spread some FUD by saying we won't sue Novell for any possible IP trespasses. In reality that has just as much weight as me asking Microsoft for £10,000 and then I won't sue them for any possible IP infringements of mine. SCO's gone, they got laughed out of court and now this is round 2.

---

### Post by Amon_Re on 2006-11-07
I fail to see the problem, if Novell is protected by this deal with M$, and they bring out new versions of eg. Mono that are still covered by the GPL, then basicly, there's not much M$ can do about it.

If they start bringing out code that's incompatable with the GPL, then don't use it.

Relax & enjoy the ride, looks like it'll get bumpy the coming months :mrgreen:

---

### Post by darkhatter on 2006-11-07
> 
Q8. What does this mean for Mono and its inclusion in non-SUSE distributions? Does Mono infringe Microsoft patents?

We maintain that Mono does not infringe any Microsoft patents. This agreement does not impact the rights and abilities of other distributions to bundle and ship Mono.

Novell is the leading contributor to Mono and we remain committed to the Mono project. Mono is a community project with many constituents and collaborators from companies, universities, governments and individuals.

The Mono project has a set of rules it uses to handle patents that might read on its implementation. The general policy is to work around, remove, or find prior technology on any patents that might read on any implementations in Mono. We continue to support this policy.


[http://www.novell.com/linux/microsoft/faq_opensource.html](http://www.novell.com/linux/microsoft/faq_opensource.html)

we can open f-spot now, its safe to come back.

---

### Post by sethmahoney on 2006-11-07
All this worry doesn't really matter much.  Unless someone wants to port tomboy, banshee, etc. over to python or whatever, its not likely that the mono dependencies are going to go away.  On the other hand, you probably can uninstall mono packages without seriously damaging your system - it will just make upgrading a pain in the ***.

---

### Post by DoctorMO on 2006-11-07
Clause 7 of the GPL does seem to prohibit Novels arangements some what.

---

### Post by darkhatter on 2006-11-07
> **DoctorMO said:**
> Clause 7 of the GPL does seem to prohibit Novels arangements some what.

> 
Q1. How is this agreement compatible with Novell's obligations under Section 7 of the GPL?
Our agreement with Microsoft is focused on our customers, and does not include a patent license or covenant not to sue from Microsoft to Novell (or, for that matter, from Novell to Microsoft). Novell's customers receive a covenant not to sue directly from Microsoft. We have not agreed with Microsoft to any condition that would contradict the conditions of the GPL and we are in full compliance.
Novell's end user customers receive a covenant not to sue directly from Microsoft for their use of Novell products and services, but these activities are outside the scope of the GPL.


Novell is for open source, lets stop the FUD

---

### Post by ago on 2006-11-07
> Our agreement with Microsoft is focused on our customers, and does not include a patent license or covenant not to sue from Microsoft

If they wanted to protect their customers, they could have done like red hat: if anybody sues their customers because of IP reasons, RH drops in their shoes and takes care of any legal issue directly on behalf of their customers. No such thing as covenants not sue, but eye for eye. And by refusing bilateral agreements with a single company, they avoid supporting the IP claims of that particular company. Well done RH! 

> Novell's end user customers receive a covenant not to sue directly from Microsoft for their use of Novell products and services, but these activities are outside the scope of the GPL.
Yes the covenants not sue from Miscrosoft is outside of the GPL, the problem is that Microsoft can sue ALL OTHER customers, and if that happens, can Novell help? No it can't, because it is giving something in return in order to protect ITS OWN customers... The fact itself that Novell is protecting their clients (and ONLY their clients) against lawsuits for their use of LINUX GPL PRODUCTS, implies that lawsuits are possible and that by itself is spreading FUD. The fact that this protection is sought via a covenant (and royalties) with a single company, reinforces the view that MS is THE company with the licenses on technologies used by LINUX... 

Have you noticed that MS has just started telling us which version of Linux is 'licensed'? I mean MS is behaving as THE authority for Linux! Do you think it is normal? And no, it is not a joke. Novell gave them such authority with their stupid covenants and royalties.

---

### Post by DoctorMO on 2006-11-07
Thats a dangerous trick to pull. it validates Microsofts IP while claiming to be doing something positive. no wonder Microsoft payed so much for this agreement.

Novel may be for Open source but it doesn't look like their for Free Software. I'll be watching with interest because all I see currently are a rather large amount of companies that are trying to aquire control over the open source and free software worlds; either because of fear or because of money and it's a dangerous precident.

---

### Post by darkninja on 2006-11-08
Though I am no fan of the way Novell has gone about striking a deal between themselves and Microsoft at the detriment of the other Linux distributions, I think Mono is too valuable to simply throw away.

Mono is a useful tool because it allows .NET applications (which are very common in business environments) to be ported to Linux easily without having to do a total rewrite, which will help Linux gain the corporate desktop.

I would think of the purpose of Mono for Linux would similar to that of WINE, that is better interoperability.

However given that .NET is still controlled by Microsoft and the risk of patent wars remain I do not think that the development of new apps under .NET should be encouraged, much like how Java development is not encouraged.

I'd advocate Python (w/GTK and QT bindings) as the best high level language for applications, due to the fact that it is controlled by the community, included in every major Linux distribution, easy to develop for and free of patent/freedom issues.

Of course, C/C++ is still fine too.

---

### Post by boban on 2006-11-08
> **ago said:**
> 
Yes the covenants not sue from Miscrosoft is outside of the GPL, the problem is that Microsoft can sue ALL OTHER customers, and if that happens, can Novell help? No it can't, because it is giving something in return in order to protect ITS OWN customers... The fact itself that Novell is protecting their clients (and ONLY their clients) against lawsuits for their use of LINUX GPL PRODUCTS, implies that lawsuits are possible and that by itself is spreading FUD. The fact that this protection is sought via a covenant (and royalties) with a single company, reinforces the view that MS is THE company with the licenses on technologies used by LINUX... 


You have some very good points here...And Microsoft has all the means to make this view a "common knowledge".. 

There are lots of people that don't know Linux. They would have eventually... But now - m$ will introduce linux to them - "licensed linux". And they will ask - "Hey! Why should I even bother to use this Linux thing? It isn't free, I have to pay Microsoft or their partners for it, I will have to learn hard (...). So I'll better stick with windows". 


> **ago said:**
> 
Have you noticed that MS has just started telling us which version of Linux is 'licensed'? I mean MS is behaving as THE authority for Linux! Do you think it is normal? And no, it is not a joke. Novell gave them such authority with their stupid covenants and royalties.

I respected Novell... But now - I hate them... It is a betrayal. It's selling your soul for the money. And in the short run it will help Novell... But trust is easy to fail and very hard to build up... I don't think that I will be able to trust Novell with anything now...

After thinking for a while - I really don't know if getting rid of mono is a good or bed thing. But I know - that making mono (and other stuff made by novell) "default" and depending on it is potentially very dangerous. It all should be optional but easy accessible - like closed source drivers...

---

### Post by ago on 2006-11-08
> **darkninja said:**
> Mono is a useful tool because it allows .NET applications (which are very common in business environments) to be ported to Linux easily

I disagree on this. Mono makes it easy to port Linux applications to Windows, not the other way around. There is much more in .Net than just the ECMA spec and most windows applications do implement those "extra bits". Those parts are patented, which means you cannot use them in Linux unless you pay royalties. Take for in instance system.*WINDOWS*.forms, is that part of the standard? Does the name of the library suggest anything to you? Mono (and dotgnu) are reimplementing them, but whether it is legal to use them is very arguable (if you are not a Novell customer that is). Without those libraries forget about porting GUI applications from windows, and the same goes for many other parts of .Net. Only applications that were designed strictly on safer mono libraries since day 0 can be ported, but chances are that not many windows apps fall in this category. On the other hand, particularly after the agreement, Mono will make sure that it is easy to port applications to windows.

So you have framework A that can run apps from framework A and apps from framework B, and you have framework B that can only run apps from framework B (unless you use a Microsoft licensed version for Linux...). If you are a CIO, which one are you going to use?

---

### Post by forrestcupp on 2006-11-08
> **ago said:**
> So you have framework A that can run apps from framework A and apps from framework B, and you have framework B that can only run apps from framework B (unless you use a Microsoft licensed version for Linux...). If you are a CIO, which one are you going to use?

If I were a CIO, I would either use Windows or a Microsoft licensed version of Linux.  All of this doesn't change the fact that Linux is excellent for servers/networks.

With how Oracle is screwing over Red Hat, can you really blame Novell for trying to get some kind of protection?  Think about it.  These are huge companies that have to pay a lot of workers' salaries.  These aren't just end-users with a Linux box in their bedroom where it ultimately doesn't matter what happens.  And now because of Oracle's dirty move it's possible that they could run a Linux giant out of business.

It is possible for the deal with Novell/Microsoft to not violate the GPL.  Have you ever heard of shimms?

---

### Post by ago on 2006-11-08
> **forrestcupp said:**
> With how Oracle is screwing over Red Hat, can you really blame Novell for trying to get some kind of protection?
Oracle is screwing up RH, Novell is screwing up Linux...

And there are various ways to protect your customers... See RH for a good example of customer protection from IP litigation which is beneficial to the Linux community at large... On the other hand, the way chosen by Novell is a disgrace for the rest of the Linux community. From now on we will have to live with "Microsoft licensed Linux"... 

Thanks a lot for the "protection"!

PS I would not be too surprised if Oracle was planning to purchase RH...

---

### Post by T_W on 2006-11-08
> **sethmahoney said:**
> All this worry doesn't really matter much.  Unless someone wants to port tomboy, banshee, etc. over to python or whatever, its not likely that the mono dependencies are going to go away.  On the other hand, you probably can uninstall mono packages without seriously damaging your system - it will just make upgrading a pain in the ***.


Tomboy is a glorified yellow stickies app.  We already had one of those written in C.

Banshee is a jukebox.  We already have Rhythmbox (also in C).  

No porting required.

Beagle is the only remotely interesting thing, and its basis is just a C# port of the (Java) Apache Lucene engine.

Other than the fact that Miguel has convinced a handful of developers to use it, what exactly does Mono bring to the table?

Put Mono and its apps in a repository holding packages with a questionable IP basis and treat it as another Wine.  Don't force it onto my hardware in the base install.

---

### Post by darkhatter on 2006-11-08
> **T_W said:**
> Tomboy is a glorified yellow stickies app.  We already had one of those written in C.

Banshee is a jukebox.  We already have Rhythmbox (also in C).  

No porting required.

Beagle is the only remotely interesting thing, and its basis is just a C# port of the (Java) Apache Lucene engine.

Other than the fact that Miguel has convinced a handful of developers to use it, what exactly does Mono bring to the table?

Put Mono and its apps in a repository holding packages with a questionable IP basis and treat it as another Wine.  Don't force it onto my hardware in the base install.

if you don't like the product shop somewhere else

---

### Post by skymt on 2006-11-08
> **T_W said:**
> Other than the fact that Miguel has convinced a handful of developers to use it, what exactly does Mono bring to the table?

C#, VB.Net, ASP.Net, IronPython, Boo, and others. All of which share a common set of object-oriented libraries, something no other technology has provided.

---

### Post by T_W on 2006-11-08
> **darkhatter said:**
> if you don't like the product shop somewhere else

Oh pardon me,  I thought this was a community-based distribution.  

I also though this was a discussion board for this community-based distribution.

---

### Post by T_W on 2006-11-08
> **skymt said:**
> C#, VB.Net, ASP.Net, IronPython, Boo, and others. All of which share a common set of object-oriented libraries, something no other technology has provided.

Untrue.

[http://www.robert-tolksdorf.de/vmlanguages.html](http://www.robert-tolksdorf.de/vmlanguages.html)

[http://www.parrotcode.org/languages/](http://www.parrotcode.org/languages/)

---

### Post by darkhatter on 2006-11-08
> **T_W said:**
> Oh pardon me,  I thought this was a community-based distribution.  

I also though this was a discussion board for this community-based distribution.

Ubuntu is a company owned distribution that is very friendly to the community. Ubuntu is also moving into the server market aka want a piece of Red Hat's share. If Mono is a problem they'll remove it, there is nothing to worry about.

---

### Post by skymt on 2006-11-08
> **T_W said:**
> Untrue.

[http://www.robert-tolksdorf.de/vmlanguages.html](http://www.robert-tolksdorf.de/vmlanguages.html)

> **The list linked to above]The following is a list of programming languages for the Java virtual machine aside of Java itself. Currently (spring 2005), it comprises close to 200 different systems. **It is a mix of experimental, research oriented implementations and of commercial ones.**[/quote]

Emphasis mine.  said:**
> [http://www.parrotcode.org/languages/](http://www.parrotcode.org/languages/)

[quote=The Parrot FAQ]Parrot is in the early phases of its implementation.[/quote]

I didn't mean .NET/mono is the only technology that's trying to do this. I just meant it's the only one that really has. .NET/mono is the only technology that can do the job well *right now*, and isn't that what's important?

---

### Post by DoctorMO on 2006-11-09
> Ubuntu is a company owned distribution that is very friendly to the community. Ubuntu is also moving into the server market aka want a piece of Red Hat's share. If Mono is a problem they'll remove it, there is nothing to worry about

Erm, no it's not Conical have their own Linux Distro; Ubuntu is a community distro that Conical helps support and organise. not even close to the same thing.

---

### Post by 3rdalbum on 2006-11-09
I don't think that Mono is in any way an infringement on anyone's IP or code. Sun couldn't go after the unofficial Java implementations. IBM couldn't go after Qemu for their PowerPC emulation.

Having said that, I think Python is a more appropriate language for the desktop. Mono should really just be for porting existing .NET applications to other platforms.

---

### Post by Choad on 2006-11-09
ok this thread has many pages so its probably already been mentioned, but novell made microsoft promise not to sue any free distribution over patents

[http://www.novell.com/linux/microsoft/openletter.html](http://www.novell.com/linux/microsoft/openletter.html)

> More importantly, Microsoft announced today that it will not assert its patents against individual, non-commercial developers. Novell has secured an irrevocable promise from Microsoft to allow individual and non-commercial contributors the freedom to continue open source development, free from any concern of Microsoft patent lawsuits. That's right, Microsoft wants you to keep hacking.

---

### Post by ago on 2006-11-09
And where exactly is the clause that says they cannot sue the USERS of such distros, i.e. us?

Not to mention that COMMERCIAL developers/companies can be sued and possibly even NON-COMMERCIAL organizations. I.E. they can sue Red Hat, Canonical, and all their developers, and even Debian is not safe...

So basically, according to MS, you can develop for FOSS provided you make no money out of it (unless you work for Suse), and you distribute your software via Suse ( because the users of such software can be sued)... 

So MS is telling us how to write LINUX software and how to distribute it!

How kind!

---

### Post by T_W on 2006-11-09
> **Choad said:**
> ok this thread has many pages so its probably already been mentioned, but novell made microsoft promise not to sue any free distribution over patents.

> More importantly, Microsoft announced today that it will not assert its patents against individual, non-commercial developers. Novell has secured an irrevocable promise from Microsoft to allow individual and non-commercial contributors the freedom to continue open source development, free from any concern of Microsoft patent lawsuits. **That's right, Microsoft wants you to keep hacking.**

Good lord, the arrogance of that statement.  As if we need Microsoft's pemission to "keep hacking".

1) The text you linked to says "individual, non-commercial developers".  I don't see anything about distributions.  The Ubuntu community is hardly an individual developer.  Canonical is clearly **not** non-commercial.

2) "That's right, Microsoft wants you to keep hacking".. as long as its in your parent's basement, not in any way organized, and certainly not used in any commercial setting... **ever**.  

Many thanks to Novell/Microsoft for granting me these rights.  Will they be "granting" me the right to vote or trial by jury any time soon?

---

### Post by T_W on 2006-11-10
> **Choad said:**
> ok this thread has many pages so its probably already been mentioned, but novell made microsoft promise not to sue any free distribution over patents

[http://www.novell.com/linux/microsoft/openletter.html](http://www.novell.com/linux/microsoft/openletter.html)

Groklaw on Microsoft's "Patent Pledge for Non-Compensated Developers":

[http://www.groklaw.net/article.php?story=20061109111321376](http://www.groklaw.net/article.php?story=20061109111321376)

> The patent covenant only applies to software that you develop at home and keep for yourself; the promises don't extend to others when you distribute. You cannot pass the rights to your downstream recipients, even to the maintainers of larger projects on which your contribution is built...

It's worse than useless, as this empty promise can create a false sense of security. Don't be confused by the illusion of a truce; developers are no safer from Microsoft patents now than they were before. Instead, Microsoft has used this patent pledge to indicate that, in their view, the only good Free Software developer is an isolated, uncompensated, unimportant Free Software developer.

---

### Post by warfly on 2006-11-17
Personally, I agree with many other posters who support getting rid of Mono.

But if that is too extreme a move, I'm all for just removing dependency of it from the ubuntu-desktop package and let the users choose.

That way I can happily enjoy using Ubuntu without having to install something I think really objectionable, and others who think otherwise still use their favorite apps built on it.

---

### Post by jhenager on 2006-11-17
After reading the actual "Non-Assertion of Patents Pledge", it appears that if you develop something yourself, you are in the clear, unless you file for patent protection against Microsoft, at which point you lose your protection, backdated to the original grant date. Anyone else that uses it is not ever protected.
One area in which Microsoft excels in is legal doublespeak, and that's what this is.

---

### Post by angrykeyboarder on 2006-11-18
[SIZE=3]If we got rid of mono we'd lose several apps I like. I have no problem with mono. Just because it's based on Microsoft's .net doesn't make it a bad thing.  It is [open source]("http://en.wikipedia.org/wiki/Mono_%28software%29") you know.

This vehement Anti-Microsoft attitude of so many Linux users just gives the community a bad name.

It's just childish.[/SIZE]

---

### Post by darrenm on 2006-11-18
> **angrykeyboarder said:**
> [SIZE=3]If we got rid of mono we'd lose several apps I like. I have no problem with mono. Just because it's based on Microsoft's .net doesn't make it a bad thing.  It is [open source]("http://en.wikipedia.org/wiki/Mono_%28software%29") you know.

This vehement Anti-Microsoft attitude of so many Linux users just gives the community a bad name.

It's just childish.[/SIZE]

You obviously haven't read the original post in this thread. Its nothing to do with being Anti-Microsoft, it's about getting rid of all threats of potential IP infringement.

---

### Post by warfly on 2006-11-18
> **angrykeyboarder said:**
> [SIZE=3]If we got rid of mono we'd lose several apps I like. I have no problem with mono. Just because it's based on Microsoft's .net doesn't make it a bad thing.  It is [open source]("http://en.wikipedia.org/wiki/Mono_%28software%29") you know.

This vehement Anti-Microsoft attitude of so many Linux users just gives the community a bad name.

It's just childish.[/SIZE]

As others have already pointed out, being an open source is no protection against IP lawsuits. Futhermore, as long as Mono trying to copycat APIs well beyond ECMA covered part of the .NET platform it effectively hand the big proprietary corporation right to decide the future of open source products built upon it.

Anyway just removing dependencies related to Mono from the core packages won't hurt anyone. I do respect your opinion. But if we could move them to multiverse, you can still use those Mono based apps without forcing everyone who thinks otherwise to do the same.

---

### Post by darkninja on 2006-11-18
[http://ometer.com/desktop-language.html](http://ometer.com/desktop-language.html)

2 years ago the GNOME devs decided that between Java and C#, C# was the best option for a high level language in GNOME.

I wonder now that both Java having gone GPL and MS/Novell spreading patent FUD if it will force the GNOME developers to reconsider their position. Python has come a long way too.

I have nothing against Mono for Linux existing for interoperability purposes however I think it would be foolish to make it an integral part of the GNOME desktop. Python and now Java are much more attractive options.

---

### Post by 3rdalbum on 2006-11-18
Python has always been a more attractive option. I hope to god's green earth that Gnome developers don't try to use Java for anything. Java is notorious for its applications not working correctly when there are slight variations in the computers. If Gnome incorporated Java applications or applets, the desktop would break for millions of users.

---

### Post by darkhatter on 2006-11-18
no one knows what their talking about, lets keep quiet. If (or when ) Microsoft says that Mono is a IP infringement, everyone including Novell will remove it, or change whatever as a problem, lock this thread then open it when someone actually releases information.

---

### Post by ago on 2006-11-18
> **angrykeyboarder said:**
> This vehement Anti-Microsoft attitude of so many Linux users just gives the community a bad name.

You got it the other way around, or maybe you just do not read the news... Mr ballmer just stated that if we want Linux we should only use MSuse or else... And for those of us who are FOoliSSh developers, we'd better keep the software for ourselves or else... i.e. he intends to squish the kernel, gnu, debian, ubuntu... i.e. us... 

Talk to me about anti-attitude...

Since WE have contributed millions of man hours to get where we are, many here feel that the only thing we owe to Mr ballmer is the finger, and we want to keep it that way, therefore we simply want to move into the stratosphere anything he touches... Which is a far shot from threatening users who make different choices, as MS does...

---

### Post by ComplexNumber on 2006-11-18
personally, i prefer C# over java. java applications always seem to be sluggish (its not just the slow start up times because that is to be expected with java due to the way it works with the JIT) and look ugly (swing is THEE ugliest and SWT which is meant to match the native toolkit still looks ugly and clunky). i used to like java a lot and found it very 'pure' when i first started programming in it in 1997, but its jsut too big and inefficient now IMO. hopefully they start streamlining it from now on instead of adding new features. because of its cross platform nature, i can't help but visualise java as being a man with his own house on his back (ie because its got to carry its own libraries and toolkit around with it everywhere it goes) :D.
as for microsoft threats, to hell with them. they wouldn't dare sue, so i'm more than happy to use and (eventually) develop using mono.

---

### Post by darkninja on 2006-11-18
> **ComplexNumber said:**
> personally, i prefer C# over java. java applications always seem to be sluggish (its not just the slow start up times because that is to be expected with java due to the way it works with the JIT) and look ugly (swing is THEE ugliest and SWT which is meant to match the native toolkit still looks ugly and clunky). i used to like java a lot and found it very 'pure' when i first started programming in it in 1997, but its jsut too big and inefficient now IMO. hopefully they start streamlining it from now on instead of adding new features. because of its cross platform nature, i can't help but visualise java as being a man with his own house on his back (ie because its got to carry its own libraries and toolkit around with it everywhere it goes) :D.
as for microsoft threats, to hell with them. they wouldn't dare sue, so i'm more than happy to use and (eventually) develop using mono.

While I do agree that Java's current cross-platform graphical toolkits are ugly as hell, I don't think that would be an issue once proper GTK bindings have been made and Java can interface with GTK just like other programming languages.

Memory usage is a bit of an issue yes, however once a program is adequately tweaked Java can run a lot nicer. Mono and Python aren't exactly lean either.

I also think Microsoft is full of hot air, however though this may sound somewhat emotive and illogical, if they're out to destroy Linux then why on earth are we helping them and relying on them?

The reasons why I'd prefer to see Java over Mono in GNOME include:

[LIST]
[*]We're not "pushing" Microsoft's standard for them. Sun have probably realised that they depend on Linux, they're not out to destroy us anymore.
[*]Java (or a free variant) is already included by default in most distros due to Java web content.
[*]Developers are still working on most of the classes for Mono, we don't have anything near full support for .NET. Java on the other hand is complete and now free.
[*]Java has been around a lot longer.
[*]Java is still THE language for huge commercial projects.
[*]Plenty of good Java apps already exist for Linux (Azureus/Eclipse/etc)
[*]Java is one of the most common languages taught to programmers in college.
[/LIST]

That said, I am also a big fan of Python and I think that it would be the best choice due to its awesome flexibility, easy syntax and strong integration into Ubuntu and other distros. No "freedom" issues with Python either.

---

### Post by T_W on 2006-11-18
> **angrykeyboarder said:**
> [SIZE=3]If we got rid of mono we'd lose several apps I like. I have no problem with mono. Just because it's based on Microsoft's .net doesn't make it a bad thing.  It is [open source]("http://en.wikipedia.org/wiki/Mono_%28software%29") you know.

This vehement Anti-Microsoft attitude of so many Linux users just gives the community a bad name.

It's just childish.[/SIZE]

Dude, if you're comfortable with having to pay Microsoft a royalty for using your Linux distribution, by all means **send them a check**.

Personally, I think they make enough money.  The thought of them imposing a Microsoft tax on software that they played no role in developing and made what results to negative contributions to sickens me.  

And before you accuse me of being childish:

[http://www.computerworld.com.au/index.php/id;839593139;fp;16;fpid;1](http://www.computerworld.com.au/index.php/id;839593139;fp;16;fpid;1)
> 
In comments confirming the open-source community's suspicions, Microsoft CEO Steve Ballmer Thursday declared his belief that the Linux operating system infringes on Microsoft's intellectual property.
...
Ballmer said Microsoft was motivated to sign a deal with SUSE Linux distributor Novell earlier this month because Linux "uses our intellectual property" and Microsoft wanted to "get the appropriate economic return for our shareholders from our innovation."

**Microsoft wanted to "get the appropriate economic return for our shareholders from our innovation".**

As per Mono, its an incomplete clone of .Net.  .Net is an incomplete single-platform clone of Java, which is owned lock stock and barrel by Microsoft.   Mono's contributions to desktop Linux amount to "yet another Jukebox program", "yet another Photo management program", "yet another yellow stickies program" and a desktop search engine based on an automated port of Apache Lucene.  

Big hairy deal.

---

### Post by darkhatter on 2006-11-18
Mono really isn't important, but we should keep it. Red Hat has said that they will rewrite anything that Microsoft "claims" is their intellectual property.

---

### Post by loell on 2006-11-18
> **darkhatter said:**
> Mono really isn't important, but we should keep it. Red Hat has said that they will rewrite anything that Microsoft "claims" is their intellectual property.

ok? so that would be like, writing from scratch? ;)

---

### Post by autoexec on 2006-11-18
im ok with mono, as long as its MONO, and not a .NET emu
if they get rid of winforms and related then i see no issue, MONO is following an open standard otherwise

any 'IP' that microsoft has on .NET that is used in MONO doesn't apply in most countrys

although anyone who doesn't live in a 'software patents' country can copy microsoft software patents all they like and they are immune

---

### Post by martinstevens on 2006-11-23
Looks like there are some people here that have the same feelings I have on the matter. I am disgusted with Microsoft's actions. As for Novel fat chance that I’ll ever be touching Novel products, Suse no more on my PC!

Does anyone have any thought on what will happen? Won’t the Linux community just change the code so Linux does not infringe on MS intellectual property? Wouldn’t it just come back to haunt Microsoft like a zombie, kill one and ten more of the living dead crawl out of the grave and come at them? A fight they will inevitably loose?

I understand that the inter operability aspect has IP issues but is there something I may be missing? Please enlighten me.

---

### Post by imagine on 2006-11-23
I agree with the thread starter.
My thoughts: Novell only recently started their business as a GNU/Linux-distributor by buying SUSE, a widespread, KDE based distribution. Then some Ximian people (including Friedman and de Icaza), whose company was also bought by Novell, first tried to set up Gnome as the default desktop in SUSE. As this plan to bring Mono applications into main part of the distribution didn't work out, the next approach was to replace the package manager in SUSE with Mono software. Apart from the fact that this new package manager written in Mono was slow to unusable, and for some users simply completely broken, I have to ask what the hell came over Novell to replace a working package manager - basically the core of a distribution - with a Mono application. Even Microsoft wasn't so insane to develop core parts of Windows Vista in C#/.NET (and the problems with the Mono package manager show that they were right doing so).

The only reason I can think of why Novell introduced a Mono based package manager in SUSE is that they want to push Mono into the Linux market by using all possible means. Not to forget, that the Ximian developers at Novell were also among the people who lobbied for the inclusion of Mono software in Gnome. And Novell, that is the same company, that now hops into the bed with Microsoft! A company which stated that all Linux users infringe their "intellectual property", except they are using products of Novell.
For me this is way too much coincidence.
Maybe I'm paranoid but in my impression Novell and Mono here play the role of a trojan horse in the free software world.



Besides there's another point against Mono, which was already brought up in this thread: The programming language market is a key market, controlling it is almost as important as dominating the market of operating systems. Everybody knows what happened to the less important markets of browsers, email clients, video players, etc after Microsoft managed to quickly gain big parts of them ("This site is optimised for IE"/"uses embedded WMVs", anyone?).
Now, one reason you often see in favour of .NET is is that it's cross platform. The reason for this is exactly Mono, which thereby helps spreading .NET. However Microsoft repeatedly stated that they do not support Mono (because "We have invested so many millions in .NET, we have so many patents on .NET, which we want to cultivate. .NET is the intellectual property of Microsoft"), there's no official approval of Mono. So as long as Mono is an useful idiot for Microsoft nothing will happen, but if it becomes a treat, then they will certainly take action.



I can't share the hope that Mono will allow more Windows desktop applications to run on Linux either. Whereas most applications developed with Mono also run on Windows, the opposite isn't true because Mono is always running behind .NET and important parts of .NET are proprietary. Also the most common IDE for .NET, Visual Studio, isn't available for Linux (and won't be), so Mono doesn't offer companies an easier transition from Windows to Linux than other languages would do.



So in the end I'm not saying that Mono or Mono based applications should be banned, maybe everything I wrote above and all the reasons against Mono given by others are wrong. But for all these reasons, and every single one of them, Mono shouldn't be part of the Ubuntu default install. Whoever needs it can find it in the repositories, the same way as eg Wine.

And btw, Red Hat already did what is proposed in this thread, namely getting rid of Mono: [http://www.internetnews.com/dev-news/article.php/3644981](http://www.internetnews.com/dev-news/article.php/3644981)

---

### Post by ComplexNumber on 2006-11-23
>  And btw, Red Hat already did what is proposed in this thread, namely getting rid of Monoi think red hat/fedora are the true heart and soul of linux. they always have been and continue to be so.

---

### Post by darkhatter on 2006-11-23
[http://www.novell.com/linux/microsoft/community_open_letter.html](http://www.novell.com/linux/microsoft/community_open_letter.html)

Even Novell says there nothing wrong with Mono, just move on

---

### Post by T_W on 2006-11-28
> **darkhatter said:**
> [http://www.novell.com/linux/microsoft/community_open_letter.html](http://www.novell.com/linux/microsoft/community_open_letter.html)

Even Novell says there nothing wrong with Mono, just move on

And why should anyone trust what Novell has to say on this or any other matter?

---

### Post by kaylus on 2006-11-28
> And why should anyone trust what Novell has to say on this or any other matter?

Because if we don't the [thwup thwup thwup] big, black [thwup thwup thwup] helicopters with microsoft agents [thwup thwup thwup] are going to carry us away!

Seriously, people. Quit the fear mongering and senseless statements. If you are hardcore and want to remove anything related to Novell or Mono, or whatever else you toss in tomorrow, why not go try Slackware.

Let's not pull a disintegration factor on Ubuntu - What's next: Mubuntu (Minus Ubuntu, Ubuntu without any apps that may infringe on others intellectual property!!). Oh, then of course you'd have to toss out the Ubuntu concept -- Silly!

Most of the fear that has been shown hear is highly irrational and not based in much logic. It is understandable considering the anti-microsoft sentiments abundant in Linux, but baseless prejudice does nothing for the furthering of the community. 

+ Kudos to the poster on (page 4?) for his wonderful sarcasm. If we apply the same logic (the risk might outweigh the benefit!) to everything we use on the operating system then we might be left with a software that can't compete, that isn't as usable and throws us back to the days of Slackware on floppy with a 600 page manual.

Regards

---

### Post by ago on 2006-11-28
> **kaylus said:**
> BIf you are hardcore and want to remove anything related to Novell or Mono, or whatever else you toss in tomorrow, why not go try Slackware.

Why don't you use slackware? Ubuntu is about the community and the idea is that community shapes Ubuntu, it does not just take it as it is. If several members have reservations vs Novell at the very least they should be allowed to voice their concerns and the devs should seriously consider whether it is appropriate to move mono away from main. You will still be able to install any mono app in 1 click, that does not mean that Ubuntu should be tainted by default. And as for the "mongering and senseless statements" here are some statements from Mark Shuttleworth's on the topic...
> 
    Novell&#8217;s decision to go to great lengths to **circumvent the patent framework clearly articulated in the GPL** has sent shockwaves through the community. If you are an OpenSUSE developer who is concerned about the long term consequences of this pact, you may be interested in some of the events happening next week as part of the Ubuntu Open Week:

    [https://wiki.ubuntu.com/UbuntuOpenWeek](https://wiki.ubuntu.com/UbuntuOpenWeek)

    ...I know that posting this message to an OpenSUSE list will be controversial. I'm greatly respectful of the long tradition of excellence in the SuSE product and community and have no desire to undermine that with this post. That said, **I think the position taken by Novell leadership in their contract with Microsoft is hugely disrespectful of the contributions of thousands of GPL programmers and contributors to SuSE**, and I know that many are looking for a new place to get involved that is not subject to the same arbitrary executive intervention. Ubuntu is one option, as are Gentoo, Debian and other communities. Please accept this mail in that spirit.


It would be quite ridiculous to slap Novell and then push their arguable technology in by default.

---

### Post by JeffS on 2006-11-28
Using Mono in Gnome/Ubuntu should not be a big deal.  C# and the CLI are ECMA standards, and Mono is an implementation of those standards.  Then GTK# is entirely an open source creation, providing C# wrappers around GTK+.

Really, patents or no, MS can't touch that stuff with lawsuits.  And they wouldn't even try, for reasons already stated in this thread.

I don't care if F-spot and Tomboy are present.  They are using GTK# and ECMA standard C#/CLI.  No big deal.

I also keep MonoDevelop on my Edgy install, mostly for the purpose of being somewhat familiar with C# and VB.Net.  My day job is mostly a MS house (we write the bulk of our stuff in VC++, with a smattering of VB).  I also do a lot of Java.  And because my day job requires .Net familiarity, it makes sense to be able to get comfortable with .Net stuff.  It's also useful for future job opportunities, even though with those I'll focus on Java and LAMP - it helps to also be competent with .Net.  Recruiters love programmers that are comfortable with multiple platforms/languages, because their clients typically have a mix a match of technologies.

Finally, the fact that Sun released Java under the GPL is huge.  For one, .Net is essentially a re-implementation of Java, with some extra bells and whistles (and syntatic sugar).  And guess what?  - Sun owns a number patents on Java.   And now that Java is GPL, those patents become safe for all users.  This spreads to .Net as well.  Sun could very easily slap a patent/GPL violation lawsuit on MS, if MS ever decides to be big bully with their .Net patents.  And I'm sure Sun would love to do that.

Also, GPL'd Java will give it a huge leg up on .Net.  It will get more adoption, more developer momentum, more uptake in businesses that are increasingly interested in open standards and open source (and avoiding vendor lock-in).  The market momentum behind Java will reduce .Net, and by extension Mono, to lower relevance.


All that said, I do wish F-spot or Tomboy or libMono were not part of the Ubuntu-desktop meta package.  All things Mono should be separate and independent, not affecting standard Gnome or Ubuntu.

---

### Post by ButteBlues on 2006-11-28
The posters at this forum are ridiculous. This forum hosts probably the single-most paranoid army of users I've ever laid eyes on.

Fact of the matter is, Mono is safe from lawsuits and it's a very good set of libraries that belong in the GNOME desktop with Tomboy.

---

### Post by ago on 2006-11-28
> **JeffS said:**
> All that said, I do wish F-spot or Tomboy or libMono were not part of the Ubuntu-desktop meta package.  All things Mono should be separate and independent, not affecting standard Gnome or Ubuntu.

This, and only this, is the issue of this thread. Whether or not individual users or developers decide to use mono is a personal choice. Whether or not Mono is used by default in Ubuntu is a statement and an encouragement. 

Mono apps should certainly be easy to install (G-A-I), but they should not be pre-installed, and possibly should be in multiverse.

---

### Post by ButteBlues on 2006-11-28
ago - Tomboy and Mono should be in Ubuntu for the same reason Epiphany should be: it's part of the official GNOME desktop.

As it is, I've totally dumped Firefox and honestly dislike its inclusion in Ubuntu over the GNOME web browser (even though I understand why Firefox is still here).

---

### Post by loell on 2006-11-28
fact of the matter is, many said gpl version 3 is ridiculous , but with the recent move of microsoft and novel , now majaority have positive views of gpl version 3 , if you think anti-mono is being ridiculous , well, think again ;)

---

### Post by JeffS on 2006-11-28
> **ago said:**
> This, and only this, is the issue of this thread. Whether or not individual users or developers decide to use mono is a personal choice. Whether or not Mono is used by default in Ubuntu is a statement and an encouragement. 

Mono apps should certainly be easy to install (G-A-I), but they should not be pre-installed, and possibly should be in multiverse.

My reasons for not wanting to include Mono as standard Ubuntu-desktop or in Gnome are more technical and freedom of choice oriented, rather than fear of MS lawsuits oriented.

On the technical side, including Mono as standard just introduces more dependencies, and makes gnome bigger, have more potential bugs, and makes it more difficult to manage.

On the freedom of choice side, many users don't want Mono on their machines/desktops, for various reasons.  But some do want it.  And since Mono is not essential for any functionality other than F-spot and Tomboy (both completely non-essential apps), it makes sense to me to just have Mono, and apps that run on or depend on Mono, as completely separate downloads either in the Universe or Multiverse repos.  Better still, put it in Multiverse, and users can either use Synaptic to get the stuff, or they can use Automatix.  

Actually, I look at the Mono situation as being similar to stuff like Flash, MP3 codecs, and libdvdcss2.  Those have legal grayness to them, at least in the USA, and having them as separate (but easy) downloads makes sense.  I'm guessing that the vast majority of Ubuntu users have used Automatix or EasyUbuntu to download Flash, MP3, libdvdcss2, and the like, despite legal warnings.  I'm guessing that Mono would be the same.

---

### Post by ago on 2006-11-28
> **a simple façade said:**
> ago - Tomboy and Mono should be in Ubuntu for the same reason Epiphany should be: it's part of the official GNOME desktop.

Ubuntu is not Gnome. 

In fact I remember reading some mono fan arguing for the inclusion of Mono within Gnome on the ground that distros where free to include it or not. Now we see people pushing Mono inside distros on the ground that Mono is in Gnome...

---

### Post by ago on 2006-11-28
> **JeffS said:**
> Actually, I look at the Mono situation as being similar to stuff like Flash, MP3 codecs, and libdvdcss2.
So do I

---

### Post by Xace123 on 2006-11-28
As **ago** says the whole point is about freedom and choice.

My original post was a question about the process that resulted in mono being an integral part of Ubuntu. Was it because it was part of Gnome and introduced by default? Were the implications, benefits and drawbacks of using mono considered? Do we really need it?

And it seems that not only the parts of mono that implement the Microsoft proposed Ecma-334 and Ecma-335 standards have made the way into the heart of Ubuntu. Please correct me if I'm wrong:

* Why is there an .aspx file in a default Ubuntu installation?
[PHP]/etc/mono/2.0/DefaultWsdlHelpGenerator.aspx [/PHP]
I was under the impression that ASP.NET was not covered by the ECMA standards.

* Why do I have a package in my machine named libmono-winforms2.0-cil? I thought that Windows.Forms was not part of the ECMA standards either.

---

### Post by tageiru on 2006-11-28
> **JeffS said:**
> On the technical side, including Mono as standard just introduces more dependencies, and makes gnome bigger, have more potential bugs, and makes it more difficult to manage.

How about less potential bugs? Protection from stack overflows, memory leaks and memory corruption are great when you want to reduce the amount of bugs.

> **JeffS said:**
> On the freedom of choice side, many users don't want Mono on their machines/desktops, for various reasons.  But some do want it.  And since Mono is not essential for any functionality other than F-spot and Tomboy (both completely non-essential apps), it makes sense to me to just have Mono, and apps that run on or depend on Mono, as completely separate downloads either in the Universe or Multiverse repos.  Better still, put it in Multiverse, and users can either use Synaptic to get the stuff, or they can use Automatix.  

Actually, I look at the Mono situation as being similar to stuff like Flash, MP3 codecs, and libdvdcss2.  Those have legal grayness to them, at least in the USA, and having them as separate (but easy) downloads makes sense.  I'm guessing that the vast majority of Ubuntu users have used Automatix or EasyUbuntu to download Flash, MP3, libdvdcss2, and the like, despite legal warnings.  I'm guessing that Mono would be the same.

That does not make any sense. By that logic we should put Linux in multiverse too since SCO have legal issues with it. Linux is in fact more dangerous as there is an ongoing trial. You can't say that about Mono.

---

### Post by ago on 2006-11-28
> **tageiru said:**
> By that logic we should put Linux in multiverse too since SCO have legal issues with it.
Last time I checked it was not SCO to decide about Linux kernel development, while it is MS to decide about .Net development and therefore about Mono development (do not even try to say that Mono is independent to any degree). Which also means that MS do have IP rights in .Net (and several patents), since they did invent .Net and they lead development, something that SCO cannot claim. And the ECMA is not protection at all, since only a small part of Mono is covered by the ECMA, all the rest has MS written all over it, and quite literally... Does "system._WINDOWS_.forms" mean anything to you? Do you think it is wise to include something called "system.WINDOWS.forms" inside a LINUX distro? 

Even assuming that Mono only implemented the ECMA standard (which is bulloks), you should know that according to ECMA, you can attach a patent to a standard (as MS did) and ECMA allows to license the product on a reasonable and non-discriminatory basis (known as RAND licensing). So ECMA does NOT guarantee that people implementing the standard can walk away without paying royalties. What is worse is that there&#8217;s no  definition for "reasonable", so patent holders (MS in this case) can charge anything. 

Not least, Novell, as Mark says, has circumvented the GPL, and that should not be allowed to happen.

---

### Post by kaylus on 2006-11-28
> **ago said:**
> Why don't you use slackware? Ubuntu is about the community and the idea is that community shapes Ubuntu, it does not just take it as it is. If several members have reservations vs Novell at the very least they should be allowed to voice their concerns and the devs should seriously consider whether it is appropriate to move mono away from main.

I am quite aware of the idea and ideal, though twisted logic and attempts to point out that I am saying you have no right to an opinion is not part of that ideal. If several members of the community have reservations about your (and the few others) paranoia concerning Mono at the very least they should be able to voice their concerns so that any decision made reflects the full will of the community, right?

> And as for the "mongering and senseless statements" 

And? Your point? Stating something that WAS NOT said in this forum, or on this topic, does not demonstrate clearly that alot of the statements made over the last 11 pages were not "Fear mongering" or "senseless". Sorry. Misdirections work in politics better.

By all means, express your opinion, but do realize that opinions that don't appear well-educated or just seem paranoid are less likely to be looked at with concern.

<snip rest...>

I snipped the rest after reading the last few posts in this forum, it's hard to take seriously the claims laid by people who are so fanatical about opposing any they deem fit to oppose. I will concede that the issue is good to discuss, but I have seen little to show why it should be removed (from a technical standpoint, or a community standpoint) other than the fact that a few want it removed from (mainly) anti-ms/anti-novell sentiments/fear.

So, fine -- I saw a reason why someone doesn't really care for it to be there, how about a good technical reason that shows why it should be removed?

---

### Post by ButteBlues on 2006-11-28
> **ago said:**
> Ubuntu is not Gnome.

Yeah - you're right. GNOME is a Desktop Environment; Ubuntu isn't. Ubuntu shouldn't be removing random applications and libraries from their DEFAULT DESKTOP ENVIRONMENT for the sake of an ignorant and arrogant approach concerning Mono.

The only possible case for having non-GNOME applications in the Default Ubuntu is in the instance of Firefox, which is default simply because it's an insanely popular web browser that is cross-platform.

> In fact I remember reading some mono fan arguing for the inclusion of Mono within Gnome on the ground that distros where free to include it or not. Now we see people pushing Mono inside distros on the ground that Mono is in Gnome...

Simply put, distros should NOT be removing core elements of their default Desktop Environment except in very rare or extreme cases which warrant this. Firefox over Epiphany warrants this (though, ideally Epiphany should be used; but let's be realistic here) due to the browser's popularity and its Free and free status. Removing Mono is NOT WARRANTED. Neither Ubuntu or its users will face a lawsuit over Mono. Removing it serves no purpose other than to satisfy the endlessly angsty "OMG I HATEZ THE MICROSOFT"-spouting kiddies.

---

### Post by warfly on 2006-11-28
> **a simple façade said:**
> Yeah - you're right. GNOME is a Desktop Environment; Ubuntu isn't. Ubuntu shouldn't be removing random applications and libraries from their DEFAULT DESKTOP ENVIRONMENT for the sake of an ignorant and arrogant approach concerning Mono.
So if you think all those concerns posted here regarding the risk of patent infringement and more importantly IMHO of giving away control of an open source platform to MS as 'ignorant and arrogant approach', then could you share your wisdom why it is so?

> **a simple façade said:**
> Removing Mono is NOT WARRANTED. Neither Ubuntu or its users will face a lawsuit over Mono.
And where's the reason behind this claim? Are you insisting Ubuntu should just ignore any possibility of legal trouble regarding Mono because you guarantee it will never happen?

I've read all of the posts in this thread, but still couldn't find any convincing, rational arguments against those concerns.

---

### Post by ButteBlues on 2006-11-28
> **warfly said:**
> So if you think all those concerns posted here regarding the risk of patent infringement and more importantly IMHO of giving away control of an open source platform to MS as 'ignorant and arrogant approach', then could you share your wisdom why it is so?

I've read all of the posts in this thread, but still couldn't find any convincing, rational arguments against those concerns.
Mono is an implementation of an OPEN standard. .NET is an implementation of the standard. Mono, however, does not equate to .NET.


What we're talking about is essentially the difference between MySQL and the Microsoft equivalent - two ways of doing the same open standard.

Microsoft has about as much legal ground to sue anyone over Mono as I have legal ground to dub myself the Queen of England.

---

### Post by Senori on 2006-11-29
Okay.

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

### Post by warfly on 2006-11-29
> **a simple façade said:**
> Mono is an implementation of an OPEN standard. .NET is an implementation of the standard. Mono, however, does not equate to .NET.
In fact, Mono is not just an implementation of an open standard but also an effort to copy major part of .NET platform which of course includes lot of entirely proprietary APIs from MS (i.e. WinForms, ASP.NET, ADO.NET).

And as you might know already if you have carefully read the previous posts, being an ECMA standard by no means protects it from being a target of IP lawsuit.

Moreover, it's obvious it's MS not Mono people who control the future of .NET platform. And I don't think it a good idea to build an open source OS over such a platform over which a big proprietary corporation has firm control.

---

### Post by warfly on 2006-11-29
> **Senori said:**
> I'm going to be responding to the original premise of the thread--that Mono should be removed from Ubuntu, because it's an evil Microsoft product and because Novell is the devil.
I'm sorry but I fail to see that many people from this thread who supports getting rid of Mono dependency base their arguments simply on 'MS is evil and so is Novell' premise - it's a straw man argument.

> **Senori said:**
> In this respect it is very similar to non-Sun open-source Java projects; both aim to create free software implementations of proprietary technologies (.NET and Java, respectively.)
It's similar but not quite the same I presume. First, ALL of the standard Java specifications come from JCP which is fairly open committee while many of the specs which Mono implements is entirely proprietary product from MS.

And as for Java, we now even have an open source version of the official RI but for .NET we only have one open source implementation which is incomplete and not entirely compatible with the 'official' .NET specification.

But even when we set aside those facts, the real problem is that Java is NOT part of the default installation of Ubuntu while now using Mono is FORCED for everyone who chooses to install the Ubuntu desktop.

---

### Post by Senori on 2006-11-29
> **warfly said:**
> I'm sorry but I fail to see that many people from this thread who supports getting rid of Mono dependency base their arguments simply on 'MS is evil and so is Novell' premise - it's a straw man argument.
The point of the first post of this thread was "In this situation I do not want anything related to Microsoft or Novell in my systems because I do not trust Microsoft nor Novell."

The point of the last post before I started considering mine was "It would be quite ridiculous to slap Novell and then push their arguable technology in by default."

Considering that my response was specifically targeted to the original post of this thread, and considering that I addressed other arguments than the "Microsoft is teh evilzors" anyway, I really fail to see why you're so indignant here.

> It's similar but not quite the same I presume. First, ALL of the standard Java specifications come from JCP which is fairly open committee while many of the specs which Mono implements is entirely proprietary product from MS.
I fail to see why the drafting process of certain specifications is relevant to this argument; an open standard is an open standard, in terms of whether it is accessible to implementation.

> And as for Java, we now even have an open source version of the official RI but for .NET we only have one open source implementation which is incomplete and not entirely compatible with the 'official' .NET specification.
Yes, *now* we do, hence the "non-Sun" part of my statement. But open-source Java efforts far predate this, such as GCJ, which I specifically used as an example.

> But even when we set aside those facts, the real problem is that Java is NOT part of the default installation of Ubuntu while now using Mono is FORCED for everyone who chooses to install the Ubuntu desktop.
No, but many people have requested Java in the desktop. Really, the only reason such efforts haven't had more effort behind them is because none of the open source implementations are as feature-complete as Mono is, and there aren't any "killer applications" in the vein of Tomboy, F-Spot, or Beagle.

---

### Post by o_fortuna on 2006-11-29
Things like C# and GTK# are implementations of standards and protected from patent problems by the OIN. And there isn't anything wrong with them. They are not evil. C# is a perfectly good programming language. Something invented by Microsoft is not automatically bad. GNOME programs like F-Spot, Banshee, and Tomboy do not use Microsoft-controlled portions of Mono. Mono's future is not controlled by Microsoft. C# is a language like C++. It is a standard. It's not constantly changing at the whim of a Microsoft executive.

Senori's post says everything else I wanted to say. Well said ;)

edit: Oh, and OpenOffice is written partially in Java, so an open-source java implementation is included (gij).

---

### Post by ago on 2006-11-29
Sayng that Mono is simply implementing a standard is complete bulloks, there are huge chunks of Mono that are not covered by the standard.

Saying that implementing the standard covers you from IP litigation is bulloks, because the ECMA explicitly allows to have a patent attached to the standard and to enforce royalties on anyone implementing the standard. Which means that you are free to implement the standard but you MUST pay whatever MS asks (which now happens to be zero, but that can be changed). And if you do not, you will be infringing IP, ACCORDING TO ECMA.

Saying that .NET is like Java is bulloks. With .Net you cannot trust the company with the IP rights (which happens to be MS, which happens to be threatening to sue us), neither the company which reimplemented .Net (which happens to be Novell, which happens to have circumvented the GPL). Do not tell me that Novell are victimized. They used to be the good guys, but that was one CEO ago...

---

### Post by greggh on 2006-11-29
Mark Shuttleworth said that Ubuntu will be keeping Mono...

[http://video.google.com/videoplay?docid=2728972720932273543&q=Linux](http://video.google.com/videoplay?docid=2728972720932273543&q=Linux)

At 42:47 of the video Mark is asked about whether Ubuntu will keep Mono in Ubuntu. He responds...

> On Mono? Careful who you kiss? Maybe Novell should have thought of that. So we don't know the terms of the deal yet. It's unclear. I understand that Microsoft and Novell are frantically rewriting the terms of the deal as they figure out what a minefield they walked into. I hope somebody loses a foot. But until we actually fully know the terms of the deal we can't really comment. I will say that I think this is probably only the first move by Microsoft to really start actively countering what they see as an emerging threat. Free software has had a huge impact on the software industry if you look below the sort of first five companies. Most of the news, most of the headlines, are taken up by the top five software companies globally, and now we are seeing free software really starting to impact. Oracle, Microsoft, both making major announcements in the last two weeks. On Mono? We're gonna ship it. So it's in Edgy. It will be in Feisty.

---

### Post by ago on 2006-11-29
Well, you have to match it with that:

> Novell’s decision to go to great lengths to circumvent the patent framework clearly articulated in the GPL has sent shockwaves through the community. If you are an OpenSUSE developer who is concerned about the long term consequences of this pact, you may be interested in some of the events happening next week as part of the Ubuntu Open Week:

[https://wiki.ubuntu.com/UbuntuOpenWeek](https://wiki.ubuntu.com/UbuntuOpenWeek)

...I know that posting this message to an OpenSUSE list will be controversial. I'm greatly respectful of the long tradition of excellence in the SuSE product and community and have no desire to undermine that with this post. That said, I think the position taken by Novell leadership in their contract with Microsoft is hugely disrespectful of the contributions of thousands of GPL programmers and contributors to SuSE, and I know that many are looking for a new place to get involved that is not subject to the same arbitrary executive intervention. Ubuntu is one option, as are Gentoo, Debian and other communities. Please accept this mail in that spirit.

---

### Post by Senori on 2006-11-29
> **ago said:**
> Sayng that Mono is simply implementing a standard is complete bulloks, there are huge chunks of Mono that are not covered by the standard.
Yes, and I admitted as much. So was Java.

> Saying that implementing the standard covers you from IP litigation is bulloks, because the ECMA explicitly allows to have a patent attached to the standard and to enforce royalties on anyone implementing the standard. Which means that you are free to implement the standard but you MUST pay whatever MS asks (which now happens to be zero, but that can be changed). And if you do not, you will be infringing IP, ACCORDING TO ECMA
Yes. Which is where the OIN comes in.

> Saying that .NET is like Java is bulloks. With .Net you cannot trust the company with the IP rights (which happens to be MS, which happens to be threatening to sue us), neither the company which reimplemented .Net (which happens to be Novell, which happens to have circumvented the GPL). Do not tell me that Novell are victimized. They used to be the good guys, but that was one CEO ago...
Because Sun has always been an awesome-happy-flower-power company, right?

---

### Post by Senori on 2006-11-29
> **ago said:**
> Well, you have to match it with that:
His discontent with the practices of Novell does not mean that everything with Novell's hands in it is subject to suspicion.

---

### Post by tageiru on 2006-11-29
> **ago said:**
> Last time I checked it was not SCO to decide about Linux kernel development, while it is MS to decide about .Net development and therefore about Mono development

Well, the trial is not over yet...

> **ago said:**
> (do not even try to say that Mono is independent to any degree).

It is indepentent. Miguel and the team could choose to ignore compatability with .NET. There is no obligation to follow .NET, i.e. the Mono developers have never signed a deal with Microsoft that restricts what they should do.

As an example, Gtk# is included in Mono, but not in .NET.

> **ago said:**
> Which also means that MS do have IP rights in .Net (and several patents), since they did invent .Net and they lead development, something that SCO cannot claim. And the ECMA is not protection at all, since only a small part of Mono is covered by the ECMA, all the rest has MS written all over it, and quite literally... Does "system._WINDOWS_.forms" mean anything to you? Do you think it is wise to include something called "system.WINDOWS.forms" inside a LINUX distro? 

Even assuming that Mono only implemented the ECMA standard (which is bulloks), you should know that according to ECMA, you can attach a patent to a standard (as MS did) and ECMA allows to license the product on a reasonable and non-discriminatory basis (known as RAND licensing). So ECMA does NOT guarantee that people implementing the standard can walk away without paying royalties. What is worse is that there&#101;&#146;s no  definition for "reasonable", so patent holders (MS in this case) can charge anything. 



We have plenty of software that is based on software that originated within Microsoft in Linux. Samba is not even a standard, just a reverse implementation. Why should we be more scared of Mono than Samba?

> **ago said:**
> Not least, Novell, as Mark says, has circumvented the GPL, and that should not be allowed to happen.

Mark is on shaky legal grounds these days too. Including binary drivers by default may be in violation of the GPL. Novell ironically chose not to include binary drivers by default since they may be illegal and by the request of several kernel developers.

In any event binary drivers "circumwent" the GPL as much as the Novell/Microsoft deal.

---

### Post by ButteBlues on 2006-11-29
> **warfly said:**
> And as you might know already if you have carefully read the previous posts, being an ECMA standard by no means protects it from being a target of IP lawsuit.

And as you might know already if you have carefully read the thread, Microsoft stands to lose millions of dollars should they push OIN to the point of OIN putting out suits against Microsoft.

> Moreover, it's obvious it's MS not Mono people who control the future of .NET platform. And I don't think it a good idea to build an open source OS over such a platform over which a big proprietary corporation has firm control.

Proprietary products aren't the devil. In a better world, proprietary wouldn't matter. It's just that for the most part, the proprietary software world is filled with pseudo-monopolies rather than solid competition.

---

### Post by ago on 2006-11-29
> **tageiru said:**
> Well, the trial is not over yet...
Yes, so why rush to start another one...

> Miguel and the team could choose to ignore compatability with .NET.
Which will never happen... Particularly now.

> As an example, Gtk# is included in Mono, but not in .NET.
They _will_ follow .Net2 then .Net3 then .Net4 then whatever else MS decides... As for the extra Mono-only libraries, thanks to the agreement, it is quite likely that such libraries will be ported to .Net. This will help use Linux apps on Windows (even without Mono), while the reverse will not be possible because of patent issues on huge parts of the libraries used by almost any .Net application. 

> Why should we be more scared of Mono than Samba?
Because Samba is a reimplementation of a PROTOCOL and it was done over wire in a clean-room environment. This is explicitly allowed by patent regulations. While patent regulation say that patents can be enforced on ECMA standard implementations. Not to mention on implementations that are not even part of the ECMA standard and covered by patents. Mentioning the OIN after having signed a bilateral agreement not to sue is pure blasphemy. 

> Including binary drivers by default may be in violation of the GPL.
In fact I am against that too, at least for the drivers/firmware which are not strictly necessary.

> In any event binary drivers "circumwent" the GPL as much as the Novell/Microsoft deal.
In a very different way. Novell is circumventing the GPL in order to distribute the products only to a section of the users (the ones who pay MS). To be more precise they distribute to everybody under GPL terms but then, via a second company, they threaten a subset of the users, thus segregating the user base. Ubuntu (and Debian and almost all distros to some degree, including Suse) are circumventing the GPL by bundling drivers (or firmware), which are arguably necessary to make the machine work at all, and make them available to EVERY user. If you think it is the same thing, you are on crack.

---

### Post by Senori on 2006-11-29
> **ago said:**
> Yes, so why rush to start another one...
There's no rush. It can happen any time, or more likely never.

> **ago]Which will never happen... Particularly now.[/quote]
Oh, they certainly could. It's not a terribly important point, but they "have the technology."

[quote=ago]They _will_ follow .Net2 then .Net3 then .Net4 then whatever else MS decides... As for the extra Mono-only libraries, thanks to the agreement, it is quite likely that such libraries will be ported to .Net. This will help use Linux apps on Windows (even without Mono), while the reverse will not be possible because of patent issues on huge parts of the libraries used by almost any .Net application. [/quote]
I haven't heard of any significant efforts to point Gtk# to .NET on Windows, and I really doubt that anyone will.

Further said:**
> Because Samba is a reimplementation of a PROTOCOL and it was done over wire in a clean-room environment. This is explicitly allowed by patent regulations. 
No; cleanroom development protects you from copyright and trade secret lawsuits. It does *absolutely nothing* for patents, because patents are not on the code, but on the principle and the implementation. This is why a cleanroom implementation of FAT would not be immune to a patent lawsuit by Microsoft (which hasn't hindered adoption of FAT, by the way.)

[quote=ago]While patent regulation say that patents can be enforced on ECMA standard implementations. Not to mention on implementations that are not even part of the ECMA standard and covered by patents. Mentioning the OIN after having signed a bilateral agreement not to sue is pure blasphemy. [/quote]
The agreement applies exclusively to customers of Novell and Microsoft. Richard Stallman, who you'd expect to be against this sort of thing as much as anyone, has said among other things that the deal does not violate the GPLv2.

[quote=ago]In fact I am against that too, at least for the drivers/firmware which are not strictly necessary.[/quote]
Why are you making an exception for "strictly necessary" drivers and firmware? Don't those constitute the same ethical and legal challenges?

[quote=ago]In a very different way. Novell is circumventing the GPL in order to distribute the products only to a section of the users (the ones who pay MS). To be more precise they distribute to everybody under GPL terms but then, via a second company, they threaten a subset of the users, thus segregating the user base. Ubuntu (and Debian and almost all distros to some degree, including Suse) are circumventing the GPL by bundling drivers (or firmware), which are arguably necessary to make the machine work at all, and make them available to EVERY user. If you think it is the same thing, you are on crack.[/QUOTE]
Okay, first of all, this "you are on crack" thing is really tiresome. Grow up.

Second, I have no idea where you're getting that on the Microsoft-Novell deal. The substance of the deal is on two things; interoperability pledges between the two vendors, and a weak covenant not to sue the customers of either company. The only sense in which they might even possibly be construed to be doing something like what you're saying is that the deal does not cover customers and developers of Linux software outside Novell, but this is by no means "paying someone else to threaten them."

Finally, Debian plans to remove non-free firmware from its kernel, as soon as is expedient (meaning after etch.)

---

### Post by tageiru on 2006-11-29
> **ago said:**
> Because Samba is a reimplementation of a PROTOCOL and it was done over wire in a clean-room environment. This is explicitly allowed by patent regulations. While patent regulation say that patents can be enforced on ECMA standard implementations. Not to mention on implementations that are not even part of the ECMA standard and covered by patents. Mentioning the OIN after having signed a bilateral agreement not to sue is pure blasphemy.

Even though re-implementation is allowed it does not save you from patent infringement.

---

### Post by warfly on 2006-11-29
> **a simple façade said:**
> Proprietary products aren't the devil. In a better world, proprietary wouldn't matter. It's just that for the most part, the proprietary software world is filled with pseudo-monopolies rather than solid competition.
I myself don't think proprietary software itself is evil, in that account I don't quite agree with RMS or FSF. But developing and using proprietary softwares is one thing and build an open source OS on top of a platform of which a big proprietary SW company has firm control is a whole different story IMO, especially when the company has been known to be hostile to the OSS community.

---

### Post by ButteBlues on 2006-11-29
> **warfly said:**
> I myself don't think proprietary software itself is evil, in that account I don't quite agree with RMS or FSF. But developing and using proprietary softwares is one thing and build an open source OS on top of a platform of which a big proprietary SW company has firm control is a whole different story IMO, especially when the company has been known to be hostile to the OSS community.
Then you're using the wrong distribution. Ubuntu has included proprietary items for this and that since Warty, by default.

---

### Post by warfly on 2006-11-29
> **a simple façade said:**
> Then you're using the wrong distribution. Ubuntu has included proprietary items for this and that since Breezy, by default.
Which default application is 'built on top of' a proprietary platform or a framework then?

---

### Post by ago on 2006-11-30
> **Senori said:**
> Further; having applications run on as many operating systems as possible is a *good thing*. Interoperability allows for products to be used more widely, and for people to become acquainted.
Interoperability in my mind is a 2-way concept. Being able to port Linux apps to windows but not windows app to Linux does not classify as interoperability IMO.

> It does *absolutely nothing* for patents, because patents are not on the code, but on the principle and the implementation.
It does when the object is a PROTOCOL. As for FAT, MS patent was rejected... [http://www.regdeveloper.co.uk/2004/09/30/microsoft_fat_patent_rejected/](http://www.regdeveloper.co.uk/2004/09/30/microsoft_fat_patent_rejected/)

> Richard Stallman, who you'd expect to be against this sort of thing as much as anyone, has said among other things that the deal does not violate the GPLv2.
They said that it CIRCUMVENTS the GPL. I.E. it does not violate it formally but it violates it in practice. And in fact they are changing the GPLv3 to explicitly avoid it being circumvented with agreements such as the Novell ones.

> Why are you making an exception for "strictly necessary" drivers and firmware? Don't those constitute the same ethical and legal challenges?
Because there is little point to allow free (as in freedom) distribution of code if you cannot turn on your computer...

> the deal does not cover customers and developers of Linux software outside Novell, but this is by no means "paying someone else to threaten them."
You have 2 companies in an agreement, company A distributes under GPL, company B sues or threatens part of the users (the ones that do not pay company A), thus discriminating the user base. This is clearly against the spirit of GPL. Why is it different from providing firmware? Because in the Novell case they are circumventing the GPL in order to RESTRICT the user base, allowing the same freedom only to their customers, while in the Ubuntu/Debian/XYZ case they are circumventing the GPL in order to EXPAND the user base allowing the same freedom to as many people as possible. They have diametrically opposite aims.

---

### Post by ago on 2006-11-30
> **a simple façade said:**
> Then you're using the wrong distribution. Ubuntu has included proprietary items for this and that since Breezy, by default.

Or maybe Ubuntu made the wrong choice and that should be rectified by the community...

---

### Post by Terracotta on 2006-11-30
> **ago said:**
> Or maybe Ubuntu made the wrong choice and that should be rectified by the community...

Or maybe GNOME made the wrong decision (which is the real reason ubuntu installs mono by default), by using kubuntu you can be quite sure you don't have any mono stuff installed (except the icons).

---

### Post by ButteBlues on 2006-11-30
> **warfly said:**
> Which default application is 'built on top of' a proprietary platform or a framework then?
While I do not have the specific citation, I can refer you to this post for further clarification: [http://www.ubuntuforums.org/showpost.php?p=1820818&postcount=27](http://www.ubuntuforums.org/showpost.php?p=1820818&postcount=27).

---

### Post by warfly on 2006-11-30
> **a simple façade said:**
> While I do not have the specific citation, I can refer you to this post for further clarification: [http://www.ubuntuforums.org/showpost.php?p=1820818&postcount=27](http://www.ubuntuforums.org/showpost.php?p=1820818&postcount=27).

Thanks for the clarification. However I think applications that are built on top of a problematic or proprietary platform pose far greater threat than proprietary drivers to which the above post refers. Since it's quite easy to replace proprietary drivers once the open source alternatives become available while there's no easy way to port applications built on a certain platform to another.

---

### Post by Aleksandersen on 2006-11-30
Some of the best desktop applications, like Banshee, requires mono.

I guess that is why it is included...

---

### Post by Senori on 2006-11-30
> **ago said:**
> Interoperability in my mind is a 2-way concept. Being able to port Linux apps to windows but not windows app to Linux does not classify as interoperability IMO.
Which is the entire point of Mono support for Windows.Forms. And which is why you can get Paint.NET working on Mono in Linux now with some very preliminary porting.

> It does when the object is a PROTOCOL. As for FAT, MS patent was rejected... [http://www.regdeveloper.co.uk/2004/09/30/microsoft_fat_patent_rejected/](http://www.regdeveloper.co.uk/2004/09/30/microsoft_fat_patent_rejected/)
No; protocols are covered by patents. And yes,  the patent was rejected on a preliminary basis, but the final decision made in January overturned that and upheld the FAT patent.

> They said that it CIRCUMVENTS the GPL. I.E. it does not violate it formally but it violates it in practice. And in fact they are changing the GPLv3 to explicitly avoid it being circumvented with agreements such as the Novell ones.
Yes; many things circumvent the GPL, and a lot of things are against the GPL v3. But neither of those are dreadful things in themselves.

> Because there is little point to allow free (as in freedom) distribution of code if you cannot turn on your computer...
Since when has practicality been part of whether something is intellectually wrong?

> You have 2 companies in an agreement, company A distributes under GPL, company B sues or threatens part of the users (the ones that do not pay company A), thus discriminating the user base. This is clearly against the spirit of GPL.
"I won't sue your customers" does not mean "I will sue everyone who is not your customer."

> Why is it different from providing firmware? Because in the Novell case they are circumventing the GPL in order to RESTRICT the user base, allowing the same freedom only to their customers, while in the Ubuntu/Debian/XYZ case they are circumventing the GPL in order to EXPAND the user base allowing the same freedom to as many people as possible. They have diametrically opposite aims.
Who's to say that SUSE selling better wouldn't expand the user base?

Both are idealogically wrong under a free software philosophy. There isn't a gray area here simply because you like your computer to work.

---

### Post by ago on 2006-11-30
> **Senori said:**
> Which is the entire point of Mono support for Windows.Forms. And would you mind explaining us how exactly system._WINDOWS_.forms is supposed to be patent-free?

> protocols are covered by patents.
Not directly. [http://www.freeprotocols.org/freeProtocolProcess/split/node2.html](http://www.freeprotocols.org/freeProtocolProcess/split/node2.html)

> but the final decision made in January overturned that and upheld the FAT patent.
I stand corrected, and yes in that case FAT will need to be moved as a restricted module. That said FAT is used only for interoperability, no Linux distro is installed on top of FAT, so the situation is quite different from building a desktop on top of a risky technology such as Mono. The equivalent would be to use FAT as the default filesystem of Ubuntu...

> Since when has practicality been part of whether something is intellectually wrong?
Intellectually wrong? No Novell is MORALLY wrong. They are restricting the user base trying to extract royalties from GPL work. I.E. they are exploiting the contributions of millions of man-hours that were donated with the sole condition NOT to be exploited the way Novell and MS are doing... Not formally, but in practice they are stealing. 

> "I won't sue your customers" does not mean "I will sue everyone who is not your customer."
Unfortunately MS (the other part of the agreement) did already threaten to sue "everyone who is not your customer" so there is little scope for interpretation.

> Who's to say that SUSE selling better wouldn't expand the user base?
They would expand THEIR user base of paying customers, which is quite a different concept from the user base intended in the GPL... 

> Both are idealogically wrong under a free software philosophy.
You are raising smoke screens. As explained above the 2 actions are only formally similar but are completely different in substance, and MORALLY. Giving ANYONE the SAME right to use the software is what the GPL stands for. And If you wanted to give ANYONE the same right, including people that unknowingly bought hardware that requires proprietary firmware, you would need to distribute such firmware. Which is quite different from threatening half of the users in order to piggyback other people's work against their will...

---

### Post by KaeseEs on 2006-11-30
I've been inactive in this discussion since I took all the mono packages off my system, but the main reason I did so has been oddly unmentioned here:  it takes up a lot of space.  By removing Mono and the apps that depended on it, I freed 120+ MB from my system.  Even if we went with a 'minimal' Mono setup, consisting of the libs, tomboy, f-spot and beagle, that's still something like 50 MB.  Now, this may not seem like a lot, as most folks have 100GB+ hard disks, but we have to remember something:

**The way most folks are introduced to Ubuntu nowadays is by LiveCD.**

50-120 MB is a LOT of space on a 695MB CD.  The ISO was at 693MB or thereabouts before the mono stuff got added.  What'd we take out to put it in?  Is this really the best use of space?

Besides this, whose idea was it to put *any* new application in an upgrade path?  Doing so for trivial reasons shows a lack of basic respect for end users' sovreignty over their own machines.

---

### Post by ButteBlues on 2006-11-30
Beagle is not insalled by default. ;)

---

### Post by sloggerkhan on 2006-11-30
I like beagle because the regular search tool rather sucks. But I must agree that it is too big, especially for live CD. It also has on occasion used too many system resources.

I suppose I don't mean that it's too big, but that it GROWS and gets big, and uses more CPU time than any other process on my comp.

---

### Post by nzjrs on 2006-12-01
Puh-leeze

This is the biggest POS thread on ubuntuforumns.org. It is this seperatist attitude that leads to the real workers, those valuable to the community, leaving.

Quote: "Only a Sith Lord deals in absolutes"

Deal with it everyone. There is a world of distance between shipping Mono and Microsoft sueing linux out of existance.

[Farewell Jorge]("http://www.whiprush.org/2006/12/its_time_to_ele.html"), [Bow your head in shame everyone, because you caused it]("http://www.bigmaninjapan.com/2006/11/29/stfu-already/")

---

### Post by ago on 2006-12-01
> **nzjrs said:**
> Bow your head in shame everyone, because you caused it

I hope by "you", you also mean Mark Shuttleworth, because he happens to share the view of many here that Novell has circumvented the GPL, segregated the community, and exploited GPL work by bundling it with a royalty-paying scheme. Not to mention that it is quite awkward accusing us of FUD, when Novell has helped MS spread FUD about the need to get a "MS licensed Linux version".

---

### Post by ago on 2006-12-01
In response to [http://www.bigmaninjapan.com/2006/11/29/stfu-already/](http://www.bigmaninjapan.com/2006/11/29/stfu-already/)

> Why Microsoft won&#8217;t sue anyone
Whether suing or not is only part of the problem. The main issue is that they are trying to split the community between "licensed" parties (=commercial companies that can be purchased) and "non licensed" parties (volunteers and non profit organizations and community efforts such as Debian or Ubuntu and big chunks of the FOSS world and the KML, the very heart of Linux). 

> First, its just bad business sense to sue your (potential) customers.
Not if they can provide an equivalent "licensed" product to their customers. In particular they are not going to sue Novell customers and they claimed they may unilaterally spare RH customers, which accounts for the vast majority of their customers. So no, they would not sue their (potential) customers.

> From a business standpoint Microsoft stands nothing to gain from doing this.
Yes they do. Undeniably Linux is one of their biggest threats. They cannot stop Linux with their usual techniques, they need to "transform" it first into a more traditional target and then go for the triple-E.

> Second, its bad legal sense to try and seek a legal relief.
You completely missed the point. They are not threatening or suing in order to extract some revenues, but in order to kill a rival and thus secure their current revenue stream. Which is worth several dozens of billions of dollars. And if they can box-in enough bilateral "agreements" they can create a "licensed" linux version. If that "brand" succeeds it will marginalize the "non licensed" part both from a techical and a legal point of view and that is enough to transform Linux back into Unix and kill the beast. All without any need to sue anybody. The threat to sue is enough to push clients to ask for "licensed version" and vendors to adhere to the scheme (+ a spare hundred millions).

On top of it, a "licensed version" is a royalty scheme, which in itself is perfectly ok, provided you do not bundle it with GPL work. Unfortunately they ARE bundling it with GPL work, thus STEALING GPL work, and they managed to do so using a loophole in the GPL license. Most devs out there did not contribute millions of man hours so that MS could ask users to pay a fee in order to use their work. It is quite sad to see companies like Novell exploiting such loopholes to circumvent the license. That is exactly why the GPLv3 is being modified.

> The defendant is going to present a case as to why the patent isn&#8217;t valid
MS does not have just 1 patent, but several hundreds. Now, it is true that it is difficult today to do anything at all without violating a patent. But there are patents and patents. Violating a very generic patent may well be a good thing, because: 

1) you expose weaknesses in the patent logic, 
2) you drag in several other parties (from Sun, to IBM) that might retaliate, 
3) you have good chances of winning the litigation. 

What you want to avoid at all costs is to have a patent infringment for issues which are limited in scope and fairly specific, particularly if they regards you and only you, because in this case you cannot take advantage of either 1 or 2 and the chances of loosing are far greater. Mono happens to fit the bill quite well...

Some may argue that the dangers above may be overblown, and they might even be right. In fact I do hope they are right. But is it worth the risk? What if they are wrong? 

Finally, nobody here is claiming that Mono must be killed, only that it should not be in by default, which does not seem such an unreasonable proposition. If people get upset about that suggestion to the point of leaving, or worse, if they get upset about others voicing different opinions, then they will not be missed.

---

### Post by ButteBlues on 2006-12-01
ago - It should be that rather if a mere handful of Ubuntu users are so caught up in their agenda that using synaptic or the CLI to simply remove the mono packages, then they won't be missed. Because, you know, 3 seconds of the minority's time in this matter isn't that much to ask.

---

### Post by ago on 2006-12-01
Why not do the reverse? Use synaptic to install Mono... That too is not such a big deal, isn't it?

---

### Post by ButteBlues on 2006-12-01
> **ago said:**
> Why not do the reverse? Use synaptic to install Mono... That too is not such a big deal, isn't it?
This goes right back to the same inherent issue with the binary drivers: the vast majority is being forced to install them manually at the moment. It makes no sense to force the vast majority to do *x* rather than simply have the minority do *-x*.

---

### Post by dca on 2006-12-01
I dunno', I commented in another post about this...  We might be reading too much into this whole Novell/M$ cockamamie...  Sure, there's Ballmer and FUD, there's the whole threat of lawsuits against GNU/Linux distro(s) which would result in suit(s) against companies that support Linux (Fedora to Redhat, SuSE to Novell - woops, bad example, or Canonical to Ubuntu).  It all boils down to 'virtualization'.  It's the future in enterprise server management.  'Xen' (mostly on Fedora, not so much SuSE) is pretty powerful.  On the Fedora end there's a nice GUI and everything.  This pact is supposed to solve the issue that if you're going to install or virtualizzzze (that's nice) M$ inside a Linux server, you don't have to worry about the EULA.  Now I know Ballmer wanted it the other way around...  Linux inside M$, but that's just silly...
 
...oh wait a minute, maybe I commented in this same thread...  :-k

---

### Post by dca on 2006-12-01
oh, oh....  and it better be SuSE that you're using...  :-D

---

### Post by Senori on 2006-12-01
> **ago said:**
> And would you mind explaining us how exactly system._WINDOWS_.forms is supposed to be patent-free?
It isn't. Neither is FAT support in the kernel. But since by far the majority of things are covered under *some* patent, it's an entirely pointless discussion to say "this could theoretically be covered by patents!" because you would end up without a functional operating system.

> Not directly. [http://www.freeprotocols.org/freeProtocolProcess/split/node2.html](http://www.freeprotocols.org/freeProtocolProcess/split/node2.html)
"In either case, the protocol can then be held hostage by the patent-holder, to the enormous detriment of anyone else who may wish to use it."

*yawn*

> I stand corrected, and yes in that case FAT will need to be moved as a restricted module. That said FAT is used only for interoperability, no Linux distro is installed on top of FAT, so the situation is quite different from building a desktop on top of a risky technology such as Mono. The equivalent would be to use FAT as the default filesystem of Ubuntu...
To be honest, most things are covered under patents. See, for example, patent [5596347](http://www.freepatentsonline.com/5596347.html) on cursors for computer screens, or (until recently) the set of patents on JPEGs.

If everything covered under a patent was moved to restricted, we would have very few things in the main repositories.

> Intellectually wrong? No Novell is MORALLY wrong. They are restricting the user base trying to extract royalties from GPL work. I.E. they are exploiting the contributions of millions of man-hours that were donated with the sole condition NOT to be exploited the way Novell and MS are doing... Not formally, but in practice they are stealing. 
I'm not going to bother with the whole "they're stealing!!!" argument, but quibbling over "intellectually" versus "morally" is incredibly pointless, considering that the two are often used synonymously.

> Unfortunately MS (the other part of the agreement) did already threaten to sue "everyone who is not your customer" so there is little scope for interpretation.
Show me the statement where Steve Ballmer says "if you don't do this sort of agreement, we'll sue you and your customers."

> They would expand THEIR user base of paying customers, which is quite a different concept from the user base intended in the GPL... 
I don't care about the user base intended in the GPL; I'm talking about the term defined as "user base"--that is, the number of people *using a particular piece of software.*

> You are raising smoke screens. As explained above the 2 actions are only formally similar but are completely different in substance, and MORALLY. Giving ANYONE the SAME right to use the software is what the GPL stands for. And If you wanted to give ANYONE the same right, including people that unknowingly bought hardware that requires proprietary firmware, you would need to distribute such firmware. Which is quite different from threatening half of the users in order to piggyback other people's work against their will...
No, they aren't! They are both, under the free software argument, *completely morally wrong!* Whether it's enabling a bunch of people to use Ubuntu, or enabling a bunch of people to use SUSE without feeling that they will be sued (and inadvertently making everyone else feel nervous) they are *both* in violation of the GPL. The *only reason* you're defending one and not the other is because you like your hardware working, which is under the free software argument simply indefensible.

> **KaeseEs said:**
> I've been inactive in this discussion since I took all the mono packages off my system, but the main reason I did so has been oddly unmentioned here:  it takes up a lot of space.  By removing Mono and the apps that depended on it, I freed 120+ MB from my system.  Even if we went with a 'minimal' Mono setup, consisting of the libs, tomboy, f-spot and beagle, that's still something like 50 MB.  Now, this may not seem like a lot, as most folks have 100GB+ hard disks, but we have to remember something:

**The way most folks are introduced to Ubuntu nowadays is by LiveCD.**

50-120 MB is a LOT of space on a 695MB CD.  The ISO was at 693MB or thereabouts before the mono stuff got added.  What'd we take out to put it in?  Is this really the best use of space?
Realistically, a working desktop system is going to require more than 700 megabytes sooner or later. During the Edgy cycle someone (I believe it was Scott Remnant) proposed moving Ubuntu onto a Live DVD, to assuage space concerns for the forseeable future; this was eventually shot down, but it'll come up again.

> Besides this, whose idea was it to put *any* new application in an upgrade path?  Doing so for trivial reasons shows a lack of basic respect for end users' sovreignty over their own machines.
You're still perfectly free to remove anything you want from Ubuntu; all it will mean is that the ubuntu-desktop metapackage, which does absolutely nothing except pull in new packages included in the desktop, will be removed. This argument is like saying "who's idea was it to put *gnome-terminal* in an upgrade path? Doing so shows a lack of respect for end users' sovereignty over their machines." The fact is that it *makes the desktop better for the vast majority of people, and allows for a better system overall.*

> **sloggerkhan said:**
> I suppose I don't mean that it's too big, but that it GROWS and gets big, and uses more CPU time than any other process on my comp.
This is a problem that has been identified and is being worked on significantly right now; several things in Beagle CVS (and things coming up in the next month or two) will improve this dramatically.

> **ago said:**
> Whether suing or not is only part of the problem. The main issue is that they are trying to split the community between "licensed" parties (=commercial companies that can be purchased) and "non licensed" parties (volunteers and non profit organizations and community efforts such as Debian or Ubuntu and big chunks of the FOSS world and the KML, the very heart of Linux). 
I really don't think that Novell is operating in a vast conspiracy with Microsoft to make the Linux desktop under them bigger, do you?

> Not if they can provide an equivalent "licensed" product to their customers. In particular they are not going to sue Novell customers and they claimed they may unilaterally spare RH customers, which accounts for the vast majority of their customers. So no, they would not sue their (potential) customers.
Ubuntu users would be considered potential customers in every sense that Red Hat customers would be.

> Yes they do. Undeniably Linux is one of their biggest threats. They cannot stop Linux with their usual techniques, they need to "transform" it first into a more traditional target and then go for the triple-E.
If they're going to agree not to sue any number of groups, i really fail to see how they would be transforming it into a traditional target. The perceived benefits of Linux (free, open source, technically better) would still in every sense be there; the only difference would be that a few companies have signed agreements regarding patents.

> You completely missed the point. They are not threatening or suing in order to extract some revenues, but in order to kill a rival and thus secure their current revenue stream. Which is worth several dozens of billions of dollars. And if they can box-in enough bilateral "agreements" they can create a "licensed" linux version. If that "brand" succeeds it will marginalize the "non licensed" part both from a techical and a legal point of view and that is enough to transform Linux back into Unix and kill the beast. All without any need to sue anybody. The threat to sue is enough to push clients to ask for "licensed version" and vendors to adhere to the scheme (+ a spare hundred millions).
See, the problem with this grand conspiracy is that the "licensed users only" thing only works if "non-licensed users" are threatened with lawsuits. As the guy you're responding to rather succinctly put, non-licensed users have no realistic fear of being sued here, making the agreements less than moot in this sense.

> On top of it, a "licensed version" is a royalty scheme, which in itself is perfectly ok, provided you do not bundle it with GPL work. Unfortunately they ARE bundling it with GPL work, thus STEALING GPL work, and they managed to do so using a loophole in the GPL license. Most devs out there did not contribute millions of man hours so that MS could ask users to pay a fee in order to use their work. It is quite sad to see companies like Novell exploiting such loopholes to circumvent the license. That is exactly why the GPLv3 is being modified.
I'm quite certain that most devs out there don't particularly care if Novell is paying some money so that their customers aren't sued.

> MS does not have just 1 patent, but several hundreds. Now, it is true that it is difficult today to do anything at all without violating a patent. But there are patents and patents. Violating a very generic patent may well be a good thing, because: 

1) you expose weaknesses in the patent logic, 
2) you drag in several other parties (from Sun, to IBM) that might retaliate, 
3) you have good chances of winning the litigation. 
This is dependent on any number of factors, notably the judge involved, the parties involved in the lawsuit, and the content of the patent.

> What you want to avoid at all costs is to have a patent infringment for issues which are limited in scope and fairly specific, particularly if they regards you and only you, because in this case you cannot take advantage of either 1 or 2 and the chances of loosing are far greater. Mono happens to fit the bill quite well...
So do a lot of very important things. This is why you have the OIN.

> Some may argue that the dangers above may be overblown, and they might even be right. In fact I do hope they are right. But is it worth the risk? What if they are wrong? 
If they are wrong, then we have been in trouble for any number of years, and we will not be until software patents are repealed wholesale. It's a simple fact that there are few pieces of any software on the market today not covered by *some* patent somewhere, which is what has caused the numerous lawsuits against Microsoft on trivial patents. Simply put; removing Mono won't make patent danger from Microsoft or anyone else any less potent; it will just remove an important piece of the operating system.

> Finally, nobody here is claiming that Mono must be killed, only that it should not be in by default, which does not seem such an unreasonable proposition. If people get upset about that suggestion to the point of leaving, or worse, if they get upset about others voicing different opinions, then they will not be missed.
Having the right to do a thing, such as speech, is not at all the same thing as that being the right thing to do. One should not say "all Catholics should be burned at the stake," even though it is perfectly within your rights to do so, because reasonable people would become offended by it.

Now, "moving Mono to non-default status" limits the potential of the Ubuntu desktop in key areas. It *is* an issue, because there are many people who want their default installation to "just work." And it has been the pronounced trend of distributions in the last few years to oblige them.

---

### Post by ago on 2006-12-06
Interesting Groklaw article:

> 

...

The Novell-Microsoft agreement also, as Richard Stallman put it, cunningly tries to sidestep GPLv2. So we have an attack from within. A serious one, because everything SCO and its backers wanted from this litigation, but failed to achieve, Novell just handed to Microsoft on a silver platter by signing that patent agreement. Let me explain why I see it that way.

...

But here's the sad part. As victory [over SCO] is in sight, Novell signs a patent agreement with Microsoft that does the following:

    1. Novell agrees to violate the clear intent and spirit of the GPL in an attempt to comply literally with the words but not with the actual known purpose of the license to make money off of code Novell didn't write and doesn't own. So instead of trying to prove the GPL isn't binding, they just kick it to the curb and step over it and dare the community to do something about it?

    2. puts a FUD legal cloud over Linux (this time a patent cloud) or in any case an "IP" cloud, as per Steve Ballmer's vague wording -- and was Darl McBride's less vague?;

    3. makes Novell's Linux cost more, because it has agreed to pay Microsoft royalties, whereas SCO asked for money for its license;

What is the cotton pickin' difference? Other than being worse? Novell, I'd like you to answer that question. From Microsoft's point of view, I see no difference. What SCO could not win, Novell has handed Microsoft without a fight. The community didn't fight this hard and this long for such a result.

So there you have it, as I see it: two companies claiming to be Linux companies that turned on the GPL and the rest of the community for money, and the beneficiary is Microsoft. What a coincidence.

Does it matter that one did it maliciously and the other was merely a dope? I don't know for sure which is which or even if either is properly described since I can't read hearts, but my answer to the hypothetical question is: no. The effect is the same. It matters only in that one makes you mad and the second makes you sad and mad. That's why I call it SCO2 Deja Vu, with Novell playing the part of EV1. Only this is far worse than SCO.

And that is precisely what is wrong with what Novell did in signing that patent agreement, and that may help to explain the deep, deep anger that the community, which has worked night and day to defend and protect Linux and the GPL, now feels. I feel it too. We worked hard, were victorious, and now are denied the reward. And until Novell fixes that agreement or pulls out, it will never be accepted by the FOSS community again, in my view. I certainly think I have enough input to form an educated opinion. So I hope they come to their senses. If not, GPLv3 will deal with it. But if it goes that far, then Novell's reputation will never be made whole. For that, it must act.

[... More ...](http://www.groklaw.net/article.php?story=20061203015212989)

---

### Post by ago on 2006-12-06
> **Senori said:**
> Having the right to do a thing, such as speech, is not at all the same thing as that being the right thing to do. One should not say "all Catholics should be burned at the stake," even though it is perfectly within your rights to do so, because reasonable people would become offended by it.

Reasonable people do not compare reasoned arguments made by big chunks of the community (including Stallman, Shuttleworth, the Samba team, Groaklaw and several others) to a claim that "all Catholics should be burned at the stake"...

---

### Post by ButteBlues on 2006-12-06
> **ago said:**
> Reasonable people do not compare reasoned arguments made by big chunks of the community (including Stallman, Shuttleworth, the Samba team, Groaklaw and several others) to a claim that "all Catholics should be burned at the stake"...
It's an applicable comparison and you know it. Stop trying to straw-man.

---

### Post by ago on 2006-12-06
It's only a pathetic attempt to godwinize the discussion...

---

### Post by darkhatter on 2006-12-06
Groklaw spreads nothing but B.S. don't quote him

---

### Post by Senori on 2006-12-06
> **ago said:**
> Reasonable people do not compare reasoned arguments made by big chunks of the community (including Stallman, Shuttleworth, the Samba team, Groaklaw and several others) to a claim that "all Catholics should be burned at the stake"...
I'm not comparing the two on any grounds; I'm using them both as statements on which reasonable people disagree. "All puppies are cute" would be equally valid here.

---

### Post by Senori on 2006-12-06
> **ago said:**
> Interesting Groklaw article:
I like Groklaw, and I have it in Liferea, but it's an opinion blog as much as anything else (in fact, recent posts have been decried as nothing less than FUD by such people as Jono Bacon and Luis Villa.)

---

### Post by neighborlee on 2007-09-05
> **Wolki said:**
> Mono is protected by the Open Invention Network, so a patent suit would likely lead to the equivalent of a patent nuclear war - no one wants to do that. (see the discussion when Fedora started shipping mono, for example here: [http://gregdek.livejournal.com/4008.html](http://gregdek.livejournal.com/4008.html))

Mono is also largely based on open, standardized specifications. Parts of Windows.Forms (or somthing like that, the Windows GUI stuff) and other high-level stuff are patented, and mono implements them anyway, but they are done in a way so they can be very easily removed should the need arise. The stuff included with Ubuntu all use GTK# as their widget library, so it wouldn't affect them at all.

See also the Mono FAQ about licensing and Patents for more information. [http://www.mono-project.com/FAQ:_Licensing](http://www.mono-project.com/FAQ:_Licensing)

I am sorry for last post, and if some post went unread by me and  this is irrelvant but I wanted to get t his out there in case it is and appreciate any comments:

[http://wtogami.livejournal.com/11305.html](http://wtogami.livejournal.com/11305.html)

would seem to indicate the situation with mono is anything but credible..is this a 'old' 2006 story and facts have outgrown it or is it stilll relevant I wonder meaning mono has no business in linux..?

I expect zero flames as Im  earnestly concerned..only serious  takers need apply.

cheers
nl

from here you willl see on this page this comment from

---

### Post by bruce89 on 2007-09-05
C# is evil and slow. The sooner people use [Vala]("http://live.gnome.org/Vala") instead, the better.

This doesn't mention the space requirements of yet-another-gnome-binding.

---

### Post by neighborlee on 2007-09-05
> **bruce89 said:**
> C# is evil and slow. The sooner people use [Vala]("http://live.gnome.org/Vala") instead, the better.

It would seem gnome is advocating this so I hope mono is on its way out unless the claims made by that url I posted are invalid.

thank you
nl

---

### Post by bruce89 on 2007-09-05
Here is a list of programs that use mono:

F-spot by Novell
Banshee by Novell
Beagle by *guess who*

---

### Post by Anthem on 2007-09-05
Great gravy, are we going to argue about this again?

---

### Post by starcraft.man on 2007-09-05
> **bruce89 said:**
> Here is a list of programs that use mono:

F-spot by Novell
Banshee by Novell
Beagle by *guess who*

That's it? Geez, I thought it was more than that. Especially the way some people said it was the end of the world after all ...

---

### Post by loell on 2007-09-05
the most effective way to show that you don't like mono base apps is to make none mono base apps, say a combination of c and python?

butt o be just vocal about it, is just nuisance.

---

### Post by tiger74 on 2007-09-06
Don't forget **Evolution**.
:lolflag:

---

### Post by tbroderick on 2007-09-06
> **bruce89 said:**
> 
F-spot by Novell
Banshee by Novell
Beagle by *guess who*

Should be:
Banshee by Aaron Bockover
Beagle by Joe Shaw

I think both are employed by Novell, but Novell maintains neither project.

---

### Post by triptoe on 2007-09-06
> **Senori said:**
> Okay.
146
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

Sticky this please?

---

### Post by loell on 2007-09-06
> **bruce89 said:**
> C# is evil and slow. The sooner people use [Vala]("http://live.gnome.org/Vala") instead, the better.

This doesn't mention the space requirements of yet-another-gnome-binding.

thanks for the tip ;) , very promising language :)

---

### Post by igknighted on 2007-09-06
> **triptoe said:**
> Sticky this please?

+1...

I swear, there's more FUD coming from the linux camps on this issue (still).  Lets grow up people.  Novell's business is linux.  They cannot create it on their own, they need the community.  If they piss off the community, they lose.  Plain and simple.  So deep down, they have to have our back, because it is their own back too.

---

### Post by igknighted on 2007-09-06
> **bruce89 said:**
> C# is evil and slow. The sooner people use [Vala]("http://live.gnome.org/Vala") instead, the better.

This doesn't mention the space requirements of yet-another-gnome-binding.

Is this Gnome only, or will there be qt bindings?  Man, the absolute last thing we need to use OSS tools to lock people into either gtk or qt.

---

### Post by Anthem on 2007-09-06
> **igknighted said:**
> Is this Gnome only, or will there be qt bindings?  Man, the absolute last thing we need to use OSS tools to lock people into either gtk or qt.
Yeah, Mono has QT bindings.

---

### Post by igknighted on 2007-09-06
> **Anthem said:**
> Yeah, Mono has QT bindings.

Sorry, I should have been more specific... I was asking about Vala.

---

### Post by neighborlee on 2007-09-06
> **igknighted said:**
> +1...

I swear, there's more FUD coming from the linux camps on this issue (still).  Lets grow up people.  Novell's business is linux.  They cannot create it on their own, they need the community.  If they piss off the community, they lose.  Plain and simple.  So deep down, they have to have our back, because it is their own back too.

+2 but -mono...isn't it interesting how those that acuse others of spreading FUD,-- they themselves are involved in spreading it thick.  I linked a website that makes it perfectly clear that the OIN contains no patent protections for .NET which mono is based on and Ill offer it again:

[http://wtogami.livejournal.com/11305.html](http://wtogami.livejournal.com/11305.html) < original link and below is the link where the OIN lists its protected patents for linux:


[http://www.openinventionnetwork.com/pat_owned.php](http://www.openinventionnetwork.com/pat_owned.php)

You can scream foul all you wish but the facts are clear unless someone has more info on this.

Fedora is removing mono and they are backed by Redhat whom does NOT include mono anywhere ( nor ever will ) in RHEE. 

cheers
nl

---

### Post by FuturePilot on 2007-09-06
Yes, get rid on Mono and then Linux will really be in a hole when it comes to photo management.:shock:

---

### Post by neighborlee on 2007-09-06
> **FuturePilot said:**
> Yes, get rid on Mono and then Linux will really be in a hole when it comes to photo management.:shock:

I'm on top of this not to worry ;)

[http://www.linux.com/articles/58887](http://www.linux.com/articles/58887)

cheers
nl

---

### Post by Andrewie on 2007-09-06
I can see why Novell is pushing Mono, right now the industry is really is making a shift to Java, and C#. Supporting this is what Novell's customers want. Is this hate fueled by Microsoft or is there some other reason. Has anyone used C#? I'm going to be learning it, next week so any feed back would be nice.

---

### Post by aks44 on 2007-09-06
> **Andrewie said:**
> Is this hate fueled by Microsoft or is there some other reason. Has anyone used C#?

"Thanks" to Java, JIT compiling has already proved its inefficiency, performance-wise.

It is OK for end-user applications (where the computer spends most of the time waiting for the user) but IMHO as soon as you're entering the back-office field the only sane thing to do is to ditch it.

From my POV, it's not a matter of companies (who cares, if the result is good), but of technology (and raw performance).

Oh well, call me old-school, I still prefer writing CGIs rather than PHP, they scale better... ;)

---

### Post by Andrewie on 2007-09-06
> **aks44 said:**
> "Thanks" to Java, JIT compiling has already proved its inefficiency, performance-wise.

It is OK for end-user applications (where the computer spends most of the time waiting for the user) but IMHO as soon as you're entering the back-office field the only sane thing to do is to ditch it.

From my POV, it's not a matter of companies (who cares, if the result is good), but of technology (and raw performance).

Oh well, call me old-school, I still prefer writing CGIs rather than PHP, they scale better... ;)

I would rather learn c/c++ but what can you do. So C# is just as slow as Java?

---

### Post by aks44 on 2007-09-06
> **Andrewie said:**
> I would rather learn c/c++ but what can you do. So C# is just as slow as Java?

C#, just like Java, is "compiled" to bytecode (the (in)famous CLI, Common Language Infrastructure), and compiled JIT (Just In Time). I don't know any comparative benchmarks but the technology is the same.

But I encourage everyone to go "mainstream" (ie. not C or C++). C and C++ will always be needed, and the less competent C++ programmers out there, the better my salary. ;)

---

### Post by fwilliams on 2007-09-09
Please stop supporting and using mono.  I like Ubuntu a lot, but will change to another distribution.  Get rid of tomboy and fspot and any other mono application from Ubuntu.  Let some else create a distribution based on Ubuntu that adds those applications if they want.   At least let people choose what they want during install.

---

### Post by Polygon on 2007-09-09
> **fwilliams said:**
> Please stop supporting and using mono.  I like Ubuntu a lot, but will change to another distribution.  Get rid of tomboy and fspot and any other mono application from Ubuntu.  Let some else create a distribution based on Ubuntu that adds those applications if they want.   At least let people choose what they want during install.

seems like a petty reason to stop using a distro because of two applications which you can easily uninstall if you dont want them on your system.

---

### Post by Anthem on 2007-09-09
> **Polygon said:**
> seems like a petty reason to stop using a distro because of two applications which you can easily uninstall if you dont want them on your system.
No doubt.

---

### Post by markba on 2007-09-10
> **fwilliams said:**
> Please stop supporting and using mono.  I like Ubuntu a lot, but will change to another distribution.  Get rid of tomboy and fspot and any other mono application from Ubuntu.  Let some else create a distribution based on Ubuntu that adds those applications if they want.   At least let people choose what they want during install.

AFAIK there are only three standard applications which make use of mono: f-spot, tomboy and beagle. 

For f-spot: strange is though that there's another photo-administrator, gthumb, also part of the standard install. Apart from the fact that this is confusing for users (why include two?), it indicates that these two are at least on par. If f-spot is removed from the standard install, because there's already gthumb, that leaves us tomboy. 

For tpmboy: many alternatives exist (zim is my favourite), so it should be possible for ubuntu to start completely without mono-based apps.

For beagle: tracker is already included in gutsy, thus beagle is already history there.

---

### Post by bruce89 on 2007-09-10
> **markba said:**
> AFAIK there are only three standard applications which make use of mono: f-spot, tomboy and beagle. 

Beagle is and has never been default in Ubuntu.

> **igknighted said:**
> Is this Gnome only, or will there be qt bindings?  Man, the absolute last thing we need to use OSS tools to lock people into either gtk or qt.

[QUOTE=http://live.gnome.org/Vala]Vala is a new programming language that aims to bring modern programming language features to GNOME developers without imposing any additional runtime requirements and without using a different ABI compared to applications and libraries written in C.[/QUOTE]

In other words, likely to be GNOME only. It is C# modified to fit GObject, which makes it a GNOME thing.

---

### Post by neighborlee on 2007-09-10
> **Anthem said:**
> No doubt.

It is not the idea of only two apps or whatever that bother him/me, its the inclusion beyond reason of mono when all signs point to doing it being a OSS debocle (  like poor nvidia getting blamed for 'tainting ' things well hmmmm )..fedora is removing it so...anyway if the other poster is correct that certainly is good news and I hope the gthumb is chosen as default if indeed it comes close'ish to what fspot can do...

cheers
nl

---

### Post by Frak on 2007-09-23
> **fwilliams said:**
> Please stop supporting and using mono.  I like Ubuntu a lot, but will change to another distribution.  Get rid of tomboy and fspot and any other mono application from Ubuntu.  Let some else create a distribution based on Ubuntu that adds those applications if they want.   At least let people choose what they want during install.
I guess GNUSense would be to your liking, its Ubuntu, without the mono or Beagle.

---

### Post by Blue Sky on 2007-09-23
Mono is inherently evil. The F-Spot and Beagle developers should be ashamed they are using it.

---

### Post by Awalton on 2007-09-29
This thread is as much a debate of technicalities as it is of religion. Should those who are righteous under Lord RMS, his nobelness of all things GNU and holy, accept an invitation from the Devil of Redmond, God of Flying Chairs?

Anyways, removing it isn't hard: "sudo apt-get remove mono-common". I will never used it, and I highly doubt anybody will ever make an application that will convince me to use it, so I'm not worried. 

I really don't know how Tomboy got its way into Gnome in the first place (a Note taking application that requires a 20MB runtime, are you kidding me), it seems like a few guys with Python could have coded up the same exact thing in less time using less code. If someone decides to take this seriously, more power to them, I just hope it's called "Prep" for the giggle factor, "Prep is a refined Tomboy".

F-Spot? Well we've got a dozen photo-managers, and my favorite will pretty much always be Nautilus/Thunar and EoG ;) (in other words, I don't care for fancy apps when a nice, concise, simple one will do). 

For the record, I don't touch Java either. Maybe I'm just a virtual-machine-phobe (or a bloataphobe, take your pick).

---

### Post by Wolki on 2007-09-29
> **Awalton said:**
> This thread is as much a debate of technicalities as it is of religion. Should those who are righteous under Lord RMS, his nobelness of all things GNU and holy, accept an invitation from the Devil of Redmond, God of Flying Chairs?

RMS actually seems to be not that fanatical about it - He thinks it might be dangerous because of potential patents and that we shouldn't depend on it too much, but that it's great that we have a free implementation of an often-used language, because all languages should have free implementations. See [http://www.germany.fsfeurope.org/documents/rms-fs-2006-03-09.en.html#q1](http://www.germany.fsfeurope.org/documents/rms-fs-2006-03-09.en.html#q1)

And I assume even Mono supporters occasinally worry about patents, and think about strategies around them - I'm a mild supporter and I definitely have some worries about that.

The conflict as I see it is more about people who care about free software vs. people who hate microsoft.

> I really don't know how Tomboy got its way into Gnome in the first place (a Note taking application that requires a 20MB runtime, are you kidding me), 

Its actual memory use seems to be quite low, it uses 19,1 MB of RSS, 3,1 MB of which are writable when in use, even less when it's not used for some time. It's almost never among the top 10 memory hogs on my computer, and I actually use it; plus it has lots of cool featuress and develops quickly - every release since it got added to GNOME has brought major new features.

Compared to that, Deskbar e.g. uses 36,1 MB RSS with 23,6 MB writable, even after not using it for quite some time. 

> F-Spot? Well we've got a dozen photo-managers, and my favorite will pretty much always be Nautilus/Thunar and EoG ;) (in other words, I don't care for fancy apps when a nice, concise, simple one will do). 


I'm similar in that regard (Nautilus/EoG is a nice combo), but f-spot is a very nice application for what it does. I rarely use it because I don't do a lot of photography, but if I would it'd be my choice.

> For the record, I don't touch Java either. Maybe I'm just a virtual-machine-phobe (or a bloataphobe, take your pick).

Python VM is ok though?

---

### Post by tageiru on 2007-09-29
> **Awalton said:**
> This thread is as much a debate of technicalities as it is of religion. Should those who are righteous under Lord RMS, his nobelness of all things GNU and holy, accept an invitation from the Devil of Redmond, God of Flying Chairs?

I think most GNU people welcome the contribution of GPL software. It's mainly the new people coming from Windows that, for various weird reasons, oppose the inclusion of Mono.

---

### Post by kirios on 2007-09-30
> **neighborlee said:**
> ..fedora is removing it so... 
[COLOR="DarkRed"]The Fedora people don't seem to have heard about that yet. :)[/COLOR]
[http://www.fedoraforum.org/forum/showthread.php?t=165708]("http://www.fedoraforum.org/forum/showthread.php?t=165708")

---

### Post by Joh_ on 2007-10-25
I can't believe this discussion is *still* (albeit half-actively) going on. :S

The thing is, Mono isn't the only CIL runtime for linux. There's also [one being developed by Gnu](http://www.gnu.org/software/dotgnu/) which seems to be relatively close to Mono's implementation (corlib, XML and WinForms). Mono is just way more complete.

Basically, my point is that whatever Gnu has no problem programming, I have no problem having on my system. In this case it just happens to be a CIL runtime.

---

### Post by pkid on 2007-12-03
Okay I am putting on my flame proof suite before giving my two cents worth.  I think that .net is pretty cool.  I have used PHP, Java and C#.  We use .net at work.  It is easy to use and I find myself very productive when using it.  I find it a bonus to be able to use a language that I know and have to use often at work at home in Linux.  Makes life so much easier.  And no I don't want to learn Python.  I am sure that it is great but it is just one more skill to learn and maintain and I am already struggling to juggle the .net and Java stuff.

I am guessing that if Microsoft really wanted to they could launch thousands of lawsuits at Linux.  They have thousands of patents and there is an incredibly good chance that Linux violates some of them.

This is my first post on the forums and I am looking forward to a good flaming by the Microsoft haters :)

---

### Post by Andrewie on 2007-12-03
qt 4 and kdevelop 4  already have their own c# bindings. Mono, and there is a new one from the gnu club. Just get your panties out of a bunch C# and Java aren't going anywhere.

---

### Post by fwilliams on 2007-12-10
Leave mono where it is.

Avoid making Gnome or KDE dependent on it

Jeff Waugh said Gnome is not currently dependent on it.

Pretty simple, the people who want to use it can use it.

The people who do not, can "sudo apt-get remove mono-common" and safely clean there system.

---

### Post by jordilin on 2007-12-24
> **fwilliams said:**
> Leave mono where it is.

Avoid making Gnome or KDE dependent on it

Jeff Waugh said Gnome is not currently dependent on it.

Pretty simple, the people who want to use it can use it.

The people who do not, can "sudo apt-get remove mono-common" and safely clean there system.

The last version of Gnome has Tomboy by default, which it is a Mono C# based application. I do not know if in the future there will be such dependency. Anyone knows?.  I would like to remember that C# is an ECMA standard and Mono is opensource, free software and Java is just beginning to be opensource. If you install sun-java, which is in the Ubuntu repositories, is worse than having mono by default. If you want to run Azureus, it will be highly recommended to use sun-java.

---

### Post by happysmileman on 2007-12-24
> Mono is a free implementation of Microsoft's language C#. Microsoft has declared itself our enemy and we know that Microsoft is getting patents on some features of C#. So I think it's dangerous to use C#, and it may be dangerous to use Mono. There&#8217;s nothing wrong with Mono. Mono is a free implementation of a language that users use. It's good to provide free implementations. We should have free implementations of every language. But, depending on it is dangerous, and we better not do that.

From RMS.

> On 2 November 2006, Microsoft and Novell announced a joint agreement whereby Microsoft agreed to not sue Novell&#8217;s customers for patent infringement.[9] According to Mono project leader Miguel de Icaza,[10] this agreement extends to Mono but only for Novell developers and customers. It was criticized by the free software community because it violates the principles of giving equal rights to all users of a particular program

So unless you work for, or pay Novell, it is not at all Free software. All it does to everyone else is introduce patent concerns and I'm not going to use it, hopefully others won't either

---

### Post by neighborlee on 2008-03-04
> **fwilliams said:**
> Leave mono where it is.

Avoid making Gnome or KDE dependent on it

Jeff Waugh said Gnome is not currently dependent on it.

Pretty simple, the people who want to use it can use it.

The people who do not, can "sudo apt-get remove mono-common" and safely clean there system.

Having to remove it in the first place is in the category of having it forced on me whether I want it or not. I dont like things forced on me, nor do many people , especially when its as clearly non gpl as  stated above.

I guess some people think they have the right to force people to do things because they are in the majority. Linux is about choice last time I checked, or is that a common fallacy...I realize of course I have the ability, given the source to spin my own version, I just never wanted to be part of fracturing the base and I still dont think I want to :)

cheers
nl

---

### Post by Sp4cedOut on 2008-03-04
> **neighborlee said:**
> Having to remove it in the first place is in the category of having it forced on me whether I want it or not. I dont like things forced on me, nor do many people , especially when its as clearly non gpl as  stated above.

I guess some people think they have the right to force people to do things because they are in the majority. Linux is about choice last time I checked, or is that a common fallacy...I realize of course I have the ability, given the source to spin my own version, I just never wanted to be part of fracturing the base and I still dont think I want to :)

cheers
nl

They also "force" GTK, GNU compilers, X11 libraries, Open Office Suite, Firefox, Metacity, and numerous other programs and libraries.  You can't possibly expect them to make different versions of Gnome or Ubuntu without Firefox for the people who don't want Firefox "forced" on them, and another without GNU compilers for those who don't want to have GNU "forced" on them, etc...  You really shouldn't install large pre-compiled operating systems and WMs if you don't want things forced on you, or start building your own distro with only the packages you want.

Which comes back to the original point: why does it matter?  It's not like Mono's not working and causing problems with your computer.  It's not like you can't remove it, I'm sure when you install a new OS you do a lot of customizing and tweaking to fit your needs, think of removing Mono as tweaking.  Then again, let's say there's a Mono program you need, it might be nice to have those 2MB library files.  Are you worried MS is going to sue you?

---

### Post by bruce89 on 2008-03-04
> **Sp4cedOut said:**
> You can't possibly expect them to make different versions of Gnome or Ubuntu without Firefox for the people who don't want Firefox "forced" on them[...]

Interesting when you look at the [least popular Ubuntu brainstorm]("http://brainstorm.ubuntu.com/idea/229/) idea. It is interesting to see the reaction of Firefox fans saying "I don't want Epiphany forced on me".

---

### Post by DoctorMO on 2008-03-04
> Then again, let's say there's a Mono program you need, it might be nice to have those 2MB library files. Are you worried MS is going to sue you?

Er 25MB I think you mean; besides I'm not worried about Microsoft, I'm worried that it's a pile of dingoes kidneys and poor unsuspecting programmers are wasting their time writing programs in it. If it wasn't installed by default perhaps they wouldn't be tempted to use it.

---

### Post by bruce89 on 2008-03-04
> **DoctorMO said:**
> Er 25MB I think you mean; besides I'm not worried about Microsoft, I'm worried that it's a pile of dingoes kidneys and poor unsuspecting programmers are wasting their time writing programs in it. If it wasn't installed by default perhaps they wouldn't be tempted to use it.

Hardly any programs not written by Novell themselves actually use mono.

---

### Post by igknighted on 2008-03-04
> **DoctorMO said:**
> Er 25MB I think you mean; besides I'm not worried about Microsoft, I'm worried that it's a pile of dingoes kidneys and poor unsuspecting programmers are wasting their time writing programs in it. If it wasn't installed by default perhaps they wouldn't be tempted to use it.

Then what languages, pray tell, does Dr Mo approve for Ubuntu/Linux programming?  Is it the fastest language available?  No, probably not.  But the cross platform ability (which is very real when done properly) allows distribution to various systems easily, and does so better than Java (at least this is a common sentiment I get from programmers, no real data to back it up though).

Forget all merits of the language... many people only learn to program in C# or vb.net.  Do we want to alienate these people from using linux and developing for linux?  I'm willing to be there are some pretty good C# programmers out there, and I'd like their expertise to be relevant to linux.  Not to mention all those poor college kids in CS programs who have to use C#/.NET or all those who have to use it at work.  Why limit their choice of operating systems by stifling the development of their platform.

As for including it as default... I will stand by my viewpoint of the best tools should be included.  If someone can create a better gtk-based photo manager than f-spot (and I am sure it can be done), then I would support its inclusion.  Same with tomboy.  And my choice of Banshee as a music library/player has nothing to do with it being mono... I just like the application.  If it was python or C I would still like it just as much... I frankly don't care about the language if the application works.  So if you really want mono gone... go write applications in a language you prefer that can rival and/or surpass the current mono ones.  But until you can provide suitable alternatives, mono will stay.

---

### Post by bruce89 on 2008-03-04
> **igknighted said:**
> But the cross platform ability (which is very real when done properly) allows distribution to various systems easily, and does so better than Java (at least this is a common sentiment I get from programmers, no real data to back it up though).


Saying as .NET's only complete implementation is on Windows, I find this hard to believe; doubly so since Java's GPL these days meaning new ports are pretty easy.

---

### Post by khensucat on 2008-03-05
I don't understand this.

Java is more of a danger to Linux than Mono. Why do people have a problem with Mono, but not with Java, Flash, blobs in the kernel, proprietary drivers so they can spin thier absurd little "cubes" for hours on end, etc... but get riled up over mono? Is it *just* because of MS? This seems a little tin-foil hattish :-(

---

### Post by Methuselah on 2008-03-05
Java has been open source.
Check the OpenJDK.

In any event, Mono isn't so bad.
We have Wine right?
Compatibility is good.
Being able to run .NET programs is advantageous.

However, I agree that it probably shouldn't be relied on for new open source software development when there are alternatives unecumbered in any way by Microsoft.

---

### Post by neighborlee on 2008-03-05
> **Methuselah said:**
> Java has been open source.
Check the OpenJDK.

In any event, Mono isn't so bad.
We have Wine right?
Compatibility is good.
Being able to run .NET programs is advantageous.

However, I agree that it probably shouldn't be relied on for new open source software development when there are alternatives unecumbered in any way by Microsoft.

Depends who you ask, what about it, depends who you ask, and I dont need it , all in that order ;)

Considering ( assuming website is correct) tomboy isnt even stable yet I dont really see the logic in including even it, and the same rationale goes for  f-spot for which exists a current bug that hasnt been addressed for about a year.

And what about RMS comments here:

Quote:
Mono is a free implementation of Microsoft's language C#. Microsoft has declared itself our enemy and we know that Microsoft is getting patents on some features of C#. So I think it's dangerous to use C#, and it may be dangerous to use Mono. There’s nothing wrong with Mono. Mono is a free implementation of a language that users use. It's good to provide free implementations. We should have free implementations of every language. But, depending on it is dangerous, and we better not do that.

**From RMS. ^^

or is this a current standing comment from him...if so its rather telling isn't it if you also consider that M$ doesn't even like MONO to get airtime for its meetings here:

[http://tirania.org/blog/archive/2005/Sep-06.html](http://tirania.org/blog/archive/2005/Sep-06.html) < and to think anyone trusts M$ intentions is kinda at question .

[http://port25.technet.com/archive/2006/08/11/Let_2700_s-talk-Mono_3A00_--Sam-interviews-Miguel-de-Icaza.aspx](http://port25.technet.com/archive/2006/08/11/Let_2700_s-talk-Mono_3A00_--Sam-interviews-Miguel-de-Icaza.aspx) < and this is also interesting as noted by:

[http://boycottnovell.com/2007/07/23/gnome-mono-dep/](http://boycottnovell.com/2007/07/23/gnome-mono-dep/)

Never hurts to keep up with current news ;)

I also find it odd that gnome would add MONO just for one tiny note taking app, and I wonder how many actually use it...

cheers
nl

---

### Post by loell on 2008-03-05
is it just me? or i'm just getting tired of reading an old controversial thread.

there is nothing left to be said here, maybe its time to get rid of the thread? (aka close it)?

---

### Post by khensucat on 2008-03-06
Would it help to point out the unreliability of boycottnovell, and the long-debunked "it rips out half your system" myth?

---

### Post by tbroderick on 2008-03-06
> **khensucat said:**
> Would it help to point out the unreliability of boycottnovell, and the long-debunked "it rips out half your system" myth?

Facts have no place in this discussion.

---

### Post by neighborlee on 2008-03-06
> **tbroderick said:**
> Facts have no place in this discussion.

I fail to see why facts have no place in this discussion ;)

Your are free to offer proof of boycotnovell myths if you wish, but I didn't see any; but I did see RMS making a good solid point that MONO is not a good idea to 'rely on', which says to me its prob.  not a  great idea to   have other apps 'depend' on it, and of course there are countless other URL's showcasing similar 'doubts' to going the MONO route including the link by SETH, so its not like there isn't anyone out there with  reasonable credentials doubting very m uch MONO.

Redhat used to be THE defacto standard  for linux, and for many it still is, yet it is defininitely not going to endorse MONO ever faik, so I think thats another indication  of the fruitless labor involved here.  I Gotta wonder how many that are for it, are for it for   shall we say speicific reasons.  Just MO  and I've a right to it, and I wonder does anyone have any debate on the URL's I posted or is everyone going to just let them stand as is  therefore insinuating they are correct and that MONO should be removed at once .

cheers
nl

---

### Post by khensucat on 2008-03-07
If by "if nobody replies to this then I win by default" you mean "everyone is pretty much tired of this argument, nothing new has been added, Redhat still packages Mono, Microsoft hasn't sued anyone, removing it doesn't harm anyone's system, and boycotnovells FUD/deadwrong vs. accidentally correct factor is about 2,000 to 1, being the "loose change" of the linux world, and most people are just sick to death of this tinfoil hat argument", then yes, you win ):P

---

### Post by Andrewie on 2008-03-07
When Microsoft starts suing then I'm all for removing it. I'm no expert and I'm not going to pretend to be one, but as long as Red Hat continues to ship it then I feel nothing is wrong.

---

### Post by neighborlee on 2008-03-07
> **Andrewie said:**
> When Microsoft starts suing then I'm all for removing it. I'm no expert and I'm not going to pretend to be one, but as long as Red Hat continues to ship it then I feel nothing is wrong.

helllo..redhat is not shipping MONO ;)..only fedora..there is a HUGE differecne ;)

cheers
nl

---

### Post by neighborlee on 2008-03-07
> **khensucat said:**
> If by "if nobody replies to this then I win by default" you mean "everyone is pretty much tired of this argument, nothing new has been added, Redhat still packages Mono, Microsoft hasn't sued anyone, removing it doesn't harm anyone's system, and boycotnovells FUD/deadwrong vs. accidentally correct factor is about 2,000 to 1, being the "loose change" of the linux world, and most people are just sick to death of this tinfoil hat argument", then yes, you win ):P

Not what I meant, and no redhat does not package mono, and it never will; your clearly thinking of fedora ;)

cheers
nl

---

### Post by PmDematagoda on 2008-03-07
> **loell said:**
> is it just me? or i'm just getting tired of reading an old controversial thread.

there is nothing left to be said here, maybe its time to get rid of the thread? (aka close it)?

Good point raised by loell, this thread has been moved to the Recurring Discussions section as this was already discussed at length in the Development section.

---

### Post by neighborlee on 2008-03-08
> **PmDematagoda said:**
> Good point raised by loell, this thread has been moved to the Recurring Discussions section as this was already discussed at length in the Development section.

Im not sure how saying you agree with someone saying something is 'controversial' when clearly its a reasonable debate raised not just by me, but many people with  solid credentials, including a major distro REdhat that atm isn't going anywhere near MONO, so I think one must be careful what one agrees with in its entirety ;)

I stilll dont see any comments on  why Redhat wont enforse MONO yet ubuntu is happy to do so, but now that this thead has been moved, maybe that threat  wont  exist for you anymore, and maybe that should tell me something about the freedom that ubuntu ( or lack thereof) really  represents ;)

cheers
nl

---

### Post by loell on 2008-03-08
**@neighborlee**

there are different ways to support the anti-mono advocacy, 

the productive ways are, 

1. to encourage people to use the non-mono equivalent apps.
2. write software to compete with those mono apps.


sadly, there are unproductive ways too.

like resurrecting a very old thread that dates back from 2006, while recycling the past points that has already been raised in this thread.

---

### Post by 23meg on 2008-03-08
[QUOTE=neighborlee]Your are free to offer proof of boycotnovell myths if you wish, [/QUOTE]

[http://jeffreystedfast.blogspot.com/2008/02/lots-of-gnomemono-fud-lately.html](http://jeffreystedfast.blogspot.com/2008/02/lots-of-gnomemono-fud-lately.html)

[QUOTE=neighborlee]but now that this thead has been moved, maybe that threat wont exist for you anymore, and maybe that should tell me something about the freedom that ubuntu ( or lack thereof) really represents[/QUOTE]

Indeed it should. In most forums, the thread would just have been closed. Here you're granted the freedom to beat the dead horse if it makes you feel good.

---

### Post by bruce89 on 2008-03-08
Take my advice : ignore all that call it "MONO".

---

### Post by saulgoode on 2008-03-09
I don't understand why this was moved to Recurring Discussions. The topic does not fit any of the bullet points in the Forum description, nor is it listed as one of the candidates in the stickied thread.

---

### Post by PmDematagoda on 2008-03-09
> **saulgoode said:**
> I don't understand why this was moved to Recurring Discussions. The topic does not fit any of the bullet points in the Forum description, nor is it listed as one of the candidates in the stickied thread.

This is because, as I stated previously, this topic was discussed heavily in the Development section so the points raised here are recurring hence the move.

---

### Post by ice60 on 2008-05-19
here's the week's most popular article on fsdaily.com. it's typical of the stuff they have there. 
[http://www.fsdaily.com/EndUser/Make_Your_Distro_Free_of_Miguel_de_Icaza_8217_s_junk_code](http://www.fsdaily.com/EndUser/Make_Your_Distro_Free_of_Miguel_de_Icaza_8217_s_junk_code)

i don't like fsdaily. i don't like the fsf either :lolflag:

---

### Post by ghindo on 2008-05-19
Direct link:

[http://tuxtraining.com/2008/05/17/make-your-distro-free-of-miguel-de-icazas-junk-code/](http://tuxtraining.com/2008/05/17/make-your-distro-free-of-miguel-de-icazas-junk-code/)

For a second there, I thought this was going to be yet-another-anti-GNOME thread. :p

---

### Post by Riffer on 2008-05-19
ok what is mono-comman and why should w get rid of it?

---

### Post by perce on 2008-05-19
I really don't get it. According to the experts, most software, free or not, infringes someone else's patents. So why is everybody happily going to install MP3 support, Windows codecs and fonts, libdvdcss, programs with progress bars (yes, that is patented too), pirate Adobe CS3 under Windows, and then freak out for Mono and moonlight (where it is not  even clear if it infringes any patent at all)?

---

### Post by madjr on 2008-05-19
i don't want anything from M$ but this may be a bit exaggerated ?

i don't use mono, moonlight, tomboy or f-spot (i prefer gthumb anyway).

---

### Post by vexorian on 2008-05-19
Stop caring about patents in Linux, I really think that civil dissbedience towards the software patent laws is the way to go now, just worry about proprietary vs. non-proprietary.

Regarding Mono, the real problem is but a practical one, why are we promoting/using what's basically a [lead pony](http://blogs.zdnet.com/open-source/?p=2445) for .net . What we should be doing is innovate, not imitate, and making everything depend on MS innvented technology doesn't sound smart to me.

---

### Post by hanzomon4 on 2008-05-20
It's not like mono is taking away from innovation on the Linux desktop. Besides tomboy, beagle, banshee!!!! They rock hard...

---

### Post by FuturePilot on 2008-05-20
not this Mono discussion again.....

---

### Post by jrusso2 on 2008-05-20
Poor Miguel, I remember when he was a Linux hero, now demoted to Linux Zero because he likes Microsoft.

---

### Post by Frak on 2008-05-20
> **FuturePilot said:**
> not this Mono discussion again.....
Guess what... YOU'RE GONNA LOVE IT!!!

Yet another Mono thread.

---

### Post by -grubby on 2008-05-20
> **FuturePilot said:**
> not this Mono discussion again.....

+1

> **Frak said:**
> Guess what... YOU'RE GONNA LOVE IT!!!

Yet another Mono thread.

I'm sure he will

---

### Post by FuturePilot on 2008-05-20
> **Frak said:**
> Guess what... YOU'RE GONNA LOVE IT!!!

Yet another Mono thread.

That made me lol :lolflag:

---

### Post by hanzomon4 on 2008-05-20
I just want to know if he was being cute by calling it mono which is common slang for an infectious disease...

---

### Post by loell on 2008-05-20
a very nice how to :lolflag:

it should be added in the tips and tutorials section :popcorn:

---

### Post by tbroderick on 2008-05-20
> **hanzomon4 said:**
> I just want to know if he was being cute by calling it mono which is common slang for an infectious disease...

No.

---

### Post by madjr on 2008-05-20
> **hanzomon4 said:**
> I just want to know if he was being cute by calling it mono which is common slang for an infectious disease...

Mono means monkey in spanish

that's why the logo is a monkey

---

### Post by hanzomon4 on 2008-05-20
I'm joking folks,

But really after all of these mono threads no one thought about mononucleosis. I mean it's pretty damn ironic, and funny.

---

### Post by karellen on 2008-05-20
](*,)

---

### Post by 3rdalbum on 2008-05-20
Maybe Miguel de Icaza only has one testicle?

Seriously though, it's not "junk code", it's just a compatibility layer for .NET.  But I agree that it shouldn't be used for Linux-only applications - that's just shooting yourselves in the foot!

---

### Post by loell on 2008-05-20
> **3rdalbum said:**
> Maybe Miguel de Icaza only has one testicle?


:lolflag:

---

### Post by p_quarles on 2008-05-20
Moved to Recurring Discussions.

Please be respectful toward Mr. Icaza, even if you don't agree with his decisions.

---

### Post by eragon100 on 2008-05-20
Booooorrrinnnggg!

zzz zzz zzz :lolflag:

---

### Post by vexorian on 2008-05-20
> **jrusso2 said:**
> Poor Miguel, I remember when he was a Linux hero, now demoted to Linux Zero because he likes Microsoft.
Seriously though he deserves it.

> Please be respectful toward Mr. Icaza, even if you don't agree with his decisions.


All the respect I had left for the guy vanished after this:
[http://tirania.org/blog/archive/2008/Apr-02.html](http://tirania.org/blog/archive/2008/Apr-02.html)

---

### Post by Frak on 2008-05-20
> **vexorian said:**
> Seriously though he deserves it.




All the respect I had left for the guy vanished after this:
[http://tirania.org/blog/archive/2008/Apr-02.html](http://tirania.org/blog/archive/2008/Apr-02.html)
I'm sorry that bringing operability to Linux was *such *an evil thing to do.

---

### Post by karellen on 2008-05-20
someone please put this thread out of his misery...

---

### Post by hanzomon4 on 2008-05-20
I'm not making fun of the man, I like mono..

---

### Post by quinnten83 on 2008-05-20
> **hanzomon4 said:**
> I'm not making fun of the man, I like mono..

Dude,
saying that around these here parts will get yer tarred and feathered!

---

### Post by Frak on 2008-05-20
> **quinnten83 said:**
> Dude,
saying that around these here parts will get yer tarred and feathered!
I like Mono, Moonlight, and OOXML translator too.

---

### Post by Kinst on 2008-05-20
This is the guy that created gnome you know.

---

### Post by cardinals_fan on 2008-05-20
> **Kinst said:**
> This is the guy that created gnome you know.
Which is my only real problem with him.

---

### Post by Frak on 2008-05-20
> **Kinst said:**
> This is the guy that created gnome you know.
And I thank him for it.

---

### Post by FuturePilot on 2008-05-20
> **hanzomon4 said:**
> I'm not making fun of the man, I like mono..


I like mono too.

> **Frak said:**
> And I thank him for it.

+1

---

### Post by quinnten83 on 2008-05-21
I don know if I like mono or not, I just like to use the pretty applications without steve or bill trying to put their grubby little hands on it and keeping me in a choke hold unless I pay them money.
Also I don't want it be illegal. My understanding is that if you use mono these freedoms can not be guaranteed as mono references MS proprietary stuff. This is the only thing that scares me.
There are certain things i don't like, not because they aren't open source, but because they support MS's bullying practices. But I am pragmatic enough to realize that there are certain things I will use because they are convenient.

I like Miguel de Icaza though, because his name sounds cool!
I will name my sons Miguel, maybe even my daughters.

---

### Post by hanzomon4 on 2008-05-21
[I]"It's Mya"
"It's Mya"
"Miguel"
"Miguel"
"Brothers and Sisters, It's Mya Miguel"[/I]

---

### Post by days_of_ruin on 2008-05-21
> **hanzomon4 said:**
> [I]"It's Mya"
"It's Mya"
"Miguel"
"Miguel"
"Brothers and Sisters, It's Mya Miguel"[/I]
:lolflag:

---

### Post by alternatealias on 2008-06-07
> **perce said:**
> I really don't get it. According to the experts, most software, free or not, infringes someone else's patents. So why is everybody happily going to install MP3 support, Windows codecs and fonts, libdvdcss, programs with progress bars (yes, that is patented too), pirate Adobe CS3 under Windows, and then freak out for Mono and moonlight (where it is not  even clear if it infringes any patent at all)?

Because the people who freak out about Mono are hypocrites.

---

### Post by alternatealias on 2008-06-07
> **vexorian said:**
> Stop caring about patents in Linux, I really think that civil dissbedience towards the software patent laws is the way to go now, just worry about proprietary vs. non-proprietary.

Regarding Mono, the real problem is but a practical one, why are we promoting/using what's basically a [lead pony](http://blogs.zdnet.com/open-source/?p=2445) for .net . What we should be doing is innovate, not imitate, and making everything depend on MS innvented technology doesn't sound smart to me.

Tell me oh great leader (who insults free software developers every chance he gets), what software innovations have *you* made?

Oh, that's right. None.

---

### Post by neighborlee on 2008-09-25
> **PmDematagoda said:**
> This is because, as I stated previously, this topic was discussed heavily in the Development section so the points raised here are recurring hence the move.

I think its moved where most people wont see it , thus in effect the debate is dead; unless of course we have some clever users that use search to find things but I suspect many dont bother, they just use their OS and dont have time to go hunting, but thats just my take on it.

I feel it is similar to the mcCain stance on the 'debates' ;) < if your keeping up on politics that is>

cheers
nl

---

### Post by cardinals_fan on 2008-09-25
> **neighborlee said:**
> I think its moved where most people wont see it , thus in effect the debate is dead; unless of course we have some clever users that use search to find things but I suspect many dont bother, they just use their OS and dont have time to go hunting, but thats just my take on it.

I feel it is similar to the mcCain stance on the 'debates' ;) < if your keeping up on politics that is>

cheers
nl
I doubt if people who "just use their OS and dont have time to go hunting" care much about Mono.  But maybe I'm crazy.

---

### Post by vexorian on 2009-02-19
> **alternatealias said:**
> Tell me oh great leader (who insults free software developers every chance he gets), what software innovations have *you* made?

Oh, that's right. None.
Hey i just found your post. It would be very easy to ask you or Miguel if you did anything innovative besides pushing MS IP on Linux. But I won't as you can see, such things are irrelevant. The fact I have not yet made any major contribution to free software is not relevant at all. It does not make my argument any less true, it does not prove that article wrong. In other words, my argument stands, while yours has become just a personal attack.

> I really don't get it. According to the experts, most software, free or not, infringes someone else's patents. So why is everybody happily going to install MP3 support, Windows codecs and fonts, libdvdcss, programs with progress bars (yes, that is patented too), pirate Adobe CS3 under Windows, and then freak out for Mono and moonlight (where it is not even clear if it infringes any patent at all)?

It is funny, cause ubuntu does freak out about even including those things on repos, has to use a restricted repository. Yet we are so happy to welcome Mono it as a requirement for our default apps. 

> Because the people who freak out about Mono are hypocrites.As I have just shown, being so eager to include Mono and Mono-dependent apps on the default, but not do so with mp3, DVD , fonts and etc. That's the true hypocrisy.

---

### Post by directhex on 2009-02-20
> **vexorian said:**
> Hey i just found your post. It would be very easy to ask you or Miguel if you did anything innovative besides pushing MS IP on Linux. But I won't as you can see, such things are irrelevant. The fact I have not yet made any major contribution to free software is not relevant at all. It does not make my argument any less true, it does not prove that article wrong. In other words, my argument stands, while yours has become just a personal attack.

Miguel started GNOME and other projects like Gnumeric. Does that count as something other than "pushing MS IP on Linux"? If you want a "miguel-free" system, run Kubuntu.

> It is funny, cause ubuntu does freak out about even including those things on repos, has to use a restricted repository. Yet we are so happy to welcome Mono it as a requirement for our default apps.

Mono is Free Software, implementing an international standard, and has never been the subject of patent-related threats. Why is it more dangerous than something like, say, Wine (which is not in Restricted/Multiverse)?

> As I have just shown, being so eager to include Mono and Mono-dependent apps on the default, but not do so with mp3, DVD , fonts and etc. That's the true hypocrisy.

If you can't understand the difference between a free software implementation of a standard, an actively protected patented codec, an actively protected DMCA-violating cracker, and closed-source files whose license expressly only permits their distribution in winzip-self-extractor form... then there's really very little anyone can do for you

---

### Post by saulgoode on 2009-02-20
> **directhex said:**
> If you can't understand the difference between a free software implementation of a standard, an actively protected patented codec, an actively protected DMCA-violating cracker, and closed-source files whose license expressly only permits their distribution in winzip-self-extractor form... then there's really very little anyone can do for you
If you would consider Mono to be a "free software implementation of a standard", why would you not consider libmpeg3 and FFMPEG to also be Free Software implementations of standards?

Since 'libdvdcss' has never been prosecuted, let alone convicted, for DMCA violations, wherein lies your distinction between it and Mono?

---

### Post by directhex on 2009-02-20
> **saulgoode said:**
> If you would consider Mono to be a "free software implementation of a standard", why would you not consider libmpeg3 and FFMPEG to also be Free Software implementations of standards?

Presumably you mean libmad or liblame there, and yes, those implement a standard (ffmpeg implements many things, some of which are standards and some of which are not).

So yes, those are indeed Free Software implementations of standards in part or in whole.

However, the MP3 standard requires implementation of a patented algorithm, which has a license fee attached - and people can and have been chased down for violation of those patents. e.g. [http://www.theregister.co.uk/2008/03/07/patent_crackdown_at_cebit/](http://www.theregister.co.uk/2008/03/07/patent_crackdown_at_cebit/)

> Since 'libdvdcss' has never been prosecuted, let alone convicted, for DMCA violations, wherein lies your distinction between it and Mono?

By "never" you mean "in a high profile case", right? [http://en.wikipedia.org/wiki/Dvd_jon#The_DeCSS_prosecution](http://en.wikipedia.org/wiki/Dvd_jon#The_DeCSS_prosecution)

---

### Post by saulgoode on 2009-02-20
> **directhex said:**
> Presumably you mean libmad or liblame there, and yes, those implement a standard (ffmpeg implements many things, some of which are standards and some of which are not).

So yes, those are indeed Free Software implementations of standards in part or in whole.

However, the MP3 standard requires implementation of a patented algorithm, which has a license fee attached - and people can and have been chased down for violation of those patents. e.g. [http://www.theregister.co.uk/2008/03/07/patent_crackdown_at_cebit/](http://www.theregister.co.uk/2008/03/07/patent_crackdown_at_cebit/)

According to the Mono Project, Microsoft holds patents on the core of the .NET Framework. There is allegedly some promise of royalty free licensing being made available; but even if such is true, there is more to software being "Free" than just cost.

> **directhex said:**
> By "never" you mean "in a high profile case", right? [http://en.wikipedia.org/wiki/Dvd_jon#The_DeCSS_prosecution](http://en.wikipedia.org/wiki/Dvd_jon#The_DeCSS_prosecution)
By "never" I meant "never". DeCSS is not libdvdcss and while I didn't mean to include DeCSS litigation in my assertion, I would point out that Mr Johansen was acquitted of all charges.

---

### Post by directhex on 2009-02-20
> **saulgoode said:**
> According to the Mono Project, Microsoft holds patents on the core of the .NET Framework. There is allegedly some promise of royalty free licensing being made available; but even if such is true, there is more to software being "Free" than just cost.

Software being "Free" has nothing to do with cost. It's to do with Freedom, as best defined in the Debian Free Software Guidelines.

The issue here is about software being "safe". That's gut feeling more than anything else. Some distributions come with MP3 support built in (because they don't feel that they're unsafe in doing so), others simply have no MP3 support at all (because they feel at high risk).

Where companies have actively threatened people (either other proprietary companies or Free Software developers), then regardless of the validity of their complaints, the supposedly infringing technology is generally either rewritten or dropped. Freetype was modified to avoid threats from Apple, for example.

Whether patent holders attack others is a measure of their business model. "Does it benefit me to do foo?" - for patent licensing companies (as surround MPEG patents) that's pretty obvious. For the case you're talking about... what is the compelling business argument for Microsoft to attack alternative ECMA-335 implementations, regardless of the legal validity of doing so? Would they win any prior-art arguments? Would they win any reciprocal attacks on Free Software companies' patents THEY violate? Would they win any goodwill or market share? Where's the profit in it?

> By "never" I meant "never". DeCSS is not libdvdcss and while I didn't mean to include DeCSS litigation in my assertion, I would point out that Mr Johansen was acquitted of all charges.

Charges... of computer hacking.

That doesn't help much with other complaints which can be pointed at people, such as DMCA violation, patent violation, or regional equivalents.

---

### Post by saulgoode on 2009-02-20
> **directhex said:**
> The issue here is about software being "safe". That's gut feeling more than anything else.
I agree with you on this; however a gut feeling of safety does seem a bit of a departure from the earlier suggestion that there exist significant tangible differences between an Open Source implementation of a patent-covered ISO/ECMA standard and Open Source implementations of patent-covered ISO/IETF standards.

Also, when considering the degree of safety of a "patent-covered" project, one should include the degree of potential "risk" that is being accepted. A tightrope walker may have just as much chance of falling from a highwire  10 feet above the ground as one 100 feet; however, there is a significant difference in the potential for harm. Likewise, there is a significant difference in the potential for harm between a project which provides audio/video support in a particular format and a project which provides a runtime environment for dozens of manifold programs.

---

### Post by directhex on 2009-02-20
> **saulgoode said:**
> I agree with you on this; however a gut feeling of safety does seem a bit of a departure from the earlier suggestion that there exist significant tangible differences between an Open Source implementation of a patent-covered ISO/ECMA standard and Open Source implementations of patent-covered ISO/IETF standards.

But that's the problem with software. What is infringing? What's the quote - "If an app is more than 10 lines long, it probably violates a software patent"? Does Mono violate any specific patents? Does GNOME? Does KDE? Does the kernel? Are those patents held by entities which actively sue for it?

MP3 is, by definition, an implementation of a patented algorithm, held by a number of hostile entities such as Fraunhofer IIS and Thompson. Whether Mono is or is not infringing on any patents held by hostile entities is a question much closer to the Freetype situation - patents *when brought to the attention of those responsible* can be worked around yet the same result achieved. Probably, anyway. With media codecs, what tends to be patented is the algorithm (laughable as that concept is) - with most other software, it's the means to a given end which is patented (and a different means can usually reach the same end). That's the significant difference you're looking for.

> Also, when considering the degree of safety of a "patent-covered" project, one should include the degree of potential "risk" that is being accepted. A tightrope walker may have just as much chance of falling from a highwire  10 feet above the ground as one 100 feet; however, there is a significant difference in the potential for harm. Likewise, there is a significant difference in the potential for harm between a project which provides audio/video support in a particular format and a project which provides a runtime environment for dozens of manifold programs.

So what specifically are you pointing towards as the risk point? If (as is claimed by some mentally subnormal blowhards), the Linux kernel violates 42 Microsoft patents, then does identification of them mean the kernel gets deleted entirely? Of course not - and I'd call the claimant a moron if they suggested it. Those specific elements would be reworked or even purged, but the overall project would remain. Similarly, if some component of Mono were attacked for patent violation, then that section would be reworked or dropped - but the apps would survive the attack. Escape route after escape route has been planned in from upstream to downstream to app developers - a cascading list of worst-case scenarios still leaves apps intact at the end, in varying degrees of modification.

Shouldn't app developers be the ones to decide on whether to accept that risk? Shouldn't distribution managers be the ones to decide on whether to accept the risk of accepting those packages?

---

### Post by Rokurosv on 2009-02-20
The only Mono application I've found useful is Gnome-Do, Docky is such an awesome dock, but needs more work.

---

### Post by directhex on 2009-02-20
> **Rokurosv said:**
> The only Mono application I've found useful is Gnome-Do, Docky is such an awesome dock, but needs more work.

I'm sure Dave & his team would welcome any contributions

---

### Post by Rokurosv on 2009-02-20
> **directhex said:**
> I'm sure Dave & his team would welcome any contributions

I've programmed with .NET before, haven't done it in a while though, mostly C# and VB. What languages are available for Mono?

---

### Post by alternatealias on 2009-02-20
Mono supports C#, VB, Nemerle, Boo, IronPython, IronRuby, etc.

---

### Post by karellen on 2009-02-21
threads like this make me bang my head against the wall and dump the Linux community forever. but I'm well aware that some zealots != the whole community consisting of people using and enjoying Linux (and, maybe, Windows)

---

### Post by directhex on 2009-02-21
> **Rokurosv said:**
> I've programmed with .NET before, haven't done it in a while though, mostly C# and VB. What languages are available for Mono?

Gnome-Do is written in C#, but remember that the Common Language Infrastructure allows multiple languages to interoperate seamlessly. In Jaunty, the following CLI languages exist: C#, VB.NET, Boo, Nemerle, Java, Python, ILasm

---

### Post by smartboyathome on 2009-02-21
If you want a GPL-compliant (therefore completely free in the GNU sense), then get GoBuntu. Since Mono doesn't violate the GPL, it gets included, and since GoBuntu is a GNU distro, they wouldn't tolerate it if Mono did do something illegal.

---

### Post by BuffaloX on 2009-02-22
I honestly don't know if mono is good or bad.
And this thread doesn't help too much.
At first it sounds like a really bad idea, why put ourselves unnecessarily in the line of fire?
But then I read about how Mono enabled the biggest accounting firm in Denmark to port their .Net based services to Linux, which enable some public offices to use Linux too, which sounds great.

Miguel de Icaza says he is very aware of US patent law, and have said that although he doesn't like US patent law he needs to work within the rules, and that he sleeps very well at night.

Miguel has done a lot of good for Linux, I think he still does.

---

### Post by HowardJZ on 2009-03-12
> **Xace123 said:**
> I see that the ubuntu-desktop package depends on mono now. I'm investing heavily in Ubuntu and I think this is a bad decision, moreover when there are other alternatives.
...


I agree. Get rid of mono, really anything produced at Novell.

For more information, see these links:

[http://boycottnovell.com/2009/03/11/abolish-mono-and-moonlight/](http://boycottnovell.com/2009/03/11/abolish-mono-and-moonlight/)

[http://boycottnovell.com/2009/03/11/bruce-perens-on-novell-ms/](http://boycottnovell.com/2009/03/11/bruce-perens-on-novell-ms/)

---

### Post by smartboyathome on 2009-03-12
> **HowardJZ said:**
> I agree. Get rid of mono, really anything produced at Novell.

For more information, see these links:

[http://boycottnovell.com/2009/03/11/abolish-mono-and-moonlight/](http://boycottnovell.com/2009/03/11/abolish-mono-and-moonlight/)

[http://boycottnovell.com/2009/03/11/bruce-perens-on-novell-ms/](http://boycottnovell.com/2009/03/11/bruce-perens-on-novell-ms/)

1) boycottnovell has been known to create facts, and thus isn't a reputable source.
2) If you want to get rid of anything related to Novell, get off Linux, as even the kernel and many drivers, programs, etc have code from Novell.
3) Tell me what Novell did that was wrong. If you say they made a deal with Microsoft, think of this: Red Hat did too. Plus, as I said in another thread, Novell wouldn't have made the deal if it meant it would destroy/harm Linux, as they are very heavily invested in it.

---

### Post by directhex on 2009-03-12
> **smartboyathome said:**
> 1) boycottnovell has been known to create facts, and thus isn't a reputable source.

They make things up on a daily basis. They're brilliant comedy. And as far as objectivity goes, the last piece of thread necrophilia on this thread was courtesy a BN contributor.

One interesting note: BN's founder quit in disgust at the worse-than-4chan level of discourse the site's main editor and contributing trolls provided.

The thing to remember, though, is it's not their fault. Whilst the casual observer might thing BN wants Free Software to fail with the constant attacks against Free projects and users and distros etc because they're simply haters of Free Software... Google for "Hanlon's Razor" for the best explanation for their behaviour

> **Andrewie said:**
> When Microsoft starts suing then I'm all for removing it

Agreed.

> **igknighted said:**
> As for including it as default... I will stand by my viewpoint of the best tools should be included.  If someone can create a better gtk-based photo manager than f-spot (and I am sure it can be done), then I would support its inclusion.  Same with tomboy.  And my choice of Banshee as a music library/player has nothing to do with it being mono... I just like the application.  If it was python or C I would still like it just as much... I frankly don't care about the language if the application works.  So if you really want mono gone... go write applications in a language you prefer that can rival and/or surpass the current mono ones.  But until you can provide suitable alternatives, mono will stay.

Absolutely agreed. I want Ubuntu to be great, that's my concern. Dropping Beagle in favour of Tracker was a good call - dropping, say, Tomboy for Zim would be a moron move.

---

### Post by jordilin on 2009-03-12
There are great applications in Mono like Tomboy and f-spot. Gnome (not Ubuntu) [www.gnome.org](www.gnome.org) includes Tomboy by default if you were to build your own distro. Mono is opensource and .Net is an ECMA standard by which anybody can implement its own .net version if you want to. Mono is not the only one implementing the CLI. Take a look at [http://www.gnu.org/software/dotgnu/](http://www.gnu.org/software/dotgnu/)
Linux is about free of choice amongst other things. Don't like Mono? Remove it. Removing Mono could imply removing Gnome? Use Kde, Xfce, fluxbox, etc...

---

### Post by directhex on 2009-03-12
> **jordilin said:**
> There are great applications in Mono like Tomboy and f-spot. Gnome (not Ubuntu) [www.gnome.org](www.gnome.org) includes Tomboy by default if you were to build your own distro. Mono is opensource and .Net is an ECMA standard by which anybody can implement its own .net version if you want to. Mono is not the only one implementing the CLI. Take a look at [http://www.gnu.org/software/dotgnu/](http://www.gnu.org/software/dotgnu/)
Linux is about free of choice amongst other things. Don't like Mono? Remove it. Removing Mono could imply removing Gnome? Use Kde, Xfce, fluxbox, etc...

Removing Mono has never removed GNOME on Ubuntu. Mono apps are Recommends: of ubuntu-desktop - you can remove Recommends without causing dependency issues

---

### Post by jordilin on 2009-03-12
> **directhex said:**
> Removing Mono has never removed GNOME on Ubuntu. Mono apps are Recommends: of ubuntu-desktop - you can remove Recommends without causing dependency issues

which is great for those who love Gnome and dont like mono.

---

### Post by directhex on 2009-03-12
> **jordilin said:**
> which is great for those who love Gnome and dont like mono.

True

And for those with an obvious agenda to push, little details like reality can't be allowed to get in the way of a good lie

---

### Post by Yfrwlf on 2009-04-22
Microsoft has attacked Linux with software patents.  They can go to hell.  This is Linux, and this is their direct competition.  Of course they want Linux developers making software they can run on their crufty soon-to-be-more-irrelevant OS under terms they control.  Amazing how fast everyone forgets things.

But if users here want to run Microsoft Linux, it's their choice, I just think it's a bad one and not helpful for Linux in the long run.  The "it's OK, we'll replace it later if they start being jerks about it" concept is horribly flawed.  The more you start investing time and effort in Microsoft Linux apps, the less everyone will want to abandon them, and the more leverage Microsoft will have in asking for royalties when they come to collect for patent infringement.  Dump it now while it's still easy.

Don't ignore history, let it teach you a lesson.  There are many articles about Microsoft attacking Linux via patent claims.  Read up on it sometime.

---

### Post by directhex on 2009-04-22
> **Yfrwlf said:**
> Microsoft has attacked Linux with software patents.  They can go to hell.  This is Linux, and this is their direct competition.  Of course they want Linux developers making software they can run on their crufty soon-to-be-more-irrelevant OS under terms they control.  Amazing how fast everyone forgets things.

But if users here want to run Microsoft Linux, it's their choice, I just think it's a bad one and not helpful for Linux in the long run.  The "it's OK, we'll replace it later if they start being jerks about it" concept is horribly flawed.  The more you start investing time and effort in Microsoft Linux apps, the less everyone will want to abandon them, and the more leverage Microsoft will have in asking for royalties when they come to collect for patent infringement.  Dump it now while it's still easy.

Don't ignore history, let it teach you a lesson.  There are many articles about Microsoft attacking Linux via patent claims.  Read up on it sometime.

[http://www2.apebox.org/wordpress/rants/70/](http://www2.apebox.org/wordpress/rants/70/)

And "many articles" doesn't count if they're on anti-Free-Software blogs like Boycott Novell

---

### Post by saulgoode on 2009-04-22
> **directhex said:**
> And "many articles" doesn't count if they're on anti-Free-Software blogs like Boycott Novell
A Google search of "microsoft attacking Linux via patent claims" (Yfrwlf's words) produces 519,000 results. While the first result is actually from Boycott Novell, it is an article about MS attacking *Google* (perhaps Google weights themselves higher when searching).  BN.com does not appear again in at least the next 12 pages of results (I gave up after page 13).

There were indeed many articles from a wide variety of sources. Certainly not all of them can be dismissed by tossing out trite accusations of being "anti-Free-Software".

Here is a sampling of some of those sites: 
[INDENT]arstechnica.com
businessinsider.com
computerworlduk.com
engadget.com
eweek.com
forbes.com
gartner.com
huffingtonpost.com
informationweek.com
internetnews.com
itworld.com
linux.com
linuxdevices.com
linux-foundation.org
linuxjournal.com
linuxplanet.com
linux-watch.com
linuxworld.com
seattlepi.com
techflash.com
techrepublic.com
zdnet.com[/INDENT]

---

### Post by Tibuda on 2009-04-22
We should also get rid of FAT/NTFS file systems, Samba, MSN protocol in Pidgin, Wine, MS Office formats in Open Office...

---

### Post by Bios Element on 2009-04-22
> **danielrmt said:**
> We should also get rid of FAT/NTFS file systems, Samba, MSN protocol in Pidgin, Wine, MS Office formats in Open Office...

Don't forget we should remove the menu's, desktop, icons, "window" interface while we're at it just chop everything else out. >.>

---

### Post by directhex on 2009-04-22
> **Bios Element said:**
> Don't forget we should remove the menu's, desktop, icons, "window" interface while we're at it just chop everything else out. >.>

Partial list at the bottom of [http://www2.apebox.org/wordpress/linux/51/](http://www2.apebox.org/wordpress/linux/51/)

---

### Post by cb951303 on 2009-04-22
you know I read a lot of mono hate threads but I still don't know on what base microsoft can sue linux. I mean C# is an ecma standard and .NET library is reimplemented from scratch for mono. What would be the official accusation? If it's patents, which ones exactly?

EDIT: nevermind, I found it on previous page.
I don't know why they let people to have patents for these kind of information.

---

### Post by pimz on 2009-04-22
Now Mono is intergrated in Jaunty Gnome (GTK) will a fork emerge? :popcorn:

---

### Post by Dragonbite on 2009-04-22
Oh, this argument again...

Use [gNewSense]("http://www.gnewsense.org/") since it's all about open source.. wait, it includes Mono.

Use KDE, so long as you don't use kbeagle (or whatever it is, the KDE front-end for Beagle).

Why not pick a distribution that lets you pick what you want during installation, like Fedora?

---

### Post by directhex on 2009-04-22
> **pimz said:**
> Now Mono is intergrated in Jaunty Gnome (GTK) will a fork emerge? :popcorn:

Mono's level of integration in Ubuntu remains unchanged since 6.10.

---

### Post by Yfrwlf on 2009-04-22
> **danielrmt said:**
> We should also get rid of FAT/NTFS file systems, Samba, MSN protocol in Pidgin, Wine, MS Office formats in Open Office...

The difference is all those can be easily chopped, as they are easily disposable, but building entire programs on their so-called "standards" which are lumped in together with non-standard proprietary code in most books (because they care about Windows, not just the "standard" parts) means you are 100% playing in their sandbox.  It's investing time and money into learning a virus that can spread, because a programming language means you are directly in violation every step of the way.

M$ is anti-Linux and have tried collecting royalties from Linux before, that's the entire point of the Novell deal which um is still going on AFAIK, so like anyone is going to trust them now.  Sorry but for some reason Linux users are weary of M$ traps now, no clue why. ^^

.NET is and always will be slanted towards M$ and their Windows platform, that's what it was designed for.  Mono is the sample, but if you want the whole .NET cinnabun, you have to pay for Windows.  That's the way it will always be.  "Come to Windows if you want the REAL fully-compatible version."  It will never function exactly as the Windows version does and the Windows version will have better features because it will use all the extensions and bells and whistles which are NOT part of the "standards".

But any way, I don't care what users here do, but I choose neutral vendors that care about all platforms equally or just about Linux, and actually directly support Linux instead of M$ using Novell as their delivery boy, and who, you know, don't threaten one of their very indirectly-supported platforms by threatening them with patent lawsuits.  Those are the companies I support, who aren't 90% illegal in their monopolistic business practices.  M$ is a very immoral company, if you actually know their history.  There are many corporations who are, but this is about operating systems, they're the biggest and the worst and I hope they die out because of their crimes though it's already too late in a sense.  The most anyone can hope for is that their empire doesn't continue for too much longer and I hope the EU continues to fight them for fair consumer rights because we all know the U.S. certainly doesn't care if consumers have no choice when they go to buy a computer.

---

### Post by karellen on 2009-04-22
> **Yfrwlf said:**
> The difference is all those can be easily chopped, as they are easily disposable, but building entire programs on their so-called "standards" which are lumped in together with non-standard proprietary code in most books (because they care about Windows, not just the "standard" parts) means you are 100% playing in their sandbox.  It's investing time and money into learning a virus that can spread, because a programming language means you are directly in violation every step of the way.

M$ is anti-Linux and have tried collecting royalties from Linux before, that's the entire point of the Novell deal which um is still going on AFAIK, so like anyone is going to trust them now.  **Sorry but for some reason Linux users are weary of M$ traps now, no clue why**. ^^

.NET is and always will be slanted towards M$ and their Windows platform, that's what it was designed for.  Mono is the sample, but if you want the whole .NET cinnabun, you have to pay for Windows.  That's the way it will always be.  "Come to Windows if you want the REAL fully-compatible version."  It will never function exactly as the Windows version does and the Windows version will have better features because it will use all the extensions and bells and whistles which are NOT part of the "standards".

But any way, I don't care what users here do, but I choose neutral vendors that care about all platforms equally or just about Linux, and actually directly support Linux instead of M$ using Novell as their delivery boy, and who, you know, don't threaten one of their very indirectly-supported platforms by threatening them with patent lawsuits.  Those are the companies I support, who aren't 90% illegal in their monopolistic business practices.  M$ is a very immoral company, if you actually know their history.  There are many corporations who are, but this is about operating systems, they're the biggest and the worst and I hope they die out because of their crimes though it's already too late in a sense.  The most anyone can hope for is that their empire doesn't continue for too much longer and I hope the EU continues to fight them for fair consumer rights because we all know the U.S. certainly doesn't care if consumers have no choice when they go to buy a computer.

I'm not sure you have a clue about what you're talking about about. if you read Mono's license, you'll see it's GPL. what more do you want? besides hate and pleas for tinfoil hats...

---

### Post by smartboyathome on 2009-04-22
> **Yfrwlf said:**
> The difference is all those can be easily chopped, as they are easily disposable, but building entire programs on their so-called "standards" which are lumped in together with non-standard proprietary code in most books (because they care about Windows, not just the "standard" parts) means you are 100% playing in their sandbox.  It's investing time and money into learning a virus that can spread, because a programming language means you are directly in violation every step of the way.

M$ is anti-Linux and have tried collecting royalties from Linux before, that's the entire point of the Novell deal which um is still going on AFAIK, so like anyone is going to trust them now.  Sorry but for some reason Linux users are weary of M$ traps now, no clue why. ^^

.NET is and always will be slanted towards M$ and their Windows platform, that's what it was designed for.  Mono is the sample, but if you want the whole .NET cinnabun, you have to pay for Windows.  That's the way it will always be.  "Come to Windows if you want the REAL fully-compatible version."  It will never function exactly as the Windows version does and the Windows version will have better features because it will use all the extensions and bells and whistles which are NOT part of the "standards".

But any way, I don't care what users here do, but I choose neutral vendors that care about all platforms equally or just about Linux, and actually directly support Linux instead of M$ using Novell as their delivery boy, and who, you know, don't threaten one of their very indirectly-supported platforms by threatening them with patent lawsuits.  Those are the companies I support, who aren't 90% illegal in their monopolistic business practices.  M$ is a very immoral company, if you actually know their history.  There are many corporations who are, but this is about operating systems, they're the biggest and the worst and I hope they die out because of their crimes though it's already too late in a sense.  The most anyone can hope for is that their empire doesn't continue for too much longer and I hope the EU continues to fight them for fair consumer rights because we all know the U.S. certainly doesn't care if consumers have no choice when they go to buy a computer.

Now you're just spreading FUD. Mono IS based on standards, and while it does *offer* windows proprietary stuff, it is neither in the default Ubuntu install, nor compiled by default. You have to specifically tell Mono to compile that stuff, and thus you aren't affected by patents unless you do.

---

### Post by directhex on 2009-04-22
> **Yfrwlf said:**
> .NET is and always will be slanted towards M$ and their Windows platform, that's what it was designed for.  Mono is the sample, but if you want the whole .NET cinnabun, you have to pay for Windows.  That's the way it will always be.  "Come to Windows if you want the REAL fully-compatible version."  It will never function exactly as the Windows version does and the Windows version will have better features because it will use all the extensions and bells and whistles which are NOT part of the "standards".

This is an attack - not an observation or argument - used ONLY by people who would never use *ANY* ".NET cinnabun", if indeed they program at all.

Fortunately, it was [already rebuffed](http://mono-project.com/Mailpost:longreply) as far back as ***2002***:

[quote=Miguel de Icaza]* What if we never can keep up?

	There is the issue that we might not be able to keep up (right
    now, we dont, as .NET Framework 1.0 is already out there, and we
    are, well still underway).  Also, theoretically there is the risk
    of a given API being unimplementable on Unix.

	Even if that is the case, we still win, because we would get
    this nice programming environment, that althought might not end up
    being 100% .NET Framework compatible, it would still be an
    improvement and would still help us move forward.  So we can reuse
    all the research and development done by Microsoft on these ideas,
    and use as much as we can.[/quote]

Mono was already being used to write decent Linux apps, far faster & easier than any other comparable framework, as far back as 2002, by leveraging Free Software enhancements to the core parts of .NET, such as GTK#. The far-flung parts of the spec? they don't *matter* for apps like Gnome-Do or Tomboy, they only matter for Windows switchers. And at that point, the question is "do we want it to be easier for these guys to migrate from Windows to Linux?" Pick your answer wisely.

---

### Post by Dragonbite on 2009-04-22
Another side benefit that people don't notice all that much is that Mono is finding its way into gaming engines and virtual worlds like Second Life. If Mono makes moves into gaming enough then maybe that could help cross-platform games as Java, Python, Ruby, PHP, Ajax and everybody else has not.

---

### Post by gnomeuser on 2009-04-22
> **directhex said:**
> This is an attack - not an observation or argument - used ONLY by people who would never use *ANY* ".NET cinnabun", if indeed they program at all.

Fortunately, it was [already rebuffed](http://mono-project.com/Mailpost:longreply) as far back as ***2002***:

Mono was already being used to write decent Linux apps, far faster & easier than any other comparable framework, as far back as 2002, by leveraging Free Software enhancements to the core parts of .NET, such as GTK#. The far-flung parts of the spec? they don't *matter* for apps like Gnome-Do or Tomboy, they only matter for Windows switchers. And at that point, the question is "do we want it to be easier for these guys to migrate from Windows to Linux?" Pick your answer wisely.

Not to mention that there are several areas where Mono is ahead of the Microsoft reference implementation like the C# shell which Microsoft won't be shipping till 2012. There are also areas where Mono expands on the .NET standard in useful ways such as Mono.SIMD. Work that can be taken to the ECMA standardization group once it's polished and proven some more.

People making the claim that Mono will always be playing catchup to Microsoft' reference implementation are simply not living in reality. It is clear that Mono is capable of not only keeping up with MS.NET in every relevant area but also outpace it and innovate within the standard as well.

---

### Post by Mateo on 2009-04-22
does mono have the asp ajax stuff?

---

### Post by Yfrwlf on 2009-04-23
> **smartboyathome said:**
> Now you're just spreading FUD. Mono IS based on standards, and while it does *offer* windows proprietary stuff, it is neither in the default Ubuntu install, nor compiled by default. You have to specifically tell Mono to compile that stuff, and thus you aren't affected by patents unless you do.

Um ya it is, I have to remove it on every fresh Ubuntu install.  Mono is included on the Live CD and gets installed.

As for everyone else using Microsoft-backed and patented programming languages, have fun with that.  I'm supporting other efforts though. ^^

---

### Post by Tibuda on 2009-04-23
> **Yfrwlf said:**
> Um ya it is, I have to remove it on every fresh Ubuntu install.  Mono is included on the Live CD and gets installed.
Mono is installed, but not Windows Forms.



@Mateo:
> [Yes, Mono versions after 1.9 do support ASP.NET AJAX.]("http://www.mono-project.com/FAQ:_ASP.NET")

---

### Post by Dragonbite on 2009-04-23
> **Yfrwlf said:**
> Um ya it is, I have to remove it on every fresh Ubuntu install.  Mono is included on the Live CD and gets installed.

As for everyone else using Microsoft-backed and patented programming languages, have fun with that.  I'm supporting other efforts though. ^^

You're free to use whatever you want, really.  I poke around Mono because at work I'm using .NET (unfortunately it's VB.NET base ASP.NET which is the least supported language in Monodevelop). I'm not going crazy with it since I don't get that much time to do things at home.

If Mono is that important for avoiding then look to a KDE based app (Kerry is the Beagle-engine with KDE front end) or Fedora, openSUSE or one of the distributions that allows you to pick-and-choose the applications instead of using a LiveCD.  Even an Ubuntu Alternative disk may allow you to bypass that selection.

As for myself, I'm really disliking F-spot, don't use Tomboy and Banshee is the only one I may use and that I'm not married to because Rythmbox works fine (providing I can get the iPod connected).

---

### Post by xoluxo on 2009-04-25
> **Yfrwlf said:**
> The difference is all those can be easily chopped, as they are easily disposable, but building entire programs on their so-called "standards" which are lumped in together with non-standard proprietary code in most books (because they care about Windows, not just the "standard" parts) means you are 100% playing in their sandbox.  It's investing time and money into learning a virus that can spread, because a programming language means you are directly in violation every step of the way.


Microsoft has been in business for a long time.

If you are going to dismiss those on the grounds that they are "easily chopped" (easier said than done) let us look at some other examples, programming interfaces.

Microsoft invented COM in the 90's and they got patents on it.   COM is the "old" .NET, and it was a useful invention for creating component software.    

Both Firefox's core and OpenOffice contain implementations of the patented bits.   And they live at the very core of these two applications, everything in these apps is built on top of COM.   In Firefox is it called XPCOM, and in OpenOffice it is called UNO.

Firefox' XPCOM is not limited to firefox, it has been used in VirtualBox, in Thunderbird, in Songbird and anything else that needed a COM implementation.   UNO has not been as successful as a platform, but the entire office suite infringes.

You can actually find many more examples using Google Code search:

[http://www.google.com/codesearch?q=iunknown+queryinterface](http://www.google.com/codesearch?q=iunknown+queryinterface)

And you can find all the patents related to the invention here:

[http://www.google.com/patents?q=queryinterface+iunknown](http://www.google.com/patents?q=queryinterface+iunknown)

> 
.NET is and always will be slanted towards M$ and their Windows platform, that's what it was designed for.  Mono is the sample, but if you want the whole .NET cinnabun, you have to pay for Windows.  That's the way it will always be.  "Come to Windows if you want the REAL fully-compatible version."  It will never function exactly as the Windows version does and the Windows version will have better features because it will use all the extensions and bells and whistles which are NOT part of the "standards".


But Linux users do not need the whole "cinnabun".   In fact, all of the Gnome apps built with Mono use the ECMA Core plus their own native APIs: Gtk#, Mono.Posix and others.  

None of that WPF, Windows.Forms or ASP.NET.

---

### Post by alternatealias on 2009-04-27
> **xoluxo said:**
> Microsoft has been in business for a long time.

If you are going to dismiss those on the grounds that they are "easily chopped" (easier said than done) let us look at some other examples, programming interfaces.

Microsoft invented COM in the 90's and they got patents on it.   COM is the "old" .NET, and it was a useful invention for creating component software.    

Both Firefox's core and OpenOffice contain implementations of the patented bits.   And they live at the very core of these two applications, everything in these apps is built on top of COM.   In Firefox is it called XPCOM, and in OpenOffice it is called UNO.

Firefox' XPCOM is not limited to firefox, it has been used in VirtualBox, in Thunderbird, in Songbird and anything else that needed a COM implementation.   UNO has not been as successful as a platform, but the entire office suite infringes.

This is an excellent point that most people forget (including me!).

---

### Post by Kilon on 2009-04-28
I am surely a windows hater but when it comes to .NET framework I am a huge fan. I am 100% behind the mono effort even though I have chosen python as my programming language. 

I would love however to see DELPHI .NET supported by mono. Already the open source community has done an amazing job with FreePascal and Lazarus. 

I cannot see Microsoft as big evil company, as any big company it does what every big company is doing . 

Personally I have turned completely to pen source and this is punishment enough for these companies. I exclude Apple because they genuinely care for their customers.

---

### Post by TheForkOfJustice on 2009-04-28
I have no idea how often this has been talked to death but does anyone else think they should leave Mono out of the next release?

Only a few disposable and easily-replaced programs use Mono and I hear it's a bit buggy to boot.  I hate removing all those -cil packages.

Anyone feel the same way?

---

### Post by doas777 on 2009-04-28
Why? linux is about choice. if you don't want to use them, then don't.
mono-develop is no visual studio yet, but with the last release they got what i really wanted: step-thru.

just my 2 bits

---

### Post by SKLP on 2009-04-28
> **TheForkOfJustice said:**
> I have no idea how often this has been talked to death but does anyone else think they should leave Mono out of the next release?Not this topic again.... Mono is here to stay, and It's looking like Banshee will replace Rhythmbox in the default install soon (hopefully) :)
> 
Only a few disposable and easily-replaced programs use Mono and I hear it's a bit buggy to boot. Quite a few apps use Mono. What do you mean by "buggy to boot".
>  I hate removing all those -cil packages. If you hate to remove them, then don't! :))
> Anyone feel the same way?Not me.

---

### Post by ghindo on 2009-04-28
Oh, this thread will end well.

---

### Post by Mehall on 2009-04-28
The main reason so many people want rid of Mono isn't for any reason other than it's an MS-based (wel... based on an MS design) product, not for any programming reason.
Mono is OSI certified (unlike Moonlight) so I don't have that issue.

From the other (good reasoning) end of the spectrum, I don't really have any problem with it.

Also: one of the most popular apps, Gnome-Do, needs Mono.

---

### Post by SKLP on 2009-04-28
> **ghindo said:**
> Oh, this thread will end well.Indeed

---

### Post by SKLP on 2009-04-28
> **Mehall said:**
> The main reason so many people want rid of Mono isn't for any reason other than it's an MS-based (wel... based on an MS design) product, not for any programming reason. Probably true, sadly.
> Mono is OSI certified (unlike Moonlight) so I don't have that issue.If by OSI-certified you mean it's released under OSI-approved license(s), then both are OSI-approved. Not that I like moonlight that much. All the javascript and flash is bad enough at it is.

---

### Post by sertse on 2009-04-28
This has been argued ad-infinitum that it's safe to assume Ubuntu knows all the various arguments already, and actively decided to stay with mono. 

What surprises me are users who think otherwise about Ubuntu.

---

### Post by Starks on 2009-04-28
Apparently Moonlight is now officially called Microsoft Moonlight.

[http://boycottnovell.com/2009/04/25/moonlight-renamed-microsoft-moonlight/](http://boycottnovell.com/2009/04/25/moonlight-renamed-microsoft-moonlight/)

---

### Post by Mehall on 2009-04-28
> **SKLP said:**
> Probably true, sadly.
If by OSI-certified you mean it's released under OSI-approved license(s), then both are OSI-approved. Not that I like moonlight that much. All the javascript and flash is bad enough at it is.

Moonlight itself is released yes, but for it to work it requires binary codecs from MSFT. As a whole, it is not OSI certified, but it get's the license since, theoretically, an OSI-certified codec *could* do the job were one to exist.

Also: the OSI-certification is under question since it's theoretically only distributable by Novell, though that has yet to be challenged properly (Ubuntu including it in the repo's and Novell/MSFT making no moves to a lawsuit says it isn't actually going to be called upon.)

---

### Post by SKLP on 2009-04-28
> **Mehall said:**
> Moonlight itself is released yes, but for it to work it requires binary codecs from MSFT. As a whole, it is not OSI certified, but it get's the license since, theoretically, an OSI-certified codec *could* do the job were one to exist.
Moonlight is available with open source codecs in the jaunty repository (package: moonlight-plugin-mozilla), FYI. 
> Also: the OSI-certification is under question since it's theoretically only distributable by Novell, though that has yet to be challenged properly (Ubuntu including it in the repo's and Novell/MSFT making no moves to a lawsuit says it isn't actually going to be called upon.)All software is threatened by software patents.

---

### Post by ronacc on 2009-04-28
the close association of mono with microsoft taints it beyond any possible redemption .

---

### Post by Mehall on 2009-04-28
> **ronacc said:**
> the close association of mono with microsoft taints it beyond any possible redemption .

I hope you built your computer out of devices whose hardware manufacturers support the open source drivers for their hardware.

This means no ATi pre-2006, no nVidia, no Intel (well.. half and half...)

and no countless other pieces of hardware (almost certainly including any WiFi card you have)

What's that? You bought <Insert OEM's name here, possibly Dell, Hp, etc.>?

Then your computer has a closer association with MSFT than Mono does.

I am not a fan of MSFTs business tactics, not by any means, but really, don't be that guy (and by that guy, I mean the stereotypical Linux user.)

---

### Post by SKLP on 2009-04-28
> **mehall said:**
> i hope you built your computer out of devices whose hardware manufacturers support the open source drivers for their hardware.

This means no ati pre-2006, no nvidia, no intel (well.. Half and half...)

and no countless other pieces of hardware (almost certainly including any wifi card you have)

what's that? You bought <insert oem's name here, possibly dell, hp, etc.>?

Then your computer has a closer association with msft than mono does.

I am not a fan of msfts business tactics, not by any means, but really, don't be that guy (and by that guy, i mean the stereotypical linux user.)+1

---

### Post by ronacc on 2009-04-28
> **Mehall said:**
> I hope you built your computer out of devices whose hardware manufacturers support the open source drivers for their hardware.

This means no ATi pre-2006, no nVidia, no Intel (well.. half and half...)

and no countless other pieces of hardware (almost certainly including any WiFi card you have)

What's that? You bought <Insert OEM's name here, possibly Dell, Hp, etc.>?

Then your computer has a closer association with MSFT than Mono does.

I am not a fan of MSFTs business tactics, not by any means, but really, don't be that guy (and by that guy, I mean the stereotypical Linux user.)

as a mater of fact I do build my own boxes, for several reasons, one of which is to avoid the "windows tax" since I have been exclusively linux for a decade , and I do prefer hardware vendors that strongly support linux although I am not hardcore about only running opensource drivers . When I bought my eeepc 701 I got the xandros model ofcourse ( it now sports jaunty on the ssd and puppy on an sdhc card ). my extreme hatred of all things MS predates linux by a long time .

---

### Post by lamalex on 2009-04-28
> **Starks said:**
> Apparently Moonlight is now officially called Microsoft Moonlight.

[http://boycottnovell.com/2009/04/25/moonlight-renamed-microsoft-moonlight/](http://boycottnovell.com/2009/04/25/moonlight-renamed-microsoft-moonlight/)

Is this supposed to be sarcasm? You don't cite boycottnovell if you want to make a serious argument with respect to Mono, those guys wouldn't know good journalism if ... I can't even think of a hyperbole, they just wouldn't know good journalism period.


OP: I don't know who told you mono was buggy (boycottnovel maybe?), it's not. You probably don't even realize you're using mono apps half the time you're using them, I know I've met tons of people who are shocked to learn that f-spot, tomboy, banshee, and GNOME Do are mono apps. Removing Mono would be a major step back for Ubuntu, and ultimately this is a moot discussion as it's really been discussed to death. Let dead horses lie.

---

### Post by ronacc on 2009-04-28
perhaps their journalism isn't up to your standards but their sentiment is alright by me , I was a dedicated SuSe user until they made a deal with the devil .

---

### Post by ninjapirate89 on 2009-04-28
Doesn't gnome-do run on mono? If so then I will never be without Mono again.

---

### Post by -grubby on 2009-04-28
Why do people have to hate on Mono so much? It's fine, and the applications written in it (At least the ones I've used) are very high quality. 

BUT OHNOES IT'S REMOTELY RELATED TO MICRO$$$$$$$$$$$OFT WE'RE ALL GOING TO DIE!!11111

---

### Post by ghindo on 2009-04-29
I don't really have much of an opinion on Mono one way or another, but one aspect of Mono I keep hearing about is "managed code."  What does this mean, and how is this an advantage versus other programming languages?

---

### Post by gtr32 on 2009-04-29
> **ghindo said:**
> I don't really have much of an opinion on Mono one way or another, but one aspect of Mono I keep hearing about is "managed code."  What does this mean, and how is this an advantage versus other programming languages?

Managed code means it runs in virtual machine, like Java. An application compiled with f.e. Visual Studio on MS platform will run with Mono on Linux (or OSX) if coded correctly, does not include native calls (unmanaged code) and Mono has the .NET libraries implemented.

---

### Post by directhex on 2009-04-29
> **ghindo said:**
> Oh, this thread will end well.

This thread will end dipped in chocolate and pure liquid ***awesome***

---

### Post by directhex on 2009-04-29
> **Starks said:**
> Apparently Moonlight is now officially called Microsoft Moonlight.

[http://boycottnovell.com/2009/04/25/moonlight-renamed-microsoft-moonlight/](http://boycottnovell.com/2009/04/25/moonlight-renamed-microsoft-moonlight/)

Nope, it's not. BoycottNovell is fiction, not fact.

---

### Post by directhex on 2009-04-29
> **Mehall said:**
> Moonlight itself is released yes, but for it to work it requires binary codecs from MSFT. As a whole, it is not OSI certified, but it get's the license since, theoretically, an OSI-certified codec *could* do the job were one to exist.

Like ffmpeg, for example? The way the Moonlight packages in every distro use ffmpeg?

Funny thing is, codecs (like MP3, needed by Silverlight amongst others) ARE patented - you can either violate the patents with ffmpeg, or use a patent-licensed decoder in the Microsoft Media Pack. Which is the lesser evil?

---

### Post by smbm on 2009-04-29
> **TheForkOfJustice said:**
> I have no idea how often this has been talked to death but does anyone else think they should leave Mono out of the next release?

Only a few disposable and easily-replaced programs use Mono and I hear it's a bit buggy to boot.  I hate removing all those -cil packages.

Anyone feel the same way?

Absolutely not.

---

### Post by directhex on 2009-04-29
> **smbm said:**
> Absolutely not.

The decision is made anyway:

```
(11:12:02 AM) jcastro: <blfgomes> QUESTION: Recently, the idea of replacing Rhythmbox for Banshee in Karmic has resparked the Mono debate in the Ubuntu community. As the SABDFL, what is your view on Mono? Is it safe to build a distribution that depends on it?
(11:12:28 AM) sabdfl: yes, i believe mono is a reasonable runtime to include in a distribution like ubuntu
(11:12:45 AM) sabdfl: i don't expect microsoft to launch any IP assaults based on mono adoption, they have said they will not do that
(11:12:51 AM) sabdfl: next?
```

---

### Post by smbm on 2009-04-29
> **directhex said:**
> The decision is made anyway:

```
(11:12:02 AM) jcastro: <blfgomes> QUESTION: Recently, the idea of replacing Rhythmbox for Banshee in Karmic has resparked the Mono debate in the Ubuntu community. As the SABDFL, what is your view on Mono? Is it safe to build a distribution that depends on it?
(11:12:28 AM) sabdfl: yes, i believe mono is a reasonable runtime to include in a distribution like ubuntu
(11:12:45 AM) sabdfl: i don't expect microsoft to launch any IP assaults based on mono adoption, they have said they will not do that
(11:12:51 AM) sabdfl: next?
```

Yeah, I'm just reading through that too. I'm glad Mark doesn't listen to all the FUD.

Did you get to the bit about the new look yet?

---

### Post by saulgoode on 2009-04-29
> (11:12:45 AM) sabdfl: i don't expect microsoft to launch any IP assaults based on mono adoption, they have said they will not do that

Where did Microsoft say that?

---

### Post by directhex on 2009-04-29
> **saulgoode said:**
> Where did Microsoft say that?

Ask Mark, not me. Presumably he's referring to the EMCA terms they agreed to for standardization.

---

### Post by saulgoode on 2009-04-29
> **directhex said:**
> Ask Mark, not me. Presumably he's referring to the EMCA terms they agreed to for standardization.

It must be something else, [the ECMA terms (PDF)]("http://www.ecma-international.org/publications/files/ECMA-ST/Ecma%20PATENT/ECMA-334%20&%20335/2001ga-123%20&%202002ga-003.pdf") to which Microsoft agreed only says that they will be offering RAND licensing upon request.

---

### Post by directhex on 2009-04-29
> **saulgoode said:**
> It must be something else, [the ECMA terms (PDF)]("http://www.ecma-international.org/publications/files/ECMA-ST/Ecma%20PATENT/ECMA-334%20&%20335/2001ga-123%20&%202002ga-003.pdf") to which Microsoft agreed only says that they will be offering RAND licensing upon request.

Then ask him, not me. I had nothing to do with the Q&A session above, nor to Ubuntu's decision to include Mono, including by default.

---

### Post by Kilon on 2009-04-30
.NET is amazing. 

It is by far the best product of Microsoft. 

It will be a huge mistake for UBUNTU to dismiss MONO. 

No there is no question that MONO is here to stay for a very very long time.  

I only wish for a Delphi .NET support in MONO.This would be the icing on the cake. 

I am in love with python at the moment but Delphi .NET is my second best option. 


GO MONO GO!!!!!

---

### Post by TheForkOfJustice on 2009-04-30
To clarify my OP comment:  I have no problem with Mono, programs that use it, or even Microsoft (yet).  Even, the thread I saw that mentioned that Mono programs were buggy seems to be gone too, so ignore that part in my OP post.

My main reason for not wanting it on Ubuntu is that installing many, many packages to run two (or a few) non-essential programs is inefficient and they should be replaced with programs written in Python or some other, more ubiquitous library.

I'm in charge of my own Ubuntu distro and need to remove unnecessary packages like Mono and the few apps that use it to make space for the packages I require.  Adding Gnome-Do and Banshee to the mix wouldn't justify my keeping it in my release.  

From this experience I don't see how that justifies it being in Ubuntu either. In the future, more valuable programs using Mono will exist and at that point it will be essential on the CD.  But I don't see that as the case now.

If Mono had a killer app then things would be different.  For example VLC, which I use in my distro for media.  It moved from Python to QT so I had to now install QT just for VLC since it wasn't in Ubuntu by default.  Still, VLC's usefulness at playing media with no codec-hunting made it too valuable to abandon so I kept it.

Also, as a side note, one day MS will make Mono act like crap on unix systems after it is adopted for use in core programs.  The FOSS community would have to abandon Mono and replace those programs in other languages which would mean a technological gap of years as we play catch up and MS will enjoy every minute.

Just my opinion.

---

### Post by mister_pink on 2009-04-30
I don't think there's any need to remove mono, but its got to be a prime target for removing from the default install to make space on the CD. As far as I can tell its only tomboy notes that actually needs it, which I'm sure we can live without.

---

### Post by Tibuda on 2009-04-30
> **mister_pink said:**
> I don't think there's any need to remove mono, but its got to be a prime target for removing from the default install to make space on the CD. As far as I can tell its only tomboy notes that actually needs it, which I'm sure we can live without.

No, there's also F-Spot. But they are planning to replace Rhythmbox with Banshee, and free around 7MB in the CD (not sure about this number).

EDIT: See [this thread]("http://ubuntuforums.org/showthread.php?t=1128206"), it would free 6MB.

---

### Post by Tibuda on 2009-04-30
> **TheForkOfJustice said:**
> Also, as a side note, one day MS will make Mono act like crap on unix systems after it is adopted for use in core programs.  The FOSS community would have to abandon Mono and replace those programs in other languages which would mean a technological gap of years as we play catch up and MS will enjoy every minute.
There's no MS code in Mono. It's a open source project. How Microsoft will "make Mono act like crap on unix" without those Linux guys behind Mono (Miguel et al) noticing it?

---

### Post by oack on 2009-04-30
After reading all this thread I am on the fence as to whether MONO is a good thing for Ubuntu.

---

### Post by gnomeuser on 2009-05-01
> **TheForkOfJustice said:**
> To clarify my OP comment:  I have no problem with Mono, programs that use it, or even Microsoft (yet).  Even, the thread I saw that mentioned that Mono programs were buggy seems to be gone too, so ignore that part in my OP post.


Excellent, but then why encourage discriminatory treatment of Mono and Mono based applications. If these do provide us with desirable functionality and are supportable within the contraints of Ubuntu let them participate on a level playing field.

> 
My main reason for not wanting it on Ubuntu is that installing many, many packages to run two (or a few) non-essential programs is inefficient and they should be replaced with programs written in Python or some other, more ubiquitous library.


What make you certain python is more efficient and by what metric do you measure this?

> 
I'm in charge of my own Ubuntu distro and need to remove unnecessary packages like Mono and the few apps that use it to make space for the packages I require.  Adding Gnome-Do and Banshee to the mix wouldn't justify my keeping it in my release. 


Your distro, your rules. 

However optimizations of the Mono stack in Ubuntu has allowed Banshee to replace Rhythmbox while [saving 6 megs](http://www2.apebox.org/wordpress/rants/74/) of space on the CD. 

More can be saved on gnome-do e.g. once it is figured out how to split out the plugins more so to reduce the amount of dependencies.

Tomboy is also smaller than the (so far feature incomplete) reimplementation in C++ GNote.  

> 
From this experience I don't see how that justifies it being in Ubuntu either. In the future, more valuable programs using Mono will exist and at that point it will be essential on the CD.  But I don't see that as the case now.


I thought just earlier you didn't at all disagree with Mono being allowable in Ubuntu (even if you seem to advocate it being a second class citizen).

> 
If Mono had a killer app then things would be different.  For example VLC, which I use in my distro for media.  It moved from Python to QT so I had to now install QT just for VLC since it wasn't in Ubuntu by default.  Still, VLC's usefulness at playing media with no codec-hunting made it too valuable to abandon so I kept it.


First: Python is a programming language and QT is a graphics (amongst other things) library they are not directly replacable as you seem to think.

Secondly: Mono has plenty of fine applications, Moonlight e.g. allows your users to enjoy Silverlight content in a 100% compatible fashion (SL1 currently, SL2 coming soon). Banshee has a rich featureset and an active community, it is a kickass media player. Tomboy, Tasque, Giver and not to forget MonoDevelop a fine IDE which serves more than just .NET. There are plenty of good Mono based applications to pick from and the collection is growing.

> 
Also, as a side note, one day MS will make Mono act like crap on unix systems after it is adopted for use in core programs.  The FOSS community would have to abandon Mono and replace those programs in other languages which would mean a technological gap of years as we play catch up and MS will enjoy every minute.

Just my opinion.

Mono is a community project implementing an ECMA standard under a set of OSI approved licenses. The applications built with it for Linux largely consist of programs using a mix of the Mono stack (gnome bindings, etc.) and .NET (As defined by ECMA). What way do you envision Microsoft being able to affect this? ([and don't say patents](http://www2.apebox.org/wordpress/linux/51/)).

Just the facts.

---

### Post by doas777 on 2009-05-01
op, i understand your desire to slim down ubuntu a bit; one of my close friends is  much the same way. 

I personally learned my lesson about removing packages referred to in ubuntu-desktop, with a failed upgrade to hardy last year, so I just remove launchers to apps that i don't plan to use. the worst part is that the folks at launchpad, pointed it out to me some months before, and I just forgot. now, I really avoid both removing ubuntu-desktop member packages, and doing version upgrades.

you may wanna vote for this brainstorm Idea: [http://brainstorm.ubuntu.com/idea/8358/](http://brainstorm.ubuntu.com/idea/8358/)

in the end, you may want to try one of the lightweight distros, like dsl or puppy or gentoo. or even bsd. ubuntu tries to be all things to all people, an approach that gains marketshare, but is designed such that it is almost always more than needed by any one user. 

I love python, but i don't believe it has the performance that .net does. I am a .net developer, so I may be a bit biased, but at home I do usually use python for many small to medium tasks. if i want a gui though, or a step thru debugger,  then nothing beats .net whether you using mono-develop or vs 2k8.

all that is important in my view is openness. if mono is open, and the code I write with it (personal code, not paid-for) , then it's all good.

have fun

---

### Post by monsterstack on 2009-05-04
Oh the ol' mono argument. I don't use it for moral reasons and remove it wherever it appears, and I suspect people who don't like mono will do likewise. People who do like mono won't do these things. And I'm okay with that. Still I have a few questions for some of the people here in this thread.

Mark Shutlleworth [says if it becomes a problem in the future]("http://boycottnovell.com/2008/02/22/mark-shuttleworth-on-patents/") [boycottnovell.com], then it will be removed from Ubuntu. Pretty simple really. Deal with the problems if and when they arise. Hurray! Common-sense approach.

I have a few niggling problems with this ordeal. I know only the hackiest C, and nothing of either C++ or C#, so I can't really comment on the merits of each, and I won't.

The biggest problem I have with all this nonsense is Silverlight. Yes Moonlight is free software, but as I see it, it will always be crippled by having to play catch-up with the proprietary Silverlight. Even if the devs do manage to keep up-to-date, it still stifles the community by not allowing them to innovate. The proprietary nature of Silverlight stifles the moonlight guys by forcing them to march to Microsoft's beat. I'm no superl33t hacker, but I imagine it is very difficult to try and make a clone of a moving target, however endorsed the attempt to do so is. Personally, I'd much prefer it if people worked on stuff that was open from start to finish, codecs and all. But what do others think?

I've seen a few people here in this thread disregard the patent issues around mono. That's fair enough. After all it is possible to violate a patent with one line in a terminal window. We can't go around living in fear of patents. Microsoft may go after vulnerable saps such as tomtom, but to go after any major GNU/Linux distribution head-on would fail, and they know it. So far so good.

I'd like to know people's opinion on [this]("http://www.microsoft.com/interop/msnovellcollab/moonlight.mspx") [microsoft.com]. As far as I can tell Silverlight is completely toxic in every respect, and makes a mockery of the ideals of free software. And more than that, it goes completely against the openness that helped create the internet in the first place.

The reason I don't have a problem with the use of mono per se is choice. I have a choice not to use it. The only mono app I might consider using is fstop. When it comes to internet content, that freedom is effectively taken away from me by things such as Silverlight. Has anyone ever come across a site that "requires internet explorer" to work properly? Do you remember the rage you felt? This is what Silverlight feels like to me.

It isn't just Silverlight of course. Flash also irks me. I don't think that having vast swathes of content on the internet provided by closed-off apps that only have a few lacklustre free implementations is good for GNU/Linux, or good for anybody for that matter.

What are people's thoughts on this particular issue? I'm quite interested to know.

---

### Post by directhex on 2009-05-05
> **monsterstack said:**
> Mark Shutlleworth [says if it becomes a problem in the future]("http://boycottnovell.com/2008/02/22/mark-shuttleworth-on-patents/") [boycottnovell.com], then it will be removed from Ubuntu. Pretty simple really. Deal with the problems if and when they arise. Hurray! Common-sense approach.

Agreed entirely.

> The biggest problem I have with all this nonsense is Silverlight. Yes Moonlight is free software, but as I see it, it will always be crippled by having to play catch-up with the proprietary Silverlight. Even if the devs do manage to keep up-to-date, it still stifles the community by not allowing them to innovate. The proprietary nature of Silverlight stifles the moonlight guys by forcing them to march to Microsoft's beat. I'm no superl33t hacker, but I imagine it is very difficult to try and make a clone of a moving target, however endorsed the attempt to do so is. Personally, I'd much prefer it if people worked on stuff that was open from start to finish, codecs and all. But what do others think?

I've seen a few people here in this thread disregard the patent issues around mono. That's fair enough. After all it is possible to violate a patent with one line in a terminal window. We can't go around living in fear of patents. Microsoft may go after vulnerable saps such as tomtom, but to go after any major GNU/Linux distribution head-on would fail, and they know it. So far so good.

I'd like to know people's opinion on [this]("http://www.microsoft.com/interop/msnovellcollab/moonlight.mspx") [microsoft.com]. As far as I can tell Silverlight is completely toxic in every respect, and makes a mockery of the ideals of free software. And more than that, it goes completely against the openness that helped create the internet in the first place.

The reason I don't have a problem with the use of mono per se is choice. I have a choice not to use it. The only mono app I might consider using is fstop. When it comes to internet content, that freedom is effectively taken away from me by things such as Silverlight. Has anyone ever come across a site that "requires internet explorer" to work properly? Do you remember the rage you felt? This is what Silverlight feels like to me.

It isn't just Silverlight of course. Flash also irks me. I don't think that having vast swathes of content on the internet provided by closed-off apps that only have a few lacklustre free implementations is good for GNU/Linux, or good for anybody for that matter.

There's room for some degree of overlap here. For example, the solution touted by some quarters of the community is the <video> tag. If we ignore the functionality issues with blind use of <video>, one of the real issues with it is it will *never* mandate the codecs those same people want - Nokia's killed that dead.

Catch-up sucks. And unlike Mono, on the web, you're right about there only being one direction things can go - the "official" way (Microsoft's). It should be noted though that there are some cool places for Moonlight to push the envelope, even to Silverlight users: for example, the Moonlight developers have already implemented a feature from SL3 which lets you write codecs in C# and use any media format for video/audio: meaning right now, if you serve your content using SL, you can use Dirac/Vorbis files and have them work on legacy browsers like IE8 without requring any dodgy Media Player add-ons that never work. Which is sorta neat.

To an extent, look at it this way - if a web company decides it really likes Adobe or Microsoft content creation slash serving tools, then given the size of the Linux market, then they'll worry about Windows users first. If they WANT to focus on the Linux market, then the availability of things like Moonlight means they have the option of continuing to use the tools they're using, but simply need to do some QA to test it - or limit their use of APIs that aren't yet available. It's a rather more "gentle" way for them to support Linux people than ripping out an entire infrastructure, re-encoding all their media to a different format, or worse - MLB.com recently changed from SL to "Flash", but not real Flash - Flash with a huge unstable Windows-only add-on to play WMV-encoded files (as they already have their media in WMV). And sadly, there's much more chance of the SL-based site having worked in Linux, especially given Moonlight 1.9's release, than there is of the new WMV-eating add-on to Flash working there.

Oh, and have you SEEN the performance difference between Flash & Moonlight? It's like night & day. FLash kills my i7 920 on HD video, Moon barely flickers. And that's without the GPU acceleration stuff being worked on.

---

### Post by monsterstack on 2009-05-05
> Catch-up sucks. And unlike Mono, on the web, you're right about there only being one direction things can go - the "official" way (Microsoft's). It should be noted though that there are some cool places for Moonlight to push the envelope, even to Silverlight users: for example, the Moonlight developers have already implemented a feature from SL3 which lets you write codecs in C# and use any media format for video/audio: meaning right now, if you serve your content using SL, you can use Dirac/Vorbis files and have them work on legacy browsers like IE8 without requring any dodgy Media Player add-ons that never work. Which is sorta neat.


I agree that it fills a gap for now, but I am not sure how sustainable it is in the long term. All future innovation rests in the hands of the few. Firefox became so popular precisely because it gave the users what they wanted and became the first browser to have proper pop-up stopping capabilities. Microsoft held off incorporating it into IE for a long time, and they paid the price. Nowadays Microsoft puts a lot of effort into making sure IE is a decent browser because they have to. 

But the whole Silverlight thing flies in the face of that. On the one hand they're responding to the ubiquity of Flash and developing some pretty cool tech at the same time, but on the other they're developing a locked-in system. Which leads me to this scary made-up scenario: imagine a world where Linux users log on to the internet in a .Net Internet Explorer clone. Would we even have such features that Firefox and Internet Explorer have now? Would such innovation be possible? It isn't a great example as the two situations are not very analogous. Even so, we are now faced with the prospect of an internet where lots of content is served up via proprietary Silverlight- or Flash-based plugins. I deferred migrating to 64-bit Linux for a long time purely because Adobe's support was lacking. Even today, Flash in Linux is often buggy and cruddy.

> To an extent, look at it this way - if a web company decides it really likes Adobe or Microsoft content creation slash serving tools, then given the size of the Linux market, then they'll worry about Windows users first. If they WANT to focus on the Linux market, then the availability of things like Moonlight means they have the option of continuing to use the tools they're using, but simply need to do some QA to test it - or limit their use of APIs that aren't yet available. It's a rather more "gentle" way for them to support Linux people than ripping out an entire infrastructure, re-encoding all their media to a different format, or worse - MLB.com recently changed from SL to "Flash", but not real Flash - Flash with a huge unstable Windows-only add-on to play WMV-encoded files (as they already have their media in WMV). And sadly, there's much more chance of the SL-based site having worked in Linux, especially given Moonlight 1.9's release, than there is of the new WMV-eating add-on to Flash working there.

Sure, but it's hardly ideal. It's the same attitude that probably causes a lot of Windows application developers to think, "Well it'll probably work in Wine." If developers start thinking this way, then nothing is ever really going to change. And worse, if Linux remains an afterthought in the minds of net application developers we'll be left with reduced-functionality (yet admirable) catch-up apps, which will fuel the fires of "Linux is not ready for prime-time" trolls for years to come, and with good reason.

---

### Post by directhex on 2009-05-05
> **monsterstack said:**
> I agree that it fills a gap for now, but I am not sure how sustainable it is in the long term. All future innovation rests in the hands of the few. Firefox became so popular precisely because it gave the users what they wanted and became the first browser to have proper pop-up stopping capabilities. Microsoft held off incorporating it into IE for a long time, and they paid the price. Nowadays Microsoft puts a lot of effort into making sure IE is a decent browser because they have to.

Competition drives innovation. Whodathinkit?

> But the whole Silverlight thing flies in the face of that. On the one hand they're responding to the ubiquity of Flash and developing some pretty cool tech at the same time, but on the other they're developing a locked-in system. Which leads me to this scary made-up scenario: imagine a world where Linux users log on to the internet in a .Net Internet Explorer clone. Would we even have such features that Firefox and Internet Explorer have now? Would such innovation be possible? It isn't a great example as the two situations are not very analogous. Even so, we are now faced with the prospect of an internet where lots of content is served up via proprietary Silverlight- or Flash-based plugins. I deferred migrating to 64-bit Linux for a long time purely because Adobe's support was lacking. Even today, Flash in Linux is often buggy and cruddy.

Question is, which is the greater evil of the two? Regardless of neato samples on the Mozilla website, <video> isn't the holy grail it was meant to be, thanks to Nokia. To an extent, having both technologies available might be the best for everyone - both formats will need to compete, and Linux compatibility (e.g. ability to be used with the growing netbook market, especially with the advent of ARM-based netbooks) may be a core issue to compete over. You can use Moonlight today on ARM - not so Adobe Flash.

> Sure, but it's hardly ideal. It's the same attitude that probably causes a lot of Windows application developers to think, "Well it'll probably work in Wine." If developers start thinking this way, then nothing is ever really going to change. And worse, if Linux remains an afterthought in the minds of net application developers we'll be left with reduced-functionality (yet admirable) catch-up apps, which will fuel the fires of "Linux is not ready for prime-time" trolls for years to come, and with good reason.

Perhaps. But there are plenty of companies out there who aren't ready for a complete epiphany - and I'd rather there be "stop-gap" measures (see: Picasa for Linux using an embedded copy of Wine) rather than Linux being frozen out completely. And with any luck, it can lead to *eventual* adoption of "our" way of doing things - e.g. games for Windows are now starting to use embedded Mono rather than Microsoft.NET - so the barrier for them to release on Linux is reduced (only the graphics engine needs porting, their scripting engine is now already portable). The again, everything bar the graphics being written in Python didn't help us get a port of Civilization 4.

Who knows. Time will tell.

---

### Post by monsterstack on 2009-05-05
> Competition drives innovation. Whodathinkit?

Well yes. You can give me ten points obviousness I suppose. :P

> Question is, which is the greater evil of the two?

Neither option is one I'd rather have, and I can't really make a choice between the two. If you put a gun to my head I'd have to go with Flash, purely because Adobe have never actually had a concerted effort to destroy Linux. Apples and oranges, though. Still there is a point to be made about the ARM netbooks coming soon: these are unlikely to support Windows at all, which means pretty much everything is up in the air at this point. 

You're right at Nokia's crappy lobbying the w3c. I suppose all anyone can do is wait for the patents on media formats to end. Mp3 is due to end in 2010, I think. In any event it's stuff like this or [this]("http://news.cnet.com/2100-1027_3-6161760.html") [cnet.com] that makes me wary of any software even remotely associated with patents. Remember the .gif/.png fiasco?

> Perhaps. But there are plenty of companies out there who aren't ready for a complete epiphany - and I'd rather there be "stop-gap" measures (see: Picasa for Linux using an embedded copy of Wine) rather than Linux being frozen out completely. And with any luck, it can lead to *eventual* adoption of "our" way of doing things - e.g. games for Windows are now starting to use embedded Mono rather than Microsoft.NET - so the barrier for them to release on Linux is reduced (only the graphics engine needs porting, their scripting engine is now already portable). The again, everything bar the graphics being written in Python didn't help us get a port of Civilization 4.

A slowly-slowly trickle is better than no movement at all, I agree. What I worry about is the threat of Linux people trying to do things "their" way more and more. Take Novell's gutless cave-in to Microsoft as an example. I think the community in general needs less of this behaviour.

---

### Post by directhex on 2009-05-05
> **monsterstack said:**
> Neither option is one I'd rather have, and I can't really make a choice between the two. If you put a gun to my head I'd have to go with Flash, purely because Adobe have never actually had a concerted effort to destroy Linux. Apples and oranges, though. Still there is a point to be made about the ARM netbooks coming soon: these are unlikely to support Windows at all, which means pretty much everything is up in the air at this point.

[img]http://www2.apebox.org/wordpress/wp-content/gallery/00-single/armless.png[/img]

Could be an interesting battle, really.

> You're right at Nokia's crappy lobbying the w3c. I suppose all anyone can do is wait for the patents on media formats to end. Mp3 is due to end in 2010, I think. In any event it's stuff like this or [this]("http://news.cnet.com/2100-1027_3-6161760.html") [cnet.com] that makes me wary of any software even remotely associated with patents. Remember the .gif/.png fiasco?

'course, you know WHY Nokia lobbied against Free formats, right?

> A slowly-slowly trickle is better than no movement at all, I agree. What I worry about is the threat of Linux people trying to do things "their" way more and more. Take Novell's gutless cave-in to Microsoft as an example. I think the community in general needs less of this behaviour.

I don't particularly like Novell's deal over patents, as it confuses and muddies the water over previously non-Novell products - like, say, Mono. But I think Moonlight is the right way to do things, actually - rather than Microsoft try to port their (traditionally crap) software to a platform they don't understand, a third party who knows the lie of the land does it for them. And recognizing the way the market is going, MS have helped rather than hindered that effort.

And I think Mono has already helped a few firms certainly evaluate moving to Linux, since they can look at hosting their internal ASP.NET and WinForms crap on Linux rather than Windows. Mono's MoMA tool is especially helpful since it even gives these companies a list of specific sections of their code which are non-portable (i.e. a TODO list). It's certainly much cheaper for them to move to Mono as their trickle than to start from scratch with Ruby or somesuch - and companies are going to go for the low-cost option any time. Whether moving to Mono is cheaper than sticking with MS.NET is the big question.

---

### Post by gtr32 on 2009-05-05
> **directhex said:**
> If they WANT to focus on the Linux market, then the availability of things like Moonlight means they have the option of continuing to use the tools they're using, but simply need to do some QA to test it - or limit their use of APIs that aren't yet available.

Not to mention all the C# (or VB) applications written for .NET that could be used with Mono.

---

### Post by monsterstack on 2009-05-05
> 'course, you know WHY Nokia lobbied against Free formats, right?

Well there is this, their [official complaint to w3c]("http://www.w3.org/html/wg/tracker/issues/24") [w3.org]:
```

Date: Fri, 30 Nov 2007 16:05:30 +0200
From: mikko.honkala@nokia.com
To: connolly@w3.org, public-html@w3.org
Subject: RE: Request for clarification on HTML 5 publication status  (ISSUE-19)

we see benefit to publish a first WD of the HTML5 spec. To avoid any
patent issues we request deletion of the following clause from the spec
before it is published. We support publication under the condition this
change is made.

> "User agents should support Ogg Theora video and Ogg Vorbis audio, as
> well as the Ogg container format." in 3.14.7.1.

```

Of course in the patent minefield that is video-codecs, it seems a daft reason to jump on, considering Ogg's lack of patent issues. I have to admit some ignorance on this issue though: I am not so very knowledgeable on the whys and wherefores Nokia were truly against it, only that it annoyed me when I heard about it. I'll go out on a limb and take a guess that Nokia would stand to lose out valuable cross-licensing deals on their patent portfolio. Again I must state this is all opinionated guess-mongering™, however. If you can correct me on this matter I would be cool with that too.

> rather than Microsoft try to port their (traditionally crap) software to a platform they don't understand, a third party who knows the lie of the land does it for them. And recognizing the way the market is going, MS have helped rather than hindered that effort.

I agree that the people to port such functionality should be the ones who know it best. But even so, the mono devs are essentially getting short-shift. The community at large could give back to the whole Silverlight project if it was free from start to finish; furthermore Microsoft would benefit from real interoperability for a change. It would be ten times easier to port it to any system users required. It's as if they're trying to be open, but doing it wrong. In my opinion it's easy to see why: having full Silverlight-esque functionality across all the OSes would mean Microsoft would lose control, and it would mean users and OEMs would have more options for their choice of OS. In other words, it's just another form of vendor lock-in. I have utmost respect for the guys trying to get all this stuff to work in Linux for our benefit, it just seems to me that they *are* being hindered simply because the stuff isn't free, and subsequently they will never have an opportunity to evolve it in new and interesting ways.

On people's personal computers, fine, run any code you wish. I have all sorts of proprietary stuff running to get my graphics working and what have you. I just don't think the internet should be part of that culture of closing things off. An internet with proper html and css and javascript standards across the board, with a variety of universally-supported free formats for all kinds of media is what we should be going for. Everything else, Flash and Silverlight included, are just sideshows to the real thing.

I know I'm talking dreamland fantasy stuff now. Everyone would prefer this state of affairs, but such as it is.

---

### Post by directhex on 2009-05-05
> **monsterstack said:**
> Well there is this, their [official complaint to w3c]("http://www.w3.org/html/wg/tracker/issues/24") [w3.org]:
```

Date: Fri, 30 Nov 2007 16:05:30 +0200
From: mikko.honkala@nokia.com
To: connolly@w3.org, public-html@w3.org
Subject: RE: Request for clarification on HTML 5 publication status  (ISSUE-19)

we see benefit to publish a first WD of the HTML5 spec. To avoid any
patent issues we request deletion of the following clause from the spec
before it is published. We support publication under the condition this
change is made.

> "User agents should support Ogg Theora video and Ogg Vorbis audio, as
> well as the Ogg container format." in 3.14.7.1.

```

Of course in the patent minefield that is video-codecs, it seems a daft reason to jump on, considering Ogg's lack of patent issues. I have to admit some ignorance on this issue though: I am not so very knowledgeable on the whys and wherefores Nokia were truly against it, only that it annoyed me when I heard about it. I'll go out on a limb and take a guess that Nokia would stand to lose out valuable cross-licensing deals on their patent portfolio. Again I must state this is all opinionated guess-mongering™, however. If you can correct me on this matter I would be cool with that too.

[http://wiki.xiph.org/index.php/TheoraHardware#Decoder](http://wiki.xiph.org/index.php/TheoraHardware#Decoder)

What DON'T you notice in that list which would concern a company who ship a lot of internet-enabled kit with DSP-based audio/video decoding?

---

### Post by monsterstack on 2009-05-05
Ah, I see. Or rather I don't see anyone at all. Thanks for the info.

---

### Post by neighborlee on 2009-05-12
> **ronacc said:**
> perhaps their journalism isn't up to your standards but their sentiment is alright by me , I was a dedicated SuSe user until they made a deal with the devil .

DOnt you know thats what the pro mono people do, is knock down any possible , reasoned debate about such issues?

Did anyone note how nice and fair the original gentlemans questions was, yet right of the bat he was attacked ?

I dont think much else needs said, that if you cant debate something without throwing out ad-hominem bombastic attacks then you aren't here to have a reasonable debate, and what that leaves should tell everyone something about the current climate surrounding this issue.

We all know there are 'alternatives' to every single mono app, that come with 'zero' risk, so honestly there is zero reason to use mono, or any of its apps unless you just like taking risks; as if M$ ever does anything else but do its best to push profits while completely losing site of the boundries between good sound moral policies, which is what happens when your basis for existing is profit based ( can you say vista and smile at the sametime? ).

cheers
nl

---

### Post by neighborlee on 2009-05-12
> **ronacc said:**
> perhaps their journalism isn't up to your standards but their sentiment is alright by me , i was a dedicated suse user until they made a deal with the devil .

+1

---

### Post by neighborlee on 2009-05-12
> **nathangrubb said:**
> Why do people have to hate on Mono so much? It's fine, and the applications written in it (At least the ones I've used) are very high quality. 

BUT OHNOES IT'S REMOTELY RELATED TO MICRO$$$$$$$$$$$OFT WE'RE ALL GOING TO DIE!!11111

That is ridiculous ad hominem attack, and not worthy of the way this thread was started, and you should be ashamed.

cheers
lee

---

### Post by neighborlee on 2009-05-12
> **directhex said:**
> Nope, it's not. BoycottNovell is fiction, not fact.

Care to state facts , to present that the entire site is fiction, therefore stating as a result that the site has no redeeming value ?

That should take you QuiTE a while..get busy ;)

Then feel free to debate the issue if you dare, one on one with theowner of that site, in freenode.net at #boycottnovell...

Fair is fair..and it will be made public for all to see, as is all conversation in that channel.

cheers
lee

---

### Post by neighborlee on 2009-05-12
> **directhex said:**
> Like ffmpeg, for example? The way the Moonlight packages in every distro use ffmpeg?

Funny thing is, codecs (like MP3, needed by Silverlight amongst others) ARE patented - you can either violate the patents with ffmpeg, or use a patent-licensed decoder in the Microsoft Media Pack. Which is the lesser evil?

Lets be clear on something here..there is NO moonlight in fedora so to make a statement like this , is hardly accurate given:

[http://fedoraproject.org/wiki/ForbiddenItems#Moonlight](http://fedoraproject.org/wiki/ForbiddenItems#Moonlight)

Lesser evil , you must be kidding..show me someone who trusts M$ unswervingly, and I'll show you..well never mind , given the mess vista was and how people were ripped off considering how horrible it runs should speak volumnes as to the morality of M$ ( yes infering profit over usefulness; to this day I would love a refund of my hastles, but we know that wont' happen dont we ).

GIven the risk behind moonlight, who in their right mind doesn't have questions about mono ,  especially given M$'s  track record.

cheers
nl

---

### Post by directhex on 2009-05-13
> **directhex said:**
> This thread will end dipped in chocolate and pure liquid ***awesome***

It's like I'm clairvoyant or something.

---

### Post by SKLP on 2009-05-13
> **directhex said:**
> It's like I'm clairvoyant or something.

Indeed, lol

---

### Post by gnomeuser on 2009-05-13
> **neighborlee said:**
> Lets be clear on something here..there is NO moonlight in fedora so to make a statement like this , is hardly accurate given:

[http://fedoraproject.org/wiki/ForbiddenItems#Moonlight](http://fedoraproject.org/wiki/ForbiddenItems#Moonlight)

Lesser evil , you must be kidding..show me someone who trusts M$ unswervingly, and I'll show you..well never mind , given the mess vista was and how people were ripped off considering how horrible it runs should speak volumnes as to the morality of M$ ( yes infering profit over usefulness; to this day I would love a refund of my hastles, but we know that wont' happen dont we ).

GIven the risk behind moonlight, who in their right mind doesn't have questions about mono ,  especially given M$'s  track record.

cheers
nl

Red Hat Legals liason with the Fedora community refuses to listen to reason. I have several times presented the Open Specification Promise for the XAML vocabulary granting use a free patent grant for implementing a system that talks XAML. He refuses to even take this to the Legal department. When I ask what patents they think are infringed upon I am told to ask Microsoft. I also already had to ask Mr. Calloway to change the text in the Forbidden Items entry for Moonlight once since he had taken to insulting Novell, a rather unprofessional approach and a clear show a personal bias (old revisions "magically" disappeared when we changed wikis though so digging it up might be hard).

This is not evidence based, this is dogma.

Now we can't include it for one very good reason, if we do it will depend on ffmpeg (which cannot ship in Fedora because it is not possible to break out the codecs which are patented), the only other option is relying on the proprietary codec pack as provided by Microsoft and that is, rightfully, felt to be against the spirit of Fedora. Also the latter solution very likely makes supporting the package rather hard.

Should Moonlight, as it has been talked about a few times, be ported to GStreamer the world would certainly look different. I don't know how this sits with the Silverlight 3 support for custom managed code only codecs (for which Vorbis and Dirac support is already present today).

So dogma and codecs, not Microsoft patents prevents Moonlight in Fedora. Even then will soon be able to get Moonlight via rpmfusion for your Fedora box, compiled against ffmpeg (and using patches provided by our very own directhex).

---

### Post by gnomeuser on 2009-05-13
> **neighborlee said:**
> That is ridiculous ad hominem attack, and not worthy of the way this thread was started, and you should be ashamed.

cheers
lee

That is NOT an ad hominem, an ad hominem would be attacking the person rather than the argument.

The general structure is "You're <something bad>, therefore <your claim> is false." 

Note: I wasn't allowed the demonstration I posted even if it was purely to show off the structure for people to avoid commiting it. No camels where harmed I promise, and no offence was intended, merely education.

(solely a demonstration of the logical fallacy in question)

---

### Post by neighborlee on 2009-05-13
> **gnomeuser said:**
> That is NOT an ad hominem, an ad hominem would be attacking the person rather than the argument e.g. You are wrong because you are the biproduct of regular camel raping. 

(solely a demonstration of the logical fallacy in question)

consists of replying to an argument or factual claim by attacking or appealing to a characteristic or belief of the source making the argument or claim, rather than by addressing the substance of the argument or producing evidence against the claim. < from:

[http://en.wikipedia.org/wiki/Ad_hominem](http://en.wikipedia.org/wiki/Ad_hominem)

oops,sorry you missed that.

Good camel anology though, I guess that explains this tude, doesn't it:

<snip>

Good try,,and sorry for the words here,,they are HERS not mine, but it def.helps to illustrate my point, and there was no way to avoid the reference as that is how the url is formed.

If I could  have hid it, trust me I would have.

cheers
nl
P.S>-= I am SO GROSSED out having had to post that url, but it was necessary to make a point,and probably just as well, it got filtered out, though if I choose I can just reference it elsewhere.

---

### Post by gnomeuser on 2009-05-13
> **neighborlee said:**
> consists of replying to an argument or factual claim by attacking or appealing to a characteristic or belief of the source making the argument or claim, rather than by addressing the substance of the argument or producing evidence against the claim. < from:

[http://en.wikipedia.org/wiki/Ad_hominem](http://en.wikipedia.org/wiki/Ad_hominem)

oops,sorry you missed that.


You will note that the OP did not reply to any claims, merely stated that these debates always devolve into "It's Microsoft, meaning it's bad". Ad hominems by their very definition require ignoring the argument and going after the person.

Now for some (quite a lot in my experience as a Mono SIG member in Fedora) people in these debates that is an accurate preception, for others I would grant it might be oversimplifying the argument. 

> 
Good camel anology though, I guess that explains this tude, doesn't it:

<snip>

Good try,,and sorry for the words here,,they are HERS not mine, but it def.helps to illustrate my point, and there was no way to avoid the reference as that is how the url is formed.

If I could  have hid it, trust me I would have.

cheers
nl
P.S>-= I am SO GROSSED out having had to post that url, but it was necessary to make a point,and probably just as well, it got filtered out, though if I choose I can just reference it elsewhere.

Now that is funny, you are so disgusted by 7 innocent little words that you couldn't even manage to read the posting and put some context into things. Instead you elect to frame me by a blog title. Also you may want to learn about your friend tinyurl if you are so easily offended at urls that you can't post them.

You are directly attacking my person instead of my claim, now that is an ad hominem. Congratulations I guess?

Oh and I am a male, I even have my real picture up there in my avatar (and as my blog image, plus the blog is directly registered in my full real name - David Nielsen, right there as part of the URL even). The tiniest bit of research would have revealed that, I have never intentionally hidden who I am or how to contact me.

---

### Post by monsterstack on 2009-05-13
This is probably old news to most people following this thread, but I haven't been interested in the mono debate for long. I thought maybe some of you might like to see this.

I have been getting lots of "Linux is doomed" type messages lately, what with Windows 7 coming out soon and what have you. I remember seeing USENET posts along similar lines for pretty much every Microsoft release. So I decided to have a search through so I could just quote a troll of long ago in response. Along the way I found this interesting tidbit re the great mono debate. This one about Microsoft's .NET coming to Linux from [2000]("http://groups.google.com/group/comp.os.linux/browse_thread/thread/3e0127e29a88293d/f30f9f758c33d418") [comp.os.linux] [google-groups]!

.NET's scope was different back then, of course, and people reckoned it would be Corel that would port the framework to Linux instead of Novell. Even so, in that thread you pretty much get everything people have been arguing about. The GPL stuff, the embrace/extend/extinguish stuff, arguments about how useful the language will be from a technical standpoint, blah blah blah, the whole shebang.

Seems nothing changes much. :)

---

### Post by gnomeuser on 2009-05-14
> **monsterstack said:**
> This is probably old news to most people following this thread, but I haven't been interested in the mono debate for long. I thought maybe some of you might like to see this.

I have been getting lots of "Linux is doomed" type messages lately, what with Windows 7 coming out soon and what have you. I remember seeing USENET posts along similar lines for pretty much every Microsoft release. So I decided to have a search through so I could just quote a troll of long ago in response. Along the way I found this interesting tidbit re the great mono debate. This one about Microsoft's .NET coming to Linux from [2000]("http://groups.google.com/group/comp.os.linux/browse_thread/thread/3e0127e29a88293d/f30f9f758c33d418") [comp.os.linux] [google-groups]!

.NET's scope was different back then, of course, and people reckoned it would be Corel that would port the framework to Linux instead of Novell. Even so, in that thread you pretty much get everything people have been arguing about. The GPL stuff, the embrace/extend/extinguish stuff, arguments about how useful the language will be from a technical standpoint, blah blah blah, the whole shebang.

Seems nothing changes much. :)

Just as an aside, it wasn't Novell who ported .NET. Firstly porting implies that they looked at the original code (which would definitely be legally problematic), reimplemented from the ECMA standard and design papers is probably more correct. Novell didn't start the Mono project, it was a company started by Nat Friedman and Miguel de Icaza called Ximian (also known as Intl. GNOME Support and Helix Code previously). 

When Novell decided to get into Linux, Ximian was the first company they bought. There was talk of them buying Red Hat as well but they ended up buying SUSE. Thus we have Novell involved heavily in Linux amongst other things developing Mono.

A little history lesson.

---

### Post by neighborlee on 2009-05-18
> **monsterstack said:**
> This is probably old news to most people following this thread, but I haven't been interested in the mono debate for long. I thought maybe some of you might like to see this.

I have been getting lots of "Linux is doomed" type messages lately, what with Windows 7 coming out soon and what have you. I remember seeing USENET posts along similar lines for pretty much every Microsoft release. So I decided to have a search through so I could just quote a troll of long ago in response. Along the way I found this interesting tidbit re the great mono debate. This one about Microsoft's .NET coming to Linux from [2000]("http://groups.google.com/group/comp.os.linux/browse_thread/thread/3e0127e29a88293d/f30f9f758c33d418") [comp.os.linux] [google-groups]!

.NET's scope was different back then, of course, and people reckoned it would be Corel that would port the framework to Linux instead of Novell. Even so, in that thread you pretty much get everything people have been arguing about. The GPL stuff, the embrace/extend/extinguish stuff, arguments about how useful the language will be from a technical standpoint, blah blah blah, the whole shebang.

Seems nothing changes much. :)

[http://www.itwire.com/content/view/23501/1090/](http://www.itwire.com/content/view/23501/1090/) < 

,,,and then there is that ..thx for your post that was revealing considering the time period..and now...and to think ubuntu is JUST OK with shipping as part of the default OS, while fedora avoids it at least ( whatever the reason, its gone ) in the livecd, I cant verify dvd atm ), and BLAG avoids it entirely in their one livecd, GO THEM!.

Someone in the community gets the patent problem at least , and is willing to stick up for free, open source software when it matters the most.

It would be lovely, for all concerned for many reasons, if we could trust M$, but they reveal time and time again, they can't be , and this latest URL showcases that very completely . IF you trust them fine your choice, but average people deserve the truth that protects them from choices that otherwise will cause them harm; that is what people that care about others, do.

At least they weren't successful with blocking ODT ( windows 7 , its there in wordpad , and its because their format LOST ), and with steady resistance ( its not  FUTILE people ! ;) .. ) mono will be gone soon too. It already is from BLAG, and I urge you, if FOSS means anything to you, to consider using that or at least consider its values, as then and then only will FOSS remain true to its principles, and thereby reamin,- free and open.

cheers
nl

---

### Post by directhex on 2009-05-18
> **neighborlee said:**
> [http://www.itwire.com/content/view/23501/1090/](http://www.itwire.com/content/view/23501/1090/) < 

,,,and then there is that ..thx for your post that was revealing considering the time period..and now...and to think ubuntu is JUST OK with shipping as part of the default OS, while fedora avoids it at least ( whatever the reason, its gone ) in the livecd, I cant verify dvd atm ), and BLAG avoids it entirely in their one livecd, GO THEM!.

Someone in the community gets the patent problem at least , and is willing to stick up for free, open source software when it matters the most.

It would be lovely, for all concerned for many reasons, if we could trust M$, but they reveal time and time again, they can't be , and this latest URL showcases that very completely . IF you trust them fine your choice, but average people deserve the truth that protects them from choices that otherwise will cause them harm; that is what people that care about others, do.

At least they weren't successful with blocking ODT ( windows 7 , its there in wordpad , and its because their format LOST ), and with steady resistance ( its not  FUTILE people ! ;) .. ) mono will be gone soon too. It already is from BLAG, and I urge you, if FOSS means anything to you, to consider using that or at least consider its values, as then and then only will FOSS remain true to its principles, and thereby reamin,- free and open.

cheers
nl

Is it worth pointing out the demagogy and inaccuracy in your link, or is it wasted effort considering who I'm replying to? Should I waste my time on it?

---

### Post by gnomeuser on 2009-05-18
> **neighborlee said:**
> [http://www.itwire.com/content/view/23501/1090/](http://www.itwire.com/content/view/23501/1090/) < 

,,,and then there is that ..thx for your post that was revealing considering the time period..and now...and to think ubuntu is JUST OK with shipping as part of the default OS, while fedora avoids it at least ( whatever the reason, its gone ) in the livecd, I cant verify dvd atm ), and BLAG avoids it entirely in their one livecd, GO THEM!.


space concerns, if Mono was legally problematic like a fringe in Fedora says it would be removed. Yet despite being encouraged by me, the former Fedora Mono SIG leader, to put that to the test and propose it as a feature to remove Mono from Fedora, they never have. Mono is part of Fedora and as such it lives up to the strict freedom requirements presented by Fedora. 

Cease using Monos absence from the Fedora livecd as an argument for Mono's supposed illegality.

---

### Post by directhex on 2009-05-18
> **gnomeuser said:**
> Cease using Monos absence from the Fedora livecd as an argument for Mono's supposed illegality.

You assume honest debate?

---

### Post by gnomeuser on 2009-05-18
> **directhex said:**
> You assume honest debate?

I have not grown to expect that from the BN crowd but I hope never the less, the best I can do is to be honest and present verfiable fact.

---

### Post by monsterstack on 2009-05-18
> **gnomeuser said:**
> Just as an aside, it wasn't Novell who ported .NET. Firstly porting implies that they looked at the original code (which would definitely be legally problematic), reimplemented from the ECMA standard and design papers is probably more correct. Novell didn't start the Mono project, it was a company started by Nat Friedman and Miguel de Icaza called Ximian (also known as Intl. GNOME Support and Helix Code previously). 

When Novell decided to get into Linux, Ximian was the first company they bought. There was talk of them buying Red Hat as well but they ended up buying SUSE. Thus we have Novell involved heavily in Linux amongst other things developing Mono.

A little history lesson.

Ah, thanks. :)

---

### Post by GOfree on 2009-05-18
Hi. Thanks everybody. If this is a long-standing debate, it is still new to me. I appreciate the good arguments and balanced discussion.

When I (recently) heard about mono, I was at first excited. I would possibly be able to run MTGO from WINE. Woo-hoo!

Now, I am not so sure... I am admittedly rather paranoid about Microsoft and its (apparent) attempts at world domination. :-|

If the Linux community can do this without becoming dependent on or beholden to Microsoft (or Novell, for that matter) than great. Just to be safe, I hope we are developing other alternatives now anyway.

Otherwise, I would gladly give up my online gaming if it means maintaining this small degree of independence from corporate control that I know as "linux".

---

### Post by neighborlee on 2009-05-18
> **directhex said:**
> You assume honest debate?

It's pathetic you resort  to personal attacks, when none are warranted, and certainly none needed nor desireable,- but that is what you get it appears from those whom fear an outcome other than what they expect and thus recoil in resistance with anger and venom.

We show you why we feel the way we do, and all you have in return is more comments from people 'like that-'..and to think you look for respect in your views, but give zero in return.

You have succeeded in showcasing your true agenda though you sat out to do just the opposite,- by 'trying' to make us look bad you had hoped to make yourselves look like the 'high'er authority in this debate, and in reality took the 'low' road. Talk about religion, I think a well respected member of religious circles warns us about high and low roads ?

Linux will succeed in spite of your attempts { and the FOSS it stands for unlike the patent minefield mono is as this and many other [remember PJ -groklaw-? ]) have pointed out, and when it does it will know who its champions of justice were and who attempted to tear it down.

You might think few know about this, but there are others who will continue to fight against oppression as well, and reference  high quality url's that legitmately showcase why the worry isn't fantasy:

[http://nocturn.vsbnet.be/node/146](http://nocturn.vsbnet.be/node/146)

[http://www.groklaw.net/article.php?story=20080528133529454](http://www.groklaw.net/article.php?story=20080528133529454)

You can disagree, its a free country and no one should be trying to thrwart anyones right to  offer their views, but the debate is out there, wont go away just because you want it to, and other people continue to see these techs for what they are.

cheers
nl

---

### Post by directhex on 2009-05-18
> **neighborlee said:**
> It's pathetic you resort  to personal attacks, when none are warranted, and certainly none needed nor desireable,- but that is what you get it appears from those whom fear an outcome other than what they expect and thus recoil in resistance with anger and venom.

We show you why we feel the way we do, and all you have in return is more comments from people 'like that-'..and to think you look for respect in your views, but give zero in return.

You have succeeded in showcasing your true agenda though you sat out to do just the opposite,- by 'trying' to make us look bad you had hoped to make yourselves look like the 'high'er authority in this debate, and in reality took the 'low' road. Talk about religion, I think a well respected member of religious circles warns us about high and low roads ?

Linux will succeed in spite of your attempts { and the FOSS it stands for unlike the patent minefield mono is as this and many other [remember PJ -groklaw-? ]) have pointed out, and when it does it will know who its champions of justice were and who attempted to tear it down.

You might think few know about this, but there are others who will continue to fight against oppression as well, and reference  high quality url's that legitmately showcase why the worry isn't fantasy:

[http://nocturn.vsbnet.be/node/146](http://nocturn.vsbnet.be/node/146)

[http://www.groklaw.net/article.php?story=20080528133529454](http://www.groklaw.net/article.php?story=20080528133529454)

You can disagree, its a free country and no one should be trying to thrwart anyones right to  offer their views, but the debate is out there, wont go away just because you want it to, and other people continue to see these techs for what they are.

cheers
nl

Why do you keep linking to things about Moonlight in a post about Mono? Do you understand the difference between them? If not, then ask. If yes, then you're attempting to deceive by sending people off to look at unrelated topics.

---

### Post by neighborlee on 2009-05-18
> **directhex said:**
> Why do you keep linking to things about Moonlight in a post about Mono? Do you understand the difference between them? If not, then ask. If yes, then you're attempting to deceive by sending people off to look at unrelated topics.

Why bother debating this , your wasting my time by not reading url's.

cheers
nl

---

### Post by directhex on 2009-05-18
> **neighborlee said:**
> Why bother debating this , your wasting my time by not reading url's.

cheers
nl

Oh, I'M wasting YOUR time? Let's see, your "completely on topic" URLS would be entitled "Shining Some Light on Microsoft's Moonlight Covenant" and "If mono brings doubt, moonlight sheds light"

So I'm wrong when I say your URLs are about Moonlight, changing the subject of the original post (Mono)? Really?

---

### Post by dmizer on 2009-05-18
Sorry folks, I think this debate's gone a bit too far.

---

### Post by monsterstack on 2009-05-28
We can all agree that there are ridiculous, insane flame wars about mono all over the internet. As such, flame wars are often the result of many threads even here in sunny old UbuntuForums. There is a lot of confusion pretty much everywhere you look. Personally, I think it can be alarming for people coming across the controversy for the first time. I've read quite a lot about mono; and for the *most part* I am ambivalent (but I have my doubts about Moonlight, so I'm probably not the best person to go ahead and start this). Still, it pains me to see people posting insane things about mono whether they support it or reject it.

So here's my idea. There are users here who actively develop with mono, and users who actively develop in other, rival languages, and probably some who do both. I'd say these guys are going to be pretty knowledgeable about the ins and outs of the technical details. I've also seen people post pertinent stuff about the licensing, the patents, the ECMA standard, and all of the other stuff people disagree about. What I find is that these posts are separated by a vast gulf of misinformation and vitriol, and it really doesn't help. I think we need an FAQ thread about the controversy, and have it stickied in *Recurring Discussions*. The OP should be modified over time to incorporate whatever happens in the thread. It should identify every single controversy people can think of, and include evidence both for and against (if it exists).

It should give no judgement at all, only conclusive proof of the facts. It should be presented in an unbiased way as possible. I know that's going to be difficult, but I don't see why it can't be done. Relevant links or even a brief description of mono, what it is, and what it does, might also be a good idea. Anyhow, I think the discussion on the controversy could go something like,

> **What's the fuss about $problem_x?**
Some people are concerned about $x and $y having an effect on $z and $g.

**Is it really a problem?**
Some people think it is a problem because of reasons $a, $b and $c. However, others reject that it is a problem because of reasons $d, $e and $f.

A good idea anybody? Would anybody be interested in giving it a go? Please don't turn this thread into a flame war about mono. Whatever your opinions are about mono, the controversy exists, and it's depressing to see it go on and on. I don't think people will ever stop arguing about it, but maybe we can stem the tide of flame wars and threads going off-topic on UbuntuForums.

---

### Post by suitedaces on 2009-05-28
I'd like an objective one too that puts both arguments in layman's terms.

---

### Post by monsterstack on 2009-05-28
> **suitedaces said:**
> I'd like an objective one too that puts both arguments in layman's terms.

Absolutely. It shouldn't just be a morass of gobbledygook. I want people who've just clicked on a link to an article about "MONO WILL DESTROY LINUX!" to think, "What the hell? what is this mono!? Should I be worried? ah, I wonder if anybody on UF knows about it." And then promptly go and discover the FAQ that tells him everything he needs to know without hyperbole, rhetoric or confusion.

---

### Post by Dragonbite on 2009-05-29
I would think a Wiki would work better because a Mono thread is just as prone to flaming from both sides of the fence while a Wiki tracks WHO changes WHAT and that little bit of accountability may keep less-learned people from making changes.

The downside, though, is the Wiki doesn't get the same attendance and in its current state, is so large it's difficult to manage.

Although, having a Wiki page that describes it, and then being able to point people to it when arguments start may be a good mixture of both worlds.

EDIT: I didn't notice the poll choices.  Ooops! ;)

---

### Post by XubuRoxMySox on 2009-05-29
I never had mono, but I heard it can be spread by kissing. One kid at school got it and in a couple of months a whole bunch of kids were out sick with it.

(I know, totally off topic... I just can't resist a pun).

-Robin

---

### Post by Dragonbite on 2009-05-29
> **dixiedancer said:**
> I never had mono, but I heard it can be spread by kissing. One kid at school got it and in a couple of months a whole bunch of kids were out sick with it.

(I know, totally off topic... I just can't resist a pun).

-Robin

I started dating a girl while I was home from College over Christmas break.  Shortly after returning  to school I started feeling sick.  Eventually I stopped by the school nurse's office.

A couple days later I saw her in the cafeteria, she said the results were back and that I was "getting over mono".

What a way to start off a relationship (didn't scare me off, though, because now she'll be my wife of 13 years this July!)

---

### Post by Giant Speck on 2009-05-29
Because all threads on UF -- whether the topic be mono, Microsoft, Tux's gender, or puppies -- are bound to decend into chaotic madness.

---

### Post by fatality_uk on 2009-05-29
> **Giant Speck said:**
> Because all threads on UF -- whether the topic be mono, Microsoft, Tux's gender, or puppies -- are bound to decend into chaotic madness.

Nonsense. A free, open and adult debate never hurt anyone and there are plenty of these on UF

---

### Post by bashveank on 2009-05-30
A wiki would be miles better than a comprehensive thread. Large consolidated threads have too much information. People just end up feeling intimidated and skipping over them.

---

### Post by UbuKunubi on 2009-06-01
I dont want mono on my system. How do i remove it?

---

### Post by monsterstack on 2009-06-01
> **UbuKunubi said:**
> I dont want mono on my system. How do i remove it?
```

sudo apt-get remove --purge mono-common libmono0
```

---

### Post by UbuKunubi on 2009-06-09
Thanks for your reply.
All the best,
Ubu

---

### Post by anechoic on 2009-06-09
[http://boycottnovell.com/2009/06/06/opposition-to-mono-by-default/](http://boycottnovell.com/2009/06/06/opposition-to-mono-by-default/)

---

### Post by TheIdiotThatIsMe on 2009-06-09
I've read the report. I think the Mono issue really is overblown, although I know there are others who have a very strong passion on one side or the other. Unfortunately, it's been brought up many many times, and nothing has really come of it. There are good arguments for both ways. I can see if gNewSense would like to take Mono out, but I think for now Ubuntu's stance has been pretty clear on keeping a balance between practicality and ideals.

---

### Post by alternatealias on 2009-06-09
> **anechoic said:**
> [http://boycottnovell.com/2009/06/06/opposition-to-mono-by-default/](http://boycottnovell.com/2009/06/06/opposition-to-mono-by-default/)

If you actually read Roy's "evidence", you'll notice that it's a gross exaggeration of what really happened (in other words, it's a lie). His friend Neighborlee was caught trolling this forum and given a warning. Neighborlee then blew that warning way out of proportion and ran crying to Roy who in turn quickly began a smear campaign against Ubuntu and Canonical with 4+ "news stories" all insinuating that Canonical/Ubuntu are censoring opinions of people who are against the inclusion of Mono.

If Roy is so willing to twist the "facts" and then spread this misinformation to as many Linux news sites as he could (LinuxToday, FSDaily, Digg, Reddit, etc), how twisted do you think his "facts" are against Mono and Novell? Think about that.




1. [http://boycottnovell.com/2009/06/01/banning-opposition-to-mono/](http://boycottnovell.com/2009/06/01/banning-opposition-to-mono/)

2. [http://boycottnovell.com/2009/06/06/opposition-to-mono-by-default/](http://boycottnovell.com/2009/06/06/opposition-to-mono-by-default/)

3. [http://boycottnovell.com/2009/06/08/microsoft-mono-embrace-extend-extinguish/](http://boycottnovell.com/2009/06/08/microsoft-mono-embrace-extend-extinguish/)

"Mono fans are meanwhile censoring opposers of Mono over in Ubuntu."


4. [http://boycottnovell.com/2009/06/09/mono-critique-for-ubuntu/](http://boycottnovell.com/2009/06/09/mono-critique-for-ubuntu/)

---

### Post by directhex on 2009-06-09
> **TheIdiotThatIsMe said:**
> I've read the report. I think the Mono issue really is overblown, although I know there are others who have a very strong passion on one side or the other. Unfortunately, it's been brought up many many times, and nothing has really come of it. There are good arguments for both ways. I can see if gNewSense would like to take Mono out, but I think for now Ubuntu's stance has been pretty clear on keeping a balance between practicality and ideals.

gNewSense includes Mono by default (except on MIPS)

---

### Post by Dragonbite on 2009-06-09
Heck, if you don't want Mono, it looks like Fedora 12 is going to try and be Mono-free and use alternatives such as gNote instead of Tomboy.

Just hope they can come up with or develop an equivalent to F-Spot for Gnome, otherwise Picasa and gThumbs should be getting a boost in popularity.

---

### Post by Tibuda on 2009-06-09
> **directhex said:**
> gNewSense includes Mono by default (except on MIPS)

That makes sense, because Mono is open source, and free as in freedom, no matter what people say.

---

### Post by dragos240 on 2009-06-09
ubuntu-desktop is a meta package, it's okay to remove it, it will not do any harm, I have mine removed. Just sudo apt-get remove mono.

---

### Post by z0mbie on 2009-06-09
Mono is very troublesome, it's already created a split in the community. Why is there a desparate need to have Mono anyway? It seems like most people think it's equivalent to the Linux kernel. I say leave Ubuntu vanilla install Mono free, and let the user install whatever they like. This will prevent further controversy and make the default install very light weight also.

---

### Post by dragos240 on 2009-06-09
> **z0mbie said:**
> Mono is very troublesome, it's already created a split in the community. Why is there a desparate need to have Mono anyway? It seems like most people think it's equivalent to the Linux kernel. I say leave Ubuntu vanilla install Mono free, and let the user install whatever they like. This will prevent further controversy and make the default install very light weight also.

If you want exactly what you want and nothing else, get arch :)

---

### Post by z0mbie on 2009-06-09
> **dragos240 said:**
> If you want exactly what you want and nothing else, get arch :)

That would mean I would have to abandon my favorite distribution. :/

---

### Post by Dragonbite on 2009-06-09
I think I would prefer if Mono was not installed by default, and popular mono-based applications has non-mono equivalents as alternatives. For example, gThumbs is an image viewer while F-Spot is an image manager. The other applications that may be comparable are digiKam and Picasa. Since Picasa is not FOSS and relies on WINE to run in Linux I do not want to see that application be propped up as the replacement.

I would also want Mono to be very easy to install if one so chooses. I use .NET at work and if I want to bring that capability home, where all I have is Linux, then I would like to be able to use Mono.

Ubuntu has done a good job about bringing up Flash installation when appropriate, and making it easy to choose to or not to.  If Mono is just as easy then that would be great.

At least with Fedora and openSUSE you can select what you want if you download the entire DVD (or do a NetInstall). I just don't have luck with DVDs.

---

### Post by alternatealias on 2009-06-09
> **z0mbie said:**
> Mono is very troublesome, it's already created a split in the community. Why is there a desparate need to have Mono anyway? It seems like most people think it's equivalent to the Linux kernel. I say leave Ubuntu vanilla install Mono free, and let the user install whatever they like. This will prevent further controversy and make the default install very light weight also.

If the community is split, it's only because trolls like Roy Schestowitz are driving a wedge into it for their own personal fame and power. If he was in it for the right reasons, then he wouldn't be trying to smear Mono everywhere he can on the internet or bashing it every day for several years in a row. Instead, he'd respectfully try to reach an agreement with the parties involved.

If people were more respectful of other people's choices to use what they wanted to use, then there would be no controversy.

I don't think the Mono developers care if you prefer to use alternative applications or not. They have respect for others' choices. The anti-Mono crowd, however, are intolerant of Mono and are the ones that show no respect for anyone else when they viciously attack Mono, the developers, and people on the Ubuntu mailing-lists (for example).

---

### Post by zekopeko on 2009-06-10
> **Dragonbite said:**
> <snip>.

Ubuntu has done a good job about bringing up Flash installation when appropriate, and making it easy to choose to or not to.  If Mono is just as easy then that would be great.

<snip>.

you are comparing **free** software to a **closed** source browser plugin?

---

### Post by alternatealias on 2009-06-10
> **zekopeko said:**
> you are comparing **free** software to a **closed** source browser plugin?

The holy war against Mono has forsaken logic in favor of blind hatred.

---

### Post by Dragonbite on 2009-06-10
> **zekopeko said:**
> you are comparing **free** software to a **closed** source browser plugin?

No, I am saying that my hope is they keep Mono being as easy to install as other applications (and as up-to-date as possible) and not get so "holier than thou" as ot put it into a seperate repository or make you jump hoops to install.

Probably a better Flash comparison isn't Mono, but Moonlight! The first time you go to a page running Silverlight, have the same thing happen as Flash in Firefox, asking if you want to install Moonlight.

---

### Post by directhex on 2009-06-10
> **Dragonbite said:**
> The first time you go to a page running Silverlight, have the same thing happen as Flash in Firefox, asking if you want to install Moonlight.

[click here](http://retro.apebox.org/test.html)

Does that work as expected?

Slightly off-topic, but...

---

### Post by Dragonbite on 2009-06-10
> **directhex said:**
> [click here](http://retro.apebox.org/test.html)

Does that work as expected?

Slightly off-topic, but...

Not in Windows ;) (I'm at work on XP)

---

### Post by directhex on 2009-06-10
> **Dragonbite said:**
> Not in Windows ;) (I'm at work on XP)

That would be as-intended! It should only do anything on Firefox on Ubuntu

---

### Post by rhys_rhaven on 2009-06-10
***I just wanted to add my vote as it were, to please remove Mono from the "ubuntu desktop" and find replacements to fspot and tomboy. ***

Having the Mono and Moonlight projects is very nice. .NET is a great setup for many users, often Windows developers, and makes Ubuntu more palatable as a product. Keep it in the repositories.

And yet, Ubuntu is supposed to work **"as if people mattered."** Linux distributions try to pick the best technical solution, the one with the most freedom, the one that won't get you in legal troubles or lock you into a single vendor. And regardless that Mono is open source, nothing tied that closely to Microsoft will be good for users. 

I work with Microsoft products every day. They often excellent, and technically superior to a majority of their competitors, including thing in the FOSS computer. What do you expect with that much paid talent? There are real reasons they are on top. But Microsoft as a company has shown time and time again, it does not give a damn about anyone or anything except profits and control. 

.NET may have been created in good intentions. But Linux is a competitor. And you will see nothing but destruction by using a MS technology in Linux. I point you to JavaScript/JScript and Java/J++. Know your history, Mono is a mistake in the core of any Linux OS.

---

### Post by Sublime Porte on 2009-06-10
Regardless of if you're pro or anti mono... the question that really needs to be asked is, is there any real need for it? Is Linux that lacking in development tools that the best we can do is concoct an implementation of Microsoft's framework? (regardless of how 'open' its specification is)

I've got no objections to it being an optional package you can install, if you require it. But I can see absolutely no justifiable reason for why it has to be part of the default install. Linux has always been a rich environment for programmers, perhaps the richest, so why all of a sudden can we not do without mono? If you like C# syntax or something, then use Vala. If there's some other overwhelming reason why we need it, then I'm all ears... but  I can't for the life of me think of what it might be.

---

### Post by zekopeko on 2009-06-10
> **rhys_rhaven said:**
> ***I just wanted to add my vote as it were, to please remove Mono from the "ubuntu desktop" and find replacements to fspot and tomboy. ***

Having the Mono and Moonlight projects is very nice. .NET is a great setup for many users, often Windows developers, and makes Ubuntu more palatable as a product. Keep it in the repositories.

And yet, Ubuntu is supposed to work **"as if people mattered."** Linux distributions try to pick the best technical solution, the one with the most freedom, the one that won't get you in legal troubles or lock you into a single vendor. And regardless that Mono is open source, nothing tied that closely to Microsoft will be good for users. 

I work with Microsoft products every day. They often excellent, and technically superior to a majority of their competitors, including thing in the FOSS computer. What do you expect with that much paid talent? There are real reasons they are on top. But Microsoft as a company has shown time and time again, it does not give a damn about anyone or anything except profits and control. 

.NET may have been created in good intentions. But Linux is a competitor. And you will see nothing but destruction by using a MS technology in Linux. I point you to JavaScript/JScript and Java/J++. Know your history, Mono is a mistake in the core of any Linux OS.

troll. Microsoft has changed the course. they are getting involved with open source in an escalating manner.
there is an arstehnica article with deeper insight about the change that is brewing in the dungeons of redmond.

---

### Post by alternatealias on 2009-06-10
> **Sublime Porte said:**
> Regardless of if you're pro or anti mono... the question that really needs to be asked is, is there any real need for it?

Yes. Absolutely there is.

.NET is the next generation of programming environments that builds on the benefits of Java.

There's a lot more to .NET than the C# syntax, so Vala isn't enough.

- .NET brings along the potential to compile once, run everywhere. As long as your program does not call into native libraries, your program can be run anywhere that there is a .NET runtime.

- It brings along garbage collection which largely solves (or at least assists in solving) object life cycle issues that plague just about every software project out there (aka memory leaks).

- It has a very nice and extensive core library which standard C and C++ lack

- It brings along the ability to sandbox code.

- It brings better parallel programming APIs which help programmers take advantage of the latest multi-core CPUs far easier than you can in C or C++

- It allows applications to be written in mixed languages far more easily than other platforms

- Mono's new SIMD stuff is amazing, it recognizes code patterns and, if the host CPU supports it, will optimize said code (at runtime!) to use SIMD. No other platform provides this functionality.

- Extremely easy to write bindings to native libraries (1 very short line of code).

- Performance of .NET is very good, often on par with native code. Mono is slower than .NET but is making great strides in this area all the time.

- The C# syntax saves a lot of typing and is very easy to learn and also very powerful.


These are just the things I can list off the top of my head, there are doubtless many many more.

---

### Post by directhex on 2009-06-10
> **Sublime Porte said:**
> Regardless of if you're pro or anti mono... the question that really needs to be asked is, is there any real need for it? Is Linux that lacking in development tools that the best we can do is concoct an implementation of Microsoft's framework? (regardless of how 'open' its specification is)

I've got no objections to it being an optional package you can install, if you require it. But I can see absolutely no justifiable reason for why it has to be part of the default install. Linux has always been a rich environment for programmers, perhaps the richest, so why all of a sudden can we not do without mono? If you like C# syntax or something, then use Vala. If there's some other overwhelming reason why we need it, then I'm all ears... but  I can't for the life of me think of what it might be.

*.NET* is not part of the default install. What's part of the default install is the libraries required to run what are considered best-of-breed apps for users. Ubuntu doesn't ship with a .NET compatibility infrastructure, it ships with the libs needed to run Tomboy and F-Spot - which means some (not all) of Mono. If other apps written in other languages are better, then they get used. Not rocket science. And not to be confused.

---

### Post by Sublime Porte on 2009-06-10
> .NET is the next generation of programming environments that builds on the benefits of Java.

I meant features, not one-liner advertisements.

But the reference to Java does raise a good point, why not just build on java? Since it is now open source, wouldn't it be better to build on the benefits of Java ourselves, and make a framework that's more suited to our environment and circumstances?

> There's a lot more to .NET than the C# syntax, so Vala isn't enough.

As I said, _IF_ it's the syntax. The ironic thing is, you then went on to list the syntax as one of the merits of.NET/Mono... "The C# syntax saves a lot of typing and is very easy to learn and also very powerful".

> - .NET brings along the potential to compile once, run everywhere. As long as your program does not call into native libraries, your program can be run anywhere that there is a .NET runtime.

Nothing new from Java here. Are you sure it's compile once run everywhere? Can I compile a program in Mono on Linux and run it on Windows, assuming I have .net framework installed of course?

> - It brings along garbage collection which largely solves (or at least assists in solving) object life cycle issues that plague just about every software project out there (aka memory leaks).

Java has garbage collection, as do most modern languages built around Linux.

> - It has a very nice and extensive core library which standard C and C++ lack

Again so does Java, as does Python etc. Anyway as far as I'm aware .Net and therefore Mono as well I would assume is language independant, so wouldn't that actually be a feature of individual languages implemented in .Net rather than .Net itself?

> - It allows applications to be written in mixed languages far more easily than other platforms

As do most languages based around Linux.

> Performance of .NET is very good, often on par with native code. Mono is slower than .NET but is making great strides in this area all the time.

That's debateable.

You've made a poor case IMHO, in fact about all you've explained is that .Net is a lot like Java...

---

### Post by directhex on 2009-06-11
> **Sublime Porte said:**
> But the reference to Java does raise a good point, why not just build on java? Since it is now open source, wouldn't it be better to build on the benefits of Java ourselves, and make a framework that's more suited to our environment and circumstances?

Actually, Java is NOT well suited. At its core: Mono has been Free for 7 years, OpenJDK for about 2; Mono with 2 full apps takes up about 50 meg on disk, OpenJDK with zero apps takes up 100+ (thanks to the spaghetti of Java's class library, you can't distinguish between "useful" parts and "junk" parts to minimize that); .NET (and Mono by extension) makes it trivial to make use of existing C-based libraries inside your app, Java is an exercise in pain and suffering.

Ever noticed the distinct lack of desktop apps for GNOME written in Java? FWIW Java 7 promises to remedy many of Java's shortcomings - but that's not out yet, and until then, developers must write with what they have NOW

> Nothing new from Java here. Are you sure it's compile once run everywhere? Can I compile a program in Mono on Linux and run it on Windows, assuming I have .net framework installed of course?

Assuming you are only using libraries available on both systems, then yes, definitely - and the reverse is also true.

> Again so does Java, as does Python etc. Anyway as far as I'm aware .Net and therefore Mono as well I would assume is language independant, so wouldn't that actually be a feature of individual languages implemented in .Net rather than .Net itself?



As do most languages based around Linux.

No, that's his point. .NET is designed to be multi-language, such that (as an example) a library written in LOLCODE.NET can be used directly within Visual Basic.NET, no strings attached. The same libs are shared by ALL languages running on the framework, meaning there's no reinventing of wheels needed to, say, draw a GUI using Boo or Nemerle, once the bindings to do so are written in C#. There are a few Java-based languages such as Jython, but the Java bytecode is not designed for it, whereas it was a design goal from day 1 with .NET

---

### Post by Dragonbite on 2009-06-11
> **rhys_rhaven said:**
> And yet, Ubuntu is supposed to work **"as if people mattered."** Linux distributions try to pick the best technical solution, the one with the most freedom, the one that won't get you in legal troubles or lock you into a single vendor.

You mean things like UbuntuOne, being Ubuntu-only? There's no "vendor lock-in" there?

> **Sublime Porte said:**
> Regardless of if you're pro or anti mono... the question that really needs to be asked is, is there any real need for it? Is Linux that lacking in development tools that the best we can do is concoct an implementation of Microsoft's framework? 

Yes, it is needed.

There is a pool of thousands, if not millions of developers out there who are brought up in the Microsoft world and who are not interested in jumping to Python scripts or Java and such.  

Do you see an alternative to F-Spot for Gnome that is as full-featured?  No? Then that answers the question "do we need Mono?" because for whatever reason, before Mono and developers willing to build things in Mono, there was nobody interested in taking photo management beyond gThumbs.  Would those same developers had been interested if they had to migrate over to Eclipse or NetBeans and learn the differences between C# and Java? 

And let us not forget that in enterprises, .NET is pretty widely used. Not sure about your area, but I see a LOT more .NET job openings than Java openings around here! Mono is a technology that helps Linux into  Enterprises and Enterprises are(is?) where the money is that Linux needs to keep growing at this pace. Look how many developers for Linux are employed specifically to work on Linux.

---

### Post by Sublime Porte on 2009-06-11
> You mean things like UbuntuOne, being Ubuntu-only? There's no "vendor lock-in" there?

You're free to use dropbox (or whatever you like, webdav onto your own webhost etc). No lockin. Is UbuntuOne an integral part of the OS? Is it is even a part of the OS at all? Not as of yet, I don't think.

> Do you see an alternative to F-Spot for Gnome that is as full-featured?

F-Spot is full featured? Depends what you mean by full featured, I personally never even opened it before, ditto for tomboy. These two programs are pretty spartan when it comes to features, so if they're your best excuse for why mono is a necessity, then you've lost me there.

> And let us not forget that in enterprises, .NET is pretty widely used. Not sure about your area, but I see a LOT more .NET job openings than Java openings around here!

I've heard people claim this before, but after doing a little research, Java jobs came up much higher in my country (Australia), and even then a lot of .Net jobs asked for Java experience as a bonus anyway.

> Mono is a technology that helps Linux into Enterprises and Enterprises are(is?) where the money is that Linux needs to keep growing at this pace

I'd say most enterprise implementations of Linux are replacing legacy Unix systems, not Microsoft systems. So .Net is probably not that big a deal to them.

Linux has grown mostly because of its community, not because of its funding. The vast majority of development for Linux is done by volunteers, not by employees.

---

### Post by alternatealias on 2009-06-11
> **Sublime Porte said:**
> F-Spot is full featured? Depends what you mean by full featured, I personally never even opened it before, ditto for tomboy. These two programs are pretty spartan when it comes to features, so if they're your best excuse for why mono is a necessity, then you've lost me there.

If you've never used the applications, how could you possibly state that they are spartan when it comes to features?

I smell a troll.

---

### Post by Dragonbite on 2009-06-11
> **Sublime Porte said:**
> You're free to use dropbox (or whatever you like, webdav onto your own webhost etc). No lockin. Is UbuntuOne an integral part of the OS? Is it is even a part of the OS at all? Not as of yet, I don't think.

Ahh.. but once you will start using UbuntuOne, you cannot, at this time, move to Fedora, Windows or any other non-Ubuntu distribution without loosing access to UbuntuOne. That's is lock-in.

Dropbox is an alternative, like Linux is for Windows.

> **Sublime Porte said:**
> F-Spot is full featured? Depends what you mean by full featured, I personally never even opened it before, ditto for tomboy. 

So basically your opinion on these applications is 3rd party hearsay at best?

> **Sublime Porte said:**
> I've heard people claim this before, but after doing a little research, Java jobs came up much higher in my country (Australia), and even then a lot of .Net jobs asked for Java experience as a bonus anyway.

YMMV

> **Sublime Porte said:**
> Linux has grown mostly because of its community, not because of its funding. The vast majority of development for Linux is done by volunteers, not by employees.

Neither one of us has the numbers for that so it's a piss contest. 

I was just thinking of all of the times I hear the Ubuntu is developed by Canonical employees, Fedora developed by Red Hat employees and openSUSE developed by Novell employees plus the number of projects that these companies (not individuals) are listed as participating in the development of open source projects like the kernel and such.  Even Java was developed by Sun employees.  

And of course, Mono is developed by some Novell employees as well as individuals.

---

### Post by Sublime Porte on 2009-06-11
alternatealias,

> If you've never used the applications, how could you possibly state that they are spartan when it comes to features?

I've seen others attempt to use it, and end up not bothering, since the features were simply not sufficient.

> I smell a troll.

I doubt you'd know a troll if it slapped you in the face. Hint, A troll is _NOT_ someone who merely holds a different opinion to yours, seems to be the favourite catchphrase for some around here though, when faced with an apparently differing opinion. Learn to explain your opinions and elaborate on their supposed merits, rather than just jumping on the troll button everytime someone says something you don't personally subscribe to.

dragonbite,

> Ahh.. but once you will start using UbuntuOne

So don't start using it, simple. Besides, I'm not necessarily an Ubuntu advocate. I believe in Freedom of software, whether that means on Ubuntu, Debian, Puppy, FreeBSD whatever, I'm not particularly phased. I'm more worried about the potential prospects for freedom, which is why my instincts tell me mono is no good. Since it is inevitably tied to Microsoft. Even if you'd like to believe that theoretically according to ECMA standards blah blah blah it is not.. In the end, it leads all the way back to Redmond. I personally don't want to risk my OS investment on that.

> So basically your opinion on these applications is 3rd party hearsay at best?

I've seen them fired up.

> I was just thinking of all of the times I hear the Ubuntu is developed by Canonical employees...

Ubuntu, Fedora & OpenSuse are distributions. Most of the work within distributions is packaging and bug fixing, not coding. The coding is done by ther various projects, most of which are not-for-profit foundations, run by volunteers, or even just individual coders. Which company funds and pays the Kernel hackers?

Also the top 10 distros, according to distrowatch are:

1) Ubuntu - Foundation/Community
2) OpenSuse - Company
3) Mint - Community
4) Fedora - Company
5) Debian - Community
6) Mandriva - Company
7) PCLinuxOS - Community
8) Puppy - Community
9) Sabayon - Community
10) CentOS - Community

Mostly community-based projects.

---

### Post by Dragonbite on 2009-06-11
According to this, up to about 25% is done by individuals (shown as "None") or those they could not determine if they were affiliated with with a corporation or who contributed 10 or fewer changes (shown as "Unknown").
> 
**Linux Kernel Development (April 2008 )**
Who is Sponsoring the Work

The Linux kernel is a resource which is used by a large variety of companies. Many of those companies never participate in the development of the kernel; they are content with the software as it is and do not feel the need to help drive its development in any particular direction. But, as can be seen in Table 4, an increasing number of companies are working toward the improvement of the kernel.
[IMG]http://www.linuxfoundation.org/publications/images/table4-companies.gif[/IMG]


---

### Post by zekopeko on 2009-06-11
> **Dragonbite said:**
> Ahh.. but once you will start using UbuntuOne, you cannot, at this time, move to Fedora, Windows or any other non-Ubuntu distribution without loosing access to UbuntuOne. That's is lock-in.

Dropbox is an alternative, like Linux is for Windows.


dropbox is a far greater lock-in then U1. U1 client and more importantly the protocol are FOSS. nobody is stopping you or anybody else to write a replacement for U1 server access. the only thing that could stop you would be Terms of Use of UbuntuOne service. but then again you could also write a FOSS server component analog to the U1 server component.

> 
So basically your opinion on these applications is 3rd party hearsay at best?

YMMV


agreed. watching somebody isn't the same as doing it yourself.

> 
Neither one of us has the numbers for that so it's a piss contest. 

I was just thinking of all of the times I hear the Ubuntu is developed by Canonical employees, Fedora developed by Red Hat employees and openSUSE developed by Novell employees plus the number of projects that these companies (not individuals) are listed as participating in the development of open source projects like the kernel and such.  Even Java was developed by Sun employees.  

And of course, Mono is developed by some Novell employees as well as individuals.

Large part of mono were developed by other companies besides novell. it's the same as with the linux kernel. there are a number of individual contributor but the kernel development is heavily helped by companies providing large pieces of code. why? because they use linux in their operations and want it to do a specific task geared toward their business. that's why linux first conquered the server space.

here is an article from the linux foundation about contributors dated april 2008:
[http://www.linuxfoundation.org/publications/linuxkerneldevelopment.php](http://www.linuxfoundation.org/publications/linuxkerneldevelopment.php)

---

### Post by zekopeko on 2009-06-11
damn you beat me to the punch dragonbite.

---

### Post by Dragonbite on 2009-06-11
> **zekopeko said:**
> dropbox is a far greater lock-in then U1. U1 client and more importantly the protocol are FOSS. nobody is stopping you or anybody else to write a replacement for U1 server access. the only thing that could stop you would be Terms of Use of UbuntuOne service. but then again you could also write a FOSS server component analog to the U1 server component.

Agreed, if it is FOSS it can be modified to play with others nicely, point taken.

> **zekopeko said:**
> 
here is an article from the linux foundation about contributors dated april 2008:
[http://www.linuxfoundation.org/publications/linuxkerneldevelopment.php](http://www.linuxfoundation.org/publications/linuxkerneldevelopment.php)
Yeah, that's where I got the chart and quote from.

---

### Post by knopper67 on 2009-06-12
Back in 2006 someone in this thread mentioned it was only a matter of time before non-mono alternatives started popping up. 

What a coincidence! I just started developing a non-mono alternative to tomboy! [IMG]http://i166.photobucket.com/albums/u115/AJ1586019/banana0tq.gif[/IMG]

---

### Post by ad_267 on 2009-06-12
> **knopper67 said:**
> Back in 2006 someone in this thread mentioned it was only a matter of time before non-mono alternatives started popping up. 

What a coincidence! I just started developing a non-mono alternative to tomboy! [IMG]http://i166.photobucket.com/albums/u115/AJ1586019/banana0tq.gif[/IMG]

You're a bit late. Have a look at gnote.

---

### Post by gnomeuser on 2009-06-12
> **Sublime Porte said:**
> 
1) Ubuntu - Foundation/Community
2) OpenSuse - Company
3) Mint - Community
4) Fedora - Company
5) Debian - Community
6) Mandriva - Company
7) PCLinuxOS - Community
8) Puppy - Community
9) Sabayon - Community
10) CentOS - Community


You wrong on Ubuntu, The Ubuntu Foundation is a trust that largely exists in case Canonical goes under. Canonical with some community participation does the Ubuntu specific development.
 
You are also wrong for openSUSE which also has a vibrant community to maintain it's packages. It isn't just Novell/SuSE employees, e.g. the contrib repo is run by a lot of volunteers.

You are wrong again with Fedora, by far the majority of the packages in Fedora are maintained exclusively by volunteer community members, community members account for the majority of Fedora spins as well as probably half the new features in any release. From the sense of being a community driven distribution Fedora is probably the single best example we have which also has corporate sponsorship.

A substanial amount of the work you use today on any given Linux desktop has been touched by community members working on Fedora. It is not just about packaging and bugfixing, community members actually drive new features and plentiful bucketloads of code to your desktop. 

Please improve your research.

---

### Post by Sublime Porte on 2009-06-12
Gnomeuser,

You validate my point. I wanted to put them as community, because they are the comunity editions of SLED & Red Hat, but I thought I'd just be a little conservative in my estimates. My position here is that community participation is a major contributing factor, probably the lion's share, not the other wway round.

---

### Post by Dragonbite on 2009-06-12
Jo Shields wrote an interesting blog response to Linux Today, which was asking for pro-Mono submissions.  
> Your request was for “a calm presentation of why Mono is desirable, why it is not a threat, and why it should be included in Ubuntu by default”. I’ll answer these three questions individually, then offer a general comment on your post, as well as the wider “anti-Mono” movement. This message is GPG-signed to ensure it is published unedited.

[[COLOR="Blue"]You can read the rest of the blog post here[/COLOR]]("http://www2.apebox.org/wordpress/rants/124/").


@Gnomeuser : thanks for the insight.

---

### Post by alternatealias on 2009-06-12
> **Dragonbite said:**
> Jo Shields wrote an interesting blog response to Linux Today, which was asking for pro-Mono submissions.  


[[COLOR="Blue"]You can read the rest of the blog post here[/COLOR]]("http://www2.apebox.org/wordpress/rants/124/").


@Gnomeuser : thanks for the insight.

Wow, great blog post!

---

### Post by Dragonbite on 2009-06-12
> **alternatealias said:**
> Wow, great blog post!
I don't like reading white text on black background.

---

### Post by cb951303 on 2009-06-12
> **Dragonbite said:**
> I don't like reading white text on black background.

it's not white

---

### Post by Dragonbite on 2009-06-12
> **cb951303 said:**
> it's not white

Ok, "light"?

---

### Post by zekopeko on 2009-06-12
> **Dragonbite said:**
> Ok, "light"?

[http://planet.ubuntu.com/](http://planet.ubuntu.com/)

scroll down.

---

### Post by Delever on 2009-06-12
Nonsense. Happens.

---

### Post by k2t0f12d on 2009-06-13
[FONT="Courier New"]127.0.0.1    <*ad server here*>[/FONT]

---

### Post by Sef on 2009-06-13
Jo Shields, a member of the Debian Mono Group, Debian CLI Applications Team, and Debian CLI Libraries Team and also a Ubuntu MOTU, has written an article [in favor of Mono]("http://blog.linuxtoday.com/blog/2009/06/why-mono-is-des.html").

---

### Post by handy on 2009-06-14
Thanks for posting that link Sef, it is the best I've read on Mono.

Jo Shields presents a thorough overview of the Mono situation in an obviously knowledgeable, clear, concise, non-reactive & even handed fashion.

I think that many Linux users need to read his words & understand them.

---

### Post by directhex on 2009-06-14
> **handy said:**
> Thanks for posting that link Sef, it is the best I've read on Mono.

Jo Shields presents a thorough overview of the Mono situation in an obviously knowledgeable, clear, concise, non-reactive & even handed fashion.

I think that many Linux users need to read his words & understand them.

I don't know about even-handed - there's some clear bias in it, especially the last two sections.

---

### Post by twright on 2009-06-14
I think that most of the people who oppose mono just do so because of the relationship with Microsoft and are thus loosing out on good applications and (dare I say it?) a good programing framework.

---

### Post by UbuKunubi on 2009-06-14
AS far as Im concerned I have python and C++, so why yet another language? Whatever reasons others give I see no reason for it.

After I removed mono from my Jaunty system there was a increase in system performance, so I now know I did the right thing.

My pennies worth,
Ubu

---

### Post by Sublime Porte on 2009-06-14
Posting in this thread is probably going to be useless, as any criticism of mono is usually met (by it's devotees) with cries of trolling, but here goes anyway.

As Ubukunubi mentioned above, we've got plenty of other languages already that work just fine. Also it seems the only real benefits that the article could mention were easier coding, that's what it all hinged on. I would submit that vala, having a c# like syntax, as well as a nice object-oriented interface to gtk would fill most of the gaps the article's author claims that mono fills for us. Python works fine for me, and I really don't find it to be as slow as they claim. Sure it's not as fast as c or c++, but now we have vala, we have that speed (vala would be faster than mono, since it actually translates everything back into pure c), in an easier to use language anyway.

---

### Post by directhex on 2009-06-14
> **UbuKunubi said:**
> AS far as Im concerned I have python and C++, so why yet another language? Whatever reasons others give I see no reason for it.

Are you telling Free Software developers what you give them permission to use?

> After I removed mono from my Jaunty system there was a increase in system performance, so I now know I did the right thing.

[http://en.wikipedia.org/wiki/Placebo](http://en.wikipedia.org/wiki/Placebo)

---

### Post by 23meg on 2009-06-14
[QUOTE=Sublime Porte]I would submit that vala, having a c# like syntax, as well as a nice object-oriented interface to gtk would fill most of the gaps the article's author claims that mono fills for us.[/QUOTE]

One downside to that argument is that Vala is not as capable, mature and complete as Mono at this time for many potential use scenarios.

I would suggest people who have a vendetta against Mono for whatever reason (regardless of its merit and validity) to put their efforts into actually providing an equally compelling alternative to it, instead of merely talking against it. Vala could indeed be it, and looks like the closest candidate, but it isn't at this point.

Of course, testing, documenting, improving, using and spreading Vala will be harder work than producing anti-Mono FUD.

---

### Post by kirsis on 2009-06-14
> **UbuKunubi said:**
> 
After I removed mono from my Jaunty system there was a increase in system performance, so I now know I did the right thing.


:---)


I can already imagine some people new to Linux perusing some threads and reading this statement.

Not knowing/caring about the whole Mono issue, they don't proceed to read the whole thread, however this quote's pretty easy to remember, even if you aren't informed about the technology (X made Y slow, X = bad).

Then, whenever Mono is brought up, they repeat it to their friends, who are also new to Linux, "Oh, Mono makes your system slow, you better uninstall it". :roll:



Good article, imo. I hope this thread doesn't devolve into people stating their "valid" reason X for hating mono, even though the very same issue was addressed in the article. It happened on reddit.

---

### Post by Sublime Porte on 2009-06-14
> I would suggest people who have a vendetta against Mono for whatever reason (regardless of its merit and validity) to put their efforts into actually providing an equally compelling alternative to it, instead of merely talking against it.

That is indeed good advice.

> Of course, testing, documenting, improving, using and spreading Vala will be harder work than producing anti-Mono FUD.

Well, those who have reservations about mono generally don't go around starting topics about it everywhere, however they will often respond to thread after thread of heaped praise for mono. So I think that point wasn't quite valid.

My resevrations about mono spring from the fact that Microsoft has clearly threatened to bring Linux down by use of patents, and although it's not entirely clear yet how they could do that with mono, I really do think we should err on the side of caution, and avoid anything that could possibly assist them in carrying out that threat. I don't know how long you've been using Linux, but for some it's been well over a decade, and we don't want to see it go down the gurgler just like that, simply so people can have some extra convenience when writing code. I do understand though that for those who've only adopted Linux in the last coupla years, they probably can't see the dangers of this threat, since for them Linux is something fairly new and novel anyway, and not something they've come to rely heavily upon, perhaps after they've become more attached to it, they'll feel the same level of protectiveness over it.

---

### Post by saulgoode on 2009-06-14
> **"Jo Shield's essay, the section WHY IT IS NOT A THREAT"]Mono is not a threat because it is not special in any legal regard.[/QUOTE]

Mono is quite unique amongst Free Software projects in that it relies upon patent licensing from a non-contributor for defense of its implementation of the patented technology. No other Free Software project does this. 

Comparisons are often made by Mono advocates between patent issues of projects such as the Linux kernel, WINE, Samba, OpenOffice.org, & Firefox and concerns over the patent issues of Mono. These comparisons invariable leave out the fact that **none of these projects rely on patent licensing from third-parties** for their implementation of technology which is potentially encumbered by patents. The Mono Project explicitly asserts that Microsoft holds patents on technology incorporated into the ECMA 334 and ECMA 335 standards and presents an offer of a patent licensing grant from Microsoft to support that implementing that patented technology is safe from infringement liability.

[QUOTE="Jo Shield's essay, the section WHY IT IS NOT A THREAT"]* Mono is not the result of any deals between Novell and Microsoft. Mono was started 4 years before that unfortunate deal took place. Mono gets no special treatment under that deal. It is not mentioned in the deal (as with other apps). This is important to note.[/quote]

While the first two sentences are entirely true, the 2006 Microsoft/Novell patent agreement does have an extremely significant impact on the issue of patent concerns over the Mono Project and this impact is indeed important to note.

The Mono Project is frequently touting the level of cooperation exhibited by Microsoft with regard to the Mono and Moonlight projects said:**
> estoppel[/URL]: in non-technical terms, you can't encourage someone to do something and then turn around sue them for doing it. However, the 2006 Novell/Microsoft patent covenant effectively cancels any defense of estoppel because MS is not endorsing a .NET implementation to be made available to everyone under Free Software licensing terms, but instead is collaborating with a business partner to develop a product that is intended only for that partner's customers. Yes, Novell customers gain further defense against infringement claims, but not Ubuntu customers (or Fedora, or Debian, or Mandriva, ...).

[QUOTE="Jo Shield's essay, the section WHY IT IS NOT A THREAT"]* Mono is covered by the OIN, as with most other major Free apps. Patent attacks against Mono carry the same risk to attackers as attacks against any other OIN entrant. Attacks against Mono would risk patent "world war", which Microsoft cannot win. Such an action would harm their business - and lose them money.
While I will not contest this point, I will state my opinion that the approach to patent security advanced by the OIN is distasteful and counterproductive. The idea that the Free Software community should strive to employ, and thereby substantiate, software patents in an effort to provide protection against them is both hypocritical and misguided. Should the OIN ever litigate a patent lawsuit I will undoubtedly be rooting for the defendant and that the patent be invalidated (just as I currently do with any defendant, including Microsoft). 

[QUOTE="Jo Shield's essay, the section WHY IT IS NOT A THREAT"]* Mono implements an international standard - albeit one from a convicted monopolist. If this is a problem, why do people use C, the standard from convicted monopolist AT&T? Mono implements an improved, Free replacement for a proprietary offering. If this is a problem, why do people use GNU (which provided an improved, Free replacement for proprietary UNIX)?[/quote]
This argument has been rebutted so often and so soundly that it amazes that Mono advocates still insist on presenting it. Being an "international standard" inheres no indemnity against patent claims. Being an ECMA standard only provides assurance that associated patent licensing will be *offered* under reasonable and non-discriminatory terms (with no clear definition of what should be defined "reasonable" or "non-discriminatory").

[QUOTE="Jo Shield's essay, the section WHY IT IS NOT A THREAT"]* Absence of "patent protection" is not the same thing as "patent violation". If I offer to sell somebody a promise not to sue them using any of my patents, their taking me up on my offer is no guarantee that I even have anything valid to sell them - merely that they are willing to buy it. If Jim buys protection from any patents I hold, it does not mean that Jim is infringing on anything specific - nor that if Ted does the same thing, that Ted is violating anything either. If a house insurance policy includes flood protection, it does not mean that your house will be flooded - and not buying flood protection does not mean that you will be flooded either.[/QUOTE]

The argument presented is accurate, however, it makes the erroneous presumption that litigation is the sole means through which patent issues might be employed to the detriment of a Mono user. If I have a business and am using Ubuntu's Mono stack on some of my systems, it would be neither inconceivable nor unprecedented that a Microsoft sales strategy might be applied to compel me to switch to a SuSE, or even a Microsoft, solution in order to avoid litigation. 

[QUOTE="Jo Shield's essay, the section WHY IT IS NOT A THREAT"]* Regardless of whether or not any specific patent licenses over ECMA 334 and 335 cover Mono's implementation of those standards, if indeed such agreements are available (ITWire's curlish "attempt" to secure such an arrangement aside), the fact that statements have been made in public supporting the idea of royalty-free licensing essentially reduces the financial impact of such infringement to zero.[/quote]

Herein lies the most egregious error in Jo Shield's essay: the idea that monetary compensation is the only economic benefit that a right's holder might expect from his licensing. It is the very foundation of reciprocal licenses such as the GPL that benefits other than direct payment of money are desirable when sharing "intellectual property". It has been recognized by the courts -- most recently in the case of [Jacobsen v. Katzer](http://en.wikipedia.org/wiki/Jacobsen_v._Katzer) -- and yet the Mono Project would have us believe that Microsoft, in offering royalty-free licensing, has sacrificed ALL of its exclusive rights and has forgone any opportunity to accrue any benefits aside from potential monetary gain. This is a grave misrepresentation of the legalities underlying Microsoft's offer of RAND-Z patent licensing.

The reason this is so egregious is because the argument is completely lacking in ethics. If a band offers their latest album as a free download from its website, the fact they are offering it "royalty-free" does not mean that everyone is free to do with it what they will. The band still holds the copyrights and reserves the right to demand that recipients visit the website and download it for themselves; and though the band may not be directly compensated monetarily, courts would readily recognize the band's expectation that the terms and conditions of their licensing be respected. Likewise, courts will readily find that Microsoft has not sacrificed ALL of their patent rights just because of their offer of royalty-free and non-discriminatory licensing.

It is the unethical nature of this argument which singles out Mono as a particular liability to the Free Software community. Ethics weigh heavily in courts' decisions and it is especially true for the field of intellectual property law. Ethics are even written into the code of law itself. Actions which might otherwise be considered legal can be ruled illegal owing to them being performed through unethical means or for unethical purposes. Cases which might otherwise be won can be lost owing to unethical arguments presented in defense. 

Consider the case of [DeCSS](http://en.wikipedia.org/wiki/Universal_v._Reimerdes), where hopes of a free implementation of DVD playback were effectively shattered because it was adjudged that the primary purpose of the defendants' actions was to promote violation of copyright laws (because they basically admitted such). If instead the defendants had been more ethical, it is quite possible that they'd have prevailed and watching DVDs on Free Software systems not be so problematic as it currently is.

It is my main concern, this increased potential of a GNU/Linux losing a software patent case owing to an unscrupulous disregard for the licensing offered by Microsoft over their ECMA 334/335 patents. Such a loss would be extremely detrimental to the cause of Free Software just at a time when it seems the courts are on the verge of abrogating software patents altogether.

I have no objection to the existence of the Mono Project nor would I ever suggest that its developers stop working on its development. However, when it comes to distros such as Ubuntu distributing Mono in its default install, this places an undue risk on the entire Free Software community and could serve to negate significant advances that have occurred over the past couple of years in the elimination of software patents.

By all means, Mono developers should continue development and distros should offer Mono as a choice for users to install. But, at least for now, distros should abide by the licensing terms which Microsoft offers or leave it to individual users to decide the applicability of patent laws in their jurisdictions. Perhaps in a year or so there will be a clearer vision of which way the fight against software patents is headed; the U.S. Supreme Court has just this month announced that their fall session will hear the appeal of the Re: Bilski ruling, and the European Patent Office is currently considering arguments on software patents.  

Alternately, the Mono Project should explicitly state what the exact terms and conditions are of Microsoft's alleged patent grant. The current lack of any hard documentation of any unrestricted license being granted is entirely unacceptable.

---

### Post by 23meg on 2009-06-14
[QUOTE=Sublime Porte]Well, those who have reservations about mono generally don't go around starting topics about it everywhere, however they will often respond to thread after thread of heaped praise for mono. So I think that point wasn't quite valid.[/QUOTE]

My impression has been rather towards the contrary. Perhaps we've been looking at different places.
 
And FUD != reservations. I do have some reservations myself, and have found writings from those with reservations in the vein of Shields' post very informative, but I prefer to keep my reservations to myself until I'm reasonably informed on the issue.

[QUOTE=Sublime Porte]I don't know how long you've been using Linux, but for some it's been well over a decade, and we don't want to see it go down the gurgler just like that, simply so people can have some extra convenience when writing code. I do understand though that for those who've only adopted Linux in the last coupla years, they probably can't see the dangers of this threat, since for them Linux is something fairly new and novel anyway, and not something they've come to rely heavily upon, perhaps after they've become more attached to it, they'll feel the same level of protectiveness over it.[/QUOTE]

I'm part of the decade old crowd, but I've seen people with varying levels of experience on both sides of the fence, as well as right on the fence.

---

### Post by directhex on 2009-06-14
> **saulgoode said:**
> Mono is quite unique amongst Free Software projects in that it relies upon patent licensing from a non-contributor for defense of its implementation of the patented technology. No other Free Software project does this. 

Comparisons are often made by Mono advocates between patent issues of projects such as the Linux kernel, WINE, Samba, OpenOffice.org, & Firefox and concerns over the patent issues of Mono. These comparisons invariable leave out the fact that **none of these projects rely on patent licensing from third-parties** for their implementation of technology which is potentially encumbered by patents. The Mono Project explicitly asserts that Microsoft holds patents on technology incorporated into the ECMA 334 and ECMA 335 standards and presents an offer of a patent licensing grant from Microsoft to support that implementing that patented technology is safe from infringement liability.

It doesn't "rely" on anything - it falls back on it at worst. As in "if you care, ask these guys who say they'll hook you up"

You used the key word here yourself - ***potentially***. There are no documented instances of patents infringed by Mono - and nobody in 7 years has stepped forward with an example. The Mono Project explicitly asserts that Microsoft holds patents on their implementation of ECMA334/335 (Microsoft.NET), but makes no claims regarding any potential overlap between specific methods which may (or may not) be patented, and the Mono (or other non-Microsoft) implementations.

Let's look to another example you name - OpenOffice.org. OOo implements, courtesy of Sun, importers for ECMA376 (OOXML). ECMA376 has an identical (almost to the letter) offer for patent licensing covering implementations, up on the ECMA website ([http://www.ecma-international.org/publications/files/ECMA-ST/Ecma%20PATENT/ECMA-376%20Edition%202%20Microsoft%20Patent%20Declaration.pdf](http://www.ecma-international.org/publications/files/ECMA-ST/Ecma%20PATENT/ECMA-376%20Edition%202%20Microsoft%20Patent%20Declaration.pdf)). Will you make the same claims against OOo as against Mono, given they both implement Microsoft-sourced ECMA standards with identical patent statements?

> While the first two sentences are entirely true, the 2006 Microsoft/Novell patent agreement does have an extremely significant impact on the issue of patent concerns over the Mono Project and this impact is indeed important to note.

The Mono Project is frequently touting the level of cooperation exhibited by Microsoft with regard to the Mono and Moonlight projects; Mono developers have often visited the Redmond campus and Miguel de Icaza (the Mono Project leader) even lectured at Microsoft's 2008 Programmers Developer Conference. All things being equal, such cooperation would provide a strong indication that Microsoft holds no opposition to a Free implementation of the .NET technology being produced. 

This cooperation would even have legal significance under the doctrine of [estoppel]("http://en.wikipedia.org/wiki/Estoppel"): in non-technical terms, you can't encourage someone to do something and then turn around sue them for doing it. However, the 2006 Novell/Microsoft patent covenant effectively cancels any defense of estoppel because MS is not endorsing a .NET implementation to be made available to everyone under Free Software licensing terms, but instead is collaborating with a business partner to develop a product that is intended only for that partner's customers. Yes, Novell customers gain further defense against infringement claims, but not Ubuntu customers (or Fedora, or Debian, or Mandriva, ...).

[http://msdn.microsoft.com/en-us/library/ms973826.aspx](http://msdn.microsoft.com/en-us/library/ms973826.aspx)

2001 would be prior to the Novell arrangement, and restore the question of estoppel, yes?

> While I will not contest this point, I will state my opinion that the approach to patent security advanced by the OIN is distasteful and counterproductive. The idea that the Free Software community should strive to employ, and thereby substantiate, software patents in an effort to provide protection against them is both hypocritical and misguided. Should the OIN ever litigate a patent lawsuit I will undoubtedly be rooting for the defendant and that the patent be invalidated (just as I currently do with any defendant, including Microsoft).

I agree - but my point is that Mono is covered by the same "patent good guys" as, say, Apache or Amarok ([http://www.openinventionnetwork.com/pat_linuxdefpop.html](http://www.openinventionnetwork.com/pat_linuxdefpop.html)).

> This argument has been rebutted so often and so soundly that it amazes that Mono advocates still insist on presenting it. Being an "international standard" inheres no indemnity against patent claims. Being an ECMA standard only provides assurance that associated patent licensing will be *offered* under reasonable and non-discriminatory terms (with no clear definition of what should be defined "reasonable" or "non-discriminatory").

It does, however, help to establish estoppel.

> The argument presented is accurate, however, it makes the erroneous presumption that litigation is the sole means through which patent issues might be employed to the detriment of a Mono user. If I have a business and am using Ubuntu's Mono stack on some of my systems, it would be neither inconceivable nor unprecedented that a Microsoft sales strategy might be applied to compel me to switch to a SuSE, or even a Microsoft, solution in order to avoid litigation.

If they explicitly cited a particular project as a problem (rather than the general statements about "Linux" issued from dimwit managers to equally dimwit salespeople), then that would be news. But bear in mind that claims are not the same thing as truth - see SCO for a well-documented example.

> Herein lies the most egregious error in Jo Shield's essay: the idea that monetary compensation is the only economic benefit that a right's holder might expect from his licensing. It is the very foundation of reciprocal licenses such as the GPL that benefits other than direct payment of money are desirable when sharing "intellectual property". It has been recognized by the courts -- most recently in the case of [Jacobsen v. Katzer](http://en.wikipedia.org/wiki/Jacobsen_v._Katzer) -- and yet the Mono Project would have us believe that Microsoft, in offering royalty-free licensing, has sacrificed ALL of its exclusive rights and has forgone any opportunity to accrue any benefits aside from potential monetary gain. This is a grave misrepresentation of the legalities underlying Microsoft's offer of RAND-Z patent licensing.

The reason this is so egregious is because the argument is completely lacking in ethics. If a band offers their latest album as a free download from its website, the fact they are offering it "royalty-free" does not mean that everyone is free to do with it what they will. The band still holds the copyrights and reserves the right to demand that recipients visit the website and download it for themselves; and though the band may not be directly compensated monetarily, courts would readily recognize the band's expectation that the terms and conditions of their licensing be respected. Likewise, courts will readily find that Microsoft has not sacrificed ALL of their patent rights just because of their offer of royalty-free and non-discriminatory licensing.

It is the unethical nature of this argument which singles out Mono as a particular liability to the Free Software community. Ethics weigh heavily in courts' decisions and it is especially true for the field of intellectual property law. Ethics are even written into the code of law itself. Actions which might otherwise be considered legal can be ruled illegal owing to them being performed through unethical means or for unethical purposes. Cases which might otherwise be won can be lost owing to unethical arguments presented in defense. 

Consider the case of [DeCSS](http://en.wikipedia.org/wiki/Universal_v._Reimerdes), where hopes of a free implementation of DVD playback were effectively shattered because it was adjudged that the primary purpose of the defendants' actions was to promote violation of copyright laws (because they basically admitted such). If instead the defendants had been more ethical, it is quite possible that they'd have prevailed and watching DVDs on Free Software systems not be so problematic as it currently is.

It is my main concern, this increased potential of a GNU/Linux losing a software patent case owing to an unscrupulous disregard for the licensing offered by Microsoft over their ECMA 334/335 patents. Such a loss would be extremely detrimental to the cause of Free Software just at a time when it seems the courts are on the verge of abrogating software patents altogether.

I have no objection to the existence of the Mono Project nor would I ever suggest that its developers stop working on its development. However, when it comes to distros such as Ubuntu distributing Mono in its default install, this places an undue risk on the entire Free Software community and could serve to negate significant advances that have occurred over the past couple of years in the elimination of software patents.

By all means, Mono developers should continue development and distros should offer Mono as a choice for users to install. But, at least for now, distros should abide by the licensing terms which Microsoft offers or leave it to individual users to decide the applicability of patent laws in their jurisdictions. Perhaps in a year or so there will be a clearer vision of which way the fight against software patents is headed; the U.S. Supreme Court has just this month announced that their fall session will hear the appeal of the Re: Bilski ruling, and the European Patent Office is currently considering arguments on software patents.  

Alternately, the Mono Project should explicitly state what the exact terms and conditions are of Microsoft's alleged patent grant. The current lack of any hard documentation of any unrestricted license being granted is entirely unacceptable.

So are you making the same calls to see the signed patent agreements for ECMA376 implementations such as OOo? If not, why not? Are OOo developers unethical for writing that code in the absence of such a written agreement?

---

### Post by &#32 Greg on 2009-06-14
> **UbuKunubi said:**
> AS far as Im concerned I have python and C++, so why yet another language? Whatever reasons others give I see no reason for it.

After I removed mono from my Jaunty system there was a increase in system performance, so I now know I did the right thing.

My pennies worth,
Ubu

We have LISP for a high level language and C and Assembly for low level stuff, what do we need C++ and Python for?

---

### Post by handy on 2009-06-15
Apparently Mark Shuttleworth thinks Mono is a good thing.

I would think that he (Mark) would know if there are existing &/or potential legal problems with Mono, before making such a statement.

If you missed it, it is referenced in the linked to article by Jo Shields.

---

### Post by Sublime Porte on 2009-06-15
> I would think that he (Mark) would know if there are existing &/or potential legal problems with Mono, before making such a statement.

With all due respect to Shuttleworth, Linux and the Free Software Movement in general does not rest on the back of one individual and his opinion, not even Stallman or Torvalds, so that was a pretty pointless statement. Likewise no one man is capable of knowing all the intricacies of software patent laws and how they will playout in the future. Unless I'm mistaken and Shuttleworth is actually a clarivoyant and a patent law expert all rolled into one?

---

### Post by handy on 2009-06-15
It really is a bit sad & also somewhat amusing how snitchy people get on this subject.

They obviously don't have enough to worry about in reality.

Mono will do its thing & become history like everything else.

If it lives or dies, or transmogrifies, I couldn't care less. :D

---

### Post by directhex on 2009-06-15
> **Sublime Porte said:**
> With all due respect to Shuttleworth, Linux and the Free Software Movement in general does not rest on the back of one individual and his opinion, not even Stallman or Torvalds, so that was a pretty pointless statement. Likewise no one man is capable of knowing all the intricacies of software patent laws and how they will playout in the future. Unless I'm mistaken and Shuttleworth is actually a clarivoyant and a patent law expert all rolled into one?

I think the point is "if Microsoft go postal, who will they sue - Sublime Porte for running something, or the billionaire who's been distributing it?"

---

### Post by Methuselah on 2009-06-15
No mo Mono!

Actually, I'm not that concerned about it as long as it remains easy to remove.

---

### Post by directhex on 2009-06-15
> **Methuselah said:**
> No mo Mono!

Actually, I'm not that concerned about it as long as it remains easy to remove.

The removal process for Karmic will be different. There will be only one package - mono-runtime - at the root of the dependency tree.

---

### Post by lykwydchykyn on 2009-06-15
I guess I'd qualify as on the fence.  I'm not terribly worried about using mono-based software (I use it at work with some in-house stuff), but as someone who occasionally wears a programming hat I've shied away from learning any of the mono/.NET related languages because of the controversy.

I think the most unfortunate part of Jo's essay is how much of it is devoted to spurious ad-hominem against the so-called "anti-mono" crowd.  I don't think there's a movement, cause, or political/social/religious ideology out there that doesn't contain at least some small-but-vocal contingent of slavering moronic cretins who can do no better than parrot superstitious dogma with their fingers in their ears.  But that doesn't automatically invalidate the movement/cause/ideology itself.  Bringing it up was pure blather.

The crux of the controversy is what saulgoode and directhex are here debating, and on that issue jo's arguments were, IMHO, poorly argued.

---

### Post by zekopeko on 2009-06-15
> **Sublime Porte said:**
> Well, those who have reservations about mono generally don't go around starting topics about it everywhere, however they will often respond to thread after thread of heaped praise for mono. So I think that point wasn't quite valid.

Whoaaa i love sci-fi!!! I see this is the one with the alternate inverted universe,no? :popcorn:

> 
My resevrations about mono spring from the fact that Microsoft has clearly threatened to bring Linux down by use of patents, and although it's not entirely clear yet how they could do that with mono, I really do think we should err on the side of caution, and avoid anything that could possibly assist them in carrying out that threat.

You are absolutely right! Therefor i suggest, nay **demand** that the Linux kernel be removed!!! it haz Microsoft patents!!! Microsoft said so!!! We **MUST** err on the side of caution, and avoid anything that could possibly assist them in carrying out that threat. </do-i-really-need-to-add-a-sarcasm-tag-?>

---

### Post by zekopeko on 2009-06-15
> **lykwydchykyn said:**
> 
I think the most unfortunate part of Jo's essay is how much of it is devoted to spurious ad-hominem against the so-called "anti-mono" crowd.  I don't think there's a movement, cause, or political/social/religious ideology out there that doesn't contain at least some small-but-vocal contingent of slavering moronic cretins who can do no better than parrot superstitious dogma with their fingers in their ears.  But that doesn't automatically invalidate the movement/cause/ideology itself.  Bringing it up was pure blather.

from a casual observation in mono threads and beyond i find it fascinating how easy it is to find an ignorant,self-righteous anti-mono crowdie(my singular of crowd. /me feels lingually mischievous), and on the other hand, how easy it is to find a intelligent,facts-supported,far-more-polite,far-more-helpful proponent of mono.

---

### Post by lykwydchykyn on 2009-06-15
> **zekopeko said:**
> from a casual observation in mono threads and beyond i find it fascinating how easy it is to find an ignorant,self-righteous anti-mono crowdie(my singular of crowd. /me feels lingually mischievous), and on the other hand, how easy it is to find a intelligent,facts-supported,far-more-polite,far-more-helpful proponent of mono.

You say so, but I am sure someone with a different view would say otherwise.  We tend to notice idiots who disagree with us more than we notice idiots who agree with us.  

And in any case, it does not matter at all because it does not invalidate the original ideology.  Ideas are not right or wrong on the basis of how many eloquent, informed people believe in them.

---

### Post by billgoldberg on 2009-06-15
> **UbuKunubi said:**
> AS far as Im concerned I have python and C++, so why yet another language? Whatever reasons others give I see no reason for it.



At least pretend to have read the article before posting.

The article says that Mono is up to 100 times faster than python in some benchmarks.

That alone makes it worth using instead of python.

---

### Post by bakedbeans4life on 2009-06-15
If this has passed me by then I apologise.

Can Microsoft sue Mono under any circumstances?

The answer should be a simple yes or no. 

I have yet to hear an official answer from Microsoft or the Mono developers on this issue. 

No hyperbole, yes or no?

---

### Post by zekopeko on 2009-06-15
> **bakedbeans4life said:**
> If this has passed me by then I apologise.

Can Microsoft sue Mono under any circumstances?

The answer should be a simple yes or no. 

I have yet to hear an official answer from Microsoft or the Mono developers on this issue. 

No hyperbole, yes or no?

let's see... oh i know what you are trying to do! you are expecting a simple answer so that you can point to it and say "Look, I told you so". I will answer it if you will answer mine with a simple yes or no: "Do you still beat your wife?"

---

### Post by zekopeko on 2009-06-15
> **lykwydchykyn said:**
> You say so, but I am sure someone with a different view would say otherwise.  We tend to notice idiots who disagree with us more than we notice idiots who agree with us.  

And in any case, it does not matter at all because it does not invalidate the original ideology.  Ideas are not right or wrong on the basis of how **many eloquent, informed people believe in them**.

But having eloquent and informed people sure helps ones arguments, does it not? Or do you prefer ignorant , ill-informed debates?
The essence of FLOSS is meritocracy with a dash of democracy. Ideas should be valued by merit not by angry peasants with pitchforks and torches.
Having F-spot and Tomboy in Ubuntu by default is a perfect example of meritocracy in action.

---

### Post by lykwydchykyn on 2009-06-15
> **bakedbeans4life said:**
> If this has passed me by then I apologise.

Can Microsoft sue Mono under any circumstances?


Microsoft can sue anyone it likes any time for any reason.  The question is whether it can win and what the fallout would be.  And that's more or less the substance of the debate, as I understand it.

---

### Post by bakedbeans4life on 2009-06-15
> **zekopeko said:**
> let's see... oh i know what you are trying to do! you are expecting a simple answer so that you can point to it and say "Look, I told you so". I will answer it if you will answer mine with a simple yes or no: "Do you still beat your wife?"

Personal insults now, of a sort.

A concise and succinct answer to the question posed would have sufficed.

Is it not forthcoming?

---

### Post by lykwydchykyn on 2009-06-15
> **zekopeko said:**
> But having eloquent and informed people sure helps ones arguments, does it not?


Only weakly and circumstantially.  But since there is no proof (only blatantly biased "observations") that the "anti-mono" crowd has significantly more idiots than the "pro-mono" crowd, why does it matter?

> 
 Or do you prefer ignorant , ill-informed debates?

That should be obvious, considering my whole initial point was to criticize the amount of unfounded ad hominem assertions in Jo's article.

Do you think that ad-hominem remarks constitute intelligent, informed debate?

> 
The essence of FLOSS is meritocracy with a dash of democracy. Ideas should be valued by merit not by angry peasants with pitchforks and torches.

I concur, but that cuts both ways in this case.  Simply declaring your opponent an angry mob of non-contributors doesn't make the valid bits of their argument go away.

> 
Having F-spot and Tomboy in Ubuntu by default is a perfect example of meritocracy in action.

I have not used either (not because they are mono, but because I'm using Kubuntu and never took notice of those apps), so I couldn't say.  Like I said, I'm not worried about using mono apps, I'm just not sure that I would choose to work with it because of the controversy.  I am not arguing that mono is either good or bad, just that this particular essay brought very little intelligence to the debate.

---

### Post by Regenweald on 2009-06-15
> **Sef said:**
> Jo Shields, a member of the Debian Mono Group, Debian CLI Applications Team, and Debian CLI Libraries Team and also a Ubuntu MOTU, has written an article [in favor of Mono]("http://blog.linuxtoday.com/blog/2009/06/why-mono-is-des.html").

It was a valiant attempt Sef, but even **this** thread is rapidly going downhill. 
Even though i understand the reservations of the anti-mono crowd,  my hypothetical: mono snowballs in development popularity and nearly the entire desktop is mono based, Microsoft then swoops in with litigation to cripple the desktop. A vala porting sprint ensues.

I still have faith in the development community not to take steps that could ultimately lead to crippling the userland environment. as for Vala, I hope it matures rapidly and proves itself a viable FOSS development platform.

With the python vs topic, Python seems to be an amazing development platform but i have C++ programs in wine(utorrent) that run circles around their python counterparts(deluge) interms of memory usage. I'm not a dev and i know that there are hundreds if not thousands of reasons that python is THE choice, but it is not the fastest available.

In the meanwhile, I love docky, and look forward to the c++ implementation of compiz.

---

### Post by bakedbeans4life on 2009-06-15
> **bakedbeans4life said:**
> If this has passed me by then I apologise.

Can Microsoft sue Mono under any circumstances?

The answer should be a simple yes or no. 

I have yet to hear an official answer from Microsoft or the Mono developers on this issue. 

No hyperbole, yes or no?

zekopeko (and those of his or her ilk) seem to take exception to this question, is it that outlandish?

YES OR NO?

---

### Post by Closed_Port on 2009-06-15
> **bakedbeans4life said:**
> zekopeko (and those of his or her ilk) seem to take exception to this question, is it that outlandish?

YES OR NO?

Like with any other piece of software MS can sue about it. So the question of weather MS can sue about it or not doesn't really make much sense.

I think the issue at hand is if the likelyhood of MS suing about Mono and succeeding is bigger than with other free software.

---

### Post by chips24 on 2009-06-15
what about smoking frogs. yeah. in a pipe.
dried frog guts..
 
 
or making ink from beetle shells.

---

### Post by zekopeko on 2009-06-15
> **Closed_Port said:**
> I think the issue at hand is if the likelyhood of MS suing about Mono and succeeding is bigger than with other free software.

not true. i don't know of any patents that have been identified as being implemented in mono.
what i do know is that MS has patent for [XPCOM]("http://en.wikipedia.org/wiki/XPCOM"). Two of the prominent users in FLOSS are Firefox (and derivatives) and OO.org.
So far more likelier scenario is FF and OO.org crashing and burning then mono.

---

### Post by zekopeko on 2009-06-15
> **bakedbeans4life said:**
> zekopeko (and those of his or her ilk) seem to take exception to this question, is it that outlandish?

Certainly it's outlandish since i don't want to post something that can be used as cheap FUD ammo. Read Jo Shields post. The answer is provided.

And you took exception to my question: "Do you still beat your wife/husband?". YES OR NO?

---

### Post by directhex on 2009-06-15
> **zekopeko said:**
> let's see... oh i know what you are trying to do! you are expecting a simple answer so that you can point to it and say "Look, I told you so". I will answer it if you will answer mine with a simple yes or no: "Do you still beat your wife?"

C'mon, dude, that's pretty low. Take the higher ground. Me, I'm gleefully hoping that people have a read of [http://opensourcetogo.blogspot.com/2009/06/when-zeal-becomes-zealotry-tawdry-tale.html](http://opensourcetogo.blogspot.com/2009/06/when-zeal-becomes-zealotry-tawdry-tale.html) rather than my own post. And not just because I've more than exceeded my monthly webhost bandwidth limit.

---

### Post by Closed_Port on 2009-06-15
> **zekopeko said:**
> no true. 

Just to clear this up. I said or meant to say that it is the relevant question that should be discussed. I did not say that it actually was the case that mono is more vulnerable than other software to a MS patent threat. I honestly don't know.

---

### Post by Closed_Port on 2009-06-15
> **directhex said:**
> [http://opensourcetogo.blogspot.com/2009/06/when-zeal-becomes-zealotry-tawdry-tale.html](http://opensourcetogo.blogspot.com/2009/06/when-zeal-becomes-zealotry-tawdry-tale.html) rather than my own post. And not just because I've more than exceeded my monthly webhost bandwidth limit.
Wow, thanks for posting this. I hadn't read it and it is disturbing, to say the least.

---

### Post by zekopeko on 2009-06-15
> **lykwydchykyn said:**
> Only weakly and circumstantially.  But since there is no proof (only blatantly biased "observations") that the "anti-mono" crowd has significantly more idiots than the "pro-mono" crowd, why does it matter?

I don't know why this didn't pop in my head earlier. In the civilized world the burden of proof is on the accusers. The best "proof" the anti-mono has is weak and circumstantial.  

> 
That should be obvious, considering my whole initial point was to criticize the amount of unfounded ad hominem assertions in Jo's article.

Ad hominem means you are attacking the person not his argument. You probably read the wrong blog post since the WHOLE post Jo posted is about dismantling their "solid proof". And the part of your alleged ad hominem attack against the anti-mono crowd is unfounded since he simply stated that some people posting on boycottnovell appear like raving lunatic. And i would agree. but then zealots are sometimes so cute :)

> 
Do you think that ad-hominem remarks constitute intelligent, informed debate?

No ad hominem attacks were made.

> 
I concur, but that cuts both ways in this case.  Simply declaring your opponent an angry mob of non-contributors doesn't make the valid bits of their argument go away.

It just makes them irrelevant. What meritorious thing did they bring to the table? And their "arguments" have been either beaten, or cast in the abyss of doubt. When people come to the ubuntu-devel-discuss list and demand mono removed without providing a migration path and new non-mono apps to replace the one's that would be lost, and get shoot down by people that provide their time to Ubuntu development, shows how far this people are from the essence of FLOSS. And don't try to say that this is only a minority of anti-mono crowd. For every quasi-intelligent anti-mono post there is a sea of ill-informed (usually by the same post they are commenting) comments.    

> 
I have not used either (not because they are mono, but because I'm using Kubuntu and never took notice of those apps), so I couldn't say.  Like I said, I'm not worried about using mono apps, I'm just not sure that I would choose to work with it because of the controversy.  I am not arguing that mono is either good or bad, just that this particular essay brought very little intelligence to the debate.

Try re-reading the essay. You obviously missed huge part's of it. Try to read it without your mono skepticism and with understanding that software patents can attack any software. Be it mono or something else.

---

### Post by zekopeko on 2009-06-15
> **directhex said:**
> C'mon, dude, that's pretty low. Take the higher ground. Me, I'm gleefully hoping that people have a read of [http://opensourcetogo.blogspot.com/2009/06/when-zeal-becomes-zealotry-tawdry-tale.html](http://opensourcetogo.blogspot.com/2009/06/when-zeal-becomes-zealotry-tawdry-tale.html) rather than my own post. And not just because I've more than exceeded my monthly webhost bandwidth limit.

Agreed. I overstepped civil discourse. My apologies. Will try to behave ;)

And that article is disturbing.

---

### Post by Sublime Porte on 2009-06-15
> With the python vs topic, Python seems to be an amazing development platform but i have C++ programs in wine(utorrent) that run circles around their python counterparts(deluge) interms of memory usage.

I must say it's quite a while since I've used utorrent, but when I did, it was a rather barebones client. Deluge is pretty full featured, so the comparison is just ridiculous.

---

### Post by zekopeko on 2009-06-15
> **Sublime Porte said:**
> I must say it's quite a while since I've used utorrent, but when I did, it was a rather barebones client. Deluge is pretty full featured, so the comparison is just ridiculous.

utorrent is probably the best full featured client. it has an extremely small footprint, rss support, custom labels and everything you might expect from a torrent client.

---

### Post by Regenweald on 2009-06-15
> **Sublime Porte said:**
> I must say it's quite a while since I've used utorrent, but when I did, it was a rather barebones client. Deluge is pretty full featured, so the comparison is just ridiculous.

Not picking a fight here, but when i started using deluge over transmission last year, certain standard features that i came to take for granted in utorrent were missing in deluge. Only this year has deluge finally caught up, and in doing so has come to resemble utorrent more and more. I consider them equally feature full. I use them both and in both windows and wine utorrent is a faster lighter client. I consider speed relative though, everyone's router/network is different.

---

### Post by handy on 2009-06-15
> **lykwydchykyn said:**
> 
I think the most unfortunate part of Jo's essay is how much of it is devoted to spurious ad-hominem against the so-called "anti-mono" crowd.  I don't think there's a movement, cause, or political/social/religious ideology out there that doesn't contain at least some small-but-vocal contingent of slavering moronic cretins who can do no better than parrot superstitious dogma with their fingers in their ears.  But that doesn't automatically invalidate the movement/cause/ideology itself.  Bringing it up was pure blather.


One way of succinctly describing the problem in the Mono (amongst so many others) debate, is that some people's minds are fundamentally convergent & others are divergent.

Personally I prefer divergent, as it has a LOT more freedom & welcomes new ideas/experiences. It is also NOT prone to telling other people what they should & shouldn't do/think/believe. :)

---

### Post by Sublime Porte on 2009-06-16
> Only this year has deluge finally caught up, and in doing so has come to resemble utorrent more and more. I consider them equally feature full.

Deluge had a pretty major rewrite recently. It has plenty of features utorrent does not. Daemon mode, with the ability to connect remotely is one of the most notable features that came about in the new rewrite. utorrent has nothing of the kind. utorrent, from my understanding specialises in being lean and lite, not featureful.

> I consider speed relative though, everyone's router/network is different.

I think we were talking about the speed of the app itself, not it's networking speed. As this was relating back to whether python is suitable for writing apps, which I certainly think it is. Sure there's apps which you want to be lite and fast, but there's others in which it's not an issue.

---

### Post by -grubby on 2009-06-16
> **UbuKunubi said:**
> AS far as Im concerned I have python and C++, so why yet another language? Whatever reasons others give I see no reason for it.

Because other people prefer developing in different languages than you?

I was personally thinking about learning C#, after I read it had a garbage collector /and/ was quite a bit faster than Python.

---

### Post by handy on 2009-06-16
> **grubby- said:**
> Because other people prefer developing in different languages than you?

I was personally thinking about learning C#, after I read it had a garbage collector /and/ was quite a bit faster than Python.

No way buddy, you are not allowed to make free choices around here, if your not careful I'll report you!

---

### Post by Joe_Bishop on 2009-06-16
Tomboy is really badly integrated with the gnome desktop. Since gnote looks almost exacty the same, takes less memory and faster in general, is it good idea to replace tomboy with gnote?

---

### Post by -grubby on 2009-06-16
> **handy said:**
> no way buddy, you are not allowed to make free choices around here, if your not careful i'll report you!

I didn't mean it! I'll submit! I'll submit!

---

### Post by gnomeuser on 2009-06-16
> **billgoldberg said:**
> At least pretend to have read the article before posting.

The article says that Mono is up to 100 times faster than python in some benchmarks.

That alone makes it worth using instead of python.

Benchmarking is tricky at best. Being 100 times faster at some operation in a benchmark doesn't automatically translate into being 100 times faster in any case the user will experience in the real world. Benchmarks should be taken in context. 

Generally though, Mono performs really well and each release of Mono has the added advantage of not regressing performance (as a whole, individual operations might regress but as a rule Mono only becomes faster as releases progress). This means your average Mono based program will take advantage of these optimizations without even a recompile or an update. Update Mono and your whole suite of applications perform better.

There are also interesting enhancements that have specialized applications where performance will increase radically such as mono.simd. A project the Mono project have expressed an interest in polishing up and taking to ECMA so that even the Microsoft reference implementation of .NET will get the benefits.

---

### Post by zekopeko on 2009-06-16
> **Sublime Porte said:**
> Deluge had a pretty major rewrite recently. It has plenty of features utorrent does not. Daemon mode, with the ability to connect remotely is one of the most notable features that came about in the new rewrite. utorrent has nothing of the kind. utorrent, from my understanding specialises in being lean and lite, not featureful.

not true. utorrent has web interface (ie. daemon mode) and you also have uRemote: [http://uremote.blogspot.com/](http://uremote.blogspot.com/)

---

### Post by gnomeuser on 2009-06-16
> **zekopeko said:**
> not true. utorrent has web interface (ie. daemon mode) and you also have uRemote: [http://uremote.blogspot.com/](http://uremote.blogspot.com/)

Incidently the utorrent WebUI has been ported to have a [MonoTorrent backend](http://monotorrent.blogspot.com/2008/03/i-got-some-amazing-news-just-few.html).

---

### Post by Sublime Porte on 2009-06-16
> utorrent has web interface (ie. daemon mode)

Web interface is _not_ daemon mode, nor anything remotely (pun intended) like it.

Can I run utorrent on a headleass server with no gui? I doubt it.

---

### Post by Gourgi on 2009-06-16
> **Joe_Bishop said:**
> Tomboy is really badly integrated with the gnome desktop. Since gnote looks almost exacty the same, takes less memory and faster in general, is it good idea to replace tomboy with gnote?

i don't really care about the switch but what you mean "badly integrated" ?
what are the pros of gnote?

Also tomboy presented a cool sync feature recently [http://automorphic.blogspot.com/2009/05/tomboy-0151-release-brings-new-online.html](http://automorphic.blogspot.com/2009/05/tomboy-0151-release-brings-new-online.html) with *Snowy*.

---

### Post by tgpraveen on 2009-06-16
well ubuntu plans to not use that online sync feature but rather integrate with ubuntu one. so we can do with gnote also.

but currently tomboy is ahead in terms of features maybe in the future.

also the thing to be considered is that we seem to be a very pro mono distro and recently we moved to banshee so i doubt we will replace tomboy.

though maybe if every one else does change, then tomboy devel ceases then only is there a chance of replacing.

---

### Post by super.rad on 2009-06-16
> **Joe_Bishop said:**
> Tomboy is really badly integrated with the gnome desktop. Since gnote looks almost exacty the same
If it looks almost exactly the same then wouldn't it be just as badly integrated?
Also does gnote have the same amount of features that tomboy does? Last time I had a look at gnote it had nowhere near as many.
Theres no point in replacing a program with one that has less features

---

### Post by tgpraveen on 2009-06-16
well ubuntu plans to not use that online sync feature but rather integrate with ubuntu one. so we can do with gnote also.

but currently tomboy is ahead in terms of features maybe in the future.

also the thing to be considered is that we seem to be a very pro mono distro and recently we moved to banshee so i doubt we will replace tomboy.

though maybe if every one else does change, then tomboy devel ceases then only is there a chance of replacing.

---

### Post by ghindo on 2009-06-16
Gnote will always, _always_ be behind Tomboy, since Gnote is merely a port of Tomboy, not really an original project.

---

### Post by tgpraveen on 2009-06-16
ohg that is not true if many devs feel that they want to deveol gnote then it will get enw features and have a development path of its own.
it does nott depen on tomboy it only used a port of it as a foundation base.
from here we can go anywhere.

---

### Post by directhex on 2009-06-16
Quoting from my own blog:

> IF Gnote can reach feature parity with Tomboy, and IF it remains smaller on disk and in RAM with those features it currently lacks, and IF it shows a clean bill of health for security and stability over a testing period longer than its one month on this Earth, and IF the desktop team are comfortable switching from an app with an upstream team to a one-man show, and IF the desktop team are comfortable going from an app which innovates to an app which emulates, then I think it’s pretty clear which app makes more sense on the default install CDs.

---

### Post by geojorg on 2009-06-16
+1 Nothing else to add.

---

### Post by DeadSuperHero on 2009-06-16
I just read this [here]("http://opensourcetogo.blogspot.com/2009/06/when-zeal-becomes-zealotry-tawdry-tale.html").

> We've seen Mark [Fink] before, more than a year ago, similarly stirring up the GNOME desktop-devel list. At that point, he was planning to write "a replacement for Tomboy" because "because Tomboy is poisoning GNOME distributions like Red Hat and Ubuntu with it's Microsoft patented **MONO** dependency crap". In support of his position, he pointed to articles on Roy Schestowitz's site, boycottnovell.com. Roy seems to have a similar dislike for Mono, although I have to say he's a lot more careful in his phrasing of things.

> It was a pretty pointless message, again referencing boycottnovell.com, and it got the expected reaction. Mark continued to escalate things even further, claiming that "the MONO camp has infiltrated canonical", and that people were "slandering roy schestowitz", Mark roundlt abused Miguel de Icaza, accusing him of "worship[ing] M$", of only starting GNOME because "because he couldn't get hired by M$" and of "splitting the Linux community", before going on to suggest that someone who expressed rational disagreement with this nonsense was a "typical M$ appologist [sic]", that "only stupid people who can't think for themselves fawn over MONO and follow it like a religion", that the forum moderators were "novell employees (or people who drink they're [sic] koolaid)", and so on.

> As I noted, Mark consistently points back to boycottnovell.com, trumpeting the cause espoused there by Roy Schestowitz, and in fact demanding at one point that Roy be made a moderator of ubuntu-devel to ensure "fairness". Mark gives every impression of being closely associated with Roy's cause and site.

With all this in mind, it seems that Roy is trying to distort and warp the Ubuntu community to follow his own personal agenda.

---

### Post by The Toxic Mite on 2009-06-16
> **Mr. Psychopath said:**
> I just read this [here]("http://opensourcetogo.blogspot.com/2009/06/when-zeal-becomes-zealotry-tawdry-tale.html").

<snip />

With all this in mind, it seems that Roy is trying to distort and warp the Ubuntu community to follow his own personal agenda.

Anti-Microsoft propaganda.

I just wish they would shut the hell up! :|

---

### Post by Icehuck on 2009-06-16
These people are pathetic, but hey we already knew that.

---

### Post by SuperSonic4 on 2009-06-16
I'm using Arch and KDE but he's just being an idiot again. Novell have made good contributions affecting all distros and continue to do so.

---

### Post by Daisuke_Aramaki on 2009-06-16
I used to visit a couple of sites at least once a day just to have an idea about the pile of crap that is being promoted online, just for some fun. But of late, boycott novell is the only place that puts out crap quite consistently, with every post actually. Looks like they are a bunch of overgrown men with the intellect of a five year old, and i feel sorry for all the five year olds.

---

### Post by directhex on 2009-06-16
I love how BN are spinning the official Technical Board statement that they don't see Mono as a risk factor ([https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028347.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028347.html)) as the 100% exact opposite

---

### Post by DeadSuperHero on 2009-06-16
A really insightful comment is on their latest article by some guy named Dave.

> Yes, they looked at it and found it is fine by them, and OSI, and FSF and RMS and GPL and Torvalds.
 “In short, at the moment, Mono is very well-maintained in Ubuntu and there appears to be no significant cause for concern over its IP situation”
 “Mono advances Microsoft (Windows, Visual Studio, etc.) at Ubuntu’s expense. Thus, it’s detrimental to everyone”
 we’ll providing more tools and methods and more ability for the many many Windows only developers to easily provide their apps for Linux is good for linux and good for the computing, and development environments in general.
If we were really concerned about patent liability, we would not use C at all, or anything else, after all, Linux (the same license as mono) grew from the proprietary world, as did GCC, emacs, Vim and so on.
 IMHO, if its good enough for the GPL, OSI, FSF, RMS and “those in the know”. then its ok with me. 
 Ater all is not RMS the spiritual leader of the FOSS movement who is very against proprietary systems, (even though he himself needed proprietary systems for his GCC development, ((kept quite)).. 
 Ofcourse, the highly technically literate FOSS users would find it trivial to remove it, yet for some reason its easier to defy RMS, FSF, GPL and so on to persue their own adjender.. 
 With total disregard to what are the long term implications that may affect the very viability of the FOSS movement.
 Especially, IF splinter groups continue to break and devalue the GPL, the very same license that binds the kernel and the FOSS community. 


Schestowitz then tries to just write off Dave's opinion by labeling him as a Microsoft shill:

> For the record, “Dave” is a nymshift  of “Darryl”, who is considered a Microsoft shill and got banned in Linux sites. 

---

### Post by Icehuck on 2009-06-16
The sad thing is most of the users here don't care what a few people are trying to do to their community.

---

### Post by DeadSuperHero on 2009-06-16
> **Icehuck said:**
> The sad thing is most of the users here don't care what a few people are trying to do to their community.

The truly horrifying aspect of it is just how far their hand goes into things like this.

---

### Post by Mr. Picklesworth on 2009-06-16
Because, of course, I don't know about 6 different Daves in my little corner of the world alone...

---

### Post by ddrichardson on 2009-06-16
> **Icehuck said:**
> The sad thing is most of the users here don't care what a few people are trying to do to their community.
This issue isn't fully understood by the majority of Ubuntu's users but that's hardly surprising given we're talking about a development platform and we've spent vast amounts of time and energy encapsulating new users from the underlying complexity.

---

### Post by bekind2thenoob on 2009-06-16
I'm a Dave :D

---

### Post by ddrichardson on 2009-06-16
> **bekind2thenoob said:**
> I'm a Dave :D
I can see this becoming the Linux community's version of "I'm Spartacus"

---

### Post by lykwydchykyn on 2009-06-16
> **Icehuck said:**
> The sad thing is most of the users here don't care what a few people are trying to do to their community.
To be fair, most users have no idea about this stuff.  And those that try to approach the topic with an open mind to both sides encounter a morass of he said/she said arguments, accusations of nymshifting, shilling, astroturfing, and conspiracy theories on top of conspiracy theories.  And that comes from BOTH SIDES.

Personally I'm not worried about Ubuntu shipping mono or mono applications.  I think FOSS and Linux are big enough to survive any real or imagined patent threats from one out of a dozen programming frameworks.

---

### Post by directhex on 2009-06-16
> **bekind2thenoob said:**
> I'm a Dave :D

[http://www.billythefish.com/mediac/400_0/media/Papa~Lazarou.jpg](http://www.billythefish.com/mediac/400_0/media/Papa~Lazarou.jpg) ?

---

### Post by ronacc on 2009-06-16
there is one overriding reason for some of us to prefer gnote , it is a port to c++ away from mono .

---

### Post by zekopeko on 2009-06-16
> **ronacc said:**
> there is one overriding reason for some of us to prefer gnote , it is a port to c++ away from mono .

and then there are most users that want something that "Just Works" (TM). Not to mention that Gnote is always lagging behind in implementation or is breaking compatibility.

---

### Post by ghindo on 2009-06-16
> **ronacc said:**
> there is one overriding reason for some of us to prefer gnote , it is a port to c++ away from mono .Most users presumably don't care what language a program is written in, only whether or not the program works well and the program has all the features the user wants.  Tomboy provides all of that; Gnote is left playing second fiddle.  If you want to use Gnote instead of Tomboy that of course is your prerogative, but it doesn't mean it's the best choice for the majority of users.

---

### Post by gnomeuser on 2009-06-16
Gnote brings nothing to the table currently of any technical nature, a suggestion to let it replace Tomboy is a suggestion to let inferior software prevail.

---

### Post by ronacc on 2009-06-16
by all means use which ever you think best suits your needs/wants . I was merely stating a personal preference .

---

### Post by Staz on 2009-06-16
> **Joe_Bishop said:**
> Tomboy is really badly integrated with the gnome desktop. 

I fail to understand you reasoning : Tomboy is really badly integrated in GNOME, so least replace it with a copy of it?

I also fail to understand how it's badly integrated since it was made for the GNOME desktop

> Since gnote looks almost exacty the same, takes less memory and faster in general, is it good idea to replace tomboy with gnote?
Gnote doesn't have all the features of Tomboy, the dev base and the momentum

---

### Post by Staz on 2009-06-16
> **tgpraveen said:**
> also the thing to be considered is that we seem to be a very pro mono distro and recently we moved to banshee so i doubt we will replace tomboy.
It's not about being pro mono or not it's about bringing the best free software to the user if they use mono or not it doesn't matter

---

### Post by DPic on 2009-06-16
> **Staz said:**
> It's not about being pro mono or not it's about bringing the best free software to the user if they use mono or not it doesn't matter

Maybe for you, but a lot of us do care about mono. I'm in full support of using Gnote instead. 

Fedora is concerned: [http://blog.internetnews.com/skerner/2009/06/fedora-is-concerned-about-mono.html](http://blog.internetnews.com/skerner/2009/06/fedora-is-concerned-about-mono.html)

and Microsoft could pull a Rambus: [http://www.channelregister.co.uk/2009/05/14/ftc_drops_rambus_antitrust_case/](http://www.channelregister.co.uk/2009/05/14/ftc_drops_rambus_antitrust_case/)

---

### Post by RAOF on 2009-06-16
> **DPic said:**
> Maybe for you, but a lot of us do care about mono. I'm in full support of using Gnote instead. 
...

And you're still perfectly welcome to remove Tomboy, F-Spot, and Banshee.

---

### Post by Staz on 2009-06-16
> **DPic said:**
> Maybe for you, but a lot of us do care about mono. I'm in full support of using Gnote instead. 

Fedora is concerned: [http://blog.internetnews.com/skerner/2009/06/fedora-is-concerned-about-mono.html](http://blog.internetnews.com/skerner/2009/06/fedora-is-concerned-about-mono.html)

and Microsoft could pull a Rambus: [http://www.channelregister.co.uk/2009/05/14/ftc_drops_rambus_antitrust_case/](http://www.channelregister.co.uk/2009/05/14/ftc_drops_rambus_antitrust_case/)

I think you misunderstood my post. I was just stating the fact that Ubuntu doesn't push a mono application especially because they are pro mono but because in a particular case an application A is better (in a certain context) than application B, which technologies theses application use being irrelevant in the comparison.

But like ROAR says theses are just default and you can remove them if you don't like them.

Lets not turn this thread in a mono trolling thread please.

---

### Post by zekopeko on 2009-06-16
> **Staz said:**
> Lets not turn this thread in a mono trolling thread please.

but,but... it's so easy!!! /s

---

### Post by ronacc on 2009-06-16
> **Staz said:**
> 

But like ROAR says theses are just default and you can remove them if you don't like them.

Lets not turn this thread in a mono trolling thread please.

I do , and please realise that it is not trolling when some of us express honestly felt concerns about mono , held for what we believe to be good reasons .

---

### Post by Staz on 2009-06-16
> **ronacc said:**
> I do , and please realise that it is not trolling when some of us express honestly felt concerns about mono , held for what we believe to be good reasons .

I wasn't calling anyone a troll but saying that continuing on this path may lead to trolling.

Ubuntu has already stated whether it's fine or not to include mono application in it and we should judge proposals by theses criterias.

You may not agree with them but this topic is not the right place to discuss this.

---

### Post by Vadi on 2009-06-16
+1! Mostly does the same stuff, but faster (as many people say) and uses less resources. I've switched full-time, and miss nothing.

---

### Post by starcannon on 2009-06-17
> **Mr. Psychopath said:**
> I just read this [here]("http://opensourcetogo.blogspot.com/2009/06/when-zeal-becomes-zealotry-tawdry-tale.html").







With all this in mind, it seems that Roy is trying to distort and warp the Ubuntu community to follow his own personal agenda.

After all the Sir Sane/Mr. Psychopath linsux.org posts here and on other sites, I'm really not sure whether to take this seriously, or whether its just a fork of your fsdaily and boycottnovell raid that is currently under way. Perhaps you can clarify before I spend any time researching your accusation?

---

### Post by SKLP on 2009-06-17
Oh noes! Yet another mono thread...

First, I do not understand what you mean by "badly integrated". Both are gtk apps...

Secondly, Gnote should only replace Tomboy *IF* it becomes MORE featurefull, more stable, and so on. 

That said, I seriously do *NOT* believe that writing a note app in C or C++ is a good idea in any way. If the anti-mono crowd wanted to make a note app then maybe they should have used their *beloved* Vala ( Which btw is very much *inspired* by the company you guys seem to hate namely Microsoft), or simply Python or Java(with java-gnome). I would have chosen Python or Java, but rather C# of course ;-) Like I said though, I'm open to moving to Gnote anyways if it was clearly superior overall.

---

### Post by Screwdriver0815 on 2009-06-17
can someone explain all this to me?

I have to admit, I tried to read all this boycott novell stuff but I couldn't because 

1. I did not understand what they want

2. it sounded like FUD to me

So what I understood is that Novell has signed this interoperation-deal with Microsoft and therefore they have also some shares (or what ever) in this Silverlight, which is a Microsoft-Flash? Is it like that?
And now, there is a programming language Mono, which is created by Microsoft and Novell uses it?
And Tomboy and Banshee are developed in Mono... this is the reason why these Boycott Novell guys say that Linux will be poisoned?

So, what is the issue and what makes all this dangerous? Maybe all this is obvious but I do not understand all this. Thats why: could someone explain?

Thanks!

---

### Post by gnomeuser on 2009-06-17
> **DPic said:**
> 
Fedora is concerned: [http://blog.internetnews.com/skerner/2009/06/fedora-is-concerned-about-mono.html](http://blog.internetnews.com/skerner/2009/06/fedora-is-concerned-about-mono.html)

Categorically no.. Fedora as a project is not concerned about Mono patents. It is treated as a second class citizen yes but the stance on the legality is that Mono is covered by the OIN and if there was _any_ cause for concern it would be examined by Red Hat Legal and action would be taken. However Red Hat Legal has deemed that Mono is not a problem and thus it is included, as well as many programs using Mono such as Tomboy and Banshee.

The reason Gnote rather than Tomboy is on the CD is mainly the fact that it is smaller, since the Fedora CD doesn't have Mono on it in the first place the required dependency chain for Tomboy would be much larger. Especially since Fedora hasn't yet enabled the Mono 2 migration patches to reduce size which Ubuntu and Debian have whipped up.

Red Hat say they are concerned, but solely about shipping Mono in their own RHEL product not Fedora. They enforce this desire to keep RHEL Mono free in Fedora by treating Mono as a second class citizen, even down to people such as Bill Nottingham saying that discrimination based on language choice is not at all objectionable. However it is to be expected that a company which invests as much money in Java as Red Hat has little desire to support a competing, and in some ways technically superior, product (Mono) in their enterprise offerings. The whole endeavor would serve to undermine their current investments.

Now please stop using Fedora as part of your crusade, it's as tiresome as it is uninformed. The article you cite even goes so far as to say there is speculation of removing Mono from Fedora, something which is most definitely not the case. How would I know you wonder, well I pretty much run the Fedora Mono SIG and we have not been appraised of any such change nor has any such debate been had on the mailing lists. I have personally encouraged the anti-mono crowd within Fedora to propose such a "Feature" so we could have the debate once and for all but none have dared draft it up because they know Red Hat Legal already okayed Mono after it entered the protective realm of the OIN. By failing to do fact checking, you further this myth that Mono is somehow in grave danger of being removed from Fedora due to non-specific threats.

Please understand that by spreading this uninformed outright lie you are making life unduly hard for people actually working on Mono to enhance the Linux user experience for no good reason. You force us to defend our work and spend time dispelling these myths, time which could have been used much more productive. Time that would not bring developers closer to burn out. You are hurting me, my fellow Mono maintainers and Linux, please stop.

- David Nielsen

---

### Post by directhex on 2009-06-17
> **Screwdriver0815 said:**
> can someone explain all this to me?

I have to admit, I tried to read all this boycott novell stuff but I couldn't because 

1. I did not understand what they want

2. it sounded like FUD to me

So what I understood is that Novell has signed this interoperation-deal with Microsoft and therefore they have also some shares (or what ever) in this Silverlight, which is a Microsoft-Flash? Is it like that?

And now, there is a programming language Mono, which is created by Microsoft and Novell uses it?
And Tomboy and Banshee are developed in Mono... this is the reason why these Boycott Novell guys say that Linux will be poisoned?

So, what is the issue and what makes all this dangerous? Maybe all this is obvious but I do not understand all this. Thats why: could someone explain?

Thanks!

Moonlight:

1) Silverlight is Microsoft's Flash competitor. Moonlight is Novell's Free Software implementation, which is done with approval from Microsoft (including providing a full official test suite to developers and licensed codecs to users)

2) When the collaboration in (1) was arranged, Microsoft offered a promise not to sue for patent-related issues anyone who obtains Moonlight from Novell, but noes not make any clear promises to those using distribution packages.

Mono:

3) Mono is an implementation of two standards, ECMA335 and ECMA334, which come from Microsoft, and are implemented by Microsoft as the .NET Framework.

4) Mono was started in 2001, 5 years before any Novell/Microsoft dealings

5) In 2006, Novell and Microsoft signed a deal promising not to sue each others' customers for patent infringements in their products. They make no promises not to sue each other, and no list of patents has ever been shown to anyone. Novell have stated in public that they aren't aware of any patent infringements in their products.

6) Some Free Software developers have written Free apps using Mono rather than alternatives such as Java. Banshee or Tomboy are examples.

7) Many (most) distributions have shipped some of the apps from (6) optionally or by default.

Shared:

7) Some people in the community see (5) as proof that (7), (3) and (2) are legally risky. They see (5) as a sign that the "community" is "poisoned" by Novell.

I think that articulates the matter in a neutral way.

Different distributions have different approaches to the "patent risk" question. Debian's approach and Ubuntu's approach are pretty much the same - assume there are no patent problems in an app until a demonstrable case of protected infringement is shown. For example, in the Mono case, there are no publicly known patent infringements. Even if some were to be revealed, Ubuntu and Debian would assume that the patent was not being enforced (as is the case for most patents) until shown otherwise, e.g. by contact from a patent holder or being shown details of a legal case surrounding the patent in question. See [https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028347.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-June/028347.html) for the Ubuntu Technical Board (highest rank in the Ubuntu governance structure) ruling on the matter.

---

### Post by DeadSuperHero on 2009-06-17
> **starcannon said:**
> After all the Sir Sane/Mr. Psychopath linsux.org posts here and on other sites, I'm really not sure whether to take this seriously, or whether its just a fork of your fsdaily and boycottnovell raid that is currently under way. Perhaps you can clarify before I spend any time researching your accusation?

While I do admit that many of the things I say are unkind, I speak the truth for the benefit of the community. There are a lot of very disturbing things about BN that could hurt this Linux community even more by dividing developers and users down the middle.

Perhaps you don't take kindly to my Sir Sane persona, but I assure you that it is merely a character. I've blogged many good things about Ubuntu on [my blog]("http://seanrtilley.blogspot.com") and recently [Linux.com.]("http://linux.com/community/blogs/The-Next-Step-Forward-When-Will-GNU-Linux-Have-REAL-Commercial-support-.html")

---

### Post by gnomeuser on 2009-06-17
> **bekind2thenoob said:**
> I'm a Dave :D

I'm David, but never ever Dave.. does that count I wonder?

---

### Post by Screwdriver0815 on 2009-06-17
thanks Directhex for the explanation. 

So if I understand right, from the point of view of the Microsoft - Novell deal, only users of OpenSuse and SLED are 100% surely safe in terms of Microsoft sueings regarding Moonlight?

So my sight of the things is: if Microsoft sues a Distro like Ubuntu or Debian because they use this Moonlight... Ubuntu resp. Debian just send out an Update which removes Moonlight from each users system. Thats it? So asking generally: whats the problem? Why does Novell poison the Linux community with that?
Because the users of OpenSuse and SLED do not have to remove Moonlight? If Novell does such a Deal with Microsoft, they can not speak for all other Distros so they only can do a Deal on their own for themselves. And as Novell is a independend company they are free to do what they want, I think.

But: who is using Moonlight anyway? I never heard about this.

Regarding the Mono stuff it is still a little bit confusing for me. 
So Novell and Microsoft promised that they will not sue each others customers but if they want to sue each other, then they can do it. Its strange... but anyway.
But what has this to do with the Moonlight deal? If Microsoft and Novell want to fight each other on court, they only can do it regarding Mono as far as I understand this, because in the Silver/Moonlight deal they agreed not to sue each other for that. 

But anyway, if Microsoft sues Novell or the users of Mono in general, they also could remove the apps, which are written in Mono. Thats it.
And the thing with Novell being free to do deals as much as they want and not being in charge for the whole Linux community is still valid, I think.

If we now would boycott Novell, which advantage would we get from this? Isn't Ubuntu or Debian responsible for their respective stuff? So if Debian or Ubuntu put in a Novell app, Moonlight and also one which is written in Mono... then they are in charge. But Novell can not say to the Debian/ Ubuntu guys: "you are not allowed" as long as the app's are licensed under the GPL, I think.

Its still strange to me that Novell should be the only one who is guilty.

And what are the consequences, beside of FUD and splitting the community? Which advantage do we have from this?

---

### Post by gnomeuser on 2009-06-17
> **Screwdriver0815 said:**
> 
But: who is using Moonlight anyway? I never heard about this.


Any site that uses Silverlight will, eventually, work with Moonlight so you might one day be a user if you want to access content on such pages. However currently only Silverlight 1 is fully supported and Silverlight 2 (and upcoming SL3) are only partially supported with full support expected later this year. Meaning right now, most of the SL content out there doesn't really work with Moonlight. 

However the development schedule has been quite impressive and results are quick to surface. The team has been extremely quick to catch up and even now  that SL3 is in beta they have some of the features ready in Moonlight today.

Another place you are likely to see Moonlight will be on your desktop. It is a very nice tool for building next generation applications with all that entails of bling and such. Aaron Bockover (the Banshee lead developer) will have 2 presentations at this years GUADEC later this month on building desktop 2.0 using Moonlight. One of the examples he is supposedly going to show off will be a Moonlight frontend for Banshee. It should blow your socks off.

---

### Post by handy on 2009-06-17
You guessed it, I think that the majority of the anti-mono crowd are running headless servers too. (Couldn't resist) :)

Live & let live, & let time (=experience) determine the next step.  Why shut down the development of something when it is immature?  Let it grow up & show us what its got for us, if it is a failure, boy will there be some lessons learned, apart from the fact that it will be modified & feed other FOSS projects.

PEACE.

---

### Post by MountainX on 2009-06-17
I want to remove mono completely from Ubuntu 9.04. What is the best way to do this?

I can replace Tomboy with Gnote.
What is the replacement for F-Spot?
Is there anything else I will need to replace?

---

### Post by frodon on 2009-06-17
I love gthumb as photo manager, it is a possible replacement.

---

### Post by Dragonbite on 2009-06-17
> **MountainX said:**
> I want to remove mono completely from Ubuntu 9.04. What is the best way to do this?

I can replace Tomboy with Gnote.
What is the replacement for F-Spot?
Is there anything else I will need to replace?

F-Spot? you could use [LIST]
[*]gThumbs, but it isn't as featured as F-Spot
[*]digiKam, but that is built for KDE and will pull in some libraries (and look awkward)
[*][[COLOR="Blue"]Google Picasa[/COLOR]]("http://www.google.com/picasa/").. basically the best bet at this point but you'll have to download and install it from the website, it isn't in the repositories. This is what I use at this time in Gnome.
[/LIST]

The big Mono apps are Tomboy (notes), Beagle (search), F-Spot (picture management), and Banshee (music/media player). I don't think they've included Beagle lately or Banshee.

---

### Post by MountainX on 2009-06-17
Thanks!

Picasa for Linux looks like a good choice to replace F-Spot.

What packages do I need to remove to remove all of mono? Or should I just use Synaptic?

---

### Post by Dragonbite on 2009-06-17
> **MountainX said:**
> Thanks!

Picasa for Linux looks like a good choice to replace F-Spot.

What packages do I need to remove to remove all of mono? Or should I just use Synaptic?

See what Synaptic comes up with. Plus I think in the properties you can list what files/applications it depends on though the dangerous thing is if anything else uses those.

I don't know if Synaptic is smart enough to remove all unused libraries as well or not. "Completely Remove" only removes the configuration files too as far as I can tell.

---

### Post by directhex on 2009-06-17
Jaunty and earlier: mono-common and libmono0

Additionally, on Jaunty, due to a packaging bug, you need to manually remove /usr/lib/mono AFTER REMOVING THE ABOVE TWO PACKAGES, NOT BEFORE.

---

### Post by MountainX on 2009-06-17
> **directhex said:**
> Jaunty and earlier: mono-common and libmono0

Additionally, on Jaunty, due to a packaging bug, you need to manually remove /usr/lib/mono AFTER REMOVING THE ABOVE TWO PACKAGES, NOT BEFORE.

Thanks!

---

### Post by zekopeko on 2009-06-17
> **Sublime Porte said:**
> Web interface is _not_ daemon mode, nor anything remotely (pun intended) like it.

Can I run utorrent on a headleass server with no gui? I doubt it.

i doubt that windows users (ie. those using utorrent - a windows applications) run headless windows servers...

---

### Post by Viva on 2009-06-17
I'm sick of this boycott Novell ********. I'm not a fan of Mono and think it is overrated, but these idiots are scaring potential linux users with their conspiracy theories.

---

### Post by sydbat on 2009-06-17
> **Mr. Picklesworth said:**
> Because, of course, I don't know about 6 different Daves in my little corner of the world alone...[http://www.youtube.com/watch?v=jmQRmHgExV0](http://www.youtube.com/watch?v=jmQRmHgExV0)

---

### Post by DeadSuperHero on 2009-06-19
I saw this in the Digg upcoming section, figured I'd share it.

[http://digg.com/linux_unix/Schestowitz_tries_to_get_Canonical_people_fired_over_mono/who](http://digg.com/linux_unix/Schestowitz_tries_to_get_Canonical_people_fired_over_mono/who)

---

### Post by SKLP on 2009-06-19
> **gnomeuser said:**
> Any site that uses Silverlight will, eventually, work with Moonlight so you might one day be a user if you want to access content on such pages. However currently only Silverlight 1 is fully supported and Silverlight 2 (and upcoming SL3) are only partially supported with full support expected later this year. Meaning right now, most of the SL content out there doesn't really work with Moonlight. 

However the development schedule has been quite impressive and results are quick to surface. The team has been extremely quick to catch up and even now  that SL3 is in beta they have some of the features ready in Moonlight today.

Another place you are likely to see Moonlight will be on your desktop. It is a very nice tool for building next generation applications with all that entails of bling and such. Aaron Bockover (the Banshee lead developer) will have 2 presentations at this years GUADEC later this month on building desktop 2.0 using Moonlight. One of the examples he is supposedly going to show off will be a Moonlight frontend for Banshee. It should blow your socks off.
Silverlight/Moonlight seems to be a pretty cool piece of technology. You state that any SL content will work in moon, but at present (afaik) there are no announced plans for moonlight to get support for the microsoft DRM.

It is a bit sad that Microsoft decided to put DRM support in Silverlight, as if they hadn't Moonlight could have become a very nice cross-platform alternative to Flash. 
If they eventually get DRM support in moonlight it will require a blob from Microsoft so it won't be freer, nor more portable, than Flash is today. And Flash (I don't like flash at all for the record) content does not seem to be DRM protected today for the most part, so for that content it is at least possible to make a LEGAL open source player. The reason flash content is not usually DRM proteted is probably only for compability with Flash 9 and whatnot. And in a while, when Flash 10 is popular enough, both Flash and Silverlight would become solutions that provide DRM. So it will be impossible to implement legal players to both in a 100% free software manner.

So the best solution to the web video situation is probably HTML5 <video> as it does not support DRM at all.

It would have been nice to be able to use C# and Python instead of client-side JavaScript, though.

---

### Post by sakabato on 2009-06-19
Where is **neighborlee **guy ?

---

### Post by Sef on 2009-06-23
Wikipedia article on [Mono]("http://en.wikipedia.org/wiki/Mono_%28software%29").  For those like me, who haven't understood what the fuss is about, read it.

From the article:

> Mono consists of three groups of components:
 
[LIST=1]
[*]Core components
[*]Mono/Linux/GNOME development stack
[*]Microsoft compatibility stack.
[/LIST]
> Mono’s implementation of those components of the .NET stack not submitted to the [ECMA]("http://en.wikipedia.org/wiki/ECMA") for standardization has been the source of patent violation concerns for much of the life of the project. In particular, discussion has taken place about whether Microsoft could destroy the Mono project through patent suits.

---

### Post by DeadSuperHero on 2009-06-23
Most of it is a bunch of hubub from the Boycott Novell community.

RMS actually approves of it in this video.

[Stallman about Mono (Padova 2007)](http://www.youtube.com/watch?v=oqpLWzPRfvU#lq-hq)

---

### Post by Grant A. on 2009-06-24
This really needs to be pinned, IMHO.

---

### Post by Tews on 2009-06-24
> **Grant A. said:**
> This really needs to be pinned, IMHO.

Why would this need to be pinned???? :confused:

---

### Post by saulgoode on 2009-06-24
> Mono’s implementation of those components of the .NET stack not submitted to the ECMA for standardization has been the source of patent violation concerns for much of the life of the project.
This Wikipedia statement is misleading as it implies that patents are not a concern for the ECMA'd components of .NET. The actuality of the current situation is that those ECMA-associated patents are of particular concern because:

[LIST=1]
[*]The Mono Project assures us that Microsoft holds patents which cover the technology of the ECMA standard being implemented by Mono.
[*]Novell, the corporate sponsor of the Mono Project, has negotiated on behalf of its customers a patent licensing agreement with Microsoft that covers the Mono Project, *but this coverage is only for Novell's customers*.
[*]The Mono Project does NOT assure us that they've made any attempt to work around the ECMA-associated patents.
[*]Microsoft has NOT provided licensing for those patents under distribution terms which fulfill the standards of the OSI's Open Source Definition, the FSF's definition of Free Software, or the Debian Free Software Guidelines.[/LIST]

---

### Post by monsterstack on 2009-06-24
It's a shame, really. But if Microsoft offered all distributors of Linux a perpetual, worldwide, non-exclusive, no-charge, royalty-free, irrevocable patent licence to use Mono for whatever purpose, all of the bickering would go away overnight. In fact, if they had done that in 2006, instead of the deal they actually did make, sites like boycottnovell.com wouldn't exist. And nobody would be arguing about it. And everything would be okay in the world.

Nice dream.

---

### Post by Swarms on 2009-06-24
> **monsterstack said:**
> It's a shame, really. But if Microsoft offered all distributors of Linux a perpetual, worldwide, non-exclusive, no-charge, royalty-free, irrevocable patent licence to use Mono for whatever purpose, all of the bickering would go away overnight. In fact, if they had done that in 2006, instead of the deal they actually did make, sites like boycottnovell.com wouldn't exist. And nobody would be arguing about it. And everything would be okay in the world.

Nice dream.

I do not believe that is the case: many "linux zealots" hate everything that has a connection to Microsoft, so they hate the mono project too.

---

### Post by monsterstack on 2009-06-24
> **Swarms said:**
> I do not believe that is the case: many "linux zealots" hate everything that has a connection to Microsoft, so they hate the mono project too.

There may be some, but I've never seen any attack sites trying to convince people to boycott the Wine project, or Samba for that matter. I just think the patent deal specifically (not that it really bothers me much), is just evidence that Microsoft doesn't really *get* free software. They're just really a bit naff, you know?  Like, "Help you Linux guys out? Sure! Let me just call a team of lawyers to make an incomprehensible spume of dubious legal obligations first!" I mean, how boring is that?

---

### Post by directhex on 2009-06-24
> **monsterstack said:**
> There may be some, but I've never seen any attack sites trying to convince people to boycott the Wine project, or Samba for that matter. I just think the patent deal specifically (not that it really bothers me much), is just evidence that Microsoft doesn't really *get* free software. They're just really a bit naff, you know?  Like, "Help you Linux guys out? Sure! Let me just call a team of lawyers to make an incomprehensible spume of dubious legal obligations first!" I mean, how boring is that?

People were making up FUD about Mono for 4 years before the Novell/MS deal

And nobody ever mentions the Sun/MS deal from 2004, because Sun are sweetness and light

So no, there is absolutely no circumstance under which Mono won't cause stomach ulcers all round.

---

### Post by philcamlin on 2009-06-24
i dont like novell either :popcorn:

---

### Post by zekopeko on 2009-06-24
> **monsterstack said:**
> There may be some, but I've never seen any attack sites trying to convince people to boycott the Wine project, or Samba for that matter. I just think the patent deal specifically (not that it really bothers me much), is just evidence that Microsoft doesn't really *get* free software. They're just really a bit naff, you know?  Like, "Help you Linux guys out? Sure! Let me just call a team of lawyers to make an incomprehensible spume of dubious legal obligations first!" I mean, how boring is that?

Considering the problems Microsoft is in, the patent deal is the best option business wise.
MS has huge problems with patents. I think they pay around 2 billion dollars a year for patent infringement(and that was a couple of years ago). 
They started to make cross licensing deals (like the one with Novell) so to stave of the threat of patents.
There is nothing compelling for MS in giving a world wide licence for **alleged** mono patents since they aren't getting nothing in return.

So why is MS being sued for patent infringement? Don't they have an army of lawyers that search patent database's and their code?
Most likely no, since there is just to much patents and code to cover.
That's why MS is doing cross licencing deals with other software vendors.

---

### Post by monsterstack on 2009-06-24
> **directhex said:**
> People were making up FUD about Mono for 4 years before the Novell/MS deal

And nobody ever mentions the Sun/MS deal from 2004, because Sun are sweetness and light

So no, there is absolutely no circumstance under which Mono won't cause stomach ulcers all round.
Yeah, but it took the deal itself to make people pissed off enough to start an entire website dedicated to boycotting two companies. If not for that, the complaining would have been limited to a few Slashdot flamewars and nothing more, just like the Sun deal you speak of.

> **zekopeko said:**
> Considering the problems Microsoft is in, the patent deal is the best option business wise.
MS has huge problems with patents. I think they pay around 2 billion dollars a year for patent infringement(and that was a couple of years ago). 
They started to make cross licensing deals (like the one with Novell) so to stave of the threat of patents.
There is nothing compelling for MS in giving a world wide licence for **alleged** mono patents since they aren't getting nothing in return.

So why is MS being sued for patent infringement? Don't they have an army of lawyers that search patent database's and their code?
Most likely no, since there is just to much patents and code to cover.
That's why MS is doing cross licencing deals with other software vendors.

I'm aware of the why they're doing it, but this still doesn't stop me from wanting to drive a stake through the heart of the guy who came up with the idea of software patents in the first place.

---

### Post by adzik on 2009-06-24
Since no one's mentioned it yet, I thought I'd chip in a thought.
Mono does pose a (slight) risk to consultants like myself. Having a few clients that I recommend and help roll out certain Linux systems for, none of which wanted the Novell solutions, this poses a liability risk to me and my clients. It has no bearing on whether I like mono or not. If a client does not use the licensed Novell product, I can't do it out of self-preservation.
I am not a multi-million dollar company yet that I can afford a patent notice one day from any company, or the work and reputation involved to remove all the offending instances were it come to that.

On a personal level, I don't believe there is anything at issue with mono. The idea is beneficial for the entire OS ecosystem.
The problem occurs in the business space and needs to be addressed, or if not - avoided.
Perhaps the mono project could spearhead a licensing arrangement with MS for business if they believe it would work.

If someone knows if there is assurances that mono can be used on non-novell systems without the legal grey-zone, I'd love to know. It would certainly be helpful.

---

### Post by directhex on 2009-06-24
> **adzik said:**
> Since no one's mentioned it yet, I thought I'd chip in a thought.
Mono does pose a (slight) risk to consultants like myself. Having a few clients that I recommend and help roll out certain Linux systems for, none of which wanted the Novell solutions, this poses a liability risk to me and my clients. It has no bearing on whether I like mono or not. If a client does not use the licensed Novell product, I can't do it out of self-preservation.
I am not a multi-million dollar company yet that I can afford a patent notice one day from any company, or the work and reputation involved to remove all the offending instances were it come to that.

On a personal level, I don't believe there is anything at issue with mono. The idea is beneficial for the entire OS ecosystem.
The problem occurs in the business space and needs to be addressed, or if not - avoided.
Perhaps the mono project could spearhead a licensing arrangement with MS for business if they believe it would work.

If someone knows if there is assurances that mono can be used on non-novell systems without the legal grey-zone, I'd love to know. It would certainly be helpful.

It would be nice for such clarity - but I don't think it's currently available. And really, that's the point as to why such deals are struck. Not having "insurance" (for want of a better term... perhaps "protection racket" is better) is no guarantee of greater risk, but it's still distasteful

That said, are you deploying Linux, knowing that Microsoft have made statements regarding hundreds of violated patents (which only Novell or Xandros are free from)?

---

### Post by adzik on 2009-06-24
> **directhex said:**
> It would be nice for such clarity - but I don't think it's currently available. And really, that's the point as to why such deals are struck. Not having "insurance" (for want of a better term... perhaps "protection racket" is better) is no guarantee of greater risk, but it's still distasteful

That said, are you deploying Linux, knowing that Microsoft have made statements regarding hundreds of violated patents (which only Novell or Xandros are free from)?


I mainly arrange deployment of systems that are either red hat, or ones that have extensive coverage on what is legally permitted. This way we usually keep the systems covered by the licensing vendor or pull the plug on the components heavily in question if a custom arrangement is needed. Many of the patents that MS described aren't related much to my end. I asked for clarification on this in my particular situation (from a proper legal source). I suppose if they want to sue people over their double-click patent and progress bars, they'll have to do that in court with many other very large corporations before I ever get contacted. Plus, proving there's no prior art involved would be a challenge.
This is where [OIN]("http://www.openinventionnetwork.com/patents.php") can also be very helpful to the general business of open source.
All in all, with MONO, it's undocumented legal nature at the end of the day is what I choose to avoid. In my experience, MS tends to not be a goodwill company, and licensing is what it lives by.

---

### Post by Dragonbite on 2009-06-24
> **monsterstack said:**
> It's a shame, really. But if Microsoft offered all distributors of Linux a perpetual, worldwide, non-exclusive, no-charge, royalty-free, irrevocable patent licence to use Mono for whatever purpose, all of the bickering would go away overnight. 

No it wouldn't.. because it's still Microsoft, MICROSOFT I SAY!!, It's *eeeeevvvviiillllllllllllll* (add insane laughter if you'd like)

:popcorn:

---

### Post by monsterstack on 2009-06-24
> **Dragonbite said:**
> No it wouldn't.. because it's still Microsoft, MICROSOFT I SAY!!, It's *eeeeevvvviiillllllllllllll* (add insane laughter if you'd like)

:popcorn:

If people choose to have nothing at all to do with Microsoft out of principle, I say let them. There are are all sorts of good reasons to be distrustful and suspicious and even hateful of Microsoft. But if they actually made a bunch of good, open and free applications with no strings attached, then threads such as these wouldn't exist. It's the existence of the [attached]("http://www.microsoft.com/interop/msnovellcollab/moonlight.mspx") [microsoft.com] [strings]("http://www.microsoft.com/interop/msnovellcollab/faq.mspx") [microsoft.com] that scares people, not the fact that it's a Microsoft-invented thing. Whether or not those attached strings really are dangerous is not a subject I can be bothered to care about any more, but it is short-sighted at best to claim that the only reason people have a problem with Mono is because it's related to Microsoft.

---

### Post by sertse on 2009-06-24
You know, I thought continual tagging of "yet another mono thread", might actually cause people to rethink, and not rehash the same arguments for over again. *sigh*

I thought the intention of this thread is background reading, an overview of the mono situation so people wgo wish to participate in the mono wars can at least do it on an informed basis, but *sigh*

---

### Post by directhex on 2009-06-24
> **adzik said:**
> I mainly arrange deployment of systems that are either red hat, or ones that have extensive coverage on what is legally permitted. This way we usually keep the systems covered by the licensing vendor or pull the plug on the components heavily in question if a custom arrangement is needed. Many of the patents that MS described aren't related much to my end. I asked for clarification on this in my particular situation (from a proper legal source). I suppose if they want to sue people over their double-click patent and progress bars, they'll have to do that in court with many other very large corporations before I ever get contacted. Plus, proving there's no prior art involved would be a challenge.
This is where [OIN]("http://www.openinventionnetwork.com/patents.php") can also be very helpful to the general business of open source.
All in all, with MONO, it's undocumented legal nature at the end of the day is what I choose to avoid. In my experience, MS tends to not be a goodwill company, and licensing is what it lives by.

Mono is in OIN though

---

### Post by adzik on 2009-06-24
> **directhex said:**
> Mono is in OIN though

Yes, you're absolutely right. I think what we're referring to is it's underlying distribution rights.
To my understanding, there is no clear method of licensing, distribution or otherwise of .net's underpinnings, making this a grey area and a risk in business on the non-MS platform.

I believe this is what is in question.
[http://www.ecma-international.org/publications/standards/Ecma-334.htm](http://www.ecma-international.org/publications/standards/Ecma-334.htm)
[http://www.ecma-international.org/publications/standards/Ecma-335.htm](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

Anyway, enough said.
My initial question was only if anyone has clearer knowledge of whether a proper (legal) licensing situation existed for deployment in a corporate/business environment - outside of novell and xandros of course. Maybe one day this will be answered one way or another.

---

### Post by directhex on 2009-06-24
> **adzik said:**
> Maybe one day this will be answered one way or another.

That would be nice. But I'm not sure whether a) such a procedure could be done without enormous expense to all parties involved, and b) whether such an expense would be worthwhile, since the ZOMG NO M$ people would never ever be satisfied with a personal irrevocable contract from Bill Gates promising a lifetime supply of ice cream alongside any alleged patent nonsense

---

### Post by Giant Speck on 2009-06-24
I think there are three camps of people when it comes to being against Mono.

1.  The people who think that including Mono makes Linux uncomfortably close to Microsoft.

2.  The people who think that there are enough programming languages and that Mono is redundant.

3.  The people who think that Mono shouldn't be included in Ubuntu simply because there are already too many programs bloating up the installation disk (*cough*Evolution*cough*).

---

### Post by Dragonbite on 2009-06-25
> **Giant Speck said:**
> I think there are three camps of people when it comes to being against Mono.

1.  The people who think that including Mono makes Linux uncomfortably close to Microsoft.

2.  The people who think that there are enough programming languages and that Mono is redundant.

3.  The people who think that Mono shouldn't be included in Ubuntu simply because there are already too many programs bloating up the installation disk (*cough*Evolution*cough*).

That's a pretty good summary.

I was surprised when I tried out a CentOS 5.3 LiveCD, I saw they hand Thunderbird included and I couldn't find Evolution.

---

### Post by SKLP on 2009-06-25
> **Giant Speck said:**
> I think there are three camps of people when it comes to being against Mono.

1.  The people who think that including Mono makes Linux uncomfortably close to Microsoft.

2.  The people who think that there are enough programming languages and that Mono is redundant.

3.  The people who think that Mono shouldn't be included in Ubuntu simply because there are already too many programs bloating up the installation disk (*cough*Evolution*cough*).

I'd also suggest > 4. The people who seem to believe that it carries is a larger patent risk than other pieces of software. (maybe due to boycottnovell and other sites spreading fud)

I believe 1 and 4 may be the biggest groups.

---

### Post by monsterstack on 2009-06-26
Well this should get an interesting response. I will quote the article here (Stallman wrote it, so as far as I'm concerned it's GNU/GPL-FDL licensed, and some people have an aversion to going to that site anyway):

[COLOR="Red"]Edit:[/COLOR] Actually it comes from a post from the Free Software Foundation site, [here]("http://www.fsf.org/news/dont-depend-on-mono") [fsf.org]. *Boycott Novell* just reposted it.

> **[rms says]("http://boycottnovell.com/2009/06/26/stallman-says-no-to-mono/") [boycottnovell.com]:**
Debian’s decision to include Mono in the default installation, for the sake of Tomboy which is an application written in C#, leads the community in a risky direction. It is dangerous to depend on C#, so we need to discourage its use.

The problem is not unique to Mono; any free implementation of C# would raise the same issue. The danger is that Microsoft is probably planning to force all free C# implementations underground some day using software patents. (See [http://swpat.org](http://swpat.org) and [http://progfree.org](http://progfree.org).) This is a serious danger, and only fools would ignore it until the day it actually happens. We need to take precautions now to protect ourselves from this future danger.

This is not to say that implementing C# is a bad thing. Free C# implementations permit users to run their C# programs on free platforms, which is good. (The GNU Project has an implementation of C# also, called Portable.NET.) Ideally we want to provide free implementations for all languages that programmers have used.

The problem is not in the C# implementations, but rather in Tomboy and other applications written in C#. If we lose the use of C#, we will lose them too. That doesn’t make them unethical, but it means that writing them and using them is taking a gratuitous risk.

We should systematically arrange to depend on the free C# implementations as little as possible. In other words, we should discourage people from writing programs in C#. Therefore, we should not include C# implementations in the default installation of GNU/Linux distributions, and we should distribute and recommend non-C# applications rather than comparable C# applications whenever possible.

Thoughts? Opinions? And don't shoot the messenger plzkthx.

---

### Post by Giant Speck on 2009-06-26
Is there any solid proof it is the real RMS?

---

### Post by dragos240 on 2009-06-26
+1

---

### Post by Grant A. on 2009-06-26
He talks about trying to avoid them, and yet he doesn't want to lose Tomboy? I am now confused.

---

### Post by OutOfReach on 2009-06-26
> **giant speck said:**
> is there any solid proof it is the real rms?

+1

---

### Post by RiceMonster on 2009-06-26
If someone has the user name rms, it must be rms himself!

---

### Post by monsterstack on 2009-06-26
> **Grant A. said:**
> He talks about trying to avoid them, and yet he doesn't want to lose Tomboy? I am now confused.

As I understand it, rms likes free implementations of C# (Mono), and the applications people have made using them. He's scared, though, that all of those applications will disappear if Microsoft eventually make a patent claim. It's not really that hard to understand. Free software = good; no software = bad.

---

### Post by .Maleficus. on 2009-06-26
> **RiceMonster said:**
> If someone has the user name rms, it must be rms himself!
Well of course silly!



+1 to the question.  I'm very skeptical right now.

---

### Post by Grant A. on 2009-06-26
> **monsterstack said:**
> As I understand it, rms likes free implementations of C# (Mono), and the applications people have made using them. He's scared, though, that all of those applications will disappear if Microsoft eventually make a patent claim. It's not really that hard to understand. Free software = good; no software = bad.

But doesn't he realize the flurry of patent suits from the Open Invention Network that will come against Microsoft, if that ever happens?

---

### Post by ghindo on 2009-06-26
No offense, but RMS is kind of an extremist when it comes to software licenses.  His views tend not to be very pragmatic.  Don't get me wrong, he's done a lot for Free software, but there are definitely times when his views aren't especially practical.  I have yet to be shown in a conclusive, objective manner that Mono is a threat to anything, and RMS's article doesn't change that.

Again, this is *assuming* that the article was actually written by RMS.

---

### Post by monsterstack on 2009-06-26
> **Grant A. said:**
> But doesn't he realize the flurry of patent suits from the Open Invention Network that will come against Microsoft, if that ever happens?

I don't know. It's a very good point, though.

---

### Post by Sealbhach on 2009-06-26
Tomboy, F-Spot and Banshee will be the three Mono apps in Karmic, afaik. I think the OP is right to suggest that Debian and other Linux distros steer clear of it, why take a gratuitous risk? Tomboy is one of the first things I delete because I have no use for it whatsoever.

.

---

### Post by jonian_g on 2009-06-26
> **ghindo said:**
> No offense, but RMS is kind of an extremist when it comes to software licenses.  His views tend not to be very pragmatic.  Don't get me wrong, he's done a lot for Free software, but there are definitely times when his views aren't especially practical.  I have yet to be shown in a conclusive, objective manner that Mono is a threat to anything, and RMS's article doesn't change that.

Again, this is *assuming* that the article was actually written by RMS.

Well, I'll get you wrong. I don't see anything extremist in Stallman's opinion about mono.

---

### Post by swoll1980 on 2009-06-26
I could start a forum account, and call myself RMS. That doesn't mean I'm RMS.

---

### Post by DeadSuperHero on 2009-06-26
At the very least, it's quoted from the FSF's site. I think his argument is good, it's not the typical "Mono is EVIL!" dribble BN usually pumps out.

Regardless of whether Mono is a good language, bad language, "inherently evil", etc: at the end of the day, it all points back to patents and what can be done with them.

---

### Post by swoll1980 on 2009-06-26
> **Sealbhach said:**
> Tomboy, F-Spot and Banshee will be the three Mono apps in Karmic, afaik. I think the OP is right to suggest that Debian and other Linux distros steer clear of it, why take a gratuitous risk? 

.

The same reason I still fly after 9-11, because you can't let people use fear to control you, or they win.

---

### Post by monsterstack on 2009-06-26
> **Mr. Psychopath said:**
> At the very least, it's quoted from the FSF's site. I think his argument is good, it's not the typical "Mono is EVIL!" dribble BN usually pumps out.

Regardless of whether Mono is a good language, bad language, "inherently evil", etc: at the end of the day, it all points back to patents and what can be done with them.

Ah, I didn't know it was from a FSF article. First post changed accordingly. Can a mod rename the title of the thread to something less click-bait-ish? "RMS on Mono [via fsf.org]" or something?

---

### Post by Grant A. on 2009-06-26
> **swoll1980 said:**
> The same reason I still fly after 9-11, because you can't let people use fear to control you, or they win.

That may be true, but there's a difference between terrorists, and Microsoft possibly abusing the legal system. Microsoft is a very untrustworthy company, as we have been shown in the past few years with all the FUD, and the Halloween documents.


Note: I don't fly because of the crash rate of planes. They've been dropping out of the sky like flies, lately.

---

### Post by swoll1980 on 2009-06-26
> **Grant A. said:**
> That may be true, but there's a difference between terrorists, and Microsoft possibly abusing the legal system. 


The tactics they implement are different, but the strategy is the same. Scare people into doing what you want them to do.

---

### Post by SunnyRabbiera on 2009-06-26
Maybe someone could try contact RMS to see if he really did post this...

---

### Post by phrostbyte on 2009-06-26
If Microsoft ever sued Mono they'd piss off not just Linux users, but also many (most?) of their own developer base. It would probably be the dumbest thing they could target strategically. It's not going to happen. This "ooooooooooh Mono is scary" thing is pretty stupid.

---

### Post by monsterstack on 2009-06-26
> **SunnyRabbiera said:**
> Maybe someone could try contact RMS to see if he really did post this...
He did. C'mon, man, read the thread.

---

### Post by conundrumx on 2009-06-26
I just wanted to echo some prior statements and try to clarify.  RMS has done a lot of great things for Free software, and really freedom from copyrights as a whole.  He's had a lot of great ideas.  However, he is definitely an extremist when it comes to software licensing.  It doesn't have to be about Mono, just in general.  RMS seems to have a very narrow, black and white view of things.

Personally, I tend to agree with Linus Torvalds on software licensing: use whatever's best.  If there's good proprietary software to be had, people shouldn't be condemned for it or ashamed of it.

As far as Mono in particular, nothing but FUD and stupidity.  There are plenty of great F/OSS projects based on it, and there's no reason to waste time on stupid things like Gnote.

---

### Post by DeadSuperHero on 2009-06-26
> **conundrumx said:**
> 
As far as Mono in particular, nothing but FUD and stupidity.  There are plenty of great F/OSS projects based on it, and there's no reason to waste time on stupid things like Gnote.

Actually, don't bash it before you try it. As of using it for a few days, I've found that it's extremely stable, responsive, and the interface basically looks like Tomboy. If there really is a threat from Microsoft patents, at the very least switching to Gnote is non-trivial.

---

### Post by k2t0f12d on 2009-06-26
There is no reason not to pursue development of a free software C# implementation. It is good to be able to run programs in freedom regardless of the language in which they are written. What RMS advocates is to avoid making any distribution dependent on free software projects written in C#. That way if C# implementation were ever made non-free by patent attack, the free software platform wouldn't suffer in any way.

If it could be proved that C# would never be made non-free by any future litigation, then the only reason to avoid an implementation of C# would be to keep a streamlined GNU+Linux system.

I personally think LLVM is more interesting technology anyway.

---

### Post by phrostbyte on 2009-06-26
They aren't bundling Mono for the sake of bundling Mono, they are bundling Mono because it's a dependency for applications that are bundled. Kind of like the reason Python is bundled with Ubuntu, because some apps are written in Python in default install. 

I really don't like this Mono hate. Mono enables rapid application development, something that was sorely missing in Linux desktop 5-10 years ago. It also allows Windows programmers to not be as scared of Linux and they feel more comfortable with the OS and FUD it less. .NET skills directly transfer to Mono and they can make high quality applications that run on Linux without pretty much any learning curve.

In order for free software desktop to progress we need to provide the tools enable all programmers to feel welcome, not just Python or C experts. We need to be compatable with all programming languages that people use. Please attack/hate Microsoft (I don't mind this :)), but don't hate programming languages just because they come from Microsoft.. 

My 2 cents.

---

### Post by starcannon on 2009-06-26
Here's a link to the article at fsf.org.
**[Why free software shouldn't depend on Mono or C#]("http://www.fsf.org/news/dont-depend-on-mono/view?searchterm=mono")**

[by Richard M. Stallman]("http://www.fsf.org/news/dont-depend-on-mono/view?searchterm=mono")

This should lay to rest all the people taking a quote of RMS out of context as fully endorsing mono when he spoke on the subject at a convention. I'm not a Stallmanite, but I do fully agree with him on this matter; that said, as has been pointed out, the distributions themselves will have to deal with any possible legal troubles regarding the use of mono, not the end users. The only thing that would likely ever be lost is time spent on mono projects if those projects were ever to be killed by MS litigation (time is valuable, but fortunately there is no shortage of it in the foreseeable future).

Anyway, love it, hate it, or don't care about it, Mono is here, and its being implemented; so all we can do now is wait and see, bickering about it won't solve anything at this point.

---

### Post by conundrumx on 2009-06-27
> **Mr. Psychopath said:**
> Actually, don't bash it before you try it. As of using it for a few days, I've found that it's extremely stable, responsive, and the interface basically looks like Tomboy. If there really is a threat from Microsoft patents, at the very least switching to Gnote is non-trivial.

Think of it this way: how much development time and effort is wasted on Gnote because of FUD?  How much wasted energy by the community as a whole will result from duplicating an existing program in a different language?  If someone decided to rewrite Gedit in C# "just because" there would be massive fallout and bitching, so I just don't understand why people would embrace Gnote.

---

### Post by DeadSuperHero on 2009-06-27
> **conundrumx said:**
> Think of it this way: how much development time and effort is wasted on Gnote because of FUD?  How much wasted energy by the community as a whole will result from duplicating an existing program in a different language?  If someone decided to rewrite Gedit in C# "just because" there would be massive fallout and bitching, so I just don't understand why people would embrace Gnote.

Ultimately, does it matter? You're kind of getting worked up over something that has marginally no effect on you. If you had never heard of Gnote, it wouldn't even matter. It doesn't hurt anyone, it's just an option for people who don't want mono, just like Gnome/Gtk was a solution for people that didn't want KDE/Qt.

After all, isn't choice one of the key aspects of FOSS?

---

### Post by phrostbyte on 2009-06-27
> **conundrumx said:**
> Think of it this way: how much development time and effort is wasted on Gnote because of FUD?  How much wasted energy by the community as a whole will result from duplicating an existing program in a different language?  If someone decided to rewrite Gedit in C# "just because" there would be massive fallout and bitching, so I just don't understand why people would embrace Gnote.

TBH, I think Gnote was also a intellectual challenge to see how far the author could go converting a C# program to C++. In a sense it's an interesting problem.

---

### Post by MikeTheC on 2009-06-27
> **swoll1980 said:**
> The same reason I still fly after 9-11, because you can't let people use fear to control you, or they win.

That sort of sentiment operates on so many levels, swoll.

Big +1 to you for having posted it here.

---

### Post by monsterstack on 2009-06-27
Err, continue.

---

### Post by Giant Speck on 2009-06-27
> **Grant A. said:**
> Note: I don't fly because of the crash rate of planes. They've been dropping out of the sky like flies, lately.

Do you drive or ride in a motor vehicle as your primary mode of transportation?

_**Odds of dying during your lifetime in a(n):**_
motor vehicle accident:  1 in 84
aviation accident:  1 in 6,460

[U][B]Odds of dying during one year in a(n):
[/B][/U]motor vehicle accident: 1 in 6,539
aviation accident: 1 in 502,554

---

### Post by MikeTheC on 2009-06-27
> **Giant Speck said:**
> Do you drive or ride in a motor vehicle as your primary mode of transportation?

Yes, however you have to understand Grant A's motor vehicle is actually a kevlar-coated 80-ton tank with massive armor plating, spiked cleats, all made from non-corroding metals, and is powered through a water/electrolytic fuel system. He's also got 10" canons, fore and aft, as well as a range of other defense systems.

His vehicle is quite safe.

---

### Post by Giant Speck on 2009-06-27
> **MikeTheC said:**
> Yes, however you have to understand Grant A's motor vehicle is actually a kevlar-coated 80-ton tank with massive armor plating, spiked cleats, all made from non-corroding metals, and is powered through a water/electrolytic fuel system. He's also got 10" canons, fore and aft, as well as a range of other defense systems.

His vehicle is quite safe.

What if he gets trapped inside?  Or if he gets out and forgets to put the parking brake on and it backs up and flattens him to death?

---

### Post by Grant A. on 2009-06-27
> **MikeTheC said:**
> His vehicle is quite safe.

Not for the other people on the road. ;)

---

### Post by eragon100 on 2009-06-27
I use banshee and f-spot. I think banshee is the best music and video player for linux currently, it's the only anyway that can play both music and video and has libraries for both. (I don't need a complete media center.)

I don't think microsoft will sue mono, because Novell and MS have a legal agreement not to sue each other. Novell is the force behind mono. So even if MS wanted to sue Novell, which would be stupid because it would only decrease the popularity of their own programming platform, I don't think they could because they have a contract with them.

---

### Post by bryonak on 2009-06-27
> **conundrumx said:**
> I just wanted to echo some prior statements and try to clarify.  RMS has done a lot of great things for Free software, and really freedom from copyrights as a whole.  He's had a lot of great ideas.  However, he is definitely an extremist when it comes to software licensing.  It doesn't have to be about Mono, just in general.  RMS seems to have a very narrow, black and white view of things.
[...]
As far as Mono in particular, nothing but FUD and stupidity.  There are plenty of great F/OSS projects based on it, and there's no reason to waste time on stupid things like Gnote.

Stallman has a few extreme opinions on some select issues, but many of his arguments are rational and in the moderate range (e.g. the one about Mono).
The bulk of his views, particularly about software licensing, is already contained within the text of the GPL... wich few people in the FOSS community would call "extreme" ;)

About Mono... (strong) opposers claim that it's only to run Windows apps on Linux, (strong) proponents tout this as an "almost coincidential" side effect to having a good framework that enables quick development of native Linux apps.
What makes me wonder is why do they have to label the processes foo.exe?

As for GNote... well it obviously has it's userbase, people who prefer it over Tomboy for whatever reason. Which means it should be developed.
And it gets a plus for making the desktop more lightweight.

For me, GNote is graphically too bloated and the note taking process itself is too circumstancial, because I don't want to waste time on "layouting" my notes... KNotes (on Gnome!) just fits the bill, while Tomboy is out of consideration (same as GNote, just slower).



Offtopic: what are the odds of dying in a motor vehicle accident involving tanks in Grant A's city?

---

### Post by directhex on 2009-06-27
> **bryonak said:**
> What makes me wonder is why do they have to label the processes foo.exe?

Essentially, because the ECMA335 spec says so, and there's no enormous benefit to NOT doing so (whereas being spec compliant was rather useful in the earliest days of Mono where the Mono compiler and libs needed to be compiled with the MS.NET compiler). That said, we (the downstream packagers) would we open to the idea of patches which enable use of a secondary file extension (e.g. .cliapp and .clilib) as long as it worked fine with the GAC. As it stands, it would cause a problem with assembly references to simply change it without patches, but it would be fine on unreferences assemblies:

```
directhex@desire:/tmp$ gmcs hello.cs 
directhex@desire:/tmp$ mv hello.exe hello.cliapp
directhex@desire:/tmp$ mono hello.cliapp 
Hello, World!
```

---

### Post by MikeTheC on 2009-06-27
> **Giant Speck said:**
> What if he gets trapped inside?  Or if he gets out and forgets to put the parking brake on and it backs up and flattens him to death?

That *would* suck.

---

### Post by SKLP on 2009-06-27
If mono is threatened with a specific patent claim, mono could probably just work around it( and at worst case, people would have to make some tiny changes to their C# apps to make them compatible again.). It's the same with all software basically (until software patents hopefully becomes abolished).

I suppose RMS could be right though, but I do not believe it.

---

### Post by froggyswamp on 2009-06-27
[http://www.fsf.org/news/dont-depend-on-mono](http://www.fsf.org/news/dont-depend-on-mono)

> 
We should systematically arrange to depend on the free C# implementations as little as possible.  In other words, we should discourage people from writing programs in C#.  Therefore, we should not include C# implementations in the default installation of GNU/Linux distributions, and we should distribute and recommend non-C# applications rather than comparable C# applications whenever possible.
+1

---

### Post by SKLP on 2009-06-27
> **bryonak said:**
> Stallman has a few extreme opinions on some select issues, but many of his arguments are rational and in the moderate range (e.g. the one about Mono).
 Maybe, I do not agree with all of his views though (for instance this one regarding mono)
> **bryonak said:**
> 
The bulk of his views, particularly about software licensing, is already contained within the text of the GPL... wich few people in the FOSS community would call "extreme" ;)Many people dislike the GPL and non-permissive licenses in general, including myself. Just look at the large amounts of software available under permissive licenses (MIT, BSD or others). Open source software is nice, but I would consider someone who considers it to be *UNETHICAL* to touch any proprietary software to be, yes, somewhat of an extremist.

---

### Post by -grubby on 2009-06-27
[quote=Wikipedia's article on C#]
C# [...] approved as a standard by Ecma (ECMA-334) and ISO (ISO/IEC 23270)
[/quote]

.

---

### Post by koenn on 2009-06-27
> **grubby- said:**
> 
Originally Posted by Wikipedia's article on C#
C# [...] approved as a standard by Ecma (ECMA-334) and ISO (ISO/IEC 23270)

The issue is not about approved standards, but about the posibility that C# is  patented; and therefore the patent holder could (try and) stop the use of C# implementations and programs build with it. - [http://www.fsf.org/news/dont-depend-on-mono](http://www.fsf.org/news/dont-depend-on-mono)

---

### Post by zekopeko on 2009-06-27
> **koenn said:**
> The issue is not about approved standards, but about the posibility that C# is  patented; and therefore the patent holder could (try and) stop the use of C# implementations and programs build with it. - [http://www.fsf.org/news/dont-depend-on-mono](http://www.fsf.org/news/dont-depend-on-mono)

hahahaha!!! total lulz! the man that created GCC by re-implementing a proprietary compiler (loaded with patents) is now calling somebody out on the thing he did! and not to mention that his beloved FSF has a .NET implementation of his own.
Hypocrisy is dripping from his every word.

---

### Post by koenn on 2009-06-27
> **zekopeko said:**
> hahahaha!!! total lulz! the man that created GCC by re-implementing a proprietary compiler (loaded with patents) is now calling somebody out on the thing he did! 
a compiler as something rathr different from a language, especially if it's a language closely linked to a development framework, such as .NET.
And you're the first one I ever heared claim that the gnu C compiler infringes on patents, so excuse me if I don't believe you. Show me facts. 

> **zekopeko said:**
>  and not to mention that his beloved FSF has a .NET implementation of his own.
Hypocrisy is dripping from his every word.
They made a .NET implementation because it's their goal to make a free implementation of any language out there, but they recommend not to use  or distribute it, for the reasons stated. Pretty straightforward and out in the open, I don't see any hypocrisy.

---

### Post by mister_pink on 2009-06-27
> **zekopeko said:**
> hahahaha!!! total lulz! the man that created GCC by re-implementing a proprietary compiler (loaded with patents) is now calling somebody out on the thing he did! and not to mention that his beloved FSF has a .NET implementation of his own.
Hypocrisy is dripping from his every word.

Did you read the article - Its not even that long! He explicitly explains why mono or portable.net are not the problem.

---

### Post by saulgoode on 2009-06-27
> **zekopeko said:**
> hahahaha!!! total lulz! the man that created GCC by re-implementing a proprietary compiler (loaded with patents) is now calling somebody out on the thing he did! and not to mention that his beloved FSF has a .NET implementation of his own.
Hypocrisy is dripping from his every word.
The C programming language was initially written in 1969, well before it was possible to even *copyright* source code for software. Richard Stallman started work on GCC at about the same time as the USPTO started granting software patents (early- to mid-80s). Anything implemented in the language before that time would not have been patented; and it was not until a decade later that software patents started being granted more regularly.  

In more basic terms, software patents effectively did not exist when Richard Stallman was working on his C language compiler, and there is no hypocrisy in his petition. (You will also find that the GCC developers have been extremely scrupulous with regard to patents over the last two decades, avoiding patented technologies when even marginally questionable, as well as benefitting from [direct involvement from IBM]("http://www-01.ibm.com/support/docview.wss?uid=swg27005175&aid=1") including [Free Software-compliant pledges of licensing]("http://www.ibm.com/ibm/licensing/patents/pledgedpatents.pdf")).

---

### Post by zekopeko on 2009-06-27
> **mister_pink said:**
> Did you read the article - Its not even that long! He explicitly explains why mono or portable.net are not the problem.

he's being passive-aggressive. Mono or Portable.Net aren't a problem but the underlying language(?) is as far as RS thinks.

---

### Post by zekopeko on 2009-06-27
> **koenn said:**
> a compiler as something rathr different from a language, especially if it's a language closely linked to a development framework, such as .NET.
And you're the first one I ever heared claim that the gnu C compiler infringes on patents, so excuse me if I don't believe you. Show me facts.

The same can be said about mono or any other MS technology that is re-implemented as free software.
But the point is that considering the number of software patents out there (in US) writing anything more complex then a "Hello,World" program is going to infringe on some patent.

> 
They made a .NET implementation because it's their goal to make a free implementation of any language out there, but they recommend not to use  or distribute it, for the reasons stated. Pretty straightforward and out in the open, I don't see any hypocrisy.

OK,OK hypocrisy is perhaps too strong a word for this case.
But why have this developer effort toward re-implementing a framework that you can't use?

---

### Post by aesis05401 on 2009-06-27
> **zekopeko said:**
> he's being passive-aggressive. Mono or Portable.Net aren't a problem but the underlying language(?) is as far as RS thinks.

It would only be passive aggressive if he was *not* specifically stating the issue.  

The primary problem with getting this conversation beyond this point is that certain FOSS developers and distributors examined their legal position with regards to IP involved in Mono that may be infringed by the implementation, and decided they needed to pay MS for an agreement about where they stood.

This is not the same as saying the code or language is 'owned' by Microsoft.  Encumberance can come in many forms.  In fact the GPL encumbers through the making public device.

---

### Post by zekopeko on 2009-06-27
> **aesis05401 said:**
> The primary problem with getting this conversation beyond this point is that certain FOSS developers and distributors examined their legal position with regards to IP involved in Mono that may be infringed by the implementation, and decided they needed to pay MS for an agreement about where they stood.

i don't understand this part. who are this people/distributors and could you point me to the infringed part of the implementation?
any link(s)?

---

### Post by aesis05401 on 2009-06-27
The largest who signed a licensing deal was Novell, but they were not the first, and I do not believe they deserve the beating they have taken from the community over their decision.  Additionally, they received some legitimate ability to work with integrating their FOSS offerings with MS products.

The reasons they signed this deal are still unknown as MS has yet to specify what infringing aspects are present.  

You may remember the press releases about all the supposed 'infringement' in the Linux kernel (235 patent infringements or something according to Ballmer).  All of that FUD was related to this same brouhaha - and it is darn near impossible to get good info.

So literally, this is where the conversation stalls.  Nobody knows why all the posturing and money changing hands and MS ain't talking.

So where do we go from here?  Good question.  One thing is certain, politics are being played to the hilt by all sides.

---

### Post by zekopeko on 2009-06-27
> **aesis05401 said:**
> The largest who signed the cross-licensing deal was Novell, but they were not the first, and I do not believe they deserve the beating they have taken from the community over their decision.  Additionally, they received some legitimate ability to work with integrating their FOSS offerings with MS products.

i think that the whole point of that deal (and others with linux vendors) is about patents. that is cross licensing patent.
as i said in a previous post: you can't write any useful software without stepping on a patent.

> 
The reasons they signed this deal are still unknown as MS has yet to specify what infringing aspects are present.  


To shed some light read this book review: [http://arstechnica.com/tech-policy/news/2009/05/making-microsoft-nicer-through-patents.ars](http://arstechnica.com/tech-policy/news/2009/05/making-microsoft-nicer-through-patents.ars)

> 
You may remember the press releases about all the supposed 'infringement' in the Linux kernel (235 patent infringements or something according to Ballmer).  All of that FUD was related to this same brouhaha - and it is darn near impossible to get good info.


because it was complete FUD. the moment MS say what patents are infringed linux devs can fix it. look at the FAT patent and TomTom. there is already a patch that works around said patent.

> 
So literally, this is where the conversation stalls.  Certain FOSS vendors felt they needed protection from something related the manner in which something might have been implemented.


So does MS. that's why the novell deal. novell could have sued the pants of MS since they have some rather important XML patents.

> 
So where do we go from here?  Good question.  One thing is certain, politics are being played to the hilt by all sides.

You ignore patents until they are pointed out. then you work around them. that's the only sane thing to do. the other one would be to stop producing any software.

---

### Post by aesis05401 on 2009-06-27
> **zekopeko said:**
> You ignore patents until they are pointed out. then you work around them. that's the only sane thing to do. the other one would be to stop producing any software.

Even though I am an equally vested partner in my little development business there is no way I could ever convince my partners or my customers to eat that burrito.

Ignore patents in general, yes.  Target anything that other people have had to pay to distribute?  No.  I don't believe for a second that the Novell settlement covers me.  Why should they pay for my free ride?  

The developers of Mono felt they needed additional protection, so I feel it is disingenuous to not raise the point that anyone who wants to marry that framework may also be required to pay.

Your other points I have no argument with.

---

### Post by zekopeko on 2009-06-27
> 
Ignore patents in general, yes.  Target anything that other people have had to pay to distribute?  No.  I don't believe for a second that the Novell settlement covers me.  Why should they pay for my free ride? 

OT: From the last sentence I'm guessing that you are from the US.
Yes?

Back on topic:
[http://www2.apebox.org/wordpress/rants/124/](http://www2.apebox.org/wordpress/rants/124/) if you haven't read it.

---

### Post by directhex on 2009-06-27
> **aesis05401 said:**
> Ignore patents in general, yes.  Target anything that other people have had to pay to distribute?  No.  I don't believe for a second that the Novell settlement covers me.  Why should they pay for my free ride?  

The developers of Mono felt they needed additional protection, so I feel it is disingenuous to not raise the point that anyone who wants to marry that framework may also be required to pay.

The Novell deal was not about Mono. Let me state that again - the Novell deal was not about Mono. The actual wording of which products are covered by the deal are pretty obtuse, but The word "Mono" is not included once. Mono is part of the deal as a whole - so try replacing the word "Mono" with "Kernel" for an equally "dubious" piece of code which is being "protected"

---

### Post by Viva on 2009-06-27
I'm with rmson this one.

---

### Post by saulgoode on 2009-06-27
> **directhex said:**
> The Novell deal was not about Mono. Let me state that again - the Novell deal was not about Mono. The actual wording of which products are covered by the deal are pretty obtuse, but The word "Mono" is not included once.

From the Joint Letter to the Open Source Community on [Novell's website](http://www.novell.com/linux/microsoft/openletter.html):
 [LIST][I]
[*] Under the patent agreement, customers will receive coverage for Mono, Samba, and OpenOffice as well as .NET and Windows Server.[/I][/LIST]

---

### Post by aesis05401 on 2009-06-28
> **saulgoode said:**
> From the Joint Letter to the Open Source Community on [Novell's website](http://www.novell.com/linux/microsoft/openletter.html):
 [LIST][I]
[*] Under the patent agreement, customers will receive coverage for Mono, Samba, and OpenOffice as well as .NET and Windows Server.[/I][/LIST]

Nice.

Unfortunately, as I stated earlier (or possibly in another thread) I do not know of anywhere where they actually state what specific infringements are being covered, just that there is coverage... so this is as far as this conversation can go until there is some sort of legal challenge that further defines the issue.

I doubt as much as anyone that MS is just going to come out with a bulleted list of infringements.  We are still a long way from any deb distro actually relying on Mono, though, so I am still on board around here.

---

### Post by aesis05401 on 2009-06-28
> **zekopeko said:**
> OT: From the last sentence I'm guessing that you are from the US.
Yes?

Back on topic:
[http://www2.apebox.org/wordpress/rants/124/](http://www2.apebox.org/wordpress/rants/124/) if you haven't read it.

*snip* n/m

---

### Post by TheBuzzSaw on 2009-06-28
C++ is better anyway.

---

### Post by Kazade on 2009-06-28
I just generally don't see the point in taking the risk... Mono as a means to run Windows developed .NET applications - fine. Developing Mono applications when you have Vala, Java, Python, Ruby, C, C++, D and god knows what else to chose from just seems crazy. Why risk it? I mean, best case scenario, MS doesn't sue, but you will always be behind on features of the "official" .NET. Worst case scenario, Mono gets sued to oblivion, is pulled from the distros, your application dies. Just doesn't make sense to me. Use something else.

Just my 2p.

---

### Post by cb951303 on 2009-06-28
So in other word's Mono is ok and C# is not.
Does he suggest to keep developing Mono but not to use it?

---

### Post by cb951303 on 2009-06-28
> **Kazade said:**
> I just generally don't see the point in taking the risk... Mono as a means to run Windows developed .NET applications - fine. Developing Mono applications when you have Vala, Java, Python, Ruby, C, C++, D and god knows what else to chose from just seems crazy. Why risk it? 

[http://www2.apebox.org/wordpress/rants/124/](http://www2.apebox.org/wordpress/rants/124/)

---

### Post by k2t0f12d on 2009-06-28
> **SKLP said:**
> If mono is threatened with a specific patent claim, mono could probably just work around it( and at worst case, people would have to make some tiny changes to their C# apps to make them compatible again.). It's the same with all software basically (until software patents hopefully becomes abolished).

I suppose RMS could be right though, but I do not believe it.Its risk management, nothing more nothing less. If patent aggression was successful against C# implementations like Mono, it could render any number of its integral components unusable. Even if a work around like you suggested could rectify the problem, why take any risk if programs implemented in C# could just as easily be written in languages with prior art already established on the GNU+Linux platform? Even worse, why would you think that rewriting programs implemented in C# is an acceptable solution for a patent attack, when they could be written in another language just once? It's probably true that any program can be the target of a patent attack, but rarely all of the programs written in the same language. Until its *proven* that Mono is safe from litigation, GNU+Linux wouldn't lose a thing by keeping Mono strictly as an optional package rather then a requirement.

> **SKLP said:**
> Maybe, I do not agree with all of his views though (for instance this one regarding mono)
Many people dislike the GPL and non-permissive licenses in general, including myself.Interesting. I believe you, but that's not a reason. If you want to have a debate about it, you need to provide a thesis for *why* you don't like copyleft.

**For example**, I don't use non-copyleft licenses because they create liability for enterprise that would otherwise support free software, and because they do not harness the optimum level of invention from the commons.

> **SKLP said:**
> Just look at the large amounts of software available under permissive licenses (MIT, BSD or others).Part of the problem with non-copyleft licensing *is* its tendency to fork, creating redundant invention.

> **SKLP said:**
> Open source software is nice, but I would consider someone who considers it to be *UNETHICAL* to touch any proprietary software to be, yes, somewhat of an extremist.Fortunately for us, the most vocal critic against proprietary software cites *reasons* for his criticisms. Just saying an idea is extreme doesn't give any rational explanation why anyone should or shouldn't be credulous. If you think proprietary software *isn't* unethical, give us a thesis that demonstrates why.

**For example**, Proprietary software *is* unethical because it gives a developer power over the users that no one should have.

---

### Post by directhex on 2009-06-28
> **saulgoode said:**
> From the Joint Letter to the Open Source Community on [Novell's website](http://www.novell.com/linux/microsoft/openletter.html):
 [LIST][I]
[*] Under the patent agreement, customers will receive coverage for Mono, Samba, and OpenOffice as well as .NET and Windows Server.[/I][/LIST]

Not on Microsoft's list - which is presumably the one that matters. Microsoft essentially have an "exclude" list, not an include list, and Mono isn't mentioned.

---

### Post by aesis05401 on 2009-06-28
> **directhex said:**
> Not on Microsoft's list - which is presumably the one that matters. Microsoft essentially have an "exclude" list, not an include list, and Mono isn't mentioned.

Then someone needs to get on the phone with Miguel and tell him he is off the hook.  

He has been taking a pounding near and far for a long time now and it ain't because of the gnome design model.  If MS doesn't care about Mono then de Icaza and his crew ruined their reps for nothing by being associated with that statement by Novell.

---

### Post by saulgoode on 2009-06-28
> **directhex said:**
> Not on Microsoft's list - which is presumably the one that matters. Microsoft essentially have an "exclude" list, not an include list, and Mono isn't mentioned.
The citation I provided is a "joint" letter from **both** Novell and Microsoft. [The exact same announcement]("http://www.microsoft.com/interop/msnovellcollab/open_letter.mspx") is also presented by Microsoft on their own website. (I initially linked to Novell's site because I considered that to be the opinion that mattered.)

---

### Post by directhex on 2009-06-28
> **saulgoode said:**
> The citation I provided is a "joint" letter from **both** Novell and Microsoft. [The exact same announcement]("http://www.microsoft.com/interop/msnovellcollab/open_letter.mspx") is also presented by Microsoft on their own website. (I initially linked to Novell's site because I considered that to be the opinion that mattered.)

Where is it mentioned in [http://www.microsoft.com/interop/msnovellcollab/patent_agreement.mspx](http://www.microsoft.com/interop/msnovellcollab/patent_agreement.mspx) though? As in the actual agreement, not the fluffy-wording letter to go with it?

---

### Post by aesis05401 on 2009-06-28
> **directhex said:**
> Where is it mentioned in [http://www.microsoft.com/interop/msnovellcollab/patent_agreement.mspx](http://www.microsoft.com/interop/msnovellcollab/patent_agreement.mspx) though? As in the actual agreement, not the fluffy-wording letter to go with it?

The fluffy letter?  The one where they spell everything out in plain English with quotes like:

*"What it really means is that customers deploying technologies from Novell and Microsoft no longer have to fear about possible lawsuits or potential patent infringement from either company."*

...

And then follow that with a section *entitled*: ***"Mono, OpenOffice and Samba"*** wherein they state that Novell customers are covered for patents included in Mono - see quote posted by another poster earlier in this thread.

This is not a fluffy letter.  If MS tried legal step one against Novell this letter would be defense 'Evidence A.'

I'm sorry directhex, but if you read my other posts you will see I am not advocating for Mono removal or suggesting that anyone currently in development stop using Mono.  I am pointing out that every indication points to undefined encumbrance on the implemented IP.

Edit: I just noticed this at the bottom of the letter: *"This is a watershed moment for Linux. It fundamentally changes the rules of the game."*

This is all I'm saying - we don't know the actual IP details of the agreement - they changed the game and didn't tell us the rules.  That is the entire argument against Mono in a nutshell.  No one knows the rules but MS and possibly Novell.

---

### Post by directhex on 2009-06-28
> **aesis05401 said:**
> The fluffy letter?  The one where they spell everything out in plain English with quotes like:

*"What it really means is that customers deploying technologies from Novell and Microsoft no longer have to fear about possible lawsuits or potential patent infringement from either company."*

...

And then follow that with a section *entitled*: ***"Mono, OpenOffice and Samba"*** wherein they state that Novell customers are covered for patents included in Mono - see quote posted by another poster earlier in this thread.

This is not a fluffy letter.  If MS tried legal step one against Novell this letter would be defense 'Evidence A.'

I'm sorry directhex, but if you read my other posts you will see I am not advocating for Mono removal or suggesting that anyone currently in development stop using Mono.  I am pointing out that every indication points to undefined encumbrance on the implemented IP.

But not a word about the aforementioned OOo and Samba, right?

---

### Post by aesis05401 on 2009-06-28
> **directhex said:**
> But not a word about the aforementioned OOo and Samba, right?

Yes, and I am glad we are back into a conversation that can get us somewhere.  

Mono is the only one of the three that Novell actually owns copyright on.  If you check the Mono licensing FAQ you will see that Novell requires copyright assignment for donated code:[http://mono-project.com/License]("http://mono-project.com/License").

Sun does (did?) the same for OO, and most FOSS projects of any size require copyright transfer to the project maintainers.  Correct me if I am wrong, and I don't know who might donate to samba, but it is a stand alone organization in my understanding.

So there is a legitimate legal difference between these things.  Now some people will tell you that Novell could simply fork future versions of the framework back to proprietary and take their patent protection with them, but my message isn't that radical.  My message is simply that we don't know what is going on.

Either way, Mono is the only one of the three that Novell actually 'controls.'

Edit: I know this is emotional for some people, but if anyone is going to post that you can't close future versions of an FOSS project on which you own copyright, please do some research before flaming.  Novell can do this so long as they don't attempt to deprive the community of the existing FOSS licensed versions.  This would leave developers with two choices, pay Novell for the proprietary version, or pay MS for a license to the existing FOSS versions (yes, the one you are using today) the same way Novell did when they signed their protection agreement. Sounds insane, but it is legal in America if Mono is implemented in a way that includes encumbered IP.  This is what people are afraid of.  

Hopefully we can work productively within the deb tree to get some clarifications on Mono in the near future.

---

### Post by entr3p on 2009-06-28
Hey. Just incase anyone else is looking for a way to do this then I recommend to check out this easy guide:

[How to Completely Remove Mono on Ubuntu]("http://www.learningubuntu.com/articles/how-completely-remove-mono-ubuntu")

---

### Post by MountainX on 2009-06-29
[http://www.itwire.com/content/view/25954/1231/](http://www.itwire.com/content/view/25954/1231/)

RMS says Debian Mono decision 'risky'                                                                                  [                     [IMG]http://www.itwire.com/images/M_images/emailButton.png[/IMG]]("http://www.itwire.com/index2.php?option=com_content&task=emailform&id=25954&itemid=1231")                                                                                                                                                             by Sam Varghese                                                                                                                                        Sunday, 28 June 2009                                                                                          [!]("http://www.informationmadness.com/cms")

The founder of the Free Software Foundation, Richard Matthew Stallman, has termed Debian's decision to include Mono as part of its default desktop task a move that "leads the community in a risky direction."                                      
         
         
In [a short statement]("http://www.fsf.org/news/dont-depend-on-mono") published on the FSF site, Stallman, who launched the GNU Project in 1984 to develop a complete Unix-like operating system which is free software, slammed Debian's move which was taken "for the sake of Tomboy which is an application written in C#."

He said: "It is dangerous to depend on C#, so we need to discourage its use."

The Debian GNU/Linux project [has plans]("http://www.itwire.com/content/view/25683/1090/") to include Tomboy, a note-taking application in its next release, Squeeze. There has been no discussion about it on any of the regular mailing lists for Debian developers; the [decision]("http://svn.debian.org/viewsvn/pkg-gnome/desktop/unstable/meta-gnome2/debian/control?view=log#rev20303")  was made by a lone developer who packages the GNOME desktop for the distribution.

A port of Tomboy known as Gnote was released recently

Stallman said: "The problem is not unique to Mono; any free implementation of C# would raise the same issue. The danger is that Microsoft is probably planning to force all free C# implementations underground some day using software patents.

"This is a serious danger, and only fools would ignore it until the day it actually happens. We need to take precautions now to protect ourselves from this future danger."

He said that implementing C# itself was not objectionable. "Free C# implementations permit users to run their C# programs on free platforms, which is good. (The GNU Project has an implementation of C# also, called Portable.NET.) Ideally we want to provide free implementations for all languages that programmers have used."

Red Hat's community Linux distribution, Fedora, recently [decided]("http://www.itwire.com/content/view/25469/1154/")  to throw out Mono altogether from its default install, and replaced Tomboy with Gnote. 

While pro-Mono zealots often claim that it is possible to obtain a royalty-free, reasonable and non-discriminatory licence for the use of Microsoft patents which may be part of Mono, in reality, it is extremely difficult [to even find out]("http://www.itwire.com/content/view/25215/1090/")  how one can do so.

What one finds is things like [this statement]("http://www.oreillynet.com/databases/blog/2004/03/mono_developer_meeting.html") from 2004: "Importantly, Miguel (de Icaza, the Novell vice-president who started the Mono project) also said that Ximian had a letter from Microsoft, Intel and HP stating that they would offer *royalty-free* RAND licensing to the ECMA-submitted components of .NET."

Of course, nobody else has ever been shown that letter. One doubts that anybody ever will get to see it, either. One doubts if it even exists.

---

### Post by t4thfavor on 2009-06-29
lol someone ese reads /. Come on, its just software, and it really doesn't infringe on any IP. All Microsoft has on it is the ability to change API's at will. Take it or eave it, its the wave of the future.

---

### Post by entr3p on 2009-06-29
> **t4thfavor said:**
> lol someone ese reads /. Come on, its just software, and it really doesn't infringe on any IP. All Microsoft has on it is the ability to change API's at will. Take it or eave it, its the wave of the future.

I don't really agree that "it's the wave of the future" as I find Vala better than Mono. Also in my opinion it's too slow to even reach the future.

---

### Post by t4thfavor on 2009-06-29
What i meant by that is that CLR languages are the wave of the future, it matters not which one wins, only that we best get comfortable with them as they are here to stay, at least for a while.

Oh, and if your going to quote me at least spell it right, or wrong whichever the case may be.

---

### Post by MountainX on 2009-06-29
> **t4thfavor said:**
> What i meant by that is that CLR languages are the wave of the future, it matters not which one wins, only that we best get comfortable with them as they are here to stay, at least for a while.

Oh, and if your going to quote me at least spell it right, or wrong whichever the case may be.

I just looked up Vala and from what I see it does not appear to be a CLR language. For me, that is a positive. 

I would prefer a future with programming languages that bring modern features without imposing the additional runtime requirements of the CLR. Microsoft likes to make thing more complex than they need to be. There are more elegant (and more simple) ways to solve what the CLR attempts to solve, IMO.

---

### Post by jimv on 2009-06-29
Bleh, not a Mono argument again.  It really boils down to rational people vs people who see MS as some sort of demonic monster.

---

### Post by blackxored on 2009-06-29
Ok. 
More on the same topic. 
Now that Stallman has spoken: [http://www.fsf.org/news/dont-depend-on-mono](http://www.fsf.org/news/dont-depend-on-mono), let me speak myself. 
I'm not agree with risking any free linux distribution because of size. That's mostly why mono is included by default in ubuntu and was accepted in debian. There's no way we couldn't find alternatives to Tomboy, and FSpot ( eyes closed: gThumb, Gnote), so why giving even the possibility we all know about. Free software is about choice, and some choices are better, others are riskier, and then finally others are safer. People have even (extremely IMHO) left ubuntu because of the decision of mono, we can't afford that.

+1 for removing mono, tomboy and fspot.

---

### Post by paul_be on 2009-06-29
I think jumping ship on mono all at once is a bad idea.  It is better to let further development mono app replacements occur.  Many people dont use linux due to "how hard it is to use", and making people use less developed/user friendly apps is worse than relying on mono.  They best solution should be slowly replace mono apps, not strip mono out right now like fedora.
-my two cents

---

### Post by HappyFeet on 2009-06-29
How is mono contributing to the downfall of mankind? Personally, I think there are more important things in this world to worry about.

---

### Post by kerry_s on 2009-06-29
can someone put the output of> **dpkg -l | grep mono**
i would like to see how much is installed. i don't have any on mine, but mines built from the base up & i'm using xfce4.

---

### Post by Bios Element on 2009-06-29
> **kerry_s said:**
> can someone put the output of> **dpkg -l | grep mono**
i would like to see how much is installed. i don't have any on mine, but mines built from the base up & i'm using xfce4.

```
dpkg -l | grep mono
ii  libmono-addins-gui0.2-cil                  0.4-3                                     GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                      0.4-3                                     addin framework for extensible CLI applicati
ii  libmono-cairo2.0-cil                       2.0.1-4                                   Mono Cairo library
ii  libmono-corlib2.0-cil                      2.0.1-4                                   Mono core library (2.0)
ii  libmono-data-tds2.0-cil                    2.0.1-4                                   Mono Data Library
ii  libmono-data2.0-cil                        2.0.1-4                                   Mono.Data.* libraries (2.0)
ii  libmono-getoptions2.0-cil                  2.0.1-4                                   Mono.GetOptions library (2.0)
ii  libmono-i18n2.0-cil                        2.0.1-4                                   Mono I18N libraries (2.0)
ii  libmono-posix2.0-cil                       2.0.1-4                                   Mono.Posix library (2.0)
ii  libmono-security2.0-cil                    2.0.1-4                                   Mono Security library
ii  libmono-sharpzip2.84-cil                   2.0.1-4                                   Mono SharpZipLib library
ii  libmono-sqlite2.0-cil                      2.0.1-4                                   Mono Sqlite library
ii  libmono-system-data2.0-cil                 2.0.1-4                                   Mono System.Data Library
ii  libmono-system-web2.0-cil                  2.0.1-4                                   Mono System.Web Library
ii  libmono-system2.0-cil                      2.0.1-4                                   Mono System libraries (2.0)
ii  libmono-zeroconf1.0-cil                    0.7.6-1ubuntu1                            CLI library for multicast DNS service discov
ii  libmono0                                   2.0.1-4                                   libraries for the Mono JIT
ii  libmono2.0-cil                             2.0.1-4                                   Mono libraries (2.0)
ii  mono-2.0-gac                               2.0.1-4                                   Mono GAC tool
ii  mono-2.0-runtime                           2.0.1-4                                   Mono runtime (2.0)
ii  mono-common                                2.0.1-4                                   common files for Mono
ii  mono-gac                                   2.0.1-4                                   Mono GAC tool
ii  mono-jit                                   2.0.1-4                                   fast CLI JIT/AOT compiler for Mono
ii  mono-runtime                               2.0.1-4                                   Mono runtime
```

---

### Post by Joeb454 on 2009-06-29
Just to add a 2nd list to that :)

```
:~$ dpkg -l | grep mono

ii  libmono-addins-gui0.2-cil                  0.4-3                                     GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                      0.4-3                                     addin framework for extensible CLI applicati
ii  libmono-cairo2.0-cil                       2.0.1-4                                   Mono Cairo library
ii  libmono-corlib1.0-cil                      2.0.1-4                                   Mono core library (1.0)
ii  libmono-corlib2.0-cil                      2.0.1-4                                   Mono core library (2.0)
ii  libmono-data-tds1.0-cil                    2.0.1-4                                   Mono Data library
ii  libmono-data-tds2.0-cil                    2.0.1-4                                   Mono Data Library
ii  libmono-data1.0-cil                        2.0.1-4                                   Mono.Data.* libraries (1.0)
ii  libmono-data2.0-cil                        2.0.1-4                                   Mono.Data.* libraries (2.0)
ii  libmono-dev                                2.0.1-4                                   libraries for the Mono JIT - Development fil
ii  libmono-getoptions1.0-cil                  2.0.1-4                                   Mono.GetOptions library (1.0)
ii  libmono-getoptions2.0-cil                  2.0.1-4                                   Mono.GetOptions library (2.0)
ii  libmono-i18n1.0-cil                        2.0.1-4                                   Mono I18N libraries (1.0)
ii  libmono-i18n2.0-cil                        2.0.1-4                                   Mono I18N libraries (2.0)
ii  libmono-peapi2.0-cil                       2.0.1-4                                   Mono PEAPI library
ii  libmono-posix1.0-cil                       2.0.1-4                                   Mono.Posix library (1.0)
ii  libmono-posix2.0-cil                       2.0.1-4                                   Mono.Posix library (2.0)
ii  libmono-relaxng1.0-cil                     2.0.1-4                                   Mono Relaxng library
ii  libmono-security1.0-cil                    2.0.1-4                                   Mono Security library
ii  libmono-security2.0-cil                    2.0.1-4                                   Mono Security library
ii  libmono-sharpzip0.84-cil                   2.0.1-4                                   Mono SharpZipLib library
ii  libmono-sharpzip2.84-cil                   2.0.1-4                                   Mono SharpZipLib library
ii  libmono-sqlite2.0-cil                      2.0.1-4                                   Mono Sqlite library
ii  libmono-system-data1.0-cil                 2.0.1-4                                   Mono System.Data library
ii  libmono-system-data2.0-cil                 2.0.1-4                                   Mono System.Data Library
ii  libmono-system-runtime1.0-cil              2.0.1-4                                   Mono System.Runtime library
ii  libmono-system-web1.0-cil                  2.0.1-4                                   Mono System.Web library
ii  libmono-system-web2.0-cil                  2.0.1-4                                   Mono System.Web Library
ii  libmono-system1.0-cil                      2.0.1-4                                   Mono System libraries (1.0)
ii  libmono-system2.0-cil                      2.0.1-4                                   Mono System libraries (2.0)
ii  libmono-zeroconf1.0-cil                    0.7.6-1ubuntu1                            CLI library for multicast DNS service discov
ii  libmono0                                   2.0.1-4                                   libraries for the Mono JIT
ii  libmono1.0-cil                             2.0.1-4                                   Mono libraries (1.0)
ii  libmono2.0-cil                             2.0.1-4                                   Mono libraries (2.0)
ii  mono-2.0-devel                             2.0.1-4                                   Mono development tools for CLI 2.0
ii  mono-2.0-gac                               2.0.1-4                                   Mono GAC tool
ii  mono-2.0-runtime                           2.0.1-4                                   Mono runtime (2.0)
ii  mono-common                                2.0.1-4                                   common files for Mono
ii  mono-devel                                 2.0.1-4                                   Mono development tools
ii  mono-gac                                   2.0.1-4                                   Mono GAC tool
ii  mono-gmcs                                  2.0.1-4                                   Mono C# 2.0 and C# 3.0 compiler for CLI 2.0
ii  mono-jit                                   2.0.1-4                                   fast CLI JIT/AOT compiler for Mono
ii  mono-runtime                               2.0.1-4                                   Mono runtime
ii  mono-utils                                 2.0.1-4                                   Mono utilities
ii  monodoc-base                               2.0-2ubuntu2                              shared MonoDoc binaries

```

---

### Post by sloggerkhan on 2009-06-29
Outside of mono vs no mono, I would love for gthumb to be default and fspot to be gone.

---

### Post by directhex on 2009-06-29
> **sloggerkhan said:**
> Outside of mono vs no mono, I would love for gthumb to be default and fspot to be gone.

Unlikely to happen as long as effort is wasted on bitching and moaning rather than making it possible.

Ubuntu has released 6 versions with F-Spot by default. Many users have spent hours tagging their photos with the default photo manager. Any F-Spot replacement would need to adequately import their data from existing F-Spot users to be considered.

---

### Post by HoldSteady on 2009-06-29
> **blackxored said:**
> Ok. 
More on the same topic. 
Now that Stallman has spoken: [http://www.fsf.org/news/dont-depend-on-mono](http://www.fsf.org/news/dont-depend-on-mono), let me speak myself. 
I'm not agree with risking any free linux distribution because of size. That's mostly why mono is included by default in ubuntu and was accepted in debian. There's no way we couldn't find alternatives to Tomboy, and FSpot ( eyes closed: gThumb, Gnote), so why giving even the possibility we all know about. Free software is about choice, and some choices are better, others are riskier, and then finally others are safer. People have even (extremely IMHO) left ubuntu because of the decision of mono, we can't afford that.

+1 for removing mono, tomboy and fspot.
Somewhere around 54 MB of space taken up by trojan horse cruft for three hardly critical apps.

+2 for MonoNoNo [http://tim.thechases.com/mononono/]("http://tim.thechases.com/mononono/")

---

### Post by cariboo on 2009-06-29
Moved to Recurring Discussions. This has nothing to do with Testimonials & Experiences

---

### Post by directhex on 2009-06-29
> **HoldSteady said:**
> +2 for MonoNoNo [http://tim.thechases.com/mononono/]("http://tim.thechases.com/mononono/")

Which fails to work properly, and won't work at all on Karmic

---

### Post by AICollector on 2009-06-29
Right, I'm here today, ladies and gentlemen, to say something;

I am sick and tired of hearing about Mono.

I'm the end user, you know? The sorta guy that apparently shouldn't be using Linux (according to some Windows fanboys I know) because I've never needed any more then two terminal commands?

Now, here's my problem. I've just been looking at a 'discussion' on the Ubuntu devs mailing list. In it was (and I do not say this lightly) a total loon (personal opinion, of course) who serves no other purposes other then to waste people's time and prove to me that there are still people out there who do not think logically. They might as well tell me that Red Hat is controlled by the devil.


Do I consider Mono a threat?

_No. Here's why;_

Mono is a fascinating system, from it we've had many, MANY good applications. Do I think it could pose a risk? Well, Microsoft has never been one to play nice with FOSS, so I imagine that, at the very least, they'll try and think about it's potential uses against us. My own concern is that Ubuntu and other distros may some day come up with a system critical application that could mean the demise of said distros should Microsoft pull a fast one. I would hope people have enough sense to try and avoid that, but that isnt happening now. 
[U]
Do I use Mono apps?[/U]

No again! And again, here's why;

Tomboy is of no use to me, Banshee was good, but heavy on resources. (I have it on my system, but only because it's the only app I've found that can connect to my iPod) GNOME-DO could do with a bit more tweaking before it earned it's place on my desktop (like getting that very nice Docky to sit on the side, instead of the bottom) I switched to Kubuntu.(Surprisingly stable, by the way, after you install WICD, disable desktop effects and get Synaptic) That, as well as me not really caring for resource heavy apps
[U]
What I think Ubuntu should do;
[/U]
If GNOME can be said to do only one thing well, it's stability. However, having tested a Ubuntu system loaded with Mono apps, I can tell you it brings the system to it's knees. I would ask that either Mono be not installed by default (for the simple reason that apps created in it are fairly resource heavy even on modern computers, let alone a four year old one.) Or that a smaller 'lite' version of Ubuntu is created for those older PC's with less in the way of meat, and more in the way of dust.


So, in short; if we become heavily Dependant on Mono, I think we're in a bad way because that can leave us vulnerable (though I am not saying we will be attacked, I am simply stating it as a minute possibility with a high chance of failure if they do) . I do not think, however, that it's inclusion means the death of it. My only concern is that my older computers may not be able to run 9.10 for the simple reason that it's too heavy.

That is all.


PS:Boycott-novell made some interesting accusations, I'd fully understand if the admins just censored out every rant about how horrible Mono is. I would, however, rather like to know why this one was censored (if it ever is)

---

### Post by tubezninja on 2009-06-29
This is probably the most realistic post I've seen on here regarding mono.

---

### Post by starcraft.man on 2009-06-29
3....2....1.... blast off!

I mean BOOOM!!!

---

### Post by Gizenshya on 2009-06-29
what is mono?

I take it he's not talking about the disease...

---

### Post by Skripka on 2009-06-29
> **starcraft.man said:**
> 3....2....1.... blast off!

I mean BOOOM!!!

Ready.

Set.



Recurring Discussions!

---

### Post by dragos240 on 2009-06-29
> **Gizenshya said:**
> what is mono?

I take it he's not talking about the disease...


It's a developing system for unix and unix-like systems for programing and porting programs in C sharp.

---

### Post by Sealbhach on 2009-06-29
It's controversial because it was created by Microsoft, afaik. I don't know what claims they have to it right now though.

.

---

### Post by magmon on 2009-06-29
Meh, I dont see it as a problem even if they say we cant use it. They can take my banshee, but they cant take my ubuntu!

---

### Post by MountainX on 2009-06-29
> **jimv said:**
> Bleh, not a Mono argument again.  It really boils down to rational people vs people who see MS as some sort of demonic monster.

I consider the 2nd type of person to be very observant of Microsoft's actual demonic behavior as well as knowledgeable of their proven criminal behavior. Those who do not recognize this pattern may be irrational or in denial because the facts are public record.

---

### Post by jonian_g on 2009-06-29
I also think that we shouldn't use mono apps because they are heavy in resources and because there could be a potentional problem with MS patents.

I don't use any mono apps. I have no use for tomboy, I don't need F-spot, neither gnome-do and I don't like banshee (I prefer Listen).

The least ubuntu can do for users that don't want mono is make the ubuntu-desktop metapackage non dependant on those apps to avoid problems during upgrades.

---

### Post by zekopeko on 2009-06-29
> **AICollector said:**
> Right, I'm here today, ladies and gentlemen, to say something;

I am sick and tired of hearing about Mono.

I'm the end user, you know? The sorta guy that apparently shouldn't be using Linux (according to some Windows fanboys I know) because I've never needed any more then two terminal commands?

Now, here's my problem. I've just been looking at a 'discussion' on the Ubuntu devs mailing list. In it was (and I do not say this lightly) a total loon (personal opinion, of course) who serves no other purposes other then to waste people's time and prove to me that there are still people out there who do not think logically. They might as well tell me that Red Hat is controlled by the devil.


agreed

> 
Do I consider Mono a threat?

_No. Here's why;_

Mono is a fascinating system, from it we've had many, MANY good applications. Do I think it could pose a risk? Well, Microsoft has never been one to play nice with FOSS, so I imagine that, at the very least, they'll try and think about it's potential uses against us. My own concern is that Ubuntu and other distros may some day come up with a system critical application that could mean the demise of said distros should Microsoft pull a fast one. I would hope people have enough sense to try and avoid that, but that isnt happening now. 


MS has been playing nicely with FLOSS for quite some time. i think that they will move toward a more open model of business since FLOSS dramatically boosts productivity and lowers costs of development. 

> 
[U]
Do I use Mono apps?[/U]

No again! And again, here's why;

Tomboy is of no use to me, Banshee was good, but heavy on resources. (I have it on my system, but only because it's the only app I've found that can connect to my iPod) GNOME-DO could do with a bit more tweaking before it earned it's place on my desktop (like getting that very nice Docky to sit on the side, instead of the bottom) I switched to Kubuntu.(Surprisingly stable, by the way, after you install WICD, disable desktop effects and get Synaptic) That, as well as me not really caring for resource heavy apps

what are your machine specs? i use 9.04 on an Asus 1000HG and Banshee is working without a problem performance-wise.
Gnome-do is also working nicely in every mode except docky which should use some speed tweaks (the zoom functionality to be precise)

> 
[U]
What I think Ubuntu should do;
[/U]
If GNOME can be said to do only one thing well, it's stability. However, having tested a Ubuntu system loaded with Mono apps, I can tell you it brings the system to it's knees. I would ask that either Mono be not installed by default (for the simple reason that apps created in it are fairly resource heavy even on modern computers, let alone a four year old one.) Or that a smaller 'lite' version of Ubuntu is created for those older PC's with less in the way of meat, and more in the way of dust.


Same as above. I don't have a problem running mono apps on a weakly netbook for the most part.

> 
So, in short; if we become heavily Dependant on Mono, I think we're in a bad way because that can leave us vulnerable (though I am not saying we will be attacked, I am simply stating it as a minute possibility with a high chance of failure if they do) . I do not think, however, that it's inclusion means the death of it. My only concern is that my older computers may not be able to run 9.10 for the simple reason that it's too heavy.

That is all.
Lame reasoning is lame. Mono is under the protection of the OIN network. MS would be crazy to start a "thermonuclear" patent war.
The kernel is probably far more alluring target for MS since it can break a lot of stuff. Not to mention that it has a larger code base to attack.

> 
PS:Boycott-novell made some interesting accusations, I'd fully understand if the admins just censored out every rant about how horrible Mono is. I would, however, rather like to know why this one was censored (if it ever is)

BN is a cesspool for intelligent thought and debate. Try to avoid it.

---

### Post by zekopeko on 2009-06-29
> **Sealbhach said:**
> It's controversial because it was created by Microsoft, afaik. I don't know what claims they have to it right now though.

.

You know wrong. Mono is a free software implementation of C#, a standardized computer language that took concepts from Sun's Java and made them better or not suck so much. It also sports a collection of libraries for developing applications.

---

### Post by monsterstack on 2009-06-29
> **zekopeko said:**
> MS has been playing nicely with FLOSS for quite some time. i think that they will move toward a more open model of business since FLOSS dramatically boosts productivity and lowers costs of development. 

Hahaha.

---

### Post by GCFreak on 2009-06-30
> **zekopeko said:**
> You know wrong. Mono is a free software implementation of C#, a standardized computer language that took concepts from Sun's Java and made them better or not suck so much. It also sports a collection of libraries for developing applications.

I'd hardly call C# standardised (even though it is ECMA and ISO standards, but still) for the simple fact is that Microsoft doesn't do much in the way of standardisation with all the other implementations other than its own. C#, a language designed by Microsoft, for Microsoft, screwing everyone who tries to help them make it open, and better.

EDIT: If C# WAS a proper standard, like everything else non-Microsoft is, we would not have these silly, unnecessary legal issues in the first place.

---

### Post by cariboo on 2009-06-30
I'm getting a little bit tired of open source advocates trying to limit my freedom of choice. Using a Linux distribution is all about freedom of choice, If I choose to use a mono based application, it should be up to me, not what someone thinks may be a problem some time down the road. If we get rid of mono, maybe we should also get rid of wine, as some day there may be a patent infringement lawsuit against it too.

---

### Post by directhex on 2009-06-30
> **cariboo907 said:**
> I'm getting a little bit tired of open source advocates trying to limit my freedom of choice. Using a Linux distribution is all about freedom of choice, If I choose to use a mono based application, it should be up to me, not what someone thinks may be a problem some time down the road. If we get rid of mono, maybe we should also get rid of wine, as some day there may be a patent infringement lawsuit against it too.

All software is Free, but some is more Free than others

---

### Post by Bigtime_Scrub on 2009-06-30
> **kerry_s said:**
> can someone put the output of> **dpkg -l | grep mono**
i would like to see how much is installed. i don't have any on mine, but mines built from the base up & i'm using xfce4.



Here you go. 

```
gary@gary-laptop:~$ dpkg -l | grep mono
ii  libmono-addins-gui0.2-cil                  0.4-3                                     GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                      0.4-3                                     addin framework for extensible CLI applicati
ii  libmono-cairo2.0-cil                       2.0.1-4                                   Mono Cairo library
ii  libmono-corlib2.0-cil                      2.0.1-4                                   Mono core library (2.0)
ii  libmono-data-tds2.0-cil                    2.0.1-4                                   Mono Data Library
ii  libmono-data2.0-cil                        2.0.1-4                                   Mono.Data.* libraries (2.0)
ii  libmono-getoptions2.0-cil                  2.0.1-4                                   Mono.GetOptions library (2.0)
ii  libmono-i18n2.0-cil                        2.0.1-4                                   Mono I18N libraries (2.0)
ii  libmono-posix2.0-cil                       2.0.1-4                                   Mono.Posix library (2.0)
ii  libmono-security2.0-cil                    2.0.1-4                                   Mono Security library
ii  libmono-sharpzip2.84-cil                   2.0.1-4                                   Mono SharpZipLib library
ii  libmono-sqlite2.0-cil                      2.0.1-4                                   Mono Sqlite library
ii  libmono-system-data2.0-cil                 2.0.1-4                                   Mono System.Data Library
ii  libmono-system-web2.0-cil                  2.0.1-4                                   Mono System.Web Library
ii  libmono-system2.0-cil                      2.0.1-4                                   Mono System libraries (2.0)
ii  libmono0                                   2.0.1-4                                   libraries for the Mono JIT
ii  libmono2.0-cil                             2.0.1-4                                   Mono libraries (2.0)
ii  mono-2.0-gac                               2.0.1-4                                   Mono GAC tool
ii  mono-2.0-runtime                           2.0.1-4                                   Mono runtime (2.0)
ii  mono-common                                2.0.1-4                                   common files for Mono
ii  mono-gac                                   2.0.1-4                                   Mono GAC tool
ii  mono-jit                                   2.0.1-4                                   fast CLI JIT/AOT compiler for Mono
ii  mono-runtime                               2.0.1-4                                   Mono runtime
gary@gary-laptop:~$ 

```

---

### Post by Grant A. on 2009-06-30
To everyone bitching about Mono, please read this [very insightful essay on Mono about why it does not pose a threat, and why it does not "suck".]("http://www2.apebox.org/wordpress/rants/124/")

---

### Post by k2t0f12d on 2009-06-30
> **cariboo907 said:**
> I'm getting a little bit tired of open source advocates trying to limit my freedom of choice.I'm getting a little bit tired of reading one dimensional posts blaming free software advocates for steal'n ur apps. Stallman's advice makes sense. By all means, keep up development on free implementations of NET, but keep it on the sidelines until its legality is certain. For all the BS that gets tossed around here, one thing staff is supposed to do is keep the forum free of stuff that could be illegal. Now I would have thought that the possibility that NET implementation might not be legal to reproduce is something you would be sensitive to. Staff never shut up about legality when derailing threads about copyright reform, but let free software advocates mention caution and suddenly its the other way around.

> **cariboo907 said:**
> Using a Linux distribution is all about freedom of choice, If I choose to use a mono based application, it should be up to me, not what someone thinks may be a problem some time down the road.Freedom is why Stallman shared his advice with you to consider, so you can make your own choice, instead of sneaking onto your computer and deleting Mono without your permission. Name a single program for me that free software ever took away from you, or quit your whining.

> **cariboo907 said:**
> If we get rid of mono, maybe we should also get rid of wine, as some day there may be a patent infringement lawsuit against it too.Demagoguery. WINE cannot be integrated into a GNU+Linux platform in a compromising way because the executables it supports are not native. If WINE goes, GNU+Linux is left exactly the same, intact. Is WINE installed on Ubuntu by default with some standard w32 apps? Didn't think so. Neither should Mono *until its legality is fully confirmed*. Full stop.

---

### Post by Dragonbite on 2009-06-30
> **jimv said:**
> Bleh, not a Mono argument again.  It really boils down to rational people vs people who see MS as some sort of demonic monster.

> **MountainX said:**
> I consider the 2nd type of person to be very observant of Microsoft's actual demonic behavior as well as knowledgeable of their proven criminal behavior. Those who do not recognize this pattern may be irrational or in denial because the facts are public record.

Yup.. looks like another Mono argument again.

---

### Post by 3rdalbum on 2009-06-30
If it's dangerous to use Mono because of the possibility of a submarine patent, or the possibility that Microsoft will object to using a language that they invented: Why do people still use Wine? That *reimplements* the Win32 API which has got to be more risky than anything Mono is doing. Microsoft don't even claim to be able to provide anyone with a fair license to implement w32.

---

### Post by Bios Element on 2009-06-30
> **k2t0f12d said:**
> I'm getting a little bit tired of reading one dimensional posts blaming free software advocates for steal'n ur apps. Stallman's advice makes sense. By all means, keep up development on free implementations of NET, but keep it on the sidelines until its legality is certain. For all the BS that gets tossed around here, one thing staff is supposed to do is keep the forum free of stuff that could be illegal. Now I would have thought that the possibility that NET implementation might not be legal to reproduce is something you would be sensitive to. Staff never shut up about legality when derailing threads about copyright reform, but let free software advocates mention caution and suddenly its the other way around.

Freedom is why Stallman shared his advice with you to consider, so you can make your own choice, instead of sneaking onto your computer and deleting Mono without your permission. Name a single program for me that free software ever took away from you, or quit your whining.

Demagoguery. WINE cannot be integrated into a GNU+Linux platform in a compromising way because the executables it supports are not native. If WINE goes, GNU+Linux is left exactly the same, intact. Is WINE installed on Ubuntu by default with some standard w32 apps? Didn't think so. Neither should Mono *until its legality is fully confirmed*. Full stop.

Why don't you just purge mono and move on with your life rather then waste your time trying to impose your opinion on everyone else? Anyway, Microsoft claims Linux is illegal too and has yet to prove it. Maybe we should just shutdown until Linux is Microsoft Certified as well?

---

### Post by jonian_g on 2009-06-30
> **Grant A. said:**
> To everyone bitching about Mono, please read this [very insightful essay on Mono about why it does not pose a threat, and why it does not "suck".]("http://www2.apebox.org/wordpress/rants/124/")

A totaly unbiased article by Jo Shields, a mono packager from debian. This guy insults the gnote author in every blog I have come across. He is a nono defender and I can not believe him. He even acuses people in that article without providing links.

---

### Post by directhex on 2009-06-30
> **jonian_g said:**
> A totaly unbiased article by Jo Shields, a mono packager from debian. This guy insults the gnote author in every blog I have come across. He is a nono defender and I can not believe him. He even acuses people in that article without providing links.

Boycott Novell commenters calling for death:
[http://boycottnovell.com/2009/06/09/mono-critique-for-ubuntu/#comment-65907](http://boycottnovell.com/2009/06/09/mono-critique-for-ubuntu/#comment-65907)
[http://boycottnovell.com/2009/01/21/death-by-microsoft-windows/#comment-58764](http://boycottnovell.com/2009/01/21/death-by-microsoft-windows/#comment-58764)
(not an exhaustive list - cannot be bothered to search for site:boycottnovell.com $METHOD_OF_DEATH for every imaginable killing strategy)

Third parties claiming (with evidence) affiliation with Boycott Novell trying to have people fired for not agreeing with them:
[http://opensourcetogo.blogspot.com/2009/06/when-zeal-becomes-zealotry-tawdry-tale.html](http://opensourcetogo.blogspot.com/2009/06/when-zeal-becomes-zealotry-tawdry-tale.html)

Boycott Novell commenters comparing Mono to cancer:
[http://www.theopensourcerer.com/2009/05/04/re-spinning-famous-quotes-linux-and-cancer/](http://www.theopensourcerer.com/2009/05/04/re-spinning-famous-quotes-linux-and-cancer/)

Unrepentant attacks against pretty much anyone:
[http://boycottnovell.com/2008/12/29/jimmi-hugh-wikipedia-censorship-on-ms/](http://boycottnovell.com/2008/12/29/jimmi-hugh-wikipedia-censorship-on-ms/)

Any other points you'd like to raise? Oh, and since you asked, the reason for the lack of hyperlinks was a conscious decision to avoid possibly confusing layout in the GPG-signed plain text of the original - that and not wanting to spend more than the three hours I already did.

---

### Post by jonian_g on 2009-06-30
> **directhex said:**
> Boycott Novell commenters calling for death:
[http://boycottnovell.com/2009/06/09/mono-critique-for-ubuntu/#comment-65907](http://boycottnovell.com/2009/06/09/mono-critique-for-ubuntu/#comment-65907)
[http://boycottnovell.com/2009/01/21/death-by-microsoft-windows/#comment-58764](http://boycottnovell.com/2009/01/21/death-by-microsoft-windows/#comment-58764)
(not an exhaustive list - cannot be bothered to search for site:boycottnovell.com $METHOD_OF_DEATH for every imaginable killing strategy)

Third parties claiming (with evidence) affiliation with Boycott Novell trying to have people fired for not agreeing with them:
[http://opensourcetogo.blogspot.com/2009/06/when-zeal-becomes-zealotry-tawdry-tale.html](http://opensourcetogo.blogspot.com/2009/06/when-zeal-becomes-zealotry-tawdry-tale.html)

Boycott Novell commenters comparing Mono to cancer:
[http://www.theopensourcerer.com/2009/05/04/re-spinning-famous-quotes-linux-and-cancer/](http://www.theopensourcerer.com/2009/05/04/re-spinning-famous-quotes-linux-and-cancer/)

Unrepentant attacks against pretty much anyone:
[http://boycottnovell.com/2008/12/29/jimmi-hugh-wikipedia-censorship-on-ms/](http://boycottnovell.com/2008/12/29/jimmi-hugh-wikipedia-censorship-on-ms/)

Any other points you'd like to raise? Oh, and since you asked, the reason for the lack of hyperlinks was a conscious decision to avoid possibly confusing layout in the GPG-signed plain text of the original - that and not wanting to spend more than the three hours I already did.

Should I assume you are Jo Shields?

I never said I agree with boycott novel (I have read only their articles linked at linuxinsider and lxer).

My point is that their opinions are biased and so are Jo Shields. The words that Jo Shields used against the gnote author don't make him any better than boycott novel.

I don't give a sh*t about mono since I don't use any mono apps. Ubuntu/Debian can do what they want with mono. If someone disagrees, then he should switch to fedora or any other mono-free distro.

And, by the way, I don't understand your agression against me.

---

### Post by MountainX on 2009-06-30
> **Dragonbite said:**
> Yup.. looks like another Mono argument again.

Well, this has become a current news item due to the Debian decision regarding Mono. Therefore, it is not just a rehash of an old discussion. 

I was not aware of the mono issues previously. After reading a bit, the issues seem totally different from Wine. I can't repeat all the details. But Microsoft's strategy is to get the open source community to write new applications on Microsoft's platforms. This is a way to undermine Linux. 

With Wine, we bring Windows apps into the Linux world. But with Mono, we end up writing new apps that target a platform technology designed and invented by Microsoft. With Wine, the development effort goes into the tool itself. If Wine were to disappear (which I do not think is a risk), no Linux-targeted open source apps would be affected.

With Mono, new development effort goes into the tool as well as new applications. If Mono becomes unavailable under a free license, and if all the best new apps over several years have been targeted to Mono, users of Linux will suffer a big setback and they will have to invest a lot of time and effort (and money) to port all those apps so they will run without Mono. Since we can develop such new apps now without Mono, and they can probably be developed just as easily without Mono, why subject the community to the risk? Even worse, why embrace a technology MS created? Sure, the CLR seems cool. Sure, writing C# GUI code is really easy compared to C or C++. But once one has used these technologies long enough for the cool factor to wear off, it becomes more obvious that the problems these technologies are designed to solve can be solved more elegantly with less complex approaches (e.g., using the Unix philosophy).

Linux is built on the Unix philosophy. Mono seems to undermine that foundation of Linux. 

Microsoft sees the .NET framework as the future of its operating system. Almost every Windows API is going to be moved to .NET. The .NET Framework is becoming the operating system. Microsoft would love to see Mono become entrenched in Linux. Mono could be a trojan horse in my mind.

---

### Post by eragon100 on 2009-06-30
edward@alchemy-lab:~$ dpkg -l | grep mono
ii  libmono-accessibility2.0-cil               2.0.1-4                                   Mono Accessibility library
ii  libmono-addins-gui0.2-cil                  0.4-3                                     GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                      0.4-3                                     addin framework for extensible CLI applications/libraries
ii  libmono-cairo2.0-cil                       2.0.1-4                                   Mono Cairo library
ii  libmono-corlib1.0-cil                      2.0.1-4                                   Mono core library (1.0)
ii  libmono-corlib2.0-cil                      2.0.1-4                                   Mono core library (2.0)
ii  libmono-data-tds1.0-cil                    2.0.1-4                                   Mono Data library
ii  libmono-data-tds2.0-cil                    2.0.1-4                                   Mono Data Library
ii  libmono-data1.0-cil                        2.0.1-4                                   Mono.Data.* libraries (1.0)
ii  libmono-data2.0-cil                        2.0.1-4                                   Mono.Data.* libraries (2.0)
ii  libmono-dev                                2.0.1-4                                   libraries for the Mono JIT - Development files
ii  libmono-getoptions1.0-cil                  2.0.1-4                                   Mono.GetOptions library (1.0)
ii  libmono-getoptions2.0-cil                  2.0.1-4                                   Mono.GetOptions library (2.0)
ii  libmono-i18n1.0-cil                        2.0.1-4                                   Mono I18N libraries (1.0)
ii  libmono-i18n2.0-cil                        2.0.1-4                                   Mono I18N libraries (2.0)
ii  libmono-peapi2.0-cil                       2.0.1-4                                   Mono PEAPI library
ii  libmono-posix1.0-cil                       2.0.1-4                                   Mono.Posix library (1.0)
ii  libmono-posix2.0-cil                       2.0.1-4                                   Mono.Posix library (2.0)
ii  libmono-relaxng1.0-cil                     2.0.1-4                                   Mono Relaxng library
ii  libmono-security1.0-cil                    2.0.1-4                                   Mono Security library
ii  libmono-security2.0-cil                    2.0.1-4                                   Mono Security library
ii  libmono-sharpzip0.84-cil                   2.0.1-4                                   Mono SharpZipLib library
ii  libmono-sharpzip2.84-cil                   2.0.1-4                                   Mono SharpZipLib library
ii  libmono-sqlite2.0-cil                      2.0.1-4                                   Mono Sqlite library
ii  libmono-system-data1.0-cil                 2.0.1-4                                   Mono System.Data library
ii  libmono-system-data2.0-cil                 2.0.1-4                                   Mono System.Data Library
ii  libmono-system-runtime1.0-cil              2.0.1-4                                   Mono System.Runtime library
ii  libmono-system-runtime2.0-cil              2.0.1-4                                   Mono System.Runtime Library
ii  libmono-system-web1.0-cil                  2.0.1-4                                   Mono System.Web library
ii  libmono-system-web2.0-cil                  2.0.1-4                                   Mono System.Web Library
ii  libmono-system1.0-cil                      2.0.1-4                                   Mono System libraries (1.0)
ii  libmono-system2.0-cil                      2.0.1-4                                   Mono System libraries (2.0)
ii  libmono-webbrowser0.5-cil                  2.0.1-4                                   Mono Web Browser library
ii  libmono-winforms2.0-cil                    2.0.1-4                                   Mono System.Windows.Forms library
ii  libmono-zeroconf1.0-cil                    0.7.6-1ubuntu1                            CLI library for multicast DNS service discovery
ii  libmono0                                   2.0.1-4                                   libraries for the Mono JIT
ii  libmono1.0-cil                             2.0.1-4                                   Mono libraries (1.0)
ii  libmono2.0-cil                             2.0.1-4                                   Mono libraries (2.0)
ii  mono-2.0-devel                             2.0.1-4                                   Mono development tools for CLI 2.0
ii  mono-2.0-gac                               2.0.1-4                                   Mono GAC tool
ii  mono-2.0-runtime                           2.0.1-4                                   Mono runtime (2.0)
ii  mono-common                                2.0.1-4                                   common files for Mono
ii  mono-devel                                 2.0.1-4                                   Mono development tools
ii  mono-gac                                   2.0.1-4                                   Mono GAC tool
ii  mono-gmcs                                  2.0.1-4                                   Mono C# 2.0 and C# 3.0 compiler for CLI 2.0
ii  mono-jit                                   2.0.1-4                                   fast CLI JIT/AOT compiler for Mono
ii  mono-runtime                               2.0.1-4                                   Mono runtime
ii  mono-utils                                 2.0.1-4                                   Mono utilities
ii  monodevelop                                2.0+dfsg-2ubuntu1                         Development Environment for GNOME
ii  monodoc-base                               2.0-2ubuntu2                              shared MonoDoc binaries
ii  monodoc-manual                             2.0-2ubuntu2                              compiled XML documentation from the Mono project
edward@alchemy-lab:~$ 

I use f-spot for photos and banshee for playing music and videos. I don't care if it uses mono or not, I simply like those apps so I use them. Period. If I would switch to another photo manager, it would be picasa, which is even open-source and is in fact a windows app bundled with wine. I don't care. It works, it's pleasant to use, and it doesn't cost money. Period. End of story. I also use the Nvidia propietary driver, to play games, a lot of which are commercial. I even pay for these games. Why? Because I have fun playing them. I have every non-free coded installed on my system. Why? Because I like to watch a lot of anime, and fansubs are usually in non-free formats. I have fun watching them, so I do.

By the way, I also use opera as my default web browser, and I like to see nice sights in google earth too. I do use the open-source evince instead of adobe reader, but only because I like it better. It loads documents faster. If the speed advantage would have been the other way around, I would use adobe reader without giving it a second tought.

Keep in mind that I am going to study computer science, so it's not like I don't know what free software is about. I. just. don't. care.

Have a nice day everyone and could you people please stop whining about what other users should and should not run on their computers, because of some stupid "moral issues"? Thanks. Some people just want to get the most out of their &#8364;700,- machines.

---

### Post by RiceMonster on 2009-06-30
> **eragon100 said:**
> I use f-spot for photos and banshee for playing music and videos. I don't care if it uses mono or not, I simply like those apps so I use them. Period. If I would switch to another photo manager, it would be picasa, which is even open-source and is in fact a windows app bundled with wine. I don't care. It works, it's pleasant to use, and it doesn't cost money. Period. End of story. I also use the Nvidia propietary driver, to play games, a lot of which are commercial. I even pay for these games. Why? Because I have fun playing them. I have every non-free coded installed on my system. Why? Because I like to watch a lot of anime, and fansubs are usually in non-free formats. I have fun watching them, so I do.

By the way, I also use opera as my default web browser, and I like to see nice sights in google earth too. I do use the open-source evince instead of adobe reader, but only because I like it better. It loads documents faster. If the speed advantage would have been the other way around, I would use adobe reader without giving it a second tought.

Keep in mind that I am going to study computer science, so it's not like I don't know what free software is about. I. just. don't. care.

Have a nice day everyone and could you people please stop whining about what other users should and should not run on their computers, because of some stupid "moral issues"? Thanks. Some people just want to get the most out of their €700,- machines.

I could not agree more. Such a simple concept that some people just cannot grasp.

---

### Post by directhex on 2009-06-30
> **jonian_g said:**
> My point is that their opinions are biased and so are Jo Shields.

I think I covered that in the signature on the original post.

> The words that Jo Shields used against the gnote author don't make him any better than boycott novel.

Sorry, but
[list]
[*] Claiming your line-for-line port of someone else's app is 100% your own work
[*] Telling people you don't care if your app writes incompatible notes as you wish to encourage lock-in
[*] Relicensing in a 1-way way, to ensure none of your code can move back to the parent project
[/list]

These are all, especially when taken together, dick moves. I said at the time that Gnote was impressive work (shame about the current note-corrupting bug in 0.5), but that doesn't excuse behaving like an ***. There are plenty of talented Free Software people who behave that way - say, Schilling or Drepper. If Hub was interested in writing a *friendly* fork of Tomboy, then the alternative behaviour would have been to
[list]
[*] Contact Tomboy upstream, and request that they clarify copyright holders of all un-headered files, to ensure due credit is given
[*] Consider any incompatibilities in written notes a critical flaw, especially when claiming to be compatible on your website (rather than blaming Tomboy for somehow not reading its own notes). And don't reject suggestions from Tomboy upstream to collaborate on a note format
[*] Keep the same license as Tomboy for any ported files, to ensure 2-way cooperation is possible. Use GPLv3 only for new add-ins not ported from Tomboy
[/list]

See the difference between list 1 and list 2?

> I don't give a sh*t about mono since I don't use any mono apps. Ubuntu/Debian can do what they want with mono. If someone disagrees, then he should switch to fedora or any other mono-free distro.

That's the spirit! People who disagree should also consider the option of working on alternative apps, to make them better, such that the Mono apps get dropped.

> And, by the way, I don't understand your agression against me.

What aggression? You would prefer, perhaps, a hug?

---

### Post by jonian_g on 2009-06-30
> **directhex said:**
> What aggression? You would prefer, perhaps, a hug?

Cut the crap!

---

### Post by Dragonbite on 2009-06-30
> **MountainX said:**
> If Mono becomes unavailable under a free license, and if all the best new apps over several years have been targeted to Mono, users of Linux will suffer a big setback and they will have to invest a lot of time and effort (and money) to port all those apps so they will run without Mono. Since we can develop such new apps now without Mono, and they can probably be developed just as easily without Mono, why subject the community to the risk? 

There already are, and at the fist whiff of anything going down with Mono, then Mono would be dropped like a hot potato and replaced with the closest equivalent applications.
[LIST]
[*]Banshee can be replaced by Rythmbox, Listen, Exaile, and many more.
[*]Tomboy can be replaced with gNotes
[*]Beagle can be replaced with Tracker
[*]F-Spot... well it isn't the best but nobody's bothered to build a replacement for Gnome for photomanaging and gThumbs, while nice, doesn't quite make it.  Currently Picasa (via Wine) is the best alternative.
[/LIST]

So instead of cutting off a number of developers who have already produced Banshee, Tomboy, Beagle and F-Spot just because of the Mono platform boogeyman and possibly loosing them completely (depends on how ingrained they are with Mono and C#) as well as the gaming engines running on Mono, have whomever feels so strongly against it produce license-free alternatives good enough to replace the Mono-based ones. Or use KDE. There are very few KDE-based Mono applications (Kerry, the Beagle with KDE front-end is the only one I know of).

Not sure how Mono "undermine that foundation of Linux." because Mono CAN be removed/replaced, because people HAVE the choice to do that.  Just because Ubuntu or Debian chooses to go one way or the other doesn't mean you have to choose to use them or keep them.

And what about the benefits to Linux in cross-compatibility?

---

### Post by zoomy942 on 2009-06-30
this is the third thread i have seen about mono..
what is it and why is it bad?  I dont understand fully.

---

### Post by directhex on 2009-06-30
> **zoomy942 said:**
> this is the third thread i have seen about mono..
what is it and why is it bad?  I dont understand fully.

It's an implementation of ECMA334 and ECMA335

And it's bad because Microsoft are the guys who filed those 2 standards.

That's the short version

---

### Post by directhex on 2009-06-30
> **MountainX said:**
> Since we can develop such new apps now without Mono, and they can probably be developed just as easily without Mono, why subject the community to the risk?

Define "we"

If "we" means "everyone who isn't a developer on apps like Tomboy, F-Spot, banshee, Muine, Drapes, Cowbell, GNOME Do, Beagle, etc etc etc", then why not do it? Nobody is going to bundle Mono apps if the non-Mono apps are better. Why doesn't someone stop moaning and make credible alternatives which make the Desktop Team (who make the decisions over default apps in Ubuntu) go "wow, we should totally use this by default"? And no, that doesn't mean half-arsed "QUICK NOW!!" changes to apps like Gnote with no record for stability (and, in fact, now a record for corrupting users' notes), it means moving to clearly superior apps which, amongst other things, contain a clear migration path (importing any and all important data from the "legacy" Mono app). Make non-Mono apps rock, and the problem solves itself. Bin Mono with no regard to whether the alternatives are any better, and make Ubuntu categorically worse for its users. And, again, this is not an urgent question - Ubuntu has shipped Mono apps in the default install since 2006. Nothing's changed.

If "we" means "everyone, including those who **ARE** developers on apps like Tomboy, F-Spot, banshee, Muine, Drapes, Cowbell, GNOME Do, Beagle, etc etc etc, i.e. the Free Software world at large" then have you considered allowing developers to pick their own tools, rather than mandating a "permitted list" to them?

---

### Post by zoomy942 on 2009-06-30
> **directhex said:**
> It's an implementation of ECMA334 and ECMA335

And it's bad because Microsoft are the guys who filed those 2 standards.

That's the short version

fair enough.  so how does that affect standard users?

---

### Post by directhex on 2009-06-30
> **zoomy942 said:**
> fair enough.  so how does that affect standard users?

Tomboy and F-Spot are apps written using Mono (along with a bucket of Linux-targeted libraries such as GTK# for the GUI). And are in the default install.

---

### Post by [h2o] on 2009-06-30
> **zoomy942 said:**
> fair enough.  so how does that affect standard users?
Most likely not at all.
If you are (in my opinion) the paranoid kind of person, then you might see Mono as some sort of Doomsday device planted by Microsoft to kill Linux.

---

### Post by karellen on 2009-06-30
> **eragon100 said:**
> edward@alchemy-lab:~$ dpkg -l | grep mono
ii  libmono-accessibility2.0-cil               2.0.1-4                                   Mono Accessibility library
ii  libmono-addins-gui0.2-cil                  0.4-3                                     GTK# frontend library for Mono.Addins
ii  libmono-addins0.2-cil                      0.4-3                                     addin framework for extensible CLI applications/libraries
ii  libmono-cairo2.0-cil                       2.0.1-4                                   Mono Cairo library
ii  libmono-corlib1.0-cil                      2.0.1-4                                   Mono core library (1.0)
ii  libmono-corlib2.0-cil                      2.0.1-4                                   Mono core library (2.0)
ii  libmono-data-tds1.0-cil                    2.0.1-4                                   Mono Data library
ii  libmono-data-tds2.0-cil                    2.0.1-4                                   Mono Data Library
ii  libmono-data1.0-cil                        2.0.1-4                                   Mono.Data.* libraries (1.0)
ii  libmono-data2.0-cil                        2.0.1-4                                   Mono.Data.* libraries (2.0)
ii  libmono-dev                                2.0.1-4                                   libraries for the Mono JIT - Development files
ii  libmono-getoptions1.0-cil                  2.0.1-4                                   Mono.GetOptions library (1.0)
ii  libmono-getoptions2.0-cil                  2.0.1-4                                   Mono.GetOptions library (2.0)
ii  libmono-i18n1.0-cil                        2.0.1-4                                   Mono I18N libraries (1.0)
ii  libmono-i18n2.0-cil                        2.0.1-4                                   Mono I18N libraries (2.0)
ii  libmono-peapi2.0-cil                       2.0.1-4                                   Mono PEAPI library
ii  libmono-posix1.0-cil                       2.0.1-4                                   Mono.Posix library (1.0)
ii  libmono-posix2.0-cil                       2.0.1-4                                   Mono.Posix library (2.0)
ii  libmono-relaxng1.0-cil                     2.0.1-4                                   Mono Relaxng library
ii  libmono-security1.0-cil                    2.0.1-4                                   Mono Security library
ii  libmono-security2.0-cil                    2.0.1-4                                   Mono Security library
ii  libmono-sharpzip0.84-cil                   2.0.1-4                                   Mono SharpZipLib library
ii  libmono-sharpzip2.84-cil                   2.0.1-4                                   Mono SharpZipLib library
ii  libmono-sqlite2.0-cil                      2.0.1-4                                   Mono Sqlite library
ii  libmono-system-data1.0-cil                 2.0.1-4                                   Mono System.Data library
ii  libmono-system-data2.0-cil                 2.0.1-4                                   Mono System.Data Library
ii  libmono-system-runtime1.0-cil              2.0.1-4                                   Mono System.Runtime library
ii  libmono-system-runtime2.0-cil              2.0.1-4                                   Mono System.Runtime Library
ii  libmono-system-web1.0-cil                  2.0.1-4                                   Mono System.Web library
ii  libmono-system-web2.0-cil                  2.0.1-4                                   Mono System.Web Library
ii  libmono-system1.0-cil                      2.0.1-4                                   Mono System libraries (1.0)
ii  libmono-system2.0-cil                      2.0.1-4                                   Mono System libraries (2.0)
ii  libmono-webbrowser0.5-cil                  2.0.1-4                                   Mono Web Browser library
ii  libmono-winforms2.0-cil                    2.0.1-4                                   Mono System.Windows.Forms library
ii  libmono-zeroconf1.0-cil                    0.7.6-1ubuntu1                            CLI library for multicast DNS service discovery
ii  libmono0                                   2.0.1-4                                   libraries for the Mono JIT
ii  libmono1.0-cil                             2.0.1-4                                   Mono libraries (1.0)
ii  libmono2.0-cil                             2.0.1-4                                   Mono libraries (2.0)
ii  mono-2.0-devel                             2.0.1-4                                   Mono development tools for CLI 2.0
ii  mono-2.0-gac                               2.0.1-4                                   Mono GAC tool
ii  mono-2.0-runtime                           2.0.1-4                                   Mono runtime (2.0)
ii  mono-common                                2.0.1-4                                   common files for Mono
ii  mono-devel                                 2.0.1-4                                   Mono development tools
ii  mono-gac                                   2.0.1-4                                   Mono GAC tool
ii  mono-gmcs                                  2.0.1-4                                   Mono C# 2.0 and C# 3.0 compiler for CLI 2.0
ii  mono-jit                                   2.0.1-4                                   fast CLI JIT/AOT compiler for Mono
ii  mono-runtime                               2.0.1-4                                   Mono runtime
ii  mono-utils                                 2.0.1-4                                   Mono utilities
ii  monodevelop                                2.0+dfsg-2ubuntu1                         Development Environment for GNOME
ii  monodoc-base                               2.0-2ubuntu2                              shared MonoDoc binaries
ii  monodoc-manual                             2.0-2ubuntu2                              compiled XML documentation from the Mono project
edward@alchemy-lab:~$ 

I use f-spot for photos and banshee for playing music and videos. I don't care if it uses mono or not, I simply like those apps so I use them. Period. If I would switch to another photo manager, it would be picasa, which is even open-source and is in fact a windows app bundled with wine. I don't care. It works, it's pleasant to use, and it doesn't cost money. Period. End of story. I also use the Nvidia propietary driver, to play games, a lot of which are commercial. I even pay for these games. Why? Because I have fun playing them. I have every non-free coded installed on my system. Why? Because I like to watch a lot of anime, and fansubs are usually in non-free formats. I have fun watching them, so I do.

By the way, I also use opera as my default web browser, and I like to see nice sights in google earth too. I do use the open-source evince instead of adobe reader, but only because I like it better. It loads documents faster. If the speed advantage would have been the other way around, I would use adobe reader without giving it a second tought.

Keep in mind that I am going to study computer science, so it's not like I don't know what free software is about. I. just. don't. care.

Have a nice day everyone and could you people please stop whining about what other users should and should not run on their computers, because of some stupid "moral issues"? Thanks. Some people just want to get the most out of their €700,- machines.

+ 1 from me

---

### Post by zekopeko on 2009-06-30
> **jonian_g said:**
> Cut the crap!

aren't you aggressive? here's a hug.

---

### Post by betrunkenaffe on 2009-06-30
> **Bios Element said:**
> Why don't you just purge mono and move on with your life rather then waste your time trying to impose your opinion on everyone else? Anyway, Microsoft claims Linux is illegal too and has yet to prove it. Maybe we should just shutdown until Linux is Microsoft Certified as well?

Call me crazy but I had the same thoughts, doesn't matter what any one person does. Even the Stallman statement was a request that people don't develop in C# or as minimal as possible.

So I decided to try doing a purge, still have mono-common and libmono0 but I might need to reboot for those to disappear. For those that feel it is too much work, it took me 5 minutes (4 reading random other stuff).

---

### Post by eragon100 on 2009-06-30
> **betrunkenaffe said:**
> Call me crazy but I had the same thoughts, doesn't matter what any one person does. Even the Stallman statement was a request that people don't develop in C# or as minimal as possible.

So I decided to try doing a purge, still have mono-common and libmono0 but I might need to reboot for those to disappear. For those that feel it is too much work, it took me 5 minutes (4 reading random other stuff).

As stated above: my favorite media player (as well as quite a few other programs I use) is mono-based (banshee), so I am not going to purge it.

---

### Post by .Maleficus. on 2009-06-30
Sticky!  Please oh please sticky this so the Mono threads can stop!


Edit:  Nevermind :) and thank you.

---

### Post by jimv on 2009-06-30
> **3rdalbum said:**
> If it's dangerous to use Mono because of the possibility of a submarine patent, or the possibility that Microsoft will object to using a language that they invented: Why do people still use Wine? That *reimplements* the Win32 API which has got to be more risky than anything Mono is doing. Microsoft don't even claim to be able to provide anyone with a fair license to implement w32.

Your logic is solid.  I don't understand it either.

---

### Post by MountainX on 2009-06-30
> **jimv said:**
> Your logic is solid.
The logic is not *that* solid... I can see several holes in it and I'm not an expert on this subject.

> **jimv said:**
> I don't understand it either.

I believe it is worth getting the full story so we understand both side of the argument. Here are some links I'm looking at now:
[http://boycottnovell.com/2009/06/13/suse-mono-good-for-windows/](http://boycottnovell.com/2009/06/13/suse-mono-good-for-windows/)
[http://boycottnovell.com/2009/05/25/licence-microsoft-moonlight-mono/](http://boycottnovell.com/2009/05/25/licence-microsoft-moonlight-mono/)
[http://www.heise.de/english/newsticker/news/141254](http://www.heise.de/english/newsticker/news/141254)
[http://www.osnews.com/story/8712](http://www.osnews.com/story/8712)

Mono is based on a standard designed and invented by Microsoft.

[SIZE=4]*&#8220;Every line of code that is written to our standards is a small victory; every line of code that is written to any other standard, is a small defeat.&#8221;*[/SIZE]
 [RIGHT]                                 &#8211;[SIZE=2][James Plamondon, Microsoft Technical Evangelist]("http://boycottnovell.com/wp-content/uploads/2008/08/comes-3096.pdf") [PDF][/SIZE] [/RIGHT]

---

### Post by AICollector on 2009-06-30
The computer I was referring to is an old one, a Pentium 2, 256mb of RAM, and a motherboard and accompanying tower chasis that makes you wonder how we can move it without bones breaking under the strain. That's my parents computer, I'm well aware that my neighbor on my left has a similar system.

So basically, I'd like to remind everyone that not every person out there has a modern computer, and hence why I suggested a 'lite' version designed to run on their machines. Linux's credentials as running on machines that the likes of Vista and Windows 7 left behind to rot will be tarnished if the most user-friendly and most public faceing distro can't run on older machines.

Regardless of the poltics invovled, try and think of those who are not so well of as to be able to purchase a new computer.


As a side note, it may be worth it to get Canocial to devote extra time to the Kubuntu releases. (The default install is a tad messy, including unprofessional items such as some of the helpful tooltips still say 'xxxxx ubuntu xxxx' instead of Kubuntu, or the inclusion of a still prototypical package manager and not-entirely-stable connection manager)

---

### Post by The Toxic Mite on 2009-06-30
inb4 teh lock???????

---

### Post by directhex on 2009-06-30
> **AICollector said:**
> So basically, I'd like to remind everyone that not every person out there has a modern computer, and hence why I suggested a 'lite' version designed to run on their machines. Linux's credentials as running on machines that the likes of Vista and Windows 7 left behind to rot will be tarnished if the most user-friendly and most public faceing distro can't run on older machines.

It's called Xubuntu.

---

### Post by directhex on 2009-06-30
> **MountainX said:**
> The logic is not *that* solid... I can see several holes in it and I'm not an expert on this subject.



I believe it is worth getting the full story so we understand both side of the argument. Here are some links I'm looking at now:
[http://boycottnovell.com/2009/06/13/suse-mono-good-for-windows/](http://boycottnovell.com/2009/06/13/suse-mono-good-for-windows/)
[http://boycottnovell.com/2009/05/25/licence-microsoft-moonlight-mono/](http://boycottnovell.com/2009/05/25/licence-microsoft-moonlight-mono/)
[http://www.heise.de/english/newsticker/news/141254](http://www.heise.de/english/newsticker/news/141254)
[http://www.osnews.com/story/8712](http://www.osnews.com/story/8712)

Mono is based on a standard designed and invented by Microsoft.

[SIZE=4]*“Every line of code that is written to our standards is a small victory; every line of code that is written to any other standard, is a small defeat.”*[/SIZE]
 [RIGHT]                                 –[SIZE=2][James Plamondon, Microsoft Technical Evangelist]("http://boycottnovell.com/wp-content/uploads/2008/08/comes-3096.pdf") [PDF][/SIZE] [/RIGHT]

Quoting Boycott Novell is like quoting the National Enquirer. Except their Elvis Lives stories are better researched and have more citations

---

### Post by AICollector on 2009-06-30
Hmmm...perhaps I'm not phrasing myself quite so clearly;

1. I am attempting to make a serious statment. Please reframe from childish comments.

2. I have tested Xubuntu on those computers mentioned. They do not work with it. I would file a bug report, were it for the fact that I could acutally see the screen (display is blank)

---

### Post by Dragonbite on 2009-06-30
> **directhex said:**
> Quoting Boycott Novell is like quoting the National Enquirer. Except their Elvis Lives stories are better researched and have more citations

And more fun to read.

---

### Post by directhex on 2009-06-30
> **AICollector said:**
> Hmmm...perhaps I'm not phrasing myself quite so clearly;

1. I am attempting to make a serious statment. Please reframe from childish comments.

2. I have tested Xubuntu on those computers mentioned. They do not work with it. I would file a bug report, were it for the fact that I could acutally see the screen (display is blank)

Your target system is over a decade old. 1998 or thereabouts. Whilst you might know people with them, that doesn't mean targeting them as primary consumers is the right move - because you'd essentially be gimping the distribution for everyone else to buy a computer in the last <11 years. Under Moore's law, a modern computer is about 2^7.3333 times more powerful (161 times for those at the back). Or at least has that many times more transistors.

As it happens, the quoted system requirements for Ubuntu ARE met by your target system (although not with the Live CD installer). Right at the bottom end. However, the simple reality is that making something more shiny needs more resources - and the last-millennium userbase is not the largest. RAM is the killer, and even from that era, 256 meg of RAM isn't much (I'm pretty sure I had 640 meg in 1999 or so). Then again, a lot of work goes on in Ubuntu to ensure a good experience on low-end Netbooks (whose Atom processors are roughly equivalent to a 600mhz P3, and start with a half gig of RAM). And as for suggesting that Canonical put in the work - as a company, they need to think about where they're going to make back some money from their investment in Ubuntu as a whole, and Netbooks is it

So, on to the next point. What's wrong with Xubuntu? For about a decade XFCE has been used as a "GNOME Lite", and correspondingly, the required specs are about half that of regular Ubuntu. So why oppose it as a suggestion for these (in your own words) bone-breaking systems? A bug? It's not a bug until it's in a bug tracker - as nobody knows about it to fix it.

---

### Post by bodhi.zazen on 2009-06-30
Moved to recurring discussions as the original question is asked and answered and now the discussion has turned to one of those recurring Mono discussions.

FYI : [**Ubuntu Technical Board Mono Position Statement**](http://ubuntuforums.org/showthread.php?t=1200818)

---

### Post by k2t0f12d on 2009-06-30
> **Bios Element said:**
> Why don't you just purge mono and move on with your life rather then waste your time trying to impose your opinion on everyone else?I'm sorry, which of the changes that I recommend were *forced* on you by nature of speaking my mind? Are you saying that only those who share your opinion are allowed to speak? Why is it a waste of time for me to speak, but not them?

> **Bios Element said:**
> Anyway, Microsoft claims Linux is illegal too and has yet to prove it. Maybe we should just shutdown until Linux is Microsoft Certified as well?Its true that Micro$oft says that the kernel violates their patents. The kernel is a critical necessity for a free software platform and Mono is not. Right now, anyway. Its a good idea to keep it that way until software patent reform were to remove those threats so we can choose our own battles.

---

### Post by k2t0f12d on 2009-06-30
> **3rdalbum said:**
> If it's dangerous to use Mono because of the possibility of a submarine patent, or the possibility that Microsoft will object to using a language that they invented: Why do people still use Wine? That *reimplements* the Win32 API which has got to be more risky than anything Mono is doing. Microsoft don't even claim to be able to provide anyone with a fair license to implement w32.

> **jimv said:**
> Your logic is solid.  I don't understand it either.MountainX answered your concerns.

> **MountainX said:**
> Well, this has become a current news item due to the Debian decision regarding Mono. Therefore, it is not just a rehash of an old discussion. 

I was not aware of the mono issues previously. After reading a bit, the issues seem totally different from Wine. I can't repeat all the details. But Microsoft's strategy is to get the open source community to write new applications on Microsoft's platforms. This is a way to undermine Linux. 

With Wine, we bring Windows apps into the Linux world. But with Mono, we end up writing new apps that target a platform technology designed and invented by Microsoft. With Wine, the development effort goes into the tool itself. If Wine were to disappear (which I do not think is a risk), no Linux-targeted open source apps would be affected.

With Mono, new development effort goes into the tool as well as new applications. If Mono becomes unavailable under a free license, and if all the best new apps over several years have been targeted to Mono, users of Linux will suffer a big setback and they will have to invest a lot of time and effort (and money) to port all those apps so they will run without Mono. Since we can develop such new apps now without Mono, and they can probably be developed just as easily without Mono, why subject the community to the risk? Even worse, why embrace a technology MS created? Sure, the CLR seems cool. Sure, writing C# GUI code is really easy compared to C or C++. But once one has used these technologies long enough for the cool factor to wear off, it becomes more obvious that the problems these technologies are designed to solve can be solved more elegantly with less complex approaches (e.g., using the Unix philosophy).

Linux is built on the Unix philosophy. Mono seems to undermine that foundation of Linux. 

Microsoft sees the .NET framework as the future of its operating system. Almost every Windows API is going to be moved to .NET. The .NET Framework is becoming the operating system. Microsoft would love to see Mono become entrenched in Linux. Mono could be a trojan horse in my mind.In addition to that, I observe that WINE is not included in the Ubuntu default installation with any standard w32 apps.

---

### Post by AICollector on 2009-06-30
Again, I think I'm not making myself clear.

I am not saying 'that is Ubuntu's target market' I am simply saying 'Hang on a minute, what about all those folks who dont have a modern computer? Are we gonna push them out of the most user friendly distro? Is that really fair, is that Ubuntu? I don't think it is, and should it come to such a matter, I don't think Ubuntu should really be named after a humanist philosophy if it's going to neglect those who need it most. (By this, I mean that many of the people around here can't afford a more up to date machine)

Why, I'd love to file a bug report on Xubuntu, with the one problem; I can't see whats causing it because I cannot SEE anything. Hence my problem, you see? ( I can't, of course).

---

### Post by Odemia on 2009-06-30
> **AICollector said:**
> 
I am sick and tired of hearing about Mono.

Then why did you bring it up?
> **AICollector said:**
> 
a total loon (personal opinion, of course)

Crazy people are everywhere.
> **AICollector said:**
> 
My own concern is that Ubuntu and other distros may some day come up with a system critical application that could mean the demise of said distros should Microsoft pull a fast one. I would hope people have enough sense to try and avoid that

Well that is essentially the exact same argument the RMS made ([http://http://www.fsf.org/news/dont-depend-on-mono]("http://http//www.fsf.org/news/dont-depend-on-mono")) that started the whole debate (or at least set it on fire), only he implied that including it by default would encourage more apps to depend on it and unlike your argument it wasn't about just one killer app but the possibility that a whole ecosystem of apps would be encouraged to grow (encouraged by Mono being part of the default install) and then fall if MS ever made a move to take on free implementations of C#.

Sounds like your real objection is to some "loon" on the dev forums.  So why did you come and bring it over here?  Not that you aren't entitled to an opinion and we all need a place to vent some times.  But hopefully you also see some irony in claiming that some guy ranting about mono (logic aside) is waisting time in the midst of this rant about mono.

PS Not looking to flame, I need to vent to sometimes.

---

### Post by directhex on 2009-06-30
> **AICollector said:**
> I am not saying 'that is Ubuntu's target market' I am simply saying 'Hang on a minute, what about all those folks who dont have a modern computer? Are we gonna push them out of the most user friendly distro? Is that really fair, is that Ubuntu? I don't think it is, and should it come to such a matter, I don't think Ubuntu should really be named after a humanist philosophy if it's going to neglect those who need it most. (By this, I mean that many of the people around here can't afford a more up to date machine)

At some point there needs to be acceptance that system requirements rise with capabilities. And even as it gets shinier, Ubuntu is STILL exceedingly low in demands compared to the competition (Vista Home Basic demands a 1GHz CPU and half gig of ram, as well as 20 gig of space; OS X 10.5 demands an entire gig of ram, 5 gig of disk space, and 1.5 GHz CPU). There is simply a limit to what can be done on a low-end system - and yes, that means that all the user-friendly doodads take resources (again, especially RAM). Should Firefox be dumped for everyone because it's a notorious RAM hog which sucks on a late-90's PC, in exchange for super-lightweight Dillo?

Again, I'm not saying that there isn't a market to be served by a low-requirement distro (and indeed IS served by Xubuntu primarily, but also others like Fluxbuntu) - but the simple reality is that that market is a niche, not the mainstream - and that as a niche, it cannot hold everyone else to ransom. A laptop with 1.6GHz processor, gig of ram, and 120 gig disk is £150! Would you begrudge developers for considering that kind of machine as the lower end of where to aim for rather than something with a 440BX in it?

As for your bug - as little info as you can provide is already a start. "Ubuntu works but Xubuntu does not, here are my system specifications" would be something that developers could use to diagnose - or at least help isolate - a problem. But throwing your hands in the air isn't how to get things fixed. The "price" for Free Software is contribution - and even bug reports are valuable currency at making the whole thing better.

---

### Post by saulgoode on 2009-06-30
Bradley Kuhn of the Software Freedom Law Center has written a cautionary essay:

[http://www.softwarefreedom.org/blog/2009/jun/29/language-patents/](http://www.softwarefreedom.org/blog/2009/jun/29/language-patents/)

---

### Post by zekopeko on 2009-06-30
@MountainX

Quoting from boycottnovell? Really?

---

### Post by bodhi.zazen on 2009-06-30
If you want to remove all non opensource,  you should run :

[http://www.gnewsense.org/](http://www.gnewsense.org/)

[http://ututo.org/www/index.php](http://ututo.org/www/index.php)

also see BLAG

[http://www.blagblagblag.org/](http://www.blagblagblag.org/)

Anybody know of any others to add to the list ?

FSF lists only two, so not sure what happend to blag on this issue :lolflag:

---

### Post by directhex on 2009-06-30
> **bodhi.zazen said:**
> If you want to remove all non opensource,  you should run :

[http://www.gnewsense.org/](http://www.gnewsense.org/)

gNewSense installs Mono by default, as Mono is Free Software.

```
directhex@desire:/tmp$ dpkg -I gnewsense-desktop_1.102gnewsense21_i386.deb
 new debian package, version 2.0.
 size 25866 bytes: control archive= 1932 bytes.
    3618 bytes,    16 lines   control              
     155 bytes,     2 lines   md5sums              
 Package: gnewsense-desktop
 Source: gnewsense-meta
 Version: 1.102gnewsense21
 Architecture: i386
 Maintainer: Matt Zimmerman <mdz@ubuntu.com>
 Installed-Size: 52
 Depends: acpi, acpi-support, acpid, alacarte, alsa-base, alsa-utils, anacron, apmd, avahi-daemon, bc, ca-certificates, consolekit, cupsys, cupsys-bsd, cupsys-client, cupsys-driver-gutenprint, dc, dcraw, desktop-file-utils, doc-base, eog, epiphany-browser, evince, fast-user-switch-applet, file-roller, foomatic-db, foomatic-db-engine, foomatic-filters, gcalctool, gconf-editor, gdebi, gdm, gedit, genisoimage, ghostscript-x, gimp-python, gnewsense-artwork, gnewsense-gdm-themes, gnome-about, gnome-app-install, gnome-applets, gnome-control-center, gnome-icon-theme, gnome-media, gnome-menus, gnome-netstatus-applet, gnome-nettool, gnome-panel, gnome-pilot-conduits, gnome-power-manager, gnome-session, gnome-spell, gnome-system-monitor, gnome-system-tools, gnome-terminal, gnome-themes, gnome-utils, gnome-volume-manager, gstreamer0.10-alsa, gstreamer0.10-plugins-base-apps, gstreamer0.10-pulseaudio, gtk2-engines, gtk2-engines-pixbuf, gucharmap, hal, hotkey-setup, language-selector, launchpad-integration, lftp, libgl1-mesa-glx, libglut3, libgnome2-perl, libgnomevfs2-bin, libgnomevfs2-extra, libpt-1.10.10-plugins-v4l, libpt-1.10.10-plugins-v4l2, libsasl2-modules, libxp6, metacity, nautilus, nautilus-cd-burner, nautilus-sendto, notification-daemon, openprinting-ppds, pnm2ppa, powermanagement-interface, pulseaudio, pulseaudio-esound-compat, readahead, rss-glx, screen, screensaver-default-images, scrollkeeper, seahorse, smbclient, software-properties-gtk, ssh-askpass-gnome, synaptic, system-config-printer-gnome, tangerine-icon-theme, tsclient, ttf-bitstream-vera, ttf-dejavu-core, ttf-freefont, ubuntu-sounds, unzip, update-manager, update-notifier, usplash, usplash-theme-gnewsense, x-ttcidfont-conf, xdg-user-dirs, xdg-user-dirs-gtk, xkb-data, xorg, xscreensaver-data, xscreensaver-gl, xterm, yelp, zenity, zip
 Recommends: avahi-autoipd, bluez-cups, bluez-gnome, bluez-utils, bogofilter, brasero, brltty, brltty-x11, bug-buddy, cdparanoia, compiz, contact-lookup-applet, cups-pdf, deskbar-applet, displayconfig-gtk, diveintopython, dvd+rw-tools, ekiga, espeak, evolution, evolution-exchange, evolution-plugins, evolution-webcal, example-content, [COLOR="Red"]f-spot[/COLOR], foo2zjs, foomatic-db-hpijs, fortune-mod, gcc, gimp, gimp-gnomevfs, gnome-accessibility-themes, gnome-games, gnome-mag, gnome-orca, gnome-screensaver, gnome-user-guide, gvfs-fuse, hal-cups-utils, hplip, im-switch, landscape-client, laptop-detect, libdeskbar-tracker, libgl1-mesa-dri, libnss-mdns, libpam-gnome-keyring, linux-headers-generic, make, min12xxw, mousetweaks, nautilus-share, network-manager-gnome, onboard, openoffice.org-calc, openoffice.org-gnome, openoffice.org-impress, openoffice.org-writer, pidgin, pidgin-otr, powernowd, pulseaudio-module-gconf, pulseaudio-module-hal, pulseaudio-module-x11, pxljr, rhythmbox, scim, scim-bridge-agent, scim-bridge-client-gtk, scim-gtk2-immodule, sound-juicer, splix, [COLOR="Red"]tomboy[/COLOR], totem, totem-mozilla, tracker, tracker-search-tool, transmission-gtk, ttf-arabeyes, ttf-arphic-uming, ttf-indic-fonts-core, ttf-kochi-gothic, ttf-kochi-mincho, ttf-lao, ttf-malayalam-fonts, ttf-thai-tlwg, ttf-unfonts-core, vinagre, vino, wodim, wvdial, xcursor-themes, xdg-utils, xsane
 Provides: ubuntu-desktop
 Section: metapackages
 Priority: optional
 Description: The gNewSense desktop system
  This package depends on all of the packages in the gNewSense desktop system
  .
  It is also used to help ensure proper upgrades, so it is recommended that
  it not be removed.
```

UTUTO packages it, but lord knows if it's in by default (I don't know how to tell)

---

### Post by mdsmedia on 2009-06-30
> **directhex said:**
> At some point there needs to be acceptance that system requirements rise with capabilities. And even as it gets shinier, Ubuntu is STILL exceedingly low in demands compared to the competition (Vista Home Basic demands a 1GHz CPU and half gig of ram, as well as 20 gig of space; OS X 10.5 demands an entire gig of ram, 5 gig of disk space, and 1.5 GHz CPU). There is simply a limit to what can be done on a low-end system - and yes, that means that all the user-friendly doodads take resources (again, especially RAM). Should Firefox be dumped for everyone because it's a notorious RAM hog which sucks on a late-90's PC, in exchange for super-lightweight Dillo?

Again, I'm not saying that there isn't a market to be served by a low-requirement distro (and indeed IS served by Xubuntu primarily, but also others like Fluxbuntu) - but the simple reality is that that market is a niche, not the mainstream - and that as a niche, it cannot hold everyone else to ransom. A laptop with 1.6GHz processor, gig of ram, and 120 gig disk is £150! Would you begrudge developers for considering that kind of machine as the lower end of where to aim for rather than something with a 440BX in it?

As for your bug - as little info as you can provide is already a start. "Ubuntu works but Xubuntu does not, here are my system specifications" would be something that developers could use to diagnose - or at least help isolate - a problem. But throwing your hands in the air isn't how to get things fixed. The "price" for Free Software is contribution - and even bug reports are valuable currency at making the whole thing better.
This and your previous post, very nicely said.

I think there are better reasons than being able to run a system on a decade old computer for not including Mono-based apps.

---

### Post by AICollector on 2009-07-01
Yes, I do see the irony, but I acknowledge that whilst I have some patience, that is thinning. Going through comments on sites (Such pristine examples include 'Mono is teh evil!) has very sadly shown me there are conspiracy nuts who prefer their reailty over everyone elses. Part of me feels we're not THAT far away from threats to Mono devs, which I especially do not want.

@directhex; I shall look up Fluxbuntu later. Also, some data about the componets in said computers are unavaible, as the motherboard itself is unmarked (and no diagnostic  tool can access that info either)


This thread was really more or less attempting to be the voice of reason whereas a good many people around the net are loosing theirs.

---

### Post by Dragonbite on 2009-07-01
Ubuntu's Mono Position

full version found here : [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000584.html]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000584.html")

> The Ubuntu Technical Board has been asked for a position statement on the use of C#, specifically the Mono implementation, by applications in Ubuntu.

These applications, as well as the Mono stack, were proposed for inclusion like any other application and underwent the same review process that all new applications and platforms undergo before being accepted into the archive.

With specific regard to the default installed application set, applications have been reviewed and compared against each other on merit and features.  These often take place during the Ubuntu Developer Summits, most recently over the default media player.

A common concern cited about Mono is the patent position, largely it seems due to the originator of the C# language and associated ECMA standards.

The Ubuntu Project takes patent issues seriously, and the Ubuntu Technical Board is the governance body that handles allegations of patent infringement.  The Ubuntu Technical Board strives to engage with rights holder openly in terms of the code that we ship.  If a rights holder claims a patent infringement applies to said code, the Technical Board will commit to a review of the claim.

The Ubuntu Technical Board has received no claims of infringement against the Mono stack, and is not aware of any such claims having been received by other similar projects.

It is common practice in the software industry to register patents as protection against litigation, rather than as an intent to litigate. Thus mere existence of a patent, without a claim of infringement, is not sufficient reason to warrant exclusion from the Ubuntu Project.

(While the Ubuntu project wishes to be responsive to patent infringement claims, we cannot commit to the assessment and review of claims made by anyone other than the registered rights holder.)


Given the above, the Ubuntu Technical Board sees no reason to exclude Mono or applications based upon it from the archive, or from the default installation set.

Since the Mono stack is already a dependency of the default installation set for many remixes of Ubuntu, including the Desktop Edition, there is no reason to consider a dependency on Mono as an issue when suggesting applications for the default set.

(Other remixes may obviously consider the CD Size implications if an  application would introduce the Mono platform to the set.)



---

### Post by satipera on 2009-07-01
I tried to post this to recurring discussions but could not. This means Red Hat, Suse community and Debian are not including it by default. So why is Ubuntu?

---

### Post by Jesus_Valdez on 2009-07-01
[http://ubuntuforums.org/showthread.php?t=1200818](http://ubuntuforums.org/showthread.php?t=1200818)

Sticky:    Ubuntu Technical Board Mono Position Statement

That shoud ask your question

---

### Post by satipera on 2009-07-01
Thanks, but I read it hours ago, it seems to state that until M$ sues someone Canonical are happy as things are. This seems reckless to me. HMM you have made 8 posts one of which is this one complete with tags so the moderator will move or delete it, how helpful of you.

---

### Post by Dragonbite on 2009-07-01
> **satipera said:**
> Thanks, but I read it hours ago, it seems to state that until M$ sues someone Canonical are happy as things are. This seems reckless to me. 

Sounds like they are focusing on usability rather than politics?

When there is a good enough/better application to fit the bill then they will likely use THAT instead.

---

### Post by satipera on 2009-07-01
It has nothing at all to do with politics. M$ has a well documented history of doing this sort of thing. Encouraging standards it wants to be adopted and then later enforcing IP laws. If Canonical has plans to substitute other programmes later then be honest with us and tell us.

---

### Post by swoll1980 on 2009-07-01
> **satipera said:**
> Thanks, but I read it hours ago, it seems to state that until M$ sues someone Canonical are happy as things are. This seems reckless to me. HMM you have made 8 posts one of which is this one complete with tags so the moderator will move or delete it, how helpful of you.

Post in non support sections don't increase your post count. He's just sick of mono threads, so am I. Ubuntu is keeping mono because there's nothing wrong with it, and they are not afraid of Microsoft's threats. Will you suggest that every time Microsoft screams "I'll sue" companies should just do what they say, whether it's right, or not?

---

### Post by andamaru on 2009-07-01
If Microsoft wants us to use their language why don't they clear up this mess. It's a nice language, it's just controlled by idiots. I'm pretty sure Canonical is going to give into peer pressure. If the opensuse guys aren't including it by default, I think that's more than enough reason to stay away.

This is coming from a fan of the language, such as waste.

---

### Post by satipera on 2009-07-01
Why are so many people so desperate to bury discussion of this important subject in the Ubuntu forums? Neither Red hat, Suse community or Debian are including mono by default. So why are Canonical? This has nothing to do with some "political" motive, it is common sense. Waiting for Microsoft to sue someone is not my idea of a plan. Microsoft have a long history of encouraging a format they want used and then later moving in with IP lawyers.

---

### Post by .Maleficus. on 2009-07-01
I'm not going to make another Mono thread for my simple questions, so sorry for the threadjack.  And sorry for the probably dumb questions.

Has Microsoft actually said they were going to sue somebody?  Don't answer "no but they will, it's what they do" because I don't care about that.  I actually want to know if they've said anything yet.

The controversy isn't the use of C#, it is the distribution of .NET libraries, correct?  Because C# is an open standard and Mono can handle languages like VB.NET, which isn't.

Why would SuSE be removing Mono if Novell develops it?

I probably have more but they'll be in regards to the answers I get, so /threadjack.

---

### Post by cariboo on 2009-07-01
I would help if you posted a link to backup your claim. So far it looks like you made it up yourself.

---

### Post by sertse on 2009-07-01
Please provides a source, an official statement from Debian declaring that. Was it recent news? Thanks

On topic: The mono topic has been around for years, and pretty every angle has been covered in the hundreds of topics since. (Hint: Tag search "Yet another mono thread" - goes back to 06, probably some earlier..). What I'm saying is that your argument has already been heard before, and Ubuntu in their official opinion has decided not to be a valid reason to be against mono. Or do you think your opinion is really novel, something actually new to offer?

---

### Post by Dragonbite on 2009-07-01
> **andamaru said:**
> If Microsoft wants us to use their language why don't they clear up this mess. It's a nice language, it's just controlled by idiots. I'm pretty sure Canonical is going to give into peer pressure. If the opensuse guys aren't including it by default, I think that's more than enough reason to stay away.

This is coming from a fan of the language, such as waste.

OpenSUSE is more of a KDE-based distro, like Ubuntu and Fedora are Gnome-based, and there are not many Mono apps for KDE, Kerry (KDE + Beagle) being the only one I can think of.

BTW, it looks like F-spot and Banshee are installed by default, according to their [[COLOR="Blue"]screenshot[/COLOR]]("http://en.opensuse.org/Image:Desktop-gnome111.png") for Gnome.

*EDIT: I am about to start testing Milestone 3 for KDE, but maybe I'll try Gnome first and see what's included*

Remember, though.. openSUSE =/= Novell or SLED or SLES from anything more than a technical standpoint and some sponsorship.

---

### Post by andamaru on 2009-07-01
> **Dragonbite said:**
> OpenSUSE is more of a KDE-based distro, like Ubuntu and Fedora are Gnome-based, and there are not many Mono apps for KDE, Kerry (KDE + Beagle) being the only one I can think of.

BTW, it looks like F-spot and Banshee are installed by default, according to their [[COLOR="Blue"]screenshot[/COLOR]]("http://en.opensuse.org/Image:Desktop-gnome111.png") for Gnome.

*EDIT: I am about to start testing Milestone 3 for KDE, but maybe I'll try Gnome first and see what's included*

Remember, though.. openSUSE =/= Novell or SLED or SLES from anything more than a technical standpoint and some sponsorship.

I know openSUSE isn't Novell, but their was wording in agreement specifically for openSuSE so I'm confused as to why they wouldn't include it.

---

### Post by Dragonbite on 2009-07-01
> **andamaru said:**
> I know openSUSE isn't Novell, but their was wording in agreement specifically for openSuSE so I'm confused as to why they wouldn't include it.
As far as I can tell, though, they do, though maybe not for the KDE version.  Where did you hear they aren't including it?

---

### Post by Tibuda on 2009-07-01
It's their option.

---

### Post by saulgoode on 2009-07-01
> **sertse said:**
> Please provides a source, an official statement from Debian declaring that. Was it recent news? Thanks

Alexander Reichle-Schmehl, a spokesperson for Debian, yesterday wrote [on his weblog]("http://blog.schmehl.info/Debian/tomboy-mono/2009/06/30#tomboy-mono") that Debian does not include Mono in its "default install". This is not news, but a clarification of the situation (which had been misreported on some news sites and this subsequently echoed by rms in [his essay]("http://www.fsf.org/news/dont-depend-on-mono")).

---

### Post by GeneralZod on 2009-07-01
> **Dragonbite said:**
>  and there are not many Mono apps for KDE, Kerry (KDE + Beagle) being the only one I can think of.


Kerry is C++, so I'm not sure that this really counts :)

---

### Post by Dragonbite on 2009-07-01
> **GeneralZod said:**
> Kerry is C++, so I'm not sure that this really counts :)My mistake then.

EDIT:
According to Linux App Finder > Kerry is a KDE frontend for the Beagle desktop search daemon.

A program for indexing and searching user's data. At the moment, it can index filesystems, chat logs, mail and data, RSS and other. .

From the Beagle website> Beagle is written in C# using Mono. The indexing is handled by Lucene.Net, a C# port of the Lucene indexer. The search user interface is written using Gtk#. 

---

### Post by unoodles on 2009-07-01
I have a question that perhaps someone can answer.

Has a patent ever stopped the FOSS community in the past?
I know that they do not ship by default, but there are mp3 and aac (and more?) codecs that violate patents, and I don't hear anyone complaining about them.
There is libdvdcss which is a blatant violation of the DMCA, and I never heard a single complaint.

Why are people complaining about mono, when there is plenty of existing software that *for sure* violates patents?

---

### Post by GeneralZod on 2009-07-01
> **Dragonbite said:**
> My mistake then.

EDIT:
According to Linux App Finder 

From the Beagle website

Yes: Kerry is a C++ KDE frontend that uses the libbeagle-dev C-bindings to interact with GNOME's Beagle.

---

### Post by directhex on 2009-07-01
> **unoodles said:**
> I have a question that perhaps someone can answer.

Has a patent ever stopped the FOSS community in the past?
I know that they do not ship by default, but there are mp3 and aac (and more?) codecs that violate patents, and I don't hear anyone complaining about them.
There is libdvdcss which is a blatant violation of the DMCA, and I never heard a single complaint.

Why are people complaining about mono, when there is plenty of existing software that *for sure* violates patents?

Because Micro$haft.

---

### Post by ericab on 2009-07-01
dont worry everyone;

sudo apt-get remove --purge mono-common libmono0 libgdiplus && sudo rm -rf /usr/lib/mono

---

### Post by directhex on 2009-07-01
> **satipera said:**
> Why are so many people so desperate to bury discussion of this important subject in the Ubuntu forums? Neither Red hat, Suse community or Debian are including mono by default. So why are Canonical? This has nothing to do with some "political" motive, it is common sense. Waiting for Microsoft to sue someone is not my idea of a plan. Microsoft have a long history of encouraging a format they want used and then later moving in with IP lawyers.

Have you lobbied for removal of OpenOffice.org, for implementing Microsoft-created ECMA 376? Yes or no?

And the "No Mono in openSUSE" thing is made up - yet somehow already accepted as fact. In openSUSE's KDE desktop, no, it isn't included - why would it be, with no apps using it? The GNOME desktop continues to use the apps that their team feels are best, which include Mono-based apps (although I disagree on some, such as Monsoon)

---

### Post by directhex on 2009-07-01
> **ericab said:**
> dont worry everyone;

sudo apt-get remove --purge mono-common libmono0 libgdiplus && sudo rm -rf /usr/lib/mono

Bear in mind this recipe won't work on Karmic.

---

### Post by blackxored on 2009-07-01
> **paul_be said:**
> I think jumping ship on mono all at once is a bad idea.  It is better to let further development mono app replacements occur.  Many people dont use linux due to "how hard it is to use", and making people use less developed/user friendly apps is worse than relying on mono.  They best solution should be slowly replace mono apps, not strip mono out right now like fedora.
-my two cents

The alternatives are there. I already posted them. gThumbViewer and Gnote. 
I would program it myself If I need to, but I hate M$ and SCO pattent issues. 
It's like Tim Berneers Lee telling you that you can't create a website!

I'm not a truly purist of free software, since we need contrib software sometimes, but that's out of point. 

My personal standview: remove it, the language is not enough, the tools aren't enough either, to take that risk. They *will* sue linux, the novell's deal isn't a casuality. 
I have always feared M$ would introduce it's code into linux, and somehow and someway it's coming closer.

---

### Post by doas777 on 2009-07-01
> **blackxored said:**
> Ok. 
More on the same topic. 
Now that Stallman has spoken: [http://www.fsf.org/news/dont-depend-on-mono](http://www.fsf.org/news/dont-depend-on-mono), let me speak myself. 
I'm not agree with risking any free linux distribution because of size. That's mostly why mono is included by default in ubuntu and was accepted in debian. There's no way we couldn't find alternatives to Tomboy, and FSpot ( eyes closed: gThumb, Gnote), so why giving even the possibility we all know about. Free software is about choice, and some choices are better, others are riskier, and then finally others are safer. People have even (extremely IMHO) left ubuntu because of the decision of mono, we can't afford that.

+1 for removing mono, tomboy and fspot.

personally I don't mind seeing people leave over stuff like this. I want linux to grow more intutitive, easier to use, and increase its market share.

the very people you mention jumping ship, are the people that would leave ubuntu as soon as my goals were realized anyway.

---

### Post by monsterstack on 2009-07-01
> **doas777 said:**
> personally I don't mind seeing people leave over stuff like this. I want linux to grow more intutitive, easier to use, and increase its market share.

the very people you mention jumping ship, are the people that would leave ubuntu as soon as my goals were realized anyway.

So the goal of the FSF and others is to ensure that Linux remains less intuitive, difficult to use, and without a significant market share? I know some anti-Mono folk seem a little crazy, but the contention that they want everybody to be miserable is *somewhat* absurd.

---

### Post by Dragonbite on 2009-07-01
> **unoodles said:**
> Why are people complaining about mono, when there is plenty of existing software that *for sure* violates patents?

Because some people see Microsoft as being EEEEEeeeeevvvvvvvvviiiiiiiiilll! :evil: :evil: :evil: :evil: :twisted: :evil: :evil:

---

### Post by SushiR on 2009-07-01
> **monsterstack said:**
> So the goal of the FSF and others is to ensure that Linux remains less intuitive, difficult to use, and without a significant market share? I know some anti-Mono folk seem a little crazy, but the contention that they want everybody to be miserable is *somewhat* absurd.

Well said - and I can only agree so far. The whole "Mono is evil, everything is evil, the sky will be crashing down on us" rant is getting boring by now.

---

### Post by blackxored on 2009-07-01
> **saulgoode said:**
> Alexander Reichle-Schmehl, a spokesperson for Debian, yesterday wrote [on his weblog]("http://blog.schmehl.info/Debian/tomboy-mono/2009/06/30#tomboy-mono") that Debian does not include Mono in its "default install". This is not news, but a clarification of the situation (which had been misreported on some news sites and this subsequently echoed by rms in [his essay]("http://www.fsf.org/news/dont-depend-on-mono")).

Actually, they will, to my sadness, assumming slashdot isn't wrong:
Source: [http://tinyurl.com/n5e66s](http://tinyurl.com/n5e66s)

---

### Post by directhex on 2009-07-01
> **blackxored said:**
> Actually, they will, to my sadness, assumming slashdot isn't wrong:
Source: [http://tinyurl.com/n5e66s](http://tinyurl.com/n5e66s)

Slashdot is wrong, and your source is 2 weeks old. See [http://ubuntuforums.org/showpost.php?p=7546513&postcount=44](http://ubuntuforums.org/showpost.php?p=7546513&postcount=44) for the detailed explanation nobody cares about

---

### Post by rookcifer on 2009-07-01
> **unoodles said:**
> I have a question that perhaps someone can answer.

Has a patent ever stopped the FOSS community in the past?
I know that they do not ship by default, but there are mp3 and aac (and more?) codecs that violate patents, and I don't hear anyone complaining about them.
There is libdvdcss which is a blatant violation of the DMCA, and I never heard a single complaint.

Why are people complaining about mono, when there is plenty of existing software that *for sure* violates patents?

Because mp3 is not included by default in the majority of distros.  And as for libdvdcss (or libdvdread) it is a necessary evil because without it, one can't watch DVD's under Linux. Besides, most distros don't include libdvdcss by default either -- it's sort of a "use at your own risk" type of thing.

This is different from Mono because Mono is *not* necessary.  It is only included for expediency and to attract C# developers to Linux.  I have never been overly impressed with Mono apps as there are much better alternatives to Banshee, just as one example.

And, no, the analogies to Samba or C are not valid either for a variety of reasons.

---

### Post by gnomeuser on 2009-07-01
> **satipera said:**
> Why are so many people so desperate to bury discussion of this important subject in the Ubuntu forums? 


BURY? have you seen how many anti-mono whining threads we have here?

> 
Neither Red hat, Suse community or Debian are including mono by default. So why are Canonical? This has nothing to do with some "political" motive, it is common sense. Waiting for Microsoft to sue someone is not my idea of a plan. Microsoft have a long history of encouraging a format they want used and then later moving in with IP lawyers.

Red Hat has no real community, Fedora being their community project on which the RHEL product line is based does and Fedora ships Mono, not by default in the Desktop release for space reasons but if you use the DVD then you get Mono as dependencies for Tomboy and F-spot by default. OpenSUSE ships Mono by default for their GNOME release to get Banshee, F-spot, Beagle and other applications. I don't feel comfortable speaking of the Debian situation, there is ongoing debate and using their current state in debate seems dishonest.

Regardless, GNewSense, the FSF sponsored and endorsed distribution currently ships Mono. All the distros above ship Mono and all of them have strict requirements for content being Free Software. Mono is Free Software, it's even covered by the OIN. 

Please get your facts straight.

---

### Post by knopper67 on 2009-07-01
> **Staz said:**
> Gnote doesn't have all the features of Tomboy, the dev base and the momentum

It doesn't have all the bloat, either.

---

### Post by cb951303 on 2009-07-01
> **knopper67 said:**
> It doesn't have all the bloat, either.

what bloat? if tomboy is bloated so is Gnote since it's a line by line clone.

---

### Post by saulgoode on 2009-07-01
> **unoodles said:**
> Has a patent ever stopped the FOSS community in the past?
History is replete with examples. Broadcast2000 was an extremely promising video editor which was canceled under threat of patents. The TIFF, JPEG, and (especially) GIF image formats have all been problematic for the Free Software community. The photomosaic plugin for GIMP is no longer available because of patents, and support for many audio and video formats is encumbered by patent claims.

> **unoodles said:**
> I know that they do not ship by default, but there are mp3 and aac (and more?) codecs that violate patents, and I don't hear anyone complaining about them.
It is not a certainty that those programs violate patents, but there is a risk that courts might so decide. There is not much cause for complaint if one is apprised of the risk and decides for himself whether it is acceptable. 


> **unoodles said:**
> There is libdvdcss which is a blatant violation of the DMCA, and I never heard a single complaint.
Actually, libdvdcss is not a blatant violation of the DMCA; in fact, usage of libdvdcss for *legal* purposes is not covered by the Act. The court case which resulted in everybody assuming that usage of libdvdcss violates the DMCA was decided because the defendents were found to be using it to engage in *illegal* acts.

Distribution of libdvdcss, however, may risk violating the DMCA, and thus many distros will not include it by default; again, letting the users assess for themselves the risk being accepted.

> **unoodles said:**
> Why are people complaining about mono, when there is plenty of existing software that *for sure* violates patents?
No software "for sure" violates patents; it is a matter of level of risk inhered by using or distributing the software. The general policy of most distros is to, when there is sufficient question about patent risks, let users decide for themselves whether the risk is too great to justify installing the software. 

People are complaining about Mono because it is included by default. Were it like the other software you mention and made available in the restricted repos, the complaints would for the most part cease.

---

### Post by knopper67 on 2009-07-01
> **cb951303 said:**
> what bloat? if tomboy is bloated so is Gnote since it's a line by line clone.

Look at that! A whopping 40MB for a freaking note-taking application.

---

### Post by knopper67 on 2009-07-01
Compared with Gnote..

5325KB - About five megabytes I do believe...

---

### Post by LowSky on 2009-07-01
this MONO stuff is getting STUPID... why dont we all stop posting about how proprietary software is killing the opensource world and help some noobs in the Absolute begginers section, the more happy Ubuntu users, the less we need to worry about Microsoft.

---

### Post by psyke83 on 2009-07-01
> **knopper67 said:**
> Look at that! A whopping 40MB for a freaking note-taking application.

Fail. Those are shared Mono libraries; you're comparing apples to oranges.

---

### Post by ronacc on 2009-07-01
and whats wrong with gedit ? I'm taking NOTES not composing and illuminating sacred tomes .

---

### Post by knopper67 on 2009-07-01
> **psyke83 said:**
> Fail. Those are shared Mono libraries; you're comparing apples to oranges.

Still, dependencies count. Especially when there's that many of them.

---

### Post by ghindo on 2009-07-01
> **knopper67 said:**
> Still, dependencies count. Especially when there's that many of them.If *only* Tomboy needed those dependencies, then I would see your point.  However, Tomboy isn't the only application that relies on those dependencies, so your point is kind of moot.

---

### Post by directhex on 2009-07-01
There's also bugs like Debian bug 534969 to consider. How is Tomboy's record for data integrity, compared to Gnote? Do we care about users' data?

---

### Post by RAOF on 2009-07-01
> **knopper67 said:**
> Look at that! A whopping 40MB for a freaking note-taking application.

I can play this too - observe from a minimal install:
```

aptitude install gnote
Reading package lists...
Building dependency tree...
Reading state information...
Initializing package states...
Writing extended state information...
The following NEW packages will be installed:
  adduser{a} consolekit{a} dbus{a} dbus-x11{a} defoma{a} devicekit-disks{a} 
  esound-common{a} file{a} fontconfig{a} fontconfig-config{a} gamin{a} 
  gconf2{a} gconf2-common{a} gnome-mime-data{a} gnote gvfs{a} 
  libart-2.0-2{a} libasound2{a} libaspell15{a} libatasmart0{a} 
  libatk1.0-0{a} libaudiofile0{a} libavahi-client3{a} 
  libavahi-common-data{a} libavahi-common3{a} libavahi-glib1{a} 
  libbonobo2-0{a} libbonobo2-common{a} libbonoboui2-0{a} 
  libbonoboui2-common{a} libboost-filesystem1.38.0{a} 
  libboost-regex1.38.0{a} libboost-system1.38.0{a} libcairo2{a} 
  libcairomm-1.0-1{a} libck-connector0{a} libcups2{a} libdatrie1{a} 
  libdbus-1-3{a} libdbus-glib-1-2{a} libdevmapper1.02.1{a} 
  libdirectfb-1.2-0{a} libeggdbus-1-0{a} libenchant1c2a{a} libesd-alsa0{a} 
  libexpat1{a} libfontconfig1{a} libfreetype6{a} libgail-common{a} 
  libgail18{a} libgamin0{a} libgconf2-4{a} libgconfmm-2.6-1c2{a} libgdu0{a} 
  libglade2-0{a} libglib2.0-0{a} libglibmm-2.4-1c2a{a} libgnome-keyring0{a} 
  libgnome2-0{a} libgnome2-common{a} libgnomecanvas2-0{a} 
  libgnomecanvas2-common{a} libgnomemm-2.6-1c2{a} libgnomeui-0{a} 
  libgnomeui-common{a} libgnomevfs2-0{a} libgnomevfs2-common{a} 
  libgtk2.0-0{a} libgtk2.0-common{a} libgtkmm-2.4-1c2a{a} libgtkspell0{a} 
  libgudev-1.0-0{a} libgvfscommon0{a} libhal-storage1{a} libhal1{a} 
  libhunspell-1.2-0{a} libice6{a} libicu40{a} libidl0{a} libjasper1{a} 
  libjpeg62{a} libmagic1{a} libnewt0.52{a} liborbit2{a} 
  libpanel-applet2-0{a} libpanelappletmm-2.6-1c2{a} libpango1.0-0{a} 
  libpango1.0-common{a} libpangomm-1.4-1{a} libparted1.8-12{a} libpcre3{a} 
  libpixman-1-0{a} libpng12-0{a} libpolkit-backend-1-0{a} 
  libpolkit-gobject-1-0{a} libpolkit2{a} libpopt0{a} libpython2.6{a} 
  libsgutils2{a} libsm6{a} libsqlite3-0{a} libsysfs2{a} libthai-data{a} 
  libthai0{a} libtiff4{a} libts-0.0-0{a} libudev0{a} libx11-6{a} 
  libx11-data{a} libxau6{a} libxcb-render-util0{a} libxcb-render0{a} 
  libxcb1{a} libxcomposite1{a} libxcursor1{a} libxdamage1{a} libxdmcp6{a} 
  libxext6{a} libxfixes3{a} libxft2{a} libxi6{a} libxinerama1{a} 
  libxml++2.6-2{a} libxml2{a} libxrandr2{a} libxrender1{a} libxslt1.1{a} 
  mime-support{a} psmisc{a} python{a} python2.6{a} shared-mime-info{a} 
  tsconf{a} ttf-dejavu{a} ttf-dejavu-core{a} ttf-dejavu-extra{a} ucf{a} 
  whiptail{a} x11-common{a} 
0 packages upgraded, 139 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.4MB/38.3MB of archives. After unpacking 162MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
aptitude install tomboy
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
The following NEW packages will be installed:
  adduser{a} cli-common{a} consolekit{a} dbus{a} dbus-x11{a} defoma{a} 
  devicekit-disks{a} esound-common{a} file{a} fontconfig{a} 
  fontconfig-config{a} gamin{a} gconf2{a} gconf2-common{a} 
  gnome-mime-data{a} gvfs{a} libart-2.0-2{a} libart2.0-cil{a} libasound2{a} 
  libaspell15{a} libatasmart0{a} libatk1.0-0{a} libaudiofile0{a} 
  libavahi-client3{a} libavahi-common-data{a} libavahi-common3{a} 
  libavahi-glib1{a} libbonobo2-0{a} libbonobo2-common{a} libbonoboui2-0{a} 
  libbonoboui2-common{a} libcairo2{a} libck-connector0{a} libcups2{a} 
  libdatrie1{a} libdbus-1-3{a} libdbus-glib-1-2{a} libdevmapper1.02.1{a} 
  libdirectfb-1.2-0{a} libeggdbus-1-0{a} libenchant1c2a{a} libesd-alsa0{a} 
  libexpat1{a} libfontconfig1{a} libfreetype6{a} libgail-common{a} 
  libgail18{a} libgamin0{a} libgconf2-4{a} libgconf2.0-cil{a} libgdu0{a} 
  libglade2-0{a} libglade2.0-cil{a} libglib2.0-0{a} libglib2.0-cil{a} 
  libgmime-2.0-2a{a} libgmime2.2a-cil{a} libgnome-keyring0{a} 
  libgnome-vfs2.0-cil{a} libgnome2-0{a} libgnome2-common{a} 
  libgnome2.24-cil{a} libgnomecanvas2-0{a} libgnomecanvas2-common{a} 
  libgnomepanel2.24-cil{a} libgnomeui-0{a} libgnomeui-common{a} 
  libgnomevfs2-0{a} libgnomevfs2-common{a} libgtk2.0-0{a} libgtk2.0-cil{a} 
  libgtk2.0-common{a} libgtkspell0{a} libgudev-1.0-0{a} libgvfscommon0{a} 
  libhal-storage1{a} libhal1{a} libhunspell-1.2-0{a} libice6{a} libidl0{a} 
  libjasper1{a} libjpeg62{a} libmagic1{a} libmono-addins-gui0.2-cil{a} 
  libmono-addins0.2-cil{a} libmono-cairo2.0-cil{a} libmono-corlib2.0-cil{a} 
  libmono-posix2.0-cil{a} libmono-security2.0-cil{a} 
  libmono-sharpzip2.84-cil{a} libmono-system2.0-cil{a} libmono0{a} 
  libndesk-dbus-glib1.0-cil{a} libndesk-dbus1.0-cil{a} libnewt0.52{a} 
  liborbit2{a} libpanel-applet2-0{a} libpango1.0-0{a} libpango1.0-common{a} 
  libparted1.8-12{a} libpcre3{a} libpixman-1-0{a} libpng12-0{a} 
  libpolkit-backend-1-0{a} libpolkit-gobject-1-0{a} libpolkit2{a} 
  libpopt0{a} libpython2.6{a} libsgutils2{a} libsm6{a} libsqlite3-0{a} 
  libsysfs2{a} libthai-data{a} libthai0{a} libtiff4{a} libts-0.0-0{a} 
  libudev0{a} libx11-6{a} libx11-data{a} libxau6{a} libxcb-render-util0{a} 
  libxcb-render0{a} libxcb1{a} libxcomposite1{a} libxcursor1{a} 
  libxdamage1{a} libxdmcp6{a} libxext6{a} libxfixes3{a} libxft2{a} 
  libxi6{a} libxinerama1{a} libxml2{a} libxrandr2{a} libxrender1{a} 
  mime-support{a} mono-2.0-gac{a} mono-gac{a} mono-runtime{a} psmisc{a} 
  python{a} python2.6{a} shared-mime-info{a} tomboy tsconf{a} ttf-dejavu{a} 
  ttf-dejavu-core{a} ttf-dejavu-extra{a} ucf{a} whiptail{a} x11-common{a} 
0 packages upgraded, 151 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.8MB/38.9MB of archives. After unpacking 168MB will be used.
Do you want to continue? [Y/n/?]  

```

Tomboy: 38.9MB.  Gnote: 38.3MB.

Of course, this comparison is stupid; we're not installing Tomboy on a raw debootstrap system, nor are we installing Gnote on a raw debootstrap system.  But, as you see, the full dependency chains are about the same size.  However, since almost all of *both* dependency chains are are pulled in already by other apps in ubuntu-desktop, the "moar dependencies" argument is a bit irrelevant anyway.

---

### Post by doas777 on 2009-07-01
> **monsterstack said:**
> So the goal of the FSF and others is to ensure that Linux remains less intuitive, difficult to use, and without a significant market share? I know some anti-Mono folk seem a little crazy, but the contention that they want everybody to be miserable is *somewhat* absurd.

look at the "minimal/streamlined" vs "everything just works" arguments. you have some people proclaiming ubuntu the king of OSes because everything on their laptops just worked on defaults, and then you have folks complaining and threatening to leave because "ubuntu is bloated". 

I do believe that there are many hobbiest and tech pros that care not a whit for marketshare, and will prolly ultimatly leave linux for something more 1337 (traditionally BSD), whenever linux gets "too mainstream" by their estimation. you should hear this SA I know....

---

### Post by Jestersage on 2009-07-01
For a while, I was debating between openSuSE and Ubuntu, because while I think ubuntu is better as a server (kernel, performance, and features), openSuSE have Mono. Even though Ubuntu right now have mono, it's outdated.

Until I see that in 9.10 it will be 2.4, which is the most up to date Mono.

Though granted, openSuSE still have Yast, but as of now Ubuntu actually become a worth while server platform by allowing C# to run.

So thanks, Canonical, for not listening to the FOSS-fanboys and understand what is needed is far more important.

---

### Post by jonian_g on 2009-07-01
> **doas777 said:**
> look at the "minimal/streamlined" vs "everything just works" arguments. you have some people proclaiming ubuntu the king of OSes because everything on their laptops just worked on defaults, and then you have folks complaining and threatening to leave because "ubuntu is bloated". 

I do believe that there are many hobbiest and tech pros that care not a whit for marketshare, and will prolly ultimatly leave linux for something more 1337 (traditionally BSD), whenever linux gets "too mainstream" by their estimation. you should hear this SA I know....

So, using mono will make linux more popular? I just don't understand that argument.

---

### Post by directhex on 2009-07-01
> **jonian_g said:**
> So, using mono will make linux more popular? I just don't understand that argument.

Making more awesome apps will make Linux more popular - the language said apps are written with is a distraction

---

### Post by jonian_g on 2009-07-01
> **directhex said:**
> Making more awesome apps will make Linux more popular - the language said apps are written with is a distraction

So without mono, can't anyone make awesome apps?

---

### Post by directhex on 2009-07-01
> **jonian_g said:**
> So without mono, can't anyone make awesome apps?

Sure. They *can*. The issue is whether they *will*. In the end, it's down to developers who actually write apps to decide on how they want to write them - and it's 100% their choice. If the people actively making awesome apps are using Mono, then that's why distributions end up including Mono

---

### Post by paul_be on 2009-07-01
wow... switch to fedora if you dont like mono.  Good luck

---

### Post by satipera on 2009-07-01
If you look around the net in the next few days I think you will find that what I said about mono not being included in Debian by default in my original thread starting post was absolutely accurate, I am seeing more sites saying the same thing.

---

### Post by directhex on 2009-07-01
> **satipera said:**
> If you look around the net in the next few days I think you will find that what I said about mono not being included in Debian by default in my original thread starting post was absolutely accurate, I am seeing more sites saying the same thing.

[http://ubuntuforums.org/showpost.php?p=7546513&postcount=44](http://ubuntuforums.org/showpost.php?p=7546513&postcount=44)

---

### Post by jonian_g on 2009-07-01
> **directhex said:**
> Sure. They *can*. The issue is whether they *will*. In the end, it's down to developers who actually write apps to decide on how they want to write them - and it's 100% their choice. If the people actively making awesome apps are using Mono, then that's why distributions end up including Mono

Well, this is just speculation. Mono has the same chance to be used by a developer as any other language available.

The only mono app that doesn't have a better alternative is F-spot. As for the rest it is a matter of personal taste (for me Listen is the best music organizer).

Till now, few developers have chosen mono. That is why we have so little mono apps and mono has been around for 5 years.

---

### Post by Tibuda on 2009-07-01
FOSS fanboys can use Mono. It is open source and is [released under free licenses]("http://www.mono-project.com/FAQ:_Licensing").

---

### Post by wayne_cat on 2009-07-01
mono vs. no mono ... squeeze vs. roll-up of the toothpaste tube.

I love these religious debates .... please go on! :popcorn:

---

### Post by paul_be on 2009-07-01
recurring discussions??????

---

### Post by satipera on 2009-07-01
I was a bit early for Boycott Novel but nice try. Even if I had not been, their sources should be taken for their individual worth and not easily dismissed as you would like.

---

### Post by directhex on 2009-07-01
> **paul_be said:**
> recurring discussions??????

Why? First I've heard about this "Mono" thing

---

### Post by directhex on 2009-07-01
> **wayne_cat said:**
> I love these religious debates .... please go on! :popcorn:

Emacs!

---

### Post by directhex on 2009-07-01
> **satipera said:**
> I was a bit early for Boycott Novel but nice try. Even if I had not been, their sources should be taken for their individual worth and not easily dismissed as you would like.

Their sources are in 99% of cases themselves. Most links are self referential. And none of their readership actually reads the sources, according to my evidence.

---

### Post by paul_be on 2009-07-01
> **directhex said:**
> Why? First I've heard about this "Mono" thing

lol i know huh:)

---

### Post by linuxmagick on 2009-07-01
> **directhex said:**
> Why? First I've heard about this "Mono" thing

Thanks for that.  I really needed a good laugh :)

---

### Post by satipera on 2009-07-01
And what is your evidence? Is there some evidence you wish to share with us about BN'S readership?

---

### Post by cariboo on 2009-07-01
This thread has nothing to do with Testimonials and experiences. It should have been posted in the Cafe to start with, now it is going in Recurring Discussions.

---

### Post by directhex on 2009-07-01
> **satipera said:**
> And what is your evidence? Is there some evidence you wish to share with us about BN'S readership?

Sure.

BN claims to have millions of readers - see [http://boycottnovell.com/2009/01/28/new-bn-readers/](http://boycottnovell.com/2009/01/28/new-bn-readers/) as an example.

I made a little experiment & wrote something I knew would get linked/attacked on BN - see [http://www2.apebox.org/wordpress/rants/84/](http://www2.apebox.org/wordpress/rants/84/) for the statistics regarding that post (short version: 4.8K visitors, 17 from BN)

In June, my post saw over 40,000 unique visitors (excluding people reading on LinuxToday, or via Monologue, Planet Debian, Planet Ubuntu, or Planet Banshee), which is about ten times the people who visited the post I analyze above. How many of those fourty thousand, which is obviously a tiny fraction of BN's traffic, came from people clicking links on BN? The article was linked three times - twice in articles, and once in the IRC logs. How many?

22.

So either their readership is a lie, or their readers don't check their sources. That's the observation, backed by measurements.

---

### Post by doas777 on 2009-07-01
> **jonian_g said:**
> So, using mono will make linux more popular? I just don't understand that argument.

I'm saying that when you strive for "everything just works", you usually end up adding additional components that not everyone will use. look at codecs. most users want them, but a few worry about the taint. if they wern't available (and easily installable), we'd have a lot of people not being able to do what they want to with their PC. it does not "just work"

mono will not make linux more popular in and of itself, but it will allow non-technical users to run mono app out of box. the more things work OOB, the better probability that new users will see value in it, and will thus count themselves amoung our ranks. the more the community grows, the more people learn that ubuntu is a viable alternative, and the community grows some more. one of the major goals of ubuntu is to be an os for people (everyone) not an os for the comparitively few technical users and FOSS purists.

having mono preinstalled is the same as an OEM installing sun java and/or .net on a windows pc prior to sale. it saves the user from having to know that they need to do it, and thus makes apps for that framework "just work".

---

### Post by doas777 on 2009-07-01
> **jonian_g said:**
> So without mono, can't anyone make awesome apps?

it's not nice to choose a programmers langague for them. its their choice. if you wanna make awesome apps without mono, do it. I'll write some awesome apps in C#. I won't tell them to take away your compiler, if you give me the same level of curtsy with my interpreter.

---

### Post by jonian_g on 2009-07-01
> **doas777 said:**
> it's not nice to choose a programmers langague for them. its their choice. if you wanna make awesome apps without mono, do it. I'll write some awesome apps in C#. I won't tell them to take away your compiler, if you give me the same level of curtsy with my interpreter.

You are the one who chooses a programmers langague for him. I never said that nobody should use mono. I just don't see any great benefit having mono preinstalled.
Who told you that I want to take away your interpreter?
If you are going to stop developing in mono if it is not preinstalled, it is your problem.

---

### Post by zekopeko on 2009-07-01
> **jonian_g said:**
> You are the one who chooses a programmers langague for him. I never said that nobody should use mono. I just don't see any great benefit having mono preinstalled.
Who told you that I want to take away your interpreter?
If you are going to stop developing in mono if it is not preinstalled, it is your problem.

The great benefit of mono are apps. F-spot doesn't have a competitor in Gnome. And there isn't a good music player for Gnome that could replace Rhythmbox except Banshee. RB should probably be replaced since it's development is slowing down and Banshee is shaping to be a better music player.
And do please find me something as good as Gnome-Do. There isn't. Gnome-Do is lightyears ahead of any competition, functionally and aesthetically.

There isn't any reason to settle for inferior app because a superior one is coded in a language that MS invented (by looking at Java).
If you don't like mono uninstall it or move to another distro.

Oh and do please explain this sentence.
> You are the one who chooses a programmers langague for him.

---

### Post by zekopeko on 2009-07-01
> **directhex said:**
> *Name of a garbage text editor*

Vi FTW!!!!!!

---

### Post by wayne_cat on 2009-07-01
> **zekopeko said:**
> Vi FTW!!!!!!

OMG!!! ... Billy Joy used stolen code (from SCO UNIX) to cook up Vi ... ask Darl McBride ... he has evidences.

Seriously ... removing Tomboy from Ubuntu would be sexist:

[http://en.wikipedia.org/wiki/Tomboy](http://en.wikipedia.org/wiki/Tomboy)

And that's that!!!!!

---

### Post by ronacc on 2009-07-01
> **wayne_cat said:**
> 

Seriously ... removing Tomboy from Ubuntu would be sexist:

[http://en.wikipedia.org/wiki/Tomboy](http://en.wikipedia.org/wiki/Tomboy)

And that's that!!!!!

fine by me I'm a dirty old man .

---

### Post by monsterstack on 2009-07-01
> **Jestersage said:**
> So thanks, Canonical, for not listening to the FOSS-fanboys and understand what is needed is far more important.

Keep trollin' trollin' trollin'.

Edit: or if not that, understand this: Linux *is* FOSS. Ubuntu *is* FOSS. Mono (regardless of the patent nonsense and the optional win32 codecs) *is* FOSS. The most vocal Mono supporters are keen to stress that Mono developers support FOSS and that they wish to create more FOSS applications for Linux. If Mono was just some lousy proprietary dev suite to create lousy proprietary applications no one would bother supporting it on Linux, and Ubuntu wouldn't even include Mono or even any Mono applications in the universe repos, let alone main. It isn't FOSS fanboyism. FOSS is the reason Linux, Ubuntu and Mono exist in the first place.

---

### Post by wayne_cat on 2009-07-01
> **ronacc said:**
> fine by me I'm a dirty old man .

Google for "CharlesBukowskiBuntu"

I love it ... it's so dirty ... and it comes with the latest mono version. Unfortunately it has no kernel modules for ntfs ... and there are no samba binaries ... but you can mount BSD ufs2 partitions "rw" ... Linus wrote the kernel module ... it is in the "sandals and socks" repository.

---

### Post by Bios Element on 2009-07-02
Enough, Stop feeding the mono troll. Really, It's just stupid. The two of you arguing about mono gets nothing gets done.

Who cares about Mono? If you want to get started on Microsoft's "Patents", Then we better just ban Linux and be done with it as Microsoft claims to hold a few thousand patents on everything from the Menu to the Desktop.

And of course Microsoft is so confident in these patents that they're suing so many people right?...right? Of course not. The patents won't float and Microsoft knows this but helping spread their FUD on your own time is just pathetic.

If you like Microsoft so much you should go use Windows and support them that way rather then go on about Mono. It's tiring, it's stupid and really needs to stop.

---

### Post by mdsmedia on 2009-07-02
> **monsterstack said:**
> Keep trollin' trollin' trollin'.

Edit: or if not that, understand this: Linux *is* FOSS. Ubuntu *is* FOSS. Mono (regardless of the patent nonsense and the optional win32 codecs) *is* FOSS. The most vocal Mono supporters are keen to stress that Mono developers support FOSS and that they wish to create more FOSS applications for Linux. If Mono was just some lousy proprietary dev suite to create lousy proprietary applications no one would bother supporting it on Linux, and Ubuntu wouldn't even include Mono or even any Mono applications in the universe repos, let alone main. It isn't FOSS fanboyism. FOSS is the reason Linux, Ubuntu and Mono exist in the first place.
As one of the FOSS fanbois, thank you. Nicely put.

---

### Post by directhex on 2009-07-02
> **monsterstack said:**
> Keep trollin' trollin' trollin'.

Edit: or if not that, understand this: Linux *is* FOSS. Ubuntu *is* FOSS. Mono (regardless of the patent nonsense and the optional win32 codecs) *is* FOSS. The most vocal Mono supporters are keen to stress that Mono developers support FOSS and that they wish to create more FOSS applications for Linux. If Mono was just some lousy proprietary dev suite to create lousy proprietary applications no one would bother supporting it on Linux, and Ubuntu wouldn't even include Mono or even any Mono applications in the universe repos, let alone main. It isn't FOSS fanboyism. FOSS is the reason Linux, Ubuntu and Mono exist in the first place.

Nicely put.

---

### Post by Viva on 2009-07-02
The orginal post is not a mono argument. It was a genuine question about removing mono. I don't understand why supporters on either side feel the need to discuss mono in unrelated threads when there are hundreds of related ones about mono exist.

---

### Post by monsterstack on 2009-07-02
[Solang]("http://santanu-sinha.blogspot.com/2009/06/solang.html") [blogspot.com] is pipped to be some sort of magical F-Spot replacement by some people. Although in reality it's intended to be more of an F-spot-lite. It isn't a straight forward port like gNote, rather a brand new project in its own right. I tested the 0.1 release. It's still *very* raw (hardly anything works on it yet!), but it's provisionally in the [Karmic repositories]("http://www.mail-archive.com/karmic-changes@lists.ubuntu.com/msg02708.html") [mail-archive.com], so it might be ready for the masses so long as the developer keeps up the pace. Screenies:

[CENTER][[img]http://2.bp.blogspot.com/_WrPRUR8Ep5g/SiPJW2CNIAI/AAAAAAAABzo/dnIrSu4Emfg/s320/search-using-tag.png.jpg[/img]]("http://2.bp.blogspot.com/_WrPRUR8Ep5g/SiPJW2CNIAI/AAAAAAAABzo/dnIrSu4Emfg/s1600-h/search-using-tag.png.jpg") [[img]http://3.bp.blogspot.com/_WrPRUR8Ep5g/SiPJDnuP7-I/AAAAAAAABzI/snLwgmw62tA/s320/enlarged-view.png.jpg[/img]]("http://3.bp.blogspot.com/_WrPRUR8Ep5g/SiPJDnuP7-I/AAAAAAAABzI/snLwgmw62tA/s1600-h/enlarged-view.png.jpg")[/CENTER]

---

### Post by directhex on 2009-07-02
> **Viva said:**
> The orginal post is not a mono argument. It was a genuine question about removing mono. I don't understand why supporters on either side feel the need to discuss mono in unrelated threads when there are hundreds of related ones about mono exist.

The original poster started it - 3 days ago, by posting a long ramble from ITWire's finest demagogue. The actual original question was answered 2 weeks ago.

---

### Post by frustphil on 2009-07-02
From what I learned about mono discussions: Mono could be one of killer tools in developing free/open source software, but it could also be the most lethal weapon MS could use against US. 

Sorry, but I love the open source community. I don't want it to crash suddenly in the future.

---

### Post by bekind2thenoob on 2009-07-02
I have noticed how no one usualy brings up GNOME-Do in mono rants.

Maybe you just cant argue with the coolness?

---

### Post by bakedbeans4life on 2009-07-02
Mono is easy enough to remove from Linux distributions that make use of this questionable (in every sense of the word) piece of software, what I worry about is when it is not.

If Gnome became dependent upon Mono (never say never) how comfortable would you feel about using it? I get queezy just thinking about this possibility.

Mono always seemed like a solution without a problem. It should be included in the repos, but should not be installed by default.

---

### Post by jonian_g on 2009-07-02
> **bekind2thenoob said:**
> I have noticed how no one usualy brings up GNOME-Do in mono rants.

Maybe you just cant argue with the coolness?

Maybe, because it is not preinstalled and will never be. Gnome3 will have a function called Activities that does the same thing and is cooler.

---

### Post by directhex on 2009-07-02
> **bakedbeans4life said:**
> Mono always seemed like a solution without a problem. It should be included in the repos, but should not be installed by default.

Mono was a solution to a specific problem, but reality isn't welcome to this party

---

### Post by zekopeko on 2009-07-02
> **frustphil said:**
> From what I learned about mono discussions: Mono could be one of killer tools in developing free/open source software, but it could also be the most lethal weapon MS could use against US. 

Sorry, but I love the open source community. I don't want it to crash suddenly in the future.

then you obviously didn't pay attention. mono is exposed as much as a any FLOSS project.

---

### Post by directhex on 2009-07-02
> **zekopeko said:**
> then you obviously didn't pay attention. mono is exposed as much as a any FLOSS project.

No, remember, every other app is immune to patent risks.

---

### Post by Vadi on 2009-07-02
It's just magically getting more attention. For no reason whatsoever.

---

### Post by zekopeko on 2009-07-02
> **Vadi said:**
> It's just magically getting more attention. For no reason whatsoever.

it's getting attention from the people who think that writing a companies name with a dollar sign ($) makes them uber cool rebels against the "evil system".

---

### Post by change_mode on 2009-07-02
I don't use any of the applications that depend on mono and I don't think these 3 applications justify the extra space mono needs, especially because they can easily be replaced with similar applications that don't depend on it... so if they ever run out of space for the CD image, mono is the first thing that should be removed.

---

### Post by ronacc on 2009-07-02
there are those of us who learn from history and those who don't .

---

### Post by cb951303 on 2009-07-02
> **Vadi said:**
> It's just magically getting more attention. For no reason whatsoever.

Yeah that makes sense. People love to use inferior products for no reason. MAGIC!

---

### Post by cb951303 on 2009-07-02
> **ronacc said:**
> there are those of us who learn from history and those who don't .

And what history would that be? Is Linux ever sued by MS for patent infringement?

---

### Post by Hyporeal on 2009-07-02
> **Bios Element said:**
> And of course Microsoft is so confident in these patents that they're suing so many people right?...right? Of course not. The patents won't float and Microsoft knows this....

That is the heart of the issue, isn't it? The arguments about morality, choice, bloat, and quality are all window dressing. The central point is whether Linux programs written in C# are going to suddenly become illegal. If so, I think we'd generally agree that we need to move away from those programs. If not, I think we'd generally agree that there's nothing wrong with using them.

This is a legal issue. I don't have the expertise necessary to judge one way or the other (and I sense that I most posters in this thread are in the same situation). Therefore I don't think that appealing to popular opinion is useful in this case. Leave it to the lawyers.

---

### Post by ronacc on 2009-07-02
not yet . but the history is one of broken promises and suits , why should we expose ourselves ?

---

### Post by zekopeko on 2009-07-02
> **ronacc said:**
> not yet . but the history is one of broken promises and suits , why should we expose ourselves ?

We should also remove python. Somebody could sue it into oblivion. Better to be safe then sorry later! REMOVE PYTHON!!!! PROTECT YOUR PARANOIA INDUCED "FREEDOM"!!!!

---

### Post by wayne_cat on 2009-07-02
Python is a "cloned" Microsoft technology? ... OMG!!! ... I REMOVED IT ... NOW I'M FREE!!!!!!!

---

### Post by doas777 on 2009-07-02
> **directhex said:**
> No, remember, every other app is immune to patent risks.

nothing is immune to patent risks. we need to destroy the system to be safe.

---

### Post by zekopeko on 2009-07-02
> **Hyporeal said:**
> That is the heart of the issue, isn't it? The arguments about morality, choice, bloat, and quality are all window dressing. The central point is whether Linux programs written in C# are going to suddenly become illegal. If so, I think we'd generally agree that we need to move away from those programs. If not, I think we'd generally agree that there's nothing wrong with using them.

This is a legal issue. I don't have the expertise necessary to judge one way or the other (and I sense that I most posters in this thread are in the same situation). Therefore I don't think that appealing to popular opinion is useful in this case. Leave it to the lawyers.

The issue is that ANY software can be sued for patent infringement. So to be truly safe you shouldn't use any software that doesn't have patent protection attached to it. Including but ,not limited to, Linux kernel and associated apps.

---

### Post by doas777 on 2009-07-02
> **ronacc said:**
> not yet . but the history is one of broken promises and suits , why should we expose ourselves ?

no, the history is broken threats of suits. not any actual suits.

---

### Post by bodhi.zazen on 2009-07-02
> **directhex said:**
> The original poster started it - 3 days ago, by posting a long ramble from ITWire's finest demagogue. The actual original question was answered 2 weeks ago.

+1 (The OP started the off topic discussion).

What they never say is that mono is released under the GPL. It is nothing more then FUD and fear mongering.

If you don't like mono, remove it or use a distro which does not have mono, such as Fedora, and stop all this off topic ranting already.

The staff is discussing what to do, if anything, about the mono ranting.

---

### Post by cb951303 on 2009-07-02
> **ronacc said:**
> not yet . but the history is one of broken promises and suits , why should we expose ourselves ?

because we're exposed no matter what you do. and it's hypocritical to use hundreds of FOSS software that infringes other patents and not use Mono just because it became popular. What if MS sues us because of SAMBA. What will happen to thousands of corporations that rely on SAMBA for communication with Windows machines?

---

### Post by bodhi.zazen on 2009-07-02
Thread closed.

**This is the old ranting thread, if you wish to discuss mono , use the new thread [Monolith](http://ubuntuforums.org/showthread.php?t=1202591)**

---

### Post by Vadi on 2009-07-02
> **cb951303 said:**
> And what history would that be? Is Linux ever sued by MS for patent infringement?

Uh, yeah? Hello, FAT? Read the news dude. Halloween documents, etc.

Do you seriously think that one of the worlds most successful corporations will be publicly talking about their blackmailing and etc? Lol ):P

edit: oooh, the samba argument. Stop trying to drag others into your hole and stay on topic. Samba actually has legal processes behind them in EU.

---

### Post by bapoumba on 2009-07-02
Welcome to the recurring discussions

---

### Post by cb951303 on 2009-07-02
> **Vadi said:**
> Uh, yeah? Hello, FAT? Read the news dude. Halloween documents, etc.

Do you seriously think that one of the worlds most successful corporations will be publicly talking about their blackmailing and etc? Lol ):P

edit: oooh, the samba argument. Stop trying to drag others into your hole and stay on topic. Samba actually has legal processes behind them in EU.

you didn't like the SAMBA argument? just pick your software. Jo Shields has hundreds of patented FOSS software list on his blog. Research it.

BTW, you have to prove your argument. "has legal processes behind them in EU" means nothing. What is your source?

---

### Post by Vadi on 2009-07-02
Er. The news. Go look.

---

