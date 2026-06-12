---
title: "How do I switch the boot loader"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by netipot on 2012-07-05
I read on the forums about a month ago how to switch the boot loader from OS to the other in a dual boot. It was a simple command in terminal. I can find it now. I have ubuntu 12.04 & I recently installed lubuntu 12.04. The boot loader is now lubuntu. I know how to change the boot order & have done so but if I want to get rid of lubuntu, don't I have to change the boot loader back to ubuntu in order for my computer to boot up again.

---

### Post by NikTh on 2012-07-05
**Boot from Ubuntu** and give 
```
sudo grub-install /dev/sda 
```

---

### Post by firekage on 2012-07-05
> **NikTh said:**
> **Boot from Ubuntu** and give 
```
sudo grub-install /dev/sda 
```


How would it look if i wanted to install it using UUID?

---

### Post by wilee-nilee on 2012-07-06
> **firekage said:**
> How would it look if i wanted to install it using UUID?

Your question makes no sense, the mbr sda has no uuid, and a uuid is not needed to load it, the uuid is basically for fstab.

---

