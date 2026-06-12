---
title: "Mandriva 2008"
date: 2007-09-22
forum: Other OS Talk
---

### Post by Amorphous_Snake on 2007-09-22
Anybody tried the new RC2 of Mandriva 2008? I am looking forward to getting the Free edition when it's released.

---

### Post by SunnyRabbiera on 2007-09-22
well I am kind of fond of mandriva spring as its one of the better ones mandy has released.

---

### Post by wolfen69 on 2007-09-22
isnt the free edition only free for a limited time?

---

### Post by SunnyRabbiera on 2007-09-23
maybe, but I was thinking of breaking down and buying mandy anyway.

---

### Post by Amorphous_Snake on 2007-09-23
> **wolfen69 said:**
> isnt the free edition only free for a limited time?

No. It's completely free, like Ubuntu. And you have unlimited access to the repos, like Ubuntu.

---

### Post by karellen on 2007-09-23
I never liked Mandriva, don't know exactly why as many folks told me is a nice and user-friendly distro. I guess it's about the urpmi...

---

### Post by SunnyRabbiera on 2007-09-23
> **karellen said:**
> I never liked Mandriva, don't know exactly why as many folks told me is a nice and user-friendly distro. I guess it's about the urpmi...

well its mainly because mandy set the stage for all desktop distro's, including ubuntu...
I give mandy a lot of credit for linux growth on the desktop

---

### Post by Amorphous_Snake on 2007-09-23
Does anybody know if XFCE will be on the Free DVD?

---

### Post by AdamWill on 2007-09-23
The Free editions of Mandriva are complete, full-featured distributions, they're not time limited, and you don't have to pay Mandriva anything for access to updates or to the Mandriva repositories.

The commercial editions of Mandriva come with some installation support and a few services, and some commercial packages. We're actually going to have some fairly cool commercial stuff in the 2008 edition but I can't say what yet =). But commercial stuff is the only difference as far as software goes, all free / open source software is available to anyone whether they're a paying customer or not.

Yes, XFCE is on the Free edition DVD:

[adamw@lenovo deluge]$ grep -i xfce mandriva-linux-2008.0-free-rc2.i586.idx 
2008-Free-i586-DVD libxfce4mcs3-4.4.1-4mdv2008.0.i586
2008-Free-i586-DVD libxfce4panel1-4.4.1-7mdv2008.0.i586
2008-Free-i586-DVD libxfce4util4-4.4.1-3mdv2008.0.i586
2008-Free-i586-DVD libxfcegui4_4-4.4.1-3mdv2008.0.i586
2008-Free-i586-DVD notification-daemon-xfce-0.3.7-5mdv2008.0.i586
2008-Free-i586-DVD task-xfce-minimal-2008-17mdv2008.0.noarch
2008-Free-i586-DVD xfce-appfinder-4.4.1-5mdv2008.0.i586
2008-Free-i586-DVD xfce-artwork-0.2-3mdv2008.0.noarch
2008-Free-i586-DVD xfce-dev-tools-4.4.0-3mdv2008.0.noarch
2008-Free-i586-DVD xfce-icon-theme-4.4.1-3mdv2008.0.noarch
2008-Free-i586-DVD xfce-mcs-manager-4.4.1-6mdv2008.0.i586
2008-Free-i586-DVD xfce-mcs-plugins-4.4.1-8mdv2008.0.i586
2008-Free-i586-DVD xfce-mixer-4.4.1-4mdv2008.0.i586
2008-Free-i586-DVD xfce-panel-4.4.1-7mdv2008.0.i586
2008-Free-i586-DVD xfce-session-4.4.1-9mdv2008.0.i586
2008-Free-i586-DVD xfce-taskmanager-0.3.2-6mdv2008.0.i586
2008-Free-i586-DVD xfce-utils-4.4.1-6mdv2008.0.i586

---

### Post by GeneralCody on 2007-10-10
I have the 2008 PowerPack, and must say I'm pleased. Plays encrypted DVD straight out of the box and mp3 as well. (It includes lisence for LinDVD and uses a gstreamer plugin for mp3).

The good news is that it's now free to become a member of the Mandriva Club, and access the Mandriva One CD with KDE, or the full free-version of Mandriva 2008, where you have to visit easyurpmi.org, to get the packages needed for playing DVD's and mp3's.

Changes are happening over at Mandriva these days...

:guitar:

---

### Post by lee_connell on 2007-10-30
how do i install xfce desktop in mandriva 2008?  I have it at the installation packages section and only gnome, kde are available.  I go into custom to select other window manager and I don't see it, only IceWM and Fluxbox

