---
title: "Firefox broke"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by Nightmist on 2012-07-30
Hi,

When I started Firefox today, it broke. Specifically, I got a message saying:

> Alert
Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.

Not sure why this suddenly decided to pop up, as I haven't done anything to my system lately, apart from surfing the web, and perhaps updating the system. Anyone know what's going on?

---

### Post by Vakman on 2012-07-30
This link will explain: [http://kb.mozillazine.org/Could_not_initialize_the_browser_security_component](http://kb.mozillazine.org/Could_not_initialize_the_browser_security_component)

---

### Post by Nightmist on 2012-07-30
Well, maybe I should have mentioned it in the first post, but I checked the obvious stuff:

-I do have plenty of free space.

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        26G  5.8G   19G  25% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           791M  952K  791M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  416K  2.0G   1% /run/shm

```

-cert8.db has Access: Read and write.

**EDIT: I deleted cert8.db. That fixed it.**

---

### Post by Vakman on 2012-07-30
Ah, good, that was the third option on that link.
Good to hear.

---

