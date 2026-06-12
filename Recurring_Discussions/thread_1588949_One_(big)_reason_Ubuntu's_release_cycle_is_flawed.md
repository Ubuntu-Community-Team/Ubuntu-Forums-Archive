---
title: "One (big) reason Ubuntu's release cycle is flawed"
date: 2010-10-05
forum: Recurring Discussions
---

### Post by LifeTheHound on 2010-10-05
The idea is simple in words, requires a slight shift in priorities, but is nonetheless profoundly relevant to the realization of desktop Linux for the mainstream. I present a somewhat novel but circumstantially compelling proposal for a revamped Ubuntu release cycle that should prove especially attractive to one of Ubuntu's most highly sought-after demographics -- the "mainstream" computer users: 
*Stable base + rolling stable user software + **optional** system backports (kernel, modules, etc as required for new/unsupported hardware).*
Before you hit that reply button with "been there, done that", "impossible", or another misunderstanding, consider at least the very first few points:
[LIST]
[*] Although this proposal gives some personal examples, I am advocating for my proposal on behalf of everyone, but with **heavy** emphasis on "mainstream" computer users, to be defined below. 
[*] I define "mainstream" user as the average computer user who knows little to nothing about Linux and Ubuntu, but becomes willing to try Ubuntu. They may have purchased a computer with Ubuntu (from Dell, eBay, or a friend), or had it completely set up for them by a techie/friend/enthusiast/vendor. It can also apply (but a bit more loosely) to individuals unfamiliar with linux but savvy enough to install it themselves from a CD without encountering [m]any problems. 
[*] This is NOT a proposal to mimic any "rolling" distro (Arch, Debian testing, etc). This is NOT a proposal for an "over-stable" distro (Debian stable). This is NOT advocating, glorifying, or supporting Windows, BSD, or any other operating system mentioned by way of comparison. 
[*] This is a post *for* Ubuntu, the developers and community (including tinkerers), *on behalf of* Ubuntu and mainstream computer users as previously defined (and also on behalf of developers and tinkerers as I outline later, but to a much lesser extent).
[*] Although this proposal espouses certain concepts to some extent loosely resembling the *release system* of Windows, Mac, and PC-BSD, it in no way advocates for a similar implementation for Ubuntu on either a technical or user level, but simply that some *concepts* used by other operating systems can prove immensely beneficial to Ubuntu as well, without sacrificing much of anything as explained below. 
[*] I chose Ubuntu for the subject of my proposal because it enjoys the greatest level of user-friendliness, community, development drive, and completeness in terms of a stand-in operating system alternative/replacement for the "mainstream" defined previously. That is, it currently comes the closest. 
[*] Based on very extensive personal involvement with Ubuntu installations and maintenance for dozens of mainstream computer users, I strongly hold (and will attempt to prove and certainly discuss) that this proposal makes great strides toward significantly alleviating many remaining barriers to this end.
[*] I elucidate the surprising and unconventional notion that many current problems with Ubuntu are actually inherited from, exacerbated, related to, or even caused by Ubuntu's biannual release cycle -- an indirect correlation that is NOT altogether-self evident.
[*] By the same token, however, I do NOT attempt to blame all of Ubuntu's problems on the release cycle. The vast majority of its current issues have proximate causes that have nothing at all to do with the release cycle -- but even for some of these, their ultimate manifestations arise in no small part as an indirect result of these very cycles.
[*] The proposed system will require greater overall manpower to maintain any given release. However, I contend that this manpower should be reallocated from the current "from scratch"-type biannual release (biannual Debian unstable import) in favor of redistributing this existing manpower to maintaining a long-term release, but without the evolutionary drawbacks expected from an LTS-only ("Debian stable"-type) approach under the current biannual system. 
[*] Under the proposed system, testing for each long-term base release is expected to be somewhat (if only "slightly") more productive, especially after a release is made (which is when the most people actually use it). This will not only promote greater initial stability due to fewer interim releases and longer developer and tester focus on each, but will also prominently feature increased stability over time in the form of point releases (much like the current LTS). This will allow for more developer effort, testing, and resource allocation within each single release, which may/will increase the overall quality of that release and will certainly free up manpower for the purposes of maintaining the proposed system.
[/LIST]

That out of the way, here is the proposal in earnest. I may add on or rephrase some segments as input is received and the proposal progressively fleshed out. 

[list]
[*] "User software" (as distinct from "system software") is defined as user-space applications such as GIMP, OpenOffice, Firefox, and many installable applications that do not directly interface with the hardware. The integral underlying components which comprise the functional framework of the system constitute "System software" by way of contrast. 
[*] Each of the three core points below is subject to the conditions and details expounded in the corresponding "point #" that follows. 
[*] **Core point #1**: That the base of an Ubuntu release remain stable in terms of system software, that this base be supported long term without biannual releases. 
[*] **Core point #2**: That user software be kept up to date and supplied on an adaptive "rolling" basis. This may be rudimentarily construed as a very heavy emphasis on the "backports" (a misleading term in this case) of said user software. In other words, within any given release, the latest stable versions of user software should be made available in a timely manner as stable feature releases are released upstream. 
[*] **Core point #3**: That hardware compatibility be maintained and critical hardware-related bugs fixed at the user's discretion (or automatically in critical cases, subject to the competence of the hardware detection); and that such hardware support is provided via *optional* "system software" backports as made available by similar technical means as they are today in LTS releases, but with the additional comprehensiveness derived from the slower release frequency and the increased manpower resultant therefrom. 
[*] Point #1A: This base can be technically similar to a well-tested Ubuntu LTS- or Debian-style base as evidenced in existing non-rolling distributions. This is similar to what Ubuntu already does, especially in regards to LTS releases. Benefits of a solid base are effectively self-evident, and the comparative (though still limited) popular success of distributions is ample testament to this reality. 
[*] Point #1B (Core release cycle): The next distribution of Ubuntu, replete with an updated stable base and attendant long term support, might viably correspond to the earliest of the following options: a certain set maximum support time, similar to the current LTS; "polished, unequivocal readiness" of the next stable base, similar to Debian; or, most novel but arguably most practical for such a proposal, that the new base simply be released once it becomes unfeasible or sufficiently impractical to warrant continued backports. This latter case occurs most obviously when most new drivers and modules are built solely for a kernel and xorg that both recently underwent sweeping architectural changes in critical areas for which backporting is impossible to an older system. This is due to second-order core interdependency webs (e.g. kernel removes EXA acceleration + new xorg no longer supports it + and all new drivers are built on UXA/Gallium3D + new libs now required by new software to take advantage of new mesa functions + new hardware came out that only uses UXA/G3D). For smaller interdepency webs, it's still a tenable proposition, of course (I've run xorg-edgers with bleeding edge kernel, intel driver, and xorg on an older Ubuntu system). 
[*] Point #2A (Implementation): Use majority of manpower freed up from biannual releases and repository space freed up from supporting 7+ Ubuntu versions concurrently. Create new repositories/software sources to manage software versions analogous to current system: "Software-Testing" repo houses point releases (e.g. KDE 4.6.X, LibreOffice 3.3.x) before they're pushed to the default "software-stable" repo; "Software-Upstream" houses latest stable upstream release (similar to "backports" but actually updated and exclusive to "user software"); provided enough time, even a "software-beta" repository can be set up akin to OpenSuse's myriad "testing" repositories for development/beta software, though this particular repo certainly isn't required for this proposal to be effective. Few packages truly require updated shared libs for a long time (most of the time such nominal "requirements" are an artifact of an updated build framework) and can be compiled perfectly even within the existing 'backport' guidelines, only in a more automated fashion. Select problematic software can simply be compiled with static libraries or delivered with coexisting updated ones, in which case the update manager should be made aware of the coexisting lib versions and deliver updates for both (similar to managing two xulrunner.so libraries for firefox-2 and firefox-3 simultaneously in Hardy). If the static build option is espoused instead, the build system itself should automatically poll the all linked/internal libs for security updates, rebuild all affected packages with any updated static libs, and push the package as a whole (or as a delta file) to the update-manager. Finally, to polish off the implementation, a simple UI for updating (or downgrading!) only select packages between these official repositories would complete this ideal "parallel" repository setup for the mainstream user and anyone else. This way, if a user regrets an upgrade decision (for single or multiple programs/packages), the option to downgrade to the version in another repo should exist graphically (all the way down to a "Software-Stable", the default). That is, if Joe doesn't like the new version of a relatively standalone program after enabling "software-upstream", he can open the software center (or the simple UI) and easily roll it back. 
[*] Point #2B (Benefits): [list]
[*] User discretion can be taken into account if a program update is undesirable for whatever reason (as implemented).
[*] Manpower can be spent automatically polling for new versions of user software rather than letting software stagnate (with any existing bugs or deficiencies) or sporadically building them "on request" as the current backport guidelines specify -- this change means the "mainstream" will actually receive these updates. 
[*] Many examples of upstream software contain bug-fixes and feature enhancements that are critical for continued use of the software in the modern world (e.g. inter-compatibility, OpenOffice docx form support, GIMP's bezier curve model, new multimedia formats, fixed a/v decoders/players, wine feature/bugfix releases) 
[*] Ubuntu's acclaimed software update system will now also be more competitive with other operating systems in which software "auto-updates" to the latest versions, while retaining all the benefits of Ubuntu's software management.  
[*] Better solution than PPA's for interim software updates: [list]
[*] The "mainstream" may or may not be comfortable with PPA's in the first place, or fully understand the risks (I learned the hard way). 
[*] Retain Ubuntu's community testing, support, and patches. 
[*] PPA's are notoriously buggy, often ill-maintained, may be vulnerable to security holes, may break future official updates, often aren't built with Ubuntu patches, optimizations, and testing, and may be incomplete (e.g. Lucid LibreOffice PPA doesn't contain KDE integration, Firefox 'nightly' pull is unecessary DE-specific dependencies and incorrect branding/integration, vlc isn't compiled with the same optimizations as stock, making it a bit slower, etc). 
[*] PPA's may break distribution upgrades (upgrading to a distro featuring VLC 1.1.7 when your PPA is on 1.1.8 can mean app breakage, and xorg-edgers to a new distro's Xorg can mean distro breakage) 
[*] Fully supported upgrade path. Users needn't find and re-enable each PPA again (which many 'mainstream' users don't/won't/can't figure out in the first place if the system came with PPA's enabled by manufacturer/techie/other) or worry about discovering that a PPA for the upgraded distro doesn't exist due to distro changes (which could make a user lose essential functionality after the upgrade). [/list]
[*] Creates uniform environment for reporting and fixing bugs. [list]
[*] One distro with only a few 'official' versions of software to support means much less "debugging noise" caused by what distro/version was used. 
[*] More people using the same base and software version equates to more reproducibility for users and devs alike.
[*] Because one stable distro updates to the latest stable upstream versions of user software, there's much less redundancy in bug reports, and developers would have much more specific and up-to-date information, with the additional end result of software being fixed more quickly easily
[*] Users don't have to wait until a new distro to report bugs with the built-in bug reporter tool. This means Ubuntu developers and trackers won't suddenly be inundated with repeated 'user software' bugs whenever they're focusing on making a new Ubuntu base (or worse, developers being forced to deal with all the bug reports that flock in immediately after every release, which require further sorting into 'upstream software bug', 'ubuntu bug', 'default configuration/environment bug', 'bug in software only relevant to use in Ubuntu'). Software will be better maintained before and after release, allowing developers to focus on the next stable base rather than wading through noise. [/list][/list] 
[*] Point 3A: The optional/critical-only "system software" backports can be provided as backported wifi/sound modules, entire kernels, etc as they are today with Lucid LTS, but enjoying all the benefits of concerted developer support/attention. Updated Xorg components can be provided similar to those in the xorg-updates PPA, but able to reap the additional benefits described for "user software" in point #2B above. In terms of automating this process, the hardware detection wizard can be improved to poll the hardware and offer to safely (and reversibly!) install just the backported components necessary to support a specific piece of new hardware for which there is known issue. The polling can take place upon detection of new hardware or at install time. The setup could be quite similar to the "proprietary driver" manager with a hardware 'definitions' file that updates along with the rest of system. This program can perform recovery if an installation fails, in addition to allowing the user to backtrack if an installation fails or doesn't work as well (a sort of friendly automated 'apt-get remove linux-backports-modules-XX') simply by unchecking the appropriate backport in the GUI. 
[*] Point 3B ("pseudo-rolling" hardware support): Additionally, these up-to-date "system software" backports can be included with the default CD and LTS-style point releases such that a completely new computer or completely new hardware can instantly be detected, the proper required backports loaded from the CD, and the computer set up without the need for any additional download or setup. Distribution point releases can stand in for biannual releases in supporting the latest hardware from the getgo via this backports-on-CD "pseudo-rolling" method -- just as an up-to-date system of the very first (point 0') release would offer the same hardware detection and optional "system software" backports. 
[*] Point 3C (Benefits to this hardware approach): [list]
[*] The "mainstream" is not presented with a potentially problematic distribution upgrade (settings/proprietary-driver/PPA reset, or worst case, breakage). My extensive experience with dozens of "mainstream" Ubuntu converts, in addition to polls on these forums, indicate that the upgrade process is still significantly far from perfect, and there is a possibility of encountering problems with each distro upgrade -- with an 80% total magnified possibility of encountering difficulty after 4 upgrades -- that is, in just 2 years -- assuming a 2/3 chance each and every upgrade goes perfectly. Many users think it's just a standard system update and are unprepared for the consequences, whatever they might be, not to mention incapable of fixing what you or I might consider the simplest and most forgettable glitch. Of course, downgrading after a distro upgrade is virtually impossible at this point without use of commandlines and significant expertise. 
[*] Users won't be forced to resort to PPA's and/or entire distribution upgrades to get helpful (and sometimes critical) software updates; see above under Point #2b. 
[*] Allows the mainstream to avoid *upgrade inconvenience/trouble* (for the life of the machine in many cases), including the following scenarios: [list]
[*] Package breakage might occur, drivers not function properly, or the system may not boot (extreme case)
[*] Some functionality might lose support after an upgrade: desktop effects not work, accelerated video not work
[*] Some hardware is entirely unsupported, but the update manager (and of course the "mainstream user" who probably trusts his system/update manager!) has no way of knowing this (e.g. Poulsbo chipsets, some webcams, sound stops working on hp laptops)
[*] Custom configuration, settings, and workarounds from both "mainstream" AND "seasoned" users are lost (e.g. added line to /etc/hosts to fix LibreOffice startup lag, line added to /etc/modprobe.d/alsa-base.conf to fix speakers playing on headphone insertion, fix for the hardware wifi notifier blinking on HP laptops [finally fixed in Lucid but broke again in Maverick&Natty], fix Flash audio in Firefox under Kubuntu or Flash player video performance again, fix mic problem in Google chat in the browser, etc). These are tiny breakages not noticed at first by anyone, but only become apparent in time with use -- and are dismissed in seconds by tinkerers and the savvy/dedicated/experienced. In terms of the mainstream, any tweaks these advanced users/distributors/techies/vendors painstakingly set up within a system would vanish, and they'd receive an influx of disillusioned complaints and demands for support after an upgrade that seemed at the time to have been "flawless" but again shows whatever flaws or misbehaviors that had been meticulously controlled for in the first place. 
[*] A sudden, near-gigabyte download of data and an entire hour (or a lot more on slower connection) of both the download and installation process every six months, in addition to the bugfix releases that swarm in for the first few weeks after release. [/list][/list]
[*] **Core Benefit**: Provides all of the benefits stated above and more, and avoids "Mainstream" discontent with all of the above issues related to the current release cycle (dated software until potentially risky upgrade, frequent large upgrades, insufficiently tested releases/software/PPA's, fluctuating levels of hardware support over time, bugs that come and go -- the coming part, specifically, is the major qualm after an upgrade, reset user/installer/vendor settings).
[/list]
There you have it. A proposal for a release cycle that may well solve problems the tinkerer might never have cared about (or even remembered exist), all of which nevertheless cripple the usability of Ubuntu as a serious alternative to mainstream computer users with accordingly mainstream computers and levels of computer aptitude. Ubuntu is doing a fantastic job with everything from its interface to its program selection to its hardware support (however finicky or rapidly fluctuating that support may be from one release to the next). Perhaps a good number of the remaining hurdles to large-scale adoption can be resolved, no matter how indirectly, from a careful reevaluation of the release cycle in light of the very same "mainstream" interests. With increased quality and stability may also come a reduction in the various modes of crippling fragmentation that conspire to divide users, developers, and interest groups even within the same operating system -- an entity known simply to the mainstream as Ubuntu.

(Side note: there are many, many other arguments that have been made for longer release cycles. For instance, longer release cycles can also mean better proprietary driver support, as companies are more willing to invest the time and money into making a driver that will last longer than a few months; or from another perspective, companies already involved could potentially invest more into stabilization than rushing to support whatever new kernel and Xserver would surely redefine the playing field in those mere few months. There have also been arguments for a shorter release cycle along such lines as "synchronization with free software trends" and "increased pace of core development and creativity", but whatever conveniences such reasons would at first seem to afford such a rapid release cycle appear to be dwarfed by quality and usability concerns by the mainstream. But I digress.)

---

### Post by endotherm on 2010-10-05
no, not really, but no time to expound. ultimately the op is only worried about his own situation.

---

### Post by drs305 on 2010-10-05
Thread moved to Recurring Discussions since it isn't really a request for support.

---

### Post by LifeTheHound on 2010-10-05
> **endotherm said:**
> no, not really, but no time to expound. ultimately the op is only worried about his own situation.

Well it hurts me, it hurts friends, it hurts everyone. Hardware support is one of the biggest qualms with desktop linux, and this is partly why-- once you get your hardware working, you have to switch distros and start over. At least if you want your software to keep up and stay relevant. 

A lot of people I know dropped linux in general because it was "too much tweaking for too many bugs across too many distros" and it was just too "high maintenence" to keep distro hopping. 

Ad hominem: attacking the person (op) instead of the problem.

---

### Post by TBABill on 2010-10-05
I get it and I see your point. So long as the kernel can support the dependency changes required for the newer software, why not update packages in the repos for applications along with the updated packages for newer versions of Ubuntu. No reason why 9.04 shouldn't have the same version of OpenOffice if it is a safe assumption that the rest of the distro can support that newer version. 

That's where I believe it could become labor intensive on the packagers. They would be facing package issues on every version of Ubuntu currently supported, which could become an exponential increase in workload. I do not know that for a fact and I wonder if that is the reason previous versions do not keep the latest and greatest of some apps....so the packagers can focus on the current distro versions with the available manpower and hours they have?

Interesting perspective and insight went into that post and I agree it has great merit if it is something that can be supported reasonably. Being forced to tweak hardware on every upgrade so you have a few of those apps you require would be a pain. I have an HP Touchsmart and every install I have to change its sound settings manually in its modprobe file. Not a major ordeal, but not something I want to do regularly if newer app versions were available in the currently installed version.

---

### Post by Dragynn on 2010-10-05
Well the gods and the mods know, that i'm one to complain, but in all fairness, the real problem with Ubuntu and most linux distros, is that nobody builds computers specifically for linux, they build them for Windoze.

Yeah I know about Dell, I don't believe for a second that Dell actually built their Ubuntu offerings from scratch design with linux in mind, Dell is nothing more than a parts assembly house manned by monkeys, they don't design squat.

And yes, I know about Lenovo...pfffft. And HP supposedly has big plans...meh...believe it when I see it, and I still won't be excited, last thing I ever want is an OEM computer ate up with garbage OEM progs and built-in spyware.

It's amazing in the first place that linux works on any hardware, not because it's not a great system, but because here in merchant-cartel-controlled A-murr-ka it's usually SOP to systematically destroy anyone or anything that's not out to make a buck.

So the fact that linux ever works at all on consumer desktops and laptops, is quite the testament to LT, and to all the programmers and developers that have ever labored on it's behalf.

---

### Post by MooPi on 2010-10-05
> **LifeTheHound said:**
> Well it hurts me, it hurts friends, it hurts everyone. Hardware support is one of the biggest qualms with desktop linux, and this is partly why-- once you get your hardware working, you have to switch distros and start over. At least if you want your software to keep up and stay relevant. 

A lot of people I know dropped linux in general because it was "too much tweaking for too many bugs across too many distros" and it was just too "high maintenence" to keep distro hopping. 

Ad hominem: attacking the person (op) instead of the problem.

Why the need to update a machine that is working perfectly. I have 9.04 system that will stay that way because it is rock solid. SOLID. Yeah it's fun to tweak a new box but I always need something to depend on

---

### Post by uRock on 2010-10-05
I think Canonical's current direction is great. The software on any release can be upgraded with a little work. Expecting Canonical to upgrade the packaging for every supported release along with all of said program's dependencies is just ridiculous.

---

### Post by Tibuda on 2010-10-05
> **endotherm said:**
> no, not really, but no time to expound. ultimately the op is only worried about his own situation.
is that wrong?


> **uRock said:**
> I think Canonical's current direction is great. The software on any release can be upgraded with a little work. Expecting Canonical to upgrade the packaging for every supported release along with all of said program's dependencies is just ridiculous.
lol, canonical already does it.

---

### Post by uRock on 2010-10-05
> **Tibuda said:**
> lol, canonical already does it.
With some apps, but not all. I was happy to see FF get upgraded from 3.0 in Jaunty.

---

### Post by Tibuda on 2010-10-05
> **uRock said:**
> With some apps, but not all. I was happy to see FF get upgraded from 3.0 in Jaunty.

it is with almost every app in the testing branch

---

### Post by uRock on 2010-10-05
> **Tibuda said:**
> it is with almost every app in the testing branch
We are on different pages. I know they use the newest possible applications in the release.

You can't get Thunderbird 3.1.3/3.1.4 in the 8.04 repos. Last time I booted my Jaunty, they still had Thunderbird 2.0. I am not complaining. I have no problem with installing from source when I can.

uRock:)

---

### Post by LifeTheHound on 2010-10-06
> **TBABill said:**
> That's where I believe it could become labor intensive on the packagers. They would be facing package issues on every version of Ubuntu currently supported, which could become an exponential increase in workload.

> Expecting Canonical to upgrade the packaging for every supported release along with all of said program's dependencies is just ridiculous. 
Canonical is maintaining 5 releases, complete with full repos, independently and simultaneously. Hardy, Jaunty, Karmic, Lucid, Maverick. That's 5 times the server space and the work. That's why this is part of the *problem*, not the solution. This development/release cycle wastes manpower (and machine power). I'm making the case that releases should (for this and the reasons in Post #1) be much less frequent. An LTS every 2 or 3 years makes all of these things practical--even more practical than they are now, and much more attractive to users and businesses alike with the power of a stable base and rolling software on top. New hardware in the interim can be supported by an official kernel or driver PPA (in-place kernel upgrades or driver swap-outs already exist and have proven merit). 

> Why the need to update a machine that is working perfectly. I have 9.04 system that will stay that way because it is rock solid. SOLID. Yeah it's fun to tweak a new box but I always need something to depend on 
Answered in the Q and A in first post. Fully agreed that dependability is king, and that's precisely what is lacking in the current model. So you ask: why not stick with an old distro (under the current release system)? Again, in sum, the user software atop the stable base becomes obsolete, irrelevant, and often completely useless over time--sometimes a short time. Take your 9.04 system as an example. Its version of OpenOffice is obsolete and doesn't work for college students (me) needing support of new Office features (table features, excel features), and its FF was just barely rescued from obscurity (3.0 is out-of-support on many sites already). Coupled with the horrible KDE version in its repo and its wacky media player versions which don't support some major new media formats (to say nothing of the optimizations), etc. Having up-to-date software in a stable environment is the pinnacle of any modern OS. Having full HW support (stable) and the latest user programs is simply keeping up and being practical. It's not even a concern in Windows and Mac, because updating to the latest and greatest is a breeze and often automatic. Needlessly swapping kernels and drivers and xorg and audio/video/hal frameworks every 6 months to get the much-needed user software? Not too smart or practical. You're lucky you managed to find the perfectly stable system. Now good luck using the software to be productive 6 months from now. ;) "Doesn't play my media, render my websites, or open my documents correctly? Uh oh." Back to square one, the reason for my post. *[edit]To top it off, 9.04 will actually be completely unsupported--even for critical security vulnerabilities and bugfixes--in a mere 17 days as of this post. *

> it is with almost every app in the testing branch
Only dot releases, only some software, only rarely, and never for very long. After the next distro 6 months later, good luck. 

> The software on any release can be upgraded with a little work. 
> I have no problem with installing from source when I can.
These are not arguments for the mainstream or for a modern operating system. Essentially, you know all about install directories, dependencies, scripts, symlinks, etc and like tweaking. That's wonderful, and linux allows for nearly limitless tweaking. But a system that requires all of this and continues to need it just to stay relevant? Not so nice. See post #1. Which comes back to this: 
> the real problem with Ubuntu and most linux distros, is that nobody builds computers specifically for linux
Well, that's one common take. But here are a few novel reasons:
Consumer side (supported by my and many friends' experiences and countless recurring threads on this forum): have to keep upgrading and tweaking to get it working (or completely failing to upgrade like with Poulsbo, etc). Need to risk a perfectly working base just for new software is quite the bummer for many. I think the first post highlighted this pretty well. 
OEM/builder (supported by discussions in lkml and irc): With vendor's offerings becoming obsolete every 6 months, who could possibly afford to provide recurring large-scale proprietary driver support in the "country driven by money?" It's hard enough for users just to get these installed/tweaked/set-up with every 6 month release; just imagine the pain felt by 3rd parties such as Adobe (video accel), Intel (Poulsbo and main), etc. Most have given up because the rug gets pulled out from under them every few months. That and of course oodles of corporate pressure, but that's a whole separate discussion. ;)

---

### Post by NotTheMessiah on 2010-10-06
> **LifeTheHound said:**
> 
A lot of people I know dropped linux in general because it was "too much tweaking for too many bugs across too many distros" and it was just too "high maintenence" to keep distro hopping. 



I completely agree with that. It's fun at the start when you are learning new things, tinkering and experimenting but it gets tiring and time-consuming very fast. You simply run out of steam; we have less and less free time & we need something that you can just set-and-forget(e.g windows 7).

---

### Post by Dustin2128 on 2010-10-06
> **Dragynn said:**
> Well the gods and the mods know, that i'm one to complain, but in all fairness, the real problem with Ubuntu and most linux distros, is that nobody builds computers specifically for linux, they build them for Windoze.

Yeah I know about Dell, I don't believe for a second that Dell actually built their Ubuntu offerings from scratch design with linux in mind, Dell is nothing more than a parts assembly house manned by monkeys, they don't design squat.

And yes, I know about Lenovo...pfffft. And HP supposedly has big plans...meh...believe it when I see it, and I still won't be excited, last thing I ever want is an OEM computer ate up with garbage OEM progs and built-in spyware.

It's amazing in the first place that linux works on any hardware, not because it's not a great system, but because here in merchant-cartel-controlled A-murr-ka it's usually SOP to systematically destroy anyone or anything that's not out to make a buck.

So the fact that linux ever works at all on consumer desktops and laptops, is quite the testament to LT, and to all the programmers and developers that have ever labored on it's behalf.
OEMs aren't really who we need to cooperate with us, its the actual parts makers, like AMD and nVidia. While I do not seek to discredit linux devs, many hardware manufactures *do *make linux drivers themselves, and support us in other ways. nVidia, AMD, and Intel to name a few. There aren't that many hurdles in hardware support left to overcome, its mostly down to AMD (ATI) graphics cards and wireless drivers, both of which are getting much better all the time. Basically it doesn't matter if HP even knows the linux community exists as long as the makers of the motherboards, GPUs, CPUs (etc) that HP puts their computers together with support linux, which most of the time nowadays, they do.

In conclusion, we're getting to the point where computers don't have to be custom built, or built a certain way to run linux well. In fact, the ubuntu release current on vista launch day (gusty I think?) arguably had better hardware support than windows vista :).

If the above post is totally incoherent, please excuse me for lack of sleep.

---

### Post by beew on 2010-10-06
I fully agree with the OP, can't put it better myself. It is a very bad idea to insist on tying software upgarde to hardware upgrade. Another problem about frequent releases is that old bugs barely got fixed and new ones appear because the dev simply have not enough time to get the feed backs they need and work on the problems while the pressure of testing and packaging for the next release is looming.

I truely cannot see the point of such frequent rate of releases. Just as you have tweaked everything to perfection for your Lucid box the softwares already starting to get stale as much attention is now going to be on  Maverick.

While we keep saying that Linux is so stable this is not true if you have to take the release cycle into account. It becomes extremely unstable if you need to upgrade the whole OS just so that you can get up to date tools (softwares) for your work.

LifeTheHound makes a very good point, if there is a much longer release cycle the work to keep software "rolling" would become less of a problem for the packager.

---

### Post by beew on 2010-10-06
> **uRock said:**
> 
You can't get Thunderbird 3.1.3/3.1.4 in the 8.04 repos. Last time I booted my Jaunty, they still had Thunderbird 2.0. I am not complaining. I have no problem with installing from source when I can.

uRock:)

If you have to install from source just so that you don't have to work with softwares that should be in  the mesuem then there is a something wrong with the picture. It compeletly negates the point of Ubuntu's software managing system (apt, Synaptic, repos etc) which is often used as one of the greatest selling point for Ubuntu over windows to newbies ("you don't need to scourge the net for software, just fire up Synaptic and you have a whole world of geat free softwares to choose from with all the dependecies automatically taken care of" etc... we all heard that before, and to a great extent it is true, the only problem is that the softwares may be very old)

---

### Post by randomizer101 on 2010-10-06
I believe Linux Mint uses a hybrid philosophy, only tained by the fact that the applications are updated only when they are for the corresponding Ubuntu release. Mint's own update manager avoids installing kernel and libc updates (among others) by default purely because they can break things.

---

### Post by mikewhatever on 2010-10-06
I've read through the thread and started thinking. "It's not the first time these questions are raised on the ubuntuforums.org. What do people actually want to achieve by posting them here? Do they think Ubuntu users around the world would travel to London and storm Canonical offices demanding changes? Probably not. Do they think Ubuntu devs might visit the forums all at once, see these threads and decide to make a change? Unlikely, but I don't know. Is there any reason at all, other then nonconstructive criticism and being moved to the recurring section? Surely, if these guys really wanted to make Ubuntu software more current, they'd be discussing things [were the decisions are made]("https://lists.ubuntu.com/archives/ubuntu-devel/2010-July/031025.html") or just packaging more recent software. What are the merits of posting rants on forums? Can somebody explain?
...and why is it that Window7 always creeps up into these rants? Should anyone here care that it works for you? I mean, sure, and I am happy it does, but why waist readers' time by prising something that has 3 million Google hits for 'Windows7 crashes' on the Ubuntu forums?

---

### Post by gradinaruvasile on 2010-10-06
There are other Lnux distros that are rolling releases - Linux Mint for example is said to be quite nice. Laso for the more technical there is ArchLinux.
Or Debian Testing (i use it and its great, i had no breakage with it for almost a year).
Ubuntu is not the only distro out there you know (if you know your way around it in the terminal, you can use any Debian derivative)...

And about the criticism: i use Debian for some of the reasons the OP mentioned. And more reasons that have to do with the decisions that were made up there.

BTW Windows 7 is here because Windows is a de facto standard in computing and naturally everyone relates to the latest and greatest of its offerings in terms of hardware and software compatibility.
Personally i see Vista/7 a bloated thing that introduces more and more abstraction layers upon the hardware making stuff that work more easy and stuff that doesnt work harder (ok, maybe not harder but it isnt easier than XP either) to manage. And, collaterally, produces more computer-ignorant users.

---

### Post by uRock on 2010-10-06
> **beew said:**
> If you have to install from source just so that you don't have to work with softwares that should be in  the mesuem then there is a something wrong with the picture. It compeletly negates the point of Ubuntu's software managing system (apt, Synaptic, repos etc) which is often used as one of the greatest selling point for Ubuntu over windows to newbies ("you don't need to scourge the net for software, just fire up Synaptic and you have a whole world of geat free softwares to choose from with all the dependecies automatically taken care of" etc... we all heard that before, and to a great extent it is true, the only problem is that the softwares may be very old)

I don't think the apps in the repos are all that out of date. Thunderbird, VirtualBox and PacketTracer are the only programs I have compiled. Everything else works fine.

---

### Post by mamamia88 on 2010-10-06
my browser is the only real software i must have up to date and i can easily enable a ppa for firefox.  everything else as long as it does it's task I don't really care if they release a few minor revisions and if i really do care there is usually a ppa.

---

### Post by psusi on 2010-10-06
You can't have it both ways.  You can't have an old, tested, stable system, AND the latest and greatest.

This discussion amounts to nothing more than a complaint that one or two specific packages that you want a more up to date version of have not been backported.  Maybe they could put more effort into backports.  Maybe you should go donate some money and suggest they hire another developer to work on that.

Ohh, look... the latest versions of firefox and OO.o HAVE been backported to the last LTS.

---

### Post by mamamia88 on 2010-10-06
> **psusi said:**
> You can't have it both ways.  You can't have an old, tested, stable system, AND the latest and greatest.

This discussion amounts to nothing more than a complaint that one or two specific packages that you want a more up to date version of have not been backported.  Maybe they could put more effort into backports.  Maybe you should go donate some money and suggest they hire another developer to work on that.

Ohh, look... the latest versions of firefox and OO.o HAVE been backported to the last LTS.

why not?  why not provide a stable base os and let the user chose what applications to update?  why can't the updated software be unstable while the underlying system remains just as stable?  If i get a new Firefox version and Firefox starts crashing i simply revert back to older Firefox or use a different browser.  so why can't we have most recent versions of applications without compromising the stability of the underlying system?

---

### Post by beew on 2010-10-06
> **psusi said:**
> You can't have it both ways.  You can't have an old, tested, stable system, AND the latest and greatest.



And how is it a stable system if you are expected to upgrade the OS every 6 months with possibly lots of breakage?

Did you even read the OP or are you just spouting the party line?

---

### Post by t.rei on 2010-10-06
Well, considering 10.04 is an LTS... you can go from LTS to LTS. Thats two years of stable system. And a good chance of getting a smooth install on the next release, because - lets admit it - dist-upgrade have gone a looooong way during the past 10 years. 

If you need the newest version of any software on said system... for whatever reason: theres usually a backport or a ppa available.

I'm kindof happy with the way things just work currently. The only thing I'm really missing is a proper, free groupware-solution-server that plays well with evolution AND kontact AND outlook AND shares/usermanagement on windows and linux. XD

---

### Post by tgm4883 on 2010-10-06
> **beew said:**
> And how is it a stable system if you are expected to upgrade the OS every 6 months with possibly lots of breakage?

Did you even read the OP or are you just spouting the party line?

Speaking of not reading and spouting your party line. You aren't expected to upgrade the OS every 6 months. At the least it's 18 months (thats how long regular releases are supported for). At the most it's 3 years (that's how long LTS desktop releases are supported for. 5 years for server LTS)

---

### Post by beew on 2010-10-06
> **tgm4883 said:**
> Speaking of not reading and spouting your party line. You aren't expected to upgrade the OS every 6 months. At the least it's 18 months (thats how long regular releases are supported for). At the most it's 3 years (that's how long LTS desktop releases are supported for. 5 years for server LTS)

