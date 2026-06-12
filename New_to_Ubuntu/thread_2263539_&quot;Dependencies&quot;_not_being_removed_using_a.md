---
title: "&quot;Dependencies&quot; not being removed using autoremove?"
date: 2015-02-01
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-02-01
I am using Kubuntu and wanted to uninstall Ktorrent cleanly. I did:

1. sudo apt-get purge ktorrent
2. sudo apt-get autoremove 
3. Deleted Ktorrent's config file in Home

Then I did dpkg -l *ktorrent* to see whether there are any remnants of Ktorrent that the system detects as installed. This is what it gave me:

$ dpkg -l *ktorrent*

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                   Version          Architecture     Description
+++-======================-================-================-==================================================
un  ktorrent               <none>           <none>           (no description available)
ii  ktorrent-data          4.3.1-2ubuntu2   all              KTorrent data and other architecture independent f
ii  libktorrent-l10n       1.3.1-3ubuntu1   all              localization files for the KTorrent library
ii  libktorrent5           1.3.1-3ubuntu1   amd64            KTorrent library for C++ / Qt 4 / KDE Platform

It says ktorrent-data, libktorrent-l10n, and libktorrent5 are installed. In the descriptions, it seems to imply that these installed files (are they packages, dependencies, or both?) are for Ktorrent only (is this true?). Are these files redundant, and if so, how can I delete them to completely remove all traces of Ktorrent? I just want to learn know how to remove all traces of an application that are not needed by the system more than actually caring that these files take up a trivial amount of space.

---

### Post by ian-weisser on 2015-02-01
There's a trick to it.
Apt remembers when you specify a package for install. It *marks* whether installed packages were *manually* specified or *automatically* pulled in.

Autoremoval requires two elements.
1) No other package depends upon it.
2) The apt-mark must be 'auto'

Here are two examples - two ways to install the ktorrent package.
```
apt-get install ktorrent      # mark ktorrent 'manual' and dependencies 'auto'

apt-get install ktorrent ktorrent-data libktorrent5 linktorrent-l10n  #mark everything 'manual'
```
The first example is the right way to work. ktorrent-data, libktorrent5, and linktorrent-l10n are all eligible for autoremoval when you uninstall ktorrent.
The second example causes the kind of problem you have. Since each package was *explicitly* installed by the user, each must be explicitly uninstalled.

mc4man in Post #3 raises a great point. When you install, only ONE package (kubuntu-desktop) is at the top of the chain of dependencies (and should be marked 'manual'. Everything else is a dependency.
But this causes a huge problem the first time you try to remove a default application (like Dolphin)...removing the dependency removed the top-level package..which them causes the *entire system* to autoremove. That's bad.
The hack that the Ubuntu installer uses to avoid that problem is to mark ALL new-install packages as 'manual'. It breaks autoremoval for those packages (subsequent installs work properly), and it confuses some users ("hey, autoremove doesn't work on these packages!"), but it prevents new users from accidentally destroying their systems.

---

### Post by mc4man on 2015-02-01
While I never really looked at, nor have used kubuntu,   it's possible that packages from the default install are all manual. If so,  then  that would have to be be considered.

---

