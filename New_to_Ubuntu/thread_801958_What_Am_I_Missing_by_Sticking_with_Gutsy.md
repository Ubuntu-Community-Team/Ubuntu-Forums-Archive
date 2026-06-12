---
title: "What Am I Missing by Sticking with Gutsy?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by joshjani on 2008-05-21
When Hardy Heron first came out, I tried to upgrade from Feisty. It did not go well, and what I wound up doing, after much reading here, was installing a fresh Gutsy. I saw that many folks were having a lot of difficulty with one piece or another in Hardy, particularly with Intel onboard graphics. So I steered clear, downloaded Gutsy and now have it running relatively nicely.

My question is, what am I missing by sticking with Gutsy? If I continue to update my version, will I eventually get close to Hardy? I'm not even  sure what long term support means, as you all here on the forum are my support! Where would I get any other support, long term or otherwise?

Which brings me to something else...Is there a Knowledge base for Ubuntu, where many of the common problems have solutions listed and outlined? How do all y'all know so much on how to fix things? Sometimes I don't even know how to phrase my search, and as much as I love coming here for help, oftentimes I can't find what I need because I don't have the right lingo, or enough knowledge even to phrase the right question. For instance, if I search for "nvidia", I get WAYYYY too many posts, many of which talk about compiz or beryl, things that are out of a beginner's league. I almost live at that psychocats.net ubuntu site- thanks Aysiu!! But it'd be great to find some other knowledge bases.

I'm very close to giving XP the boot, at least on this machine, as I find that I really can do everything in Ubuntu- even Slacker (internet music), which was my one remaining reason for keeping XP in a dual boot. Before I do rid this PC of XP, though, I'd love to get more knowledgeable and confident with Ubuntu and linux in general.

---

### Post by Inxsible on 2008-05-21
You are missing out on updates to the packages and the bug fixes in those new versions if there were any.

If you have a separate home, then a fresh install of Hardy in the same root partition should be a breeze. Having said that, I upgraded a Xubuntu install from Gutsy to Hardy without any problems whatsoever.

Check out the links for Ubuntu Geek and Ubuntu Guide in my signature for a whole bunch of info on Ubuntu.

---

### Post by iaculallad on 2008-05-21
You're not missing anything just by sticking with Gutsy (just the updates). You're still using Linux and there's no big difference in using Hardy either, just an upgraded version. All the commands are the same, applications that could be executed in Hardy can be done in Gutsy, so, they're all virtually the same. You could wait for another 3 months or so if you decide to ride on to Hardy, giving enough time for the Ubuntu team to "fix" their 8.04 version.
This forum gives you the detailed solutions on problems posted by its members, it is in this forum that we all learn. We share ideas, solutions to problems we met before and now being encountered by some users. This forum is where we learn to tweak things and this forum help us exercise our brains and spread the spirit of Ubuntu.
In sticking with this forum, you'll still be meeting more knowledge-based site that show you solutions to problems.

---

### Post by Xiong Chiamiov on 2008-05-21
What do you mean LTS?  Kubuntu isn't LTS 'cause of KDE 4.0!

Oh, yeah.  GNOME users.

Anyway, aside from the default firefox3 (aka "crash all the time!") browser and the problems with [the kernel and the NVIDIA driver]("http://ubuntuforums.org/showthread.php?t=785074"), the only thing I've really noticed is that I can cancel the automatic fsck of my drives when booting by pressing escape.  That's quite a handy feature for when I'm troubleshooting (rebooting constantly) and I don't want to wait for a 300 gig partition check.

---

### Post by miesnerd on 2008-05-21
As I understand how the release cycle for ubuntu works, you will stop getting upgrades, i believe, as most of the upgrades will start going into the hardy heron repos. As others have said, I might be wrong. This last part, imo, is important because the release cycle separates ubuntu from other distos, such as Arch, which have a "rolling release" style.

what you're missing out on, as I see it, is both the pluses and the minuses.
If everything is working in gusty, there's no imminent reason to switch to hardy.

However, there are always updates which fix things-- runaway programs, uses of resources better (such as ram), etc. But you're also not having to deal with some potential bugs.

---

### Post by zvacet on 2008-05-21
@** joshjani**

As every release Hardy need to be polished and I think job will be done very soon.But,if you have working and customized Gutsy which is capable to do whatever you need to do there is no reason to upgrade.Gutsy is supported until April 2009 so you have planty of time to think about Hardy.LTS means that release is supported for 3 years(desktop) or 5 years (server).

---

