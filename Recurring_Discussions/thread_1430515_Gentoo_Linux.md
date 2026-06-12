---
title: "Gentoo Linux"
date: 2010-03-15
forum: Recurring Discussions
---

### Post by Shining Arcanine on 2010-03-15
Ubuntu introduced me to using Linux, first via Wubi and then via virtual machines, but I hardly used it, opting to use Windows XP primarily. I switched to Windows 7 in September, but then I decided to use my winter break to become better at Unix, so I switched to Linux on my laptop to force myself to use it on a day to day basis and I have been happy ever since.

I decided to install Gentoo Linux on my laptop because I had installed it in virtual machines to play with it around September and I liked how customizable it was. I was able to use Gentoo's package manager to install stable software shortly after it was released by upstream that my experience showed would take 6 to 12 months to become available in Ubuntu's repositories. I am impatient when it comes to getting the latest versions of software I use frequently, so the idea that I could get the latest versions of software I use shortly after the upstream developers release it appealed to me greatly.

Does anyone else here use Gentoo Linux?

---

### Post by Bachstelze on 2010-03-15
> **Shining Arcanine said:**
> 
Does anyone else here use Gentoo Linux?

I did at some point, some 3-ish years ago, then I realized it just wasn't worth the hassle. If I want the latest version of something, I can compile it in Ubuntu, too.

---

### Post by Simian Man on 2010-03-15
Arch updates their packages very quickly after they are released upstream, but uses simpler, binary package management.  So that may be good option if Gentoo becomes too tedious for you.

---

### Post by swoll1980 on 2010-03-15
*stands up slowly* =D>

---

### Post by Shining Arcanine on 2010-03-15
> **Bachstelze said:**
> I did at some point, some 3-ish years ago, then I realized it just wasn't worth the hassle. If I want the latest version of something, I can compile it in Ubuntu, too.

How do you avoid conflicts with the package manager's dependency resolution? Wouldn't the package manager think that files for your compiled programs are not installed and attempt to install them automatically? How do you handle long dependency chains where a newer versions of program x requires newer versions of programs a, b and c, which in turn require newer versions of yet more programs, all of which are outside of Ubuntu's repositories? How do avoid having linker issues when the default location for libraries is not Ubuntu's expected location?

It seems like more of a hassle to compile stuff under Ubuntu than it is under Gentoo. If you managed to resolve the issues involved in doing this, I would love to hear how you did it.

---

### Post by Bachstelze on 2010-03-15
> **Shining Arcanine said:**
> How do you avoid conflicts with the package manager's dependency resolution? Wouldn't the package manager think that files for your compiled programs are not installed and attempt to install them automatically?

Apt doesn't know 'bout my compiled programs. ;) As far as it is concerned, they are not installed, never were, never will be.

> **Shining Arcanine said:**
> How do you handle long dependency chains where a newer versions of program x requires newer versions of programs a, b and c, which in turn require newer versions of yet more programs, all of which are outside of Ubuntu's repositories?[ How do avoid having linker issues when the default location for libraries is not Ubuntu's expected location?

I never run into those issues. I don't run any monster programs like that. And by the way, what makes you think Ubuntu installs libraries in an obscure, non-standard location? It doesn't.

---

### Post by swoll1980 on 2010-03-15
> **Shining Arcanine said:**
> 
It seems like more of a hassle to compile stuff under Ubuntu than it is under Gentoo. If you managed to resolve the issues involved in doing this, I would love to hear how you did it.

Compiling any thing for any reason is a hassle. I have had to compile a couple of things. ZSNES for 64 bit Ubuntu for one. I didn't have any problems, and because apt wasn't used to install it, it has no idea it even exist.

---

### Post by MisfitI38 on 2010-03-15
> **Shining Arcanine said:**
> How do you avoid conflicts with the package manager's dependency resolution? Wouldn't the package manager think that files for your compiled programs are not installed and attempt to install them automatically? How do you handle long dependency chains where a newer versions of program x requires newer versions of programs a, b and c, which in turn require newer versions of yet more programs, all of which are outside of Ubuntu's repositories? How do avoid having linker issues when the default location for libraries is not Ubuntu's expected location?

