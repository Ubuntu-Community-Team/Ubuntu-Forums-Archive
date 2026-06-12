---
title: "Ubuntu Philosophy and Multimedia codecs"
date: 2009-06-22
forum: Recurring Discussions
---

### Post by Andy06 on 2009-06-22
I've been reading and looking around the internet at various links but everywhere it just says that due to licensing/patent issues, multimedia codecs are not included with the default Ubuntu install.

Which is fine but now raises 4 questions for me:

1. How is Linux Mint able to package drivers and codecs into its distribution? They don't charge users anything so I doubt they are paying for the license. How do they manage it? Are they doing something semi-legal?

2. When I manually install codecs through Ubuntu-restricted-extras or through the separate packages, am I doing something semi-legal or illegal? Coz neither Canonical nor I have paid anyone for the license and yet I now have the capability to play everything.

And if manually installing them myself is not illegal, why can't it be automated or pre loaded?

3. VLC player is free and Open source, it comes with the codecs however, it can play pretty much anything, how does it manage to legally distribute codecs or whatever it uses? Can it not be packaged as such into Ubuntu for out of the box functionality?

4. The NTFS-progs package isn't installed by default on a clean install, presumably due to the aforementioned licensing issues but yet it can be found on the LiveCD/LiveUSB. How does this work? Either they can or they can't use it legally. Why is it there on the Live CD but not there on a full install?

Thank you very much.

---

### Post by coffeecat on 2009-06-22
I'll let others answer the codec issue, but I can give you an answer for...

> **Andy06 said:**
> 4. The NTFS-progs package isn't installed by default on a clean install, presumably due to the aforementioned licensing issues but yet it can be found on the LiveCD/LiveUSB. How does this work? Either they can or they can't use it legally. Why is it there on the Live CD but not there on a full install?

The ntfsprogs package is a set of toolls needed for creating/resizing NTFS partitions and some other miscellaneous tasks on NTFS filesystems. It's not necessary for read-write of NTFS partitions - the drivers necessary for that come with a default install. The live CD includes ntfsprogs because many users will want to resize their Windows partition when doing an install, or even create a NTFS partition.

But only a minority of users will need the ntfsprogs tools on a hard drive install since they'll be able to read/write NTFS partitions. Those that need them can install them. I don't believe licensing comes into this at all since the ntfs-3g driver and the toolset were all done through reverse engineering.

---

### Post by Skripka on 2009-06-22
Ubuntu toes the Debian line regarding non-free software such as codecs.

Mainly, it appears to be out of fear of draconian US copyright/licensing law.  Which seems at best unfounded, as no Linux distribution that takes a pragmatic approach to codecs has YET gotten in legal hot water over it.

Ubuntu chooses to make it difficult.  Lots of distros such as Mint, or Arch (Those two come to my mind quickly, there are probably others) take the pragmatic approach-and nonfree codecs hitch an automatic lift as depends to their media players.  Ubuntu chooses to have green linux users have to come here and start 1000s of threads about how to get things working.

---

