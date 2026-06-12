---
title: "ufw rule not working for ssh"
date: 2020-03-03
forum: New to Ubuntu
---

### Post by cnedas on 2020-03-03
Hello,

I am using Ubuntu 14.04

Below is what I get whe I do: [B]sudo ufw status verbose

[/B]```

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    Anywhere
25/tcp                     ALLOW IN    Anywhere
21000/tcp                  ALLOW IN    Anywhere
21000                      ALLOW IN    Anywhere
22/tcp (v6)                ALLOW IN    Anywhere (v6)
25/tcp (v6)                ALLOW IN    Anywhere (v6)
21000/tcp (v6)             ALLOW IN    Anywhere (v6)
21000 (v6)                 ALLOW IN    Anywhere (v6)


```
I log out off SSH and I try to login using port 21000, but it won't let me, and I get the below message:


```

Network error: Connection refused

```

But, when I go back to port 22, I am able to log in.

Any idea why?

---

### Post by TheFu on 2020-03-03
Did you tell sshd to listen on a different port?  The sshd_config file controls this.
I honestly hope you have fail2ban installed and configured too.

---

### Post by cnedas on 2020-03-03
I had not changed sshd_config.
I just did, and ssh works just fine now.
Thanks!

---

### Post by DuckHook on 2020-03-04
> **cnedas said:**
> …I am using Ubuntu 14.04…
> **TheFu said:**
> …I honestly hope you have fail2ban installed and configured too.
If I were the OP, I would be far more concerned about security holes from a dead OS. There have been dozens of security holes found since Trusty reached EoL.

---

### Post by TheFu on 2020-03-04
> **DuckHook said:**
> If I were the OP, I would be far more concerned about security holes from a dead OS. There have been dozens of security holes found since Trusty reached EoL.

+10!    I completely missed that.  

14.04 Server is EoL and has been over a year.  It isn't safe to run that OS.  There are remote exploits and no on-system firewall will prevent them.  Not sure how to impart the appropriate amount of fear into the OP.  If you must run 14.04, there are 2 choices:
[LIST=1]
[*]Pay Canonical for ESM to get patches.
[*]Don't let it on any network.
[/LIST]

ESM [https://ubuntu.com/blog/extended-security-maintenance-ubuntu-14-04-trusty-tahr](https://ubuntu.com/blog/extended-security-maintenance-ubuntu-14-04-trusty-tahr)
Basically, this is a stop-gap as migration to a supported release happens.

---

