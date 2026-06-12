---
title: "Menu.lst small issue"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Kdawkins on 2008-04-26
Hey all,

I updated from 7.10 to 8.04 yesterday. I went into menu.lst to change the title to Ubuntu 8.04 and noticed I was not booting the newest kernel. How can I change that?

Here is the current ubuntu entry for my menu.lst

```


title		Ubuntu 8.04, kernel 2.6.22-16-generic
#  root		(hd2,0)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-16-generic root=UUID=5413b280-4f48-4bb1-8bee-26a2e463710c ro quiet splash
initrd		/boot/initrd.img-2.6.22-16-generic
quiet

```

---

### Post by sisco311 on 2008-04-26
[read this first: http://ubuntuforums.org/showthread.php?t=769042]("http://ubuntuforums.org/showthread.php?t=769042")

It's the new kernel installed?
```
ls /boot/vmlinuz*
```If not install it:
```
sudo apt-get -y install linux linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
```

---

