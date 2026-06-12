---
title: "Gnome Schedulr not executing (neither on timer nor manually)"
date: 2013-08-31
forum: New to Ubuntu
---

### Post by rebmcr on 2013-08-31
Hi all,

I have a series of short scripts used to cycle the MAC address on wlan0 (in AP mode).
They're all located in /bin/macwalk, and look like this:

```
sleep 1
/sbin/ifconfig wlan0 down
sleep 2
/sbin/ifconfig wlan0 hw ether {MAC address here in each script}
sleep 2
/sbin/ifconfig wlan0 up
sleep 2
/usr/bin/service hostapd restart
sleep 1
```

They are set to be executable by anybody, and do execute correctly from the command line with (for example): [FONT=courier new]root@pc:~# /bin/macwalk/macwalk01[/FONT]

The scripts are all loaded in the root account's Gnome Scheduler, to execute at intervals. However, they do not appear to run when they are timed to in Gnome Scheduler; they also do not appear to run when executed manually from within Gnome Scheduler, including when Gnome Scheduler is running as root.

As far as I can tell, cron is running and as you can see, I have fully written out the paths to [FONT=courier new]ifconfig[/FONT] and [FONT=courier new]service[/FONT] in the scripts. I'm having trouble finding a solution to this problem, as searching just returns previous posts where the manual execution **is** working — so that's all the troubleshooting I've managed to do thus far.

---

### Post by rebmcr on 2013-08-31
Nevermind, it appears to have started working by itself on timer. Very confusing but at least it's working now.

---