### Post by t0p on 2009-06-22
I may be wrong (and if I am, I'm sure someone will correct me) but this is my understanding of the non-Free codecs issue:

Ubuntu's stance concerning non-Free codecs is not a legalistic one, it is a moral one.  The proprietary codecs are not Free.  Ubuntu is founded on a belief that Freedom of software is important morally.  So they don't provide the codecs.  Of course, Ubuntu is not in the business of telling people what to do - this would be anti-Freedom - so we are free to install the non-Free software if we wish.  But Ubuntu wish we wouldn't.

Linux Mint is not founded on such strict moral codes, in common with many other distros.  So they think it's okay to include non-Free codecs with the default install.

---

### Post by Tibuda on 2009-06-22
> **Andy06 said:**
> 3. VLC player is free and Open source, it comes with the codecs however, it can play pretty much anything, how does it manage to legally distribute codecs or whatever it uses? Can it not be packaged as such into Ubuntu for out of the box functionality?
From the VLC FAQ:
[QUOTE="http://www.videolan.org/support/faq.html"]The use and distribution of the libdvdcss library is controversial in a few countries such as the United States because of a law called the DMCA (Digital Millennium Copyright Act). If you are unsure about the legality of using and distributing this library in your country, please consult your lawyer.

Beware: VLC media player binaries are distributed with the libdvdcss library included. [/QUOTE]

---

### Post by gn2 on 2009-06-22
1: Because they have two versions and allow users to choose which one they want, either the useful one with the useful bits installed or the other one.

2: Depends on what country you live in

3: Because VLC leaves it up to users to comply with any legal niceties which may apply to them

4: No idea, presumably because not everyone will need it.

---

### Post by castrojo on 2009-06-22
> **Skripka said:**
> Ubuntu chooses to make it difficult.  Lots of distros such as Mint, or Arch (Those two come to my mind quickly, there are probably others) take the pragmatic approach-and nonfree codecs hitch an automatic lift as depends to their media players.  Ubuntu chooses to have green linux users have to come here and start 1000s of threads about how to get things working.

It's not difficult, if something needs a codec it asks you, you press a button and it installs.

---

### Post by bryonak on 2009-06-22
> **Skripka said:**
> 
Mainly, it appears to be out of fear of draconian US copyright/licensing law.  Which seems at best unfounded, as no Linux distribution that takes a pragmatic approach to codecs has YET gotten in legal hot water over it.


No Linux distribution that has money you could sue for (i.e. a company behind it) and has a pragmatic approach to codecs has got in legal hot water over it.
Mint&Arch are simply too small to bother. Canonical would be noticed.

This of course mainly applies to the USA and Japan. But those places are enough to drive a company into bankruptcy in court.


To answer the OP's questions...

1. What Mint does is illegal in some countries, undecided in most (where I live for example) and legal in some others. Canonical wants to distribute legally everywhere.
There is a no-codecs version of Mint, where you can install them the same way as in Ubuntu.

2. This is the... ahem... beauty of those licenses. The decoders to the various formats are usually freely available at their sites for personal use, but not for commercial use.
So when a distro packages them by default, the company is distributing it "commercially" (nevermind that Ubuntu is free/Free).
But if they just offer the user a function to download them after installation, it's private/personal use, because the user decided to click on that button.

3. See danielrmt's response.

4. I'm not sure about the status of the ntfs-progs package. Aren't these reverse engineered? Then the one who created them may distribute them freely as long as the way he reverse engineered the system stays within the boundaries of law.
If the package is offered by the copyright holders of ntfs (Microsoft I guess), and they want us to comply with some license, then probably a similar private/commercial usage rules as mentioned above with the codecs would apply.



As many have noted, there is also a strong moral component Ubuntu inherited from Debian. These morals are the very reason why Debian is the most forked GNU/Linux distro there is, why they have over 1000 developers and why their and the descending communities (Ubuntu) are so attractive to many people.

---

### Post by kamitsukai on 2009-06-22
Regarding the Linux Mint codecs and drivers thing I have answerd a simmilar question on the official Mint forums

> [http://forum.linuxmint.com/viewtopic.php?f=6&t=25422](http://forum.linuxmint.com/viewtopic.php?f=6&t=25422)
Mine is the first reply but others also mention useful information =]

---

### Post by ghindo on 2009-06-22
> **Andy06 said:**
> 1. How is Linux Mint able to package drivers and codecs into its distribution? They don't charge users anything so I doubt they are paying for the license. How do they manage it? Are they doing something semi-legal?I *assume* that Mint and Arch are able to do what they do because they are community distributions and don't have a major foundation or corporation backing them like Ubuntu, Debian, Fedora, etc. does.

Also, bear in mind that the legality of such codecs and programs like VLC depend entirely on which country you live in.

---

### Post by SunnyRabbiera on 2009-06-22
> 1. How is Linux Mint able to package drivers and codecs into its distribution? They don't charge users anything so I doubt they are paying for the license. How do they manage it? Are they doing something semi-legal?

Yes Mint is doing something semi legal, they are not based in a country like the US they are in France.
France has very loose copyright laws compared to the US, also they are not backed by a major Microsoft competitor like Novell or Canonical so they slip under the radar.

> 2. When I manually install codecs through Ubuntu-restricted-extras or through the separate packages, am I doing something semi-legal or illegal? Coz neither Canonical nor I have paid anyone for the license and yet I now have the capability to play everything.

And if manually installing them myself is not illegal, why can't it be automated or pre loaded?

Installing codecs on Ubuntu is practically automated with the restricted extras package.
The installation of codecs is a very loose area depending on where you live.
Here in the US it is illegal to distribute the codecs by default but if you bought a windows computer then technically you are allowed to install the codecs on your own as you bought the windows license with your computer.
Rather it be by using something like Mint or not you are semi legally allowed to install the codecs on your own.

> 3. VLC player is free and Open source, it comes with the codecs however, it can play pretty much anything, how does it manage to legally distribute codecs or whatever it uses? Can it not be packaged as such into Ubuntu for out of the box functionality?

VLC warns its users of what is used with it, it gives the user the option to install the codecs or not.

> 4. The NTFS-progs package isn't installed by default on a clean install, presumably due to the aforementioned licensing issues but yet it can be found on the LiveCD/LiveUSB. How does this work? Either they can or they can't use it legally. Why is it there on the Live CD but not there on a full install?

This one I am not sure on

---

### Post by Andy06 on 2009-06-22
1.So folks in USA cannot legally use these codecs at all??
There is no way you can play mp3s and avi legally on Linux in the US?

2.When we manually install codecs on linux, are these the official ones that are free for personal use? Or are they reverse engineered ones made by the community? The package names seem to suggest they are unofficial.

3.What exactly are the patent holders demanding? Royalties? So hardware manufacturers pay these royalties when they pre-install linux?

4.What about Adobe flash, does adobe ask for royalties? Is the objection here moral and not monetary or legal?

Thank you all for the replies, I just wanted to know what the behind the scenes story was instead of just living with "some unknown licensing issue" view which many users aren't sure about.

---

### Post by SunnyRabbiera on 2009-06-22
> 1.So folks in USA cannot legally use these codecs at all??
There is no way you can play mp3s and avi legally on Linux in the US?

Technically no, thats because here in the US Microsoft and companies like them have the power to practically buy out the patent office and hold down those said patents.
But really the issue is moot anyway as technically if you bought a computer with Windows you already have the right to install codecs in linux too.
The legal grounding here is basically BS though, in other nations there are limitations like this too but its not as bad as the US and some other nations, but the US is one of the worst.
But if you are scared I say screw it, use your codecs and screw the patent system its corrupt anyhow.

> 2.When we manually install codecs on linux, are these the official ones that are free for personal use? Or are they reverse engineered ones made by the community? The package names seem to suggest they are unofficial.

They are mostly reverse engineered, but again I say screw it...
I stopped caring about that copyright crap ages ago.

> 3.What exactly are the patent holders demanding? Royalties? So hardware manufacturers pay these royalties when they pre-install linux?

They want a lot of money, and companies like Microsoft can give them money.
Linux is restricted from coming into the market because of this.
The more royalties the less chance linux has, its one of the things keeping linux from taking the market...
Corrupt copyright laws.

> 4.What about Adobe flash, does adobe ask for royalties? AFAIK, it does not, in fact it would be quite happy if it is distributed freely. So then there is only the moral and not monetary or legal objection on this front?

Yes adobe flash is free to use but not free to redistribute in some nations.
There are some nations where flash is downright illegal to use without paying for it as the EULA has a lot of crap jargon in it.

---

### Post by Andy06 on 2009-06-22
Mods,

Wouldn't this topic be better off in the Absolute beginner section where newbies could see it? Why did you shift it?:D

Thanks anyway

---

### Post by steveneddy on 2009-06-22
My take on this is that if you have ever bought a Windows OS or a PC with Windows pre-installed, you did your part and have "paid" your portion.

---

### Post by Bigtime_Scrub on 2009-06-22
Politics and philosophy aside, the codecs are not included and that's fine and all. The argument can be spun anyway you want, but if they really wanted to make it easy on new users then Ubuntu should distribute Ubuntu without the codecs for mp3, DVDs, etc so there would be no legal problems anywhere and simply add the ubuntu-restricted-extras option ON THE DESKTOP from a clean install. Clicking on the 'multimedia' icon gets it all installed, hooked up, and ready to go. No problems and no 1000's of posts in the forums about how CDs and DVDs do not play. Simple.

---

### Post by Therion on 2009-06-22
> **Bigtime_Scrub said:**
> Clicking on the 'multimedia' icon gets it all installed, hooked up, and ready to go. 
I've wondered this myself.  I also have to wonder if by doing as you suggest (One-Click Multimedia Support icon on the desktop) Canonical would be... "Tempting Fate"?  I don't know how able or willing they are to do that since going to court is expensive.  Even if you win.  And really, I could see how you could spin a case that by making the installation *"that easy"* it becomes, practically speaking, the same thing as providing the codecs preinstalled.  Yes, we could very well argue the merit of that statement, both pro and con and, in the final analysis, who would be right?  I'm guessing Canonical has thought along these very same lines and come up with the answer that finding out, to the tune of a battery of attorneys each wracking up $700 an hour in a long, drawn-out court case, is just not going to happen.  

Canonical, I am assuming, intends not to get burned by steering clear of the hot stove.

---

### Post by Bigtime_Scrub on 2009-06-22
> **Therion said:**
> I've wondered this myself.  I also have to wonder if by doing as you suggest (One-Click Multimedia Support icon on the desktop) Canonical would be... "Tempting Fate"?  I don't know how able or willing they are to do that since going to court is expensive.  Even if you win.  And really, I could see how you could spin a case that by making the installation *"that easy"* it becomes, practically speaking, the same thing as providing the codecs preinstalled.  Yes, we could very well argue the merit of that statement, both pro and con and, in the final analysis, who would be right?  I'm guessing Canonical has thought along these very same lines and come up with the answer that finding out, to the tune of a battery of attorneys each wracking up $700 an hour in a long, drawn-out court case, is just not going to happen.  

Canonical, I am assuming, intends not to get burned by steering clear of the hot stove.

Well that is the thing. Legally I don't see how it violates copyright laws. You are not actually installing them on your computer. When a user clicks the codec install icon a warning box can appear telling you that it may be illegal in your country. "Check applicable laws". The only problem is what you say, in that even if you win the case you lose because of all the money you would spend on defense. 


Just because I am curious....

Does Ubuntu comes with codec support preinstalled when you buy a laptop or netbook with Ubuntu already on it. Like if I bought a Dell with Ibex will it have mp3 and DvD playback out of the box? I'm just curious.

---

### Post by donkyhotay on 2009-06-22
> **Andy06 said:**
> 1.So folks in USA cannot legally use these codecs at all??
There is no way you can play mp3s and avi legally on Linux in the US?

2.When we manually install codecs on linux, are these the official ones that are free for personal use? Or are they reverse engineered ones made by the community? The package names seem to suggest they are unofficial.

3.What exactly are the patent holders demanding? Royalties? So hardware manufacturers pay these royalties when they pre-install linux?

4.What about Adobe flash, does adobe ask for royalties? Is the objection here moral and not monetary or legal?

Thank you all for the replies, I just wanted to know what the behind the scenes story was instead of just living with "some unknown licensing issue" view which many users aren't sure about.

> **Bigtime_Scrub said:**
> Well that is the thing. Legally I don't see how it violates copyright laws. You are not actually installing them on your computer. When a user clicks the codec install icon a warning box can appear telling you that it may be illegal in your country. "Check applicable laws". The only problem is what you say, in that even if you win the case you lose because of all the money you would spend on defense. 


Welcome to the USA, land of the [url=http://en.wikipedia.org/wiki/Digital_rights_management]
DRM[/url]'d and home of the [DMCA](http://en.wikipedia.org/wiki/Dmca).

---

### Post by Paqman on 2009-06-22
There is at least one perfectly legal way for US citizens to get multimedia codecs on their Ubuntu system:

[The Fluendo codec pack from the Ubuntu store]("http://shop.canonical.com/index.php?cPath=19&currency=USD")

---

### Post by Therion on 2009-06-22
> **Bigtime_Scrub said:**
> Just because I am curious....

Does Ubuntu comes with codec support preinstalled when you buy a laptop or netbook with Ubuntu already on it. Like if I bought a Dell with Ibex will it have mp3 and DvD playback out of the box? I'm just curious.
I don't see how they could (be included).  Dell doesn't own the rights, Microsoft does; so obviously Dell can't (legally) give away what isn't their property to begin with.  

If you want an answer straight from the horse's mouth, though, you could ask this question in the System76 Support forum.  System76 builds Ubuntu PC's and they would be no different than Dell in what they're legally able to provide, at least to my knowledge.

---

### Post by praveesh on 2009-06-23
> **Paqman said:**
> There is at least one perfectly legal way for US citizens to get multimedia codecs on their Ubuntu system:

[The Fluendo codec pack from the Ubuntu store]("http://shop.canonical.com/index.php?cPath=19&currency=USD")

Still there is a problem ;fluendo is only available for gstreamer . What about KUbuntu which uses phonon? . More over ,fluendo costs 39.95 USD . But at the same time , XP costs only 40 USD & if you are buying  an oem xp with a netbook  , it will cost only 17 USD

---

### Post by pbpersson on 2009-06-23
> **Therion said:**
> I don't see how they could (be included).  Dell doesn't own the rights, Microsoft does; so obviously Dell can't (legally) give away what isn't their property to begin with

I doubt that Microsoft invented any of these codecs.  I did research on MP3 for instance, and it is owned by Thomson Consumer Electronics in several countries including the United States.

---

### Post by sertse on 2009-06-23
The point we are having this argument aka "it is not 100% absolutely clear" already justifies why Ubuntu doesn't include codecs etc by default. Ubuntu as a proper organisation, need to be stay on the "safe side". Other more community-based distro can afford to chance it.

---

### Post by Closed_Port on 2009-06-23
> **Therion said:**
> I don't see how they could (be included).  Dell doesn't own the rights, Microsoft does; 

It doesn't. Neither for mp3 nor for DVD-playback.

> **Therion said:**
> 
so obviously Dell can't (legally) give away what isn't their property to begin with.  

They can of course legally buy a license. 

@praveesh: I'm certainly not a phonon expert, but isn't phonon a higher level abstraction layer that works with different backends, gstreamer being one of them?

---

### Post by master5o1 on 2009-06-23
Ubuntu leaves the codecs uninstalled simply to keep the forums alive and well maintained with new users.


If they had all the codecs working on a default install then we wouldn't see as many people here.  It's a decision that has made this forum community stornger and will continue to make our community stronger.


Thanks Ubuntu for leaving the codecs out I really love you :)

---

### Post by Andy06 on 2009-06-23
> Politics and philosophy aside, the codecs are not included and that's fine and all. The argument can be spun anyway you want, but if they really wanted to make it easy on new users then Ubuntu should distribute Ubuntu without the codecs for mp3, DVDs, etc so there would be no legal problems anywhere and simply add the ubuntu-restricted-extras option ON THE DESKTOP from a clean install. Clicking on the 'multimedia' icon gets it all installed, hooked up, and ready to go. No problems and no 1000's of posts in the forums about how CDs and DVDs do not play. Simple.

> I've wondered this myself. I also have to wonder if by doing as you suggest (One-Click Multimedia Support icon on the desktop) Canonical would be... "Tempting Fate"? I don't know how able or willing they are to do that since going to court is expensive. Even if you win. And really, I could see how you could spin a case that by making the installation "that easy" it becomes, practically speaking, the same thing as providing the codecs preinstalled. Yes, we could very well argue the merit of that statement, both pro and con and, in the final analysis, who would be right? I'm guessing Canonical has thought along these very same lines and come up with the answer that finding out, to the tune of a battery of attorneys each wracking up $700 an hour in a long, drawn-out court case, is just not going to happen. 

Canonical, I am assuming, intends not to get burned by steering clear of the hot stove.

The solution to this I think is a Start Up wizard desktop icons. (much like the install icon on LiveCDs). This would hold options not only for codecs but also to install flash, wireless drivers, graphics drivers, display mounted volumes on the desktop, options/links for popular apps such as Songbird, Thunderbird, VLC, Opera etc. This would make it less targeted towards codecs and everything just buried under a whole lot more. This would take care of 90% of newbie problems and be a big win for usability and out-of-the-box functionality. You can have Ubuntu give you warnings about how this is illegal in the following countries and how Ubuntu does not advise users in those countries use the wizard ;)

