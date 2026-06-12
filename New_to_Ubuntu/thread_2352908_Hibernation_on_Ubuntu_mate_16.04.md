---
title: "Hibernation on Ubuntu mate 16.04"
date: 2017-02-16
forum: New to Ubuntu
---

### Post by crazzyshooter on 2017-02-16
Hi,

I am using ubuntu mate 16.04 on acer laptop and i don't know how to enable hibernation. I am using 8GB Ram and SWAP of 2 gigs.

Please help.

Thanks in advance!

---

### Post by wildmanne39 on 2017-02-16
Please have a look at the link below it will tell you how to enable it and the warning of doing so.
[https://help.ubuntu.com/stable/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/stable/ubuntu-help/power-hibernate.html)

---

### Post by crazzyshooter on 2017-02-16
Thanks for replying so quick. I did try the above guide by running the sudo pm-hibernate command but it didn't work.

This is my partition table: [http://s11.postimg.org/vfw9ij5wj/Workspace_1_001.png](http://s11.postimg.org/vfw9ij5wj/Workspace_1_001.png)

Please have a look. :)

---

### Post by ajgreeny on 2017-02-17
You have nowhere near sufficient swap in your machine; you need slightly more swap than you have ram for hibernation to be possible, and I see you have only 1.91GB swap, but 8GB ram.

There is also the possibility as the sudo pm-hibernate was not successful, that your machine is physically unable to hibernate, which is why the option was removed from Ubuntu by default some time ago; it was more of a problem than a help.

---

### Post by crazzyshooter on 2017-02-17
> **ajgreeny said:**
> You have nowhere near sufficient swap in your machine; you need slightly more swap than you have ram for hibernation to be possible, and I see you have only 1.91GB swap, but 8GB ram.

There is also the possibility as the sudo pm-hibernate was not successful, that your machine is physically unable to hibernate, which is why the option was removed from Ubuntu by default some time ago; it was more of a problem than a help.

Ohh, I am gonna need more swap to enable hibernation. Thanks a lot ajgreeny for the help. I will add more swap when i reinstall the ubuntu OS later. ;)

---