Yes, and in 18 months your software would be quite outdated. For some softwares it may not matter, for others may be it does. Open source softwares tend to have a much more rapid developing and release cycle than commercial ones so 18 months is a very long time.

---

### Post by snowpine on 2010-10-06
There are 100's of Linux distros. Whatever you desire, from ultra-stable-long-support-cyle to bleeding-edge-rolling-release, it's probably already available. It is more productive to find a distro that meets your needs than to demand a particular distro change into something different.

Now, one argument I hear a lot is, "I *would *switch to Distro X, but it just doesn't work as well as Ubuntu--it is difficult to install/too buggy/doesn't support my hardware/etc. So I guess I am stuck with Ubuntu and all its flaws, sigh."

My response to that is, "Have considered that the thing you do not like about Ubuntu is the very thing that makes it great? If Ubuntu morphed into something different, maybe it would no longer be the #1 desktop Linux distro, maybe it would not have such great hardware support, maybe it would not be so easy to install, etc. By cranking out a new release every 6 months, and then turning their attention to the next release (instead of wasting a lot of time fixing bugs or backporting new apps to old releases), Canonical creates a wonderfully innovative and fast-moving showcase for the latest desktop Linux innovations."

My 2 cents anyway. :)

---

### Post by mikewhatever on 2010-10-06
> **mamamia88 said:**
> why not?  why not provide a stable base os and let the user chose what applications to update?  why can't the updated software be unstable while the underlying system remains just as stable?  If i get a new Firefox version and Firefox starts crashing i simply revert back to older Firefox or use a different browser.  so why can't we have most recent versions of applications without compromising the stability of the underlying system?

Indeed, why not? Simply because this is precisely the state of affairs today. Are you suggesting to redo what exist just to get the very same thing?

> **LifeTheHound said:**
> ..........

Well, that's one common take. But here are a few novel reasons:
Consumer side (supported by my and many friends' experiences and countless recurring threads on this forum): have to keep upgrading and tweaking to get it working (or completely failing to upgrade like with Poulsbo, etc). Need to risk a perfectly working base just for new software is quite the bummer for many. I think the first post highlighted this pretty well. 
OEM/builder (supported by discussions in lkml and irc): With vendor's offerings becoming obsolete every 6 months, who could possibly afford to provide recurring large-scale proprietary driver support in the "country driven by money?" It's hard enough for users just to get these installed/tweaked/set-up with every 6 month release; just imagine the pain felt by 3rd parties such as Adobe (video accel), Intel (Poulsbo and main), etc. Most have given up because the rug gets pulled out from under them every few months. That and of course oodles of corporate pressure, but that's a whole separate discussion. ;)

Ha ha ha! This is killing me!
So flash and poulsbo suck because of the 6 months release cycle. Very interesting. Is that why flash also sucks on OSX, and only recently got hardware acceleration on Window? I mean, sure, if not for the 6 months cycle, Adobe would have been able to provide cross platform hardware acceleration 5 years ago. Yeah right. Do you think we are stupid or what?
And the poulsbo fiasco, sure, that's none of Intel's fault. Intel is just stuck with 3 different drivers it licensed from third parties, but can't manage to ship with its own Meego OS, all because the Ubuntu release cycle is wrong. Perfect, you should get a Nobel prize for most irrational reasoning.

---

### Post by psusi on 2010-10-06
> **mamamia88 said:**
> why not?  why not provide a stable base os and let the user chose what applications to update?  why can't the updated software be unstable while the underlying system remains just as stable?  If i get a new Firefox version and Firefox starts crashing i simply revert back to older Firefox or use a different browser.  so why can't we have most recent versions of applications without compromising the stability of the underlying system?

That is what we have.  You can run 10.04 and install updates that have been backported.

---

### Post by psusi on 2010-10-06
> **beew said:**
> And how is it a stable system if you are expected to upgrade the OS every 6 months with possibly lots of breakage?

Did you even read the OP or are you just spouting the party line?

*What?*

You DON'T have to upgrade every release, but that has nothing to do with my comment you replied to.  What I said is that having the latest and greatest software is the exact opposite of sticking with older, more well tested versions.  The OP seems to want both at the same time.
 
> **beew said:**
> Yes, and in 18 months your software would be quite outdated. For some softwares it may not matter, for others may be it does. Open source softwares tend to have a much more rapid developing and release cycle than commercial ones so 18 months is a very long time.

Stable = out of date.  You can't have software that is both new, and stable.

---

### Post by koenn on 2010-10-06
> **tgm4883 said:**
>  You aren't expected to upgrade the OS every 6 months. At the least it's 18 months (thats how long regular releases are supported for). At the most it's 3 years (that's how long LTS desktop releases are supported for. ... 
true, you don't *have to* upgrade. 
However, last time I checked, you can not skip releases when you do decide to upgrade. So at the end of your 18 months, you'll have to upgrade through all intermediate releases, or install a newer release from scratch. 

imo, that puts a somewhat less interesting perspective on your "you're not expected to upgrade every 6 months, you're supported for 18 months" claim.

---

### Post by beew on 2010-10-06
> **psusi said:**
> *What?*

Stable = out of date.  You can't have software that is both new, and stable.


Then it is a tautology by (your?) definition of "stable". So what was you point??!!

And based on that definition, why would "stability" be desirable???!! 

It seems that you are committing a fundamental logical fallacy, namely using "stable" in two entirely difference senses whenever it suits you.

**Koenn**,

Good point!

---

### Post by tgm4883 on 2010-10-06
> **koenn said:**
> true, you don't *have to* upgrade. 
However, last time I checked, you can not skip releases when you do decide to upgrade. So at the end of your 18 months, you'll have to upgrade through all intermediate releases, or install a newer release from scratch. 

imo, that puts a somewhat less interesting perspective on your "you're not expected to upgrade every 6 months, you're supported for 18 months" claim.

You can upgrade just fine from LTS to LTS

---

### Post by koenn on 2010-10-06
> **tgm4883 said:**
> You can upgrade just fine from LTS to LTS
Obviously, I wasn't talking about LTS, unless you want to claim that in the remark I replied to, your "upgrade the OS every 6 months. At the least it's 18 months (thats how long regular releases are supported for)", you were in fact referring to LTS. 

The situation with LTS is indeed slightly better, although it's an either/or proposition :  from an LTS release,  six months later you have a choice : stay with LTS, or go back to the 6 months cycle. It's a point of no return, and you only get that chance once, cause you can't skip a release. 

And that's in theory.
In praxtise; I'm on my 3rd LTS release now, so I should have seen 2 upgrades. 
At the fisrt one, the upgrade manager failed to run the upgrade - I pulled trough with some apt-get and dpkg -fu
At the second one, I could not get upgrade manager to detect a new available release - in the end I did a reinstall because I got a newer machine.

But that's probably just an implementation flaw, or mere coincidence. 
The all-or-nothing approach of the upgrade paths feels like a design flaw, which is worse. 

The only way these make sense is when you look at those 6 months releases as tests and develepment versions, and the real releases are the LTS.
I wonder whether Canonical sees it that way too.

---

### Post by psusi on 2010-10-06
> **beew said:**
> Then it is a tautology by (your?) definition of "stable". So what was you point??!!

My point is that you are asking for two diametrically opposed things at once.

> **beew said:**
> It seems that you are committing a fundamental logical fallacy, namely using "stable" in two entirely difference senses whenever it suits you.


And the second sense would be what?

> **koenn said:**
> Obviously, I wasn't talking about LTS, unless you want to claim that in the remark I replied to, your "upgrade the OS every 6 months. At the least it's 18 months (thats how long regular releases are supported for)", you were in fact referring to LTS. 

The situation with LTS is indeed slightly better, although it's an either/or proposition :  from an LTS release,  six months later you have a choice : stay with LTS, or go back to the 6 months cycle. It's a point of no return, and you only get that chance once, cause you can't skip a release. 

And that's in theory.
In praxtise; I'm on my 3rd LTS release now, so I should have seen 2 upgrades. 
At the fisrt one, the upgrade manager failed to run the upgrade - I pulled trough with some apt-get and dpkg -fu
At the second one, I could not get upgrade manager to detect a new available release - in the end I did a reinstall because I got a newer machine.

But that's probably just an implementation flaw, or mere coincidence. 
The all-or-nothing approach of the upgrade paths feels like a design flaw, which is worse. 

The only way these make sense is when you look at those 6 months releases as tests and develepment versions, and the real releases are the LTS.
I wonder whether Canonical sees it that way too.

So what's your point?  I thought it was that you should not have to upgrade every 6 months.  Now you seem to be shifting to the LTS to LTS upgrades often have issues that need fixed.  You have to concede the first point in order to make the second.

---

### Post by koenn on 2010-10-06
> **psusi said:**
> 
So what's your point?  I thought it was that you should not have to upgrade every 6 months.  Now you seem to be shifting to the LTS to LTS upgrades often have issues that need fixed.  You have to concede the first point in order to make the second.
My first point was that you practically **have to** upgrade every 6 months  - in reply to someone elses claim to the contrary. 
I don't want to do the whole "he said, then I said, then he said" thing - you can follow the quotes, I presume.
You will then also see where the LTS came from. 

I don't see where I have to concede what, as, to me, LTS and 6 monthly releases are 2 separate tracks and they don't mix

But my main point is the followuiing 
You end up with 2 scenarios :

You track LTS. You know what you have, and rest assured it won't change. If the release as a whole suits your needs, you're golden. 

or you track the normal releases, and deal with major changes every 6 months. If every new release works with your hardware, and nothing else goes wrong, you 'll enjoy reasonably current system almost continuously


Canonical's idea behind this was to get the best of both worlds :
- stability (a known, not changing environment) for those who need it
- delivering the newest versions of programs at a reasonable pace - every 6 months - good for users, and good for Ubuntu (release often, get good feedback, improve your product at a fast pace - the open source way)


Whats wrong with this approach :
There are a couple of scenarios that are not covered - eg you want stability, but the current LTS release contains a bug or a flaw in one of its components that constitutes a deal breaker for you, but won't get fixed in this release.
The solution is : you go to the competition for all your OS needs.

Another thing that's wrong : All of this applies to "the supported repositories". Install something from "Universe" and all deals are of. 


Those are design flaws.
The 3rd problem is a less of a design flaw, more of an unexpected side effect.
It turns out a lot of people find 6 months too still too slow (Firefox published a minor version upgrade yesterday and I have to wait for the Next Ubuntu in 2 months  or so before I can get it ? WTF ?!!), whereas in terms of development effort and release management, it's probably hell, and there are way to many 'it worked in the previous release, how com it's not working in the new release?' problems. 


So yeah, I'd say there's 1 or 2 (or 3) things wrong with Ubuntu's release cycle.  As in, Canonical tried for the best of both worlds, and ended up with disadvantages for everyone.

---

### Post by hhh on 2010-10-06
I just want to make a point that most everyone seems to think there are only 3 reasonable upgrade options... upgrade from point release to point release, upgrade from LTS to LTS, or do a fresh install. I'd like to point this out (this is Community Documentation but it's linked directly from the Ubuntu Support site)...
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
Please note the second paragraph... if you do a fresh install but manually override the partition formatting, Ubuntu will automatically act as if you have a separate home partition and not overwrite it. Then it's a matter of installing whatever drivers and programs differ from your old setup to the new release and you should be good to go. I don't know why this isn't better publicized.

That whole document is worth reading.

---

### Post by koenn on 2010-10-06
that is not really a 4th option, merely a way to preserve user data. It's still a "fresh install", technically, 

> will renew all system settings under /etc as well as the default set of installed packages. 

---

### Post by tgm4883 on 2010-10-06
What about LTS and upgrading specific software from PPA's?

---

### Post by koenn on 2010-10-06
> **tgm4883 said:**
> What about LTS and upgrading specific software from PPA's?

Answer me this first :
LTS are targetted at corporate enviironments. 
say, I run Ubuntu LTS in a corporate environment. I have a support contract with  cannonical. 
I add software from PPA's.
Something goes wrong at some time after we started using PPA's - one of those weird intermittend problems that are hard to pinpoint to a specific cause. 

Is my system still supported ? 
Is Canonical still bound by the SLA we agreed to prior to adding PPA's ? 

Or, in slightly other words : what are the terms and conditions on using PPA's ? (I had a look around a couple of times, didn't find any)µ

So, until I know where PPA's stand, I consider PPA's an experiment, and I don't experiment with production systems.

Besides this 'corporate' scenario, I kinda depend on my home computer. I prefer it to be available at any time. The Ubuntu repo's are usually trustworthy, and I reduce the risk of upgrades by using LTS. 

Where can I find a good explanation on the status of (software from) PPA's in this respect : eg terms of testing, quality assurance, .... ?  
Is it strictly a use at your own risk, YMMV solution ?



edit:
and while we're on the subject : 
Ubuntus upgrade paths are narrow, as discussed before. Apart from the 'dont skip a release', there's also' upgrades may fail if your system was substantially modified from the default install". 
How exactly are PPA'd systems expected to behave in upgrades ?

---

### Post by snowpine on 2010-10-06
Is a day of troubleshooting every 6 to 24 months *really *too high a price to pay for a functional, reliable, FREE operating system?

---

### Post by Dugger5688 on 2010-10-06
> **NotTheMessiah said:**
> I completely agree with that. It's fun at the start when you are learning new things, tinkering and experimenting but it gets tiring and time-consuming very fast. You simply run out of steam; we have less and less free time & we need something that you can just set-and-forget(e.g windows 7).

I spend a lot of time fixing friends screwed up windows 7 installs, much more than I spend fixing my own Lucid install. Actually, I haven't really done anything big since I installed it. It only ever reboots on a kernel upgrade, and once b/c of a power outage. Trust me windows is NOT set-and-forget once the average computer using monkey sits in front of it.

---

### Post by koenn on 2010-10-06
> **snowpine said:**
> Is a day of troubleshooting every 6 to 24 months *really *too high a price to pay for a functional, reliable, FREE operating system?

Depends on your perspective. 
If Open source/linux/Canonical/Ubuntu/... wants to play a role in the real world  - which I assume it does -- it will have to be able to live up to real world expectations. And in that world, a day of non-productivity (and associated loss of income) every 6 months for the entire workforce, may indeed be too high a price, especially if there are alternatives that don't suffer from those disadvantages. 


It also depends on what you mean by FREE.
if you're going for the "it didn't cost you anything so don't expect it to be any good" defense, you might want to know I consider that an insult to the open source community.

---

### Post by tgm4883 on 2010-10-06
> **koenn said:**
> Answer me this first :
LTS are targetted at corporate enviironments. 
say, I run Ubuntu LTS in a corporate environment. I have a support contract with  cannonical. 
I add software from PPA's.
Something goes wrong at some time after we started using PPA's - one of those weird intermittend problems that are hard to pinpoint to a specific cause. 

Is my system still supported ? 
Is Canonical still bound by the SLA we agreed to prior to adding PPA's ? 

Or, in slightly other words : what are the terms and conditions on using PPA's ? (I had a look around a couple of times, didn't find any)µ

So, until I know where PPA's stand, I consider PPA's an experiment, and I don't experiment with production systems.

Besides this 'corporate' scenario, I kinda depend on my home computer. I prefer it to be available at any time. The Ubuntu repo's are usually trustworthy, and I reduce the risk of upgrades by using LTS. 

Where can I find a good explanation on the status of (software from) PPA's in this respect : eg terms of testing, quality assurance, .... ?  
Is it strictly a use at your own risk, YMMV solution ?



edit:
and while we're on the subject : 
Ubuntus upgrade paths are narrow, as discussed before. Apart from the 'dont skip a release', there's also' upgrades may fail if your system was substantially modified from the default install". 
How exactly are PPA'd systems expected to behave in upgrades ?

heh, this is fun. :)

If you run Ubuntu in a corporate environment (and if it's like any other corporate environment) you don't upgrade software on a whim. You stick with what works. If you must upgrade software (to fix a bug), that software is tested in YOUR environment on test machines first, not rolled out to thousands of computers with no testing. 

If you are having an issue with some piece of software AND you have a SLA with canonical, don't come to the forums asking for help. You are paying for help, go to canonical for an answer. In that respect your argument is invalid since if you are a paying customer (mind you not many of us are paying customers) then support for a particular issue comes from canonical and if backports (or SRU's) are needed to resolve it then they get done.

If you are a home user and depend on your system. Ok fine. You have a few extra hoops to jump though to get new software or you can stick with what is available. In my experience PPA's have worked fine in the past, but that is a risk I am willing to take with some software. Look for a PPA from one of the developers. If you can't trust that, I'm not sure what you can trust then.

If you think a rolling release is better, fine. Use a rolling release. It isn't important that you run Ubuntu (after all Ubuntu != Linux), it's important that you run Linux. That is one of the reasons there are so many different distributions. Find one that works for you and stick with it. If it's Ubuntu great. If it's Arch, fine. If there isn't one that suits you, Linux from scratch it is then.

The issue is you think you are right, and that no other opinion matters. You want what basically amounts to a rolling release. I've discussed this in other threads where people want the release schedule slowed down to yearly. Other people don't want software to get updated at all as that specific software may break from time to time. Tell me. Who is right here?

Do you think we should just get rid of the repository and force users to download the software directly from the developers?

---

### Post by hhh on 2010-10-06
@koenn, understood, it's the same as creating a separate /home and doing a fresh install, just easier. My third option was a fresh install too, I realize my wording was clumsy. My point was how many people even know about that feature, and if you knew about it would you consider using it?

Re: purchased support...
[http://www.canonical.com/support/services/support-features](http://www.canonical.com/support/services/support-features)
[https://forms.canonical.com/sales/](https://forms.canonical.com/sales/)

And regarding Canonical liability, it seems everything is provided on an as-is basis...
[http://www.canonical.com/legal](http://www.canonical.com/legal)

---

### Post by snowpine on 2010-10-06
> **koenn said:**
> Depends on your perspective. 
If Open source/linux/Canonical/Ubuntu/... wants to play a role in the real world  - which I assume it does -- it will have to be able to live up to real world expectations. And in that world, a day of non-productivity (and associated loss of income) every 6 months for the entire workforce, may indeed be too high a price, especially if there are alternatives that don't suffer from those disadvantages. 

Nobody is deploying 6-month releases to thousands of employees; that is just silly and I won't even try to defend it. ;) Users in that category will choose LTS or Enterprise releases. (Or maybe Windows. They certainly aren't using Arch!)

> **koenn said:**
> It also depends on what you mean by FREE.
if you're going for the "it didn't cost you anything so don't expect it to be any good" defense, you might want to know I consider that an insult to the open source community.

No, that is not my point at all. :) Rather, that administering an operating system requires a certain amount of effort. You can pay someone to do it for you, or you can spend a little time and do it yourself (my preference, since it gives me total control). Certainly, it is not unreasonable (in my book) for Canonical to expect users to set aside one day every 6 to 24 months for system maintenance. (For most users, however, the release upgrade will be 100% seamless with no loss of productivity whatsoever.)

---

### Post by hhh on 2010-10-06
Again regarding corporate use of Linux and Ubuntu, this article is recent, seems well researched and is an eye opener, and also covers the well-publicized French Police's adoption of Ubuntu...
[http://scienceblogs.com/gregladen/2010/09/linux_in_schools.php?utm_source=networkbanner&utm_medium=link](http://scienceblogs.com/gregladen/2010/09/linux_in_schools.php?utm_source=networkbanner&utm_medium=link)

---

### Post by LifeTheHound on 2010-10-06
I think some ideas are being confused, so I'm going to clarify the position necessary to espouse the initial idea. 
- If you read the OP examples, you'll see that I mention a few cases that cannot be fixed on a different/upgraded version of Ubuntu, no matter how many days of "troubleshooting" are spent. This is true of Poulsbo, my camera driver, etc. 

- This is about popularity and functionality with end users, as well as the issue of manpower invested into the myriad of releases (and the *support* necessary to maintain 5 concurrent releases, all but one of which now have many pieces of software lagging [far] behind in the repos). 

- The word "stable" here means with "functions completely and well with the hardware" and "without many crashes" and is used as a diametric opposite to "broken system." Or something close enough. 

- Some vendors and their products (especially those that deal with closed-source, proprietary components) might indeed "suck" from a practical coding standpoint. Such is the case with a good proportion of software and coding in general. The question is not with code soundness so much as with the pervasive nature of the products they produce. While the world would perhaps be utopian if it weren't so; and while it's easy, satisfying, and perhaps even fair to single them (and even their customers, at times) out for blame, this doesn't change the avoidable reality of the problem--the carpet-pulling philosophy that compounds this problem. Taken to a logical conclusion, one might propose dramatic standardization and stabilization of practically all linux interface specifications, but this is as unfeasible as it is unrealistic in today's open-source world. My idea as it stands is not only feasible, but would engender a great sigh of relief in all affected parties (perhaps the vast majority of computer users). But do read on if you're still unclear as to what exactly this idea entails. 

- I agree that Ubuntu has excellent hardware support. Let's take a look at a trend, though, that illustrates my overall point. Let's say 80% of the time, a distro will work flawlessly with a given system. This is unrealistic in many, many ways (including statistically, where some hardware enjoys a consistently high level of support and some do not). If a user installs or upgrades 5 times, what's the likelihood of not having a broken system somewhere down the line? 80%^5 = 32.8% chance. That's right, this arbitrary number game is supposed to illustrate the concept that even with great hardware support, the fact that changes in hardware support are forced upon the user with every upgrade means it's very likely to somewhere down the line end up with [significant] breakage.  And for what? Just to get up-to-date, relevant software? This isn't good. The solution, as I've mentioned, is to maintain fewer releases (the LTS schedule is one model) and invest the manpower in keeping the user software in the repositories truly up-to-date. 

- There is confusion in this thread which leads to accusing this idea of being flawed because it asks for an impossible situation: pushing out all bleeding-edge software while paradoxically providing the stablest possible software, or some such absurdity. The key idea here is that it is quite possible for a system to be both stable, fully supported, and up-to-date in a manner far *superior* to the status quo. To do this, however, a distinction must be made between two types or "classes" of software. Please keep this in mind. Here is the distinction I proposed:  
**Hardware-interfacing software, drivers, and core dependencies--that's everything in the guts of the system, including kernel, X, drivers, hal (or other hardware interface bridges), core libraries, etc-- should be locked, while the user software (Java, OpenOffice, FireFox, Thunderbird, VirtualBox, GIMP, etc etc...) should be kept entirely up-to-date with release versions**. Because of the largely self-reliant nature of these programs (and those exceptions that require an updated dependency can be built statically as in Windows/PC-BSD), it is extremely unlikely that any of these would pose a system stability problem, simply because they aren't core system components. Espousing such a philosophy, even if it means keeping all of these 'release versions' in a backport (non-default) repository, is quite possible and entails roughly the same or less work than producing an entirely reworked distro every few months (with all attendant testing phases, coding, hammering around with kernels and dependency chains and xorg versions and drivers). 

- This idea itself isn't rocket science, but it isn't quite easy to grasp, either. Really think about it; to do so you should of course understand it first. 

- Another point to think about: the story below. 

Most of my friends/acquaintances are NOT linux experts. That stands to reason, demographically, as most people aren't, so this can speak for "the masses." A few friends and I had over-zealously offered to set the whole club up with Hardy awhile back. When "the masses" grew weary of the ancient software offerings in 8.04, they attempted to upgrade to 10.04 at roughly the same time (it was a big shiny button). I have to be honest--the vast majority ended up with some breakage and/or unsupported components--regressions all around. Most didn't know what to do. Some, few, sought help from these forums, and in a week or two, things were working fine; good for them. Some upgraded a system for which the upgrade could never work correctly--Poulsbo netbooks mostly (a very, very common piece of hardware). Others suffered graphics slowdowns (10.04's comparatively lousy open-source Intel stack version), and in a few cases a broken X system (an older i800 chipset, and an ATI with proprietary driver). It was a large-scale, hurtfully eye-opening experience when many ditched it soon after. Some came to me of course... not pretty. The question was angrily raised, "Why couldn't I just keep the old one and install new programs?" To them, of course, who'd been relatively content with their systems before many of their programs became obsolete, they probably didn't know the distintion between software I'm trying to make. They did NOT want to upgrade/destroy their systems, drivers, X, or any core components. They couldn't care less, and they wanted to keep what worked with their computers. They DID want the latest version of OpenOffice, GIMP, and a plethora of other things they'd installed from the repositories. Why? Because the older stuff either did not support newer formats properly, or they no longer maintained feature parity with the attractive new versions being touted by their peers. Some were just buggy because they were early releases Canonical somehow deemed "stable" (Hardy's abysmal KDE4 spin comes to mind). Even so, KDE SC (or many parts thereof) can itself be considered a "deep" component and may deserve freezing. On the other hand, it might not. 
**But the problem now isn't the distinction itself--**rubrics can always be constructed. The problem is **nobody in charge is making the distinction at all, which curtails the very possibility of a stable-base-rolling-software Ubuntu** (a highly desirable thing to most end users). This is why I single out the release schedule, which diverts manpower from this highly relevant possibility into making long trains of releases and ensuring the continued existence of the very problem I bring up.

---

### Post by psusi on 2010-10-06
Koenn has gone rather far afield from the original topic and is quickly headed for a windoows vs linux argument, which is a good way to get the thread locked.

LifeTheHound, the reason why it is an impossible situation is because to get stable software means that you stop updating to the latest and greatest release and only fix bugs in the old software.  It also requires lots of people to try the new software to find the bugs during the time it settles down and becomes stable.  We do that now during the development cycle, and as I've said, lengthening it is not likely to help matters since all the serious bugs that are found are fixed already before the release.  The rest aren't found until more people decide to try the new release.

Then you suggest keeping most of the system old and stable, but frequently updating to the latest and greatest of a few select packages.  Well that's what we have.  The latest version of firefox and OO.o are in the lucid updates repository.  The others you mention probably are too, though I didn't go check.

---

### Post by tgm4883 on 2010-10-06
> **LifeTheHound said:**
> snip

The distinction you are looking for is kernel space vs user space. You want kernel space stuff to stay the same and user space stuff to be upgradable though the repos. 

What you want is already available via backports. Please see [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by beew on 2010-10-06
> **tgm4883 said:**
> The distinction you are looking for is kernel space vs user space. You want kernel space stuff to stay the same and user space stuff to be upgradable though the repos. 

What you want is already available via backports. Please see [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Theoretically only. There is nothing in the backport. Take a look at the packages in it. Some libraries, ClamAv (which is a complete joke for an AV anyway), a bunch of KDE stuffs and Virtualbox (free version). The KDE backport though seems more interesting though I don't use a lot of kde stuffs. My default mode of installing software is by PPAs, the official repo versions are several versions behind typically.

---

### Post by psusi on 2010-10-06
> **beew said:**
> Theoretically only. There is nothing in the backport. Take a look at the packages in it. Some libraries, ClamAv (which is a complete joke for an AV anyway), a bunch of KDE stuffs and Virtualbox (free version). The KDE backport though seems more interesting though I don't use a lot of kde stuffs. My default mode of installing software is by PPAs, the official repo versions are several versions behind typically.

Two of the most important packages to keep up to date that have been mentioned so far ( firefox and OO.o ) are in there.  What specifically do you think should have a more up to date version in lucid that doesn't?

---

### Post by beew on 2010-10-06
> **psusi said:**
> Koenn has gone rather far afield from the original topic and is quickly headed for a windoows vs linux argument, which is a good way to get the thread locked.

LifeTheHound, the reason why it is an impossible situation is because to get stable software **means that you stop updating to the latest and greatest release and only fix bugs in the old software. **


So that old carnard again. Stability = not changing, but then how is it desirable? softwares have new features because they often enhance usability and it seems ridiculous to insist that users should give up on all the enhancement in order for the system of be "stable" (now in the common sense understanding of the word). If a system cannot be made stable (again in the common sense meaning) without requiring the users to stay months if not years behind unless they risk even greater instability (again common sense definition) by upgrading the whole OS (and installing PPAs, using porpietary drivers all make the upgrading process more harzardous ) then it is a failure of the design of the OS.

> 
Then you suggest keeping most of the system old and stable, but frequently updating to the latest and greatest of a few select packages.  Well that's what we have.  The latest version of firefox and OO.o are in the lucid updates repository.  The others you mention probably are too, though I didn't go check.I think most people would use more apps than OO.o (hopefully LibO soon) and Firefox, these are the most basic really.(I actually don't use OO.O. I am not an office worker, I only play with it. On the other hand I use science and math software a lot and I can't rely on the Ubuntu repo for them. Even the software devs advise users to download from their PPAs because the Ubuntu repo is hopelessly outdated. Having those outdated softwares around and making them the apparent default choices give both Ubuntu and the softwares a bad reputation)

In another thread someone asked about a bug in Lucid, the bug was fixed apparently but he didn't know where the fix was released. You told him in Maverick. Now how does it make sense if a "stable" system means even the bugs stay the same?

---

### Post by snowpine on 2010-10-06
An interesting theoretical discussion, to be sure. But if you want concrete, real-world answers, my suggestion is to examine distros that are renowned for their stability (yes, they do exist) and see how they accomplish it.

---

### Post by LifeTheHound on 2010-10-06
> **psusi said:**
>  The rest aren't found until more people decide to try the new release.
More time between releases doesn't necessarily entail less testing. In fact, I'd wager statistically that more people would find the time to test a release if the testing interval is longer. But this is hardly a question of release cycles as much as it is release methodology and conduction of testing phases. 

> Then you suggest keeping most of the system old and stable, but frequently updating to the latest and greatest of a few select packages.  Well that's what we have.  The latest version of firefox and OO.o are in the lucid updates repository.  The others you mention probably are too, though I didn't go check.

Not quite; see below. In regards to the two packages you mention in Lucid, it's wonderful that this is the case, but this is because Lucid is still the latest released version. My case is that very soon they will *not* be kept up to date. Notice that right now, both packages you mention have only seen dot updates since the initial versions. You bring up Firefox and OpenOffice. The latest version of both of these are merely security/bugfix bumps, and neither are actually found in backports (OpenOffice was in Proposed, last I checked, and Firefox was in Updates). The backports likely will not contain major new versions of either of the two, be it OpenOffice 3.3, for instance, or Firefox 4.X, both of which are due relatively soon. 

> **tgm4883 said:**
> What you want is already available via backports. Please see [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)
With the greatest respect, I urge you to glance at the contents of the backports repositories for any of the 3 or so oldest supported versions. Hardy is still technically supported, but the backports are virtually empty of up-to-date content. Even the lucid backports see little activity (though so early in its 3-5 year life, this should very much be the case). 

Standalone pieces of software, especially major new releases, do have minor bugs at times (though sometimes the opposite is true and they are significantly more stable than previous incarnations). But even so, bugs are introduced in the normal update process as well, as even some security/bugfix updates have to be tested and occasionally rolled back. This is why there is a "Proposed" repository--to test these before they are let loose. This is an ideal solution with rolling software as well--release new versions to a riskier repository first, collect feedback, and release when ready. 

The problem, of course, is that the current development model doesn't even try. I don't see OpenOffice 3.2.1 in Hardy repos, for instance, despite significant bug fixes and enhancements from its ancient 2.X, or newer versions of GIMP, etc. Firefox (for now only) seems to have been the only exception recently granted; it's said that exceptions prove the rule. This can be changed by the rolling user software concept, and the work currently put into making a new distro every 6 months can be saved or put into the very software-testing you mention, albeit via slightly different means (though arguably even more effective ones; more people will be running the released distro with the "proposed" repo active and more reports will come in).

---

### Post by tgm4883 on 2010-10-06
> **beew said:**
> Theoretically only. There is nothing in the backport. Take a look at the packages in it. Some libraries, ClamAv (which is a complete joke for an AV anyway), a bunch of KDE stuffs and Virtualbox (free version). The KDE backport though seems more interesting though I don't use a lot of kde stuffs. My default mode of installing software is by PPAs, the official repo versions are several versions behind typically.

I hope you read the wiki page. It says how you can request software to be backported. What is required for a backport. What backports are to accomplish. Have you filed a bug to get something backported to the stable release? There is also developer information if you want to backport software yourself.

---

### Post by psusi on 2010-10-06
> **beew said:**
> So that old carnard again. Stability = not changing, but then how is it desirable? softwares have new features because they often enhance usability and it seems ridiculous to insist that users should give up on all the enhancement in order for the system of be "stable" (now in the common sense understanding of the word). If a system cannot be made stable (again in the common sense meaning) without requiring the users to stay months if not years behind unless they risk even greater instability (again common sense definition) by upgrading the whole OS (and installing PPAs, using porpietary drivers all make the upgrading process more harzardous ) then it is a failure of the design of the OS.

I didn't say it was desirable, you did.  Stable means unchanging.  What you seem to really want is bug free.  When you figure out how to develop software and add new features without ever introducing a new bug, every software developer in the world would like to hear about it.  Until then, the way it is done is to stop adding new features and only fix bugs.  Eventually all of the bugs are fixed and you have a bug free program, without all of the new features that have been developed since the freeze.

> **beew said:**
> In another thread someone asked about a bug in Lucid, the bug was fixed apparently but he didn't know where the fix was released. You told him in Maverick. Now how does it make sense if a "stable" system means even the bugs stay the same?

Again, you are confusing stable with bug-free.  Bugs get fixed in the stable release when they are severe enough to warrant someone taking the time to carefully evaluate the fix, decide that it isn't likely to cause any other breakage, apply the fix to the stable version, test it thoroughly, then release.  This takes a lot of effort and sometimes is not possible since the fix isn't a small change, but requires a number of significant changes to the program that are likely to cause more bugs.

> **LifeTheHound said:**
> More time between releases doesn't necessarily entail less testing. In fact, I'd wager statistically that more people would find the time to test a release if the testing interval is longer. But this is hardly a question of release cycles as much as it is release methodology and conduction of testing phases. 

A longer testing period would mean more time for testing and bug fixing, but without significantly more people doing the testing, and on significantly more hardware, it would not help much, and would mean releasing with older software than happens now.

> **LifeTheHound said:**
> It's wonderful that this is the case, but this is because Lucid is still the latest released version. My case is that very soon they will *not* be kept up to date. Hardy is still technically supported, but the backports are virtually empty. Even the lucid backports see little activity (though so early in its 3-5 year life, this should very much be the case). You bring up Firefox and OpenOffice. The latest version of both of these are dot releases (security/bugfix bumps) from the initial version. The backports likely will not contain OpenOffice 3.3, for instance, or Firefox 4.X, both of which are due relatively soon. 

True, it has only gone from 3.6.3 to 3.6.10.  Hardy stuck with a 2.0.x.  So now we seem to be coming to the real issue, which is not with the current release cycle, but with there not being *enough* backports.

> **LifeTheHound said:**
> Standalone pieces of software, especially major new releases, do have minor bugs at times (though sometimes the opposite is true and they are significantly more stable than previous incarnations). But even so, bugs are introduced in the normal update process as well, as even some security/bugfix updates have to be tested and occasionally rolled back. This is why there is a "Proposed" repository--to test these before they are let loose. This is an ideal solution with rolling software as well--release new versions to a riskier repository first, collect feedback, and release when ready. 

How many people do you think actually use -proposed?  Almost nobody.  Anyone willing to be more risky with updates has already moved on to the development release.

> **LifeTheHound said:**
> The problem, of course, is that the current development model doesn't even try. I don't see OpenOffice 3.2.1 in Hardy repos, for instance, despite significant bug fixes and enhancements from its ancient 2.X, or newer versions of GIMP, etc. Firefox (for now only) seems to have been the only exception granted; it's said that exceptions prove the rule. This can be changed by the rolling user software concept, and the work currently put into making a new distro every 6 months can be saved or put into the very software-testing you mention, albeit via slightly different means (though arguably even more effective; more people will be running the distro with the "proposed" repo active and more reports will come in).

This is the way debian works, which is why their stable release tends to have significantly older software.  Because it first has to make its way through the rolling unstable release, sit in the testing release for months to years, then finally get released as the next stable release.

---

### Post by LifeTheHound on 2010-10-06
> **tgm4883 said:**
> I hope you read the wiki page. It says how you can request software to be backported. What is required for a backport. What backports are to accomplish. Have you filed a bug to get something backported to the stable release? There is also developer information if you want to backport software yourself.

I did. This was part of the manpower argument -- the current model requires an additional effort on the part of the users and the developers, and is specific to only certain requested software. This model exists because of the prohibitive amount of time it would otherwise take to comb upstream sources for every single package in all 5 concurrently maintained versions of Ubuntu. Therefore, under the current system, this process is valid as it places broad limiters on the amount of work attempted. 

However, in the system I'm suggesting, there is both a new form of limitation and a different (much higher) source of manpower. Chiefly, the distinction between programs which are system-internal and those which are user software -- essentially, a mark of what packages follow the rules outlined on the wiki page -- should already exist for every package. Those that qualify are automatically surveyed for changes and backported if necessary. The manpower will of course come from diverting resources away from the "*Two* All-new Operating Systems Each and Every Year, Guaranteed!!" cycle.

Some common-sense reasons why the current report-to-backport system is severely flawed for most people (or "the masses," "me," and likely "you too"):
- Very few applicable programs wind up in the backports repos (take a look) for one reason or another, including some reasons below.
- Most users don't know what a "library" is, what an API or ABI is, or what any of the "tech jargon" on that page means. None of "the masses", even if presented this page, would have the ability or gumption to follow through. The page is clearly written for people with programming backgrounds -- a friend I just showed via chat verified my fears and replied "lol, linux is showing its roots" and promptly dismissed the idea as ludicrous. (Yes, she's being a jerk, but she kind of has a point)
- Other competitive operating systems do not require direct user request and approval processes for what could otherwise be (and often is) an automatic or streamlined procedure.

---

### Post by NotTheMessiah on 2010-10-06
> **Dugger5688 said:**
> I spend a lot of time fixing friends screwed up windows 7 installs, much more than I spend fixing my own Lucid install. Actually, I haven't really done anything big since I installed it. It only ever reboots on a kernel upgrade, and once b/c of a power outage. Trust me windows is NOT set-and-forget once the average computer using monkey sits in front of it.

Messed up installs of 7 by users is quite different compared to a fresh ubuntu install that can't connect/drops wireless networks(wifi just an example). In my case, I loved lucid netobook version and wanted to keep it but it simply wouldn't do wifi. On the other hand, wifi was rock solid with 9.10 but the os overall was choppy, slow and it would lock up and the sreen would flicker. Now i have MM rc on and it has the same wifi problem(constant drop outs).So, as i've said before, it **does get tired** after a while. I am still trying, though. I have zero headaches with my desktop's 7 install but i would love to get lucid working on my netbook as it should(as my crappy, old, ugly xp home does)  

I apologize if i am completely Off topic. And it is not my intention to start any tired and stupid "this vs that" clan fights.In fact, i want ubuntu to succeed. Just your average user with typical experiences :)

---

### Post by LifeTheHound on 2010-10-06
> **psusi said:**
> 
A longer testing period would mean more time for testing and bug fixing, but without significantly more people doing the testing, and on significantly more hardware, it would not help much, and would mean releasing with older software than happens now. <snip>

This is the way debian works, which is why their stable release tends to have significantly older software.  Because it first has to make its way through the rolling unstable release, sit in the testing release for months to years, then finally get released as the next stable release.


Aside from proposal of a superior system which I am entirely convinced would entice users to stay on (and thus attract new users), it's common sense that fewer distributions leads to more using a single distribution. People who suffer through older software or are afraid of breakage or simply haven't "gotten around to it" are using some of the other 5 currently supported releases. Fewer releases + up-to-date user software + already invested tweak time/troubleshooting = more people on one release. 

That said, you've entirely missed the point. Testing of new software can and should be done after release. Your thinking reflects the very system I'm arguing against-- true, keeping the current system, longer releases would simply mean the software becomes more obsolete at release and will remain so throughout the support cycle (an even longer painful wait for the next already-outdated offering years later). Absolutely not. The user software (backport-style) is kept on rolling update with a Proposed repository for testing major releases. The testing occurs WITHIN the released operating system. I'm easily testing a beta Firefox and OpenOffice in Windows, for instance, without upgrading the operating system, and all my programs keep themselves up-to-date automatically or notify me of new releases. Linux can be a step up because it has a powerful centralized software management system. 

> True, it has only gone from 3.6.3 to 3.6.10.  Hardy stuck with a 2.0.x.  So now we seem to be coming to the real issue, which is not with the current release cycle, but with there not being *enough* backports.
Of course this is the real issue. Re-read the first post (or read it if you haven't already) with this in mind. This is precisely the "(big) reason Ubuntu's release cycle is flawed" -- because the system I propose that fixes the lack of current software very much requires a stable, less-frequent base *and* the manpower that would otherwise go into producing and maintain such huge numbers of sequential releases. 

> 
How many people do you think actually use -proposed?  Almost nobody.  Anyone willing to be more risky with updates has already moved on to the development release.
Says who? I do, but even so, that's hardly the point. No, under the current system, both hardware-interfacing components (kernel-side), libraries, etc -- system-wide changes, in other words -- are tested there. People are afraid of broken systems. This is part of the problem with the lack of distinction between system software and user software. In the user-software-only "Proposed" (like a backports-proposed of sorts) tons of people would rally to try it out just as enthusiasts do on other OS's when a new beta of their favorite program comes out.

---

### Post by NCLI on 2010-10-07
> **LifeTheHound said:**
> I did. This was part of the manpower argument -- the current model requires an additional effort on the part of the users and the developers, and is specific to only certain requested software. This model exists because of the prohibitive amount of time it would otherwise take to comb upstream sources for every single package in all 5 concurrently maintained versions of Ubuntu. Therefore, under the current system, this process is valid as it places broad limiters on the amount of work attempted. 

However, in the system I'm suggesting, there is both a new form of limitation and a different (much higher) source of manpower. Chiefly, the distinction between programs which are system-internal and those which are user software -- essentially, a mark of what packages follow the rules outlined on the wiki page -- should already exist for every package. Those that qualify are automatically surveyed for changes and backported if necessary. The manpower will of course come from diverting resources away from the "*Two* All-new Operating Systems Each and Every Year, Guaranteed!!" cycle.

Some common-sense reasons why the current report-to-backport system is severely flawed for most people (or "the masses," "me," and likely "you too"):
- Very few applicable programs wind up in the backports repos (take a look) for one reason or another, including some reasons below.
- Most users don't know what a "library" is, what an API or ABI is, or what any of the "tech jargon" on that page means. None of "the masses", even if presented this page, would have the ability or gumption to follow through. The page is clearly written for people with programming backgrounds -- a friend I just showed via chat verified my fears and replied "lol, linux is showing its roots" and promptly dismissed the idea as ludicrous. (Yes, she's being a jerk, but she kind of has a point)
- Other competitive operating systems do not require direct user request and approval processes for what could otherwise be (and often is) an automatic or streamlined procedure.

I find many of your arguments compelling, but if you really want this to be taken seriously, you should write to one of the official developer mailing-lists, post a bug on Launchpad, or maybe even send Mark a short, concise email. He usually replies.

---

### Post by fergy123 on 2010-10-07
I totally agree with him.

I have an hp compaq nx9420 and have had endless issues trying to get 10.04 to install. 

I really do believe that as awesome as it is to have a new release as often as they do, they are kinda shooting themselves in  the foot as the releases are not always as stable as the last ones. 

I love Ubuntu and would really love to have it working on all my machines but unfortunately Win7 does it better on the less supported ones. And it pains me to say that. 

Reuben Fergusson

Linux Enthusiast

---

### Post by psusi on 2010-10-07
It doesn't really take hardly any development time to have karmic still sitting in the repository.  After the initial few months of fixing a few serious bugs that are found, the only further changes to supported releases are back porting security fixes, which doesn't take that much time.  Most developer effort is focused on improving the next release.

So again, what you really seem to be talking about is running the LTS and installing backports, which we have, but could be improved.

---

### Post by beew on 2010-10-07
> **psusi said:**
> After the initial few months of fixing a few serious bugs that are found, the only further changes to supported releases are back porting security fixes, which doesn't take that much tim**e.  Most developer effort is focused on improving the next release.**


Yes, and the OP argues,--I agree,--that this is a problem. Why is it that the Ubuntu team is behaving like it is suffering from collective ADHD?

---

### Post by psusi on 2010-10-07
> **beew said:**
> Yes, and the OP argues,--I agree,--that this is a problem. Why is it that the Ubuntu team is behaving like it is suffering from collective ADHD?

To avoid being stuck with old, outdated software.  It takes a certain amount of manpower to get the latest software, build it, test it, and fix some bugs in the development release.  It takes more manpower to then back port it to an older release.  It seems they don't have enough spare manpower for a whole lot of backporting.

---

### Post by beew on 2010-10-07
> **psusi said:**
> To avoid being stuck with old, outdated software.  It takes a certain amount of manpower to get the latest software, build it, test it, and fix some bugs in the development release.  It takes more manpower to then back port it to an older release.  It seems they don't have enough spare manpower for a whole lot of backporting.

You are getting stuck with old, outdated softwares under the current system. Moreover, if you do want upgrade so that you don't stuck with obsolete sofwares (which you have to wait for at least 6 months, never mind what breakthroughs have happen in softwares in between) you risk breaking the whole system. So basically you have neither stability (in the sense of system being bug free and doesn't crash) nor up to date softwares in this all or nothing model. It is the worst of both worlds.

The OP's suggestion would overcome that.

---

### Post by tgm4883 on 2010-10-07
> **beew said:**
> You are getting stuck with old, outdated softwares under the current system. Moreover, if you do want upgrade so that you don't stuck with obsolete sofwares (which you have to wait for at least 6 months, never mind what breakthroughs have happen in softwares in between) you risk breaking the whole system. So basically you have neither stability (in the sense of system being bug free and doesn't crash) nor up to date softwares in this all or nothing model. It is the worst of both worlds.

The OP's suggestion would overcome that.

What about people that just want to stick on the same versions of software (such as gwibber, gimp, etc), but still get security updates? Wouldn't the OPs idea mean that these apps are getting updated as well?

---

### Post by psusi on 2010-10-07
> **beew said:**
> You are getting stuck with old, outdated softwares under the current system. Moreover, if you do want upgrade so that you don't stuck with obsolete sofwares (which you have to wait for at least 6 months, never mind what breakthroughs have happen in softwares in between) you risk breaking the whole system. So basically you have neither stability (in the sense of system being bug free and doesn't crash) nor up to date softwares in this all or nothing model. It is the worst of both worlds.