It would be like an official version of Automatix or the set up routine most ubuntu users go through anyway on every fresh install.

> Does Ubuntu comes with codec support preinstalled when you buy a laptop or netbook with Ubuntu already on it. Like if I bought a Dell with Ibex will it have mp3 and DvD playback out of the box? I'm just curious.

It may or may not. When it does, it is because OEMs can purchase those themselves and then load them on the comptuer. As it is you almost never get a clean install of any OS from an OEM. Earlier they would put their "customisations" on windows and now you can see them do the same with Linux. In fact with Netbook Remix, on the official site, Ubuntu recommends that OEMs install optional legally licensable software and codecs.

[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)


> Ubuntu leaves the codecs uninstalled simply to keep the forums alive and well maintained with new users.


If they had all the codecs working on a default install then we wouldn't see as many people here. It's a decision that has made this forum community stornger and will continue to make our community stronger.


Thanks Ubuntu for leaving the codecs out I really love you

Was that sarcasm :D? I can see how you would want a nice community but seriously, 1000 threads on the same issue does not make a stronger community, just a frustrated one. The forum would be better organised and of more help if the same threads did not repeat themselves again and again and again and again and again............

---

### Post by XubuRoxMySox on 2009-06-23
The **manufacturers** buy licensing from the software companies, which is how they can include codecs *from* those software companies in their pre-installed software.

The software cannot be legally *distributed* without a license, but they can certainly be *downloaded* for free from a licensed distributor.

---

### Post by Therion on 2009-06-23
> **Closed_Port said:**
> It doesn't. Neither for mp3 nor for DVD-playback.  They can of course legally buy a license. 
I realized the folly of my statement shortly after making it.  MS doesn't own the codecs in question and I knew that.  I was thinking/confusing codecs with proprietary formats and misspoke. 

Still, to some degree the point remains valid in that the codecs ARE owned and licensed, even if not by MS.

---

### Post by Andy06 on 2009-06-23
That's the funniest thing about the whole issue which also justifies the anger of so many people.

The ownership isn't clear! Different regions, different owners, even then there is dispute. Thomson is only for some countries and certain use cases. Check out the mp3 article on wikipedia to see what an absolute circus it is.

A bit like picking up sand from a desert and then having to pay for it. (To whom when there is no one in sight? No one is sure, but you must pay, go to the nearest town, find someone selling sand, and pay them.....absurd)

---

