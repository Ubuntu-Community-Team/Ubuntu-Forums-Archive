---
title: "Can't send files from ntfs partition"
date: 2020-02-25
forum: New to Ubuntu
---

### Post by deividas93 on 2020-02-25
Hello,

In my pc are three partitions, one ext4 with Ubuntu 18.04 LTS in it, and two ntfs, in one there is a windows 10 installed, in other are my other files.
If i trying to send files from ntfs partition for example in gmail or facebook, i'm getting error, but if copy that file from ntfs partition to ext4 partition, then everything works fine and i can send files. Is there any way to solve this?

---

### Post by yancek on 2020-02-25
How are you trying to 'send' files in gmail/facebook from the ntfs partition and of course, what error?

---

### Post by TheFu on 2020-02-25
What program is being used.  If it is a snap package, the security constraints could be limiting access outside the userid's HOME.  Chromium does this.  It would fail regardless of the NTFS or not.

---

### Post by deividas93 on 2020-02-26
If i'm trying to attach file to email or facebook message from ntfs partition, i'm getting error: Could not read the contents of C(some numbers of partition name): error opening directory: /media/"user_name"/C(some number of partition name): permission denied. I'm using Opera browser if there is a difference

---

### Post by TheFu on 2020-02-26
is it a snap package?
**snap list ** is the command to check.

---

### Post by deividas93 on 2020-02-26
If you asking about Opera browser, then yes, i can see it in the snap list

---

### Post by Holger_Gehrke on 2020-02-26
snap packages are severely restricted in what they are allowed to do. Check 'snap connections --all' and see whether opera has a plug named 'removable-media'. If it does you can run 'snap connect opera:removable-media' which should give this snap access to '/media' (and '/mnt' if your Ubuntu is new enough). If that plug is not available you're out of luck. There is a .deb package of opera available from opera.com which does not have these restrictions, but I'm not certain that it will run on your system.

Holger

---

