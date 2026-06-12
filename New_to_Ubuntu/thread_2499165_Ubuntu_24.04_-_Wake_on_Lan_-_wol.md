---
title: "Ubuntu 24.04 - Wake on Lan - wol"
date: 2024-07-16
forum: New to Ubuntu
---

### Post by oisik on 2024-07-16
Hi all,
I dont know why, but my search doesnt show my any hits regarding wol/ wake on lan.

I am pretty new to Ubuntu, but i could flee finaly from windows :)
Now I would like to enable wol.

I set a static IP on my router, where i can force wol.
on my Ubuntu 24.04 i installed ethtool and activated wol by using "sudo ethtool -s <nic> wol g"

When i shut down the computer i can wake up my server using the gui from my router.
but, in a unspecific time, wake on lan does not work and i discoverd, that my wol on my nic is disabled "wol d".

How can i set this parameter permanent?
I found some documents which ask to edit the /etc/network/interfaces file. BUT, i dont have that file and if i try to create it by "sudo echo > inferfaces" it says no permission.

can please some expert can help :) Thank you

---

### Post by ActionParsnip on 2024-07-16
Should help
[https://pimylifeup.com/ubuntu-enable-wake-on-lan/](https://pimylifeup.com/ubuntu-enable-wake-on-lan/)

---

### Post by oisik on 2024-07-16
Hi,

thanks for the quick response. I try it, but the nic is after reboot still not in the wol status.
it seems like the service is not running at the startup. 

xxx@xxx:~$ sudo systemctl status wakeonlan.service 
&#9675; wakeonlan.service - Enable Wake On Lan
     Loaded: loaded (/usr/lib/systemd/system/wakeonlan.service; enabled; preset: enabled)
     Active: inactive (dead) since Tue 2024-07-16 17:23:56 CEST; 3min 5s ago
   Main PID: 1126 (code=exited, status=0/SUCCESS)
        CPU: 5ms


Jul 16 17:23:56 xxx systemd[1]: Starting wakeonlan.service - Enable Wake On Lan...
Jul 16 17:23:56 xxx systemd[1]: wakeonlan.service: Deactivated successfully.
Jul 16 17:23:56 xxx systemd[1]: Finished wakeonlan.service - Enable Wake On Lan.

ethtool:
Supports Wake-on: pumbg
	Wake-on: d
	Link detected: yes

---

### Post by oisik on 2024-07-16
Solved:
i created a yaml file in /etc/netplan/50.wol.yaml
include this:

network:
    ethernets:
        enp3s0:
            dhcp4: true
            wakeonlan: true
    version: 2

---

### Post by ActionParsnip on 2024-07-18
Please mark as solved

---