The OP's suggestion would overcome that.

This is not true since serious bugs ARE fixed in the stable release.  What you choose between is having the latest and greatest features, or the older version without all of the bells and whistles, but that has been better debugged.  The OP wants both.

> **tgm4883 said:**
> What about people that just want to stick on the same versions of software (such as gwibber, gimp, etc), but still get security updates? Wouldn't the OPs idea mean that these apps are getting updated as well?

That is how the current system works.

---

### Post by tgm4883 on 2010-10-07
> **psusi said:**
> This is not true since serious bugs ARE fixed in the stable release.  What you choose between is having the latest and greatest features, or the older version without all of the bells and whistles, but that has been better debugged.  The OP wants both.



That is how the current system works.

Not exactly. There is a security repo that hosts the security updates. then there is -backports and -updates

---

### Post by snowpine on 2010-10-07
You do realize that, regardless of which Ubuntu release you're using, you can always get the latest Firefox from mozilla.org, the latest OpenOffice from openoffice.org, the latest Gimp from gimp.org, and so on?

Ubuntu does not "force" you to be "stuck" with anything; rather it gives you a reasonably stable platform as a *starting point* for your own explorations. You can always install any version of any application you like; you can even customize and recompile apps specifically to your needs... this is the true meaning of "open source"! :)

Now, a few times lately I've heard the argument that "some apps should be held back at outdated stable versions, while other apps should be updated to the latest version." The problem with this approach is, *who gets to decide *which apps are the "important" ones? What if my needs are the opposite of yours and I want older, stable end-user apps but the need latest kernel and hardware suport? Or what if I need current multimedia apps but don't need the latest and greatest OpenOffice and don't want the Update Manager cramming a 100mb download down my throat. The nice thing about most Linux distros (including Ubuntu) is that they leave this choice to the individual user based on individual needs.

---

### Post by koenn on 2010-10-07
> **tgm4883 said:**
> heh, this is fun. :)
thanks for playing along, I'm rather enjoying it too
(too bad time zones and not wanting to lose sleep over a recurring discussion, got in the way)

> **tgm4883 said:**
> 
If you are having an issue with some piece of software AND you have a SLA with canonical, don't come to the forums asking for help. ... 

If you are a home user  ... .

If you think a rolling release is better, ...

I think you misunderstood. I'm not looking for help. I gave those (hypothetical but realistic) examples to illustrate the gaps in Canonicals two-pronged approach to relases. Leaving those gaps means losing potential users/customers. Given that Ubuntu aims for mass adoption, and Canonical would like to become profitable, I'd say those gaps are indeed flaws in Canonical's release concept.  


> **tgm4883 said:**
> 
The issue is you think you are right, and that no other opinion matters. 
Of course I think I'm right. Don't you ? 
In any case, if I didn't think I'm right, I'd be arguing a position I don't believe in - that's borderline trolling, something  the people who run these forums doe not approve of. So yeah, I think I'm right. 
As for "no other opinion matters" - that's an assumption on your part, I can't help what you think. 


> **tgm4883 said:**
> 
You want what basically amounts to a rolling release. I've discussed this in other threads where people want the release schedule slowed down to yearly. Other people don't want software to get updated at all as that specific software may break from time to time. Tell me. Who is right here?


Do you think we should just get rid of the repository and force users to download the software directly from the developers?
I don't remember proposing any of those ; those are, again, mere assumptions. As it happens, I do not want a rolling release, I have no opinion on speeding up or slowing down the release frequency, and I think forcing users to download software directly from the developers would not be a smart move.

---

### Post by koenn on 2010-10-07
> **psusi said:**
> Koenn has gone rather far afield from the original topic and is quickly headed for a windoows vs linux argument, which is a good way to get the thread locked.
for the record, 
I think I 'm pretty well on topic (flaws in ubuntu's release cycle), I'm just introducing a different angle here and there, and some new elements that, imo, pertain to the discussion. 
Discussions where the only accepted replies are "i agree with the OP" or "i don't agree with the OP", tend to get rather boring. 

I don't seewhere you got the "Koen is [... ] headed for a windows vs linux argument" from. I find those incredibly boring.

---

### Post by koenn on 2010-10-07
> **snowpine said:**
> You do realize that, regardless of which Ubuntu release you're using, you can always get the latest Firefox from mozilla.org, the latest OpenOffice from openoffice.org, the latest Gimp from gimp.org, and so on?

Ubuntu does not "force" you to be "stuck" with anything; rather it gives you a reasonably stable platform as a *starting point* for your own explorations. You can always install any version of any application you like; you can even customize and recompile apps specifically to your needs... this is the true meaning of "open source"! :)

Now, a few times lately I've heard the argument that "some apps should be held back at outdated stable versions, while other apps should be updated to the latest version." The problem with this approach is, *who gets to decide *which apps are the "important" ones? What if my needs are the opposite of yours and I want older, stable end-user apps but the need latest kernel and hardware suport? Or what if I need current multimedia apps but don't need the latest and greatest OpenOffice and don't want the Update Manager cramming a 100mb download down my throat. The nice thing about most Linux distros (including Ubuntu) is that they leave this choice to the individual user based on individual needs.

well, no, Ubuntu doesn't do that.
The recommended way to install software, is from the repos. Yes, I know there are alternatives, but the people who  deliver this platform to me strongly advise me to use their software delivery system.

Added to that, Ubuntu, as a platform, is pretty much release oriented. For instance, ubuntu packages resolve all their dependencies within the release they belong to, although they could, at least technically, also satisfy their dependencies with packages from other releases. 

Which boils down to: you use whatever software is provided in the repos of the release you're on, and you follow either the LTS releaases, or the fast and furious releases, nothing else. 

> The nice thing about most Linux distros (including Ubuntu) is that they leave this choice to the individual user based on individual needs.
I'd love it if Ubuntu did that, but it doesn't. 
At best, it doesn't stop you from applying workarounds outside "official channels". 
Which is fine for a hobby project or a home user with a bit of knowledge, but, unless I'm misinformed, Canonical's target audiance with Ubuntu is way wider than that.

---

### Post by snowpine on 2010-10-07
> **koenn said:**
> well, no, Ubuntu doesn't do that.
The recommended way to install software, is from the repos. Yes, I know there are alternatives, but the people who  deliver this platform to me strongly advise me to use their software delivery system.

Added to that, Ubuntu, as a platform, is pretty much release oriented. For instance, ubuntu packages resolve all their dependencies within the release they belong to, although they could, at least technically, also satisfy their dependencies with packages from other releases. 

Which boils down to: you use whatever software is provided in the repos of the release you're on, and you follow either the LTS releaases, or the fast and furious releases, nothing else. 

I'd love it if Ubuntu did that, but it doesn't. 
At best, it doesn't stop you from applying workarounds outside "official channels". 

Which is fine for a hobby project or a home user with a bit of knowledge, but, unless I'm misinformed, Canonical's target audiance with Ubuntu is way wider than that.

Your argument is circular. If you are scared to go outside the "official recommendation" then guess what? You must accept the way that Ubuntu chooses to do things (or get involved with the project and mold it to your vision). If you choose to be spoon-fed then don't complain that the crayons are dull and the walls are padded. ;)

If on the other hand you choose to exercise the basic freedoms that all Linux users have, you will discover that you are, indeed, able to administer your system however you see fit. Learning how to install "upstream" applications is a basic skill that all Linux users should have, in my opinion.

Peanuts have been removed from school cafeterias and airline snacks due to allergy concerns; does this mean they are not a healthful and delicious food for diners aware of the risks?

---

### Post by beew on 2010-10-07
> **tgm4883 said:**
> What about people that just want to stick on the same versions of software (such as gwibber, gimp, etc), but still get security updates? Wouldn't the OPs idea mean that these apps are getting updated as well?

Then just pin your versions. Should Ubuntu be catering to people who want obsolete softwares?

---

### Post by snowpine on 2010-10-07
> **beew said:**
> Then just pin your versions. Should Ubuntu be catering to people who want obsolete softwares?

Depending on your definition of the word "obsolete":

1. Yes, Ubuntu does indeed cater to people who want "obsolete softwares" and its release cycle is designed specifically for this purpose.
or
2. No, there are no "obsolete softwares" in any of the currently-supported Ubuntu releases, because they all continue to serve their intended purpose as well as they did on release day.

As an example, 8.04 uses OpenOffice 2.4. Is OO 2.4 "obsolete"? I say "no" because it still serves its purpose of generating office documents. If it no longer effectively creates documents, spreadsheets, etc. only then does it become "obsolete" in my book.

A counter-example is that Firefox 3.0 did, indeed become "obsolete" (no longer recommended/supported by Mozilla) and so at that point Canonical provided an update to 3.6 through the security repo.

---

### Post by beew on 2010-10-07
> **snowpine said:**
> Depending on your definition of the word "obsolete":
As an example, 8.04 uses OpenOffice 2.4. Is OO 2.4 "obsolete"? I say "no" because it still serves its purpose of generating office documents. If it no longer effectively creates documents, spreadsheets, etc. only then does it become "obsolete" in my book.

I define "obsolete" in a functional sense, Ubuntu can support  whatever ancient technology and it is still obsolete. When OO.O3.3 is at the corner (or LibreOffice) it is a complete waste of everyone's time and resources to support OO2.4. I see no reason why they can't port OO.O3.2 to the 8.04 repo. New features are not just "bell and whistles",--I have the feeling that people who use the expression  think that all new features are just frills. They may add essential enhancements to usability. OO2.4 was painfully slow as I remember (like it took almost a minute to open a document? )

 A computer is just a calculator with more "bells and whistles".:)

---

### Post by psusi on 2010-10-07
> **beew said:**
> I define "obsolete" in a functional sense, Ubuntu can support  whatever ancient technology and it is still obsolete. When OO.O3.3 is at the corner (not to mention LibreOffice) it is a complete waste of everyone's time and resources to support OO2.4. New features are not just "bell and whistles",--I have the feeling that people who use the expression  think that all new features are just frills. They may add essential enhancements to usability. OO2.4 was painfully slow (like it took a minute to open a document? ) A computer is just a calculator with more "bells and whistles".:)

And the new features that you might consider essential someone else considers frills.  Either way, the new features introduce new bugs.  This is why your choice is between new software with new features and new bugs, or old software with fewer bugs and features.  You want the new features without the new bugs, but I'm sorry to tell you that just isn't possible.

---

### Post by beew on 2010-10-07
> **psusi said:**
> And the new features that you might consider essential someone else considers frills.  Either way, the new features introduce new bugs.  This is why your choice is between new software with new features and new bugs, or old software with fewer bugs and features.  You want the new features without the new bugs, but I'm sorry to tell you that just isn't possible.


So if you stick to 1990 technology you will be bug free? Like I said, this is striaght out of the abstinace school of safe sex.

BTW, I don't believe a feature update on an end user software like OOO ,--the OP made the crucial distinction between end user apps and softwares to run the system and we should keep that in mind to avoid strawman arguments,--would introduce more bugs than upgrading the whole OS to a new release (Speaking of which Open Office doesn't even open in Maverick last night's build and pun intended)

---

### Post by snowpine on 2010-10-07
> **beew said:**
> When OO.O3.3 is at the corner (or LibreOffice) it is a complete waste of everyone's time and resources to support OO2.4. I see no reason why they can't port OO.O3.2 to the 8.04 repo. 

I understand your point (it is **very** frequently asked/argued here on the Forums), and I respectfully disagree (as do the people in charge at Canonical, apparently). :)

To flip your statement around, I see no reason why **you** can't port OO.O3.2 to your 8.04 install. If it is really that easy, just do it already and get back to work. ;)

---

### Post by koenn on 2010-10-07
> **snowpine said:**
> Your argument is circular. If you are scared to go outside the "official recommendation" then guess what? You must accept the way that Ubuntu chooses to do things (or get involved with the project and mold it to your vision). If you choose to be spoon-fed then don't complain that the crayons are dull and the walls are padded. ;)

If on the other hand you choose to exercise the basic freedoms that all Linux users have, you will discover that you are, indeed, able to administer your system however you see fit. Learning how to install "upstream" applications is a basic skill that all Linux users should have, in my opinion.

Peanuts have been removed from school cafeterias and airline snacks due to allergy concerns; does this mean they are not a healthful and delicious food for diners aware of the risks?

It's not about being scared. 
Please keep in mind that I'm looking at this from a corporate perspective (which is a valid point of view, as they are part of Ubuntus and Canonical's target market, and LTS's, where these problems are most acute, are targeted specifically at 'businesses')
So it's not about being scared, it's about governance, risk assesment and risk management, liabilities, etc

Let's do yet another car analogy:
Say a company purchases a large number of cars. Say they come with strong recommendations from the manufacturer, about following the prescribed maintenance schedule, having all maintenance and repairs done by qualified mechanics from authorized dealerships, and only using official spare parts and accessories.

How many people, in charge if such a company, do you think would rather adhere to these recommendations than to risk their investment (wave their warranty, etc etc) ?
Or, if you were the transport manager in such a firm, would you rather follow the official recommendations, or, at your own risk, go get second market parts and have maintenance and repairs done by some independent "all makes and models" mechanic shop - knowing that if something goes wrong, you'll be held responsible, and possibly liable for damages and what not. Probably get fired as well, if something goes very wrong and can be traced back to your decision.


My guess is that in such a case, the majority of people will tend to stick with "official". For those people, there are these obvious gaps in Ubuntu's release model - gaps that may be solved by a better designed release model rather than by stop gaps such as backports (and PPA's)

So, the current release model excludes a, possibly large, part of potential customers. I think that's not smart. 

(But what you do at home with your own car is your business. You can build a car from scratch for all I care -- I might even volunteer to come and help)

---

### Post by snowpine on 2010-10-07
> **koenn said:**
> Please keep in mind that I'm looking at this from a corporate perspective (which is a valid point of view, as they are part of Ubuntus and Canonical's target market, and LTS's, where these problems are most acute, are targeted specifically at 'businesses')
So it's not about being scared, it's about governance, risk assesment and risk management, liabilities, etc

Sorry but I have to (respectfully) call "shenanigans" here... are you, in fact, the IT decision maker for a company with a large Ubuntu 8.04 deployment? Or are you speculating about what you *think* the corporate world needs?

On my work computer right now, I'm running CentOS 5.5 (the "free" version of Red Hat Enterprise, which I would happily purchase if I needed the support). It gives me an extremely stable base system (kernel 2.6.18, KDE 3.5, etc.), a 7-year support cycle, and up-to-date end user applications like Firefox 3.6.x and OpenOffice 3.x. It is well-documented, in print and on the 'web, and there are plenty of highly-trained and certified Linux professionals to assist me if I get into a jam.

Canonical knows they cannot possibly compete with this (their entire business model is based on "taking a snapshot of Debian Unstable every 6 months") and so, rightfully, they don't even try. Instead, they do what they are best at (6-month snapshots of the latest Linux desktop innovations) and it seems to be working, as most estimates place them as the #1 consumer/hobbyist Linux distro (a niche that Canonical felt Debian was neglecting when Ubuntu was first conceived).

> **koenn said:**
> Let's do yet another car analogy:
Say a company purchases a large number of cars...

OK, I will bite, since I love car analogies too. :)

I'm imagining I am the transportation manager and purchase a fleet of 1,000 vehicles. The very last thing in the world I want is for my drivers to start asking me, "what happened to my truck last night? why did you move the shifter from the right to the left side of the column?" and the driver's union demanding "your drivers need a week paid leave to train them on these new safety features" and the mechanics complaining "what's going on here? I stockpiled a year's supply of spark plugs and oil filters and now they don't fit!" and building maintenance says "your trucks suddenly got 6 inches taller and wrecked all of our garage doors" and the customer says "sorry, we're going with a different vendor because your trucks are suddenly 5mph slower and can't get here on time any more."

In a large deployment, change is expensive and dangerous. I want my fleet of 1,000 vehicles to work reliably the same way in 5 years as they work today, with only basic maintenance and safety upgrades. I will drive those vehicles into the ground before I let someone else change the specification of my fleet without my authorization.

> **koenn said:**
> My guess is that in such a case, the majority of people will tend to stick with "official". For those people, there are these obvious gaps in Ubuntu's release model - gaps that may be solved by a better designed release model rather than by stop gaps such as backports (and PPA's)

Yes, there are "gaps" in Ubuntu's release model. They are exactly 6 months in duration. They are a "feature not a bug" and I guarantee you that if Ubuntu suddenly backports a lot of post-2008 applications to 8.04, they will have a lot of angry customers.

---

### Post by psusi on 2010-10-07
> **beew said:**
> So if you stick to 1990 technology you will be bug free? Like I said, this is striaght out of the abstinace school of safe sex.

BTW, I don't believe a feature update on an end user software like OOO ,--the OP made the crucial distinction between end user apps and softwares to run the system and we should keep that in mind to avoid strawman arguments,--would introduce more bugs than upgrading the whole OS to a new release (Speaking of which Open Office doesn't even open in Maverick last night's build and pun intended)

Stop engaging in reductio ad absurdum.  If you stick with software that is a year or two old, it will have less bugs ( or at least known bugs with workarounds ) than software released yesterday.  That is how software development works.

Once you start drawing distinctions about which packages should be kept more up to date vs others, then you are who needs to make those decisions because only you know what new features you want enough to risk breaking things, and you are free to do that.  Just because the specific package and version you want isn't already served up for you in the repository does not mean that the release cycle is to blame.

> **koenn said:**
> It's not about being scared. 
Please keep in mind that I'm looking at this from a corporate perspective (which is a valid point of view, as they are part of Ubuntus and Canonical's target market, and LTS's, where these problems are most acute, are targeted specifically at 'businesses')
So it's not about being scared, it's about governance, risk assesment and risk management, liabilities, etc

If you are a buisiness then you can pay them to back port whatever version of whatever program you want.  That is neither here nor there as far as release schedules go.

> **koenn said:**
> Let's do yet another car analogy:
Say a company purchases a large number of cars. Say they come with strong recommendations from the manufacturer, about following the prescribed maintenance schedule, having all maintenance and repairs done by qualified mechanics from authorized dealerships, and only using official spare parts and accessories.

Cars don't get ANY updates.  You got the car you bought, and that's it.  The new 2010 Prius has a solar panel on the roof, but my 2008 doesn't get one, and saying Toyota should not release a new model car every year isn't going to change that.

> **koenn said:**
> My guess is that in such a case, the majority of people will tend to stick with "official". For those people, there are these obvious gaps in Ubuntu's release model - gaps that may be solved by a better designed release model rather than by stop gaps such as backports (and PPA's)

I've shown why a longer release cycle will not get you what you want.  What you want is already provided by backports, just not the specific version of the specific package that you want.

---

### Post by koenn on 2010-10-07
> **snowpine said:**
> Sorry but I have to (respectfully) call "shenanigans" here... are you, in fact, the IT decision maker for a company with a large Linux deployment? Or are you speculating about what you *think* the corporate world needs?
Neither.
I'm a sysadmin and head of the [small] IT department in an SME (~ 175-200 IT users), which is mostly MS Windows, with a couple of Linux servers and applications. I *am* the (de facto) decision maker - as in, if I think we should be migrating to Virtual Infrastructure, it happens, and it happens the way I designed or envisoned it, at the price I agreed with the supplier. So if we were to migrate user desktops to Ubuntu, it would be at my initiative, and by my decision. 

As such, and although a migration at the moment is not feasible, I'm constantly evaluating Ubuntu as a candidate desktop OS, and that includes support, release models, etc. 

good enough ?  

> **snowpine said:**
>  car analogy 
What you're saying her is, essentially,
- go for a stable release (LTS, in Ubuntu terms)
- make sure you have in-house expertise

Well. exactly. 
but inhouse expertise (in the context of this thread : the capacity to backport and maintain apps as required, possible up to maintaining a private, possibly slightly customized repo mirror) is not something an SME can easily afford. I imagine this works well for larger enterprises, though. 

So, for an SME : if LTS doesn't cover your needs, it's a no go - even if a release 6 months later would solve your problem. That's what I've been sayin al along. 

Small anecdote : 
Belgian eID's are smartcards. The give access to a number of governement web applications, a lot of which I need for work. The driverrs for the most popular  smart card reader (promoted by the governement during promotion campains for the eID's and associated web apps), and the middleware to use the certificates on the card's chip, was not available in Ubuntu 6.06. There were a slightly buggy but usefull packages in 6.10.
No backport, and PPA's didn't exist. Compiling from source resulted in errors I could make heads or tails of. 

Now, if I then imagined running Ubuntu at work (for all  users, with  large portion of them needing those web apps for work), I'd have had the following options :
- stick with LTS, wait for the next LTS approx 1 year later - quite a while for something you *need* for work (and embarrassing, as it didn't seem to be a problem for other operating systems)

- switch to 6.10 and sit out the 6 monthly upgrade trouble. I've had people reply to me in this thread that this is simply not done, and i fully agree. 

- move part or all of my users to another OS. No thanks. 

- get someone to build a working package for me, and prepare for trouble at the next LTS-to-LTS upgrade (did I mention that until now, none of the LTS-to-LTS upgrades worked for me, possibly because of straying away from the default setup ?)

All of these are less than optimal. 
Hence my opinion that Ubuntu's release model is flawed.

> **snowpine said:**
> 
On my work computer right now, I'm running CentOS 5.5 (the "free" version of Red Hat Enterprise, which I would happily purchase if I needed the support). It gives me an extremely stable base system (kernel 2.6.18, KDE 3.5, etc.), a 7-year support cycle, and up-to-date end user applications like Firefox 3.6.x and OpenOffice 3.x. It is well-documented, in print and on the 'web, and there are plenty of highly-trained and certified Linux professionals to assist me if I get into a jam.


Canonical knows they cannot possibly compete with this (their entire business model is based on "taking a snapshot of Debian Unstable every 6 months") and so, rightfully, they don't even try. Instead, they do what they are best at (6-month snapshots of the latest Linux desktop innovations) and it seems to be working, as most estimates place them as the #1 consumer Linux distro.

With that CentOS example, you've illustrated that it is not impossible the have a stable system with up to date  end-user apps. 

The question that now remains  is : is it really impossible for Ubuntu to devise a release model that accomplishes the same or a similar  result (without necessarily copying the production and release mechanisms)

They may have proven that they can pull of the 6-monthly snapshot thing, and that there actually is a market for that. Their offerings to customers who want the long term stability still need some adjustment, imo.

---

### Post by koenn on 2010-10-07
> **psusi said:**
> 
Cars don't get ANY updates.  You got the car you bought, and that's it.  The new 2010 Prius has a solar panel on the roof, but my 2008 doesn't get one, and saying Toyota should not release a new model car every year isn't going to change that.
apparently you did not quite get the finer points of  the analogy. See my reply to snowpine for hints. 


> **psusi said:**
> 
I've shown why a longer release cycle will not get you what you want.  What you want is already provided by backports, just not the specific version of the specific package that you want.
I never said I wanted a longer release cicle.

Backports solve some of the problems, at the cost of additional complexity (on the user /sysadmin side), and additional work (on the developers side)
As such, "backports" as a whole seem to have the characteristics of a workaround to a problem in the release model. 
Next step should be: a permanent, structural solution.

---

### Post by snowpine on 2010-10-07
> **koenn said:**
> Neither.
I'm a sysadmin and head of the [small] IT department in an SME (~ 175-200 IT users), which is mostly MS Windows, with a couple of Linux servers and applications. I *am* the (de facto) decision maker

Cool! It is always good to hear from people who are "in the trenches" and I value your contributions to the forum. Sorry if I was dismissive of your expertise earlier. :)

> **koenn said:**
> The question that now remains  is : is it really impossible for Ubuntu to devise a release model that accomplishes the same or a similar  result (without necessarily copying the production and release mechanisms)

A good question. My gut feeling is "yes, it is impossible for Canonical to achieve this." Their primary expertise is as repackagers and marketers of other people's work (primarily Debian). It has been said a thousand times before, but I'll say it again: if you are looking for "a stable Ubuntu," it is called "Debian Stable." Debian was around for years before Ubuntu and will probably be around long after. 

