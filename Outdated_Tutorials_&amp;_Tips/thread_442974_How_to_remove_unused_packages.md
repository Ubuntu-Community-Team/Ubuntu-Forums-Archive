---
title: "How to remove unused packages"
date: 2007-05-14
forum: Outdated Tutorials &amp; Tips
---

### Post by capink on 2007-05-14
[COLOR="Red"]DISCLAIMER: This guide involves removing packages form your system. Be sure to backup your system before proceeding. I am not responsible for any damage that might happen for your system.[/COLOR]


> 
[SIZE="4"]**Introduction:[/SIZE]**

[SIZE="4"]**_Note: This section is a clarification of how the process works. You don't have to read it. You can skip it if you want._**[/SIZE]


The purpose of this guide is to enable the user to remove any unnecessary packages on his ubuntu machine, so that his system contains only the packages he wants. There are two problems that face us when trying to remove unnecessary packages from the system:


[LIST=1]
[*]While the end user is aware of what programs he interacts with like his favorite browser and music player, he is not necessarily aware of all the other programs that have more subtle role in the operation of his machine. This will be taken care of on behalf of the user thanks to the brilliant debian package management system, and ubuntu's use of metapackages. More on this later. Suffices to say here that the user needs only be aware of the programs he interacts with on daily basis.



[*]Removing packages on linux system might lead to dependency problems. We might think that we don't need a certain package and try to remove it, only to find that it is required by another package that we need. Dealing with this manaully on a linux system with hundreds of packages installed can turn out to be a nightmare. Again this will be taken care of thanks to the debian smart package manager called aptitude. 

A unique feature of aptitude is that it can label packages as 'automatically installed'. As far as aptitude is concerned an 'automatically installed' package only remains on the system if it is needed to satisfy a dependency of 'manually installed' package. Otherwise, it will be removed. Of course a 'manually installed' is package we have explicitly told aptitude that we need. You can learn more about this by consulting [aptitude documentation]("http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/").

Taking advantage of this feature of aptitude, we will label all the packages we want on our system as 'manually installed'. As for the rest of the packages, we are not going to directly uninstall them to avoid going into nightmare situation described above "dependency hell". Instead, we will just label them as 'automatically installed' and leave it to aptitude to automatically keep only the packages required by other 'manually installed' packages, and remove the packages which does not satisfy any dependency.[/LIST]



[SIZE="3"]**Ubuntu and metapackages:[/SIZE]**

A  [metapackage]("https://help.ubuntu.com/community/MetaPackages") is an empty package that has no actual files. But it depends on other packages, so that when you install this dummy metapackage the system will have to install all the packages on which it depends. simply put, it is hook for installing its dependecies. For example, an Ubuntu user can install the Kubuntu environment (KDE and all its associated programs) by selecting "kubuntu-desktop." You can read more on metapackges [here]("https://help.ubuntu.com/community/MetaPackages").

Ubuntu take advantage of metapackages beautifully. An Ubuntu system installed from a cd is comprised of following metapackages:

[LIST=1]
[*]**linux-generic**: This metapackage always depends on the latest generic Linux kernel available.
[*]**ubuntu-minimal**: This metapackage depends on all of the packages in the Ubuntu minimal system, that is a functional command-line system.
[*]**ubuntu-standard**: This metapackage depends on all of the packages in the Ubuntu standard system. This set of packages provides a comfortable command-line Unix-like environment. 
[*]**ubuntu-desktop**: This metapackage this package depends on all of the packages in the Ubuntu desktop system. It installs a desktop environment (GNOME) and lots of software for home and office use.[/LIST]

So to install a complete ubuntu system, all you have to install is these four metapackages and apt will take care of the rest.





[SIZE="4"]**The process:[/SIZE]**



1. Install aptitude

Aptitude is no longer installed by default in ubuntu. We have to install it ourselves:


```
sudo apt-get install aptitude
```



2. Delete old package states if present:

```
sudo rm -v /var/lib/aptitude/pkgstates*
```



3. Mark all the packages installed on your system as "Automatically installed". 


```
sudo aptitude markauto ~i [COLOR="Red"]--schedule-only[/COLOR]
```


Note: ~i is an [aptitude search term]("http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s03s05.html") meaning installed packages.

[COLOR="Red"]Note: Aptitude will want to remove any package that is marked as "automatically installed", so to prevent it form doing this ( until we do all the steps ) we will use the option --schedule-only from here on until we reach the final step. That is very important.[/COLOR]



4. Label the packages we want to keep as 'manually installed':


Packages essential to the operation of your linux system is labeled as 'manually installed' by running the following command:

```
sudo aptitude install [COLOR="Red"] --schedule-only[/COLOR] linux-generic ubuntu-minimal ubuntu-standard [COLOR="Red"]xorg[/COLOR] [COLOR="Magenta"]openbox firefox lxpanel pcmanfm ....... [/COLOR]
```

you can replace the part highlighted with [COLOR="Magenta"]magenta[/COLOR] with your favorite packages. Remember to include [COLOR="Red"]xorg[/COLOR] if you wish to have graphical system. You will also have to install a window manager like [COLOR="Magenta"]openbox[/COLOR]. Other packages to install are file manager like [COLOR="Magenta"]pcamafm[/COLOR], panel, media player, internet browser .........


