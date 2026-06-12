---
title: "Building packages on a clean-room environmend"
date: 2006-06-30
forum: Outdated Tutorials &amp; Tips
---

### Post by mlind on 2006-06-30
This HOWTO tries to solve the common problems related to package building
[LIST]
[*]Prevent installing unwanted cruft on your system by doing the build process on a chroot (as a sandboxed, jailed) environment
[*]Making sure that the package works for other people too who are trying it
[*]Automatically downloaded dependencies make process smoother
[*](Easier to automate larger scale building process and testing)
[/LIST]


[INDENT]**[[COLOR="Blue"]pbuilder[/COLOR]]("http://www.netfort.gr.jp/~dancer/software/pbuilder-doc/pbuilder-doc.html")** is a tool which is *"used for creating and maintaining chroot environment and building Debian package in the chroot environment".*[/INDENT]




[INDENT]l'll be doing all the configuration locally only, by overriding the defaults. Another way is to make pbuilder settings to */etc/pbuilderrc*
and create your hooks on */etc/pbuilder/hook.d* accordingly[/INDENT]



[SIZE="4"]Installing[/SIZE]
[LIST=1]
[*]Install necessary packages
```

sudo aptitude install [COLOR="Blue"]pbuilder[/COLOR] devscripts

```

[*]Create the pbuilder environment
```

sudo pbuilder create

```
Now we have ready chroot environment for package building using Ubuntu defaults from **/etc/pbuilderrc**

[SIZE="1"](You can test environment by doing *sudo pbuilder login*. Command *exit* will leave the environment)[/SIZE]




[*]Override the default pbuilder settings
```

nano ~/.pbuilderrc

```
These are the file contents.
```

## Overrides /etc/pbuilderrc

# Default distribution
#DISTRIBUTION=feisty
[COLOR="DarkRed"]COMPONENTS="main restricted universe multiverse"
[/COLOR]
# Repositories
MIRRORSITE=http://archive.ubuntu.com/ubuntu
[COLOR="Navy"]#OTHERMIRROR="deb ${MIRRORSITE} ${DISTRIBUTION}-updates ${COMPONENTS}|deb ${MIRRORSITE} ${DISTRIBUTION}-security ${COMPONENTS}"
[/COLOR]
# For build results
BUILDRESULT=${HOME}/pbuilder/result

# Hooks for chroot environment
HOOKDIR=${HOME}/pbuilder/hook.d

# Mount directories inside chroot environment
BINDMOUNTS=${BUILDRESULT}

# Bash prompt inside pbuilder
export debian_chroot="pbuild$$"

# For D70results hook
[COLOR="Purple"]export LOCALREPO=${BUILDRESULT}[/COLOR]

[COLOR="Silver"]# Always include source package
#DEBBUILDOPTS="-sa"
[/COLOR]

```


[*]Create a *hook* that allows to include local packages as dependencies. This feature is ofter necessary
when the package you're building depends on other package(s) which is not found on Ubuntu repositories.
```

mkdir -p ~/pbuilder/result
mkdir ~/pbuilder/hook.d
nano ~/pbuilder/hook.d/**D70**results

```
These are the file contents
```

#!/bin/sh

echo "Executing hook: $0"

cd [COLOR="Purple"]${LOCALREPO}[/COLOR]
dpkg-scanpackages . /dev/null > Packages

**echo "deb file:[COLOR="Purple"]${LOCALREPO}[/COLOR] ./" >> /etc/apt/sources.list**
apt-get update

```
This code block creates a list of the packages in [COLOR="Purple"]${LOCALREPO}[/COLOR] folder for APT to use as repository.
Hook is always executed inside the chroot environment before the build phase, and packages are available
for APT to use on dependency resolving.


[*]Make the hook file executable
```

chmod +x ~/pbuilder/hook.d/D70results

```



[*]Update the chroot environment, so that new modules (repositories) are included too.
[COLOR="Silver"](Also, If you later need to change your chroot environment, use this command)[/COLOR]
```

sudo pbuilder update --override-config

```
[/LIST]



[SIZE="4"]Building packages[/SIZE]
[LIST]
[*]Building the packages should be as easy as
```

mkdir -p ~/packages/*mypackage*
cd ~/packages/*mypackage*
apt-get source *mypackage*

```

Then either
```

sudo **pbuilder** build *mypackage_x.x.x.**dsc***

```
or
```

cd *mypackage-x.x.x*
**pdebuild** --use-pdebuild-internal

```


[*]Succefully built packages are placed on **${BUILDRESULT}** folder
[*]These packages are also used as dependencies, so if you get weird behaviour when building other packages,
clean the contents of this folder and try again
[/LIST]



[SIZE="4"]Updating the base build environment[/SIZE]
[LIST]
[*]You should update the build environment when new updates are released for the base system
```

sudo pbuilder update --autocleanaptcache

```
[/LIST]



[SIZE="4"]A real life example: **nautilus**[/SIZE]

```

# enable Ubuntu source repositories on */etc/apt/sources.list*

mkdir -p ~/packages/nautilus
cd ~/packages/nautilus
apt-get source nautilus
sudo pbuilder build nautilus_2.14.1-0ubuntu9.dsc

#or alternatively do *pdebuild --use-pdebuild-internal* on nautilus folder

```



