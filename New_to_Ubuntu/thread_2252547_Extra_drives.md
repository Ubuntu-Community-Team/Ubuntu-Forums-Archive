---
title: "Extra drives"
date: 2014-11-12
forum: New to Ubuntu
---

### Post by kevinch417 on 2014-11-12
I have Windows 8.1 and Ubuntu on my PC's Solid State Drive. I also have a Hard Disk Drive ( K: ) where I keep most of my files since it has much more storage than my SSD. I can access it just fine from Windows.

The left taskbar in Ubuntu lists the K: drive, but I am unable to open it up/access it when I click on it.

Is there a way to access K: drive files from both operating systems rather than being limited to Windows?

---

### Post by yancek on 2014-11-12
Partitions on external drives are usually available under the /media directory.  You should see /media/user, look for it there.  Replace user with your actual user name.

---

### Post by ajgreeny on 2014-11-12
Disable fast-startup in Win 8.1 or the ntfs partition will remain in a mounted state when you close Windows which, by default, goes into a hibernation state, not a full shutdown.  That means that Ubuntu can not mount that partition and you will not be able to see any files or folders on it.

If Win 8.1 is shutdown properly there should be no problem and the partition should mount when you click on the icon in Places.

---

