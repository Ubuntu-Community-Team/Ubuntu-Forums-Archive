---
title: "How safe or risky to share landlord's ISP connection?"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by freshinodes on 2008-09-08
I haven't installed Ubuntu yet, but plan to soon.  Once I make the switch from Windows XP and Vista I also plan to drop my current unsatisfactory ISP and to instead use my landlord's Comcast ISP connection; he lives in the house next to me, so I'd be running a CAT-5 line from an open port on his router, which isn't wireless-enabled, by the way.  ( I checked with a Comcast installer who was in the neighborood, and he assured me this would be permissable. ) 

The landlord's son is the primary web user in their house, and he's not technically literate at all - I doubt he could name a programming language, if asked - but, says the father, he does visit a lot of ... let's say "unsavory" web sites, as I understand it: gambling sites and sites that display ... um, scantily-clad persons engaging in mutual robust activity.  He and his dad run XP, if it matters.

I'm not worried about the son or his father re privacy and security, because I'm sure neither would know how to use a packet sniffer, for example, or how to use a script to hack my system or whatever, nor would they likely have the desire or willingness to learn.  But I *am* concerned that sharing a router with them might compromise my system indirectly, because the sites the son visits are generally more prone to malware than other kinds of sites.  It has also occurred to me that if the son does something really stupid on the internet, like harassing someone, for example, that he could try to place the blame for that on me - an unlikely prospect, I think, but it has occurred to me.

I've spent around 20 hours in the last few days increasing my understanding of network technology, starting from about zero knowledge, and learning lots of cool acronyms like VPN, IPSec, PPTP, and so forth, and following links that people in a non-linux nextworking forum suggested concerning free and commercial products like Hamachi, puTTY, etc., and some of the proxy-related add-ons for Firefox. I've learned a fair bit, but nowhere near enough to make an informed decision about whether I can share their ISP connection in relative safety, or to determine exactly what steps I'd need to take to do so.  I had no idea that network security was as potentially complex an issue as it now appears to me to be.  

And since most of what I've learned was not specific to GNU/Linux or Ubuntu, I thought it'd make sense to ask here whether Ubuntu might include or support any relatively *simple* solution for the relatively limited goal I'm trying to accomplish.  I didn't see anything in the help on this (or in previous posts) that I felt I could implement in any reasonable period of time, given my very newbie level of understanding, and that I was fairly sure would adequately address the issue.

So I'd be grateful for any opinions about how risky this might be compared to, say, using WiFi at a public hotspot or sharing a connection in a college dormitory, and especially for any ideas about how I might address the issue in as simple a way as is consistent with some minimal-but-reasonable measure of security.

I'll also mention that a couple of people on the non-linux networking forum I've been reading suggested I could buy a router of my own that provides a hardware firewall or hardware encryption and put it *behind* the landlord's router, i.e. just plug the cable I get from them into my own router.  That seemed like an attractive solution to me in that I like the idea of a hardware-based layer of isolation, but is it feasible? 

I realize this is a long post.  If it's inappropriately long let me know, please (although I won't be able to check for replies for a few hours). Thanks!

---

### Post by lukjad on 2008-09-08
I am no expert but...
I would not share a router with someone that may have an infected PC. Even if they do not know it, there may be a packet sniffer or other type of spyware that could track you online. I don't know really what real risk there may be, but I would not do any online banking until you find out. 

As for the length of your article, I don't mind it, just realize not everyone is going to read it all.

---

### Post by t0p on 2008-09-08
I don't think you need to worry about malware if you'll be running ubuntu.  Any windows nasties the landlord's son may pick up will not affect you.

---

### Post by anewguy on 2008-09-08
Regardless of what the tech said, Comcast does not allow sharing of their service - it is specifically stated in their rules.  I don't know if you could get in trouble (read "liable for back fees") or if just the purchaser from Comcast would be.

We all know about using someone else's wireless connection, figuring if they're dumb enough to leave it open then use it, but even that is against Comcast's rules.  By physically running a cable between 2 different houses, I guarantee you would be breaking their rules and subject to prosecution.

Please keep that in mind.

---

### Post by OffAxis on 2008-09-08
You can install a router on your end and that will isolate your section of the network from the landlord, but being the final gateway between your place and the internet his router can still maintain a log of all your activity (if you care).
If you're in the states, you should be able to pick up a wireless router for about the same price as a wired one, and if you can convince your landlord to change his out, then you won't be doing things like drilling through exterior walls. Much cleaner, easier, and faster.