[SIZE="3"]Notes[/SIZE]
[LIST]
[*][COLOR="DarkRed"]Prefer **pbuilder** instead of pdebuild wrapper[/COLOR]
[*]pbuilder uses .orig.tar.gz and .diff.gz to build the package.
[*]If you change anything inside the source folder, source package must be rebuilt   for pbuilder (or use **pdebuild** instead).
[*]To rebuild source package
```

dpkg-source -b *folder*

```
[*]**/usr/share/doc/pbuilder/examples** contains some nice example hooks, especially [COLOR="DarkOrange"]C10shell[/COLOR] which is invoked when something goes wrong on build process.
You can find the build target files in /tmp/buildd.
[*][COLOR="Red"]If you want to pass DEB_BUILD_OPTIONS to pbuilder and you're using sudo, you must prevent reset of certain environment variables. Using **visudo**, add definition[/COLOR]
```

Defaults  env_keep+="DEB_* BUILD* PATH"

```
[*]Default dependency resolution logic using apt-get is quite slow. To make it way more faster, change the resolver to gdebi. Add to your ~/.pbuilderrc
```

[B]# use gdebi for dependency resolution
PBUILDERSATISFYDEPENDSCMD=/usr/lib/pbuilder/pbuilder-satisfydepends-gdebi
[/B]

```



[*]pdebuild doesn't support hooks.
[*]pdebuild ignores BUILDRESULT variable set on /etc/pbuilderrc. You can specify it using **--buildresult**. see pdebuild man page for details.
[*][COLOR="DarkOliveGreen"]if you want to improve pbuilder's speed, check out package called **cowdancer**[/COLOR]

[*]Useful way to clean out obsolete packages from pbuilder cache
```

sudo pbuilder update --autocleanaptcache

```
[/LIST]



