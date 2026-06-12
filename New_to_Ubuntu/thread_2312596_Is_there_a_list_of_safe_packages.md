---
title: "Is there a list of safe packages?"
date: 2016-02-05
forum: New to Ubuntu
---

### Post by helm10101 on 2016-02-05
Hello,

many times when I encounter a problem I go online to search for a solution, and truly I find it quickly. (Ubuntu seem to have a lot of support online)
I just noticed that many of the solutions include installing packages, for example the last one, dconf-editor, so I find myself installing many packages.
Although Linux, and Ubuntu in particular is less prone to viruses and malwares (from what I understood), can't there be some packages that I install that contain a malware/virus?

Is there a place I can search my package name and it tells me it's safe to install?
I think that if it does not exist, it's a good thing to have, an official (or maybe unofficial) documentation of known packages?

Or, since I am new here, I just wrote a lot of nonsense and you can enlighten me?

Thanks :)

---

### Post by buzzingrobot on 2016-02-05
I don't believe any such list exists. All packages -- there are tens of thousands -- would need to be constantly re-tested against new threats.

In general, turn first for packages to Ubuntu's official repositories.  

Turn second to PPA's hosted on launchpad.net. (Unofficial and not supported, meaning you depend on that developer for updates, fixes, security patches, continuing compatibility with Ubuntu updates, etc. Each PPA has a page on launchpad.et.  Be sure to check it for info, warnings, etc.)

Turn third to packages hosted on sites that Google turns up.  Think very carefully, though. I don't recommend this.

Linux uses a shared library scheme.  That means that a library that another package depends on -- a dependency -- is installed only once, when the first package that requires it is installed.

This eliminates a considerable amount of the duplication that occurs when developers are free to include all dependencies in their software's installation archive. You can end up with multiple copies of the same library in multiple locations in the file system. Security issues happen, too, because you rely on each developer to provide security patches.  Not only must that happen, the user must know a patch is available, must install it, and must repeat that exercise for every piece of software that's been installed in that fashion, even if they all use an identical dependency.

In Ubuntu, or any other properly run distribution, on the other hand, security updates are acquired from developers -- upstream -- built and packaged and placed on the repos.  When a user updates a system, they get the updates.  

A "package manager" in Ubuntu runs behind the scenes to track what packages have been installed (or removed).  It knows where to download packages (from a list of sources maintained in /etc/apt, initially containing only official Ubuntu repositories.) The Ubuntu Software Center, Synaptic, apt and apt-get are all front-ends for that package manager. 

One dependency very often has its own dependencies, and so on, until the chain ends. Which ones are actually downloaded and installed depends on what packages are already installed. When you saw packages being installed as dependencies to dconf-editor, that was normal and safe.

---

### Post by matt_symes on 2016-02-05
Hi

> **helm10101 said:**
> Hello,

many times when I encounter a problem I go online to search for a solution, and truly I find it quickly. (Ubuntu seem to have a lot of support online)
I just noticed that many of the solutions include installing packages, for example the last one, dconf-editor, so I find myself installing many packages.
Although Linux, and Ubuntu in particular is less prone to viruses and malwares (from what I understood), can't there be some packages that I install that contain a malware/virus?

Is there a place I can search my package name and it tells me it's safe to install?
I think that if it does not exist, it's a good thing to have, an official (or maybe unofficial) documentation of known packages?

Or, since I am new here, I just wrote a lot of nonsense and you can enlighten me?

Thanks :)

Any package you install from the standard repositories will be safe to install. It is maintained by canonical and is a trusted source.

When you start veering away from that standard repositories, you start increasing the risk.

PPAs are *generally* safe to use but they are untrusted. This means that canonical are not in control of them and did not build the software.

Moving away from PPAs brings another level of risk. Installing arbitrary debs downloaded from the Internet can cause problems as there is a slight risk they may contain malware.

There have been examples in the past of malware in themes downloaded from the Internet.

Here's an example

