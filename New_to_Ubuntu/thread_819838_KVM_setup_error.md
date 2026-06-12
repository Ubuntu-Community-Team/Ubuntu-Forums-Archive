---
title: "KVM setup error"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by hopelessone on 2008-06-05
Hi,

Im following:

[http://www.greenhughes.com/content/virtualisation-with-kvm-and-virtmanager-kubuntu-804](http://www.greenhughes.com/content/virtualisation-with-kvm-and-virtmanager-kubuntu-804)

i get the following error when i click FINISH...

What do i have to do?

Thanks

---

### Post by ibuclaw on 2008-06-05
Is qemu installed properly?
```
sudo apt-get install qemu
```
Or
```
sudo aptitude reinstall qemu
```

Regards
Iain

---

### Post by hopelessone on 2008-06-05
do this
sudo apt-get install ubuntu-vm-builder

---

