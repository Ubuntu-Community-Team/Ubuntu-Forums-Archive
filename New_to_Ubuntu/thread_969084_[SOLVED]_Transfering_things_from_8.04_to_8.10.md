---
title: "[SOLVED] Transfering things from 8.04 to 8.10"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by sanderella on 2008-11-03
I have installed 8.10, and still have 8.04 installed, too. Please can someone tell me what is the easiest way to transfer my bookmarks, documents and folders from 8.04 into 8.10? Thank you.

---

### Post by Paqman on 2008-11-03
All you bookmarks and settings are stored in folders inside your /home directory. Go to your home and hit ctrl-H to see them.

Open Nautilus as root by hitting alt-F2 and typing:
```

gksu nautilus

```

Browse to the old home on 8.04 (through Places) and copy all the files in each user's folder into the new home on 8.10. Then right click on the username folder and set the permissions so that each user owns all files within their own home (remember to check "apply permissions to enclosed files"!)

Any other data files can just be copied over from one partition to the other.

**Close Nautilus once you are done**

---

