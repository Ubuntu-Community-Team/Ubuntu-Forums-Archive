---
title: "[SOLVED] yes, i need a new distro again"
date: 2008-09-12
forum: Other OS Talk
---

### Post by cardinals_fan on 2008-09-12
I'm at it again.  Every distro I use seems to have some deal-breaking fault.  Obviously, no distro will perfectly fit all these requirements, but whatever does the best job should be good enough.  Here's what I want:

* **Speed**.  This one is HUGE.  I care about RAM usage (I have plenty, but don't like to waste it) and overall responsiveness.

* **Minimalism**.  There are many possible ways to measure the minimalism of a distro.  The best I've found is iso size.  A small iso image can't contain much bloat.  Plus, I don't like waiting forever for a 700 MB iso to download.

* **Package management**.  This one is a bit awkward.  I don't need huge repos or fancy package managers.  All I want is a clean, easy way to install some basic packages.  I dislike Debian packaging - any Debian-based distro would have to be extraordinary in order to please me.

* **Hardware support**. I need an OS that supports the following:
- an **NVIDIA 6100** graphics card
- an **HP OfficeJet 7300** all-in-one printer
- a **Belkin F5D7050** wireless adapter, using rt73 chipset

* **Stability**.  I don't need five-year-old packages with enterprise-grade stability.  However, I like to stay a comfortable distance away from the bleeding edge.  If there's one thing I hate, it's when something that works fine is broken in an "upgrade".

* **Security**.  Security is a difficult term to define.  I expect a reasonable permissions policy and regular security updates.

* **Vanillaness**.  I realize that I'm asking a lot here.  This isn't required; it's just desired.  I prefer vanilla packages without a bunch of distro-specific patches.

* **Openness**.  No, I don't mean the source code.  I mean the developers.  Good projects listen to user input and don't snuff out bug reports out of denial (I'm looking at you, [Pardus]("http://bugs.pardus.org.tr/show_bug.cgi?id=7407")!).

**[COLOR="Blue"]Of course, I won't get all that.  I just need as much as is possible.[/COLOR]**  To speed up the process, I'll list some significant OSs that I've used, and what I dislike about them:

* Windows XP: Stable and with lots of software available, but permissions are handled awkwardly, there's no package management, and Microsoft handles updates poorly.

* Ubuntu and derivatives: For a while, I thought that Xubuntu might work for me.  Sure, it's bloated, but it worked pretty well.  Then I discovered some breakage in a number of packages I use frequently... and things went downhill fast.  It also uses Debian packages :(

* Slackware: One of my favorites.  It has great speed, packaging, vanillaness, stability, and just about everything else.  Unfortunately, it simply refuses to work with my printer.

* OpenSolaris: Almost great.  Almost.  The hefty resource usage and weak package management drag it down.

* Arch: I almost loved Arch.  It was fast, vanilla, custom... and broken.  Very, very broken.  The stability was ugly for me.

* Gentoo: No.  Just no.

* Vector: Light and nice, but truly ancient packages and lacking security updates worried me.

* Zenwalk: Buggy for me, and getting pretty bloated.

* Fedora: Bugs, and then more bugs.  Throw in a little bloat, and you've got a Fedora casserole!

* Mandriva: Bloated with creepy packaging

* OpenSUSE: Bloat and things that go bump in the night.  Maybe not.

I've used many others, but I think those are most of the big ones.

---

### Post by Whiffle on 2008-09-12
Arch works great for me... ?

---

### Post by cardinals_fan on 2008-09-12
> **Whiffle said:**
> Arch works great for me... ?
*pacman -Syu*
*NVIDIA driver breaks*
*fixes*
*pacman -Syu*
*wireless adapter breaks*
*fixes*
...

---

### Post by Whiffle on 2008-09-12
lol.  Yeah thats pretty weird.  I've had it on my NVIDIA equipped desktop for a while now, zero upgrade issues.  And wireless worked fine on my laptop when I had it on there.  Maybe NVIDIA + wireless is the deadly combo.  

What were you using for wireless?  I had WICD working very nicely.

---

### Post by jaqie on 2008-09-12
Well if you don't mind a do it yourself OS, or running 32 bit...

I used to babysit make all the time on FreeBSD. Thats what you will be doing all the time on it, babysitting make whenever you want to install something new.  I love the ports system, if only you didn't have to babysit make.  I would still be using FreeBSD if only.... I didn't have to babysit make.

I hope you see the only real problem I had with FreeBSD by now ;)

~edit~
Afterthought: Tried Fedora? I tried it in a VM just now and it seems quite nice.

---

### Post by cardinals_fan on 2008-09-12
> **jaqie said:**
> Well if you don't mind a do it yourself OS, or running 32 bit...

I used to babysit make all the time on FreeBSD. Thats what you will be doing all the time on it, babysitting make whenever you want to install something new.  I love the ports system, if only you didn't have to babysit make.  I would still be using FreeBSD if only.... I didn't have to babysit make.

I hope you see the only real problem I had with FreeBSD by now ;)

~edit~
Afterthought: Tried Fedora? I tried it in a VM just now and it seems quite nice.
I forgot to mention *BSD!  FreeBSD was nice, and it's something I'll consider.  NetBSD was my true favorite... if only NVIDIA offered drivers!

