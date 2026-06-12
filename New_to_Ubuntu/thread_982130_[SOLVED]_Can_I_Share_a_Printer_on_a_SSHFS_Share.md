---
title: "[SOLVED] Can I Share a Printer on a SSHFS Share?"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by getitright on 2008-11-14
I am using SSHFS to share files is it possible to access the server printer to print files from the client?

---

### Post by jbrown96 on 2008-11-14
No. SSHFS is a filesystem. It's not the same as Samba. The closest thing that you could do would be to send post-script files over SSHFS and have a cron job that constantly checks a specific folder and immediately prints any files in there and then deletes them.

---

