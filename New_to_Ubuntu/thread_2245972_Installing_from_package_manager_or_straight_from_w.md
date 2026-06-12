---
title: "Installing from package manager or straight from website?"
date: 2014-09-27
forum: New to Ubuntu
---

### Post by garycheng12 on 2014-09-27
I know a difference between installing from each (advantages and disadvantages). From the package manager: there is better compatibility with your distro (what does this mean?). From the website: it is guaranteed to be the latest version. How much does it matter that the application "works better" with your distro from the package manager as opposed to directly from the website? I hate the idea that someone tinkered with an application to somehow make it work better with a distro (problems with the functionality of the application could be compromised, stability issues, etc.). It seems to make more sense that an application from a website has a version with Linux that is [I]already designed to work great with Linux.

[/I]After answering these questions, I would like to know who actually makes the applications from the website to the package manager. How can I be sure it is up-to-date to the original application? There is a possibility that I could be having problems with an application down the road and that is the result of the package not being able to catch up to the latest application version from the website.

I am likely going to have applications installed from the website because it cannot be found in a package manager anyway so if it's better to install applications from the website instead then then I might as well get used to it. I am considering removing the default Firefox that comes with Kubuntu and installing it directly from the website instead.

Thanks!

---

### Post by ian-weisser on 2014-09-27
You can install anything you want from any source you want. It's your system.

I find it more difficult to help support manually-installed software.
As long as you don't need support from me, manually install whatever you want.

> I would like to know who actually makes the applications from the website to the package manager.
Volunteer packages and package maintainers do that.

> How can I be sure it is up-to-date to the original application?
Use the version number or release number. The same way you tell two different versions of _any_ software apart.

---

### Post by whitesmith on 2014-09-27
Actually the version on the developer's webpage may be more current, but the version in the repos has been subjected to more rigorous testing and so is more likely to play nice with other components of the repo.

---

### Post by garycheng12 on 2014-09-27
I'm not sure I know what "play nice with other components of the repo" mean. If an application has a version for Linux, what makes a package from a package manager of the same application more compatible with the distro? Practically speaking, can a power user install all applications without the use of a package manager and directly from the website and still achieve reasonable stability and usability? I'm asking these questions more to learn about how Linux works rather than be nit-picky.

---

### Post by whitesmith on 2014-09-27
Changes are key. If some part of an app is fixed/updated in a point-release, then it might not be 100% compatible with other apps in the repo on your machine, or with the OS for that matter. This is one reason why we experience bugs that seem to have a life of their own, appearing and disappearing on an unpredictable basis. I've reduced, but not eliminated, them by getting packages from the repos, even if it puts me a little behind. Better behind and up than current and down.

---

### Post by garycheng12 on 2014-09-27
Thank you for the informative replies.

---

### Post by ian-weisser on 2014-09-27
> **garycheng12 said:**
> I'm not sure I know what "play nice with other components of the repo" mean. If an application has a version for Linux, what makes a package from a package manager of the same application more compatible with the distro?

Let's illustrate with an example.

You want to install applications Foo and Bar.
Both rely upon libbaz...but upon different *versions* of libbaz (libbaz1.1 and libbaz1.2). And, unfortunately, the libbaz project changes their feature set a lot between releases.

Now you have a problem to test and perhaps solve. Maybe both Foo and Bar are compatible with libbaz 1.1 after all. Or libbaz1.2. Or you can install both versions of libbaz, and do a bunch of technical pokery to make both work on the same system,  for each application to refer to the correct lib. Or you can use an older version of Foo that is compatible with 1.1. No firm answers - you must test each solution yourself to determine the right one for your needs.

If you are not a power user, this is an awful way to install software - never knowing if it's going to work, and required to do all that complex diagnosis yourself when it doesn't work. That's quite a learning curve.

Package management is another way to solve the problem. The distro uses libbaz 1.1, and an older version of Foo compatible with 1.1, and a newer version of Bar compatible with 1.1. The packages install with one click, and it all works. Both Foo and Bar have been compiled using 1.1, and tested that way. When Foo bumps up to 1.2 compatibility, the maintainer updates the packages and everyone benefits. When a bug gets reported, the package list tells the bug triager everything they need to know to duplicate the environment.

Power users can complain that packaged Foo isn't the latest and greatest, but they can still install libbaz1.2 and Foo manually if they wish. Or, if they don't want to invest that much time, they can live with the older Foo until the next release of Ubuntu. They have a non-exclusive choice.

---

### Post by buzzingrobot on 2014-09-27
Remember, there is no such thing as "Linux".  There are several hundred, or more, different packaging efforts called 'distributions'. 

