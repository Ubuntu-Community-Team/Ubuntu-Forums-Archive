---
title: "Setting up network interfaces to promiscuous mode"
date: 2012-10-03
forum: New to Ubuntu
---

### Post by termvrl on 2012-10-03
Hi all,
i have two network interface, eth0 and eth1.
eth0 set to static and eth1 set to promiscuous mode.
my problem is, eth1 is down and i need to set to promiscuous mode again after rebooting. 
how can i make it auto during boot up. 

Thanks!

---

### Post by NikTh on 2012-10-03
Hi , 

any command that needs sudo (admin privileges) you can set it up in rc.local file to executed during OS boot.

Place the command **before _exit 0_**  (no need of sudo in the begin) 

Save the file and reboot. 

Thanks

---

### Post by termvrl on 2012-10-03
Hi NikTh,

i put two line in rc.local
ifconfig eth1 up
ifconfig eth1 promisc
and reboot. 
done. 
:p
Thanks for ur help!!!

---

