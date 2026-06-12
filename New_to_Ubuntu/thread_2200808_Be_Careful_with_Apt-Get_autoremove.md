---
title: "Be Careful with Apt-Get autoremove"
date: 2014-01-21
forum: New to Ubuntu
---

### Post by dave2001 on 2014-01-21
Just a reminder for newbies (and those like myself, who have been using linux for years, but still manage to make silly mistakes all the time):

The command ```
sudo apt-get autoremove
``` which is often suggested to be run by the terminal output after using apt-get to install or remove something, can do bad things to your installation of ubuntu.

I used "apt-get autoremove" for the first time.  I looked over the packages it said it was going to be getting rid of, then I ran it, only to find it removed a few packages I don't remember seeing listed in the "packages to be removed" text. Important and useful packages like my text editor and file manager (kwrite and dolphin)!  

The man-page for apt-get claims the autoremove command " is used to remove packages that were automatically installed to satisfy dependencies for other packages and are now no longer needed."  The default file manager of a major desktop environment is not exactly something that should fit into this category.   Now I'm left wondering if it uninstalled some other, less noticable, but equally vital packages.

Did I do something wrong here? Is there some linux hoo-doo I neglected to perform before using autoremove?

---

### Post by vasa1 on 2014-01-21
Please provide some context if you can. It would possibly help understand what happened. Otherwise, others may appear just to say that they've been using apt-get autoremove for years without problems.

Since you have experience, perhaps you could provide the context from /var/log/apt.

---

### Post by westie457 on 2014-01-21
Been there done that.

Recently found out about the simulate option. This tells you what is going to be removed or installed.

```
sudo apt-get -s
```with whatever you intend to do with apt-get.

The '-s' option overrides the lock caused by having another 'apt' process running (software centre/update-manager as examples) and shows what is going to happen for real.

No changes happen to the system, only a simulation is run.

---

### Post by dave2001 on 2014-01-21
> **vasa1 said:**
> Please provide some context if you can. It would possibly help understand what happened. Otherwise, others may appear just to say that they've been using apt-get autoremove for years without problems.

Since you have experience, perhaps you could provide the context from /var/log/apt.

Rather than reinstalling missing packages, and fussing with going through logs and making sure I wasn't missing anything important but less noticable, I just re-imaged the partition with my latest backup (which was just from last night since this is pretty new installation). Took all of 2 minutes while I walked into the kitchen and got a snack.

So this means my computer is in the exact state it was before the whole problem. I tried auto-remove again..(with results below) and now it DOES list dolphin and kwrite amongst the packages to be removed.. I could swear they weren't before, but it's likely just I missed them when reading over the list initially. Still doesn't make sense to my why they would be there though.

