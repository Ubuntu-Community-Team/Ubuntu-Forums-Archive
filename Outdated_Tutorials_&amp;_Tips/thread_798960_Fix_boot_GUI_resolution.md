---
title: "Fix boot GUI resolution"
date: 2008-05-18
forum: Outdated Tutorials &amp; Tips
---

### Post by soxs on 2008-05-18
Everytime I install Ubuntu, my usplash (the boot GUI) is 640x480. So here is howto make the usplash resolution fit your display resolution:

1. Open a terminal and type:
```
sudo nano /etc/usplash.conf
```
This will ask you for your userpasswd, so you can edit that file with root permissions.
You will get something like this:
```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.
xres=640
yres=480
```

OR

```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.
```

2. Adjust xres and yres to your targeted resolution, e.g. for 1280x1024:

```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.
xres=1280
yres=1024
```
Save via <STRG><O>

3. You now must update your initramfs so the changes take effect:
```
sudo update-initramfs -u
```

4. Finish. Enjoy your well-sized usplash-boot-screen

---