It seems like more of a hassle to compile stuff under Ubuntu than it is under Gentoo. If you managed to resolve the issues involved in doing this, I would love to hear how you did it.
I don't use Ubuntu, but ```
./configure --prefix=/usr/local
```
Sounds like you're making something dead simple and trivial into a straw man argument.

---

### Post by Bachstelze on 2010-03-15
> **MisfitI38 said:**
> I don't use Ubuntu, but ```
./configure --prefix=/usr/local
```
Sounds like you're making something dead simple and trivial into a straw man argument.

--prefix is /usr/local by default. ;)

---

### Post by Simian Man on 2010-03-15
Sure compiling an application here and there on Ubuntu is easy enough, but I'd like to see you guys upgrade to, say, KDE 4.4 by compiling it from source.

---

### Post by Bachstelze on 2010-03-15
> **Simian Man said:**
> Sure compiling an application here and there on Ubuntu is easy enough, but I'd like to see you guys upgrade to, say, KDE 4.4 by compiling it from source.

Why would anyone do such a thing? That's what backports and PPAs are for.

---

### Post by SushiR on 2010-03-15
> **Shining Arcanine said:**
> Ubuntu introduced me to using Linux, first via Wubi and then via virtual machines, but I hardly used it, opting to use Windows XP primarily. I switched to Windows 7 in September, but then I decided to use my winter break to become better at Unix, so I switched to Linux on my laptop to force myself to use it on a day to day basis and I have been happy ever since.

I decided to install Gentoo Linux on my laptop because I had installed it in virtual machines to play with it around September and I liked how customizable it was. I was able to use Gentoo's package manager to install stable software shortly after it was released by upstream that my experience showed would take 6 to 12 months to become available in Ubuntu's repositories. I am impatient when it comes to getting the latest versions of software I use frequently, so the idea that I could get the latest versions of software I use shortly after the upstream developers release it appealed to me greatly.

Does anyone else here use Gentoo Linux?

I used Source Mage, which is a source based distro, some years ago. I liked it, but I must admit it wasn't worth the hassle. If you're tired of compiling, have a look at Arch. That's really one fine distro with bleeding edge packages. It's easy to maintain and i686 optimized. I'd give it a try if I were you... ;-)

---

### Post by swoll1980 on 2010-03-15
> **Bachstelze said:**
> Why would anyone do such a thing? That's what backports and PPAs are for.
I guess that 2 week wait is to much to handle.

---

### Post by Bachstelze on 2010-03-15
> **swoll1980 said:**
> I guess that 2 week wait is to much to handle.

"How poor are they that have not patience!"

--William Shakespeare, *Othello*, II, 3

---

### Post by Shining Arcanine on 2010-03-15
> **Bachstelze said:**
> Why would anyone do such a thing? That's what backports and PPAs are for.

I had KDE 4.4.0 running on my laptop the day after it was released. KDE 4.4.1 I had installed on the same day it was released. While doing this, I was able to strip out much of the bloat (e.g. strigi, nepomuk) from KDE to have a leaner running system. It is difficult to do that with Ubuntu's repositories. :/

By the way, while having the latest version of KDE is nice, that is not what I meant when I was talking about having the latest versions of the software I use. I meant more along the lines of having the latest versions of Open Office, Firefox, GCC and any open source libraries (e.g. GMP, Boost) I use or might use for software development. That sort of software is usually the software I found to be frustratingly out of date when I ran Ubuntu via either Wubi or virtual machines. I imagine that having the latest development release of Chromium available for web development on Ubuntu is probably much more difficult than it is on Gentoo.

---

### Post by MisfitI38 on 2010-03-15
> **Bachstelze said:**
> --prefix is /usr/local by default. ;)

Not to split hairs, but there is no such thing as 'default' here, because **not** all scripts will install to /usr/local. 
It's always best to specify it, to keep it separate from the /usr/ hierarchy.:popcorn:

---

### Post by Shining Arcanine on 2010-03-16
> **MisfitI38 said:**
> Not to split hairs, but there is no such thing as 'default' here, because **not** all scripts will install to /usr/local. 
It's always best to specify it, to keep it separate from the /usr/ hierarchy.:popcorn:

Even if the files are in the right place, I do not see how someone would inform the package manager that x version of package y was installed manually, so its dependency resolution does not do strange things when you use it to install/upgrade software that depends on it, both in the case that the software can work with version x of package y that you installed and in the case that it cannot.

Gentoo does this easily because its packages are wrappers for the build systems of various software packages and it keeps track of every file that a package installs in its database. If a new software package or an upgrade of an existing package requires that another one be upgraded, it can just remove every file it installed previously and then build the new version, assuming it has the new version available in the portage tree, which is usually the case. If it is not the case, you can usually find it in an overlay someone else made or you can write your own ebuild for it:

[http://www.gentoo.org/proj/en/devrel/handbook/handbook.xml?part=2&chap=1](http://www.gentoo.org/proj/en/devrel/handbook/handbook.xml?part=2&chap=1)
[http://www.gentoo.org/proj/en/desktop/games/games-ebuild-howto.xml](http://www.gentoo.org/proj/en/desktop/games/games-ebuild-howto.xml)
[http://en.gentoo-wiki.com/wiki/Writing_Ebuilds](http://en.gentoo-wiki.com/wiki/Writing_Ebuilds)

I guess you could use CheckInstall to remove stuff you compiled on your own on Ubuntu, but I do not see how this approach to compiling your own software integrates into Ubuntu's package manager in the same way that software compilation integrates into Gentoo's package manager:

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by MisfitI38 on 2010-03-16
> **Shining Arcanine said:**
> Even if the files are in the right place, I do not see how someone would inform the package manager that x version of package y was installed manually, so its dependency resolution does not do strange things when you use it to install/upgrade software that depends on it, both in the case that the software can work with version x of package y that you installed and in the case that it cannot.
It will either work or not. As for 'informing the package manager'; apt, or any other binary package manager does not 'care' nor does it need to 'know' about manually compiled packages. It is the user who maintains his own manually built packages on a binary system, unless you have the availability of a ports-like system, which adds a level of convenience.
> 
Gentoo does this easily because its packages are wrappers for the build systems of various software packages and it keeps track of every file that a package installs in its database. 
Portage is a source-based packaging system, and it's good at what it's designed for.

Note that people who gravitate toward binary systems in the first place do not compile hundreds or even dozens of packages manually...that's the whole point of using binary, and it works quite well.
You won't win many points by advocating source-based packaging on the Ubuntu forums.

---

### Post by Tibuda on 2010-03-16
> **Shining Arcanine said:**
> Even if the files are in the right place, I do not see how someone would inform the package manager that x version of package y was installed manually, so its dependency resolution does not do strange things when you use it to install/upgrade software that depends on it, both in the case that the software can work with version x of package y that you installed and in the case that it cannot.

Debian based distros can handle compiled software using checkinstall, and Arch has PKGBUILD/makepkg/AUR.

---

### Post by kk0sse54 on 2010-03-16
I used to run it quite extensively and it used to be my favorite OS until I switched to FreeBSD. It was a great system and I didn't mind compiling everything, unfortunately the project itself seems to be continually falling apart with more developer in fighting and even a few resignations. Furthermore, it seems like the quality has generally decreased at least in regards to the ebuilds in portage. Instead, what's more interesting to see is the direction that funtoo will be taking in these coming years.

---

### Post by Shining Arcanine on 2010-03-17
> **C!oud said:**
> I used to run it quite extensively and it used to be my favorite OS until I switched to FreeBSD. It was a great system and I didn't mind compiling everything, unfortunately the project itself seems to be continually falling apart with more developer in fighting and even a few resignations. Furthermore, it seems like the quality has generally decreased at least in regards to the ebuilds in portage. Instead, what's more interesting to see is the direction that funtoo will be taking in these coming years.

I believe those issues were resolved when the people who were causing the in-fighting broke off to make Exherbo according to their own ideas. I think that the decline in quality left with them, because I understand that upgrading a Exherbo weekly (or even daily) will result in breaking a system running it while you can upgrade Gentoo as much as you want without issue, even if you use software from Gentoo's testing tree (all of it is declared stable by upstream) by using ACCEPT_KEYWORDS="~x86" in /etc/make.conf.

---

### Post by kk0sse54 on 2010-03-17
> **Shining Arcanine said:**
> I believe those issues were resolved when the people who were causing the in-fighting broke off to make Exherbo according to their own ideas. 

No they weren't. [http://blog.flameeyes.eu/2010/02/22/what-s-wrong-with-gentoo-anyway](http://blog.flameeyes.eu/2010/02/22/what-s-wrong-with-gentoo-anyway)

---

### Post by MisfitI38 on 2010-03-17
> **Shining Arcanine said:**
> ...you can upgrade Gentoo as much as you want without issue, even if you use software from Gentoo's testing tree (all of it is declared stable by upstream) by using ACCEPT_KEYWORDS="~x86" in /etc/make.conf.

I'm not sure who told you this (they don't sound like your words), but it is hogwash. You *will* eventually run into breakage with portage; it's something you either get used to or flee from.

---

### Post by Shining Arcanine on 2010-03-17
> **MisfitI38 said:**
> I'm not sure who told you this (they don't sound like your words), but it is hogwash. You *will* eventually run into breakage with portage; it's something you either get used to or flee from.

It is my experience so far. I actually have had some minor issues with portage on occasion, but they were so trivial to fix that I hardly consider them to be issues, especially since I am running ~arch, so such minor things are to be expected.

---

### Post by Shining Arcanine on 2010-03-17
> **C!oud said:**
> No they weren't. [http://blog.flameeyes.eu/2010/02/22/what-s-wrong-with-gentoo-anyway](http://blog.flameeyes.eu/2010/02/22/what-s-wrong-with-gentoo-anyway)

There is a discussion on the Gentoo Linux forums about that:

[http://forums.gentoo.org/viewtopic-t-816607.html](http://forums.gentoo.org/viewtopic-t-816607.html)

While he makes some points, they are not as bad as they appear.

---

