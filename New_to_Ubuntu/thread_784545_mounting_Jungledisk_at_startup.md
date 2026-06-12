---
title: "mounting Jungledisk at startup"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by OXB on 2008-05-06
Hi all, I am having a problem getting the Junglediskmonitor utility to mount my disk at startup. I can mount the disk manually by double-clicking the utility & using the "connect to server" menu option, so the connection to Amazon S3 & all the settings work. I followed the install instructions that come with the Jungledisk utility, including installing FUSE (which was already installed on my machine), but no luck. I am running Ubuntu 8.04 and I am a beginner: If there is anyone out there who has set this up and is willing to take a few minutes to write the blow-by-blow description of how to do it, I would appreciate it immensely.

Thanks

---

### Post by toddward on 2008-05-07
OXB, have you added the mount point to your /etc/fstab file.  When the system starts up, it'll reference this file and mount the correct directories.

---

### Post by OXB on 2008-05-07
> **toddward said:**
> OXB, have you added the mount point to your /etc/fstab file.  When the system starts up, it'll reference this file and mount the correct directories.

Thanks for your reply toddward, this is the step I am missing as the disk now mounts automatically when I double-click the "Junglediskmonitor" application located in the /usr/bin folder. Embarrassed to say that I don't know how to add the mount point - any pointer to instructions greatly appreciated.

---

