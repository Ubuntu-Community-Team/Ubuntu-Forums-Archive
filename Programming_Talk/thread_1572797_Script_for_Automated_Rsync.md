---
title: "Script for Automated Rsync"
date: 2010-09-11
forum: Programming Talk
---

### Post by ductiletoaster on 2010-09-11
Simply put im writing a script to do an automated rsync. The Issues I am having is that i have the script setup to wake up the remote machine and then shut it down. however I wanted to also test to see if the machine was on before the wakeonlan cmd was given. adn if so to not Shutdown the machine when the rsync is done.

My issues how would i check the the remote machine to see if it was on and then run seperates commands based on the situation 

Example sudo code:
```

if remote machines is off {
    wakeonlan that machines
} else do nothing


```

My linux server has a mounted windows share. Could i just do something like 

if share is there then continue else break.....

---

### Post by ductiletoaster on 2010-09-11
Any body?

---

### Post by v1ad on 2010-09-11
ping ?

---

### Post by ductiletoaster on 2010-09-11
I guess im just a little lost on how i would write it out in a script

---

### Post by v1ad on 2010-09-11
did you start on the script? or are you asking for one.

people would probably help out more if they knew more info.

* did you start the script?
* if yes can you post the script minus any sensitive information?
* figure it out bit by bit and piece em together, then ask for help on specific parts.

---

### Post by ductiletoaster on 2010-09-12
No I am writing one on my own i just need to be able to turn off a windows machine remotely and i didn't know how. but i figured it out and I finished the script

```

#!/bin/bash
# Description: This script first wakes up the client machine and syncs the appropriate folders. 
# Finally the script shuts down both client and server.

# Default Variables
IP_ADDRESS="192.168.1.180"
MAC_ADDRESS="00:00:00:00:00:00"
MOUNT_SHARE="/mnt/windowshare"

ping -c3 $IP_ADDRESS
if [ $? -ne 0 ]; then
	wakeonlan $MAC_ADDRESS # Wakes Windows Client
	client_status=0 # Sets the computers status to was OFF
	sleep 120 # Waits 2 mins for the computer to boot
else
	client_status=1 # Sets the computers status to was ON
fi

sudo smbmount //$IP_ADDRESS/D$ $MOUNT_SHARE -o username=user,password=password # Mounts Windows Share

# Synchronizes All direcotries between both computers
rsync -ruz --delete --progress $MOUNT_SHARE/Development/* /home/user/Development/ 
#rsync -ruz --delete --progress $MOUNT_SHARE/Downloads/* /home/user/Downloads/ 
rsync -ruz --delete --progress $MOUNT_SHARE/Documents/* /home/user/Documents/ 
#rsync -ruz --delete --progress $MOUNT_SHARE/Music/* /home/user/Music/ 
#rsync -ruz --delete --progress $MOUNT_SHARE/Pictures/* /home/user/Pictures/ 
#rsync -ruz --delete --progress $MOUNT_SHARE/Videos/* /home/user/Videos/ 

sudo umount //$IP_ADDRESS/D$ # Unmounts Windows Share

if [ $client_status -eq 0 ]; then
	net rpc SHUTDOWN -I $IP_ADDRESS -U user%password # Shutsdown Windows Client
fi
# Shutsdown Linux Server
sudo halt

```

Now the problem I am having is that im trying to figure out how to have this run let say every monday on startup. Like a cron job but i need it to happen before any users login. But i only wanted it to happen once a week.... O and it needs root permissions

---

