---
title: "Multimedia Legality Issues"
date: 2006-12-16
forum: Programming Talk
---

### Post by .:{MM&amp;I}:.CodeJockey on 2006-12-16
So, I wanted to make a Media Center PC using Kubuntu on an AMD64 unit, you know, so I can say to my wife: "Look, honey! Using this is great fun!" Then she'd say: "You have improved the quality of ours lives, yet again! I love you (smooch!)" or some other such delusionally idealistic statement I can imagine her saying...

What could it take? Maybe:
 - Download the 6.10 image, burn a disk....done!
 - While that's going on - snap together an AMD Sempron 2800+ on a K8M800 with a new SATA DVD burner and 160GB HD...done!!

Sounds easy enough... and so; it was until I came to actually test playing a disk on my new OS.  "You do not have permission... ...or the source is encrypted....."

While I'm not a Linux expert, I am no noob, either. I'd have to say: "This is just plain vague..." Ever wanting to be the "upper-lip-stiff-keeper," I guessed this to be a CODEC/encryption issue and leapt onto Google to follow the trails of the mighty individuals that sought to slay this very breed of beast.

Then came nine hours of wget-ing, key updating and apt-get installing and, eventually, buying another OS and re-installing several different OS's to test the difference... ](*,)

If it works without issue under different OS's including different versions of the same OS, must be something lacking in this image that the previous had. Hmmm... :-k 

A colleague calls and says: "I had a that problem two versions ago. Just get 'Automatix.'" So, I did (which also had some steps involved.) Starting Automatix, one sees:
 -	"Please note that downloading and installing... ...and other non-free codecs without paying the concerned authorities constitutes a CRIME in the US..."

Because I purchased a copy the other OS and DVD software for that OS and cannot use them simultaneously, I think that I am harmless but: What if I didn't want to buy the other OS?

I mean: I don&#8217;t want to commit a crime, I just want to watch some @#$%&* anime! How can I BUY the codecs and decryption scheme for use under Kubuntu OS?

Bringing my cracked-pot rant to a close: This is without a doubt, the finest distribution of Linux there is. This has become more than just a tinkerer&#8217;s playground, it&#8217;s usable by regular humans and the numbers on Distro-Watch say that I&#8217;m far from alone in making this observation. So, if there is anyone that could coordinate an effort to make a legitimate path to the use codecs and decryption, it&#8217;s the Ubuntu Team (looks over at Mr. Shuttleworth&#8230;)

What it should take:
-	Convince the &#8216;Apt&#8217; squad to facilitate:
o	Package encryption
o	Serial keys to activation decryption
o	Automated addition lines to the sources list by erecting a single package root directory array (kinda like the way DNS works.)
-	Convince Adept crew to facilitate:
o	A prompt to enter a serial key before download of non-free content will begin.
-	In the commercial software arena:
o	Commission a squad to produce a local key management system (in-and-of-itself not open-sourced) so that manufactures can use to protect against duplication then, make the API free&#8230;
o	Recruit perspective component developers that have already secured the right to dev with the CSS algorithm ($5600 per developer) and codecs, suggest a price of $5 per unit.

---

### Post by Wybiral on 2006-12-16
I could be wrong... But I think for that, ubuntu would have to purchase the rights to use the codecs in their installers. Then, they would have to charge us... And well... It just wouldn't be ubuntu anymore. I say, if you've purchased the codecs before for another OS, you should have the right to install them on ubuntu!

---

### Post by .:{MM&amp;I}:.CodeJockey on 2006-12-16
That's not quite true that Ubuntu has to charge.

The supplier of the codec has to charge. I'm saying that the third parties need a gentle 'push' to make that happen.

---

### Post by pmasiar on 2006-12-17
> **.:{MM&I}:.CodeJockey said:**
> 
I mean: I don’t want to commit a crime, I just want to watch some @#$%&* anime! How can I BUY the codecs and decryption scheme for use under Kubuntu OS?
(snip)
So, if there is anyone that could coordinate an effort to make a legitimate path to the use codecs and decryption, it’s the Ubuntu Team (looks over at Mr. Shuttleworth…)

