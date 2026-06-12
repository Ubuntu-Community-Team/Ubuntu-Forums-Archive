---
title: "Opening ports in Ubuntu"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by crashcoredump on 2008-07-18
In RHEL you can add additional ports to open or close in the FW sec manager. I was wondering if Ubuntu has an equivalent to this functionality?

I am trying to launch **Nessus** which wants to use 1241 and a quick look at netstat -l shows that port not in a listen state.

Does anyone know where the firewall or port security controls are located in Ubuntu?

Thanks.

---

### Post by hyper_ch on 2008-07-18
well, by default no ports are closed - but no services are listening. So your output is right or should be right. You'd first need to make a services listening before nessus will report something.

If you want to close down the iptables have a look at UFW.

---

### Post by cdtech on 2008-07-18
Are you running a firewall?

The command line to manipulate the iptables:
```
iptables -I INPUT -p tcp --dport 25 -j ACCEPT
```

Changing the port "25" to any port you want.

---

### Post by crashcoredump on 2008-07-18
In that case after a quick iptables -F and checking UFW and seeing it is not active maybe the "cannot connect to localhost" error is due to something in Nessus.
Let me dig through the docs.

Valew!

---

### Post by bodhi.zazen on 2008-07-18
ufw ftw :)

uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

---

