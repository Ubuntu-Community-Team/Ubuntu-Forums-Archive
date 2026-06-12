---
title: "Release Candidate VS Final Release"
date: 2010-04-20
forum: Recurring Discussions
---

### Post by KdotJ on 2010-04-20
Are there many differences between these two versions? I that on the wiki documentation it states that the RC should practically be the final release.
But I have only been using linux/ubuntu since November, so I am yet to be around for a new version release.

In the past with versions, are there many changes after the RC?

thanks

---

### Post by soro2005 on 2010-04-20
No feature changes, but expect a fair amount of bug fixes and updates. After all, the RC is for bug fixing. There will also be some changes in the first weeks and months after release. If you want to have it rock solid and without major downloads now and then, experience tells that you best wait a couple of weeks into the release cycle.

---

### Post by KdotJ on 2010-04-20
Thanks for the quick reply.
And thanks for the info, I have been running Lucid since Beta1 in a virtual machine. I'm very impatient for it to be released lol, I was going to wait for the final release before I install it to my hard drive, but then I thought about doing it once the RC is released.

I guess the trouble is that I don't know how well Lucid will work on my laptop and netbook for real as I've only been running it in a VM...

Maybe I'll re-think..

---

### Post by xebian on 2010-04-20
By the time you are done installing the final release there would be tons of updates.

---

### Post by soro2005 on 2010-04-20
> **KdotJ said:**
> 
I guess the trouble is that I don't know how well Lucid will work on my laptop and netbook for real as I've only been running it in a VM...

Maybe I'll re-think..

Why don't you trow in a Live CD and take it for a spin? Should give you a pretty good sense of what problems may come up in terms of your hardware. Also: If your computer works with Karmic, it should normally also work with Lucid. There may be regressions, though, but you should be able to learn about them here on the forum.

In any case, safest to wait into the final release. Upgrades can also go very very very rough.

---

### Post by P4man on 2010-04-20
Main difference? With the RC you still have hopes that the bugs that bite you and that you submitted during Alpha 1 will be fixed before it ships; with the final version you have precious little such hope and you wait for the next release cycle ;)

---

### Post by KdotJ on 2010-04-20
Thanks for the replies guys, I think I'll try it out with a live cd and then wait for the final. It's less than 10 days, I guess I can wait lol

---

### Post by 23meg on 2010-04-20
> **P4man said:**
> Main difference? With the RC you still have hopes that the bugs that bite you and that you submitted during Alpha 1 will be fixed before it ships; with the final version you have precious little such hope and you wait for the next release cycle ;)

Actually, almost the contrary is the case.

During [Final Freeze]("https://wiki.ubuntu.com/FinalFreeze"), even though the *number* of updates may look great compared to what you'd expect at this phase, the actual fixes will be limited to very high-impact bugs, will be restricted to the greatest extent possible in terms of invasiveness in order not to inadvertently break things that work at the final phase, and every upload will be very tightly scrutinized by the release team. So if the impact of your bug isn't very severe and a fix isn't available and well tested, the chances of a fix for it going through are pretty low.

However, once the release happens, we shift to the regular [stable release update policy]("https://wiki.ubuntu.com/StableReleaseUpdates") for updates, and many updates that weren't eligible for the FF criteria and/or were deemed too invasive will once again be eligible to be applied after the release. This is why you'll typically see many bugs for which a fix *is* available being marked as "Triaged" or "Fix Committed" shortly before or during FF the uploads for which will be withheld until after the release, and a flood of bug fixes that were too invasive to be applied during Final Freeze, but can go through the SRU process, will be available right after the release.

Of course, this is not to say that the bug you filed at the Alpha 1 phase is *necessarily* going to go through the SRU policy, which also has severe restrictions.

---

### Post by P4man on 2010-04-20
> **23meg said:**
> Actually, almost the contrary is the case.


You're right of course, but I do wonder if this is the right approach. I really think ubuntu is on a much too tight schedule, the time between alpha, beta and release is simply too short to do testing AND have bugs fixed. 