> I checked with a Comcast installer who was in the neighborood, and he assured me this would be permissable. 
Probably not...I can't imagine Comcast leaving a big hole like this in their service agreement; the contract should specify a single family dwelling or an address for service - something which would preclude this connection from being shared out to the whole neighborhood. Watch out.

---

### Post by OffAxis on 2008-09-08
> We all know about using someone else's wireless connection, figuring if they're dumb enough to leave it open then use it,
The last time I checked (about 3 years ago) this was falling under the 'wiretapping' section. Unless things have changed since then (and there certainly may have been some clarification -seemed a bit harsh to me) this makes it a federal crime in the U.S.

---

### Post by caljohnsmith on 2008-09-08
To put things maybe a bit more in perspective, consider the millions of people who use a DSL modem to connect to the internet; the modem has no routing functionality, and therefore it does not act as a hardware firewall like a router does; that's because as you may have all ready read about, routers use "network address translation" or NAT, which by its very nature acts like a firewall. But if you have good firewall software on your machine, that can be just as good as a hardware firewall. And that's how millions of DSL users who don't use routers protect themselves, and it works great as long as their firewall software is good. 

But the above example also makes another point: DSL users without routers who use software firewalls for their protection are protecting themselves from attacks from the *entire* internet; anyone in the world could try and access their IP address, yet if they use good firewall software they can be totally safe for all practical purposes. When you are using your landlord's router, you have a hardware firewall between you and the internet; the only threat then to your computer is those who share your LAN, namely the landlord and his son. So bottom line, if you run good firewall software on your computer, you will be completely safe when it comes to TCP/UDP port hacking, considering that the odds of an attack have been reduced from millions of computers on the internet down to just a few computers on your LAN. 
> **freshinodes said:**
> 
I'll also mention that a couple of people on the non-linux networking forum I've been reading suggested I could buy a router of my own that provides a hardware firewall or hardware encryption and put it *behind* the landlord's router, i.e. just plug the cable I get from them into my own router.  That seemed like an attractive solution to me in that I like the idea of a hardware-based layer of isolation, but is it feasible? 
Like I was trying to point out above, I really don't think it is necessary to spend the money for an additional router just to protect yourself from your landlord and his son. From all the security articles I've read and from my own experience, I think good firewall software is perfectly adequate. Of course it's your decision though, I'm just offering my opinion. :)

---

### Post by mkvnmtr on 2008-09-08
If you do on line banking or buy stuff with your credit cards you should not use a connection that is not only yours. No matter what the installer says I also would not believe Comcast would not try to charge you at a later date if they find out. For what a connection costs it hardly seems worth it to take the chance.

---

### Post by Old_Grey_Wolf on 2008-09-08
If the Landlord is offing this Internet Service to you, the Landlord is defiantly violating the Terns of Service agreement between the Landlord and Comcast. 

Another concern I would have is whether these computer un-savvy people have the router set up correctly. A router can provide security but only if it is set up correctly. 

Personally, I would pass on the offer.

---

### Post by handydan918 on 2008-09-08
Well, since everyone else has sounded off here, I may as weel make an **** of myself, too.

First, contractual problem with Con-Cashed is beetween them and their customer. 
That would be your landlord. If he is offering a shared connection, their legal remedy is against him, not you.

Second, from a security standpoint, i would say that if you have some sort if useful interface set up for using iptables (the universal *nix firewall) then you should be alright, if you do a bit of research about port functions and such. It sounds from your post as though you are not averse to reading. 
That is good.
I would worry not at all about an "accidental" infection from a random pr0n site. It's not that Linux can't be hacked, it's that no one goes for the toughest 0.1 percent of the market.
Putting a second router between you and your landlord is not only possible, but just short of trivial. About 40.00 (USD) worth of hardware and 10 minutes worth of configuration (after the obligatory 2 day learning curve) should make you one of the least attractive targets on the net.

---

### Post by niteshifter on 2008-09-08
Hi,

Basically, the OP text boils down to this:

"Hi - I'm thinking of accessing the internet through a network that is compromised. Is this a smart thing to do? Am I (is my traffic) safe?"

Answer: No.

---

### Post by Vadi on 2008-09-08
I doubt your Ubuntu PC would be affected, but your internet packets would be. You could be getting fake websites and such :\

---

### Post by LowSky on 2008-09-08
its the internet its dirty and grimy and full of crap. connect to it without protection and you might get sick. use protection then you might not get sick. either way you get free connection with your lanlord taking all the risk.
i say start downloading all the stuff you ever wanted and let him worry.

---

### Post by anewguy on 2008-09-08
> **OffAxis said:**
> The last time I checked (about 3 years ago) this was falling under the 'wiretapping' section. Unless things have changed since then (and there certainly may have been some clarification -seemed a bit harsh to me) this makes it a federal crime in the U.S.

