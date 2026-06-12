---
title: "Is it possible to port games to Linux by back-engineering?"
date: 2006-01-18
forum: Programming Talk
---

### Post by jingo811 on 2006-01-18
This is kind of a continue topic on my previous thread:
**Why Game developers never program for Linux?**
After having listened to a lot of ppl in the previous thread talking about DirectX, OpenGL/OpenAL, and other related stuff it got me thinkin'. #-o
[COLOR="SeaGreen"]
**1. (Replacing the Lego parts?)**[/COLOR]
If you wanted to port modern Windows-only 3D-games to Linux.  Would it just be a matter of figuring out what sections do Graphics, Sound, Game Engine, etc. and then try to replace them with OpenGL/OpenAL API:s?
Or do you have to back-engineer even further down to the Low-level-language in order to port it over entirely?

[COLOR="SeaGreen"]**2. (Any market potential?)**[/COLOR]
If there would be a company who offered to do the above tasks indirectly for Game Developing Companies.  Do you think that there would be a market for it?  Would this kind of porting/back-engineering business be a waste of time and resources to both parties?
I mean sure the cake-% of the Linux game market is incredibly small.
But any existing classic game willing to offer platform compatibility for Linux would gain a big PR-value which must be worth something right?

---

### Post by Jimmey on 2006-01-18
It'd be illigal, I'm pretty sure. If you read the box of most games, it says you're not allowed to disassemble, etc.

---

### Post by gord on 2006-01-18
it'd also (for the most part) be like trying to reverse enginer the human dna so that we have reptile skin instead of mammal, its a task thats better done by letting the programs run as normal and then when they look for the DirectX api, you give them an emulated version that makes it go through opengl. or to put it in other words, [wine :)](http://www.winehq.com)

---

### Post by Viro on 2006-01-18
> **jingo811]
If you wanted to port modern Windows-only 3D-games to Linux.  Would it just be a matter of figuring out what sections do Graphics, Sound, Game Engine, etc. and then try to replace them with OpenGL/OpenAL API:s?
Or do you have to back-engineer even further down to the Low-level-language in order to port it over entirely?
[/quote]

Porting a DirectX game to Linux is a difficult enough of a task, without the need for reverse engineering. I assume you are not a coder, hence you are asking such questions. Try reading some C++ source code from an open source game without  comments or supporting documentation. You will feel like smashing your head into a wall after a few minutes. Now try imagine doing that with reverse engineered machine code  said:**
> 
If there would be a company who offered to do the above tasks indirectly for Game Developing Companies.  Do you think that there would be a market for it?  Would this kind of porting/back-engineering business be a waste of time and resources to both parties?
I mean sure the cake-% of the Linux game market is incredibly small.
But any existing classic game willing to offer platform compatibility for Linux would gain a big PR-value which must be worth something right?

One company did port games to Linux for a while. It was called Loki games, and it went bankrupt some years back. It costs money to do a port, and the end result is the Linux ports ended up costing more than the Windows version of the games. IIRC, the Linux games tended to cost about 30% more than the Windows counterpart (£39.99 vs £29.99). Who apart from the die-hard Linux gaming fans will pay more money for a Linux game compared to a Windows game? 

The end result? Loki died.

---

### Post by Viro on 2006-01-18
[QUOTE=gord]it'd also (for the most part) be like trying to reverse enginer the human dna so that we have reptile skin instead of mammal, its a task thats better done by letting the programs run as normal and then when they look for the DirectX api, you give them an emulated version that makes it go through opengl. or to put it in other words, [wine :)](http://www.winehq.com)[/QUOTE]

I agree. The best chance of getting Windows games ever 'ported' to Linux is to support the Wine project, and hope that they get better, and support more Windows games.

---

### Post by jonathanm on 2006-01-18
[QUOTE=gord]it'd also (for the most part) be like trying to reverse enginer the human dna so that we have reptile skin instead of mammal[wine :)](http://www.winehq.com)[/QUOTE]

wow, what an idea, got to try this

---

### Post by LordHunter317 on 2006-01-18
[QUOTE=Jimmey]It'd be illigal, I'm pretty sure. If you read the box of most games, it says you're not allowed to disassemble, etc.[/QUOTE]That doesn't make it illegal, merely in violation of their (illegal) EULA.

---

### Post by jingo811 on 2006-01-19
Wine ey?!  Maybe I should do a more in-depth looksie at them, here I've been having this prejudice about Wine for years now.  Believing that it's merely an emulator for Linux to run a Windows Platform within Linux, in order to run Windows Software/Games.
 [**Wine**] = [[COLOR="Purple"]Linux --> emulator --> Windows --> Software/Games[/COLOR]]
