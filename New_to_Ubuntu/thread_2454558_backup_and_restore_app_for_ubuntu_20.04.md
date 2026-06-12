---
title: "backup and restore app for ubuntu 20.04"
date: 2020-12-01
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-12-01
what is a good backup and restore app that you like and have been using for years. i will be using an external hard drive for the backup. or old school command and reinstall scripts.
please ones that you may like. tks

---

### Post by GhX6GZMB on 2020-12-02
Timeshift.

---

### Post by TheFu on 2020-12-02
rdiff-backup since around 2010 for about 20 systems.
Same for desktops and servers. No need for 3 other backup tools for a complete solution.
Daily, automatic, versioned, backups that are stored efficiently and runs faster than other options.

However, there isn't any GUI.  GUIs are a liability. Running a GUI incorrectly with elevated privileges can cause problems. Usually, it is just better not to do that.

Also used back-in-time for a few years - suitable only for end user file backups. Most backup tools with GUIs are useful only for end-user files - effectively the HOME directory for 1 user.  If you want a system backup, then that needs to run with elevated privileges to retain user permissions, ownership, groups, ACLs and xattrs of all the files.  Without those, no backup tool can restore a correct set of files.

Of course, there are highly inefficient ways to do backups (not versioned) which have a GUI and waste time and lots of storage. But few people can have 3x the amount of storage as the source files just for backups.  1 copy ("a" backup), is never sufficient.

---

### Post by mastablasta on 2020-12-02
Areca is also an option. it has GUI and CLI and i use in the way you propose. but on windows PC.&#382;i also used it on XP and linxu before, but not so much lately.
on linux i mostly have static data that i copy to another disk when i am done with it or when i think "hmm this could be important". for exmaple photos, documents, i would always make a copy on another drive and then another copy on external drive, before i open them. and that copy stays there.

or i use my nextcloud server for photos.

---

### Post by rburkartjo on 2020-12-02
tks ya'll

---