Why would someone as smart as Mark want to waste his time solving problems created by US congress paid by US music/film lobby and big pharmas? How Mark, or anyone can compete with rich lobby who spend millions of collars to elect "right" congressmen and senators? Even if he could - it would be against basic rules of democracy. And Mark is not even US citizen - he cannot legally spend even $1 to influence right solution. Sadly, indifferent US of A voters are responsible for all this mess (by electing and re-electing these representatives).

Problem is, that we have binary blobs, which look *exactly* same for computer, but we **for legal reasons want to handle then differently**: some are free software binaries (protected by copyright in the source - which is distributed separately), some binaries are public domain or similar, some binaries are encrypted but easy to break into, and some are binaries when you break the law only if you try to look into them how they are build, even without decrypting them. And some are even covered by patents: so if it can be proven you looked inside, you are responsible for triple damage. But for computer. they are all binary files, trivial to copy and distribute, with near-zero marginal cost. Read Eben Moglen writings, he is brilliant lawyer and former hacker.

With different laws in different countries, why would Ubuntu want to get involved with this mess? There are other organizations (specific in each country), and Ubuntu wisely restricts activities to technical solutions.

Mess is created by stupid laws, and only law reform can solve it. No technical solutions for this mess, unfortunately.

IMHO, IANAL, YMMV.

---

### Post by .:{MM&amp;I}:.CodeJockey on 2006-12-17
I'm not talking about reverse engineering (usually covered in the other OS's EULA.)
I'm not talking about intercepting encrypted information not intended for me (usually covered in a cable tv company&#8217;s EULA and expressly covered in regs of the FCC.)

It's not a question of how EASY it is to decrypt the information for display. What matters is if a person has secured the right to execute an instance the decryption algorithm which, in this case, is separate from the right an instance of display of the media.
 
So, I'm talking about a facility for packages that are NOT FREE so that the community can actually be back in the realm of FAIR USE when it comes to this very common use of a PC. This thing called Ubuntu is BEAUTIFUL and I would like to put all of my use of it above board so that I can move to using it exclusively.

The laws in context are to protect people that want to charge for their work. The conflict here is that the Open Source community is designed to help programmers make names for themselves by donating highly useful things which become widely used. There is not reason why the two can't coexist. All we have to do is make a way for them to do so.

---

### Post by .:{MM&amp;I}:.CodeJockey on 2006-12-17
> ...And Mark is not even US citizen - he cannot legally spend even $1 to influence right solution. Sadly, indifferent US of A voters...

Why exactly do you think this is just a US issue. Copyright is a UN level issue and this topic about the entire planet.

---

### Post by pmasiar on 2006-12-17
> **.:{MM&I}:.CodeJockey said:**
> The laws in context are to protect people that want to charge for their work. 

Thats the problem. Marginal cost to make a car or sandwich or even to print a CD is non-zero (so obviously you have to pay someone making it for you), but to make yet another copy of any existing file is close to zero. Only for *legal reasons* we need to pretend that some files cannot be copied unless we pay someone.

Imagine if candlemakers persuaded congres to pass a law that people are not allowed to have windows in rooms: they have to buy candles, because candlemakers want to charge for light. And rogue freemasons will start making windows for everyone. What an outrage! Sue them!

There is no technological reason to pay for file copy, that's the problem. Computer files are **different kind of product** (immaterial product), for which our** laws,  designed to handle manufacturing of material products**, cannot apply. And they fail. Rest is legal scaffolding. Can you see it now?

---

### Post by .:{MM&amp;I}:.CodeJockey on 2006-12-17
Well, you know: The day that someone passes a law that I can't have a window will be the day that my Left-wing AND Right-wing brothers will come together to remind people the actual reason folks in the US can own guns (and I’m anti-handgun!)

Until that day, I'll be worried more about things like:
I'm working my hands off for 10hrs a day, so I can't service any contracts during a project period of 5wks. Three more days to get a web site up, merchant account attached, pay some people for nice, frilly graphics. Couple hours of search engine submissions.

100,000 people visit my site, 50 people pay $30, yet 10,000 IP's are logged downloading extras and patches...

You can argue all the differences between real property and intellectual property (which is still property) that you like. None of this would exist if there were not someone paying for it (in some way, direct or indirect) and most of it would not exist if the people that created it didn’t truly believe that someone would pay, them in particular, for it.

