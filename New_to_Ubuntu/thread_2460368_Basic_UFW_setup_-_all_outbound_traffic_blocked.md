---
title: "Basic UFW setup - all outbound traffic blocked"
date: 2021-04-08
forum: New to Ubuntu
---

### Post by andrewmoore on 2021-04-08
Hi all,

Brand new Ubuntu 20.04 Server installation and I have applied the following UFW configuration.
```

ufw allow in on lo
ufw allow out from lo
ufw deny in from 127.0.0.0/8
ufw deny in from ::1
ufw allow out on all
ufw allow in ssh
ufw default deny incoming
ufw default deny outgoing
ufw default deny routed
ufw enable

```

With the following result.

```

Status: active
Logging: on (low)
Default: deny (incoming), deny (outgoing), disabled (routed)
New profiles: skip


To                         Action      From
--                         ------      ----
Anywhere on lo             ALLOW IN    Anywhere
Anywhere                   DENY IN     127.0.0.0/8
22/tcp                     ALLOW IN    Anywhere
Anywhere (v6) on lo        ALLOW IN    Anywhere (v6)
Anywhere (v6)              DENY IN     ::1
22/tcp (v6)                ALLOW IN    Anywhere (v6)


Anywhere                   ALLOW OUT   Anywhere on lo
Anywhere                   ALLOW OUT   Anywhere on all
Anywhere (v6)              ALLOW OUT   Anywhere (v6) on lo
Anywhere (v6)              ALLOW OUT   Anywhere (v6) on all

```

SSH in is working as expected. However no outbound traffic (DNS, apt, ICMP etc) is working. My understanding is this should be covered by the *ufw allow out on all *rule?

Any assistance to understand where I have gone wrong would be greatly appreciated. Thanks in advance.

---

### Post by Doug S on 2021-04-08
Is there a return path for your outgoing traffic?
With iptables, which ufw is just a front end for, the path would be via a "RELATED,ESTABLISHED" rule.
I do not use ufw, so do not know the answer.

---

