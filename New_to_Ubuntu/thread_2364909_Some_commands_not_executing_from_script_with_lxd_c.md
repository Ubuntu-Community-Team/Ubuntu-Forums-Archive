---
title: "Some commands not executing from script with lxd containers."
date: 2017-06-29
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2017-06-29
Trying to script creation of lxd containers for a future project I'm working on. I run this from my main user in the lxd group. I know these commands work when I run them manually but when they run through the script they fail with permission denied and so forth. I'm at a loss.

```

lxc exec "$container" -- adduser --uid 1001 mcserver # fails with permission denied
lxc exec "$container" -- usermod -aG sudo mcserver # fails because adduser failed
lxc exec "$container" -- echo "Acquire::http { Proxy \"http://failbox.mylan.home:3142\"; };" > /etc/apt/apt.conf.d/02proxy # permission denied
lxc exec "$container" -- sed -i 's/prohibit-password/yes/' /etc/ssh/sshd_config # permission denied
lxc exec "$container" -- sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/' /etc/ssh/sshd_config #permission denied
lxc exec "$container" -- echo "newpass\newpass" | passwd # permission denied

```

---

