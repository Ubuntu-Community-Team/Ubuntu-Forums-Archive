---
title: "bash script to test network connection - please help newbie"
date: 2009-09-20
forum: Programming Talk
---

### Post by shadow_boi on 2009-09-20
I want to test if my host can connect to any of the following 10 hosts (192.168.1.0 to 192.168.1.9)

I didnt know which command i should use, so i chose ping. (i wonder if i should use tracepath or sth else)

my code is the following:

```


#!/bin/bash
clear
firstPart="192.168.1"
maxNum="9"

for (( lastPart=0; lastPart<=$maxNum; lastPart++ ))
do
    ipAddr="$firstPart.$lastPart"

    if ping -c 1 -W 1 $ipAddr
    then
        echo "This comp can be connected."
    fi
done

```

The problem is on this line "ping -c 1 -W 1 $ipAddr"
It would take 10 seconds to check the network connection in the worse case. (if all hosts are not reachable from my host), which is so long.

So i am wondering, is possible to make it faster? or if there another approach to accomplish the same thing? Is that possible to use tracepath instead of ping?

Thanks in advance.

---

### Post by firen on 2009-09-20
ever gave snmp a try?

---

### Post by j7%&lt;RmUg on 2009-09-20
What if you put all the ip addresses you want to ping in a file called ip.list, then in the same directory put this in a bash script:
```

#!/bin/bash
for i in $(cat ip.list); do
ping ${i}
echo "This comp can be connected"

```

---