[COLOR="Red"]Note: if there are any important packages required for a specific hardware you have, include it in the command above. e.g. wireless drivers[/COLOR]


[COLOR="Purple"]Note: You might want to use the -R switch with aptitude, this switch will prevent installing or keeping [dependencies in the Recommend field]("http://www.debian.org/doc/debian-policy/ch-controlfields.html#s5.6.10")[/COLOR]

> if you want to have only the packages that were isntalled by default with ubuntu modify the previous command to:

```
sudo aptitude install [COLOR="Red"] --schedule-only[/COLOR] linux-generic ubuntu-minimal ubuntu-standard ubuntu-desktop
``` 


if you want a complete command line system:

```
sudo aptitude install [COLOR="Red"] --schedule-only[/COLOR] linux-generic ubuntu-minimal ubuntu-standard
```


if you want a minimal command line system:

```
sudo aptitude install [COLOR="Red"] --schedule-only[/COLOR] linux-generic ubuntu-minimal
```





Here are some metapackages that you might be interested in installing

[LIST]**ubuntu-restricted-extras:** metapackage containing codecs and adobe flash[/LIST]

[LIST]**gnome-core:** barebones gnome[/LIST]

[LIST]**gnome:** The GNOME Desktop Environment, with extra components[/LIST]

[LIST]**xfce4:** Meta-package for the Xfce Lightweight Desktop Environment[/LIST]

[LIST]**xubuntu-desktop:** XCFE desktop with more bells and whistles[/LIST]

[LIST]**lxde-core:** barbone LXDE (lightweight X11 Desktop Environment)[/LIST]

[LIST]**lxde:** LXDE with extra components[/LIST]

[LIST]**kde-full:** KDE desktop[/LIST]

[LIST]**kubuntu-desktop:** KDE desktop with more bells and whistles[/LIST]




5. Let aptitude remove unncessary packages:

Now that we told aptitude what are the packages we want to keep (or add), it is time to let it do its magic.

First we will make aptitude run in simulation mode by using the -s switch. In this mode aptitude will not actually remove anything, it will just print a list of actions it would take if run in real mode (without the -s switch)

```
sudo aptitude install -s
```


> 
Examine the output of this command carefully and make sure you do not want any of the packages that are going to be removed. If you spot any packages in the output of the above command that you would like to keep, you can label it as 'manually installed' by running this command:

```
sudo aptitude install packagename [COLOR="Red"]--schedule-only[/COLOR]
```

Also make sure that there are no confilcts. If you don't like what aptitude is going to do and want to revert back all the changes we did, run this command:

```
sudo aptitude keep-all
```



After you are fully satisfied with what aptitude printed in the simulation mode. You can remove the pacakges using aptitude without the simulation switch:

```
sudo aptitude install
```

---

### Post by capink on 2008-01-18
deleted

---

### Post by urukrama on 2008-01-18
Do you know debfoster and deborphan? 

From the man pages:

**Debfoster**:

> debfoster maintains a list of installed packages that were explicitly requested rather than installed as a dependency.  Arguments are entirely
     optional, debfoster can be invoked per se after each run of dpkg and/or apt-get.

     Alternatively you can use debfoster to install and remove packages by specifying the packages on the command line.  Packages suffixed with a -
     are removed while packages without a suffix are installed.

     If a new package is encountered or if debfoster notices that a package that used to be a dependency is now an orphan, it will ask you what to do
     with it.  If you decide to keep it, debfoster will just take note and continue.  If you decide that this package is not interesting enough it
     will be removed as soon as debfoster is done asking questions.  If your choices cause other packages to become orphaned more questions will
     ensue.

     Whenever debfoster asks you about a package, any of the following responses can be given:

       &#8216;y&#8217;         Yes, keep the package. This is the default response.
       &#8216;n&#8217;         No, delete the package.
       &#8216;p&#8217;         Prune the package. This tells debfoster to also delete all
                   packages that are only installed because this package
                   depends on them.  A list of such packages, if any, is shown
                   above the prompt.
       &#8216;s&#8217;         Skip this question. The next time you run debfoster it will
                   ask you again about this package.
       &#8216;h&#8217;         Print a help message.
       &#8216;i&#8217; or &#8216;?&#8217;  Show information about the package.
       &#8216;u&#8217;         Undo last response.
       &#8216;q&#8217;         Exit without removing packages.  All changes will be lost.
       &#8216;x&#8217;         Save changes to debfoster database, remove unwanted pack&#8208;
                   ages, and exit without asking further questions.


**Deborphan**:

>  deborphan  finds  packages that have no packages depending on them. The default operation is to search only within the libs  and  oldlibs  sec&#8208;
       tions to hunt down unused libraries. 

       If  it is invoked with an optional list of packages, only the dependencies on those packages will be checked. The results are printed to std&#8208;
       out as if the option --show-deps had been given. Searching for specific packages will show the package, regardless of its priority. It is  pos&#8208;
       sible to specify -, to read a list of packages from standard input.


---

### Post by capink on 2008-01-18
Yes I heard about them. But I usually install a lot of programs just to try them and my system becomes cluttered with a host of applications I did not need. deborphan and debfoster did not allow me to return to my base install as they only remove libs and dependencies of packages that were already removed (and the packages I chose to install but no longer need).

The idea of the script in the first post was to have it read form a premade list what applications I want on my system and it would remove anything else. I run it whenever my system get cluttered with programs I do not want.

---

