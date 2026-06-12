---
title: "Does OS X violate the BSD license?"
date: 2010-06-17
forum: Recurring Discussions
---

### Post by standingwave on 2010-06-17
I don't really know much about the BSD license (I'm more familiar with GPL). In other words, does the BSD license allow an individual or corporation to take a piece of open source code and make it proprietary? In related news, [does the iPhone violate GPL3]("http://news.cnet.com/8301-10784_3-9737829-7.html")? And further, how would anyone know if MS or Apple are violating GPL in general?

---

### Post by KiwiNZ on 2010-06-17
No it does not

Apple is not using GPL3 versions so no again

---

### Post by LowSky on 2010-06-17
> **standingwave said:**
> I don't really know much about the BSD license (I'm more familiar with GPL). In other words, does the BSD license allow an individual or corporation to take a piece of open source code and make it proprietary? In related news, [does the iPhone violate GPL3]("http://news.cnet.com/8301-10784_3-9737829-7.html")? And further, how would anyone know if MS or Apple are violating GPL in general?

OS/X doesn't violate the GPL. Apple actually does contributes back, and whatever it invents it is legally allowed to keep, and not share if it doesn't want to.

---

### Post by MasterNetra on 2010-06-17
BSD License != Open Source or GPL

BSD is its own thing.

And to answer the title. To my knowledge Apple hasn't violated the BSD License, as I understand it, they can take parts of BSD code and convert it into their own proprietary software.

---

### Post by alphaniner on 2010-06-17
> **KiwiNZ said:**
> No it does not

The title and the first question in his post are essentially opposite.  I'm guessing you were answering the title?

> **MasterNetra said:**
> BSD License != Open Source or GPL

BSD is its own thing.

I'm pretty sure the BSD license is considered an open-source license.

---

### Post by standingwave on 2010-06-17
> **KiwiNZ said:**
> No it does not

Apple is not using GPL3 versions so no again
OK. Thanks. So the cnet article if full of bleep?

---

### Post by Frak on 2010-06-17
> **MasterNetra said:**
> BSD License != Open Source or GPL

BSD is not the GPL: True

BSD is not Open Source: Explain. Interesting story will be interesting.

---

### Post by standingwave on 2010-06-17
> **LowSky said:**
> OS/X doesn't violate the GPL. **Apple actually does contributes back**, and whatever it invents it is legally allowed to keep, and not share if it doesn't want to.Is that a requirement of the license?

---

### Post by Frak on 2010-06-17
> **standingwave said:**
> Is that a requirement of the license?
Any modified software using the GPL must have the appropriate sources accompanied with it.

---

### Post by Groucho Marxist on 2010-06-17
> **Frak said:**
> BSD is not the GPL: True

BSD is not Open Source: Explain. Interesting story will be interesting.

