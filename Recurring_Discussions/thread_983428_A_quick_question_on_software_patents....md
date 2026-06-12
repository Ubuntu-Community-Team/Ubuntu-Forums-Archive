---
title: "A quick question on software patents..."
date: 2008-11-15
forum: Recurring Discussions
---

### Post by vexorian on 2008-11-15
Why is it that the software patents ghost is strong enough to prevent us all from having mp3 and DVD playback available after installing ubuntu, yet it is not as scary when we talk about Mono?

I mean, really, why is it Canonical does not mind risking a law suit when the thing in question is something that we don't really need (unless that silly notes software is necessary for you?) While that thing that ubuntu, being a desktop OS, needs so hardly, mp3 playback is not installed by default?

Have you ever seen a person complain about windows not having a desktop notes software by default? Now, have you ever seen users complaining about ubuntu not having mp3 playback?

In other words, couldn't we just have mp3 as easily as we have Mono? Or in the other side of the coin, shouldn't Mono be as hard to install as mp3 is? Shouldn't it be in a restrictive repository?

For example, Fedora 10 does not ship with Mono installed [[1]](http://boycottnovell.com/2008/08/15/no-mono-in-fedora-10/)

And yes, the establishment shall feel free to move this post to recurring discussions so people don't look at it.

---

### Post by amauk on 2008-11-15
** standard "I am not a lawyer" disclaimer **

patents are granted on specific processes within a product

If I create a new audio encoding algorithm, I could patent the process by which I encode PCM
but I can't patent "audio encoding" in general

the key here, is "specific process"

.NET is (by and large) not a specific process, but rather a specification (indeed, I believe it's ISO now)

It is possible to implement .NET without running afoul of potential patents

However, the problem people have with Mono is two-fold

1.) Different countries treat software patents differently (most do not recognise them, but some - notably the USA - do) so you introduce regional problems

2.) as stated above ".NET is (by and large) not a specific process" - If Linux devs were to stray into Windows specific parts of .NET, there may be cause to make a claim, as this could be tied back to a specific process

---

### Post by mips on 2008-11-15
Software patents are BS, period.

---

### Post by amauk on 2008-11-15
> **mips said:**
> Software patents are BS, period.
oh, agreed

---

### Post by eragon100 on 2008-11-15
> **vexorian said:**
> Why is it that the software patents ghost is strong enough to prevent us all from having mp3 and DVD playback available after installing ubuntu, yet it is not as scary when we talk about Mono?

I mean, really, why is it Canonical does not mind risking a law suit when the thing in question is something that we don't really need (unless that silly notes software is necessary for you?) While that thing that ubuntu, being a desktop OS, needs so hardly, mp3 playback is not installed by default?

Have you ever seen a person complain about windows not having a desktop notes software by default? Now, have you ever seen users complaining about ubuntu not having mp3 playback?

In other words, couldn't we just have mp3 as easily as we have Mono? Or in the other side of the coin, shouldn't Mono be as hard to install as mp3 is? Shouldn't it be in a restrictive repository?

