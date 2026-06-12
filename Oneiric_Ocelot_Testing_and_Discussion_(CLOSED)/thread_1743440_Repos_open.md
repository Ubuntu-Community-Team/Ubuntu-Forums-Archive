---
title: "Repos open"
date: 2011-04-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Starks on 2011-04-29
sudo sed -i 's/natty/oneiric/g' /etc/apt/sources.list
sudo aptitude update
sudo aptitude dist-upgrade

You might want to save the natty-updates, natty-backports, natty-security, and natty-proposed repo lines in sources.list

eric@kingfisher:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"

---

### Post by scradock on 2011-04-29
> **Starks said:**
> sudo sed -i 's/natty/oneiric/g' /etc/apt/sources.list
sudo aptitude update
sudo aptitude dist-upgrade

You might want to save the natty-updates, natty-backports, natty-security, and natty-proposed repo lines in sources.list

eric@kingfisher:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"

To fix the Software Sources GUI:

Add the following suite above natty in /usr/share/python-apt/templates/Ubuntu.info

```
Suite: oneiric
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-powerpc: http://ports.ubuntu.com/
MatchURI-powerpc: ports.ubuntu.com|archive.ubuntu.com
BaseURI-lpia: http://ports.ubuntu.com/
MatchURI-lpia: ports.ubuntu.com|archive.ubuntu.com
MirrorsFile-amd64: /usr/share/python-apt/templates/Ubuntu.mirrors
MirrorsFile-i386: /usr/share/python-apt/templates/Ubuntu.mirrors
Description: Ubuntu 11.04 'Oneiric Ocelot'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported Open Source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained Open Source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues
```

What updates /etc/lsb-release? I've edited the sources.list, added the Oneiric suite as above, and still get Natty in lsb-release.....

---

### Post by DougieFresh4U on 2011-04-30
the first post, it was said to go to:
**Add the following suite above natty in /usr/share/python-apt/templates/Ubuntu.info**
and then follow the rest of his post.
I didn't have to do that as it just 'appeared'

---

### Post by scradock on 2011-04-30
> **DougieFresh4U said:**
> Post #2 it was said to go to:
**Add the following suite above natty in /usr/share/python-apt/templates/Ubuntu.info**
and then follow the rest of his post.
I didn't have to do that as it just 'appeared'

Yes, I did that. The Oneiric suite info is in the Ubuntu.info file.

I also edited the sources.list.

But I was expecting the lsb-release info to update at some stage - or do I have to do that by hand as well? Can't remember ever having to do that before - or am I just jumping too far ahead of the gun this time?

---

### Post by DougieFresh4U on 2011-04-30
> **scradock said:**
> Yes, I did that. The Oneiric suite info is in the Ubuntu.info file.

I also edited the sources.list.

But I was expecting the lsb-release info to update at some stage - or do I have to do that by hand as well? Can't remember ever having to do that before - or am I just jumping too far ahead of the gun this time?

oops, sorry, hope I didn't come off rude as it wasn't intended.
I had just changed sources using the first commands that were listed in OP and rebooted and lsb-release info was updated.
Also I am using the .39rc5 kernel as well.
Might as well go all the way!:P

---

### Post by Starks on 2011-04-30
pre-alpha ubuntu is usually the best time to use ubuntu.

1. syncing with debian sid and experimental
2. rc kernels and driver stacks
3. daily images to provide a quick and bleeding-edge linux desktop

---

### Post by dino99 on 2011-04-30
Possible typo:

Description: Ubuntu 11.04 'Oneiric Ocelot'

changed to:

Description: Ubuntu 11.10 'Oneiric Ocelot'

---

### Post by Harry33 on 2011-04-30
Well you do not have to that ubuntu.info file editing any more.
There is already the package python-apt in the Oneiric official repos.

---

### Post by donniezazen on 2011-05-02
> **Starks said:**
> 
You might want to save the natty-updates, natty-backports, natty-security, and natty-proposed repo lines in sources.list