I wrote about Fedora.

---

### Post by Canis familiaris on 2008-09-12
> **cardinals_fan said:**
> I forgot to mention *BSD!  FreeBSD was nice, and it's something I'll consider.  NetBSD was my true favorite... if only NVIDIA offered drivers!

I wrote about Fedora.
PC BSD? It's based on FreeBSD. I'm trying it out today.

---

### Post by jaqie on 2008-09-12
> **cardinals_fan said:**
> if only NVIDIA offered drivers!
Um..... they do. for 32 bit only, which is why I specified FreeBSD 32 bit.

---

### Post by cardinals_fan on 2008-09-12
> **Anurag_panda said:**
> PC BSD? It's based on FreeBSD. I'm trying it out today.
I need the new version for my wireless drivers, and I won't install KDE 4.

---

### Post by ajmorris on 2008-09-12
gentoo is a very nice OS, you might like to try it :)
(and it meets all the requirements you outlined)

---

### Post by cardinals_fan on 2008-09-12
> **ajmorris said:**
> gentoo is a very nice OS, you might like to try it :)
(and it meets all the requirements you outlined)
To quote myself (in the OP):> **cardinals_fan said:**
> 
* Gentoo: No.  Just no.


---

### Post by Canis familiaris on 2008-09-12
Exact reason for that?

---

### Post by jaqie on 2008-09-12
Was the (thought) lack of an nvidia binary driver for FreeBSD (which its there for the 32 bit versions) the only major issue you had with fBSD? I'm quite curious now...

---

