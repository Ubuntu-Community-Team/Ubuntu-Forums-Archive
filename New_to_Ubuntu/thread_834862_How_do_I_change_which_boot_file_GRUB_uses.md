---
title: "How do I change which boot file GRUB uses?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by I_R_LEENUCKS_MAN on 2008-06-19
I have Linux Mint and Ubuntu 7.10 installed. I need to get rid of Linux Mint, but it currently controls my GRUB. How do I change which  boot.lst GRUB uses, and once I change that to Ubuntu, can I just wipe Linux Mint's partition, or are there references that'll be messed up if I do that?

---

### Post by kpkeerthi on 2008-06-19
In /boot/grub/menu.lst, look for a line that says **default 0**. Change 0 to point to the entry that you want booted by default. 0 correponds to the first GRUB entry, 1 corresponds to Second and so on and so forth. For eg., if you have Ubuntu listed as fourth entry in GRUB, change it to **default 3**

Yes you can just delete your Mint partition and remove the correponding entries from GRUB's menu.lst. Then run the following command:
```
 sudo update-grub
```

---

### Post by I_R_LEENUCKS_MAN on 2008-06-19
No, it's using a boot.lst that's in linux mint. If I delete that, will it default to the one in ubuntu?

---

### Post by louieb on 2008-06-20
I guess you want Ubuntu to boot. Reboot - at the Grub menu press **c **to get the grub prompt. 

```
find /boot/grub/menu.lst
```returns something like (hd0,0) you should get 2 one for mint one for Ubuntu.

Now use the one that points to the Ubuntu parttion.

```
root (hd#,#)
setup (hd0)
quit

```Now when you reboot it should boot to grub on Ubuntu and you can do whatever you want with the space now used by mint.

---