You mean do not change natty-updates, natty-backports, natty-security, and natty-proposed to on oneiric-updates etc. Should i keep both natty-updates and oneiric-update etc. ?

If i am not wrong extra.ubuntu.com is opened later in release cycle.

---

### Post by Starks on 2011-05-02
oneiric-* is not needed right now

---

### Post by Harry33 on 2011-05-03
> **soham_1207 said:**
> You mean do not change natty-updates, natty-backports, natty-security, and natty-proposed to on oneiric-updates etc. Should i keep both natty-updates and oneiric-update etc. ?

If i am not wrong extra.ubuntu.com is opened later in release cycle.

I think natty-proposed only mixes things up. These updates are meant to fix Natty setup, not Oneiric. Using that repo may even cause dependency issues in Oneiric.
Natty-backports and Natty-security should not be used with Oneiric.

So the correct way is to switch to Oneiric-security.
Also, as long as Oneiric is in development phase, the repos Oneiric-backports and Oneiric-proposed are empty repos and not needed now.

Note, that Natty Partner repo still has for example the sun-java packages while Oneiric Partner repo is empty.

---

### Post by donniezazen on 2011-05-03
Thanks for the reply. If i am not wrong this is what i am suppose to do.

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
#deb http://us.archive.ubuntu.com/ubuntu/ natty-proposed restricted main multiverse universe
deb-src http://extras.ubuntu.com/ubuntu natty main
```

---

### Post by Harry33 on 2011-05-04
I would create a much simplier sources.list.
You should not use Natty-updates. Instead you should use Oneiric-updates. However, that repos is empty during the dev phase.
Here:

```

# deb cdrom:[Ubuntu 11.04 _Oneiric Ocelot_ - Release i386 (20110504)]/ oneiric main restricted

## Main repositories
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted multiverse universe

## Updates repositories
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted multiverse universe

## Security repositories
deb http://security.ubuntu.com/ubuntu oneiric-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted multiverse universe

## Backports repository
#deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

## Partner repository
#deb http://archive.canonical.com/ubuntu oneiric partner
#deb-src http://archive.canonical.com/ubuntu oneiric partner

## Extras repository
#deb http://extras.ubuntu.com/ubuntu oneiric main
#deb-src http://extras.ubuntu.com/ubuntu oneiric main

## Proposed repository
#deb http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed restricted main multiverse universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-proposed restricted main multiverse universe

```

---

### Post by donniezazen on 2011-05-04
Thank You for your help.

---

### Post by zika on 2011-05-04
After 2 hours of working on &#8222;stable&#8220; Natty, back from 20-days trip, reporting from Oneiric. Let us have a nice ride...

---

### Post by arpanaut on 2011-05-05
Trouble Ahead?
I'm in the process of upgrading with the commands in the first post, and at the dist-upgrade part I get this:
```
Calculating upgrade... Done
The following packages will be REMOVED:
  apparmor-utils doc-base gnome-system-tools hpijs hplip hplip-cups libapparmor-perl libapt-pkg-perl libcairo-perl
  libclass-accessor-perl libdigest-hmac-perl libdigest-sha1-perl libemail-valid-perl libglib-perl libgtk2-perl libhpmud0
  libio-pty-perl libipc-run-perl libnet-dbus-perl libnet-dns-perl liboobs-1-5 libpango-perl libparse-debianchangelog-perl
  libperl5.10 libpurple0 libsane-hpaio libsnmp15 libsub-name-perl libterm-readkey-perl libuuid-perl lintian system-tools-backends
  telepathy-haze ubuntu-desktop

