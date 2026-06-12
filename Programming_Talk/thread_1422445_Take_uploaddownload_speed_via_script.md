---
title: "Take upload/download speed via script?"
date: 2010-03-05
forum: Programming Talk
---

### Post by hakermania on 2010-03-05
Is possible to take the upload/download speed with the help of a script file?
something like:
```

#!/bin/sh
upspeed=Ihavenoidea
downspeed=Ihavenoideaasswell
echo "Your up speed is $Ihavenoidea 
and your down speed is $Ihavnoideaaswell !"
exit
```
Suggest me things I can do in order to have the current upload/download speed.
If it is needed, my interface is wlan0
Txh in advance!:popcorn:

---

### Post by Zugzwang on 2010-03-07
These speed values are dependent on a lot of issues, so there's no simple answer. For the downloading part, what you might want to try out is running "LANG=C; wget -O /tmp/stuff http://www.somefastserver.com/someFile.zip" adding some scripting commands to decompose the output as wget returns the download speed encountered. However, I have no clue about the scripting part.

---

### Post by matchett808 on 2010-03-07
there are ways to do this.....Conky manages to grab it from somewhere yet I have no idea where.....

---

### Post by hakermania on 2011-11-24
Way too old thread, but seeing my subscription I came up with this, so anyone who is digging up, here's a solution:
```

#!/bin/bash

# This shell script shows the network speed, both received and transmitted.

# Usage: net_speed.sh interface
#   e.g: net_speed.sh eth0

# Global variables
interface=$1
if [[ $interface == "" ]]; then
   echo "You didn't specify interface...
Example: $0 wlan0"
   exit
fi
received_bytes=""
old_received_bytes=""
transmitted_bytes=""
old_transmitted_bytes=""

# This function parses /proc/net/dev file searching for a line containing $interface data.
# Within that line, the first and ninth numbers after ':' are respectively the received and transmited bytes.
get_bytes()
{
    line=$(cat /proc/net/dev | grep $interface | cut -d ':' -f 2 | awk '{print "received_bytes="$1, "transmitted_bytes="$9}')
    eval $line
}

# Function which calculates the speed using actual and old byte number.
# Speed is shown in KByte per second when greater or equal than 1 KByte per second.
# This function should be called each second.
get_velocity()
{
    value=$1
    old_value=$2

    let vel=$value-$old_value
    let velKB=$vel/1024
    if [ $velKB != 0 ];
    then
 echo -n "$velKB KB/s";
    else
 echo -n "$vel B/s";
    fi
}

# Gets initial values.
get_bytes
old_received_bytes=$received_bytes
old_transmitted_bytes=$transmitted_bytes

# Shows a message and waits for one second.
echo "Starting...";
sleep 1;
echo "";

# Main loop. It will repeat forever.
while true;
do

    # Get new transmitted and received byte number values.
    get_bytes

    # Calculates speeds.
    vel_recv=$(get_velocity $received_bytes $old_received_bytes)
    vel_trans=$(get_velocity $transmitted_bytes $old_transmitted_bytes)

    # Shows results in the console.
    echo -en "$interface DOWN:$vel_recv\tUP:$vel_trans\r"

    # Update old values to perform new calculations.
    old_received_bytes=$received_bytes
    old_transmitted_bytes=$transmitted_bytes

    # Waits one second.
    sleep 1;

done

```

---

