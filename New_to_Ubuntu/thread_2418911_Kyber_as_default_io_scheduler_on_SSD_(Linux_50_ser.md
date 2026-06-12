---
title: "Kyber as default io scheduler on SSD (Linux 50 series) - A mystery"
date: 2019-05-13
forum: New to Ubuntu
---

### Post by sandrito2 on 2019-05-13
So I wanted to use kyber (instead of mq-deadline) as default io scheduler for my SSD (Toshiba Q300). What I did is very simple, and it works well. I&#8217;ve just created a file /etc/udev/rules.d/60-ioscheduler.rules with the following content:

```
# set scheduler for NVMe
ACTION=="add|change", KERNEL=="nvme[0-9]*", ATTR{queue/scheduler}="none"
# set scheduler for SSD and eMMC
ACTION=="add|change", KERNEL=="sd[a-z]|mmcblk[0-9]*", ATTR{queue/rotational}=="0", ATTR{queue/scheduler}="kyber"
# set scheduler for rotating disks
ACTION=="add|change", KERNEL=="sd[a-z]", ATTR{queue/rotational}=="1", ATTR{queue/scheduler}="mq-deadline"
```

After rebooting kyber is working as expected:

```
sandrito@maverick:~$ cat /sys/block/sda/queue/scheduler
mq-deadline [kyber] none
```

So far so good. No need to preload kyber-iosched at boot since I&#8217;m using:

```
ACTION=="add|change"
```

But why is it that if I also add kyber-iosched in /etc/modules-load.d/modules.conf my laptop performs much better with lower memory usage and CPU temperature? Isn&#8217;t kyber module loaded axactly the same way?

---

### Post by LwIh%*7 on 2019-06-03
Could you have a look at this?

[https://unix.stackexchange.com/questions/400483/how-to-enable-kyber-scheduler-in-ubuntu-17-10-kernel-4-13/454783](https://unix.stackexchange.com/questions/400483/how-to-enable-kyber-scheduler-in-ubuntu-17-10-kernel-4-13/454783)

And see if this helps.

---

