---
title: "should linux have a standard installer?"
date: 2009-05-29
forum: Recurring Discussions
---

### Post by mamamia88 on 2009-05-29
wouldn't linux be much better with a standard installer?  that way you would never have to install from source and confuse newer users.  this is honestly the biggest turnoff to linux as far as i'm concerned.

---

### Post by dragos240 on 2009-05-29
nope. That would kill gentoo.

---

### Post by Dimitriid on 2009-05-29
Linux wouldn't be better ( and in fact would be a lot worst ) with a standard anything.

---

### Post by RedPandaFox on 2009-05-29
Troll much?

---

### Post by unknownPoster on 2009-05-29
compiling from source is one of my favorite things about Linux... if you get rid of it, you'll lose quite a few Linux Users, (Gentoo, Lunar, Arch + ABS, etc)

---

### Post by hanzomon4 on 2009-05-29
When do you have to compile from source?

---

### Post by monsterstack on 2009-05-29
Avoid monoculture and ubiquity in all its forms. That road leads to Internet Explorer.

---

### Post by mamamia88 on 2009-05-29
> **RedPandaFox said:**
> Troll much?

 just frustrated that vmware only offers rpm or tar.gz packages and i converted rpm with alien and can't even launch vmware player

---

### Post by Xbehave on 2009-05-29
Can't work, if a program is going to work on ubuntu 7.10 it needs different dependencies than 8.04 let alone Fedora. If a program doesn't have specific dependencies, then there is a standard installer, tar. A distros main purpose is to establish a quality assured secure base, canonical doesn't do much more than make sure all the apps in their repositories play nicely with each-other and select which packages go into a default install, if your going to start installing your own untested applications then there is no benefit to using apt-get over downloading and unpacking in /opt. 

The ONLY place i can see there being an advantage to standardizing packaging is if your producing an app with no specific system dependencies* (e.g firefox) and want an easy way of offering autoupdates hosting a single unified repo would be easier than
1) rolling your own update system (ala firefox)
2) hosting a both .deb & .rpm based repos, but tbh the solution to this is to provide a tool that makes that easy not to go messing around with the complexities of package managment!

*or dependancies that are met by lsb

---

### Post by albinootje on 2009-05-29
> **mamamia88 said:**
> just frustrated that vmware only offers rpm or tar.gz packages and i converted rpm with alien and can't even launch vmware player

Any reason you prefer VMware over VirtualBox ? (The only plus I can see is that VMware apparently runs BSD better than VB does)

---

### Post by Keithhed on 2009-05-29
> **dimitriid said:**
> linux wouldn't be better ( and in fact would be a lot worst ) with a standard anything.

+1

---

### Post by mamamia88 on 2009-05-29
hoping usb works out of the box and hoping abc.com works.  maxed out video memory in virtualbox and still wouldn't render video from their site

---

### Post by jrusso2 on 2009-05-29
Having a standard installer would make it easier for commercial applications to port to Linux.

---

### Post by SunnyRabbiera on 2009-05-29
No, we cannot force one standard format as that would go against the diversity of Linux.
Really Microsoft technically has more installer formats then linux does, sure .exe is the standard but there are others.

Its not that hard to make a universal .deb or maybe a universal .rpm that works for all distros, both flash and real use a .deb or .rpm that can work on all systems theoretically.
Virtualbox and opera have a lot of legacy ports though, especially virtualbox with its multitude of optional installers.
Opera is still at QT3 in design, while virtualbox offers obth qt3 and 4 options.

> **jrusso2 said:**
> Having a standard installer would make it easier for commercial applications to port to Linux.

Nonsense, both RPM and Deb are similar enough to port for.

---

### Post by Firestem4 on 2009-05-29
> **mamamia88 said:**
> just frustrated that vmware only offers rpm or tar.gz packages and i converted rpm with alien and can't even launch vmware player

There should be a VMWare.bundle package available for download. That is what I used to install VMWare on my Kubuntu machine.

If you download the bundle you have to make it an executable before you can launch the installer.

---

### Post by SunnyRabbiera on 2009-05-29
.rpm is more common in commercial apps as redhat has a lot of influence on the market, but Ubuntu is catching up.

---

### Post by mamamia88 on 2009-05-29
> **Firestem4 said:**
> There should be a VMWare.bundle package available for download. That is what I used to install VMWare on my Kubuntu machine.

