---
title: "Oneiric boot problem"
date: 2011-09-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by laoe1 on 2011-09-14
Hi all.
Installed Oneiric beta1, xubuntu, on AsusN55s notbook. Install looks wery nice, but one problem remains. 

At startup the screen goes black, and nothing more happens. Killing it, (Alt-SysRq-b)and rebooting, gets me to a grub-menu. I can then start in recovery mode, and "Resume normal boot" lets me log in as a user (in text-mode), Btw, "Repair broken passages" don't give any errors.

Then, after "sudo start lightdm" all is nice and shiny! Very nice indeed, thanks to all!

But somehow I feel it should not be that difficult ;) Any ideas?

l

---

### Post by drs305 on 2011-09-14
I have a lightdm link in my /etc/init.d folder, which links to //lib/init/upstart-job. There is also an /etc/init.d/lightdm.conf file.

If you are missing any of these (or even if not) perhaps reinstalling lightdm might help:
```
sudo apt-get install --reinstall lightdm
```

---

### Post by Seq on 2011-09-14
How long did you wait on boot before rebooting? Was magic sysrq necessary, or would CTRL+ALT+DEL on a VTY trigger a friendly reboot?

I was bit by two issues yesterday: I had ethernet plugged in during install, causing an 'auto eth0' entry to be dropped into /etc/network/interfaces. NetworkManager administers this on my desktop and removed the configuration from that file (leaving the auto line).

However, boot scripts saw it should be brought up (even though it had no config), and would wait for a timeout. That was issue #1, waiting for an non-configurable interface to be configured.

Issue #2 was the timeout was recently increased from 30 to 120 seconds, causing an extremely noticeable delay (I always thought oneiric booted a little slow). If I booted and left the machine for two minutes, it would continue happily.

---

### Post by laoe1 on 2011-09-14
Thanks both!

drs305: will try that tomorrow after work!

seq: Tried the reboots many times, some  of them quite some time between. Ctrl-alt-del did not work, SysRq necessary.

Btw, forgot to say i had to use the "nomodeset" option to make it install. Sorry. Can it have something to do with it?

---

### Post by laoe1 on 2011-09-15
Ok, problem solved - sort of!

First, tried to reinstall lightdm. That did not work.

Then I found the thread below, and searched around some more.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

My fault for forgetting to state from the beginning that I had to use the "nomodeset" option when installing. It seems that was the problem. Normal boot did not find video drivers. 

Added repositories "ppa:ubuntu-x-swat/xupdates", and installed the "nvidia-current" drivers. After reboot everything seems to work nice :D Maybe reinstalling default nvidia-driver would also have worked?

But I hesitate to mark this as "solved", because it is really just a workaround, as I don't think using the "nomodeset" option should be necessary to install?

Cheers, and thanks all!

---

