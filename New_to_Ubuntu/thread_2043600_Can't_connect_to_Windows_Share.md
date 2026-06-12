---
title: "Can't connect to Windows Share"
date: 2012-08-16
forum: New to Ubuntu
---

### Post by jamesaepp on 2012-08-16
Internal network; no domain. Username has full access in security settings.

IP is 192.168.03 (D-link likes proprietary, I'll tell ya)

Was working the other day in same install; now it's not.
Still works fine on windows hosts. Portable distros I have on some flash drives aren't connecting either. 

Probably some setting I've messed up or overlooked.
I've done all updates. 


Thanks!

---

### Post by mastablasta on 2012-08-17
try to restart samba while connected to windows.
make sure you are in same user group.

---

### Post by jamesaepp on 2012-08-17
> **mastablasta said:**
> try to restart samba while connected to windows.
make sure you are in same user group.

Again, can't connect to windows.
Can't restart samba when it's not installed.
There are no user groups; just each user for authentication on the Windows machine. This was working fine just the other day.

---

### Post by d4m1r on 2012-08-17
While having nautilus active (go to your home directory for example) go to the very top bar and search for something like "Connect to server.....". It will ask for the machines IP, a username and password, and will mount a shared Windows drive for you under Ubuntu.

---

### Post by jamesaepp on 2012-08-17
> **d4m1r said:**
> While having nautilus active (go to your home directory for example) go to the very top bar and search for something like "Connect to server.....". It will ask for the machines IP, a username and password, and will mount a shared Windows drive for you under Ubuntu.

This is precisely what I'm doing.

*EDIT*

I did not have a folder open while doing this. Why I need a folder open to mount a drive is beyond me.
Thanks for the info!

---

