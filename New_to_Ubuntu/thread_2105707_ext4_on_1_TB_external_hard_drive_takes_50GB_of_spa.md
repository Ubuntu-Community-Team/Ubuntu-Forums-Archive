---
title: "ext4 on 1 TB external hard drive takes 50GB of space"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by Froylan on 2013-01-16
where are the rest of the space? is there any way to have them back? if so, how? anything else I need to know about ext4?

---

### Post by jerome1232 on 2013-01-16
Probably the space reserved for root, 5% by default. You can change it with tune2fs. You would need to change the blue part to the real /dev path for your device.

```
sudo tune2fs -m 0 /dev/[COLOR="Blue"]sdbx[/COLOR]
```

The inodes and journal will still consume some space, but this is true of all file-systems.

---

### Post by haqking on 2013-01-16
> **Froylan said:**
> where are the rest of the space? is there any way to have them back? if so, how? anything else I need to know about ext4?

it is filesystem overhead which is about 5% for Ext4

You can adjust it  if you want

But do some research before you blindly do that incase you dont want to, depending on types of data storage

Edit: ninja'd above

---

### Post by Froylan on 2013-01-16
thanks you two, i'll do some research about the overhead ;) anyways, thread solved, i just love how ubuntu is better than windows when it comes to problem solving!

---