Definitely, it is not correct to say that the copying and unauthorized redistribution does little damage to the author or distribution house:
-	Each inquiry about a product is a possible payment to the authority.
-	For each unfair copy that is made, the possibility of an actual sale of the product to the copy receiver is lower.
-	Lowered chances of sale/longer interval between sales mean the cost of the product’s availability from the authorized source goes up.
-	If the margin of a product goes low enough, the supplier will either discontinue support, believing that there is no money to be made or the supplier will increase the price to absorb the cost of the unauthorized copies.

So, eventually, the people that are actually willing to pay for an IP product are the people that pay for the copies that were unauthorized…


Even at that, I’m saying: If the rules are that I have to pay, then let’s make it so I CAN. I have anime over here that is languishing on the shelf! Oh, the humanity!!!

---

### Post by .:{MM&amp;I}:.CodeJockey on 2006-12-17
> ...Marginal cost to make a car or sandwich ...

By the way: Being a person that has my IP used by automotive suppliers, I can tell you that the cost to make a car is about $3100US, not $0.99. This does not include the cost of telling you that it exists and where to get it, carrying it there, housing it for 6months before you even see it or paying the guy that sold it to you...

---

### Post by moopere on 2006-12-18
> **.:{MM&I}:.CodeJockey said:**
> Well, you know: The day that someone passes a law that I can't have a window will be the day that my Left-wing AND Right-wing brothers will come together to remind people the actual reason folks in the US can own guns (and I’m anti-handgun!)

Yeah, well, thats great, yet look where you are today.  You have the power to overthrow dictatorial government yet choose not to do so.  Anyway, this thread is not really about that... 


> **.:{MM&I}:.CodeJockey said:**
> 
You can argue all the differences between real property and intellectual property (which is still property) that you like. None of this would exist if there were not someone paying for it (in some way, direct or indirect) and most of it would not exist if the people that created it didn’t truly believe that someone would pay, them in particular, for it.

Definitely, it is not correct to say that the copying and unauthorized redistribution does little damage to the author or distribution house:
-	Each inquiry about a product is a possible payment to the authority.
-	For each unfair copy that is made, the possibility of an actual sale of the product to the copy receiver is lower.
-	Lowered chances of sale/longer interval between sales mean the cost of the product’s availability from the authorized source goes up.
-	If the margin of a product goes low enough, the supplier will either discontinue support, believing that there is no money to be made or the supplier will increase the price to absorb the cost of the unauthorized copies.

So, eventually, the people that are actually willing to pay for an IP product are the people that pay for the copies that were unauthorized…


Even at that, I’m saying: If the rules are that I have to pay, then let’s make it so I CAN. I have anime over here that is languishing on the shelf! Oh, the humanity!!!

Peeps are not trying to convince you that the laws passed by US congress are not good laws to govern americans - they are just asking you why you think Ubuntu, which is headquartered outside the US, and caters to the world audience should bother itself with a 'problem' that really isn't a problem almost everywhere in the world.

There are linux distributions which cater to the needs of users who live under restrictive regimes, there are also other operating systems which do the same.  

Mark Shuttleworth doesn't need to act on this at all as its not a problem of his making and doesn't affect more than a given percentage of his users in a certain location in the world (ie, not all ppl using ubuntu in the USA are going to be affected, only those wanting to watch/listen to content encrypted/encoded in a certain way).

The thing is that this is an American made problem and needs an american made solution -  in other words, start up a company which packages and sells codecs and decryption utilities legally inside the USA for use with Ubuntu.  You could probably do it yourself from your garage (it would be an internet business model after all).

Best regards,
Craig

---

### Post by po0f on 2006-12-18
I really don't understand why this is in PT, better suited for the Cafe.

---

### Post by .:{MM&amp;I}:.CodeJockey on 2006-12-18
> Peeps are not trying to convince you that the laws passed by US congress are not good laws to govern americans - they are just asking you why you think Ubuntu, which is headquartered outside the US, and caters to the world audience should bother itself with a 'problem' that really isn't a problem almost everywhere in the world.

So: Are you saying that the issue of copyright only affects US citizens and that no country, other than the US, has copyright enforcement legislation?

