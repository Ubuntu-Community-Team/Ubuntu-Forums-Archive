---
title: "Can't find drive names in 12.04 LTS..."
date: 2014-02-25
forum: New to Ubuntu
---

### Post by Priest Apostate on 2014-02-25
Currently working with the above listed OS to get my LPIC. I am trying to work with the fdisk command, but for that, I need the drive names. The drives don't show up as /dev/sd* -- unfortunately, I don't know how else the drives would be listed...does anyone have any information on how the drives would be listed in Ubuntu?

---

### Post by tomearp on 2014-02-25
```
sudo fdisk -l
```
will list all of the drives and information about their partition(s). See the [man page]("http://manpages.ubuntu.com/manpages/precise/en/man8/fdisk.8.html") for further info on fdisk.

---

### Post by Priest Apostate on 2014-02-25
Thanks!

---

