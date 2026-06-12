---
title: "Quick and dirty HOWTO for Rhythmbox 0.9.5 for Dapper"
date: 2006-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by mlind on 2006-06-20
[INDENT]This is a simple guide for building and installing new Rhythmbox straight
from upstream using existing debian templates for RB.
**Use at your own risk**.[/INDENT]




[SIZE="4"]Initial setup[/SIZE]
[LIST]
[*]It's suggested to build this using chrooted build system like [**pbuilder**]("http://www.ubuntuforums.org/showthread.php?t=206382") or sbuild. If you do, you don't need to install any other dependencies than devscripts package.
 

[*]Alternatively you can use **debfoster**. Run run it  once and answer 'yes' (or no if you know what you're doing) asked questions. This way you set *default* state for installed packages and can easily uninstall all RB build dependencies after building. You can later "reset" debfoster using -n parameter _after_ the whole buildprocess is complete and installed dependencies have been removed.
[/LIST]


[SIZE="4"]Configuring build environment[/SIZE]
[LIST]
[*]Install required packages for building
```

sudo aptitude install build-essential cdbs devscripts dh-make fakeroot

```

[*]Setup your local environment
```

mkdir -p ~/packages/rhythmbox
cd ~/packages/rhythmbox

```
[/LIST]

[SIZE="4"]Getting the sources[/SIZE]
[LIST]
[*]We'll use debian's package as base package for the source. Add new source
reposirtory on /etc/apt/sources.list
```

deb-src http://ftp.uk.debian.org/debian **unstable** main contrib non-free

```
**Note!**


[*]Fetch RB's source from debian repository. _Don't use sudo while getting the source package_!
Before doing this, make sure you're at the rhythmbox directory you created earlier.
```

sudo apt-get update && apt-get source rhythmbox
cd rhythmbox-0.9.5

```
[/LIST]


[SIZE="4"]Preparing the new package[/SIZE]
[LIST]
[COLOR="Red"][*]You must edit *debian/control* and *debian/control.in* files and _replace_ libgnome-media-dev with **gnome-media** on Build-Depends: section,
Debian on Ubuntu seem to have difference regarding to package naming.[/COLOR]

[*]Insert new changelog entry
```

**dch [B]-i**[/B]

```

[*]Insert your own comments about new version
```

rhythmbox (0.9.5-**1ubuntu1**) dapper; urgency=low

  * debian/control,
    debian/control.in:
    - Changed libgnome-media-dev to gnome-media

 -- Firstname Lastname <yourname@mail.com>  Tue, 20 Jun 2006 22:11:35 +0300

```
Save file after modifying it (contents will actually be written on debian/changelog)






[*]If you want to enable experimental ipod writing support, add this to **debian/rules**
```

DEB_CONFIGURE_EXTRA_FLAGS += --enable-ipod-writing

```

[/LIST]


[SIZE="4"]Installing required build dependencies[/SIZE]
[LIST]
[*]Run **dpkg-checkbuilddeps** and install _all_ listed packages. Those are needed for building this package. For RB 0.9.5 build dependencies are
```

sudo aptitude install libgnome2-dev libgtk2.0-dev libgnomeui-dev libgnomevfs2-dev docbook-xsl docbook-utils gnome-pkg-tools libxt-dev libdbus-glib-1-dev libnautilus-burn-dev libhal-dev libtotem-plparser-dev liblircclient-dev libsoup2.2-dev libavahi-client-dev libmusicbrainz4-dev libavahi-glib-dev libtool libgpod-dev libnotify-dev libglade2-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev zlib1g-dev libx11-dev libglib2.0-dev gtk-doc-tools libsexy-dev python-gtk2-dev python-dev

```
[/LIST]

[SIZE="4"]Building the package[/SIZE]
[LIST]
[*]Build rhythmbox packages
```

dpkg-buildpackage -rfakeroot -us -uc

```

[*]Install new rhythbox
```

sudo dpkg -i ../rhythmbox_0.9.5-0ubuntu1_i386.deb

```
[/LIST]

[SIZE="4"]Removing the build dependencies[/SIZE]
[LIST]
[*]If you installed **debfoster** as suggested in the beginning, you can now clear
all build dependencies by running debfoster again and answering **p** (as purge) for
all questions regarding to applications and libraries installed on build process.


[*]Remove/comment debian source repository from/etc/apt/sources.list

[/LIST]



**[edit]**
I changed howto to use debian experimental repository instead, because
changelog contained some important build rules. There's also instructions
to apply launchpad integration pacthes if anyone wants to use the feature.


**[edit 2]**
[LIST]
[*]Added suggestion to build using pbuilder
[*]Changed to use debian unstable repository
[*]Removed confusing steps about applying launchpad integration patches
[/LIST]

---

### Post by mlind on 2006-06-20
[SIZE="4"]Building **music-applet** from upstream repository[/SIZE]


[INDENT][music-applet]("http://web.ics.purdue.edu/~kuliniew/music-applet/") package hasn't landed on Ubuntu repositories yet, but
luckily we can use already debianized package directly from upsteam without any
modifications to debian/control or debian/rules. This way we don't have to start
from scratch. *This one of the nice benefits of Ubuntu being Debian derivation*



You should use **[pbuilder]("http://www.ubuntuforums.org/showthread.php?t=206382")** to build the package. Alternatively you can use **debfoster** for tracking build dependencies as stated on post above.

[/INDENT]




[LIST]
[*]Insert Debian unstable repository in /etc/apt/sources.list
```

deb-src http://ftp.uk.debian.org/debian sid main contrib non-free

```


[*]Configure build environment like above, exept this time for music-applet
```

mkdir -p ~/packages/music-applet
cd ~/packages/music-applet

```

[*]Get the source package from debian unstable. At time of writing version was 0.9.2.
_Don't use sudo while getting the source package_! Before doing this, make sure
you're at the music-applet directory you created earlier.
```

sudo apt-get update && apt-get source music-applet
cd music-applet-0.9.2

```

[*]Open editor for changelog
```

dch **-i**

```
[*]Insert your own build info and save the file
```

music-applet (0.9.2-**0ubuntu1**) unstable; urgency=low

  * Ubuntunized

 -- Fistname Lastname <yourname@yourmail.com>  Wed, 21 Jun 2006 18:57:08 +0300

```


[*]Check build dependencies
```

dpkg-checkbuilddeps

```

Install any missing packages using aptitude or apt-get (like above). Version 0.9.2 required no changes
to debian/control regarding to dependencies.



[*]Build package (by default, this process will also build deprecated rhythmbox-applet, but can prevent this by
removing rhythmbox-applet package information from **debian/control** file. Removing isn't required though.)
```

dpkg-buildpackage -rfakeroot -us -uc

```

[*]Install music-applet
```

sudo dpkg -i ../music-applet_0.9.2-0ubuntu1_i386.deb

```

[*]Remove Debian unstable repository from /etc/apt/sources.list
[*]Clear build dependencies using **debfoster**
[/LIST]

---

### Post by Technoviking on 2006-06-21
Great howto. Bravo.=D> 

If you want just to download and install the debs, you can find info here.
[http://www.mikesplanet.net/?p=37](http://www.mikesplanet.net/?p=37)

---

### Post by mlind on 2006-06-21
[QUOTE=Mike]Great howto. Bravo.=D> 

If you want just to download and install the debs, you can find info here.
[http://www.mikesplanet.net/?p=37](http://www.mikesplanet.net/?p=37)[/QUOTE]

Thanks Mike :)

New RB with all new features and bugfixes sure feels great!

---

### Post by kupajava on 2006-06-21
I get this when I run dpkg-buildpackage -rfakeroot -us -uc

dpkg-buildpackage: source package is rhythmbox
dpkg-buildpackage: source version is 0.9.5-0ubuntu1
dpkg-buildpackage: source changed by X  <X@localhost.localdomain>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
/usr/bin/dpkg-buildpackage: line 175: fakeroot: command not found

Any Ideas?

---

### Post by mlind on 2006-06-21
[QUOTE=kupajava]I get this when I run dpkg-buildpackage -rfakeroot -us -uc

dpkg-buildpackage: source package is rhythmbox
dpkg-buildpackage: source version is 0.9.5-0ubuntu1
dpkg-buildpackage: source changed by X  <X@localhost.localdomain>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
/usr/bin/dpkg-buildpackage: line 175: fakeroot: command not found

Any Ideas?[/QUOTE]

oops.. fakeroot package must be installed, I thought it was part of devscripts package. I'll update the requirements, thanks.

try doing
```

sudo aptitude install fakeroot

```
and then continue

/edit typo

---

### Post by kupajava on 2006-06-21
That worked!  Thanks!

---

### Post by kupajava on 2006-06-21
spoke too soon, now I get this...

checking for RHYTHMBOX... configure: error: Package requirements (  gtk+-2.0 >= 2.6.0                                        libgnomeui-2.0  libglade-2.0                                             launchpad-integration  gnome-vfs-2.0 >= 2.7.4                   gnome-vfs-module-2.0) were not met:

Package glitz was not found in the pkg-config search path.
Perhaps you should add the directory containing `glitz.pc'
to the PKG_CONFIG_PATH environment variable
Package 'glitz', required by 'cairo', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables RHYTHMBOX_CFLAGS
and RHYTHMBOX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

make: *** [config.status] Error 1

---

### Post by mlind on 2006-06-21
[QUOTE=kupajava]spoke too soon, now I get this...

checking for RHYTHMBOX... configure: error: Package requirements (  gtk+-2.0 >= 2.6.0                                        libgnomeui-2.0  libglade-2.0                                             launchpad-integration  gnome-vfs-2.0 >= 2.7.4                   gnome-vfs-module-2.0) were not met:

Package glitz was not found in the pkg-config search path.
Perhaps you should add the directory containing `glitz.pc'
to the PKG_CONFIG_PATH environment variable
Package 'glitz', required by 'cairo', not found

[config.status] Error 1[/QUOTE]

hmm.. You're building this for Dapper right ? 
Did you install all packages that were listed on "Installing required build dependencies" ?
There are total of **33** dependecy packages that you must install on that step.

I just tested building RB myself from clean table and everything worked as expected.

---

### Post by kupajava on 2006-06-21
yep, definately using dapper and did cut and paste on every step.

is there a way to undo the whole process and start over?  I imagine I must have done something wrong somewhere and maybe I can just clean it out and redo the whole thing.

Thanks!

---

### Post by mlind on 2006-06-21
[QUOTE=kupajava]yep, definately using dapper and did cut and paste on every step.

is there a way to undo the whole process and start over?  I imagine I must have done something wrong somewhere and maybe I can just clean it out and redo the whole thing.

Thanks![/QUOTE]

Yes, you can use **debclean** on rhythmbox build folder to clean the build tree,
and use **debfoster** to remove all installed build packages (answering p
to its questions removes package and it's dependencies completely).

You can even remove folders and their contents from ~/packages/rhythmbox folder
using *rm -rf* if you wish.

---

### Post by Laterix on 2006-06-23
Thanks for the guide! I just can't figure out how to use Lyric plugin. Where are the lyrics?

EDIT: Ok, I found them. Click on song and select Properties -> Lyrics. Could be easier...

---

### Post by mlind on 2006-06-23
I updated instructions to use debian experimental instead, because there was
somewhat important changes on packaking rules.

@ kupajava
Errors you got were caused by missing liblaunchpad-integration-dev package which
was required by launchpad integration patches. This feature is not required, but
it's included on official Ubuntu packages.

I also added steps to get that feature on current source by pulling the patches from
old RB source.

Sorry for the inconvenience.

---

### Post by Technoviking on 2006-06-23
I rebuilt the package but I'm still not getting notifications.

---

### Post by FredB on 2006-06-23
Great Howto. But is there any hope to have RB 0.9.5 backported... Not that I hate compiling, but such a long howto makes me lazy.

Please don't kick my a-- ;)

---

### Post by mlind on 2006-06-23
[QUOTE=Mike]I rebuilt the package but I'm still not getting notifications.[/QUOTE]

you mean song balloon notifications from tray ?

---

### Post by Technoviking on 2006-06-23
[QUOTE=mlind]you mean song balloon notifications from tray ?[/QUOTE]
Yes.

---

### Post by mlind on 2006-06-23
[QUOTE=Mike]Yes.[/QUOTE]

I though all balloon tray fixes were already merged upstream..

I tried looking through Ubuntu's RB [changelog]("http://changelogs.ubuntu.com/changelogs/pool/main/r/rhythmbox/rhythmbox_0.9.3.1-0ubuntu9/changelog") where notifications (usually?) work, but closest suspect I could find was

```

* debian/patches/03_escaping_for_notification_bubble.patch:
    - fix the notification bubble title escaping issue (Ubuntu: #31101)

```

You could try to build 0.9.5 with this patch, dunno if it helps.

---

### Post by Technoviking on 2006-06-23
No Joy
```
Trying patch debian/patches/03_escaping_for_notification_bubble.patch at level 0...1...2...failure.
make: *** [debian/stamp-patched] Error 1
```

---

### Post by mlind on 2006-06-23
okay, I'll have to poke that a bit.

I noticed I had screwed up with the required dependencies already. Debian has package called libcddb2-dev which doesn't exist in ubuntu, but you need to replace it
with dependency called **libcddb2-dev**, not gnome-media like I thought before.
Oops.

/edit

scratch that. gnome-media package seems to include development libraries too. strange.

---

### Post by mlind on 2006-06-24
I think that notification bubble not showing up is a RB regression bug. I played like 30
songs, but I saw it appearing **once**. So feature is definetly there.

I was able to apply only patches 01, 02 and 16 from Ubuntu's RB 0.9.3, so other
patches must have been merged already.

---

### Post by PsychoTrauma on 2006-06-24
I used the guide and compiled rhythmbox just fine on my amd64 machine. I am getting the notification bubble on every new track so I don't seem to have the problems mentioned earlier.

Thank you for the guide mlind.

---

### Post by amoore on 2006-06-25
I was just wondering if anyone has gotten the Blue Remote plugin or feature in RB to work?  Blue Remote is a bluetooth remote for RB.The link on the official RB webpage " [http://www.gnome.org/projects/rhythmbox/utils.html](http://www.gnome.org/projects/rhythmbox/utils.html) " is broken. "That is the link to Blue Remote not the page I just listed."  blue remote is a feature I would like to use. Anyone have any sugestions?

---

### Post by mlind on 2006-06-26
[QUOTE=amoore]I was just wondering if anyone has gotten the Blue Remote plugin or feature in RB to work?  Blue Remote is a bluetooth remote for RB.The link on the official RB webpage " [http://www.gnome.org/projects/rhythmbox/utils.html](http://www.gnome.org/projects/rhythmbox/utils.html) " is broken. "That is the link to Blue Remote not the page I just listed."  blue remote is a feature I would like to use. Anyone have any sugestions?[/QUOTE]

I tried searching that plugin too without success.. :-|

---

### Post by maubp on 2006-06-26
I've found a few old emails:

[http://mail.gnome.org/archives/rhythmbox-devel/2004-August/msg00042.html](http://mail.gnome.org/archives/rhythmbox-devel/2004-August/msg00042.html)
[http://mail.gnome.org/archives/rhythmbox-devel/2004-October/msg00011.html](http://mail.gnome.org/archives/rhythmbox-devel/2004-October/msg00011.html)

It looks like Blue Remote was written by "Jonatan Magnusson", he has a [blog here](http://www.pnx.se/jonatan/) which used to have some entries about Blue Remote (look at google's cache or the way back machine).  You could try emailing him?

P.S. He has a [Last.fm account](http://www.last.fm/user/ionte/?chartstyle=sideGrey), which I have used to ask him...

---

### Post by Technoviking on 2006-06-27
This package is in Ubuntu Edgy now, may be backported.

---

### Post by dlai on 2006-06-27
[QUOTE=Mike]This package is in Ubuntu Edgy now, may be backported.[/QUOTE]
It is? I don't see it.... Tried installing the package from Mike but it had a dependency error with libpango... Anyone found a way to fix this when in edgy?

---

### Post by FredB on 2006-06-27
[QUOTE=Mike]This package is in Ubuntu Edgy now, may be backported.[/QUOTE]

Yes. I saw that on the rss feed :

[http://media.ubuntu-nl.org/rss/edgy.xml]("http://media.ubuntu-nl.org/rss/edgy.xml")

Let's hope backport will be done soon and great ;)

---

### Post by dlai on 2006-06-27
[QUOTE=FredB]Yes. I saw that on the rss feed :

[http://media.ubuntu-nl.org/rss/edgy.xml]("http://media.ubuntu-nl.org/rss/edgy.xml")

Let's hope backport will be done soon and great ;)[/QUOTE]

I don't get it, it is not on my edgy testing... enabled both multiverse and universe....

---

### Post by Technoviking on 2006-06-27
The source and debian diff files (needed to build package) are at 
[http://archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/](http://archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/)

But no debs yet.

---

### Post by dlai on 2006-06-27
yes i just realised thank you

---

### Post by mlind on 2006-06-27
[QUOTE=Mike]This package is in Ubuntu Edgy now, may be backported.[/QUOTE]

Thanks for the heads up Mike, I'm interested about Ubuntu's changelog, If they
have included anything new or if just a debian sync.

People who want to get hands on the official .deb, just include **edgy's main**
deb-src repository on your sources.list, then do

```

sudo apt-get update 
sudo apt-get build-dep rhythmbox && sudo apt-get source -b rhythmbox

```

---

### Post by maubp on 2006-06-27
[QUOTE=amoore]I was just wondering if anyone has gotten the Blue Remote plugin or feature in RB to work?  Blue Remote is a bluetooth remote for RB.The link on the official RB webpage " [http://www.gnome.org/projects/rhythmbox/utils.html](http://www.gnome.org/projects/rhythmbox/utils.html) " is broken. "That is the link to Blue Remote not the page I just listed."  blue remote is a feature I would like to use. Anyone have any sugestions?[/QUOTE]

[QUOTE=maubp]I've found a few old emails:

[http://mail.gnome.org/archives/rhythmbox-devel/2004-August/msg00042.html](http://mail.gnome.org/archives/rhythmbox-devel/2004-August/msg00042.html)
[http://mail.gnome.org/archives/rhythmbox-devel/2004-October/msg00011.html](http://mail.gnome.org/archives/rhythmbox-devel/2004-October/msg00011.html)

It looks like Blue Remote was written by "Jonatan Magnusson", he has a [blog here](http://www.pnx.se/jonatan/) which used to have some entries about Blue Remote (look at google's cache or the way back machine).  You could try emailing him?

P.S. He has a [Last.fm account](http://www.last.fm/user/ionte/?chartstyle=sideGrey), which I have used to ask him...[/QUOTE]

I emailed Jonatan and the bad news is he hasn't touched the code for a year, and the server it was on crashed.

The good news is he says he'll have a look for it...

---

### Post by amoore on 2006-06-28
I hope that he is able to find the code to blue remote. Thanks for giving him an email!!!! I'll keep checking this thread.

---

### Post by dlai on 2006-06-28
[QUOTE=mlind]
```

sudo apt-get update 
sudo apt-get build-dep rhythmbox && sudo apt-get source -b rhythmbox

```[/QUOTE]

Thank you I was actually wondering how to do that!

---

### Post by dlai on 2006-07-06
[QUOTE=dlai]Thank you I was actually wondering how to do that![/QUOTE]
Do you know how to do this with ipod-support?

---

### Post by mlind on 2006-07-06
[QUOTE=dlai]Do you know how to do this with ipod-support?[/QUOTE]

Debian unstable contains 0.9.5 source now, just get it there.

Then, edit debian/rules and add
```

DEB_CONFIGURE_EXTRA_FLAGS += --enable-ipod-writing

```
and build the package.

---

### Post by donar73 on 2006-07-07
I just downloaded the package "rhythmbox test backport" from the dapper-backports-site ([klick](https://launchpad.net/products/dapper-backports/+bug/50477)) and installed it with dpkg. Seems to work fine so far...

---

### Post by dlai on 2006-07-13
Is it possible to create a deb, like mike did, with ipod-write enabled, or is it already enabled?

---

### Post by mlind on 2006-07-13
> **dlai said:**
> Is it possible to create a deb, like mike did, with ipod-write enabled, or is it already enabled?

? 

That's what this HOWTO is about, creating a .deb package of rhythmbox, and there's instructions how to enable ipod write support too.

I removed some steps from guide to make it easier to follow.

---

### Post by mlind on 2006-07-13
> **Mike said:**
> I rebuilt the package but I'm still not getting notifications.

I dunno what was wrong with notifications, but I made a .deb out of CVS build and notifications seem to work fine now.

---

### Post by dlai on 2006-07-13
I'm sorry, I should've rephrased that: Is the deb mike created ipod-write-support enabled?

---

### Post by citizenkeith on 2006-12-16
> **maubp said:**
> I emailed Jonatan and the bad news is he hasn't touched the code for a year, and the server it was on crashed.

The good news is he says he'll have a look for it...

I take it Jonatan never found it?

---

### Post by citizenkeith on 2006-12-26
bump :mrgreen:

---