I guess it's my imagination that people in South Africa, or Australia or EU or Japan should not also worry about fair use because their governments because don't have such laws. It must be that companies in those countries don't care about unauthorized copies, eh?

In the mission statement of this Ubuntu project are phrases like: "...To make Linux usable by non-specialist..." and "...to raise the bar for Linux distributions..."

This thing called Ubuntu has done each of those things, genuinly impacted the world computer market and it has the potential to move into the main stream, so much so that you can hardly do a Google search containing the name "Linux" and not have one of the first two leads contain the names "Ubuntu" or "Kubuntu." On that note, I hear some people at Google use something with a name like "Goobuntu." I wonder what that's about.;) 

I wonder how long it will be before someone thinks an OEM provision is needed... Oops! Too late!
[http://www.internetnews.com/dev-news/article.php/3556736]("http://www.internetnews.com/dev-news/article.php/3556736")

---

### Post by moopere on 2006-12-18
> **.:{MM&I}:.CodeJockey said:**
> So: Are you saying that the issue of copyright only affects US citizens and that no country, other than the US, has copyright enforcement legislation?

I guess it's my imagination that people in South Africa, or Australia or EU or Japan should not also worry about fair use because their governments because don't have such laws. It must be that companies in those countries don't care about unauthorized copies, eh?

You are not talking about unauthorised copies, you are talking about the hassle you are having in finding a legal way to buy the right to use the codecs and decryption products that will enable you to use content on media which you have purchased the right to view/hear.

I'm just saying that "fair use" has long been handled in different parts of the world in ways that actually ensure that legitimate owners of content get 'fair use' of it.  The DMCA and associated legislation does not allow for this, its plain and simple.   If you use a back engineered product to decrypt legally encrypted content on media you own (or more properly, media you are probably licenced to use but don't acutally own; ie, DVD movie) then you are open to being prosecuted and probably jailed forthwith.

Oh, and now that Australia (where I live) has accepted a 'free trade' agreement with the USA the citizenry are no longer free to fair use of their legally owned and licenced content either...


> **.:{MM&I}:.CodeJockey said:**
> In the mission statement of this Ubuntu project are phrases like: "...To make Linux usable by non-specialist..." and "...to raise the bar for Linux distributions..."

This thing called Ubuntu has done each of those things, genuinly impacted the world computer market and it has the potential to move into the main stream, so much so that you can hardly do a Google search containing the name "Linux" and not have one of the first two leads contain the names "Ubuntu" or "Kubuntu." On that note, I hear some people at Google use something with a name like "Goobuntu." I wonder what that's about.;) 

