---
title: "Decision between sidux and arch - your thoughts"
date: 2008-03-20
forum: Other OS Talk
---

### Post by n1kol@! on 2008-03-20
hi there
i have spent a considerable amount of time reading about other linux distros, because my ubuntu partition wants a friend to talk to and i want to try out something new. i have come to the conclusion that the lucky distro to make it onto my harddrive will either be arch linux or sidux. my reasons for this choice are as follows:

-rolling release: i want a rolling release distro that is always up to date and so that i never have to reinstall

-speed: i have read that both arch and siux are blazingly fast

-bleeding edge, but still somewhat stable:both distros are quite 
bleeding edge, but i have read that they are both still quite stable

a bonus point for sidux is that it has many 'killer' scripts and very good hardware recognition. on the other hand, after looking at the debian sid and arch repos it looks like arch has newer packages (these are in the aur, though, which means i could just as well compile them in sidux, and sidux has MANY more packages, which are all precompiled.). arch is also i686 optimized, which sounds to me like arch is faster than sidux. does this make a big difference?

what are your thoughts? please also don't just tell me which is better, instead give me a reason why you prefer one of them over the other. please also list more advantages of each, so that i get a broadre perspective, so that i can make up my mind.

thanks a lot!:):)

PS:how is the wireless support on sidux/arch? i read that sidux has a gui control center that lets you set up wireless. 
PPS:how is 64 bit support for these distros? if they work nicely in 64 bit then i will download the 64 bit version of the distro that i am going to choose.
PPPS:is sabayon any good? it has slipped up quite high in distrowatch recently and it supports binary packages. has anyone tried it?

---

### Post by notwen on 2008-03-20
Are you wanting a pre-determined gui? sidux generally uses kde(other wm available) while arch you can pick your de.  are you comfortable adding/removing/updating existing packages through CLI, arch's package manager pac man is strictly CLI,  if you're familiar w/ apt-get then you'll be comfy using it to add/remove/upgrade packages in sidux. 

I would recommend Arch if you're wanting to learn more about the OS and sidux if you're just wanting to try something new.  I've used both, neither for extended amounts of time, I ran sidux for a bout a month, but fell back to Debian Etch.  Arch is more of a customized distro, being you will actually build it to your needs.  Good luck on whichever you decide on.  =]

---

### Post by n1kol@! on 2008-03-20
> Are you wanting a pre-determined gui? sidux generally uses kde(other wm available) while arch you can pick your de. are you comfortable adding/removing/updating existing packages through CLI, arch's package manager pac man is strictly CLI, if you're familiar w/ apt-get then you'll be comfy using it to add/remove/upgrade packages in sidux.

i don't mind using the CLI, as long as it is efficient (meaning just as fast or faster to use than a gui app, which i presime it is.).

> Good luck on whichever you decide on. =]

thanks!:):):)

---

### Post by RAV TUX on 2008-03-20
Sidux & Arch are both good try them both.

Skip Sabayon.

---

### Post by 67GTA on 2008-03-20
Sidux is supposed to be i686 also. I have used Sidux. It is a good, fast distro. You will break something if you use apt-get update/upgrade the way you would in Ubuntu/Debian. The way they keep it so stable *and* bleeding edge is to choose updates wisely from Debian unstable/testing. They have a special script for updating/upgrading the system. I'm with RAV TUX on Sabayon. It is cool as a live CD, but it is basically a modified version of Gentoo. I wouldn't want to install it as an everyday OS. I have not tried Arch because I'm lazy. I just can't talk myself into putting a distro together, but a lot of people on the forums talk highly of it.

---

### Post by mips on 2008-03-20
I find Arch sipler with it's KISS approach and I have tried Sidux before. Nothing wrong with Sidux though.

---

### Post by Rumor on 2008-03-21
I've used both. The only one that I continued with is Arch. Pacman is, IMO, more versatile than apt-get, especially so when you couple it with the Arch build System (ABS). 

