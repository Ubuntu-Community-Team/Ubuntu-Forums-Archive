---
title: "Bash help: &quot;nmcli con status&quot; no longer working"
date: 2015-06-10
forum: Programming Talk
---

### Post by bathynomusBLUE on 2015-06-10
I did not write this original script, but I am trying to modify the new script to kill Firefox if VPN fails. The new script appears to be working. However, would there be a better option to use, instead of "nmcli con show --active"? Thanks

Old Script:
```
#! /bin/bash

while true
do
   connection="MyNetworkConnection"
   vpn_connection="myvpn"
   run_interval="10"


   active_connection=$(nmcli con status | grep "${connection}")
   active_vpn=$(nmcli con status | grep "${vpn_connection}")


   if [ "${active_connection}" -a ! "${active_vpn}" ];
   then
      killall firefox
   fi


   sleep $run_interval
done
```

New Script:
```
#! /bin/bash


while true
do
   connection="EUROPE"
   vpn_connection="europevpn"	# must be lowercase, here and in NetworkManager
   run_interval="10"		# how many seconds between checks


   active_connection=$(nmcli con show --active | grep "${connection}")
   active_vpn=$(nmcli con show --active | grep "${vpn_connection}")


   if [ "${active_connection}" -a ! "${active_vpn}" ];
   then
      killall firefox		# what to do, upon check failure of VPN
   fi


   sleep $run_interval
done
```

nmcli 0.9.8 old commands Vs nmcli 0.9.10 counterpart
[https://wiki.gnome.org/Projects/NetworkManager/nmcli](https://wiki.gnome.org/Projects/NetworkManager/nmcli)

---