I wonder how long it will be before someone thinks an OEM provision is needed... Oops! Too late!
[http://www.internetnews.com/dev-news/article.php/3556736]("http://www.internetnews.com/dev-news/article.php/3556736")

Ubuntu is usable by the non specialist, and indeed has raised the bar, theres no contesting this as a statement.  But I don't understand why you would think that Canonical as Ubuntu's benefactor has a responsibility to those poor souls such as us who live under restrictive laws?  

Don't get me wrong, if Canonical wanted to spin off a small branch company to sell the likes of you and I licences to use our already owned content on Ubuntu I'd be pretty happy, but it really does strike me that you also have to be prepared to cater for every countries odd laws, all of them, from Diego Garcia through to China.

Cheers,
Craig

---

### Post by .:{MM&amp;I}:.CodeJockey on 2006-12-18
WoRd! This went from a programming proposition to a philosophical argument, really fast!

I&#8217;m not questioning the perception of US law being oppressive. In the city were I live, there is a law that says a cop can come by your house, scale your grass and if it&#8217;s longer than 4inches, give you a fine, then call someone to cut your lawn and charge you for that, too! (Good thing I live in an apartment, I could never leave town for more than a week&#8230;)
I&#8217;m saying that the only legal CSS decryption program I even had a second-hand whiff of was PowerDVD and I, so far have not seen a way to buy even that!

> ...Don't get me wrong, if Canonical wanted to spin off a small branch company to sell the likes of you and I licences...
I&#8217;m not saying that Canonical should be responsible for selling anything, itself.
I&#8217;m saying that because Ubuntu is now top peg on the DistoWatch.com list, and has been for some time, that the Canonical higher-ups can use influence to pull manufacturers into making products for Linux. This way, I don&#8217;t have to be &#8220;fightin&#8217; the Man&#8221; just to use my nice, cool 3D desktop, &#8216;cause, I&#8217;m tellin&#8217; ya &#8211; I read the EULA of the next version of the other OS, I don&#8217;t want to buy that craziness. The EULA has too many holes, like:
-	If you buy PC A which later breaks, and you install it on PC b, they do not have to activate it - The license is per device rather than per instance.
-	If you buy a pre-loaded PC, use it, give it to your friend that then uses it, he cannot, in turn, donate it and the recipients use it &#8211; Limited transfer of license.

The stability of the Linux OS is proven. When I can do business without the other OS, I will. The best hope for that is making the Allen-Bradley-Rockwells and the G.E. Fanucs and the Modicons feel that Linux, and in particular, Ubuntu, is a financially solid place to hold market. For that you start by influencing the home PC market, first but, imagine it:
-    Whole cars being designed and constructed by machines running Ubuntu.
-    Navigational systems, Ubuntu.
-   Game and DVD player in the back of the SUV, Ubuntu.

---

### Post by pirithiumx on 2006-12-18
CodeJocky Like me I believe is a potiential windows convert. Interest sparked even more  by EULA from the ( OTHER :twisted: OS )? we are people used to paying for software and are not entirely against it. I think that Ubuntu is making many more people like us. 

I Think bottom line Codejockey is pleading for a way us people living in these restricted ](*,)  country's can come up with a way to legally use DVD codecs and the sort in a much more painless way that may be integrated into the operating system. 
This in fact may spawn Non-Free ( I beleive this is the term used for software that is not under the GPL? ) software manufacturers more incentive to produce applications for the Linux/Ubuntu community.
I feel that both sides of the coin will only benifit end users world wide. 
After all the path which the (OTHER :twisted: OS) is taking is one of brutal :twisted: world dominance. LINUX Needs to Progress! And it has been and we should not discourage opportunity.

So we here in the US and Australia are bound by legal issues which do not provide a legal means of watching DVD's on our linux work stations, there seems to be no way to even pay someone to be able to watch our DVD's? What do we do? Over throw our governments? or give Non-Free software manufacturers a way to provide software to us?

Bottom line all we want to do is watch DVD's on Ubuntu, while in the US & Austrailia on Monday -Sunday Jan-Dec. If we have to pay the Lords of media to do so ( because they paid off all of the senators ) then so be it. What does it take to make it happen. I think that is what we want to ask the developers. I know it is not a World Problem, but how can we bring the world togehter if we all say it's not our problem. I mean it don't hurt to ask.

---

### Post by pmasiar on 2006-12-18
> **.:{MM&I}:.CodeJockey said:**
> 100,000 people visit my site, 50 people pay $30, yet 10,000 IP's are logged downloading extras and patches...

I fell your pain. I had small software business myself. Try to sell services. Upgrades for registered users only or something.
> You can argue all the differences between real property and intellectual property (which is still property) 

When you say [intellectual property]("http://en.wikipedia.org/wiki/Intellectual_property") , you are mixing together many different laws: patents, trademarks, and copyright. Read Stallman and Lessig about the issue.
> most of it would not exist if the people that created it didn’t truly believe that someone would pay, them in particular, for it. 

Standard FUD, sorry I read rebukes so many times I am immune to it now. Most of free software under GPL was created by volunteers, exactly like art. Linux? GNU utilities? Debian? LOL! You have no idea what are you talking about. Will people stop singing if no-one will get paid for it? Stop playing guitar? Dont make me laugh.

Of course if companies would not employ kernel hackers, Linux would advance slower. But it would not stop.

One kata of martial school of business might be especially relevant to you: good trick is: **turn something your competitor makes, into commodity (something  you buy not as brand product, but based exclusively on price, like sugar or gas coal)**. MS did it to PC makers like IBM: PC became commodity, and you buy the cheapest PC which runs windows. Now IBM is doing same service to MS: Operating system is now a commodity, and you buy the cheapest one which comes with IBM consulting services.

> Even at that, I’m saying: If the rules are that I have to pay, then let’s make it so I CAN. I have anime over here that is languishing on the shelf! Oh, the humanity!!!

