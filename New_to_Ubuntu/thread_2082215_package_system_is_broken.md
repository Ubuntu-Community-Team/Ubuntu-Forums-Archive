---
title: "package system is broken?"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by bekirs on 2012-11-08
Hi, 

I get the following message when I try to install new updates. Could you recommend a solution?

"The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"

---

### Post by Bucky Ball on 2012-11-08
Please open a terminal and paste this in:
```

nano /etc/apt/sources.list

```Post the output back here.

Also, from the message you posted:
> 
Check if you are using third party repositories. If so disable them, since they are a common source of problems. Furthermore run the following command in a Terminal: apt-get install -f

Are you using third-party repos? The command I posted first will let us know. Also, you can try the other command, in the error message, but add 'sudo'.

```
sudo apt-get install -f
```

---

### Post by bekirs on 2012-11-08
> **Bucky Ball said:**
> Please open a terminal and paste this in:
```

nano /etc/apt/sources.list

```Post the output back here.

Also, from the message you posted:


Are you using third-party repos? The command I posted first will let us know. Also, you can try the other command, in the error message, but add 'sudo'.

```
sudo apt-get install -f
```

here is what I got:

```

  GNU nano 2.2.6          File: /etc/apt/sources.list                           

# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ $

# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ $
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ $
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ $
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ $

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise restricted main multiverse$

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates restricted main mu$

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
                [ Read 53 lines (Warning: No write permission) ]

```

---

### Post by bekirs on 2012-11-08
[QUOTE=bekirs;12344547]

I think this one is the full version:

```

# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/multiverse/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/universe/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise universe
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main


```

---

### Post by Bucky Ball on 2012-11-08
Strange. You appear to have some repos missing. Did you just install?

Could you open update-manager, hit 'Settings' in bottom left corner and see what you have *un*-ticked. You don't need any of the repos ending with .src unless you are looking to tweak, experiment and develop.

You could also open a terminal and try:
```

sudo apt-get update
sudo apt-get upgrade
```

Ignore the first message. The second will NOT upgrade you to 12.10, if it works anyway.

---

### Post by bekirs on 2012-11-08
Under "Software Sources"
*Ubuntu Software (everything is ticked)
*Updates (pre-released updates and unsupported updates are unticked)

---

### Post by Bucky Ball on 2012-11-08
Oh, okay; now I see the full version. ;)

```

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
**deb http://archive.canonical.com/ubuntu precise partner**
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
**deb http://extras.ubuntu.com/ubuntu precise main**
# deb-src http://extras.ubuntu.com/ubuntu precise main
```This is not going to fix your issue but I would personally un-hash the two lines as I have in bold above and hash # the lines beginning with 'deb-src'. You may not want to use any third-party stuff at all, though. If so, don't enable those two repos. It is safer to tick/untick the repos in the Software Sources GUI; update manager>Settings. 

You might save enabling any new repos for later, though, as it might confuse things at the moment. ;)

Oh, and run:

```
sudo apt-get install -f
```Let us know what that spews out ...

---

### Post by bekirs on 2012-11-09
> **Bucky Ball said:**
> Oh, okay; now I see the full version. ;)

```

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
**deb http://archive.canonical.com/ubuntu precise partner**
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
**deb http://extras.ubuntu.com/ubuntu precise main**
# deb-src http://extras.ubuntu.com/ubuntu precise main
```This is not going to fix your issue but I would personally un-hash the two lines as I have in bold above and hash # the lines beginning with 'deb-src'. You may not want to use any third-party stuff at all, though. If so, don't enable those two repos. It is safer to tick/untick the repos in the Software Sources GUI; update manager>Settings. 

You might save enabling any new repos for later, though, as it might confuse things at the moment. ;)

Oh, and run:

```
sudo apt-get install -f
```Let us know what that spews out ...


Hi again,

after(un)hashing operations, I typed ```
sudo apt-get install -f
``` and the output is

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libreoffice-help-en-gb libreoffice-help-en-us libunistring0 mythes-en-au
  mythes-en-us libqt4-test language-pack-kde-zh-hans-base hyphen-en-us
  po-debconf intltool-debian firefox-locale-zh-hans libgconf2-4:i386 gettext
  libqt4-help python-qt4 python-sip kde-l10n-engb libqtassistantclient4
  libgettextpo0 language-pack-zh-hans-base libreoffice-l10n-zh-cn
  kde-l10n-zhcn language-pack-zh-hans language-pack-kde-zh-hans
  libmail-sendmail-perl libreoffice-help-zh-cn libsys-hostname-long-perl
  libnss3-1d:i386 libreoffice-l10n-en-gb openoffice.org-hyphenation
  libreoffice-l10n-en-za
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  jadetex latex-sanskrit tex-common
Suggested packages:
  docbook-dsssl debhelper
