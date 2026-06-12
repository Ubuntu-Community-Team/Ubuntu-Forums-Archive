---
title: "How does emerge differ from apt??"
date: 2007-10-27
forum: Other OS Talk
---

### Post by kevdog on 2007-10-27
How does the emerge package management tool in sabayon/gentoo differ from the apt package management system in debian/ubuntu?  It seems like a lot of people either hate or have a lot of trouble with the emerge tool?  Just trying to figure out why this is -- newbies, didnt read documentation, it really is more of a pain, other??

---

### Post by aysiu on 2007-10-27
I've personally never used Sabayon or Gentoo, but as far as I know, Emerge differs from Apt in that it compiles all software from source. Apt tends to use precompiled binaries.

---

### Post by leg on 2007-10-27
Its a package management system that retrieves source code rather than binary files. Apts packages are binary files or files that already been compiled. Once you get the hang of it it is a fantastic tool. Most peoples problems come from the compilation stage as something is not set correctly or maybe conflicts with something else. Essentially you are manging the compilation of your programs with emerge where Apt installs the already compiled binary package.

---

### Post by DoorGunner on 2007-10-27
apt-get is a program that loads pre compiled progrs for you on  your system. It can work with rpms, debs etc. It is simple and proven. .deb files are the most popular and have the largest selection.

Merge on the the other hand downloads sourse code information and will compile it specifically for your system. This depends on the settings that you have set. It can take quite some time to compile depending on what you have for a system set up. I worked with gentoo for a while. I got tired of waiting for updates to compile. Sometimes up to an entire evening. 

I havent tried Sabayon to give an opinion. 

Some say that by compiling you have a faster machine. I have heard the opposite as well. In the end I really dont see that much of a difference to warrant the headache of waiting for comipiled programming. The benifit comes in learning your system down to the nuts and bolts. Gentoo really forces you to learn your system well.

---

### Post by SunnyRabbiera on 2007-10-27
personally I feel apt is better as really having emerge compile crap just takes too long.
Sabayon though is fair, I have used it off and on and it seems to be gentoo made easy... but emerge really cant take it, give me apt anyday.

---

### Post by mthei on 2007-10-27
Aside from what has been mentioned about the source vs binary thing, when uninstalling an application and all of its dependencies, APT will not remove those that are needed for other applications, and to the best of my knowledge (what I've read in the Gentoo manual over the summer), Emerge will not check if the depencies being removed with a certain application are still needed by others. For example, if you're running Gnome, have Amarok and Ktorrent install, and want to remove Ktorrent and all of its dependencies, including the KDE libraries, you can kiss your working Amarok goodbye.

---

### Post by kevdog on 2007-10-27
I really dont mind compiling from source code, it does take a long time however, but the tradeoff is that you get the latest updates.  I dont like what you guys have told me however about the uninstallation potential problems.  I could see that breaking a lot of packages real quick.  Seems like once you install something -- I would never uninstall for fear of package breakage.  I thought I read also that Sabayon (maybe Gentoo) used some system to keep track of various dependency compilations/installs so that if you wanted to install a second package that shared many same packages with a package already installed, it would not re-compile the shared dependencies.  I did a little reading emerge (just the basics).  I'm a little worried about compilation flags that might be needed.  Ive compiled on ubuntu before, and other than config options, Ive never had to use compilation flags.  Has anybody else found this to be a problem?

---

### Post by qamelian on 2007-10-27
Emerge doesn't require you to compile from source. If you want a quicker install (i.e., no long compilation process), you can tell emerge to download and install a precompiled package. I think the precompiled packages are referred to as ebuilds.

---

### Post by kevdog on 2007-10-27
Are ebuilds contained within the gentoo repository branch??

---

### Post by qamelian on 2007-10-27
> **kevdog said:**
> Are ebuilds contained within the gentoo repository branch??

Yes, they are, although I don't know for sure if there is a pre-compiled build for every package. It's been a while since I've used Gentoo and emerge.

---

### Post by leg on 2007-11-29
> **qamelian said:**
> Emerge doesn't require you to compile from source. If you want a quicker install (i.e., no long compilation process), you can tell emerge to download and install a precompiled package. I think the precompiled packages are referred to as ebuilds.ebuilds are usually the link to the source code but you are correct in stating that you can install binaries aswell. Not sure how many are contained and I think the main point is to create your own binaries for maintaining many systems. 
[QUOTE=mthei]APT will not remove those that are needed for other applications, and to the best of my knowledge (what I've read in the Gentoo manual over the summer), Emerge will not check if the depencies being removed with a certain application are still needed by others[/QUOTE]This is somewhat true, you may choose to uninstall dependancies or not, but is accounted for with a tool called revdep-rebuild which should be run after large or complicated updates to check that all dependencies are still in place.
[QUOTE=SunnyRabbiera]personally I feel apt is better as really having emerge compile crap just takes too long.
Sabayon though is fair, I have used it off and on and it seems to be gentoo made easy... but emerge really cant take it, give me apt anyday.[/QUOTE]I have to disagree and notice the speed difference of my Gentoo system over Ubuntu. My machine is older however and the difference may be less noticeable, if at all, on newer hardware. Also I could choose to further optimise by altering my compilation flags where some one else has chosen the optimisation level of a binary build. Compiling does take a long time and things will go wrong until you have got used to the system. I generally spend about half an hour a week updating Gentoo and only occasionally does this time extend any longer. The worst update time I had was when I updated GCC and this took the best part of a day. Everything on the system had to be recompiled for that one and obviously took a long time. That is equivalent to a complete re-install though.

In the end each to their own. I really like Gentoo and think it is a great system. Your software is configured for your hardware and you are forced to learn about your system.

---

### Post by igknighted on 2007-11-29
> **kevdog said:**
> I really dont mind compiling from source code, it does take a long time however, but the tradeoff is that you get the latest updates.

This is true, but not for the reasons you state.  You get the latest versions of apps because Gentoo chooses to put the latest versions in there.  You could do the same with a binary distro.  Check out Debian Sid (or Sidux) and you will have the same thing but with Apt and a Debian system.

> **kevdog said:**
> I dont like what you guys have told me however about the uninstallation potential problems.  I could see that breaking a lot of packages real quick.  Seems like once you install something -- I would never uninstall for fear of package breakage.  I thought I read also that Sabayon (maybe Gentoo) used some system to keep track of various dependency compilations/installs so that if you wanted to install a second package that shared many same packages with a package already installed, it would not re-compile the shared dependencies.

There are tools that assist you in removing packages safely.  See this page from the handbook: [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=1#doc_chap3](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=2&chap=1#doc_chap3)

Also, it is basically just like apt as far as solving dependencies when installing, so it will only install a certain dependency once.  It will recompile the same app if you install something that needs it with different sue flags enabled.  In fact should you decide to change your use flags, you can tell emerge to just recompile the programs that are effected by the change.

> **kevdog said:**
> I did a little reading emerge (just the basics).  I'm a little worried about compilation flags that might be needed.  Ive compiled on ubuntu before, and other than config options, Ive never had to use compilation flags.  Has anybody else found this to be a problem?

Nope, not really.  Sometimes you get funny things like when I had a KDE system with a -gtk flag set and installed pidgin, I didn't get the typical gtk frontend with it (only the libpurple/finch backend).  Adding the +gtk useflag got me the interface.

Just follow the handbook... it really is foolproof.  Use one of the default setups as far as useflags are concerned (the one that fits the system you want), and don't be afraid to ask questions on the forum.  It is by far the most knowledgeable linux community on the net, IMHO.

---

