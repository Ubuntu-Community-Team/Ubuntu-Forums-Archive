---
title: "duplicate error messages opening synaptic"
date: 2005-03-17
forum: Repositories &amp; Backports
---

### Post by Datchew on 2005-03-17
using the ubuntuguide.org method of copy/pasting my way to enable extra repositories, i ended up now getting these little popup errors every time i open synaptic package manager. 

how can i get rid of them? 
(messages pasted below)
********************************************************************************

Duplicate sources.list entry [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) warty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_main_binary-i386_Packages)

Duplicate sources.list entry [ftp://archive.ubuntu.com](ftp://archive.ubuntu.com) warty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-i386_Packages)

Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_main_binary-i386_Packages)

Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-i386_Packages)

Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_main_binary-i386_Packages)

Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-i386_Packages)

---

### Post by WW on 2005-03-17
You probably have a line like this

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

and another like this

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe multiverse

in /etc/apt/sources.list. But this means "main" and "restricted" are listed twice.
If this is the case, you can delete (or comment out with a #) the first line.

---

### Post by Datchew on 2005-03-17
hmmm... yes, i found duplicates. 

i was trying to find duplicates inside the preferences -> repositories of synaptic manager but couldn't. 

i #'d out the duplicates. 
that seems to have done it. 
thanks much. 

nice to finally have an EASY fix.

---

