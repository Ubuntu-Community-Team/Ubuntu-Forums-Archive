---
title: "Daemon tool in Linux"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by vlad1975 on 2008-05-26
Is there a software like Daemon tool for Ubuntu?

---

### Post by quelx on 2008-05-26
You use a loop device, from the terminal

```
sudo mkdir /mnt/iso
sudo mount -o loop /home/username/Desktop/iamanisoimage.iso /mnt/iso
```

Fileroller will also open .iso files for you to peruse the contents

---

