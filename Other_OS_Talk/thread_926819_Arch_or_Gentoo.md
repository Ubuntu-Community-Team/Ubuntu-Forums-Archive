---
title: "Arch or Gentoo?"
date: 2008-09-22
forum: Other OS Talk
---

### Post by lumpy211 on 2008-09-22
Hi all,

I've just ordered a Dell M1330 with Ubuntu pre-installed. I've been an Ubuntu user for a while now, but my real reason for buying a computer with Ubuntu pre-installed was so that I could get a machine with hardware optimized for Linux.

On my previous laptop, I've tried the following distributions:
[LIST]
[*]Ubuntu (beginning to become a bit bloated for my tastes)
[*]OpenSUSE (I'm still running this on my desktop actually)
[*]Fedora 9 (the KDE4 LiveCD was glitchy (and the MD5 sum was okay), so I didn't even bother to install it)
[*]Gentoo (had issues with the ALPS touchpad, but from what I understand the M1330 has a synaptics, so I don't think that'll be too much of an issue)
[*]Gobo Linux (loved the filesystem layout, but the nVidia recipe for Compile was broken, and the script on their website didn't work either. Not enough recipes to really make it usable)
[*]Sabayon (I loved the idea of how Portage worked, and Sabayon "just works" with my hardware, though it's very bloated, perhaps even more so than Ubuntu)
[/LIST]

Now, when I get the new M1330 I'm going to keep Ubuntu on it so that I can get support from Dell if I ever need it, but I want to use either Gentoo Linux or Arch Linux as my main operating system. My problem is, I can't find a non-biased review of the merits of Arch vs. Gentoo, or vice versa. Most Arch users seem to think Gentoo is dead (which [Google Trends]("http://google.com/trends?q=arch+linux%2C+gentoo+linux") seems to support), while (some) Gentoo users think that Gentoo is the king of all Linux distributions and that those who use other distros aren't really Linux users.

I think I understand pretty well the differences between them - Gentoo is all source based, whereas Arch is binary based on Pacman (though ABS can compile things from source), both are simple in that you have to get the computer running from just a kernel and install things from there, etc, etc. But what about the day-to-day running of the system? With Gentoo, I didn't have to do much maintenance once I got things running, but I always worried that my next update would break some packages. Furthermore, with Gentoo I don't have to worry about pulling in GNOME when all I want to do is install something like Pidgin by setting USE="-gnome" (I'm a diehard KDE user and I hate installing both KDE and GNOME side by side because my menus begin getting cluttered). What is the experience like with Arch? Is it comparable to Gentoo? I know what [Arch's wiki]("http://wiki.archlinux.org/index.php/Arch_vs_Others#Arch_vs_Gentoo") says, but that may be biased towards Arch.

So, those of you who have had experience with Gentoo or Arch (preferably with both!), which do you suggest I use on my dazzling new M1330? Please try to keep it clean and objective!

Thanks for your time!

---

### Post by crimesaucer on 2008-09-22
I just went through this myself. I have been using Archlinux for a year now. When I first installed it, I had a very weak laptop with a Celeron M chip, so Arch with xfce4 was much faster than xubuntu had been.


Recently, I got a nice laptop with an AMD Turion 64 X2 TL-60 so I installed ARCH x86_64.


Then I started to configure some new kernels for my machine and I realized the ARCH 64 kernel is a generic x86_64 kernel and when I tried to build a new -ARCH kernel with the -ARCH patch customized with AMD64 selected in the make menuconfig, I was displeased to find out it still was using the "generic" x86_64 setting instead of AMD64 after I built the kernel and installed it. (by checking the /proc/config)..... the 1000HZ setting stayed, but it went back to genericx86_64.


So, I went ahead and made a Vanillia kernel26 using AMD64 optimization and a zen2 patch to add some nice touches and optimizations like custom CFLAGS, CXXFLAGS, MFLAGS, and nice settings.... 


I liked the way my computer felt afterwards, it could have just been the nice settings with the timing set to 1000HZ instead of default 300HZ..... the only thing that I lost was suspend/resume.... which broke every update and barely worked anyway. Plus, if your hardware permits, you could build a tuxonice kernel.


But then I started to wonder about how a computer with all the programs built from source with the best CFLAGS/CXXFLAGS for AMD64 Turion 64X2 TL-60 would feel..... so I went for it. I tried an install from the Gentoo Live CD.


I'm no computer expert, but I do have 2 solid years on Linux, and 1 of them on Archlinux installing from the console and working with all of the conf files and pacnew files..... Anyway, after 2 days, and 2 full 12 hour attempts at Gentoo, I still had a failed computer.


I know I followed every instruction perfectly from the AMD64 handbook..... but it failed to boot into anything from the grub screen, and I didn't feel like waisting another day with a 3rd try.


So, I just fired up the Arch FTP install cd and had a fully working computer in less than an hour.


Afterwards, I installed my custom AMD64 zen2 kernel, and then found a program in the AUR called "pacbuilder".


Using pacbuilder you can edit your /etc/makepkg.conf to use your custom CFLAGS/CXXFLAGS etc.... and then you can rebuild your entire system from source just like Gentoo..... using your custom settings. Plus, you can use it as your default package manager to install new programs from AUR and ABS, you can even update with it.


I found that not every program compile for some reason, but it will list the ones that fail and you can either figure it out on your own and edit the PKGBUILD or install the failed programs in a different way (like a regular ./configure make & make install).... or just use the un-optimized binaries from pacman and the Arch repositories.


I just built the whole xfce4 desktop with my CFLAGS/CXXFLAGS for my chip, and only 2 programs didn't compile properly, so I just installed them with regular pacman.... Everything feels very fast and stable.


So to finish this up, you could just use Arch, build a custom kernel (or not), and have both the option to build everything from source using your CFLAGS/CXXFLAGS using pacbuilder, or install a quick binary from regualar pacman.


pacbuilder thread: [http://bbs.archlinux.org/viewtopic.php?id=48957](http://bbs.archlinux.org/viewtopic.php?id=48957)

---

### Post by chucky chuckaluck on 2008-09-22
the arch wiki has a pretty fair comparison of the two...

"Because the Arch installation is binary, it is much less time-consuming than the source-based Gentoo installation. Both Gentoo and Arch allow binary and source-based packaging; however, the Gentoo base system is source-based while Arch's is binary. Both are rolling-release systems. Arch PKGBUILDs are widely perceived as easier and more expedient to create than Gentoo ebuilds. Gentoo offers support for x86, ppc, sparc, alpha, amd64, mips, hppa, and itanium, whereas Arch offers i686 and x86-64 only. The Arch design approach is more focused on simplicity and minimalism, whereas Gentoo focuses more on the ability to globally control each aspect of source compilation. Both distros allow for a very high level of customization, therefore, Gentoo users will generally feel quite comfortable with most aspects of Arch."

i had considered gentoo at one point, but the documentation was tl/dr. arch's documentation was much more to the point and very good.

---

### Post by crimesaucer on 2008-09-22
I didn't mean to write so much..... but when I woke up early this morning, I fixed a lot of things on my new xfce4 install and drank some coffee so I just had one of those blah-blah-blah days.


Just to let you know, xfce4 optimized for my chip, on an AMD64 optimized zen2 kernel, using pacbuilder and pacman as a backup has made me happy about my computer again. I just got all my multimedia keys to bind on xfce4 with keytouch (also optimized), so all I have left to do is make suspend/resume work.


The best thing about Arch in my opinion is the Arch wikis, and the AUR/ABS.

---

### Post by will1911a1 on 2008-09-22
I've had very little experience with Gentoo, but if it helps, I've been using Arch for a while now and I love it.

---

### Post by mips on 2008-09-22
I've used both and prefer Arch. I find it easier & simpler to run, their philosophy is KISS after all.

If you like KDE then you MUST try KDEmod.

---

### Post by molom on 2008-09-23
From what I've heard, Gentoo takes ages to compile...

---

### Post by stokedfish on 2008-09-23
Arch, obviously.

---

### Post by afonic on 2008-09-23
+1 for Arch.

You can rebuild anything with any option you need using ABS. Building the whole system from source never made any sense imho, some programs can surely benefit while other may even be better left at default build settings.

---

### Post by void_false on 2008-09-23
> but I always worried that my next update would break some packages. 

Well, you are true Gentoo user - cant live without daily updates ;)
Personally, I dont think you should update your system much often. I've purchased a laptop last year, tried different distros and stopped with Ubuntu 7.04 because it recognized all my hardware (even multimedia and Fn+sumthing keys). After that I never run any updates on it. Why would you fix what's not broken?

---

### Post by molom on 2008-09-23
> **void_false said:**
> Well, you are true Gentoo user - cant live without daily updates ;)
Personally, I dont think you should update your system much often. I've purchased a laptop last year, tried different distros and stopped with Ubuntu 7.04 because it recognized all my hardware (even multimedia and Fn+sumthing keys). After that I never run any updates on it. Why would you fix what's not broken?

I think the exact same way.

---

### Post by Pogeymanz on 2008-09-23
I can at least tell you why I use Arch instead of Gentoo...

I assume that portage and pacman are about equal. This may or may not be true.

Gentoo is source-based and Arch is binary with the option of being source-based. I'm referring to ABS and pacbuilder. 

With Arch you can have a fully source-based installation, which takes time to compile or just install a binary which only takes seconds. With Gentoo, you have to compile. What if you need your system up ASAP? Or just a certain app ASAP? For me Linux is about choices, and Arch provides the most flexibility, I think.

However, I still want to play with Gentoo. But my main system will always be Arch.

I'm dying to find out how portage compares to pacman.

---

### Post by RiceMonster on 2008-09-23
I was going through this decision too. I chose arch because I really didn't want to compile everything. I pretty much only compile if somethings not in the official arch repos (which i rarely run into).

---

### Post by GrueTamer on 2008-09-25
I've used Gentoo and Arch quite a bit (likely my two most used distros, but with a bit more Gentoo experience), and I think there are a few things that need clarification.

First off, Gentoo is not made to be a simple distribution.  Rather, Gentoo puts you in the driver's seat when installing/configuring your system.  This is reflected through Portage.  The various flags and settings configured through make.conf are not what I would call simple, but they do their duties of giving the user control of the source compilations.  Arch doesn't have these settings, as you know.  Arch's configuration and other settings were created to be simple, and they have achieved their goal.  If you want simplicity, Arch is the way to go.  But Gentoo, through control, provides more flexibility and adaptability in the source compilations, but it can only be taken advantage of if the needs of your computer can take advantage of it.

Second, the binary package management used in Arch is much better for getting a system set up quickly and easily.  If you don't feel that compiling packages instead of installing from binary is very beneficial to you when considering the time it takes, then chances are binary package management will be better for you.  Having source installations available is also a nice touch, and very helpful for third party packages, but the compilation control given by Gentoo is lost here.  If you don't feel that you need this, it shouldn't matter.  I'd even say that most people don't need this control, but Gentoo's purpose is to give this control, whether it's needed by most or not.  Arch takes me half an hour to get the basic install done, and not a whole lot more to get a basic operating environment.  Due to the source compilation time and more extensive configuring in the install, Gentoo takes me a lot longer.  Based on my needs, this is fine, less time is usually not critical, but in other environments, time may be much more vital.  Gentoo also requires much more work and care to maintain (seeing as Arch takes close to nothing for me), but Gentoo's control and adaptability make it my system of choice.  Things don't break often for me, I believe this is a common misconception, but when things do break, the build log and (possibly) a google search are all I have needed to get things worked out.  Gentoo's documentation is very well done, with both the main documentation and a great wiki (don't forget the man pages, of course).  This, of course, isn't to say that Arch's is bad, because it's not, their documentation is very good as well.  But in Arch, I didn't need these things much at all.  It was simpler to figure out, easier to do later.

Arch is by far my favorite binary distribution.  It's goals of simplicity are met very well in my opinion, and if I couldn't have Gentoo, it'd most likely be my next choice.  However, I chose Gentoo for control.  Not because forum users told me it was better, but strictly because of the distro's goals and features.  When choosing between Arch and Gentoo, I recommend choosing based on the differing philosophies, seeing as they are both accomplished distros. This situation is no different.  Neither are better, they can only be better for the users with different needs.  My final advice is to ignore the amount of responses for each distro in this thread and compare the simplicity vs control approach, choose which one you want, and go for it.  Choosing distros isn't a competition, there is no better of the two, they can only be better for individuals and their individual needs.  This can be easy to forget when there are a ton of pro-Arch comments, but it's very important.  (This doesn't mean that the various comparisons of user friendly distros that often appear on this forum are wrong; these distros have similar goals, and are much easier to compare.  Gentoo and Arch remain fundamentally different).

I'd also like to mention that updating packages daily is not a requirement of Gentoo.  This is another misconception; Gentoo gives you the power to choose whether to update or not.

Don't have anything more to say, just pick based on design goals and enjoy the ride.  We'll still be here no matter which you choose :)

PS:  Distro-specific documentation will be inherently biased.  You're also on the Ubuntu Forums, which should naturally lean towards simpler and easier to use distros, rather than the fully configurable and controllable ones.  Plus, there are a lot of Arch users here.  Oh, and my post wasn't planned out, so it probably has some (possibly major) flaws in the way I wrote it.

---

### Post by kalpik on 2008-09-25
Arch, anyday..

---

### Post by Themaister on 2008-09-27
Arch ;) Can be as customizable as you want.

---

### Post by nrs on 2008-09-27
FWIW I just switched from Gentoo after some rocket scientist start littering ebuilds in the desktop-effects with EAPI="2" and other breakage. I'm sure it would've been fixed, eventually, but more and more I'm becoming dissastisfied with the quality of ebuilds, and the length of time it takes bigger projects to hit even ~arch.

---

### Post by Sorivenul on 2008-09-27
2 years ago I would have said Gentoo, maybe even up to a year ago.  Arch gets my vote though.  Gentoo is seeing too many [hard times]("http://www.gentoo.org/news/20080922-releng-announcement.xml") right now to be the system it can be.

---

### Post by cardinals_fan on 2008-09-27
> **Sorivenul said:**
> 2 years ago I would have said Gentoo, maybe even up to a year ago.  Arch gets my vote though.  Gentoo is seeing too many [hard times]("http://www.gentoo.org/news/20080922-releng-announcement.xml") right now to be the system it can be.
Sad news.  I've never been a Gentoo fan, but it's too bad that they're having so much trouble.

---

### Post by mips on 2008-09-27
> **cardinals_fan said:**
> Sad news.  I've never been a Gentoo fan, but it's too bad that they're having so much trouble.

As with other things in life it's politics related.

---

