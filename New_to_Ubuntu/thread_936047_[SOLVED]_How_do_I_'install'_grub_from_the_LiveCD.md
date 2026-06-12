---
title: "[SOLVED] How do I 'install' grub from the LiveCD"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by argie on 2008-10-02
During the installation I chose not to install a bootloader because I wanted to install it to an extended partition like in [this post]("http://ubuntuforums.org/showpost.php?p=3113451&postcount=8"). How do I install a bootloader?

I'm not 'restoring' grub, there are no grub files on the hard-drive *at all*.

Is it possible for me to go through the installer and just install grub and not have to copy files and stuff like that?

---

### Post by louieb on 2008-10-02
Here are the steps.
[https://help.ubuntu.com/community/GrubHowto#GUI](https://help.ubuntu.com/community/GrubHowto#GUI)

---

### Post by argie on 2008-10-12
When you're installing to an extended partition, sometimes the steps in that wiki don't work. In which case you have to specify your root directory with:
```

sudo grub-install --root-directory=/media/disk/
```

The above is just an example. If you've already installed grub to some partition and you want to do this to install to an extended partition, you have to mount the disk and then use root-directory. Point it to the folder which contains boot var etc folders.

---

### Post by argie on 2008-10-12
When you're installing to an extended partition, sometimes the steps in that wiki don't work. In which case you have to specify your root directory with:
```

sudo grub-install --root-directory=/media/disk/
```

The above is just an example. If you've already installed grub to some partition and you want to do this to install to an extended partition, you have to mount the disk and then use root-directory. Point it to the folder which contains boot var etc folders.

---

