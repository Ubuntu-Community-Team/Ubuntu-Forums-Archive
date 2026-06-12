---
title: "Ubuntu Developer Edition"
date: 2006-11-22
forum: Programming Talk
---

### Post by daz4126 on 2006-11-22
Hi everybody,

What do you think of a version of Ubuntu aimed specifically at developers. I am thinking of web development, but it could be any sort of programming.

This could come with Apache, MySQL, phpAdmin, Php, ruby on rails already configured. Lots of browswers to test on. Development software such as bluefish, radrails, aptana, eclipse, nvu etc

Any thoughts on this or suggestions for pre-installed software?

DAZ

---

### Post by amo-ej1 on 2006-11-22
what's the difference with any other version of ubuntu ? ;)

---

### Post by daz4126 on 2006-11-22
Lots of the software isn't standard on the default installation of Ubuntu. Certainly Ruby on Rails and Aptana aren't installed by default. 

I would imagine it to maybe have development type programs easily accessible from the panel or in their own menu.

DAZ

---

### Post by Ramses de Norre on 2006-11-22
Isn't it too much of a hassle to make another version of ubuntu when you can just install those packages in a few minutes?

---

### Post by hod139 on 2006-11-22
Instead of a new version of Ubuntu, why not write an install script (like automatix) for these apps?

---

### Post by daz4126 on 2006-11-22
> **hod139 said:**
> Instead of a new version of Ubuntu, why not write an install script (like automatix) for these apps?

This sounds like a great idea, is anybody able to do this?

I really do think that if you could say to people, look there is this distro that gives you all these great web development tools straight out of the box then people would be interested.

So come on people, can we get a list of apps and then could somebody put a script together??

Here are my apps:
Ruby on Rails
RadRails
Aptana
Scribes (Textmate for Linux potentially)
Inkscape
Firefox Web Developer toolbar


Any others??

DAZ

---

### Post by justin whitaker on 2006-11-22
IANAD (I am not a developer), but it seems to me that you would want a broad spectrum of applications that covered:

Ruby+Rails+Gem
Apache+PHP+Perl
A default database 
Python
The Full GCC chain
Java+VM
XML
C++
Mono or some other .net implementation
XAML?
Actionscript?
AJAX toolkits?
Google Toolkit?
One good editor or IDE to rule them all.

---

### Post by daz4126 on 2006-11-22
This sounds like a good list to get us going, keep the suggestions coming. Still waiting for somebody who coudl make this happen ... any takers??

DAZ

---

### Post by daz4126 on 2006-11-22
> **justin whitaker said:**
> I
One good editor or IDE to rule them all.

I would vote Eclipse with various plugins - from experience the Aptana and Radrails plugins are excellent. Aptana covers lots of AJAX stuff and toolkits and Radrails is perfect for RoR development.

DAZ

---

### Post by justin whitaker on 2006-11-22
> **daz4126 said:**
> I would vote Eclipse with various plugins - from experience the Aptana and Radrails plugins are excellent. Aptana covers lots of AJAX stuff and toolkits and Radrails is perfect for RoR development.

DAZ

The full eclipse environment is pretty big. Did you look at Easy Eclipse as an option?

---

### Post by arnieboy on 2006-11-22
just a note in this context: we are planning to include Programming Tools and Server as options on Automatix2. These will have several install options under them. It would be useful to get some feedback and help from folks who would want this done.

---

### Post by daz4126 on 2006-11-22
> **arnieboy said:**
> just a note in this context: we are planning to include Programming Tools and Server as options on Automatix2. These will have several install options under them. It would be useful to get some feedback and help from folks who would want this done.

That sounds awesome arnieboy, thanks.

Aptana was such a pain to get working, thanks to an autoinstaller that doesn't autoinstall. Had to go searching for a guide. Don't have the url at the moment, but will find it if required.

An automatic setup of Apache, phpmyadmin, mysql and php would be useful also.

DAZ

---