or...
[**Wine**] = [[COLOR="Purple"]Linux -->[COLOR="Red"](emulator+Windows like APIs)[/COLOR]--> Software/Games[/COLOR]]
???

------------------------------------
I've read an article sometime ago, where Wine said that they wanted permission to modify the Linux core or is it Kernel.  In order to make certain server application ports to Linux more efficient.
Is that a good thing you think to have ppl modify the basic Linux core and possibly start different branches of Linux cores?  (again I may have misinterpreted the intentions of Wine project in that article or the article itself and the whole Linux deal also) :rolleyes:

---

### Post by David Marrs on 2006-01-19
[QUOTE=LordHunter317]That doesn't make it illegal, merely in violation of their (illegal) EULA.[/QUOTE]
Ah, but how illegal is that? Didn't an EULA get upheld in court recently? (I googled for the story and found [this story](http://www.svmedialaw.com/ecommerce-9-eula-upheld-in-dmca-hacker-case.html) which may be what I am thinking of.

---

### Post by gord on 2006-01-19
wine 'emulates' the windows api, the programs run as normal because you are running on the same archetecture. 

[http://www.winehq.com/site/myths](http://www.winehq.com/site/myths) debunks myths like wine is an emulator that runs windows n stuff, there ain't no windows in wine.

---

### Post by LordHunter317 on 2006-01-19
[QUOTE=David Marrs]Ah, but how illegal is that?[/quote]It isn't, in this case.  You can't sign away those rights. 

> Didn't an EULA get upheld in court recently? (I googled for the story and found [this story](http://www.svmedialaw.com/ecommerce-9-eula-upheld-in-dmca-hacker-case.html) which may be what I am thinking of.That involves the DMCA, which is a totally different can of retardation.

---

### Post by mscman on 2006-01-19
[QUOTE=LordHunter317]That doesn't make it illegal, merely in violation of their (illegal) EULA.[/QUOTE]
Yes, actually it is illegal.  When you purchase a game and install it on your computer, you make a legal agreement, that's what the EULA is.  That's why it's illegal to disassemble Windows code (althought it is done...).  Coded programs under EULA are under copyright protection.  Breaking a EULA agreement violates your right to own/possess the software.

---

### Post by LordHunter317 on 2006-01-19
[QUOTE=mscman]Yes, actually it is illegal.[/quote]No, it isn't.  *Redistributing* your reverse engineered program would be illegal, but reverse engineering a piece of software is not.  EULAs can't let you sign away your rights under fair use, and that's included.

Moreoever, if you never distribute what you did, they have no legal grounds to sue you on *anyway*.  So even if it were illegal, it wouldn't matter, as they have no forum they can actually sue you for it in.  You can pretty much do anything you want to something you own as long as you do it in the privacy of your own home.

>  When you purchase a game and install it on your computer, you make a legal agreement, that's what the EULA is.I'm well aware.  That doesn't matter.

> Coded programs under EULA are under copyright protection.No, they aren't *per se*.  Most EULAs go well beyond the provisions of copyright law, and are legal contracts.  You cannot enter into a contract that signs away certain rights.  Rights under fair use are such an exmaple.

> Breaking a EULA agreement violates your right to own/possess the software.Not if you paid for it.  Doctrine of first sale trumps an EULA.

---

### Post by hod139 on 2006-01-19
First, let me say that I hate EULA's and as LordHunter317 so prefectly stated the "can of retardation" DMCA.  Second, I highly suggest reading what the electric frontier foundation (EFF) has to say about EULA's ([http://www.eff.org/wp/eula.php)](http://www.eff.org/wp/eula.php)).

(Court cases from the above EFF article)
As far as the EULA, US courts have upheld the US Copyright Act allowing reverse-engineering for the purpose of "creating a non-infringing interoperable program":  Sega Enterprises, Ltd. v. Accolade, Inc., 977 F.2d 1510 (9th Cir. 1992); Atari Games Corp. v. Nintendo of America, Inc., 975 F.2d 832.

However, LordHunter317 was wrong about their legality, courts have upheld their legitimacy: ProCD, Inc. v. Zeidenberg a case challenging the validity of clickwrap contracts in which the Seventh Circuit court of appeals decided in 1996 that contract terms displayed on a computer screen after purchase did constitute a valid contract. Read the ruling at [http://laws.lp.findlaw.com/7th/961139.html](http://laws.lp.findlaw.com/7th/961139.html). Other court cases about the enforceability of EULAs often cite ProCD.

The bigger problem (at least in the US) is the *horrible* Digital Millennium Copyright Act (DMCA).  This legislation is what states reverse engineering is illegal (along with a ton of other crap) and jeopardizes fair use rights.  I really don't want to rant about how horrible the DMCA is, so again I refer you all to the EFF which has set up a website devoted to the unintended consequences of the DMCA: [http://www.eff.org/IP/DMCA/?f=unintended_consequences.html](http://www.eff.org/IP/DMCA/?f=unintended_consequences.html)

---

### Post by LordHunter317 on 2006-01-19
[QUOTE=hod139]However, LordHunter317 was wrong about their legality,[/quote]No, that's not what I said.  What I said was the they can't sign away your reverse-engineering rights.  I never said EULAs are invalid, just that clause of many of them is.  The cited case agrees with me.

And depending on the terms you except the EULA under, that clause is perfectly valid too.  Software not purchased, but leased, would be potentially under such a consideration.

---

### Post by hod139 on 2006-01-19
[QUOTE=LordHunter317]No, that's not what I said.  What I said was the they can't sign away your reverse-engineering rights.  I never said EULAs are invalid, just that clause of many of them is.[/QUOTE]

LordHunter317, I apologize if you feel I put words in your mouth. I read: 
[QUOTE=LordHunter317]
That doesn't make it illegal, merely in violation of their (illegal) EULA.
[/QUOTE]
which in hindsight is probably your feeling (mine as well) of the EULA, not a statement of fact. 

To get back onto the thread's topic, as my previous post maybe missed, in terms of backwards-engineering a game, the real problem isn't the EULA, but the DMCA.  Hopefully that piece of crap law will be overturned soon, as it is hindering much more than game porting.

---

### Post by LordHunter317 on 2006-01-19
[QUOTE=hod139]which in hindsight is probably your feeling (mine as well) of the EULA, not a statement of fact.[/quote]Well, no, the statement was vauge.  My intent was to mean that the specific portion of the EULA is invalid, not necessarily the concept of EULAs or anything of the sort.

---

### Post by honeybear on 2010-12-04
> **Viro said:**
> I agree. The best chance of getting Windows games ever 'ported' to Linux is to support the Wine project, and hope that they get better, and support more Windows games.

man, wine is SLOW !! (+buggy)

---

### Post by lucasart on 2010-12-04
> **jingo811 said:**
> This is kind of a continue topic on my previous thread:
**Why Game developers never program for Linux?**
After having listened to a lot of ppl in the previous thread talking about DirectX, OpenGL/OpenAL, and other related stuff it got me thinkin'. #-o
[COLOR=SeaGreen]
**1. (Replacing the Lego parts?)**[/COLOR]
If you wanted to port modern Windows-only 3D-games to Linux.  Would it just be a matter of figuring out what sections do Graphics, Sound, Game Engine, etc. and then try to replace them with OpenGL/OpenAL API:s?
Or do you have to back-engineer even further down to the Low-level-language in order to port it over entirely?

[COLOR=SeaGreen]**2. (Any market potential?)**[/COLOR]
If there would be a company who offered to do the above tasks indirectly for Game Developing Companies.  Do you think that there would be a market for it?  Would this kind of porting/back-engineering business be a waste of time and resources to both parties?
I mean sure the cake-% of the Linux game market is incredibly small.
But any existing classic game willing to offer platform compatibility for Linux would gain a big PR-value which must be worth something right?

Tthis is a naive question. anyone who has a decent knowledge of programming will tell you that the answer is no. The problem is that "back-engineering" is not as simple as you may imagine, and practically impossible unless in very simple cases. And besides, it is illegal as proprietary software licenses explicitly forbid it. Have you ever read assembly code ? Maybe that would give you an idea why reverse engineering is (to say the least) not a simple task...

and secondly, windows games are heavily dependant on Microsoft's DirectX libraries. The right way to solve the problam is that all games developpers use OpenGL instead, and then they can write portable games (Windows/Linux/Mac OS). But they don't want to, and Microsoft does everything they can to impose DirectX, thereby limiting the offer of games on non Windows systems.

There are however some OpenGL games running in Linux, but if you are interested in playiong computer games, then Windows is definitely the best choice for you. Or you can use Wine, but it's a real nightmare to get these games working under Wine.

Regarding your second point, the GNU/Linux community is (or was originally) made up of people who only want free software (free in the sense of freedom, not just price, so open source if you want). So I don't think there is a market potential that justifies game developping companies to consider writing portable games.

---

### Post by Some Penguin on 2010-12-04
> **honeybear said:**
> man, wine is SLOW !! (+buggy)

Why did you resurrect a years-old thread just to post a non-contributing whine?

---