### Post by Sneaky07 on 2008-09-12
I don't know if this is what your looking but I'll just throw it out there:
How about DSL?  
[http://www.damnsmalllinux.org/]("http://www.damnsmalllinux.org/")

---

### Post by cardinals_fan on 2008-09-12
> **Anurag_panda said:**
> Exact reason for that?
Bugginess and endless compiling.
> **jaqie said:**
> Um..... they do. for 32 bit only, which is why I specified FreeBSD 32 bit.
Reread my post (bolded for emphasis):
> **cardinals_fan said:**
> I forgot to mention *BSD!  FreeBSD was nice, and it's something I'll consider.  **NetBSD was my true favorite... if only NVIDIA offered drivers!**


---

### Post by ajmorris on 2008-09-12
> **cardinals_fan said:**
> To quote myself (in the OP):

Why not?

---

### Post by cardinals_fan on 2008-09-12
> **ajmorris said:**
> Why not?
See above.

---

### Post by mike1234 on 2008-09-12
> **cardinals_fan said:**
> I need the new version for my wireless drivers, and I won't install KDE 4.


Gnome is available after installation. Not sure if PCBSD meets your requirements. It's Unix. :)

M.

[http://www.pcbsd.org/](http://www.pcbsd.org/)
[http://www.pbidir.com/bt/category/themes](http://www.pbidir.com/bt/category/themes)

---

### Post by linuxlizard on 2008-09-12
I love using tinyflux

fluxbox based on pclinuxos with thunar file manager.

ISO  235mb

full featured with the famous pclinuxos control center for easy setup of your hardware.

zillions of packages available via synaptic- you can install and run all the latest softwares like firefox3 opera open office, gimp, bluefish, games etc and they even run at a decent speed on my old 333mhz with 128mb ram and I can run opera, bluefish, gimp, and xmms with netradio going all at the same time.

It's very fast, very light, very clean. And lately makes me wonder what the heck ubuntu is doing with all my system resources on my desktop.

To do nvidia- just search nvidia in synaptic and select the driver with your card in the description- it will set it up automatically and ask permission to restart x.

printer set up in the control panel. My belkin wireless card on my laptop was set up automatically on install.

If you want a panel with start menu and desktop switcher, etc- install fbpanel, for icons- wbar.

If you want something more like ubuntu- pclinuxos gnome edition is very fast and light comparatively, yet seems to have all the bells and whistles like ubuntu- just not the huge friendly user community.

---

### Post by ajmorris on 2008-09-13
> **cardinals_fan said:**
> See above.
ah, sorry, missed that, yeah, the compiling requires a certain taste... its not buggy though ;) Its only buggy if the operator doesnt set something up correctly, as in gentoo, the user has to configure everything themselves. Thats how i like it, but its not for everyone :)

---

### Post by MaxIBoy on 2008-09-13
PuppyLinux impressed me with its lightness. On an old Pentium II with 256 MB of RAM, the liveCD booted as fast as Ubuntu does on my laptop. The desktop environment was too Windows-like for my tastes (only one menu, only one panel,) and the interface in general looked condescending (small parts, not for children under 4 years old.)

I haven't used it extensively, only as a liveCD, so I can't speak for its package management. I know it has its own package format but I haven't used it. I have also heard that you can install stuff and save stuff to the PuppyLinux liveCD after it's already been burned, but I didn't try that. I just burned a liveCD when I needed something for that Pentium II (which belongs to my neighbor. It's royally screwed over with viruses, so I'm helping her get files off it in return for being able to keep it.)

---

### Post by jaqie on 2008-09-13
> **cardinals_fan said:**
> Reread my post
Reread *MY* post. **they do.**
[http://www.nvidia.com/object/freebsd_1.0-7174.html](http://www.nvidia.com/object/freebsd_1.0-7174.html)

---

### Post by cardinals_fan on 2008-09-13
> **jaqie said:**
> Reread *MY* post. **they do.**
[http://www.nvidia.com/object/freebsd_1.0-7174.html](http://www.nvidia.com/object/freebsd_1.0-7174.html)
Apparently twice is not enough - I was referring to NetBSD ;)

I'll write more in the morning - I'm going to sleep.

---

### Post by molom on 2008-09-13
I think your looking for the perfect Cardinals ;)
I think the closest to stability and less breakages is one of the BSD's and if Arch doesn't suit you, I don't know what will :)

Cheers,
molom

---

### Post by pelle.k on 2008-09-13
There ought to be a "stable" arch. That would have been perfect.
There's been some talk about this on the arch linux forums, but generally when you mention this, people just sigh and basically say that they're in it for the rolling updates. I'm not. I like the system, but not the rolling updates. I'm a minority it seems. Long live democracy.
And, before anyone tells me to shut up and do something about it - let me tell you that i'm perfectly comfortable using ubuntu or any other "stable" linux distro should i need something stable, so i'm not whining or begging someone to do it for me. I'm just saying it would be neat.

---

### Post by miggols99 on 2008-09-13
I have found Arch to be very unstable as well. I'm going to keep an eye on this thread because I'm looking for a distro like the one you're looking for. Except I'd prefer KDE or Xfce on it (no GNOME!!)

---

### Post by TheSlipstream on 2008-09-13
Why not build your own Xfce from Ubuntu Server? Like Xubuntu without the bloat. I've never encountered any sort of package breakage in any Ubuntu, however. How can a package break when the packages aren't updated until 6 months? Unless you use dist-upgrade...

Edit: And I guess you can compile the current kernel, for the sake of vanilla-ness.

---

### Post by darrelljon on 2008-09-13
If you can get over the Debian package management, I'd recommend Debian or **MEPIS**. Good speed, minimal, good hardware support, stable and secure. You probably won't find the perfect distro unless you build one yourself.

---

### Post by Sorivenul on 2008-09-13
> **pelle.k said:**
> There ought to be a "stable" arch. That would have been perfect.

If you get your system to a stable or stable-enough point, isn't there still the ability to hold packages back from upgrading via your pacman.conf?  Forgive me for being potentially uninformed, it has been a few months since I've used Arch.

---

### Post by 67GTA on 2008-09-13
Have you tried PCLinuxOS? It almost meets your requirements. Tex and the gang are very secretive about what is happening. Their slogan is "It will be ready when it's ready." , and with no news about what is happening in between.

---

### Post by pelle.k on 2008-09-13
> Forgive me for being potentially uninformed, it has been a few months since I've used Arch.
Yes, you may hold a package, but that "block" isn't really aware of the rest of the system like say all the linked libraries and such, so in the end it may require more work from you than it's worth.
Also, you never know what package is gonna "break" during an upgrade, so theres little you can do about it unless you block everything in a stable state, and that case you may just as well not upgrade at all. Also, you'll not get security updates unless you upgrade.
I usually block nvidia, kernel26, glibc and xorg. Anything else than that is overkill IMHO.
Enough of that. I'm OT.

cardinals_fan, didn't you like frugalware?

---

### Post by chucky chuckaluck on 2008-09-13
if slackware is nearly perfect, except for your printer, then there must be a way of working it out. is it a matter of not knowing how to make it work, or not being willing to put in the effort (not judging you here. i wouldn't bother)?

---

### Post by forger on 2008-09-13
You're controversial on your requests by the way, minimalism+speed against already compiled binaries.. you can't seriously expect minimalism and speed and customisation if you don't compile it yourself! :)

On the other hand, here's what you asked for:
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)
Not debian, not redhat, not gentoo, not *bsd, clean linux.
Build it the way you want, the programs you want, the drivers you want, with the level of minimalism you want. You still have to build the whole system and compile everything.

Gentoo would be the ideal for you, your expectations are practically begging for it. Or slackware!
By the way, I have used Arch and wireless and nvidia 7300GT and never faced problems while upgrading or using that operating system during the week I tested it.

---

### Post by jaqie on 2008-09-13
> **cardinals_fan said:**
> Apparently twice is not enough
Funny, I was about to say the same thing. I asked you twice why you don't want to try ***_FreeBSD_*** again, but you seem to have ignored the question and answered one I did not ask instead, twice.

---

### Post by Bart_D on 2008-09-13
UbuntuLite* - [http://ubuntulite.tuxfamily.org/?q=node/2#cd](http://ubuntulite.tuxfamily.org/?q=node/2#cd)
Crunchbang Linux LITE version** - [http://crunchbang.org/forums/topic/crunchbang-linux-80402-download-locations](http://crunchbang.org/forums/topic/crunchbang-linux-80402-download-locations)
BoxBuntu** - [http://boxbuntu.com/?page_id=6](http://boxbuntu.com/?page_id=6)

* This one may do the trick for you.  **The ISO is 9.6 MB!!!**  As per Canonical's email message, their name will soon be changed to something else.

** may be larger (ISO size) than what you are looking for, but who knows.......worth a try.

---

### Post by Sorivenul on 2008-09-13
> **pelle.k said:**
> Yes, you may hold a package, but that "block" isn't really aware of the rest of the system like say all the linked libraries and such, so in the end it may require more work from you than it's worth.
Thanks for the information.  I held pretty much the same selection of packages when I was using Arch.  I figured the block more or less operated that way.

---

### Post by cardinals_fan on 2008-09-13
> **miggols99 said:**
> I have found Arch to be very unstable as well. I'm going to keep an eye on this thread because I'm looking for a distro like the one you're looking for. Except I'd prefer KDE or Xfce on it (no GNOME!!)
I'm not a GNOME fan either.  I prefer Xfce or Fluxbox.
> **Sorivenul said:**
> If you get your system to a stable or stable-enough point, isn't there still the ability to hold packages back from upgrading via your pacman.conf?  Forgive me for being potentially uninformed, it has been a few months since I've used Arch.
Yes, but you won't get any security updates that way.
> **67GTA said:**
> Have you tried PCLinuxOS? It almost meets your requirements. Tex and the gang are very secretive about what is happening. Their slogan is "It will be ready when it's ready." , and with no news about what is happening in between.
PCLinuxOS always seemed like Mandriva with DVD playback, but I'll think about it.
> **jaqie said:**
> Funny, I was about to say the same thing. I asked you twice why you don't want to try ***_FreeBSD_*** again, but you seem to have ignored the question and answered one I did not ask instead, twice.
FreeBSD is a possibility, but it (in my experience) takes a lot of downloading, and my connection tends to get bogged down in 50kb/sec speeds.

---

### Post by cotcot on 2008-09-13
Your requests fit quite well to gentoo. Your comment on gentoo is not very clear. Maybe it is worth to retry gentoo.

---

### Post by cardinals_fan on 2008-09-13
> **cotcot said:**
> Your requests fit quite well to gentoo. Your comment on gentoo is not very clear. Maybe it is worth to retry gentoo.
Waiting hours for that wretched thing to compile did not leave me happy.

---

### Post by afonic on 2008-09-13
Just my 2 cents on this one, without meaning to oppose the OP or anyone.

Most of the people that I meet and have the attitude "Ubuntu is broken!", "Arch is buggy" or "Fedora can't print" usually apply to one of those symptoms:

-they fail to follow simple instructions on how to make something work
-cannot use Google as a tool to solve most common problems
-have misconfigured their system or completely messed it by not following doc's instructions
-miserably fail to apply some new configuration or just run 1-2 commands after an update, concluding "this update broke my system".

For example, Arch. You say it is.. broken. Well sorry, but I couldn't help myself and started laughing with that statement. How did you come in such a conclusion? I am using Arch for 2 years now, the very first install I ever did is still serving me after moving the hard disk drive over 3 *very* different systems. (AthlonXP -> Opteron 939 -> Core 2 Quad). All I had to do is fix the filesystems mounting breakage and set the new modules in rc.conf. All my devices always worked, from the most basic ones to the most exotic. I have gone through 4 major Gnome upgrades, to not mention Nvidia drivers, kernels and and and... I never formatted or had to reset any configuration (for instance Gnome). And guess what? Not only it works without a hitch, it is fast, blot-free and stable. As a matter of fact I haven't logged out of Gnome for more than a week. To not mention 3 servers I am running in Arch, flawlessly.

Why? Because I know what I am doing.

To finish, I really didn't want to start any kind of fight or hijack this thread, I just wrote all these as an advice. Next time you want to find "the perfect distro" think about what *you* are doing wrong. Search, ask about your problems and try to solve them. Then help others with your experience. Educate yourself in using Linux better. Heck, it is all the same. If a printer works in Linux, it works in ALL distros, you just have to make it work!

---

### Post by cardinals_fan on 2008-09-13
> **afonic said:**
> Just my 2 cents on this one, without meaning to oppose the OP or anyone.

Most of the people that I meet and have the attitude "Ubuntu is broken!", "Arch is buggy" or "Fedora can't print" usually apply to one of those symptoms:

-they fail to follow simple instructions on how to make something work
-cannot use Google as a tool to solve most common problems
-have misconfigured their system or completely messed it by not following doc's instructions
-miserably fail to apply some new configuration or just run 1-2 commands after an update, concluding "this update broke my system".

For example, Arch. You say it is.. broken. Well sorry, but I couldn't help myself and started laughing with that statement. How did you come in such a conclusion? I am using Arch for 2 years now, the very first install I ever did is still serving me after moving the hard disk drive over 3 *very* different systems. (AthlonXP -> Opteron 939 -> Core 2 Quad). All I had to do is fix the filesystems mounting breakage and set the new modules in rc.conf. All my devices always worked, from the most basic ones to the most exotic. I have gone through 4 major Gnome upgrades, to not mention Nvidia drivers, kernels and and and... I never formatted or had to reset any configuration (for instance Gnome). And guess what? Not only it works without a hitch, it is fast, blot-free and stable. As a matter of fact I haven't logged out of Gnome for more than a week. To not mention 3 servers I am running in Arch, flawlessly.

Why? Because I know what I am doing.

To finish, I really didn't want to start any kind of fight or hijack this thread, I just wrote all these as an advice. Next time you want to find "the perfect distro" think about what *you* are doing wrong. Search, ask about your problems and try to solve them. Then help others with your experience. Educate yourself in using Linux better. Heck, it is all the same. If a printer works in Linux, it works in ALL distros, you just have to make it work!
I'll address these points under two blocks:

* I'll give a more thorough explanation of my printing issues in Slackware.  Could I get hplip setup in Slackware?  Certainly.  I haven't been in the mood to do so, but it's not something I'm unwilling to do.  My other issue with Slack is it's distribution format - my connection isn't fast, and I don't like to download anything over 350 MB unless it's absolutely necessary.  I'll go this route if it's necessary, but I'd rather not.

* I guess I'm just unlucky with my hardware.  The latest NVIDIA drivers are broken with my card (NVIDIA's fault, not Arch's).  So, when I upgraded, I couldn't start X.  My wireless adapter was broken a couple weeks ago with the upgrade to kernel version 2.6.26.2.  Could I fix these things?  Sure.  However, when I don't have a relatively free weekend (like this one), I haven't got the time.  I need something ROCK-SOLID.  When I have to turn in an English essay the next day, and I've already spent most of the day at school / ski practice, I have no time to deal with a broken Abiword package.

I actually think I would like CentOS - but there's no way I'm downloading a DVD.  Maybe I should actually shell out a couple bucks to have it shipped up here to Alaska...

---

### Post by 67GTA on 2008-09-13
PCLinuxOS is based on Mandriva, so it has similarities, but it uses Synaptic/Apt. They should have an updated 2007 ISO out real soon so you don't have to catch up on all of the updates since the first version was released. I installed it on my aunt's low end Emachine with 256MB ram, and it was very snappy. I just never liked the weird GTK theme Mandriva(PCLinuxOS) used.

---

### Post by cardinals_fan on 2008-09-13
As for a few other distros suggested:

* Puppy.  I've never really liked Puppy - the interface is very condescending.  Still, it IS light...

* CrunchBang.  I hated that.  It felt like Openbox mashed into Ubuntu with a hammer.

* UbuntuLite. Interesting.  A script that downloads packages and installs them on an Ubuntu mini cd.  Note that the 9.6 MB iso is really no better than CentOS's 7.7 MB version... they're both for network installs.  The cd boots and then installs everything else from the net.

---

### Post by jrusso2 on 2008-09-14
> **cardinals_fan said:**
> I'm at it again.  Every distro I use seems to have some deal-breaking fault.  Obviously, no distro will perfectly fit all these requirements, but whatever does the best job should be good enough.  Here's what I want:

* **Speed**.  This one is HUGE.  I care about RAM usage (I have plenty, but don't like to waste it) and overall responsiveness.

* **Minimalism**.  There are many possible ways to measure the minimalism of a distro.  The best I've found is iso size.  A small iso image can't contain much bloat.  Plus, I don't like waiting forever for a 700 MB iso to download.

* **Package management**.  This one is a bit awkward.  I don't need huge repos or fancy package managers.  All I want is a clean, easy way to install some basic packages.  I dislike Debian packaging - any Debian-based distro would have to be extraordinary in order to please me.

* **Hardware support**. I need an OS that supports the following:
- an **NVIDIA 6100** graphics card
- an **HP OfficeJet 7300** all-in-one printer
- a **Belkin F5D7050** wireless adapter, using rt73 chipset

* **Stability**.  I don't need five-year-old packages with enterprise-grade stability.  However, I like to stay a comfortable distance away from the bleeding edge.  If there's one thing I hate, it's when something that works fine is broken in an "upgrade".

* **Security**.  Security is a difficult term to define.  I expect a reasonable permissions policy and regular security updates.

* **Vanillaness**.  I realize that I'm asking a lot here.  This isn't required; it's just desired.  I prefer vanilla packages without a bunch of distro-specific patches.

* **Openness**.  No, I don't mean the source code.  I mean the developers.  Good projects listen to user input and don't snuff out bug reports out of denial (I'm looking at you, [Pardus]("http://bugs.pardus.org.tr/show_bug.cgi?id=7407")!).

**[COLOR="Blue"]Of course, I won't get all that.  I just need as much as is possible.[/COLOR]**  To speed up the process, I'll list some significant OSs that I've used, and what I dislike about them:

* Windows XP: Stable and with lots of software available, but permissions are handled awkwardly, there's no package management, and Microsoft handles updates poorly.

* Ubuntu and derivatives: For a while, I thought that Xubuntu might work for me.  Sure, it's bloated, but it worked pretty well.  Then I discovered some breakage in a number of packages I use frequently... and things went downhill fast.  It also uses Debian packages :(

* Slackware: One of my favorites.  It has great speed, packaging, vanillaness, stability, and just about everything else.  Unfortunately, it simply refuses to work with my printer.

* OpenSolaris: Almost great.  Almost.  The hefty resource usage and weak package management drag it down.

* Arch: I almost loved Arch.  It was fast, vanilla, custom... and broken.  Very, very broken.  The stability was ugly for me.

* Gentoo: No.  Just no.

* Vector: Light and nice, but truly ancient packages and lacking security updates worried me.

* Zenwalk: Buggy for me, and getting pretty bloated.

* Fedora: Bugs, and then more bugs.  Throw in a little bloat, and you've got a Fedora casserole!

* Mandriva: Bloated with creepy packaging

* OpenSUSE: Bloat and things that go bump in the night.  Maybe not.

I've used many others, but I think those are most of the big ones.

Glad to see you have finally come to realize Linux is the best desktop operating system.

From you description I would say SLackware comes the closest to meeting your needs.  If your printer works with other distros you should be able to get a driver for it to work with Slackware.  Search for the .ppd file for cups.

---

### Post by cardinals_fan on 2008-09-14
> **jrusso2 said:**
> Glad to see you have finally come to realize Linux is the best desktop operating system.

From you description I would say SLackware comes the closest to meeting your needs.  If your printer works with other distros you should be able to get a driver for it to work with Slackware.  Search for the .ppd file for cups.
I wouldn't be so sure ;)

I'm actually using XP at the moment.  We'll see what I settle on...

---

### Post by DR583V3 on 2008-09-14
How about Sidux?

---

### Post by afonic on 2008-09-14
> **cardinals_fan said:**
> Could I fix these things?  Sure.  However, when I don't have a relatively free weekend (like this one), I haven't got the time.  I need something ROCK-SOLID.  When I have to turn in an English essay the next day, and I've already spent most of the day at school / ski practice, I have no time to deal with a broken Abiword package.

I actually think I would like CentOS - but there's no way I'm downloading a DVD.  Maybe I should actually shell out a couple bucks to have it shipped up here to Alaska...

When you have to turn in an English essay next day, DO NOT UPDATE! Simple as that. Do your critical work and update any packages that may bring any degree of breakage next time.

CentOS is nice, it is rock solid. However it is not recommended for desktop use unless you are happy having the same version of your programs for 5 years.

---

### Post by Bart_D on 2008-09-14
> **cardinals_fan said:**
> ..* CrunchBang.  I hated that.  It felt like Openbox mashed into Ubuntu with a hammer.....

How about really start from scratch and do a Ubuntu Minimal-CD installation and add OpenBox as the window manager.  There's plenty of how-to's on doing that and you start with a completely empty desktop.  It'll fly......

---

### Post by cardinals_fan on 2008-09-14
Problem solved!  I'm using OpenSolaris.  The memory usage issue was really not a problem - ZFS uses almost all of my RAM, but releases it when I need it.

The OpenSolaris community is truly extraordinary.  This forum is great for chatting about various things, but I never had much luck getting technical help here.  The OpenSolaris forums/mailinglists are filled with very competent people willing to help explain things in detail.

---

### Post by kk0sse54 on 2008-09-14
> **cardinals_fan said:**
> Problem solved!  I'm using OpenSolaris.  The memory usage issue was really not a problem - ZFS uses almost all of my RAM, but releases it when I need it.

The OpenSolaris community is truly extraordinary.  This forum is great for chatting about various things, but I never had much luck getting technical help here.  The OpenSolaris forums/mailinglists are filled with very competent people willing to help explain things in detail.

How's the package management though?

---

### Post by cardinals_fan on 2008-09-14
> **C!oud said:**
> How's the package management though?
Poor, but I've got all the important stuff (Opera, OpenOffice 3, zsh, VLC) installed fine.

---

### Post by gjoellee on 2008-10-18
Ever tried PCLinuxOS? I that should fit you nicely! But the current version is PCLinuxOS 2007 and it was released like a year ago so its packages are not up to date. You should wait for PCLinuxOS 2008 comes out (most likely before 1st January 2009). 

PCLinuxOS is a very out of the box distro wich you can easily control using PCLinuxOS' own control center wich is quite powerful. It comes with stuff like Flash PLayer by default and has a pretty good community. 

It does not require much RAM to run (512mb recommended) and does not use much either. When a new version of PCLinuxOS releases I would say it is the most up do date distro by default you may get at that moment. PCLinuxOS does use APT package manager which is very good. The default package format is RPM.

It is totally worth a try!

---

### Post by MONODA on 2008-10-18
If things dont work out later on (and i know something will go wrong, it always does for me) I think you should try, frugalware, zenwalk and give opensuse another try. It is kind of slow, but in the end, almost everything works which is the important thing.

---

### Post by cardinals_fan on 2008-10-18
> **MONODA said:**
> If things dont work out later on (and i know something will go wrong, it always does for me) I think you should try, frugalware, zenwalk and give opensuse another try. It is kind of slow, but in the end, almost everything works which is the important thing.
Frugalware always interested me, but the idea of downloading so much to install so little doesn't appeal to me.  I've used Zenwalk extensively, and it's solid.  I always wanted to like openSUSE, but couldn't.  If they had a minimal CD, I'd give it a shot...

For now, I'm happy with Arch and Slackware.

EDIT: Regarding PCLinuxOS, I never got the hype.  I really don't care about having things like Flash and DVD playback out-of-the-box, and it didn't have too much else that stood out.

---

### Post by medic2000 on 2008-10-18
I love Arch very much but it broke my system again.(after an nvidia upgrade of course,the next time it will be wireless :)) I join the Arch is unstable community.

---

### Post by cardinals_fan on 2008-10-18
> **medic2000 said:**
> I love Arch very much but it broke my system again.(after an nvidia upgrade of course,the next time it will be wireless :)) I join the Arch is unstable community.
Hence the Arch/Slackware dual-boot.  The perfect combo of new/stable :)

---

### Post by Bucky Ball on 2008-10-18
You could build your own from the basic kernel. There are plenty of how to's. And whilst not a 'new' operating system, it will at least only contain the things you want and the bare essentials for your hardware, therefore might speed things up a bit and be less hungry than a standard 'off the shelf' install (which chucks a heap of stuff on that is irrelevant to your particular setup and circumstance). :)

---

### Post by kforum on 2008-10-19
i would challenge you to try sabayon, gentoo stability+ binary installer...
its a no miss situation,
im actually surprised no one mentioned it.

-but of course i really like gentoo, and just recommend sab. for those that dont want to compile, while retaining the gentoo reality. ;)

cheers.

---

### Post by medic2000 on 2008-10-19
> **cardinals_fan said:**
> Hence the Arch/Slackware dual-boot.  The perfect combo of new/stable :)

Yes it is worth to try :) Also debian has rock solid stable branch so it could be Arch/Debian too.

