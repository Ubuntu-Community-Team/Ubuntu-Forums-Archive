---
title: "Count DHCP clients in network"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by Blagomir on 2008-11-14
Hello

I have successfully created local network using Ubuntu in my router (pc). I have one problem - can`t count how many users are currently connected to my router. How can i do this?

---

### Post by Iowan on 2008-11-14
The **who** command is supposed to tell who is logged on.  I suppose you could filter the results through **grep -c** for a count. (who |grep -c "192.168.1.")

That may not tell you who is actually connected, though.
/var/lib/dhcp3/dhcpd.leases shows which machines have leases. but dunno if it tells which are actually connected - sometimes old leases are still there, too.

---