I believe Inspire is debian-based distro with all non-free codecs etc. Maybe Inspire will be better fit for your needs. But you might miss excellent community of volunteers, helping newcomers --  for free, in own free time, despite your theories. :-)

---

### Post by pmasiar on 2006-12-18
> **.:{MM&I}:.CodeJockey said:**
> the cost to make a car is about $3100US, not $0.99. .

I never said that cost to make car and sandwich is the same. But both are posivive non-zero. [Marginal cost]("http://en.wikipedia.org/wiki/Marginal_cost") of distributing one additional digital copy of existing digital file is negligible. Digital files are radically different kind of product, and our laws (for products with positive marginal cost) have problems to cope with it. That is the problem.

---

### Post by .:{MM&amp;I}:.CodeJockey on 2006-12-19
OK, we are off on one hell-of-a tangent but:
My point in bringing up the cost of a car is to say that it is not "near zero," which is relative but, if you don't have a $M, and are not the world's fastest metal former, you probably couldn't do it for $3100 starting from iron-ore, ground well petroleum, animal skin and some rather nice wood ( = a classic Jag...) When you are an automotive supplier that fails to make a shipment, the automakers will remind you of that by charging you $3000 for every minute that they were scheduled to make a car and could not (we call those "career enders.")

When I spoke of IP, personally I DO see patents, copyrights and trademarks as groupable for, they are the proof of my unique thoughts forged into something visible, audible and usable by others. If I didn't charge for some, I would not have resources to make more. This thing we are using was provided for by someone that felt the same way.

The Open Source Community has produced so much great work. The work of volunteers is the work of the inspired. What I say is: When inspired work is also provided for, the inspired worker is free to produce his best. Again, this thing is here because someone felt the same.



