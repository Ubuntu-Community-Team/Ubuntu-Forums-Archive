---
title: "help with dealing with floppy disk images"
date: 2008-06-27
forum: Programming Talk
---

### Post by maybeway36 on 2008-06-27
Is there a way to use dd to automatically add enough zeroes to the end of a file to make it 1474560 bytes?

---

### Post by geirha on 2008-06-27
Not to my knowledge. You can do something like this though.
```

dd if=/dev/zero bs=1 count=$((1440*1024 - `stat -c %s image_file`)) >>image_file

```

---