```
boku@T500-Saucy-Sal:~$ sudo apt-get -s autoremove
[sudo] password for boku: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  acl app-install-data-partner at-spi2-core colord dolphin gcr gir1.2-soup-2.4
  gnome-keyring init-system-helpers kde-baseapps-bin kfind konqueror-nsplugins kwrite
  libatk-bridge2.0-0 libatspi2.0-0 libcap-ng0 libcap2-bin libcolord1 libcolorhug1
  libgcr-ui-3-1 libgtk-3-0 libgtk-3-bin libgtk-3-common libgusb2 libieee1284-3
  libkonqsidebarplugin4a libnepomukwidgets4 libp11-kit-gnome-keyring libpam-cap
  libpam-gnome-keyring libruby1.9.1 libsane libsane-common libwayland-cursor0
  libxkbcommon0 libyaml-0-2 p11-kit plasma-widget-folderview python-crypto
  python-dirspec python-httplib2 python-oauthlib python-openssl python-pam
  python-serial python-twisted-bin python-twisted-core python-twisted-web
  python-ubuntu-sso-client python-zope.interface ruby ruby1.9.1 ubuntu-sso-client
0 upgraded, 0 newly installed, 53 to remove and 0 not upgraded.
Remv colord [1.0.2-1]
Remv libsane [1.0.23-0ubuntu3]
Remv acl [2.2.52-1]
Remv app-install-data-partner [13.04]
Remv at-spi2-core [2.10.1-0ubuntu0.1]
Remv dolphin [4:4.11.3-0ubuntu0.1]
Remv ubuntu-sso-client [13.10-0ubuntu1.1]
Remv python-ubuntu-sso-client [13.10-0ubuntu1.1]
Remv gnome-keyring [3.8.2-0ubuntu3.1]
Remv gcr [3.8.2-4]
Remv gir1.2-soup-2.4 [2.42.2-6]
Remv init-system-helpers [1.7]
Remv kde-baseapps-bin [4:4.11.3-0ubuntu0.1]
Remv kfind [4:4.11.3-0ubuntu0.1]
Remv konqueror-nsplugins [4:4.11.3-0ubuntu0.1]
Remv kwrite [4:4.11.3-0ubuntu0.1]
Remv libgtk-3-bin [3.8.6-0ubuntu3.1]
Remv libgcr-ui-3-1 [3.8.2-4]
Remv libgtk-3-0 [3.8.6-0ubuntu3.1]
Remv libatk-bridge2.0-0 [2.10.0-1]
Remv libatspi2.0-0 [2.10.1-0ubuntu0.1]
Remv libcap-ng0 [0.7.3-1ubuntu1]
Remv libcap2-bin [1:2.22-1.2ubuntu2]
Remv libcolorhug1 [1.0.2-1]
Remv libcolord1 [1.0.2-1]
Remv libgtk-3-common [3.8.6-0ubuntu3.1]
Remv libgusb2 [0.1.5-0ubuntu1]
Remv libieee1284-3 [0.2.11-11]
Remv libkonqsidebarplugin4a [4:4.11.3-0ubuntu0.1]
Remv libnepomukwidgets4 [4:4.11.2-0ubuntu1]
Remv libp11-kit-gnome-keyring [3.8.2-0ubuntu3.1]
Remv libpam-cap [1:2.22-1.2ubuntu2]
Remv libpam-gnome-keyring [3.8.2-0ubuntu3.1]
Remv ruby [1:1.9.3]
Remv ruby1.9.1 [1.9.3.194-8.1ubuntu2.1]
Remv libruby1.9.1 [1.9.3.194-8.1ubuntu2.1]
Remv libsane-common [1.0.23-0ubuntu3]
Remv libwayland-cursor0 [1.1.0-2ubuntu3]
Remv libxkbcommon0 [0.3.1-1]
Remv libyaml-0-2 [0.1.4-2build1]
Remv p11-kit [0.18.3-2ubuntu1]
Remv plasma-widget-folderview [4:4.11.3-0ubuntu0.1]
Remv python-oauthlib [0.5.1-1]
Remv python-crypto [2.6-5]
Remv python-dirspec [13.10-0ubuntu1]
Remv python-httplib2 [0.8-2]
Remv python-openssl [0.13-2ubuntu4]
Remv python-pam [0.4.2-13ubuntu6]
Remv python-serial [2.6-1]
Remv python-twisted-web [13.0.0-1]
Remv python-twisted-core [13.0.0-1ubuntu1]
Remv python-twisted-bin [13.0.0-1ubuntu1]
Remv python-zope.interface [4.0.5-1ubuntu2]

```

---

### Post by vasa1 on 2014-01-21
Dave, what may provide a clue is what was run ***before*** apt-get automremove. In other words, what did you delete before running apt-get autoremove?

Edit: changed remove to autoremove.

The other point is that running apt-get autoremove frequently will give a better idea of what is being removed and why.

If one runs autoremove after a lot of removes/purges it won't be easy to link cause and effect.

---

### Post by philinux on 2014-01-21
@dave,

Is this a pure KDE install or ubuntu then you installed kubuntu-desktop etc?

---

