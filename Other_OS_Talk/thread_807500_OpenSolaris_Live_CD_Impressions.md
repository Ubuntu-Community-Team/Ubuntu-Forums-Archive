---
title: "OpenSolaris Live CD Impressions"
date: 2008-05-25
forum: Other OS Talk
---

### Post by cardinals_fan on 2008-05-25
My free OpenSolaris Live CD arrived yesterday.  I gave it a spin this afternoon.  Here are my impressions from the Live CD:

[LIST]
[*]The CD booted up surprisingly quickly, almost as fast as Puppy
[*]The proprietary NVIDIA drivers loaded up perfectly **by default**.  This has never happened on any other OS and was an excellent surprise.
[*]The default GNOME environment was functional and looked great
[*]If you read many of my other posts, you'll see that I'm no fan of Compiz.  However, for the sake of my mini-review, I tested it out.  By virtue of the proprietary NVIDIA driver, it worked flawlessly off the Live CD - another first for me.  Even the water effects worked with minimal lag.
[*]Even when I had Compiz enabled, the system felt very snappy (for a Live CD), certainly faster than Ubuntu.
[*]I have never had a Linux distro recognize my wireless-adapter-from-hell off the Live CD, and OpenSolaris was no surprise here.  Total failure.  When I install it tomorrow, I'll follow a helpful guide to get ndiswrapper running, which I know supports my card.  There is currently a project to port the rum driver from the BSDs.  When completed, my adapter should work out of the box!  The only thing that I didn't like was the silly Network Auto-Magic tool.  It didn't work magically and must be disabled before you can configure the network manually.
[*]I was pleased to see that OpenSolaris avoided including bloatware like OpenOffice and Mono on the Live CD.  OOo is in the repos for any who need it.
[/LIST]
If that sounded like an advertisement... it could have been.  Since this is a first release, I expected bugs, not out-of-the-box perfection.  I'll post a more detailed review tomorrow or the next day discussing my installation and configuration attempts.  On the list: connect to network, test IPS packaging system, install/configure and run dwm, and install Opera.

---

### Post by Playa1313 on 2008-05-25
Wow, thanks for making this thread.  I always hear about other distributions that start with 'OPEN.'  By these, I mean OpenBSD and OpenSolaris for example.  Honestly, I am quite confused between these and Gnu/Linux, but am not afraid to say that.

I am willing to try something new.. but first I have to find out what the differences between them all are!

Anyways, great review/impressions list.

Thanks,
Brian

---

### Post by cardinals_fan on 2008-05-25
> **Playa1313 said:**
> Wow, thanks for making this thread.  I always hear about other distributions that start with 'OPEN.'  By these, I mean OpenBSD and OpenSolaris for example.  Honestly, I am quite confused between these and Gnu/Linux, but am not afraid to say that.

I am willing to try something new.. but first I have to find out what the differences between them all are!

Anyways, great review/impressions list.

Thanks!  I didn't expect such rave reviews ;)

Assuming everything goes according to plan tomorrow, this may be my perfect OS.  I really liked NetBSD, but the lack of a proprietary NVIDIA driver forced me away.  Every Linux distro I've tried, including my favorites (Arch and Zenwalk) have been difficult with my hardware.

If the OpenSolaris crew can get the rum driver into the next release, it would be the first OS that has ever worked out-of-the-box flawlessly for me.

---

### Post by Playa1313 on 2008-05-25
> **cardinals_fan said:**
> If the OpenSolaris crew can get the rum driver into the next release, it would be the first OS that has ever worked out-of-the-box flawlessly for me.

Wow, that is QUITE amazing for a first release (i think that is what you said).  If this is not just a coincidence and this OS works well with other setups too, this might be BIG.

---

### Post by cardinals_fan on 2008-05-25
> **Playa1313 said:**
> Wow, that is QUITE amazing for a first release (i think that is what you said).  If this is not just a coincidence and this OS works well with other setups too, this might be BIG.
I'm guessing that it should work well with most NVIDIA setups.  My wireless care is actually more difficult than many - some should work 'magically'.

Project Indiana has been around for a while, but this is their first official release (according to Ars Technica).  Their site lists their goal as "Production Ready All The Time".  Sounds awesome to me.

---

### Post by Playa1313 on 2008-05-25
> **cardinals_fan said:**
> I'm guessing that it should work well with most NVIDIA setups.  My wireless care is actually more difficult than many - some should work 'magically'.

Project Indiana has been around for a while, but this is their first official release (according to Ars Technica).  Their site lists their goal as "Production Ready All The Time".  Sounds awesome to me.

Wow, just reading their website, FAQ, and documentation, these guys look like they really have their act together.

