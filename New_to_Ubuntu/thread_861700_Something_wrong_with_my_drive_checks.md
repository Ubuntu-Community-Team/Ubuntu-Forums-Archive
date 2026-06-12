---
title: "Something wrong with my drive checks"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-07-16
when i boot up ubuntu it checks my drives and it always says the automatic drive check has failed or something...should i re-install ubuntu

---

### Post by lisati on 2008-07-16
Are you able to restart your computer after the file checks have finished their stuff, or are you getting repeated problems?

---

### Post by mr-Kirch on 2008-07-16
i can restart..it all works fine if i skip the check but there is something wrong w/ the files since it keeps failing

---

### Post by iaculallad on 2008-07-16
> **mr-Kirch said:**
> when i boot up ubuntu it checks my drives and it always says the automatic drive check has failed or something...should i re-install ubuntu

Does the error message tells you what drive partition failed on drive checking? If so, you can try to boot from you're LiveCD and do a manual check on that partition.

i.e. If it points the error on hda3 then:

```
fsck /dev/hda3
```

---

### Post by mcduck on 2008-07-17
Could you run the following commands in temrinal and post the outputs here so we can take a look at your disk configuration:

"sudo fdisk -l"

"blkid"

"cat /etc/fstab"

..and no, you shouldn't reinstall Ubuntu. Most of the problems in Linux can be fixed without reinstallin, it's not Windows, you know.. ;)

(you can copy & paste to/froma  terminal by selecting the text you want to copy and the pressing the middle mouse button (the wheel) where you wish to paste. Or with Shift-Ctrl-C and Shift-Ctrl-V, if you like)

---

