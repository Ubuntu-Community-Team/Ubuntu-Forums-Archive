---
title: "which linux distro updates packages as they release?"
date: 2008-07-31
forum: Other OS Talk
---

### Post by TusharG on 2008-07-31
Which linux distro updates packages as they release? I'm Ubuntu user but usually I have seen that when a new package is released its not available in Ubuntu repos. Usually Ubuntu only patches the bug fixes/security updates on the installed packages. Ex: Banshee 1.2 is now released but Ubuntu repos are still pointing to the old one.
  Is there any Linux disto that updates the packages immediately rather then waiting for the new distro release? 
  I know i have option of downloading source and compiling but that leads to may problems of solving dependencies, but if there is a way like apt-get or yum I'd like to know if any Linux distro provides that.

---

### Post by cardinals_fan on 2008-07-31
Rolling release distros do that.  Arch is my favorite - I believe that Debian Testing/Sid is also rolling.  Gentoo and Sidux are also rolling.

---

### Post by ibutho on 2008-07-31
I know several distros that do that e.g. Arch Linux, Mandriva, openSUSE, PCLinuxOS and Fedora. With openSUSE you have to make sure that you have added the GNOME, KDE or whatever experimental repos you need otherwise it will just behave like Ubuntu (i.e. provide only security updates). With Mandriva, you need to enable the backports repos.

---

### Post by TusharG on 2008-08-01
Thanks a lot for quick reply. I'll definitely check Arch and PCLinuxOS Linux, In past I've tried Mandriva and Fedora and I did not like them at all.

---

### Post by kpkeerthi on 2008-08-01
Debian Sid/Sidux, Zenwalk snapshot, Slackware current usually update their repository as soon as packages are released upstream. But these are considered 'testing ground' and tend to break the integrity of the whole setup. Arch has similar Testing repo if you want to really stay on the bleeding edge. But usually, only stable packages get into Arch's main repositories.

---

### Post by TusharG on 2008-08-01
If that is the case... what is the typical time frame for a package to move from testing/backport to the main stream? So will Ubuntu also do the same? I mean will i get updated newer version of the package on ubuntu if i wait longer? Or do i need to upgrade the entire distro?

---

### Post by dca on 2008-08-01
Ubuntu doesn't necessarily alter LTS releases after...  I believe they do offer a backports repo but I've never needed that on any distro that offers a rolling six month release cycle:  openSUSE, Fedora, Ubuntu, & Mandriva...

---

### Post by L815 on 2008-08-01
What's the difference between "Normal Releases" and "LTS releases" only in the software sources menu for updates? 

I'm figuring that using an LTS (8.04) version with "normal releases" would make it kinda rolling release?? (probably far from haha)

---

### Post by maybeway36 on 2008-08-01
The closest thing to rolling release in Ubuntu is proably backports.
If you want a rolling distro with APT, try Debian sid.

---

### Post by 67GTA on 2008-08-01
PCLinuxOS uses the "rolling release" strategy. They don't put out a new release every six months. As long as you keep your system updated with apt/synaptic, you will have the latest versions they offer.

---

### Post by TusharG on 2008-08-09
This thread indeed has become very informative. Thanks everyone for contributing your knowledge in this post and putting light on this topic.

---

### Post by Naiki Muliaina on 2008-08-09
Curious to know, how up to date the backports/propsed updates in software sources?

[IMG]http://ubuntuforums.org/picture.php?albumid=427&pictureid=1473[/IMG]

---

### Post by kpkeerthi on 2008-08-09
Starting Elyssa, LinuxMint will follow pseudo-rolling package updates for LTS releases. That means LinuxMint LTS releases will continue to receive updates and hence remain up-to-date for 2 years:
> 
Starting with Elyssa, Linux Mint will consider two of its releases "current": The latest release, and the latest LTS release. Basically, this means that innovations put into Linux Mint 6, Linux Mint 7 and Linux Mint 8 will be backported into Linux Mint 5 until the next LTS release comes out. Users will have a choice to stay current over the next 2 years by keeping Linux Mint 5 Elyssa, or by following the latest releases every 6 months.