---

### Post by darrelljon on 2008-10-19
> **gjoellee said:**
> Ever tried PCLinuxOS? I that should fit you nicely! But the current version is PCLinuxOS 2007 and it was released like a year ago so its packages are not up to date. You should wait for PCLinuxOS 2008 comes out (most likely before 1st January 2009).I think you mean PCLinuxOS 2009.

---

### Post by MONODA on 2008-10-19
> For now, I'm happy with Arch and Slackware.
*Scrolls to top of page and reads C_F post*
*scratches head* :P
if things go wrong (and once again, I know they will :P) check out [http://linuxcentral.com/](http://linuxcentral.com/) They are pretty expensive (relatively) but they ship everywhere (I even got cds shipped to Lebanon :D:D:D:D:D) and have almost every distro.

---

### Post by MONODA on 2008-10-19
Now that I think about it, your situation is vey similar to mine. I cant seem to find a distro that fits me (I like simple and fast). I used arch until they started using kde4. I tried so many distros that I think my cd drive is going to die soon. I have a slow internet connect (50 kbps down) and a very small limit (2 gb down) and I live in lebanon so its hard to find places that will deliver cds here. Eventually I got an opensuse 11 dvd from linux central (I also got a slcakware and Knoppix) and installed that. I hated Zypp at first (even though it is soooooo much better than in 10.3) but eventually got used to it. I am using opensuse 11 now with kde. It has Novell's version of OOo which is great and I really like Yast now. I cant print to my network printer and all the bloat was annoying at first but it isnt too bad. I needed something that worked and needed it fast because school was about to start. I was able to contain myself and not compile my kernel again or do anything stupid like try and change the hdd filesystem and everything has been working great for about 2 months YAY!

---

### Post by cardinals_fan on 2008-10-19
> **medic2000 said:**
> Yes it is worth to try :) Also debian has rock solid stable branch so it could be Arch/Debian too.
I don't like Debian or its derivatives.
> **MONODA said:**
> *Scrolls to top of page and reads C_F post*
*scratches head* :P

