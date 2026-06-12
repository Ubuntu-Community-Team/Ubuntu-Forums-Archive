---
title: "vmware network issue - want to change bridge"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Dev'olution on 2008-06-13
hey,

i originally set the computer to bridge to wlan0... however i want to change it to eth0

how do i go about changing this...

thanks,
kris:popcorn:

---

### Post by hyper_ch on 2008-06-13
power off the machine, then select settings and in there you should be able to switch.

---

### Post by Dev'olution on 2008-06-13
> **hyper_ch said:**
> power off the machine, then select settings and in there you should be able to switch.

nope. not possible. it just gives me the option of nat etc...

---

### Post by Dev'olution on 2008-06-13
bump

any ideas guys?

---

### Post by hyper_ch on 2008-06-13
hmmm, disconnect wlan0, connect eth0 and redo the vmware configuration...

```

sudo vmware-config.pl

```

and have the network there reconfigured

---

### Post by Dev'olution on 2008-06-13
> **hyper_ch said:**
> hmmm, disconnect wlan0, connect eth0 and redo the vmware configuration...

```

sudo vmware-config.pl

```

and have the network there reconfigured

i followed ur advice and now my vmware config is completely messed up with subnets and what not. any way to purge this?

---

### Post by hyper_ch on 2008-06-13
and what do you mean by that?

---

### Post by Dev'olution on 2008-06-13
its got two networks or something - plus - it searched for a subnet and a NAT :|

---

### Post by Dev'olution on 2008-06-13
Help?

---

