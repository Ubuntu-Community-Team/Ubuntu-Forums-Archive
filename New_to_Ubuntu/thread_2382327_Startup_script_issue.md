---
title: "Startup script issue"
date: 2018-01-11
forum: New to Ubuntu
---

### Post by landisar on 2018-01-11
Hello fine assorted men and women of the Ubuntu community. I'm very new to Linux so please be patient with me and I will do my level best to be as clear as possible.

My line of work requires me to work with Lubuntu based machines (14.04, Trusty Tahr). These machines experience an issue where hardware is not initialized correctly during boot after a power loss. That is an issue for our manufacturer and I do not want advice on how to solve it.

I have devised a workaround which is where I do need help. The workaround looks something like this. I have a reference file that contains either a 0 or a 1. There is a script related to that reference file. When the script runs, if it detects a 0 in the reference file, it will change the 0 to a 1 and reboot. If it detects a 1 in the reference file, it will change the 1 to a 0 and it will not reboot. This is intended to be a startup script so that when the machine boots, it will essentially reboot one more time but will not get locked in a cycle of booting infinitely.

The script seems to work perfectly fine and performs just as I'd like it to. My problem has developed in getting this script to run properly at startup. The script itself is in /etc/init.d/ and I've run the command "update-rc.d script_name.sh start 95 5 . stop 5 0 1 6 ." to run it at startup. I've also made the script executable (+x) and given it suitable permissions (2733).

My issue is that after linking my script to rc.d, it runs beautifully the first time but not after that unless invoked manually. You can take a look at the full code below-

### BEGIN INIT INFO
#Provides: script_name
#Required-Start: $remote_fs $syslog
#Required-Stop: $remote_fs $syslog
#Default-Start: 5
#Default-Stop: 0 1 6
#Short-Description: Start daemon at boot time
#Description: adds boot cycle to first boot to avoid screen freeze
### END INIT INFO

#!/bin/bash
screenset=$(awk 'NR==1' /home/iva/Desktop/bootreference);
if [ $screenset == 0 ];then
sed "s/0/1/g" -i /home/iva/Desktop/bootreference
reboot
else
sed "s/1/0/g" -i /home/iva/Desktop/bootreference
fi
unset screenset
count=$(awk 'NR==1' /home/iva/Desktop/bootcount);
sed "s/$count/$count+1/g" -i /home/iva/Desktop/bootcount


Any tips or advice are enormously appreciated.

---

### Post by steeldriver on 2018-01-11
What's the purpose of the final `sed` command (the one that's outside the conditional)? 

FYI `$count+1` won't undergo evaluation so it will keep replacing 0 with literal 0 + 1 I think

---

### Post by landisar on 2018-01-11
The final sed is really just a counter. For one of our machines in the field, the idea is that I can count the "+1's" and average over time to get an idea of how often the machine loses power.

---

