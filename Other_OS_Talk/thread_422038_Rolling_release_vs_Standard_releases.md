---
title: "Rolling release vs Standard releases"
date: 2007-04-24
forum: Other OS Talk
---

### Post by Adamant1988 on 2007-04-24
Would you rather a distro:
[list]
[*]Release once every couple years or so, but use a rolling release method to keep your system up to date and your package selection new and interesting. (Like Arch, or Foresight) 

[*]Release on a standard, predictable, cycle with frozen repos, each release bringing in tons of newer software and features. 
[/list]

I'm just interested in seeing what you think about this and why you think that.

---

### Post by Rumor on 2007-04-24
One vote for rolling release system. I think it is one of the best features of Arch. It may just be that I am too impatient to wait between releases for the next version of Gnome or whatever else.
Also, I find with a rolling release system upgrading is not such a big production. It is like drinking a large glass of iced tea in little sips each time you pacman -Syu (or whatever command to update) rather than guzzling it down with a dist-upgrade or equivalent . . . both get the tea down, but one way can cause headaches :)

---

### Post by darweth on 2007-04-25
It depends on what the box is for, obviously.  For a server or a mission-critical workstation that MUST always work, you are better off using a more stable tested and proven distro that is on LOCKDOWN, baby!!!

If you are your average IRC chatting, web surfing, mp3 playing, casual 'productivity' homeboy who likes shiny new Amaroks and pidgins and ZSNES's and k3bs and even new GNOMEish and KDEkitty features rather quickly and can deal with the possibility of there existing a few kinks... why not a rolling release?

I have no idea about GENTOO or FORESIGHT, but it seems that though ARCH may be bleeding edge and rolling, it is not that much of a risk.  It has an excellent community, wonderful thorough testers, and ample warnings about problems that might arise and how to correct them.  Thunderbird 2.0 is not even in Pacman yet!!!!  So it is not THAT bleeding edge.  Damn!!!

***After having read about FORESIGHT, I can say that there is one aspect about it that turns me off.  It seem to be a GNOME-specific distro.  Nothing against that, of course.  It is the USER's CHOICE what to use and FORESIGHT might make a fine distro!!  I like things Vanilla though and prefer ARCH which is ideally a 'start from base and build your own home" distro.  I do not choose ones (rolling, at least) that set out to favor or push a certain DE.  It might be silly, but whatever!!!  I can always go to #gnome on some network to get GNOME support rather than needing it in distro-specific channels/forums***

---

### Post by Adamant1988 on 2007-04-25
> **darweth said:**
> It depends on what the box is for, obviously.  For a server or a mission-critical workstation that MUST always work, you are better off using a more stable tested and proven distro that is on LOCKDOWN, baby!!!

If you are your average IRC chatting, web surfing, mp3 playing, casual 'productivity' homeboy who likes shiny new Amaroks and pidgins and ZSNES's and k3bs and even new GNOMEish and KDEkitty features rather quickly and can deal with the possibility of there existing a few kinks... why not a rolling release?

I have no idea about GENTOO or FORESIGHT, but it seems that though ARCH may be bleeding edge and rolling, it is not that much of a risk.  It has an excellent community, wonderful thorough testers, and ample warnings about problems that might arise and how to correct them.  Thunderbird 2.0 is not even in Pacman yet!!!!  So it is not THAT bleeding edge.  Damn!!!

***After having read about FORESIGHT, I can say that there is one aspect about it that turns me off.  It seem to be a GNOME-specific distro.  Nothing against that, of course.  It is the USER's CHOICE what to use and FORESIGHT might make a fine distro!!  I like things Vanilla though and prefer ARCH which is ideally a 'start from base and build your own home" distro.  I do not choose ones (rolling, at least) that set out to favor or push a certain DE.  It might be silly, but whatever!!!  I can always go to #gnome on some network to get GNOME support rather than needing it in distro-specific channels/forums***

So you're saying that a slow paced carefully tested rolling release is undesirable? (add things when they're ready)

---

### Post by darweth on 2007-04-25
> **Adamant1988 said:**
> So you're saying that a slow paced carefully tested rolling release is undesirable? (add things when they're ready)

No.  The comment about Thunderbird was to merely emphasize that while Arch is bleeding edge and rolling, it is not 0day fanatical.  Arch, I believe, is pretty much a slow-paced carefully tested rolling release.  Some things are added in faster than others (new Amaroks... which probably have also been extensively tested in SVN incarnations and so on), but more critical packages receive the testing they are due.

