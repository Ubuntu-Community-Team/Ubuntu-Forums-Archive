---
title: "my ubuntu 11.04 cannot update automatically"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by yath on 2012-10-16
hie guys 

i have a dual boot sytem that is win7 and ubuntu 11.04. they are ok however cannot update ubuntu automatically, moreover when i try manually this is what i get.
 any help?

E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by s3a on 2012-10-16
Did you try rebooting?

---

### Post by audiomick on 2012-10-16
I believe you get that when you try to use two instances of package management at the same time, like, for instance, trying to use apt-get while synaptic is open or trying to use the update manager with synaptic open. Are you sure there is not something along those lines happening?

---

### Post by overdrank on 2012-10-16
Hi and could it be that 11.04 has reached  [_end of life support_]("https://wiki.ubuntu.com/Releases")?

---

