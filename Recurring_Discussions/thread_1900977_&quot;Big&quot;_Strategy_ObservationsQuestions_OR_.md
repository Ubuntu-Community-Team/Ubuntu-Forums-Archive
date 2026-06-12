---
title: "&quot;Big&quot; Strategy Observations/Questions OR Why Ubuntu won't increase market share"
date: 2011-12-27
forum: Recurring Discussions
---

### Post by ReFranz on 2011-12-27
This user is a very ordinary computer user, ie NO programming skills, no significant aptitude for or inclination to learn programming. I use my computer for surfing, record keeping, and to listen to streaming audio.    After much delay, I finally installed 11.04 in a dual boot setup w/ Windows 7. I was satisfied--Natty Narwhal worked as 'advertised. When I 'upgraded' to 11.10, my sound system went bonkers. The default sound level is far too loud and high volume would assuredly destroy my speakers. I filed a bug report, and just skimming over the list convinced me that my 'minor' problem, which completely eliminates listening or recording while using Ubuntu, is far less troublesome than other users' bugs. It will never get any attention.    The volume of bugs caught my eye. It reminds me of the complaints about Windows in the 90's--that in Microsoft's mania to dominate the market, they brought out buggy, sloppy systems not ready for public use. UBUNTU'S INSISTENCE ON REVAMPS OF ITS OPERATING SYSTEM EVERY SIX MONTHS GUARANTEES THAT EACH REVAMP WILL BE LOADED WITH BUGS!! An operating system is a vast endeavor, according to 2 Ph.D acquaintances who SPECIALIZE in operating system architecture. If large organizations with vast resources such as Microsoft and Apple spend YEARS on each major upgrade of their systems, how can Canonical have major upgrades every six months and NOT HAVE BUGS GALORE???     Until Canonical changes the 'every six months' model and troubleshoots its Ubuntu releases BEFORE making them public, those bug lists will keep its market share near its present level.

---

### Post by arpanaut on 2011-12-27
It is not required that you upgrade your system every six months.
The interim releases are supported for 18 mo.
The LTS releases are implemented to give Long Term Support, Previously 3 years:
and with 12.04 this will increase to 5 year support. 

Excellent for commercial support and for those who do not want or need to be on the cutting edge of development.
Although this is not the official stance on the release cycles, personally I look at the interim releases as 
developmental/experimental, so in your case it might be best to stay with the LTS releases.

The Open Source philosophy is to release early and release often so as many people as possible can get their eyes on the software to fix bugs and move things along as fast as possible. Not everyones cup of tea... hence the LTS paradigm.

---

### Post by ReFranz on 2011-12-28
What is the practical upshot of LTS? Does this mean I need to uninstall 11.10 and install 10.04 which is the last release w/ LTS? What does LTS mean for minor bugs like this, which aren't important for the aggregate, but is a calamity for me & my machine?

---

### Post by mörgæs on 2011-12-28
If 11.04 works well for you, best is to stay with this one until support runs out. At that time 12.04 should have matured enough for installing, meaning you have an operating system for the next five years.

---

### Post by Paqman on 2011-12-28
> **ReFranz said:**
> What is the practical upshot of LTS?

It's simply supported for longer. The length of time between LTS releases roughly equates to what you'd get between releases of other major OSes like Windows. Both Windows releases and Ubuntu LTS releases are designed to be released at a pace that is suitable for use in an enterprise environment. The 6-monthly releases are for home enthusiasts. 

> 
Does this mean I need to uninstall 11.10 and install 10.04 which is the last release w/ LTS?

You could, or you if you can wait you could upgrade to 12.04 when it's released, as that's the next LTS. You can upgrade from one LTS straight to the next, skipping all the 6-monthly releases in between.

> 
What does LTS mean for minor bugs like this, which aren't important for the aggregate, but is a calamity for me & my machine?

If your machine is showing a regression from a previous release then it makes sense to use a different version. LTS releases are slightly less likely to suffer from these regressions, as they're tested for longer. They're also more likely to have fixes for bug backported into them if it's a serious problem.

What I would suggest you do is download the Alpha of 12.04 and see if your bug is still present when you boot up into the LiveCD. If it is, file a bug against it and it's highly likely to get fixed in time for release. The earlier in the cycle you report bugs the more likely they are to get sorted. If your bug report on Launchpad doesn't see much action, ask for help on IRC. Sometimes it's a case of attracting the right person's attention.

---