Many of the bugs I have reported or encountered during alpha and beta have not even been triaged or afaik, looked at, just confirmed by other users and thats it. For instance:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/559163](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/559163)
Not resuming after wake up, thats rather nasty, and its not limited to my particular notebook, there are dozens such reports. And just one example, its not like its the only open bug. I have another one where livecd doesnt boot with 2 monitors connected on an nvidia card and one that has been marked "urgent" [since 2008]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267779") about VIA Rhine network card not working after a resume. The only thing that changes with each release is that I need to hunt for a new workaround.

If you look at microsoft, there is 6-10 months between beta and release, with ubuntu there is just 5 or so weeks? Thats barely enough time for testers to install and test, hardly enough for for developpers to even read and assess the bugs reported, lets just forget about properly testing the patches (if any). Its just too fast.

As a result we will get another "LTS" release riddled with confirmed and open bugs that will become the default download for the next 6 months. 

FWIW, I think it would be better to just rename the stable release to beta, have it in beta for 6 months, and provide the previous release (karmic now) with all updates as the stable release. 6 months from now you release Lucid as "stable". That would be more honest IMHO.

---

### Post by SgtPepperKSU on 2010-04-20
> **P4man said:**
> As a result we will get another "LTS" release riddled with confirmed and open bugs that will become the default download for the next 6 months.
Not necessarily agreeing or disagreeing with the rest of your post, but 10.04 will only be the "default" download for 3 months.  At that point 10.04.1 will be released, including fixes for bugs found in 10.04.

Those point releases will continue to be released throughout 10.04's lifespan, and *those* will be the recommended "stable" download until the next LTS release.

LTS doesn't mean it will be inherently more stable on the original release date than other releases, just that it will be maintained/supported for longer.

---

### Post by Taoye on 2010-04-20
> **SgtPepperKSU said:**
> Not necessarily agreeing or disagreeing with the rest of your post, but 10.04 will only be the "default" download for 3 months.  At that point 10.04.1 will be released, including fixes for bugs found in 10.04.

Those point releases will continue to be released throughout 10.04's lifespan, and *those* will be the recommended "stable" download until the next LTS release.

LTS doesn't mean it will be inherently more stable on the original release date than other releases, just that it will be maintained/supported for longer.

LTS does stand for "long-term support" after all, rather than "better initial support."

---

### Post by ranch hand on 2010-04-20
You also have to consider the ISO for the final release.  There is not much room to fool with things right now.

Between the release of 10.04 and the release of 10,04.1 is when you should see a lot of bugs repired that are not critical to the release.  This give the devs a chance to also make an ISO that is reliable and has the fixes included.

8.04.4 is very recent and I installed next to 8.04 to see the difference (and update both and upgrade them to 10.04).  There  was quite a bit of difference in the base install.

I think that the way they release Ubuntu is actually very well thought out and efficient.

---

### Post by P4man on 2010-04-20
> **ranch hand said:**
> 
Between the release of 10.04 and the release of 10,04.1 is when you should see a lot of bugs repired that are not critical to the release. 

Well, I guess that depends how you define critical. On 3 of my 4 machines with yesterdays daily build I can not get online, suspend or hibernate, then resume and be online again. On one I cant even boot the livecd. I have to disconnect a monitor, modify some scripts or jump through other hoops to get there (or closer to there, only on 1 machine can I actually get it to work to the point where I can suspend/resume and be online again).

although I have no exotic hardware, Im not saying my machines are representative of all ubuntu users, nor can i reasonably expect everything to work on every PC.  But what worries me is that most of these bugs are either long standing problems with long known workarounds that for some reason never get implemented, or regressions, things that worked on karmic,  yet havent even been looked at afaict. It seems highly unlikely im the only one suffering from these and many other bugs. How many critical bugs would there be in launchpad that havent even been evaluated? 