### Post by arnieboy on 2006-11-22
a similar thread was started here some time back and might be useful for those who wish to contribute ideas and howtos:
[http://www.getautomatix.com/forum/index.php?showtopic=210](http://www.getautomatix.com/forum/index.php?showtopic=210)

---

### Post by po0f on 2006-11-22
Instead of a "Developer Edition", go with different meta-packages.  (Meta-packages are just packages that don't install stuff themselves, but instead have several dependencies.)

Say for instance, a kernel-development meta-package could install build-essential, linux-headers and linux-sources, whatever the Debian kernel packager is called, and so on.  A web-development meta-package could install most of the packages already mentioned, as it looks like the original intent was more for *web* development as opposed to broader, more generic development.

I would suggest meta-packages over anything, even though I don't think that the meta-packages will get popular much at all (at least among developers).  (Broad, sweeping generalization ahead) Most developers know what they want and are more Linux-saavy than your average Joe User, and can thus find and install what they want relatively easily.  It's a good idea, but you're targeting *developers*.  These are people that (hopefully) know how to get things done.

And just to echo previous sentiment, we really don't need another Ubuntu knock-off.

---

### Post by daz4126 on 2006-11-23
@ po0f:

Thanks for the idea about a meta-package. I personally would prefer something like the Automatix solution where you could choose from some popular solutions.

I have to disagree a little with your 'sweeping generalisation' that developers are Linux-savvy. Many web developers do just html and css with a sprinkling of javascript on macs, so maybe an easy install option that would set all the best software up for them would be useful?

And pardon my ignorance, but how come people are so against different versions of Ubuntu? I thought the idea of Linux was that you could take a base distro and then change it to suit needs, hence all the different distros, some based on others??

DAZ

---

### Post by daz4126 on 2006-11-23
> **arnieboy said:**
> a similar thread was started here some time back and might be useful for those who wish to contribute ideas and howtos:
[http://www.getautomatix.com/forum/index.php?showtopic=210](http://www.getautomatix.com/forum/index.php?showtopic=210)

Thanks for the link arnieboy, these all sound like the sorts of things I was thinking, but I was also thinking of editors and IDEs as well (I'll say it again, Aptana was a pain to set up..!)

Any ideas when this is due to be in Automatix2?

cheers,

DAZ

---

### Post by jamesrose on 2006-11-23
I think most of the base programs are already included:

GCC
G++
Text Editor


Thats all I need, and thats whats included.

Although, you are right. Something a little less "noobie" would be good, for the professionals and developers :]:D

---

### Post by Steveire on 2006-11-23
On the metapackage point:
```

stephen@ubuntu:~$ aptitude show kdewebdev kde-devel kdesdk kde-devel-extras
Package: kdewebdev
New: yes
State: installed
Automatically installed: no
Version: 4:3.5.5-0ubuntu1
Priority: optional
Section: kde
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 61.4k
Depends: quanta (>= 4:3.5.5-0ubuntu1), kfilereplace (>= 4:3.5.5-0ubuntu1), kimagemapeditor (>= 4:3.5.5-0ubuntu1), klinkstatus (>=
         4:3.5.5-0ubuntu1), kommander (>= 4:3.5.5-0ubuntu1), kxsldbg (>= 4:3.5.5-0ubuntu1)
Suggests: kommander-dev (>= 4:3.5.5-0ubuntu1), kdewebdev-doc-html (>= 4:3.5.5-0ubuntu1)
Description: web development apps from the official KDE release
 KDE (the K Desktop Environment) is a powerful Open Source graphical desktop environment for Unix workstations. It combines ease of use,
 contemporary functionality, and outstanding graphical design with the technological superiority of the Unix operating system.

 This metapackage includes a collection of web development applications provided with the official release of KDE.

Package: kde-devel
New: yes
State: not installed
Version: 5:47
Priority: extra
Section: universe/kde
Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Uncompressed Size: 41.0k
Depends: kde-core (>= 5:47), kdesdk (>= 4:3.4.3), libartsc0-dev (>= 1.4.2), libarts1-dev (>= 1.4.2), kdelibs4-dev (>= 4:3.4.3), kdebase-dev
         (>= 4:3.4.3), libkonq4-dev (>= 4:3.4.3), qt3-designer
Suggests: kde-i18n (>= 4:3.4.3)
Description: the K Desktop Environment development files and modules
 KDE (the K Desktop Environment) is a powerful Open Source graphical desktop environment for Unix workstations. It combines ease of use,
 contemporary functionality, and outstanding graphical design with the technological superiority of the Unix operating system.

 This metapackage includes official KDE modules that are useful to developers, including KDE's software development kit (SDK), Qt3's designer
 tool, and all core KDE header and development packages.

Package: kdesdk
New: yes
State: not installed
Version: 4:3.5.5-0ubuntu1
Priority: optional
Section: universe/kde
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Uncompressed Size: 69.6k
Depends: cervisia (>= 4:3.5.5-0ubuntu1), kapptemplate (>= 4:3.5.5-0ubuntu1), kbabel (>= 4:3.5.5-0ubuntu1), kbugbuster (>= 4:3.5.5-0ubuntu1),
         kcachegrind (>= 4:3.5.5-0ubuntu1), kdesdk-kfile-plugins (>= 4:3.5.5-0ubuntu1), kdesdk-kio-plugins (>= 4:3.5.5-0ubuntu1) |
         kdesvn-kio-plugins, kdesdk-misc (>= 4:3.5.5-0ubuntu1), kdesdk-scripts (>= 4:3.5.5-0ubuntu1), kmtrace (>= 4:3.5.5-0ubuntu1), kompare
         (>= 4:3.5.5-0ubuntu1), kspy (>= 4:3.5.5-0ubuntu1), kuiviewer (>= 4:3.5.5-0ubuntu1), kunittest (>= 4:3.5.5-0ubuntu1), poxml (>=
         4:3.5.5-0ubuntu1), umbrello (>= 4:3.5.5-0ubuntu1)
Suggests: kcachegrind-converters, kbabel-dev, kdesdk-doc-html
Description: software development kit from the official KDE release
 KDE (the K Desktop Environment) is a powerful Open Source graphical desktop environment for Unix workstations. It combines ease of use,
 contemporary functionality, and outstanding graphical design with the technological superiority of the Unix operating system.

 This metapackage includes the KDE Software Development Kit, a collection of applications and tools useful for developing KDE applications.

Package: kde-devel-extras
New: yes
State: not installed
Version: 5:49
Priority: optional
Section: universe/kde
Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Uncompressed Size: 41.0k
Depends: kde-core (>= 5:47), kde-devel (>= 5:47), kdbg, kdevelop (>= 4:3.3.2), kprof
Description: extra development applications for use with KDE
 KDE (the K Desktop Environment) is a powerful Open Source graphical desktop environment for Unix workstations. It combines ease of use,
 contemporary functionality, and outstanding graphical design with the technological superiority of the Unix operating system.

 This metapackage includes programs of use to developers that are not part of the official KDE modules, including a debugger, a profiling
 tool, and KDevelop, a complete development environment.

```

When I get around to it (Might not be til the summer) I'm going to have a go at making automatix etc obsolete. I'll report when I have proof of concept.

---

### Post by pedrotuga on 2006-11-23
Actualy i think a developer edition would be cool.
i already installed sooooooo much stuff.

It could come with:
boa constructor
spe
build-essential ( it's a bit an ubuntu fault... not having this on the default distro )
eclipe
JSDK
Kdeveloper
php
mysql
postgresql
apache
sqlite
ruby
perl
etc

like... why does python comes already and not gcc/g++??? a bit non sense in my opinion

I think it would save a lot of time... but if a big collection of libraries would be included then it would end up being a ditro like suse.

---

### Post by hod139 on 2006-11-27
Looks like someone beat you all to it, DevUbuntu was just released: [http://www.giovelug.org/articles.php?lng=en&pg=106](http://www.giovelug.org/articles.php?lng=en&pg=106)

---

### Post by ihavenoname on 2007-06-03
devubuntu doesn't seem very active. i think we need something on the lines of this [http://www.ibiblio.org/onebase/onebaselinux.com/About/features/developgo.php](http://www.ibiblio.org/onebase/onebaselinux.com/About/features/developgo.php)

---

### Post by CaptainMorgan on 2007-06-03
Sounds great. Installing all this stuff takes too long. I would love to see what others have already mentioned as default/standard in a new distro. In addition I would add Netbeans including the Javadoc.

---

### Post by bobbocanfly on 2007-06-03
Love this idea! First thing i do when i install any distro is add apache,php,mysql,ruby, etc. Would take out loads of work!

---

### Post by daxumaming on 2007-06-03
I've used Fedora before, and one of the things I missed is the ability to just select Developer during install and it'll install every IDE, Debugging apps, etc. you'll need. Of course, it'll also install apps I don't need. 

Today, I installed KDevelop, but had some problems compiling a Hello World program, I have to download and install dozens of packages before I got it working (I'll be blogging about this). It seems that Aptitude installed KDevelop, not the *-dev packages that it needs in order to make it useable. 

A meta-package is a great idea, as long as it installs every dependencies that it needs. As for Automatix, I've used it before, and a Dev Package would be really nice. This way, we don't have to remaster Ubuntu.

Ubuntu Developer Edition? Hell Yeah!

---

### Post by hantsy on 2007-06-03
I think the offical ubuntu can provide some dummy package .
I dislike all-in-one solution.
May be it is slipt into serval package for different purpose.
Such as,
java-developer(Java VM ,basic libs such as jatarta commons series, Java EE runtime and desing time tool, such as IDE , application server , jdbc drivers)
mono-developer(Mono , C# , MonoDevelop)
web-devloper(support PHP 5 and php framework ,such as Zend framework, Prdao , and  RoR , Apache 2)
gnome-developer (Glade designer , all languga gnome binging such C, C++,Perl ,python ,Java  C# gnome binding , a gnome developer envirorments base on Anjuta IDE, support deb packge )
provide database for all section.(MySQL and PostgreSQL)

---

### Post by pedrotuga on 2007-06-03
At first i was very enthusiastic about this idea. But looking to the way this topic is going it looks like each person has his/her own preferences of course.
What to include and what not to?
Hantsy has a point in the post right above this one, but on the other hand some guys use different tools and different languages/toolkits/whatever and like to have the whole thing there just in case. Both opinions are equally valid.

Maybe we are forgetting here how easy is to use aptitude, synaptic, automatix, et al.
Also, there is good trusted documentation on the wiki with information on how to set up a couple of develop environments. Besides that, we should remember that a developer is a guy that understands in some way how it's computer work, we are not really talking about a tech dummy end users here.
One last thing: an operative system is not something we install from time to time when necessary. The longer it last on a system the beter it is.

---

### Post by Jessehk on 2007-06-03
I never really understood all these separate "editions". If you want development programs, just download them using dpkg -- it takes 30 seconds.

In my opinion, it's an unnecessary forking that causes more confusion then benefit.

---

### Post by pmasiar on 2007-06-03
> **pedrotuga said:**
>  it looks like each person has his/her own preferences of course.

Exactly. If you want to be developer, you spend on your own bugs *much* more than couple minutes it takes to install most of packages. And synaptic will install them in standard, well-tested way. Why waste time on making custom non-standard install work?

I am not sure about current state of automatix, but I heard that (because automatix claims to be distro-independent) it can screww your install in way hard to fix. IN IRC ppl even refused to fix automatix installs. 

So continue on your own risk.

---

### Post by ArieT on 2007-06-03
I don't need a developer edition. I've developed multiple websites and a couple of 'real' programs but i don't see why someone would need a special 'developer edition'. Besides that it's almost impossible to make one. We've got Python, PHP, Ruby, Java, C, C++, C# with mono and lots of other languages. All with their own ide's and own compilers. You can't include all of them in one distro.

In fact i don't know much good reasons for having Xubuntu and Kubuntu. Isn't it possible to install KDE and all the apps with apt-get? Isn't it possible to remove Gnome with apt-get? We don't need multiple flavours of one distro. It's too confusing for beginners and for advanced users it's very simpel to download KDE or XFCE with apt-get ...

---

### Post by pmasiar on 2007-06-03
Maybe for a beginner whose PC will run only XFCE, having xubuntu for hassle-free start still makes sense, don't you think so?

---

### Post by bobbocanfly on 2007-06-03
One of the main objections to this idea in this thread is that without doubt it will install something you dont need. TO get around that problem you could put in a Fedora style post install package setup dialog. So you could choose between a set of different programming styles. IE

[LIST]
[*]Web Development - Apache Server, HTML/JS Editors
[*]Java Development - Java IDE/Compilers
[*]C++ Development - G++, C++ IDE
[*]PHP/MYSQL Development - Apache, PHP, MySQL, IDE 
[*]etc.
[/LIST]

It would probably be a lot of work to implement it but would save a lot of complaints like 'Ooh theres too many packages, im going to make UbuntuC++Dev'.

Also for software with multiple versions (Thinking of PHP4/5 and Apache1/2), once you selected the web development packages a little prompt box would come up "Which version do you want to install? PHP4 or PHP5?"

bobbocanfly

---

### Post by ihavenoname on 2007-06-03
"I don't see the point in having Ubuntu, we could all just install Debian and use apt-get to install everything else." ;)  You see why that argument isn't really the best way to go about it. The point is, if you are a developer on the go you can have a live-cd and work on some of your projects while traveling without installing, if you are a developer and you are upgrading and you don't want to spend time downloading all the software packages for development you can have an option to have them installed right away. There are numerous uses for this, even just as a show-case. After all a large number of distros (just look at the top 5/10 distros on distrowatch) are just customized versions of other distros. In this case we are not talking about a totally revamping of ubuntu, just a different method of installing. How many people do you see complaining about not having out of box support of some random codec, we could tell them that they could just use synaptic, but instead the Ubuntu-devs went and made codec buddy.

---

### Post by JT673 on 2007-06-03
The install script idea is good!  How about if we start a list of debian packages to install, then we'll get to the generic binaries:

Ruby -> ruby, irb, rdoc, ri (1.8 or 1.9?), rake, rails, ruby-tk
Java -> netbeans, sun-java-5 (needs doc .zip from Java download page...), ant, javacc (?), junit
C/C++ -> manpages-dev, binutils, autoconf, autogen, automake1.9, cpp-doc, indent
Objective C -> gobjc4.1
Perl -> (?)
Python -> python-2.5, python-glade2, python-gnome2, python-qt3 (4 will break some dependencies...)
Php -> php5.5-dev
Tk/Tcl -> tk8.4-dev, tcl8.4-dev
Other -> mysql-server-5.0, mysql-admin, cvs, svn, debmake, doxygen, devhelp, help2man

You know, maybe we're better off making a program that will back up your current debian packages...You can backup your other stuff...

---

### Post by bobbocanfly on 2007-06-04
If the setup script for different types of development, things like CVS and SVN should definately be included as most (if not all developers) will have to use it at some point. 

The only downside i can see of using this type of setup script is that the LiveCD would essentially be the same (Maybe slightly different, with CVS, SVN and Vim/Emacs instead of Gedit) as the default Ubuntu, so would not work with ihavenonames idea of the travelling developer.

---

### Post by KaeseEs on 2007-06-04
I would like to add to the metapackage suggestion.

**dev-tools-basic**
[list]vim|emacs[/list]
[list]build-essential[/list]
[list]debhelper[/list]
[list]exuberant-ctags[/list]
[list]valgrind[/list]
[list]svn|cvs[/list]

**dev-tools-c**
[list]manpages-dev[/list]
[list]binutils[/list]
[list]gdb[/list]
[list]linux-headers-generic[/list]
[list]glibc-doc[/list]
[list]linux-libc-dev[/list]
[list]dev-tools-basic[/list]

**dev-tools-c++**
[list]dev-tools-c[/list]
[list]g++[/list]

**dev-tools-perl**
[list]perl[/list]
[list]vim-perl[/list]
[list]perltk[/list]
[list]libdb-mysql-perl[/list]
[list]dev-tools-basic[/list]

**dev-tools-web**
[list]php[/list]
[list]rails[/list]
[list]python[/list]
[list]mysql|postgresql[/list]
[list]apache2|lighttpd[/list]
[list]dev-tools-basic[/list]


...and so on.  I would suggest this sort of thing because it's a pain in the rear to install all the junk I need on a dev machine by hand, and I always wind up forgetting something until I need it.  I would suggest to take the metapackage tack over the sibling-distro tack because:
[list]There's no need for a new artwork set[/list][list]It's easier to maintain this way[/list][list]Upgrading a metapackage updates everyone who's using the package automatically[/list][list]It provides the user control without adding a post-install checkbox script[/list][list]Simpler upgrade path for those with *buntu already installed[/list]

---

### Post by WW on 2007-06-04
I really like the idea of meta-packages, and KaeseEs list is a good start.  I'm sure there won't be 100 percent agreement on what should be included in any particular meta-package, but I'm also sure it will be better than simply having build-essential (which is only good for C and C++, and doesn't include any additional doc. packages).

I would also add:

**dev-tools-fortran**
[list]
[*]gfortran
[*]gfortran-doc
[*]libgfortran0-dev
[*]fort77
[/list]

(Yes, some folks *still* use Fortran...)

---

### Post by xtacocorex on 2007-06-04
Looks like WW knows that I'm a FORTRAN programmer. :)

Instead of a new distro, a script would be best.  Maybe as a side project to this, include syntax files for vi and other editors.

---

### Post by ihavenoname on 2007-06-05
maybe a meta-package for each language/use case.  So we don't have to get all those things we don't need.

Ex. Ubuntu-C++ Ubuntu-java Ubuntu-ruby etc. Each meta-package would contain documentation, IDEs, compilers, and other necessary files/headers for development. Of course only the best of breed applications should be used. In the future though, an "On the go" live-cd should be made.

---

### Post by jaked122 on 2010-03-14
well, I think that geany(for gnome) would be a good fairly small text editor for something like this.

---

### Post by overdrank on 2010-03-14
> **jaked122 said:**
> well, I think that geany(for gnome) would be a good fairly small text editor for something like this.

[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

