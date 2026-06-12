---
title: "How to compile imageshack-uploader with Ubuntu?"
date: 2014-03-27
forum: Packaging and Compiling Programs
---

### Post by ron998 on 2014-03-27
Hi
Does anybody know how to compile **imageshack-uploader**?

There's some information at Slackbuilds.
Here ---> [http://slackbuilds.org/repository/14.1/network/imageshack-uploader/](http://slackbuilds.org/repository/14.1/network/imageshack-uploader/)
Is it possible to modify these instructions to compile it with Ubuntu?

---

### Post by kostkon on 2014-03-27
[It's already in the repos]("https://apps.ubuntu.com/cat/applications/imageshack-uploader/"). Why do you need to compile it?

---

### Post by ron998 on 2014-03-27
> **kostkon said:**
> [It's already in the repos]("https://apps.ubuntu.com/cat/applications/imageshack-uploader/"). Why do you need to compile it?

Available versions
Ubuntu 13.10
Ubuntu 13.04
Ubuntu 12.10
Ubuntu 12.04
Ubuntu 11.10
Ubuntu 11.04

Not available for Ubuntu-14.04. :mad:

---

### Post by sammiev on 2014-03-27
> **ron998 said:**
> Available versions
Ubuntu 13.10
Ubuntu 13.04
Ubuntu 12.10
Ubuntu 12.04
Ubuntu 11.10
Ubuntu 11.04

Not available for Ubuntu-14.04. :mad:

Have you tried to install it into 14.04 yet?
This would be best posted in Ubuntu + 1 section. I'm sure a mod/admin will move it shortly.

---

### Post by kostkon on 2014-03-27
Hmm, [yeah]("https://launchpad.net/ubuntu/trusty/i386/imageshack-uploader")...

You could grab the [deb for saucy]("http://packages.ubuntu.com/saucy/imageshack-uploader"), it may work.

---

### Post by andrew.46 on 2014-03-28
> **ron998 said:**
> There's some information at Slackbuilds.
Here ---> [http://slackbuilds.org/repository/14.1/network/imageshack-uploader/](http://slackbuilds.org/repository/14.1/network/imageshack-uploader/)
Is it possible to modify these instructions to compile it with Ubuntu?

Note that this Slackbuild does not *compile* as such, it simply opens up a Debian archive, fixes up a libavutil symlink and then packages suitable for Slackware...

---