This is a quote from their [Direct Rendering and 3D Drivers page]("http://www.opensolaris.org/os/project/dri/"):
> This project is targeted to port open-sourced DRI framework to Solaris, and provide 3D acceleration for Solaris x86. Meanwhile we would work with hardware vendors to enhance the 3D performance. 

Sounds really proactive and professional to me.

I might just download this puppy. :D

---

### Post by cardinals_fan on 2008-05-25
> **Playa1313 said:**
> 
I might just download this puppy. :D
I'm a sucker for nice CD art, so I ordered the Free CD.  It got here fast considering that I live in Alaska.

---

### Post by Cap'n Skyler on 2008-05-26
> **cardinals_fan said:**
> I'm a sucker for nice CD art, so I ordered the Free CD.  It got here fast considering that I live in Alaska.

well,you know--it is tougher in alaska--to get your wireless up and running :P
:lolflag:

---

### Post by digger95 on 2008-05-26
My experience with OpenSolaris wasn't quite as nice as yours.  

The Live CD was *painfully* slow to load (over 20 minutes) and I never did get a usable desktop.  It *looked* pretty spiffy (the gnome desktop that is) but I couldn't move my mouse more than a few inches without the cd-rom spinning back up and reading for another ten minutes.  Never did get to check anything out.  

I realize that my system specs are at the bare minimum for OpenSolaris so I expected it to be sluggish, but I at least expected to be able to click around a little and see what's under the hood.  On the plus side it looks like all my hardware was recognized and it even setup my HP printer for me.  No error messages of any kind.  It just wasn't designed to run on low-end machines like mine (P4, 3Ghz, 512MB).

By contrast, the Ubuntu live cd's run fine on my machine.

Dig

---

### Post by paul.matthijsse on 2008-05-26
> **digger95 said:**
> My experience with OpenSolaris wasn't quite as nice as yours. [...] The Live CD was *painfully* slow to load (over 20 minutes) and I never did get a usable desktop. Hello, same story here. I installed the OpenSolaris live-cd in a virtual machine (VirtualBox). Indeed some twenty minutes before the Gnome desktop showed up. First impression: a six years old desktop, it looked ugly! The install process took more than two hours, as opposed to half an hour or less with other OSes (Linux, Windows). After installation in a VM it stays a slow thing. Not my OS of choice... 

My hardware is moderate but recent (dual core, 1 GB ram etc).

---

### Post by MilesRdz on 2008-05-26
Everything was going great, up until I chose to install it. It just crashed and restarted. Weird?

---

### Post by chachawpi on 2008-05-26
The best thing about OpenSolaris is the Nimbus theme.  I use it in Arch.

---

### Post by cardinals_fan on 2008-05-26
Did most people who had problems with OpenSolaris burn their own disks?

---

### Post by kk0sse54 on 2008-05-26
Just finished trying out liveCD and for the most part all I can say is that it's alright. First thing I noticed was the awesome look, very nice default theme with a bunch of wallpapers. As for the speed I have to say it wasn't that fast for me actually more on the slow side. It had the speed of what I expect a liveCD to have of course nothing at all like puppy or DSL for me but it still wasn't as fast as the Ubuntu liveCD had been for me or Fedora. My biggest problem was that there was no sound because the driver was misconfigured for my audio and I couldn't get the the correct driver for my printer either. Both of them I am still trying to fix although I have to admit I don't what to do. Another minor problem for me was that while it recognized my video card and installed the correct driver I wasn't able to get compiz to work and enable any effects not even the most basic. Again only a minor of a problem not one of major concern considering compiz is more like icing on the cake nothing required. In all I was very pleased with OpenSolaris and if I can get the correct drivers working for me I think I am definitely going to try and install it.

---

### Post by d80zoom on 2008-05-27
I just tried it and it worked great. I have 1GB of ram and it loaded fairly fast. The only problems I had was with my wireless internet connection and no sound from my SoundBlaster Card. Compiz worked with my NVIDIA card and I liked the familiarity with the Gnome desktop. I have a Dell 1720 on USB, and it recognized it and loaded the drivers for printing. I downloaded the iso image from the OpenSolaris site and had no problems burning it. 

Likewise I did the same with the latest Ubuntu release of Hardy Heron and it will always hang up on me before it gets to the desktop. 

That ticked me off, so I am thinking seriously about learning more about OpenSolaris and trying to find a USB Wireless Adapter that will work with Solaris and eventually switch to it as my primary operating system.

---

### Post by damansandhu on 2008-05-27
open solaris live cd booted very fast , much faster than ubuntu
but the problem is that i dont know how to install it in another partition because i want to use windows and linux also .
and it looks similar to ubuntu.

---

### Post by handy on 2008-05-27
I used the version from November 2006, which was posted to me, 3 DVD's, it was a difficult install & an unpleasant experience to use.  I did not like it & removed it within a week.

---

### Post by digger95 on 2008-05-27
cardinals_fan,