I do think Ubuntu has the know-how to create and market an enterprise "spin" based on Debian Stable, with 5-10 years of paid subscription updates and support (Debian Stable only gets 3 years of updates, and has no official paid support that I'm aware of), a great look-and-feel, and some key business partners. Ubuntu would then become Canonical's "Fedora." However, I have seen no indication that Canonical intends to move in this direction. (Plus they would have to name it something else due to the "Ubuntu will always be free" promise.)

Anyway, you can probably tell from my "beans" that I am an Ubuntu enthusiast and will defend their release cycle until I'm blue in the face. :) That being said, I haven't used Ubuntu on my home computers in a couple of years, and I certainly wouldn't use or recommend it in the enterprise, no more than I would use my Honda Civic to haul a cord of wood. What Ubuntu **is** is a snapshot release that showcases the latest "oooh! ahhh!" that desktop Linux has to offer and converts new enthusiasts to Linux. In my opinion, your suggestion runs counter to this goal by negating the need to update to the latest release every 6 months, which is the primary catalyst for the project's forward momentum and innovation.

---

### Post by psusi on 2010-10-07
> **koenn said:**
> 
Small anecdote : 
Belgian eID's are smartcards. The give access to a number of governement web applications, a lot of which I need for work. The driverrs for the most popular  smart card reader (promoted by the governement during promotion campains for the eID's and associated web apps), and the middleware to use the certificates on the card's chip, was not available in Ubuntu 6.06. There were a slightly buggy but usefull packages in 6.10.
No backport, and PPA's didn't exist. Compiling from source resulted in errors I could make heads or tails of. 


Again, you are saying that the specific version of the specific application you needed was not backported.  That does not mean that the release cycle is flawed, it just means that the specific version of the specific package of specific interest to you at the time was not backported.

> **koenn said:**
> 
Backports solve some of the problems, at the cost of additional complexity (on the user /sysadmin side), and additional work (on the developers side)
As such, "backports" as a whole seem to have the characteristics of a workaround to a problem in the release model. 
Next step should be: a permanent, structural solution.

Again, as soon as you can find the magic bullet of software development that allows you to both develop new features, and reduce bugs at the same time, there is no known way to accomplish that.  Changing the release cycle certainly won't.

---

### Post by nikefalcon on 2010-10-07
Maybe you should try Debian-testing or Debian stable. For new software add repos for testing and unstable.

---

### Post by LifeTheHound on 2010-10-07
> **psusi said:**
> [To "Why does the Ubuntu make new distribution releases so compulsively?"] To avoid being stuck with old, outdated software.  It takes a certain amount of manpower to get the latest software, build it, test it, and fix some bugs in the development release.  It takes more manpower to then back port it to an older release.  It seems they don't have enough spare manpower for a whole lot of backporting.
Thanks -- that's an excellent statement of the problem and a major reason for this alternative idea, which is intended to overcome precisely this issue (and many others, as mentioned).  By the way, who is this Mark to whom you recommend I make contact? Surely not Mr. Shuttleworth himself?

> What about people that just want to stick on the same versions of software (such as gwibber, gimp, etc), but still get security updates? Wouldn't the OPs idea mean that these apps are getting updated as well?
As I have mentioned elsewhere in the thread, it is perfectly acceptable to opt for security-/bugix-only updates. With my idea, it's literally a matter of marking a single checkbox in "Software sources."

> What you choose between is having the latest and greatest features, or the older version without all of the bells and whistles, but that has been better debugged. The OP wants both.
Yes. Again, the simple checkbox mentioned above and below is a very feasible answer from the user's side. 

> There is a security repo that hosts the security updates. then there is -backports and -updates
Yes. Under this new system, this particular feature is maintained (albeit with subtle changes, as mentioned), and testing of potential "backports" en masse is performed with a backports-proposed repo for testers and enthusiasts. However, "backports," again, would follow the guidelines already established (consult the wiki), with individual package eligibility (to be considered "backports") pre-assigned to all packages. No system-level packages would be approved, ideally, so overall system stability would not risk being compromised even while running backports-proposed. Manpower, like I mentioned, would be readily available by diverting it from the current 6-month release cycle. This would also solve the other practical problems (hardware compromises, support periods, multi-distro maintenance issues, etc).

> You do realize that, regardless of which Ubuntu release you're using, you can always get the latest Firefox from mozilla.org, the latest OpenOffice from openoffice.org, the latest Gimp from gimp.org, and so on?
Of course. But equally valid to this point are the observations I made previously about the ease and organization of software upgrades. The firefox from mozilla.org does not play well with KDE, and it forces a different list of dependencies than Ubuntu's compile, not to mention the Ubuntu branding and integration often suffers. Of course, it also requires more work. OpenOffice requires the download of many .deb files, tweaking symlinks and menus, and uninstalling the old files, not to mention the risk of losing Ubuntu's theming and KDE integration. The debs must be installed simultaneously or in a specific order. This requires significant amounts of work and expertise. Other software requires recompilation, and some compilation requires specific tweaks and new dependencies. Essentially, users are forced to rebuild their distro to keep all "user software" up to date, risk breakage, lose much of the automatic update features often praised in Ubuntu, and so forth. The list of cons is staggering and leads us right back to square one, another powerful reason behind my idea. 

Koenn sums it up nicely, "[That which you mention] is fine for a hobby project or a home user with a bit of knowledge, but, unless I'm misinformed, Canonical's target audiance with Ubuntu is way wider than that." "Ubuntu for people" and all that, I suppose. Also:
> If you are scared to go outside the "official recommendation" then guess what? You must accept the way that Ubuntu chooses to do things (or get involved with the project and mold it to your vision). 
Well said. There is a lot of excellent delivery framework in place. The problem is to align the "way that Ubuntu chooses to do things" and this proposed solution to most (if not all) of the practical problems caused by deviating from recommended, elegant practice, thereby averting the list of cons explained above. Speaking of said list,

> 
Peanuts have been removed from school cafeterias and airline snacks due to allergy concerns; does this mean they are not a healthful and delicious food for diners aware of the risks?
:) If only the time, effort, and risks taken on with a manual, experienced, high-maintenance, and sometimes even impossible approach were as easy as deigning not to reach for a jar of peanuts. The point is, it's quite feasible to have the best of both worlds in the same simple, recommended, low-maintence, hands-off, managed framework while of course *still* maintaining the freedom for tweakers and daredevils to do precisely as they please. I daresay you'll still be quite happy under this new system yourself--unless you like playing with bleeding-edge system software, drivers, and whatnot inherent to the current 6-month release model. But even so, xorg-edgers, kernel-ppa, and other such experimental PPA's provide a comparable minefield experience even in stable releases. In other words, many of cons of the current model can still be willfully taken upon oneself, if so desired, even within the new system. I simply argue from the standpoint of common sense that the masses might not appreciate having all of the above practical issues forced upon them. Truly, to each his own, especially within this new proposed system. The key difference in this case is that under the new system, such "pain" would then be optional (and non-default). :P

> As an example, 8.04 uses OpenOffice 2.4. Is OO 2.4 "obsolete"? I say "no" My apologies for what might at first glance seem like a mere difference in opinion, but from a practical standpoint, had you read the concrete examples I've written, you'd see that even this particular instance of the general problem clearly deserves a "Yes, it is obsolete." Many other pieces of software are also obsolete by similar reasoning. Here I define obsolete from a purely practical standpoint: it does not support current formats, and essential/competitive feature parity is not maintained. In Hardy, as per your example, the media player doesn't support some emerging formats, OpenOffice 2.4 does not support many of the new table features in docx, nor does its spreadsheet support many essential regression functions, and the lack of compatibility and features itself is also becoming burdensome in a real-world college/work environment inundated with recent releases of Office. Even under this definition, simply desiring "bells and whistles" (in addition to the allure of having some cool new feature[s]) shouldn't be so readily frowned upon in context of mainstream users, for such a seemingly trivial reason alone is reason enough for other operating systems to gladly offer their users this choice (which, in my experience, is often almost universally taken up). With Ubuntu, the choice simply doesn't exist in any feasible or practical way for the mainstream. Not to mention the ability to chose between the two aforementioned repositories ("stable" and "backport"-like) and even pick and chose between the two in the case of exceptions (via "pinning" and whatnot) leaves very little to be desired either way. In this way (and many others), this proposed system offers the best of both worlds. For this reason...
> You want the new features without the new bugs, but I'm sorry to tell you that just isn't possible.
...this conclusion is unwarranted, again as a result of possible misunderstandings. The answer as I've outlined simply allows the choice of either. The choice of both is simply impossible unless the newer version is more stable (KDE). Some food for thought, though, is that bugfix updates of newer major versions may actually cause software to *become* significantly less bug-ridden *within a distro's release cycle* under the current system. Version 3.0.1 ('stable' repo) may be far buggier than 3.2.4 (new 'backports' repo). In fact, KDE 4.5.2 is already significantly less buggy than 4.4.x, partly as a result of the improved focus on stability in this major release cycle of KDE. It's not black and white either way, and the ability to choose greatly ameliorates both issues in the sense that the user can stick with (or jump to) whichever of the two (new or old release cycle) that suits him, all within the same framework. There's a reason many windows programs keep themselves up to date with the latest release versions, which people seem to enjoy. Conversely, there's a reason debian keeps much older versions of software in its repos, which others seem to enjoy as well. The point is it's perfectly feasible in this proposed system to have both models in place concurrently, distinguished by the user's selected repository, and all made possible by the investment of work that would otherwise go into creating all-new releases every few months. 

It deserves mention at this point that all of this is just one of the ways the proposed system would be superior to the current. The others, of course, are the indirect effects of the cycle as mentioned earlier: forced base system upgrades every 6 months (and the attendant probability for complete/minor system breakage, with all ramifications thereof), the manpower argument, and so forth.

One last thing: It's fantastic there's excitement from the corporate community about this idea. Although I do believe it serves the corporate community's best interests to have a perfectly feasible system which engenders the possibility of a choice between the "stable old" and "new, up-to-date (but not beta or system-stability-compromising)," I initially proposed this for the standpoint of popular users, "the masses." That said, I don't believe any harm can come to companies or corporate users with such a system that allows for what is essentially a refocused LTS-only system from which it is trivial to opt out (or "not to opt into") using the repository containing the latest versions of user software ('backports'). That said, because of this system's emphasis on a stable base of unchanging, security-updated system components and rolling user software releases (the latter only if selected), it should not pose a corporate problem. 

The black-and-white dichotomy implying the lack of simple choice between a stable and backport repository is not the case at all with this system. I might suggest you return to read the details of my proposal (if you haven't already) if you harbor any lingering qualms to this effect.

---

### Post by koenn on 2010-10-08
> **snowpine said:**
> What Ubuntu **is** is a snapshot release that showcases the latest "oooh! ahhh!" that desktop Linux has to offer and converts new enthusiasts to Linux. In my opinion, your suggestion runs counter to this goal by negating the need to update to the latest release every 6 months, which is the primary catalyst for the project's forward momentum and innovation.
Yes, it's clear that Ubuntu is one of Canonical's main strategies is to drive innovation and marketability of Free Software, and that that is where the 6-montly cycle is for. 


On the other hand, they also claim > Ubuntu is a great way to streamline your business operations.  ...  provide essential stability for enterprise deployments ...  Ubuntu Desktop is perfect for work ...   -- [http://www.canonical.com/about-ubuntu/for-business](http://www.canonical.com/about-ubuntu/for-business)
I'm saying they're not doing so great in that department, and their release model is an issue here, for reasons I already explained.

---

### Post by koenn on 2010-10-08
> **psusi said:**
> Again, you are saying that the specific version of the specific application you needed was not backported.  That does not mean that the release cycle is flawed, it just means that the specific version of the specific package of specific interest to you at the time was not backported.
No, I'm saying there was no usable version . 
I wasn't looking for a specific version, or something newer than I already had, or specific features of a given program. Any version, as long as it runs and provides basic functionality, would have been OK. 


As it happens, in the smart card example I provided earlier. 2 out of 3 of the required 6.10 packages could be made to run on 6.06 simply by manually overriding the dependencies (I made it ignore version numbers when checking for dependencies, and it installed by depending on the versions already present on the system)- which means these packages were artificially, unnecessarily  tied to the 6.10 release. 
I find that silly. 


> **psusi said:**
> 
Again, as soon as you can find the magic bullet of software development that allows you to both develop new features, and reduce bugs at the same time, there is no known way to accomplish that. 
It's called testing. 
It's not exactly a magic bullet, and it's not entirely unknown. Debian has been doing it for years.

(and no, this is not intended to spark a Ubuntu vs Debian argument, this is not an argument for longer release cycles, and I'm not saying Debian's approach is the *only* way - just pointing out new featuers and acceptable risk levels are not mutually exclusive)

---

### Post by danbuter on 2010-10-08
I agree with the OP. There is no reason (other than laziness) that programs like OpenOffice should not be kept up to date. Ubuntu has already proven this by updating Firefox regularly.

---

### Post by papangul on 2010-10-09
The version of the popular youtube client Minitube in the lucid repos is frozen at 0.9: [http://packages.ubuntu.com/lucid/minitube](http://packages.ubuntu.com/lucid/minitube)
Heck! Even version 1.0 stopped working long ago! The current version(only version that works) is 1.1.

The ppa system is good for selectively installing/upgrading a few packages only, but having to resort to ppa for everything is a hassle and it also feels somewhat stupid to do things that way(inspite of having a great centralized package management system which can potentially address this issue).

---

### Post by guimaster on 2010-11-16
> **mikewhatever said:**
> I've read through the thread and started thinking. "It's not the first time these questions are raised on the ubuntuforums.org. What do people actually want to achieve by posting them here? Do they think Ubuntu users around the world would travel to London and storm Canonical offices demanding changes? Probably not. Do they think Ubuntu devs might visit the forums all at once, see these threads and decide to make a change? Unlikely, but I don't know. Is there any reason at all, other then nonconstructive criticism and being moved to the recurring section? Surely, if these guys really wanted to make Ubuntu software more current, they'd be discussing things [were the decisions are made]("https://lists.ubuntu.com/archives/ubuntu-devel/2010-July/031025.html") or just packaging more recent software. What are the merits of posting rants on forums? Can somebody explain?
...and why is it that Window7 always creeps up into these rants? Should anyone here care that it works for you? I mean, sure, and I am happy it does, but why waist readers' time by prising something that has 3 million Google hits for 'Windows7 crashes' on the Ubuntu forums?
 
 I think the reason the rants keep returning is because the frustrations continue to occur. New people come to Ubuntu, download the LTS and think they are set. After-all, they do advertise software updates for 3 years, right? Then the ugly truth sets in that the programs in the Repos are growing outdated. People then begin to wonder what is wrong, "why haven't the program versions updated?" Then they begin to search online for answers and then they learn the ugly truth, that they have to upgrade the entire OS in order to get new versions of software in the Repos! This is an extremely frustrating realization that every new user to Ubuntu eventually and inevitably faces!
 
 New users to Ubuntu expect that the operating system will work just like Windows or Mac, that you can constantly get access to new software for your old operating system. Yes, after 5-10 years the new apps and games stop coming, but that is a reasonable time frame for people to be expected to upgrade. 3-5 years to upgrade to a new version of the OS is considered normal by the general public, not every 6 months just to stay compatible!
 
 Can you imagine buying a Macintosh computer and only having access to software that was current when you bought the Mac? No new software unless you purchase and download the new version of the OS? If Apple ran their business like that you could bet they would be out of business pretty quick. Therefore, if Apple and Microsoft would go out of business with a program like that, how do we expect that Ubuntu should succeed amongst the masses?
 
 I stick with Ubuntu because I don't like Big-Brother spying on me. I backed up the Restoration Partition on my new Netbook in case I ever wanted to use Windows 7 for some reason, but then I wiped the drive and loaded Ubuntu on by itself. Now I have some quirky bugs to deal with (10.10) and I am wondering if 10.04 would be better because it is LTS. So the downgrade appeals to me. But as appealing as having an LTS is, I realize that my packages would slowly grow outdated. So basically I am continually banging my head against the wall between stability and new software. Why do I have to choose between the two? Why can't we have both at the same time? 
 
 Ubuntu will not succeed with the masses unless people can have both stability and the latest software, all available in one neat package!

---

### Post by guimaster on 2010-11-16
> **psusi said:**
> *What?*
 
You DON'T have to upgrade every release, but that has nothing to do with my comment you replied to. What I said is that having the latest and greatest software is the exact opposite of sticking with older, more well tested versions. The OP seems to want both at the same time.
 
Stable = out of date. You can't have software that is both new, and stable.
 
Why is Macintosh capable of this and Ubuntu not so? Mac is stable and up-to-date. It isn't perfect, but it is what Shuttleworth and Canonical are chasing after, correct? I'm glad they are fixing these tiny bugs that make Linux difficult to use. Now it's time to quash the big bugs like this one, or they aren't going to reach their goal of an equal experience with Mac.
 
 No I am not a Mac fanboy either. I have never owned one. But my years of working in Tech Support and fiddling around with computers - and enjoying doing so - have come to an end. Now I just want something that works...

---

### Post by snowpine on 2010-11-16
If you purchase a Windows computer and do nothing, your applications will slowly become out of date.
If you purchase a Mac computer and do nothing, your applications will slowly become out of date, too.
Likewise, if you install Ubuntu and do nothing, your applications will also slowly become out of date.

I fail to see how it is an Ubuntu-vs-Mac-vs-Windows issue. In all three cases, action is necessary on the user's part to obtain the latest applications. The only difference with Ubuntu is that these applications are free...

---

### Post by guimaster on 2010-11-16
> **tgm4883 said:**
> What about LTS and upgrading specific software from PPA's?
 
There are two problems with PPAs. Firstly, they are not perfectly simple for new users. Secondly, most programs do not have them. I visited the RKHunter site today to have a look and all I could find was a tarball installer. This is the norm for Linux software, not the exception.
 
 The ideal would be for all programs to appear as .deb installation files, as Windows users would simply need to adjust from .exe extensions to .deb extensions when installing new software. But there is simply no way to force all of these developers to create .deb files compatible with each currently supported version of Ubuntu. If only Download.com stocked .deb file downloads!!!
 
 GuiMasTER

---

### Post by guimaster on 2010-11-16
> **snowpine said:**
> If you purchase a Windows computer and do nothing, your applications will slowly become out of date.
If you purchase a Mac computer and do nothing, your applications will slowly become out of date, too.
Likewise, if you install Ubuntu and do nothing, your applications will also slowly become out of date.
 
In all three cases, action is necessary on the user's part to obtain the latest applications. The only difference with Ubuntu is that these applications are free...
 
Let's quickly compare taking this "action" on an Ubuntu OS, a Windows OS and a Mac OS:
 
Ubuntu: Open the "Software Center" find the application and click install. An **_out-dated version_** of said program is downloaded and installed.
 
Windows: Open your browser and visit Download.com. Find the application and click install. An **_up-to-date version_** of said program is downloaded and installed.
 
Macintosh: Visit a website offering Mac Downloads. Find the application and click install. An **_up-to-date version_** of said program is downloaded and installed.
 
I quite imagine Download.com wouldn't exist today if they didn't always have the latest program versions available for download.

---

### Post by psusi on 2010-11-16
> **guimaster said:**
> I think the reason the rants keep returning is because the frustrations continue to occur. New people come to Ubuntu, download the LTS and think they are set. After-all, they do advertise software updates for 3 years, right? 

No, they don't advertise software updates for 3 years.  You get *support* for 3 years, which means critical bug fixes, not updates to the latest and greatest version of everything.

> **guimaster said:**
> New users to Ubuntu expect that the operating system will work just like Windows or Mac, that you can constantly get access to new software for your old operating system

Which involves you manually going out and downloading a new version of the program and installing it, which you are perfectly free to do on Ubuntu.

> **guimaster said:**
> Yes, after 5-10 years the new apps and games stop coming, but that is a reasonable time frame for people to be expected to upgrade. 3-5 years to upgrade to a new version of the OS is considered normal by the general public, not every 6 months just to stay compatible!

It is only considered "normal" because that is how pathetic Microsoft has been with their last few releases.  When they first released Windows NT 3.1, their release schedule was to have a service pack for critical bug fixes every quarter, and a new OS release every 12-18 months.  Releases since NT 4.0 have continuously slipped further and further behind schedule.
 
> **guimaster said:**
> Can you imagine buying a Macintosh computer and only having access to software that was current when you bought the Mac?  No new software unless you purchase and download the new version of the OS? If Apple ran their business like that you could bet they would be out of business pretty quick. Therefore, if Apple and Microsoft would go out of business with a program like that, how do we expect that Ubuntu should succeed amongst the masses?

You DON'T get new versions of all of the programs that they ship; why do you think they DO ship a whole new OS release every year or so it seems?
 
> **guimaster said:**
> So basically I am continually banging my head against the wall between stability and new software. Why do I have to choose between the two? Why can't we have both at the same time?

Because that is the nature of software development.  You make changes, add new features, etc, and you inevitably introduce new bugs.  The one method that has been developed to produce "stable" software is to stop making feature enhancements, and focus only on fixing existing bugs, which is exactly why you find yourself using "old" software.

> **guimaster said:**
> Ubuntu will not succeed with the masses unless people can have both stability and the latest software, all available in one neat package!

Again, nobody in the world has yet to figure out how to accomplish that.  When you do, let us all know.

> **guimaster said:**
> Why is Macintosh capable of this and Ubuntu not so? Mac is stable and up-to-date.

They aren't.  You don't get the new OS until you upgrade to the new OS, which has been what?  About every 6-12 months the last few releases?

---

### Post by snowpine on 2010-11-16
> **guimaster said:**
> Ubuntu: Open the "Software Center" find the application and click install. An **_out-dated version_** of said program is downloaded and installed.

With Ubuntu, you get *two* choices when installing an app, not just one choice like Mac or Windows.

1. You can download a stable version from the Ubuntu repos that's been tested specifically your release. 

or

2. You can download the latest version from download.com (or another site) just like a Windows or Mac user.

Mac and Windows users don't really have the benefit of a central, stable software repository like we do. It is good for users to have a sane default configuration *and* good for developers to have a stable platform for coding--a win-win. :)

---

### Post by NCLI on 2010-11-16
> **snowpine said:**
> With Ubuntu, you get *two* choices when installing an app, not just one choice like Mac or Windows.

1. You can download a stable version from the Ubuntu repos that's been tested specifically your release. 

or

2. You can download the latest version from download.com (or another site) just like a Windows or Mac user.

Mac and Windows users don't really have the benefit of a central, stable software repository like we do. It is good for users to have a sane default configuration *and* good for developers to have a stable platform for coding--a win-win. :)
or

3. You can add a PPA.

Currently, PPAs aren't rated on trust, and are still hard to add for new users. However, this is set to change in 11.04, making them a viable option for new users and power users alike.

---

### Post by Merk42 on 2010-11-16
I wonder how Mac will handle updates in the Mac App store...

---

### Post by uRock on 2010-11-17
I can appreciate Ubuntu's release cycle. 

People can easily download the newer version from source and install it. I do that with VBox and Thunderbird and I have had very little problems with installing them.

On the other hand, those who are more dependent on having a secure machine an have one. All one has to do is stay with the old versions, that have been well patched for security.

Ubuntu has done better with 10.04, because it has been upgrading the firefox versions as they release. Just as Firefox in Windows does. Google Chrome does this as well.

---

### Post by Merk42 on 2010-11-17
> **uRock said:**
> Ubuntu has done better with 10.04, because it has been upgrading the firefox versions as they release.
Riiiight.
We'll see how long after Firefox 4 is release that you get it in 10.04.

---

### Post by beew on 2010-11-17
> **Merk42 said:**
> Riiiight.
We'll see how long after Firefox 4 is release that you get it in 10.04.

I will get it pretty soon because I have added the Mozilla ppa. Now I am getting the betas right the way. :)

---

### Post by beew on 2010-11-17
> **uRock said:**
> 

People can easily download the newer version from source and install it. I do that with VBox and Thunderbird and I have had very little problems with installing them.


Yeah, but then it is outside of the package management system. You are not supposed to do that if you adhere to the 'official' Ubuntu way. I have no doubt that installing from source  would be considered  extremely "risky" by those who insist we need a 6 month feature freeze  to ensure that things don't break. 

So you're basically saying that Ubuntu's scheme is reasonable because you have the know how to circumvent it (installing from source is not easy for newbies) Well it doesn't sound logical to me. If it is so reasonable you shouldn't have to circumvent it!

The repo is a big selling point to new users. How many times have you heard someone telling new users on the forum that Ubuntu is so easy because you get all the softwares in the repository and all you need to do is highlight and click and all the updates will be taken care of, unlike in Windows where you have to search the net etc etc? I heard that a lot. Now if you have to install from source to keep yourself updated it would undermine the advantage of the repo quite a bit.

I install almost all applications I can name from PPAs. I download a tar ball or a .deb package only occassionally when there is no PPA. 

I manage to keep my system up to date with PPAs and even mixing repos (I have Maverick stuffs installed in Lucid and have broken things along the way but so far always manage to get out of the trouble.) Since PPAs are supposed to be potentially unstable I too am circumventing the official way of doing things.

---

### Post by pickarooney on 2010-11-17
I broadly agree. There's nothing as frustrating as upgrading to a new version of a distro only to find that some of your hardware no longer works and there are new problems with sound and video. It happens all the time with Ubuntu.

---

### Post by psusi on 2010-11-17
> **pickarooney said:**
> I broadly agree. There's nothing as frustrating as upgrading to a new version of a distro only to find that some of your hardware no longer works and there are new problems with sound and video. It happens all the time with Ubuntu.

This statement seems to have nothing to do with this thread.

---

### Post by uRock on 2010-11-17
> **beew said:**
> Yeah, but then it is outside of the package management system. You are not supposed to do that if you adhere to the 'official' Ubuntu way. I have no doubt that installing from source  would be considered  extremely "risky" by those who insist we need a 6 month feature freeze  to ensure that things don't break. 

So you're basically saying that Ubuntu's scheme is reasonable because you have the know how to circumvent it (installing from source is not easy for newbies) Well it doesn't sound logical to me. If it is so reasonable you shouldn't have to circumvent it!

The repo is a big selling point to new users. How many times have you heard someone telling new users on the forum that Ubuntu is so easy because you get all the softwares in the repository and all you need to do is highlight and click and all the updates will be taken care of, unlike in Windows where you have to search the net etc etc? I heard that a lot. Now if you have to install from source to keep yourself updated it would undermine the advantage of the repo quite a bit.

I install almost all applications I can name from PPAs. I download a tar ball or a .deb package only occassionally when there is no PPA. 

I manage to keep my system up to date with PPAs and even mixing repos (I have Maverick stuffs installed in Lucid and have broken things along the way but so far always manage to get out of the trouble.) Since PPAs are supposed to be potentially unstable I too am circumventing the official way of doing things.
If one requires the latest and greatest at all times, then use Arch, Debian testing, LMDE, or install programs via the sources .debs. I do not see anything wrong with using the current version of Firefox for a while until the next LTS is released.

If one sticks with the repo versions of programs, then they will work and they will be secure. I don't consider installing programs from source as circumventing anything. It just means you will have to make sure you are getting a secure version of the new software and that you will have to create custom AppArmor profiles for the software, which is not very easy.

The only PPAs I use outside of Ubuntu's are VirtualBox's and Chrome's.

---

### Post by guimaster on 2010-11-17
> **psusi said:**
> This statement seems to have nothing to do with this thread.
 
I disagree, please read the opening post in this thread.
 
> **snowpine said:**
> With Ubuntu, you get *two* choices when installing an app, not just one choice like Mac or Windows.
 
1. You can download a stable version from the Ubuntu repos that's been tested specifically your release. 
 
or
 
2. You can download the latest version from download.com (or another site) just like a Windows or Mac user.
 
Mac and Windows users don't really have the benefit of a central, stable software repository like we do. It is good for users to have a sane default configuration *and* good for developers to have a stable platform for coding--a win-win. :)
 
Regarding the responses to my posts in this thread, I have come to a conclusion. The responsibility to make applications easier to install shouldn't fall on the Ubuntu devs, but rather on the developers of each individual Linux application. Software created for Windows is created with an "executable" installer, for ease of installation by the user of Windows. Linux app devs **directly** affect Linux adoption rates by their choice to make their program updates difficult to install or easy to install.
 
However, with Ubuntu releasing new versions every 6 months, Canonical is actually discouraging developers from making direct software installation easier! Why should they make the effort when they can have a new version added to a repository every 6 months? So then either become a Linux geek or be annoyed by the complexity of adding updates. The frustrations regarding updates for software will continue for new users and Linux adoption rates will suffer.
 
 Installation of updated software has to become easier during an LTS lifespan! Perhaps if there was a simple gui program designed to make adding PPAs easier that would help? I also know there is a website called: "GetDeb" that acts as a kind of "Download.com" for Ubuntu, which is a great start. .Deb is the easiest way for a newbie to install updated software.

---

### Post by snowpine on 2010-11-17
> **beew said:**
> Yeah, but then it is outside of the package management system. You are not supposed to do that if you adhere to the 'official' Ubuntu way. I have no doubt that installing from source  would be considered  extremely "risky" by those who insist we need a 6 month feature freeze  to ensure that things don't break. 

So you're basically saying that Ubuntu's scheme is reasonable because you have the know how to circumvent it (installing from source is not easy for newbies) Well it doesn't sound logical to me. If it is so reasonable you shouldn't have to circumvent it!

Have you ever heard the phrase "open-source software"? Installing an application from its source is a basic "Linux 101" skill. You can choose not to exercise this skill if you wish. Lots of people happily get through life without ever learning how to drive stick-shift, use a power tool, or bake a loaf of bread.

---

### Post by psusi on 2010-11-17
> **guimaster said:**
> I disagree, please read the opening post in this thread.

Huh?  This thread is about Ubuntu shipping and maintaining stable releases rather than constantly tracking the most up to date, and therefore untested and buggy.  This statement has nothing to do with that:

> **guimaster said:**
> I broadly agree. There's nothing as frustrating as upgrading to a new version of a distro only to find that some of your hardware no longer works and there are new problems with sound and video. It happens all the time with Ubuntu.


> **guimaster said:**
> Regarding the responses to my posts in this thread, I have come to a conclusion. The responsibility to make applications easier to install shouldn't fall on the Ubuntu devs, but rather on the developers of each individual Linux application. Software created for Windows is created with an "executable" installer, for ease of installation by the user of Windows. Linux app devs **directly** affect Linux adoption rates by their choice to make their program updates difficult to install or easy to install.

No, Windows software uses an executable installer because Windows has no package manager.  It is a terrible system with many flaws, and even Microsoft is trying to move away from it and have developed their own package manager and are pushing developers to distribute MSI installation packages instead of executable self installers.

The developers of open source software CAN NOT provide such a broken installer because there are so many different versions of Linux, and other POSIX operating systems out there which they support.

> **guimaster said:**
> However, with Ubuntu releasing new versions every 6 months, Canonical is actually discouraging developers from making direct software installation easier! Why should they make the effort when they can have a new version added to a repository every 6 months? So then either become a Linux geek or be annoyed by the complexity of adding updates. The frustrations regarding updates for software will continue for new users and Linux adoption rates will suffer.

Yes, releasing even LESS often so people are stuck with even OLDER software is a perfect way to alleviate frustration about having old software.  :rolleyes:
 
> **guimaster said:**
> Installation of updated software has to become easier during an LTS lifespan!

Enabling the backports repository and getting automatic updates seems pretty easy to me.  Granted there isn't enough in the backports repository, but that's a problem of not enough, rather than flawed system.

---

### Post by koenn on 2010-11-17
> **snowpine said:**
> Have you ever heard the phrase "open-source software"? Installing an application from its source is a basic "Linux 101" skill. You can choose not to exercise this skill if you wish. Lots of people happily get through life without ever learning how to drive stick-shift, use a power tool, or bake a loaf of bread.

that's incorrect.
Yes, building from source is the original method of distributing open source software, and it's an adequate method of doing so. One of the advantages is that it's highly customizable, and an easy way to achieve cross-platform portability. 

However, as early as 15 or more years ago, "distro's" started delivering the software in compiled form. For modern, 'mass-market"-oriented distro's like Ubuntu, repositories of compiled software are the preferred, or even the only official, supported method of delivering software to its the user base.
So beew is right: if Ubuntu's approach only makes sense if you know how to circumvent it, that means it's flawed.

---

### Post by cchhrriiss121212 on 2010-11-17
> **koenn said:**
> 
So beew is right: if Ubuntu's approach only makes sense if you know how to circumvent it, that means it's flawed.
But it is only flawed if you care about having the latest software, in my experience most users do not even know what version of software they are using.
Software that is 18 months old is fine for 90% of users, the ones that are in the 10% are free to learn to install PPAs or compile.

---

### Post by snowpine on 2010-11-17
> **koenn said:**
> However, as early as 15 or more years ago, "distro's" started delivering the software in compiled form. For modern, 'mass-market"-oriented distro's like Ubuntu, repositories of compiled software are the preferred, or even the only official, supported method of delivering software to its the user base.
So beew is right: if Ubuntu's approach only makes sense if you know how to circumvent it, that means it's flawed.

I just don't buy this argument, sorry. It's like saying, "My car's design is flawed because I need snow tires in the winter." If you live in a warm climate and the factory-preinstalled all-season tires meet your needs, good for you... However, the ability to easily install tires appropriate to my local driving conditions is a "feature not a bug" of the car's design. 

Now maybe you can argue that, "Turning a series of lugs counter-clockwise is arcane and unintuitive to the average user; why can't we change tires using velcro or a zipper?" but surely you are not arguing that the factory-installed tires should be permanently attached to the axle! :)

---

### Post by koenn on 2010-11-17
> **cchhrriiss121212 said:**
> But it is only flawed if you care about having the latest software, in my experience most users do not even know what version of software they are using.
Software that is 18 months old is fine for 90% of users, the ones that are in the 10% are free to learn to install PPAs or compile.
That's true as well (and I think I made a similar point somewhere in this thread - but hey, it's we're in recurring)

imo, the obsession with 'the latest version' only makes sense if a newer version fixes a problem that your current version doesn't. In all other cases : your current software doesn't magically stop working when a new version is released. It served you well so far - what's the rush to upgrade ?


also software releases in open source work differently from those on other platforms, say Mac or Windows. 
the commit of a bugfix to a public svn is not a new release, and does not mean you can expect the patched program to be delivered to you the next day. 
Also, the release of a new version on sourceforge or a project's website only means they think 'the source code is ready' - to build it into a working program for an existing system still requires compiling it, possibly in a number of different configurations, and integreting the result in and  testing it against the system(s) it will be made available to. So a program's version number 'lagging behind' against what's available on the project's website does not (automatically) mean the software is old or outdated.

---

### Post by koenn on 2010-11-17
> **snowpine said:**
> I just don't buy this argument, sorry. It's like saying, "My car's design is flawed because I need snow tires in the winter." If you live in a warm climate and the factory-preinstalled all-season tires meet your needs, good for you... However, the ability to easily install tires appropriate to my local driving conditions is a "feature not a bug" of the car's design. 

Now maybe you can argue that, "Turning a series of lugs counter-clockwise is arcane and unintuitive to the average user; why can't we change tires using velcro or a zipper?" but surely you are not arguing that the factory-installed tires should be permanently attached to the axle! :)

