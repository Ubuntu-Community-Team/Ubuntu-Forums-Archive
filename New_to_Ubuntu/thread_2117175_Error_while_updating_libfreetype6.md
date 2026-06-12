---
title: "Error while updating libfreetype6"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by 81duz1d0 on 2013-02-17
Hello!

Whenever I run 'apt-get update' I get this:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libfreetype6 : Breaks: libfreetype6:i386 (!= 2.4.8-1ubuntu2) but 2.4.8-1ubuntu2.1 is installed
 libfreetype6:i386 : Breaks: libfreetype6 (!= 2.4.8-1ubuntu2.1) but 2.4.8-1ubuntu2 is installed
E: Unmet dependencies. Try using -f.


On Ubuntu 12.04.1

---

### Post by Bashing-om on 2013-02-17
81duz1d0; Hi !

> You might want to run 'apt-get -f install' to correct these.what results from terminal codes:
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by 81duz1d0 on 2013-02-18
Thanks for the reply! Apparently the error is about the VLC package.

I got this after apt-get -f install:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libfreetype6
The following packages will be upgraded:
  libfreetype6
1 upgraded, 0 newly installed, 0 to remove and 156 not upgraded.
6 not fully installed or removed.
Need to get 0 B/343 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: error processing libfreetype6 (--configure):
 libfreetype6:amd64 2.4.8-1ubuntu2 cannot be configured because libfreetype6:i386 is in a different version (2.4.8-1ubuntu2.1)
dpkg: error processing libfreetype6:i386 (--configure):
 libfreetype6:i386 2.4.8-1ubuntu2.1 cannot be configured because libfreetype6:amd64 is in a different version (2.4.8-1ubuntu2)
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libfreetype6 (>= 2.2.1); however:
  Package libfreetype6 is not configured yet.