The following packages will be upgraded:
  jadetex latex-sanskrit tex-common
3 upgraded, 0 newly installed, 0 to remove and 72 not upgraded.
20 not fully installed or removed.
Need to get 0 B/1,981 kB of archives.
After this operation, 600 kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  jadetex latex-sanskrit tex-common
Install these packages without verification [y/N]? y
Setting up tex-common (2.10) ...
Error: The new file /usr/share/tex-common/05TeXMF.cnf does not exist!
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on texlive-common (>= 2011); however:
  Package texlive-common is not configured yet.
 texlive-binaries depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-doc-base:
 texlive-doc-base depends on texlive-common (>= 2012.20120516); however:
  Package texlive-common is not configured yet.
 texlive-doc-base depends on tex-common (>= 3); hoNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                            No apport report written because the error message indicates its a followup error from a previous failure.
                      No apport report written because MaxReports is reached already
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                              No apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          No apport report written because MaxReports is reached already
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    wever:
  Version of tex-common on system is 2.10.
dpkg: error processing texlive-doc-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-doc-base (>= 2012.20120516); however:
  Package texlive-doc-base is not configured yet.
 texlive-base depends on texlive-binaries (>= 2012.20120516); however:
  Package texlive-binaries is not configured yet.
 texlive-base depends on texlive-common (>= 2012.20120516); however:
  Package texlive-common is not configured yet.
 texlive-base depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-binaries (>= 2012-0); however:
  Package texlive-binaries is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
               No apport report written because MaxReports is reached already
                                                                             No apport report written because MaxReports is reached already
                                                           No apport report written because MaxReports is reached already
                                         No apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
                                                                   012.20120516); however:
  Package texlive-common is not configured yet.
 texlive-latex-base depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
 texlive-latex-base depends on texlive-base (>= 2012.20120516); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-common (>= 2012.20120516); however:
  Package texlive-common is not configured yet.
 texlive-fonts-recommended depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
 texlive-fonts-recommended depends on texlive-base (>= 2012.20120516); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-binaries (>= 2012-0); however:
  Package texlive-binaries is not configured yet.
 texlive-latex-recommended depends on texlive-latex-base (>= 2012.20120516); however:
  Package texlive-latex-base is not configured yet.
 texlive-latex-recommended depends on texlive-common (>= 2012.20120516); however:
  Package texlive-common is not configured yet.
 texlive-latex-recommended depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on texlive-common (>= 2012.20120516); however:
  Package texlive-common is not configured yet.
 texlive-generic-recommended depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
 texlive-generic-recommended depends on texlive-base (>= 2012.20120516); however:
  Package texlive-base is not configured yet.
dpkg: error processing texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tipa:
 tipa depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 tipa depends on texlive-base-bin; however:
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not configured yet.
 tipa depends on tex-common (>= 3); however:
  Version of tex-common on system is 2.10.
dpkg: error processing tipa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of jadetex:
 jadetex depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 jadetex depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 jadetex depends on texlive-fonts-recommended; however:
  Package texlive-fonts-recommended is not configured yet.
 jadetex depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 jadetex depends on tipa; however:
  Package tipa is not configured yet.
dpkg: error processing jadetex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-sanskrit:
 latex-sanskrit depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 latex-sanskrit depends on texlive-base; however:
  Package texlive-base is not configured yet.
dpkg: error processing latex-sanskrit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of preview-latex-style:
 preview-latex-style depends on tex-common; however:
  Package tex-common is not configured yet.