Nice try, but my (and, i assume, most people's) software needs don't change with the weather, and, unlike tires, programs don't wear from usage, so the analogy doesn't quite work out.

Also, since car analogies are fun, 
As soon as my car is 3 years old, I know there'll be a new model, most likely slightly "better" 'more modern' 'more feature rich' ... than what I'm driving. So I *want* those new seats with the sexy colors, and the slightly larger engine but at the dealership they tell me : we don't sell those engines and seats separately because we can't guarantee they'd actually fit on your current car, so you have to get the whole car, but we can offer you a handsome trade-in on your old car. 
Is that a flaw in the car design ? a flaw in their way of doing business?

---

### Post by uRock on 2010-11-17
With the car analogies, it is like expecting the manufacturer to call you in for a free upgrade every time they design parts for the next model. We know that they would go broke trying to do that.

The same goes with expecting the Canonical devs to update all of the dependencies so that they can offer the newer version of a program, while at the same time people would expect them to keep the old versions as well, because some people don't care about upgrading to the latest when their current version makes them happy.

IMHO, they can't make everyone happy and if someone really needs the latest and greatest at the moment it is released, then maybe another distro would suit their needs. I think Canonical does a great job at keeping the LTSs as stable as possible while offering reasonable versions of popular softwares.

---

### Post by beew on 2010-11-17
> **snowpine said:**
> Have you ever heard the phrase "open-source software"? Installing an application from its source is a basic "Linux 101" skill. You can choose not to exercise this skill if you wish. Lots of people happily get through life without ever learning how to drive stick-shift, use a power tool, or bake a loaf of bread.

That's right. But then it would be unstable and risky according to those who think that you need to have feature freeze for 6 months to ensure things don't break. People who argue that you need to use fossil software to remain safe and secure should be logically against installing from source. Well I have no problem with it as I am not one of these people.

---

### Post by psusi on 2010-11-17
> **koenn said:**
> 
So beew is right: if Ubuntu's approach only makes sense if you know how to circumvent it, that means it's flawed.

Except that it does't only make sense if you know how to circumvent it.  It makes sense because people expect the software they get to work, which means it has been tested for a while rather than being shoved out the door this morning and thrown at you an hour later, completely untested.

> **koenn said:**
> Nice try, but my (and, i assume, most people's) software needs don't change with the weather, and, unlike tires, programs don't wear from usage, so the analogy doesn't quite work out.

I thought it was a pretty good analogy.  For most people, all weather tires are fine, just like for most people, the well tested versions of software in the repository are fine.  If you have special needs, then you are free to go and get the latest version yourself, so quit complaining that the one that car/distibution came with does not meet your special needs.

> **koenn said:**
> Also, since car analogies are fun, 
As soon as my car is 3 years old, I know there'll be a new model, most likely slightly "better" 'more modern' 'more feature rich' ... than what I'm driving. So I *want* those new seats with the sexy colors, and the slightly larger engine but at the dealership they tell me : we don't sell those engines and seats separately because we can't guarantee they'd actually fit on your current car, so you have to get the whole car, but we can offer you a handsome trade-in on your old car. 
Is that a flaw in the car design ? a flaw in their way of doing business?

Of course not.

> **beew said:**
> That's right. But then it would be unstable and risky according to those who think that you need to have feature freeze for 6 months to ensure things don't break. People who argue that you need to use fossil software to remain safe and secure should be logically against installing from source. Well I have no problem with it as I am not one of these people.

Why should they be against YOU installing from source?  You are perfectly free to do that, and when you do, YOU deal with the breakage.  Right now you are asking other people to test out the new stuff, deal with the breakage, then serve it up to you already working and tested, all in only a few days.  That simply isn't realistic.

---

### Post by snowpine on 2010-11-17
> **koenn said:**
> Nice try, but my (and, i assume, most people's) software needs don't change with the weather, and, unlike tires, programs don't wear from usage, so the analogy doesn't quite work out.

Maybe my needs are atypical :) but let me give you a specific example. In my work, I often need to import documents that are sent to me from Windows or Mac users. If I stick with an outdated version of OpenOffice, I may be unable to open documents in the latest MS Office formats.

> **koenn said:**
> Also, since car analogies are fun, 
As soon as my car is 3 years old, I know there'll be a new model, most likely slightly "better" 'more modern' 'more feature rich' ... than what I'm driving. So I *want* those new seats with the sexy colors, and the slightly larger engine but at the dealership they tell me : we don't sell those engines and seats separately because we can't guarantee they'd actually fit on your current car, so you have to get the whole car, but we can offer you a handsome trade-in on your old car. 
Is that a flaw in the car design ? a flaw in their way of doing business?

The big difference is that a new car costs a lot of $$$, whereas Ubuntu is free. If consumers could get a new car with the latest features every 6 months for free, cars would become a disposable item for most drivers. (Of course, there would continue to be a thriving sub-culture of drivers who prefer to tinker with older vehicles.)

p.s. I agree with the manufacturer-affiliated dealership's refusal in your hypothetical example--it would be bad business (and arguably unethical) for them to sell you a "frankencar" assembled from disparate components that have not been thoroughly road-and-safety tested to work together as a whole.

---

### Post by koenn on 2010-11-17
> **snowpine said:**
> Maybe my needs are atypical :) but let me give you a specific example. In my work, I often need to import documents that are sent to me from Windows or Mac users. If I stick with an outdated version of OpenOffice, I may be unable to open documents in the latest MS Office formats.
iirc, my first thread in this post said something like "unless the newer version solves a problem the current version doesn't ...".
so, OK. 

> **snowpine said:**
> 
p.s. I agree with the manufacturer-affiliated dealership's refusal in your hypothetical example--it would be bad business (and arguably unethical) for them to sell you a "frankencar" assembled from disparate components that have not been thoroughly road-and-safety tested to work together as a whole.
yes, and the point is that, the way ubuntu is designed, adding programs from outside the repos would be like making it a frankencar. That's the point I originally wanted to make : if you need to resort to a frankenstein solution, something is wrong.   That's way I find the 'you can always compile from source' argument invalid. 

But I also agree with uRock on this:
> The same goes with expecting the Canonical devs to update all of the dependencies so that they can offer the newer version of a program, while at the same time people would expect them to keep the old versions as well, because some people don't care about upgrading to the latest when their current version makes them happy

So, it's a complex issue, and in the end the project makes a judgment call that will suit their vision, but may not suit every possible user. So it goes. 

Otoh, maybe the whole idea of having a monolithic distro, is the wrong idea (no matter how slow or how fast the release cycle is). 
Source distribution would probably have less of these problems, so maybe for open source, a "source code compiling software distribution system' (the way Gentoo and some BSD distro's do it ?)  is a better solution

Or a system with a minimal base, to which the user can add software at will, without *artificial* restrictions as to which versions of what software are  installable (there will, of course, always be some, hopefully not too many, technical limitations, like you don't expect a Windows 7 driver to work on an NT4 Workstation).

But, apparently, that is not Ubuntu's approach. And there is something to say in favor of delivering  a complete system in which all components have been tested and are guaranteed to work together in a stable manner.

---

### Post by snowpine on 2010-11-17
> **koenn said:**
> yes, and the point is that, the way ubuntu is designed, adding programs from outside the repos would be like making it a frankencar. That's the point I originally wanted to make : if you need to resort to a frankenstein solution, something is wrong.   That's way I find the 'you can always compile from source' argument invalid. 

Not what I said at all... I don't want to *buy* a Frankencar, but I believe I have the right to Frankenize *my own* car however I see fit! This desire for freedom is why I'm a Linux user... Windows is like buying a car with the hood welded shut so you can't tweak the engine. :)


p.s. Here, the analogy starts to break down... in real life I can't actually do "anything I want to" with my car... if my modifications make it unsafe, then it will not pass inspection... whereas there is no inspection sticker process for whether a Linux install is safe to "drive."

---

### Post by koenn on 2010-11-17
> **snowpine said:**
> Not what I said at all... I don't want to *buy* a Frankencar, but I believe I have the right to Frankenize *my own* car however I see fit! This desire for freedom is why I'm a Linux user... Windows is like buying a car with the hood welded shut so you can't tweak the engine. :)
I don't dispute your right to make a frankencar, I just disagree with people who suggest building a frankencar is a valid solution for people who require slight modifications to the car they have. 

> **snowpine said:**
> 
p.s. Here, the analogy starts to break down... in real life I can't actually do "anything I want to" with my car... if my modifications make it unsafe, then it will not pass inspection... whereas there is no inspection sticker process for whether a Linux install is safe to "drive."

Oh but there is.
Some software vendors will refuse to support their application unless its deployed on a certified system. Even if Ubuntu as such qualifies, your frankenstein version will most  likely not. 

Or, if a business critical system crashes, the company looses loads of money,  and your the sysadmin, your position in the case where you followed recommended best practices will differ from your position in the case you hacked together somethings that worked (for a while). The latter case is the one you *don't* want to be in.

---

### Post by snowpine on 2010-11-18
> **koenn said:**
> Oh but there is.
Some software vendors will refuse to support their application unless its deployed on a certified system. Even if Ubuntu as such qualifies, your frankenstein version will most  likely not. 

Or, if a business critical system crashes, the company looses loads of money,  and your the sysadmin, your position in the case where you followed recommended best practices will differ from your position in the case you hacked together somethings that worked (for a while). The latter case is the one you *don't* want to be in.

That is an excellent point... support from software vendors/company sysadmin is very important for many users! :)

---

### Post by psusi on 2010-11-18
> **snowpine said:**
> Maybe my needs are atypical :) but let me give you a specific example. In my work, I often need to import documents that are sent to me from Windows or Mac users. If I stick with an outdated version of OpenOffice, I may be unable to open documents in the latest MS Office formats.

Unless you are still running 8.04, you have the latest version of OO.o ( 3.2 ).

> **koenn said:**
> That's the point I originally wanted to make : if you need to resort to a frankenstein solution, something is wrong.

What is wrong is that your specific needs are not met by the product as is, not that there is something flawed with the way the product is designed and manufactured.  Just because YOU want a more powerful engine and special sport tires than the ones that come with the car does not mean the car manufacturer is doing it wrong.

> **koenn said:**
> 
Otoh, maybe the whole idea of having a monolithic distro, is the wrong idea (no matter how slow or how fast the release cycle is). 
Source distribution would probably have less of these problems, so maybe for open source, a "source code compiling software distribution system' (the way Gentoo and some BSD distro's do it ?)  is a better solution

Go run Gentoo then if that meets your needs.  Yes, you will always have the latest software.  Of course this means that you often will get breakage because you are the guinea pig testing the latest software and finding the bugs in it, not to mention spending a lot of your time compiling.

> **koenn said:**
> Or a system with a minimal base, to which the user can add software at will, without *artificial* restrictions as to which versions of what software are  installable (there will, of course, always be some, hopefully not too many, technical limitations, like you don't expect a Windows 7 driver to work on an NT4 Workstation).

Once again, there are no restrictions; you are perfectly free to go download, compile, and install the very latest.

> **koenn said:**
> And there is something to say in favor of delivering  a complete system in which all components have been tested and are guaranteed to work together in a stable manner.

Now you are getting it.

---

### Post by koenn on 2010-11-18
> **psusi said:**
> 
What is wrong is that your specific needs are not met by the product as is, not that there is something flawed with the way the product is designed and manufactured.  Just because YOU want a more powerful engine and special sport tires than the ones that come with the car does not mean the car manufacturer is doing it wrong.

Nope, that comment was in a context that your preference for line by line quote and rebuttal makes you miss entirely. 
The point there was that the current as is suites me fine, but as soon as I (and the "I" here is "some people", not me in person) a newer version with something I like, I wanted.
Furthermore, the point of that analogy at the time was to show that 'outdated" is relative, and that the concept of selling a product as a whole, without much to mix and match across versions, can make sense. For cars, and for linux distros. 
So, in essence, you didn't get it.


> **psusi said:**
> 
Go run Gentoo then if that meets your needs.  Yes, you will always have the latest software.  Of course this means that you often will get breakage because you are the guinea pig testing the latest software and finding the bugs in it, not to mention spending a lot of your time compiling.

Gentoo does not meet my needs and I have no intention of running it. I only mentioned it to clarify what i meant with "source code compiling software distribution system", which in turn was only meant to suggest that delivering binaries, and the disadvantages associated with it, isn't the only way to distribute software, and that occasionaly looking at what others are doing and see if you can learn from it, is not a bad idea. 


> **psusi said:**
> 
Once again, there are no restrictions; you are perfectly free to go download, compile, and install the very latest.

Actually, there are, as I stated in a couple of other posts here.
But again, the sentence you quote out of context here was, liker the Gentoo statement, meant to  suggest that occasionaly looking at what others are doing and see if you can learn from it, is not a bad idea.
You seem to have missed that entirely.

> **psusi said:**
> 
Now you are getting it.
No, but I said something that agrees with your opinion.

Yet again, that sentence comes out of a 5 paragraph post and should be read in that context - the other paragraphs are just as important as this 1 sentence you singled out, and thit 1 sentence is meaningless without the rest of the post - at least, if your interested in knowing my opinion, that is. 

So, that 'sentence by sentence" quote style is really harming your understanding, it seems. It's also the main reason I did not respond to your earlier post in the same style (and the same sort of missing the point at every quote).

---

### Post by tgm4883 on 2010-11-18
It is your opinion that they are doing it right and maybe they are, for their own goals. I say find a distro that works for you and use it, making minor tweaks (such as using PPAs in this case) when necessary. If it's Ubuntu great, if it's something else thats fine too. 

Some distros have a goal of "this is the tested software versions that we support for this release", others have goals for having the latest and greatest software available in every release. But that is what separate the distributions. If every distro shared the same goals, there would be a single distribution and only one way to do things.

---

### Post by snowpine on 2010-11-18
> **psusi said:**
> Unless you are still running 8.04, you have the latest version of OO.o ( 3.2 ).

3.1 actually (I'm not an Ubuntu user) but the point is, I know how to upgrade if I need to. :)

---

### Post by psusi on 2010-11-18
Reading your comments *in context*, it sounds like you are saying that:

1)  Ubuntu places restrictions on what versions of software you can install

2)  If, in order to get the latest features you want, you have to go get unsupported versions and install them yourself, then there is a flaw in Ubuntu's release cycle.

If that isn't what you mean, then I withdraw my comments.

---

### Post by snowpine on 2010-11-18
> **psusi said:**
> 1)  Ubuntu places restrictions on what versions of software you can install

Ubuntu is open-source software. You can install anything you want, without restrictions.

---

### Post by koenn on 2010-11-18
> **psusi said:**
> Reading your comments *in context*, it sounds like you are saying that:

1)  Ubuntu places restrictions on what versions of software you can install

2)  If, in order to get the latest features you want, you have to go get unsupported versions and install them yourself, then there is a flaw in Ubuntu's release cycle.

If that isn't what you mean, then I withdraw my comments.

That's pretty accurate, yes. There are however, some subtleties about "in order to get the latest features you want" -- I'm actually leaning more towards "during the lifecycle of a release, new (business / end-user) needs may emerge and if the release policy doesn't allow you to deal wuth those, then that policy is flawed". imo, Ubuntu does not handle those circumstances well. 

On a whole different level, I'm also wondering if this flaw is an indication that distributing binaries may not actually be the optimal approach to distributing Open Source Software, but I do not (yet) have a strong opinion on that matter

---

### Post by koenn on 2010-11-18
> **snowpine said:**
> Ubuntu is open-source software. You can install anything you want, without restrictions.
*technically*, yes.

---

### Post by CharlesA on 2010-11-18
> **snowpine said:**
> Ubuntu is open-source software. You can install anything you want, without restrictions.

I guess what psusi meant is that there are certain versions of software in the repos. If you want a different version you'd have to use a PPA or build it from source.

---

### Post by uRock on 2010-11-18
> **snowpine said:**
> Ubuntu is open-source software. You can install anything you want, without restrictions.

Yup, I think the only flaw here is when people think that Ubuntu is supposed maintain their packaging in the same manner as a rolling release.

Ubuntu isn't listed in this link because it isn't a rolling release. [http://en.wikipedia.org/wiki/Rolling_release](http://en.wikipedia.org/wiki/Rolling_release)

---

### Post by snowpine on 2010-11-18
> **koenn said:**
> *technically*, yes.

Good enough for me. :)

---

### Post by koenn on 2010-11-18
> **snowpine said:**
> Good enough for me. :)

:)

but is it, say from a Canonical point of view, also a good enough foundation to build a profitable software company on ? 
Or would they benefit from having a release policy / cycle / frequency that does not force their users to go hunt for software ouside the channels they, as a company, provide ?

---

### Post by snowpine on 2010-11-18
> **koenn said:**
> but is it, say from a Canonical point of view, also a good enough foundation to build a profitable software company on ? 

I'm not sure whether Canonical is actually turning a profit, but they are certainly very successful in terms of user base (#1 most popular desktop Linux distro by most estimates).

> **koenn said:**
> Or would they benefit from having a release policy / cycle / frequency that does not force their users to go hunt for software ouside the channels they, as a company, provide ?

I would suggest looking at some "case studies" of successful open-source software companies to see how they have accomplished it. 

Also, nobody is "forcing" anyone to do anything. ;)

---

### Post by koenn on 2010-11-18
> **snowpine said:**
> I'm not sure whether Canonical is actually turning a profit, but they are certainly very successful in terms of user base (#1 most popular desktop Linux distro by most estimates). 
Last time a heard (this summer or so), they were not turning a profit and the forecast was that it could still take a while before they do.

They are successful in terms of numbers of users, but those are mostly computer enthousiasts why feel there's no risk in trying, sonce it doesn't cost anything. It's hard tu turn that in to paying customers, apparently.


> **snowpine said:**
> 
I would suggest looking at some "case studies" of successful open-source software companies to see how they have accomplished it. 
 
There aren't enough of those for a meaningful analysis 
(I'm limiting the field to distros because that what this thread is about, and releasing a distro is different from releasing a single program, or a stack)

---

### Post by snowpine on 2010-11-18
> **koenn said:**
> Last time a heard (this summer or so), they were not turning a profit and the forecast was that it could still take a while before they do.

They are successful in terms of numbers of users, but those are mostly computer enthousiasts why feel there's no risk in trying, sonce it doesn't cost anything. It's hard tu turn that in to paying customers, apparently.

That is too bad. Maybe more people would pay for Canonical support if these forums weren't so darn helpful? :)
 
> **koenn said:**
> There aren't enough of those for a meaningful analysis 
(I'm limiting the field to distros because that what this thread is about, and releasing a distro is different from releasing a single program, or a stack)

So you are saying the successful companies of the real world have nothing to teach us? ;)

---

### Post by cariboo on 2010-11-18
The one thing nobody seems to have said is that Ubuntu takes a snapshot of Debian unstable at the beginning of a development cycle, and sticks with those packages until the release EOL's. If it isn't in Debian unstable, then it won't make it into the release.

As far as the latest and greatest goes, the majority of users, make use of software that is out of date according to the posters in this thread. With a 6 month cycle, there is always a newer version of some package only 6months at the most away.

People using the LTS releases use them for stability.  The only people that seem to be concerned with the latest and greatest are computer enthusiasts, who aren't the target market for LTS releases.

---

### Post by snowpine on 2010-11-18
> **cariboo907 said:**
> The one thing nobody seems to have said is that Ubuntu takes a snapshot of Debian unstable at the beginning of a development cycle, and sticks with those packages until the release EOL's. If it isn't in Debian unstable, then it won't make it into the release.


As a long-time user of Debian Unstable, I can tell you that simply isn't true... Just off the top of my head, I can think of several important packages that are newer in Ubuntu 10.10 than in Debian Unstable ("Sid"): 

the kernel (Sid is at 2.6.32)
the browser (Sid is at 3.5.15)
the desktop environment (Sid is at Gnome 2.30 and KDE 4.4.5)

---

### Post by psusi on 2010-11-18
> **koenn said:**
> That's pretty accurate, yes. There are however, some subtleties about "in order to get the latest features you want" -- I'm actually leaning more towards "during the lifecycle of a release, new (business / end-user) needs may emerge and if the release policy doesn't allow you to deal wuth those, then that policy is flawed". imo, Ubuntu does not handle those circumstances well.

Then my comments about how you are wrong were spot on, so now I am confused about why you seemed to say they were not because I misunderstood what you said.  Once again, YOU are perfectly free to deal with updating software to deal with your unique needs.  Ubuntu's packaging methods have no flaw that prevents you from doing so.  They just don't do it FOR you.

> **koenn said:**
> :)

but is it, say from a Canonical point of view, also a good enough foundation to build a profitable software company on ? 
Or would they benefit from having a release policy / cycle / frequency that does not force their users to go hunt for software ouside the channels they, as a company, provide ?

Since it meets the needs of most people, the answer is yes.  Most people don't care to install beta quality software.

---

### Post by guimaster on 2010-11-19
I am going to give Linux Mint Debian Edition a go on my old laptop and see what happens. But there is no harm in Ubuntu developers also starting a Rolling Distribution on the side, and allowing the people to make the choice.
 
I hope it isn't a huge backside pain to make LMDE look like Lucid...

---

### Post by koenn on 2010-11-20
> **snowpine said:**
> 
So you are saying the successful companies of the real world have nothing to teach us? ;)
How many companies do you know that both
a) are financially succesful
b) have a business activity that could serve as a model for linux distro's, i.e. delivering an operating system + assorted end user applications
c) have overcome problems similar to those that linux distro's face, i.e. that "selling bytes" is most likely not an option. 




> **psusi said:**
> my comments about how you are wrong were spot on,
I fail to see how

> **psusi said:**
> Once again, YOU are perfectly free to deal with updating software to deal with your unique needs.  Ubuntu's packaging methods have no flaw that prevents you from doing so.  They just don't do it FOR you.
I'm not looking for an ad hoc solution to a specific problem of mine. I'm pointing out a structural flaw (which is what this thread is about),
See for example : 
"Some software vendors will refuse to support their application unless its deployed on a certified system. Even if Ubuntu as such qualifies, your frankenstein version will most likely not. " -> therefore the availability of source tarballs or PPAs is not an acceptable solution -> therefore Ubuntu can not deal adequately with business/user needs that emerge during the lifetime of a release -> this is a result of Ubuntu's release policy -> so this policy is flawed.


As an aside, an other conclusion could be: it's not Ubuntu's release policy  that is flawed, it's just that a business whose software needs might change over the period of 2 years should not use Ubuntu, they should've picked something else.

> **psusi said:**
> 
Since it meets the needs of most people, the answer is yes.  Most people don't care to install beta quality software.
see above: needs may change over time, and Ubuntu is apparently not well  equipped to deal with that.

---

### Post by koenn on 2010-11-20
> **cariboo907 said:**
> 
As far as the latest and greatest goes, the majority of users, make use of software that is out of date according to the posters in this thread. With a 6 month cycle, there is always a newer version of some package only 6months at the most away.

People using the LTS releases use them for stability.  The only people that seem to be concerned with the latest and greatest are computer enthusiasts, who aren't the target market for LTS releases.

apparently you haven't read the entire thread before posting.

I've posted this before, but it seems relevant to your post, so I'll post it again:

Small anecdote :
Belgian eID's are smartcards. They give access to a number of government web applications, a lot of which I need for work. 
It's 2006 and I'm using Ubuntu 6.06, the current LTS, because I want a stable OS and no 6-monthly change management (I'm talking a business setting here)

The drivers for the most commonlmy available smart card readers and the middle-ware to use the certificates on the card's chip, were not available in Ubuntu 6.06. There were (slightly buggy but useable) packages in 6.10.

Now, say I'm the sysadmin for a company that uses Ubuntu LTS on the desktop. A large portion of the users needs to use those eID smartcard readers to access those web apps for work.

I'd have had the following options :
- stick with LTS, wait for the next LTS approx 1 or 1.5  years later - quite a while for something you need for work (and embarrassing, as it didn't seem to be a problem for other operating systems)

- switch to 6.10 and sit out the 6 monthly upgrade trouble until the next LTS is released. Kinda goes against the general "businesses stick with LTS for stability and ease of (change) management" paradigm

- move part or all of my users to another OS. Quite an operation, and it creates a heterogeneous environment, which is harder to maintain and support. I'd rather not go there. 

- get someone to build a working package for me, and prepare for trouble at the next LTS-to-LTS upgrade because the upgrade manager trips over 'rogue' packages. 




All of these options are less than optimal.
All of them are a direct result of the way Ubuntu organizes its releases.
Hence my opinion that Ubuntu's release model is flawed.

---

### Post by psusi on 2010-11-20
> **koenn said:**
> 
I'm not looking for an ad hoc solution to a specific problem of mine. I'm pointing out a structural flaw (which is what this thread is about),

And I have pointed out to you that the problem is structurally satisfied by the backports repository.  You want more up to date versions of some packages on an older LTS release, you can go install them from the backports repository.

---

### Post by koenn on 2010-11-21
> **psusi said:**
>  You want more up to date versions of some packages on an older LTS release, you can go install them from the backports repository.
Let me point out that, at the time, 6.06 was the *current* LTS, not some old EOL'd release.


> **psusi said:**
> And I have pointed out to you that the problem is structurally satisfied by the backports repository. 
To which I have replied that this would indeed be satisfactory if, and only if,
-1- the packages in question were available in backports, and
-2- backports would have the same official support status as the 'main' repository - this may be pretty irrelevant to home users, but may well matter to businesses, in regard to support contracts and SLAs.

re. #2: as far as I can tell, Canonical seems to have overlooked this issue, I can find no reference to backports on their website, and the community documentation only says "judge for yourself whether this is a good idea".

---

### Post by snowpine on 2010-11-22
> **koenn said:**
> How many companies do you know that both
a) are financially succesful
b) have a business activity that could serve as a model for linux distro's, i.e. delivering an operating system + assorted end user applications
c) have overcome problems similar to those that linux distro's face, i.e. that "selling bytes" is most likely not an option. 

Check today's news. Big story about Novell...

---

### Post by koenn on 2010-11-22
> **snowpine said:**
> Check today's news. Big story about Novell...

on topic:
that's 1 - hardly enough for analysis - unless you want to argue that canonical should model itself after Novell in terms of release practice


off topîc:
Novell up for sale etc ... yes, that's worth a look ...

---

### Post by snowpine on 2010-11-22
> **koenn said:**
> on topic:
that's 1 - hardly enough for analysis - unless you want to argue that canonical should model itself after Novell in terms of release practice


Red Hat is another company that comes to mind.

Ubuntu's release cycle is "Not Flawed" in my opinion, so I have no interest in arguing anything, sorry. :)

---

### Post by cariboo on 2010-11-22
> **koenn said:**
> Let me point out that, at the time, 6.06 was the *current* LTS, not some old EOL'd release.



To which I have replied that this would indeed be satisfactory if, and only if,
-1- the packages in question were available in backports, and
-2- backports would have the same official support status as the 'main' repository - this may be pretty irrelevant to home users, but may well matter to businesses, in regard to support contracts and SLAs.

re. #2: as far as I can tell, Canonical seems to have overlooked this issue, I can find no reference to backports on their website, and the community documentation only says "judge for yourself whether this is a good idea".

You're assuming that Canonical treats their paying customers the same way they treat us free users, from what I've seen Canonical will do almost anything a paying customer requests as long as they pay for it.

---

### Post by madjr on 2010-11-22
starting from **12.04 LTS**, ubuntu might want to consider **1 year releases**...

and a rolling release dev version for us to play with, along with the other remixes.

At first it might seem they lose some big "press/buzz" twice a year or that dev slows a bit, but they will gain support from manufacturers and get "Better" press, since many more bugs can be ironed out before release.

Also less versions to support and more focus on 1 for longer time. 1 years isnt too much or too little.

they might also consider a **modified kernel fork** if it benefits the end user experience and resolves some of the bugs and low support from proprietary hardware driver manufacturers.

of course the rapid releases has some benefits at first like in the case of **android**, but google also plans to slow down to create a more stable base for manufacturers and end user experience.

---

### Post by koenn on 2010-11-22
> **cariboo907 said:**
> You're assuming that Canonical treats their paying customers the same way they treat us free users, from what I've seen Canonical will do almost anything a paying customer requests as long as they pay for it.


yep, that's true. 
And in terms of "satisfactory solution', that would indeed fix the issue.
otoh, it's still an ad hoc fix to what, imo, might be a structural problem. 


that it may indeed be a structural problem perhaps becomes more clear if you look at it from different angles.
here are a few:

1/ for open source software, it may actually make more sense to do source releases than distributing binaries. the freeze- and release schedules and the 'depend only on versions in the current release'-reflex  are partially a way of dealing with the fact that you want to know the system you're compiling for. Compiling "in place" on the target system 'as is' might actually be an easier way of reaching that goal.


2/ What Ubuntu (and a lot of other linux distro's) attempt to do, is delivering 1 monolithic block, from the most low-level hardware-compatibility in a kernel module to the layout of the menus in the user's desktop. That's a form of centralisation that works well on mainframes and other forms of server-based computing, but is not necessarily the ideal way of dealing with desktop systems that are either stand-alone, or clients in a client-server environment. 

Wouldn't it be better to deliver an operating system that covers essential computing needs (filesystems, network capability, ... ) and may come with a default set of end-user apps, but at least lets the user upgrade to newer versions as the become available (within a certain range, for practical reasons : you can't maintain compatibility for ever) with having to replace the entire operating system as well ?

---

### Post by koenn on 2010-11-22
> **madjr said:**
> starting from **12.04 LTS**, ubuntu might want to consider **1 year releases**...

and a rolling release dev version for us to play with, along with the other remixes.

so, someone at Canonical also thinks the current model maybe wasn't perfect.

I rest my case.
:)

---

### Post by LifeTheHound on 2011-03-21
> **snowpine said:**
> Red Hat is another company that comes to mind.

Ubuntu's release cycle is "Not Flawed" in my opinion, so I have no interest in arguing anything, sorry. :)

Tell that to the many friends I've painstakingly set up Ubuntu 9.04 up for who now don't get even critical updates... friends who, when they naively tried distro upgrading, ended up with broken computers and couldn't invest the week or so in their busy schedules learning the ultra-technical expertise necessary to debug everything from graphics to sound to multimedia breakage and so switched to Windows 7 with a bitter taste in their mouth. 

This happens *all the time*. Ubuntu's current release cycle is like a baby into whom you're forced to invest so much time to turn into a functional adult... an adult who then immediately goes off and leaves you with another baby a few months later. It's a constant, back-breaking investment on the part of both the users and the devs, whereas with other (obviously more popular) operating systems, the adult (who comes as a teen at youngest, not a baby) works for you for up to **10 years**, to take the XP example. 

*Ideal: Stable base + constant rolling non-system upgrades + **optional** system upgrades (kernel backports, etc for those with new hardware).*

Debian fails at this because it is not user-friendly to set up and does NOT update the user software, so it suffers from an extreme case of Ubuntu's 'lock-in' problem with software that's even older. On the other hand, Arch fails at this because it is also user-unfriendly and rolls system upgrades along with user software, so it's constantly unstable, suffering from the extreme opposite end of Ubuntu's release problems, rapid breakage even faster than a 6-month cycle. It's the pinnacle of irony that M$, who can't seem to get anything right, got the one thing right that actually mattered -- system support. How? Having a proper release cycle. It ensured constant user software updates by maintaining one release for a long time, and it ensured hardware compatibility by ensuring drivers are built against a single kernel version (with is obviously possible in linux too; see ubuntu-backports-modules-wireless/alsa/etc for an ironic and misused example).

---

### Post by snowpine on 2011-03-21
Again, I have no interest in arguing whether or not "Ubuntu's release cycle is flawed" but I always love debating semantics, in this case your use of the words "flaw" and "fail."

Is Newsweek a "failed daily newspaper" because it only comes out once a week? Is a fork a "flawed spoon" because you can't use it to eat soup? Is a gallon of milk "failed cheese?" Is a regular hamburger a "flawed Big Mac"? Am I a "failed Olympic pole vaulter" because I don't have a gold medal in the event (since I have never competed)? Are nickels "flawed" because they are worth less than dimes?

