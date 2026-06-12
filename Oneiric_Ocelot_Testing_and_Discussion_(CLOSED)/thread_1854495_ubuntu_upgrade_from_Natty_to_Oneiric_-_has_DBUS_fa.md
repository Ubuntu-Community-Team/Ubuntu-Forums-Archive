---
title: "ubuntu upgrade from Natty to Oneiric - has DBUS failing"
date: 2011-10-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by nicolasdiogo on 2011-10-04
hello,

just upgraded ubuntu from 11.04 (natty) to 11.10 (Oneiric) and it has taken me a while to figure out this simple but trouble-some *BUG*

the problem is that after the upgrade completed, i rebooted my laptop and it started giving erros messages about dbus not been able to communicate..

it turns out that during upgrade it somehow felt old version of my files under:
**/var/run/dbus**

to solve this problem - one has only to remove this folder and reboot:
**rm -Rv /var/run/dbus**

hope this problem gets corrected by the final version

---

### Post by madjr on 2011-10-04
> **nicolasdiogo said:**
> hello,

just upgraded ubuntu from 11.04 (natty) to 11.10 (Oneiric) and it has taken me a while to figure out this simple but trouble-some *BUG*

the problem is that after the upgrade completed, i rebooted my laptop and it started giving erros messages about dbus not been able to communicate..

it turns out that during upgrade it somehow felt old version of my files under:
**/var/run/dbus**

to solve this problem - one has only to remove this folder and reboot:
**rm -Rv /var/run/dbus**

hope this problem gets corrected by the final version

hope they fix broken stuff like that, else it would be [better not to offer the upgrade button]("http://ubuntuforums.org/showthread.php?t=1852654") in such an easy way

---

### Post by philinux on 2011-10-04
> **nicolasdiogo said:**
> hello,

just upgraded ubuntu from 11.04 (natty) to 11.10 (Oneiric) and it has taken me a while to figure out this simple but trouble-some *BUG*

the problem is that after the upgrade completed, i rebooted my laptop and it started giving erros messages about dbus not been able to communicate..

it turns out that during upgrade it somehow felt old version of my files under:
**/var/run/dbus**

to solve this problem - one has only to remove this folder and reboot:
**rm -Rv /var/run/dbus**

hope this problem gets corrected by the final version

I hope you've bugged this one. :P

---

### Post by xyzzyman on 2011-10-04
This happened to me when I upgraded a few weeks back.

[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441)
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/807306](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/807306)

Even if you're not having any dbus errors now I'd still do the following so everything is how it should be (I did these from a recovery prompt):

> There's a transition happening from /var/run to /run see bug #807306. In my case the update that was supposed to handle this transition didn't work.

You need to
(i) create directories /run and /run/lock,
(ii) move contents of /var/run into /run and /var/lock into /run/lock,
(iii) delete directories /var/run and /var/lock
(iv) create replacement simlinks; e.g. 'ln -s /run /var/run' and 'ln -s /run/lock /var/lock'

---

### Post by alphacrucis2 on 2011-10-04
I notice on my Oneiric that /var/run is a link to /run.

I recall reading some mailing lists where I think it was Lennart Poettering who mooted introducing /run and it was first used in Fedora 15. There were some going ballistic about it corrupting Unix standards but Lennart's arguments for it seemed quite convincing and sensible to me.

---

### Post by nicolasdiogo on 2011-10-05
yep

it seems to be related to moving:
/var/run to /run
/var/lock to /run/lock

look at this:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441)


thanks - my idea for upgrading was to assist with the fixing prior to launch; it seems that some people are more interested to mock others then to help out.

Cheers!

---

### Post by madjr on 2011-10-05
> **alphacrucis2 said:**
> I notice on my Oneiric that /var/run is a link to /run.

I recall reading some mailing lists where I think it was Lennart Poettering who mooted introducing /run and it was first used in Fedora 15. There were some going ballistic about it corrupting Unix standards but Lennart's arguments for it seemed quite convincing and sensible to me.

it was not corrupting any standards, in fact it was made a new standard and adopted by all main distros

---

