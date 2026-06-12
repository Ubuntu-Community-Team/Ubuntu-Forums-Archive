---
title: "rollback"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by vinceUUUU on 2008-05-14
Hello

what types of system restore features are available in Linux distro's?

My winXP has this feature that enables you to rewind your system back to an earlier snapshot....after any current problem situation with installs....

what kind of system is there within Linux?...does it need this kind  of system?...

thanks

Vince.

---

### Post by SunnyRabbiera on 2008-05-14
well yes there is a few backup utilities for ubuntu, some people here swear by simplebackup that is found in the repositories.

---

### Post by t0p on 2008-05-14
**cedar-backup2** and **pybackpack** are 2 backup utilities that I'm about to examine.  However, they're not the simple rollback-type solution you seem to want.

---

### Post by vinceUUUU on 2008-05-14
hello

well...how would you use these simple backup tools then...

say you were installing a new Linux tool into your system....and it went poorely...

what files and directories would you need to take note of....with regard to the tool that failed....and what files and directory's would you need to take note of with regard to your linux system and installs?...please?

what core directory's would you'd need to backup and restore...?

i am just talking about software installs here....installs that don't go so smoothe  and you want to rollback..

and how long would the tool take to do this job?....i remember system restore was instant...

thanks

Vince.

---

### Post by Paqman on 2008-05-14
If it's just a package you've installed, you shouldn't need to restore. Just uninstall the package. Linux is highly modular, there's not much you can do that will trash your system so much you can't fix it.

Simple Backup adds two menu options: simple backup and simple restore. How quickly it restores you to an earlier backup will depend on how much your system has changed since you last backed up.

---

