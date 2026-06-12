---
title: "[SOLVED] how to increase time period at the grub screen ?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by anubhav2k on 2008-11-08
I want to increase the time period as its only 2 seconds .... so if i have to switch to windows , i miss it some times , or some way to boot win vista 1st ??
please help

---

### Post by moffa on 2008-11-08
```

gksu gedit /boot/grub/menu.lst

```

Find the lines:

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

change the timeout value to suit your needs

---

### Post by anubhav2k on 2008-11-08
thnks

---

