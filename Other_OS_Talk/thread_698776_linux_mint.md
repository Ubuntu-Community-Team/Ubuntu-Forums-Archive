---
title: "linux mint?"
date: 2008-02-16
forum: Other OS Talk
---

### Post by Cew27 on 2008-02-16
hello everyone during my search for the best distro i have come across linux mint, i have a few questions about this distro as it looks impressive 
1. does it have the same repositories as ubuntu? 
2. what is the difference between ubuntu and mint?
3. why does ubuntu let me use my wireless card and mint doesn't?
also can i hear some opinions of linux mint good points and bad points 
that's about it, thanks

---

### Post by jan quark on 2008-02-16
> 1. does it have the same repositories as ubuntu? 

the newest mint daryna is based in gutsy gibbon 7.10 so yes it uses the repositories
> 2. what is the difference between ubuntu and mint?

mint comes with all the restricted codecs pre-installed, so flash and mp3 are supported out of the box.

the multimedia support is better ( but everything what mint can do, ubuntu can too)

> 3. why does ubuntu let me use my wireless card and mint doesn't?

more info needed to solve this issue. I had no problems or the same problems with mint and wireless as with ubuntu and wireless
please specify your issue

---

### Post by Cew27 on 2008-02-16
it could just be me its no big problem 
so mint is just a prettier ubuntu basically? 
another reason why ubuntu should step up their looks!

---

### Post by Cew27 on 2008-02-16
i presume it will be similar to ubuntu to set up

---

### Post by iamhugeinjapan on 2008-02-16
Linux MInt will not detect my wireless card with the live cd. But when it has been installed it all works fine. *shrug*. Ubuntu live cds have no problems.

Linux Mint has an Ubuntu backend but it has been heavily customised, now much more than early versions. DIfferent apps, codecs, specialised config apps etc.  I do like it for an out of the box experience.

---

### Post by Midwest-Linux on 2008-02-16
I don't use wireless with Linux Mint 4.0, but let me add to this by saying its the best Linux distro out there (in my opinion). I'm sure you can get the wireless problem fixed easily enough...with some help from the fine members of this forum.

---

### Post by wolfen69 on 2008-02-16
i like mint and ubuntu. they both work great for me. mint just requires a little less work to set up.

---

### Post by chris4585 on 2008-02-16
> **Cew27 said:**
> hello everyone during my search for the best distro i have come across linux mint, i have a few questions about this distro as it looks impressive 
1. does it have the same repositories as ubuntu? 
2. what is the difference between ubuntu and mint?
3. why does ubuntu let me use my wireless card and mint doesn't?
also can i hear some opinions of linux mint good points and bad points 
that's about it, thanks

1 linux mint is based off ubuntu, so yes it has the ubuntu repositories, and some more added
2 mint is completely out of the box, able to watch youtube, vista cant even watch youtube videos out of the box, ubuntu cant either out of the box
3 no clue, i dont have wireless internet

mint is great, and ubuntu is great, mint is completely out of the box by my opinion, multi media wise, i like xfce mint

---

### Post by sandysandy on 2008-02-16
> **Cew27 said:**
> i presume it will be similar to ubuntu to set up

hi

i converted Edubuntu 7.10 to Mint. This is the link to the thread.

