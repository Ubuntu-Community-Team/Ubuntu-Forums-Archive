---
title: "starting the internet????"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by sankz.21 on 2008-09-03
hey im absolutely new to ubuntu.......n i have juss installed dis 8.04 LTS Desktop Edition........n i wanna enable internet on it.......i have a cable net...........can ne1 help me......how to go about......IN DETAIL.......plz it will be a good help!!!!!!.........

---

### Post by paul_mcl on 2008-09-03
cable net? how your modem is connected? if via ethernet, use (under root)
    ifconfig eth0 xxx.xxx.xxx.xxx netmask 255.255.255.0 up
    route add default gw yyy.yyy.yyy.yyy
    echo "nameserver zzz.zzz.zzz.zzz" > /etc/resolv.conf
where
xxx.xxx.xxx.xxx - your ip,
yyy.yyy.yyy.yyy - your gateway,
zzz.zzz.zzz.zzz - your dns.

---

### Post by sankz.21 on 2008-09-03
thanx paul i'll try that..........ne more suggestions...

---

