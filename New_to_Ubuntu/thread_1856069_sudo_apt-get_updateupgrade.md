---
title: "sudo apt-get update/upgrade"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by Perplexed Pat on 2011-10-06
> **avtolle said:**
> When you do the update command, the information in the system as to the repositories is refreshed "to date". When you do the upgrade command, the refreshed information is used by the system to determine whether there are updated packages to install to update your system, and, if so, the same are reported to you and then, after you accept them, downloaded and installed. During this process, some packages will be "held back" for the reasons I posted earlier. To install updated kernel, the dist-upgrade command is used. Many recommend that when doing a CLI update, all three commands be used, e.g.```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```to get all available updates installed. HTH.
My poor little computer won't work on Ubuntu 11, I've tried. Will sudo apt-get upgrade work for me?

---

### Post by oldos2er on 2011-10-07
Post moved to its own thread, and edited for inappropriate language.

---

### Post by duke.tim on 2011-10-07
Maybe? go ahead and try it.

You need to give us a little more information about your problem, to get good advice.

---

### Post by audiomick on 2011-10-07
How about a few clues.
What have you got on the computer now?
How "modern" is the computer" CPU? Graphics? RAM? Any specs at all?

---

### Post by woodp on 2011-10-13
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

I have a similar question - Running 11.04 on a modern laptop with no problems. The code sequence above has worked for all core upgrades as far back as I can remember (7.xx).

But when I try to do a 11.04 to 11.10 upgrade, **dist-upgrade** doesn't work.

Update Manager *(update-manager -d)* brings up the option to install 11.10. Why won't dist-upgrade?

---

### Post by gmargo on 2011-10-13
> **woodp said:**
> Update Manager *(update-manager -d)* brings up the option to install 11.10. Why won't dist-upgrade?

**apt-get** (and **aptitude**) will never edit the **/etc/apt/sources.list** file.  If you manually edit that file to change references from 'natty' to 'oneiric', then "apt-get dist-upgrade" will perform the release upgrade you expect. This is how we did it in the olden days.

But now the recommended way to upgrade is through either the **update-manager** command (the GUI way), or the **do-release-upgrade** command (the CLI way).

---

### Post by woodp on 2011-10-13
Great response. Thank you!

---

### Post by MG&amp;TL on 2011-10-13
Install 11.10 and use Unity2d-I find it has a very similiar footprint to GNOME.

---

### Post by oldos2er on 2011-10-13
> **woodp said:**
> But when I try to do a 11.04 to 11.10 upgrade, **dist-upgrade** doesn't work.

Update Manager *(update-manager -d)* brings up the option to install 11.10. Why won't dist-upgrade?

From **man apt-get**:

 dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new
versions of packages; apt-get has a "smart" conflict resolution
system, and it will attempt to upgrade the most important           packages at the expense of less important ones if necessary. So,
dist-upgrade command may remove some packages. The  /etc/apt/sources.list file contains a list of locations from
which to retrieve desired package files. See also
           apt_preferences(5) for a mechanism for overriding the general settings for individual packages.

Seems some people assume from the wording *dist*-upgrade that their *distro* will be upgraded. But that's not the function of dist-upgrade, as you see.

---