Mind you, im not criticizing ubuntu developers here at all, I just know Id be vilified by my developers if I were to announce a release date  to our customers for our software 6 months ahead, and timed it only a month after we actually started testing and with 100's of open and even unread bug reports. And thats for software that isnt 1% as complicated as ubuntu.

If its a release intended for testing and finding/fixing problems as you seem to imply, then its a beta release.  Karmic has been tested and bugfixed for 6 months now, its still not perfect, but Id call that stable. Lucid isnt, and given the time table, there is no way it could be. So call it a beta until 10.04.1 or .2 until its been properly tested, most bugs have at least been evaluated and where needed, fixed, and the fixes tested.  I think it would be a lot more honest then releasing it as is, and remove the beta label just because its april 28.

---

### Post by jedlacks on 2010-04-20
from my point of view, I went from using a monitor attached to my laptop on 9.10 to it being unreadable in the initial 10.04 RC.  With each upgrade the second monitor resolution  has gotten better and with the upgrade I just did I can at least make out characters on the second monitor.  Now it will stay plugged in on my desk and I can use it for the non-essentials.  

I am hoping that by the Final Release it was back to normal.

If it does not, I may try another distro as Ubuntu has been my friend for many years and I can't buy windows.

---

### Post by ranch hand on 2010-04-20
You probably ought to check the date on that daily.  I have not looked but I would be really surprised if that was dated the 19th.

Why?  Because of the freeze and the ISO yesterday came to ISO testing as the RC ISO candidate.

It worked real well on my hardware but I think it may not be the one, we may get another.  There were some bugs that looked that way, to me, in the i386 ISO (I am on x86-64).

I hope you did file bugs (somehow) on that network problem.

---

### Post by Artemis3 on 2010-04-20
Sometimes it needs to be released, so thousands of complains come in to make them act for a bug to be fixed.

In my case, i can suspend/resume perfectly in my desktop machines at home and work. So far the only thing i have been unable to do is install [**gallery2**](http://packages.ubuntu.com/lucid/gallery2), hopefully I'm not a production server, but should they keep ignoring [this bug](https://bugs.launchpad.net/ubuntu/+source/gallery2/+bug/558961), by release date it will become really evident when thousands of complains come from server admins.

So i view it like its some sort of permanent beta cycle. Once it reaches a point of stability (everything works) stay there and only upgrade if you dare to deal with new bugs ;)

---

### Post by P4man on 2010-04-20
> **ranch hand said:**
> You probably ought to check the date on that daily.  I have not looked but I would be really surprised if that was dated the 19th.

I always get them from here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Says april 19th.

> I hope you did file bugs (somehow) on that network problem.

Someone else did. Back in [2008]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267779") I just confirmed and added what I could (including rants lol).  Its still the same bug, just a different workaround. Anyway, that network card is not all that popular i guess (onboard nic for some asrock boards), but its not the only issue. Just using it as illustration.

---

### Post by KdotJ on 2010-04-20
Ok, so say I do install the RC on my machine and providing I keep updating it, by the time the final release comes, my system will be a fully fledged release version?

I know it's a n00b question, but updating from the RC to the Final release is not the same as say upgrading from 9.10 to 10.04.
I.E apart from bug fixes and updates, there's no real advantage to installing the Final release instead of the RC?

---

### Post by ranch hand on 2010-04-20
Yes you will be updated to the same thing as the final release.

There is a sticky for commonly asked questions.

There should not be much difference in the 2 ISOs.  You would probably miss a lot of last minute updates by waiting for the final.

---

### Post by KdotJ on 2010-04-20
> **ranch hand said:**
> 
There is a sticky for commonly asked questions.

Apologies for the repeat, and thank you for the reply

---

### Post by 23meg on 2010-04-20
> **P4man said:**
> You're right of course, but I do wonder if this is the right approach.

There's no single correct approach to doing free software distribution "right". There are various approaches that have been proven to be effective for different scenarios and goals; Ubuntu's [time based release model]("https://wiki.ubuntu.com/TimeBasedReleases"), like all others, works well in some areas, and fails at others. While the particular things that work and fail may change over time, [that fact is unlikely to ever change]("http://mdzlog.alcor.net/2008/10/29/ubuntu-quality"). 

