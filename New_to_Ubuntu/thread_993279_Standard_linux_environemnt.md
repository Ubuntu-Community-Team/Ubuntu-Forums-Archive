---
title: "Standard linux environemnt?"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by MillDaKill on 2008-11-25
I had a question... Every 6 month a new version of Ubuntu is released and with all the latest and greatest software/libraries comes computability issues with software that is not from the Ubuntu repos.  Why doesn't Ubuntu continue to roll out the latest and greatest every 6 months but also include something like the "Ubuntu Standard Application Environment version 1.0" where they maintain a 2nd set of tools/libraries that never make major changes.  This way, if a company like Amazon wants to offer their mp3 download software, they could just develop it using the tools in the "Ubuntu Standard Application Environment" that will be made available in all future release of Ubuntu.

---

### Post by opscure on 2008-11-25
> **MillDaKill said:**
>  "Ubuntu Standard Application Environment version 1.0" where they maintain a 2nd set of tools/libraries that never make major changes.

Why would they need the version number if they are not going to make any changes? ](*,)

---

### Post by MillDaKill on 2008-11-25
> **opscure said:**
> Why would they need the version number if they are not going to make any changes? ](*,)

well, I think there would be a need to make minor changes to keep up with security issues and bugs so you could have 1.x versions.  I also believe at some point you would want to roll out a newer version with a new set of tools you will maintain going forward.

---

### Post by scorp123 on 2008-11-25
> **MillDaKill said:**
>  where they maintain a 2nd set of tools/libraries that never make major changes. That's what the Ubuntu "LTS" (long term support) releases are for ;)

Current LTS release is 8.04 (the previous was 6.06).

---

### Post by MillDaKill on 2008-11-25
> **scorp123 said:**
> That's what the Ubuntu "LTS" (long term support) releases are for ;)

Current LTS release is 8.04 (the previous was 6.06).


What percentage of users stick on an LTS for the full cycle?

---

### Post by scorp123 on 2008-11-25
> **MillDaKill said:**
> What percentage of users stick on an LTS for the full cycle? What percentage of users skipped XP and Vista and still use good old Windows 2000? ;)

The answer is: "Hard to tell." :)

LTS releases definitely have their appeal. In my company we still use Ubuntu 7.10 and 8.04 in most places, simply because the software is more or less "bug free" and quite stable now. And why should I touch or change systems that are running tip top? So we're likely to leave those systems "as is" for as long as we can get patches for them. And it's likely the same thinking you'd encounter in other companies too. Stability and continuity of the services always comes first ... new (and potentially unneeded?) features and new gadgets come second.

---

### Post by MillDaKill on 2008-11-25
> **scorp123 said:**
> What percentage of users skipped XP and Vista and still use good old Windows 2000? ;)

The answer is: "Hard to tell." :)

LTS releases definitely have their appeal. In my company we still use Ubuntu 7.10 and 8.04 in most places, simply because the software is more or less "bug free" and quite stable now. And why should I touch or change systems that are running tip top? So we're likely to leave those systems "as is" for as long as we can get patches for them. And it's likely the same thinking you'd encounter in other companies too. Stability and continuity of the services always comes first ... new (and potentially unneeded?) features and new gadgets come second.


I totally agree with that opinion for the business prospective, but the non-business user is not just concerned with stability, this user wants the newest version of firefox, wants to have the newest version of pidgin and wants the newest version of pretty much every major app.  The only problem is that the way things are set up now, it makes offering software outside of the repos a pain.

---

### Post by scorp123 on 2008-11-25
> **MillDaKill said:**
> The only problem is that the way things are set up now, it makes offering software outside of the repos a pain. Nobody is stopping you to start your own repo, e.g. on launchpad? Many people do exactly that. I too have a few apps for my own personal laptop that I get via semi-inofficial launchpad repos. All you need to do as end-user is to copy & paste the repo's URL's into your synaptic package manager and voila, done, you easily get more access to more software.

Bigger companies and organisations usually maintain their own repos anyway and thanks to Google it should be no big problem to find the info. I have e.g. Sun's repo for xVM VirtualBox (the non-free version) and Google's repo for their Linux software (Google Earth, Picasa, some others) configured on my system. Works tip top.

---

### Post by MillDaKill on 2008-11-25
> **scorp123 said:**
> Nobody is stopping you to start your own repo, e.g. on launchpad? Many people do exactly that. I too have a few apps for my own personal laptop that I get via semi-inofficial launchpad repos. All you need to do as end-user is to copy & paste the repo's URL's into your synaptic package manager and voila, done, you easily get more access to more software.

Bigger companies and organisations usually maintain their own repos anyway and thanks to Google it should be no big problem to find the info. I have e.g. Sun's repo for xVM VirtualBox (the non-free version) and Google's repo for their Linux software (Google Earth, Picasa, some others) configured on my system. Works tip top.

You are right, you can configure your way out of pretty much anything.  I just see this as one of the barriers of entry, its a bit unreasonable to expect software producers to make new builds every 6 months for what is now a pretty small user base and its a bit unreasonable to expect most users to have to re-configure apt-get every time they want to install something that's not in the repos.

---

### Post by halitech on 2008-11-25
I don't think there is anyone forcing software developers into coming out with a new version every 6 months (I could be wrong though). They should be able to just submit to Canocal the same version to be included as is if they haven't made any changes for the next version of Ubuntu. 

and it wouldn't be apt-get that they would have to reconfigure, just a matter of adding a line to /etc/apt/sources.list ;)

---

