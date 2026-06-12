---
title: "i've had errors in synaptic for a while. can you show me a sources.list i can use?"
date: 2006-02-07
forum: Repositories &amp; Backports
---

### Post by ice60 on 2006-02-07
i'd love to be able to use apt and not have errors, i changed the sources.list around abit and have manged to be error free at times but i have more errors again when i just used Synaptic. can you show me how my sources.list should look so it's error free, please?

here's my sources.list

```
deb http://dk.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu breezy universe
deb-src http://dk.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## Multiverse
deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Skype
#deb http://download.skype.com/linux/repos/debian/ stable non-free

## Wine
#deb http://wine.sourceforge.net/apt/ binary/
#deb-src http://wine.sourceforge.net/apt/ source/

## Penguin Liberation Front
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## Backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
#deb http://ubuntu-backports.mirrormax.net/ breezy-backports-staging main restricted universe multiverse
 
#backports-extras
#deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main universe multiverse restricted

# Open Office 2 final
#deb http://people.ubuntu.com/~doko/OOo2 ./

#VLC Media Plyer
deb http://download.videolan.org/pub/videolan/debian sarge main
deb-src http://download.videolan.org/pub/videolan/debian sarge main

# Opera web browser
deb http://deb.opera.com/opera/ etch non-free


```

here's the error i just got

```
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy-updates/universe Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy-updates/multiverse Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://packages.freecontrib.org breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://packages.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://download.videolan.org sarge/main Packages (/var/lib/apt/lists/download.videolan.org_pub_videolan_debian_dists_sarge_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://deb.opera.com etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)

```

if anyone can help at all that would be great. thanks

---

### Post by public_void on 2006-02-07
See the sticky thread at the top of this forum [here]("http://www.ubuntuforums.org/showthread.php?t=92672").

---

### Post by ice60 on 2006-02-07
[QUOTE=public_void]See the sticky thread at the top of this forum [here]("http://www.ubuntuforums.org/showthread.php?t=92672").[/QUOTE]
thanks, public_void. i'm really happy with my new sources.list :cool:

---

### Post by ice60 on 2006-02-14
hi, i still have errors with my new list :cry: do you know why i always have errors?

after i have an error i reload the list, then everything on the list has the new icon next to it in synaptic. then a day or two later i have the error again.

here's my sources.list
```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf secondary repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secondary are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
 deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./

```

and here is the error.

```
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://packages.freecontrib.org breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://packages.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://deb.opera.com etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)

```
thanks.

---

### Post by jonathanm on 2006-02-15
im having sort of the same problem, my normal sources work fine but the backports aren't recognised.  I tried to refresh them and now I am downloading a load of updates for language packs and wine, heres the errors I get if anyone could offer help to both myself and ice60 then it would be appreciated.

```
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-backports Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-backports_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-custom Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-custom_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/breezy-extras Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_breezy-extras_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://seveas.ubuntulinux.nl breezy-seveas/madwifi Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_madwifi_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://kubuntu.org breezy/restricted Packages (/var/lib/apt/lists/kubuntu.org_packages_kde35_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://kubuntu.org breezy/universe Packages (/var/lib/apt/lists/kubuntu.org_packages_kde35_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://kubuntu.org breezy/multiverse Packages (/var/lib/apt/lists/kubuntu.org_packages_kde35_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
```

thanks

---

### Post by snake1130 on 2006-02-15
I'm having problem as well...although i'm using Gnome [http://www.ubuntuforums.org/showthread.php?t=130977]("http://www.ubuntuforums.org/showthread.php?t=130977").

---

