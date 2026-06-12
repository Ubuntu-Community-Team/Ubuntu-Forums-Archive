---
title: "symbolic link failure"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by nnjond on 2008-10-02
Hi,

I have a 2nd, physical Drive, sdb1, with all my data on it, but have only established one shrtcut to Desktop. When I try to add more, I get:

Error while creating link to... -and a "Operation not permitted" popup as further explaination. What should I do?

Thanks

---

### Post by unutbu on 2008-10-02
Try:
```

ln -s TARGET_DIR_OR_FILE   SYMLINK_NAME
```

for example, if /dev/sdb1 is mounted at /mnt, and you want to create a symlink 
from /home/user/music to /mnt/music, type
```

ln -s /mnt/music /home/user/music

```
If it doesn't work, please post the terminal output.

---

### Post by markbuntu on 2008-10-02
You most likely have a permissions issue. That is the most common cause of 

Operation not permittted

---

