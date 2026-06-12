---
title: "network-manger vpnc no longer connecting"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by travishume on 2011-09-29
Starting today I'm no longer able to connect my vpnc connections. Syslog shows:

```
NetworkManager[2648]: <error> [1317336367.844192] [nm-vpn-connection.c:882] get_secrets_cb(): Failed to request VPN secrets #2: (6) No agents were available for this request.
```

No luck finding a solution yet. Anyone know what's going on or the best way to debug this?

Thanks

---

### Post by M0ses on 2011-09-30
I also have the problem, but found no solution. Seems like it`s a known problem and was already patched in older versions of network-manager:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-openconnect/+bug/824255](https://bugs.launchpad.net/ubuntu/+source/network-manager-openconnect/+bug/824255)

---

### Post by travishume on 2011-09-30
Hmmm, so it's a regression then? I'm not sure why it would be trying to present and auth dialog. I told the config to save the passwords.

---

### Post by FlashBuster on 2011-10-04
Same problem here with PPTP.. :((

> Oct  4 13:52:45 Fry NetworkManager[1151]: <info> Starting VPN service 'pptp'...
Oct  4 13:52:45 Fry NetworkManager[1151]: <info> VPN service 'pptp' started (org.freedesktop.NetworkManager.pptp), PID 14366
Oct  4 13:52:45 Fry NetworkManager[1151]: <info> VPN service 'pptp' appeared; activating connections
Oct  4 13:52:45 Fry NetworkManager[1151]: <error> [1317729165.708949] [nm-vpn-connection.c:882] get_secrets_cb(): Failed to request VPN secrets #2: (6) No agents were available for this request.
Oct  4 13:52:45 Fry NetworkManager[1151]: <info> Policy set 'Auto-Ethernet' (eth0) as default for IPv4 routing and DNS.
Oct  4 13:52:50 Fry NetworkManager[1151]: <info> VPN service 'pptp' disappeared


---

### Post by travishume on 2011-10-04
This problem resolved itself for me. I'm not positive which update fixed the problem but here are my installed versions:

```

ii  network-manager                                0.9.1.90-0ubuntu2                                  network management framework (daemon and userspace tools)
ii  network-manager-gnome                          0.9.1.90-0ubuntu6                                  network management framework (GNOME frontend)
ii  network-manager-pptp                           0.9.0-0ubuntu2                                     network management framework (PPTP plugin core)
ii  network-manager-pptp-gnome                     0.9.0-0ubuntu2                                     network management framework (PPTP plugin GNOME GUI)
ii  network-manager-vpnc                           0.9.0-0ubuntu1                                     network management framework (VPNC plugin core)
ii  network-manager-vpnc-gnome                     0.9.0-0ubuntu1                                     network management framework (VPNC plugin GNOME GUI)

```

I don't have a pptp tunnel to test with sorry.

---