[SIZE="3"]**[COLOR="Green"]References[/COLOR]**[/SIZE]
[LIST]
[*][http://manpages.debian.net/cgi-bin/display_man.cgi?id=4a633e1b1c199643c8e9c015b86604d5&format=html](http://manpages.debian.net/cgi-bin/display_man.cgi?id=4a633e1b1c199643c8e9c015b86604d5&format=html)
[*][http://manpages.debian.net/cgi-bin/display_man.cgi?id=d1ea566713f3ab748e56c30ff7d2108f&format=html](http://manpages.debian.net/cgi-bin/display_man.cgi?id=d1ea566713f3ab748e56c30ff7d2108f&format=html)
[*][http://www.netfort.gr.jp/~dancer/software/pbuilder-doc/pbuilder-doc.html](http://www.netfort.gr.jp/~dancer/software/pbuilder-doc/pbuilder-doc.html)
[*][http://edseek.com/~jasonb/articles/pbuilder_backports/index.html](http://edseek.com/~jasonb/articles/pbuilder_backports/index.html)
[/LIST]



**[edit]**
[LIST]
[*]Debian version of [COLOR="Blue"]pbuilder[/COLOR] doesn't currently have support for [COLOR="DarkRed"]COMPONENTS[/COLOR] option
[*]added OTHERMIRROR to ~/.pbuilderrc. This allows to use additional Ubuntu repositories. [COLOR="Red"]Not enabled by default[/COLOR].
If you enable it, use *pbuilder update --overrideconfig* to make the changes apply
[*]added PBUILDERSATISFYDEPENDSCMD to ~/.pbuilderrc. Makes dependency resolution very fast by using gdebi instead (In Ubuntu package only)
[/LIST]

---

### Post by mlind on 2006-06-30
As second usecase example, we'll test how self-buit packages which are not in official repositories 
work with this pbuilder setup.



Picture a scenario where you would want to build a package that's not on any Ubuntu repository,
but Debian upsteam has it available. You've cheked out the changelogs and verified that no major
dependencies have changed. [COLOR="Red"]If library is on **main** Ubuntu repository, think twice before actually upgrading it[/COLOR].




I won't be inserting any changelog info on the packages (or changing package naming), but you may do so if you want.
Use **dch -iDdapper** on the directory where sources were extracted (contains debian/ subdirectory).
```

cd *mypackage-x.xx*
dch -iDdapper

```



[SIZE="4"][COLOR="Blue"]gmpc[/COLOR][/SIZE]
[LIST]
[*]Add debian **unstable** to your */etc/apt/sources.list*
```

deb-src http://ftp.uk.debian.org/debian **unstable** main contrib non-free

```

[*]Get the sources
```

mkdir -p ~/packages/gmpc
cd ~/packages/gmpc
sudo aptitude update
apt-get source gmpc

```

[*]Try to build it first time
```

sudo pbuilder build gmpc_0.13.0-2.dsc

```

When you fist time try to build this package, you'll notice that it fails miserably because some dependency is missing.
This is usually caused by missing module (respository) on *pbuilderrc* or like in this case, unmet version number although package is available.
```

-> Considering  libmpd-dev (>=** 0.12.0**)
      Tried versions: **0.01-3**
  -> _Does not satisfy version_, not trying

```

Poking the [Ubuntu package info]("http://packages.ubuntulinux.org/dapper/libs/libmpd") (or use apt tools for this) for [COLOR="Green"]**libmpd**[/COLOR] you notice that it's really too old for satisfying
the build-time requirement. Debian upstream luckily provides [updated version]("http://packages.debian.org/unstable/libs/libmpd0").
[/LIST]



[SIZE="4"][COLOR="Green"]libmpd[/COLOR][/SIZE]
[LIST]
[*]Get [COLOR="Green"]libmpd[/COLOR] source from debian unstable
```

mkdir -p ~/packages/libmpd
cd ~/packages/libmpd
apt-get source libmpd

```

[*]Build libmpd
```

sudo pbuilder build libmpd_0.12.0-2.dsc

```
When build process is finished, new packages are available on **/var/cache/pbuilder/result**. Good thing is that
pbuilder chroot environment that was set previously, can see these packages too (using the provided hook).
[/LIST]


[SIZE="4"][COLOR="Blue"]gmpc[/COLOR][/SIZE] (2nd try..)
[LIST]
[*]Back to building gmpc
```

cd ~/packages/gmpc
sudo pbuilder build gmpc_0.13.0-2.dsc

```
[/LIST]



[SIZE="4"]Install[/SIZE]
[LIST]
[*]Install builded packages
```

cd **/var/cache/pbuilder/result**
sudo dpkg -i [COLOR="Green"]libmpd0_0.12.0-2_i386.deb[/COLOR] [COLOR="Blue"]gmpc_0.13.0-2_i386.deb[/COLOR]

```
[/LIST]

---

### Post by mlind on 2006-06-30
[SIZE="5"][COLOR="Blue"]mplayer[/COLOR][/SIZE]



[SIZE="4"]Initial setup[/SIZE]
[LIST]
[*]Disable any **multiverse** [COLOR="Red"]source[/COLOR] repositories from */etc/apt/sources.list*
[*]Add new source repository to /etc/apt/sources.list
```

deb-src http://www.debian-multimedia.org sid main

```
[*]Update package list
```

sudo aptitude update

```
[/LIST]



[SIZE="4"][COLOR="Green"]ffmpeg[/COLOR][/SIZE]
[LIST]
[*]Build ffmpeg first
```

mkdir -p ~/packages/ffmpeg
cd ~/packages/ffmpeg
apt-get source libavcodeccvs51-dev

```

[*]NOTE if you get error *"can't find a register in class 'GENERAL_REGS' while reloading 'asm'"* you must edit *debian/rules* and
change CFLAGS to appropriate values. For my system I had to use
```

CFLAGS = **-Wall**
LDCONFIG =

ifneq (,$(findstring noopt,$(DEB_BUILD_OPTIONS)))
        CFLAGS += -O0 -fPIC -DPIC
else
       ** CFLAGS += -pipe -fomit-frame-pointer**

```

[*]**If** you edited anything inside the source folder, you must regenerate the diffs against the original package. (Argument is the source folder)
```

dpkg-source -b ffmpegcvs-20060625

```

[*]Build
```

sudo pbuilder build ffmpegcvs_20060625-0.0.dsc

```
[/LIST]

[SIZE="4"][COLOR="Green"]libdivxdecore0[/COLOR][/SIZE]
[LIST]
[*]Build libdivxdecore0
```

mkdir -p ~/packages/libdivxdecore0
cd ~/packages/libdivxdecore0
apt-get source libdivxdecore0
sudo pbuilder build divx4linux_5.0.1-1.dsc

```
[/LIST]

[SIZE="4"][COLOR="Green"]libvstream[/COLOR][/SIZE]
[LIST]
[*]Build libvstream
```

mkdir -p ~/packages/libvstream
cd ~/packages/libvstream
apt-get source libvstream-**dev**
sudo pbuilder build vstream-client_1.2-0.1.dsc

```
[/LIST]



[SIZE="4"][COLOR="Blue"]mplayer[/COLOR][/SIZE]
[LIST]
[*]Get source first
```

mkdir -p ~/packages/mplayer
cd ~/packages/mplayer
apt-get source mplayer

```

[*]I had to change *mplayer-skin* (virtual) package dependency to ***mplayer-skins***. To do this, modify debian/*control.marillat* file
on mplayer source folder and either remove mplayer-skin dependency from mplayer-custom Package or change it to mplayer-skins
```

Package: mplayer
Architecture: any
Depends: ${shlibs:Depends}, **mplayer-skins**

```

[*]Regenerate the diffs against the original package (if you changed dependecies)
```

dpkg-source -b mplayer-1.0-pre8

```


[*]Build
```

**DEB_BUILD_OPTIONS=marillat** sudo pbuilder build mplayer_1.0-pre8-0.0.dsc

```
[/LIST]


[SIZE="4"]Install[/SIZE]
[LIST]
[*]Install mplayer and dependencies
```

sudo aptitude install libjack0.100.0-0 libdirectfb-0.9-22 libsvga1
cd /var/cache/pbuilder/result/
sudo dpkg -i mplayer_1.0-pre8-0.0_i386.deb libavcodeccvs51_20060625-0.0_i386.deb libdivxdecore0_5.0.1-1_i386.deb libavutilcvs49_20060625-0.0_i386.deb

```
[/LIST]

---

### Post by mlind on 2006-07-01
pbuilder can also be used to test your build scripts or other stuff on a sandboxed environment.
```

cp -R ~/packages/mypackage /tmp
sudo pbuilder login --bindmount /tmp/*mypackage*

apt-get install nano
*(start editing)*

```

Now */tmp/mypackage* is accessible/visible on chrooted environment (on / folder). Be aware that changes you make on **--bindmount**ed
folders are persisted and because you're logged as root, you'll get some unwanted permission issues. It may be 
better to use temporary folders.

Every package that you install, or any other change you make (excluding --bindmount folders) are not preserved.
So you can safely do almost anything you want.


If you login using **--save-after-login**, then all changes you make on the environment are persisted.
It's convinient way to install **nano** for example, which is not included by default.

---

### Post by PsychoTrauma on 2006-07-03
These guides are great mlind. Would it be possible to take the debian folder from say a older version of a program and use it for the latest cvs? How do you recommend going about compiling things without source debs?

---

### Post by mlind on 2006-07-04
[QUOTE=PsychoTrauma]These guides are great mlind. Would it be possible to take the debian folder from say a older version of a program and use it for the latest cvs? How do you recommend going about compiling things without source debs?
[/QUOTE]

Yes it's possible and you should do it like that. Let's say you have source package
foo-1.0.3 that's already been been debianized (it contains the debian folder)
and you'd like use that with new version foo-1.0.4 that you've downloaded.

```

~/packages/foo$  ls
foo-1.0.3            foo_1.0.3-1.dsc        **foo-1.0.4.tar.gz**
foo_1.0.3-1.diff.gz  foo_1.0.3.orig.tar.gz

```

To apply foo-1.0.3 debian folder contents (it will actually patch using .diff.gz file)
```

cd foo-1.0.3
**uupdate** ../foo-1.0.4.tar.gz

```


[QUOTE=PsychoTrauma]
After building files with the method above how would you go about removing everything so your system is the same before you started?[/QUOTE]

What method do you mean? If you use pbuilder then your system stays the same.
Everything is installed on chrooted environment which is always untarred from
same archive for each pbuilder session. 


Downloaded packages are stored on /var/cache/pbuilder/aptcache, which you
can clean using *pbuilder clean*. 

Sometimes, if you ctrl-c the pbuilder process /proc is not correctly umounted from
chroot environment and as result, /var/cache/pbuilder/build/ may contain folders
left behind by the build process. To get rid of these, see /etc/mtab and umount
everything pbuilder related, then *rm -rf* build folder's contents.


If you wanted to remove everything that this guide made you to install, then
```

sudo aptitude purge pbuilder fakeroot devscripts

```

and make sure /var/cache/pbuilder doesn't exist.

---

### Post by mlind on 2006-07-04
[QUOTE=PsychoTrauma]How do you recommend going about compiling things without source debs?[/QUOTE]

You should read [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

To debianize the source, use debhelper dh_make (see man debhelper). This will
create debian folder with initial scripts inside, maintainer guide explains briefly what
files are for. I also suggest to check out [cdbs]("https://perso.duckcorp.org/duck/cdbs-doc/cdbs-doc.xhtml") which is intended to do package maintaining easier.


You can test your packaging rules on pbuilder environment by doing
[LIST]
[*]pbuilder login --bindmounts *yourtestfolder*
[*]test by executing **debian/rules build** (test **install** and **clean** targets too)
[*]after executing install target, make sure debian/*yourpackage*/ contents look okay
[/LIST]

---

### Post by LKRaider on 2006-07-12
This is really great mlind !

Now I don't need to install tons of -dev packages on my main system : D
Great How-To!

I wish there was a GUI to debianize source packages tho (yeah, I'm lazy) :P

---

### Post by mlind on 2006-07-12
> **LKRaider said:**
> This is really great mlind !

Now I don't need to install tons of -dev packages on my main system : D
Great How-To!

I wish there was a GUI to debianize source packages tho (yeah, I'm lazy) :P

Thanks, that was why I wanted to look for alternative solutions, keep unwatend cruft out and be sure that package would actually work for others too.

I've modified proposed pbuilder configuration a bit. My BUILDRESULT, where builded packages appear is BUILDRESULT=/home/*myusername*/pbuilder/result, which makes package handling little easier.

You can set aliases to pbuilder commands to make invoking little non-verbosive, but working gui would be nice too.



Here's few tips too
[LIST]
[*]If you are testing packages using **pbuilder login --bindmounts** /path/to/mypackage, you can copy /usr/lib/pbuilder/**pbuilder-satisfydepends** to your hookdir and call it inside chroot environment to automatically fetch and install all dependencies.


[*]Hooks are found on /tmp/hooks/ inside chroot environment, and may be called explicitly too.


[*]You can run X-server applications "the easy, but not right" -way inside chroot, by bindmounting your /tmp folder to chroot environment. This contains necessary files for applications to use X. You also need to grant privileges for root user. This can be done by using xhost on normal environment.
```

xhost +local:root

```
(Remember to umount **bindmounted** /tmp before exiting the environment)
[/LIST]

---

### Post by PsychoTrauma on 2006-07-24
I seem to be having trouble with the new changes. Pbuilder no longer sees the files I have compiled previously. A example is I compiled libx264-dev for the newer version on ffmpeg. I go to compile ffmpeg and it can't find the libx264-dev deb in ~/pbuilder/result.

I also should add this is on a fresh install so I never had the previous method set up yet.

---

### Post by meff on 2006-07-24
> **PsychoTrauma said:**
> I seem to be having trouble with the new changes. Pbuilder no longer sees the files I have compiled previously. A example is I compiled libx264-dev for the newer version on ffmpeg. I go to compile ffmpeg and it can't find the libx264-dev deb in ~/pbuilder/result.

I also should add this is on a fresh install so I never had the previous method set up yet.

There is a typo up top in the .pbuilderrc file..

Where is says hook.d put hooks.d :)

Had the same problem. Good luck.

---

### Post by Chrissss on 2006-07-24
Hi There!

I'm trying to build my first "real" - not quick&dirty deb - this way. For my test i take sensors-applet-1.7.5 which i can build via the "usual" way without problems. So all necessary libs etc are installed.

When i try to create the package with
```
pdebuild --use-pdebuild-internal
```
I get this error
```
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
make: *** [config.status] Error 1
```
libxml-parser-perl is installed on my system, so i really don't know what to do.

Thanks
 Christoph

---

### Post by mlind on 2006-07-24
> **meff said:**
> There is a typo up top in the .pbuilderrc file..

Where is says hook.d put hooks.d :)

Had the same problem. Good luck.

oops, fixed. Thanks.

---

### Post by mlind on 2006-07-24
> **Chrissss said:**
> Hi There!

I'm trying to build my first "real" - not quick&dirty deb - this way. For my test i take sensors-applet-1.7.5 which i can build via the "usual" way without problems. So all necessary libs etc are installed.

When i try to create the package with
```
pdebuild --use-pdebuild-internal
```
I get this error
```
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
make: *** [config.status] Error 1
```
libxml-parser-perl is installed on my system, so i really don't know what to do.

Thanks
 Christoph

I'd say don't use pdebuild wrapper, use pbuilder instead. pdebuild will expose the build directory inside chroot and atleast that's not what I want. It doesn't support hooks either.

The idea of pbuilder is to use chroot environment. Think it as a minimal (and even static) environment required for compiling. It doesn't matter what libraries you've installed on your system, pbuilder executes on its own environment.

Does debian/control contain libxml-parser-perl? Use pbuilder build x.x.x.dsc instead.

---

### Post by LKRaider on 2006-07-26
Do you know anything about pbuilder-uml ? It seems like a cool thing, tho seems to be abandoned since 2003 or so.

I've seen this: [http://lists.alioth.debian.org/pipermail/pkg-uml-devel/2006-June/000247.html](http://lists.alioth.debian.org/pipermail/pkg-uml-devel/2006-June/000247.html)

Would be nice if they are working on a release for it :)

---

### Post by mlind on 2006-07-26
> **LKRaider said:**
> Do you know anything about pbuilder-uml ? It seems like a cool thing, tho seems to be abandoned since 2003 or so.

I've seen this: [http://lists.alioth.debian.org/pipermail/pkg-uml-devel/2006-June/000247.html](http://lists.alioth.debian.org/pipermail/pkg-uml-devel/2006-June/000247.html)

Would be nice if they are working on a release for it :)

pbuilder [User's manual]("http://www.netfort.gr.jp/~dancer/software/pbuilder-doc/pbuilder-doc.html#user-mode-linux-config") contains stuff about pbuilder-uml, but I understood that it's pretty much broken feature. I'm actually very happy with pbuilder once I figured out to put some hooks to make life easier. 

I've been playing around with **sbuild** too, which feels much faster than pbuilder. I suggest to try it out, although its documentation is bit poor.

---

### Post by mlind on 2006-08-02
I added optional OTHERMIRROR in ~/.pbuilderrc example. This allows pbuilder to use additional Ubuntu repositories (updates, security, backports, ..etc) when searching build dependencies.

---

### Post by anodizer on 2006-09-19
I'm trying to build a package and I got this error:

```
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
make: *** [config.status] Error 1
pbuilder: Failed autobuilding of package
W: no hooks of type C found -- ignoring
```

???
I thought pbuilder auto-installs dependencies.

---

### Post by mlind on 2006-09-19
> **anodizer said:**
> I'm trying to build a package and I got this error:

```
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
make: *** [config.status] Error 1
pbuilder: Failed autobuilding of package
W: no hooks of type C found -- ignoring
```

???
I thought pbuilder auto-installs dependencies.

/usr/lib/pbuilder-satisfydepends installs the build dependencies, but only the ones listed on debian/control. Which package are you trying to build?

debian/control should probably have **libxml-parser-perl** or similar on Build-Depends.

---

### Post by anodizer on 2006-09-19
> **mlind said:**
> Which package are you trying to build?

Banshee, again.

Edit: I added the file in the control file and now something else is missing. Isn't there any better way to automatically calculate dependencies than dh_make?

---

### Post by mlind on 2006-09-19
> **anodizer said:**
> Banshee, again.

Alright, is this a custom package or official Ubuntu package?

You can try the following:
```

#nice script to use inside temporary testing environment
cp /usr/lib/pbuilder/pbuilder-satisfydepends /path/to/pbuilder/hook.d
cp -R /path/to/banshee-x.xx.xx /tmp
sudo pbuilder login --bindmounts /tmp/banshee-x.xx.xx

#on pbuilder environment
cd /tmp/banshee-x.xx.xx
#automatically install Build-Depends on debian/control
/tmp/hook.d/pbuilder-satisfydepends
debian/rules build

#now, when build fails, install additional libxml-parser-perl 
apt-get install libxml-parser-perl
debian/rules clean
debian/rules build

#if build succeeds, exit the environment, otherwise keep finding that satisfies the condition

```

When you've found the missing package(s), add it to debian/control and then rebuild source package
```

dpkg-source -b banshee-x.xx.xx

```

And build with pbuilder again.

---

### Post by mlind on 2006-09-19
> **anodizer said:**
> 
Edit: I added the file in the control file and now something else is missing. Isn't there any better way to automatically calculate dependencies than dh_make?

dh_make doesn't calculate dependencies for you, it just applies default debinization templates to source directory.
To find out the correct build-depends is a matter of trial and error.

Why not use existing banshee packaging information? It should have most of the build depends already figured.

---

### Post by anodizer on 2006-09-20
Hey mlind, how can I add a Source repository?

```
E: You must put some 'source' URIs in your sources.list
```

---

### Post by mlind on 2006-09-20
> **anodizer said:**
> Hey mlind, how can I add a Source repository?

```
E: You must put some 'source' URIs in your sources.list
```

You shouldn't need to use source repositories in pbuilder environment, but you can denfine one in several ways if needed. In /etc/apt/sources.list while  doing login, using a hook (like F70results does) or using .pbuilderrc and invoking pbuilder with --override-config.

I'm interested why do you need a source repository in pbuilder environment, or do you just mean a source repository in general?

---

### Post by anodizer on 2006-09-20
I'm trying to "apt-get build-dep xxx"

---

### Post by mlind on 2006-09-20
> **anodizer said:**
> I'm trying to "apt-get build-dep xxx"

Then just add source repository locations to /etc/apt/sources.list and update package lists. apt-get build-dep will cause a mess though..

---

### Post by anodizer on 2006-09-20
I managed to build it at last. With some problems with icons though, it sure is tough to build proper debian packages.

Btw, thanks for the help mlind.

---

### Post by mlind on 2006-09-21
> **anodizer said:**
> I managed to build it at last. With some problems with icons though, it sure is tough to build proper debian packages.

Btw, thanks for the help mlind.

Yeah, at least if you have to do it from scratch. A lot of software is already packaged though, so you can use it when building newer upsteam version.

---

### Post by wesley_of_course on 2007-04-01
Wesley here ;

 Greetings !   Very interested in trying this , correctly assuming this applies to Feisty ?

           Great 'tut ,would like to try this out !  Thanks again for your timely response .

---

### Post by mlind on 2007-04-01
> **wesley_of_course said:**
> Wesley here ;

 Greetings !   Very interested in trying this , correctly assuming this applies to Feisty ?

           Great 'tut ,would like to try this out !  Thanks again for your timely response .

Yes, this tut should apply all Debian/Ubuntu releases which feature pbuilder. This means all Ubuntu distributions, from Warty to Feisty.

---

### Post by LKRaider on 2007-04-23
Would be nice to update this to cowbuilder + ccache, it really speeds things up :)

---

### Post by mlind on 2007-04-24
> **LKRaider said:**
> Would be nice to update this to cowbuilder + ccache, it really speeds things up :)

Yeah, I'll try to add the cowbuilder stuff in near future. I've been using cowbuilder ever since I discovered it, and it's great. COW stuff speeds up the overall process nicely. Does using cowbuilder + ccache make significant difference btw? I've seen posts about pbuilder + ccache though, but I haven't tried it yet myself.

---

### Post by LKRaider on 2007-04-25
Yep ccache only really helps if you have to recompile a package several times, like, for instance, when debugging patches and so on.

For one time compiles, it makes no difference.

---

### Post by H.E. Pennypacker on 2007-05-13
This guide is far too confusing.  I am not even sure what this guide does.  I am trying to create a .deb file from source, and I don't know if this guide will help.  I am confused, because this guide is nothing like the one I followed the first time I created a deb package.

This is the guide I followed before:

[http://doc.gwos.org/index.php/Deb_Guide](http://doc.gwos.org/index.php/Deb_Guide)

I can't follow it now, because I don't have a config file and I don't know how to create one.

---

### Post by mlind on 2007-05-13
@ H.E. Pennypacker
This guide is about building binaries from a debian source package in a minimal temporary sandbox. This guide is not about creating a debian source packages.

---

### Post by H.E. Pennypacker on 2007-05-13
mlind, I have downloaded ndiswrapper (the source), and I am trying to create a deb file.  I do not want to use checkinstall.  Will your guide work for me?

Please do not ask why I am trying to create a deb file for ndiswrapper.  I just am.  I know I can download ndiswrapper from Synaptic, and that's why I ask that you do not ask me why I am creating a package.

---

### Post by mssever on 2007-05-14
> **H.E. Pennypacker said:**
> mlind, I have downloaded ndiswrapper (the source), and I am trying to create a deb file.  I do not want to use checkinstall.  Will your guide work for me?

Please do not ask why I am trying to create a deb file for ndiswrapper.  I just am.  I know I can download ndiswrapper from Synaptic, and that's why I ask that you do not ask me why I am creating a package.

This thread is for building packages that have already been debianized. If a Debian source package meets your needs, you can use this howto. If you're using the vanilla ndiswrapper source, you'll have to create a debian subfolder with the proper contents, which this guide doesn't address.

EDIT: You also will have to build Debian source package before you can build a .deb. I use ```
debuild -S
``` to build a Debian source package. Generating a proper debian directory is most of the battle. But, you might cheat and use (and modify) an existing Debian package for starters.

---

### Post by mlind on 2007-05-14
> **H.E. Pennypacker said:**
> mlind, I have downloaded ndiswrapper (the source), and I am trying to create a deb file.  I do not want to use checkinstall.  Will your guide work for me?

Please do not ask why I am trying to create a deb file for ndiswrapper.  I just am.  I know I can download ndiswrapper from Synaptic, and that's why I ask that you do not ask me why I am creating a package.

What mssever said :mrgreen:

Have you tried ndiswrapper in Debian unstable?
```

# deb-src http://ftp.debian.org/debian unstable main contrib non-free

mkdir /tmp/ndiswarpper
cd /tmp/ndiswrapper
apt-get source ndiswrapper
sudo pbuilder build ndiswrapper_1.43-1.dsc

```
?

---

### Post by H.E. Pennypacker on 2007-05-14
msserver, thanks for the explanation.  

> If you're using the vanilla ndiswrapper source, you'll have to create a debian subfolder with the proper contents, which this guide doesn't address.

That's what I am trying to do, but I have not found a thorough guide on how to do this.  I have found guides on creating .deb packages, but they specifically mention I need a config file.  The problem is that ndiswrapper's source does not come with a config file (while most other applications do, since you do the ./configure step while compiling).  I have found nothing to show me how to create a config file.  

mlind, I have not tried that.  I already have the source (downloaded from ndiswrapper's website) so I don't know why you are telling me to apt-get it.  Also, I do not know enough about pbuilder, but I don't think it does what I am trying to do.  The only thing I am trying to do is create a deb package ..exactly like the ones you'll find on [www.getdeb.net](www.getdeb.net) or anywhere else.

---

### Post by mlind on 2007-05-14
What I was trying to suggest is not to reinvent the wheel when someone has already done it (debianized the source for you). If my earlier posts left you wondering, then this is not thread to help you further, sorry.

---

### Post by mssever on 2007-05-14
> **H.E. Pennypacker said:**
> msserver, thanks for the explanation.  

That's what I am trying to do, but I have not found a thorough guide on how to do this.  I have found guides on creating .deb packages, but they specifically mention I need a config file.  The problem is that ndiswrapper's source does not come with a config file (while most other applications do, since you do the ./configure step while compiling).  I have found nothing to show me how to create a config file.  

Debianizing source from scratch isn't a simple process. I tried doing that a while back and found it to be really frustrating due to the lack of documentation that I could understand.

What I do--and I don't know if it will suit your purpose, but I suspect it will--is put the following debian source lines in my sources.list ```
deb-src http://http.us.debian.org/debian unstable main
deb-src http://http.us.debian.org/debian unstable non-free
deb-src http://http.us.debian.org/debian unstable contrib
```Then I do ```
sudo apt-get update && apt-get source whatever
``` Now, you can modify the source however you want. When you're satisfied, you need to change the version number, or the package won't behave right. Add an entry to debian/changelog. This is where the version number is set. The file format is extremely strict about indentation, spacing, etc. Unless you have a reason to do otherwise, your version number should be tacked to the end of the existing version string as a modifier string and your revision number. For example, I add mssever1, mssever2, etc.

Next, cd to the root directory of the source tree and type ```
debuild -S
```If it completes successfully, you'll have a new source package in the parent directory with the new version number. You can build it with pbuilder per the instructions in the original post.

---

### Post by Technoviking on 2007-05-17
It is taking forever for sudo pbuilder create to run. Is that normal?

Mike

---

### Post by mlind on 2007-05-17
> **Mike said:**
> It is taking forever for sudo pbuilder create to run. Is that normal?

Mike

If you're using default Ubuntu mirror (archive.ubuntu.com/ubuntu), then try using an alternative mirror from [https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors). Downloading packages from main mirror is usually very slow if new Ubuntu has been recently released.

```

sudo pbuilder create --distribution feisty --mirror http://mirrors.kernel.org/ubuntu

```

---

### Post by 12345 on 2007-05-30
1. question:

**[COLOR="DarkRed"]pdebuild[/COLOR]** can sign the package, 
but what is with **[COLOR="DarkGreen"]pbuilder[/COLOR]**, can it do the job too? and how?


2. question:

With **[COLOR="DarkGreen"]sudo pbuilder build[/COLOR]**, i get a lot of errors like this. What does that mean?:

> dpkg-genchanges: warning: no utmp entry available and LOGNAME not defined; using uid of process (1234)
dpkg-architecture: warning: no utmp entry available and LOGNAME not defined; using uid of process (1234)
dpkg-parsechangelog: warning: no utmp entry available and LOGNAME not defined; using uid of process (1234)

thanks

---

### Post by mlind on 2007-05-30
> **12345 said:**
> 1. question:

**[COLOR="DarkRed"]pdebuild[/COLOR]** can sign the package, 
but what is with **[COLOR="DarkGreen"]pbuilder[/COLOR]**, can it do the job too? and how?


I'm using **debsign** to sign packages. see *man debsign* for the usage.
After binaries have been built, I just just pass .changes file to debsign
```

debsign *mypackage**.changes

```

> **12345 said:**
> 
With **[COLOR="DarkGreen"]sudo pbuilder build[/COLOR]**, i get a lot of errors like this. What does that mean?

Those are normal warnings, although look alarming. You can check pbuilder manual for the [ details]("http://www.netfort.gr.jp/~dancer/software/pbuilder-doc/pbuilder-doc.html#LOGNAME").

---

### Post by Carlos Santiago on 2007-05-31
Hi.
I am interested in building a deb package with all the configuration files needed to connect to my ISP and using my modem.

I dont need to compile any software, just need to copy some files do a specific path, and append some text to a file that already exist in the system.

Also, as I need to use setserial, that package should be on the requisits.

After this being done and tested for my specific modem and to my ISP, I would like to make it work with other modems and other ISPs.

What is the simpler way to do this?

---

### Post by LKRaider on 2007-06-02
Any tips on how to upgrade an existing base.cow (or base.tgz) from one distribution version to another?
Should I just delete the old one and create a new?

What's the best option? Any other tips regarding this?

I'm currently creating a second base dir for feisty (/var/cache/pbuilder/base-feisty.cow), keeping the base.cow I used for dapper on another folder (/var/cache/pbuilder/base.cow), which I'll probably delete later.

---

### Post by mlind on 2007-06-02
> **LKRaider said:**
> Any tips on how to upgrade an existing base.cow (or base.tgz) from one distribution version to another?
Should I just delete the old one and create a new?

What's the best option? Any other tips regarding this?

I'm currently creating a second base dir for feisty (/var/cache/pbuilder/base-feisty.cow), keeping the base.cow I used for dapper on another folder (/var/cache/pbuilder/base.cow), which I'll probably delete later.

Well, I dunno about best practices, but I've always created new base.cow or .tgz for each distribution and maintained it using --update --autocleanaptcache flags. I guess you get the same result using the --override-config option as noted in pbuilder manual.

To upgrade base.cow from edgy to feisty
```

sudo cowbuilder --update --distribution feisty --override-config --autocleanaptcache

```

---

### Post by tyraen on 2007-06-14
For some reason "pbuilder create" kept failing while trying to download the release file.  I did --debug and pasted the URL it spat out and it worked fine, and then I ran debootstrap with the params that --debug gave me and that worked fine too.

Anyways, now that I've got the debootstrap done, and since "pbuilder create" still isn't working, is there any way to point it to the directory of the debootstrap contents to have it just continue from that step?  I checked out the parameters but none seem to do the trick (maybe it can't be done...).

Thanks!

---

### Post by mlind on 2007-06-25
> **tyraen said:**
> For some reason "pbuilder create" kept failing while trying to download the release file.  I did --debug and pasted the URL it spat out and it worked fine, and then I ran debootstrap with the params that --debug gave me and that worked fine too.

Anyways, now that I've got the debootstrap done, and since "pbuilder create" still isn't working, is there any way to point it to the directory of the debootstrap contents to have it just continue from that step?  I checked out the parameters but none seem to do the trick (maybe it can't be done...).

Thanks!

Do you still have the problem? You can use pbuilder option **--debootstrapopts** to pass options for debootstrap when invoking pbuilder create. see pbuilder manual and debootstrap manual for details (man pbuilder and man deboostrap).

For example
```

pbuilder create --debootstrapopts --arch=amd64 --debootstrapopts --keep-debootstrap-dir

```

---

### Post by mlind on 2007-06-25
I just found out how useful it is to define
```

PBUILDERSATISFYDEPENDSCMD=/usr/lib/pbuilder/pbuilder-satisfydepends-gdebi

```
in your ~/.pbuilderrc or /etc/pbuilderrc

dependency resolution time went down to few seconds. dammit.

---

### Post by shirilover on 2007-11-28
> **mlind said:**
> I just found out how useful it is to define
```

PBUILDERSATISFYDEPENDSCMD=/usr/lib/pbuilder/pbuilder-satisfydepends-gdebi

```
in your ~/.pbuilderrc or /etc/pbuilderrc

dependency resolution time went down to few seconds. dammit.

After using the above, I get the following when attempting to backport transmission-0.94
```

E: There are problems and -y was used without --force-yes
E: pbuilder-satisfydepends failed.

```

---

### Post by mlind on 2007-11-28
> **shirilover said:**
> After using the above, I get the following when attempting to backport transmission-0.94
```

E: There are problems and -y was used without --force-yes
E: pbuilder-satisfydepends failed.

```

[https://bugs.launchpad.net/ubuntu/+source/pbuilder/+bug/123068](https://bugs.launchpad.net/ubuntu/+source/pbuilder/+bug/123068)
You need to add --force-yes in /usr/lib/pbuilder/pbuilder-satisfydepends

---

