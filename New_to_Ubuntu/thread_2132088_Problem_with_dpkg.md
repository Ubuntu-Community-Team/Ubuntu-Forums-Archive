---
title: "Problem with dpkg"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by 91BBBenz on 2013-04-03
I get this Warning " WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/bob/gvfs
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF     NODE NAME"
dpkg    2662 root    3uW  REG  252,1        0 20840589 /var/lib/dpkg/lock

Anyone know what's going on? New to Ubuntu 12.10, but liking it soo far!!!!!!

---

### Post by 91BBBenz on 2013-04-03
I get this Warning " WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/bob/gvfs
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF     NODE NAME"
dpkg    2662 root    3uW  REG  252,1        0 20840589 /var/lib/dpkg/lock

Anyone know what's going on? New to Ubuntu 12.10, but liking it soo far!!!!!!

BTW: 64bit HP Compaq nx 7400 Intel® Core™2 CPU T5600 @ 1.83GHz × 2

---

### Post by matt_symes on 2013-04-03
Hi

@1BBBenz. I have spit your post into it's own thread for you.

Anyway, open a terminal and type

```
sudo kill 2662
```

Then

```
sudo apt-get update
```

Finally

```
sudo apt-get upgrade
```

After that has finished, reboot your PC and wait 5 minutes. After 5 minutes, post the output of

```
ps aux | grep dpkg
```

Kind regards

---

