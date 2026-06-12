---
title: "I'm confused by the purpose of Arch..."
date: 2007-12-08
forum: Other OS Talk
---

### Post by travismh on 2007-12-08
I'm confused by the purpose of Arch Linux.  Right now I'm a Debian user, and I like it a lot.  I've installed Arch, and I can't decide on which environment I should go with.  Then, this quesiton came to my mind: as to how a GNOME environment on Arch would differ from Debian-- don't they have the same things, would I have to manually install the packages I need for that environment?


For example if I use 'startxfce4' would I have an xubuntu enviornment-- so what's the point of Arch?

---

### Post by SOULRiDER on 2007-12-08
Im using Arch. The point is to have anything and just what you want, no unwanted extras.

I think, however that this thread would be better of in the Community Cafe or Archlinux forums instrad of the newbie section.

---

### Post by bapoumba on 2007-12-08
Moved to "Other OS Talk".

---

### Post by SunnyRabbiera on 2007-12-08
Arch is pretty good, the only thing I dont like is pacman

---

### Post by Rumor on 2007-12-08
> **SunnyRabbiera said:**
> Arch is pretty good, the only thing I dont like is pacman

And one of the things I most like about Arch is pacman. I have not found a package manager that equals it. To each their own, eh?

> **travismh said:**
> I'm confused by the purpose of Arch Linux.

