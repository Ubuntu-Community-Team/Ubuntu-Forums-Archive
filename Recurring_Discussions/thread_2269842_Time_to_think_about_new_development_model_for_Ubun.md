---
title: "Time to think about new development model for Ubuntu"
date: 2015-03-18
forum: Recurring Discussions
---

### Post by girtsz on 2015-03-18
There muststart discussions how Ubuntu to be sure that Ubuntu gest all latest updates and packages. Ubuntu development must merge together with Debian and use not modifying packages but use originals from Gnome, KDE, XFce, Kernel, GNU and so on.
Sometimes there are very old packages which are no more in development and newer versions contains strong bug fixes. (Gnome 3.10, 3.12...., other software)

;)

---

### Post by Bucky Ball on 2015-03-18
Please use default font and colour. Thanks.

---

### Post by QIII on 2015-03-18
Canonical chooses not to follow your model.

Except for some well-defined conditions, the versioning of included packages is not changed after release.

Canonical chooses to modify packages to suit Ubuntu because Ubuntu is Ubuntu, which is largely Debian-based but not Debian.

There are other distributions that may better suit your desires.  You are welcome to use one of them if that suits you.

---

### Post by grahammechanical on 2015-03-18
> [COLOR=#333333][FONT=Ubuntu Beta]The [/FONT][/COLOR][MOTU]("https://wiki.ubuntu.com/MOTU")[COLOR=#333333][FONT=Ubuntu Beta] team cares for the packages in universe and multiverse (which are comprised mostly of packages from the Debian archive) on a best-effort basis, as there are a large number of packages relative to the resources of the team. Therefore, _a vast majority of these packages are used unchanged from Debian_, rebuilt in an Ubuntu build environment, and do not receive personal attention from an Ubuntu developer.[/FONT][/COLOR]

> [COLOR=#333333][FONT=Ubuntu Beta]Most source packages in all Ubuntu components (about 4 in 5 at the time of this writing) _are copied unmodified from Debian_, but other sources include[/FONT][/COLOR][apt-get.org]("http://www.apt-get.org/")[COLOR=#333333][FONT=Ubuntu Beta], directly from organisations such as Blackdown and WineHQ, software which has been packaged by Ubuntu developers, and packages created specifically for Ubuntu.[/FONT][/COLOR]

[https://wiki.ubuntu.com/Ubuntu/ForDebianDevelopers](https://wiki.ubuntu.com/Ubuntu/ForDebianDevelopers)

> [COLOR=#333333][FONT=Ubuntu Beta]In the _beginning of each Ubuntu development cycle_ the packages in Ubuntu _are updated to those in Debian unstable_. However, because Ubuntu is not the[/FONT][/COLOR]*same*[COLOR=#333333][FONT=Ubuntu Beta] as Debian, some of the packages need to be modified to work in Ubuntu. [/FONT][/COLOR]

> [COLOR=#333333][FONT=Ubuntu Beta]At the _start of the development cycle a decision has to be_ made with regard to these Ubuntu-versioned packages. Of course if the Debian version hasn't changed since the last Ubuntu release then nothing needs to be changed. However, if there is a newer version of the package in Debian then one of two things should happen. If all of the reasons that the Ubuntu version existed (bug fixes, dependencies, etc.) are fixed in the new Debian package (or if the residual difference is sufficiently trivial _it's not worth the maintenance overhead of merging) then we can just take the Debian package directly. This is called a _[/FONT][/COLOR]_**sync**_[COLOR=#333333][FONT=Ubuntu Beta]_._ However, if the new Debian version has the same issues that caused the Ubuntu version to be made, then those changes need to be applied to the new Debian version. This is called [/FONT][/COLOR]**merging**[COLOR=#333333][FONT=Ubuntu Beta].[/FONT][/COLOR]

[https://wiki.ubuntu.com/UbuntuDevelopment/Merging](https://wiki.ubuntu.com/UbuntuDevelopment/Merging)

[https://wiki.ubuntu.com/UbuntuDevelopment/Merging](https://wiki.ubuntu.com/UbuntuDevelopment/Merging)

It seems to me that a lot of thought and effort has gone into how Ubuntu is developed. I am willing to trust those directly involved in Ubuntu development to be best placed to know what works well and what needs changing.

I have benefited for 8 years from using Ubuntu. I am a happy bunny.

Regards.

EDIT: Oh, I forgot. You mentioned the kernel.

> [COLOR=#333333][FONT=Ubuntu Beta]The Ubuntu Kernel Team aims to provide the highest quality Linux kernel for Ubuntu and the Ubuntu family of products. The Linux Kernel is the core of Ubuntu and is the rock upon which we base all other Ubuntu technology,[/FONT][/COLOR]

[https://wiki.ubuntu.com/KernelTeam](https://wiki.ubuntu.com/KernelTeam)

> [COLOR=#333333][FONT=UbuntuBeta]Our Vivid kernel remains based on v3.19.1 and we uploaded a[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuBeta]kernel last week.[/FONT][/COLOR]

[http://voices.canonical.com/kernelteam/](http://voices.canonical.com/kernelteam/)

---

### Post by cariboo on 2015-03-18
To add to QIII said, Ubuntu is designed to be easy to use. For the most part users are happy to get things done, and not worry about the latest and greatest packages, as we've seen here on the Forums, many users don't even update unless they really have to.

Ubuntu isn't designed for computer enthusiasts. If you feel the need to have the latest packages available, either resort to using ppa's, or move on to another distribution.

BTW, this subject comes up so often that I'd call it a recurring discussion, Moved to Recurring.

---

### Post by ian-weisser on 2015-03-19
> **girtsz said:**
> There muststart discussions how Ubuntu to be sure that Ubuntu gest all latest updates and packages.
Such discussions are already ongoing in the developer community, and have been for 10 years.
There are many thousands of us in the Ubuntu communities, and more than a few have thought about this, and more than a few are working on it. (Hello Snappy and Click Packages)

> **girtsz said:**
> Ubuntu development must merge together with Debian and use not modifying packages but use originals from Gnome, KDE, XFce, Kernel, GNU and so on.
Good news - Ubuntu already has a policy to keep the differences with Debian as small as possible, and to push those changes upstream to Debian and Gnome and KDE and XFCE and Kernel and GNU and so on so they can incorporate patches that grew from Ubuntu's very large user base and community.

'Merging together' implies that there must be some benefit, and that the groups involved *want* to merge. You may see it clearly, but I don't.

> **girtsz said:**
> Sometimes there are very old packages which are no more in development and newer versions contains strong bug fixes. (Gnome 3.10, 3.12...., other software)
Even more good news - Ubuntu has an active process in place to locate that newer software quickly, import it into the next release of Ubuntu, integrate it with other software in the Ubuntu repositories, test it for compatibility with other Ubuntu software, and push the discovered bugs (and patches) upstream. And to do all this within --usually-- a few weeks.

By the way, the Ubuntu Gnome team would certainly love your help to test and integrate the next Gnome update, which will be released in 5 weeks.

---

