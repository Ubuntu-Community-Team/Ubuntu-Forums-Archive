---
title: "Help with drive permissions"
date: 2007-09-30
forum: Other OS Talk
---

### Post by HappyFeet on 2007-09-30
I installed Debian and i got the drives mounted in fstab. everything seems good except that my 2 ntfs drives say i dont have the permissions to blah, blah, blah. i've tried everything i could find online, and i'm still stumped. do i need ntfs drivers or something? i've been trying for over 3 hours to get this working. any help would be much appreciated. i included a screenshot of my fstab.

---

### Post by epimer on 2007-09-30
Do you have read access to them? If not, install ntfs-3g.

If you want to change the ownership, then it's e.g

```
sudo chown -R username:username /media/backup
```

---

### Post by Arwen on 2007-09-30
Try changing "user" to "users" and "rw" to "ro" and "0 2" to "0 0".
ntfs-3g lets you write in ntfs
-->[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) really useful thread for fstabbing

---

