---
title: "Booting Error in Ubuntu 13.04"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by surenther.ss on 2013-08-22
Hi All,

I am new to Ubuntu. I have installed Ubuntu 13.04 and removed Windows.

Ubuntu worked fine for me. 

But for the last couple of days, My system booting very slow

i am getting the following error during booting

```
[ 1.602819] 18042: No Controller Found
[ 15.228258] radeon 0000:01:00.0: radeon_uvd: Can't load firmware "radeon/CYPRESS_uvd.bin"
```

After this error. It's booting normally but it takes very long time

Please help me fix this problem.

Thanks
Surenther

---

### Post by grahammechanical on 2013-08-22
Have you tried changing video drivers? This is only a guess but you could have a corupted video driver and after trying several times to use it the boot process uses the open source driver (Nouveau). That might explain the time it takes Ubuntu to load and also why it finally does load.

At the Grub boot menu we can select Advanced Options for Ubuntu and if we choose Recovery Mode>Resume, Ubuntu will load without using the proprietary video driver. See, if it takes as long to load.

Regards.

---

### Post by sandyd on 2013-08-22
what kernel are you using, if its 3.10, you need to wait for kernel maintainers to update initrd, or do it yourself
[https://bugzilla.redhat.com/show_bug.cgi?id=972518](https://bugzilla.redhat.com/show_bug.cgi?id=972518)

try
```

sudo dracut --install /lib/firmware/radeon/CYPRESS_uvd.bin --force
``` to fix it manually

---

### Post by surenther.ss on 2013-08-24
Guys, I have fixed this issue by changing the drivers

Now, I am not get this error.

Thanks for your help

---