"Ubuntu is flawed because releases do not have 10 years of support" is a nonsense argument because no Ubuntu release has ever been designed with 10 years of support in mind. (In fact, Ubuntu didn't even exist 10 years ago.) Elephants have a gestation period of 22 months, human females only 9 months... does this mean the human womb is "flawed" because it cannot support a 22-month pregnancy? Or maybe it's just that humans are not elephants?

Ubuntu releases are supported for exactly as long as Canonical says they will be supported (18-60 months depending on the release). This information is well-known and publicized in advance. If you converted all your friends to Ubuntu 9.04, told them it would last 10 years, and then left them dangling in the wind when Jaunty went end-of-life in Oct. 2010, that is really not Canonical's fault, but rather the "failure" is yours for giving your friends false expectations and not providing follow-up support.

I hear your arguments about Ubuntu, and I think you have some valid suggestions (personally I stopped using Ubuntu a couple of years ago because of similar concerns). But I think any discussion of "flaws" and "failures" must keep the developers' intent in mind. There is a big difference between saying "Ubuntu is a flawed rolling-release distro" and "Ubuntu is not a rolling release distro." :)

---

### Post by LifeTheHound on 2011-03-21
> **snowpine said:**
> Again, I have no interest in arguing whether or not "Ubuntu's release cycle is flawed" but I always love debating semantics, in this case your use of the words "flaw" and "fail."

Is Newsweek a "failed daily newspaper" because it only comes out once a week? Is a fork a "flawed spoon" because you can't use it to eat soup? Is a gallon of milk "failed cheese?" Is a regular hamburger a "flawed Big Mac"? Am I a "failed Olympic pole vaulter" because I don't have a gold medal in the event (since I have never competed)? Are nickels "flawed" because they are worth less than dimes?

"Ubuntu is flawed because releases do not have 10 years of support" is a nonsense argument because no Ubuntu release has ever been designed with 10 years of support in mind. (In fact, Ubuntu didn't even exist 10 years ago.) Elephants have a gestation period of 22 months, human females only 9 months... does this mean the human womb is "flawed" because it cannot support a 22-month pregnancy? Or maybe it's just that humans are not elephants?

Ubuntu releases are supported for exactly as long as Canonical says they will be supported (18-60 months depending on the release). This information is well-known and publicized in advance. If you converted all your friends to Ubuntu 9.04, told them it would last 10 years, and then left them dangling in the wind when Jaunty went end-of-life in Oct. 2010, that is really not Canonical's fault, but rather the "failure" is yours for giving your friends false expectations and not providing follow-up support.

I hear your arguments about Ubuntu, and I think you have some valid suggestions (personally I stopped using Ubuntu a couple of years ago because of similar concerns). But I think any discussion of "flaws" and "failures" must keep the developers' intent in mind. There is a big difference between saying "Ubuntu is a flawed rolling-release distro" and "Ubuntu is not a rolling release distro." :)

It's flawed and failed insofar as the stated main goal of Ubuntu -- to be an accessible and usable OS (which implies being maintainable) by everyday people. 

-A fork is not a flawed spoon because it wasn't intended to be one -- people know it's used as a fork because they understand the two objects and the difference between them. People new to Ubuntu do not understand that their systems will break in 6 months and/or that they will not get any user software updates unless and until they upgrade at that point.

-Newsweek isn't flawed because its staff is capable of producing the news in complete and palatable form within that timeframe. The quality checks suffice, and people actually expect a weekly release because they are familiar with the Sunday paper and other popular weekly magazines that do the same. Additionally, weekly papers are made thicker/denser depending on the intended topic. The type of news covered by Newsweek does not suddenly go out-of-date within a week's time -- for breaking stories, users have only to turn on the TV. As a mainstream OS, Ubuntu is flawed because it *does* attempt to be an end-user operating system for (almost) everyone. It's NOT expected that the mainstream be forced to use Ubuntu only in a dual-boot situation any more than Newsweek is expected to provide users the essential news of the day. To be fair, both the late breaking and stable are accessible in windows within seconds, not only biannually. In fact, the version of windows is the weekly magazine, and the versions of software are the day-breakers. With windows, the system allows for both, and without the quality deterioration you'd expect if you had to release Newsweek on an hourly basis as Ubuntu is attempting to do. 

- A gallon of milk isn't failed cheese because cheese cannot be used for everything milk can. Milk is a precursor to cheese; Ubuntu shouldn't have to be merely a precursor to another release a few months down the line. Ubuntu is intended to be the milk AND cheese of the consumer, according to the rhetoric, even if it can't be the niche Cotswald English variety for those professional connoisseurs. 

- A regular hamburger is indeed a flawed big mac if the hamburger is delivered when the big mac was advertised. Check out Ubuntu's main page and/or the word of fellow Linux enthusiasts/users. Sure Ubuntu was never advertised to be the Triple Bypass Burger that Windows is, but for most people, that's fine, and to many others even preferred over the bloat and messiness of the latter. Ubuntu doesn't have to be the sparse and flavorless burger only appealing to purists and minimalists willing to spend the time to add their own ingredients, just as it doesn't have to be the bloated and inherently unstable Triple Bypass. 

- You aren't a failed olympic *because* you never tried. Ubuntu doesn't pretend to be of olympic level, either. It does aim to be relatively capable of a decent long-jump, though, and plenty of other activities besides -- all without the constant risk of random injury. 

- Theoretically, the human womb *can* support an indefinite pregnancy, provided the adequate growth conditions of the baby and an alteration to the hormonal capacity to signal the end of the pregnancy. But it is obviously absurd to impose a 22-month pregnancy on humans when the 9-month cycle suffices incredibly well. Human evolution, to say nothing of the modern societal ecosystem, has perfected this release, and development is perfectly completed in that timeframe, with some exceptions. The baby that then emerges, unlike the baby kangaroo, for instance, is provided for and well supported by the framework of society that allows it to be nursed into maturity, but it's still tethered to the mother as a learning and growing prototype ("alpha") of the child ("beta") who matures into a productive adult ("release"). My central argument is that Ubuntu is not only aborted/delivered prematurely, but also that the learning and human development allowed atop the 'adult' is also curtailed, leaving an already-crippled individual who cannot adapt or learn new things but will be replaced with another such woeful individual soon enough. 

If the failure is mine for believing in the simplicity and elegance of the release system, in expecting the hard work that went into debugging an existing system to be maintained across upgrades, and expecting new software to be made available as stable upstream releases are made, then sure, my bad for assuming a basal level of what I considered rudimentary competence. But if this is indeed the case while alternative operating systems are fully capable of thwarting these issues with their superior release cycles, then I beg you to reconsider who you believe to be at fault. Regardless, then, of who is at fault for giving them the system (for it seems you are implying giving Ubuntu to human beings is in fact a problem on my part), the release system is still to blame for leaving them out in the cold -- whether I found the system for them or they did so themselves.

The point is Ubuntu is capable of so much more, and the solution I proposed is proven successful method to go about realizing these ambitions (though I'd hardly call something so fundamental an "ambition").

---

### Post by Copper Bezel on 2011-03-21
> Tell that to the many friends I've painstakingly set up Ubuntu 9.04 up for who now don't get even critical updates... friends who, when they naively tried distro upgrading, ended up with broken computers and couldn't invest the week or so in their busy schedules learning the ultra-technical expertise necessary to debug everything from graphics to sound to multimedia breakage and so switched to Windows 7 with a bitter taste in their mouth.

You're overlooking the basic fact that this has nothing to do with the release cycle.

My Eee S101:

9.10: WiFi, brightness, etc. worked out of the box, CPU scaling did not, suspend state did not, some function keys were non-functional.

10.04: WiFi and brightness still worked, CPU scaling (IIRC) improved slightly, function keys were fixed, suspend state killed WiFi and required restart.

10.10: WiFi and brightness still worked, function keys still worked, CPU scaling got full support, suspend state still worked, a minor script tweak corrected the WiFi-on-resume problem.

Delaying updates would have meant my hardware wouldn't be properly supported until Natty. This sort of thing makes updating a *very* anxiety-inducing process, but there's more good than bad in there. Since Ubuntu uses the generic Linux kernel, hardware support problems, including backwards compatibility, are almost by definition upstream. With a six-month cycle, we at least get the best that kernel.org has to offer. even if it's not always ideal.

---

### Post by oldsoundguy on 2011-03-21
"RE:One big reason Ubutnu's release cycle is flawed."

Because I think so and my opinion is far more important than that of those that have capital and energy invested in the program... and besides that I think the desktop should be bouncing polka dots to impress my 13 year old girlfriend.

RIGHT!!!!

---

### Post by LifeTheHound on 2011-03-21
> **oldsoundguy said:**
> "RE:One big reason Ubutnu's release cycle is flawed."

Because I think so and my opinion is far more important than that of those that have capital and energy invested in the program... and besides that I think the desktop should be bouncing polka dots to impress my 13 year old girlfriend.

RIGHT!!!!

Thanks for contributing! Gold star, sir; and may that gold be forged from that which you've so delightfully shared with us today.

---

### Post by LifeTheHound on 2011-03-21
> **Copper Bezel said:**
> You're overlooking the basic fact that this has nothing to do with the release cycle.

My Eee S101:

9.10: WiFi, brightness, etc. worked out of the box, CPU scaling did not, suspend state did not, some function keys were non-functional.

10.04: WiFi and brightness still worked, CPU scaling (IIRC) improved slightly, function keys were fixed, suspend state killed WiFi and required restart.

10.10: WiFi and brightness still worked, function keys still worked, CPU scaling got full support, suspend state still worked, a minor script tweak corrected the WiFi-on-resume problem.

Delaying updates would have meant my hardware wouldn't be properly supported until Natty. This sort of thing makes updating a *very* anxiety-inducing process, but there's more good than bad in there. Since Ubuntu uses the generic Linux kernel, hardware support problems, including backwards compatibility, are almost by definition upstream. With a six-month cycle, we at least get the best that kernel.org has to offer. even if it's not always ideal.

Yes, they're upstream. In the kernel. And can be supplied as modules. I beg you to check out the linux-backports-modules-wireless/alsa/etc packages for a demonstration that a solid base can in fact be made to support the latest hardware. This only supports my point. 

Also, "upstream" kernels in their entirety can be swapped painlessly within a release with a ppa or deb packages. There is no reason to force the system-breaking changes on users every 6 months -- and by the same token, no reason NOT to provide updated stable upstream user software. 

All of this has been taken account of in my write-up.

---

### Post by uRock on 2011-03-21
I can't say that it is flawed. I am running it on multiple systems and it works perfectly on all of the machines in my house.

---

### Post by C1377 on 2011-03-21
Ubuntu 9.04's update manager still works for me... I re-installed 9.04 a few weeks ago, and there were several security updates and what not available.....

---

### Post by LifeTheHound on 2011-03-21
[quote=uRock]I can't say that it is flawed. I am running it on multiple systems and it works perfectly on all of the machines in my house.[/quote]
I applaud you for being skilled, dedicated, and/or lucky enough to get a version working on all of your machines. I've managed to do something similar with 9.04 when it was supported. But the point is, this version is already obsolete in terms of both user software AND security updates. If you managed to get the latest and greatest working, another round of congratulations, but who's not to say it won't break 6 months (now only 2 months) down the line? If you look at the statistics, a great many people will not be able to report a perfect success. This comes back to my point. Speaking of 9.04...

[quote=C1337]Ubuntu 9.04's update manager still works for me... I re-installed 9.04 a few weeks ago, and there were several security updates and what not available.....[/quote]
Of course the update manager won't spontaneously break. The repos are still up, just essentially frozen in time. New security/stability/feature/bugfix updates won't be pushed out. (Maybe a few random packages are somehow being maintained, but this false sense of total security/support is probably more dangerous than if nothing came through at all.)

---

### Post by uRock on 2011-03-21
I have used 8.04, 9.04, 9.10, 10.04, 10.10 with no issues that weren't easy to fix. I am thankful for every upgrade as it brings even more usability to my system,

---

### Post by LifeTheHound on 2011-03-22
> **uRock said:**
> I have used 8.04, 9.04, 9.10, 10.04, 10.10 with no issues that weren't easy to fix. I am thankful for every upgrade as it brings even more usability to my system,

I am pleased that you, especially as a member of the ubuntuforums staff, are able to debug your system fairly easily, and I am also pleasantly struck by your good luck. You might have one of those few "golden systems" that are without issue (or only "minor" issue) for a large number of releases. In my experience, few people who buy standard HP/Dell/Lenovo laptops (the most common) are as lucky or as knowledgeable as yourself. For this reason, I am both lucky and thankful that you are investing your time and energy into these forums and helping people overcome their issues. 

But all the same, I must reiterate my own unequivocal experience with many novice users, most of whom don't even know what a forum is or that they exist (and of these, many refuse to "register" with any entity or forum, much less venture to post in them... or know what to make of whatever commandlines they might find filed away under some ancient site about "Red Hat 3 Linux" if they search for why their headphones don't work). 

Truly, a release system in line with what I've suggested would make it easier (and far more compelling) for the average person -- a human being far less technologically savvy than to understand the process of searching forums for technical issues, but a human being all the same greatly benefited by an easy-to-use, functional operating system that lasts more than a few months on their systems with up-to-date user software. And of course, I daresay such a system wouldn't exactly hurt the lucky and savvy users like yourself, either, while simultaneously keeping abreast of the very usability you advocate, without ever having to open a terminal or edit an uncomfortable config file they don't understand (and could potentially ruin their systems with one false step; I've seen that happen all too often as well). ;)

Such a release cycle is simply the best of all worlds, constitutes the optimal balance with the amount of manpower available, and provides compelling impetus for new and mainstream computer users (the vast majority) to switch to Ubuntu.

---

### Post by uRock on 2011-03-22
Debug? What is that. You speak as if this distro doesn't work on the majority of computers. I think you have it backwards.

---

### Post by tgm4883 on 2011-03-22
> **LifeTheHound said:**
> I am pleased that you, especially as a member of the ubuntuforums staff, are able to debug your system fairly easily, and I am also pleasantly struck by your good **luck**. You might have one of those few "golden systems" that are without issue (or only "minor" issue) for a large number of releases. In my experience, few people who buy standard HP/Dell/Lenovo laptops (the most common) are as **lucky** or as knowledgeable as yourself. For this reason, I am both **lucky** and thankful that you are investing your time and energy into these forums and helping people overcome their issues. 

But all the same, I must reiterate my own unequivocal experience with many novice users, most of whom don't even know what a forum is or that they exist (and of these, many refuse to "register" with any entity or forum, much less venture to post in them... or know what to make of whatever commandlines they might find filed away under some ancient site about "Red Hat 3 Linux" if they search for why their headphones don't work). 

Truly, a release system in line with what I've suggested would make it easier (and far more compelling) for the average person -- a human being far less technologically savvy than to understand the process of searching forums for technical issues, but a human being all the same greatly benefited by an easy-to-use, functional operating system that lasts more than a few months on their systems with up-to-date user software. And of course, I daresay such a system wouldn't exactly hurt the lucky and savvy users like yourself, either, while simultaneously keeping abreast of the very usability you advocate, without ever having to open a terminal or edit an uncomfortable config file they don't understand (and could potentially ruin their systems with one false step; I've seen that happen all too often as well). ;)

Such a release cycle is simply the best of all worlds, constitutes the optimal balance with the amount of manpower available, and provides compelling impetus for new and mainstream computer users (the vast majority) to switch to Ubuntu.

I'm pretty sure that your issue is that you think having Ubuntu work without major issues has something to do with luck. Quite the contrary. Having Ubuntu work without major issues is due to a minor amount of research before purchase for compatibility. 

Question, if you purchased a piece of hardware that was made for Linux and it didn't work properly in Windows, would you blame the hardware manufacturer or the operating system?

:EDIT:

As an added note, since I have been doing this bit of research when purchasing a computer and/or parts, I have had no major issues. I build most of my systems, but do own one Dell Mini 9 and an HP Mini 210. The only major issue I've had was a faulty SSD drive in the mini 9 that once replaced Ubuntu works beautifully on. My wife doesn't have a single issue with that system. (Unless you count forgetting to plug it in)

---

### Post by beew on 2011-03-22
I think you are going off tangent. OP's point is that it is risky to have to upgrade the whole OS every 6 months to get updated software. I don't think there is any reasonable argument against it. 

If it is risky to use unsupported software and ppas (Ubuntu's official line) then how would it be less risky to upgrade the whole OS? The worst thing a bad ppa could do is to break your system so badly that you need a clean  install,--extremely unlikely as you should check what is being installed and removed before going ahead. But you are now doing a clean install every 6 months as a ritual, how can anything be worse?

Another point is that Ubuntu once in a while goes on compulsive risk taking, e.g unity is a small one, and Wayland would be much bigger. Now what if you don't want to gamble with your working system but still want updated user softwares?  

Finally, what if you have a system perfectly tweaked and customized and don't want to lose it  after barely 6 months and yet still want your software to be up to date?

PPA (install from source or .deb) is a solution, but as I said way back, it is a way to circumvent the official limitation. If the only way for the system to work is to circumvent it then the system is flaw.

---

### Post by LifeTheHound on 2011-03-22
> **beew said:**
> I think you are going off tangent. OP's point is that it is risky to have to upgrade the whole OS every 6 months to get updated software. I don't think there is any reasonable argument against it. 

If it is risky to use unsupported software and ppas (Ubuntu's official line) then how would it be less risky to upgrade the whole OS? The worst thing a bad ppa could do is to break your system so badly that you need a clean  install,--extremely unlikely as you should check what is being installed and removed before going ahead. But you are now doing a clean install every 6 months as a ritual, how can anything be worse?

Another point is that Ubuntu once in a while goes on compulsive risk taking, e.g unity is a small one, and Wayland would be much bigger. Now what if you don't want to gamble with your working system but still want updated user softwares?  

Finally, what if you have a system perfectly tweaked and customized and don't want to lose it  after barely 6 months and yet still want your software to be up to date?

PPA (install from source or .deb) is a solution, but as I said way back, it is a way to circumvent the official limitation. If the only way for the system to work is to circumvent it then the system is flaw.

Well said on all counts! 

As for the ppa point, since many ppa's aren't maintained by Ubuntu itself, there are some glitches in many of them -- Firefox's ppa doesn't install with proper KDE integration and pulls in tons of gnome dependencies, LibreOffice for Lucid doesn't have proper Kubuntu bindings/integration, VLC ppa isn't as optimized (compiler switches used aren't as fast as stock switches), etc. Yet another piece of evidence against the current release cycle/system and in favor of the new one I've proposed. That way, the user software would be always be up-to-date, maintained and supported by the Ubuntu team, with far fewer bugs than are introduced due to the time/testing/manpower constraints inherent to rebuilding a whole new version from the ground up every 6 months. 

> **uRock]Debug? What is that. You speak as if this distro doesn't work on the majority of computers. I think you have it backwards.[/quote]
I'm sorry, but tremendous amounts of intensive and far-reaching experience with many systems and many mainstream computer users cause me (and them) to vehemently and unequivocally disagree without question. This is beyond opinion said:**
> Having Ubuntu work without major issues is due to a minor amount of research before purchase for compatibility. 
It strikes me as eye-opening that you'd suggest that someone not only put the cart before the horse, but that the mainstream even knows about Linux's existence in the first place enough to research "what system works." And then throw out their old computer. And then figure out the jargon. And then buy a new one (which may not be on sale at Best Buy at the time, which any mainstream computer user would of course pick up) to cater to a new system they've never used before and haven't even judged. I myself am astounded, having worked with Ubuntu for years, for to this very day I wouldn't even know where to start looking or whose word to take; people on hearsay have praised Atom netbooks as being compatible and Intel chipsets enjoying great open-source graphics and sound support. So you'd go buy a Poulsbo laptop and face insurmountable difficulty even getting it to boot. Or the same netbook that worked flawlessly last Ubuntu version but for some reason the sound doesn't work properly this version due to some silly config oversight the devs simply didn't have the time or testing to address beforehand in the absurd 6-month timeframe. It's a minefield. I know this intimately. I live and breathe it. 

So let's assume you're spot on, and the only way to ensure Ubuntu will work is to know computers, Linux, Ubuntu, and hardware well enough already to custom-purchase a suitable system. Does that sound like a rational approach to target the vast, vast majority of computer users? If this is the way the current system works, that's just the way it works. But that's certainly not the way it has to be. The release cycle alone can take great steps to overturn this broken approach for the mainstream by not only proving more enticing and well tested and up-to-date with user software, but to retain those who were brave enough to dabble in the first place after the first 6-month novelty period either wears on to the point where the user gets tired of the dated user software in the repos, or that period expires when that user tries to upgrade after all his meticulous configuration (or worse, the configuration a manufacturer or a friend had painstakingly set up). 

Returning a previous statement, how successful an operation do you think it would be to preach the merits and benefits of Linux (as well as the "free" cost) or actually spread awareness (not to mention the OS) when you need to add some ridiculous ground-up explanation to someone who just learned how to insert images into MS Word, something like:

 "Oh, and you'll have to research and buy a new computer -- not get the cheap cool one at best buy, but possibly some more obscure and pricey one with inferior specs -- oh, "specs" means the processor and RAM and speed of the computer -- to be compatible with specific versions, or 'distros' of a Linux system, paying specific attention to driver status -- oh, a 'driver' is something that controls hardware -- oh, and that means the physical components of the computer -- oh, and make sure that the version you want to install is also supported and your peripherals -- that's your webcam and microphone and such -- work with the version -- that's the 'newness' -- of the distro -- remember, that's the 'type' of Linux -- you choose -- oh? Well I don't know how you'd decide, I suggest Ubuntu or Kubuntu -- no, the names come from an African word meaning "humans" -- yeah, very easy to use -- how to check, you say? Well that beats me, you figure it out and jump through hurdles to figure out even how to even start thinking about going about what this novel system could potentially run well on...

...for six months. Before you have to install your graphics, multimedia, ppas, customizations, and firmwares all over again. Oh, did I mention how easy to use this 'Linux for Human Beings' is?"

> if you purchased a piece of hardware that was made for Linux and it didn't work properly in Windows, would you blame the hardware manufacturer or the operating system?
Neither. That's a bit off-topic, but it makes excellent support for my proposal. Indeed, long-term releases consisting of a solid base, rolling user software, and optional system backports would certainly be a great deal more usable, even on an original Windows system. After a great deal of effort, debugging, and setup, even some of the trickiest systems can be made to run on a certain version or two of Ubuntu. Once working, these systems would require another huge investment of effort to get working again a few months later. But consider my proposal. Assuming point releases (similar to those of 10.04) that include updated hardware detection scripts and the requisite slew of backport modules (similar to a more comprehensive and automated version of linux-backports-modules-XX), even these tricky systems would enjoy a great deal more support, not to mention it would give the time and motivation for enthusiasts to compile a set of instructions that wouldn't go completely obsolete in the next few months. So again, don't blame the OS, blame the release cycle for making it a lot more difficult than it needs to be -- the definition of a 'flawed' construct. 

But wait. What about blaming the manufacturer? Consider this before heaping the blame on them too. Let's ask: "When you buy an Ubuntu computer, would you expect it to run Ubuntu well? Or have up-to-date Ubuntu software a mere few months later? Or even the next version of Ubuntu those few months later?" The answer is a resounding "NO" even though it is an easy "YES" for Windows users because of the much longer support the latter enjoys. Look at the Dell mini. It's a *bone fide* Ubuntu 8.04 netbook. It was obsolete in 4 months, and useless for any serious work less than a year later. How? OpenOffice was soon obsolete and inoperable with much of the new docx format. It was impossible to update Ubuntu on that machine without very, very extensive and system-breaking hacking, and Ubuntu did not provide updated user software of Firefox until well after 3.0 lost support with many websites, nor did it ever offer new (more stable!) versions of Wine, GIMP, OpenOffice, printer recognition, and so forth, not to mention even the simplest backport driver builds, not that they're needed for that netbook anyway. Its Windows counterpart running XP, on the other hand (seamlessly upgradable to 7, by the way), is running strong today in the hands of novices to soccer moms to college students everywhere. 

At this point I'm tempted to say "think about it," but even without much thought at all it's difficult NOT to see the myriad problems with the current release cycle. 

Please answer honestly: have you even talked to a classmate, college, acquaintance, older family member about this? Or considered ever *not* having to be constantly on call for tech support for a newbie every 6 months? Honestly, some serious fieldwork seems to be required for many developers who grew up into the Linux community (or are absurdly lucky) actually see how the "mainstream" really works. To me it's obvious as a result of intense and extensive experience with them, in addition to my very own frustrations with these problems, for which the current release cycle again takes the great bulk of the blame. 

> [I] own one Dell Mini 9 and an HP Mini 210. The only major issue I've had was a faulty SSD drive in the mini 9 that once replaced Ubuntu works beautifully on.
Again, you are totally misunderstanding the concept of "mainstream users." What's an SSD? How do you "replace" Ubuntu? (The setup is quite complicated for a poulsbo system, requires USB tethering, a custom build, etc). You're there to provide tech support for your wife. To diagnose an SSD issue when most would have returned the device. To "reinstall" Ubuntu from a method Poulsbo scoffs at from a bootable USB device. To compile whatever software she needs or fetch ppas, repos, debs, scripts, etc to update the user software from 8.04's versions to a semi-usable state. I wish my spouse were half as knowledgeable as that, to be able to toil with my computer and navigate all the complexities for me! Your wife is quite lucky to have you. (Again, luck plays into being able to use an up-to-date Ubuntu system...for more than 6 months at a time, if that ;) ). So here's my story featuring a couple and a Dell mini. Two dell minis, in fact. 
A woman bought a Dell mini with Ubuntu 8.04 and her husband bought the Windows XP version. I daresay the woman who bought the Ubuntu model was confused at first, but grew to love the simplicity, speed, and elegance of the system tremendously... for the greater part of a year. Then the pattern decisively reversed for exactly the reasons discussed above, and she sold it to buy a Windows netbook shortly after "learning her lesson". Her husband, who'd bought the windows one initially, uses the same netbook today. OpenOffice alerts and guides him to download any updated versions, Firefox updates itself seamlessly, and to use the new printer was a point and click from the manufacturer's website to the installable EXE mentioned in the manual (it used to be as easy as plugging in the cord for the Ubuntu system before the devs just stopped updating the printer support). 

But again, I digress. None of this innocent but misinformed misinterpretation of how great hardware support is -- based on your case study of specific heavily researched hardware and the technical knowhow to wave away potential showstoppers with a few deft terminal commands -- in any way relates to the core of my main point. See first post.

---

### Post by Zlatan on 2011-03-22
you don't have to upgrade every 6 months. your desktop is supported for 18months and even longer if you're on LTS. there's NOTHING forcing you to upgrade.

---

### Post by LifeTheHound on 2011-03-22
> **Zlatan said:**
> you don't have to upgrade every 6 months. your desktop is supported for 18months and even longer if you're on LTS. there's NOTHING forcing you to upgrade.

Thanks for the input, but I wish you'd read even a few paragraphs of the first post. 

What forces people to upgrade their system (besides an 18 month "support" period) is out-of-date user software that undergoes critical stability and feature releases that are never made available (or "backported", which is a silly and deceptive word to describe new, tested, stable user software which, for the most part, can even be compiled with the very same toolchain against the very same framework and libraries as previous versions; exceptions can be statically linked with updated libs). 

Hardy LTS is still technically "supported" by this narrow definition, but the user software is completely obsolete to the point of being unusable for productive and competitive work in any modern setting, as it doesn't support modern media formats, document formats, and productivity features that have since become essential in the modern world. It is not competitive or capable of maintaining basic feature parity with other popular operating systems with rolling user software (including 10yr old Windows XP) in that respect, and is therefore "flawed" on that basis and the many others I've described in great detail. Please read the first post, part of the first post, or any fragments of my subsequent posts on the matter before regurgitating an argument I've addressed so thoroughly and repeatedly, from so many contexts and use cases, and with so many examples it makes my head spin. 

Thanks.

PS: Nice blog, though. ;)

---

### Post by snowpine on 2011-03-22
I think the major flaw in your logic is that Microsoft Windows XP does **not** provide an effortless "rolling release" of end-user applications (office suite, browser, etc.). Windows is an operating system only; the individual user is responsible for installing and upgrading each additional application individually, with no organized package manager like in Linux.

You propose an ideal situation (stable "core" with rolling release apps) and argue Ubuntu is flawed because it does not automatically meet this ideal without some amount of user intervention. However, Windows XP does not meet your ideal without some user intervention either (does a default-out-of-the-box Windows XP install include Word 2010, Firefox 4.0, the latest multimedia codecs, etc.?), therefore by your own logic Windows XP has flaws of its own. 

At the end of the day, there is a maintenance cost to running any computer system over time. My personal experience is that it takes roughly 20 minutes to completely install and configure Linux on [supported hardware]("http://www.ubuntu.com/certification/") (including a full suite of all productivity apps I need for my job) while achieving a fresh Windows XP install with all the apps I need takes a couple of days (and several hundred dollars). But maybe your experience is the exact opposite, and I respect your testimonial. 

The nice thing is we have lots of choices; if some guy on an internet forum says Ubuntu is great, and another guy says Windows is better, I can try both and form my own opinion based on my own experience. And the beauty of open-source is that, if I cannot find an existing distro that meets my needs, I am free to start a new project to create the perfect distro. :)

---

### Post by uRock on 2011-03-22
> **LifeTheHound said:**
> <snip>
Sounds like you are looking for a rolling release. There's always Debian Testing or Arch.

---

### Post by psusi on 2011-03-22
> **beew said:**
> 
If it is risky to use unsupported software and ppas (Ubuntu's official line) then how would it be less risky to upgrade the whole OS?

Simple: the new OS has been well tested to work as a whole, but some build someone put in their ppa has not been well tested on a 2 year old release.

> **beew said:**
> Another point is that Ubuntu once in a while goes on compulsive risk taking, e.g unity is a small one, and Wayland would be much bigger. Now what if you don't want to gamble with your working system but still want updated user softwares?  

Then Ubuntu isn't for you.  Most people prefer Ubuntu over Debian exactly because it aggressively updates to the latest and greatest, which is a little risky.

> **beew said:**
> Finally, what if you have a system perfectly tweaked and customized and don't want to lose it  after barely 6 months and yet still want your software to be up to date?

The upgrade process handles this quite well for most people.

> **beew said:**
> PPA (install from source or .deb) is a solution, but as I said way back, it is a way to circumvent the official limitation. If the only way for the system to work is to circumvent it then the system is flaw.

When you go get a hammer instead of your trusty wrench to insert a nail into a piece of wood, that does not mean the wrench is flawed; it means you are using the wrong tool for the job.

This thread boils down to "Ubuntu doesn't work perfectly for me, doing exactly what I want when I want without mistake, therefore, it is an unqualified failure, and I blame the release cycle."

Bollocks.

It has been explained why the release cycle works well and how you can get what you want: fork over some cash and ask that it be used to hire someone to put more effort into the backports system.  It is a manpower problem, not a release cycle problem.

Now can we leave this thread back in the grave where it was happily resting for months?

---

### Post by beew on 2011-03-22
> **psusi said:**
> Simple: the new OS has been well tested to work as a whole, but some build someone put in their ppa has not been well tested on a 2 year old release.


Well what can be worse with ppa not well tested? You have to reinstall, --it is very unlikely, but you are telling is  it is better to reinstall in 6 months (ie. implementing the worse case scenario) Does it make any sense?

> 
Then Ubuntu isn't for you.  Most people prefer Ubuntu over Debian exactly because it aggressively updates to the latest and greatest, which is a little risky.

This confirms to me that you haven't even read one single post from OP despite posting so many rebuttals (or you have read but never comprehend) Ubuntu is aggressively updating the OS but the user software are forever playing catch up. That is the basic issue OP tries to address. In other words, what needs "aggressive updates" are not getting them, while what requires longer term stability is being compulsively and aggressively updated. (Debian stable is of course neither, it is basically for people who wouldn't mind running totally obsolete software on obsolete OS for the sake of stability,--as in  doesn't change)

Even in Ubuntu some softwares get old and obsolete even at time of release because of the repo freeze. If you risk backward incomaptibility and breakage to upgrade the OS every 6 months you get less outdated, but hardly bleeding edge. I am here only talking about user softwares.

6 months may not be a very long time for commercial software but with opensource it can make a big difference. The reason is that commercial softwares usually don't get released unless they are reasonably usable and well polished (or you would want your money back) and once purchased you don't get new features for a long time because it is unrealistic to expect users to pay again in few months (consider MS Office). But open source often doesn't do in house testing and it relies on community feed back to add new features and fix bugs so chances are there can be usability problems and critical features may be missing at any given time and they get fixed through rapid updates. Having the repo frozen for 6 months means you can be forever using inferior, buggy obsolete versions and get none of the benefit of the rapid development cycle of open source.

As an example, when I got Lucid the document reader was a total piece of crap, it was incredible slow and didn't render pictures properly,but what a change in 10.10, it is smooth and fast l was like wow. It turned out there has been several releases between Lucid and Maverick but none of them get into the Lucid repo. in fact Lucid is still running the crappy version even now.

One particular area is multimedia. If you care to read the threads in the multimedia section you would know many multimedia softwares in the Ubuntu repo are  broken or crippled (like mplayer, vlc etc) and to get the best performance (or even basic functions some times) out of your hardware you would have to either get a ppa or compile from source. The official system is adequate only if you don't care about performance.


> The upgrade process handles this quite well for most people.

Well how do you figure that? Who are "most people"? Care to provide some evidence?

If you read the forum threads many people have issues with distro upgrades and the advice by experienced  users is  always "do a clean install" I have done an experiment, I took a fresh install of Lucid, installed a few software from the official repos (no ppas) and upgraded it to Maverick, it took a few hours and it hanged on the first attempt. You call this "quite well"?

Now if you have some  customized configurations, ppas or propietary drivers the process would be even more messy.


> This thread boils down to "Ubuntu doesn't work perfectly for me, doing exactly what I want when I want without mistake, therefore, it is an unqualified failure, and I blame the release cycle."

Bollocks.

It has been explained why the release cycle works well and how you can get what you want: fork over some cash and ask that it be used to hire someone to put more effort into the backports system.  It is a manpower problem, not a release cycle problem.
Yet they have the manpower to make a new release every 6 months with some compulsive risk taking such as Unity and Wayland,--which will break a lot of graphic cards if they rush it like they do with Unity,-- yet they don't have the manpower to consolidate and maintain what is working (Unity is not ready even by their own admission. They expect to get the basic features nailed down and fix most of the bugs by the time of official release but other usability features will have to wait til 11.10, so one wonders why they make Unity the default UI when by their own admission it is not ready)

You have explained nothing, address nothing, you are just here to spew the party line ad nauseum and may I add, in a very high handed and arrogant fashion which is really a turn off.

---

### Post by psusi on 2011-03-22
> **beew said:**
> Well what can be worse with ppa not well tested? You have to reinstall, --it is very unlikely, but you are telling is  it is better to reinstall in 6 months (ie. implementing the worse case scenario) Does it make any sense?

I can't understand this.

> **beew said:**
> I am here only talking about user softwares.

This is once again "I want package X backported to the old, stable release", which is accommodated by the release cycle, but does not have enough people working on it so that quite often package X has not been backported when you want it.

> **beew said:**
> Well how do you figure that? Who are "most people"? Care to provide some evidence?

The millions of people using Ubuntu who DON'T come complain on the forums about upgrade problems.  They aren't all doing a clean reinstall every release.

> **beew said:**
> If you read the forum threads many people have issues with distro upgrades and the advice by experienced  users is  always "do a clean install" I have done an experiment, I took a fresh install of Lucid, installed a few software from the official repos (no ppas) and upgraded it to Maverick, it took a few hours and it hanged on the first attempt. You call this "quite well"?

There are a few people on the forums who advise that.  Most people don't advise it, and most people don't do it.  There are a few people around the forums who have been upgrading every release since hardy or before.  It doesn't work for everyone, but it does for most.

> **beew said:**
> Yet they have the manpower to make a new release every 6 months with some compulsive risk taking such as

Yes, because this is their goal; to not be a 3 year release cycle of old, stale software like Debian, and it is this that has made Ubuntu so successful.  Supporting backports to keep a relatively smaller number of people happy takes a lot more effort for a lot less benefit.

> **beew said:**
> You have explained nothing, address nothing, you are just here to spew the party line ad nauseum and may I add, in a very high handed and arrogant fashion which is really a turn off.

I have explained how the process works, why it is done that way, and how it addresses your concerns.  Ignoring it does not change that fact.

---

### Post by beew on 2011-03-22
> **psusi said:**
> 

The millions of people using Ubuntu who DON'T come complain on the forums about upgrade problems.  They aren't all doing a clean reinstall every release.



There are a few people on the forums who advise that.  Most people don't advise it, and most people don't do it.  There are a few people around the forums who have been upgrading every release since hardy or before. .


There are also millions of people who don't use the forums at all, does it therefore follow that only a few people have need for forum support?

You also don't know how many people have simply given up and move back to Windows. Or how many people who only read without posting.

Your argument is basically the absence of evidence = the evidence of absence. Good thinking and I really can't take you seriously when you resort to such intellectual dishonesty (or you could be genuinely confused, if that is the case that would also make me question your ability to comprehend what is written)
[B]
EDITED:[/B] again the issue is not whether i am getting package X, I get package X from ppas so thank you very much. The issue OP tries to address is a structural one, not relating to any particular package. By repeatedly setting up strawman (after being pointed out to you many times)  it really only paints you in a bad light. You come across as either deliberately obtuse or genuinely clueless. So stop playing that game for your own sake.

---

### Post by tgm4883 on 2011-03-22
> **LifeTheHound said:**
> <snip>

O..M...G

So as much as I didn't want to, I read thought that giant wall of text.

In that huge post, you missed on a few points. The users that don't know anything about computers aren't usually the ones that go and install Ubuntu. They upgrade their OS by buying a new system. 

Also, I'm unsure exactly what you mean regarding the SSD issue I was having. It's faulty hardware, which has absolutly nothing to do with the OS. My wife doesn't come to me for Ubuntu support, and has no idea how to diagnose a faulty drive. But neither do most Windows users. When dealing with a faulty piece of hardware, on any OS, a user would take that to someone who could fix it. Be that a computer repair shop or a tech savvy friend. Ubuntu could have 10 year release cycles and still wouldn't be able to deal with some types of faulty hardware, no OS can. 

I'll respond to it with what another poster already said. Use the correct tool for the job. It's obvious that Ubuntu isn't the right choice for you. Instead, you should be using a rolling release such as Arch (or even Debian testing). This is precisely why there are different distros, so you have a choice and can use what works best for you.

> **LifeTheHound said:**
> 
Please answer honestly: have you even talked to a classmate, college, acquaintance, older family member about this? Or considered ever not having to be constantly on call for tech support for a newbie every 6 months? Honestly, some serious fieldwork seems to be required for many developers who grew up into the Linux community (or are absurdly lucky) actually see how the "mainstream" really works. To me it's obvious as a result of intense and extensive experience with them, in addition to my very own frustrations with these problems, for which the current release cycle again takes the great bulk of the blame. 


Yes, I so do wish I didn't have to be tech support for my family every six months, as I have many friends and family who come to me with their computer issues. Guess what though, out of all of them that come to me with computer issues, 100% of them are Windows users. None of my friends or family that that use Ubuntu have come to me for support. Oh, they do come to me, but it's usually for praise. 

You can blame the release cycle all you want, but the problem is you are using an OS that isn't the right fit. Stop using the butt end of a screwdriver to pound in nails.

---

### Post by tgm4883 on 2011-03-22
> **beew said:**
> There are also millions of people who don't use the forums at all, does it therefore follow that only a few people have need for forum support?

You also don't know how many people have simply given up and move back to Windows. Or how many people who only read without posting.

Your argument is basically the absence of evidence = the evidence of absence. Good thinking and I really can't take you seriously when you resort to such intellectual dishonesty (or you could be genuinely confused, if that is the case that would also make me question your ability to comprehend what is written)
[B]
EDITED:[/B] again the issue is not whether i am getting package X, I get package X from ppas so thank you very much. The issue OP tries to address is a structural one, not relating to any particular package. By repeatedly setting up strawman (after being pointed out to you many times)  it really only paints you in a bad light. You come across as either deliberately obtuse or genuinely clueless. So stop playing that game for your own sake.

Actually, his forum argument is pretty valid. There are Ubuntu users. A subset of those users are on the Ubuntu forum. Statistically speaking, we can draw from the number of users on the forum who complain about the release cycle vs the users who don't and get a good idea about how large the issue actually is. Doesn't matter if the users just read instead of post, as both sides have that.

Also, please do not do personal attacks. They are against the forum rules.

---

### Post by beew on 2011-03-22
Actually Debian testing is not that up to date. I have an installation of LMDE and some software in their repo is older than Ubuntu's (and the gap is even bigger with ppas) Ubuntu takes a snap shot of Debian unstable, which is newer than Debian testing. I don't know how long would software remain in Debian unstable before they make it into testing, but it is not the newest build you would get. (Actually I think LMDE had some problems with drivers or something when it just came out because the Debian kernel is too old to work with newer hardware and they had to later make a respin using a newer kernel)

---

### Post by snowpine on 2011-03-22
I'm looking now at the 5 top ranked distros at distrowatch.com.

Ubuntu is not rolling release. It has a 6 month release schedule with 18 months of support (more for LTS releases).
Mint is not rolling release. It has a 6 month release schedule with 18 months of support.
Fedora is not rolling release. It has a 6 month release schedule with 13 months of support.
Debian is not rolling release. It has a (roughly) 24 month release schedule with (roughly) 36 months of support.
OpenSUSE is not rolling release. It has an 8 month release schedule with 18 months of support.

These are (arguably) the 5 most popular non-enterprise Linux distros. I don't see how the "most Linux users want a rolling-release distro with 10 years of support" assertion is supported by these statistics. Most users seem to prefer the "flawed" model of frequent, time-based, stable releases from the available evidence.

---

### Post by beew on 2011-03-22
> **snowpine said:**
> I'm looking now at the 5 top ranked distros at distrowatch.com.

Ubuntu is not rolling release. It has a 6 month release schedule with 18 months of support (more for LTS releases).
Mint is not rolling release. It has a 6 month release schedule with 18 months of support.
Fedora is not rolling release. It has a 6 month release schedule with 13 months of support.
Debian is not rolling release. It has a (roughly) 24 month release schedule with (roughly) 36 months of support.
OpenSUSE is not rolling release. It has an 8 month release schedule with 18 months of support.

These are (arguably) the 5 most popular non-enterprise Linux distros. I don't see how the "most Linux users want a rolling-release distro with 10 years of support" assertion is supported by these statistics. Most users seem to prefer the "flawed" model of frequent, time-based, stable releases from the available evidence.

It could be that these distros have other qualities that people want in spite of not being rolling. This is not evidence that people would not prefer a rolling release (if these other qualities are maintained) and that these distros are popular because they are non rolling.

For example, I would prefer Ubuntu (with ppas) over Debian testing, LMDE or Arch any day because of the ease of use, good hardware compatibility rich software support in the repo and beyond and large forum support etc.
[B]
EDITED:[/B] I don't think anyone is asking for 10 year support rolling release. I have no problem with 18 months of support, but instead of having 6 month releases it would be more sane to offer distro upgrade once a year and in between keep the user software up to date. The man power freed up from compulsory 6 month release cycle can be deployed  for consolidating, maintaining and building on what already works and doing development more thoroughly instead of unveiling half baked and buggy products just to meet the release deadline.

---

### Post by snowpine on 2011-03-22
> **beew said:**
> It could be that these distros have other qualities that people want in spite of not being rolling. This is not evidence that people would not prefer a rolling release (if these other qualities are maintained) and that these distros are popular because they are non rolling.

It *possible* that Americans prefer falafel to hamburgers, and that fast food chains like McDonald's, Burger King, and Wendy's are popular because of "other qualities that people want in spite of" the fact they don't serve falafel. 

Or maybe Americans like burgers... :)

