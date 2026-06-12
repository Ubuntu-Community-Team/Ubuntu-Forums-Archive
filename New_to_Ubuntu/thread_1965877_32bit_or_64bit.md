---
title: "32bit or 64bit?"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Primus1 on 2012-04-26
Hi I am using 10.04 LTS and wish to get 12.04 LTS. I will do a clean install as other methods look too complicated.
The site recommends the 32bit version. I have a dual core processor (64bit?) 
Would it be better for me to choose the 64bit version rather than the 32bit?

Thanks

---

### Post by Curtis6767 on 2012-04-26
64bit

---

### Post by TBABill on 2012-04-26
Both versions work superbly. If your machine is capable, 64 bit is usually recommended now. I would recommend testing it to be sure there are no conflicts with hardware, but I have yet to buy a machine in the last few years that didn't run smoothly and without issue on 64 bit.

---

### Post by mikewhatever on 2012-04-26
You could upgrade directly from 10.04 to 12.04, it's very very simple. 

How much RAM do you have? If there's 2GB or less, I'd recommend the 32bit version.

---

### Post by Primus1 on 2012-04-26
@ mikewhatever - I saw no way to directly upgrade from 10.04 LTS to 12.04 LTS , it said do it in steps 10.04 to 10.10 etc.

I have 4gig of RAM

Pentium dual core CPU E5800 at 3.20 GHz

---

### Post by mikewhatever on 2012-04-26
That may have been before 12.04 got released, although I've upgraded and old computer directly from 10.04 to 12.04 about two weeks ago. Try running 'update-manager -d'.

With 4GB of RAM, you should definitely be running a 64bit release.

---

### Post by s1wood on 2012-04-26
I just tried that command and got a message saying 10.04 isn't supported any more, it didn't offer me an upgrade to 12.04 option.

Susan

---

### Post by mikewhatever on 2012-04-26
> **s1wood said:**
> I just tried that command and got a message saying 10.04 isn't supported any more, it didn't offer me an upgrade to 12.04 option.

Susan

Interesting. Are you sure you have 10.04 installed? Your signature has 9.10, and 10.10, which indeed are no longer supported.

---

### Post by ammofreak on 2012-04-26
Hi ):P
Briefly, if you have 3Gig of RAM or more, the extension PAE (physical address extension) will automatically be installed upon a new 32 bit install. This extension will enable one to use RAM up to 64 Gig I believe. However, the extension does slow the RAM access time. It is for this reason that many recommend using a 64 bit version. This being said, I have run into instances where the 64 bit platform does not render some 32 bit applications optimally. I find this is true with Oracle Java, Eclipse & some video rendering software. In my case, I switched back from a 64 bit to a 32 bit & quite frankly, I see no difference. On the other hand, if one were crunching algorithms, then obviously the 64 bit platform would be the choice. i hope this clarified your inquiry.:)

---

### Post by Primus1 on 2012-04-26
I have some dice so will give them a roll   :rolleyes:

---

### Post by Revolutionary101 on 2012-04-26
I would suggest getting the 64 bit version. Last year I was in a similar position as you are now. I had just bought a new computer and I was wondering if I should use the 64 bit version. I had hesitations because I had always used the 32 bit version of Ubuntu but once I made the switch I never looked back. The 64 bit version of Ubuntu works fine for me. I would suggest getting the 64 bit version for your case because like ammofreak said, above 3 GB of RAM with the 32 bit version you see slower performance. Plus since in the future you will see more and more programs developed for the 64 bit architecture with 32 bit being phased out, you may want to take that into consideration. Best of luck with your choice!

---

### Post by Primus1 on 2012-04-26
I remember years ago when 64 first came out they said without 64 apps coming out it wouldn't be useful, now I think it's the same, doesn't seem to have taken off. I don't know though because it is given as an option for Ubuntu so there must be a reason to it. Confusing.

---

### Post by jerome1232 on 2012-04-26
32 bit OS's run on a minority of machines these days. Most applications  (Linux side) are available as 64 bit applications. Windows seems to be slower at making the switch (as in many Windows applications are still 32 bit ) but the change over is happening.

I have used 64 bit for years now, the changes have been drastic since I first adopted it. As I see it, the only reason to use a 32 bit OS is if you are very severely pressed for ram (1 GB or less) or your cpu doesn't support it [64 bit].

