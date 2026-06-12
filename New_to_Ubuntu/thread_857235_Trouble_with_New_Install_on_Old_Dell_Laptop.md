---
title: "Trouble with New Install on Old Dell Laptop"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by PierreDeKat on 2008-07-12
Ubuntu Noob here, just installed Xubuntu on an old Dell C600 laptop with 256M RAM, and I'm experiencing a lot of apparent freezes and other mystery weirdness.

I came across a couple threads related to the swap file, and I was able to launch "System Monitor" -- it does appear that my swap file is working. At various times, data seems to be getting stored there, anyway.

And I'm not exactly pegging the needles on things with the stuff that I've done thus far. Whatever I'm doing has the memory usage around 128M and the swap file around, like, 37M.

So more about the quirky behavior. After the initial installation, I logged in for the first time, and I was greeted with the message that I needed to install some updates.

I managed to establish an internet connection and verified it with Firefox, though it took about a minute after I typed "www.yahoo.com" in the address bar for the letters to display there, and I think Firefox froze not long after that.

Anyway, I launched the updater, clicked whatever it was, "Install", or whatever, and the updater apparently froze, too.

After about 30 minutes with no apparent progress, I finally decided to restart the computer and try it again. 

Same deal.

That's when I pursued the swap file issue, with no real satisfaction in that department.

Then I decided to snoop around the various "System" applications and see where that led me. Launched "Authorizations", and it opened and seemed to operate properly, though I didn't attempt to change anything, not really knowing that much about things at this stage.

Tried to launch "Hardware Drivers", I see my cursor go to the "I'm-working-on-it" phase, then it reverts to normal, but "Hardware Drivers" never launches.

Clicked "Update Manager" to see how that went, and I was asked to enter my password. The problem was that I couldn't enter a password because my keyboard strokes aren't getting registered, or aren't getting registered in a timely manner.

Okay, I canceled that.

Keyboard, huh?... So I launched "Abiword", remembering it from my Redhat experience several years ago. I am able to type "ABC" before the keyboard strokes stop registering.

Closed Abiword, and that seemed to go quite normally.

So what am I looking for? I'm thinking a hardware issue of some sort, but I can't launch "Hardware Drivers" to see what I might find there.

Part of me wants to think there is some sort of, like, buss issue or other bottleneck-type thing going on. But I'm not sure where to go from here.

Sorry about the long post. Any ideas sure would be appreciated, but remember I'm a Noob. Not an idiot, necessarily, but it's been several years since I last used any sort of Linux.

---

### Post by Polygon on 2008-07-12
can you access any sort of system log? i havent used xubuntu in a while but i know in ubuntu its system > administration > system log, or you can just manually look at the /var/log files

this sounds like a problem i used to have with my laptop, applications started freezing and refusing to run, and i checked my logs and it was complaining about how the cpu was getting stuck (aka a bug of some sort)....

anyway take a look at the last entries of the log before you have to restart because of all the problems, if something is wrong its usually there

---

### Post by PierreDeKat on 2008-07-12
Okay, I seem to be doing a little better, after a major crash this morning. Oddly enough, I am able to use all of the "System" applications now, and holy smokes, I'm actually typing this from Xubuntu. 

Weird.

Anyway, I snooped through the log files, and let's see if any of this means anything. First, I'm finding this message in several of the log files.

> Jul 12 09:30:28 bob-laptop kernel: [   49.100324] ondemand governor failed, too long transition latency of HW, fallback to performance governor

And the other suspicious stuff I'm finding are in bootstrap.log.

> Selecting previously deselected package base-files.
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_4.0.1ubuntu5_i386.deb) ...
Selecting previously deselected package base-passwd.
Unpacking base-passwd (from .../base-passwd_3.5.16_i386.deb) ...
dpkg: base-passwd: dependency problems, but configuring anyway as you request:
 base-passwd depends on libc6 (>= 2.6.1-1); however:
  Package libc6 is not installed.
Setting up base-passwd (3.5.16) ...

dpkg: base-files: dependency problems, but configuring anyway as you request:
 base-files depends on awk; however:
  Package awk is not installed.
 base-files depends on libpam-modules (>= 0.79-3ubuntu3); however:
  Package libpam-modules is not installed.
Setting up base-files (4.0.1ubuntu5) ...

