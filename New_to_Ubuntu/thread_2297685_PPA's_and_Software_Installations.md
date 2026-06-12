---
title: "PPA's and Software Installations"
date: 2015-10-05
forum: New to Ubuntu
---

### Post by eddiefiggie on 2015-10-05
I almost understand this concept.  "Almost" being the key word.

I understand that Ubuntu/Linux has the ability to maintain packages.  I get that these packages are archived in repositories.  I understand that PPA's are "install at your own risk" repositories.  Once you add a repository however, how do you get a list of the software available within a repository?

More specifically, I "think" I added a PPA repository...  I have my eye on a package that I want.  How do I do it though?

Steps:

1) Add the repository

2) install the package.....but how?!

---

### Post by sandyd on 2015-10-05
You can view the packages in the web interface. For example, for the gnome3 ppa, [https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3/+packages](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3/+packages) will show all packages (I just hit the "view package details" button).

If you know the name (or part of the name) of the package, you can use apt-cache to search for it.

For example:
```

apt-cache search gnome
```

---

### Post by CantankRus on 2015-10-05
If you are going to use third party repos I suggest you install and use synaptic.

Steps to install package from a ppa:
1) Add the repository
```
sudo add-apt-repository [COLOR="#696969"]somerepo[/COLOR]
```

2) Update sources
```
sudo apt-get update
``` 

3) Install your application
```
sudo apt-get install [COLOR="#696969"]someapp[/COLOR]
```

Always check what other packages are in a repo before upgrading as this is where you can run into incompatibility problems.
Synaptic can list ppa packages.
[ATTACH=CONFIG]264825[/ATTACH]


If a ppa also contains unrelated packages to the one I want I will disable the ppa after installation.
Every so often I will enable the ppa to check for updates, then disable again.
Update your sources each time with **sudo apt-get update** or hit the reload button in synaptic.

You can view added repos from within synaptic.
If you add a  "Comment" to represent the ppa it makes it easier to find.
[ATTACH=CONFIG]264827[/ATTACH]

If a ppa causes problems you can downgrade versions of packages you may have installed from a ppa
to the official versions and disable the ppa using [**_[COLOR="#B22222"]ppa-purge[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2264416&p=13224880#post13224880")

---

### Post by mastablasta on 2015-10-06
> **eddiefiggie said:**
> 
Steps:

1) Add the repository

2) install the package.....but how?!

it should be:


1) Add the repository

2) Update list of packages in all your repositories (sudot apt-get update or refresh or something like that in software center)

 3) Search for package that will now be in yoru software center or whatever you use (in CLI apt-get install *package*)


we add the source of the package, we tell the OS to update the sources package, appears in software installer.

---

### Post by grahammechanical on 2015-10-06
After adding the PPA as a repository to our list of software sources and running apt-get update, applications should appear in Software Centre. We can also use

```
sudo apt-get install <package name>
```

If the package is a library then we need to use the full name for the library. This is where Synaptic Package Manager is most useful. It will also identify what other packages will be removed.

Regards.

---

### Post by ian-weisser on 2015-10-06
> **eddiefiggie said:**
> Once you add a repository however, how do you get a list of the software available within a repository?

Your system's low-level package installer, dpkg, maintains a database of all packages available from all known sources.
  - Known sources are in /etc/apt/sources.list* , including PPAs you have added.
  - The database is located at /var/lib/dpkg/info .
  - You can browse the database using the 'apt-cache' command.
  - Apt uses the database to calculate upgrades, dependencies and much more.

When you add or remove a source (or periodically), you must *update* that database from those sources. That's what the 'apt-get *update*' command does.

---

### Post by mc4man on 2015-10-06
As shown in post 3 synaptic represents a good way to see what's in a repo you've added & what's been installed from there, if anything.
aptitude has a range of search & filter commands that will print a list though some of the syntax is complicated.

A simpler aptitude command is to use owner or if you've more than one ppa from that owner than owner-ppaname . This is the same 'names'  that one would use from the add-apt-repository command except done with - instead of / in the case of owner-ppaname

So as example I have a number of my own ppa's in use here, this shows all avail. from all the ppa's - 
> aptitude search '~O LP-PPA-mc3man'
If I wanted just from one specific I'd add that specific ppa after a - 
> aptitude search '~O LP-PPA-mc3man-testing6'
(- The add-apt-repository command to the above to show relationship to aptitude searches
add-apt-repository ppa:mc3man/testing6

For you though synaptic > origins  would be good, also it's generally best to go to a ppa before using for any info. From the main ppa page you can see the actual packages by clicking on the "View package details" link on the page

---