I can be flexible on some things.  I fixed my problem with hplip and Slack, and Arch works fine when updates don't break it.  So, I can use the latest software on Arch and boot into Slackware if things break :)
> **MONODA said:**
> Now that I think about it, your situation is vey similar to mine. I cant seem to find a distro that fits me (I like simple and fast). I used arch until they started using kde4. I tried so many distros that I think my cd drive is going to die soon. I have a slow internet connect (50 kbps down) and a very small limit (2 gb down) and I live in lebanon so its hard to find places that will deliver cds here. Eventually I got an opensuse 11 dvd from linux central (I also got a slcakware and Knoppix) and installed that. I hated Zypp at first (even though it is soooooo much better than in 10.3) but eventually got used to it. I am using opensuse 11 now with kde. It has Novell's version of OOo which is great and I really like Yast now. I cant print to my network printer and all the bloat was annoying at first but it isnt too bad. I needed something that worked and needed it fast because school was about to start. I was able to contain myself and not compile my kernel again or do anything stupid like try and change the hdd filesystem and everything has been working great for about 2 months YAY!
My internet connection isn't that slow, but my CD burner is unreliable and I hate downloading 700 MBs of things I'll never use.

---

### Post by medic2000 on 2008-10-19
> **cardinals_fan said:**
> I don't like Debian or its derivatives.

