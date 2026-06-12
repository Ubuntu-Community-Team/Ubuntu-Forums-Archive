---
title: "OpenVPN duplicate services causing conflicts, how to delete a service?"
date: 2017-11-11
forum: New to Ubuntu
---

### Post by maxburn on 2017-11-11
16.04. Somehow I added a second openvpn service that I can't disable or get rid of. Present state is VPN clients will not connect after a reboot. I have to SSH into the server and 
```

sudo systemctl stop openvpn@server
sudo systemctl start openvpn@server
```
It's like it isn't starting the right config file at first????


If I leave both services enabled I get TWO vtun# connections in ifconfig and it causes all sorts of problems like remote SSH won't work. right now my services look like this: 


```

$ sudo systemctl list-unit-files | grep vpn
openvpn.service                            disabled
openvpn@.service                           enabled 

```


Even though I have what I "think" is the right one enabled it won't work after I reboot until I stop/start the service.
I think somehow the errors I get when disabling the one I don't want are involved. Something is crossed up here, how do I get rid of the service I don't want?


```

$ sudo systemctl disable openvpn
Synchronizing state of openvpn.service with SysV init with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install disable openvpn
insserv: warning: current start runlevel(s) (empty) of script `openvpn' overrides LSB defaults (2 3 4 5).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `openvpn' overrides LSB defaults (0 1 6).
insserv: warning: current start runlevel(s) (empty) of script `openvpn' overrides LSB defaults (2 3 4 5).
insserv: warning: current stop runlevel(s) (0 1 2 3 4 5 6) of script `openvpn' overrides LSB defaults (0 1 6).
```

---