Back to what brought me to this forum:
As far as I read, their site did not state a per unit royalty (to find out more I'm filling out a form concerning what they call "Schedule C" for hardware/software decrypter makers) so, anyone that pays the fee and signs a non-dislclosure can have the right to distribute a decrypter, provided he states that the resulting work will honor the regional playback system and keep their components treated as secret. By the way, in the FAQs at the CSS site, there is a target statement that sums up to "Linux welcome here..."

On top of that, I shot a note to the cat the runs the apt site. Turns out he's not a developer and pointed me to the Debian list.

If both those things pan, I'll next look for a non GNU compiler that will produce the correct module type.
(Hey, did I just volunteer to dev something? @#$%%$!!!! :-? )

---

### Post by moopere on 2006-12-19
> **pirithiumx said:**
> CodeJocky Like me I believe is a potiential windows convert. Interest sparked even more  by EULA from the ( OTHER :twisted: OS )? we are people used to paying for software and are not entirely against it. I think that Ubuntu is making many more people like us. 

I Think bottom line Codejockey is pleading for a way us people living in these restricted ](*,)  country's can come up with a way to legally use DVD codecs and the sort in a much more painless way that may be integrated into the operating system. 
This in fact may spawn Non-Free ( I beleive this is the term used for software that is not under the GPL? ) software manufacturers more incentive to produce applications for the Linux/Ubuntu community.
I feel that both sides of the coin will only benifit end users world wide. 
After all the path which the (OTHER :twisted: OS) is taking is one of brutal :twisted: world dominance. LINUX Needs to Progress! And it has been and we should not discourage opportunity.

So we here in the US and Australia are bound by legal issues which do not provide a legal means of watching DVD's on our linux work stations, there seems to be no way to even pay someone to be able to watch our DVD's? What do we do? Over throw our governments? or give Non-Free software manufacturers a way to provide software to us?

Bottom line all we want to do is watch DVD's on Ubuntu, while in the US & Austrailia on Monday -Sunday Jan-Dec. If we have to pay the Lords of media to do so ( because they paid off all of the senators ) then so be it. What does it take to make it happen. I think that is what we want to ask the developers. I know it is not a World Problem, but how can we bring the world togehter if we all say it's not our problem. I mean it don't hurt to ask.

Well written post.

To boil down my comments that are not related to overthrowing the American and Australian governments NOW to reclaim our freedoms (big smile): 

Someone, who probably isn't Canonical could/should make the various codecs available as a paid service to the people living under those regimes where obtaining the rights to use their paid for content on Linux is not otherwise available, and there are probably millions of them.

If it could be marketed effectively, and if the installation of and payment for these codecs could be made to be painless then you'd probably even capture a pretty large business audience as well.

The problem though I think, from a business model perspective is that overly restrictive laws, particularly those dealing with fair use (including time shifting) and the playing of owned content on different systems, are just completely ignored by the vast majority of users under those regimes.  

Its a form of civil disobedience I think, but would probably severely restrict the viability of a business set up specifically to 'do the right thing'.

Cheers,
Craig

---

### Post by bieber on 2006-12-19
Okay, seriously, what's wrong with you?  libdvdcss was written and released as *free software* by volunteers who don't demand any money of you (although I'm sure if you'd like to donate, they'd be happy to have the money).

The "rights" you're worried about infringing are the "rights" of the movie producers to control on what devices and in what ways you can watch a DVD.  So, unless you actually think that you should need an arbitrary third party's permission to watch movies that you've purchased, just download and install the damn software.  There's no feasible way for you to get caught, so there's nothing to worry about.  The way I see it is this: to use libdvdcss is illegal, but to use non-free software to watch DVDs is unethical.  I'll take that which is moral over that which is legal any day.

In the meantime, *please* refrain from coming around ranting at us about how our package management systems need to have built in systems to keep secrets from their users (encryptions and unlocking keys and whatnot?  Those are problems for Windows users; we don't want them) so that the "intellectual property" (which is a ridiculous word for two seperate reasons, read Stallman as others have suggested to find out why) of a party that seeks nothing other than to unreasonably control you can be protected.  You may not care about it, but I for one value my freedom; my computer is remaining under *my* control, not Hollywood's.

---

### Post by .:{MM&amp;I}:.CodeJockey on 2006-12-20
Yes, I know: libdvdcss **is** free and it **is** easy to get.

In the day and age when Martha Stewart can actually receive jail time for acting on a phone call conversation
or more toward the context
the RAA names 2600+ people including 11 year old kids that it tracked down by grabbing IP logs
+
SCO brings a case against IBM for trying to dev it's own Linux
+
the Football Coach of Redmond raises a list of 128 liabilities the Linux community can have used against it,

why would anyone be crazy enough to suggest a method for knocking a few items off those lists.

That guy that made that suggestion must be nuts.

---

### Post by moopere on 2006-12-21
> **bieber said:**
> You may not care about it, but I for one value my freedom; my computer is remaining under *my* control, not Hollywood's.


Yeah, this is the civil disobedience thing I mumbled about above.  

Nevertheless it remains that those who use libdvdcss to watch legally purchased DVD's on their linux in America and Australia (and a fistful of other oppressive regimes worldwide) are doing so illegally.  

It might not need to bother you personally, but it leaves you wide open if you are a business trying to replace Windows with Linux and have a need to view encrypted DVD's.  One disgruntled ex-employee and a phone call later.....you know the drill.

Anyway, I digress, let someone from one of the countries where this is a problem step forward, business licence in hand, and sell legal copies of libdvdcss to the masses in their enslaved lands - no need to fiddle with apt-get, nor make demands on Ubuntu or Canonical, or Debian or anything or anyone.  Just talk to the licence holders, get the rights and sell away.

A few scary TV adverts will either have the business customers beating down your door with money to buy the goods or getting off linux mighty fast as they realise the liabilities of using uncontrolled full function free software in certain countries is just a nightmare.

We should all think about these issues before voting next time we get the chance.

Regards,
Craig

---

### Post by .:{MM&amp;I}:.CodeJockey on 2006-12-21
Dudes, it's that I see this particular this as a liability againt home users. It seems to me that the hardly-profitable SCO is out to materialize some bottom line with lawsuites if not package sales. If those guys will go after people like [Autozone or Daimler-Chrysler]("http://www.eweek.com/article2/0,1895,1541989,00.asp") just for using Linux in a business, what will be used and where will they stop when someone feels threatened about _home users_?

Attack the lists, not the attackers...

---

### Post by pmasiar on 2006-12-21
> **.:{MM&I}:.CodeJockey said:**
>  the hardly-profitable SCO is out to materialize some bottom line with lawsuites if not package sales. If those guys will go after people like [Autozone or Daimler-Chrysler]("http://www.eweek.com/article2/0,1895,1541989,00.asp") just for using Linux in a business, what will be used and where will they stop when someone feels threatened about _home users_

More FUD - and not the finest quality either. Anyone from Free Software community interested in SCO suite of lawsuits :-) (novell, redhat, IBM, AutoZone, DC, I hope I did not missed any) is (or should be) aware about [http://www.groklaw.net/](http://www.groklaw.net/) website. Groklaw articles, written by **legal experts** (and not by coders dabbling in law matters) will explain you what **really **is going on (at least they did to me). AutoZone and DC were not any random Linux users - they were SCO customers, who switched to linux, and the case were build on the process of this switch.

You would not ask your plumber about expert opinion on operating systems, right? Why would you trust programmers on slashdot to explain complicated  law cases? 

Of course it is not too wise a strategy for SCO to sue own customers - even ex-customers. All current SCO customers stampeded to the exits. Linux home users have hardly anything to worry about from SCO - except paying too much attention to SCO's FUD. Like one hosting provider did - forgot the company name - who gave to bullying and paid something to SCO and agreed to be example of "customer who settled". As a result, his customers did not liked their hosting fees went to SCO, and they left. Afterwards, director went on the record he woild not gave in knowing what he knows now - he buckled under SCO pressure and regretted it. Not much of a case? Recently, about 60% of the "offenses" which IBM allegedly did were dismissed as unsubstantiated. Go read Groklaw and you will be less gullible to this kind of FUD too.

OK, while I stand on the soapbox, great amount of excellent Linux-related info, selected articles with comments, are at** Linux Weekly News** - [http://lwn.net/](http://lwn.net/) Not free, but the $5 monthly is well worth the price: you also support extremely insightful Kernel Articles by Chief editor Corbet. Or you may read old archives for free, if you are cheapskate.

---

### Post by bieber on 2006-12-21
> **moopere said:**
>  Just talk to the licence holders, get the rights and sell away.

That's not going to happen.  Ever.  A) The "license holders" aren't going to let you sell libdvdcss because it's free software, and if it were legalized, then anyone would be able to read its code and get their "secret" algorithm legally, which they won't stand for, and B) It allows you to deal with your DVDs in a completely unrestricted way, which they don't find acceptable.  The only type of DVD descrambling software they'll allow legally is the kind that will be completely secret and force you to watch DVDs only in the ways they want (meaning forget doing things like backing them up or skipping over the ads in the beginning).  Thankfully, no one's been willing to go through all that to bring "legal" DVD playback to GNU/Linux, and I can only pray that they never will.

---

### Post by .:{MM&amp;I}:.CodeJockey on 2006-12-22
It is true that the "Regional Playback Control" has to be honored and the code within does have to be treated as secret. Their rules even had wording related to employees having memorized the information. There was also a rule about having to certify your statement of destroying books and disks after membership was withdrawn.

There was a clear statement about distribution being royalty-free.

You would still be able to archive your discs.

From what I can remember, this whole "reverse engineered descrambler" thing was related to bootleg cable/sat boxes.

Thanks for the link to Groklaw, it lead to some interesting things related to the actual issue. Through there, I jumped into a gov site for the Office of Copyright which last year this time, took notices from individuals that were concerned that the anti-circumvention law would hamper a "class of work" from creating mechanisms that still fell under fair use of copyrighted material...
A problem is that "class of work" is not defined and so would have had to have been defined in the notices posted. I'm looking to see if any congressional argument came of it.

On top of that, a copy of Linspire just arrived and I'm pulling a Dell 8200 off the shelf. If I can find a DVD player in there, finding out whatever it takes to legally use it here is well worth exploring.

---

### Post by bieber on 2006-12-22
> **.:{MM&I}:.CodeJockey said:**
> 
From what I can remember, this whole "reverse engineered descrambler" thing was related to bootleg cable/sat boxes.



Yeah, that has zero to do with reality.  DVD Jon was pissed that he couldn't watch DVDs on his GNU/Linux box, so he and two other guys wrote DeCSS.  Which is now used by millions of people around the world, not a single one of which is doing anything wrong by using it, and not a single one of which has ever been prosecuted for the act of watching DVDs with free software, so what's your issue with using it?

---