If you download the bundle you have to make it an executable before you can launch the installer.

nope only tars

---

### Post by dspari1 on 2009-05-29
> **mamamia88 said:**
> just frustrated that vmware only offers rpm or tar.gz packages and i converted rpm with alien and can't even launch vmware player

The standard Linux installer is *.rpm. If your distro doesn't support rpm, then it's not Linux compliant.

[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)

> Choice of RPM package format

For example, the LSB specifies that software packages should either be delivered as an LSB compliant installer, or (preferably) be delivered in a restricted form of the RPM format. Debian however uses its own format, the deb package format, which predates rpm. Debian developers argue their format is superior to RPM, and that further changing the underlying package format of a distribution to satisfy the LSB is fairly unrealistic. Most packages can be converted between .rpm and .deb with alien or other package conversion program, but each format has capabilities the other lacks, so this operation doesn't work every time and is impossible to use with some packages.

To address this, the standard does not dictate what package format the software system must use for its own packages, merely that RPM must be supported to allow packages from third-party distributors to be installed on a conforming system.

Since Debian already includes optional support for the LSB (at version 1.1 in "woody" and 2.0 in "sarge"), this issue evaporates under closer scrutiny (i.e. the end user just needs to use Debian's alien program to transform and install the foreign RPM packages in the native package format). This is part of the reason the specified RPM format is a restricted subset&#8212;to block usage of untranslatable RPM features. By using alien, Debian is LSB-compatible to all intents and purposes, but according to the description of the lsb-package, the presence of the lsb-package "does not imply that we believe that Debian fully complies with the Linux Standard Base, and should not be construed as a statement that Debian is LSB-compliant." This theoretical possibility of Debian's non-compliance to LSB might be considered a valid criticism, however slight.

My belief is that standardization puts limits on progress because people will try to focus on being compliant rather than progressing to something newer and better.

---

### Post by jrusso2 on 2009-05-29
> **SunnyRabbiera said:**
> No, we cannot force one standard format as that would go against the diversity of Linux.
Really Microsoft technically has more installer formats then linux does, sure .exe is the standard but there are others.

Its not that hard to make a universal .deb or maybe a universal .rpm that works for all distros, both flash and real use a .deb or .rpm that can work on all systems theoretically.
Virtualbox and opera have a lot of legacy ports though, especially virtualbox with its multitude of optional installers.
Opera is still at QT3 in design, while virtualbox offers obth qt3 and 4 options.




Nonsense, both RPM and Deb are similar enough to port for.

Nonsense to you.  Have a look at some commercial apps.  RPM, DEB, Tar.gz, QT, Gnome for one application.  Then divide by distros.  No wonder they won't make photoshop for Linux.

---

### Post by albinootje on 2009-05-29
> **jrusso2 said:**
> Nonsense to you.  Have a look at some commercial apps.  RPM, DEB, Tar.gz, QT, Gnome for one application.  Then divide by distros.  

See here an excellent example that this is not a problem : [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php) -> Linux client.
Three options (deb,rpm,tar) for 32bit and three options for 64bit. No problem at all.
> 
No wonder they won't make photoshop for Linux.
We don't know exactly why there is no PhotoShop for sale for Linux. It is not the market-share myth, because PhotoShop for Apple is there since years, (and years ago when PS for Apple was brought to the market,) Apple probably had a market share below 1% on the desktop all over the planet.

I think that companies who make more than enough cash (Like Adobe), are not interested because they think that Linux users don't want to spend money, certainly not if they did already spend it on PS on the other OS on their dual-boot machines.

---

### Post by jrusso2 on 2009-05-29
[QUOTE=albinootje;7369890]See here an excellent example that this is not a problem : [http://www.nomachine.com/download.php](http://www.nomachine.com/download.php) -> Linux client.
Three options (deb,rpm,tar) for 32bit and three options for 64bit. No problem at all.

Heh, thanks for helping me prove my point.  Have a  look at the Opera download page for even more packages needed for Linux.

I don't know why any commercial company should bother with this when it takes two packages for Windows and one for mac.

---

### Post by albinootje on 2009-05-29
> **jrusso2 said:**
>  I don't know why any commercial company should bother with this when it takes two packages for Windows and one for mac.

Nomachine is a commercial company, and so is Opera.

---

### Post by lykwydchykyn on 2009-05-29
It is not a problem for anyone to make an *installer* that works on any Linux system.  Write a script that drops static binaries into /opt and you're done.  Make a GUI if you like to bloat things up. I've installed several pieces of commercial Linux software that work this way; see googleearth if you want an example.

The downside to this approach is that you don't interact with the package management system.  What you guys are asking for is not a universal INSTALLER, but a universal PACKAGE MANAGER.  Big difference.

It seems to me that package managers exist to manage dynamic library dependencies.  I have seen relatively few commercial Linux packages that rely on shared dynamic libraries.  If you're just going to statically link packages and dump them in /opt or /usr/local (which I'd think most proprietary commercial products would), there is no need to check for dependencies, file conflicts, or previous versions.  All the package management would do is provide a consistent install/uninstall interface for the user.

I think this "there are too many packaging formats!" excuse is baloney.  Plenty of software vendors, large and small, offer software for multiple Linux distros in spite of it.  Of course, that's my totally non-expert armchair opinion on the subject. YMMV.

---

### Post by jrusso2 on 2009-05-30
> **albinootje said:**
> Nomachine is a commercial company, and so is Opera.

What's your point.  The only reason I mentioned Opera was that is was commercial?

I mentioned them to show the number of packages they have to make to be absurd.

---

### Post by Tibuda on 2009-05-30
> **lykwydchykyn said:**
> It is not a problem for anyone to make an *installer* that works on any Linux system.  Write a script that drops static binaries into /opt and you're done.  Make a GUI if you like to bloat things up. I've installed several pieces of commercial Linux software that work this way; see googleearth if you want an example.

The downside to this approach is that you don't interact with the package management system.  What you guys are asking for is not a universal INSTALLER, but a universal PACKAGE MANAGER.  Big difference.

It seems to me that package managers exist to manage dynamic library dependencies.  I have seen relatively few commercial Linux packages that rely on shared dynamic libraries.  If you're just going to statically link packages and dump them in /opt or /usr/local (which I'd think most proprietary commercial products would), there is no need to check for dependencies, file conflicts, or previous versions.  All the package management would do is provide a consistent install/uninstall interface for the user.

