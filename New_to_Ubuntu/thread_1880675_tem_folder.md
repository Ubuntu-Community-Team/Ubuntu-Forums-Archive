---
title: "tem folder"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by pmohankumar on 2011-11-14
Hi  friends,

Deleting all files and folders inside the "tem" folder may cause any damage to OS or start up applications or anything-else?

---

### Post by mr.suchy on 2011-11-14
Hi,

Where is located this folder ? It seems to me that is not a system folder. Am I right ? If it's true U can delete it.

Best regards.

---

### Post by aeiah on 2011-11-14
do you mean /tmp/ ?

---

### Post by 3rdalbum on 2011-11-14
> **pmohankumar said:**
> Hi  friends,

Deleting all files and folders inside the "tem" folder may cause any damage to OS or start up applications or anything-else?

Assuming you mean /tmp, it's not a good idea to remove its contents while the system is running. Some parts of the system place temporary files inside /tmp, and rely on those files being there. Removing files from /tmp can result in a crash.

/tmp is automatically wiped on shutdown anyhow, when it's safe to do so. There's really no benefit to erasing it manually.

---

### Post by pmohankumar on 2011-11-14
hi ,
Ya Its /tmp folder.

---

### Post by Paqman on 2011-11-14
> **3rdalbum said:**
> 
/tmp is automatically wiped on shutdown anyhow, when it's safe to do so.

I think technically it's done during boot, but the effect is the same.

---

