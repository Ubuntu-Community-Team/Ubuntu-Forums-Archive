---
title: "How can I see the process that init starts?"
date: 2019-04-14
forum: New to Ubuntu
---

### Post by anthony10053 on 2019-04-14
Hi, I have been using Ubuntu GUI for several years now and would like to learn more about the inner workings of Ubuntu and Linux. That being said, I am reading Linux for Dummies and have learned to use some of the basic commands available on a terminal. I have hit a wall in the chapter titled Understanding How Linux Boots. The author says that the /etc/inittab file is the key to understanding the processes that init starts at various run levels. As you are probable aware, the inittab file does not exist. How can I see the process that init starts? Thanks for the help.

---

### Post by cruzer001 on 2019-04-14
Sounds like your talking about ***systemd***

[https://www.freedesktop.org/wiki/Software/systemd/](https://www.freedesktop.org/wiki/Software/systemd/)

If so, your getting into some heavy reading.

[https://wiki.archlinux.org/index.php/systemd](https://wiki.archlinux.org/index.php/systemd)

The basic commands for system information are good to know, so its not necessary to get into the nuts and 
bolts of it.  Also systemctl can be very helpful knowledge.

[https://www.linode.com/docs/quick-answers/linux-essentials/introduction-to-systemctl/](https://www.linode.com/docs/quick-answers/linux-essentials/introduction-to-systemctl/)

---

### Post by anthony10053 on 2019-04-14
Thanks cruzer001, I'll check out the links and see where that gets me.

---

### Post by anthony10053 on 2019-05-03
Update on my research. 

The init process has been managed in the past by SysVinit which was replaced by Upstart around 2006, which has now been replaced by Systemd around 2015. Previous to Systemd the init process utilize the inittab file to load the default system configuration. The inittab file does not exit by default in a modern system, but it can be created to temporarily modify the default system configuration and deleted once it is no longer needed.

The default runlevel is set in the file rc-sysinit.conf under the Systemd init system and the various runlevels available are found in the directory etc/rc0.d, rc1.d, rc2.d and so on.

In conclusion: Cruzer001 you are correct about those links you provided being some pretty heavy reading. I had plenty of meat to chew on these past weeks and now it's now time for a little milk. I appreciate your help!  I am sure there will be more questions.

---

### Post by dino99 on 2019-05-03
Coding rules: what was true yesterday can be false today and even worse tomorrow; That is coder life; there is nothing static in that world, everything can be rebuild via a different way.

---

### Post by drvshrm on 2019-05-07
If what I am understanding is right, you can press "Down Arrow" key while booting Ubuntu, this can show you the init process during startup...

---

### Post by cruzer001 on 2019-05-07
I do not know about the down arrow.  I would prefer boot info in a fixed format after boot and would use the command:
```
systemd-analyze blame
```
[https://www.tecmint.com/systemd-analyze-monitor-linux-bootup-performance/](https://www.tecmint.com/systemd-analyze-monitor-linux-bootup-performance/)

---