---

### Post by wildmanne39 on 2012-04-26
Hi, I recommend 64 bit also I have used it for about five years.

I do recommend a clean install there are a lot of differences between 10.04 and 12.04 and a lot of the time upgrades go badly concerning upgrading to 11.04 and above partly because of the switch from gtk2 to gtk3.
Thanks

---

### Post by mikewhatever on 2012-04-26
> **Primus1 said:**
> I remember years ago when 64 first came out they said without 64 apps coming out it wouldn't be useful, now I think it's the same, doesn't seem to have taken off. I don't know though because it is given as an option for Ubuntu so there must be a reason to it. Confusing.

I think there is a pattern - people that struggle with the 32 vs 64bit issue suffer from having too much imagination. They imagine stuff that's not there, for example, that the 64bit version lacks applications, or is given as an option - all versions are optional, but something has to be selected by default. Someone else here, in another thread said that, since the 32bit was recommended, the 64bit was not recommended, though no one has ever said that. Where does this come from? :P

Here is the reason why the original intention to make 64bit the default choice has not been followed through:
[https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035088.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035088.html)

---

### Post by Primus1 on 2012-04-26
> **mikewhatever said:**
> I think there is a pattern - people that struggle with the 32 vs 64bit issue suffer from having too much imagination. They imagine stuff that's not there, for example, that the 64bit version lacks applications, or is given as an option - all versions are optional, but something has to be selected by default. Someone else here, in another thread said that, since the 32bit was recommended, the 64bit was not recommended, though no one has ever said that. Where does this come from? :P

Here is the reason why the original intention to make 64bit the default choice has not been followed through:
[https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035088.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035088.html)

Thanks I read it and note this:

* "in terms of performance, there are both pros and cons for switching to *>* amd64: memory consumption goes up, and therefore power consumption goes up *>* if the system is making more use of swap, but on the other side, most *>* CPU-bound operations will be faster on amd64.  So there is no clear *>* performance argument for preferring one over the other"*

---

### Post by mikewhatever on 2012-04-26
Quite true, but that is mostly relevant for systems with 1 or 2GB of RAM. With 4GB of RAM, your system will likely never need to swap.

---

### Post by cmcanulty on 2012-04-26
I am having similar problem. I have 10 laptops to upgrade at a library and I got one of 10 to show me the upgrade option. The others wouldn't upgrade from update manager or run box or a USB and they are all identical machines.

---

### Post by mikewhatever on 2012-04-26
It appears, a somewhat similar issue is mentioned in the Release Notes:

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Upgrades](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#PrecisePangolin.2BAC8-ReleaseNotes.2BAC8-CommonInfrastructure-1.Upgrades)

> Upgrades from Ubuntu 10.04 LTS to 12.04 LTS do not work using the alternate CD or the server CD as a package repository. It is recommended that users running Ubuntu 10.04 LTS wait for the 12.04.1 LTS point release, scheduled for July, before upgrading. (988941) 

Edit: Just tested the 'update-manager -d' command, and the update manager launched offering to upgrade to 12.04. Perhaps not all mirrors are fully updated yet. Wait a day or two, then try again.

---

### Post by Primus1 on 2012-04-27
Ok, I'll wait while 12.04.1, thanks all.

---

### Post by anejo on 2012-04-27
I've noted that this topic comes up quite often... so let me repeat...

When I got my first 4GB RAM machine... I wanted to see what Linux Mint--back those day--was gonna do. I've never looked back. I've been using  64-bit Windows and Linux for about four years now and the experience  just keeps getting better and better. This laptop that I'm currently  writing on runs 12.04 on 8G... I wouldn't want it any other way!

---

### Post by Primus1 on 2012-04-27
Experiences differ, Ammofreak in this thread for instance.

Also:

*"in terms of performance, there are both pros and cons for switching to *>* amd64: memory consumption goes up, and therefore power consumption goes up *>* if the system is making more use of swap, but on the other side, most *>* CPU-bound operations will be faster on amd64.  So there is no clear *>[I] performance argument for preferring one over the other"

[/I]I guess that's why this topic keeps coming up[I]. 
[/I]

---

