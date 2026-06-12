---
title: "Shame on ATI"
date: 2009-03-05
forum: Recurring Discussions
---

### Post by Romu on 2009-03-05
[AMD Dropping R300-R500 Support In Catalyst Driver]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1")

When I think the X1600 of my Macbook Pro is still not well supported and it's just 2 years old, I just can say this will be my last computer with an ATI card.

And I'm going to quit Ubuntu to return back to OSX, the bad support of the ATI is one reason. This announce is a really bad news for Linux and Ubuntu.

---

### Post by mr_raider on 2009-03-05
S**t! I still use an x1900xt and play games on it like NWN under Ibex. What are my options when Jaunty comes around and Xorg gets upgraded? Will the open source drivers even run games?

---

### Post by Skripka on 2009-03-05
> **Romu said:**
> [AMD Dropping R300-R500 Support In Catalyst Driver]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1")

When I think the X1600 of my Macbook Pro is still not well supported and it's just 2 years old, I just can say this will be my last computer with an ATI card.

And I'm going to quit Ubuntu to return back to OSX, the bad support of the ATI is one reason. This announce is a really bad news for Linux and Ubuntu.


In all honesty...it isn't like the support was that great for those cards anyway.

---

### Post by WatchingThePain on 2009-03-05
I wonder if ATI are using trained snails as cheap labour.
They don't seem to operate with any urgency.

---

### Post by modestmelody on 2009-03-05
This is one of the reasons I've always had Nvidia cards and I've never had a problem.

---

### Post by WatchingThePain on 2009-03-05
My ATI is radeon 2400 HD basically I paid peanuts for it and got monkeys.
My other card is nvidia 8600gtx strangely it's never given me a single problem to date.
Maybe the expensive ATI cards are better but after the jams I've had I'm not gonna experiment with ATI.
It's like I've spent time doing loads of fixes which was their job.

---

### Post by Vince4Amy on 2009-03-05
I've always bought ATI Cards and in all fairness the ones they are dropping support for are quite old. With them cards I've found that the OpenSource Driver works great on them.

---

### Post by SamNSane on 2009-03-05
Still, if you read the entire story at the link, it's apparent that ATI has released the information necessary for driver development for most of their GPUs to the Open Source community. nVidia has not.

I've got a fairly expensive nVidia graphics subsystem (Quadro FX Go 1400) in a notebook that doesn't work as well with its restricted drivers as the cheap integrated Intel video subsystem using Open Source drivers on another notebook.

A lot of people with nVidia graphics are having problems with notebooks that overheat when running the restricted drivers under 8.04 and 8.10.

Offhand, I'd say the future in Linux looks brighter for people using ATI and Intel than it does for people running nVidia. If that is to change it will require nVidia to expend a lot more effort on Linux support -- or it will require them to go Open Source with their drivers.

I'm typing this on a notebook that is running Ubuntu 8.04. It is running an instance of Thunderbird, two tabs in Firefox, a couple of X applications via SSH on another box, and Zim. All lightweight apps. The GPU temp is 68 C, and the CPU temp is 49 C. But sometimes, if I open another browser instance and run the simplest flash object in it the CPU will climb above 70 C. And sometimes it will keep climbing (unless I kill the related processes) until I get a thermal shutdown.

NOT a hardware problem. Doesn't do it in WinXP, or Vista, or Server 2003 no matter how hard I drive it. Doesn't do it, either, if I revert from restricted to Open Source drivers. Doesn't do it on any of my other systems (9 in all) running Ubuntu with non-nVidia display subsystems. DEFINITELY nVidia's fault. (Or Dell's fault for a crappy implementation of the nVidia subsystem, but then why doesn't it crap out under Windows?)

---

### Post by binbash on 2009-03-05
Another reason to move to nvidia.It is a shame that we do not have enough brain power to count them  : )

---

### Post by WatchingThePain on 2009-03-05
Lol so let me figure this out..ATI drop support for old cards and don't offer support for new cards?. RI-DAMN-DICULOUS.
The line between old and new is so thin that we can consider it negligible hence ATI don't offer support. 
How the hell have they stayed afloat for so long.

---

### Post by Skripka on 2009-03-05
> **WatchingThePain said:**
> Lol so let me figure this out..ATI drop support for old cards and don't offer support for new cards?. RI-DAMN-DICULOUS.
The line between old and new is so thin that we can consider it negligible hence ATI don't offer support. 
How the hell have they stayed afloat for so long.