Yes - you are correct.  I was trying to make a point and assumed (and we know what that made me!  :) ) the poster would understand the illegality there as well.  Thank you for pointing out in specifics what I should have included in my post!!  


Dave  :)

---

### Post by freshinodes on 2008-09-09
Wow, quite a response, quickly generated, and all so well-mannered and  civil compared to other forums I've looked at.  Gotta love that Code of Conduct; very "ubuntu" of you all. Thank you.

( Note: Because several contributors remarked upon the illegality of ISP signal/connection theft, I've appended a fairly detailed explanation to the end of this post that should address most of the concerns that were expressed. ) 

It was my understanding from the reading I've done that it would be nearly impossible, through the use of a packet-sniffer, at least, to retrieve https ( note the "s" ) login information I might enter at any time. All the web transactions or logins I use regularly that involve money in any way employ https, and most of those that don't involve money at least use an encrypted login. If my information about that is sound, then I would feel reasonably confident that I'm unlikely to expose myself to financial fraud if I decide to go ahead and share the ISP connection.

I realize this doesn't rule out the possiblity of ... are they called "spoofing" sites, or "phishing" sites?  Of being directed to a look-alike site by a compromised or intentionally misleading Domain Name Server, I mean, a hazard that Vadi mentioned.  But that would be prevented to some extent by Firefox 3.x's new anti-phishing alerter facility, yes?  As an additional precaution, I've read that it would be wise to *manually* set the IP addresses of the DNS I want to use?  And I imagine there must be software out there - or perhaps built into Ubuntu, or into the Firestarter firewall package? - that prevents these addresses from being changed without one's explicit permission to do so?  

( HandyDan, I'm speculating that your mention of iptables is related to this?  I intend to read up on iptables, in any case. Thank you for the suggestion, and for your comments about NAT, which I had encountered, breifly, in my "learning curve" travels so far.  A few people commented that NAT was pretty simple to break/hack, as I recall, but I'm not concerned that my landlord or his son will or could do so, at least. ) 

So at this point, I'm thinking that if I do go ahead with this, that I'll 

(1) Avoid non-encrypted logins for anything I really care about or that involves finances;  

(2) Use firewall software and/or a second router of my own, behind the one facing the modem and internet; 

(3) Manually set the IP addresses for my DNS and take steps to make sure those can't be easily overwritten without my explicit permission; 

(4) Optionally use a proxy server if I care about my surfing history being tracked, and 

(5) Possibly install Ubuntu with the option to encrypt the hard drive, too, if it doesn't complicate administration too greatly.  ( Opinions about that would be most welcome! )    

With the point that caljohnsmith makes to the effect that my exposure is likely to be restricted to the people on the LAN, rather than the entire internet (always assuming the landlord's router, which Comcast installed and - I think - also sold, is doing its firewall duty), and with the above steps in place, it seems to me that that my computer might present a comparatively unappealing target.  Anyway, I'm hoping this would be sufficient for an initial install until I can read up on, and implement, more comprehensive "hardening" methods... You don't have to run faster than the bear, they used to say when I worked in Grizzly country, you just have to run faster than the other guy. ;)
 
Or have I gotten ahead of myself?  Have I misunderstood something fundamental here?    

( Here follows a rather long and somewhat off-topic clarification re the legality issue of this proposed sharing of a Comcast ISP connection:

I probably should have been more specific about why the Comcast rep said this would be permissable - I didn't go into detail because my post was already too long, and because no one on the previous ( non-Ubuntu, non-linux ) forum I had posted to previously raised the question, or apparently cared one way or the other.  I like it that people here *do* care about the issue, however, as I do myself, and likewise appreciate the informational warnings and the respectful tone with which they were delivered.  The "vibe" here re ethics and legality is as it should be, and is much more congenial to me than that which obtained on the other forum I posted to previously.  

As I explained to the Comcast installation representative, the house I'm renting and the landlord's house are legally the same property.  The very small house I'm in has been added to by the landlord since he bought the property 40+ years ago, but it was originally a caretaker's cabin for a  fruit orchard that blanketed a parcel then outside the city limits.  ( Great huge plums on several remaining trees in each of our back yards all this month; very pleasant, indeed. ) 

When my landlord built his place next door, he added house numbers to the house I'm in and to his new house, but my house number is a legal fiction.  Although he had two other parcels from the original orchard legally subdivided, and sold them, this one never was subdivided from the property his house stands on, and only his house number is actually registered with the County Tax Assessor, not mine, although they are aware that mine is present here. ( I checked when I became curious after I could find no reference for my house number on Zillow.com; I'd been thinking vaguely of offering to buy the place, and wondered about its appraised and assessed values. ) 

The house I'm in has been "grandfathered" in what city ordinances refer to as a "mother-in-law unit", even though it's a freestanding house.  We have a single utility bill between us for water/sewer/garbage, which he pays, although separate electrical service and metering were installed on my house five years back, and I pay for the electricity I use.  The post office delivers mail to me in a separate mail box, but that's evidently just a courtesy.  

The Comcast rep said the situation was no different from his company's perspective than if I were living in the same house as the landlord and his son - he had dealt with "mother-in-law units" previously, he said (they're fairly common in our city) and was aware of Comcast's policies about them.  Also, when the landlord had Comcast install the modem and router in his house, he paid for an installation that comprises up to five *simultaneous* connections; I'm dead certain of that.  As long as the landlord wasn't explicitly charging me for the use of the connection, as a fee above and beyond the rental I pay on the house, the rep said, it was fine.  

I suppose, that to be extra careful, I could pay the landlord's expense to have Comcast come out and bury/run the cable themselves, or buy a wireless router as OffAxis suggested, and then have them come out and install it in place of the existing one, although their installation sevices are quite expensive.  I'll at least ask the landlord to get some documentation of the propriety of this from Comcast, himself, and "copy" me with that, just to make sure no question arises in the future.  But the rep seemed quite sure of what he was talking about, and I saw - and see - no reason to doubt his familiarity with the issue. 

Excuse the long explanation - again - but I didn't think it right to leave you all with the impression that I condone signal/connection theft; I don't.  Thanks for your patience in reading.  

End of rather long and somewhat off-topic clarification. :) )

