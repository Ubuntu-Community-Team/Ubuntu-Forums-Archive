---
title: "Permision Denied."
date: 2008-04-30
forum: New to Ubuntu
---

### Post by kikapu on 2008-04-30
Hi,

i used powertop to achieve a more optimum battery life and i try to apply it's suggestions.
So i have 3 commands:

sudo hal-disable-polling --device /dev/cdrom
sudo echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
sudo echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

the first i can execute without problem, but the seconds and third i cannot. It gives me a "permission denied" message although i give my password to sudo.

What i am doing wrong ? And if there is a way to execute them,how i can do it so automatically when my system boot so i will not have to type theme every time ?

Thanks a lot for any help!


ps: i am using 8.04

---

### Post by master5o1 on 2008-04-30
try doing this:

```
sudo -i
hal-disable-polling --device /dev/cdrom
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
logout
```

It might work.

---

### Post by lemming465 on 2008-04-30
The solution is OK.  The problem is that I/O redirection happens in the parent shell **before** the sudo runs.  So the ">" is still running as you, not as root.

You can put the commands into /etc/rc.local and they will be run as root each time the system boots.

---

### Post by kikapu on 2008-05-01
> **lemming465 said:**
> The solution is OK.  The problem is that I/O redirection happens in the parent shell **before** the sudo runs.  So the ">" is still running as you, not as root.

You can put the commands into /etc/rc.local and they will be run as root each time the system boots.

Thank you both. The commands seems to be working if i do a "sudo -i" first. They do note display a "permission denied" now so i suppose they work. but if after that i run powertop, it stills display the same suggestions...as the commands i entered didn't take effect...Strange.

---

