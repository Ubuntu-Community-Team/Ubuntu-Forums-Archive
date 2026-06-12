---
title: "Computer randomly rebooting (serious problem)"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by linuxneeewb on 2008-06-03
Dear all:

I just installed Ubuntu on my work computer,and did a clean fresh install of Ubuntu 7.10. My problem is that Ubuntu will randomly log me out for no apparent reason(s). I never told it to log out or reboot. This happens very randomly, but has happened to me at least 5 times in the last 2 days. I have used Ubuntu for almost 2 years, and I have never experienced something like this before. For example, I will be surfing the web with Firefox or using a terminal, and I might be randomly logged out. In fact I installed Ubuntu 7.10 3 times because of the problem, but I still get the same problem. I would greatly appreciate if you could walk me through the steps to fix the problem. Any and all help is appreciated.

Thank You
:guitar:

---

### Post by django0909 on 2008-06-03
Try reconfiguring X

```
sudo dpkg-reconfigure xserver-xorg
```

Also read this...

[http://ubuntuforums.org/showthread.php?t=812856]("http://ubuntuforums.org/showthread.php?t=812856")

---

### Post by linuxneeewb on 2008-06-03
I still have the problem. But after a recent crash, I found the log file of the exact error.

In /var/log there is a file called daemon.log which has a log of many operations in the computer.

The error message that I get is

Jun  3 17:12:48 myusername-desktop gdm[5946]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

Any additional help is appreciated.

Thanks

---

### Post by adobrakic on 2008-06-03
My computer used to randomly turn off, I noticed that one of the fans would get stuck from all the dust that got picked up in it. I don't think this is your problem, but you never know.

---