---

### Post by lukjad on 2008-09-09
I still would not share a web connection with someone whose security is compromised. Even if the https are relatively secure, there will still be a risk. Also, there is more information that is available and valuable to the spammers/crackers than your credit card number (while they would like it anyway). For instance, your browsing history is useful, as it your login names and passwords to various sites, such as this one. If you try to abstain from logging onto sites that are not https, then you just be limiting yourself. Why have an Internet connection when all you can do is nothing you really want to?

---

### Post by Vadi on 2008-09-09
For what it's worth, this isn't the most "dangerous" network. There are tons of wireless routers out there that are completely open, and probably present the same security concerns.

Personally, I'd just keep a close watch on my history - credit, email (gmail has a "Last account activity" feature at the bottom), and change my passwords regularly. That alone will give you more protection than the average computer users.

---

### Post by anewguy on 2008-09-10
How do I get some plums???? !!! :):)

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-09-10
> **niteshifter said:**
> Hi,

Basically, the OP text boils down to this:

"Hi - I'm thinking of accessing the internet through a network that is compromised. Is this a smart thing to do? Am I (is my traffic) safe?"

Answer: No.

hehehe the internet is a network that i would consider compromised

---

### Post by t0p on 2008-09-10
> **lukjad007 said:**
> I still would not share a web connection with someone whose security is compromised. Even if the https are relatively secure, there will still be a risk. Also, there is more information that is available and valuable to the spammers/crackers than your credit card number (while they would like it anyway). For instance, your browsing history is useful, as it your login names and passwords to various sites, such as this one. If you try to abstain from logging onto sites that are not https, then you just be limiting yourself. Why have an Internet connection when all you can do is nothing you really want to?

Some people are talking like the landlord's internet connection has been compromised.  It hasn't.  Just because the landlord's son likes to visit gambling and porn sites, doesn't mean any nasties are lurking on the LAN.  And anyway, the OP can endeavor to teach his neighbors some safe browsing habits.

---

