---
title: "can I get rid of &quot;ubuntu-mate-welcome&quot; and install MATE Desktop 1.14?"
date: 2016-09-07
forum: New to Ubuntu
---

### Post by 894532185610544562 on 2016-09-07
My info:
[B]Release 16.04.1 LTS (Xenial Xerus) 64-bit
Kernel Linux 4.4.0-36-generic x86_64
MATE 1.12.1[/B]

I have this PPA for some reason, I think it has to do with the welcome screen: 
[http://ppa.launchpad.net/ubuntu-mate-dev/welcome/ubuntu](http://ppa.launchpad.net/ubuntu-mate-dev/welcome/ubuntu)
Can I purge **ubuntu-mate-welcome** without the entire desktop blowing up? Because that was the warning when attempting to remove it.

Reading this, it appears my mate desktop version is out of date:
[https://launchpad.net/~ubuntu-mate-dev/+archive/ubuntu/xenial-mate](https://launchpad.net/~ubuntu-mate-dev/+archive/ubuntu/xenial-mate) ??? I really would prefer the latest mate versions and want to see [this pull request]("https://github.com/mate-desktop/caja/pull/605") implemented that brings back mouse button functionality.

---

### Post by howefield on 2016-09-07
Regarding the first issue, the desktop won't blow up by removing the welcome screen package.

```
hugh@xenial:~$ sudo apt purge ubuntu-mate-welcome
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  ubuntu-mate-desktop* ubuntu-mate-welcome*
0 to upgrade, 0 to newly install, 2 to remove and 0 to upgrade.
After this operation, 17.8 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 185168 files and directories currently installed.)
Removing ubuntu-mate-desktop (1.154) ...
Removing ubuntu-mate-welcome (16.04.9) ...
Purging configuration files for ubuntu-mate-welcome (16.04.9) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
hugh@xenial:~$
```

---

### Post by oldrocker99 on 2016-09-07
There is a checkbox for "Open Welcome when I log in" on the main screen; uncheck it and no more Welcome at login.

---

### Post by Geoffrey_Arndt on 2016-09-07
Well, the website for Mate you reference provides instructions for updating Mate via PPA add.

If having ALL the latest and greatest DE's and Apps, is important, then consider a true "Rolling Release" model such as Arch Linux.   Of course, there are pros and cons to rolling release models . . . not the least of which it is assumed that the user is well versed in Linux & Computer Systems ABC's.    If that's not the case, be prepared for some interesting responses to newbie questions.

---

### Post by Impavidus on 2016-09-07
> **howefield said:**
> Regarding the first issue, the desktop won't blow up by removing the welcome screen package.

```

The following packages will be REMOVED
  ubuntu-mate-desktop* ubuntu-mate-welcome*
```

ubuntu-mate-desktop is a metapackage. It doesn't contain anything itself, but has dependencies to conveniently pull in a lot of default mate software. The worst thing that can happen after purging is that some packages may turn autoremovable. You may want to check that and set those packages as manually installed. But I think that if you got these packages automatically during installation, the dependencies of ubuntu-mate-desktop are already marked as manually installed.

---

### Post by 894532185610544562 on 2016-09-07
> **oldrocker99 said:**
> There is a checkbox for "Open Welcome when I log in" on the main screen; uncheck it and no more Welcome at login.

Unchecking that box doesn't apparently remove the PPA so it just keeps updating in the background whenever there's a new update to the welcome screen?

> **Impavidus said:**
> ubuntu-mate-desktop is a metapackage. It doesn't contain anything itself, but has dependencies to conveniently pull in a lot of default mate software. The worst thing that can happen after purging is that some packages may turn autoremovable. You may want to check that and set those packages as manually installed. But I think that if you got these packages automatically during installation, the dependencies of ubuntu-mate-desktop are already marked as manually installed.

The concept of removing metapackages when getting rid of a child package is a strange concept to me. Is the theory something like, "well **metapackagex** sees one of its child packages has been removed...better go re-download and install it" ... so by removing **metapackagex** (when a child package gets removed) will stop that behavior? There's quite a bit that **ubuntu-mate-desktop** depends: vlc...gufw...caja...all of these are listed as "installed" in synaptic...how do I check whether they are "manually" installed? And yes they were installed through the iso.

---

### Post by Geoffrey_Arndt on 2016-09-07
Seems like Howefield's post (#2) addresses the core issue . . . does it not?

---

### Post by vasa1 on 2016-09-07
> **Geoffrey_Arndt said:**
> Seems like Howefield's post (#2) addresses the core issue . . . does it not?

All the same, the information that removing package X will cause the removal of *buntu-desktop as well terrifies quite a few users :) 

Re. OP's concern about "*There's quite a bit that ubuntu-mate-desktop depends: vlc...gufw...caja...all of these are listed as "installed" in synaptic...how do I check whether they are "manually" installed?*", I have routinely caused lubuntu-desktop to be removed when I removed a package listed by the lubuntu-desktop metapackage, but that didn't affect other packages and I've never found the need to check whether they're manually installed or installed automatically.

As a side-note, [autoremove can cause issues]("https://ubuntuforums.org/showthread.php?t=2314397") but I haven't encountered problems myself.

---

### Post by Geoffrey_Arndt on 2016-09-07
Well OK, . . . on changes like this I don't do on a PROD machine.    Best to do on a Test PC or at least, on a Test partition if you have the resources.

---

### Post by howefield on 2016-09-08
> **894532185610544562 said:**
> Unchecking that box doesn't apparently remove the PPA so it just keeps updating in the background whenever there's a new update to the welcome screen?

As far as I can see, the ubuntu-mate-welcome package is in the Ubuntu *universe* repository so as long as you have the package installed you will continue to get updates for it, so either uninstall it or mark it as a held package so that it doesn't update. To confirm, use..

```
apt-cache policy ubuntu-mate-welcome
```

Is this installation an older one that has been upgraded to 16.04 ? Just curious as to where the ubuntu-mate-dev ppa came from, it wouldn't be installed by default with 16.04, so it has either been manually added or perhaps installed by default prior to Mate becoming an official Ubuntu flavour.

---

### Post by 894532185610544562 on 2016-09-08
> **howefield said:**
> As far as I can see, the ubuntu-mate-welcome package is in the Ubuntu *universe* repository so as long as you have the package installed you will continue to get updates for it, so either uninstall it or mark it as a held package so that it doesn't update. To confirm, use..

```
apt-cache policy ubuntu-mate-welcome
```

```
ubuntu-mate-welcome:
  Installed: 16.10.0~xenial1.11
  Candidate: 16.10.0~xenial1.11
  Version table:
 *** 16.10.0~xenial1.11 500
        500 http://ppa.launchpad.net/ubuntu-mate-dev/welcome/ubuntu xenial/main amd64 Packages
        500 http://ppa.launchpad.net/ubuntu-mate-dev/welcome/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status
     16.04.9.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
     16.04.9 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
```

> Is this installation an older one that has been upgraded to 16.04 ? Just curious as to where the ubuntu-mate-dev ppa came from, it wouldn't be installed by default with 16.04, so it has either been manually added or perhaps installed by default prior to Mate becoming an official Ubuntu flavour.

No manual install of this PPA...and I installed the OS fresh, straight from the mate download site. 16.04.1 LTS: [https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/)

---

### Post by vasa1 on 2016-09-08
You could try asking on Google Plus. I've noticed Martin Wimpress to be quite active there: [https://plus.google.com/communities/108331279007926658904](https://plus.google.com/communities/108331279007926658904)

The list of files provided by Ubuntu Mate is here: [http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/release/ubuntu-mate-16.04-desktop-amd64.manifest](http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/release/ubuntu-mate-16.04-desktop-amd64.manifest)

```
ubuntu-mate-wallpapers-common	16.04.6
ubuntu-mate-wallpapers-xenial	16.04.6
ubuntu-mate-welcome	16.04.9
ubuntu-minimal	1.361

```So how you've ended up with "Installed: 16.10.0~xenial1.11" is unclear. It's quite unusual for a release to include a ppa by default.

---

### Post by 894532185610544562 on 2016-09-08
Well that's odd, I purged the welcome package but that PPA still remained, even after reboot. Manually deleted it. Hopefully that's the end of it.

---

### Post by 894532185610544562 on 2016-09-08
> **vasa1 said:**
> You could try asking on Google Plus. I've noticed Martin Wimpress to be quite active there: [https://plus.google.com/communities/108331279007926658904](https://plus.google.com/communities/108331279007926658904)

The list of files provided by Ubuntu Mate is here: [http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/release/ubuntu-mate-16.04-desktop-amd64.manifest](http://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/release/ubuntu-mate-16.04-desktop-amd64.manifest)

```
ubuntu-mate-wallpapers-common    16.04.6
ubuntu-mate-wallpapers-xenial    16.04.6
ubuntu-mate-welcome    16.04.9
ubuntu-minimal    1.361

```So how you've ended up with "Installed: 16.10.0~xenial1.11" is unclear. It's quite unusual for a release to include a ppa by default.

16.04.1 vs 16.04?

---

### Post by howefield on 2016-09-08
> **894532185610544562 said:**
> [CODE]No manual install of this PPA...and I installed the OS fresh, straight from the mate download site. 16.04.1 LTS: [https://ubuntu-mate.org/download/](https://ubuntu-mate.org/download/)

Well, very strange because the ppa isn't installed by default. It has to be added post install.

The PPA only has one package in it, ubuntu-mate-welcome which is included as said, in the *universe* repository. In any event, it doesn't really matter how the ppa was added, you seem to have got it sussed.  

> **894532185610544562 said:**
> Well that's odd, I purged the welcome package but that PPA still remained, even after reboot. Manually deleted it. Hopefully that's the end of it.

That would be normal, all the ppa does is tell the system what packages are available for install, whether they actually are or not.

---