Sidux made too many choices for me on install, Arch lets me make those choices, so I feel like the system is more what I have made it to be.

Arch has very good 64 bit support.

---

### Post by n1kol@! on 2008-03-21
if there are any other distrobutions you have tried out and liked, recommend them to me. my specs for a perfect distro are:

-rolling release
-large + up to date repos (i know arch doesn't really meet this spec, if i end up using arch, can anyone recommend any 3rd-party repos, preferably 64-bit?)

if ubuntu was a rolling release distro it would be perfect, and it has THIS community. if opensuse's package management was sorted and it was rolling release, i would love it. i know that pclinuxos is rolling release, but i heard that the repos are quite outdated. any comments on this?

PS:if anyone can convince me as to why a sheduled release (as opposed to a rolling release) i might consider changing my specs

---

### Post by 67GTA on 2008-03-21
PCLinuxOS repos are not really outdated. They just don't put the latest versions into the repos every time something is updated. This is one of the reasons for their stability. Ubuntu often has a lot of minor bugs because of using the Debian testing repos. You can look at the PCLinuxOS repo and decide for yourself. [http://pclosusers.com/pclosusers/pclosfiles/](http://pclosusers.com/pclosusers/pclosfiles/) They now have a Gnome version if you don't like KDE. They have testing repos you can use if you want the latest versions. You can compare the app versions in the link I posted. If you want to build a distro from the command line try Arch, If you want to install and go without much config then PCLinuxOS is the only other distro I would recommend for daily use.

---

### Post by 67GTA on 2008-03-21
I was just quickly comparing repos from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) gutsy and [http://pclosusers.com/pclosusers/pclosfiles/](http://pclosusers.com/pclosusers/pclosfiles/) main. A lot of PCLinuxOS's apps are newer than Gutsy's. Cups has an older version in the PCLinuxOS repos. It is all relative to what you want.

---

### Post by n1kol@! on 2008-03-21
thanks for the quick reply. i have heard many good things about pclos. are there any drawbacks? the pclos control center is said to be very good. how is 64-bit support. should i even bother about 64-bit atm? it looks like there are many more packages for 32-bit. atm i see the arch repo as a major drawback for arch, because there are so few packages. kdemod looks interesting though, but again, kdemod4 packages are only available for 32-bit at the moment. please keep the advice coming.

PS: why is pclos starting to fall so far behind ubuntu on distrowatch atm? if you look at recent data spans, they are losing places quite quickly.

---

### Post by 67GTA on 2008-03-21
There aren't really any drawbacks to PCLinuxOS. Since it is a rolling release, when you install it, it will have about 400-500MB of updates to install. It doesn't have an automatic updater. You just use apt-get or synaptic to update when you want. The repos are a little smaller than Ubuntu repos. I haven't seen any packages I actually use that aren't there. Most of the Debian/Ubuntu repo girth is made up of outdated apps that most modern users never install anyway. If you took out all of the old command line apps, and the crappy ncursers apps that have better replacements, then the repos are about the same size. All the important stuff is there. You can use alien to convert .deb files to .rpm if there is some must have app. They use the Mandriva control center(pclinuxos is based off mandriva). It is similar to Yast in opensuse. I can't say anything bad about it. I wouldn't pay any attention to the distrowatch rankings. They simply measure the (hits per day) when someone visits distrowatch and then clicks through to the distro's homepage. It does not show any parallel to the quality or number of users each particular distro has. If you will watch when new or development versions come out, those distros will always climb towards the top. After a couple of weeks and the buzz dies down, and everyone stops blogging about the new releases, they will slip back down. Don't base which distro you use on distrowatch rankings.

---

### Post by 67GTA on 2008-03-21
I have a 64bit Desktop, but have never bothered with installing a 64bit OS. I have not seen any evidence so far that suggests any major speed difference. The difference would be hard to notice. Once more apps are built for 64bit machines, I will give it a try. There are posts on every major distro's forums about how to get certain 64bit apps to work, or make 32bit apps work on a 64bit OS. 64bit technology has not come full circle yet. Microsoft has not even fully implemented it in their OS. I wouldn't bother with it yet.

---

### Post by n1kol@! on 2008-03-21
i have decided that i do not need 64-bit. the only advantages are that you can have more than 4gb of (who needs more than that?) and that there are optimisations for multimedia things like video encoding, but the speed difference is minor. i will give pclos a shot sometime soon. from what i've read it sounds nicer than ubuntu, but i'll have to test it for myself to find out. i might go for a arch + pclos dualboot to try both and then settle for one of them. sidux does not really sound that appealing. some of its packages are older than the ubuntu ones. the only adavantage i can see in it are the hardware detection scripts and modules it inherited from kanotix, but most distros' hardware detection is good nowadays. i am still thinking whether i should try arch. it looks like its quite bleeding edge, which i like and it has pacman, which is said to be better than apt. arch does not have a control center or gui configuration apps like pclos, so system maintenance might be more complicated, but it does not really matter that much. my only other main concern for arch is the amount of packages. i think the dualboot idea is not too bad.

---

### Post by 67GTA on 2008-03-21
I have the PCLinuxOS Gnome version installed on Virtualbox in Opensuse. It is better to me than the KDE version, even though I'm a KDE man. There free, so if you have the bandwidth to spare, just download them both and give the live CD's a spin. PCLinuxOS does things a little different than Ubuntu. If you install the KDE version, and then install Gnome, or vice versa, you won't get the same experience. They completely redone the base for the Gnome version.

---

### Post by n1kol@! on 2008-03-22
ok. thanks to all the helpful input i have come to a decision: i will settle for arch, and i might download pclos to try it out as a livecd. 

the reasons why i will settle for arch are as follows:

-more bleeding edge, but apparently very stable
-i like the KISS approach
-by using arch i will learn more about how the OS works
-kdemod and kdemod4, they are wonderful
-arxin, an arch systemsettings app to configure your whole system, it can be integrated into kdemod4 systemsettings as a tab
-shaman, a gui package manager. from what i've seen it looks more advanced than synaptic and it's wriiten for qt4
-pacman. it sounds wonderful
-speed: because i only install what i need. kdemod is also faster than kde, because not all packages are installed, only the ones i need

thanks for all the helpful advice, and special thanks :KS to 67GTA, who gave me very helpful answers very quickly.:guitar:

cheerz.:):)

