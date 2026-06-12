---
title: "gettnig updates error again."
date: 2022-02-25
forum: New to Ubuntu
---

### Post by ronjjjg8885 on 2022-02-25
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290094&stc=1[/IMG]

this is how it is for the last couple of days

---

### Post by Impavidus on 2022-02-25
Try by terminal and show us the output. There may be some interesting error messages.```
sudo apt update
```

---

### Post by ronjjjg8885 on 2022-02-25
```
Err:10 http://il.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata
  404  Not Found [IP: 192.115.211.70 80]
Ign:23 http://il.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata
Err:23 http://il.archive.ubuntu.com/ubuntu focal-backports/universe amd64 c-n-f Metadata
  404  Not Found [IP: 192.115.211.70 80]
Get:26 http://security.ubuntu.com/ubuntu focal-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Fetched 223 kB in 1s (161 kB/s)                                              
Reading package lists... Done
E: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/focal-updates/main/cnf/Commands-amd64  404  Not Found [IP: 192.115.211.70 80]
E: Failed to fetch http://il.archive.ubuntu.com/ubuntu/dists/focal-backports/universe/cnf/Commands-amd64  404  Not Found [IP: 192.115.211.70 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

this is only a part

---

### Post by guiverc on 2022-02-25
You're using [https://launchpad.net/ubuntu/+mirror/mirror.isoc.org.il-archive](https://launchpad.net/ubuntu/+mirror/mirror.isoc.org.il-archive) from [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Have you tried switching to a different available mirror (I'd likely just remove the "**il.**" from the archive.ubuntu.com and use the main site as a trial.  Your messages show it works in the one line that doesn't use the IL mirror, but errors on each line that uses IL.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by ronjjjg8885 on 2022-02-25
it's now working fine after i've changed it to the main server
thanks

---

### Post by MAFoElffen on 2022-02-25
Start (first) with the basics:
```

ping 8.8.8.8
ping www.google.com
ping il.archive.ubuntu.com
ping 192.115.211.70

```

> **ronjjjg8885 said:**
> it's now working fine after i've changed it to the main server
thanks

EDIT: Nevermind, saw an update with your last posts. Good Luck.

---

