---
title: "Is there a replacement for the software center?"
date: 2014-01-03
forum: New to Ubuntu
---

### Post by StevenHodges92 on 2014-01-03
Is there another package installer I can use instead of the Ubuntu Software Center because whenever I open the software center it just freezes upon startup and when I try to purge it and re install it or update it I get this:

```
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/workrave:workrave.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
Software catalog update was successful.

```

Is there an easy way to just fix this problem with the software center?

---

### Post by Irihapeti on 2014-01-03
You can install synaptic package manager -- sudo apt-get install synaptic . It's usually the first thing I install in a new system.

Usually there's no need to remove software center.

I've seen those errors re sonic-visualiser many times. Not sure what they are but I just ignore them.

---

### Post by monkeybrain20122 on 2014-01-03
Yes, of course. :) I always use synpatic instead of the Software Centre. 

```
sudo apt-get install synaptic
```

Then if you download the occasional .deb and want to be able to install by right clicking, install gdebi and make it the default to open this kind of files (instead of the USC) It is a lot faster than the USC, it would finish installing by the time USC starts. :)

```
sudo apt-get install gdebi.
```

---

### Post by bertan2 on 2014-01-03
Judging by the text of those messages, it looks like a bug in the Software Center.

You can install pretty much anything from the command line if you know the name of the package:

**sudo apt-get install packagenamegoeshere**

---

### Post by monkeybrain20122 on 2014-01-03
> **bertan2 said:**
> Judging by the text of those messages, it looks like a bug in the Software Center.

You can install pretty much anything from the command line if you know the name of the package:

**sudo apt-get install packagenamegoeshere**


Yeah what if you don't know the exact name of the package or just want to browse? What if name of package has changed? (so say instead of foo it is now foo2-3?) "Do the terminal" is not a very helpful answer for new users while there are clearly more appropriate alternatives.

---

### Post by ajgreeny on 2014-01-03
Like some of the others who have replied, I also use synaptic for installing and removing packages and it is the first thing I add after installing a new system.  Try it and you won't regret it; it is quicker than USC in my opinion, but more importantly, it is very much more flexible and can do many things that USC can not, for example, searching for details of installed files of any installed package.

---

### Post by mc4man on 2014-01-03
> **StevenHodges92 said:**
> Is there another package installer I can use instead of the Ubuntu Software Center because whenever I open the software center it just freezes upon startup and when I try to purge it and re install it or update it I get this:

```
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/workrave:workrave.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
Software catalog update was successful.

```

Is there an easy way to just fix this problem with the software center?
There is nothing to fix, that just reflects that those 2 sources have some issues with their .desktops. **You can safely ignore**.

Never looked at workrave but the issue with sonic-visualiser is the package has 3 .desktops, 2 are not needed & have improper install paths. Maybe someone will fix for 14.04, maybe not.
See here
[https://bugs.launchpad.net/ubuntu/+source/sonic-visualiser/+bug/1161283](https://bugs.launchpad.net/ubuntu/+source/sonic-visualiser/+bug/1161283)

The issue is that app-install-data lists all 3 .desktops, it should only list the actual one. If you really wanted the S-C message concerning s-v to go away then you'd simply remove the 2 highlighted .desktops in screen

---

### Post by andrew.46 on 2014-01-04
> **monkeybrain20122 said:**
> Yeah what if you don't know the exact name of the package or just want to browse? What if name of package has changed? (so say instead of foo it is now foo2-3?) .

A little time spent with:

```
apt-cache search *regex*
```

would be a great supplement to searches with either Synaptic or the Software Centre...

---