But i like :D

---

### Post by cardinals_fan on 2008-10-19
> **medic2000 said:**
> But i like :D
Enjoy, just stay quarantined so honest Slackware users like myself don't get contaminated :D

---

### Post by medic2000 on 2008-10-20
> **cardinals_fan said:**
> Enjoy, just stay quarantined so honest Slackware users like myself don't get contaminated :D

I can not promise that :D

---

### Post by Arthur Archnix on 2008-10-21
I'm curious what your passionate dislike of debian package management is all about.

---

### Post by Antman on 2008-10-21
> **cardinals_fan said:**
> Problem solved!  I'm using OpenSolaris.  The memory usage issue was really not a problem - ZFS uses almost all of my RAM, but releases it when I need it.

The OpenSolaris community is truly extraordinary.  This forum is great for chatting about various things, but I never had much luck getting technical help here.  The OpenSolaris forums/mailinglists are filled with very competent people willing to help explain things in detail.
I see your using Arch/Slackware now. Your trip to OpenSolaris land didn't last long. :lolflag:
What made you change your mind again?

---

### Post by cardinals_fan on 2008-10-21
> **Arthur Archnix said:**
> I'm curious what your passionate dislike of debian package management is all about.
There are two main reasons:

1) This has nothing to do with Debian packages in and of themselves, but the Debian policy regarding package patching is in direct conflict with my opinions.  I believe that distro-specific software patches are idiotic, poorly reasoned, and downright wrong.  This is both because of security concerns and a desire to see software as it was written.