### Post by 3rdalbum on 2011-12-28
I don't understand why you don't just turn down the volume, if it's too high. Usually the default volume is "mute", actually.

The amplifier in the computer/speakers will not output enough power to damage the speakers themselves.

Extremely slight regressions such as yours do not slow Ubuntu's growth. That's too simplistic a statement.

Almost every piece of software changes from one version of Ubuntu to another. These are mostly not Ubuntu-specific changes, but changes in "upstream" projects. With change comes the possibility of regressions. If you'd prefer no change, then stick to the LTS releases.

Linux as a whole moves very quickly, and without six-monthly releases things would fall behind and be old and crusty. Xandros Linux fell behind quite badly a few years ago, and lost all its popularity. I think the distro is dead now.

Is there any evidence that developers knew about the problem you reported? If they didn't know about the problem, then you can't expect them to have fixed it before release. If Ubuntu was released yearly instead of twice-yearly, then the bug would still be present at release unless somebody reported it.

But as I said, maybe somebody did notice it. They just decided to turn down the volume a little instead of filing a bug report.

---

### Post by utnubuuser on 2011-12-28
The OP has actually raised a valid concern/point, which I noticed years ago too. Namely, that some of the releases are "interim" releases, and not LTSs, is not obvious to anyone "new" to linux who gets as far as deciding to download and try Ubuntu from the Ubuntu site.  
Whenever there is a "interim" release, that release becomes the default download, instead of keeping the LTS as the default download, wih the option to switch to the "new release".

And that is a fairly serious MARKETING issue, which is exactly what the OP stated. (Though the current setup at ubuntu.com has vastly improved when compared to how the site functioned as little as 2 years ago.)  

Personally, I'm of the opinion that only the LTSs should appear in the main download option, (even though my first install was 7.04), thereby making it the "automatic" version for newbs, and those who want, and/or are able to handle the quirkiness of "interim" releases can get the "latest and greatest" through a provided link...(the above opinion only pertains to "market-share", "marketing", and "new and in-experienced users").

---

### Post by Paqman on 2011-12-29
> **utnubuuser said:**
> 
Whenever there is a "interim" release, that release becomes the default download, instead of keeping the LTS as the default download, wih the option to switch to the "new release".


Which is a sensible default for geeks who're downloading Linux and loading it on their own systems (which is who that download page is for). Enterprise users or OEMs preinstalling it would obviously be far more likely to use the LTS, and aren't going to just install an image they've downloaded from ubuntu.com without talking to Canonical first anyway.

---

### Post by 2F4U on 2011-12-29
> Personally, I'm of the opinion that only the LTSs should appear in the  main download option, (even though my first install was 7.04), thereby  making it the "automatic" version for newbs, and those who want, and/or  are able to handle the quirkiness of "interim" releases can get the  "latest and greatest" through a provided link...(the above opinion only  pertains to "market-share", "marketing", and "new and in-experienced  users").

I would disagree on that. If the new versions wouldn't be the default, less people would download them and therefore less testing and feedback would be provided. But this is necessary to bring the development of new features and technologies forward.

---

### Post by ReFranz on 2011-12-30
@ 3rdalbum: 

I got as far as using the Alsa Mixer to try to fix the problem, after I fiddled w/ Banshee's settings. If my sound system is turned on, default is NOT mute.

---

### Post by ReFranz on 2011-12-30
And that is a fairly serious MARKETING issue, which is exactly what the OP stated. (Though the current setup at ubuntu.com has vastly improved when compared to how the site functioned as little as 2 years ago.)  

Personally, I'm of the opinion that only the LTSs should appear in the main download option, (even though my first install was 7.04), thereby making it the "automatic" version for newbs, and those who want, and/or are able to handle the quirkiness of "interim" releases can get the "latest and greatest" through a provided link...(the above opinion only pertains to "market-share", "marketing", and "new and in-experienced users").[/QUOTE]

Thanks for getting the idea! Will anyone @ Canonical listen to you?

---

### Post by madjr on 2011-12-30
i agree they should have less buggy point-releases and focus more on the LTS.

in fact the next LTS will have new hardware/kernel support for **2 extra years** (till the next LTS) and 5 years total support, so another point releases every 6 months **wont** make sense, they will just be duplicational work/bugs and a waste of resources canonical doesnt have.

**Point releases will be point-LESS**.

what they should do is have a **separate rolling dev release** to test all this stuff and for the **geeks** who want to be on the **bleeding edge**.

---

