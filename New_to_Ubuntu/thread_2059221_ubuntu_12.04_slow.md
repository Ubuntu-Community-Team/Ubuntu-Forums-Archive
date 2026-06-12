---
title: "ubuntu 12.04 slow"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by chitragurung on 2012-09-17
I installed ubuntu 12.04 lts in my dell mini 10 inspiron machine but it gets slower than before. It is common issue or something else.

---

### Post by snowpine on 2012-09-17
What were you using before that was faster?

Some of the Dell Mini 10's have a graphics driver issue, can you please post the output of:

```
lspci | grep VGA
```

---

### Post by chitragurung on 2012-09-18
chitra@chitra-Inspiron-1011:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
chitra@chitra-Inspiron-1011:~$

---

### Post by lincoln32 on 2012-09-18
saw the same thing on a dell mini 1010 and did not find a fix for the video driver so I sold it and got a better netbook dell 1018 seem to be fine msi n1033 are great

---

### Post by snowpine on 2012-09-18
> **chitragurung said:**
> chitra@chitra-Inspiron-1011:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
chitra@chitra-Inspiron-1011:~$

That's one of the good ones--supported no additional drivers.
But it is a slow computer with slow graphics, so you might not want to use Unity. You can try Xfce/Xubuntu or LXDE/Lubuntu instead, maybe get a performance boost.

---

### Post by NikTh on 2012-09-18
> **snowpine said:**
> That's one of the good ones--supported no additional drivers.
But it is a slow computer with slow graphics, so you might not want to use Unity. You can try Xfce/Xubuntu or LXDE/Lubuntu instead, maybe get a performance boost.

Hi ,

or try to use Unity-2d instead. 

From login screen , at the login box click on Ubuntu little icon and choose "ubuntu-2d". 

Can you post the output of ```
lspci -nnk | grep -iA2 vga
cat /proc/cmdline
``` 

Thanks

---

### Post by chitragurung on 2012-09-18
chitra@chitra-Inspiron-1011:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller [8086:27ae] (rev 03)
    Subsystem: Dell Device [1028:02f4]
    Kernel driver in use: i915
chitra@chitra-Inspiron-1011:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=1532277b-4589-49fc-ae8f-42b53ce59314 ro quiet splash console=tty1 vt.handoff=7
chitra@chitra-Inspiron-1011:~$

---

### Post by NikTh on 2012-09-18
Hi , 
my thoughts are about the low specs netbook. 

Try to use ubuntu-2d . I think you will notice the difference. 

Thanks

---