> **P4man said:**
> If you look at microsoft, there is 6-10 months between beta and release, with ubuntu there is just 5 or so weeks? Thats barely enough time for testers to install and test, hardly enough for for developpers to even read and assess the bugs reported, lets just forget about properly testing the patches (if any). Its just too fast.


[QUOTE=P4man]I just know Id be vilified by my developers if I were to announce a release date to our customers for our software 6 months ahead, and timed it only a month after we actually started testing and with 100's of open and even unread bug reports. And thats for software that isnt 1% as complicated as ubuntu.[/QUOTE]

Those are direct comparisons between companies that develop software in-house from the ground up in a closed manner (Microsoft, and I assume, your company), and companies or projects that integrate and maintain software that's developed in a distributed manner by other parties with open processes (Canonical / Ubuntu), thus any conclusions derived from them are destined to be inaccurate.

---

### Post by ranch hand on 2010-04-20
@23meg

So well said.  Thank you.

---

### Post by cornflake000 on 2010-04-20
I'm sorry guys but I just don't get it.  I have 5 servers and 3 personal computers in my house and I run 52 computers outside of home and I just have never had the kinds of problems with these early releases that I read so much about every day on this site.  All of these machines are about as varied in type, age, hardware you name it.  I have simply never had the problems.  Of course the occasional not terribly important thing here or there that was put to bed by the developers or by my own simple tweaks but not the instantaneous, from the beginning, complained about but never been looked at type.  I have been using Ubuntu as well as several other Linux distributions for years now.  I worked with Karmic from the first day of alpha 1 and Lucid since Beta 1 with little or no issues whatsoever.

I made a similar comment during the Karmic development and I can say it again for Lucid. Sometimes I get the feeling there is some background bashing, lurking going on with undermining comments aimed at whatever one wishes to imagine.  I understand it's ridiculous for me to think that there really aren't any problems and it's all fiction but in my personal experience with Ubuntu, I just can't see anything but forest... I can see the trees too.

Maybe the deities just bless my computers above all others, or maybe I'm that millionth monkey... or maybe I'm just in the twilight zone.

I'd rather win the lottery!

---

### Post by P4man on 2010-04-21
> **23meg said:**
> There's no single correct approach to doing free software distribution "right". There are various approaches that have been proven to be effective for different scenarios and goals; Ubuntu's [time based release model]("https://wiki.ubuntu.com/TimeBasedReleases"), like all others, works well in some areas, and fails at others. While the particular things that work and fail may change over time, [that fact is unlikely to ever change]("http://mdzlog.alcor.net/2008/10/29/ubuntu-quality"). 

I have my doubts on the model, but even if you maintain that, I dont see the argument against making beta test periods (a lot) longer.

> Those are direct comparisons between companies that develop software in-house from the ground up in a closed manner (Microsoft, and I assume, your company), and companies or projects that integrate and maintain software that's developed in a distributed manner by other parties with open processes (Canonical / Ubuntu), thus any conclusions derived from them are destined to be inaccurate.

I humbly disagree. The development process would be vastly different (and I imagine, in many ways a lot more difficult to manage for canonical, as they have no direct control over 95% of the actual coding), but the testing and debugging would be similar, if not exactly the same. 

Once our code (or MS', or canonical's) falls in to the hand of end users and beta testers it becomes all but irrelevant if that code is the result of an opensource distributed development effort or not. Testing procedures would be the same, as would bug reporting (arguably a bit more difficult in a distributed process), defect retesting etc. 

