---
title: "Error when updating - ppa.launchpad"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by sealevelubu on 2013-01-03
When updating, i get an error  (pasted from update output):

[I]W: Failed to fetch [http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/thomas.tsai/ubuntu-tuxboot/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.[/I]

Update then quits automatically. 
The ppa.launchpad.net sources are nowhere in my sources.list.

Any thoughts?

---

### Post by windscape on 2013-01-03
Hi,

Do you have any files in /etc/apt/sources.list.d/ ? apt adds any files in there as sources as well.

---

### Post by Paddy Landau on 2013-01-03
That is the PPA for Tuxboot. It must be somewhere in your PPA list!

It simply means that the PPA is temporarily down. Try again later.

---

### Post by arpanaut on 2013-01-03
There are no packages for quantal in that repository.
There is the possibility that the packages for precise may work, but I do not know and it may be risky, best investigate why there are no packages for quantal first. There may be incompatibilities.

---

### Post by Paddy Landau on 2013-01-03
@arpanaut: I stand corrected! I think you are right.

Get the [.deb download from SF]("http://tuxboot.org/download/files-on-sf.php"). If it doesn't work, just uninstall it.

---

### Post by sealevelubu on 2013-01-03
> **windscape said:**
> Hi,

Do you have any files in /etc/apt/sources.list.d/ ? apt adds any files in there as sources as well.

You got it right. Dunno why this problem didnt emerge earlier, I used tuxboot month ago. Anyway, #-ed the relevant lines, all's well again, thx!

---

