---
title: "Trouble creating a symbolic link"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by dschlic12 on 2014-04-28
I am running Ubuntu 14 Desktop (latest version) in a VMWare virtual machine. In configuring the virtual machine, I created a shared folder with the host OS which is Windows 7 Pro. This share shows up in the folder /mnt/hgfs. I would like to place a link to that shared folder on my desktop. However when I right click on the shared folder and click on the Make Link item I get an error message "The target doesn't support symbolic links." The shared folder is NTFS. Can someone help me with this issue?

---

### Post by ajgreeny on 2014-04-28
You may have to make do with a launcher for nautilus pointing to the share folder rather than making a symbolic link.

I think only Linux filesystems (and maybe mac?) will allow symbolic links.  It is the same in reverse where windows shortcuts mean nothing to Linux.

---