For example, Fedora 10 does not ship with Mono installed [[1]](http://boycottnovell.com/2008/08/15/no-mono-in-fedora-10/)

And yes, the establishment shall feel free to move this post to recurring discussions so people don't look at it.

Because mono is sponsored by microsoft :wink: (they have full acces to MS's test profiles and documentation, and AFAIK, MS has even written some of the code :))

---

### Post by Grant A. on 2008-11-15
> **eragon100 said:**
> Because mono is sponsored by microsoft :wink: (they have full acces to MS's test profiles and documentation, and AFAIK, MS has even written some of the code :))

Mono isn't "sponsored" by Microsoft, they just help out due to the Novell-Microsoft deal. See? It isn't so bad.

---

### Post by Frak on 2008-11-15
> **Grant A. said:**
> Mono isn't "sponsored" by Microsoft, they just help out due to the Novell-Microsoft deal. See? It isn't so bad.
It is sponsored to the point where Microsoft acknowledges Mono's existence and will treat it as a legitimate program.

---

### Post by Npl on 2008-11-15
I dont see the point in having Mono installed by default, and I dont see why mp3 shouldnt be included, given that patents shouldve expired by now.

But for protected DVD-Playback you have to deal with encrypted data, which is the DVDs copyprotection. Decrypting it without license = circumventing copyprotection = illegal. It has nothing do to with patents.

---

### Post by directhex on 2008-11-15
> **Npl said:**
> I dont see the point in having Mono installed by default,

In order to install F-Spot and Tomboy, considered the best choices in their class by the Desktop team, installed by default.

> **vexorian said:**
> Why is it that the software patents ghost is strong enough to prevent us all from having mp3 and DVD playback available after installing ubuntu, yet it is not as scary when we talk about Mono?

Because The owners of the DVD and MP3 patents make active legal threats against all & sundry (and even have SWAT teams perform raids during trade shows of people who haven't paid their patent bills)

Conversely, there have been no specific or general threats made to anyone regarding patent violation in Mono. If that ever happens, and the supposedly infringing code can't be changed, then it's out of the archive, simple as that. Same goes for anything and everything in the archive - specific substantiated legal threats will lead to workaround-or-removal

---

### Post by cardinals_fan on 2008-11-15
> **directhex said:**
> In order to install F-Spot and Tomboy, considered the best choices in their class by the Desktop team, installed by default.

I often wonder why, but that's a question for another day.

---

### Post by p_quarles on 2008-11-15
Moved to Recurring Discussions.

---

### Post by vexorian on 2008-11-15
> specific substantiated legal threats will lead to workaround-or-removal


MS' CEO has threatened to sue numerous times: [http://blog.seattlepi.nwsource.com/microsoft/archives/108806.asp](http://blog.seattlepi.nwsource.com/microsoft/archives/108806.asp)

MS already claims to give license coverage or protection conditionally (aka read about the Novell deal) about patents related to mono.

So, the threat seems more real than the mp3 one here... Ask fedora.

> n order to install F-Spot and Tomboy, considered the best choices in their class by the Desktop team, installed by default.
By who exactly?

---

### Post by cardinals_fan on 2008-11-15
> **directhex said:**
> 
Because The owners of the DVD and MP3 patents make active legal threats against all & sundry (and even have SWAT teams perform raids during trade shows of people who haven't paid their patent bills)

Since Fluendo is happy to give away the mp3 decoder, I think it's only left out because of Ubuntu's emphasis on using open source software over closed source by default.

As for the actual concept of software patents, I think they're ridiculous.  I support software copyrights, where devs can copyright their actual code, but I don't see why patents for the idea of something are worthwhile.

---

### Post by Frak on 2008-11-15
FYI, all of the MP3 patent holders have agreed to not pursue anybody who gives away MP3 decoders for free. i.e. not-for-profit.

It's crazy that Ubuntu still doesn't have MP3 support by default while everybody is practically giving it to them.

---

### Post by cardinals_fan on 2008-11-15
> **Frak said:**
> FYI, all of the MP3 patent holders have agreed to not pursue anybody who gives away MP3 decoders for free. i.e. not-for-profit.

It's crazy that Ubuntu still doesn't have MP3 support by default while everybody is practically giving it to them.
That's what I thought.  Where did I read that...?

---

### Post by Frak on 2008-11-15
[http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues)

---

### Post by Grant A. on 2008-11-15
> **cardinals_fan said:**
> I often wonder why, but that's a question for another day.

IMHO, mirage runs circles around f-spot in image viewing.

---

### Post by cardinals_fan on 2008-11-15
> **Frak said:**
> [http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues](http://en.wikipedia.org/wiki/MP3#Licensing_and_patent_issues)
That wasn't it, but it's a good link nonetheless.
> **Grant A. said:**
> IMHO, mirage runs circles around f-spot in image viewing.
I personally love GQView, but the learning curve can be a bit steep at first, so gThumb is a good compromise.  It's based on GQView, but has more GNOME dependencies and a less wantonly cruel interface.

---

### Post by Frak on 2008-11-16
> **cardinals_fan said:**
> That wasn't it, but it's a good link nonetheless.

Wasn't where I heard it first either, but it's the best place to check. Heard it from Groklaw the first time.

---

### Post by directhex on 2008-11-16
> **vexorian said:**
> MS' CEO has threatened to sue numerous times: [http://blog.seattlepi.nwsource.com/microsoft/archives/108806.asp](http://blog.seattlepi.nwsource.com/microsoft/archives/108806.asp)

That's *everything*, from a business manager. Everything. GNOME, KDE, the Kernel, everything that ships in a standard SLES package. Are you suggesting everything in SLES be removed from Ubuntu, including XOrg, because Novell customers get patent protection on it?

> MS already claims to give license coverage or protection conditionally (aka read about the Novell deal) about patents related to mono.

Here you go, show me where: [http://www.microsoft.com/interop/msnovellcollab/patent_agreement.mspx](http://www.microsoft.com/interop/msnovellcollab/patent_agreement.mspx)

> So, the threat seems more real than the mp3 one here... Ask fedora.

Fedora ships Mono

> By who exactly?

The Ubuntu Desktop team, like I already said

---

### Post by directhex on 2008-11-16
> **cardinals_fan said:**
> Since Fluendo is happy to give away the mp3 decoder, I think it's only left out because of Ubuntu's emphasis on using open source software over closed source by default.

Indeed. And Mono is completely Free Software, whichever way you look at it

> As for the actual concept of software patents, I think they're ridiculous.  I support software copyrights, where devs can copyright their actual code, but I don't see why patents for the idea of something are worthwhile.

Absolutely

---

### Post by directhex on 2008-11-16
> **Frak said:**
> FYI, all of the MP3 patent holders have agreed to not pursue anybody who gives away MP3 decoders for free. i.e. not-for-profit.

[http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

The mere existence of that page puts the "agreement" at risk

> It's crazy that Ubuntu still doesn't have MP3 support by default while everybody is practically giving it to them.

It's hardly a burden, though, to have it install itself on demand. Unless you lack internets, of course. But if it's so safe, why does Fedora also not ship with MP3 playback?

---

### Post by Frak on 2008-11-16
> **directhex said:**
> [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

The mere existence of that page puts the "agreement" at risk



It's hardly a burden, though, to have it install itself on demand. Unless you lack internets, of course. But if it's so safe, why does Fedora also not ship with MP3 playback?
That link includes more than just the MP3 decoder, but it also includes decoders and encoders for various other formats. As for the second, it's just a matter of one or two distribution decided not to include the MP3 decoders long ago (Debian and RedHat), and since that day, nobody has changed that.

Though, in 2012, there's no excuse to why distributions won't include the decoder by default.

---

### Post by AllenGG on 2008-11-16
Software patents !! Are they legal, are they legitimate ?
These issues are before the courts in the U.S. right now. The problem emanates from the U.S. but is worldwide.
Please follow [GROKLAW]("http://www.groklaw.net/index.php")
All of the companies that file intellectual patents are concerned, as they should be. Putting a patent on processes, like "double-clicking" , or sneezing has gotten out of hand, exacerbated by extreme court decisions, for example RIM's loss of $456Million to a patent troll ([WashPost)]("http://www.washingtonpost.com/wp-dyn/content/article/2005/10/21/AR2005102101989.html")
Greed and dishonesty prevail. 
Canonical is taking the proper course, they don't need to jump into lawsuits as Microsoft would love this to happen. It's a minefield.

---

### Post by neighborlee on 2008-11-16
> **directhex said:**
> That's *everything*, from a business manager. Everything. GNOME, KDE, the Kernel, everything that ships in a standard SLES package. Are you suggesting everything in SLES be removed from Ubuntu, including XOrg, because Novell customers get patent protection on it?



Here you go, show me where: [http://www.microsoft.com/interop/msnovellcollab/patent_agreement.mspx](http://www.microsoft.com/interop/msnovellcollab/patent_agreement.mspx)



Fedora ships Mono



The Ubuntu Desktop team, like I already said

I said I would not post in  recurring threads but you leave me no choice due to your  error here:

Fedora does not ship mono on its livecd , so next time you decide to bring that up again, take note.

cheers
nl

---

### Post by directhex on 2008-11-16
> **neighborlee said:**
> I said I would not post in  recurring threads but you leave me no choice due to your  error here:

No error, despite what you may believe

> Fedora does not ship mono on its livecd , so next time you decide to bring that up again, take note.

Due to space constraints, that's true - the LiveCD does not contain Mono. The actual install media, however, does. Fedora, unlike Ubuntu, does not use a LiceCD as its primary means of installation.

---

### Post by neighborlee on 2008-11-16
> **directhex said:**
> No error, despite what you may believe



Due to space constraints, that's true - the LiveCD does not contain Mono. The actual install media, however, does. Fedora, unlike Ubuntu, does not use a LiceCD as its primary means of installation.

What makes you sure its space constraints ?

I dont recall version wize, but I think fedora 9 is when mono apps were no longer part of default install, so I seriously doubt it had anything to do with space but if you can verify thats fine.

Based on this ( feel free to discredit it JUST because its from that hateful fud'ing site :)..:

[http://boycottnovell.com/2008/08/15/no-mono-in-fedora-10/](http://boycottnovell.com/2008/08/15/no-mono-in-fedora-10/) , I doubt sincerely it was due to space, due to as noted that fedora is   drawing a wide birth around moonlight ;)

cheers
nl

---

### Post by directhex on 2008-11-16
> **neighborlee said:**
> What makes you sure its space constraints ?

I dont recall version wize, but I think fedora 9 is when mono apps were no longer part of default install, so I seriously doubt it had anything to do with space but if you can verify thats fine.

"Default install" or "Live CD"? You've shown yourself to be confused by the difference before, and I don't really want to waste my time downloading a fedora image if you're just going to go "oh whoops I meant something else"

> Based on this ( feel free to discredit it JUST because its from that hateful fud'ing site :)..:

It comes pre-discredited, not only because of the site it's posted on, but also because the entire post is about your pseudo-research.

[http://boycottnovell.com/2008/08/15/no-mono-in-fedora-10/](http://boycottnovell.com/2008/08/15/no-mono-in-fedora-10/) , I doubt sincerely it was due to space, due to as noted that fedora is   drawing a wide birth around moonlight ;)[/QUOTE]

Okay then. Where would Mono (which is a large dependency on non-Debian-based OSes) fit, given the Fedora 10 LiveCD image currently weighs in at 684 MiB?

And what has Moonlight got to do with it? Start talking about OOXML while you're at it, and the party will be complete!

And why isn't Mono on [https://fedoraproject.org/wiki/ForbiddenItems](https://fedoraproject.org/wiki/ForbiddenItems) if it's been removed?

---

### Post by p_quarles on 2008-11-16
Thread closed, as it's been hijacked by a running spat from another closed thread.

---