dpkg: error processing preview-latex-style (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of auctex:
 auctex depends on preview-latex-style; however:
  Package preview-latex-style is not configured yet.
dpkg: error processing auctex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hevea:
 hevea depends on texlive-base; however:
  Package texlive-base is not configured yet.
 hevea depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing hevea (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing pgf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on pgf (>= 1.00-1); however:
  Package pgf is not configured yet.
 latex-beamer depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tex4ht-common:
 tex4ht-common depends on texlive-base-bin; however:
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not configured yet.
dpkg: error processing tex4ht-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tex4ht:
 tex4ht depends on texlive-base-bin; however:
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not configured yet.
 tex4ht depends on tex4ht-common (= 20090611-1.1); however:
  Package tex4ht-common is not configured yet.
dpkg: error processing tex4ht (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive:
 texlive depends on texlive-latex-base (>= 2012.20120516); however:
  Package texlive-latex-base is not configured yet.
 texlive depends on texlive-fonts-recommended (>= 2012.20120516); however:
  Package texlive-fonts-recommended is not configured yet.
 texlive depends on texlive-latex-recommended (>= 2012.20120516); however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing texlive (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tex-common
 texlive-common
 texlive-binaries
 texlive-doc-base
 texlive-base
 texlive-latex-base
 texlive-fonts-recommended
 texlive-latex-recommended
 texlive-generic-recommended
 tipa
 jadetex
 latex-sanskrit
 preview-latex-style
 auctex
 hevea
 pgf
 latex-beamer
 tex4ht-common
 tex4ht
 texlive
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and in case you're interested in the output of ```
nano /etc/apt/sources.list
```

```

# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/multiverse/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/universe/binary-i386/
# deb cdrom:[Xubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise universe
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
 deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
 deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main


```

---

### Post by Bucky Ball on 2012-11-09
First run:

```
sudo apt-get autoremove
```Then try again, but when you get to this bit:

```
WARNING: The following packages cannot be authenticated!
   jadetex latex-sanskrit tex-common
 Install these packages without verification [y/N]? y
```... say 'n'.

****** Update***, and on second thoughts after a bit more digging around; you could just go to Synaptics (or Software Centre I guess) and uninstall these three:

jadetex
latex-sanskrit
tex-common

I'm not actually sure why they're installed on your system in the first place unless you installed them manually. They are not installed by default in my 12.04 and are for a specific purpose. Odd. See if uninstalling them does the trick unless you have installed them for a specific purpose (you are using TeX???). Good luck.

PS: If this does work and you can run just a regular, without the '-f':

```
sudo apt-get update
```... in a terminal without error, follow that up with:

```
sudo apt-get upgrade
```You have a lot of upgrades waiting there and 12.04.1 has just become 12.04.2. Got that update today.

If you can't do the regular update, add the '-f' like last time and see if the error's changed (which it should if you've removed the three things that were causing the previous one). ;)

---

### Post by bekirs on 2012-11-09
I tried to follow your commands but it didn't straightforwardly solved the problem. However, I succeeded to remove the 3 packages by using "Synaptic Package Manager". 

Automatic update notifications continued to appear and fail... I noticed that under **Update Manager>Settings>Other Software**, some texlive and texworks web addresses are selected. After removing the tick from those, automatic updates started to work properly again...

Indeed I had several unsuccessful installation experiences with TeXLive, TeXworks and some other LaTeX softwares... and probably I messed up while trying to solve the problem or uninstall them.

Before restarting my LaTeX adventure,could you tell me how to upgrade my xubuntu 12.04?

---

### Post by Bucky Ball on 2012-11-10
Upgrade? Upgrade to 12.10 or just upgrade the system? To upgrade the system, all apps and software, use:

```

sudo apt-get upgrade
```This will NOT upgrade to 12.10. Just software, if required. Make sure you always run:

```
sudo apt-get update
```... before the upgrade command. ;)

As this current problem appears to be solved, could you mark it as such and start a new thread(s) with any further, unrelated issues. Cheers. Post a link back here if you want.

PS: If you're want to upgrade the OS to 12.10 (although as this is working not sure why; you should have a specific reason to fix something that's not broken!) you can do that via Update Manager. A fresh install is generally cleaner, though.

---

### Post by bekirs on 2012-11-10
Hi, I was actually asking the upgrade from 12.04.1 to 12.04.2...

---

### Post by Bucky Ball on 2012-11-10
```
sudo apt-get upate
sudo apt-get upgrade
```... and I was actually telling you. ;) 

That will upgrade everything in your current system; kernel, apps, dependencies ... all software, if required. But WON'T upgrade the OS to 12.10.

PS: 12.04.1 to 12.04.2 is just a regular update/grade, not a release upgrade. This would just happen if you get your regular updates without issue or any manual intervention of bells and whistles. Just part of the cycle. It get to 12.04.4 next year where it stops and that's it. Then just regular updates but the basics of the release will then be locked. ;)

---

### Post by monkeybrain2012 on 2012-11-10
> **bekirs said:**
> Hi, I was actually asking the upgrade from 12.04.1 to 12.04.2...


12.04.2 won't be release until end of Jan next year.

[https://launchpad.net/ubuntu/+milestone/ubuntu-12.04.2](https://launchpad.net/ubuntu/+milestone/ubuntu-12.04.2)

---