```I'm pretty positive there are quite a few of those I don't want to lose.
This working from a freshly installed and upgraded natty.
Last night I attempted the same thing on one of my old testing nattys and after doing the whole command line boogie, I never could get it booted again.  No recovery mode, it god stuck running the init scripts, and hangs just after the fsck line with: ```
Starting CUPS printing spooled/service....[fail]
```Hence the concern about the hplip-cups etc.
 I do not recall these packages being removed last night but... I might have missed it? 
Anyway, has anybody seen this?  I have installed over the system from last night.

Any Ideas about my current situation?
In previous years I haven't had problems with this method to dist-upgrade especially early in the cycle.

Thanks

---

### Post by dino99 on 2011-05-05
just got this huge proposal to remove packages but thanks i've not accepted, in fact it only happen if perl (and the related packages) is chosen for upgrade.

wonder if its the gtk2 beginning removal, wait & see.

---

### Post by Harry33 on 2011-05-05
> **arpanaut said:**
> Trouble Ahead?
I'm in the process of upgrading with the commands in the first post, and at the dist-upgrade part I get this:
```
Calculating upgrade... Done
The following packages will be REMOVED:
  apparmor-utils doc-base gnome-system-tools hpijs hplip hplip-cups libapparmor-perl libapt-pkg-perl libcairo-perl
  libclass-accessor-perl libdigest-hmac-perl libdigest-sha1-perl libemail-valid-perl libglib-perl libgtk2-perl libhpmud0
  libio-pty-perl libipc-run-perl libnet-dbus-perl libnet-dns-perl liboobs-1-5 libpango-perl libparse-debianchangelog-perl
  libperl5.10 libpurple0 libsane-hpaio libsnmp15 libsub-name-perl libterm-readkey-perl libuuid-perl lintian system-tools-backends
  telepathy-haze ubuntu-desktop

