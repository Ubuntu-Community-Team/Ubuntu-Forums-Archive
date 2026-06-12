---
title: "External USB / disks automounting read-only"
date: 2014-02-28
forum: New to Ubuntu
---

### Post by morningsunshine on 2014-02-28
Hi all,

I have set up ubuntu 12.04 fresh install. When I plug in my external usb drives - 1 fat and 1 ntfs formatted - both are auto mounted (nautilus) as read only. However, I can write to them as 'root' via terminal. When plugged in, both do not show up in /etc/fstab.

Pointers needed please.

Thanks.

---

### Post by sudodus on 2014-02-28
They should not show up in ** /etc/fstab**. That is for what is permanently installed unless you do some advanced things. But they should show up in the file **/etc/mtab **and if you run the command ***df***

When the USB drives are connected (and mounted), ***please post the output of the following commands*** between code tags, and I or someone else have a better chance to help you.

```
ls -l /media
```
```
sudo parted -l
```
```
cat /etc/mtab
```
and
```
df
```

---

