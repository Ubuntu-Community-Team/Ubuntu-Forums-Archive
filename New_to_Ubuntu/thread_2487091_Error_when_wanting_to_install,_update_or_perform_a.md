---
title: "Error when wanting to install, update or perform any action in xubuntu"
date: 2023-05-22
forum: New to Ubuntu
---

### Post by zeiin772 on 2023-05-22
Des:1 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) jammy/universe amd64 libqt5serialport5 amd64 5.15.3-1 [34.6 kB]
Des:2 [http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu) jammy/universe amd64 cutecom amd64 0.30.3-1build1 [101 kB]
Downloaded 136 kB in 4s (35.7 kB/s)
(Reading the database... 284647 currently installed files or directories.)
Uninstalling linux-image-5.19.0-35-generic (5.19.0-35.36~22.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.19.0-35-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 10: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.19.0-35-generic (--remove):
thread installed package linux-image-5.19.0-35-generic post-removal script returned error exit code 1
dpkg: too many errors, stopping
Errors encountered while processing:
linux-image-5.19.0-35-generic
Process stopped due to too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

I need to install apps in my xubuntu, but i can' t do anything, please help

---

### Post by Bashing-om on 2023-05-22
Hello zeiin772 - Welcome to the forums :D

> 
but i can' t do anything, please help

Help is what we do.

Let's gather some info and then see what there is to do.

Post back the results of these terminal commands - between code tags ! -
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

```

df -h
lsb_release -a
uname -r
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux

```

we see what we can finger out about that linux-image-5.19.0-35-generic kernel.

[INDENT]We can do that[/INDENT]

---

### Post by MAFoElffen on 2023-05-23
```

...
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 10: /etc/default/grub: splash: not found
...

```
Please post the contents of your /etc/default/grub file within CODE Tags so we can look at it...

You have a typo in that /etc/defualt/grub file, which is causing an error on the update-grub (underlying utility grub-mkconfig) process of the update. Most likely on the GRUB_CMDLINE_DEFAULT= line... That is where it produce that error saying it couldn't find splash... Usually, like when there is not a matching quotation mark there in that line.

You could confirm that yourself, just by doing
```

sudo update-grub

```
...and watch that error out.

---