[http://ubuntuforums.org/showthread.php?t=624064&page=3](http://ubuntuforums.org/showthread.php?t=624064&page=3)

regards

---

### Post by Cew27 on 2008-02-17
i love ubuntu and i am getting familiar with it but i hate the stock looks and from what i understand mint is just ubuntu but prettier and with an easier interface. 
im stuck as to what i want installed on my pc now.
i have a computer i just buit i will use it mainly for games on windows and java on linux.
i will use my laptop for internet browsing and music.
what should i have on which?
im guessing mint on the laptop and maybe mint on the pc, but i like the fact that ubuntu has a 6 month release cycle, i dont want to put mint on the pc and then hardy turns out to be fabulous and i then have to switch.

---

### Post by jrusso2 on 2008-02-17
a new version of Mint will follow after Hardy comes out they are just a bit behind.

---

### Post by Cew27 on 2008-02-17
yey! :D 
i think i will go to mint, i just dont want to stray away from ubuntu

---

### Post by Caraibes on 2008-02-17
I like the MintUpdate concept: The Mint Staff does a "test-drive" of the updates, to make sure they won't damage systems, and then let them out to the general public...

---

### Post by Cew27 on 2008-02-17
i think i will go to mint when i need to re-install there is no point changing now when i have all of the software and plugins mint does

---

### Post by r4ik on 2008-02-17
System-->Administration-->Software Sources

Check the repositories you think you will need (main, universe, restricted, multiverse). You probably won't need the 'sources' repository.

    * Add any third-party repositories. Such repositories are not monitored in any way. Some are quite popular, however. Use any third-party repository at your own risk. 

System-->Administration-->Software Sources-->Third-party software-->Add

Add the name of your repository. In this example, we will use Medibuntu, a popular third-party repository not affiliated with Ubuntu in any way.

APT line: deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

    * Download any needed gpg keys and add them to the keylist. This key verifies the repository to your system. The Medibuntu repository (not affiliated with Ubuntu) example is shown: 

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

Is all there is to it.

Sorry from,

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by tgalati4 on 2008-02-17
I think Linux Mint removed Gutsy's Network Manager because it was causing problems.  You can reinstall it through Synaptic.  Mint uses WICD instead and may not configure some cards correctly.    

As stated earlier, Mint rates updates on a scale of 1 to 5.  Ubuntu updates get a "3".  Kernel and xorg updates get a "1" or "2".  Mint themes and mint applications get a "4" or "5".  Basically, unless you change the default settings, users will never see kernel or xorg updates--because they tend to break things quickly.  Mint applications are rated lower-risk because they are heavily tested before being released and are considered low-risk for breakage.

I like the quick install (18 to 25 minutes versus 80 minutes for Foresight!).  The fact that a lot of stuff works out of the box means less questions in the forums.

---

### Post by skippi90 on 2008-02-17
I just installed Mint straight out of the box (well, CD) and it's absolutely great! Everything I need already installed, quick, and wireless is perfect. :-)

Best distro I have come across thus far.

---

### Post by Cew27 on 2008-02-17
i just read about a firefox advert issue this isnt a big problem but in my oppinion has let the distro down :(

---

### Post by exploder on 2008-02-18
The change in Firefox generates income that will be put back into the distribution. Income generated has always been used to improve things for everyone.

If this very small inconvenience will help the distribution, I support it.

---

### Post by SunnyRabbiera on 2008-02-19
really though its simple to ignore and get around

---

### Post by Cew27 on 2008-02-19
i spose 
i think mint should team up with conical (spelling?)

---

### Post by chris4585 on 2008-02-19
why would they do that? Canicals, and the mint team both want something completely different, i dont really seeing that happen anytime soon.

---

### Post by Changturkey on 2008-02-19
Linux Mint takes what Ubuntu and Debian has done and refines it so that the end user does not have to do very much out of the box, while still retaining the ability to customize the installation to their liking.

---

### Post by mikewhatever on 2008-02-20
> **Cew27 said:**
> it could just be me its no big problem 
so mint is just a prettier ubuntu basically? 
another reason why ubuntu should step up their looks!

Here we go, again! It's not like you get married to the default look after the installation. Ubuntu looks are customizable: System>Preferences>Appearance.

I am no expert in Mint, but it seems that the core philosophies of the two distributions are radically different. Mint's approach may be described as KISS (Keep It Simple Stupid). They try to provide out of the box functionality, hence the inclusion of a lot of proprietary software. You can read about Ubuntu's approach [HERE]("http://www.ubuntu.com/community/ubuntustory/philosophy"). It should be quite clear that the two head in different directions, so any teaming up is not possible.

---

### Post by kazuya on 2008-02-21
They are essentially the same thing with Mint providing the extra stuffs out of the box.

---

### Post by rfurman24 on 2008-02-23
I have used Feisty and Gutsy. It took numerous days to get Gutsy installed and I had to use the alternate cd on a new machine. Gutsy had tons of broken packages installed and alot of stuff that worked in Feisty no longer worked. After a few months of use Gutsy quit booting for me. Not wanting to go through the mes s I had to in the first place and not wanting to go back to Feisty I tried Mint. Everything worked. All the bugs and most of the non-working items in Gutsy were fixed. I do not care about looks as I will probably always change to my own themes preferences. Mint just seems way more polished to me.

---

### Post by Cew27 on 2008-02-24
i hope ubuntu can learn from mint

---

### Post by chris4585 on 2008-02-24
> **Cew27 said:**
> i hope ubuntu can learn from mint

eh... i think ubuntu, and mint are both fine the way they are today

what should ubuntu learn from mint? to include proprietary software into its release, so when anyone from certain countries download ubuntu it'll be illegal?
Mark Shuttleworth and Canonical make Ubuntu to have a choice for you to include those things, they want ubuntu to be free and not illegal.

If you want to be able to play any type of media there's one thing you have to do, download ubuntu-restricted-extras via synaptic, and you wont have problems playing any type of media, although it may be illegal in your country

I dont want to argue i just want you to understand Ubuntu a bit more, but why should ubuntu learn from mint? so we have two distros the same?

---

### Post by Cew27 on 2008-02-24
the bug fixes the mint has introduces along with the realisation that looks do matter

---

### Post by mikewhatever on 2008-02-25
> **Cew27 said:**
> the bug fixes the mint has introduces along with the realisation that looks do matter

For your info, Ubuntu has launchpad.net for bug reports. Has Mint introduced something radically new? I've looked around their home site, but could not find anything, other that they seem to fail acknowledging their origin. It's simply not mentioned anywhere they are Ubuntu based.

As for the looks, some people are so entrenched in their opinions, there is no point arguing, and you seem to be one of them, yet, for the sake of whoever may read this:
1. Ubuntu's default brown is great. It's innovative, refreshing, and, most importantly, customizable.
2. Ubuntu has eight themes preinstalled, and gnome-look.org has about a hundred more.
3. No default theme will ever satisfy everyone, what's the point of changing it?

---

### Post by Cew27 on 2008-02-25
yo attract new users, most people i showed stock ubuntu said it looks horrible, i however acknowledge the fact that i can change the looks but its aways nice to have it looking good to start

---

### Post by chris4585 on 2008-02-25
i like ubuntu's default theme, if you dont you can change it, when i get a new system going no matter what i always change the look, even mint i dont care for its look a whole bunch, i like sabayon's look but sadly i dont like sabayon, i like vista's look but vista is horrible in my opinion, maybe ubuntu's default isnt the best, but at least it has what counts, the ability to cusomize it and a good system

---

### Post by r4ik on 2008-02-25
> **chris4585 said:**
> i like ubuntu's default theme, if you dont you can change it, when i get a new system going no matter what i always change the look, even mint i dont care for its look a whole bunch, i like sabayon's look but sadly i dont like sabayon, i like vista's look but vista is horrible in my opinion, maybe ubuntu's default isnt the best, but at least it has what counts, the ability to cusomize it and a good system

If you want a Vista look see,

[http://vixta.sourceforge.net/](http://vixta.sourceforge.net/)

---

### Post by chris4585 on 2008-02-25
erm no i dont want vista, (i was simply saying it looks great and i said it was horrible as a system) vista was the reason i switched mostly, then it led to other things now i love exploring and learning linux

EDIT i just looked at the link and no i dislike vixta, it was horribly slow on my computer for some reason..... isnt it based on fedora? i dont care for rpm systems, correct me if i'm wrong

besides i can make my system look just like vista, not hard <3 gnome-look.org, i may give vixta another try in a vm, just to play with it again, i havent tried vixta 3D

---

### Post by aysiu on 2008-02-25
> **mikewhatever said:**
> For your info, Ubuntu has launchpad.net for bug reports. Has Mint introduced something radically new? I've looked around their home site, but could not find anything, other that they seem to fail acknowledging their origin. It's simply not mentioned anywhere they are Ubuntu based. Yes, it is.

From [the Linux Mint About page](http://linuxmint.com/about.php): > Linux Mint is one of the surprise packages of the past year. **Originally launched as a variant of Ubuntu with integrated media codecs**, it has now developed into one of the most user-friendly distributions on the market - complete with a custom desktop and menus, several unique configuration tools, a web-based package installation interface, and a number of different editions. Perhaps most importantly, this is one project where the developers and users are in constant interaction, resulting in dramatic, user-driven improvements with every new release. DistroWatch has spoken to the founder and lead developer of Linux Mint, Clement Lefebvre, about the history of the distribution.

Some of the reasons for the success of Linux Mint are: [list][*] It's one of the most community driven distributions. You could literally post an idea in the forums today and see it implemented the week after in the "current" release. Of course this has pros and cons and compared to distributions with roadmaps, feature boards and fixed release cycles we miss a lot of structure and potentially a lot of quality, but it allows us to react quickly, implement more innovations and make the whole experience for us and for the users extremely exciting.
    [*] **It is a Debian-based distribution** and as such it is very solid and it comes with one of the greatest package managers.
    [*] **It is compatible with and uses Ubuntu repositories.** This gives Linux Mint users access to a huge collection of packages and software.
    [*] It comes with a lot of desktop improvements which make it easier for the user to do common things.
    [*] There is a strong focus on making things work out of the box (WiFi cards drivers in the file system, multimedia support, screen resolution, etc).[/list]


---

### Post by mikewhatever on 2008-02-25
I've actually read that, but here's what it tells me:

> Originally launched as a variant of Ubuntu with integrated media codecs

It started as Ubuntu based, so we are sure about the first eddition. What happened next? Is the second edition still based on Ubuntu or is it based on something else? What about the latest edition?

> It is a Debian-based distribution

Ah, so now it is Debian based, no longer Ubuntu based? Have they started with Ubuntu and later switched to Debian? When did they make the switch?

> It is compatible with and uses Ubuntu repositories.

In view of the above, is it because LinuxMint was originally Ubuntu based? Had they switched to Debian but remained compatible with Ubuntu repositories?

Perhaps my English is not good enough, but I simply can't see the acknowledgment in the quoted lines. It's not even clear whether or not their current version is based on Ubuntu or on Debian.

---

### Post by chris4585 on 2008-02-25
i'm sure its ubuntu based, since now there is a debian version, which isnt much different from the main edition, why would they have a debian editiion as a secondary, if its based on debian? i dont think it is, it would make more sense if it was ubuntu based, and they had a debian edition, just my thoughts

---

### Post by mikewhatever on 2008-02-25
> **chris4585 said:**
> i'm sure its ubuntu based, since now there is a debian version, which isnt much different from the main edition, why would they have a debian editiion as a secondary, if its based on debian? i dont think it is, it would make more sense if it was ubuntu based, and they had a debian edition, just my thoughts

Well, I also thought along these lines, but I am not sure any more. Couldn't they have two Debian based versions? I mean, Debian itself has several versions, as well as Ubuntu, so why not Mint? It would be great if someone could provide a link clearly stating that Darina is a modified version of Ubuntu 7.10 or something similar. Of cause, it's perfectly fine if they are no longer Ubuntu based too.

---

### Post by skubisnack on 2008-02-25
I've been using Mint for a couple months.  It started as an experiment and I stuck with it.  I barely ever go to their forums because they are difficult to search and there's just not that much information there.  Any issues or questions I have I get answered here.  So in that respect, I'd have to say that Mint is Ubuntu-based.  All the fixes and tweaks that work for Ubuntu work for Mint (at least in my experience).

That being said, I'm thinking about going back to Ubuntu because I'm pretty sure I've tweaked Mint down to Ubuntu anyway.  I'd like to get a fresh install and clean up my system (lots of installs, as well as trying different desktop environments).  

So if it tells you anything, I've been using Mint for awhile and I'm searching the forums for the differences between the two...

---

### Post by Caraibes on 2008-02-26
I use Mint right now (4.0). It is based on Ubuntu 7.10. That's a fact, and it's good, as it is a great base. I would say that Mint is 96% Ubuntu... That suits me fine :)

---

### Post by Zero Prime on 2008-02-27
I'm using Mint as well.  I surprised at how fast it is.

---

### Post by mikewhatever on 2008-02-27
Well, the consensus seems to be that Darina, or whatever version you use, is Ubuntu based, yet nobody has been able to provide a word of credit, apart from the vague notion that Mint started as Ubuntu based, quoted by aysui. It's been nice to hear how fast and customizable your Mint systems are, but let me repeat the question again. **Why wouldn't Mint community acknowledge the origin?** I've browsed their site several times, but found nothing even remotely similar to [Ubuntu and Debian]("http://www.ubuntu.com/community/ubuntustory/debian"). Are they ashamed? :confused:
If anyone has a link to the acknowledgment page, feel free to post it here.

---

### Post by Zero Prime on 2008-02-28
They are Ubuntu based.  If you browse a little more you will see that they acknowledge this a lot.  Such as when they release an updated distro.  Their newest one will be based on Hardy.  They even say that the next release will be out shortly after Hardy.

---

### Post by j_dog on 2008-03-01
Is there no 64 bit mint ?  Putting the pre-installed codecs aside, what would be a better choice ? Mint or 64 bit Ubuntu ?              :-k

---

### Post by Zero Prime on 2008-03-01
It's really up to your preferences.  For me LM runs faster that7.10.  I don't know why but it does.  Speed is a big factor for me.

---

### Post by Cew27 on 2008-03-02
yes but wouldnt 64bit run faster than a 32 bit os

---

### Post by Caraibes on 2008-03-02
> **Cew27 said:**
> yes but wouldnt 64bit run faster than a 32 bit os
I don't think it would make any noticeable difference...
The good thing about running a 32bit distro is that most things are compatible... That is not always the case in a 64 bit distro...

---

### Post by Cew27 on 2008-03-02
well then whats the point in 64 bit ?!

---

### Post by skitch on 2008-03-02
ok guys heres my issue
i'm an absolute noob to linnex in every way shape or form but i would like very much to git comfortable in it
right now i'm restricted to a lap top with really horrible wireless internet (the best we can git in iraq atm)
unfortunatly the copy of kubuntu that i downloaded(took me 2 days) dosn't do any thing for my wireless card (i found some instructions that r supposed to make it work but as of yet i am still very unfamilur with it
so my question is is there a distro of linnex that will have my wireless card (an althereo's ar5007eg ) working out of the box and if so where can i download it
thanks for any and all help

---

### Post by wolfen69 on 2008-03-02
> i'm an absolute noob to **_linnex_** in every way shape or form
**LINUX** not linnex.

---

### Post by Cew27 on 2008-03-02
also your out of luck with that wireless card, i had to buy a new one to get wireless on my ubuntu

---

### Post by khensucat on 2008-03-05
> **mikewhatever said:**
> Well, the consensus seems to be that Darina, or whatever version you use, is Ubuntu based, yet nobody has been able to provide a word of credit, apart from the vague notion that Mint started as Ubuntu based, quoted by aysui. It's been nice to hear how fast and customizable your Mint systems are, but let me repeat the question again. **Why wouldn't Mint community acknowledge the origin?** I've browsed their site several times, but found nothing even remotely similar to [Ubuntu and Debian]("http://www.ubuntu.com/community/ubuntustory/debian"). Are they ashamed? :confused:
If anyone has a link to the acknowledgment page, feel free to post it here.

[http://distrowatch.com/table.php?distribution=mint](http://distrowatch.com/table.php?distribution=mint)

Linux Mint is an Ubuntu-based distribution...

[http://www.linuxmint.com/about.php](http://www.linuxmint.com/about.php)

Originally launched as a variant of Ubuntu... ...and uses Ubuntu repositories.

---

### Post by mikewhatever on 2008-03-05
> **khensucat said:**
> [http://distrowatch.com/table.php?distribution=mint](http://distrowatch.com/table.php?distribution=mint)

Linux Mint is an Ubuntu-based distribution...

Yes, I saw that on Distrowatch. Are you trying to market it as Mint community's official recognition? If so, it hardly qualifies.

> [http://www.linuxmint.com/about.php](http://www.linuxmint.com/about.php)

Originally launched as a variant of Ubuntu... ...and uses Ubuntu repositories.

That's already been discussed earlier in this thread. Check posts #35, #36.

---

### Post by Zero Prime on 2008-03-05
Here's an idea.  I don't know what the big deal is with whether or not they are Ubuntu based, but why not log onto their forums and ask them.

---

### Post by exploder on 2008-03-05
The best way to explain things is that Mint is not built from the latest Ubuntu build, Packages are updated as the developer sees fit. An example of this is the print system in Daryna is not the same as the one in Gutsy.

LinuxMint does use Ubuntu repositories.As Mint grows as a distribution more packages will probably come from the Mint repositories.

Weather you are looking at Mint or Ubuntu, they are actually Debian based.

---

### Post by wvn on 2008-03-06
To all the Distro Hoppers...

Is it fast enough...? Is it slow...? Does it look better...? Is it the same Distro or not...?

For :) sake we all come from a Win background that caused us a world of problems. Most of the people out there started with pre-configured PC's made by Major corporations that never gave u an option choosing a OS. Instead every single person that ever owned a PC had to eat the M$ overpriced pill. And you thing that that worked out of the box?

I always had to built my boxes from scratch and i always faced issues with drivers and codecs in M$ OS, no matter if it was 95, 98, 2000, xp, Vi$ta or whatever. If u need totally out-of-box experience get yourself a Dell Ubuntu Box, or just dont be lazy and configure the damned thing. Oh.... i forgot that we are hooked on pre-configured solutions that manage to control more than 90% of system users worldwide.

Linux Mint or Ubuntu = any. I am just glad that people have a choice. Yes, we need to work with many distros until we settle but hey, thats part of the game. Whatever is the case, my skills in computing came to be only by using distros. And i am damn proud for that.

BTW Ubuntu's awesome.

---

### Post by uberlube on 2008-03-06
Mint is based on both debian and ubuntu. They say that it is still very different from both, but they took the best of both and made a whole new distro. As for your wireless, just install the drivers yourself no biggie. Mint comes with a ndiswrapper GUI even to help you out.

---

### Post by j_dog on 2008-03-06
I am using Mint. Everything works. I dont see any difference from ubuntu other than cosmetic. A couple of pre-installed codecs is really no big deal.
 To say to somone that you use "UBUNTU"  does sound a lot cooler than saying "LINUX MINT" though. I will probably stay with it until Hardy is released.

---

### Post by Zero Prime on 2008-03-08
I can think of 2 really big differences from LinuxMint and Ubuntu.  Ubuntu 7.10 took about 45 seconds to get from power up to the GDM and then about a minute to get to a working desktop.  LinuxMint only takes 15 seconds for me to get to GDM and then another 15 to get to a working desktop.  That's with the same system, both running Compiz-Fuzion and AWN.

Speed is very important to me in choosing a distro.  I switched from Windows because of long boot times (even after fresh installs).

---

### Post by uberlube on 2008-03-08
I <3 mint! :lolflag:

---

### Post by j_dog on 2008-03-08
yes........Mint is a bit faster to boot !

---

### Post by CaptainCabinet on 2008-03-08
> **uberlube said:**
> I <3 mint! :lolflag:

Me too! :D

---

### Post by MattBD on 2008-03-08
I have Mint on a USB flash drive so I can take it with me anywhere. It's great for that because it has the multimedia codecs and so on already installed, along with Compiz-Fusion so it's good for impressing people.

---

### Post by khensucat on 2008-03-09
> **mikewhatever said:**
> Yes, I saw that on Distrowatch. Are you trying to market it as Mint community's official recognition?

*I'm* not trying to market it as anything. I use Ubuntu Hardy. I just found it easily enough, and it's common knowledge besides. 

[quote="mikewhatever"]If so, it hardly qualifies.[/QUOTE]

In your opinion.

---