FWIW, on this this wikipedia page on [software testing]("http://en.wikipedia.org/wiki/Software_testing"), open source or distributed development arent even mentioned, as it seems not relevant to testing:
[http://en.wikipedia.org/wiki/Software_testing](http://en.wikipedia.org/wiki/Software_testing)

Now someone might argue that testing eg a windows beta is blackbox testing and ubuntu whitebox (or at least greybox), but in practice the differences would be minute; windows would be grey too as most API's are exposed and documented, and most ubuntu testers would never dive in to the source code to do stuff like fault injection etc. Operating systems are just too big pieces of code for that. Especially something like ubuntu which contains a lot of productivity apps as well, making it a pretty massive testing target. Even though most of these apps are tested individually, testing something as massive as a linux distro  in a few weeks just makes no sense to me.

Anyway, downloading opensuse and debian right now, see if I have any more luck with the result of their approaches.

---

### Post by P4man on 2010-04-21
> **cornflake000 said:**
> I'm sorry guys but I just don't get it.  I have 5 servers and 3 personal computers in my house and I run 52 computers outside of home and I just have never had the kinds of problems with these early releases that I read so much about every day on this site.  

Im curious, how many of those are laptops (and are used as laptops) ? How many of the users actually use the bells and whistles (compiz, bluetooth, wifi, gaming, multi monitors, audio beyond just playing flash movies, etc)?

If those machines are bog standard desktops operating in a business or business like environment where they only need to connect to the network and run OO and evolution, Im more than willing to believe you'd get a vastly different result than me.

---

### Post by dcstar on 2010-04-21
> **SgtPepperKSU said:**
> Not necessarily agreeing or disagreeing with the rest of your post, but 10.04 will only be the "default" download for 3 months.  At that point 10.04.1 will be released, including fixes for bugs found in 10.04.

Those point releases will continue to be released throughout 10.04's lifespan, and *those* will be the recommended "stable" download until the next LTS release.

LTS doesn't mean it will be inherently more stable on the original release date than other releases, just that it will be maintained/supported for longer.

10.04 is deliberately based on more mature packages than any other previous Ubuntu release, so it will - all things being equal - have far less issues than any previous Ubuntu version. There will be bugs, but from what I have already seen far, far less than the usual avalanche that accompanies the usual Ubuntu "bleeding edge" releases.

I would equate 10.04 right now as equal in functionality and stability to a "normal Ubuntu release a month after official release date.

---

### Post by james.lancaster on 2010-04-21
> **dcstar said:**
> 10.04 is deliberately based on more mature packages than any other previous Ubuntu release, so it will - all things being equal - have far less issues than any previous Ubuntu version. There will be bugs, but from what I have already seen far, far less than the usual avalanche that accompanies the usual Ubuntu "bleeding edge" releases.

I would equate 10.04 right now as equal in functionality and stability to a "normal Ubuntu release a month after official release date.

I agree with this assessment.  I've been compiling test OEM images since Alpha 1, and I've been impressed with the coherence of this release.  I'd say Lucid has been at "final release" quality since about 4 days after Beta 2 if using Jaunty and/or Karmic as examples for comparison.

---

### Post by ranch hand on 2010-04-21
> **james.lancaster said:**
> I agree with this assessment.  I've been compiling test OEM images since Alpha 1, and I've been impressed with the coherence of this release.  I'd say Lucid has been at "final release" quality since about 4 days after Beta 2 if using Jaunty and/or Karmic as examples for comparison.
If you are comparing to 9.10, 10.04 was a lot more stable earlier than that.  The RC for 9.10 wasn't all that stable, I think we got 3 (might have been only 2) kernel updates after the RC was out.

---

### Post by seeker5528 on 2010-04-21
> **P4man said:**
> I have my doubts on the model, but even if you maintain that, I dont see the argument against making beta test periods (a lot) longer.

To me the argument against having a longer development cycle, is that you want to get the software to the people in a current enough state that those who only install final releases have a shot at providing feedback, making suggestions, etc... that are still relevant to the upstream developers.

The upstream projects have their own development schedules, beta testing, QA, etc... So how much work there actually is for the Ubuntu devs in integrating this stuff will vary from project to project, depending on how well the upstream works and/or how well communication is between upstream and downstream.

And while releases do come every 6 months there is still that longer 2 year arc between LTS releases for things that are expected to take longer to develop. Where something may go from only being available outside of normal channels in one release, to being available in the repositories in the next release, to being included but not the default in another, then still have some time to decide if it should be default in the next LTS release.

To my way of thinking 2 years is the real development cycle, everything in between is just progress. Even though I think of it that way I still expect a certain amount of stability in every 6 month release. 

Can't really see having a longer beta period for LTS than other releases, extra stability, if there is such a thing, will have be brought about a different way, which I think is partially automatic as a result of the extra thought in the version selection process when it is known the support period will be longer. But the longer support period can be a double edged sword as well, since it may mean going with something less baked in order to get the support from the upstream.

Later, Seeker

---

### Post by ranch hand on 2010-04-21
> **seeker5528 said:**
> To me the argument against having a longer development cycle, is that you want to get the software to the people in a current enough state that those who only install final releases have a shot at providing feedback, making suggestions, etc... that are still relevant to the upstream developers.

The upstream projects have their own development schedules, beta testing, QA, etc... So how much work there actually is for the Ubuntu devs in integrating this stuff will vary from project to project, depending on how well the upstream works and/or how well communication is between upstream and downstream.

And while releases do come every 6 months there is still that longer 2 year arc between LTS releases for things that are expected to take longer to develop. Where something may go from only being available outside of normal channels in one release, to being available in the repositories in the next release, to being included but not the default in another, then still have some time to decide if it should be default in the next LTS release.

To my way of thinking 2 years is the real development cycle, everything in between is just progress. Even though I think of it that way I still expect a certain amount of stability in every 6 month release. 

Can't really see having a longer beta period for LTS than other releases, extra stability, if there is such a thing, will have be brought about a different way, which I think is partially automatic as a result of the extra thought in the version selection process when it is known the support period will be longer. But the longer support period can be a double edged sword as well, since it may mean going with something less baked in order to get the support from the upstream.

Later, Seeker
I have become very tired of this silly argument about the release cycle.  It works the way it is.

I have seen all the points you have made here made before.  They have not been all in one place or as well stated.  Thank you very much.

It will not change any of the folks minds that want it changed.

Just like trying to tell  the plymouth and packagekit fans last cycle that they were bad ideas didn't change any minds.

I do not see any of them whooping about how great kpackage kit is (you fix it by installing synaptic) or how great plymouth is now.

Oh well, you get a system of releases that works so someone has to want to break it.

---

### Post by P4man on 2010-04-22
The current schedule is great if you like bleeding edge and dont mind having to cope occasionally with kernels that wont work on your system, having to try this or that videodriver, disable plymouth to get it booting and living with stuff like non working power management on your laptop (or working your way around it). Or if you're okay crossing your fingers your issue will be resolved in patch in a few weeks while you dualboot another OS or version.

But put yourself in Dell's shoes. Or any large company. Would you commit to shipping 10.04 on a gazillion laptops if you know the RC has been tested for only a *week*? If you've had the beta for barely a few weeks more? 

Dell will obviously have to do some of their own testing, but thats a pretty damn tough job if 10.04 itself is such a fast moving target. Even if they do test the beta, they barely have time to report issues or retest the fixes. 

Large companies need to plan things like this ahead, test thoroughly and you cant expect them to retest and validate your OS and its fresh patches in a matter of days. Its even worse if 10.04 comes out with a lot of openstanding issues that will be resolved shortly after release. Thats what you have beta's for normally, and its just not a good idea to ship your laptop with an OS that may or may not work properly only after the end user installed all updates. It should be bulletproof upon release, and that should have been proven already by a bulletproof beta that has been tested extensively, or oems and large corporations wont touch it.

Frankly, its no wonder to me ubuntu uptake with OEMs is less than stellar. Having a fixed release schedule is something they may like, but not having an opportunity to test the release before committing to it, I doubt they like.

---

### Post by philinux on 2010-04-22
Thread moved to recurring discussions.

---

