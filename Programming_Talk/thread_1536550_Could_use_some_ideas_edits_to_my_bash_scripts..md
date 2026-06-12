---
title: "Could use some ideas/ edits to my bash scripts."
date: 2010-07-22
forum: Programming Talk
---

### Post by d3vi1dog562 on 2010-07-22
Hello let me start off by saying THANK YOU to all of the advice and help i have received on this site over the last two years. That being said.... OK this is my first post here and my first attempt to help automate an aircrack-ng setup and exit with very little effort. It is a work in progress, however i feel Im going on  some "dangerous"  tangents and would like some help please! Anything and everything will be considered and appreciated! Please be gentle with me :P 
 
```
 
#KILL SCRIPT TO MAKE AIRCRACK EASIER TO RUN
# CREATED BY: TheD3vi1

#!/bin/sh
echo "Here we go!" 

#Kill any previous rfmon processes
sudo airmon-ng stop wlan0
sudo airmon-ng stop wlan1
sudo airmon-ng stop wlan2
sudo airmon-ng stop wlan3
sudo airmon-ng stop mon0 

## Killing the processes
sudo stop network-manager 
sudo killall NetworkManager
sudo killall avahi-daemon
sudo killall wpa_supplicant
sudo killall dhclient
sudo pkill -9 airodump-ng
#start rfmon mode
if ifconfig wlan2 up
then    
    sudo airmon-ng start wlan2
else    
    sudo airmon-ng start wlan0
fi
    sudo airmon-ng start wlan1

#Setting the rate of wireless card to 1Mb
sudo iwconfig wlan0 rate 1Mb
clear



# start scanning, save temp file, and shutdown.
sudo airodump-ng mon0 &
sleep 22

sudo killall airodump-ng

exit

```

---

### Post by d3vi1dog562 on 2010-07-22
Forgot the return back to managed mode script #-o 

```
 
# Reinitialization of nm-applet and wireless devices

#!/bin/sh
sudo clear
#kill and reinitiate processes
#sudo killall nm-applet
sudo killall NetworkManager
sudo wpa_supplicant
sudo avahi-daemon
sudo iwconfig wlan0 rate 54Mb
sudo airmon-ng stop mon0 
sudo airmon-ng stop wlan0
#restart nm-applet---pain in the *** process....
#nm-applet
sudo NetworkManager


#Cleaning up and exiting script

echo """
Internet should be working........
Exiting program in
3......
2......
1......

""" & 
sleep 1 
sudo clear
exit

```

---