### Post by prshah on 2008-05-21
> **joshjani said:**
> When Hardy Heron first came out, I tried to upgrade from Feisty. It did not go well, and what I wound up doing, after much reading here, was installing a fresh Gutsy. I saw that many folks were having a lot of difficulty with one piece or another in Hardy, particularly with Intel onboard graphics. 


The intel graphics issue is pretty well cleared up; the acceleration method in hardy was changed to exa from xaa, and particularly for exa, an additional parameter was required. If you decide to upgrade, post/pm and I'll be happy to give you more details.

I run intel onboard in all (most) of my computers, all are working excellent.

On the whole, I'd recommend upgrading.

---

### Post by roderick on 2008-05-21
> **prshah said:**
> The intel graphics issue is pretty well cleared up; the acceleration method in hardy was changed to exa from xaa, and particularly for exa, an additional parameter was required. If you decide to upgrade, post/pm and I'll be happy to give you more details.

I run intel onboard in all (most) of my computers, all are working excellent.

On the whole, I'd recommend upgrading.

What parameter? I never had any issues with my Intel card, so I am curious as to what parameter was missing, as I never had to add anything to make my setup run flawlessly (unless it was magically added in the backend).

I even recently performed a fresh install, and prior to updates, my card worked fine (base xorg.conf). Are you sure there was an Intel issue affecting new installs or just potential with upgrades if someone had a config option previously set in their old xorg.conf when using XAA?

Just curious, as my experience was flawless, both on an upgrade from Gutsy to Hardy and a fresh install of Hardy on the same Laptop (Acer Aspire 9410).

---

### Post by philinux on 2008-05-21
> **Xiong Chiamiov said:**
> What do you mean LTS?  Kubuntu isn't LTS 'cause of KDE 4.0!

Oh, yeah.  GNOME users.

Anyway, aside from the default firefox3 (aka "crash all the time!") browser and the problems with [the kernel and the NVIDIA driver]("http://ubuntuforums.org/showthread.php?t=785074"), the only thing I've really noticed is that I can cancel the automatic fsck of my drives when booting by pressing escape.  That's quite a handy feature for when I'm troubleshooting (rebooting constantly) and I don't want to wait for a 300 gig partition check.

[http://www.howtoforge.com/the-perfect-desktop-kubuntu-8.04-lts](http://www.howtoforge.com/the-perfect-desktop-kubuntu-8.04-lts)
Only the remix version with kde4 is not LTS, as it's bleeding edge.

---

### Post by aeiah on 2008-05-21
im another user that is sticking with gutsy for now. from what ive read about pulseaudio and the 'simplifying' of xorg i dont think ill be upgrading for a while. i only use it for websurfing, listening to music and watching movies and using bit torrent. im not about to mess around with a changed xorg to get my hdtv to stop overscanning again or mess around with audio.

---

### Post by philinux on 2008-05-21
On July 3rd Ubuntu 8.04.1 is due. This could be what you're waiting for.

---

### Post by SlappyPappy on 2008-05-21
I started in late April by installing Gutsy. I'm extremely happy as it's fast, doesn't crash or freeze, and I'm able to get most of the things I want to get done with it. Running W2K in VirtualBox is a great bonus as I have a few programs I can't do without that are PC based.

I will probably hang on to Gutsy for quite a while. If it ain't broke, why fix it?  :)

---

### Post by Inxsible on 2008-05-21
> **SlappyPappy said:**
> I will probably hang on to Gutsy for quite a while. If it ain't broke, why fix it?  :)
My motto is > If it ain't broke, you are not trying hard enough !!

I love the challenge of making things work. That's why since Ubuntu has become so stable that release after release just works, that I now trying my hand at the minimal install and also a few other distros like Arch and Zenwalk.

Eventually, I plan to give Gentoo a try too. ;)

---

### Post by joshjani on 2008-05-21
> **prshah said:**
> The intel graphics issue is pretty well cleared up; the acceleration method in hardy was changed to exa from xaa, and particularly for exa, an additional parameter was required. If you decide to upgrade, post/pm and I'll be happy to give you more details.

I run intel onboard in all (most) of my computers, all are working excellent.

On the whole, I'd recommend upgrading.

Well, I know from my personal experience that Hardy did not want to work with my Intel i810 onboard graphics. I could start a GUI and desktop, but got nothing but 640x480, no matter how many times I tried reconfiguring X. When I searched for answers, the result from several posts was something along the lines of, "Yeah, Hardy dropped the ball when it comes to i810 Intel graphics..." Since then, I have purchased an nVidia Geforce 6200 card, and with Envy have it running pretty well, though I did have trouble with X confused between the Intel driver and the nVidia. I did a lot of stuff in terminal that I didn't understand, (sorry I can't remember what guide I used) eventually updating and installing the nVidia drivers and controls.