### Post by scorp123 on 2008-11-26
> **MillDaKill said:**
> its a bit unreasonable to expect software producers to make new builds every 6 months Why do you assume that?? Unless the software in question is dramatically outdated and e.g. relies on ancient features that are no longer present (I once had an ancient proprietary VPN client that would rely on Linux 2.4x kernels and refused to work on the current 2.6x kernels!) it should work tip top with what's inside any given Ubuntu release. You see: most stuff is downwards-compatible. So if Ubuntu ships version "1.1" of a certain library and a software maker decides that their software needs that library, fine. No problem there. "apt" should resolve the issue. Fast-forward six months into the future: Ubuntu now ships version "1.3" of the same library, but the software you previously used still requires version "1.1" of said library. Taaadaaaa: no problem whatsoever! :D

As a matter of fact you can check it yourself. Let's take xVM VirtualBox from Sun Microsystems for example:

```
> apt-cache show virtualbox-2.0

Package: virtualbox-2.0
Version: 2.0.6-39765_Ubuntu_intrepid
Architecture: i386
Maintainer: Sun Microsystems, Inc. <info@virtualbox.org>
Installed-Size: 64036
[COLOR="Red"]**Pre-Depends: debconf (>= 1.1) | debconf-2.0[/COLOR]**
[B][COLOR="Red"]Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1), libqt4-network (>= 4.4.3), 
libqtcore4 (>= 4.4.3), libqtgui4 (>= 4.4.3), libsdl1.2debian (>= 1.2.10-1), 
libssl0.9.8 (>= 0.9.8f-5), libstdc++6 (>= 4.2.1), libx11-6, 
libxcursor1 (>> 1.1.2), libxext6, libxml2 (>= 2.6.27), 
libxslt1.1 (>= 1.1.18), libxt6, python2.5 (>= 2.5), 
psmisc, adduser[/COLOR][/B]
Recommends: libasound2, libpulse0, libsdl-ttf2.0-0, dkms, linux-headers, 
gcc, make, binutils, bridge-utils, uml-utilities, libhal1 (>= 0.5), pdf-viewer
Conflicts: virtualbox
Replaces: virtualbox
Provides: virtualbox
Priority: optional
Section: misc
Filename: pool/non-free/v/virtualbox-2.0/virtualbox-2.0_2.0.6-39765_Ubuntu_intrepid_i386.deb
Size: 30152018
SHA1: bdda18265f9c0f21a22a0cd2cb8acbff23879f8c
MD5sum: c5653bbabed78fb97858e127375cd6cd
Description: Sun xVM VirtualBox
 VirtualBox is a powerful PC virtualization solution allowing you to run a
 wide range of PC operating systems on your Linux system. This includes
 Windows, Linux, FreeBSD, DOS, OpenBSD and others. VirtualBox comes with a broad
 feature set and excellent performance, making it the premier virtualization
 software solution on the market.
``` See those parts I highlighted in red?

"Pre-Depends: debconf (>= 1.1) | debconf-2.0" ... in other words the software is OK with your system for as long as you either get version 1.1 or better (>= 1.1) of "debconf" or ( | ) you get a "2.x" version of that package.

Same with the other stuff I highlighted above. There is no need for e.g. Sun and the designers to rebuild VirtualBox from scratch every six months just to satisfy us Ubuntu users. That's not how it works :D

As I said above: most libs and stuff are downwards-compatible, so you'd only run into problems if you downgrade your distro (because then all those ">=" 'equal or higher' dependencies cannot be satisfied any longer), but not if you upgrade every six months. :)

---

### Post by hyper_ch on 2008-11-26
> **MillDaKill said:**
> its a bit unreasonable to expect software producers to make new builds every 6 months

Nobody forces them... what you have in the repos are compiled programs by ubuntu devs and communicty members... they compile the source code and put the bianries into the repos.

It's not the software producers who do that. The software producers just have to release the source whenever they want and distro maintainers will then compile that stuff.

---

### Post by scorp123 on 2008-11-26
> **hyper_ch said:**
>  It's not the software producers who do that. The software producers just have to release the source ...  Not exactly true. In the case e.g. of Sun's xVM VirtualBox or Google's "Google Earth" it is them -the so called "software producers"- who maintain their own repos. You can't get the source code for those products (the source code for VirtualBox OSE is just a sub-set and e.g. doesn't contain some features of the closed-source variant). Same goes for the "Partner" repos and the software in there. ;)

---

### Post by hyper_ch on 2008-11-26
> **hyper_ch said:**
> Nobody forces them... [...]
The software producers just have to release the source whenever they want and distro maintainers will then compile that stuff.

> **scorp123 said:**
> In the case e.g. of Sun's xVM VirtualBox or Google's "Google Earth" it is them -the so called "software producers"- who maintain their own repos.
.... they do this, by their choice ;)

---

### Post by scorp123 on 2008-11-26
> **hyper_ch said:**
> .... they do this, by their choice ;) Yes, but to get back on-topic: They're in no way forced to recompile their own products every six months if they don't want to, regardless what Ubuntu does with their distro. Chances are that the new versions of any library in any new Ubuntu release will still work tip top with the software.

But as far as open source software is concerned you are of course right: chances are that e.g. the makers of Debian and/or Ubuntu take the source packages, compile them against anything new in the distro and then place the packages into the community repos. Again no need for any developer to recompile his stuff himself every few months ... once for Debian, then twice a year for Ubuntu, then for Fedora, then for OpenSUSE, then for <insert name of distro> ... that would be a bit weird :)

---