I think this "there are too many packaging formats!" excuse is baloney.  Plenty of software vendors, large and small, offer software for multiple Linux distros in spite of it.  Of course, that's my totally non-expert armchair opinion on the subject. YMMV.

Yeah, there's nothing stoping the software vendors to create their own installer like they do for Windows. Or maybe just compressing the binaries in a tar.gz like does Mozilla.

---

### Post by SunnyRabbiera on 2009-05-30
> **jrusso2 said:**
> Nonsense to you.  Have a look at some commercial apps.  RPM, DEB, Tar.gz, QT, Gnome for one application.  Then divide by distros.  No wonder they won't make photoshop for Linux.

Feh they can use GTK as GTK right now seems more universally ready then QT4.
QT4 still needs work, but in the future it could become viable for everyone.
But people like you want there to only be 1 distro, 1 choice...
Linux is about diversity, its about time you learned that.
To force everyone to use the same linux would be no better then MS.

---

### Post by WatchingThePain on 2009-05-30
Having different installers is a good thing as some work better on various hardware.
People like choice and to me that flexibility is part of what Linux is about.

I suppose this 'one fits all' installer would be graphical, maybe with a blue background?.

---

### Post by Paqman on 2009-05-30
> **mamamia88 said:**
> wouldn't linux be much better with a standard installer?

Absolutely, but due to the fractured nature of open source development it'll never happen. We're basically stuck with a hell of a lot of duplication of effort, which is massively inefficient.

---

### Post by SunnyRabbiera on 2009-05-30
> **Paqman said:**
> Absolutely, but due to the fractured nature of open source development it'll never happen. We're basically stuck with a hell of a lot of duplication of effort, which is massively inefficient.

right so lets break peoples arms to force them to use the same thing... feh

---

### Post by Paqman on 2009-05-30
> **SunnyRabbiera said:**
> right so lets break peoples arms to force them to use the same thing... feh

I'm not advocating that. I'm also aware that you'll never get every player to agree on a single standard. But you can't deny that having one standard package would cut down on the duplication of packaging effort that we currently have.