2) I haven't seen any package managers for Debian systems that work well for me.  Apt-get and Aptitude were both lacking in my experiences.
> **Antman said:**
> I see your using Arch/Slackware now. Your trip to OpenSolaris land didn't last long. :lolflag:
What made you change your mind again?
I like OpenSolaris, but it isn't quite there yet.  I couldn't get the package manager to update - I couldn't figure out how to make the CLI system work, and the GUI wanted to download 3 **GB** of packages.

---

### Post by Arthur Archnix on 2008-10-21
> **cardinals_fan said:**
> There are two main reasons:

1) This has nothing to do with Debian packages in and of themselves, but the Debian policy regarding package patching is in direct conflict with my opinions.  I believe that distro-specific software patches are idiotic, poorly reasoned, and downright wrong.  This is both because of security concerns and a desire to see software as it was written.

2) I haven't seen any package managers for Debian systems that work well for me.  Apt-get and Aptitude were both lacking in my experiences.



1. So you have to rule out Fedora, Red Hat, Suse, Ubuntu, Mint, Mepis, Sabayon, Slack, Gentoo... maybe even Arch. At a minimum Arch patches the kernel to be "distro specific". Basically, every distro does this. LFS doesn't, but that wouldn't have a package management system. My guess is Arch and Gentoo are closest to this "ideal" after that I'd say Slackware and then Debian are the "purest".

