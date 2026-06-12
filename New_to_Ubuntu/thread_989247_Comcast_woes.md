---
title: "Comcast woes"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by LoudShirts on 2008-11-21
Thanks in advance for any assistance.  

Here's the nutshell:

Running Hardy Heron 8.04 on a older Dell.  Installed due to XP install crapping out, and I really like it.  Got up to speed fast with some great updates and tweaks, and everything's been chugging along smoothly for a few months, now.  

That is, until today.  

Due to an unfortunate and temporary drought of necessary funding, my Comcast cable internet connection was "suspended" for about a week.  Today being payday, I called and took care of it.  My wife has the day off, and I called her to let her know all should be kosher again.  But she fires up the box, and gets the "your OS is not supported" B.S. in Firefox.  

Now, prior to the service suspension, Comcast and Hardy played nice with absolutely zero issue.  But now they're telling me I need to abandon my nice new OS and pony up for the crap-fest that is Vista?  I refuse to accept this.  

Focused Googling has revealed two things: One, that this is not an unheard-of problem.  Two, that any solutions I've read thus far kind of don't make a lot of sense to me.  I'm still a relative n00b, so I'm hoping someone can break this down in some pretty simple "beginner talk" lay-speak for me in order that I correct the problem.  I'm sure there's a solution, but I don't know what it is, and can't seem to figure it out on my own.  

Other possibly-important data:

I'm connected through a router, not sure of the brand or model number.  I COULD theoretically take it out of the chain for the time being if it might possibly help. Because while there are three other PC's in the house (two desktops and a notebook), all three are XP machines that one by one all decided to start refusing to connect to the internet for whatever reason...Hence the Hardy install in the first place.  So, while I have seen one solution that says establishing an IP address with a Windows box first and THEN connecting the Ubuntu machine sometimes helps, I don't really have the option of doing so at the moment.  

Are there some Terminal commands I can punch up?  Is there a fix, or workaround?  I mean, everything was just jake until the service suspension, so I know the problem is not that Comcast simply won't work with Linux...so there must be some band-aid I can slap on this annoying, festering blister.  

Please help!  The thought of facing another weekend without internet is a bleak one indeed!

---

### Post by beno1990 on 2008-11-21
Personally, I'd just call Comcast and complain. It isn't an ISP's place to say what operating systems its users should use. If they still refuse to budge, change ISP.

That's what I'd do personally, and cheating the system just isn't worth it for an ISP who wants to control how you use your computer.

---

### Post by lifestream on 2008-11-21
Clear your firefox cookies.
Install [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)
Restart Firefox.
Go to Tools->User Agent, switch to IE7/Vista, or similar.
Go to the comcast page.
Tadah!

Final step: Go punch Comcast CEO. Do us all a favor, and go punch Verizon, Time Warner Cable, AT&T CEOs too.

And all those websites that "don't" support Ubuntu, but do when you fool them.





Beno that's all nice and sweet, but no USA ISP supports Linux. It is too dificult for them, they just don't understand it. They're too lazy to do any work that would make them realize they were wrong, even if it gains them more clients.

I was with Time Warner Cable for 10 months, and every single week, I would call:
"Please, can you tell me what is my router's IP adress so that I can go secure my wireless?"
Before you ask, no it was not my gateway, and it is some obscure router provided by TWC. The router's website did not have the correct IP.

I spent 1 day a week asking them for that damn IP.
They would start with:
Rep: "Okay, ermm, go to your Start menu...."
Me:  "Sir, I don't have a Start menu"
Rep: "Oh... mmmm... I'm going to have to pass you to higher tech"
Me:  "There is no need, you can just ask them what the router IP is, go ahead and put me on hold"
Rep: "..."
*beautiful song plays*
Rep-high-Tech: "Hello. Ok, go to your start menu"






**...**

---

### Post by fluxlizard on 2008-11-21
I have comcast as well.

I think it's just a registration thingie that happens when you access it the first time seems to require you to start in explorer. After that first few seconds in explorer, you should be able to use linux or anything else.

Borrow a friend's laptop, hook up directly to your cable modem, login, shutdown the laptop, disconnect and hook your linux box up like normal and move on with life.

Comcast is trying to get legislation that would make it legal for certain sites who pay them money to load up as usual, and the rest to load up slowly or not at all when accessed through comcast. They are also starting a policy limiting bandwidth that will probably become more and more restrictive over time, reducing what you can get for your money. I think they are dangerous (in that other ISPs are likely to follow their example) and bad, but other than dialup (too slow) or satelite (too expensive) they are my only option for an ISP in my area (out in the country- too far out for dsl). If you have other options, I'd consider telling them off about linux and switching to another ISP.

---

