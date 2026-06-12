---
title: "CUPS Reloading Automatically"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by vba_djs on 2008-05-22
My server running 7.10 sporadically displays messages that it is Reloading CUPSD or the System Log Daemon.

Is this something that I should be worried about, or is this normal operating procedure?

This never happened, or at least it wasn't displayed, when the server was running 6.06.

Thanks,

---

### Post by cmnorton on 2008-05-22
Look at the logs in /var/log/cups, and look at /var/log/messages and /var/log/syslog.
I have had the CUPS daemon crash and not restart on a Red Hat EL 4 system, because my Ubuntu workstation was advertising a printer. You'll have to poke around to see if you can set the cups daemon to restart on error.

---

### Post by vba_djs on 2008-05-23
> **cmnorton said:**
> Look at the logs in /var/log/cups, and look at /var/log/messages and /var/log/syslog.
I have had the CUPS daemon crash and not restart on a Red Hat EL 4 system, because my Ubuntu workstation was advertising a printer. You'll have to poke around to see if you can set the cups daemon to restart on error.

These were the significant entries in /var/log/messages that are related to cups.  I have no idea what any of this means.

May 21 07:35:06 server2 kernel: [514957.050971] audit(1211373306.694:100):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/var/run/samba/gencache.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:06 server2 kernel: [514957.050999] audit(1211373306.694:101):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/run/samba/gencache.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:06 server2 kernel: [514957.053539] audit(1211373306.694:102):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/var/run/samba/gencache.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:06 server2 kernel: [514957.053565] audit(1211373306.694:103):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/run/samba/gencache.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:06 server2 kernel: [514957.142038] audit(1211373306.694:104):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/run/samba/unexpected.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:07 server2 kernel: [514957.231886] audit(1211373306.694:105):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/run/samba/unexpected.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:07 server2 kernel: [514957.321738] audit(1211373306.694:106):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/run/samba/unexpected.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:07 server2 kernel: [514957.411593] audit(1211373307.194:107):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/run/samba/unexpected.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:07 server2 kernel: [514957.501444] audit(1211373307.194:108):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/run/samba/unexpected.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:07 server2 kernel: [514957.591296] audit(1211373307.194:109):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/run/samba/unexpected.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:07 server2 kernel: [514957.681153] audit(1211373307.194:110):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/run/samba/unexpected.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:07 server2 kernel: [514957.771001] audit(1211373307.194:111):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/run/samba/unexpected.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:07 server2 kernel: [514957.860854] audit(1211373307.194:112):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/run/samba/unexpected.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:07 server2 kernel: [514957.869448] audit(1211373307.194:113):  type=1503 operation="inode_permission" requested_mask="rw" denied_mask="rw" name="/var/run/samba/gencache.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:07 server2 kernel: [514957.869474] audit(1211373307.194:114):  type=1503 operation="inode_permission" requested_mask="r" denied_mask="r" name="/var/run/samba/gencache.tdb" pid=4735 profile="/usr/sbin/cupsd"
May 21 07:35:17 server2 syslogd 1.4.1#21ubuntu3: restart.

---

### Post by rossigee on 2009-08-17
I had the same error. It seems I was missing '/var/run/samba' from the AppArmor profile for cupsd. I added the last two lines from the following:

root@rossg-workstation:~# grep samba /etc/apparmor.d/usr.sbin.cupsd 
  /var/samba r,
  /var/samba/* r,
  /var/run/samba r,
  /var/run/samba/* r,

---

### Post by rossigee on 2009-08-17
...and restarted AppArmor:

root@rossg-workstation:~# service apparmor restart
 * Reloading AppArmor profiles ... [OK]

---