---

### Post by kasrawis on 2009-05-30
yes yes yes 100% agree if linux would have installer it would be popular than windows

---

### Post by lykwydchykyn on 2009-05-30
For goodness sakes, folks; it's not like they have to rewrite the whole program from scratch for every package format.  Has anyone here ever built a .deb from source?  Assuming you're packaging static binaries like I said before, the process of packaging them into multiple formats is something you can script.  

If it's profitable to port the thing to Linux in the first place, spending a couple extra hours on packaging isn't going to suddenly make it unprofitable.

---

### Post by b@sh_n3rd on 2009-05-30
> **unknownPoster said:**
> compiling from source is one of my favorite things about Linux...
Mine too :D
> **unknownPoster said:**
> if you get rid of it, you'll lose quite a few Linux Users, (Gentoo, Lunar, Arch + ABS, etc)
In other words, "loose quite alot of geeks" (like me :D)

---

### Post by gnomeuser on 2009-05-30
We have a near universal installer mechanism with GUIs for both popular DEs.. it's PackageKit. (why yes, after this years Google Summer of Code it will even support Gentoo' Portage - no kidding)

It elegantly handles the problem of installing and managing available software and provides the same tools across every distro. 

That is step one of the larger problem of having the same level of software packaged for every distro. Long term more unification would be nice but the stricter we make our packaging formats, the easier it will be to script a translation from say an ebuild to an rpm spec file. Till we hopefully one day arrive at something that is as strict and readable as a Conary recipe for all distros. There are many approaches, unification of Package Management tools is another but this is far less likely for now as people for some odd reason have very strong feelings about their legacy cr.. implementations. Also getting that many people to agree would take a serious amount of alcohol and doughnuts.

---

### Post by juancarlospaco on 2009-05-30
Theres one, called Zero Install.

---

### Post by jrusso2 on 2009-05-30
> **SunnyRabbiera said:**
> Feh they can use GTK as GTK right now seems more universally ready then QT4.
QT4 still needs work, but in the future it could become viable for everyone.
But people like you want there to only be 1 distro, 1 choice...
Linux is about diversity, its about time you learned that.
To force everyone to use the same linux would be no better then MS.

Who said one distro?  I don't see where I said that.  I have been using Linux for 13 years.  Give me a few great developers and I will show everyone a distro that can beat Windows and have commercial software made for it.

---

### Post by albinootje on 2009-05-30
> **jrusso2 said:**
> What's your point.  The only reason I mentioned Opera was that is was commercial?

I mentioned them to show the number of packages they have to make to be absurd.

I showed the Nomachine example because I think there's not an absurd amount of packages to create.

Here a MS-Windows download of one software package, with three choices (exe,zip,msi) :
[http://www.foxitsoftware.com/pdf/reader/download.php](http://www.foxitsoftware.com/pdf/reader/download.php)

And for the record, yesterday I wanted to try some MS-Windows software in Wine (Some pdf editor), and Wine can do msi packages, but this company gave an unusable msi package as only choice, which meant that it was completely unusable for me in Wine. (I could extract the separate files with "cabextract", but after that there was no way I could -try- to make it run with Wine.
My conclusion : more choice is nice.

---

### Post by albinootje on 2009-05-30
> **jrusso2 said:**
> Give me a few great developers and I will show everyone a distro that can beat Windows and have commercial software made for it.

There was the promising Corel Linux many years ago.
[http://en.wikipedia.org/wiki/Corel_Linux](http://en.wikipedia.org/wiki/Corel_Linux)
But see what happened :
[http://www.forbes.com/2000/10/03/1003corel.html](http://www.forbes.com/2000/10/03/1003corel.html)

But good luck with your Linux distribution.

---

### Post by lykwydchykyn on 2009-05-30
> **albinootje said:**
> There was the promising Corel Linux many years ago.
[http://en.wikipedia.org/wiki/Corel_Linux](http://en.wikipedia.org/wiki/Corel_Linux)
But see what happened :
[http://www.forbes.com/2000/10/03/1003corel.html](http://www.forbes.com/2000/10/03/1003corel.html)

But good luck with your Linux distribution.

Ironically, Corel Linux became Xandros, which (thanks to the eeePC) is one of the more widely used Linux distros out there.

---