Although Linux Mint isn't a rolling distribution an LTS strategy will be put in place to ensure that Linux Mint 5 Elyssa will stay up to date over the next 2 years. Users will have the choice to enable the backport repository for Elyssa in which upgrades for important desktop applications (Firefox, Thunderbird, OpenOffice..) will be made available.
... from [http://www.linuxmint.com/rel_elyssa.php](http://www.linuxmint.com/rel_elyssa.php)

---

### Post by tel93 on 2008-08-09
> **TusharG said:**
> Which linux distro updates packages as they release? I'm Ubuntu user but usually I have seen that when a new package is released its not available in Ubuntu repos. Usually Ubuntu only patches the bug fixes/security updates on the installed packages. Ex: Banshee 1.2 is now released but Ubuntu repos are still pointing to the old one.
  Is there any Linux disto that updates the packages immediately rather then waiting for the new distro release? 
  I know i have option of downloading source and compiling but that leads to may problems of solving dependencies, but if there is a way like apt-get or yum I'd like to know if any Linux distro provides that.

Debian Lenny (or unstable) (apt-get)
Arch (pacman, which is very similar to apt)

---

### Post by rsambuca on 2008-08-10
Of the rolling release distros, I prefer Arch.  Foresight is another that hasn't been mentioned yet, and is done quite well.

---

### Post by basenvironment on 2008-08-11
ubuntu rolls, you just need to track the latest version that is in development but I would suggest debian testing...

---

### Post by rsambuca on 2008-08-11
> **basenvironment said:**
> ubuntu rolls, you just need to track the latest version that is in development but I would suggest debian testing...

I hardly think that a development branch of a distro qualifies as a rolling release distro.  They clearly are not the same, and have drastically different purposes.

---

### Post by basenvironment on 2008-08-11
you say tomato, I say  tomato

updating packages is updating packages. It isn't like devs grab a package that they know is going to cause a large amount of breakage and imediately upload it to the repo.

Where do you think intrepid came from? Did they start from scratch on every package or mirror hardy and start updating packages?

If gnome releases a.b.c then regardless if it you put it in a 'development branch' or a 'rolling release' it is still the same software.

Heck, I consider anything except the LTS releases to be from the 'development branch'.
:lolflag:

---

### Post by mips on 2008-08-11
> **rsambuca said:**
> i hardly think that a development branch of a distro qualifies as a rolling release distro.  They clearly are not the same, and have drastically different purposes.

+1

---

### Post by cardinals_fan on 2008-08-11
> **basenvironment said:**
> you say tomato, I say  tomato

updating packages is updating packages. It isn't like devs grab a package that they know is going to cause a large amount of breakage and imediately upload it to the repo.

Where do you think intrepid came from? Did they start from scratch on every package or mirror hardy and start updating packages?

If gnome releases a.b.c then regardless if it you put it in a 'development branch' or a 'rolling release' it is still the same software.

Heck, I consider anything except the LTS releases to be from the 'development branch'.
:lolflag:
Rolling != unstable.  Ubuntu's development versions include unstable software that hasn't been released yet.  Most true rolling distros only include software when it is deemed stable.

---

### Post by mips on 2008-08-11
> **cardinals_fan said:**
> Rolling != unstable.  Ubuntu's development versions include unstable software that hasn't been released yet.  Most true rolling distros only include software when it is deemed stable.

And that can be proved by the fact that they have Unstable->Testing->Stable repos ;)

---

### Post by cardinals_fan on 2008-08-11
> **mips said:**
> And that can be proved by the fact that they have Unstable->Testing->Stable repos ;)
Indeed.

---

### Post by basenvironment on 2008-08-11
> **cardinals_fan said:**
> Rolling != unstable. 
rolling == unstable if by unstable you mean 'constant changes'

> **cardinals_fan said:**
>  Ubuntu's development versions include unstable software that hasn't been released yet.  Most true rolling distros only include software when it is deemed stable.
Ubuntus LTS include 'unstable' software that hasn't been released. Most software in rolling release distros as well as software in non-rolling distros development releases have similar versions. Software in one may be newer than the other and vice versa. Some rolling distros play it a bit more safe than others.

But my point is that software is not pulled into either type without some regard to breakage and usability, period. Even devel versions have some older software as does rolling distros. Even devel versions are have to be usable to be testable.

Once again, updating software is updating software. Neither should be done flippantly in a rolling distro or a devel release.

---

### Post by rsambuca on 2008-08-11
> **basenvironment said:**
> Where do you think intrepid came from? Did they start from scratch on every package or mirror hardy and start updating packages?


Actually, the Ubuntu developers take a snapshot of debian sid every six months, apply their patches, fixes, etc.

Rolling release distros are designed to be as stable as they can make it given their timeframe and goals.

Development branches are for testing compatibility issues, fixing bugs, etc.  These are things that most rolling release distros do BEFORE packages are officially released.

---

### Post by basenvironment on 2008-08-11
> **rsambuca said:**
> Actually, the Ubuntu developers take a snapshot of debian sid every six months, apply their patches, fixes, etc.

Different distros use different versions based on what they consider prudent while considering breakage as well. Packages also get updated in intrepid, some packages are newer than debian unstable, some thing in intrepid are older than what is in debian unstable. Check the package versions between debian unstable, ubuntu intrepid, fedora, arch, and so forth. You can find various versions in each of those. One will have newer A and older B while another will have newer C but older D.

updating software is updating software....

I would certainly agree more works goes into a rolling distro to make sure breakage is minimized but things aren't just chucked into devel versions without some consideration either.

---

### Post by rsambuca on 2008-08-11
> **basenvironment said:**
> Different distros use different versions based on what they consider prudent while considering breakage as well. Packages also get updated in intrepid, some packages are newer than debian unstable, some thing in intrepid are older than what is in debian unstable. Check the package versions between debian unstable, ubuntu intrepid, fedora, arch, and so forth. You can find various versions in each of those. One will have newer A and older B while another will have newer C but older D.

updating software is updating software....

I would certainly agree more works goes into a rolling distro to make sure breakage is minimized but things aren't just chucked into devel versions without some consideration either.
I think we agree here, but the fact remains that the Ubuntu developers base their six month snapshot on sid.  Yes, then they make their changes, which may involve newer or older versions of some packages.  Obviously they don't just "chuck things in"!

---

### Post by TusharG on 2008-08-19
and when Ubuntu developers put the fixes on the debian sid do they send back the fixes to debian?

---

### Post by rsambuca on 2008-08-19
Of course.  This is open source software, for the most part.  Some Ubuntu patches will not work directly with debain, however, since Ubuntu has a slightly modified filesystem.

---

