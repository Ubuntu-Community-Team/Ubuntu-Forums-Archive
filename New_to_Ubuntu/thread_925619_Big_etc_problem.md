---
title: "Big /etc problem"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by AADude on 2008-09-20
So yeah, I was trying to change permissions on the lampp etc folder and some how accidentily changed the etc folder in my file system.

So this comes up:
```

stephen@stephen-laptop:/$ sudo chown -R root etc
sudo: /etc/sudoers is owned by uid 1000, should be 0

```

;-; any ideas?

---

### Post by AADude on 2008-09-20
Also, when I do:
```

chown -R root etc

```

It comes up with stuff like:
```

chown: changing ownership of `etc/dhcp3/dhclient-exit-hooks.d/zzz_avahi-autoipd': Operation not permitted
chown: changing ownership of `etc/dhcp3/dhclient-exit-hooks.d/debug': Operation not permitted
chown: changing ownership of `etc/dhcp3/dhclient-exit-hooks.d': Operation not permitted

```

---

### Post by unutbu on 2008-09-20
Let's try to get sudo working again first:
Type
```

ls -l /etc/sudoers
```
The permissions and ownership should look like this:
```
-r--r----- 1 root root 716 2008-09-11 16:16 /etc/sudoers
```
If it doesn't, reboot into Recovery Mode. 
This will drop you into to a root shell. Then type
```

chown root:root /etc/sudoers
chmod 440 /etc/sudoers
init 2
```
This will resume a normal boot. Login and test that sudo works.

---

### Post by AADude on 2008-09-20
I have
```
stephen@stephen-laptop:/$ ls -l /etc/sudoers
-r--r----- 1 stephen root 470 2008-07-21 23:24 /etc/sudoers
```

I'm going to try the recovery mode part, brb.

---

### Post by AADude on 2008-09-20
Sudo works now. Any suggestions on fixing the other parts of /etc/?

---

### Post by unutbu on 2008-09-20
To your knowledge, is it only the ownership that needs to be fixed? If so, try
```
sudo chown -R root /etc
```

---

### Post by AADude on 2008-09-20
> **unutbu said:**
> To your knowledge, is it only the ownership that needs to be fixed? If so, try
```
sudo chown -R root /etc
```

Okay it seemed to have worked, no errors this time.
Thanks for your help :)
EDIT: and yes it was just the ownership I believe.

---

