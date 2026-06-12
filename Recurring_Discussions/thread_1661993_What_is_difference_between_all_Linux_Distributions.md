---
title: "What is difference between all Linux Distributions"
date: 2011-01-07
forum: Recurring Discussions
---

### Post by asifnaz on 2011-01-07
I am relatively new Linux user (using for 1 year ) I have used many distros in small time ...like ubuntu , fedora , puppy linux , dsl , slitaz , Debian , mandriva , linux mint , pc linux os , and some other as well .

I dont see any real difference among them all . Despite cosmetic differences and weight (light wight , mediam weight etc ..)

Applications are almost the same .

same system under the hood IMHO ...

any real differences ..???

---

### Post by Simian Man on 2011-01-07
The versions of the programs available, which programs are installed by default and the tools used to install new programs.  You are right that the differences are mostly minor.

---

### Post by pbpersson on 2011-01-07
All Linux distributions are based on the same kernel and they all use the same applications.  However, that should be the only similarity.

Some use the RPM (Redhat Package Manager) package system and some use the DEB (Debian) system.

Ubuntu is produced using the Debian system and in my opinion the method of resolving dependencies and conflicts is superior - but it has been years since I looked at Fedora, they might be better now.

Each distribution in theory customizes the kernel for the blend of applications they package with the distro to make it more stable.  There is also some customization of themes and configuration utilities.

However, you are correct in your observation that they are all very similar.

I have tried SUSE, Fedora, Mandriva, and Ubuntu and at the time found Ubuntu to be much easier to use and customize.

---

### Post by Simian Man on 2011-01-07
> **pbpersson said:**
> Ubuntu is produced using the Debian system and in my opinion the method of resolving dependencies and conflicts is superior - but it has been years since I looked at Fedora, they might be better now.

I have tried SUSE, Fedora, Mandriva, and Ubuntu and at the time found Ubuntu to be much easier to use and customize.
The "best" distro is always the one you know best.  I can assure you that RPM works great and Ubuntu is not especially easy to customize.  Customization is usually a function of the desktop, not the distro.

> **3602 said:**
> It seems like SuSE boots slower.
One user of Mandriva told me that "it is easier to hack into other people's routers" and he claims to be controlling a zombie network (of routers) in a radius of 9 kilometers.
Another user of "METI Linux" said it is more powerful (unspecific as to how) than Ubuntu and Kubuntu.
Also, there's this:
[image removed]

None of that is correct - especially the "comic".

---

