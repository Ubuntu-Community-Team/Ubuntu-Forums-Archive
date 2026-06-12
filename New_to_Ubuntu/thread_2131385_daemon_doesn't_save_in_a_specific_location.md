---
title: "daemon doesn't save in a specific location"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by creepwood on 2013-04-01
I have a daemon that's suppose to save a file in a specific place. I used to have a NAS that it did this to, it was mounted as specific user and all went fine. Now I mount another drive on the linuxmachine so that it can save the files there instead. I just switched in fstab the mount location, so that the place is the same. I thought there was a hiccup with the rights but I changed them to full rights 666 and 777 on files and directories respecitively. It still seems to be some problems with the daemon not being able to save the files there. Is there some way to "act" as the user the daemon is run as to see if I can make a file as that user?

---

### Post by schragge on 2013-04-03
sudo -u *user* *command*?

---