Either way I agree that evaluating a product based on its popularity is tricky.

---

### Post by psusi on 2011-03-22
It is a basic fact of human psychology that we remember and complain about bad times, and not about good times.  That extends to people complaining about software quite well.  While not everyone who is dissatisfied complains, and not everyone uses the forums to complain, most people do, ergo, if people are not complaining, then you can quite reliably conclude that one of two things is true:

1)  There is nothing wrong, or
2)  Nobody is using the software in the first place

Even when you don't have anything wrong, statistically you will get lots of complaints when you have enough users.  Take World of Warcraft as an example.  Tens of millions of people playing, and there's always a few complaining on the forums that there is something wrong with WoW because their computer overheats and shuts down.  You don't see millions of people posting that their computers run WoW just fine, because they are busy well, playing WoW, or having more interesting conversations elsewhere on the forums.

Ubuntu didn't get to be as popular as it is because everyone has the same problems you do.  Some people have problems upgrading, but that does not mean everyone does.

---

### Post by beew on 2011-03-22
removed for double posting by author

---

### Post by beew on 2011-03-22
> **psusi said:**
> It is a basic fact of human psychology that we remember and complain about bad times, and not about good times.  That extends to people complaining about software quite well.  While not everyone who is dissatisfied complains, and not everyone uses the forums to complain, most people do, ergo, if people are not complaining, then you can quite reliably conclude that one of two things is true:

1)  There is nothing wrong, or
2)  Nobody is using the software in the first place

Even when you don't have anything wrong, statistically you will get lots of complaints when you have enough users.  Take World of Warcraft as an example.  Tens of millions of people playing, and there's always a few complaining on the forums that there is something wrong with WoW because their computer overheats and shuts down.  You don't see millions of people posting that their computers run WoW just fine, because they are busy well, playing WoW, or having more interesting conversations elsewhere on the forums.

Ubuntu didn't get to be as popular as it is because everyone has the same problems you do.  Some people have problems upgrading, but that does not mean everyone does.


How about that for high handiness and arrogance? By that brilliant logic you can basically dismiss all negative feedbacks out of hand on almost any subject because invariably most people don't bother to express an opinion unless it is very urgent.  Computers (and lot of other things) is not a very high priority for most computer users. It is always only a relatively small number of people would bother to speak out on any given non essential issue.

---

### Post by Zlatan on 2011-03-22
> **beew said:**
> How about that for high handiness and arrogance? By that brilliant logic you can basically dismiss all negative feedbacks out of hand on almost any subject because invariably most people don't bother to express an opinion unless it is very urgent.  Computers (and lot of other things) is not a very high priority for most computer users. It is always only a relatively small number of people would bother to speak out on any given non essential issue.

negative feedbacks should be converted to bug reports somehow. and one more thing- as far as i remember- if you do not buy ubuntu support, it comes without any warranty (i'm not too sure about it, please correct me if i'm wrong). what do you complain about then? do you study what you install? have a life and deep breath, it is not so bad after all...

---

### Post by uRock on 2011-03-22
> **Zlatan said:**
> negative feedbacks should be converted to bug reports somehow
Why? Many of the complaints we see here on the forums were created by user error. That would create a huge need for people to work on the bug squad to go through bug reports and follow up on said reports, as many of the complaints we see here do not provide enough information to create a usable bug report.

---

### Post by 3Miro on 2011-03-22
> **Zlatan said:**
> negative feedbacks should be converted to bug reports somehow. and one more thing- as far as i remember- if you do not buy ubuntu support, it comes without any warranty (i'm not too sure about it, please correct me if i'm wrong). what do you complain about then? do you study what you install? have a life and deep breath, it is not so bad after all...

I second uRock on the bug report thing. Even support requests often don't provide enough information, negative feedback hardly ever provides anything useful for debugging purposes.

As for the warranty, Windows and all Linux distributions come with no warranty (for Mac the hardware, like all hardware, comes with warranty, but I doubt the software has any, in fact I don't think any software anywhere comes with any warranty). You CAN purchase support form Canonical, which gives you a phone number that you can call and ask questions to payed staff, people who are obliged to help you. Here you get volunteers for free.

You can also purchase a computer with Linux pre-installed, depending on the company, you also get payed staff to answer your questions (check the System76 forum here for example). Those situations are even better as the corresponding company knows both the software and hardware.

---

### Post by Zlatan on 2011-03-22
> **uRock said:**
> Why? Many of the complaints we see here on the forums were created by user error. That would create a huge need for people to work on the bug squad to go through bug reports and follow up on said reports, as many of the complaints we see here do not provide enough information to create a usable bug report.

my meaning was- filling bug reports should be much more productive than any kind of negative feedback. and studying on what you install. this does not require any super knowledge.
that was for guys that want something constructive anyway- for the OP.

---

### Post by snowpine on 2011-03-22
Share your ideas/suggestions at [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by NCLI on 2011-03-22
> **beew said:**
> There are also millions of people who don't use the forums at all, does it therefore follow that only a few people have need for forum support?

You also don't know how many people have simply given up and move back to Windows. Or how many people who only read without posting.

Your argument is basically the absence of evidence = the evidence of absence. Good thinking and I really can't take you seriously when you resort to such intellectual dishonesty (or you could be genuinely confused, if that is the case that would also make me question your ability to comprehend what is written)
I actually have quite good evidence that the upgrade process is not very problematic. 

If you look at the users who voted in the official stability poll for the past many releases, you can see that the number of people who have issues with a clean install is only slightly lower than the number of people who have problems with upgrades nowadays.
From that, we can conclude that out of all the people who come here for support and notice the poll, only a small percentage of their problems are caused by the upgrade process, with the large majority being caused by changes between releases, or problems that were there in the previous release as well.

[Here are the stats, you can confirm it yourself.]("https://spreadsheets.google.com/ccc?key=0AhT2q9EW-seKdDBYV2ZXZ3FKcFl4Q0dBWjFHOFUtb2c&hl=en_GB")

---

### Post by beew on 2011-03-22
So firefox 4 just comes out today. It will never appear in the Maverick repo so if I want it I would have to install from Mozilla or through its ppa. What do people such as psusi suggest me to do?

Wait til late April to upgrade to Natty and losing all my Maverick customization (and risk breaking something, as of now the nvidia driver in Natty is not working) or forget about it because ff3 is still "supported"?

I am going for the ppa, thank you very much.

---

### Post by beew on 2011-03-22
> **NCLI said:**
> I actually have quite good evidence that the upgrade process is not very problematic. 

If you look at the users who voted in the official stability poll for the past many releases, you can see that the number of people who have issues with a clean install is only slightly lower than the number of people who have problems with upgrades nowadays.
From that, we can conclude that out of all the people who come here for support and notice the poll, only a small percentage of their problems are caused by the upgrade process, with the large majority being caused by changes between releases, or problems that were there in the previous release as well.

[Here are the stats, you can confirm it yourself.]("https://spreadsheets.google.com/ccc?key=0AhT2q9EW-seKdDBYV2ZXZ3FKcFl4Q0dBWjFHOFUtb2c&hl=en_GB")


This is what I think.

A clean install takes about 20 min and maybe another 30 mins to reinstall your software (provided nothing breaks, driver still works etc). Customization and reinstalling third party softwares will take a lot longer, but upgrading would make this even worse.

An upgrade takes several hours and if your system is not pristine enough (say you have third party software, have ppa enabled, or may be proprietary drivers ) it may not even go through.  Now if you have skipped the 6 month upgrade before the upgrade would have to go through all the intermediate versions that you have skipped and it would take even longer. During that couple of hours you may be so lucky that you loose your internet connection and then you are screwed (that can happen to me as I mostly use wireless)

So finally let's say everything appears to work. How do I know there isn't anything hidden that got messed up, maybe a configuration file somewhere, which would not manifest until later? When it manifests you probably wouldn't even know what hits you.

So, no, I would always do clean install when the time comes.

But clean install vs upgrade  is only a side issue. I just don't see the rationality of upgrading the whole system, having to overhalt everything, gamble with my stable install which has been working perfectly, lose my customization and go through the hassles of redoing them (if it is possible, but maybe the new system wouldn't even allow it) All that just because I need some key softwares to be up to date.

---

### Post by NCLI on 2011-03-22
> **beew said:**
> So firefox 4 just comes out today. It will never appear in the Maverick repo so if I want it I would have to install from Mozilla or through its ppa. What do people such as psusi suggest me to do?

[Yes it will.]("https://wiki.ubuntu.com/DesktopTeam/Specs/Lucid/FirefoxNewSupportModel")
> **beew said:**
> This is what I think.

A clean install takes about 20 min and maybe another 30 mins to reinstall your software (provided nothing breaks, driver still works etc). Customization and reinstalling third party softwares will take a lot longer, but upgrading would make this even worse.

An upgrade takes several hours and if your system is not pristine enough (say you have third party software, have ppa enabled, or may be proprietary drivers ) it may not even go through.  Now if you have not been doing the 6 month upgrade before the upgrade would have to go through all the intermediate versions that you have skipped and it would take even longer.
Ok, so you'd never want to do an upgrade anyway, then why are you complaining that upgrades are unstable??
> 
So finally let's say everything appears to work. How do I know there isn't anything hidden that got messed up, maybe a configuration file somewhere, which would not manifest until later? When it manifests you probably wouldn't even know what hits you.
How do you know there isn't something broken that the testers didn't notice after doing a clean install? You don't.

> So, no, I would always do clean install when the time comes.

But clean install vs upgrade  is only a side issue. I just don't see the rationality of upgrading the whole system, having to overhalt everything, risk,gambling with my stable install which works perfectly, losing my customization and going through the hassles just because I need some key softwares to be up to date.
The problem is that most "user" packages in Ubuntu depend on "system" packages to work. So in order to have the latest version of something, you need to upgrade other packages as well, leading to instability.

That is why PPAs sometimes cause problems.

---

### Post by beew on 2011-03-22
> **NCLI said:**
> 

The problem is that most "user" packages in Ubuntu depend on "system" packages to work. So in order to have the latest version of something, you need to upgrade other packages as well, leading to instability.

That is why PPAs sometimes cause problems.


So far I haven't had a problem that cannot be solved by purge ppa or disabling/enabling some repos. 

What is the worst stability issue that can be caused by a problematic ppa? That it messes things up so badly that I have to do a clean install, but what you are saying is that I should do it every 6 months even if nothing is broken. That is actually the worst case scenario you are recommending others to go through to avoid much more manageable stability problems that may arise from ppas!

Does it make any sense my friend?

---

### Post by NCLI on 2011-03-22
> **beew said:**
> So far I haven't had a problem that cannot be solved by purge ppa or disabling/enabling some repos.
Which is why it is a very, very bad idea to bring what the PPAs do into the main repo. Then you can't simply purge them.

> What is the worst stability issue that can be caused by a problematic ppa? That it messes things up so badly that I have to do a clean install, but what you are saying is that I should do it every 6 months even if nothing is broken. That is actually the worst case scenario you are recommending others to go through to avoid much more manageable stability problems that may arise from ppas!
When did I advise you to avoid PPAs?? I use plenty of PPAs myself, I think they're a great solution to this problem, and that they need to be featured more prominently.

---

### Post by tgm4883 on 2011-03-22
I say use LTS+PPA's, but it's obvious that this thread is going nowhere

---

### Post by BobSongs on 2011-03-23
I've never liked topics that seem to present technical data that can go over the average user's head resulting in Fear, Uncertainty and Doubt, only to have some release of Windows presented as the solution to every Linux problem ("If only Linux worked more like Windows!").

I can't say I've scrutinized every post in this thread. Mainly because, as with the previous post, I see this as going nowhere.

Ubuntu is an operating system. Okay? Period! It isn't MacOS and it sure isn't Windows! And by golly Canonical isn't bound to either of those O/Ses development cycles.

Putting Ubuntu onto someone's machine is always a risk. More technical users delight in the options at hand and all the tweaking to get things going. We like knowing how the guts of our PCs work and respond. And the average PC owner, who thinks his/her O/S is called "Word", doesn't want to know any more about the inside of his/her PC than the inside of his/her automobile's engine area. And I'm not going to go tell BMW that their machines should resemble Fords in order to please Americans.

These posts about how superior Windows is to Linux make me laugh. Why? Easy: I fix Windows PCs. I see the OS hobbling all the time, corrupted by some of the lamest and stupidest scams and pitfalls. I'll install Win7 on a friend's box only to drop in a few months later to hear about how THIS doesn't work or THAT isn't working. I sit and try to re-establish a connection with a wireless printer that's definitely registered as being on the network... only to have Win7 see it intermittently. I shake my head and sigh that the system isn't Linux.

Then? I realize that if it WERE Linux, I'd only drop in to fix things less regularly.

So, yay for Windows: It keeps me employed. If only my Linux customers would call me as frequently. Oh well.

This thread should be locked.

---

### Post by Shining Arcanine on 2011-03-23
> **LifeTheHound said:**
> The idea is simple in words, not quite as simple in execution, but nonetheless profoundly necessary. Here's a somewhat compelling idea for a release cycle:
*Stable base + rolling stable user software + **optional** system upgrades/backports (kernel, modules, etc -- for those with new/unsupported hardware).*
But please, never accept anyone's opinion without sufficient foundational elaboration. That said, please allow me to explain my (and perhaps much of the target demographic's) position. 

I most heartily concur. See opposing arguments and my follow-ups or explanations throughout this thread. 

I had naively, painstakingly set up Ubuntu 9.04 for a few friends who now don't get even critical updates... friends who, when they naively tried upgrading to a new distro version in desperation, ALL ended up with somewhat broken systems and couldn't/wouldn't invest the week or so in their busy schedules acquiring the ultra-technical expertise necessary to debug everything from graphics to sound to multimedia breakage, and so switched to Windows 7 for practical reasons. 

This happens *all the time*. I've experienced it myself and seen it take place in much the same way with friends and acquaintances. Ubuntu's current release cycle can be likened to a baby into whom you're forced to invest substantial time to turn into a functional adult... an adult who then seems to immediately pass away and leaves behind yet another baby in his wake. It's a constant, back-breaking investment on the part of both the users and the developers, whereas with other (obviously more popular) operating systems, the "adult" (who often comes as a teen at youngest, not a baby) works for you for up to **10 years**, to invoke the XP example. 

*Ideal case: Stable base + rolling user software + **optional** system upgrades/backports (kernel, modules, etc).*

Debian fails at this because it is not user-friendly to set up and does NOT update any user software, so it suffers from an extreme case of Ubuntu's 'lock-in' problem, but with software that's even older. At the opposite extreme, Arch also fails at this because it, too, is user-unfriendly and rolls *system* upgrades along with user software, making it constantly unstable and producing breakage even more rapidly than a 6-month cycle. It's the pinnacle of irony that Microsoft, for instance, who can't seem to get anything right, got the one thing right that actually mattered -- system support. How? Having a proper release cycle. It ensured constant user software updates by maintaining one release for a long time, and it ensured hardware compatibility by ensuring drivers are built against a single kernel version (with, again, is obviously possible in linux too; see ubuntu-backports-modules-XX for an ironic and poorly implemented example).

You are "barking up the wrong tree". If you want what Ubuntu gives you, then use Ubuntu. If want something else, then use something else. Don't expect Ubuntu to change just because you don't agree with it. Instead, change operating systems to one with which you agree.

Speaking of which, if you do not agree with how Canonical does things, why do you even care in the first place? You could be using Gentoo or FreeBSD, which do far more for you in this regard than Canonical ever will.

---

### Post by LifeTheHound on 2011-03-23
> **snowpine said:**
> I'm looking now at the 5 top ranked distros at distrowatch.com.

Ubuntu is not rolling release. It has a 6 month release schedule with 18 months of support (more for LTS releases).
Mint is not rolling release. It has a 6 month release schedule with 18 months of support.
Fedora is not rolling release. It has a 6 month release schedule with 13 months of support.
Debian is not rolling release. It has a (roughly) 24 month release schedule with (roughly) 36 months of support.
OpenSUSE is not rolling release. It has an 8 month release schedule with 18 months of support.

These are (arguably) the 5 most popular non-enterprise Linux distros. I don't see how the "most Linux users want a rolling-release distro with 10 years of support" assertion is supported by these statistics. Most users seem 

to prefer the "flawed" model of frequent, time-based, stable releases from the available evidence.

No. These distros are popular because they are easy to use and only break the system once every 6 months rather than potentially once a day with the current flawed "rolling **system**" model. I don't want Ubuntu to become 

these ultra-flawed systems. Ubuntu's current model (roll nothing, update every 6 months) is far better than Arch's roll everything all the time. Read my first post again please. I propose rolling user software (the non-

breakage stuff) on a stable hardware base with optional hardware backports for new hardware support. I know of no distro that does this, but Ubuntu is in the best position to do so and leverage its popularity on behalf of its 

large user base and the mainstream who need it. 

> **tgm4883 said:**
> A subset of those users are on the Ubuntu forum. Statistically speaking, we can draw from the number of users on the forum who complain about the release cycle vs the users who don't and get a good 

idea about how large the issue actually is. Doesn't matter if the users just read instead of post, as both sides have that.

Again, most of the people who read, post, and vote on these forums are not the mainstream, who aren't aware of the forum's existence unless/until they have these very problems and go through the drawn-out process to fix them, 

become gurus, and therefore forget their own plight or those of many others a year down the road. When the next poll comes up, guess how "difficult" it was for these forum goers? 

My evidence is the dozens of genuinely mainstream I've worked with on equally mainstream systems. Fieldwork, people. If Ubuntu had a "real-world usability check" position, I'd apply in a heartbeat with boatloads of evidence 

to prove it. A priori simply isn't enough. 

> **psusi said:**
> Simple: the new OS has been well tested to work as a whole, but some build someone put in their ppa has not been well tested on a 2 year old release.

PPAs are nice, but only serve to plug the gaping hole left by the negligent backports on the part of the official Ubuntu channels due to lack of manpower. Were the proposed release system be used instead of the burn-out 

inducing biannual cycle, more than enough manpower would be available to not necessitate ppas. 

I've had mixed experience with ppas. They're often not as optimized as Ubuntu releases, don't play well with other DE's (firefox, openoffice come to mind), and may not receive security updates if the ppa maintainer decides 

for some reason to give up providing updates altogether. 

> Then Ubuntu isn't for you.  Most people prefer Ubuntu over Debian exactly because it aggressively updates to the latest and greatest, which is a little risky.

The upgrade process handles this quite well for most people.

This thread boils down to "Ubuntu doesn't work perfectly for me, doing exactly what I want when I want without mistake, therefore, it is an unqualified failure, and I blame the release cycle."

Bollocks.

I'm sorry, but you've missed the point and the dozens of real-world examples I've directly had a hand in. It would also serve to re-familiarize yourself with the notion of 
*stable base + rolling user software + OPTIONAL system backports only if necessary*. No other distro I know of does this, especially the likes of the "edge/unstable" distros like Arch, Debian Unstable, etc.
> It has been explained why the release cycle works well and how you can get what you want: fork over some cash and ask that it be used to hire someone to put more effort into the backports system.  It is a manpower 

problem, not a release cycle problem.
I addressed the manpower issue repeatedly as follows. The manpower currently allocated to the 6-month ground-up release cycle can (and like I propose, should) be reallocated to my proposed cycle in the interest of all. 

Because it isn't re-inventing the wheel twice a year, it might actually take significantly *less* manpower overall than the current cycle, another win. 


> **psusi said:**
> This is once again "I want package X backported to the old, stable release", which is accommodated by the release cycle, but does not have enough people working on it so that quite often package X has 

not been backported when you want it.

Exactly the manpower allocation point I mentioned. To summarize: the current release cycle doesn't allow for the sufficient manpower for the ideal case.

> The millions of people using Ubuntu who DON'T come complain on the forums about upgrade problems.  They aren't all doing a clean reinstall every release. 

True! But this supports my proposed release sytem, not the current one. Thanks for bringing this up! Re-read my comments on the forum knowledgeability of the mainstream. Approximately 4/5 of the dozens of test cases 

(mainstream users with mainstream systems, including many of my own) switch to windows or get tech support [me] soon enough, not the forums. Most don't know of these particular forums, what a forum is, and are afraid to 

register for websites they liken to "chat rooms." Googling for support for all the technical issues that would lead them to the forum in the first place is also a skill the mainstream for some reason hasn't picked up 