### Post by LoudShirts on 2008-11-21
> **lifestream said:**
> Clear your firefox cookies.
Install [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)
Restart Firefox.
Go to Tools->User Agent, switch to IE7/Vista, or similar.
Go to the comcast page.
Tadah!

This is, quite possibly, a REALLY stupid question, and forgive me if it is...But if I clear The Firefox cookies, will that "loosen" things to the point that I'll able to get to the extensions page in order to install the agent switcher?   

> Final step: Go punch Comcast CEO. Do us all a favor, and go punch Verizon, Time Warner Cable, AT&T CEOs too.

Boy, would I love to. :) 

[quote=beno1990]Personally, I'd just call Comcast and complain. It isn't an ISP's place to say what operating systems its users should use. [/quote]

Wholeheartedly agreed; they've zero right to dictate my decision of OS.  Especially when it was working just peachy a week ago.  And when all's said and done, I certainly intend to call them and render a tongue-lashing the likes of which they've rarely experienced.  I just want to wait to do so until after the issue's put to bed, so the call will be for the sole purpose of complaining.  I've just seen from other posts here and elsewhere that calling Comcast for actual help with this problem has traditionally been about as productive as trying to teach boolean algebra to goldfish, only slightly more frustrating.  Based on the reports of others who have called Comcast with a big "WTF?", their CSR's tend to fall back on boilerplate "help" speak along the lines of, "we apologize for the inconvenience, but you can officially suck it unless you want to line Steve Ballmer's moist pockets" the second you even THINK the word "Linux."  

Even so, rest assured...They'll be getting an earful.  Especially if I print off all of the sage advice I get in this thread, go home and try it, and I still can't achieve the elusive joy for whatever reason.

---

### Post by tjwoosta on 2008-11-21
verizon said i cant use linux

i complained but they refused to budge


so when i got it hooked up i booted into windows to set everyhting up

after setup i deleted windows and installed ubuntu

everything has been working great so far, but luckily i have never had to reconnect my service

---

### Post by lifestream on 2008-11-21
@fluxlizard,
I guess we could threathen to switch to another IP, but really, they all want to do what you've posted about. More people should know about Internet Neutrality.

But it doesn't really matter if you switch ISP, they are all oblivious to the fact that they need to stop lying about not supporting Linux. 


I wondered if it is because Linux doesn't have enough users?
Ironically they support Mac OS, yet it too does not have many users.

---

### Post by lifestream on 2008-11-21
> **LoudShirts said:**
> This is, quite possibly, a REALLY stupid question, and forgive me if it is...But if I clear The Firefox cookies, will that "loosen" things to the point that I'll able to get to the extensions page in order to install the agent switcher?   

The agent switcher should isntall regardless.
Are you getting problems when you go to the firefox add-on page?

The only reason I told you to clear the cookies, is because the comcast page might have given you a cookie that will tell them: "haha! This cookie says they run Linux... but Firefox is telling me now that it's vista? "

I'm not sure that would happen, but it could. You can try installing the add-on, then restarting, then selecting IE7/Vista from Tools->Agent Switcher.

Then if that doesn't work, try clearning your cookies.

---

### Post by LoudShirts on 2008-11-21
> **lifestream said:**
> The agent switcher should isntall regardless.
Are you getting problems when you go to the firefox add-on page?

This sucks, actually, but I can't tell you.  I'm at work, and the problem is at home.  I could call my wife and have her relay some trial-and-error info, but she had to go to class.  And I won't be able to get a look at it for myself until I get home...Where, if that DOESN'T work, I won't be able to come back in here and let you know as much.  Grrr. 

> The only reason I told you to clear the cookies, is because the comcast page might have given you a cookie that will tell them: "haha! This cookie says they run Linux... but Firefox is telling me now that it's vista?"

Yeah, that's entirely possible.  I hadn't thought of that.  

> I'm not sure that would happen, but it could. You can try installing the add-on, then restarting, then selecting IE7/Vista from Tools->Agent Switcher.

I'll certainly give it a shot, provided I'm able to d/l the extension.

---

### Post by lifestream on 2008-11-21
OH WAIT.

So Comcast is blocking EVERY SINGLE PAGE? Not just a comcast page regarding activation? They redirect you to their comcast page when you try to go to google.com?
WHOA! If that's the case, I think Comcast is asking for a lawsuit.

Sorry I misunderstood the situation.