They (ATi) make great cards....drivers ehhhhh, not so much.

---

### Post by SamNSane on 2009-03-06
> **WatchingThePain said:**
> Lol so let me figure this out..ATI drop support for old cards and don't offer support for new cards?. RI-DAMN-DICULOUS.
The line between old and new is so thin that we can consider it negligible hence ATI don't offer support. 
How the hell have they stayed afloat for so long.

well, from the way I look at it, ATI is offering the best kind of support to the Open Source community. They (supposedly) gave all the information the devs need to write their own drivers. That's kind of the whole idea for getting hardware to work properly in an Open Source operating system.

It's why I've been happy to see that Intel is aggressively ramping up their R&D on dedicated and integrated display subsystems. Their contributions to the Open Source community in the form of data for writing drivers for their devices appears to have been prodigious.

Of course I'm no insider. Perhaps I'm interpreting it improperly.

---

### Post by WatchingThePain on 2009-03-06
So ATI gave up the code but no one developed it?.
Maybe they took a pay off.
But to the end user thats all just a 'black box' process- which never got processed, thus Nvidia is still better from the end users point of view.

---

### Post by mªrty on 2009-03-06
Not "the code", ATI released the specifications; meaning you and I can go look up *how* to write a driver for any old radeon card.

As one of the many former-ATI users here (I had a radeon 200M in a laptop), I'm not likely to buy their hardware again soon.

---

### Post by SamNSane on 2009-03-06
AFAIK, there are Linux devs actively developing drivers for ATI and Intel video subsystems. I think ATI was just announcing that they, themselves (as a company), are no longer participating in development for the Linux platform. Though this might result in a temporary inconvenience to some ATI users, my guess is it will be for the best in the long run -- unless you happen to have a particularly unpopular display subsystem. Developers tend to develop to their "market". Obviously the devs will first write drivers for the most popular chipsets and then write drivers for less popular chipsets. And, if you're unlucky enough to have a chipset with a miniscule representation on the platform, you might never see a driver. That's going to be true of any display subsystem from any manufacturer, regardless of whether or not it's supported directly by the manufacturer.

For instance, I bought an expensive nVidia display subsystem in my M70 about four years ago. nVidia will not provide official drivers on the Windows platform for any notebook. They shift that onus to the manufacturer of the notebook, claiming that the particular implementation by the notebook manufacturer can result in "generic" drivers not being functional. (That's true enough, I guess. But they're probably overstating the point.) Dell produced drivers for that several hundred dollar display subsystem for Windows XP -- and never bothered to do so for Vista. Why? Because, even though that sucker was expensive, they sold very few of them, and they ain't gonna spend the time and money to support them when the same investment in development will please more customers who bought cheaper stuff. You don't always get what you pay for.

---

### Post by sloggerkhan on 2009-03-06
hate to burst bubbles, but for a good stretch of time before ATI updated their fglrx driver and started releasing monthly, my x700 mobility worked better at nearly everything with open ati driver than fglrx. I remember switching from fglrx to the open driver so dri would work with compiz, and then switching back to play some video games with better FPS. About all this change means is that opengl apps will perform a worse than with proprietary and power management will be poorer. So for most users this seems pretty overblown. At least if you have x800 x700 etc gen parts.

---

### Post by sloggerkhan on 2009-03-06
> **SamNSane said:**
> AFAIK, there are Linux devs actively developing drivers for ATI and Intel video subsystems. I think ATI was just announcing that they, themselves (as a company), are no longer participating in development for the Linux platform. Though this might result in a temporary inconvenience to some ATI users, my guess is it will be for the best in the long run -- unless you happen to have a particularly unpopular display subsystem. Developers tend to develop to their "market". Obviously the devs will first write drivers for the most popular chipsets and then write drivers for less popular chipsets. And, if you're unlucky enough to have a chipset with a miniscule representation on the platform, you might never see a driver. That's going to be true of any display subsystem from any manufacturer, regardless of whether or not it's supported directly by the manufacturer.

For instance, I bought an expensive nVidia display subsystem in my M70 about four years ago. nVidia will not provide official drivers on the Windows platform for any notebook. They shift that onus to the manufacturer of the notebook, claiming that the particular implementation by the notebook manufacturer can result in "generic" drivers not being functional. (That's true enough, I guess. But they're probably overstating the point.) Dell produced drivers for that several hundred dollar display subsystem for Windows XP -- and never bothered to do so for Vista. Why? Because, even though that sucker was expensive, they sold very few of them, and they ain't gonna spend the time and money to support them when the same investment in development will please more customers who bought cheaper stuff. You don't always get what you pay for.