I'm pretty sure that it's just my low system memory (512MB) that gave me the poor experience.  That's the bare minimum requirement for OpenSolaris and Sun admits that it hasn't been well tested with that amount of ram.  I have even read several reports on the web of people with 1+ GB of ram having poor experiences as well.  

I'm quite disappointed because it really looks like a nice OS.  With Linux I only use Slackware now because it's so stable, and because (for educational purposes) I want to stick to the most unix-like os I can get.  Outside of Linux it seems like OpenSolaris would be a great learning experience and future clients (once I graduate) might well have Solaris machines.  It would at least benefit me to take a peek at it I think.

I might give [_[COLOR="Blue"]Belenix[/COLOR]_]("http://www.genunix.org/distributions/belenix_site/") OpenSolaris a try when I pick up some more cd blanks.  It offers xfce and kde as alternatives to gnome and reportedly has lower system requirements.

Dig

---

### Post by chachawpi on 2008-05-27
There's a reason why it's called Slowaris when running on x86 architecture ;-)

---

### Post by aamukahvi on 2008-05-27
> **handy said:**
> I used the version from November 2006, which was posted to me, 3 DVD's, it was a difficult install & an unpleasant experience to use.  I did not like it & removed it within a week.
That's nowhere near the 2008.05 release. If you want to look at some pretty pictures:
[http://www.phoronix.com/scan.php?page=article&item=solaris_200805&num=1](http://www.phoronix.com/scan.php?page=article&item=solaris_200805&num=1)

---

### Post by LowSky on 2008-05-27
OK I got the LiveCD running on my Lenovo T60 (ATI graphics work), I then installed it on my home computer (atlon64 3700+, 2GB RAM, Nvidia 8600gt) and it was fast and very sleek, only problem was it completely messed up my Linux partition and also Grub. Thank God I installed Windows on a seperate Hard drive, I just booted directly to it and the deleted the Solaris parition.

Oddly enough when I went to fix grub with a Ubuntu 8.04 LiveCD,I couldn't get the live CD to boot, kept bringing me to some Debian Busybox thing. Some reason a 7.10 disk worked fine.

Other than my woes, what I like was the seemingly lower processor use and neat Nimbus theme (using it right now in Ubuntu). What I didn't like was the repos that had little or nothing of use. I might try Nexenta (sp?) as it has a proper Apt-get Debian Repo installed. I think if I wanted to run nothing but unix I would use OpenSolaris. I has all the normal things like Firefox and pidgen and Evolution and it install thevideo drivers and has compiz active, but it misses the mark with not having enough access to things like plugins for DVD playing and Wine. I bet in time OpenSolaris will be as good if not better than Ubuntu, and if Microsoft can actually prove that Linux is ripping them off, them many opensource people will move from linux to unix.

---

### Post by handy on 2008-05-27
> **aamukahvi said:**
> That's nowhere near the 2008.05 release. If you want to look at some pretty pictures:
[http://www.phoronix.com/scan.php?page=article&item=solaris_200805&num=1](http://www.phoronix.com/scan.php?page=article&item=solaris_200805&num=1)

I'm not really interested in playing with Solaris again at the moment, maybe sometime in the future?

It looks to have developed a long way in the last 18 months... good.

By the way, the machine I installed it on had a fast 64bit processor & 2Gb of RAM. 

Here is a link to Nexenta, which uses the OpenSolaris Kernel, APT & GNU Linux repo's!

***_[http://www.nexenta.org/os](http://www.nexenta.org/os)_***

I installed it some time ago, when it too had a long way to go, it will be much better now though.  

Nexenta is now in the process of developing a marriage between APT & the [***_ZFS_***]("http://en.wikipedia.org/wiki/ZFS"), which is cool, perhaps one day we will all be able to use ZFS in Linux/BSD as well?

***_[http://www.nexenta.org/os/TransactionalZFSUpgrades](http://www.nexenta.org/os/TransactionalZFSUpgrades)_***

---

### Post by cardinals_fan on 2008-05-27
> **handy said:**
> 
Nexenta is now in the process of developing a marriage between APT & the [***_ZFS_***]("http://en.wikipedia.org/wiki/ZFS"), which is cool, perhaps one day we will all be able to use ZFS in Linux/BSD as well?

Our dear friend the GPL restricts the use of CDDL licensed code... even though the source is available!  NetBSD and FreeBSD (perhaps OpenBSD as well) have projects under way to port ZFS to their respective platforms.  I can't wait to see it in NetBSD.

---

### Post by handy on 2008-05-28
> **cardinals_fan said:**
> Our dear friend the GPL restricts the use of CDDL licensed code... even though the source is available!  NetBSD and FreeBSD (perhaps OpenBSD as well) have projects under way to port ZFS to their respective platforms.  I can't wait to see it in NetBSD.

I don't expect it will become available under the GPL in a hurry, but we can hope, Sun is capable of changing the license.

---

### Post by LaRoza on 2008-05-28
I just tried the OpenSolaris livecd a few hours ago. I spent hours on it without thinking about it. It has all the standard GNOME tools and its driver support was (for me) as good/better than Linux (on the live cd). Compiz worked and all hardware worked. Interestingly, my headphones (my preferred sound device) were automatically used instead of my speakers. Installing flash was simple and didn't require me to restart Firefox (although it said it did).

I found OpenSolaris's theme to be very nice and its speed very admirable (remember, I was on a live cd, but didn't feel any lag during use)

So, in short, I spent several hours on it chatting on IRC and watching youtube. It sounds like a winner to me.

---

### Post by cardinals_fan on 2008-05-28
The OpenSolaris live CD is one of the best I've ever tried.  The installed OS was considerably less pleasant - for me.  You can read about my trials and tribulations (complete with extremely helpful responses) at [http://www.opensolaris.org/jive/thread.jspa?threadID=61548&tstart=0](http://www.opensolaris.org/jive/thread.jspa?threadID=61548&tstart=0).

My last post (I'm toast) explains what my **real** problems were.  As a replacement for standard Ubuntu, I would probably love OpenSolaris.  But I was looking for something more like NetBSD or Slackware.

---

### Post by cmay on 2008-05-28
i just played around whit the opensolaris live cd. if there is a 64bit version for my new computer i will install it. however i was surprised to see a unix system other than linux whit gnome. it looks cool but the session i had was whitout any internet acces. unlike linux that just find these things. 
the solaris look and feel is very much like my debian lenny setup so i felt very much "at home "
all in all a very nice experience.

---

### Post by jrusso2 on 2008-05-29
> **digger95 said:**
> My experience with OpenSolaris wasn't quite as nice as yours.  

The Live CD was *painfully* slow to load (over 20 minutes) and I never did get a usable desktop.  It *looked* pretty spiffy (the gnome desktop that is) but I couldn't move my mouse more than a few inches without the cd-rom spinning back up and reading for another ten minutes.  Never did get to check anything out.  

I realize that my system specs are at the bare minimum for OpenSolaris so I expected it to be sluggish, but I at least expected to be able to click around a little and see what's under the hood.  On the plus side it looks like all my hardware was recognized and it even setup my HP printer for me.  No error messages of any kind.  It just wasn't designed to run on low-end machines like mine (P4, 3Ghz, 512MB).

By contrast, the Ubuntu live cd's run fine on my machine.

Dig

I think your problem is ram.  Another 512 mb or more would make it a lot better.  I think you have plenty of CPU for it.

---

### Post by digger95 on 2008-05-29
> **jrusso2 said:**
> I think your problem is ram.  Another 512 mb or more would make it a lot better.  I think you have plenty of CPU for it.
Yeah I suspect you're right.  But in the end I'm kinda glad it didn't work out.  I'm really very happy with Slackware.  If Solaris had worked well, I'd have installed it to my hard drive, played with it for a few days, then just gone back to Slackware anyway.  So I count it as a 'near-miss'.  :)

---

### Post by cardinals_fan on 2008-05-29
> **digger95 said:**
> Yeah I suspect you're right.  But in the end I'm kinda glad it didn't work out.  I'm really very happy with Slackware.  If Solaris had worked well, I'd have installed it to my hard drive, played with it for a few days, then just gone back to Slackware anyway.  So I count it as a 'near-miss'.  :)
Slack is the best :)

---

### Post by digger95 on 2008-05-29
> **cardinals_fan said:**
> Slack is the best :)
Well I think so anyway!  Right now I'm running 12.1 on an Xfce-only install.  I'm loving the speed, and also that it's forcing me to learn things about Linux/Unix that I would not have learned otherwise.  And oddly enough, now that I've learned how to manage my own packages, I couldn't imagine giving up that control to an automated system.  Funny how things work out like that.

---

### Post by cardinals_fan on 2008-05-29
> **digger95 said:**
> Well I think so anyway!  Right now I'm running 12.1 on an Xfce-only install.  I'm loving the speed, and also that it's forcing me to learn things about Linux/Unix that I would not have learned otherwise.  And oddly enough, now that I've learned how to manage my own packages, I couldn't imagine giving up that control to an automated system.  Funny how things work out like that.
I like to install SLAX - it gives you a fully functional but still very minimal Slackware install.

---

### Post by damansandhu on 2008-05-30
yea , open solaris is very good to use in live cd , but i am going to try slack :d

---

### Post by handy on 2008-06-02
[***_Solaris_***]("http://www.imdb.com/title/tt0307479/") is a really cool science fiction movie, though I doubt Sun had anything to do with it. ;-)

---

