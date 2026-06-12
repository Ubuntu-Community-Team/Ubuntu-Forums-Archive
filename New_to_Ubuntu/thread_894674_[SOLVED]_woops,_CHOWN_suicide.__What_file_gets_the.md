---
title: "[SOLVED] woops, CHOWN suicide.  What file gets the fix?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by smandoli on 2008-08-19
In newbie fashion, I CHOWN-ed everything (chown -hR myname).  Now I can't sudo or access the Internet; I receive the message "sudo: must have sudeid ..."  (I apologize for working from memory, that is not the precise message.)

I am getting good to logging in through Recovery Console.  But the advice I find on this doesn't seem to apply:  
[LIST]
[*]The etc/sbin/groups file conforms to what is recommended
[*]The etc/bin/sodoers file, ditto
[*]The etc/sbin/sodo file doesn't seem to exist.
[/LIST]

Any ideas where I can make the change I need and start moving back to normal?  Ubuntu 8.04, tend to use gnome.

---

### Post by kpatz on 2008-08-19
/usr/bin/sudo needs to be owned by root and have 4755 permissions.

A bunch of other files also need SUID.  Here's a quick script I built based on what my box has (in /bin, /sbin, /usr/bin and /usr/sbin).

```
#!/bin/bash
cd /usr/bin
chown root:root *
chown daemon:daemon at
chown root:tty bsd-write wall
chown root:shadow chage expiry
chown root:crontab crontab
chown root:mail dotlock.mailutils
chown root:lpadmin lppasswd
chown root:mlocate mlocate
chmod 4755 arping chfn chsh gpasswd lppasswd mtr newgrp passwd pulseaudio sudo sudoedit traceroute6.iputils
chmod 6755 at X
chmod 2755 bsd-write chage crontab dotlock.mailutils expiry mlocate screen ssh-agent wall xterm
cd /usr/sbin
chown root:root *
chown root:dip pppd
chown libuuid:libuuid uuidd
chmod 4754 pppd
chmod 6755 uuidd
cd /bin
chown root:root *
chown root:fuse fusermount
chmod 4754 fusermount
chmod 4755 mount ping ping6 su umount
cd /sbin
chown root:root *
chown root:shadow unix_chkpwd
chmod 2755 unix_chkpwd
chmod 4755 mount* umount*
 
```

---

### Post by smandoli on 2008-08-19
Thanks to kpatz' reply I feel much closer to freedom.  I still can't access the Internet, however.  Any suggestions?

The only command that seemed to be rejected was chmod 2755 dotlock.mailutils.  If that isn't related, the Internet issue obviously could have something to do with my use of tinyproxy and DansGuardian.  I can ping localhost.

---

### Post by ghostdog74 on 2008-08-19
> **smandoli said:**
> In newbie fashion, I CHOWN-ed everything (chown -hR myname).  Now I can't sudo or access the Internet; I receive the message "sudo: must have sudeid ..."  (I apologize for working from memory, that is not the precise message.)

I am getting good to logging in through Recovery Console.  But the advice I find on this doesn't seem to apply:  
[LIST]
[*]The etc/sbin/groups file conforms to what is recommended
[*]The etc/bin/sodoers file, ditto
[*]The etc/sbin/sodo file doesn't seem to exist.
[/LIST]

Any ideas where I can make the change I need and start moving back to normal?  Ubuntu 8.04, tend to use gnome.
you should always backup first before you do chown
```

find `pwd` -printf "%u:%p\n" > /tmp/backup.txt

```

if you want to revert back after chown
```

while IFS=":" read a b; do chown $a $b done < /tmp/backup.txt

```

---

### Post by smandoli on 2008-08-29
It took a while but I have a computer again.  Kpatz got me a bit of start.  I decided a re-install was clearly needed, but I wanted to move files off before re-installing.  My chown disaster had made storage devices AND the Internet unavailable, so I was stuck.  

Then I bumped into an old friend who turned out to be Ubuntu-adept and very helpful.  He gave me a Knoppix system CD, which he explained would let me mount my USB storage accessories.  (Knoppix is also really cool to launch and poke around in.)  So I got my files off-loaded.  Now have reinstalled Ubuntu and am most of the way to goodness.  

I would have posted more on this forum (and asked for more advice), but my logon consistently failed for a week or more.  If it happens again I will try to make a new account.

---