[http://www.omgubuntu.co.uk/2009/12/yet-more-malware-found-on-gnome-look](http://www.omgubuntu.co.uk/2009/12/yet-more-malware-found-on-gnome-look)

Whenever you install software, the writer of that software has root on your system. This goes for most general purpose operating systems. With that level of privilege the software can do what it likes.

The key is to look for trusted sources and Canonical's standard repositories are about as safe as you can get.

Kind regards

---

### Post by HermanAB on 2016-02-05
In general, everything in the repos are OK.  With everything not in the repos, you are on your own.

---

### Post by helm10101 on 2016-02-05
Thank you!
So if I install using the apt it will only install from the official repos? (If I didn't change any settings?)

---

### Post by 1clue on 2016-02-05
This is a really good set of questions, you're thinking in the right way.

[http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/) has the currently available list of vulnerabilities for the Ubuntu repository.

This list needs to be tempered with some understanding of how it works.  Bear with me.
[LIST=1]
[*]Software is written or modified.
[LIST=1]
[*]Some number of security or stability issues exist from this moment, but we don't know how many.
[*]Some of the software comes from Canonical, which is the company financing/hosting Ubuntu.  Most comes from other sources, which we call "upstream."
[/LIST]

[*]Software is released to us, effectively at the moment we install or update our Linux box.
[*]Somebody (white hat, black hat or gray hat) discovers a bug.
[LIST=1]
[*]White hats are the good guys.
[LIST=1]
[*]Security professionals, Distro managers, Users, Developers
[*]They report the bug to the development team(s) and/or to the people who manage the vulnerability databases worldwide.
[*]The recipients of the bug report test the issue, contemplate severity and attach a priority to the fix.
[*]In some cases the bug is in the database before it becomes publicly visible. This is to enable the software people time to fix the bug.
[*]The developer(s) fix the bug and test it.
[*]The development team pushes out a new release, but not always immediately.  New releases are given when enough important changes have been made to the application.
[*]The downstream people (the distro managers) receive the code and make their own build, and test it.
[*]The patch is possibly added to the update list, or the bug goes back to the developers as unfixed.
[*]Some time later (maybe weeks) you get around to updating your system and your software is fixed.
[/LIST]

[*]Black hats are the bad guys.
[LIST=1]
[*]They find a way to exploit the vulnerability and maybe tell their black hat buddies.
[*]They distribute the exploit as malware, or attack it from remote servers, or whatever they feel appropriate.
[*]They wind up with credit card data, or whatever they're after.
[/LIST]

[*]Gray hats are the people who don't care, or rather don't do anything about it.
[LIST=1]
[*]They bitch and moan, but don't tell anyone.
[/LIST]
[/LIST]
[/LIST]

Note that even though your software may be fixed, the fix will NOT contain any way to repair damage already done by the exploit.

---

### Post by grahammechanical on 2016-02-05
This might be of interest

[https://wiki.ubuntu.com/AppReviewBoard](https://wiki.ubuntu.com/AppReviewBoard)

[https://wiki.ubuntu.com/AppReviewBoard/Review](https://wiki.ubuntu.com/AppReviewBoard/Review)

> Check the app for the following criteria, noting each as Pass/Fail, and including any comments. 

 
[h=4]Content[/h] 
[LIST]
[*]Content is suitable under the terms of the Ubuntu Code Of Conduct 
[*]Submissions should be applications, not stand-alone documentation or media (image bundles, fonts, movies). 
[*]Apps should not be forks of existing applications in the Ubuntu archive (main/universe/etc). 
[*]Apps should be useful or interesting to a general audience. 
[*]No  other software can depend on the application being submitted (e.g.  development libraries should be submitted to main/universe or upstream  to Debian instead). 
[*]Applications must be Free/Libre/Open Source software. We follow the [Ubuntu Licensing Policy]("http://people.canonical.com/%7Ecjwatson/ubuntu-policy/policy.html/ch-archive.html#s-ulp"). 


[*]Applications  must be able to be built with tools & libraries in the Ubuntu  archive. Apps may bundle additional libraries they depend on, but may  not include new versions of already packaged libraries. 

[/LIST]
 
[h=4]Running[/h] 
[LIST]
[*]Application runs correctly 
[*]Major features operate as expected 
[*]Does not perform any malicious actions 
[/LIST]
 
[h=4]Packaging[/h] 
[LIST]
[*]The application is well packaged using the Debian packaging system 
[*]All correct dependencies are met 
[*]Application installs cleanly 
[*]Application can be removed cleanly 
[*]Includes suitable copyright and licensing content 
[*]Application integrates into the desktop, with appropriate Launcher or menu entries 
[/LIST]
If the app fails on any points, the reviewer will contact the submitter with suggestions for changes.

Regards.

---

### Post by sonicwind on 2016-02-05
This is some really good info. Thanks helm10101 for starting this thread and the rest of you for providing great answers.

I was kind of alarmed looking at 1clue's link. That seems like a lot of vulnerabilities (I narrowed it to 14.04 LTS) just in 2016 so far! I guess that's a good thing as these things are getting discovered and fixed.[**[COLOR=#000000][/COLOR]**[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=2019034")

---

### Post by helm10101 on 2016-02-05
Really thank you guys for the detailed answers and for taking your time to explain so well.
It was really good ( and fun ) to read these
sonicwind you're welcome :D

So that leaves me with my question: everything I download using Software Center / the command in terminal "sudo apt-get install" will be directly from the official repos? thus I should care less? (unless I added a PPA manually before)

---

### Post by 1clue on 2016-02-05
People need to understand the process involved in developing software and fixing bugs.  If you look at [https://nvd.nist.gov/](https://nvd.nist.gov/) you'll be able to search on pretty much all software, including Windows.  Be careful, I lost about 3 days the first time I saw it, it can suck you in.

Those vulnerabilities may have fixes out there, they may or may not be applied to your system already depending on how recently you updated.

Most important of all is the understanding that ALL software above a certain size has bugs or vulnerabilities, even if none are known. And when they show up in the database, it means that the white hat guys know about it and have had time to test it.  The black hat guys may have known about it for years, may have already developed an exploit for it, may have already stolen a terabyte of information using it before the white hats even got a clue.

I'm not trying to be a doom-sayer, but this is not a pure Linux thing. It is true for all software, and you could even apply it to mechanical devices.  Think of early fortifications and weaponry, they may have been unstoppable 1000 years ago but today the same thing is not so fantastic, because we know more about the weaknesses of a device or technique.

It's best to look at security as a moving target, one that you need to constantly pay attention to and research in order to stay relatively safe.

---

### Post by matt_symes on 2016-02-05
Hi

> **helm10101 said:**
> So that leaves me with my question: everything I download using Software Center / the command in terminal "sudo apt-get install" will be directly from the official repos? thus I should care less? (unless I added a PPA manually before)

Most software may contain vulnerabilities including software in the repositories. This also includes Windows, Mac, Android, router firmware, other firmware....

That you have to deal with and hope the vulnerabilities get found and fixed. There are steps you can take to mitigate these risk.

This is different than whether software contains coded malware though, such as a virus scanner may look for. 

Software you download from the Ubuntu repositories should be fine. That not to say it may not have vulnerabilities but it should not contain malware.

I would not worry. Just take the usual incremental backup and practice safe browsing. 

The browser and other applications software (along with social engineering) is now the main vector for malware for most desktop users.

BTW: I've never had any problems when installing software from a PPA that were due to malware in that PPA.

Kind regards

---

### Post by 1clue on 2016-02-05
> **helm10101 said:**
> ...So that leaves me with my question: everything I download using Software Center / the command in terminal "sudo apt-get install" will be directly from the official repos? thus I should care less? (unless I added a PPA manually before)

Software distributed in the official repositories is usually pretty safe.  It's important to pay attention to updates and the news related to software (see my usn link above) and to apply that news to your specific software and the way you use that software in your business.

You can be certain that EVERY medium-to-large business with an IT team has somebody watching one or more of these vulnerability databases every day for exploits in software they use.  Many small companies do too, and even some individuals (me) do so for their homes.

The rule of thumb is this:  When you install software, think about where that software comes from and the stake that vendor has in having clean software.  Think about everyone who touches that software from its original authoring to the web site/software repository/whatever to your computer.  The more hands it passes through, the more likely somebody is to have altered it, or the more chances that some third party has broken in and altered it without the site owner's knowledge.

Software coming from vendors with a reputation and possible money at stake (Canonical/Ubuntu) is probably pretty good.  Meaning that the software was probably compiled from good sources upstream, and that few if any bugs/exploits have been introduced by the vendor.  You may not know it, but the tools we use to install/update software in Ubuntu have a checksum created by the people who have built, tested and certified the software.  When you pull it from the repository that checksum is compared to the checksum of the downloaded software, and if it doesn't match then the software is not installed.

---

