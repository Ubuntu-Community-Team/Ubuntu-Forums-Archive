---
title: "Is it possible for Windows Explorer to report free space on Samba file share?"
date: 2015-02-28
forum: New to Ubuntu
---

### Post by PDXPat on 2015-02-28
Hello.  Newbee question.  I was wondering if it was in the realm of possibility for a Windows Explorer to report free/used space on a Ubunutu Server Samba file share.

Similar to how windows is able to report percentage used/free on a windows system.

Thanks.

PDXPat

---

### Post by TheFu on 2015-02-28
**df -h**```

Filesystem                         Size  Used Avail Use% Mounted on
/dev/sda5                           20G  6.5G   12G  36% /
/dev/mapper/vg--hadar-lv--hadar    388G  324G   44G  89% /var
/dev/mapper/vg--hadar-lv--backups  387G  236G  132G  65% /Backups
istar:/D                           3.5T  3.2T  170G  95% /D
//172.22.22.14/K                    74G   42G   32G  57% /Data/K
//172.22.22.14/D                   245G  174G   71G  72% /Data/D
```

Seems pretty clear to me how much is the total, what is used, and what is available to be used. 
* .14 is a Windows machine with a few CIFS shares mounted.
* istar is NFS storage.
* everything else is local.

Hopefully this helps.

---

### Post by PDXPat on 2015-02-28
Hey TheFu.  Thanks for the quick answer.  I may have asked my question poorly.

Is there anyway to get the data from a WINDOWS machine.  Specifically through Windows explorer.  Thanks.

PDXPat

---

### Post by tripp98 on 2015-02-28
Have you mapped a drive letter to it?

---

### Post by TheFu on 2015-03-01
> **PDXPat said:**
> Hey TheFu.  Thanks for the quick answer.  I may have asked my question poorly.

Is there anyway to get the data from a WINDOWS machine.  Specifically through Windows explorer.  Thanks.

PDXPat

right click - properties?
Or use cygwin.

Really not a Linux question.

---

### Post by PDXPat on 2015-03-01
Thank you tripp98!  That did the trick and got the information I was looking for.

---

### Post by TheFu on 2015-03-01
> **PDXPat said:**
> Thank you tripp98!  That did the trick and got the information I was looking for.

You don't need to map a drive letter. Properties has the data.

---

