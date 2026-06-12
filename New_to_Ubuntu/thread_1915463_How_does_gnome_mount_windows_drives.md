---
title: "How does gnome mount windows drives?"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by gr@ss_h@pper on 2012-01-26
I am with Ubuntu 10.04 for quite some time now. I have a dual boot system with default-dell-win-vista that i rarely use. I access windows drives by mounting them in Ubuntu. 

What I do: Go to "Places" ==> click on win-drive ==> It gets mounted in  /media/some-name and comes to desktop also.

Now I want to understand how that works. I have no rules related to it in udev. 
I think it might be some gnome specific thing that takes care of mounting of the drive when we click on it. My queries are:
1. As the win-drive is not mounted yet, how is it shown in "Places" on the desktop bar (Panels) at the top?

2. When we click on the win-drive, what gets triggered that does the mounting of the drive? It creates a temporary dir in /media and mounts on it. Gives a link at the desktop also. Later on unmouting, it also removes the /media/some-folder. Does it read some rules from some conf file to do this?

3. If I want to permanently and automatically mount the win-drives in ubuntu, I think I need to put entires in /etc/fstab. Then it wouldn't be gnome specific. Am I corrrect?

Thanks in advance for you help :)

---

### Post by gr@ss_h@pper on 2012-01-26
Hi ecstasyforum,

Thanks for your reply. I actually don't have any problem with mounting. I just want to understand how it works. I saw in /var/log/syslog that a driver ntfs-3g takes care of it. I want to go a little deeper and understand who listens to the click and asks the ntfs driver to do the mounting etc and does it have some rules and configurations to do it? Can we modify it.. etc? 

from the logs:
ntfs-3g[2395]: Version 2010.3.6 external FUSE 28
ntfs-3g[2395]: Mounted /dev/sda2 (Read-Write, label "ddrive", NTFS 3.1)
ntfs-3g[2395]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
ntfs-3g[2395]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sda2,blkdev,blksize=4096,default_permissions
ntfs-3g[2395]: Global ownership and permissions enforced, configuration type 1
ntfs-3g[2395]: Unmounting /dev/sda2 (ddrive)

---

### Post by Mark Phelps on 2012-01-26
> **gr@ss_h@pper said:**
> 3. If I want to permanently and automatically mount the win-drives in ubuntu ...
As long as you're running Windows XP, automounting should not be a problem.

But ... if you're running Vista or Win7, those OSs are very finicky about changes being made to their filesystems from "outside" -- which is what you're doing if you mount them read/write in Linux.

Since you're intent on automounting the Windows filesystem, if it is Vista or Win7, strongly suggest you mount it Read-only.  That will greatly minimize your chances of filesystem corruption.

---