One very big reason few developers do not build packages for a variety of distributions is that it's too much work:  They would need to maintain (at least VM) instances of each distribution and its variouos versions, very likely modify their code to make it compatible with different distributions, and then build and package each verson for each distribution they wanted to target. .  Much simpler to release source code and let each distribution build and package it for binary distribution.  Distros would build their own packages from source, regardless, because they're the distributors, not the developer.

(For example, packages intended to run on Unity often need to be compiled and linked against specific Unity libraries. But, they don't if you're targeting Fedora, but there you do need to decide if you want to build for the current release, the last supported release, the next forthcoming release, etc. It's the same for the other distros.)

The same applies to updates and bug fixes:  Developer releases source and distributions build, package, and distribute.  Users, then, only need to look to their distribution for patches and updates, not to hundreds of individual developers, who are pretty unlikely to have any idea at all about who is using their software, much less make an effort to tell them it's time to update.(Case in point:  Do you know the identity of the developer(s) responsible for Bash and how to get the patches for the current Bash bugs?)

Distributions ave typically woefully short of people and resources.  They have better things to do than make random changes to source code.

(Note:  Server space and bandwidth isn't free. Popular software could easily generate substantial costs for a developer who decided to self-host the binaries.  Few FOSS developers make any money from their efforts, so that is not an atractive prospect.)

---

### Post by garycheng12 on 2014-09-27
Will installing applications from websites (not package manager) cause problems in the library, dependencies, or be more insecure? From what I've learned, it takes time for Ubuntu (Kubuntu repositories in my case) to package, test, and optimize an application for the distro. However, it is still recommended to use the out-of-date package from these repositories because they have been through all that and stability is guaranteed. I am mainly a Windows user and I prefer applications that I use on both operating system to be the same, up-to-date version that is available on the website--it would be impractical if the one application on Windows has a new feature that is not yet available on the Linux counterpart because it still need to be re-packaged.

Also, who are the people that are re-packaging the packages and how behind are packages compared to the up-to-date versions in general? If I were to stay on Kubuntu for say 10 years (past LTS) would there still be people packaging?

---

### Post by Iowan on 2014-09-27
Duplicate:
[http://ubuntuforums.org/showthread.php?t=2245972](http://ubuntuforums.org/showthread.php?t=2245972)
Please stop creating duplicate threads. From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):> Do not cross post, or post the same thing in multiple locations.

---

### Post by QIII on 2014-09-27
LOL!

Simultaneous Staff Action.

Now merged...

---

### Post by JKyleOKC on 2014-09-27
> **garycheng12 said:**
> Will installing applications from websites (not package manager) cause problems in the library, dependencies, or be more insecure?
Yes to all three items. The non-managed application may require libraries that do not exist in your system, may have unsatisfied dependencies on other programs, and will definitely never get any automatic security updates. While managed applications always lag a bit (often, quite a bit) behind the latest bleeding edge, they will have been tested, have all dependencies accounted for, and get automatic security updates when needed.
> **garycheng12 said:**
> From what I've learned, it takes time for Ubuntu (Kubuntu repositories in my case) to package, test, and optimize an application for the distro. However, it is still recommended to use the out-of-date package from these repositories because they have been through all that and stability is guaranteed. I am mainly a Windows user and I prefer applications that I use on both operating system to be the same, up-to-date version that is available on the website--it would be impractical if the one application on Windows has a new feature that is not yet available on the Linux counterpart because it still need to be re-packaged.If the new version doesn't work, is that more practical? Far too many applications these days seem to bring out new versions simply to boost revenue or add useless bells and whistles. Best productivity usually seems to result from following the rule "if it ain't broke, don't fix it."

> **garycheng12 said:**
> Also, who are the people that are re-packaging the packages and how behind are packages compared to the up-to-date versions in general? If I were to stay on Kubuntu for say 10 years (past LTS) would there still be people packaging?Much of the packaging is done by volunteers, but the testing is overseen by the folk whose reputations depend on guaranteeing good results. Some distributions provide what is called "rolling releases" that can vary from being only hours behind a new version, up to months. The *buntu flavors operate on strictly timed basis, with new releases every 6 months and "long term support" releases every two years. An LTS release, then, can be up to 23 months out of date in some areas -- but that gives time for most all of its bugs to be found and fixed. Those of us who depend on reliable systems often wait six months after release of an LTS version before installing it, to allow for the majority of serious problems to be located and corrected.

Security updates get released immediately, as soon as they pass testing. Others, including cosmetic features and added capabilities, must wait for the next full release.

Support for LTS versions currently continues for 5 years. After that time, no updates at all will be available, so if you stay on that version for 5 more years, it won't be getting any security fixes. And nobody will be packaging its components.

---

### Post by vasa1 on 2014-09-27
> **JKyleOKC said:**
> ... The non-managed application ... will definitely never get any automatic security updates. ...
Just a minor point: OP mentioned Firefox. Installing Firefox direct from Mozilla results in a browser that is automatically updated. Same with Dropbox.

---

