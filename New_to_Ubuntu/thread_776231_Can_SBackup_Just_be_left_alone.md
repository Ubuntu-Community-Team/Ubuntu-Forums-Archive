---
title: "Can SBackup Just be left alone?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by fraser_m on 2008-04-30
I have configured SBackup to Backup hourly, and set all the settings, blah blah blah.

But I was wondering if I can just leave it now, or do I need to set it as a startup program in Sessions?

---

### Post by mikeyphi on 2008-04-30
If you've worked through the Simple Backup config - then it's all done. Just let it run!

---

### Post by eivind on 2008-05-13
You can leave it running, but make sure that the backup file is valid after sbackup has finished - open the tarball with file-roller and see if it's readable:

[https://answers.launchpad.net/ubuntu/+source/sbackup/+question/30719](https://answers.launchpad.net/ubuntu/+source/sbackup/+question/30719)

If it's not, your backup may be invalid.

---