---

### Post by AdamWill on 2007-10-31
Ensure you have the official package repositories configured:

[http://wiki.mandriva.com/en/Docs/Basic_tasks/Installing_and_removing_software#Making_more_applications_available](http://wiki.mandriva.com/en/Docs/Basic_tasks/Installing_and_removing_software#Making_more_applications_available)

then just install the 'task-xfce' (or 'task-xfce-minimal') package.

---

### Post by jviscosi on 2007-10-31
> **GeneralCody said:**
> The good news is that it's now free to become a member of the Mandriva Club, and access the Mandriva One CD with KDE, or the full free-version of Mandriva 2008, where you have to visit easyurpmi.org, to get the packages needed for playing DVD's and mp3's.

That **is** interesting ... one of the reasons I quit Mandriva was I was tired of paying for the club membership (I was Gold I think) and then still being expected to pay per incident for online support, and then not having access to the "members only" repositories as well as not being notified of updates to packages without the club membership.  To this day I have a "check for updates" icon in my fbpanel because of that.  (The other reason I switched was that I never had a successful version upgrade via urpmi, and the other, other reason was that I hated the name change from Mandrake [kidding ... mostly].)

I'm unlikely to switch back to Mandriva but it sounds like things are moving in a positive direction there.

---

### Post by justin whitaker on 2007-11-01
> **jviscosi said:**
> That **is** interesting ... one of the reasons I quit Mandriva was I was tired of paying for the club membership (I was Gold I think) and then still being expected to pay per incident for online support, and then not having access to the "members only" repositories as well as not being notified of updates to packages without the club membership.  To this day I have a "check for updates" icon in my fbpanel because of that.  (The other reason I switched was that I never had a successful version upgrade via urpmi, and the other, other reason was that I hated the name change from Mandrake [kidding ... mostly].)

I'm unlikely to switch back to Mandriva but it sounds like things are moving in a positive direction there.

The Club has completely changed. For $50 per year, you get access to two Powerpacks, which includes proprietary software. 

Everything else, they are opening up, taking ideas from Fedora and from Ubuntu on how to get community participation. 

I don't know about paid support, since I never used it...basically, they are pushing everything over to community based, and concentrating on getting good code out the door.

---

### Post by beast2k on 2007-11-01
Why would we pay for something we already get for free in ubuntu? and give up apt-get for urpmi ? no way.

---

### Post by igknighted on 2007-11-01
> **beast2k said:**
> Why would we pay for something we already get for free in ubuntu? and give up apt-get for urpmi ? no way.

(a) the URPMI is the only GUI package manager I have ever used that I actually like, although the CLI interface for URPMI is pretty poor.

(b) You pay for things that you CANNOT get in ubuntu.  Legally at least.  Cedega and LinDVD are the biggies.  Sure, LinDVD isn't the greatest DVD player out there... but as far as I know, it is the only LEGAL way for those in the US and other places to legally decrypt and watch commercial DVDs

---

### Post by beast2k on 2007-11-02
I forgot about cedega but then again I gave up trying to do gaming in Linux but for those still trying IMHO they should pay the small fee of $5us and install cedega into ubuntu. This way they would help out the cedega guys a bit. For what you get out of Ubuntu for free and weigh that against what you get from Mandriva for whatever they charge now, it's no contest Ubuntu gets it. As long as Ubuntu is free and they ship cd's for free, it's going to be very hard for any distro, company, group, etc to ask for money for their distro unless the product brings to the table at least what Ubuntu gives away for nothing, and that is a tall order.

---

### Post by ffi on 2007-11-02
> **beast2k said:**
> I forgot about cedega but then again I gave up trying to do gaming in Linux but for those still trying IMHO they should pay the small fee of $5us and install cedega into ubuntu. This way they would help out the cedega guys a bit. For what you get out of Ubuntu for free and weigh that against what you get from Mandriva for whatever they charge now, it's no contest Ubuntu gets it. As long as Ubuntu is free and they ship cd's for free, it's going to be very hard for any distro, company, group, etc to ask for money for their distro unless the product brings to the table at least what Ubuntu gives away for nothing, and that is a tall order.

You dont have to pay for anything  in Mandriva which other distros, like Ubuntu give away for free,  except for the fact that you have to burn your own copy....oh well......

---

### Post by igknighted on 2007-11-02
> **beast2k said:**
> I forgot about cedega but then again I gave up trying to do gaming in Linux but for those still trying IMHO they should pay the small fee of $5us and install cedega into ubuntu. This way they would help out the cedega guys a bit. For what you get out of Ubuntu for free and weigh that against what you get from Mandriva for whatever they charge now, it's no contest Ubuntu gets it. As long as Ubuntu is free and they ship cd's for free, it's going to be very hard for any distro, company, group, etc to ask for money for their distro unless the product brings to the table at least what Ubuntu gives away for nothing, and that is a tall order.

Dude, Mandriva is **100% free (as in beer)**.  You have an OPTION to buy things that you have to buy anyways, but Mandriva is nice enough to offer them to you in one convenient package.  Powerpack is not the linux distribution, but a package of commercial, paid-for software that they offer to sell you that works with their linux distribution.  And, if you get the free version, you can get all 100% free as in speech software too.  As the above poster said, you have to burn the CD yourself (no ship-it), but ship-it takes a month anyways, so you are cutting 1/6 of the life off the product by using it... and time is money.  So no, I don't use ship-it and burn my own Ubuntu CD as well.

Your argument makes no sense and is completely false.  Go look up what Mandriva offers before you go on tirades like this.

---

### Post by jviscosi on 2007-11-02
> **justin whitaker said:**
> The Club has completely changed. For $50 per year, you get access to two Powerpacks, which includes proprietary software. 

That's cheaper than I remember; I'm pretty sure I was paying somewhere north of $120 for the yearly membership.  I'd have to check my old KMyMoney file to be sure though.

---

### Post by beast2k on 2007-11-02
$50 a year for a properly working system basicly, with ubuntu it's all free. I think there's another way to get the contents of the power pack cd's but the average user will not have the skills to install by any other means.

---

### Post by ffi on 2007-11-03
> **beast2k said:**
> $50 a year for a properly working system basicly, with ubuntu it's all free. I think there's another way to get the contents of the power pack cd's but the average user will not have the skills to install by any other means.

please point show me where in their repositories ubuntu hides lindvd and cedega

---

### Post by AdamWill on 2007-11-03
> **beast2k said:**
> $50 a year for a properly working system basicly, with ubuntu it's all free. I think there's another way to get the contents of the power pack cd's but the average user will not have the skills to install by any other means.

As has been explained to you several times, the stuff that's exclusive to the Powerpack edition of Mandriva is *not* stuff you can get from the Ubuntu repositories. You cannot get LinDVD, Cedega, or Fluendo media codecs from Ubuntu's repositories. These (and a few less important, equally commercial and impossible-to-legally-distribute-for-free packages) are the only things that are in the Powerpack edition of Mandriva but no other edition. *Everything* else in Mandriva is available for free.

---

### Post by igknighted on 2007-11-03
Adam, How many packages are in the Mandriva repo's?  I feel like it is roughly similar to what Ubuntu has, but I could be wrong there.

Also, don't forget that Mandriva has a true backports repository that you can enable to have the newest versions of popular applications, even if they come out mid-release.

[quote=beast2k]$50 a year for a properly working system basicly, with ubuntu it's all free. I think there's another way to get the contents of the power pack cd's but the average user will not have the skills to install by any other means.[/quote]

Wrong.  Just flat wrong, end of story.  You can, of course, get your system "fully working" for free using the plf repositories, which include things like VLC, libdvdcss2 and the win32codecs.  You can install wine, or use an existing purchase of Cedega or Xover Office.  But for those who live in countries (like the United States) where those programs are illegal, and who want to stay in line with the law (businesses or law-abiding citizens), Mandriva 2008 PowerPack is one of (if not THE ONLY) way to get these functionalities.  So there is no need, no lack of other apps that requires PowerPack for functionality.  It is purely an option, and a very fair one in my humble opinion.

---

### Post by beast2k on 2007-11-03
> **ffi said:**
> please point show me where in their repositories ubuntu hides lindvd and cedega
You ask that question as if cedega & lindvd somehow justify the cd cost. Cedega is only $5 a month from here [http://transgaming.org/subscription/subscribe.html](http://transgaming.org/subscription/subscribe.html) .
I have never used lindvd so I wouldn't know about that one. I think both are "non free" so they are not in the ubuntu repos lindvd may be in the medibuntu repos though.

---

### Post by igknighted on 2007-11-03
> **beast2k said:**
> You ask that question as if cedega & lindvd somehow justify the cd cost. Cedega is only $5 a month from here [http://transgaming.org/subscription/subscribe.html](http://transgaming.org/subscription/subscribe.html) .
I have never used lindvd so I wouldn't know about that one. I think both are "non free" so they are not in the ubuntu repos lindvd may be in the medibuntu repos though.

1yr PowerPack subscription: $69.00 USD [http://store.mandriva.com/product_info.php?products_id=73](http://store.mandriva.com/product_info.php?products_id=73)

vs.

1yr Cedega subscription: 12 x $5 USD = $60.00 USD
Fluendo Codecs: 28euros ~ $40 USD(?) 
[https://shop.fluendo.com/product_info.php?products_id=42&osCsid=da5gbs3jg9p27ki3ski275n824](https://shop.fluendo.com/product_info.php?products_id=42&osCsid=da5gbs3jg9p27ki3ski275n824)
LinDVD is not available for purchase individually yet, but judging by the prices on the intervideo website, I am guessing at best it'll be in the $30-$40 USD range.

So that's $69 versus a $100 for just those two things, plus a bunch more stuff including LinDVD.  On top of that, remember that all the "free" and "patent encumbered" dvd and audio/video playback that is available for free in Ubuntu's repo's is also available for free in the repo's of Mandriva's free versions.

Remember that Mandriva's PowerPack is just an add-on, giving those that want the above listed software a chance to buy it at a reduced price.  So lighten up.  It's a good deal if you want the software, and if you don't want it, don't buy it.  You lose nothing by not using it.

---

### Post by beast2k on 2007-11-04
> **igknighted said:**
> You lose nothing by not using it.
Now that is true.

---

### Post by AdamWill on 2007-11-05
You don't get a one year subscription to Cedega, so you should revise that number down a bit.

beast2k, LinDVD is *commercial* software - it's not available for free distribution - so any repository which made it available to the public would be breaking the law.

---

### Post by igknighted on 2007-11-05
> **AdamWill said:**
> You don't get a one year subscription to Cedega, so you should revise that number down a bit.

beast2k, LinDVD is *commercial* software - it's not available for free distribution - so any repository which made it available to the public would be breaking the law.

Do you get any update subscription?  Or just the Cedega version that was out when Mandy was released?

---

### Post by AdamWill on 2007-11-06
You get either one month or three, I'm not quite sure which.

---

### Post by igknighted on 2007-11-06
> **AdamWill said:**
> You get either one month or three, I'm not quite sure which.

No offense, but wouldn't it make more sense to just have a "powerpack" repository and have the latest versions of these commercial apps available to powerpack customers all the time?

Either way, keep up the good work.  Mandriva 2008 is the most fun I have had with a linux distribution.

---

### Post by samwyse on 2007-11-09
What's up with the 880 MB memory limit?

[http://wiki.mandriva.com/en/Releases/Mandriva/2008.0/Errata#2008_One_detects_only_up_to_880MB_of_RAM](http://wiki.mandriva.com/en/Releases/Mandriva/2008.0/Errata#2008_One_detects_only_up_to_880MB_of_RAM)

120 megabytes is a lot of memory. A reasonable trade for some kernel speed?

---

### Post by drcranium on 2007-11-10
I'm Mandriva 2008 and its great.  I've been through about 5 distros and Mandriva seems to nail KDE the best so far.  The last major one I need is OpenSUSE but I'm happy with Mandriva right now.  Basic stuff such as wireless drivers and codecs are easy to configure quickly but still allows you to do more complex stuff to the system.  I couldn't be happier.  Plus-KDE4 beta.  And its awesome :guitar:

---

### Post by tbroderick on 2007-11-12
Well, I switched over to Mandriva KDE One.

---

### Post by AdamWill on 2007-11-12
igknighted: there is one. The thing with Cedega is that Transgaming sells it on an ongoing subscription basis, $5/month or something, which gives you access to their regular updates. Obviously, the longer a subscription we want to give our Powerpack customers, the more Transgaming want us to pay them. As a Powerpack subscriber you get access to the Powerpack repo and can always download the base Cedega package, but the code you get to activate it will only give you access to the regular updates for a fixed period.

samwyse: yeah, it's a speed trade-off. himem support gives about a 5% performance hit in most scenarios. It's generally more useful to have the speed boost than the extra 120MB of RAM on a 1GB machine; the trade-off goes in favour of RAM when you get above 1GB.

---

### Post by rustybronco on 2007-11-18
keep in mind I don't care for kde (gnome fanboy), but I i am running a live cd, playing a cd of john denver and typing this in firefox...
6 year old machine, geforce mx400  with a widescreen monitor @1440x900, 512mb shared memory.
it's the only distro to do it so far, Impressive!

---

### Post by AdamWill on 2007-11-19
rustybronco: there's a GNOME live CD too. [http://torrent.mandriva.com/public/mandriva-linux-2008-one-GNOME-cdrom-i586.torrent](http://torrent.mandriva.com/public/mandriva-linux-2008-one-GNOME-cdrom-i586.torrent) , or you can get it from any of the official servers in /official/iso/2008.0 .

---

### Post by rustybronco on 2007-11-20
AdamWill, Thank you! I'll download and burn it tonight.
Got to make the wifes xp machine "linux" you know.

---

### Post by suziequzie on 2007-11-23
> **SunnyRabbiera said:**
> well its mainly because mandy set the stage for all desktop distro's, including ubuntu...
I give mandy a lot of credit for linux growth on the desktop

I'll give it the respect it's due mainly because it was the first linux distro I ever installed, way back in 2002. I had to sell my computer for rent money shortly afterwards, so it was a very short lived introduction. I was blown away by the very fact that it was so unlike any OS I had used before (Dos, Win 3.1, Win 98) and it was pretty slick. 

I'll give 2008 a try on my testdrive when it's out. Least I can do.

---

### Post by tbroderick on 2007-11-23
> **suziequzie said:**
> 
I'll give 2008 a try on my testdrive when it's out. Least I can do.


It's out.

---

### Post by suziequzie on 2007-11-24
> **tbroderick said:**
> It's out.

Cool. I'll give it a go after I've installed linux on an old amd k6-2 500 mhz computer a friend gave me to mess with. I'm thinking Puppy Linux, but I'm still doing some research.

---

### Post by darksong on 2007-11-24
I don't know if they still do. But i hated the way that FREE is plastered all across Mandy frees artwork, menu's and the advertisement for powerpack and the commercial mandriva on start-up. 

Yea is pretty cool, but i would rather use PClinuxOS, it doesn't come with all that crap.

---

### Post by tbroderick on 2007-11-24
> **darksong said:**
> 
Yea is pretty cool, but i would rather use PClinuxOS, it doesn't come with all that crap.

I'm using 2008 One KDE and don't see "free" plastered anywhere. There is an icon on the default desktop for "Upgrade to Powerpack", but that is easily deleted. There is a "Welcome" screen that popups after install, but is also easily turned off. You can see the "Welcome" screen in the [4th screenshot at TCS]("http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution=Mandriva%202008").

---

### Post by AdamWill on 2007-11-26
The wallpaper for Free says Free, the wallpaper for One says One, and the wallpaper for Powerpack says Powerpack. That's not really 'plastered all over', it's just wallpaper, you can change it if you like. And the 'Free' means 'Free Software', btw, not 'freeloader'. :)

---

### Post by lee_connell on 2007-11-28
anyone have an idea of when xfce one is going to be released?

---

### Post by igknighted on 2007-11-28
> **lee_connell said:**
> anyone have an idea of when xfce one is going to be released?

Is there supposed to be an Xfce One?  I don't believe previous versions have had an Xfce One, and I don't remember seeing a plan for one anywhere.

Download the DVD, there's an option to install an Xfce system from that.

---

### Post by lee_connell on 2007-11-29
I did download the DVD and i see NO option for XFCE at all.  Have you tried?  Check here about xfce one: [http://wiki.mandriva.com/en/Releases/Mandriva/2008.0/Tour](http://wiki.mandriva.com/en/Releases/Mandriva/2008.0/Tour).  Where is the option, I've tried custom and I don't see XFCE there.

---

### Post by igknighted on 2007-11-29
> **lee_connell said:**
> I did download the DVD and i see NO option for XFCE at all.  Have you tried?  Check here about xfce one: [http://wiki.mandriva.com/en/Releases/Mandriva/2008.0/Tour](http://wiki.mandriva.com/en/Releases/Mandriva/2008.0/Tour).  Where is the option, I've tried custom and I don't see XFCE there.

Weird... I don't have a DVD for mandy so I can't explore myself, but I thought for sure it was on there.  I would suggest installing a base system and installing Xfce via urpmi.

Xfce One is also a possibility, if it ever comes out.  I had never heard of it, thanks for the link.

---

### Post by AdamWill on 2007-11-29
XFCE One would be made by the volunteers who maintain the MDV XFCE packages, it wouldn't be an official build, but we'd probably mention it on our pages.

In the end XFCE didn't get moved to /main and put on the discs for 2008, it's still in /contrib for now. It's easy to install, though. Just set up the official repositories and install 'task-xfce' or 'task-xfce-minimal'. I believe a backport of 4.4.2 is impending, too.

---

