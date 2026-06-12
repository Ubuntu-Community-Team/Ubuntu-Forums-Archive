---
title: "CLI Maintenance Commands"
date: 2014-07-27
forum: New to Ubuntu
---

### Post by Kurt_Alan on 2014-07-27
****

I'm posting this to the beginners' section because beginners might find it useful.

Compared to Windows OS, we Linux users don't have much to do in the way of maintenance. But I was thinking that it might be nice to come up with a list of terminal commands that one could use for maintaining any Debian based Linux distro. For example: ```
 sudo apt-get upgrade 
``` for existing software and ```
 sudo apt-get check 
``` for broken dependencies and ```
 sudo apt-get -f install 
``` for broken dependencies and ```
 sudo-apt-get autoclean 
``` for Debian packages.

More?

---

### Post by ian-weisser on 2014-07-28
Most regular maintenance, including log rotation, filesystem database updates, package database updates and security upgrades, and many more normal maintenance tasks, are already handled automatically. Look in /etc/cron* for many of them.

There really isn't _any_ normal maintenance that most unskilled users need to perform manually. Developers have spent years working on that.

I disagree with using 'sudo apt-get -f install' and 'sudo apt-get autoclean' without specific reason, or without an understanding of what they really do. While they (usually) don't hurt, they often don't help. Apt-get and repo management tools have improved over the years, and the kinds of problems solved by those commands have become more rare.

That's the nature of problems in Ubuntu - they change over time as the common problems get programmatic fixes.

---

