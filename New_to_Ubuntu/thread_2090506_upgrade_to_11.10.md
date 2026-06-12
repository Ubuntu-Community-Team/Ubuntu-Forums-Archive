---
title: "upgrade to 11.10"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by wizardkc on 2012-12-02
Upgrading from 11.04 to 11.10 and have run into a problem
The upgrade fetch completes,
Setting up software channel has a problem and disables some entries in sources.list
Package manager gives the following error:

-------------------------------------------------------------------------------
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug update-manager' in a terminal.
----------------------------------------------------------------------
None of the above apply
----------------------------------------------------------------------
In sources.list all the references to natty have been changed to oneiric.  There are three references to lucid:
          # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
     Other lines
          # deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
         deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

All three lines were uncommented  before the upgrade was started.

I have tried commenting out the three lines before performing the upgrade, and the closest I could get was to have lots of updates individually show up.  I abandoned that effort.

Thanks in advance.
Kerry

---

### Post by ajgreeny on 2012-12-02
What files are there in the folder /etc/apt/sources.list.d?

Any repositories other than the standard Ubuntu ones will have their entries in that folder, not in the sources.list file itself, and will be shown in the software-sources dialog in the "**Other Software**" tab, so if you have anything there highlight it and use the **Remove** button then try the upgrade again.

---

