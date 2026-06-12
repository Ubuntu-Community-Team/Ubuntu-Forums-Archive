---
title: "How can I tell how much swap space I have?"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by WBL on 2008-05-12
I have a Dell preinstalled Ubuntu laptop.  How can I tell how much swap space I have?

-WBL

---

### Post by dublued on 2008-05-12
type in sudo fdisk -l into the terminal...  it'll display all drives and partitions

---

### Post by SunnyRabbiera on 2008-05-12
you should be able to view it with the system monitor by going up to system> administration> system monitor
and check out the "resources" tab

---

### Post by licensedorchid on 2008-05-12
From the command line:
```
top
```
fifth line down is swap usage.
Top is just useful in general, though.

---

### Post by WBL on 2008-05-12
> **SunnyRabbiera said:**
> you should be able to view it with the system monitor by going up to system> administration> system monitor
and check out the "resources" tab

Thanks.  I've got 4.6 GB of swap.  Is that enough for my 2 GB of memory?

-WBL

---

### Post by licensedorchid on 2008-05-12
Yup. It is common to run twice your ram for swap. That way, you can hibernate!

---

### Post by SunnyRabbiera on 2008-05-12
> **WBL said:**
> Thanks.  I've got 4.6 GB of swap.  Is that enough for my 2 GB of memory?

-WBL

more then enough, swap memory is more or less "emergency" memory so just in case you have RAM issues it will come in handy even with your decent sized memory.

---