I concur. If I remember correctly, I recall reading in [Practical Guide to Linux Commands, Editors and Shell Programming]("http://www.amazon.com/Practical-Guide-Commands-Editors-Programming/dp/0131367366/ref=sr_1_9?ie=UTF8&s=books&qid=1276803732&sr=1-9") that OSX is based largely off of the BSD Mach Kernel [author's note: I may have listed this incorrectly based off of memory].  Whether or not this leads to a violation of the license, I am interested in exploring and understanding more about this subject.

---

### Post by Bachstelze on 2010-06-17
> **Groucho Marxist said:**
> OSX is based largely off of the BSD Mach Kernel.

The OSX kernel is in part based on Mach, which has nothing to do with BSD. The BSD parts of OSX are in the userland.

> **Groucho Marxist said:**
> Whether or not this leads to a violation of the license, I am interested in exploring and understanding more about this subject.

It is not.

---

### Post by Frak on 2010-06-17
> **Groucho Marxist said:**
> I concur. If I remember correctly, I recall reading in [Practical Guide to Linux Commands, Editors and Shell Programming]("http://www.amazon.com/Practical-Guide-Commands-Editors-Programming/dp/0131367366/ref=sr_1_9?ie=UTF8&s=books&qid=1276803732&sr=1-9") that OSX is based largely off of the BSD Mach Kernel [author's note: I may have listed this incorrectly based off of memory].  Whether or not this leads to a violation of the license, I am interested in exploring and understanding more about this subject.
Let me give you a quick rundown of how the BSD works:

Give the author their due in copyright, everything else is up to you. You don't have to distribute the source code and you don't have to keep the application free to distribute. As long as you make sure you say that *I* made it, do as you want.

Also, the BSD subsystem runs in userland, not kernel.

---

### Post by kaldor on 2010-06-17
Please visit [http://www.opensource.apple.com/](http://www.opensource.apple.com/) for all their FOSS contributions. The OS X kernel (darwin) is also released under the BSD license.

Apple, despite popular belief, did not take open source components and close them/steal them. They made their own things with the HELP of some open source components. For example...

-Darwin (OS X kernel) uses BSD code.
-Terminal.app uses Bash
-Safari, while being proprietary, uses Webkit.
-Command line tools such as nano, vi, etc are there.
-SSH is included by default

etc, etc etc.

They just used some open source stuff to enhance the OS X experience. They didn't steal anything.

Take for example Google Chrome. Google did essentially the same thing; they used the open source Webkit engine and then added some proprietary code on top.

---

### Post by Bachstelze on 2010-06-17
> **kaldor said:**
> 
-Darwin (OS X kernel) uses BSD code.


Darwin is not OSX's kernel. It is basically to OSX what GNU/Linux is to Ubuntu or what DOS was to Win 9x: the base OS upon which it is built. Just like GNU/Linux's kernel is Linux, Darwin's kernel is XNU, and it is based on Mach, not BSD.

*EDIT: By the way, Darwin is entirely open source.*

---

### Post by schauerlich on 2010-06-17
People have done a pretty good job explaining the BSD/FOSS-Apple relationship, but in case anyone wants more information (with relevant links), check the link in my sig.

---

### Post by Bachstelze on 2010-06-17
I should have inb4'ed that.  :p

---

### Post by schauerlich on 2010-06-17
> **Bachstelze said:**
> I should have inb4'ed that.  :p

I never miss an opportunity to pimp that thread. :)

---

### Post by Helkaluin on 2010-06-17
> **Bachstelze said:**
> Darwin is not OSX's kernel.
Am I correct if I say:

[CENTER]Mac OSX
||
Proprietary stuff (Aqua, Cocoa, Carbon, etc.)
|
Darwin (which is APSL)

And, Darwin
||
BSD userland
|
XNU hybrid kernel
[LEFT]
Please correct if I'm wrong.

IIRC someone quipped along the lines of 'the BSD license protects the coder, whereas the GPL license protects the code.' Or is it the other way round...

Gah. A Levels fry your brain...
[/LEFT]
[/CENTER]

---

### Post by cprofitt on 2010-06-17
> **LowSky said:**
> OS/X doesn't violate the GPL. Apple actually does contributes back, and whatever it invents it is legally allowed to keep, and not share if it doesn't want to.

I do not think it is quite so easy... it would depend on if they are the copyright holder of the 'original' work or what the license was of the original work. There are licenses that require 'modifications' to be published under the same license as the original.

---

### Post by Bachstelze on 2010-06-17
> **Helkaluin said:**
> Am I correct if I say:

[CENTER]Mac OSX
||
Proprietary stuff (Aqua, Cocoa, Carbon, etc.)
|
Darwin (which is APSL)

And, Darwin
||
BSD userland
|
XNU hybrid kernel
[/center]
Please correct if I'm wrong.

Depends, what do those double and single lines mean?

> **Helkaluin said:**
> IIRC someone quipped along the lines of 'the BSD license protects the coder, whereas the GPL license protects the code.' Or is it the other way round...

I guess you could put it that way, yes. That is for a very loose meaning of "protect", though.

---

### Post by juancarlospaco on 2010-06-17
**Not violate the License, but the Users, with the price.**

*Webkit is stealed code from KHtml made by KDE*

---

### Post by Frak on 2010-06-17
> **juancarlospaco said:**
> **Not violate the License, but the Users, with the price.**

*Webkit is stealed code from KHtml made by KDE*
Stealed code? I like to look at WebKit and call it KHTML, unsuckified. Also, WebKit is Open Source, so I don't see how it's "stolen".

---

### Post by schauerlich on 2010-06-17
> **Frak said:**
> Stealed code? I like to look at WebKit and call it KHTML, unsuckified. Also, WebKit is Open Source, so I don't see how it's "stolen".

Because when a company uses FOSS code and releases the sources, it's stealing, but when someone else does it, it's sharing.

---

### Post by Helkaluin on 2010-06-17
> **Bachstelze said:**
> Depends, what do those double and single lines mean?
"||" means equal. "|" means 'sitting on top of'.

> Webkit is stealed code from KHtml made by KDEForked from KHTML? Yes. Stolen? No. It's released under a BSD-style license with LGPL components. Was the fork bitter? Ask the devs.

---

### Post by Bachstelze on 2010-06-17
> **Helkaluin said:**
> "||" means equal. "|" means 'sitting on top of'.

Then no. In an OS, the userland is not "on top" of the kernel. Darwin is the combination of a (mostly, but not only, BSD) userland and the XNU kernel. The kernel is not part of the userland, so you should put them side-by-side, not the userland on top.

*EDIT:* Actually, that could be what you meant, but putting it vertically like that is misleading. Darwin is not equal to BSD userland, it is BSD userland + XNU.

---

### Post by Helkaluin on 2010-06-17
> **Bachstelze said:**
> you should put them side-by-side, not the userland on top.
Thanks for clarifying. I learnt another thing today.

---

### Post by wilee-nilee on 2010-06-17
> **Helkaluin said:**
> Thanks for clarifying. I learnt another thing today.

Hey man I like the shameless self promotion Bach is the only four letter word I really love. I live next door to a pipe organ manufacturer, and am also a musician, good playing. I have always had a respect for drummers and organ players all four limbs moving differently thats is always impressive.

On Apple I just wish I had the money to buy a nice Apple laptop, it would be a nice addition in knowledge of OS.

---

### Post by Primefalcon on 2010-06-17
> **schauerlich said:**
> Because when a company uses FOSS code and releases the sources, it's stealing, but when someone else does it, it's sharing.
I hope to hell you were being sarcastic there.......

---

### Post by kaldor on 2010-06-17
> **juancarlospaco said:**
> **Not violate the License, but the Users, with the price.**

*Webkit is stealed code from KHtml made by KDE*

Why don't you ever look things up before you make snarky comments on these forums?

---

### Post by phrostbyte on 2010-06-17
> **Helkaluin said:**
> "||" means equal. "|" means 'sitting on top of'.

Forked from KHTML? Yes. Stolen? No. It's released under a BSD-style license with LGPL components. Was the fork bitter? Ask the devs.

It definitely started out bitter, but Apple was fairly receptive to KDE project's complaints regarding how they handed the original WebKit release.

---

### Post by kamaboko on 2010-06-17
Apple took the trademarked 'iPhone' from Cisco.  Do you think they're concerned about taking some code?  LOL.  Never.

---

### Post by zekopeko on 2010-06-17
> **kamaboko said:**
> Apple took the trademarked 'iPhone' from Cisco.  Do you think they're concerned about taking some code?  LOL.  Never.

IIRC they made a deal with Cisco on that one. Large amounts of money most likely exchanged hands.

---

### Post by zekopeko on 2010-06-17
> **kaldor said:**
> Why don't you ever look things up before you make snarky comments on these forums?

Because being snarky is easier then being educated and informed?

---

### Post by Frak on 2010-06-17
> **zekopeko said:**
> Because being snarky is easier then being educated and informed?
*Ding* *Ding* *Ding*

Here's a cookie.

---

### Post by wilee-nilee on 2010-06-17
> **zekopeko said:**
> Because being snarky is easier then being educated and informed?

:lolflag:

---

### Post by juancarlospaco on 2010-06-17
*I dont say its a bad thing, stealing on open source coding is good.*

---

### Post by K.Mandla on 2010-06-17
This has been discussed and discussed and discussed, so ... moved to Recurring Discussions.

---

### Post by zekopeko on 2010-06-18
> **Frak said:**
> *Ding* *Ding* *Ding*

Here's a cookie.

OMG!!! Snarky-ness is contagious!

---

### Post by Frak on 2010-06-18
> **zekopeko said:**
> OMG!!! Snarky-ness is contagious!
At least I enjoy my snarkiness. That's the only person that matters.

---

### Post by Frak on 2010-06-18
> **zekopeko said:**
> OMG!!! Snarky-ness is contagious!
At least I enjoy my snarkiness. That's the only person that matters.

---

### Post by schauerlich on 2010-06-18
> **Frak said:**
> At least I enjoy my snarkiness. That's the only person that matters.

> **Frak said:**
> At least I enjoy my snarkiness. That's the only person that matters.

You must really enjoy it.

---

### Post by schauerlich on 2010-06-18
> **Frak said:**
> At least I enjoy my snarkiness. That's the only person that matters.

> **Frak said:**
> At least I enjoy my snarkiness. That's the only person that matters.

You must really enjoy it.

---

### Post by KiwiNZ on 2010-06-18
Through the teeth 
Around the gums
Look out lock
Here it comes

A dose of these gas remedy for 24 hours until things calm down

---