```I'm pretty positive there are quite a few of those I don't want to lose.
This working from a freshly installed and upgraded natty.
Last night I attempted the same thing on one of my old testing nattys and after doing the whole command line boogie, I never could get it booted again.  No recovery mode, it god stuck running the init scripts, and hangs just after the fsck line with: ```
Starting CUPS printing spooled/service....[fail]
```Hence the concern about the hplip-cups etc.
 I do not recall these packages being removed last night but... I might have missed it? 
Anyway, has anybody seen this?  I have installed over the system from last night.

Any Ideas about my current situation?
In previous years I haven't had problems with this method to dist-upgrade especially early in the cycle.

Thanks

Try updating with Synaptic, one package at a time. You will then find out wich package causes these dependency issues.
It may be the perl package (5.12.3-6ubuntu3).

---

### Post by Harry33 on 2011-05-05
> **dino99 said:**
> just got this huge proposal to remove packages but thanks i've not accepted, in fact it only happen if perl (and the related packages) is chosen for upgrade.

wonder if its the gtk2 beginning removal, wait & see.

GTK+2 cannot be removed for a long time.
A number of applications depend on and will depend on GTK+2.

---

### Post by arpanaut on 2011-05-05
> **Harry33 said:**
> Try updating with Synaptic, one package at a time. You will then find out wich package causes these dependency issues.
It may be the perl package (5.12.3-6ubuntu3).

LOL, there are 234 packages waiting to be installed or upgraded.
One package at a time... :?: 

):PThanks I'll look into the perl package

Not a big deal, just a test partition.

---

### Post by Harry33 on 2011-05-05
> **arpanaut said:**
> LOL, there are 234 packages waiting to be installed or upgraded.
One package at a time... :?: 

):PThanks I'll look into the perl package

Not a big deal, just a test partition.

Yes, but note there are three perl packages:
- perl
- perl-base
- libperl5.12

And yet, a new update to the perl is in Launchpad waiting to be published.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/perl/5.12.3-6ubuntu4](https://launchpad.net/ubuntu/oneiric/+source/perl/5.12.3-6ubuntu4)

---

### Post by cecilpierce on 2011-05-05
Whats the favorite or best way to get updates, apt-get, aptitude, dist-grade, safe-upgrade, upgrade or wait ? I've tried all and can't remember what is best.

sudo aptitude upgrade shows this:

---

### Post by dino99 on 2011-05-05
my fav is synaptic, nothing else, then view details changelog with update-manager

---

### Post by cecilpierce on 2011-05-05
> **dino99 said:**
> my fav is synaptic, nothing else, then view details changelog with update-manager

Thanks, I'll give it a shot, fun fun fun til daddy took the T-Bird away... 
:)

---

### Post by el_koraco on 2011-05-05
> **arpanaut said:**
> 
Any Ideas about my current situation?
In previous years I haven't had problems with this method to dist-upgrade especially early in the cycle.

Thanks

Might mean that some of the packages ready for update haven't reached the server yet, so apt only gets the command to remove the hell out of thigs. It had that habit during the last Kubuntu dev cycle.

---

### Post by cecilpierce on 2011-05-05
what's with my update-manager ?

---

### Post by zika on 2011-05-05
> **cecilpierce said:**
> Whats the favorite or best way to get updates, apt-get, aptitude, dist-grade, safe-upgrade, upgrade or wait ? I've tried all and can't remember what is best.

sudo aptitude upgrade shows this:```
/usr/bin/sudo /usr/bin/aptitude update ; /usr/bin/sudo /usr/bin/aptitude safe-upgrade ; /usr/bin/sudo /usr/bin/aptitude clean 
```for years ...

---

### Post by arpanaut on 2011-05-05
> **Harry33 said:**
> Yes, but note there are three perl packages:
- perl
- perl-base
- libperl5.12

And yet, a new update to the perl is in Launchpad waiting to be published.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/perl/5.12.3-6ubuntu4](https://launchpad.net/ubuntu/oneiric/+source/perl/5.12.3-6ubuntu4)


Right you are!

I did a simple upgrade which removed all but about 50 conflicts, and then went through in Synaptic "one by one" and installed everything that didn't want to remove anything.  It is now down to 13 perl & related packages.

This is what the upgrade command gives:```
The following packages have been kept back:
  doc-base libalgorithm-diff-xs-perl libhtml-parser-perl liblocale-gettext-perl libnet-dbus-perl libterm-readkey-perl
  libtext-charwidth-perl libtext-iconv-perl libuuid-perl libxml-parser-perl perl perl-base perl-modules
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
```dist-upgrade gives  ```
The following packages will be REMOVED:
  apparmor-utils hpijs hplip hplip-cups libapparmor-perl libapt-pkg-perl libcairo-perl libclass-accessor-perl
  libdigest-hmac-perl libdigest-sha1-perl libemail-valid-perl libglib-perl libgtk2-perl libhpmud0 libio-pty-perl
  libipc-run-perl libnet-dns-perl libpango-perl libparse-debianchangelog-perl libperl5.10 libpurple0 libsane-hpaio
  libsnmp15 libsub-name-perl lintian telepathy-haze
The following NEW packages will be installed:
  libclass-isa-perl libpod-plainer-perl libswitch-perl libyaml-tiny-perl
The following packages will be upgraded:
  doc-base libalgorithm-diff-xs-perl libhtml-parser-perl liblocale-gettext-perl libnet-dbus-perl libterm-readkey-perl
  libtext-charwidth-perl libtext-iconv-perl libuuid-perl libxml-parser-perl perl perl-base perl-modules
13 upgraded, 4 newly installed, 26 to remove and 0 not upgraded.

```LOL I think I will be waiting for the fix.
Thanks for pointing me in the right direction!

---

### Post by donniezazen on 2011-05-06
lol i need to install perl for webmin, rtorrent, etc.

---

### Post by dino99 on 2011-05-07
> **cecilpierce said:**
> what's with my update-manager ?

[https://bugs.launchpad.net/ubuntu/oneiric/+source/update-manager/+bug/776311](https://bugs.launchpad.net/ubuntu/oneiric/+source/update-manager/+bug/776311)

---

