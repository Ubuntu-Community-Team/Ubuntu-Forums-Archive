---
title: "finding/installing basic repositories? programs?"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by Sonoran Desert Rat on 2012-09-13
Hello, I've been searching all over for repositories. I found the firefox sticky thread but I'm thinking those are for people interested in the programming going on? Where can I get a basic education on them? Several questions so you know what I'm looking for:

Are the beta ones the stable versions? 

How do you know if a program is tried and true or still buggy and being tested? For instance, I want to download firefox but since I am new would like to avoid anything [I]to[I] new. 

Is there a "go-to" repository for these or do different programs have different repositories? 

I keep reading about stable or safe Ubuntu repositories. How do I get those?

Is there an easy place to go to get the command names for installation and upgrade of these programs? For instance I now know firefox is under mozilla and this discovery makes me think I need a mozilla repository and not a firefox one?

Do I keep them "loaded" when not in use? 

Thanks ahead! :)

---

### Post by Lars Noodén on 2012-09-13
I'd start with this document:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Stable means unchanging, so you have a predictable set of packages and versions.  It has more to do with the constellation of packages rather than the bugginess.

The repositories you have for Precise are more or less stable.  If you want newer packages with new versions then dig in the backports repository. Otherwise it should just be security updates that you get.

Firefox and just about everything else will be in Ubuntu's repositories.  It's very seldom that you will have to go outside those.  Read up on the difference between main and universe, for example.  There will be some rare packages like Opera which you have to get from partner or third party repositories.

[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

apt-get and apt-cache are the two main text-based tools to add or remove packages.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

You mentioned programming.  What aspect?

---

### Post by Sonoran Desert Rat on 2012-09-13
Oh, the programming question was put in the wrong place. The education I was referring to was on repositories. :/ I also referred to people who get the newest unstable versions probably because they do programming (I assumed). While I would love to do programming eventually, I am sticking with understanding my new Linux OS first, at face value, so to speak. :) 

Thanks for those links, I'll get right on them!

---

### Post by Lars Noodén on 2012-09-13
OK.  The bleeding edge can usually be found in the PPA's

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

There's often programming going on with those. Though you don't have to be a programmer to help with testing, if you like living on  the edge or have a particular interest in a specific package.

---

### Post by snowpine on 2012-09-13
Ubuntu will always give you a stable and supported Firefox for the duration of support, there is no need to add additional repositories for Firefox.

A significant percentage of the support problems I see on these forums are related to users adding unsupported repositories to their software sources.

---

### Post by Sonoran Desert Rat on 2012-09-13
> **Lars Noodén said:**
> OK.  The bleeding edge can usually be found in the PPA's

[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

There's often programming going on with those. Though you don't have to be a programmer to help with testing, if you like living on  the edge or have a particular interest in a specific package.

LOL, I'm avoiding anything referred to as the "bleeding edge" for a while yet. :D 

I was thinking of doing that with Firefox or Open Office as I am familiar with those...on a WindowsXP OS. Eventually. ;)

p.s. I'm on a 30 gig hard drive at 32 bit. I'm going to avoid opera so far, I found Synaptic so that's a start.

---

### Post by Sonoran Desert Rat on 2012-09-13
> **snowpine said:**
> Ubuntu will always give you a stable and supported Firefox for the duration of support, there is no need to add additional repositories for Firefox.

A significant percentage of the support problems I see on these forums are related to users adding unsupported repositories to their software sources.

That's exactly what I'd like to avoid! Thank you. :)

---

