---
title: "How does APT know?"
date: 2023-02-17
forum: New to Ubuntu
---

### Post by magnoliafan2000 on 2023-02-17
How does my computer know the app exists, to download at all? For instance, "git" the app.
sudo dnf install git-all

---

### Post by #&amp;thj^% on 2023-02-17
> **magnoliafan2000 said:**
> How does my computer know the app exists, to download at all? For instance, "git" the app.
sudo dnf install git-all

Ubuntu does not use dnf or cnf it use's "Apt"
Example from your querry:
```
apt policy git
git:
  Installed: 1:2.39.1-0.1
  Candidate: 1:2.39.1-0.1
  Version table:
 *** 1:2.39.1-0.1 990
        990 http://deb.debian.org/debian testing/main amd64 Packages
        500 https://deb.kaisenlinux.org kaisen-rolling/main amd64 Packages
        100 /var/lib/dpkg/status
     1:2.39.1-0.1~bpo11+1 100
        100 http://deb.debian.org/debian bullseye-backports/main amd64 Packages
     1:2.30.2-1+deb11u1 500
        500 http://security.debian.org/debian-security bullseye-security/main amd64 Packages

```
and:
```
apt policy git-all
git-all:
  Installed: (none)
  Candidate: 1:2.39.1-0.1
  Version table:
     1:2.39.1-0.1 990
        990 http://deb.debian.org/debian testing/main amd64 Packages
        500 https://deb.kaisenlinux.org kaisen-rolling/main amd64 Packages
     1:2.39.1-0.1~bpo11+1 100
        100 http://deb.debian.org/debian bullseye-backports/main amd64 Packages
     1:2.30.2-1+deb11u1 500
        500 http://security.debian.org/debian-security bullseye-security/main amd64 Packages

```
I'm not trying to confuse you from my examples I'm using Debian, ATM
If your just looking for a single application then Apt has a nice search tool as well.
```
apt search git-all
Sorting... Done
Full Text Search... Done
git-all/testing,kaisen-rolling 1:2.39.1-0.1 all
  fast, scalable, distributed revision control system (all subpackages)


```

---

### Post by magnoliafan2000 on 2023-02-18
Thankyou! I appreciate how in-depth your answer is!

---

### Post by TheFu on 2023-02-18
> **magnoliafan2000 said:**
> Thankyou! I appreciate how in-depth your answer is!

There are about 5 major families of Linux distributions. The membership in each "family" is mostly based on which package management system they use.
[LIST]
[*]RPM (redhat)
[*]DEB (debian)
[*]TGZ (like slackware)
[*]Pacman (Arch)
[/LIST]
are the biggest.
Here's a link [https://en.wikipedia.org/wiki/File:Linux_Distribution_Timeline_21_10_2021.svg](https://en.wikipedia.org/wiki/File:Linux_Distribution_Timeline_21_10_2021.svg) that shows these relationships.  You'll likely need to zoom in and out of the SVG image.

BTW, if you found these answers sufficient for your needs, please use the Thread Tools button to mark the thread **SOLVED** to help out the community.  

If you want more details, there are lots of those that haven't been provide so you aren't overwhelmed with that extra, mostly unnecessary, information for how things **really** work behind the scenes.  If you aren't a programmer or professional Linux admin, the you probably don't care any more than someone driving a car doesn't need to know what the pressure is on their fuel injectors.
> How does my computer know the app exists, to download at all?

**apt** works a little different than **dnf**.  It doesn't refresh the local cache files automatically, so we have to request it periodically.   Daily is sufficient for pretty much everyone.
APT is the overall name for the package management system used on Debian-based Linux systems. There are a number of tools that make up "APT" .... dpkg, apt-get, aptitude, apt, synaptic are a few. They all share the local cached files which have a list of every package available in the configured repositories.  "Software Center" is another GUi that works at a very high level. I find it doesn't provide sufficient details, so I'd prefer to use synaptic or aptitude if I were a GUI user.
dpkg is a low-level tool for package management and doesn't handle things like dependencies.  It is similar to the rpm tool, you might know.
In general, I use 'apt' 99% of the time as 1fallen spelled out above. It is a nice little front-end to apt-get that adds some features, but passes through most capabilities, so we don't lose anything possible in apt-get by using apt.  apt adds some features that apt-get cannot do.