[http://wiki.archlinux.org/index.php/The_Arch_Way](http://wiki.archlinux.org/index.php/The_Arch_Way)

Though I suppose a more concrete answer is in order. IMO the purpose of Arch is to put the control of one's computer fully in the user's hands in the simplest way. Give the user a working Linux environment with a base install and then let them do the rest. Arch gives me the tools to build what I want. I can install just the basic gnome or I can install the bells and whistles with gnome and gnome-extra. The developers do not assume any decisions for the user beyond what is included in the base install. From there you take it where you want it. you choose your desktop environment or your window manager; your applications; what daemons automatically start when you boot up; what modules you want loaded at start and so on.

Yes, there are other distros that do this same thing. But they don't have pacman; they don't have a rolling release and, at least in my experience, they are not as wonderfully simple as Arch.

---

### Post by fwojciec on 2007-12-08
I fully agree with what Rumor said about this...  

In comparison to Debian specifically though...  In Arch it is much easier to build your own packages or customize distro packages.  Arch doesn't try to create its own convention for doing things and gives you, pretty much, everything in vanilla flavor + a minimal set of sysadmin tools (which are probably the best thing about Arch) - this is why Arch is extremely customizable and flexible.  I also prefer the way Arch does initscripts (BSD style rather than System V style) - I think it produces a much more transparent system.  That's just off the top of my head...  The deeper you dig the more differences you'll notice.

---

### Post by david_2001 on 2007-12-08
I suppose that from an Arch perspective you could ask what's the point of Debian other than providing the basis for Ubuntu and thus these forums!  From a Slackware position, you could ask what's the point of Arch or Debian.  And so on and so forth...though if you want to see a fundamental difference, compare the contents of the Gnome System -> Administration menu of Ubuntu with that of Arch (mine's a little busy :-P)

---

### Post by crimesaucer on 2007-12-08
> **travismh said:**
> I'm confused by the purpose of Arch Linux.  Right now I'm a Debian user, and I like it a lot.  I've installed Arch, and I can't decide on which environment I should go with.  Then, this quesiton came to my mind: as to how a GNOME environment on Arch would differ from Debian-- don't they have the same things, would I have to manually install the packages I need for that environment?


For example if I use 'startxfce4' would I have an xubuntu enviornment-- so what's the point of Arch?

Read this: [http://wiki.archlinux.org/index.php/Arch_vs_Others](http://wiki.archlinux.org/index.php/Arch_vs_Others)

as for gnome, xfce4, or others... a Desktop Environment is going to be basically the same... with Arch, you can have the most bleeding edge version of them, and with pacamn, it is much better than apt in my opinion.

I feel that way about pacman because of the how simple it is to build AUR and ABS packages, as well as features of pacman, check the manual page: 

```

pacman(8)                                       Arch Linux Utilities                                      pacman(8)

NAME
       pacman - package manager utility

SYNOPSIS
       pacman <operation> [options] [packages]

DESCRIPTION
       pacman  is a package management utility that tracks installed packages on a Linux system. It features depen-
       dency support, package groups, install and uninstall hooks, and the ability to sync your local machine  with
       a remote ftp server to automatically upgrade packages. pacman packages are a zipped tar format.

       Since  version  3.0.0, pacman has been the frontend to libalpm, the "Arch Linux Package Management" library.
       This library allows alternative front ends to be written (for instance, a GUI front end).

OPERATIONS
       -A, --add (deprecated)
              Add a package to the system. Either a URL or file path can be specified. The package will  be  uncom-
              pressed  into  the  installation  root  and  the  database  will  be updated. The package will not be
              installed if another version is already installed. NOTE:  please  use  --upgrade  in  place  of  this
              option.

       -F, --freshen
              This is like --upgrade except it will only upgrade packages already installed on the system.

       -Q, --query
              Query  the package database. This operation allows you to view installed packages and their files, as
              well as meta-information about individual packages  (dependencies,  conflicts,  install  date,  build
              date,  size). This can be run against the local package database or can be used on individual .tar.gz
              packages. See QUERY OPTIONS below.
       -F, --freshen
              This is like --upgrade except it will only upgrade packages already installed on the system.

       -Q, --query
              Query  the package database. This operation allows you to view installed packages and their files, as
              well as meta-information about individual packages  (dependencies,  conflicts,  install  date,  build
              date,  size). This can be run against the local package database or can be used on individual .tar.gz
              packages. See QUERY OPTIONS below.

       -R, --remove
              Remove a package from the system. Files belonging to the specified package will be deleted,  and  the
              database will be updated. Most configuration files will be saved with a .pacsave extension unless the
              --nosave option is used. See REMOVE OPTIONS below.

       -S, --sync
              Synchronize packages. Packages are installed directly from the ftp servers, including  all  dependen-
              cies required to run the packages. For example, pacman -S qt will download and install qt and all the
              packages it depends on. You can also use pacman -Su to upgrade all packages that are out of date. See
              SYNC OPTIONS below.

       -U, --upgrade
              Upgrade  or  add  a  package  to  the  system.  Either a URL or file path can be specified. This is a
              "remove-then-add" process. See HANDLING CONFIG FILES for an explanation on how pacman takes  care  of
              config files.

       -V, --version
              Display version and exit.

       -h, --help
              Display  syntax  for  the  given  operation.  If no operation was supplied then the general syntax is
              shown.

OPTIONS
       --ask number
              Pre-specify answers to questions. It is doubtful whether this option even works, so I would not  rec-
              ommend  using  it. TODO: document this more, as I have no idea how it works or when you would use it,
              or if we should just dump it.

       -b, --dbpath path
              Specify an alternative database location (default is "/var/lib/pacman/"). This  should  not  be  used
              unless you know what you are doing.

       -d, --nodeps
              Skips  all  dependency  checks.  Normally,  pacman will always check a package's dependency fields to
              ensure that all dependencies are installed and there are no package conflicts in the system.

       -f, --force
              Bypass file conflict checks and overwrite conflicting files. If the  package  that  is  about  to  be
              installed  contains  files  that  are already installed, this option will cause all those files to be
              overwritten.  This option should be used with care, ideally not at all.

       -r, --root path
              Specify an alternative installation root (default is "/"). This should  not  be  used  as  a  way  to
              install software into /usr/local instead of /usr.  This option is used if you want to install a pack-
              age on a temporary mounted partition which is "owned" by another system. By using this option you not
              only  specify where the software should be installed, but you also specify which package database and
              cache location to use.

       -v, --verbose
              Output more status messages, such as the Root and DBPath.

       --cachedir dir
              Specify an alternative package cache location (default is "/var/cache/pacman/pkg/"). This should  not
              be used unless you know what you are doing.

       --config filepath
              Specify an alternate configuration file.

       --noconfirm
              Bypass  any  and all "Are you sure?" messages. It's not a good idea to do this unless you want to run
              pacman from a script.

       --noprogressbar
              Do not show a progress bar when downloading files. This can be useful for scripts  that  call  pacman
              and capture the output.

       --noscriptlet
              If  an  install  scriptlet  exists,  do  not execute it. Do not use this unless you know what you are
              doing.

QUERY OPTIONS
       -c, --changelog
              View the ChangeLog of a package. Not every package will provide one but it will be  shown  if  avail-
              able.

       -e, --orphans
              List all packages that were pulled in by a previously installed package but no longer required by any
              installed package.

       -g, --groups
              Display all packages that are members of a named group. If not name is specified,  list  all  grouped
              packages.

       -i, --info
              Display  information on a given package. The -p option can be used if querying a package file instead
              of the local database.

       -l, --list
              List all files owned by a given package. Multiple packages can be specified on the command line.

       -m, --foreign
              List all packages that were not found in the sync database(s). Typically these are packages that were
              downloaded manually and installed with --upgrade.

       -o, --owns file
              Search for the package that owns file.

       -p, --file
              Signifies  that  the package supplied on the command line is a file and not an entry in the database.
              The file will be decompressed and queried. This is useful in combination with --info and --list.

       -s, --search regexp
              This will search each locally-installed package for names or descriptions that matche regexp.

       -u, --upgrades
              Lists all packages that are out of date on the local system. This option works best if the sync data-
              base is refreshed using -Sy.

REMOVE OPTIONS
       -c, --cascade
              Remove  all target packages, as well as all packages that depend on one or more target packages. This
              operation is recursive.

       -k, --keep
              Removes the database entry only. Leaves all files in place.

       -n, --nosave
              Instructs pacman to ignore file backup designations.  Normally, when a file is removed from the  sys-
              tem the database is checked to see if the file should be renamed with a .pacsave extension.

       -s, --recursive
              Remove  each  target specified including all dependencies, provided that (A) they are not required by
              other packages; and (B) they were not explicitly installed by the user.  This option is analogous  to
              a backwards --sync operation.


SYNC OPTIONS
       -c, --clean
              Remove  old  packages  from the cache to free up disk space. When pacman downloads packages, it saves
              them in /var/cache/pacman/pkg. Use one --clean switch to remove old packages; use two to  remove  all
              packages from the cache.

       -e, --dependsonly
              Install  all dependencies of a package, but not the specified package itself.  This is pretty useless
              and we're not sure why it even exists.

       -g, --groups
              Display all the members for each package group specified. If no group names are provided, all  groups
              will be listed; pass the flag twice to view all groups and their members.

       -i, --info
              Display  dependency and other information for a given package. This will search through all reposito-
              ries for a matching package.

       -l, --list
              List all packages in the specified repositories. Multiple repositories can be specified on  the  com-
              mand line.

       -p, --print-uris
              Print  out  URIs  for  each  package  that  will  be  installed, including any dependencies yet to be
              installed. These can be piped to a file and downloaded at a later time, using a program like wget.

       -s, --search regexp
              This will search each package in the sync databases for names or descriptions that match regexp.

       -u, --sysupgrade
              Upgrades all packages that are out of date. Each currently-installed package  will  be  examined  and
              upgraded  if  a  newer  package exists. A report of all packages to upgrade will be presented and the
              operation will not proceed without user confirmation. Dependencies are automatically resolved at this
              level and will be installed/upgraded if necessary.

       -w, --downloadonly
              Retrieve all packages from the server, but do not install/upgrade anything.

       -y, --refresh
              Download  a  fresh  copy  of  the master package list from the server(s) defined in pacman.conf. This
              should typically be used each time you use --sysupgrade or -u. Passing two --refresh or -y flags will
              force a refresh of all package lists even if they are thought to be up to date.

       --ignore package
              Directs pacman to ignore upgrades of package even if there is one available.

HANDLING CONFIG FILES
       pacman  uses  the  same  logic as rpm to determine action against files that are designated to be backed up.
       During an upgrade, 3 md5 hashes are used for each backup file to determine the required action: one for  the
       original  file  installed,  one  for  the new file that's about to be installed, and one for the actual file
       existing on the filesystem. After comparing these 3 hashes, the follow scenarios can result:

       original=X, current=X, new=X
              All three files are the same, so overwrites are not an issue Install the new file.

       original=X, current=X, new=Y
              The current file is the same as the original but the new one differs.  Since the user  did  not  ever
              modify the file, and the new one may contain improvements or bugfixes, install the new file.

       original=X, current=Y, new=X
              Both  package  versions contain the exact same file, but the one on the filesystem has been modified.
              Leave the current file in place.

       original=X, current=Y, new=Y
              The new file is identical to the current file. Install the new file.

       original=X, current=Y, new=Z
              All three files are different, so install the new file with a .pacnew extension and  warn  the  user.
              The user must then manually merge any necessary changes into the original file.

CONFIGURATION
       See pacman.conf(5) for more details on configuring pacman using the pacman.conf file.

BUGS
       Bugs?  You  must  be  kidding,  there are no bugs in this software. But if we happen to be wrong, send us an
       email with as much detail as possible to <pacman-dev@archlinux.org>.

SEE ALSO
       pacman.conf(5), makepkg(8), libalpm(3)

       See the Arch Linux website at <http://www.archlinux.org> for more current information  on  the  distribution
       and the pacman family of tools.

AUTHORS
       Judd Vinet <jvinet@zeroflux.org>
       Aurelien Foret <aurelien@archlinux.org>
       Aaron Griffin <aaron@archlinux.org>
       Dan McGee <dan@archlinux.org>

       See the 'AUTHORS' file for additional contributors.

pacman version 3.0.0                                Feb 07, 2007                                          pacman(8)
(END) 


```

---

### Post by Tenken on 2007-12-08
Installing  XFCE for example you wouldn't have a desktop like xubuntu on Arch because xubuntu preinstalls packages like Firefox and Thunderbird, uses GDM, etc. where with Arch all you get is base xfce, you choose if you want to use Firefox, or Opera or whatever.

---

### Post by crimesaucer on 2007-12-08
> **Tenken said:**
> Installing  XFCE for example you wouldn't have a desktop like xubuntu on Arch because xubuntu preinstalls packages like Firefox and Thunderbird, uses GDM, etc. where with Arch all you get is base xfce, you choose if you want to use Firefox, or Opera or whatever.

Plus, the new xubuntu has a different menu that is more "Gnome-like" with "places" and things... at least that was how it was when I tried the 7.10 alpha tribe 5...

I sort of liked that better than just Xfce Menu. But other than that... to me at least, xfce4 and gnome were pretty much the same, same apps except ubuntu/xubuntu come with more apps installed... and Firefox and Thunderbird instead of Epiphany.


But with Arch, you start with the bare minimum and then add what you want. And there is an easy wiki install for almost anything.


My main reason to switch to **[COLOR="RoyalBlue"]Archlinux[/COLOR]** was because of it being so fast on i686... and it's true.

---

### Post by SunnyRabbiera on 2007-12-09
> **Rumor said:**
> And one of the things I most like about Arch is pacman. I have not found a package manager that equals it. To each their own, eh?

I just feel pacman is messy, its not as intuitive it seems as say apt/synaptic to me

---

### Post by crimesaucer on 2007-12-09
> **SunnyRabbiera said:**
> I just feel pacman is messy, its not as intuitive it seems as say apt/synaptic to me

Intuitive... I think pacman is a bit more intuitive because it picks all dependencies for all the packages, installs them, and will then print out any message of what you might have to do to any config files concerning the install/upgrade...

Or, for building a package, all you need to do is grab the PKGBUILD from the cvs page and put it in a directory, then run makepkg -S in that same directory, and it will download the package using wget, unpack it, build it and download all dependencies and install them, all with sudo privileges if needed... 


If I sudo apt-get install "something", it will pull it from the repository and install it, and some dependencies, recommending other dependencies and packages, that I might need. Then if I need them I have to sudo apt-get install again to get those packages. And it won't print a message if I need to change a setting in a config file somewhere... pacman does.


I like how in pacman, all I have to do is pacman -Sy "something", and it updates the repository and then targets all dependencies needed for that package and installs them all at once. I like how it gives notes of of anything that needs to be configured after installing a package or updating. I also like how a full sys upgrade is just pacman -Syu... not sudo apt-get update then sudo apt-get upgrade.


I guess aptitude is supposed to download all dependencies also, but I guess I used apt-get more when I was in xubuntu.

---

### Post by insane_alien on 2007-12-09
i use the yaourt pacaman wrapper, integrades tha AUR repos with the normal ones and you can use the ABS with it as well. of course i have it aliased to the more sensible yacman and to upgrade the system it is merely typing in 'upgrade' then my password.

---

### Post by b9anders on 2007-12-11
I just set up a fresh arch install (again) last week with xfce. Love the fact that I have to actively choose what I want instead of having to undo choices made for me.

It also gave me the chance to learn some new software. One of my aims was to not have to pull in gnome dependencies - so instead of network-manager I got to try out wicd, which is a fantastic networking tool.

It's a wonderful thing thing to know that there is nothing running in your system that you haven't actively approved by installing and setting up.

On startup, with xfce incl. compiz fusion running, I use less than 160 MB RAM. On a normal session of just a bit of terminal work, internet browsing and maybe a bit of file management, I never go above 256 MB ram usage (I have 512 mb ram). Even multitasking with opera, firefox, thunar, terminal, system monitor, gimp, mplayer, exaile, pidgin, abiword, mirage and squeeze I don't reach 500 mb usage. 
I don't think any of the buntus can match that. For a 3+ year old laptop, that kind of efficiency is gold, meaning I can still be bleeding edge, get all the bling I want and not have to endure any lag when starting apps or spinning the cube or anything. No other distro can do that for me.

As for pacman, it's great. Fastest package manager around and very powerful to boot. The only thing I am missing is some more refined search options. Makes you wonder what the hell the likes of suse are doing with yast.

---

### Post by kpkeerthi on 2007-12-11
* Rolling release: Keep updating and you are always on bleediing edge. No need for fresh install every 6 months or so
* Solid package management tool: pacman. Any experienced Arch user will agree that is fast, solid and functional - on par with aptitude/apt-get.
* Lean setup:  You build an Arch system by choosing only the packages/libraries you need. 
* i686 optimized: It does make a difference. 
* Portage like build system & Community Repository: The Arch Build System (ABS) & AUR - You can build your favorite packages from source and still have pacman control the version and future upgrades.

Its been a month since I installed Arch. Not even one problem so far. Very stable and solid distro.  

Here is a post that I made last month about Arch [http://ubuntuforums.org/showthread.php?t=604374](http://ubuntuforums.org/showthread.php?t=604374)

> 
I just feel pacman is messy, its not as intuitive it seems as say apt/synaptic to me

aptitude update => pacman -Sy
aptitude dist-upgrade => pacman -Syu
aptitude (re)install <package> => pacman -S <package>
aptitude remove <package> => pacman -Rs <package>
aptitude purge <package> => pacman -Rsn <package>
aptitude search <keyword> => pacman -Ss <keyword>
aptitude clean => pacman -Scc

I have these commands aliased to more meaningful constructs like pac-upgrade, pac-install and so on.

yaourt is another fine pacman wrapper. Just type "yaourt dvd" and you will be presented with all packages that has dvd in its name/description and you can select which one to install - search and install in one go.

---

### Post by K.Mandla on 2007-12-12
Wow, I was going to reply but I think everything I would suggest has already been mentioned. 

Ubuntu and Arch are, to me, opposite sides of the same coin. Ubuntu gives you everything you need at the start and sets it up for you. Arch gives you nearly nothing and lets you set it up how you want.

One leans toward usability and ease-of-setup. The other toward speed and efficiency.

I use both.

---

