---
title: "10_linux and 30_os-prober files missing"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by BJones007 on 2012-04-16
Somehow I've managed to delete both files from the folder **/etc/grub.d** and now I'm unable to get em back. So now whenever my computer boots up I have to go through a long string of code to get away from the **Grub> prompt ** screen cos they're not present in the command line of the **grub.cfg**  Is there anyway I could prolly get these files back?

---

### Post by kimda on 2012-04-16
reinstall grub-common package 

```
sudo apt-get install --reinstall grub-common
```

---

