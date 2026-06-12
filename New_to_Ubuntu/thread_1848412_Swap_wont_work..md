---
title: "Swap wont work."
date: 2011-09-22
forum: New to Ubuntu
---

### Post by wyattwic on 2011-09-22
Hello everyone.

I have a small issue.   I cant get swap to work at all.

I have created a swapfile (1GB) then attempted to "swapon /swapfile" with no success. (Error message: "swapon: /swapfile: swapon failed: Operation not permitted"

I have re-tried this many times and I do have root/superuser.  Does anyone have any ideas?

I am using Ubuntu 10.04.3 LTS x64bit

To help out..

Copy of my fstab
```

# vim /etc/fstab
proc  /proc       proc    defaults    0    0
none  /dev/pts    devpts  rw          0    0

```

---

### Post by Elfy on 2011-09-22
You need to add the swap to fstab

[https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F)

---

### Post by Enigmapond on 2011-09-22
Not seeing a swap in the fstab file. One question, what is the reason you need that size of swap? With normal operation, you don't even need it. I did away with mine...and I use GIMP, Blender and Audacity without even wanting swap.

However, on your question, you may have to tell swapon the /dev where it's located and may have to enter the command as root. i.e. sudo swapon /dev/sda?

---