Or the more you pay for a computer, the more you're screwed in the long run.

---

### Post by SamNSane on 2009-03-06
> **sloggerkhan said:**
> Or the more you pay for a computer, the more you're screwed in the long run.

There may be a certain kernel of truth in what you say. It may even be reasonably generalized to other categories of merchandise. I have in mind two execrable BMWs and one truly accurse Mercedes with which I was personally acquainted. All purchased new. And then the used Volvo from the bad place which cost more in repairs each month than did all of the other cars combined.

My first VW bug ('63) was the best car I ever owned.

;)

---

### Post by bodhi.zazen on 2009-03-06
Moved to recurring discussions as this is an age old topic and it does not appear this is a support thread.

---

### Post by wolfen69 on 2009-03-06
> **SamNSane said:**
> 
Of course I'm no insider. Perhaps I'm interpreting it improperly.

yes, you are. just because your nvidia card (which is not that popular anyway) has issues doesn't mean ati is the better choice right now. i don't care if nvidia's drivers are not open, i just want it to work well. ati's drivers are garbage for the most part. ask anyone who has owned both cards. nvidia wins hands down.

---

### Post by SamNSane on 2009-03-06
> **wolfen69 said:**
> yes, you are. just because your nvidia card (which is not that popular anyway) has issues doesn't mean ati is the better choice right now. i don't care if nvidia's drivers are not open, i just want it to work well. ati's drivers are garbage for the most part. ask anyone who has owned both cards. nvidia wins hands down.

Wow! Stress much? Anyone of us drawing from his own limited experience can't necessarily do a good job of extrapolating to make such a broad statement. I think the thread is mostly conjecture about the eventual meaning of these developments. It looks as though the way forward for ATI and Intel users is better-assured than it is for nVidia users. You're free to draw different conclusions from mine, but you hardly have the absolute truth in your grasp any more than I do.

Ubuntu-system-wise I own three ATI cards, one nVidia card, and six integrated Intel display subsystems. The nVidia is the only one with display reliability problems and overheating. And even that system doesn't have a problem when booted into Windows XP, Windows Vista, or Windows Server 2003. If I were to extrapolate from my experience to the general, I'd be telling everyone that nVidia cards don't work in Ubuntu. (But I hear from many Ubuntu users that their nVidia display subsystems work admirably well. So I don't make such statements.)

From fairly early days of Linux development up to the recent past, at least, nVidia was in general a pretty good bet. But I wish they'd get on board the whole Open Source idea, at least if their continuing efforts are going to be less than whole-hearted. Even then, I'd personally choose to go to another manufacturer because I agree with the philosophy of  going Open Source.

Different horses for different courses.

---

### Post by sloggerkhan on 2009-03-06
I have systems with intel integrated, ati, and nVidia integrated and dedicated. Out them, currently intel's have been annoying me the most as they have a lot of driver performance regressions right now, but after than I dislike working with nvidia because they're more trouble to install and maintain if you want the latest driver. Keep having to rebuild the kernel module and don't show up in your package manager unless you package them yourself. I like fglrx on older on newer cards, I think it's mostly the x1000 and 2000 series that have a gray area right now.

---

### Post by Vince4Amy on 2009-03-06
> ask anyone who has owned both cards. nvidia wins hands down.

I do and I've never got the nVidia drivers to work as good as they should and I always end up finding that the drivers perform better on Windows. ATI drivers work almost equally on both platforms for me (And Better in Linux when I build the Kernel module for my custom kernel). Also why does the nVidia driver put a big splash screen on bootup.

---

### Post by RaZoR1394 on 2009-03-07
NVIDIA doesn't work perfectly under Linux for me but they work significantly a lot better than with AMD's fglrx. I had a really big problem with ATI some years ago with the so called X850XT. There was a bug which made the system totally lock up when logging out with GDM. It was not possibleto use the framebuffer and the stability was very bad. It got on my tits so I switched totally to nVidia on all machines. There was a major difference on almost all areas even though the GPU's were very different (lowend,highend,notebook). Now I got myself an HD3200 with a notebook after hearing about ATI's open source efforts. Well, I can't say it works that well specially in Jaunty as the 2d acceleration is totally unavailable. In Intrepid the open drivers work ok for 2d but when using fglrx the system is VERY unstable no matter when idling on the desktop or playing a movie. The login/logout bug was back again as well. WTF?

