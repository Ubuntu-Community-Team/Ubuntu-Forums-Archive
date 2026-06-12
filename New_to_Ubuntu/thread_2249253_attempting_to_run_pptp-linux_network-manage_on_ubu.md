---
title: "attempting to run pptp-linux network-manage on ubuntu 14.04 LTS unity DE"
date: 2014-10-20
forum: New to Ubuntu
---

### Post by gnowair on 2014-10-20
i ran command via terminal "sudo apt-get install pptp-linux network-manager-pptp" then set up VPN via Network Connections,  and a miami adress as my proxy on VPN connection , but always get "the VPN connection 'ProXPN' failed because the service failed to start".

any advise? or any more info needed from me to help solve this?
many thanks!

---

### Post by gnowair on 2014-10-21
anything? anyone?

---

### Post by sandyd on 2014-10-21
Please try the solution offered in [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1175897](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1175897)

Before that, please post the output of
```

apt-get -s purge network-manager-pptp network-manager-pptp-gnome ppp pppconfig pppoeconf pptp-linux
```
Just want to make sure that nothing essential will be removed by the purge command before you run it :)

---

