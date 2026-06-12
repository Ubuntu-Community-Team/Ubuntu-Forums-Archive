---
title: "login as root from USB flash drive"
date: 2014-07-19
forum: New to Ubuntu
---

### Post by Randy_Long on 2014-07-19
How do you login as root if you're running UBUNTU on a USB flash drive?

ubuntu 14.04?

---

### Post by progman-dt on 2014-07-20
sudo chroot

---

### Post by coffeecat on 2014-07-20
What do you mean by "login as root"?

If you mean log into a graphical environment as root, then that is not supported on this forum.

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

If you mean to start a root shell, simply use "sudo -i" as described here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Impavidus on 2014-07-20
You mean from a live system? Just as in a normal install with sudo. If it aks for a password, just hit enter.

---