### Post by garycheng12 on 2015-02-01
How can I be sure the dependencies that are for Ktorrent are only for Ktorrent (so I don't accidentally delete something that is also a dependency for a package I use)? How can I find all the dependencies of a particular program? I haven't tried Synaptic yet, will using Synaptic do all these things? (I know that it does some of them.)

Also, does a package manager like Synaptic literally initiate the same commands as "apt-get install, apt-get autoremove, apt-get purge"? If not, what does it do specifically and is it more thorough? How is apt-get different from dpkg (from what I'm getting, dpkg is like the predecessor and apt-get is preferred nowadays) and aptitude)?

---

### Post by ian-weisser on 2015-02-01
> **garycheng12 said:**
> How can I be sure the dependencies that are for Ktorrent are only for Ktorrent (so I don't accidentally delete something that is also a dependency for a package I use)? How can I find all the dependencies of a particular program? I haven't tried Synaptic yet, will using Synaptic do all these things? (I know that it does some of them.)

Easy. Two ways.

1) You can use the **apt-cache rdepends <packagename>** command to discover what packages depend on the package you are considering.
```
$ apt-cache rdepends libktorrent5
libktorrent5
Reverse Depends:
  libktorrent5:i386
  plasma-widget-ktorrent
  libktorrent-l10n
  libktorrent-dev
  libktorrent-dbg
  ktorrent
  kget
```
That's a list of all the package that depend upon libktorrent5.

You can also use **apt-cache depends** to find all the dependencies of one package.
```
$ apt-cache depends ktorrent
ktorrent
  Depends: kde-runtime
  Depends: libc6
  Depends: libgcc1
  Depends: libgeoip1
  Depends: libkcmutils4
  Depends: libkdecore5
  Depends: libkdeui5
  Depends: libkdewebkit5
  Depends: libkdnssd4
  Depends: libkio5
  Depends: libknotifyconfig4
  Depends: libkparts4
  Depends: libkrosscore4
  Depends: libktorrent5
  Depends: libkworkspace4abi2
  Depends: libphonon4
  Depends: libqt4-dbus
  Depends: libqt4-network
  Depends: libqt4-qt3support
  Depends: libqt4-xml
  Depends: libqtcore4
  Depends: libqtgui4
  Depends: libqtwebkit4
  Depends: libsolid4
  Depends: libstdc++6
  Depends: libsyndication4
  Depends: libtag1c2a
  Depends: phonon
  Depends: ktorrent-data
  Depends: libktorrent-l10n
  Suggests: plasma-widget-ktorrent
  Suggests: krosspython
  Conflicts: ktorrent:i386
```


2) You can simply read the 'Are you sure?' response from apt-get or Synaptic.
Example: Let's try to uninstall a dependency.
```
$ sudo apt-get remove gnome-icon-theme
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**The following packages will be REMOVED:**
  account-plugin-aim account-plugin-facebook account-plugin-flickr
  account-plugin-google account-plugin-jabber account-plugin-salut
  account-plugin-twitter account-plugin-windows-live account-plugin-yahoo
  apturl brasero deja-dup deja-dup-backend-gvfs empathy eog evince evolution
  evolution-plugins friends-facebook friends-twitter gnome-disk-utility
  gnome-icon-theme gnome-icon-theme-symbolic humanity-icon-theme ibus
  ibus-pinyin ibus-table libevolution libgtkhtml-4.0-0 libgtkhtml-4.0-common
  libgtkhtml-editor-4.0-0 light-themes mcp-account-manager-uoa
  network-manager-gnome python3-autopilot-vis rhythmbox rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins simple-scan software-center
  system-config-printer-gnome totem totem-mozilla totem-plugins ubuntu-artwork
  ubuntu-mono unity unity-asset-pool unity-control-center
  unity-control-center-signon unity-scope-gdrive webaccounts-extension-common
  xul-ext-webaccounts
0 upgraded, 0 newly installed, **56 to remove** and 9 not upgraded.
After this operation, 80.9 MB disk space will be freed.
**Do you want to continue? [Y/n]** n
Abort.
```
 56 packages to be removed. And an opportunity to cancel.



> **garycheng12 said:**
>  Also, does a package manager like Synaptic literally initiate the same commands as "apt-get install, apt-get autoremove, apt-get purge"? If not, what does it do specifically and is it more thorough? How is apt-get different from dpkg (from what I'm getting, dpkg is like the predecessor and apt-get is preferred nowadays) and aptitude)?

That's a pretty deep question. It's easier to answer it in reverse. It's an onion, with dpkg in the center.

dpkg (debian package manager) came first. dpkg does only three things: It install packages. It uninstalls packages. It keeps a database of packages, so it can do it's work.

apt (debian advanced package tool) came years later. apt uses dpkg and it's database. On top of the ability to install/uninstall/track packages, apt adds awareness of software repositories and other conveniences.
apt doesn't replace dpkg - dpkg is the motor under apt's hood.
When you use apt-cache, apt is reading the dpkg database (anyone can read it)...but it's much easier to use apt tools for common use.

apt has all kinds of frontends to interface with it. Apt-cache, apt-get, Synaptic, Software Center, and many more. They all are merely pretty ways to communicate with apt. They all do the same thing the same way - apt's way.

---

### Post by garycheng12 on 2015-02-01
Just what I needed, thanks for the information.

---

