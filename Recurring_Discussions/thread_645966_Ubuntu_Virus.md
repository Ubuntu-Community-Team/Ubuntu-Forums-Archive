---
title: "Ubuntu Virus"
date: 2007-12-20
forum: Recurring Discussions
---

### Post by cartisdm on 2007-12-20
First off I have no complaints about Ubuntu so far and I've been using it for about 2 months now.  I tried Fedora 7 for like a week and didn't like it nearly as much.  Other than that this has been my only linux experience so I have a question.  Do Macs and linux boxes not need virus protection because of their security or because Windows is just the more obvious target?  If the latter is true then as the Ubuntu community grows then won't the virus risk grow?

---

### Post by aimran on 2007-12-20
[http://ubuntuforums.org/showthread.php?t=323028](http://ubuntuforums.org/showthread.php?t=323028)

Recurring discussions section of the forums is your friend :)

---

### Post by ~LoKe on 2007-12-20
Both.

Windows was horribly coded in a way that almost completely obliterated any kind of permission system, which allows a "virus" to spread wherever it wants.  Security patches over and over just leave more holes.  It is also the most widely used operating system so it's more prone to attacks.

Linux, however, is strict with its permissions.  A virus can not spread far enough to do irreparable damage unless run as super user (sudo or as root).  However, there are still **many** people targeting Linux/UNIX systems (since most servers are hosted on such machines), it's just extremely rare for something to actually get in and do damage unless you're doing it on purpose.

---

### Post by dhobbs on 2007-12-20
Yes and no.  Viruses are just malicious programs that gain access to system files (that's a very generic statement).  Pre-Vista Windows basically let everyone and their dog have administrative privileges on the system which made it very easy for a virus to gain the necessary privileges to do damage.

Linux doesn't run in "Administrator" mode, I don't believe it ever has.  That means applications do not have access to the system files unless it is given to them (thus the use of "su" and "sudo").

There are better explanations as to why you don't need to be that afraid of Linux viruses because it is more complex than that, but it's a starting point.

---

### Post by fatality_uk on 2007-12-20
And of course, NEVER, unless you REALLY need to log in as ROOT user under Linux.

---

### Post by bapoumba on 2007-12-20
Thread moved to "Recurring Discussions".

---

### Post by Linuxratty on 2007-12-20
Peter van der Linden wrote:
The "don't run as root" mantra dates from the days of
timesharing servers. When you run on a single user PC, your
most valuable resource is your data, not the integrity of
the system.

If your system is compromised, the attacker can do all the
things he wants to do in your user account, equally well as
a root account (store files, send spam, run zombie
software). Being or not being root doesn't hinder him at
all.

On a server it is bad to be root all the time because a
mistake by you could affect many other people. On a single
user PC behind a firewall there is no compelling reason not
to run as root."

---

### Post by gn2 on 2007-12-20
> **Linuxratty said:**
>  On a single
user PC behind a firewall there is no compelling reason not
to run as root."

Protection from one's own mistakes perhaps.....?

---

### Post by smartboyathome on 2007-12-20
If you are really scared, I would recommend using Moblock. It is basically a Peerguardian alternative for Linux.

---

### Post by bruce89 on 2007-12-20
> **dhobbs said:**
> Pre-Vista Windows basically let everyone and their dog have administrative privileges on the system which made it very easy for a virus to gain the necessary privileges to do damage.

Whereas Vista nags you so much, you don't want to use it.

> **Linuxratty said:**
> The "don't run as root" mantra dates from the days of
timesharing servers. When you run on a single user PC, your most valuable resource is your data, not the integrity ofthe system.

Surely not running things as root is to stop them doing a rm -fr <censored> type thing. (replace <censored> with the root filesystem location)

---

