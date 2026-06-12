---
title: "Error Messages in Grsync"
date: 2016-02-19
forum: New to Ubuntu
---

### Post by stevemid on 2016-02-19
I've got Grsync up working to a local disk now. However, Here is one error message and 5  informational messages from grsync warnings that I don't understand.  These seem minor and I plan to just ignore them unless someone tells me otherwise.  

As always thanks for your help.
Steve

**** Medion Backup - Sat Feb 20 14:32:58 2016

** Launching RSYNC command:
rsync -r -t -p -v --progress --delete --ignore-existing -s --exclude-from=exclude.txt /home /media/medion/Seagate Backup Plus Drive

sending incremental file list
rsync: opendir "/home/lost+found" failed: Permission denied (13)
home/
IO error encountered -- skipping file deletion
skipping non-regular file "home/medion/.dropbox/command_socket"
skipping non-regular file "home/medion/.dropbox/iface_socket"
skipping non-regular file "home/medion/.kde/cache-Medion"
skipping non-regular file "home/medion/.kde/socket-Medion"
skipping non-regular file "home/medion/.kde/tmp-Medion"
home/medion/

---