PS: i will only use 64-bit in a few months or years, whenever all apps are ported and it works just as well as 32-bit. i also don't see a need for more than 4gb ram, and i don't do a lot of video encoding, so i won't see any improvements.

PPS: although i might not use ubuntu a lot in future, i will definitively keep reading and posting on these forums, they are absolutely wonderful.:):)

---

### Post by 67GTA on 2008-03-22
Have fun! You can come back and post in the Arch section. You know you can't stay away...

---

### Post by pieisgood4589 on 2008-03-22
Heh, I'd go with Linux Mint, but that's based off of Ubuntu...

---

### Post by n1kol@! on 2008-03-22
> Have fun! You can come back and post in the Arch section. You know you can't stay away...

true...arch's forum doesn't look too bad, but it is not as active as ubuntu's. i think i have been spoiled by ubuntu and it's forums.:)
can arch users please share some good 3rd party repos? currently i know of:

[http://pkg.markconstable.com/kde/](http://pkg.markconstable.com/kde/) - kde4
[http://pkg.markconstable.com/gui](http://pkg.markconstable.com/gui) - arxin + shaman
[http://kdemod.ath.cx/repo/testing/](http://kdemod.ath.cx/repo/testing/) - kdemod4
[http://repo.archlinux.fr/](http://repo.archlinux.fr/) - is this one good + uptodate? it looks like it's french, so are the packages also french? should i use it?

thanks again for all the help:):):)

*edit*if someone knows a repo that has 64-bit flash player and all the other stuff that's only available for 32-bit on the arch repo, then i'll use arch64, so that i won't have to reinstall in future:)

---

### Post by 67GTA on 2008-03-22
> **n1kol@! said:**
> true...arch's forum doesn't look too bad, but it is not as active as ubuntu's. i think i have been spoiled by ubuntu and it's forums.:)
can arch users please share some good 3rd party repos? currently i know of:

[http://pkg.markconstable.com/kde/](http://pkg.markconstable.com/kde/) - kde4
[http://pkg.markconstable.com/gui](http://pkg.markconstable.com/gui) - arxin + shaman
[http://kdemod.ath.cx/repo/testing/](http://kdemod.ath.cx/repo/testing/) - kdemod4
[http://repo.archlinux.fr/](http://repo.archlinux.fr/) - is this one good + uptodate? it looks like it's french, so are the packages also french? should i use it?

thanks again for all the help:):):)

*edit*if someone knows a repo that has 64-bit flash player and all the other stuff that's only available for 32-bit on the arch repo, then i'll use arch64, so that i won't have to reinstall in future:)

Post this in the Arch sub forum, and one of the Arch heads will probably know.

---

### Post by dptxp on 2008-03-22
Never tried Arch, but sidux seems good to me, There is bunch of dedicated developers there and they have not taken the easy way. They strongly encourage 64-bit (In Debian there is not much differences in no of packages, and if you going for latest then 64-bit is a better option.

I use 64-bit in Ubuntu. It is said 64-bit has less problems than 32 bit.

---

### Post by greymongrey on 2008-03-22
I think you'll enjoy Arch. If I ever get the time and also get up the nerve I would like to try it. In the meantime I use sidux, and it rocks.I also use PCLinuxOS and it's a solid system but kind of dull.

---

### Post by mips on 2008-03-22
> **n1kol@! said:**
> true...arch's forum doesn't look too bad, but it is not as active as ubuntu's. i think i have been spoiled by ubuntu and it's forums.:)
can arch users please share some good 3rd party repos? currently i know of:

[http://pkg.markconstable.com/kde/](http://pkg.markconstable.com/kde/) - kde4
[http://pkg.markconstable.com/gui](http://pkg.markconstable.com/gui) - arxin + shaman
[http://kdemod.ath.cx/repo/testing/](http://kdemod.ath.cx/repo/testing/) - kdemod4
[http://repo.archlinux.fr/](http://repo.archlinux.fr/) - is this one good + uptodate? it looks like it's french, so are the packages also french? should i use it?

thanks again for all the help:):):)

*edit*if someone knows a repo that has 64-bit flash player and all the other stuff that's only available for 32-bit on the arch repo, then i'll use arch64, so that i won't have to reinstall in future:)

Have a look at kdemod4.

---

### Post by n1kol@! on 2008-03-23
i might also try opensuse, because it offers constantly updated software from the build service and 64-bit support is very good. i also like that it has a central place to configure the whole system. will arxin for arch offer similar capabilities? i hope package management will improve in opensuse 11, as it just plain sucks (what is the point of downloading the latest package database every time the package manager is opened?) to me pacman and the gui package manager shaman sound excellent. why do ubuntu and opensuse offer 64-bit flash, but arch doesn't? and also wine, virtualbox, some codecs + some other stuff that i can't remember are not available for 64-bit. it looks like arch has to few package maintainers to keep up with all the work. some 64-bit packages are newer than the 32-bit ones, and vice-versa. to me arch sounds like a perfect distro except for the fact that 64-bit support is not that great (and i don't want multilibs and a fake chroot environment. i guess i'll go for 32-bit then.) and that there are not that many packages and that some are uptodate and some not.

---

### Post by 67GTA on 2008-03-23
I use Opensuse 10.3 for my everyday OS. You can get the latest stuff from the build service repos. You can open Yast and go to SOFTWARE REPOSITORIES, click on each repo, and uncheck the auto refresh box. Then you can run ```
sudo zypper refresh
``` when you want to update the repos. Opensuse 11 will still use Yast as the package manager, but it is supposed to be faster.

---

