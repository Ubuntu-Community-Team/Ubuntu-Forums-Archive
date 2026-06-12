---
title: "Eclipse and FTP"
date: 2011-02-11
forum: Programming Talk
---

### Post by The_Aegidius on 2011-02-11
Is it possible to add FTP support to Eclipse for editing remote files directly?

---

### Post by Zugzwang on 2011-02-11
I don't know, but you might want to consider the alternative of mounting your remote directory to your local file system using FUSE/ftpfs. Then it appears to be a local file to Eclipse and any other program (but is actually transferred to the FTP server whenever you save it).

---

### Post by 3177 on 2011-02-11
dont use ftp or ftps, use ssh

---

### Post by The_Aegidius on 2011-02-11
I'm just connected to the FTP server, doing *Connect to server* from the *Places* menu, but I can't see that folder with Eclipse.

If I would use SSH protocol can I connect directly to the server from Eclipse?

---

### Post by 3177 on 2011-02-11
yes you can connect to ssh from anywhere.
Please dont use ftp its not secure.

---

### Post by The_Aegidius on 2011-02-11
Ok, thanks for the advice.

I can't try now, but I let you know if it works.

---

### Post by aynshtein on 2011-02-11
> **The_Aegidius said:**
> Is it possible to add FTP support to Eclipse for editing remote files directly?

Simly install Aptana. Aptana has FTP feature...

---

