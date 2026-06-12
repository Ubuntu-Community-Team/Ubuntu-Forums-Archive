---
title: "unattended updates"
date: 2023-11-07
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2023-11-07
i ran sudo update. At the end i got this message
Canonical released microcode updates for both Intel (CVE-2022-40982) and AMD# (CVE-2023-20593). ‘Unattended upgrades’ provide security updates by default.
# Ensure it remains enabled to always get all updates as they become available.
#
how do you enable unattended upgrades? Thx for help

---

### Post by MAFoElffen on 2023-11-07
Is enabled by default...

That message is apt news, delivered to everyone, regardless if it relates you (your personal device) or not. When it does updates, however they are done, they will apply.

If you want to check your update settings, open the "Software & Updates" > Updates Tab > Check for Updates... The default setting is "Daily"

---

### Post by tuesdaybarrett on 2023-11-08
thx i have it set for daily updates and update on a daily basis using terminal commands

---

### Post by ajgreeny on 2023-11-08
> **tuesdaybarrett said:**
> thx i have it set for daily updates and update on a daily basis using terminal commands
So do you mean from that comment that you do have **unattended upgrades** enabled or not?

You need to see what I show in my image attached to get security updates with no action on your part.

---

### Post by vmpx on 2023-11-10
I have changed the Unattended-Upgrade on Ubuntu from every day to 14 days:

/etc/apt/apt.conf.d/10periodic
/etc/apt/apt.conf.d/20auto-upgrades
```
APT::Periodic::Unattended-Upgrade "14";
```
"0": means is disabled

---

