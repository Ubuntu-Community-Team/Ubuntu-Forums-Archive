---
title: "Can I access an NTFS file system from a program running in wine?"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by klemperal on 2008-09-19
What I'm asking is can I access an NTFS file system from a program running in wine? For example, if I'm using a DVD ripper in wine, could I select the output be a NTFS file system/partition? The reason I ask is because I noticed I couldn't select my windows partition from a wine program.

---

### Post by scorchgeek on 2008-09-19
I am pretty sure that wine is completely divided from the rest of the filesystem and this is not possible.

---

### Post by The Cog on 2008-09-19
Yes you can. By default the filesystem root is mapped to Z:\ but this can be changed nad other mappings created with the **winecfg** utility.

---

### Post by iansane on 2008-09-19
If you have ntfs-3g installed and can access it from linux you should be able to access it through wine. Like The Cog said, it's Z drive by default. You may need to use windows commands with the backward slashes and stuff depending on what your doing but if there is an option to browse to point the program to it browsing to the z drive should work.

---

### Post by klemperal on 2008-09-19
Thanks for the help guys.

---

### Post by Paqman on 2008-09-19
> **iansane said:**
> If you have ntfs-3g installed

Which is installed by default in all recent versions of Ubuntu, btw.

---

### Post by iansane on 2008-09-19
Yeah I forgot. Was thinking of when I used 6.10 and had to install it from add remove. Don't know why. I haven't used that since gutsy released

---