---

### Post by Pobega on 2007-04-25
Rolling releases are better in my opinion, which is one of the great things about Debian; You can use it either way! I personally stick with Debian testing as a rolling release.

---

### Post by darweth on 2007-04-25
> **Pobega said:**
> Rolling releases are better in my opinion, which is one of the great things about Debian; You can use it either way! I personally stick with Debian testing as a rolling release.

I definitely want to try out Debian in such a manner someday.  I chose Arch because it seems easier to use as a rolling release and more stable, but I could be wrong.  Obviously Arch only has a *stable* branch (actually, there are testing/unstable repos but I never use the former and RARELY the latter) while Debian is in a perpetual state of unstable/testing that frightens me off.  And i would rather avoid Sidux for now.

---

### Post by Pobega on 2007-04-25
> **darweth said:**
> I definitely want to try out Debian in such a manner someday.  I chose Arch because it seems easier to use as a rolling release and more stable, but I could be wrong.  Obviously Arch only has a *stable* branch (actually, there are testing/unstable repos but I never use the former and RARELY the latter) while Debian is in a perpetual state of unstable/testing that frightens me off.  And i would rather avoid Sidux for now.

Well, I wish I had the page now, but there was a page describing the differences between testing/unstable and stable. Stable is only for the server side, really.

Testing's upgrades are thoroughly tested for bugs in unstable, before they fall into testing. So testing is probably more stable than Ubuntu (Being that testing has something to protect it, while Ubuntu has almost nothing behind it). Unstable is equally as stable as Ubuntu in my opinion, and 75% of people who run Ubuntu (Outside of servers) use unstable, so you'll be sure to find good support if you ever run into problems with Sid.

The only downfall to using testing, though, is you can run into trouble if you don't upgrade directly into the new testing (Rolling release), and jump 2~3 versions of XOrg, or something like that. If you go in as a rolling release (Under a month after the new stable was released) and just run apt-get update && apt-get dist-upgrade you should be perfectly fine :D

---

### Post by darweth on 2007-04-25
> **Pobega said:**
> Well, I wish I had the page now, but there was a page describing the differences between testing/unstable and stable. Stable is only for the server side, really.

Testing's upgrades are thoroughly tested for bugs in unstable, before they fall into testing. So testing is probably more stable than Ubuntu (Being that testing has something to protect it, while Ubuntu has almost nothing behind it). Unstable is equally as stable as Ubuntu in my opinion, and 75% of people who run Ubuntu (Outside of servers) use unstable, so you'll be sure to find good support if you ever run into problems with Sid.

The only downfall to using testing, though, is you can run into trouble if you don't upgrade directly into the new testing (Rolling release), and jump 2~3 versions of XOrg, or something like that. If you go in as a rolling release (Under a month after the new stable was released) and just run apt-get update && apt-get dist-upgrade you should be perfectly fine :D

Cool.  I am pretty much dedicated to Arch right now on this desktop and cannot be swayed (lol), but I am considering purchasing a laptop in the future.  That one is open to anything and Debian increasingly sounds promising.  Something fun and new to play with plus access to outstanding repos!  I just have a question... I know Debian is 100% FOSS when it comes to codecs, video drivers, flash, etc... but what about wireless drivers and laptop chipset stuff?  As long as I buy a laptop with Intel Wireless and so on, will I be pretty much fine?  I have never owned a laptop in my life so I am pretty intimidated by just about any distro in that regard.  Are there any manufactures out there in particular where it is rather simple to get all the stuff like SUSPEND, SLEEP, etc. working?  This might be off-topic for this thread though.

---

### Post by manmower on 2007-04-25
I prefer the rolling release system by far. Sometimes I'm tempted to try a server install of Ubuntu again, until I read all the threads about failing dist-upgrades etc., I just can't be arsed to reinstall every six months. Also, as of late, Arch devs have decided to release install ISOs more frequently (with each kernel version) which will make the initial install even more painless. Arch is at this point the one distro I truly know and love.

The only thing that might sway me is the sheer size of the Debian repos, so I'm interested by the comments of people who are using Debian as a rolling release distro. Does it work without glitches? How do you go about it to keep it safe and reliable?

---

### Post by Pobega on 2007-04-25
Debian is not only FOSS, Debian is only free software. The main repositories are all FOSS, but the contrib and non-free repositories are where the non-free programs go.

The only thing that doesn't go into the Debian repositories as far as I know are programs with restrictive copyrights, or anything that is illegal (You won't find certain things in US repositories).

