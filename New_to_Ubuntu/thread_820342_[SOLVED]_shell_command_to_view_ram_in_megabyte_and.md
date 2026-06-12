---
title: "[SOLVED] shell command to view ram in megabyte and CPU speed"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by chrisdee on 2008-06-06
Hello.

Iv googled for Ubuntu shell commands that lets me view
the speed and type of CPU installed and shows how much ram is installed viewed in megabyte.

Any tips ?

---

### Post by kpkeerthi on 2008-06-06
```
free -m
```
```
cat /proc/cpuinfo
```

---

### Post by sisco311 on 2008-06-06
```
hwinfo --cpu
```
and
```
hwinfo --memory
```

---

### Post by talktoari on 2008-06-06
'cat /proc/cpuinfo' 

This will give you processor speed and other CPU-related stuff.

'top' 

This will give you info about memory and cpu use of running programs. press 'q' to quit top.

Hope this helps.

---

### Post by chrisdee on 2008-06-06
Thank you all.

While waiting for answer I found the dmidecode command.
It lists out info about both bios and hardware.

---

