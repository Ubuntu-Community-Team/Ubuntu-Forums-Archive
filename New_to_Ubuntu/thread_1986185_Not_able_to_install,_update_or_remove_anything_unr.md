---
title: "Not able to install, update or remove anything: unrecoverable fatal error"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by nkl on 2012-05-24
Hi everyone,
                    I am using Lucid Lynx. One day when I started my ubuntu, the avant-window-navigator (AWN) crashed. All icons became sad face smiley on the awn bar. I thought there might be some problem with the awn. I didn't pay attention on that. But later, when I was trying to install something, I got this error:

dpkg: unrecoverable fatal error, aborting:
 files list file for package 'avant-window-navigator-trunk' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

then I tried to reinstall awn.. but same error. Now, neither I can remove any software nor install. I tried replacing /var/lib/dpkg/diversions and others with their old copy, but still no luck.
I want to upgrade Lucid to Precise. But :( without solving this problem, it won't be possible. So I need you guys help.

---

### Post by nkl on 2012-05-26
any suggestions??

---

### Post by wilee-nilee on 2012-05-26
> **nkl said:**
> any suggestions??

Open synaptic go to custom filters and then broken packages.

What you want to do is purge/fully remove all packages attached to awn. Check the .config file in home it is hidden for a awn folder to make sure it is gone after the full removal, not sure if one wil be there never used it. Then reinstall it if you want it.

If you are getting errors in a terminal on any updates or upgrades or installs or purges or removals post those details are helpful.

It may be that just fixing broken packages may be all you need, hard to say really.

---

### Post by raja.genupula on 2012-05-26
could you give us the output of

```
sudo apt-get update
```

---

### Post by nkl on 2012-05-26
Thanks for your replies wilee-nilee and raja.
@wilee-nilee: It is not showing any package in broken package's list. In .config folder, awn folder is not there. When I try to remove, say avant-window-navigator-trunk, I get this:
```
$ sudo apt-get remove avant-window-navigator-trunk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpackagekit-glib2-12 kpackagekit fortunes-min awn-applets-common-trunk
  python-gdata fortune-mod zeitgeist dolphin zeitgeist-core
  libpackagekit-qt-12 librecode0 libdesktop-agnostic-fdo-glib kfind
  python-packagekit packagekit python-gweather zeitgeist-datahub
  python-awn-extras-trunk update-manager-kde libqca2-plugin-ossl
  packagekit-backend-apt libzeitgeist-1.0-0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  avant-window-navigator-data-trunk avant-window-navigator-trunk
  awn-applets-c-core-trunk awn-applets-c-extras-trunk
  awn-applets-python-core-trunk awn-applets-python-extras-trunk
  awn-settings-trunk
0 upgraded, 0 newly installed, 7 to remove and 47 not upgraded.
After this operation, 13.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 85%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'avant-window-navigator-trunk' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```@raja: sudo apt-get update works fine, without error. Still, the output is:
```
Hit http://mirror.cse.iitd.ernet.in lucid Release.gpg
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid/main Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid/restricted Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid/universe Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid/multiverse Translation-en_IN
Hit http://mirror.cse.iitd.ernet.in lucid-proposed Release.gpg
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-proposed/main Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-proposed/restricted Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-proposed/universe Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-proposed/multiverse Translation-en_IN
Hit http://mirror.cse.iitd.ernet.in lucid-updates Release.gpg
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-updates/main Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-updates/restricted Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-updates/universe Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-updates/multiverse Translation-en_IN
Hit http://mirror.cse.iitd.ernet.in lucid-security Release.gpg
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-security/main Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-security/restricted Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-security/universe Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-security/multiverse Translation-en_IN
Hit http://mirror.cse.iitd.ernet.in lucid-backports Release.gpg
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-backports/main Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-backports/restricted Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-backports/universe Translation-en_IN
Ign http://mirror.cse.iitd.ernet.in/ubuntu/ lucid-backports/multiverse Translation-en_IN
Hit http://mirror.cse.iitd.ernet.in lucid Release
Hit http://mirror.cse.iitd.ernet.in lucid-proposed Release
Hit http://mirror.cse.iitd.ernet.in lucid-updates Release
Hit http://mirror.cse.iitd.ernet.in lucid-security Release
Hit http://mirror.cse.iitd.ernet.in lucid-backports Release
Hit http://mirror.cse.iitd.ernet.in lucid/main Packages
Hit http://mirror.cse.iitd.ernet.in lucid/restricted Packages
Hit http://mirror.cse.iitd.ernet.in lucid/universe Packages
Hit http://mirror.cse.iitd.ernet.in lucid/multiverse Packages
Hit http://mirror.cse.iitd.ernet.in lucid/main Sources
Hit http://mirror.cse.iitd.ernet.in lucid/restricted Sources
Hit http://mirror.cse.iitd.ernet.in lucid/universe Sources
Hit http://mirror.cse.iitd.ernet.in lucid/multiverse Sources
Hit http://mirror.cse.iitd.ernet.in lucid-proposed/main Packages
Hit http://mirror.cse.iitd.ernet.in lucid-proposed/restricted Packages
Hit http://mirror.cse.iitd.ernet.in lucid-proposed/universe Packages
Hit http://mirror.cse.iitd.ernet.in lucid-proposed/multiverse Packages
Hit http://mirror.cse.iitd.ernet.in lucid-proposed/main Sources
Hit http://mirror.cse.iitd.ernet.in lucid-proposed/restricted Sources
Hit http://mirror.cse.iitd.ernet.in lucid-proposed/universe Sources
Hit http://mirror.cse.iitd.ernet.in lucid-proposed/multiverse Sources
Hit http://mirror.cse.iitd.ernet.in lucid-updates/main Packages
Hit http://mirror.cse.iitd.ernet.in lucid-updates/restricted Packages
Hit http://mirror.cse.iitd.ernet.in lucid-updates/universe Packages
Hit http://mirror.cse.iitd.ernet.in lucid-updates/multiverse Packages
Hit http://mirror.cse.iitd.ernet.in lucid-updates/main Sources
Hit http://mirror.cse.iitd.ernet.in lucid-updates/restricted Sources
Hit http://mirror.cse.iitd.ernet.in lucid-updates/universe Sources
Hit http://mirror.cse.iitd.ernet.in lucid-updates/multiverse Sources
Hit http://mirror.cse.iitd.ernet.in lucid-security/main Packages
Hit http://mirror.cse.iitd.ernet.in lucid-security/restricted Packages
Hit http://mirror.cse.iitd.ernet.in lucid-security/universe Packages
Hit http://mirror.cse.iitd.ernet.in lucid-security/multiverse Packages
Hit http://mirror.cse.iitd.ernet.in lucid-security/main Sources
Hit http://mirror.cse.iitd.ernet.in lucid-security/restricted Sources
Hit http://mirror.cse.iitd.ernet.in lucid-security/universe Sources
Hit http://mirror.cse.iitd.ernet.in lucid-security/multiverse Sources
Hit http://mirror.cse.iitd.ernet.in lucid-backports/main Packages
Hit http://mirror.cse.iitd.ernet.in lucid-backports/restricted Packages
Hit http://mirror.cse.iitd.ernet.in lucid-backports/universe Packages
Hit http://mirror.cse.iitd.ernet.in lucid-backports/multiverse Packages
Hit http://mirror.cse.iitd.ernet.in lucid-backports/main Sources
Hit http://mirror.cse.iitd.ernet.in lucid-backports/restricted Sources
Hit http://mirror.cse.iitd.ernet.in lucid-backports/universe Sources
Hit http://mirror.cse.iitd.ernet.in lucid-backports/multiverse Sources
Reading package lists... Done

```

---

### Post by mapes12 on 2012-05-26
> I want to upgrade Lucid to Precise.If this is the objective then what I would do is make sure I backup my personal files, make a note of any applications I use including any configuration stuff, then do a fresh install. 

I use Xmarks to keep my FF bookmarks in sync.

---

### Post by nkl on 2012-05-26
Upgrading Lucid to Precise is not my main motive, though I want to upgrade it. I don't want to install all programs again as well as configuring the desktop.
If there is no other option,  then I will do a fresh install. :-(

---

### Post by nkl on 2012-12-11
Found solution to my problem here:
[http://www.linuxquestions.org/questions/showthread.php?p=4846856#post4846856](http://www.linuxquestions.org/questions/showthread.php?p=4846856#post4846856)

basically, I deleted the avant-window-navigator-trunk.list file in /var/lib/dpkg/info/
and then ran *sudo apt-get remove avant-window-navigator-trunk --purge *and problem solved :p

---