Anyway- as much as I would like to have the "latest and greatest" version of Ubuntu, I am nervous about hitting that Upgrade Now? button, because I don't want to mess a good thing up now that I have it running smoothly. I do think I will someday, after I understand what I'm doing a bit more.

JC

---

### Post by Exsecrabilus on 2008-05-21
> **joshjani said:**
> When Hardy Heron first came out, I tried to upgrade from Feisty. It did not go well, and what I wound up doing, after much reading here, was installing a fresh Gutsy. I saw that many folks were having a lot of difficulty with one piece or another in Hardy, particularly with Intel onboard graphics. So I steered clear, downloaded Gutsy and now have it running relatively nicely.

My question is, what am I missing by sticking with Gutsy? If I continue to update my version, will I eventually get close to Hardy? I'm not even  sure what long term support means, as you all here on the forum are my support! Where would I get any other support, long term or otherwise?

Which brings me to something else...Is there a Knowledge base for Ubuntu, where many of the common problems have solutions listed and outlined? How do all y'all know so much on how to fix things? Sometimes I don't even know how to phrase my search, and as much as I love coming here for help, oftentimes I can't find what I need because I don't have the right lingo, or enough knowledge even to phrase the right question. For instance, if I search for "nvidia", I get WAYYYY too many posts, many of which talk about compiz or beryl, things that are out of a beginner's league. I almost live at that psychocats.net ubuntu site- thanks Aysiu!! But it'd be great to find some other knowledge bases.

I'm very close to giving XP the boot, at least on this machine, as I find that I really can do everything in Ubuntu- even Slacker (internet music), which was my one remaining reason for keeping XP in a dual boot. Before I do rid this PC of XP, though, I'd love to get more knowledgeable and confident with Ubuntu and linux in general.
You should understand that, when Gutsy first came out, there were issues also. Even more than Hardy, probably.

---

### Post by roderick on 2008-05-21
The problem with Intel was not Intel or Hardy specific. It was more likely your BIOS did not properly advertise the supported modes correctly. I had an issue with that in an earlier laptop, but using the correct xf86-video-intel (not xf86-video-i810) driver, the modesetting works flawlessly, even if the BIOS garbles it.

---

### Post by lazyart on 2008-05-21
No worries.  I've been watching the forums as well and am also holding off on Hardy for the time being.  I held off on Gusty on my desktop for a while... then forgot about it.   Then I realized Hardy was on the way and I was still on Feisty.

So I bumped up to 7.10 a week before Hardy was released.  If your system is humming, resist the initial urge to upgrade.  It'll probably be August or September before I make the move.  I too have a Nvidia card (FX5200) that I have seen a blurb or two about.  On top of that I'm pretty sure an update to VMWare is going to be necessary as well.  I'd also like to see my FF plugins redone for FF3.

When you do decide to do it, allow yourself a day to get things running they way you like it.  When I finally went to Gutsy (again, nearly 6 months after release) I waited for a Friday night and started the update.  I rebooted and everything...... worked.  Anticlimatic, but that's how I wanted it.  Had I jumped on early, who knows?

---

### Post by Exsecrabilus on 2008-05-21
> **lazyart said:**
> No worries.  I've been watching the forums as well and am also holding off on Hardy for the time being.  I held off on Gusty on my desktop for a while... then forgot about it.   Then I realized Hardy was on the way and I was still on Feisty.

So I bumped up to 7.10 a week before Hardy was released.  If your system is humming, resist the initial urge to upgrade.  It'll probably be August or September before I make the move.  I too have a Nvidia card (FX5200) that I have seen a blurb or two about.  On top of that I'm pretty sure an update to VMWare is going to be necessary as well.  I'd also like to see my FF plugins redone for FF3.

When you do decide to do it, allow yourself a day to get things running they way you like it.  When I finally went to Gutsy (again, nearly 6 months after release) I waited for a Friday night and started the update.  I rebooted and everything...... worked.  Anticlimatic, but that's how I wanted it.  Had I jumped on early, who knows?
LOL, I'm just the complete opposite of you.

I LOVE trying out new stuff, especially OSes.

When Hardy came out, I started anticipating for Intrepid.

I upgrade as soon as I can. XD

---

### Post by philinux on 2008-05-21
I'm going to try intrepid on my spare HD or virtualbox etc as soon as.

If it's broke I can fix it. Well try at least. :lolflag:

---

