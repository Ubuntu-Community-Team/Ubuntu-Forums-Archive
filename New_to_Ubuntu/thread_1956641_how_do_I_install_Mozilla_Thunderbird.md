---
title: "how do I install Mozilla Thunderbird?"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by TooFreppaT on 2012-04-11
using ubuntu 10.10 64-bit

went to [http://www.mozilla.org/en-US/thunderbird/](http://www.mozilla.org/en-US/thunderbird/)

downloaded file: thunderbird-11.0.1.tar.bz2

double-clicking on it just opens it up in Archive Manager... open the folder "thunderbird" - no idea what to do!

¿what do I do now?

---

### Post by daslinkard on 2012-04-11
Quick question....asking to learn here....but, was it not available for you to download in the Ubuntu Software Center?

---

### Post by ld114 on 2012-04-11
If you want to install the latest version of Thunderbird on Ubuntu 10.10, then here is a link:

[http://www.liberiangeek.net/2011/03/install-latest-version-thunderbird-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2011/03/install-latest-version-thunderbird-ubuntu-10-10-maverick-meerkat/)

However this should come with a health warning, as the version you install may not have been fully tested. Best advice is to start with the version in Ubuntu Software Centre, and if that is not what you want, then try the other option.

---

### Post by kc1di on 2012-04-11
First is there any reason that you don't want to install it using Synaptic?

But you can install the latest sable by following this page's advice.

[http://ubuntu-install.blogspot.com/2011/06/how-to-install-thunderbird-5-on-ubuntu.html]("http://ubuntu-install.blogspot.com/2011/06/how-to-install-thunderbird-5-on-ubuntu.html")

Simply copy and paste the command one at a time in a terminal.

If you want to use the file you downloaded you'll have to unpack it 
and make links to the proper files.  not impossible but more involved than needed. 
you can unpack in place in in your home folder and run it from there. but it will not be integrated with ubuntu that way.

---

### Post by Peripheral Visionary on 2012-04-11
In Windows we were accustomed to finding software on some web site and downloading some "setup.exe" file.

But in Linux, the most common (and by far the safest) way of installing software is from the repositories. The 'Buntu's enjoy some of the biggest and best repositories in the Linux world!

Use the Ubuntu Software Center or the Synaptic Package Manager. It's as easy as three clicks of a mouse to find, choose, and install Thunderbird and lots of other awesome software.

---

### Post by daslinkard on 2012-04-12
Could not have said that last part better myself.  I understand that some people want to be able to use the CLI to be able to download some things, etc., but if it's in the repository, that is your friend....simply get it from there.

Also, we learn that Windows teaches bad habits....bad habits such that software should cost money....Gosh do I love FOSS!
[]("http://ubuntuforums.org/member.php?u=1570698")

---

### Post by alphacrucis2 on 2012-04-12
The commands specified by the site linked by a previous poster are adding the official Mozilla stable PPA. I would say that is a lot less likely to cause trouble than your typical PPA. In any case PPA's are likely to give less trouble than downloading random deb files that may not be built for the specific distro/version.


FYI

[https://launchpad.net/~mozillateam](https://launchpad.net/~mozillateam)

and

[https://wiki.ubuntu.com/MozillaTeam](https://wiki.ubuntu.com/MozillaTeam)

They provide ppa's for FF & T'bird in stable, next and daily. Next is sort of beta and daily is alpha releases as I understand it.

---

### Post by mastablasta on 2012-04-12
> **Peripheral Visionary said:**
> In Windows we were accustomed to finding software on some web site and downloading some "setup.exe" file.
 
But in Linux, the most common (and by far the safest) way of installing software is from the repositories. The 'Buntu's enjoy some of the biggest and best repositories in the Linux world!
 
Use the Ubuntu Software Center or the Synaptic Package Manager. It's as easy as three clicks of a mouse to find, choose, and install Thunderbird and lots of other awesome software.
 
if you have 10.04 all software in repositories would be out of date. If you installf or example scribus, it will be the old version, while the windows computer will likely have new version. they are not compatible, so often either PPA is needed, manual compile& install (tar, deb) or you would need to upgrade to the next release whenever possible.
 
LTS software has mostly only the security pacthes. but various bugs that are fixed in higher software version or necessary new features would not be there.
 
so i am not sure installing form repositories is actually a super good method. it is safe, but only if you can do with old software. just take for example Openoffice. it's relatively good, but has a number of issues (MS office compatibility, Calc row numbers...) that were fixed with latest libre office releases. you won't get those unless you use the unsafe PPA method or deb form the website.

---