### Post by Spice Weasel on 2011-01-07
[LIST]
[*]Different applications installed by default.
[*]Different init systems (this won't affect most desktop users)
[*]Different package methods and frontends (but with most distribtions both RPM (Yum/APT) and Dpkg (APT/Aptitude) are available)
[*]Different release schedules.
[/LIST]

That is about it, really.

> Some use the RPM (Redhat Package Manager) package system and some use the DEB (Debian) system.

RPM is now no longer controlled by Red Hat and is independent. RPM now stands for RPM Package Manager.

---

### Post by RiceMonster on 2011-01-07
Breakdown of that comic:

"Ubuntu is used by normal people. Only stupid/crazy people use something else".

---

### Post by pbpersson on 2011-01-07
> **Simian Man said:**
> The "best" distro is always the one you know best.  I can assure you that RPM works great and Ubuntu is not especially easy to customize.  Customization is usually a function of the desktop, not the distro.


I tried Fedora but regardless of what I was trying to install:
Java Development Kit
My SQL server
NetBeans
Eclipse

I remember getting a screen of twenty different problems with a message, "Before you continue, you must resolve these package conflicts/dependencies"

That was a huge turn off and have never had that happen with Ubuntu.

Fedora LOOKED really nice but I was not able to use it.  This was probably three years ago and hopefully this has been fixed.

When I sit down at the computer my time is very limited.  I want to quickly install packages and use them - I cannot spend hours fooling around with package dependencies.  Ubuntu has allowed me to be more productive than other distros I have tried.  When I try to install something it says "20 other packages will be upgraded" and I don't need to know what it is doing behind the scenes, it takes care of all the details for me.  :)

---

### Post by Simian Man on 2011-01-07
> **pbpersson said:**
> I tried Fedora but regardless of what I was trying to install:
Java Development Kit
My SQL server
NetBeans
Eclipse

I remember getting a screen of twenty different problems with a message, "Before you continue, you must resolve these package conflicts/dependencies"

That was a huge turn off and have never had that happen with Ubuntu.

Fedora LOOKED really nice but I was not able to use it.  This was probably three years ago and hopefully this has been fixed.

```

yum install java-1.6.0-openjdk-devel mysql-server netbeans eclipse-jdt
Loaded plugins: langpacks, presto, refresh-packagekit
Adding en_US to language list
Setting up Install Process
**Package mysql-server-5.1.52-1.fc14.x86_64 already installed and latest version**
Resolving Dependencies
<dependency stuff removed>
**Dependencies Resolved**

================================================================================
 Package                     Arch    Version                     Repository Size
================================================================================
Installing:
 eclipse-jdt                 x86_64  1:3.6.1-6.1.fc14            updates   23 M
 java-1.6.0-openjdk-devel    x86_64  1:1.6.0.0-49.1.9.3.fc14     updates  8.5 M
 netbeans                    noarch  6.9-2.fc14                  fedora   1.2 M
Installing for dependencies:
<a bunch of java dependencies>
Is this ok [y/N]:

```
Seems fine here, and I have used Fedora since Fedora 7 - nearly four years - without seeing anything like that when installing packages from the repos.

> **pbpersson said:**
> When I try to install something it says "20 other packages will be upgraded" and I don't need to know what it is doing behind the scenes, it takes care of all the details for me.  :)
Yeah because that's *how package managers work*.  Why do people who have clearly never used anything but apt for more than a short while feel they are in a position to say it's the only one that works?  Seriously WTF?

---

### Post by pbpersson on 2011-01-07
> **Simian Man said:**
> 

Yeah because that's *how package managers work*.  Why do people who have clearly never used anything but apt for more than a short while feel they are in a position to say it's the only one that works?  Seriously WTF?

I can only tell you what happened.  In Fedora when I tried to install things I got screens full of errors.  When I went to Ubuntu everything installed just fine.  Perhaps Fedora just had a bad day, I have no idea.  I am certain I was using Synaptic in Fedora as that is what I always use.

---

### Post by RiceMonster on 2011-01-07
> **pbpersson said:**
> I can only tell you what happened.  In Fedora when I tried to install things I got screens full of errors.  When I went to Ubuntu everything installed just fine.  Perhaps Fedora just had a bad day, I have no idea.  I am certain I was using Synaptic in Fedora as that is what I always use.

Synaptic in Fedora? What? Synaptic is an apt fontend.

---

### Post by Simian Man on 2011-01-07
> **pbpersson said:**
> I am certain I was using Synaptic in Fedora as that is what I always use.

LOL that would be it.  That's why I said "The best distro is always the one you know best".  I know not to use synaptic in Fedora just like you know not to use yum on Ubuntu (though it is available).  Someone new to Fedora would have had no problem installing those packages because they would have used the default package installer rather than installing another one that doesn't work.

---

### Post by pbpersson on 2011-01-07
There is a very good article comparing Fedora and Ubuntu [here]("http://itmanagement.earthweb.com/osrc/article.php/12068_3862556_2/Fedora-vs-Ubuntu-Is-Either-Better.htm")

The article states in part:

[COLOR="Navy"]**"Seven or eight years ago, Debian packages would automatically install missing software needed to run the applications you chose, while RPM packages would leave you having to install the missing software yourself, and often send you into an endless loop of requirements unfondly known as dependency hell."**[/COLOR]

Maybe the last time I tried Fedora was many years ago based on how this article compares the two distros.

---

### Post by pbpersson on 2011-01-07
> **Simian Man said:**
> LOL that would be it.  That's why I said "The best distro is always the one you know best".  I know not to use synaptic in Fedora just like you know not to use yum on Ubuntu (though it is available).  Someone new to Fedora would have had no problem installing those packages because they would have used the default package installer rather than installing another one that doesn't work.

So....are you saying that all distros include package managers that are known to be defective in that distro so people will try them and be convinced that Linux is worthless?

Please provide more details concerning this design decision.  Who thought this was a good idea?

---

### Post by Simian Man on 2011-01-07
> **pbpersson said:**
> There is a very good article comparing Fedora and Ubuntu [here]("http://itmanagement.earthweb.com/osrc/article.php/12068_3862556_2/Fedora-vs-Ubuntu-Is-Either-Better.htm")

The article states in part:

[COLOR="Navy"]**"Seven or eight years ago, Debian packages would automatically install missing software needed to run the applications you chose, while RPM packages would leave you having to install the missing software yourself, and often send you into an endless loop of requirements unfondly known as dependency hell."**[/COLOR]

Maybe the last time I tried Fedora was many years ago based on how this article compares the two distros.
That is definitely true, but yum was included in Fedora Core 2 circa 2004.  I suppose if you used it before then, that would be the case.

> **pbpersson said:**
> So....are you saying that all distros include package managers that are known to be defective in that distro so people will try them and be convinced that Linux is worthless?

Please provide more details concerning this design decision.  Who thought this was a good idea?

Yes.  [Ubuntu comes with yum]("http://manpages.ubuntu.com/manpages/lucid/man8/yum.8.html") in case someone wants to install a bunch of RPM packages and wants dependency analysis.  Likewise Fedora comes with apt-get and synaptic.  It seems there was an effort to get apt to work with RPMs as well on Fedora, but was abandoned.  These packages are not installed by default and remember most Linux users are tinkerers :).

---

### Post by koenn on 2011-01-07
> **pbpersson said:**
> The article states in part:

[COLOR="Navy"]**"Seven or eight years ago [...] RPM packages would leave you having to install the missing software yourself, and often send you into an endless loop of requirements "**[/COLOR]

I have similar memories of SuSE from around the same era.

---

### Post by Spice Weasel on 2011-01-07
[COLOR="Red"]**Problems that were around in 2003 have about a 1% chance of still being around today. Would you judge Windows XP on your experiences of Windows 3.1?**[/COLOR]

Anyway, if you don't like Yum or it doesn't meet your standards, there is a thing called **[COLOR="Blue"]APT-RPM.[/COLOR]**

> It seems there was an effort to get apt to work with RPMs as well on Fedora, but was abandoned.

Nah, it turned out fine. PCLinuxOS now uses APT and Synaptic as RPM frontends to handle packages.

[http://en.wikipedia.org/wiki/Apt-rpm](http://en.wikipedia.org/wiki/Apt-rpm)

---

### Post by asifnaz on 2011-01-08
Come back to the topic guys . I seriously think much of the development work is wasted because many of the developers are aiming for cosmetic changes . 

I have been flamed for this but I must say we should have a common standard for Linux .

---

### Post by Simian Man on 2011-01-08
> **asifnaz said:**
> Come back to the topic guys . I seriously think much of the development work is wasted because many of the developers are aiming for cosmetic changes . 

Most developers who actually improve Linux are working on upstream projects such as desktops and applications.  They aren't impacted by the large number of different distros.

---

