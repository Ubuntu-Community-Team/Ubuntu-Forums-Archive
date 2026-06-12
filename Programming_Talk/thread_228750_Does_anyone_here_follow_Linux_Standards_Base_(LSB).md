---
title: "Does anyone here follow Linux Standards Base (LSB) specifications?"
date: 2006-08-03
forum: Programming Talk
---

### Post by H.E. Pennypacker on 2006-08-03
I've recently found out about Linux Standards Base (and the Free Standards Group), and I love the idea, and what they're trying to spread.  For that reason, I want to make sure any applications I make satisfy their specifications.

I know lots of people ignore projects like LSB, but I truly believe in them.

Anyone here follow the LSB?  I've checked out their specifications, but I still need to know whether it's difficult to meet their needs.  Is it?

[http://www.freestandards.org/en/Main_Page](http://www.freestandards.org/en/Main_Page)

[http://www.freestandards.org/en/LSB](http://www.freestandards.org/en/LSB)

---

### Post by wmcbrine on 2006-08-04
My understanding of the LSB is that it's something distros would conform to, not individual apps. If so, one might better ask whether Ubuntu follows the LSB. (I don't know. It's not on the certified products page, though.)

---

### Post by 23meg on 2006-08-04
LSB is of interest to individual application developers as well. There's even a LDK (LSD Development Kit) which AFAIK is set of a LSB compatible development tools. 

From [http://www.freestandards.org/wordpress/?p=174](http://www.freestandards.org/wordpress/?p=174) :

> &#8220;LSB-compliance is very important for Ubuntu,&#8221; said Mark Shuttleworth, Ubuntu founder and chief developer. &#8220;We believe that Linux offers the world freedom of choice, freedom to innovate and freedom to localize. The Linux Standard Base is a crucial enabler of those freedoms, creating confidence in the standardization of the core platform while still preserving the ability of the platform to evolve and improve.&#8221;

---

### Post by H.E. Pennypacker on 2006-08-05
wmcbrine, it applies to everyone...distributions and developers.  

23meg, thanks for the quote.  I know that Ubuntu is not certified, and I was afraid it didn't care about LSB certification.

---

### Post by LordHunter317 on 2006-08-05
Ubuntu (and Debian) aren't LSB certified because by and large the standard is rather poor.  The parts they didn't put a lot of thought into (like packaging) are rather apparent.

---

### Post by neighborlee on 2006-08-08
> **LordHunter317 said:**
> Ubuntu (and Debian) aren't LSB certified because by and large the standard is rather poor.  The parts they didn't put a lot of thought into (like packaging) are rather apparent.

poor ?..so poor that suse, IBM, redhat, mandrake , linspire , mepis, xandros and other important players are integrating it  ?

surely you can do better than that ;) lol

LSB IS important because it sets 'standards' for distros, so that when a vendor  releases a binary they dont have to worry about getting bugged to death from users with stuff like: im missing lib this or that blah blah..a 'app.lsb' would run on any distro that intergrates LSB, and to suggest otherwise is just pure FUD or your not understanding the big picture..did you read the goal from the FSG ??,,here it is:

[http://www.freestandards.org/en/Benefits](http://www.freestandards.org/en/Benefits)

the LSB is one of the standards of the FSG and to suggest ubuntu can't rise to meet such standards is to suggest failure.

besides,,if you check the packages for ubuntu, you would see that lsb-core is there, so its not like ubuntu isn't taking it seriously on some level although its clear ubuntu/debian overall aren't in total compliance and they state that rather emphatically . ( to what degree im not sure as I haven't looked into that deeply but it does make the rather ambiguous statement which I find arrogant,- but hey )

I know mark said he feels that LSB is important , but the way this lsb-core info reads, I find all of this a mixed message for ubuntu.

cheers
g.leej (nl()

---

### Post by bieber on 2006-08-08
> **neighborlee said:**
> poor ?..so poor that suse, IBM, redhat, mandrake , linspire , mepis, xandros and other important players are integrating it  ?

Shall I provide you with a list of companies that use Windows?  Would that prove its obvious superiority?

---

### Post by KaeseEs on 2006-08-09
Neither Ubuntu nor any other Debian derivative will ever be *fully* LSB-compliant, unless certain [ poorly thought-out ] LSB mandates are changed.  Namely this one:

> Once your application is built using the LSB headers and linked with the LSB stub libraries and runtime loader, you can start packaging your application the LSB way. **The LSB suggests that you are to package your application in an RPM v3 formatted file.** In addition, you may not use triggers, nor depend on the execution order of pre-install or pre-uninstall scripts. You are also limited to using only commands specified by the LSB in those scripts and in your application, because other commands are not guaranteed to be present or to behave in expected ways. **The LSB does not specify the tool to install these RPM-packaged applications. You can use the rpm tool on RPM-based systems, and alien on Debian.** For more information on packaging, see the chapter called Packaging Your LSB Application. from [http://freestandards.org/docs/lsbbook/bin-comp.html#UNDER](http://freestandards.org/docs/lsbbook/bin-comp.html#UNDER)


Despite this, Ubuntu still strives to be as LSB-compliant as possible.  The standard does serve a purpose, and deviations therefrom are minimized by most major distros, as such deviations are a pain to desktop users and a bane to the enterprise.

---

### Post by neighborlee on 2006-08-17
> **KaeseEs said:**
> Neither Ubuntu nor any other Debian derivative will ever be *fully* LSB-compliant, unless certain [ poorly thought-out ] LSB mandates are changed.  Namely this one:

 from [http://freestandards.org/docs/lsbbook/bin-comp.html#UNDER](http://freestandards.org/docs/lsbbook/bin-comp.html#UNDER)


Despite this, Ubuntu still strives to be as LSB-compliant as possible.  The standard does serve a purpose, and deviations therefrom are minimized by most major distros, as such deviations are a pain to desktop users and a bane to the enterprise.

fully compliant maybe not , if indeed alien can't rise to the occaSion, and if not I'd like to hear reasons why not from an authority on the topic.  If this is so then how is xandros, mepis and linspire handling these things , as even xandros is first distro faik, to use desktop standards  in version 4 ?

I am  just wondering what degree of non compliance ubuntu represents based on their opening statement on the lsb package page, and of course why,- and only cause i'd like to see linux succede and ubuntu has a good a shot as anyone with LSB behind it IMO.  I use linux and want to see as strong leader emerge as then we just might get good support from vendors finally ( all vendors not just nvidia/ati/blah ). I know some dont 'care' but I am sure susie homemamker does ;) ( and face it ubuntu IS targeting that audience )

cheers
g.leej(nl)

---

