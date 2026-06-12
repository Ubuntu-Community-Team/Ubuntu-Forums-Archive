---
title: "Xfs"
date: 2022-10-28
forum: New to Ubuntu
---

### Post by arminimra on 2022-10-28
Is Ubuntu 22.10 able to mount the xfs partition by default or does it still need to install the package?

---

### Post by &amp;KyT$0P# on 2022-10-28
> **arminimra said:**
> or does it still need to install the package?

what package?

---

### Post by arminimra on 2022-10-29
> **halogen2 said:**
> what package?

xfs

---

### Post by &amp;KyT$0P# on 2022-10-29
I can't find any package named "xfs", and the references to such package I'm seeing are all about X fonts?

Anyway I was able to mount an xfs partition in a minimal install of Ubuntu Unity 22.10 without installing any additional packages nor having any packages with "xfs" in the name installed.

---

### Post by deadflowr on 2022-10-29
As long as the xfs module can load, or is loaded, it should be able to mount an xfs filesystem.
The module is built into Ubuntu's kernel packages.
I think if you want to create or manipulate an xfs filesystem you might need to make sure you have the xfsprogs, and maybe the xfsdump, packages installed.

---

### Post by MAFoElffen on 2022-10-29
Like this
```

sudo mount -t xfs /dev/sdb1 /mnt/storage

```

---