2. Lacking what? What feature did pacman, or yum have that aptitude doesn't? Or what it lacking in another way?

---

### Post by cardinals_fan on 2008-10-22
> **Arthur Archnix said:**
> 1. So you have to rule out Fedora, Red Hat, Suse, Ubuntu, Mint, Mepis, Sabayon, Slack, Gentoo... maybe even Arch. At a minimum Arch patches the kernel to be "distro specific". Basically, every distro does this. LFS doesn't, but that wouldn't have a package management system. My guess is Arch and Gentoo are closest to this "ideal" after that I'd say Slackware and then Debian are the "purest".

2. Lacking what? What feature did pacman, or yum have that aptitude doesn't? Or what it lacking in another way?
1. Slackware has a reputation for absolutely vanilla packages, and Arch is similar if a bit more relaxed.

2. I find the way apt-get/aptitude display information during installation confusing compared to the cleaner layouts in pacman, yum, tazpkg, and pisi, to name a few.

---

### Post by init1 on 2008-10-23
FreeDOS fits almost all of those, except maybe drivers :D

---

### Post by Cl0ud9 on 2008-10-23
If you want something small and fast try [CRUX]("http://crux.nu/").

---

### Post by kk0sse54 on 2008-10-23
> **Cl0ud9 said:**
> If you want something small and fast try [CRUX]("http://crux.nu/").

In my brief encounter with crux it was indeed blazing fast

---

### Post by cardinals_fan on 2008-10-23
> **Cl0ud9 said:**
> If you want something small and fast try [CRUX]("http://crux.nu/").
I've always been interested in CRUX.  The compiling scared me off (for now :P)

---

### Post by Sorivenul on 2008-10-23
> **cardinals_fan said:**
> I've always been interested in CRUX.  The compiling scared me off (for now :P)

In my experience, if you can build Gentoo you can deal with CRUX.  Indeed, if you can handle Arch, you should try CRUX as a good learning experience.  I could never use it day to day, so I don't suggest it for most people, but from my limited experience (and what I know of yours) you should at least try it.

---

### Post by cardinals_fan on 2008-10-26
> **Sorivenul said:**
> In my experience, if you can build Gentoo you can deal with CRUX.  Indeed, if you can handle Arch, you should try CRUX as a good learning experience.  I could never use it day to day, so I don't suggest it for most people, but from my limited experience (and what I know of yours) you should at least try it.
There's an important difference between "can" and "want to".  I **can** set up Gentoo, but I don't **want to**

I'll give CRUX a shot someday :)

---

### Post by init1 on 2008-10-26
> **cardinals_fan said:**
> I've always been interested in CRUX.  The compiling scared me off (for now :P)
Yeah, I started to install it from the CD, but I stopped when it started talking about how to compile the kernel...

---