### Post by tgalati4 on 2014-01-21
Yes, autoremove can cause problems if you add piece parts of different desktop environments.  Because you don't have the meta-packages installed, the package manager gets confused as to why you have these piece parts installed.  An alternative is to install the meta-packages and then uninstall the pieces that you don't want.  Of course that can cause breakage as well.  If you "pin" a particular package, that might protect it from autoremove.

---

### Post by vasa1 on 2014-01-21
> **tgalati4 said:**
> Yes, autoremove can cause problems ... If you "pin" a particular package, that might protect it from autoremove.
I'm sure it's possible to contrive situations for anything to break. I, personally, have not experienced breakage with apt-get.

Re. pinning, suppose apt-get autoremove wants to remove package_A and package_B but a user wants to retain package_B, then 
exit by pressing "n" instead of continuing with the process
run sudo apt-get install package_B
run sudo apt-get autoremove. Now apt-get autoremove will only prompt to remove package_A.

---

### Post by Bashing-om on 2014-01-21
@ vasa1; Nice one !

Great to know.

[INDENT][INDENT][INDENT]thanks from me
[/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-01-21
There are two possible use cases here, and people frequently get confused between them.

Use Case #1: Fresh install (or release-upgrade). Most applications and utilities and lots of other packages are automatically marked as manually-installed despite that they are automatically-installed. So if you installed Kubuntu from an .iso, Dolphin is installed automatically, but marked as manual. When you customize your system, you can remove the kubuntu-desktop metapackage, but all your applications don't autoremove.
Advantage: Autoremove won't uninstall large chunks of your system when you uninstall a metapackage or key application.
Disadvantage: Lots of dependencies are not autoremoved when no longer needed. This is a lot of the stuff that minimal-install folks and are trying to avoid.

Tip: Use the command **apt-mark showmanual** to see what is currently marked as manual on your system.
Tip: Use the command **sudo apt-mark [auto | manual] <packagename>** to change a package's (or list of packages) marking.

Use Case #2: Adding a new application plus dependencies. New stuff you install is properly marked by apt as manually-installed, and all the dependencies that come with it are properly-marked as automatically-installed. It's dependency management the way we expect apt to behave...except when users install entire desktop environments and forget that Dolphin is a (automatic) dependency of (manual) kubuntu-desktop and other kubuntu applications.
Advantage: For single applications and libs, expected behavior.
Disadvantage: Removing a metapackage may remove large chunks of included packages.


I think the big news here is that you read the apt-get output, you had a backup, and that you saved yourself a lot of heartache.
Good for you!

---

### Post by dave2001 on 2014-01-22
In response to Vasa1 and Philinux,

This is a fresh installation of ubuntu 13.10. I made a base-system only install from the minimal.iso. Then rebooted into base system tty prompt. From cli, I installed some needed basic packages such as manpages, nano, etc. Then I installed the kde-plasma-desktop metapackage (which is the smaller of the kde metapackages, and has very little included default software with it). I then installed some other software I desired (such as kcalc, libre-office, okular, etc) using apt-get.

So there was literally nothing purged, removed , or otherwise deleted before I ran auto-remove.

---

### Post by ptn107 on 2014-01-23
I keep a little [_tool_]("https://www.dropbox.com/s/sbbthmni9xodr7j/list-packages.tar.gz") around in my Dropbox for such occasions.  If I ever do something accidental and a lot of stuff got removed I can run
```
sudo list-missing saucy ubuntu
```
and look at the missing.packages file in my home folder and see what's missing from my install.  Or on the reverse if I ever install too much crap (I build and compile a lot of packages from scratch) then I can remove anything additional by running
```
sudo list-extra saucy ubuntu
```
and check the extra.packages file in my home folder for all the packages safe to remove.

This is useful with Ubuntu and Lubuntu at the moment.  Not any other environments.

---

### Post by rahul_bhise on 2014-08-20
> **dave2001 said:**
> Rather than reinstalling missing packages, I just re-imaged the partition with my latest backup Took all of 2 minutes while I walked into the kitchen and got a snack. 

rather its off the topic
but i would like to know which tool you used to take the backup.

---

