---
title: "[SOLVED] Update Manager errors"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by expatCM on 2008-11-29
When I run either the Update Manager or sudo apt-get update I get the following errors which appear to be "Hash Sum mismatch"

What do I need to do in order to get rid of these errors?

<code>GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.bz2)  Hash Sum mismatch
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.bz2)  Hash Sum mismatch</code>

---

### Post by frankleeee on 2008-11-29
Here is a link to the source list for intrepid take a look at your own and see if it is different.
[http://blog.anandkapre.com/2008/ubuntu/tutorial/11/ubuntu-intrepid-ibex-repository-source-list/](http://blog.anandkapre.com/2008/ubuntu/tutorial/11/ubuntu-intrepid-ibex-repository-source-list/)
You might just need to change servers.

Here is a launchpad link of the same.
[https://answers.launchpad.net/ubuntu/+question/44045](https://answers.launchpad.net/ubuntu/+question/44045)

---

### Post by expatCM on 2008-11-29
I took a look at the link and the comment posted there and pulled together a new sources.list.  After importing one key it all worked which really cannot be bad ..  that is the name of game.  Thanks for your help :)

---