Anyway, my recommendation is to patch weekly, not more often and to run 2 commands, say over the weekend, right after you've made your weekly system backups (assuming you don't backup daily). Those are the command:
```
sudo apt update
sudo apt full-upgrade
```
The first refreshes the local cache of all available packages in the repos you've configured.
The second downloads and updates any newer versions of packages that are on your system already, along with dependencies that need updating.  

One of the coolest things about Linux distributions is the ability to extend your repo list to include specialized repos from specific project teams to have selected software pulled not from the Canonical repos, but directly from the project that is creating the software we run.  This way, we can get a newer versions for some specific tools, but not all. So our systems can be mostly stable and working.  "New" isn't always better, but for some programs, especially those likely to be targeted for malware or nefarious attacks, the trade off to be patched is probably the best option.  Things like web browsers fall in to that category.

Anyway, your local cache files are under /var/cache/apt.  It doesn't hurt to to and look at those files. Some will be binary. Be careful which you try to open in any editor. They can be large and would used lots of RAM to view.  Best to use a 'pager' tool, like **less** or **more**, which is always safer to view files.

---

### Post by mIk3_08 on 2023-02-18
For more info. about the package management of Linux Distro that uses yum or dnf: Regards and cheers.

RedHat Enterprise Linux
Fedora
CentOS
AlmaLinux
Rocky Linux
Oracle Enterprise Linux
Scientific
CERN
SUSE
OpenSUSE
Mageia
PCLinuxOS
Berry
Elastix
ClearOS
FrameOS
Fermi
Turbolinux

---

### Post by VMC on 2023-02-18
"There are about 5 major families of Linux distributions. The membership  in each "family" is mostly based on which package management system they  use.

[LIST]
[*]RPM (redhat)
[*]DEB (debian)
[*]TGZ (like slackware)
[*]Pacman (Arch)"
[/LIST]

Don't forget suse that uses package manager zypper. Also if trying to compare usage or if in unfamiliar iterator, here "Arch Rosetta" to help out:
 [https://wiki.archlinux.org/title/Pacman/Rosetta](https://wiki.archlinux.org/title/Pacman/Rosetta)

---

### Post by TheFu on 2023-02-18
> **VMC said:**
>  
Don't forget suse that uses package manager zypper. Also if trying to compare usage or if in unfamiliar iterator, here "Arch Rosetta" to help out:
 [https://wiki.archlinux.org/title/Pacman/Rosetta](https://wiki.archlinux.org/title/Pacman/Rosetta)

Last time I ran SuSE, it was using RPM underneath. Has that changed?

There are hundreds of Linux distros, but few are 100% standalone.  Nothing wrong with "standing on the shoulders of giants" in the Linux world.

---

### Post by VMC on 2023-02-19
> **TheFu said:**
> Last time I ran SuSE, it was using RPM underneath. Has that changed?

.... Yes, but with a twist. See here:
[https://serverfault.com/questions/1094042/difference-between-zypper-and-rpm-for-installed-packages](https://serverfault.com/questions/1094042/difference-between-zypper-and-rpm-for-installed-packages)

---

### Post by grahammechanical on 2023-02-19
Sometimes APT will throw out the message that a certain repository does not have a release file. I am guessing that the release file contains the information about which packages have upgrade code. I am also guessing that this is how APT knows which packages are to be updated/upgraded.

[https://unix.stackexchange.com/questions/721809/what-is-a-release-file](https://unix.stackexchange.com/questions/721809/what-is-a-release-file)

It is all guess work I am afraid. Sorry.

Regards

---

### Post by ActionParsnip on 2023-02-20
When you run
```

sudo apt update

```
The package list of your sources are read and the available versions are put into your system. This is how it knows

---

### Post by MAFoElffen on 2023-02-20
> 
Both DNF and APT (the package managers for Red Hat and Ubuntu-based  Linux distributions) store cached information to ensure the process of  installing software is much faster and reliable. With these caches in  place, neither package manager has to download the information every  time you attempt to update, upgrade or install software.

It is a database. It also stores what is installed, and what is needed as dependencies to install a package. 

If refreshing the package cache from the sources/repo's has a version that is newer, than what is installed, it then triggers that an update in the version of those packages are needed. 

Unfortunately, what has happened to me over the years, is that some "combinations" of packages do not play nice together, or some packages conflict with other packages. When that happens, you may not be able to install some software or get an update because of that conflict... That takes some research on what is conflicting and how to resolve that.

That is how that part of a package manager works.

---