(although googling everything else from people's names to why their cat poops on the rug to how to diagnose a cold, etc are googled every minute). Please don't interpret lack of forum evidence as evidence the status quo is 

optimal.


> Yes, because this is their goal; to not be a 3 year release cycle of old, stale software like Debian, and it is this that has made Ubuntu so successful.  Supporting backports to keep a relatively smaller number of 

people happy takes a lot more effort for a lot less benefit.

No, please re-read my first post. The ideal case is stable base + rolling user software (debian does not do this) + optinal, non-default backports of system software, drivers etc (debian testing, arch et al roll system 

software with the user stuff unnecessarily, causing constant breakage, hence the name "unstable" and its lower popularity).

> I have explained how the process works, why it is done that way, and how it addresses your concerns.  Ignoring it does not change that fact.

No, you haven't, because it seems you haven't actually read the first post, not to mention my rebuttals to many of the same misunderstandings as yours. Familiarize yourself with my proposal and the notion of 
*Stable base + rolling user software + OPTIONAL hardware backports* as I've laid it out. 


> **uRock said:**
> Sounds like you are looking for a rolling release. There's always Debian Testing or Arch.

Nope, read above. Rolling releases also roll system software and are therefore patently unstable (as the name suggests). Please re-familiarize yourself with the concept of "stable, long-term system base [this is key!] + 

rolling user software [so no obsolete and uncompetitive user software like openoffice/gimp/etc -- even KDE point releases] + OPTIONAL system BACKPORTS [this is the most important aspect of all -- at install time the system 

can simply detect whether or not to install 'linux-backports-modules-XX' or the user can do so himself to support new hardware]." 

This will of course take up the manpower that will be saved stopping the feverish biannual releases. 

> **NCLI said:**
> I actually have quite good evidence that the upgrade process is not very problematic. 

If you look at the users who voted in the official stability poll for the past many releases, you can see that the number of people who have issues with a clean install is only slightly lower than the number of people who 

have problems with upgrades nowadays.
From that, we can conclude that out of all the people who come here for support and notice the poll, only a small percentage of their problems are caused by the upgrade process, with the large majority being caused by changes 

between releases, or problems that were there in the previous release as well.

[Here are the stats, you can confirm it yourself.]("https://spreadsheets.google.com/ccc?key=0AhT2q9EW-seKdDBYV2ZXZ3FKcFl4Q0dBWjFHOFUtb2c&hl=en_GB")
You obviously have not been reading carefully. This poll is actually humorous to me because in the very same statistical assumptions I made earlier, I assumed the scenario was [i]a lot better than this poll "proves" it to be

[/i]. My goodness, I don't know whether to smile or to frown, but I'll thank you for supporting my proposed system nonetheless. Please re-read the first post and my latest posts, for your own good if nothing else. To 

reiterate (which I feel like I'm doing a lot of, sadly): 1. Assuming this means 50% of people have trouble with a single upgrade (which most mainstream users would be stuck not knowing how to fix), use the 'AND' rule to 

figure out what the odds are the same person would be able to encounter perfect success the second time. Or third. Or forth (that's a mere 2 years worth of updates with this existing flawed release cycle). .5 x .5 x .5 x .5 = 

6.25% success. Linux for the masses indeed. XD  2. The people who come online to post are the 'basically savvy', not the mainstream. Remember I'm talking about the mainstream. In my experience, not a single one of the dozens 

of truly mainstream users (not enthusiasts) have posted (or voted) on this forum, and many don't know what a forum is at all, much less 'register' at this one.

> **snowpine said:**
> I think the major flaw in your logic is that Microsoft Windows XP does **not** provide an effortless "rolling release" of end-user applications (office suite, browser, etc.). Windows is an 

operating system only; the individual user is responsible for installing and upgrading each additional application individually, with no organized package manager like in Linux.

Flaw? Perhaps you misunderstand. XP takes setup only once. The setup time in an ideal case is debatably similar to the ideal Ubuntu case. By default, windows programs are set to update themselves or direct users to an update 

EXE. Windows keeps itself and office up to date automatically, as does Firefox by default, as does OpenOffice, antivirus, etc. 

I must again refer to my dozens of case studies. Even when tech support is required ("Should I trust OpenOffice when it says it wants to download the latest 'updates'?"), it's a walk in the park. With Ubuntu, it's impossible 

to install the latest LibreOffice and have it work properly (the ppa version, by the way, is broken with the KDE desktop and has some other glitches). 

This is not a flaw in my argument. It is resounding support for it. Think about it once more. ;) 

> You propose an ideal situation (stable "core" with rolling release apps) and argue Ubuntu is flawed because it does not automatically meet this ideal without some amount of user intervention. However, Windows XP does 

not meet your ideal without some user intervention either (does a default-out-of-the-box Windows XP install include Word 2010, Firefox 4.0, the latest multimedia codecs, etc.?), therefore by your own logic Windows XP has 

flaws of its own. 

At the end of the day, there is a maintenance cost to running any computer system over time. 
Again, at the risk of being a bit too obvious, this only supports my argument (and it's not Ubuntu that's flawed, it's the release cycle.) Kubuntu doesn't come with GIMP. It doesn't come with some pretty-much essential Amarok 

plugins. It doesn't come with basic video and image editing programs. It doesn't come with multimedia plugins. It doesn't come with the necessary proprietary drivers to have a fully functional system (including wifi in some 

cases). ;) This is still not the point, however, which is that after the system is set up, XP need not be actively user maintained for many, many years. Ubuntu needs maintenance (often extremely heavy maintenance--sometimes 

impossible maintenance--and I refer you again to my dozens of experiences for evidence of both ideal and suboptimal 'mainstream' cases) every 6 months. 

> My personal experience is that it takes roughly 20 minutes to completely install and configure Linux on [supported hardware]("http://www.ubuntu.com/certification/") (including a full suite of all productivity 

apps I need for my job) while achieving a fresh Windows XP install with all the apps I need takes a couple of days (and several hundred dollars). But maybe your experience is the exact opposite, and I respect your 

testimonial. 
Again, it's not simply a personal experience, and it's not merely a testimonial. Well, many of my examples are, but the dozens I've set up over the years make it not quite so personal, and a compelling reflection of the 

mainstream. It's a solid proposal that's being misunderstood right and left by people who think they've heard it before. 

Again, let me remind you that even on this supported hardware, there are bugs that the user has to work around (and this list does not reflect a large number of them; for instance, headphones don't work properly on the 

world's most popular HP laptops, requiring deep config manipulation). Some require setup of proprietary drivers (for instance, a few people I set up Ubuntu for needed a closed wifi driver and couldn't get on the internet at 

all after an upgrade because most people in the city don't have wired connections or think to use them). It requires EXPERTISE. KNOWLEDGE. ABILITY. **The mainstream does not have this expertise.** I don't care how trivial 

you think it is to repeat the "20 minutes" every few months (and just setting up medibuntu+dvd, wine, user config, ppas [needed due to lack of properly maintained backports], proprietary drivers, debugging upgrade problems 

(which occur the majority of the time, no matter how trivial someone with knowledge of "sudo" thinks they are), etc... this is AGAIN besides the point. The point being, of course, that my proposed release cycle will benefit 

everyone and hurt nobody at all. 

> The nice thing is we have lots of choices; if some guy on an internet forum says Ubuntu is great, and another guy says Windows is better, I can try both and form my own opinion based on my own experience. And the 

beauty of open-source is that, if I cannot find an existing distro that meets my needs, I am free to start a new project to create the perfect distro. :)
And the mainstream who don't talk about either Windows or Ubuntu on any form whatsoever will obviously *choose* a more functional end-user system. Read first post. Currently there is no *choice* that weds a stable 

base to rolling user software and optional system backports. Ubuntu is the best candidate for this reason due to its [initial/niche] popularity with enthusiasts and the solid funding developer team it employs. I am an 

intermediate-level user who happens to have tremendous amounts of experience with dozens of mainstream users who have been introduced (many by my own hand) to functional Ubuntu systems and who then lose the functionality in a 

few months and grow quite disillusioned with Linux in general. 

> **NCLI said:**
> 
Ok, so you'd never want to do an upgrade anyway, then why are you complaining that upgrades are unstable??
You answered your own question. Unnecessary system upgrades are unnecessary and potentially dangerous. Therefore, they should be optional and provided as optional backports. I really wish people would read at least the first 

paragraph of the first post.[/quote]

> How do you know there isn't something broken that the testers didn't notice after doing a clean install? You don't.
Which is why a longer period of testing that comes as a *side effect of* my proposed release cycle is also incredibly useful. Also, since system upgrades won't be rolled and will be optional as backports, this is 

unnecessary for those, too, as only those who need them will use them and test them for others who do. It's a problem of logistics, and not a terribly complicated one, at that. One solution to the question of "how do we test 

the backports then?" is the obvious analogous case to Ubuntu's current "testing" repository. See how elegant this can be? I'd love to go into specifics about exactly how this model would work. Perhaps in a different thread 

for those unwilling to even try to understand this proposal? 

> The problem is that most "user" packages in Ubuntu depend on "system" packages to work. So in order to have the latest version of something, you need to upgrade other packages as well, leading to instability.

That is why PPAs sometimes cause problems.
PPA's cause problems because they are built differently, are poorly maintained, are poorly tested (often by only one person not affiliated with Ubuntu), and do not include proper bindings or Ubuntu patches. (Often the Ubuntu 

team patches releases to work properly with Ubuntu's framework. This is of course a time consuming process that repeats every 6 months -- in my proposed release system, it would only happen once every odd number of YEARS at 

the most. PPA builders don't include these patches and as a result the programs have problems in certain cases. If Ubuntu itself maintained them, this wouldn't be an issue). As for "requiring upstream system dependencies," 

which I think you are trying to get at, this is often not actually the case, surprisingly enough, especially for the most popular packages. Often these stated dependencies are nominal at best and are an artifact of the build 

environment at worst. A cursory code review would prove that this is often unnecessary. For the few cases it is, static libs can be provided without any extra effort (this means the program comes with what it needs to work, 

like BSD and Windows). Again, it's a matter of logistics I'd be more than happy to discuss, but this is what I mean by a "reallocation of manpower." See above.

---

### Post by LifeTheHound on 2011-03-23
> **BobSongs said:**
> I've never liked topics that seem to present technical data that can go over the average user's head resulting in Fear, Uncertainty and Doubt, only to have some release of Windows presented as the solution to every Linux problem ("If only Linux worked more like Windows!").
This isn't really about what you or I might like in terms of operating systems. I love Ubuntu a tremendous amount more than I like Windows, for one thing. This isn't even a matter of opinion. If you read carefully and actually come to an understanding as to what I'm talking about, you'll see that I present quite a compelling solution to a very large problem that prevents Ubuntu from seeing the adoption rates we'd like (and especially full-time usage rates, re-uptake rates, and usage outside the enthusiast community). 

> I can't say I've scrutinized every post in this thread. Mainly because, as with the previous post, I see this as going nowhere.
It is obvious you haven't. Please take the time to at least understand where I'm coming from. I'm not complaining without offering a solution, and I'm not bashing without taking the time to exhaustively and repeatedly explain myself at every step. So far I have managed to present a solution to every problem that has been brought up, but I spend most of my time correcting misconceptions from people who do not understand the basic tenets of the release cycle I am proposing. 

> Ubuntu is an operating system. Okay? Period! It isn't MacOS and it sure isn't Windows! And by golly Canonical isn't bound to either of those O/Ses development cycles.
Of course it's an OS, and of course Canonical isn't bound to the competition! For this reason and countless more, I love it, and I don't like Windows and MacOS. *But I am taking the time to address in great length one of the biggest hurdles to mainstream adoption of Ubuntu* since 'mindshare', and one that will certainly increase even that once the plethora of issues related to the release cycle are fixed. You'd be surprised how many people love Ubuntu after they get it working (or it is set up for them by Dell, a manufacturer, a techie, etc) -- and the vast majority of these very people who grow disillusioned with it when it invariably either doesn't provide user software updates in an existing version or forces an entire system upgrade to do so (which in turn is is needlessly tedious at best and devastating at worst, with emphasis on the latter for the "mainstream"). I've done it dozens of times. Ubuntu's stated goals isn't to "be different for the sake of being different" or be "techie-friendly only" -- quite the contrary! This is a big thing, believe it or not. 

> 
Putting Ubuntu onto someone's machine is always a risk.
It doesn't have to be. That's a central part of my main point. And a central reason for this "risk" you speak of is the release cycle. Re-read the first post at least.

> More technical users delight in the options at hand and all the tweaking to get things going. We like knowing how the guts of our PCs work and respond. And the average PC owner, who thinks his/her O/S is called "Word", doesn't want to know any more about the inside of his/her PC than the inside of his/her automobile's engine area.
This yet another result of the release system and its flaws -- you're saying that Ubuntu is therefore usable only to techies and tinkerers. According to Ubuntu itself, this is a problem. This is actually one goal of Ubuntu's goals, to overcome and circumvent this "tinkerer/enthusiast/techie-only" conception surrounding linux. Ubuntu is designed to be user-friendly, stable, and easy-to-use. The release cycle, however, is counterproductive to these ends, and not only maintains the status quo, but causes many former enthusiasts to drop it (or tentative adopters to drop it, or existing MAINSTREAM users to switch away). 

Also, if you read the Linux Haters blog (to "know thy enemy" if nothing else), a huge amount of the tongue-in-cheek but admittedly relevant criticism stems not from Linux at all, but are all artifacts and fallout of the current release system for MAINSTREAM users. Everything from occasional instability to lack of intuitiveness to upgrade hassles to ever-changing levels of hardware/software support, to unfounded zealotry, to false advertising promises (a 50% problem rate every upgrade is a popular source of bashing), to overworked staff who've already moved on to the next release and therefore won't/aren't disposed to fix a current one, lack of compatibility across versions of a distro, stereotypes of the entrenched techie-only userbase, etc etc. For more elaboration, I'd be happy to write an article for you. 

> These posts about how superior Windows is to Linux make me laugh. 
And it makes me depressed that you misunderstand me to the point of putting words in my mouth that would make me gag. Because someone points out a single (though tremendous) flaw in the release cycle of an operating system they love, specifically *because* they love it and want to improve and spread it, makes me very sad indeed. I beg you to read before posting, even if it's only a small amount, and to keep an open mind, even if it hurts your commercial interests that Ubuntu become usable and self-maintainable to the mainstream.

---

### Post by uRock on 2011-03-23
I'm not the one complaining the system is flawed. There is a reason that there are only a handful here complaining of the release cycle. It works just fine the way it is.

I am unsubscribing since this thread is going nowhere.

---

### Post by LifeTheHound on 2011-03-23
> **uRock said:**
> I'm not the one complaining the system is flawed. There is a reason that there are only a handful here complaining of the release cycle. It works just fine the way it is.

I am unsubscribing since this thread is going nowhere.

I have explained to you countless times why there are only a handful here doing so. Please read my post where I addressed the topic of my extensive experience with dozens of newbies and mainstream users, statistics, and forum-going. You are repeating yourself again without even reading or trying to understand. 

I beg you to spend some time with a mere 4 or 5 mainstream computer users you've installed Ubuntu for. You'll understand the hard way, since you refuse to even understand any of my points or facts (not opinions), and also decline to comment even once about any of them, instead criticizing me. 

The thread is going nowhere because so far either people haven't understood, don't want to understand, or are downright spiteful. I haven't heard a single argument *against* my proposal. Not a single one, except the misguided "if it works, don't fix it" mantra which not only betrays a lack of experience with newbies, but also by definition fails to address why my proposal won't still be *better* than the current system! It's hurtful, unprofessional, and inherently unproductive. 

I believe I've addressed in great detail, and often repeatedly for those new to the thread who haven't read through it (or the first post), every point that has been made. The vast majority of posts made under misunderstood pretenses (usually with the intention to bash or criticize) have actually lent a great deal of support to my proposal, and I always reply to gently show how this is the case.  I'd like anyone new to this thread to keep that in mind. This is not a hostile environment, and I invite anyone, with any level of professional know-how, to read my proposal and share your comments (as this forum was intended). 

If anything is unclear, or you'd like elaboration about anything, I'd be more than happy to reply in whatever level of detail you like, always with an open mind and with the intention to promote understanding. If there's a detail or a point you believe I got wrong, don't hesitate to call me out on it -- but please, only do so after attempting to understand my proposal. While simple and elegant to me, I've found it to have been quite difficult for many people to understand, and many people seem to believe I'm advocating anything remotely similar to any of the following: 
- that I dislike Ubuntu for whatever reason, or like something else more.
- that this is a purposeless rant or personal complaint/testimonial 
- that Ubuntu become Windows or Mac
- that Ubuntu be a rolling unstable distro like Arch, Debian Testing, or similar
- that Ubuntu be transformed into Debian stable or similar
- that I propose an untenable stability/modernity trade-off within the current cycle
- that what I propose already exists in another distro or within Ubuntu

If you have a rebuttal that implicates one of the above, please do a bit more reading-up first to keep this thread clean and civil (not to mention keeping repetition to a minimum). Thanks!!

---

### Post by wojox on 2011-03-23
> **LifeTheHound said:**
> rather than potentially once a day with the current flawed "rolling **system**" model.

Really? I run Arch with absolutely no problems. Do you speak from experience or hearsay?

---

### Post by LifeTheHound on 2011-03-23
> **wojox said:**
> Really? I run Arch with absolutely no problems. Do you speak from experience or hearsay?

Both to varying degrees, although on an HP system Arch did actually have less issues than an Ubuntu upgrade for me, but my experience is too limited to know either way. In any case, the merits of a rolling system over a non-rolling system is not at all the point of the thread (though I'd be more than happy to discuss and hear testimonials of other distros, too). It has been my experience that Arch is openly targeted to existing linux users (or tinkerers in general) than Ubuntu, and for this reason if nothing else it's not a perfectly viable drop-in to other mainstream OS's and computer users like Ubuntu strives to be. 

But since we're off topic, I grant you that I have heard wonderful success stories from people using Arch -- almost as many, proportionately, as those who've had success upgrading between Ubuntu versions, but not quite. ;) As far as a pure rolling release goes, I've heard nothing beats Arch. And I believe it. If you're even moderately linux-competent and aren't afraid of living on the edge (even if that edge is more stable than most), I would of course recommend Arch. But this isn't about distro-hoppers, or even the stability of Arch as a rolling distro as opposed to Ubuntu's 6-month cycle upgrades (for all I know the stability could be similar!). The point is that users should have to upgrade hardware-interfacing components until and unless they opt to/have to. If this seems to good to be true, and a tall and overly idealized scenario for the mainstream, I would suggest the first post be read again. 

But again, back to the topic, this thread isn't meant to be a personal testimonial or complaint on behalf of myself or any Linux-savvy 'distro hopper.' From my testing, Ubuntu seems to be the most accessible and user-friendly variant of any free operating system, and it also seems that Ubuntu is always straddling the cusp of being a perfectly viable OS alternative for mainstream computer users (at least after an initial setup/bugfix). No, this thread is intended as a solid proposal squarely aimed at a component of Ubuntu --its release cycle-- on behalf of the millions of genuinely mainstream computer users Ubuntu seeks to attract. This actually brings to mind a quote issued earlier in the thread: 

> **Shining Arcanine said:**
> You are "barking up the wrong tree". If you want what Ubuntu gives you, then use Ubuntu. If want something else, then use something else. Don't expect Ubuntu to change just because you don't agree with it. Instead, change operating systems to one with which you agree.

Speaking of which, if you do not agree with how Canonical does things, why do you even care in the first place? You could be using Gentoo or FreeBSD, which do far more for you in this regard than Canonical ever will.
You see, *for some reason there's an overwhelming impression that this is all about me (notice the word "you" is used many times), or existing Ubuntu/Linux users, and not about mainstream computer users*, dozens of whom I've set up with Ubuntu because it comes closest to perfect of any free desktop OS I know of (even if it still falls short due to reasons the developers can't really help -- and one big one they can; cue first post!). Let's discuss this from the perspective of the demographic of the millions of regular computer users Ubuntu is trying to make inroads into. I think I might need to re-write my first post; perhaps I was a bit too direct in light of the fact that most people here are expecting a free-for-all individualistic approach rather than a perfectly feasible idea that would potentially help the millions in Ubuntu's core demographic. The fact is, the savvier, techier, and more computer/Linux capable you are, the less you will be benefited by my proposal. The less time you spend "in the field" with newbies, the less you will understand where I come from, even if *my proposal truly helps everyone* (albeit to varying extents), not just the largest potential userbase. :) (For explanation of whom and how, refer to previous posts).

---

### Post by tgm4883 on 2011-03-23
[QUOTE=LifeTheHound]<snip huge wall of text>[/QUOTE]

Summary for the lazy

> Stable system software with very long release cycle. Rolling release for user mode software. Security fixes get backported for system software. Everyone wants this. This would without a doubt make Ubuntu better. Ubuntu builds every release from the scratch, I'm not even sure what a Debian import is.

If you say people don't want this type of system then you are wrong. If you try to post some numbers to back up the claim that people don't want this type of system I'll just say that those numbers are wrong. Any statistics you have that don't agree with my point of view are invalid. I'll use arguments that forums are used by people that have issues with Ubuntu, unless it doesn't fit my argument at that time. If Ubuntu has an issue, it is a direct result of the release cycle. If you try to blame anything else, you are wrong. 


I think I'm with uRock, unsubscribbing

---

### Post by LifeTheHound on 2011-03-23
> **tgm4883 said:**
> Summary for the lazy

> Stable system software with very long release cycle. Rolling release for user mode software. Security fixes get backported for system software. Everyone wants this. This would without a doubt make Ubuntu better. Ubuntu builds every release from the scratch, I'm not even sure what a Debian import is.

If you say people don't want this type of system then you are wrong. If you try to post some numbers to back up the claim that people don't want this type of system I'll just say that those numbers are wrong. Any statistics you have that don't agree with my point of view are invalid. I'll use arguments that forums are used by people that have issues with Ubuntu, unless it doesn't fit my argument at that time. If Ubuntu has an issue, it is a direct result of the release cycle. If you try to blame anything else, you are wrong. 


I think I'm with uRock, unsubscribbing

This is a very disrespectful and incorrect interpretation of essentially everything I've said up to this point. I've bent over backwards to address every statistic provided, which also don't show why people wouldn't want my system. I haven't seen any statistic (much less an explanation!!) of why anyone, especially the core intended demographic (mainstream computer users) wouldn't want this system, even once in this entire thread. I welcome statistics that say people do not want it, and with these statistics, I'd like an explanation. None were forthcoming, but it seems fear of change, misunderstandings, and personal attacks are the norm instead. On the other hand, I do have plenty of statistics (dozens, based on the mainstream users I've set up with Ubuntu). I've also never disregarded a statistic present, and instead showed how it *actually supported my proposal*. From the start I assumed the existence of statistics far more favorable to the null hypothesis (the status quo) than you have presented. 

Please do not add a personal spin to this proposal, or make assumptions that I've tried to deconstruct plenty of times. Threatening to unsubscribe because you don't want to understand or read what I wrote or give me the opportunity to respond to your concerns...that's your concern. But advertising your unsubscription after bashing me personally not only comes off as immature and spiteful, but entirely non-constructive to the thread. I would appreciate responses to anything I've written. In lack of being willing/able to so, and posting blatantly accusatory "summaries" that are not only incorrect but confusing to new readers and disloyal to the very premise upon which this thread is based.

Let me respond in-quote (responses in bold):
> I'll use arguments that forums are used by people that have issues with Ubuntu, unless it doesn't fit my argument at that time. 
[b]I was attempting to address and balance between forumgoers who come to the forum because they were enthusiasts, those who stumbled upon the forums by accident, and those that don't use forums at all, which is a significant portion of both the current userbase and the novice demographic I am vouching for, both based off of perfectly statistical evidence (for instance, for the current userbase, the number of speculated users, the number of ISO downloads, etc is orders of magnitude higher than forum-goers, etc). 

Even if the forumgoers argument on my part was completely invalid, such a point represents one of the tiniest inconsequential (not to mention somewhat off-topic) exposatory points I made and has little to do with the proposal itself. I was also contextualizing the one statistic you displayed (which also had nothing to do with the number of people, mainstream or otherwise, who have grounds to oppose my proposal). I then took the presented statistics and applied a simple statistical rule to demonstrate that by your own presentation, you were shooting yourself in the foot by claiming that the existing release system is superior to a proposal that has not yet even been understood, much less properly presented. [/b]

If Ubuntu has an issue, it is a direct result of the release cycle. 
If you try to blame anything else, you are wrong. 
[b]Many of ubuntu's issues stem indirectly from the release cycle, including testing time, upgrade issues, backport manpower, configuration tediousness, and all of the numerous examples I've given, which represent to great extent the problems encountered by dozens of 'mainstream' computer users I'd initially set up with (K)Ubuntu.

Passing the blame is also not good, and many proximate causes are not, in fact, the release cycle. But if you consider the ultimate causes for many of the observable effects of these proximate causes, you'd see that many of these issue, even they aren't solved by the proposed release cycle, can nonetheless be addressed more effectively, with greater manpower and testing, and with greater opportunity for workaround, with my proposal. 

Let's take JUST ONE of these long-term manifestations of the issue, *even if ubuntu's release cycle isn't the CAUSE of the problem at all!*--bug filing/tracking. I've seen many bug reports in trackers that have been filed against projects only to be blamed on a bunch of things, which is fine. But a more accurate trace would rule out the underlying effect of the many "supported" versions of Ubuntu and older "supported" versions of a piece of software that have been corrected upstream. 

Less releases to support, less versions to support between releases, less potential for the bugs resulting from lack of testing and the many versions (of both release and software) maintained. Problems will be fixed more easily this way, since everyone will be using the same distro release, and the software built only for that release. What's more, the version used will be rolled/updated ("backported") to the stable upstream feature releases, which depending on the magnitude of the changes, can hit the "testing" repository first (again, working it out is merely a matter of logistics, repo/update-manager setup, etc).[/b] 

Ubuntu builds every release from the scratch, I'm not even sure what a Debian import is.
**This is an example of making assumptions with the intent to criticize. I would appreciate it if these stopped. A personal retort is the last defense of a failed argument. And yes, I know what it is, and I know that Ubuntu bases its release off an unstable snapshot, replete with all underlying architectural and framework changes both within that snapshot and those Ubuntu imposes atop them. How does the nature of 'Debian imports' detract from my proposal?**

---

### Post by johntaylor1887 on 2011-03-24
I know one thing. The ethos of linux won't change because of this "debate". 

It's amazing that people in a glorified chat room think they are going to affect change by rambling. But I guess it kills time though. Sometimes unsubscribing is the best thing to do, and get out and go for a walk.

---

### Post by LifeTheHound on 2011-03-24
Massive update and overhaul of the first post!
Hopefully this decisively addresses any misunderstandings that might yet exist, and as always, I'm happy to elaborate. 

> The ethos of linux won't change because of this "debate". 
I'm not sure I follow. Many Linux distributions already espouse different (and in some cases conflicting) release strategies. My proposal simply weds the inherently unstable "rolling distro" concept to the "stable base" concept in the way most conducive to mainstream usability, one of Ubuntu's primary goals. 

There's nothing inherently untenable about such a proposal on its most theoretical and idealistic level, at least.

[edit]Can a mod please change the thread title to match my modified title? The old title invited a lot of personal emotion which is obviously unwarranted for such a proposal. Thanks.

---

### Post by snowpine on 2011-03-24
I think you have a basic misunderstanding of how "rolling release" distributions work. Arch users are not forced to blindly update every package every day! Arch allows you to selectively upgrade only the apps you want (Firefox and LibreOffice for example) when you want (daily, weekly, monthly, never), and ignore updates you don't want (kernels and other system updates for example). Therefore your "some things rolling, some things stable" ideal can easily be achieved in Arch with an edit to your pacman.conf. 

I recommend reading the Arch Beginners Guide. Not only does it describe exactly how to achieve what you want, but it also gives a warning and specifically explains that your "stable core, rolling apps" proposal is a flawed idea that can lead to system breakage: 
[https://wiki.archlinux.org/index.php/Beginners'_Guide#Ignoring_Packages](https://wiki.archlinux.org/index.php/Beginners'_Guide#Ignoring_Packages)

> Please note that the power user is expected to keep the system up to date with pacman -Syu, rather than selectively upgrading packages. You may diverge from this typical usage as you wish; just be warned that there is a greater chance that things will not work as intended and that it could break your system. The majority of complaints happen when selective upgrading, unusual compilation or improper software installation is performed. Use of IgnorePkg in /etc/pacman.conf is therefore discouraged, and should only be used sparingly, if you know what you are doing.

For more info:
[https://wiki.archlinux.org/index.php/Beginners'_Guide#Ignoring_Packages](https://wiki.archlinux.org/index.php/Beginners'_Guide#Ignoring_Packages)

---

### Post by psusi on 2011-03-24
> **LifeTheHound said:**
> Ubuntu's current model (roll nothing, update every 6 months)

I keep trying to tell you and you keep ignoring me, that this is NOT Ubuntu's model.  Ubuntu's model is not roll nothing, but roll only critical fixes that aren't going to cause other breakage to everyone, and less critical, more risky updates to -backports for people to install if they want.

> **LifeTheHound said:**
> breakage stuff) on a stable hardware base with optional hardware backports for new hardware support. I know of no distro that does this, but Ubuntu is in the best position to do so and leverage its popularity on behalf of its 

Again, this IS what Ubuntu does; it just doesn't do the -backports part as much as it maybe could.  Also sometimes backports just aren't possible because software has dependencies.  A new version of application X might require a new version of library Y and application Z.  Getting these mixes right is hard work.

> **LifeTheHound said:**
> Again, most of the people who read, post, and vote on these forums are not the mainstream, who aren't aware of the forum's existence unless/until they have these very problems and go through the drawn-out process to fix them, 

Then whoever their more technical friend that set them up with Ubuntu would be coming to the forums and complaining that his friends keep going back to Windows because of this.  You seem to be the only one saying this.

> **LifeTheHound said:**
> I addressed the manpower issue repeatedly as follows. The manpower currently allocated to the 6-month ground-up release cycle can (and like I propose, should) be reallocated to my proposed cycle in the interest of all. 

And that will do more harm to more people than it will help, which is why it isn't going to happen.  Ubuntu became popular because every 6 months you can upgrade and see progress being made, rather than being stuck with the same poorly functioning system for years.  That isn't going to go away to free up more manpower to work on backports, which if you pardon my language, is like pissing up a rope.

> **LifeTheHound said:**
> Because it isn't re-inventing the wheel twice a year, it might actually take significantly *less* manpower overall than the current cycle, another win. 

Actually, it would take more, because backports are harder than upgrading the whole system.

Since you keep arguing for a system that I keep pointing out Ubuntu already has, I think we're done here.

---

### Post by el_koraco on 2011-03-24
bianual (or shorter, as in opensuse's case) release cycles are the reason the top distros are the top distros. there's no better way of bringing in improvements than releasing new software and seeing it work in the field. some may call it as being in permanent beta stage, but say it's the price to pay for progress. that's why ubuntu has lts releases, in order to accomodate users who have no wish or time to experiment or adequate hardvare to go beyond a certain point. 

if the powers to be were to follow your advice, they would soon end up with a 99,5 percent stable, but completely stale system. and i don't just mean packages, i mean the whole thing. it's hard to see why users would then stick with ubuntu, rather then go back to debian.

it's precisely because of the rapid development cycle that maverick is the crown jewel of the gnome 2x desktop, and why the unity shell has the potential to be the norm for the gnome 3x desktop.

---

### Post by handy on 2011-03-24
Show me something that a flaw can't be found in?

---

### Post by ivanovnegro on 2011-03-24
> **beew said:**
> i think you are going off tangent. Op's point is that it is risky to have to upgrade the whole os every 6 months to get updated software. I don't think there is any reasonable argument against it. 

If it is risky to use unsupported software and ppas (ubuntu's official line) then how would it be less risky to upgrade the whole os? The worst thing a bad ppa could do is to break your system so badly that you need a clean  install,--extremely unlikely as you should check what is being installed and removed before going ahead. But you are now doing a clean install every 6 months as a ritual, how can anything be worse?

Another point is that ubuntu once in a while goes on compulsive risk taking, e.g unity is a small one, and wayland would be much bigger. Now what if you don't want to gamble with your working system but still want updated user softwares?  

Finally, what if you have a system perfectly tweaked and customized and don't want to lose it  after barely 6 months and yet still want your software to be up to date?

Ppa (install from source or .deb) is a solution, but as i said way back, it is a way to circumvent the official limitation. If the only way for the system to work is to circumvent it then the system is flaw.

+10!!

---

### Post by ivanovnegro on 2011-03-24
> **Zlatan said:**
> you don't have to upgrade every 6 months. your desktop is supported for 18months and even longer if you're on LTS. there's NOTHING forcing you to upgrade.

Seems you misunderstood his arguments.
What you are saying is the argument of LTS and not forcing to update, you did not discuss some basic points of LifeTheHound.

---

### Post by uRock on 2011-03-24
Keep it civil or this thread will get closed.

---

### Post by ivanovnegro on 2011-03-24
> **psusi said:**
> 

Now can we leave this thread back in the grave where it was happily resting for months?

Why? I find it quiet interesting and it is an uncomfortable discussion, I know.

> **beew said:**
> Actually Debian testing is not that up to date. I have an installation of LMDE and some software in their repo is older than Ubuntu's (and the gap is even bigger with ppas) Ubuntu takes a snap shot of Debian unstable, which is newer than Debian testing. I don't know how long would software remain in Debian unstable before they make it into testing, but it is not the newest build you would get. (Actually I think LMDE had some problems with drivers or something when it just came out because the Debian kernel is too old to work with newer hardware and they had to later make a respin using a newer kernel)

Thats the reason why I would not use LMDE, there is Arch and if you want a conservative rolling distro but also up-to-date there is also PCLinuxOS.
And about the whole discussion, this distro, Im using it also with Ubuntu makes many things like th OP described/wanted it.

> **snowpine said:**
> I'm looking now at the 5 top ranked distros at distrowatch.com.

Ubuntu is not rolling release. It has a 6 month release schedule with 18 months of support (more for LTS releases).
Mint is not rolling release. It has a 6 month release schedule with 18 months of support.
Fedora is not rolling release. It has a 6 month release schedule with 13 months of support.
Debian is not rolling release. It has a (roughly) 24 month release schedule with (roughly) 36 months of support.
OpenSUSE is not rolling release. It has an 8 month release schedule with 18 months of support.

These are (arguably) the 5 most popular non-enterprise Linux distros. I don't see how the "most Linux users want a rolling-release distro with 10 years of support" assertion is supported by these statistics. Most users seem to prefer the "flawed" model of frequent, time-based, stable releases from the available evidence.

Yes, they are on top, but I think also because they make good marketing that the other distros dont have. Two rolling release distros are also between the Top 10, Arch and PCLinuxOS but they dont recieve so much attention because they are not releases to talk about because it rolls. Every new release of Ubuntu/Mint/Suse got new reviews and you will see them in the media, thats the reason.

> **BobSongs said:**
> I've never liked topics that seem to present technical data that can go over the average user's head resulting in Fear, Uncertainty and Doubt, only to have some release of Windows presented as the solution to every Linux problem ("If only Linux worked more like Windows!").

I can't say I've scrutinized every post in this thread. Mainly because, as with the previous post, I see this as going nowhere.

Ubuntu is an operating system. Okay? Period! It isn't MacOS and it sure isn't Windows! And by golly Canonical isn't bound to either of those O/Ses development cycles.

Putting Ubuntu onto someone's machine is always a risk. More technical users delight in the options at hand and all the tweaking to get things going. We like knowing how the guts of our PCs work and respond. And the average PC owner, who thinks his/her O/S is called "Word", doesn't want to know any more about the inside of his/her PC than the inside of his/her automobile's engine area. And I'm not going to go tell BMW that their machines should resemble Fords in order to please Americans.

These posts about how superior Windows is to Linux make me laugh. Why? Easy: I fix Windows PCs. I see the OS hobbling all the time, corrupted by some of the lamest and stupidest scams and pitfalls. I'll install Win7 on a friend's box only to drop in a few months later to hear about how THIS doesn't work or THAT isn't working. I sit and try to re-establish a connection with a wireless printer that's definitely registered as being on the network... only to have Win7 see it intermittently. I shake my head and sigh that the system isn't Linux.

Then? I realize that if it WERE Linux, I'd only drop in to fix things less regularly.

So, yay for Windows: It keeps me employed. If only my Linux customers would call me as frequently. Oh well.

This thread should be locked.

Maybe Im wrong but I did not see that anybody said that Windows is better.

---

### Post by snowpine on 2011-03-24
I just wanted to chime in with a testimonial for CentOS. Until the recent release of Debian Squeeze, I was using CentOS 5.x every day on my work desktop. It offered an *extremely* stable core system (kernel 2.6.18!) but recent "rolling" versions of the end-user apps I care about (Firefox and OpenOffice). There is going to be a new CentOS 6 release soon, too. Highly recommended.

---

### Post by slackthumbz on 2011-03-24
I actually like the frequent release cycle, I like playing with the latest software. I accept that a by-product of that is that sometimes things will break or be less dependable but if I really wanted rock solid stability I'd use Debian. I'm looking forward to Natty and to seeing what it has to offer compared to previous releases.

Bring it on.

---

### Post by beew on 2011-03-24
> **ivanovnegro said:**
> 


Thats the reason why I would not use LMDE, there is Arch and if you want a conservative rolling distro but also up-to-date there is also PCLinuxOS.
And about the whole discussion, this distro, Im using it also with Ubuntu makes many things like th OP described/wanted it.

.



I cannot get pass the UI of PCLinuxOS. It is like they are trying so hard to look like Windoze XP, that is enough to turn me off.

---

### Post by ivanovnegro on 2011-03-24
> **beew said:**
> I cannot get pass the UI of PCLinuxOS. It is like they are trying so hard to look like Windoze XP, that is enough to turn me off.

Thats right in certain aspects but as KDE is unlimited to customizations it wont look like Windows especially not like XP, there are also other flavors like Gnome that could look just like Ubuntu if you want.
Dont blame the looks, what is under the hood is more important. :)

---

### Post by beew on 2011-03-24
> **el_koraco said:**
> bianual (or shorter, as in opensuse's case) release cycles are the reason the top distros are the top distros. there's no better way of bringing in improvements than releasing new software and seeing it work in the field. some may call it as being in permanent beta stage, but say it's the price to pay for progress. that's why ubuntu has lts releases, in order to accomodate users who have no wish or time to experiment or adequate hardware to go beyond a certain point. 

Sorry dude, that doesn't  make any sense unless you assume the majority of users use computers for testing rather than to do actual work.

I don't want to get into a debate on OpenSuse but tried it briefly recently, buggy as hell and the installer didn't even see all my partitions, wireless didn't work and if this is cutting edge it should remain in the lab until they work out the details.

I am all for innovations, I am not asking for 10 year rolling distro (neither is OP  I think). This can be implemented if they make available experimental isos instead of releasing half baked technology (just to meet the 6 month release requirement) and  expect everyone to trade in their working systems for testing out new technology. 

Take Unity, for example, why would they make it the default while they are still scrambling last minute to nail down the basic features? Wouldn't it make more sense to make it an option or to release experimental isos to get feed back  until they are ready to roll out a full feature version? (This is not going to happen until at least 11.10) Why in such a rush to make a bad first impression especially for new users who had no experience with Linux?  I shudder to think what would happen if they rush to make Wayland the default when hardware supports are not in place.

I should add that some people who are most loud in yelping "bring on the breakage" are not even Linux users in the real sense. They keep Windows (or Mac) for production purpose and install Linux on the side for experimentation. For such people I can see why they don't care whether things actually work as long as they get their fix for the fetish for something new and shiny.

---

### Post by beew on 2011-03-24
> **ivanovnegro said:**
> Thats right in certain aspects but as KDE is unlimited to customizations it wont look like Windows especially not like XP, there are also other flavors like Gnome that could look just like Ubuntu if you want.
Dont blame the looks, what is under the hood is more important. :)


I know, it may be irrational, but just looking at the screenshots kills me and they even call themselves "PC"?? I expect more self respect from a Linux distro than that. :)

---

### Post by ivanovnegro on 2011-03-24
> **beew said:**
> 

I should add that some people who are most loud in yelping "bring on the breakage" are not even Linux users in the real sense. They keep Windows (or Mac) for production purpose and install Linux on the side for experimentation. For such people I can see why they don't care whether things actually work as long as they get their fix for the fetish for something new and shiny.

That was not bad, Im using for example only Linux on my systems, no "fallbacks" to Windows or Mac. :)
Ubuntu is a testing bed, every release a new surprise, good or bad, but there is no real consistency even if it is one of the best distros out.

---

### Post by handy on 2011-03-25
> **ivanovnegro said:**
> That was not bad, Im using for example only Linux on my systems, no "fallbacks" to Windows or Mac. :)
Ubuntu is a testing bed, every release a new surprise, good or bad, but there is no real consistency even if it is one of the best distros out.

I have to disagree with you, as I have consistency.

I'm using Arch, I upgrade my entire system everyday unless I'm not home that day. I have the most consistent, stable & easy to maintain system that I have ever owned, with perhaps the exception in some areas where the AmigaOS was better, all those years ago.

---

### Post by el_koraco on 2011-03-25
> **beew said:**
> Sorry dude, that doesn't  make any sense unless you assume the majority of users use computers for testing rather than to do actual work.

I don't want to get into a debate on OpenSuse but tried it briefly recently, buggy as hell and the installer didn't even see all my partitions, wireless didn't work and if this is cutting edge it should remain in the lab until they work out the details.

I am all for innovations, I am not asking for 10 year rolling distro (neither is OP  I think). This can be implemented if they make available experimental isos instead of releasing half baked technology (just to meet the 6 month release requirement) and  expect everyone to trade in their working systems for testing out new technology. 

Take Unity, for example, why would they make it the default while they are still scrambling last minute to nail down the basic features? Wouldn't it make more sense to make it an option or to release experimental isos to get feed back  until they are ready to roll out a full feature version? (This is not going to happen until at least 11.10) Why in such a rush to make a bad first impression especially for new users who had no experience with Linux?  I shudder to think what would happen if they rush to make Wayland the default when hardware supports are not in place.

I should add that some people who are most loud in yelping "bring on the breakage" are not even Linux users in the real sense. They keep Windows (or Mac) for production purpose and install Linux on the side for experimentation. For such people I can see why they don't care whether things actually work as long as they get their fix for the fetish for something new and shiny.

as far as i've been able to observe, most of the "bring on the breakage" guys and gals are long time linux users not afraid of getting their feet wet with new ideas and not minding a little bit of tweaking here and there. some of them do keep windows or mac on their machines, either because they wanna play games, or because .docx formats can't be rendered fully in OO/LO. shayt, the real hard core ones use development releases, because they're having fun when something crashes. 

my experience with opensuse has been quite different than yours, as is those of all of my friends and acquaintances who regularly use it as a production OS (the only one). the experience i've had with people using ubuntu is also different. there's 60-year-olds who have it installed, hit the update manager every six months and a couple of hours later go "check it out, it's even more awesome". long time windows users have been overjoyed with having the mutter-unity version installed on their machines. but individual experience doesnt's have statistical value. 

i do see your point to an extent, as well as that of the OP, but it comes down to differences in strategy. ubuntu was created as a hybrid between the stability of debian and the innovation of cutting edge distros. they could have gone for a more conservative approach, but they obviously decided they'd roll out new, sometimes not really fully implemented features, taking the risk of pissing users off in the meanwhile. the end result is a distro that even the most hardcore linux users, if they are honest, admit is among the best ones. 

the only full time stats that you can see are those of the evergrowing base of ubuntu users. if things were constantly breaking, i just don't see how this growth would be maintained. so, it's a strategy that's been paying off, and changing it would be going against the "if it ain't broken, don't fix it" moto that one can read every time canonical decides tol do something about the ui.

---

### Post by ivanovnegro on 2011-03-27
> **handy said:**
> I have to disagree with you, as I have consistency.

I'm using Arch, I upgrade my entire system everyday unless I'm not home that day. I have the most consistent, stable & easy to maintain system that I have ever owned, with perhaps the exception in some areas where the AmigaOS was better, all those years ago.

I said this about Ubuntu and not about Arch or Linux in general. But you can disagree anyway. :P

---

### Post by Shmantiv_Radio on 2011-03-27
> **LifeTheHound said:**
> Well it hurts me, it hurts friends, it hurts everyone. Hardware support is one of the biggest qualms with desktop linux, and this is partly why-- once you get your hardware working, you have to switch distros and start over. At least if you want your software to keep up and stay relevant. 

A lot of people I know dropped linux in general because it was "too much tweaking for too many bugs across too many distros" and it was just too "high maintenence" to keep distro hopping. 

Ad hominem: attacking the person (op) instead of the problem.

You're right, but it's the same old catch 22.

---