Intel Wireless works fine for me, I'm using my ipw3945 without any problems. For some reason the only firmware that Debian offers is for the ipw3945 card, but I have a feeling that's because of some kind of copyright Intel has on the others. If you get an older wireless card, downloading the firmware from Intel's site isn't the hardest thing in the world; The rest you can just apt-get.

[http://packages.debian.org/cgi-bin/search_packages.pl?keywords=ipw&searchon=names&subword=1&version=all&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=ipw&searchon=names&subword=1&version=all&release=all)


> **manmower said:**
> I prefer the rolling release system by far. Sometimes I'm tempted to try a server install of Ubuntu again, until I read all the threads about failing dist-upgrades etc., I just can't be arsed to reinstall every six months. Also, as of late, Arch devs have decided to release install ISOs more frequently (with each kernel version) which will make the initial install even more painless. Arch is at this point the one distro I truly know and love.

The only thing that might sway me is the sheer size of the Debian repos, so I'm interested by the comments of people who are using Debian as a rolling release distro. Does it work without glitches? How do you go about it to keep it safe and reliable?

As a rolling release distro, it works completely glitchless. Of course, as any Linux distribution does, it eventually faces problems; But usually they're easy to fix. and the mailing list and forums are always their to help you;

[http://www.us.debian.org/support](http://www.us.debian.org/support)

I find Debian to be all around more stable than other distributions, mostly because packages are double checked by the Debian devs before they even fall into the repositories. And then they have to pass a ten day preliminary period of harsh testing in unstable, before they can even go into testing's repositories!

---

### Post by ThinkBuntu on 2007-04-25
I prefer a rolling release. Monolithic releases tend to give upgraders problems, as we've seen with Feisty. On the other hand, a kernel update here, a gcc update there, and you're computer is always up to date, rather than when the developers feel it's "time" to dump a ton of upgrades on you.

Monolithic releases are good for stability (Sarge, Etch) but are usually intended to create buzz.

---

### Post by manmower on 2007-04-25
> **Pobega said:**
> As a rolling release distro, it works completely glitchless. Of course, as any Linux distribution does, it eventually faces problems; But usually they're easy to fix. and the mailing list and forums are always their to help you;

[http://www.us.debian.org/support](http://www.us.debian.org/support)

I find Debian to be all around more stable than other distributions, mostly because packages are double checked by the Debian devs before they even fall into the repositories. And then they have to pass a ten day preliminary period of harsh testing in unstable, before they can even go into testing's repositories!
Having just browsed through the Debian repos it seems testing is still at Gnome 2.14 (to name just one piece of software), which seems particularly "old" for something labeled as being in testing. I guess I'm back to square one, thinking Debian is just not for me.

---

### Post by Adamant1988 on 2007-04-25
> **manmower said:**
> Having just browsed through the Debian repos it seems testing is still at Gnome 2.14 (to name just one piece of software), which seems particularly "old" for something labeled as being in testing. I guess I'm back to square one, thinking Debian is just not for me.

Debian testing is very stable for all intents and purposes, and significantly more behind the times. 

I agree with the points here, I can't really see where a rolling release is a major failure.  Other than the fact that release dates aren't nearly as important.

---

### Post by Rodneyck on 2007-04-25
Rolling releases are so much better. It is one of the shining attributes of Sidux. You never have to upgrade via a CD. They do have releases, but you can get everything on the new CD through an dist-upgrade or preferably through their custom script which captures any Debian Sid problems.

Distros like Sabayon who update about every two or three months, to the *buntus (every 6 months) are a pain in the ****. When you have your system tweaked and working perfectly, it does not make sense to destroy all the hard work and wipe the slate clean everyother month. I think these CD upgrades will be a thing of the past soon.

---

### Post by Adamant1988 on 2007-04-25
I kind of discuss another reason I feel that rolling releases might be better suited for users, on my blog. 

[ Should your OS be trivial? (part 1) ](http://opinunix.blogspot.com/2007/04/should-your-os-be-trivial-part-1_24.html)

---

### Post by Pobega on 2007-04-25
> **manmower said:**
> Having just browsed through the Debian repos it seems testing is still at Gnome 2.14 (to name just one piece of software), which seems particularly "old" for something labeled as being in testing. I guess I'm back to square one, thinking Debian is just not for me.

There are backports with 2.16, and I think it will fall into the repositories eventually; But keep in mind that Debian has JUST gotten out of a freeze, which means it may take a month or so for the programs to start falling back in.

Plus, really WHAT differences are there between 2.14 and 2.16? Any specific software you need you can apt-pin from different releases.

You could always just run Debian Sid.

---

### Post by Adamant1988 on 2007-04-25
I had a Poll added to see who thinks what :)

---

### Post by Nils Olav on 2007-04-25
It depends. Standard releases have the advantage of being set up in a particularly well tested way and thus are more stable. Then again it's not really an issue anymore.

---

### Post by Adamant1988 on 2007-04-26
> **Nils Olav said:**
> It depends. Standard releases have the advantage of being set up in a particularly well tested way and thus are more stable. Then again it's not really an issue anymore.

As said in the thread earlier, Debian Testing is a rolling release.  It's very stable.

---

### Post by Schalken on 2007-05-19
I'm all for the rolling release. Its not fair that I should have to take the risk of upgrading my system every 6 months in order to get any software that has been updated since the last release.

Plus, most of the time the upgrade breaks from doing some manual tweaks or using Envy or forgetting to reinstall ubuntu-desktop or something else, and I have to do a fresh install. That would be hell for anyone who doesn't have seperate "/home" and "/" partitions, and would be even worse on a mission-critical server.

Rolling release just works, and I would use Arch if only: [LIST]
[*]It had a nice default desktop install like the rest of the distros.
[*]It wasn't a DIY distro like Debian and Gentoo.
[*]It's package manager had a nice GUI. You can't expect new Linux users to know what "pacman -Syu" means.
[*]The rest of the system administration had a GUI.
[*]It had a comprehensive set of binary packages, like VMWare and Skype.
[*]It had support from ISVs. For example I don't see anything about Arch (or even Ubuntu) on the [Mathematica Linux compatibility list]("http://www.wolfram.com/products/mathematica/platforms/").
[/LIST] In short, I'm not using a distro that needs comprehensive Linux knowledge in order to operate, just for the rolling release.

---

### Post by jerrylamos on 2007-05-19
What is unfolding right now is there are a bunch of problems with Feisty 7.04 for some users.
Rule #1. Only bug fixes development says they are interested in releasing are for really big failures, whatever that means to them.  Everything else waits 6 months to the next release.
Rule #2. With the 6 month release cycle, that means twice a year there are all of a sudden a lot of people with different hardware and setups trying the new release all at once, and unforseen bugs crop up.  Rule #1 then applies.
Rule #3. There aren't any troubleshooting guides since "The Official Ubuntu Book" for Dapper.  Everyone is left searching forums and trying to help each other out.  This works, but is very inefficient from the user's time standpoint.
Rule #4. There are always a few gluttons for punishment (like me) who are trying the earliest of the early pre-Alpha, Beta, pre-release trying to find bugs in time for Development to fix them for release.  I found 2 months warning wasn't enough for the broken CD Live feature "persistent" which I and some others like a lot.  One user has spent a ton of time on that and found that maybe a dozen modules pinned at Feisty Fawn Herd 3 will enable "persistent".  After Herd 3, Ubuntu development picked up some experimental boot scripts from Debian which broke "persistent" big time.  You bet I'll try that on the June 7 Gutsy for whatever it might or might not be worth.  I'm all ready to try "can't access tty" as well.....everybody line up their favorite gripes to try out early.....can't say we didn't try.

The stated objective for Gutsy is "more polish" whatever that means.....

Cheers, Jerry

---

### Post by jariku on 2007-05-20
> **Schalken said:**
> In short, I'm not using a distro that needs comprehensive Linux knowledge in order to operate, just for the rolling release.

Foresight Linux has a web-gui for their package manager and they have rolling releases. But their repository system is a bit confusing, though.

---

### Post by SunnyRabbiera on 2007-05-20
I really want something that is in the middle.

Ubuntu's 6 month release cycle is a double edged sword, on one had I like it as version A would work better then version B, but version C can be better then versions A and B.
But Debian's release cycle also is double edged sword too, sure you might get a nice and **_stable_** system but when new software and hardware arrives you cannot get it unless you use **_unstable_** repos.

I want there to be a linux distro that has a yearly release cycle, where new packages are availible but you dont have to worry about breaking your system

---

### Post by Rodneyck on 2007-05-20
I think standard releases (every 6 months or whatever timeframe) will become obsolete. Who wants to completely backup their whole system and start fresh every few months?  What a backwards way of thinking, imo.

I use Sidux Linux and thank the stars they use a rolling release. Never had a problem and I never have to reinstall.

---

