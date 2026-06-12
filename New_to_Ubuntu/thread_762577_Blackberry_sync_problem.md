---
title: "Blackberry sync problem"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by satterle on 2008-04-22
Trying to set up sync between Blackberry Curve and Evolution.

Installed Barry and upgraded opensync per:
[http://celeduc.blogspot.com/2007/10/blackberry-support-in-ubuntu-gutsy.html](http://celeduc.blogspot.com/2007/10/blackberry-support-in-ubuntu-gutsy.html)

Curve connects fine, charges, and barrybackup seems to work.

Set up msynctool per:
[http://www.linux.com/feature/123251](http://www.linux.com/feature/123251)

Tried to configure the barry-sync plugin:
msynctool --configure Blackberry 1

get an error message: unable to open file usr/share/opensync/defaults/barry-sync

Tried going into msynctool-gui and sync, but no go.

Any thoughts?

---

### Post by aeiah on 2008-04-22
does the file usr/share/opensync/defaults/barry-sync exist? does running the command with sudo help? (not that doing so would be a permanent fix but it could rule out a permission error)

---

### Post by satterle on 2008-04-22
File does not exist.

Setting up with sudo makes no difference.

Create an empty file "barry-sync". It is called when using --configure, but since there is no information, it's useless.

Both multisync-gui and msynctool --showgroup indicates that barry-sync still needs to be configured.

---

### Post by chipbennett on 2008-06-01
> **satterle said:**
> Trying to set up sync between Blackberry Curve and Evolution.

Installed Barry and upgraded opensync per:
[http://celeduc.blogspot.com/2007/10/blackberry-support-in-ubuntu-gutsy.html](http://celeduc.blogspot.com/2007/10/blackberry-support-in-ubuntu-gutsy.html)

Curve connects fine, charges, and barrybackup seems to work.

Set up msynctool per:
[http://www.linux.com/feature/123251](http://www.linux.com/feature/123251)

Tried to configure the barry-sync plugin:
msynctool --configure Blackberry 1

get an error message: unable to open file usr/share/opensync/defaults/barry-sync

Tried going into msynctool-gui and sync, but no go.

Any thoughts?

I have my BB Curve synchronizing with KDE-PIM. [Here are step-by-step instructions]("http://www.chipbennett.net/wordpress/index.php/2008/05/synchronizing-a-blackberry-in-linux/").

I noticed that the synch groups and synch group member configuration files are found not in usr/share/opensync but rather in ~/.opensync-0.22

I'm not sure why msynctools would be looking in the wrong directory, though.

---

### Post by itmanvn on 2008-08-11
1. Download the lastest barry-0.13: [http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564&release_id=616724](http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564&release_id=616724)

2. Syncing your BlackBerry with Evolution
[http://www.netdirect.ca/software/packages/barry/sync.php](http://www.netdirect.ca/software/packages/barry/sync.php)

---