Well that system runs Windows 7 very good now so I'm not going back to Ubuntu on it for some time.

---

### Post by zolookas on 2009-03-07
> **Vince4Amy said:**
> Also why does the nVidia driver put a big splash screen on bootup.

Splash screen could be easily disabled by editing xorg.conf.

> **wolfen69 said:**
> ati's drivers are garbage for the most part. ask anyone who has owned both cards. nvidia wins hands down.

I can confirm that. I've had nVidia and ATi hardware and had no issues with nVidia. On the other hand, i've had (and still have) a lot of trouble with ATi's fglrx.

---

### Post by Vince4Amy on 2009-03-07
Most of peoples experiences are from a while ago when indeed the drivers were bad but remember AMD have not long taken over and they are trying as hard as possible to get this working.

---

### Post by Redache on 2009-03-08
Did anybody else see the part where they said Windows as well?. This is ATI trying to kill off older Cards to focus on the newer card ranges that they've released.

Since Architecturally things before the 2000 series were fairly different we can probably assume that they are going to be killing a lot of legacy bloat by not supporting these devices and this should hopefully lead to better drivers for the latest cards!.

You can probably pick up a 2000 series Radeon for cheap anyway, if you really want to.

---

### Post by mips on 2009-03-09
Arch Linux has actually gone as far as removing the proprietary ATI?AMD drivers from their repos because they are so crap.

---

### Post by Icehuck on 2009-03-15
> **mips said:**
> Arch Linux has actually gone as far as removing the proprietary ATI?AMD drivers from their repos because they are so crap.

Really? I just grabbed the latest catalyst drivers from the arch repos. Which work great on my old x850PE card.

---

### Post by mips on 2009-03-15
> **Icehuck said:**
> Really? I just grabbed the latest catalyst drivers from the arch repos. Which work great on my old x850PE card.

Or they are in the process of doing it. Read it on the mailing lists I think, will be moved to community or AUR from what I recall.

Edit: Found some links,

[http://www.archlinux.org/pipermail/arch-dev-public/2009-February/010394.html](http://www.archlinux.org/pipermail/arch-dev-public/2009-February/010394.html)
[http://www.phoronix.com/scan.php?page=news_item&px=NzEwMg](http://www.phoronix.com/scan.php?page=news_item&px=NzEwMg)
[http://www.phoronix.com/forums/showthread.php?t=15722](http://www.phoronix.com/forums/showthread.php?t=15722)

---

### Post by handy on 2009-03-15
Just so long as it is still available for those Arch users with cards that have benefited from AMD/ATi's ongoing driver work.

At least some of us have seen a lot of improvements over the last eight months or so.

***[Edit:]** Something in the ATi driver's favour is how incredibly easily they install.  I've never had nVidia drivers install so easily on the 2 different nVidia cards I have used under Linux.*

---

### Post by Primefalcon on 2009-03-16
I am running an x1300 myself, I'm not going to worry too much about this. from what I've been reading the OS community will have working drivers soon enough anyhow, tbh I'd prefer OS drivers over commercial ones anyhow as long as I get get full acceleration out of the OS driver which apparently is going to be possible now

---

### Post by arunthopil on 2009-03-19
> **Romu said:**
> [AMD Dropping R300-R500 Support In Catalyst Driver]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1")

When I think the X1600 of my Macbook Pro is still not well supported and it's just 2 years old, I just can say this will be my last computer with an ATI card.

And I'm going to quit Ubuntu to return back to OSX, the bad support of the ATI is one reason. This announce is a really bad news for Linux and Ubuntu.




hi ROMU................. I can help you fixing this............  its true that ATi giving a very bad support but the truth is most of the drivers are avilable in UBUntu ,......... a bit difficult to find.......... am new with linux but i found the way 2 fix your issue........... i was also facing the same issue with my ATi chipset X1200............ just visit my blog that i recently created.............  [http://thopilismaakan.blogspot.com/](http://thopilismaakan.blogspot.com/)

i am sure you will find the fix here :D :) :D

---

### Post by sloggerkhan on 2009-03-19
Arch is just moving them to the unsupported/extra/user repos. I don't think it matters much as my experience with arch is that those extra places to get stuff are vital for a good arch experience no matter what, and the open drivers should provide more than enough OTB to get up and running with arch.

---

### Post by Sprut1 on 2009-03-19
Are they stupid? Or just careless?

I won't ever buy an ATI card again, ever.

---