I've been through this before, but with TWC, not Comcast. All they asked was "What is your MAC adress on your modem/router?" 
(I don't remember which because the modem/router was all one piece. Cheap c***)


If that's the case, maybe it would help to switch (even if temporarely) to another DNS, so as to bypass Comcast's.
Here are some, at the bottom of this page:
208.67.222.222
208.67.220.220 
[http://www.opendns.com/select_network_type.php?p=start](http://www.opendns.com/select_network_type.php?p=start)

Now if someone can tell him how to setup DNS on Ubuntu, that would be grand. I know Network Manager does not like DNS, but he can't install wicd if Comcast is being an ***. Could he just set those on his router? 

BTW I use those DNS listed because I DETEST Verizon's so-called "Friendly Search Page that it likes to take me to when I made a 'typo' on my browser"

Using that DNS bypasses it.






EDIT: WHOA! Check this out! [http://izanbardprince.wordpress.com/2008/06/20/comcast-says-well-get-you-mister-linux-user-and-your-fat-fluffy-cat-too/](http://izanbardprince.wordpress.com/2008/06/20/comcast-says-well-get-you-mister-linux-user-and-your-fat-fluffy-cat-too/)

So yes, I see that Comcast is blocking every page. They are REALLY asking for a lawsuit. What kinda bull**** is that?! My Linux can open websites just fine! The point of the Internet is be able to access information anywhere, from any sort of device.

BTW you might want to buy your own router, so you don't have to use theirs. >_<

---

### Post by gpsmikey on 2008-11-21
I have not been down this path, but I do have Comcast here in the Seattle area (Washington) and use Linux all the time - most of my machines are XP Pro, but several Ubuntu machines as well with no issues at all.  Couple of things to try -- first, cycle power on both the cable modem and the router to clear anything strange in the router (it may have a goofy address or DNS entry they handed you when they shut the service off).  
If that does not clear it, try going to Google using the IP 72.14.207.99 (this bypasses the DNS to see if they are handing you a bad IP for all DNS resolution attempts).  You can also try to Ping Google.com from a console window for example and see if that resolves to a reasonable address or takes you to the "Comcast you have been bad" page.

mikey

---

### Post by richg on 2008-11-21
That is a new one to me. About three years ago I set up a wireless router at my brother's place where he has Comcast. I set up the router using his XP PC. When I go over to his house, I use two different wireless laptops. One with Linspire 5.1.427 and the other for a Xandros Linus EEE PC. No issues. I do not use Comcast email.
His Comcast email account was set up using his XP PC.

At home with Charter, I know my online bank keeps telling me to use other OSs but Linux works fine for me.

Rich

---

### Post by Kain000 on 2008-11-21
Im pretty sure that comcast lost that in court in the last month or so, where the ruling is that they have to treat all traffic equaly and that a tiered internet is not legal.



I whole heartely agree that comcast sucks hard.

Their new internet cap of 250gb per month is too large to hit for most users to be certain....... (although with the advent of streaming high def movies on your computer, and now even xbox360 some may hit that limit and be cut off for a year)

While this limit is generous, how long until bandwith demands are stressed with newer tech?     will the limit go up?

I espacially dislike the fact that not only is their a limit, but no ammount of money can get you a larger limit!!!        

What really makes me mad is that all this limit and cap talk is because more and more people are using the internet each day......


and comcast (and other isps) have been biding their time untll the very last second to upgrade their infrastructure to better fiber.

---

### Post by oldsoundguy on 2008-11-21
I have Comcast .. 
I have seven computers
Two are Windows machines
3 are 8.10 machines
1 is a Mythbunu machine
1 is a Linux Mint.

The secret is that they are all behind a ROUTER.

And a lot of the above ranting and raving is just total BS!

I have talked to many a tech, and some of them are using Linux of one kind or another on their OWN machines.  Many UNDERSTAND and know the system.

They might as well block Apple users if the above is really TRUE as there are now about as many Linux users as Apple users! (with the advent of the new mini PC's (web books), which almost all run Linux (mostly Ubuntu)

Oh, and in this area in mid December Comcast is bumping up the basic speed from it's present 6mbp to 15mbps at no change in rates. (gamers can buy an extra 5mbps for a bit more .. same amount as they are charged now for 8mbps over the standard 6mbps.  

AND, they kept their word and are no longer blocking torrent uploading.

---

### Post by gpsmikey on 2008-11-21
Even if they did take our newsgroups away with nothing other than "too bad so sorry".  That was part of the fee I was paying - and they have absolutely no intention of dropping our rates because they cut off the service they sold us.  A lot of the smaller newsgroups like rec.metalworking don't really have support forums out there (unlike Linux etc).  

From my experience, it's always good to be behind a router - amazing how much cr*p those things stop that are busy probing around out there looking for ways to get into any network they can.  My few experiences with Comcast customer (non)support have been somewhat less than rewarding.  They don't hesitate to send people door to door to get you to buy the latest $$$ package, but trying to get support is like talking to a tree stump in many cases.

mikey

---

### Post by silverglade00 on 2008-11-21
Funny part is... many routers run Linux! Mine does. So how the heck do they not support Linux?

---

### Post by gpsmikey on 2008-11-21
Very true on the Linux on the routers -- I actually have Tomato installed on my Linksys instead of the default firmware and it works fine (also reports how much bandwidth we have been using).  I have not seen any issues here with the Linux machines talking to anywhere although I do go through the router.  I have the Surfboard 5100 cable modem that has worked fine for several years now.  Once or twice a year, something gets confused and I have to cycle the power on them, but that is very unusual.

mikey

---

### Post by LoudShirts on 2008-11-21
> **oldsoundguy said:**
> The secret is that they are all behind a ROUTER.

I'm actually using a router, too...And still, "Your OS is not supported blah blah installation wizard blah blah."  Stinky.

I'm heading home in a few.  Wish me luck trying to beat Comcast, and possibly their tech support CSR's, into submission.  Wish I had a way to record my phone calls.  I have a feeling it's going to be good, if not efficient.

---

### Post by ljoslin on 2008-11-21
This happens to me A LOT, I just call comcrap and have them do the registration on their end!  If you get one that says they can't do it, hang up and try the next person, it seems 1/3 is actually competent!  

-=ljoslin=-

---

### Post by MrWES on 2008-11-21
> **ljoslin said:**
> This happens to me A LOT, I just call comcrap and have them do the registration on their end!  If you get one that says they can't do it, hang up and try the next person, it seems 1/3 is actually competent!  

-=ljoslin=-


I don't think this is a case of Comcast banning Linux OS's, but that the registration web site only supports IE -- I've come across a couple of sites like that. ADP Total source is like that. Either use a windows machine, or install virtualbox and install XP to handle those few sites with issues. I've found the agent switcher to not always work.

Bill

---

### Post by gpsmikey on 2008-11-21
In our area, I just called them when I got a new modem (returned the leased one) and had them activate it from their end.  No software was installed on any of my systems - they just had me read them a couple of numbers if I remember correctly and it was done ( I got tired of the $5/month lease on their modem ).  Didn't seem to be a big deal at all with them and when I have switched routers (so the MAC address on the WAN side of the router changes), all I have had to do is reboot the modem and router and they talk.  No MAC cloning was needed.

mikey

---

### Post by oldsoundguy on 2008-11-21
I have the RCA VoIP/Internet modem and it still is only 5 bucks a month for the lease (they have had to replace it once as the initial one had issues on the phone lines) .. for a savings of nearly 40 bucks a month vs my QWASTED land line services, I will gladly pay the lease!

I had my router take a shower (leak in the enclosed back porch roof in the apartment and router is there! Since fixed.)  I replaced the unit with another matching one (D-Link 624), did NOTHING to set it up and didn't even bother to call Comcast .. that was a year+ ago.

They have been out here to fix wiring twice during that time and no charge.  

But some people want the service for free and will bi**h about any body that has the GALL to charge them money for something.  And find even the smallest thing to complain about.

Have a friend in Florida on Road Runner and leasing their home network wireless package (she is elderly and has no CLUE about how things go together and how they work .. she just wants it to work!) .. with her and RR, it does NOT work.  They make about a once a week visit to fix "something" that has died!  This last time out they managed to screw up her SCANNER of all things .. now what the he** are they doing messing with the scanner other than the fact it is plugged into the USB? (and her wireless transmitters are USB) 

So NOBODY gives perfect service .. and in areas where the major providers have come in and bought out a mom and pop operation that was falling apart in the first place .. it takes time and MONEY to do the upgrades!

---

### Post by jharadie on 2009-01-05
I just now ran across this thread and can't resist the chance to add my two cents.  I live in Bellingham, WA, less than 100 miles away from the main m$ campus.  I also know somebody who used to work for Comcast in the "Answer the phone and read from a script" dept (aka Tech Support).  He says that while he has no proof, he strongly believes that Comcast has a deal with M$, all their "support" scripts are M$ and they are told to discourage, even lie to people not using M$.  He also said that last year when Vista came out people in his dept were told to "strongly encourage" customers to upgrade.  BTW, this call center is in Everett, WA, even closer to the M$ campus.

I don't know how much truth there is to all this, but it sure sounds like it.

My friend says the best thing to do is get a router and do setup through it, so Comcast doesn't see the Linux.

On the funny side, a couple months ago a neighbor switched to Comcast, the installer showed up with a modem and PCI card.  The installer swore up and down that drivers were needed, but when I put in the PCI card, fired up 7.10 and everything worked immediately, he said that couldn't be right.  No amount of demonstrating to him that everything was working just fine could change his mind.  I gave him a LiveCD and asked him if he had the courage to try it.  Never heard back. :)

---

### Post by Captain_tux on 2009-01-05
To the OP... the page that does open up in your web browser, is it a Wall Garden page?

---