dpkg: regarding .../dpkg_1.14.16.6ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on coreutils (>= 5.93-1)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../dpkg_1.14.16.6ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on libc6 (>= 2.7-1)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../dpkg_1.14.16.6ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on lzma
  lzma is not installed.
dpkg: warning - ignoring pre-dependency problem !
(Reading database ... 97 files and directories currently installed.)
Preparing to replace dpkg 1.14.16.6ubuntu3 (using .../dpkg_1.14.16.6ubuntu3_i386.deb) ...
Unpacking replacement dpkg ...
dpkg: dpkg: dependency problems, but configuring anyway as you request:
 dpkg depends on coreutils (>= 5.93-1); however:
  Package coreutils is not installed.
 dpkg depends on libc6 (>= 2.7-1); however:
  Package libc6 is not installed.
 dpkg depends on lzma; however:
  Package lzma is not installed.
Setting up dpkg (1.14.16.6ubuntu3) ...

Selecting previously deselected package libc6.
(Reading database ... 330 files and directories currently installed.)
Unpacking libc6 (from .../libc6_2.7-10ubuntu3_i386.deb) ...
dpkg: libc6: dependency problems, but configuring anyway as you request:
 libc6 depends on libgcc1; however:
  Package libgcc1 is not installed.
Setting up libc6 (2.7-10ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package perl-base.
(Reading database ... 672 files and directories currently installed.)
Unpacking perl-base (from .../perl-base_5.8.8-12_i386.deb) ...
Setting up perl-base (5.8.8-12) ...
Selecting previously deselected package mawk.
(Reading database ... 794 files and directories currently installed.)
Unpacking mawk (from .../mawk_1.3.3-11ubuntu2_i386.deb) ...
Setting up mawk (1.3.3-11ubuntu2) ...

Selecting previously deselected package debconf.
(Reading database ... 813 files and directories currently installed.)
Unpacking debconf (from .../debconf_1.5.20_all.deb) ...
dpkg: debconf: dependency problems, but configuring anyway as you request:
 debconf depends on debconf-i18n | debconf-english; however:
  Package debconf-i18n is not installed.
  Package debconf-english is not installed.
Setting up debconf (1.5.20) ...

(Reading database ... 988 files and directories currently installed.)
Preparing to replace base-files 4.0.1ubuntu5 (using .../base-files_4.0.1ubuntu5_i386.deb) ...
Unpacking replacement base-files ...
Preparing to replace base-passwd 3.5.16 (using .../base-passwd_3.5.16_i386.deb) ...
Unpacking replacement base-passwd ...
Selecting previously deselected package bash.
dpkg: regarding .../bash_3.2-0ubuntu16_i386.deb containing bash, pre-dependency problem:
 bash pre-depends on libncurses5 (>= 5.6+20071006-3)
dpkg: warning - ignoring pre-dependency problem !
Unpacking bash (from .../bash_3.2-0ubuntu16_i386.deb) ...
Selecting previously deselected package belocs-locales-bin.
Unpacking belocs-locales-bin (from .../belocs-locales-bin_2.4-2.2ubuntu7_i386.deb) ...
Selecting previously deselected package bsdutils.
Unpacking bsdutils (from .../bsdutils_1%3a2.13.1-5ubuntu1_i386.deb) ...
Selecting previously deselected package coreutils.
dpkg: regarding .../coreutils_6.10-3ubuntu2_i386.deb containing coreutils, pre-dependency problem:
 coreutils pre-depends on libacl1 (>= 2.2.11-1)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../coreutils_6.10-3ubuntu2_i386.deb containing coreutils, pre-dependency problem:
 coreutils pre-depends on libselinux1
  libselinux1 is not installed.
dpkg: warning - ignoring pre-dependency problem !
Unpacking coreutils (from .../coreutils_6.10-3ubuntu2_i386.deb) ...
No diversion `any diversion of /usr/share/man/man1/md5sum.textutils.1.gz', none removed
No diversion `any diversion of /usr/bin/md5sum.textutils', none removed
Selecting previously deselected package dash.
Unpacking dash (from .../dash_0.5.4-8ubuntu1_i386.deb) ...
Preparing to replace debconf 1.5.20 (using .../debconf_1.5.20_all.deb) ...
Unpacking replacement debconf ...
Selecting previously deselected package debconf-i18n.
Unpacking debconf-i18n (from .../debconf-i18n_1.5.20_all.deb) ...
Selecting previously deselected package debianutils.
dpkg: regarding .../debianutils_2.28.2-0ubuntu1_i386.deb containing debianutils, pre-dependency problem:
 debianutils pre-depends on coreutils (>= 4.5.8-1)
  coreutils is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../debianutils_2.28.2-0ubuntu1_i386.deb containing debianutils, pre-dependency problem:
 debianutils pre-depends on mktemp
  mktemp is not installed.
dpkg: warning - ignoring pre-dependency problem !
Unpacking debianutils (from .../debianutils_2.28.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package diff.
Unpacking diff (from .../diff_2.8.1-12ubuntu1_i386.deb) ...
dpkg: regarding .../dpkg_1.14.16.6ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on coreutils (>= 5.93-1)
  coreutils is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../dpkg_1.14.16.6ubuntu3_i386.deb containing dpkg, pre-dependency problem:
 dpkg pre-depends on lzma
  lzma is not installed.
dpkg: warning - ignoring pre-dependency problem !
Preparing to replace dpkg 1.14.16.6ubuntu3 (using .../dpkg_1.14.16.6ubuntu3_i386.deb) ...
Unpacking replacement dpkg ...
Selecting previously deselected package e2fslibs.
Unpacking e2fslibs (from .../e2fslibs_1.40.8-2ubuntu2_i386.deb) ...
Selecting previously deselected package e2fsprogs.
dpkg: regarding .../e2fsprogs_1.40.8-2ubuntu2_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on e2fslibs (= 1.40.8-2ubuntu2)
  e2fslibs is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../e2fsprogs_1.40.8-2ubuntu2_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libblkid1 (>= 1.34-1)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../e2fsprogs_1.40.8-2ubuntu2_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libcomerr2 (>= 1.34-1)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../e2fsprogs_1.40.8-2ubuntu2_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libss2 (>= 1.34-1)
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../e2fsprogs_1.40.8-2ubuntu2_i386.deb containing e2fsprogs, pre-dependency problem:
 e2fsprogs pre-depends on libuuid1 (>= 1.34-1)
dpkg: warning - ignoring pre-dependency problem !
Unpacking e2fsprogs (from .../e2fsprogs_1.40.8-2ubuntu2_i386.deb) ...
Selecting previously deselected package findutils.
Unpacking findutils (from .../findutils_4.2.32-1ubuntu2_i386.deb) ...
Selecting previously deselected package gcc-4.2-base.
Unpacking gcc-4.2-base (from .../gcc-4.2-base_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package grep.
Unpacking grep (from .../grep_2.5.3~dfsg-3_i386.deb) ...
Selecting previously deselected package gzip.
Unpacking gzip (from .../gzip_1.3.12-3.2_i386.deb) ...
Selecting previously deselected package hostname.
Unpacking hostname (from .../hostname_2.94_i386.deb) ...
Selecting previously deselected package initscripts.
Unpacking initscripts (from .../initscripts_2.86.ds1-14.1ubuntu45_i386.deb) ...
Selecting previously deselected package libacl1.
Unpacking libacl1 (from .../libacl1_2.2.45-1_i386.deb) ...
Selecting previously deselected package libattr1.
Unpacking libattr1 (from .../libattr1_1%3a2.4.39-1_i386.deb) ...
Selecting previously deselected package libblkid1.
Unpacking libblkid1 (from .../libblkid1_1.40.8-2ubuntu2_i386.deb) ...
Preparing to replace libc6 2.7-10ubuntu3 (using .../libc6_2.7-10ubuntu3_i386.deb) ...
Unpacking replacement libc6 ...
Selecting previously deselected package libcomerr2.
Unpacking libcomerr2 (from .../libcomerr2_1.40.8-2ubuntu2_i386.deb) ...
Selecting previously deselected package libdb4.6.
Unpacking libdb4.6 (from .../libdb4.6_4.6.21-6ubuntu1_i386.deb) ...
Selecting previously deselected package libdevmapper1.02.1.
Unpacking libdevmapper1.02.1 (from .../libdevmapper1.02.1_2%3a1.02.20-2ubuntu2_i386.deb) ...
Selecting previously deselected package libgcc1.
Unpacking libgcc1 (from .../libgcc1_1%3a4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package liblocale-gettext-perl.
Unpacking liblocale-gettext-perl (from .../liblocale-gettext-perl_1.05-2ubuntu1_i386.deb) ...
Selecting previously deselected package libncurses5.
Unpacking libncurses5 (from .../libncurses5_5.6+20071124-1ubuntu2_i386.deb) ...
Selecting previously deselected package libpam-modules.
Unpacking libpam-modules (from .../libpam-modules_0.99.7.1-5ubuntu6_i386.deb) ...
Selecting previously deselected package libpam-runtime.
Unpacking libpam-runtime (from .../libpam-runtime_0.99.7.1-5ubuntu6_all.deb) ...
Selecting previously deselected package libpam0g.
Unpacking libpam0g (from .../libpam0g_0.99.7.1-5ubuntu6_i386.deb) ...
Selecting previously deselected package libselinux1.
Unpacking libselinux1 (from .../libselinux1_2.0.55-0ubuntu4_i386.deb) ...
Selecting previously deselected package libsepol1.
Unpacking libsepol1 (from .../libsepol1_2.0.20-0ubuntu3_i386.deb) ...
Selecting previously deselected package libslang2.
Unpacking libslang2 (from .../libslang2_2.1.3-2_i386.deb) ...
Selecting previously deselected package libss2.
Unpacking libss2 (from .../libss2_1.40.8-2ubuntu2_i386.deb) ...
Selecting previously deselected package libstdc++6.
Unpacking libstdc++6 (from .../libstdc++6_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package libtext-charwidth-perl.
Unpacking libtext-charwidth-perl (from .../libtext-charwidth-perl_0.04-4build1_i386.deb) ...
Selecting previously deselected package libtext-iconv-perl.
Unpacking libtext-iconv-perl (from .../libtext-iconv-perl_1.4-3_i386.deb) ...
Selecting previously deselected package libtext-wrapi18n-perl.
Unpacking libtext-wrapi18n-perl (from .../libtext-wrapi18n-perl_0.06-5_all.deb) ...
Selecting previously deselected package libuuid1.
Unpacking libuuid1 (from .../libuuid1_1.40.8-2ubuntu2_i386.deb) ...
Selecting previously deselected package locales.
Unpacking locales (from .../locales_2.7.9-4_all.deb) ...
Selecting previously deselected package login.
dpkg: regarding .../login_1%3a4.0.18.2-1ubuntu2_i386.deb containing login, pre-dependency problem:
 login pre-depends on libpam-runtime (>= 0.76-14)
  libpam-runtime is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../login_1%3a4.0.18.2-1ubuntu2_i386.deb containing login, pre-dependency problem:
 login pre-depends on libpam0g (>= 0.99.7.1)
  libpam0g is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
Unpacking login (from .../login_1%3a4.0.18.2-1ubuntu2_i386.deb) ...
Selecting previously deselected package lsb-base.
Unpacking lsb-base (from .../lsb-base_3.2-4ubuntu1_all.deb) ...
Selecting previously deselected package lzma.
Unpacking lzma (from .../lzma_4.43-12ubuntu1_i386.deb) ...
Selecting previously deselected package makedev.
Unpacking makedev (from .../makedev_2.3.1-84ubuntu1_all.deb) ...
Preparing to replace mawk 1.3.3-11ubuntu2 (using .../mawk_1.3.3-11ubuntu2_i386.deb) ...
Unpacking replacement mawk ...
Selecting previously deselected package mktemp.
Unpacking mktemp (from .../mktemp_1.5-5ubuntu2_i386.deb) ...
Selecting previously deselected package mount.
dpkg: regarding .../mount_2.13.1-5ubuntu1_i386.deb containing mount, pre-dependency problem:
 mount pre-depends on libselinux1
  libselinux1 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
Unpacking mount (from .../mount_2.13.1-5ubuntu1_i386.deb) ...
Selecting previously deselected package ncurses-base.
Unpacking ncurses-base (from .../ncurses-base_5.6+20071124-1ubuntu2_all.deb) ...
Selecting previously deselected package ncurses-bin.
dpkg: regarding .../ncurses-bin_5.6+20071124-1ubuntu2_i386.deb containing ncurses-bin, pre-dependency problem:
 ncurses-bin pre-depends on libncurses5 (>= 5.6+20071006-3)
  libncurses5 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
Unpacking ncurses-bin (from .../ncurses-bin_5.6+20071124-1ubuntu2_i386.deb) ...
Selecting previously deselected package passwd.
Unpacking passwd (from .../passwd_1%3a4.0.18.2-1ubuntu2_i386.deb) ...
Preparing to replace perl-base 5.8.8-12 (using .../perl-base_5.8.8-12_i386.deb) ...
Unpacking replacement perl-base ...
Selecting previously deselected package procps.
Unpacking procps (from .../procps_1%3a3.2.7-5ubuntu2_i386.deb) ...
Selecting previously deselected package python-minimal.
Unpacking python-minimal (from .../python-minimal_2.5.2-0ubuntu1_all.deb) ...
Selecting previously deselected package python2.5-minimal.
Unpacking python2.5-minimal (from .../python2.5-minimal_2.5.2-2ubuntu4_i386.deb) ...
Selecting previously deselected package sed.
Unpacking sed (from .../archives/sed_4.1.5-5_i386.deb) ...
Selecting previously deselected package startup-tasks.
Unpacking startup-tasks (from .../startup-tasks_0.3.9-2_i386.deb) ...
Selecting previously deselected package system-services.
Unpacking system-services (from .../system-services_0.3.9-2_i386.deb) ...
Selecting previously deselected package sysv-rc.
Unpacking sysv-rc (from .../sysv-rc_2.86.ds1-14.1ubuntu45_all.deb) ...
Selecting previously deselected package sysvutils.
dpkg: regarding .../sysvutils_2.86.ds1-14.1ubuntu45_i386.deb containing sysvutils, pre-dependency problem:
 sysvutils pre-depends on sysv-rc (>= 2.86.ds1-1.2)
  sysv-rc is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
Unpacking sysvutils (from .../sysvutils_2.86.ds1-14.1ubuntu45_i386.deb) ...
Selecting previously deselected package tar.
Unpacking tar (from .../archives/tar_1.19-3_i386.deb) ...
Selecting previously deselected package tzdata.
Unpacking tzdata (from .../tzdata_2008b-1ubuntu1_all.deb) ...
Selecting previously deselected package upstart.
dpkg: regarding .../upstart_0.3.9-2_i386.deb containing upstart, pre-dependency problem:
 upstart pre-depends on sysvutils (>= 2.86.ds1-14.1ubuntu11)
  sysvutils is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
Unpacking upstart (from .../upstart_0.3.9-2_i386.deb) ...
Selecting previously deselected package upstart-compat-sysv.
Unpacking upstart-compat-sysv (from .../upstart-compat-sysv_0.3.9-2_i386.deb) ...
Selecting previously deselected package upstart-logd.
Unpacking upstart-logd (from .../upstart-logd_0.3.9-2_i386.deb) ...
Selecting previously deselected package util-linux.
dpkg: regarding .../util-linux_2.13.1-5ubuntu1_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libncurses5 (>= 5.6+20071006-3)
  libncurses5 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../util-linux_2.13.1-5ubuntu1_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libselinux1
  libselinux1 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../util-linux_2.13.1-5ubuntu1_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libslang2 (>= 2.0.7-1)
  libslang2 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../util-linux_2.13.1-5ubuntu1_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on libuuid1
  libuuid1 is unpacked, but has never been configured.
dpkg: warning - ignoring pre-dependency problem !
dpkg: regarding .../util-linux_2.13.1-5ubuntu1_i386.deb containing util-linux, pre-dependency problem:
 util-linux pre-depends on zlib1g (>= 1:1.2.3.3.dfsg-1)
dpkg: warning - ignoring pre-dependency problem !

Do you think these dependency problems could be causing some of my bugginess? And is it normal to have so many dependency problems from a prepackaged distribution?

And any ideas why things seem to be doing better after the major crash?

Or any other ideas?

---

### Post by duckfeet on 2008-07-19
May have nothing to do with it, but I was having a hell of a time about a month ago, installing Ubuntu (7.10) on my Dell Inspiron 2600 Notebook, about, oh, ten years old, and w/XP and we kept trying to load from the Disk in the back of the book I had bought, but it too kept freezing up...

Anyway, I was at one of the local installfests here in San Diego, and these guys tried different things, one of which was to re-partition the Hard Drive, and then I got some more memory:(I had 256mb, and got another one, so I had 512mb) and finally, it did load, around the fifth time, but it was when I had clicked on "check CD" for errors: for some reason from there it finally installed, and now seems to work fine....

Anyway, best wishes, hopefully by now u have sorted it out...

Geff

---

