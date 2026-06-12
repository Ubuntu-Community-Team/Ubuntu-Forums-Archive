---
title: "Script to monitor network interface card utilization?"
date: 2013-06-03
forum: Programming Talk
---

### Post by termvrl on 2013-06-03
Hi All,

I want to ask, how can i write a script that can check current nic load, for e.g incoming traffic. 
How did we measure (if it use any parameter) the nic load, "heavy" load or "low" load.

Thanks!

---

### Post by aromo on 2013-06-03
I would run a crontab job that extracts the network usage (e.g. ifconfig eth0|grep "RX bytes"), say every minute and append it to a history file, then do the math to calculate the average usage between the last and the current sample.

---

### Post by sanderj on 2013-06-03
If nethogs and ntop don't do what you want, and you're able to do some scripting, I would go for inspecting /proc/net/dev

A hint:

```
sander@hapee:~$ cat /proc/net/dev | grep wlan0 | cut -c9- | awk '{ print $1 " " $9 }'  ; sleep 10; cat /proc/net/dev | grep wlan0 | cut -c9- | awk '{ print $1 " " $9 }'
2468014158 67043735
2524567250 68250702
sander@hapee:~$
```

HTH

---

### Post by ofnuts on 2013-06-03
> **sanderj said:**
> If nethogs and ntop don't do what you want, and you're able to do some scripting, I would go for inspecting /proc/net/dev

A hint:

```
sander@hapee:~$ cat /proc/net/dev | grep wlan0 | cut -c9- | awk '{ print $1 " " $9 }'  ; sleep 10; cat /proc/net/dev | grep wlan0 | cut -c9- | awk '{ print $1 " " $9 }'
2468014158 67043735
2524567250 68250702
sander@hapee:~$
```

HTH
My own little "netrate" script:

```

#!/bin/bash

dev=$1
[[ -z $1 ]] && dev=$(grep -o "eth." /proc/net/dev | head -1)

function getcount
{
    echo $(grep $dev /proc/net/dev | tr ':' ' ' | tr -s ' ' | cut -d ' ' -f 3,11)
}
    
current=($(getcount))
[[ -z $current ]] && echo "No network device \"$dev\"" && exit 1

printf "%10s %4s %4s \n" Device Recv Send

for i in $(seq 1000)
do
    sleep 1
    new=($(getcount))
    recvdiff=$(( ${new[0]} - ${current[0]} ))
    senddiff=$(( ${new[1]} - ${current[1]} ))
    recvdiff=$(( $recvdiff / 1024 ))
    senddiff=$(( $senddiff / 1024 ))
    printf "%10s %4d %4d\r" $dev $recvdiff $senddiff
    current=(${new
[*]})
done

```

---

### Post by sanderj on 2013-06-03
> **ofnuts said:**
> My own little "netrate" script:

```

#!/bin/bash

dev=$1
[[ -z $1 ]] && dev=$(grep -o "eth." /proc/net/dev | head -1)

function getcount
{
    echo $(grep $dev /proc/net/dev | tr ':' ' ' | tr -s ' ' | cut -d ' ' -f 3,11)
}
    
current=($(getcount))
[[ -z $current ]] && echo "No network device \"$dev\"" && exit 1

printf "%10s %4s %4s \n" Device Recv Send

for i in $(seq 1000)
do
    sleep 1
    new=($(getcount))
    recvdiff=$(( ${new[0]} - ${current[0]} ))
    senddiff=$(( ${new[1]} - ${current[1]} ))
    recvdiff=$(( $recvdiff / 1024 ))
    senddiff=$(( $senddiff / 1024 ))
    printf "%10s %4d %4d\r" $dev $recvdiff $senddiff
    current=(${new
[*]})
done

```

Ooohhhhh ... beautiful! And I like the "\r" very much ... clever!

---

### Post by ofnuts on 2013-06-03
> **sanderj said:**
> Ooohhhhh ... beautiful! And I like the "\r" very much ... clever!
A very old trick...

---

### Post by termvrl on 2013-06-04
Hi All,
Thanks for your reply. What i want to do is, i want to check  if the incoming traffic is heavy or not. If the incoming traffic is too  heavy, it will return 1, and if not, it will return 0.

I try to use ofnuts script, but the result is show like this:-[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1382218")
root@ubuntu:/home/Sh# ./Nic.sh
    Device Recv Send
      eth0    0    0

Thanks.

---

### Post by ofnuts on 2013-06-04
All the script does is get the appropriate line from /proc/net/dev, extract the sent and received by counts at one-second intervals, and compute the difference (and display it divided by 1024). If you just want the received count:
```

received=$(grep eth1 /proc/net/dev | awk '{print $2}')

```

Do it once, sleep one sec (or shorter), get the new value, compute the difference and act if that is above some trigger value.

---

### Post by sanderj on 2013-06-04
> **termvrl said:**
> Hi All,
Thanks for your reply. What i want to do is, i want to check  if the incoming traffic is heavy or not. If the incoming traffic is too  heavy, it will return 1, and if not, it will return 0.

I try to use ofnuts script, but the result is show like this:-[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1382218")
root@ubuntu:/home/Sh# ./Nic.sh
    Device Recv Send
      eth0    0    0

Thanks.

Questions:
1) are you connected via fixed ethernet, or wireless? If wireless, use "./Nic.sh wlan0"
2) are you doing any traffic? Cause traffic with "wget  [http://ftp.belnet.be/ubuntu.com/ubuntu/releases/precise/ubuntu-12.04.2-desktop-i386.iso](http://ftp.belnet.be/ubuntu.com/ubuntu/releases/precise/ubuntu-12.04.2-desktop-i386.iso) -O /dev/null "

HTH

---

### Post by termvrl on 2013-06-04
Hi thanks for your tips.

After generate some traffic, i able to see the "Recv".

Thanks again!

---

