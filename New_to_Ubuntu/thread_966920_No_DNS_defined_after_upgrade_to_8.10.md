---
title: "No DNS defined after upgrade to 8.10"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Terpsicore on 2008-11-01
After upgrading to version 8.10 there is no DNS defined on the network connection, so i can't access any page on the web.

The rest of the network connection seems ok. If i make a ping to an extern address, i have response. Same with my internal network.

The problem seems to be with DNS definition. I can't (don't know how) define any DNS for my connection. Trying to edit the connection through the Network Manager icon doesn't work.

Any ideas?

Thanks in advance...

---

### Post by taurus on 2008-11-01
What does your /etc/resolv.conf look like?

Applications -> Accessories -> Terminal
```
cat /etc/resolv.conf
```

---

### Post by Terpsicore on 2008-11-01
It is empty.

If i edit the file and add the DNS...

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx


when i restart the file is empty again.

Trying to edit the network connection from the icon gives me an error (only read) when i press the OK button after the changes.

---

### Post by diablo75 on 2008-11-01
> **Terpsicore said:**
> It is empty.

If i edit the file and add the DNS...

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx


when i restart the file is empty again.

Trying to edit the network connection from the icon gives me an error (only read) when i press the OK button after the changes.

Try editing it with this command:

```
sudo gedit /etc/resolv.conf
```

---

### Post by Terpsicore on 2008-11-01
> **diablo75 said:**
> Try editing it with this command:

```
sudo gedit /etc/resolv.conf
```

This is what I've done, but after restart changes are reverted, and DNS keep undefined.

I've read other posts and it seems there is a bug with the Network Manager. None of the solutions i've tried solves the problem.

The funny thing is that the connection seems ok. All the pings respond ok, even external adress, but there is no way to tell the connection which DNSs to use.

---

### Post by gbragante on 2008-11-01
The same here, in addition I have also problem with some cifs mounts in fstab. The name of the SMB server is in hosts so DNS is not involved.
Using mount -a after boot mounts ok, even without editing resolv.conf

---

