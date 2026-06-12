---
title: "Looking for a good KDE centered ubuntu like distro"
date: 2008-01-16
forum: Other OS Talk
---

### Post by JaggedOne on 2008-01-16
I am a gnome user looking to migrate to KDE. I have heard (and confirmed with experience) that Kubuntu is unstable and not the best KDE distro. Is there anything else out there that is KDE centric and uses the Ubuntu repositories?

Basicly what KDE distro is as close as Ubuntu as possible in terms of package management (with the exception of Kubuntu).

---

### Post by kellemes on 2008-01-16
Debian obviously..
It's not centered on anything, instead you have one of the best engine's to build you KDE-centric system on.

---

### Post by aks44 on 2008-01-16
Although Debian+KDE is a good choice (I'm running it, works fine), I wouldn't say that Debian is a KDE-centric distro... (in fact it's Gnome-centric).

Concerning stability, I am under the impression that Lenny (Debian testing) is way more stable than Kubuntu but I have yet to confirm that in the long run (I have had Kubuntu 7.04 for like 8 months, but I've been running Lenny for less than a month).

---

### Post by p_quarles on 2008-01-16
> **aks44 said:**
> Although Debian+KDE is a good choice (I'm running it, works fine), I wouldn't say that Debian is a KDE-centric distro... (in fact it's Gnome-centric).
Yes, and consequently any Debian- or Ubuntu- based distros are going to inherit some of the problems with KDE. Not that it's that bad, just "less good" than something like Mandriva or OpenSUSE. 

Mepis, though, is a KDE-centric distro that is Ubuntu-based. Haven't tried it, so I present this as a fact rather than a recommendation.

---

### Post by aks44 on 2008-01-16
> **p_quarles said:**
> Not that it's that bad, just "less good" than something like Mandriva or OpenSUSE.

From what I've seen and heard, Debian's KDE is very close to (if not exactly the same as?) the vanilla KDE project.

Despite the fact that it requires more work from the user for getting things correctly integrated together, I like that (haven't tried Mandriva or OpenSuse though, so I can't comment on those). YMMV. :)

---

### Post by JaggedOne on 2008-01-16
If I went with Debian+KDE, how would package management be different from ubuntu? It uses the same package system but not the same repositories, correct? Would I be able to use the many Ubuntu based guides on the interent? Would I be able to install the same software?

---

### Post by p_quarles on 2008-01-16
> **aks44 said:**
> From what I've seen and heard, Debian's KDE is very close to (if not exactly the same as?) the vanilla KDE project.

Despite the fact that it requires more work from the user for getting things correctly integrated together, I like that (haven't tried Mandriva or OpenSuse though, so I can't comment on those). YMMV. :)
That's exactly right, and Ubuntu's version is hardly altered at all. For those who dislike Kubuntu, Debian + KDE isn't likely to be a very good solution.

---

### Post by kellemes on 2008-01-16
> **JaggedOne said:**
> If I went with Debian+KDE, how would package management be different from ubuntu? It uses the same package system but not the same repositories, correct? Would I be able to use the many Ubuntu based guides on the interent? Would I be able to install the same software?


It's the same indeed.. you use other repositories but that's obvious since the packages are build for Debian.
You can use most guides from the Ubuntu community for Debian, although not all, and I'd check the Debian community first.
You can install a hole bunch of software, Debian has the largest repository of all.. if you need newer versions of software not in the repositories of the Debain-branche you're using, you can add repositories from other more bleeding edge Debian-branches.

Debian will install Gnome by default.. open synaptic, browse for KDE, install the lot, and you're on your way..
Listen, give it a try.. the worse that can happen is having fun. :popcorn:

---

### Post by SunnyRabbiera on 2008-01-16
Mepis is a good place to look, it is debian based and its pretty well developed.
You can give mandriva a shot as well, even though its not based on debian mandriva 2008 is a wonderful dist... a vast improvement over older versions.

---

### Post by aks44 on 2008-01-16
> **JaggedOne said:**
> If I went with Debian+KDE, how would package management be different from ubuntu? It uses the same package system but not the same repositories, correct? Would I be able to use the many Ubuntu based guides on the interent? Would I be able to install the same software?

Both Ubuntu and Debian are based on dpkg / apt-get / aptitude, so the package management is exactly the same. IIRC Debian repositories have a bit more packages available than Ubuntu, but I guess this is normal since I'm comparing Lenny vs Feisty. A more valid comparison would be Lenny vs Gutsy.

Now as a matter of fact, half of the resources I used to get my Lenny up and running were in fact (K)Ubuntu resources...


> **p_quarles said:**
> That's exactly right, and Ubuntu's version is hardly altered at all. For those who dislike Kubuntu, Debian + KDE isn't likely to be a very good solution.

I can only speak for myself here, but the *only* thing that bothers me with Kubuntu is its (un)stability. Which is why I'm perfectly happy with Debian ATM. But I can understand that some people may not like Kubuntu (vanilla KDE in fact) for other reasons, in which case I agree that Debian may not be a good choice.

---

### Post by p_quarles on 2008-01-16
> **SunnyRabbiera said:**
> Mepis is a good place to look, it is debian based and its pretty well developed.
You can give mandriva a shot as well, even though its not based on debian mandriva 2008 is a wonderful dist... a vast improvement over older versions.
And it's super easy to use. Mandriva has put an enormous amount of work into building GUI tools on top of the basic Linux + KDE setup.

---

### Post by mips on 2008-01-16
Archlinux+kdemod: You will never look back!

---

### Post by aks44 on 2008-01-16
> **SunnyRabbiera said:**
> Mepis is a good place to look, it is debian based and its pretty well developed.

Now you got me interested. I'm very reluctant to switch to anything that is not Debian-based for several reasons (quality of implementation and package management come first), and I can hardly stand any other DE than KDE. So Mepis may well be worth a try... :)

---

### Post by zipperback on 2008-01-16
> **JaggedOne said:**
> I am a gnome user looking to migrate to KDE. I have heard (and confirmed with experience) that Kubuntu is unstable and not the best KDE distro. Is there anything else out there that is KDE centric and uses the Ubuntu repositories?

Basicly what KDE distro is as close as Ubuntu as possible in terms of package management (with the exception of Kubuntu).


Ubuntu / Kubuntu / Fluxbuntu / Xubuntu are all built from  the same core distribution of Linux which happens to be Debian.

Ubuntu = Ubuntu with Gnome
Kubuntu = Ubuntu with KDE
Xubuntu = Ubuntu with Xfce
Fluxbuntu = Ubuntu with Fluxbox


They are ALL Ubuntu Linux. They just have different GUI Desktop Environments.

I use Ubuntu Gutsy 7.10 with Gnome, but I have several KDE based applications that I use, and it is no problem at all.
I installed the applications from the repositories using Synaptic and it installed the required dependencies and the applications run without problems.

- zipperback
:popcorn:

---

### Post by SunnyRabbiera on 2008-01-16
> **p_quarles said:**
> And it's super easy to use. Mandriva has put an enormous amount of work into building GUI tools on top of the basic Linux + KDE setup.

Oh yes, by almost every standard I think mandriva 2008 is much better then gutsy/feisty in terms of ease of use and getting things running.
I am very happy using mandriva 2008, despite some annoying but solvable bugs... but no one is perfect.

> **zipperback said:**
> Kubuntu and Ubuntu are both using the same core distribution of Linux.

The general difference is simply that Kubuntu ships with KDE for the default desktop and Ubuntu ships with Gnome for the default desktop.

Both of these distributions are VERY stable.

- zipperback
:popcorn:

eh, well Kubuntu 7.10 is definitely a step in the right direction as it is much more stable then older versions... but KDE in ubuntu isnt as good as in other cases.

---

### Post by aks44 on 2008-01-16
> **zipperback said:**
> The difference is simply that Kubuntu ships with KDE for the default desktop and Ubuntu ships with Gnome for the default desktop.

Both of these distributions are VERY stable.

Kubuntu is very UNstable, there is no appeal.

And I don't mean to look picky, but *buntu emphasizes bleeding edge software at the expense of some stability. The fact that it is based on Debian Sid snapshots speaks for itself...

If you want *real* stability, try Debian stable (currently, Etch) or better yet some BSD. Unfortunately the price to such stability is some obsolescence... ;)

---

### Post by pieisgood4589 on 2008-01-16
1 question- Why the heck hasn't anyone recommended openSUSE? Seriously. It's the second top Linux in the WORLD, for God's sake. :confused: Seriously. Is everyone here openSUSE-fearful? It's a great, superb, super-polished distro, the most polished one I have ever used in my try-outs of 52 Linux distros, but I quit using it because it wouldn't support my wireless card, and I was having trouble setting up ndswrapper.

Mint is also a great option, it's Ubuntu just mintified, and looks a lot more professional.

---

### Post by voteforpedro36 on 2008-01-16
> **pieisgood4589 said:**
> 1 question- Why the heck hasn't anyone recommended openSUSE? Seriously. It's the second top Linux in the WORLD, for God's sake. :confused: Seriously. Is everyone here openSUSE-fearful? It's a great, superb, super-polished distro, the most polished one I have ever used in my try-outs of 52 Linux distros, but I quit using it because it wouldn't support my wireless card, and I was having trouble setting up ndswrapper.

Mint is also a great option, it's Ubuntu just mintified, and looks a lot more professional.

openSUSE isn't Debian based though.

It uses YUM, but I've heard ups and downs about it.

---

### Post by zipperback on 2008-01-16
> **SunnyRabbiera said:**
> 
eh, well Kubuntu 7.10 is definitely a step in the right direction as it is much more stable then older versions... but KDE in ubuntu isnt as good as in other cases.


And which cases would those be? Kubuntu is very stable

- zipperback
:popcorn:

---

### Post by Malcy on 2008-01-16
Can I suggest PCLinuxOS. It's a stable kde system with origins in Mandrake. While it uses rpm, it does so through synaptic and I never had any dependency problems.

---

### Post by Whiffle on 2008-01-16
I installed Debian Lenny the other day, with KDE, and so far it works quite well, no real bugs to mention and way better than kubuntu in my opinion.  And, apt-get rocks.

---

### Post by SunnyRabbiera on 2008-01-16
> **zipperback said:**
> And which cases would those be? Kubuntu is very stable

- zipperback
:popcorn:

from my experience kde in ubuntu's repos and kubuntu is much more of a memory hog and a resource eater.
while kde based distros like mandriva and mepis seem smooth and near error free, kde in ubuntu seems shaky and unstable.
this is my personal experiences, I wont speak for everyone but I will speak on how my experiences were with it.
But I admit Kubuntu gutsy is top notch, it seems much better at managing itself then previous versions on my computer.

---

### Post by wolfen69 on 2008-01-16
> **SunnyRabbiera said:**
> 
while kde based distros like mandriva and mepis seem smooth and near error free, kde in ubuntu seems shaky and unstable.
this is my personal experiences, I wont speak for everyone but I will speak on how my experiences were with it.


i have to agree. but im not a Kde person to begin with, but my experience with kubuntu was very short lived. it had a very unstable feel to it. i couldve lived with it if i had to, but gnome runs near perfect for me, so i stick with what works. if i had to pick between mepis and mandriva i would choose mepis. if only because i know debian-based fairly well.

---

### Post by JaggedOne on 2008-01-16
To me it looks like a toss up between SUSE, Mepis and Debian+KDE. I know SUSE is rpm and very different from Ubuntu in terms of package management. How hard would it be to switch?

Mepis however I know nothing about. How close is its package management and use of repositories to ubuntu? Would I be able to use ubuntu specific guides with mepis?

---

### Post by p_quarles on 2008-01-17
> **JaggedOne said:**
> Mepis however I know nothing about. How close is its package management and use of repositories to ubuntu? Would I be able to use ubuntu specific guides with mepis?
Mepis is based on Ubuntu and uses APT. So, yes, package management will work the same.

---

### Post by SunnyRabbiera on 2008-01-17
> **JaggedOne said:**
> To me it looks like a toss up between SUSE, Mepis and Debian+KDE. I know SUSE is rpm and very different from Ubuntu in terms of package management. How hard would it be to switch?

Mepis however I know nothing about. How close is its package management and use of repositories to ubuntu? Would I be able to use ubuntu specific guides with mepis?

Mepis uses synaptic and apt, Mepis is based on debian and its package management is relatively the same.
there should not be much to learn really, Mepis is one of the easiest ones out there so learning it should be a no brainer.

> **p_quarles said:**
> Mepis is based on Ubuntu and uses APT. So, yes, package management will work the same.
not the mepis 7 series, its back to a debian base.

---

### Post by JaggedOne on 2008-01-17
> **SunnyRabbiera said:**
> Mepis uses synaptic and apt, Mepis is based on debian and its package management is relatively the same.
there should not be much to learn really, Mepis is one of the easiest ones out there so learning it should be a no brainer.


not the mepis 7 series, its back to a debian base.

Then should I go with mepis 7 or 6.5?

---

### Post by SunnyRabbiera on 2008-01-17
> **JaggedOne said:**
> Then should I go with mepis 7 or 6.5?

go with 7, really debian is a close cousin to ubuntu in fact it is what ubuntu was based on in the first place.
you cant go too wrong with it.
Really if you are so worried about walking away from something that runs like ubuntu you should not be thinking about Suse... its RPM based, it uses a entirely different packager.

---

### Post by JaggedOne on 2008-01-17
Two questions:

Should I go with Debian lenny or Etch?

When I try to boot the Mepis live cd I get to a text based interface asking me for a login name and user name. What do I do here? I tried everything obvious.

---

### Post by SunnyRabbiera on 2008-01-17
eh etch should do...
the mepis live CD has multiple loads on it, try each one and see if you can get to kdm.

what are your specs?
do you use amd?

---

### Post by kvonb on 2008-01-17
-

---

### Post by svasanth on 2008-01-17
u can try arch

---

### Post by SunnyRabbiera on 2008-01-17
arch is good, but our friend here seems intent on debian based stuff...
but I still suggest mandriva 2008 if mepis doesnt work, I think its great.

---

### Post by svasanth on 2008-01-17
> **SunnyRabbiera said:**
> arch is good, but our friend here seems intent on debian based stuff...
but I still suggest mandriva 2008 if mepis doesnt work, I think its great.

yes...mandriva is a good option...but arch + KDEMod makes it a good deal :)

---

### Post by r76 on 2008-01-17
> **JaggedOne said:**
> Two questions:

Should I go with Debian lenny or Etch?

When I try to boot the Mepis live cd I get to a text based interface asking me for a login name and user name. What do I do here? I tried everything obvious.

did you try typing "demo" for both?  that worked for me on Mepis 7

As above, if Mepis doesn't work out, try Mandriva 2008.  I know it's not Debian based but it is good.
I'm sure openSUSE is too, but I didn't understand the installer. Arch with kdemod is super fast, and the forums great help - the wiki explains the installation very well.

---

### Post by kvonb on 2008-01-17
-

---

### Post by SunnyRabbiera on 2008-01-17
oh trust me mandriva 2008 is eons better then its older counterparts.

---

### Post by mindtrick on 2008-01-17
Slackware is very stable
Debian is also very stable

Any Ubuntu based product will have same stability issues because of same binaries.

---

### Post by doorknob60 on 2008-01-18
I've used Mandriva and Kubuntu and Mandrive seems WAY more stable, but I haven't used it in a while and I know there were some things I didn't like about it but I was new to Linux then.

---

### Post by mips on 2008-01-18
> **kvonb said:**
> 
Now off to try *arch + KDEMod*, and maybe even *Mandrake* (hope it's better than 6, 7, and 8!).


For arch do an ftp install with the small 31MB iso. Archlinux-x86_64-2007.08-2.ftp is the 64bit version.

Why? Because safe yourself some download time because once you installed the base setup and you upgrade your system to current it's going to install another 100MB of the net anyway. With a ftp install you get the current stuff.

---

### Post by kvonb on 2008-01-18
-

---

### Post by mips on 2008-01-18
> **kvonb said:**
> Ah bugger, I just downloaded Archlinux-x86_64-2007.08-2.core.iso it's 166 megs.

Should I dump it and use the one you suggested?  Although, I would have to have my wireless working to download anything first!  Do you think Arch will enable my Broadcom 4312v2 with WAP2 by default?

No, don't dump it and waste another 31MB. The good thing is the core.iso also allows you to do a FTP install. 

I think wireless might be a biatch to try and get working and install over but should be possible, just load the required models and configure. I have never tried it but I suggest looking at the wiki and maybe ask #archlinux, #archlinux64 on IRC.

Can you not connect via a wired connection initially just to get you up and running.

---

### Post by kvonb on 2008-01-18
-

---

### Post by Linuxratty on 2008-01-18
I'm using mepis7 right now an d I do like it..Klikit is another good one,but it's still in beta.

---

### Post by Changturkey on 2008-01-18
> **Linuxratty said:**
> I'm using mepis7 right now an d I do like it..Klikit is another good one,but it's still in beta.

Hey Linuxratty!

---

### Post by wolfen69 on 2008-01-19
Looking for a good KDE centered ubuntu like distro.

no such thing.

just kidding.

not

---

### Post by Lord DarkPat on 2008-01-19
freespire is a good distro, but CNR is bunch of crap. I wish it wasn't spoiled by it's package management system. I love the OS, hate the package manager(seriously)
Mepis is OK, openSUSE is a nightmare, don't try it if you think Kubuntu is unstable.

---

### Post by Incense on 2008-01-19
I'm wondering why no one has reccomended SIDUX yet?

---

### Post by Incense on 2008-01-19
> **Lord DarkPat said:**
> freespire is a good distro, but CNR is bunch of crap. I wish it wasn't spoiled by it's package management system. I love the OS, hate the package manager(seriously)
Mepis is OK, openSUSE is a nightmare, don't try it if you think Kubuntu is unstable.

Isn't freespire based on Kubuntu? OpenSUSE is actually fantastic and very stable.

---

### Post by S3Indiana on 2008-01-19
> **Incense said:**
> [quote=Lord DarkPat;4165108]freespire is a good distro, but CNR is bunch of crap. I wish it wasn't spoiled by it's package management system. I love the OS, hate the package manager(seriously)
Isn't freespire based on Kubuntu?[/quote]Freespire 2.0 is Debian-based using ubuntu repositories (OS core is Debian, but the packages used are from ubuntu with some Freespire specific). Freespire is unique compared to Debian or ubuntu distributions.
For clarification [CNR.com]("http://www.cnr.com") and the CNR Client are Beta products, so you'd expect some issues (personally I've had success installing numerous packages with the CNR system)...

---

### Post by kvonb on 2008-01-20
-

---

### Post by samwyse on 2008-01-20
I'd like a distro with more stable KDE apps, but how can they be much different? Do distros do their own custom patching? :confused:

It's pretty much just the occasional Gwenview and Konqueror crash I get with Kubuntu.

---

### Post by SunnyRabbiera on 2008-01-20
> **samwyse said:**
> I'd like a distro with more stable KDE apps, but how can they be much different? Do distros do their own custom patching? :confused:

It's pretty much just the occasional Gwenview and Konqueror crash I get with Kubuntu.

some of them do, especially the ones that use KDE by default.
but I have noted that the kde patching in kubuntu isnt like that in others, it just seems to use a slightly modified one that is in the repo.

---

### Post by S3Indiana on 2008-01-20
> **kvonb said:**
> Every application you install is done through that horrid CNR thing, for which you have to register, and they then know exactly what you are installing.

Sorry, I don't subscribe to the "...users who installed this app, also installed this one too, click here to try it now" nonsense, I really don't care what other people are doing, I can think for myself thankyou very much!With [CNR.com]("http://www.cnr.com") there is no registration required to install the vast listing of open source applications (just required to make and access purchases of commercial products). CNR is designed for the mainstream that purchase pre-installed systems. Others might want to give CNR a valid evaluation...

P.S. visit any web site and they track your IP (even this one :)...

---

### Post by samwyse on 2008-01-22
I think might go back to Fedora after a couple of years of Kubuntu. Not that KDE is anything special in Fedora, but because I'd like a less hacked one.

---

### Post by VCSkier on 2008-01-23
@ samwyse

You should consider reading aysiu's article on a ["A faster KDE."]("http://www.psychocats.net/ubuntu/kde-core")  He details some steps for cleaning up Kubuntu a bit, and making it  more KDE-like and less Kubuntu-like.  It's valuable information until Canonical kicks up the development of Kubuntu up a notch (hopefully by 8.04).

---

### Post by dasunst3r on 2008-01-23
Try openSUSE -- they seem to have one of the most polished KDE distros around.  However, I gave 10.3 a shot not long ago, and I was disappointed because of the quirks I had to deal with, like not being able to automount my external disks, having to ask me for credentials over and over again when connecting to my University's network (uses 802.1x authentication), etc.

---

### Post by samwyse on 2008-01-23
> **dasunst3r said:**
> Try openSUSE -- they seem to have one of the most polished KDE distros around.  However, I gave 10.3 a shot not long ago, and I was disappointed because of the quirks I had to deal with, like not being able to automount my external disks, having to ask me for credentials over and over again when connecting to my University's network (uses 802.1x authentication), etc.

It does [something](https://bugzilla.novell.com/show_bug.cgi?id=341142) [odd](https://bugzilla.novell.com/attachment.cgi?id=183073) when using certain settings in Konqueror. You could say it's a minor thing, but I've never seen that happen in Kubuntu and I don't want to change to something worse. Also, I'm not sure I like the Yast Control Center.

---

### Post by samwyse on 2008-01-23
> **VCSkier said:**
> @ samwyse

You should consider reading aysiu's article on a ["A faster KDE."]("http://www.psychocats.net/ubuntu/kde-core")  He details some steps for cleaning up Kubuntu a bit, and making it  more KDE-like and less Kubuntu-like.  It's valuable information until Canonical kicks up the development of Kubuntu up a notch (hopefully by 8.04).

The thing that bugs me is making unfinished software like Dolphin default and [simpilifying Konqueror](https://launchpad.net/ubuntu/+source/kdebase/+bug/43949) the wrong way. I also hope there's a bit more stable packages in another distro. Also the Kmenu is a mess and there's too many apps installed by default, probably because of the packaging. Fedora still seems to package KDE in a "non optimal" way, for example there's just one big kdegames package. In Kubuntu (Debian) you can choose which games you want.

---

