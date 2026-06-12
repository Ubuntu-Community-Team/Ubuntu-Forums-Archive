---
title: "client error 'dsn server not responding but detected'"
date: 2013-06-18
forum: New to Ubuntu
---

### Post by trilju2005 on 2013-06-18
i am setting up dns dhcp ubuntu 12.04 server.  i have 2 eth0 eth1 cards.  my client can ping host 127.0.0.1 but cannot ping router internet.  i believed i am lost.  i can use webmin also. i have eth0 coming in and i want eth1 to connect clients to go out.  i have books to give definitions. it is now i am lost in a maze, also i did not know what nm ment finally found out what that was network manager so first tell me all then abbreviate; thanks.

---

### Post by Vitsliputsli on 2013-06-18
If you use server, you probably have no GUI (graphical user interface), so you have no Network Manager (tool for network setting).
How are you control network? 
127.0.0.1 is loopback, it's yourself pc. It's work even without network adapter.

---

### Post by trilju2005 on 2013-06-18
i have a ubuntu server gui and webmin.  i have bind9 and downloaded dhcp which both can be managed with webmin.  i did try to download dnsmasq but couldnt get it to download all the way maybe, dont know if i had all of the package.  then read somewhere that the network manager(NM) and dnsmasq didn't work well together with 12.04. but read that dnsmasq is just great to have and might make my life easier..should i try to reinstall dnsmasq? And if so do i uninstall NM. i believe my client is talking to the server but is not let in?

---

### Post by newb85 on 2013-06-18
What happens if you
```
 ping 8.8.8.8 
```

(Ctrl+C to stop it.)

---

### Post by trilju2005 on 2013-06-18
i can ping on server but not client-windows7.  i checked sys/logs and the
 dhcp gave 2 leases on eth1, 
dhcpinform on eth1, 
dhcpack to the lease ip via eth1, 
eth1 no ipv6

---