dpkg: error processing vlc-nox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-notify:
 vlc-plugin-notify depends on vlc-nox (= 2.0.5-0ubuntu0.12.04.1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc-plugin-notify (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 2.0.5-0ubuntu0.12.04.1); however:
  Package vlc-nox is not configured yet.
 vlc depends on libfreetype6 (>= 2.2.1); however:
  Package libfreetype6 is not configured yet.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-pulse:
 vlc-plugin-pulse depends on vlc-nox (= 2.0.5-0ubuntu0.12.04.No apport report written because the error message indicates its a followup error from a previous failure.
                       No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                                                                                                             1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc-plugin-pulse (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libfreetype6
 libfreetype6:i386
 vlc-nox
 vlc-plugin-notify
 vlc
 vlc-plugin-pulse
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

But I have no clue about how to fix it

---

### Post by cortman on 2013-02-18
Try

```
sudo dpkg --configure -a
```

---

### Post by 81duz1d0 on 2013-02-19
Got this error. Still poiting to VLC

```

dpkg: error processing libfreetype6 (--configure):
 libfreetype6:amd64 2.4.8-1ubuntu2 cannot be configured because libfreetype6:i386 is in a different version (2.4.8-1ubuntu2.1)
dpkg: error processing libfreetype6:i386 (--configure):
 libfreetype6:i386 2.4.8-1ubuntu2.1 cannot be configured because libfreetype6:amd64 is in a different version (2.4.8-1ubuntu2)
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libfreetype6 (>= 2.2.1); however:
  Package libfreetype6 is not configured yet.
dpkg: error processing vlc-nox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 2.0.5-0ubuntu0.12.04.1); however:
  Package vlc-nox is not configured yet.
 vlc depends on libfreetype6 (>= 2.2.1); however:
  Package libfreetype6 is not configured yet.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-notify:
 vlc-plugin-notify depends on vlc-nox (= 2.0.5-0ubuntu0.12.04.1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc-plugin-notify (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc-plugin-pulse:
 vlc-plugin-pulse depends on vlc-nox (= 2.0.5-0ubuntu0.12.04.1); however:
  Package vlc-nox is not configured yet.
dpkg: error processing vlc-plugin-pulse (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libfreetype6
 libfreetype6:i386
 vlc-nox
 vlc
 vlc-plugin-notify
 vlc-plugin-pulse

```

---

### Post by Bashing-om on 2013-02-19
81duz1d0;

Well, might be able to remove the vlc and libfree6type6 packages with the package manager and reinstall them.

But there is libfreetype6:i386 to deal with, I have yet to identify it. How did you install it ?

I'll do some more looking with 'dpkg' and search engines to see what I can find.

[INDENT][INDENT]I be look'n
[/INDENT][/INDENT]

---

### Post by 81duz1d0 on 2013-02-19
I couldn't remove VLC either

```

apt-get remove vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libfreetype6 : Breaks: libfreetype6:i386 (!= 2.4.8-1ubuntu2) but 2.4.8-1ubuntu2.1 is to be installed
 libfreetype6:i386 : Breaks: libfreetype6 (!= 2.4.8-1ubuntu2.1) but 2.4.8-1ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2013-02-20
81duz1d0;
I am beginning to get a handle on this. I do not have this fonts engine package installed on my system, so will have to look at it from your end.
Let's look at the inter-relationship of libfreetype6 and libfreetype6:i386 to vlc;
--Maybe a conflict in packages (??)--
Post the results of terminal codes:
```
 
dpkg -L libfreetype6
dpkg -S libfreetype6
dpkg -L libfreetype6:i386
dpkg -S libfreetype6:i386
dpkg -L vlc
``` All we are doing here is looking -see  man dpkg-. 

We will see what is to be seen and take off again.[INDENT]it's a learning process

[/INDENT]

---

### Post by 81duz1d0 on 2013-02-21
Thanks for the help! Let's go to the commands:

```

root@biduzido-note:/home/biduzido# dpkg -L libfreetype6
/.
/usr
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libfreetype.so.6.8.0
/usr/share
/usr/share/doc
/usr/share/doc/libfreetype6
/usr/share/doc/libfreetype6/changelog.Debian.gz
/usr/share/doc/libfreetype6/TODO
/usr/share/doc/libfreetype6/ft2faq.html
/usr/share/doc/libfreetype6/copyright
/usr/share/doc/libfreetype6/pcf
/usr/share/doc/libfreetype6/pcf/README
/usr/share/doc/libfreetype6/FTL.TXT.gz
/usr/lib/x86_64-linux-gnu/libfreetype.so.6

```

```

root@biduzido-note:/home/biduzido# dpkg -S libfreetype6
libfreetype6, libfreetype6:i386: /usr/share/doc/libfreetype6/copyright
libfreetype6, libfreetype6:i386: /usr/share/doc/libfreetype6/TODO
libfreetype6, libfreetype6:i386: /usr/share/doc/libfreetype6/ft2faq.html
libfreetype6, libfreetype6:i386: /usr/share/doc/libfreetype6/changelog.Debian.gz
libfreetype6, libfreetype6:i386: /usr/share/doc/libfreetype6/pcf
libfreetype6, libfreetype6:i386: /usr/share/doc/libfreetype6/FTL.TXT.gz
libfreetype6, libfreetype6:i386: /usr/share/doc/libfreetype6
libfreetype6, libfreetype6:i386: /usr/share/doc/libfreetype6/pcf/README

```

```

root@biduzido-note:/home/biduzido# dpkg -L libfreetype6:i386
/.
/usr
/usr/lib
/usr/lib/i386-linux-gnu
/usr/lib/i386-linux-gnu/libfreetype.so.6.8.0
/usr/share
/usr/share/doc
/usr/share/doc/libfreetype6
/usr/share/doc/libfreetype6/ft2faq.html
/usr/share/doc/libfreetype6/FTL.TXT.gz
/usr/share/doc/libfreetype6/pcf
/usr/share/doc/libfreetype6/pcf/README
/usr/share/doc/libfreetype6/TODO
/usr/share/doc/libfreetype6/changelog.Debian.gz
/usr/share/doc/libfreetype6/copyright
/usr/lib/i386-linux-gnu/libfreetype.so.6

```

```

root@biduzido-note:/home/biduzido# dpkg -S libfreetype6:i386
dpkg-query: no path found matching pattern *libfreetype6:i386*.

```

```

root@biduzido-note:/home/biduzido# dpkg -L vlc
/.
/usr
/usr/share
/usr/share/menu
/usr/share/menu/vlc
/usr/share/bug
/usr/share/kde4
/usr/share/kde4/apps
/usr/share/kde4/apps/solid
/usr/share/kde4/apps/solid/actions
/usr/share/kde4/apps/solid/actions/vlc-openvcd.desktop
/usr/share/kde4/apps/solid/actions/vlc-openbd.desktop
/usr/share/kde4/apps/solid/actions/vlc-opencda.desktop
/usr/share/kde4/apps/solid/actions/vlc-opendvd.desktop
/usr/share/man
/usr/share/man/man1
/usr/share/doc
/usr/share/applications
/usr/share/applications/vlc.desktop
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/vlc
/usr/lib
/usr/lib/mime
/usr/lib/mime/packages
/usr/lib/mime/packages/vlc
/usr/lib/vlc
/usr/lib/vlc/plugins
/usr/lib/vlc/plugins/video_output
/usr/lib/vlc/plugins/video_output/libxcb_x11_plugin.so
/usr/lib/vlc/plugins/video_output/libxcb_glx_plugin.so
/usr/lib/vlc/plugins/video_output/libxcb_xv_plugin.so
/usr/lib/vlc/plugins/video_output/libxcb_window_plugin.so
/usr/lib/vlc/plugins/video_output/libaa_plugin.so
/usr/lib/vlc/plugins/video_output/libcaca_plugin.so
/usr/lib/vlc/plugins/services_discovery
/usr/lib/vlc/plugins/services_discovery/libxcb_apps_plugin.so
/usr/lib/vlc/plugins/misc
/usr/lib/vlc/plugins/misc/libxscreensaver_plugin.so
/usr/lib/vlc/plugins/misc/libxdg_screensaver_plugin.so
/usr/lib/vlc/plugins/access
/usr/lib/vlc/plugins/access/libxcb_screen_plugin.so
/usr/lib/vlc/plugins/control
/usr/lib/vlc/plugins/control/libglobalhotkeys_plugin.so
/usr/lib/vlc/plugins/gui
/usr/lib/vlc/plugins/gui/libskins2_plugin.so
/usr/lib/vlc/plugins/gui/libqt4_plugin.so
/usr/lib/vlc/plugins/codec
/usr/lib/vlc/plugins/codec/libsdl_image_plugin.so
/usr/lib/vlc/plugins/codec/libavcodec_plugin.so
/usr/lib/vlc/plugins/video_filter
/usr/lib/vlc/plugins/video_filter/libpanoramix_plugin.so
/usr/bin
/usr/bin/qvlc
/usr/bin/svlc
/usr/share/bug/vlc
/usr/share/man/man1/qvlc.1.gz
/usr/share/man/man1/svlc.1.gz
/usr/share/doc/vlc

```

---

### Post by Bashing-om on 2013-02-21
81duz1d0;

Is it that you are attempting to run a 32 bit package on a 64 bit machine ? ( is the supporting libraries installed - to be looked at later--).

What architecture do you have ?

```
uname -m
```-That should have jumped out at me to start with.-

I am looking -- right now I just do not see the connections. 
I will continue to try and puzzle it out. Looking at my possible miss use of the commands.

All I can determine for now, what I thought might be is not -> the *:i386 was a dependent of libfreetype6.[INDENT]carry'n on

[/INDENT]

---

### Post by 81duz1d0 on 2013-02-21
I'm running a x86_64 system. I don't know how both packages end up being installed

---

### Post by Bashing-om on 2013-02-21
81duz1d0;

OK ...I have been pursuing this most of the day -> leading into a realm I was not even aware of the current status (workable) of multi-arch. Presently I am no closer to understanding why those packages can not be removed - due to inter dependency relationships-//in all my poking about I have seen no proffered solutions that you have not done//

I do have some avenues to explore but I am not one to blindly attempt any thing with out KNOWING why and what I am doing...but more than willing to take a poke and see what results to obtain additional information.

Poke'n:
#See if multi-arch is enabled:
```
 cat  /etc/dpkg/dpkg.cfg.d/multiarch
dpkg --print-foreign-architectures
#see what is installed and not:
apt-cache policy libfreetype6
apt-cache policy libfreetype6:i386
sudo apt-cache policy ia32-libs
#list unconfigured packages -if any-
dpkg --audit
```The goal is to (re)configure OR remove the problem packages.
As I see it, gotta define the dependencies and work from the bottom up.[INDENT][INDENT]open to other opinions

[/INDENT][/INDENT]

---

### Post by 81duz1d0 on 2013-02-21
I think there are to factors here! The multi-architecture and multi-version. One package seems connected to "2.4.8-1ubuntu2" and the other one to "2.4.8-1ubuntu2.1"
```

root@biduzido-note:/home/biduzido# cat  /etc/dpkg/dpkg.cfg.d/multiarch
foreign-architecture i386
root@biduzido-note:/home/biduzido# dpkg --print-foreign-architectures
i386
root@biduzido-note:/home/biduzido# apt-cache policy libfreetype6
libfreetype6:
  Installed: 2.4.8-1ubuntu2
  Candidate: 2.4.8-1ubuntu2.1
  Version table:
     2.4.8-1ubuntu2.1 0
        500 http://sft.if.usp.br/ubuntu/ precise-updates/main amd64 Packages
        500 http://sft.if.usp.br/ubuntu/ precise-security/main amd64 Packages
 *** 2.4.8-1ubuntu2 0
        500 http://sft.if.usp.br/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
root@biduzido-note:/home/biduzido# apt-cache policy libfreetype6:i386
libfreetype6:i386:
  Installed: 2.4.8-1ubuntu2.1
  Candidate: 2.4.8-1ubuntu2.1
  Version table:
 *** 2.4.8-1ubuntu2.1 0
        500 http://sft.if.usp.br/ubuntu/ precise-updates/main i386 Packages
        500 http://sft.if.usp.br/ubuntu/ precise-security/main i386 Packages
        100 /var/lib/dpkg/status
     2.4.8-1ubuntu2 0
        500 http://sft.if.usp.br/ubuntu/ precise/main i386 Packages
root@biduzido-note:/home/biduzido# apt-cache policy ia32-libs
ia32-libs:
  Installed: (none)
  Candidate: 20090808ubuntu36
  Version table:
     20090808ubuntu36 0
        500 http://sft.if.usp.br/ubuntu/ precise-updates/universe amd64 Packages
     20090808ubuntu35 0
        500 http://sft.if.usp.br/ubuntu/ precise/universe amd64 Packages
root@biduzido-note:/home/biduzido# dpkg --audit
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libfreetype6:i386    FreeType 2 font engine, shared library files
 vlc-plugin-pulse     PulseAudio plugin for VLC
 vlc-nox              multimedia player and streamer (without X support)
 vlc                  multimedia player and streamer
 vlc-plugin-notify    LibNotify plugin for VLC

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 libfreetype6         FreeType 2 font engine, shared library files

```

---

### Post by Bashing-om on 2013-02-24
81duz1d0;
I don't see my response from yesterday, guess I must have goofed and not sent it properly.

Any way -> I see that multi-arch is enabled and the supporting libraries are not installed.
-may have to install those libraries in order to deal with "libfreetype6.i386'-. We'll see bout that later.

For now lets do the "libfreetype6"  -specifically as you had done so generally prior
> 100 /vat/lib/dpkg/status may have a hold on it.

Terminal code:
```
dpkg --configure libfreetype6
```Does "dpkg" successfully configure the package ? No ? Post the errors generated.
[INDENT][INDENT][INDENT]still try'n
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-02-24
81duz1d0;

Looks like I may have my perceptions backward.
> sysop1@1204-a:~$ apt-cache depends libfreetype6
libfreetype6
  Depends: libc6
  Depends: zlib1g
  PreDepends: multiarch-support
    multiarch-support:i386
  Replaces: libfreetype6:i386
  Breaks: libfreetype6:i386Maybe focus our attention on "libfreetype6.i386" ???
Still of interest is the return of dpkg's attempt to configure "libfreetype6"
[INDENT][INDENT]the continuing saga

[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-02-26
81duz1d0;

Continues on my mind 'till resolution is achieved.
Found background info on what is going on and how to look at the dependencies:
 [https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)
[INDENT][INDENT]this should help

[/INDENT][/INDENT]

---

### Post by 81duz1d0 on 2013-03-07
Sorry for the delay, I was moving!

Well, I tried an

```

apt-cache depends libfreetype6

```

and got

```

libfreetype6
  Depends: libc6
  Depends: zlib1g
  PreDepends: multiarch-support
    multiarch-support:i386
  Replaces: libfreetype6:i386
  Breaks: libfreetype6:i386

```

still no clue. I guess the problem is around the versions "2.4.8-1ubuntu2.x"

---