### Post by oldsoundguy on 2008-09-10
First read this:
[http://www.howstuffworks.com/home-network.htm](http://www.howstuffworks.com/home-network.htm)

That should make you familiar with how a network and internet access WORKS and the terminology.

Second:  (in the US) Any person that has an internet connection can grant permission for others to access same.  Especially a property owner to tenants (can be an incentive for renters), apartment houses, condos and so on.  No LEGAL restrictions as long as the system uses it's OWN router/hub system.  The landlord assumes the maintenance responsibilities of anything home side of the modem to include cat 5 cable or wireless operations.

Third:  If you look at the diagrams of a "home" network, you will see that in no way do you "go through" another computer if you use a router/hub set up.  You access on the web side of the computer and unless networking permissions are granted by ALL parties on the network, there is no exchange of data possible.

Forth:  The best way (has been suggested) is to buy your own router.  Getting one with wireless capabilities for later use by YOU and you alone as you can protect it, may be a thought, but not needed as you can get a hardwired access point and do the same thing (I have two on my home network to increase signal strength for wireless computers in my place.)

Finally: It makes no difference between BRAND names of routers chosen, but for the sake of ON LINE HELP if needed, getting the same brand as that of your landlord is recommended. 

Bottom line .. go for it!

---

### Post by OffAxis on 2008-09-10
> **oldsoundguy said:**
> 

Second:  (in the US) Any person that has an internet connection can grant permission for others to access same.  Especially a property owner to tenants (can be an incentive for renters), apartment houses, condos and so on.  No LEGAL restrictions as long as the system uses it's OWN router/hub system.  The landlord assumes the maintenance responsibilities of anything home side of the modem to include cat 5 cable or wireless operations.


No. That's explicitly forbidden in Comcast's Terms of Use.
> **7. Use Of Services**

You agree that the Services and the Comcast Equipment will be used only by you and the members of your immediate household living with you at the same address and only for personal, residential, non-commercial purposes, unless otherwise specifically authorized by us in writing. 
The full text can be found here:
[http://www.comcast.net/terms/](http://www.comcast.net/terms/)

Not having a recognized address may qualify as 'immediate household', but it certainly doesn't extend to apartment buildings.

---

### Post by oldsoundguy on 2008-09-10
"unless otherwise specifically authorized by us in writing."

Right.  EASILY done.  All you have to do in most cases is ASK and sign a waver assuming (as holder of record) responsibility for on line conduct or switch over to a commercial account.  My brother just did so WITH COMCAST in his apartment complex.  But you had best believe there will be somebody watching!  AND with the new limits on traffic that Comcast has said they are going to initiate, that could, in and of itself, present usage issues on a residential sharing system.

HOWEVER, if you want to get a COMMERCIAL usage tag on your service for 10 to 20 bucks a month more (not sure of the actual charge as brothers set up was 17.50 USD), there are no limitations.

BUT, there are many that share a connection, the idea being "don't ask, don't tell!"  And it is REALLY easy to do if they go wireless!

---

### Post by lukjad on 2008-09-10
Just because something is easy, doesn't mean that it is moral, or even legal.

---

### Post by fballem on 2008-09-10
I wouldn't recommend it for the ethical and legal reasons - it's a generous offer on the part of your landlord, but not worth the risk to him or you. By the way, any idea how much your own service would cost, particularly if bundled with cable and/or phone?

---

### Post by barney385 on 2008-09-10
Anyone who gives a damn what Concast puts in a contract just doesn't get it.

Concast does not and never will, supersede Federal or State regulations.

---

### Post by crispy_420 on 2008-09-11
Don't necessarily trust those Comcast installers, they are sub-contractors and are there make a quick buck. They will tell you anything cause they don't care. And I can bet a week's pay that Comcast will forbid this.

As far as malware, you should be in the clear with Ubuntu.

I don't know if anyone has mentioned this yet but one thing to worry about is being the scape goat. Say said landlord's son does something wrong such as file sharing, child porn, etc.; who's to say that you get the blame?

---

### Post by carusoswi on 2008-09-11
Most of the responses on this thread cause me to bemoan the times in which we live.  Some of you would have me believe that if I piggy back onto someone's open wireless connection to browse this BBS I'm committing a felony.  That's ridiculous.

I suppose that, when my grown daughter comes to my house, she is also committing a felony when she taps into my "secure" wireless connection to browse the net while she is a guest in my home.

. . . and, when invited to do so at no charge, the OP is committing a felony by connecting his ethernet card to the landlord's router.

C'mon.  Loosen up folks.  The landlord is paying for up to five connections at his address, the OP lives at his address, no violation will take place by the OP's use of a free connection.

As for the security issues, you are more vulnerable (much more so) using your ATM card at a supermarket than the OP if he avails himself of the landlord's generosity.

Let's get real.

Caruso

---

### Post by lukjad on 2008-09-11
If you take something that does not belong to you, that is a crime. It doesn't matter what it is, so long as it is not yours to take, it is wrong. If you are walking along and you see that someone left their door open, you wouldn't just walk into their house and take a chair or two, would you? So how is this any different than tapping into someone's unsecured network without their permission. That being said, the OP is not doing this, and then we get into technicalities. And that is where this conversation is having problems.

Sometimes a representative of a company will say one thing, and another will say another. It's really hard to know who to believe, and since I have never used Comcast, I cannot really give advice on that matter.

---

### Post by antgul338 on 2008-09-11
get a 30 dollar wireless router

---

### Post by stalkingwolf on 2008-09-11
We have Comspeed here. Our landlord supplies our internet connection as part
of our rental agreement. That connection supplies both our house and his
business.  Comspeed is aware of this and there is no problem.  I dont know about Comcast.

---

### Post by carusoswi on 2008-09-12
> **lukjad007 said:**
> If you take something that does not belong to you, that is a crime. It doesn't matter what it is, so long as it is not yours to take, it is wrong. If you are walking along and you see that someone left their door open, you wouldn't just walk into their house and take a chair or two, would you? So how is this any different than tapping into someone's unsecured network without their permission. That being said, the OP is not doing this, and then we get into technicalities. And that is where this conversation is having problems.

Sometimes a representative of a company will say one thing, and another will say another. It's really hard to know who to believe, and since I have never used Comcast, I cannot really give advice on that matter.

Why are you injecting this element into the discussion?  No one is taking something that is not theirs, and no one is walking through an open door uninvited.

If anything, the OP is exercising more than required circumspection with respect to this issue, and the landlord has specifically invited him/her to share the connection which is, as it turns out, at the same mailing/street address.

Caruso

---

### Post by lukjad on 2008-09-13
Please read my text that you quoted:
> That being said, the OP is not doing this, and then we get into technicalities. And that is where this conversation is having problems.
I was responding to your post that said:
> Some of you would have me believe that if I piggy back onto someone's open wireless connection to browse this BBS I'm committing a felony. That's ridiculous.
I made sure to point out that the OP is not doing this. Others that have posted before mentioned that people tap into unsecured networks. I may have misunderstood your intent as saying that that was fine. If that is the case, I apologize.

---

### Post by freshinodes on 2008-09-13
Update:  I was able to connect with a Comcast rep 
via live-chat and was once again told that it would 
be just fine for me to share my landlord's internet 
connection at his invitation.  

( Caveat: this is a long post, and might be getting 
  too specific and technical to really fit in the 
  Absolute Beginners forum.  Didn't see any way 
  to avoid the first, but will certainly have no 
  objection if moderators need it to be edited 
  for length or edited and moved to a different 
  forum.  To everyone who has been following 
  this thread so far, I am grateful. ) 

I've appended a transcript of that chat session, to 
the end of this post, for those who are interested, 
and have also positioned my own concluding 
remarks about the ethics & legality issues so that 
they immediately precede that transcript.    

I'm more than satisfied on those points, and would 
like to move on to conclude the security/privacy 
aspect of the thing, if people are willing to 
entertain that just a bit longer still.

Specifically, I've learned that Comcast provides  
each customer account with one dynamically-
assigned IP address, but allows the customer to 
obtain up to four more of the same, at a cost of 
five dollars (U.S.) per additional address.  The 
information Comcast provides online about this 
is minimal,  

[http://www.comcast.com/customers/faq/FaqDetails.ashx?Id=2428](http://www.comcast.com/customers/faq/FaqDetails.ashx?Id=2428)

but I also asked the live-chat rep about it, as you'll 
see if you have the ( pretty extraordinary ;) ) patience 
to read through the appended transcript.

Since first hearing about this possibility, I've read 
about "provisioning", and I'd just like to confirm 
that I understand what that means, and what's 
implied by using a second IP address.

Under this arrangement, I'd split the coaxial cable 
that Comcast brought onto the property for the 
landlord's service in the first place, split it at the 
"on-property source", I mean.  I'd then run the 
resulting second coaxial cable to a second modem, 
presumably in my house.  So I'd still have a 
cable running from my landlord's house, but it 
would be a coaxial one coming from a splitter 
rather than a CAT-5 cable coming from one of 
his open router ports.  I'd then attach a newly-
purchased router to this second cable modem 
and I'm good to go, i.e. to connect my PC 
( wirelessly or via CAT-5 ) to the router to 
the modem to Comcast and, hey presto! 
( I've always wanted to say that ) to 
the internet.  

I'd be grateful if someone would explain any 
errors in my understanding of this config-
uration, which, I'm told would provide pretty 
strong "isolation" from whatever the landlord's 
son might be into on the web. I'm still not 
entirely sure, despite the reading, that I 
completely understand what the Comcast 
live-chat rep meant by this statement: 

  "Additional IP address will be provisioned first 
   in the billing account for the account holder. 
   The provisioning would take up to 24-48 hours. 
   Upon successful provisioning, it will automatically 
   assign to the PC."

I *think* he was saying that they need to get their 
payment for this from the account holder first, before 
they'll make a second IP address available, yes?  And 
I'm thinking the rep's use of the word "automatic" 
does *not* correspond to dhcp's  "AUTOMATIC mode" 
as it's described in 

[http://en.wikipedia.org/wiki/DHCP](http://en.wikipedia.org/wiki/DHCP)

In other words, the rep wasn't saying that the 
second IP address would be "provisioned" via 
"dhcp RESERVATION mode" (as opposed to the 
more usual "dhcp DYNAMIC mode" mentioned 
in the Wikipedia entry) , which would assign it 
to a router - or whatever is connected to the 
second modem - permanently, was he, as 
in "a static IP address"?  The appliance, whether 
PC or router, that's "downstream" from the 
second modem would still get it's IP address 
assigned in the same dhcp manner as the 
existing one that the landlord has in place, 
correct?

( BTW, fballem, a 6Mbps (download) connection would 
cost me $54 per month from Comcast here in the 
States, if I were to subscribe directly.  I can't answer 
your query re their bundled offers ( which are complicated 
by the "come on" pricing offered in the early months of 
service ); I don't watch televison, and I'm quite happy 
having only a mobile phone, so I've paid no attention 
to such offers. )

ON ETHICS & LEGALITY RE THIS SHARING SITUATION

My impression is that with respect to Comcast, at 
least, oldsoundguy aptly calls our attention to the 
final words of the sentence from their "Terms of 
Use" that OffAxis was kind-enough to find and 
quote:

  "You agree that the Services and the Comcast 
   Equipment will be used only by you and the 
   members of your immediate household living 
   with you at the same address and only for 
   personal, residential, non-commercial purposes, 
   UNLESS OTHERWISE  SPECIFICALLY AUTHORIZED 
   BY US IN WRITING."

( Emphasis mine, as per OffAxis. )

Well, a live chat session is writing, I'd say, wouldn't 
you all?  Yes, yes; I know - technically my landlord 
would have to receive this written authorization, but 
to say so would, I think, miss the point here.  

That point would be that twice now I've made inquiries 
of Comcast about sharing a connection, and each time 
the response I've received has been underwhelming, 
pretty much on par with the intensity of a yawn.  I 
can't really say they seem *eager* to grant exceptions 
to the "immediate household" and related limitations 
in the above, but Comcast representatives certainly 
don't respond with anything like the alarm that was 
expressed in a few posts here before I explained the 
particulars to the group. 

My impression - and it's just an impression - based 
on the two times I've asked about this is that the 
company would ideally like to discourage sharing 
to maximize revenue, and thus has the restrictive 
language in the Terms of Use, but as long as you're 
not exceeding five simultaneous connections or using 
inordinate amounts of bandwidth, they're willing to 
grant written exceptions on the basis of pretty much 
any plausible justification for sharing.  "Business users 
share, home users share: Don't worry, be happy," might 
fairly characterize the reaction I've received to my 
inquiries.  ( If you haven't already, please read the 
live-chat transcript, at least, before you fire off a 
response to that characterization. )

Or perhaps Comcast thinks it would be too complicated 
to spell out in their Terms of Use all the circumstances 
in which sharing is allowed and all in which it's not, 
and they prefer to reserve the right to decide on a case 
by case basis by granting (or denying) exceptions.  When 
you start to examine possible cases, it really does  
begin to look like good fodder for a law-school  
case, or perhaps its own Wikipedia page.  

( A point of order might be of use here.  Certainly 
anyone has the right to continue posting about  
ethics & legality issues, if they like; I admit those 
issues are interesting. But please read the entire 
thread before you post advice on those topics [I]as 
they apply to the specific case I've documented 
at length in this thread.[/I]  It might also be helpful 
if you'd consider using the Comcast live-chat 
contact info that appears below, yourself, to 
research any questions you might have with 
Comcast directly, before posting.  One of the 
most fruitful exchanges of the thread so far, in 
my opinion, resulted from such; i.e. from "going 
to the source" rather than just stating beliefs; 
I refer to OffAxis' post that quoted from 
Comcast's Terms of Use. )

- - -

Chat Session with Comcast Rep 

(  This Comment by freshinodes, it's not part of chat session:

   Live chat support is accessible to anyone, not just current 
   Comcast customers, via this URL: 

   [http://help.comcast.net/content/faq/Six-Ways-to-Get-Help](http://help.comcast.net/content/faq/Six-Ways-to-Get-Help)

   Selecting the "Live Chat" option results in a screen that asks 
   for too much personal information, in my opinion - I get 
   enough ads from Comcast already, courtesy of the 
   U.S. Postal Service - so I chose to enter my name as "I just 
   want to ask a question", and likewise entered an obviously 
   impossible street address, e-mail address, etc.  I was very
   pleasantly surprised to find that their system allows one 
   to decline to provide such information in this way, and still
   connects one with a live-chat representative. 

   Also, I've edited the following to concatenate lines into
   paragraphs, and have preserved the analyst's anonymity 
   by replacing his user ID with "Comcaster" since he had 
   no expectation of being quoted in a forum.  I've also cut 
   some wholly-irrelevant passages to try to shorten the 
   thing a little.  But no words besides the analyst's user ID 
   and the one I entered for myself have been altered, and no          

meanings have been changed.  ) 

analyst COMCASTER has entered room
user FRESH:   has entered room

COMCASTER ( 06:48:26 )

Hello! Good morning! How may I assist you? 


FRESH:   ( 03:48:51 )

Hi, thanks. Wanted to ask about whether your 
Terms of Service allow a connection to be shared 
in a particular circumstance.

FRESH:   ( 03:50:41 )

I rent a "mother-in-law apartment" from my landlord 
who lives in the main house.  He has offerred to let me 
access the web through his Comcast connection.  
Just want to make sure that's okay with y'all. 
My place is a separate, freestanding structure, but is ... 


COMCASTER ( 06:51:43 )

Okay, thank you for the detailed information.  


COMCASTER ( 06:52:38 )

The internet service would still be under the account 
holder's name. Now with regard  to billing, we cannot 
split the bill or identify how much you consumed. It 
is now up to you on how to share the bill. 


FRESH:   ( 03:53:22 )

... legally the exact, same address as his. He did put 
different numbers on my structure, but they're not 
registered with the city or county at all; only his 
house numbers are, and we're on the same property/ 
lot, rather than two separate ones.


FRESH:   ( 03:53:33 )

Okay, got that re billing.


FRESH:   ( 03:54:05 )

But no ethical/legal/contractual violation, based on  
what I've said so far?

COMCASTER ( 06:54:39 )

Yes, there is none. All responsibility or liability is still 
under the account holder's name. 


FRESH:   ( 03:55:15 )

Okay; that's helpful info - thanks.  Did have a 
technical question, though, okay?  He's paying 
for a "2-5 simultaneous connections" arrangement. 
He and his son are the only current users. Is it okay 
with y'all, given what I've described, if we just plug 
a CAT-5 cable into his router, to get my computer 
connected?

COMCASTER ( 06:58:26 )

Yes, you are correct. That does not matter. 

FRESH:   ( 03:58:58 )

Okay.  Also, I was considering the possibility 
of our paying an additional amount for a 
second IP address.  I've been told that doing 
so might (?) afford an added "layer" of isolation 
for me re whatever the son might be up to on 
the web.  

COMCASTER ( 07:00:32 )

If you wish to add an additional IP address, you can. $5.00

COMCASTER ( 07:02:43 )

You do not have to worry on that. You can install McAfee 
security for free if you are using Comcast internet 
connection. 

FRESH:   ( 04:04:07 )

I didn't know that about McAfee; nice.  But I'll be using Linux 
most of the time, although I know you don't support that, 
and that I'd be on my own re tech help. I have no problem 
with that at all.

COMCASTER ( 07:06:20 )

I see. That is also good to know. 

COMCASTER ( 07:09:10 )

For answers to frequently asked questions 
and updates on new features, please visit 
[www.comcast.com](www.comcast.com) and go to search.


FRESH:   ( 04:10:00 )

Oh, um ... taking too long here?

COMCASTER ( 07:10:00 )

Do you have anymore questions for me to answer?


FRESH:   ( 04:10:53 )

Yes, re a second IP address, as to how that works.  


FRESH:   ( 04:11:16 )

Specifically, I was told that it would involve splitting the  
coaxial cable where it enters the property, but I wasn't  
sure that sounded right.  If that's too basic a question, 
I will go read up some more or, if need be, contact the 
local Comcast office about paying to have an installer 
come out and do what's needed.  

COMCASTER ( 07:13:43 )

Additional IP address will be provisioned first in the 
billing account for the account holder. The provisioning 
would take up to 24-48 hours. Upon successful 
provisioning, it will automatically assign to the PC.

COMCASTER ( 07:14:49 )

Do you have anymore questions for me to answer?


FRESH:   ( 04:15:29 )

Nah, need to read up a bit.  Don't know what provisioning 
means.  Thanks.


COMCASTER ( 07:15:55 )

Not a problem! You may visit comcast.com -FAQ for more 
information.

---

### Post by lukjad on 2008-09-14
I'm being attacked by text!!! ;)

---

