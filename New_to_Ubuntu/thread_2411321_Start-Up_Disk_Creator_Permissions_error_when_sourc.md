---
title: "Start-Up Disk Creator: Permissions error when source ISO is on NAS"
date: 2019-01-28
forum: New to Ubuntu
---

### Post by barddzen on 2019-01-28
Hello,

When using start-up disk creator, I can use "Files" to connect to my Synology NAS and drag a location over to the Start-up disk creator (or just navigate to the NAS location) of the ISO, specify the destination and when I try to make the USB boot image, I get a "permission denied" error.  After some investigation the process apparently doesn't like the ISO being sourced from the NAS.  The user name I'm logged in under has full R+W permissions to that particular folder.

If I copy the same ISO local, the process works perfectly.

If I (through terminal) or Files, navigate to that same folder, I can do whatever I want under the same user name, it's just Start-Up Disk Creator seems to have an issue.

Any ideas of where/what I might look to figure this out?

---

