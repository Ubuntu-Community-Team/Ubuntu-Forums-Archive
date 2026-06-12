---
title: "Help input/out error"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by PureKaoz on 2008-11-13
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


fresh install just done today, first timee using ubuntu how do i fix this wont install anyting or make anything

---

### Post by kaptengu on 2008-11-13
Sounds like a hardware issue. Does anything work as it should on your computer? Can you boot Windows?

---

### Post by PureKaoz on 2008-11-13
There is no windows i formatted ovr windows it was also a fresh install of windows, and internet and everything is working great. what could the problem be?

---

### Post by porchrat on 2008-11-13
Looks like your filesystem got a little corrupted there.

Try this forum discussion it didn't help this guy, but perhaps it will save you from needing to reinstall.  Please note that they are dealing with a  different package to the one you're experiencing problems with so don't use the information posted there for copying and pasting into the .list package (seen on page 2).  However I doubt this will work, unfortunately it seems like a pretty fatal problem and you will probably need to reinstall.

[http://ubuntuforums.org/showthread.php?t=747537]("http://ubuntuforums.org/showthread.php?t=747537")

However if it is a new install I would recommend using the LiveCD to get what you need off the drive and then reinstalling.

---

### Post by kaptengu on 2008-11-13
Try this:
```

sudo dpkg --clear-avail
sudo apt-get update

```

---

### Post by kaptengu on 2008-11-13
Nevermind above post, it probably won't make any difference. I agree with porchrat, your filesystem is probably corrupted and the best way to solve this, if it is a fresh install, is to just reinstall.

---

