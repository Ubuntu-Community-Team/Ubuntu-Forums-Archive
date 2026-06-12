---
title: "[SOLVED] no localhost, lo=lo"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Statik on 2008-07-13
hey all,

I was trying to setup a LAMP server but I have no connection to localhost. In trying to solve the problem I rebooted and I noticed in the boot messages the following:
```
Ignoring unknown network lo=lo
```

or something like that. I'm going from memory. Where can I find that message and how do I fix it?

Statik

---

### Post by Dedoimedo on 2008-07-13
Hello,

Boot messages can be found under var/log/messages.

You can also type sudo dmesg to look for suspicious and conflicting drivers and errors, which might help you understand the nature of the problem.

Dedoimedo

---

### Post by Statik on 2008-07-13
That message wasn't in any of the readable logs in /var/log. I didn't find it in dmesg either (dmeseg | grep lo=lo). I definitely saw it during boot. The one where it lists [ok] or [fail] after each step.

Statik

---

### Post by Dedoimedo on 2008-07-13
Hello,

What do you have under ifconfig:

ifconfig -a

And did you perhaps forbid loopback in firewall rules? Did you maybe define a default drop or reject policy for all input / output, including loopback?

Dedoimedo

---

### Post by Statik on 2008-07-13
Did some searching on the internet. Found that the /etc/network/interfaces had the following:
```
auto lo/niface lo inet loopback
```

this didn't seem right, so I changed it to:
```
iface lo inet loopback
```

rebooted and it works!

Statik

---

