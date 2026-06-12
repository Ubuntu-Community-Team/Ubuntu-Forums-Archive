---
title: "How do i start to make a small script to do automation task"
date: 2009-07-13
forum: Programming Talk
---

### Post by brad_pitt on 2009-07-13
Hi All,

I am using Ubuntu 9.04.As you all know in ubuntu 9.04 when internet network connection is disconnected a splash message will be displayed on the upper right hand corner of the screen saying that "**Disconnected - A network connection is disconnected and now you are offline.**"

I want to run a small script whenever my internet connection is diconnected.

Please tell me how do i proceed to accomplish this task.

I know only JAVA language but can learn any launguage if i have to learn..

Please suggest me on how to start off with this task

Regards
Brad

---

### Post by Martin Witte on 2009-07-13
you can run a shell script like 
```
#!/bin/bash
while true; do
	alive=$(ping -q -c1 192.168.2.1 > /dev/null 2>&1)
	if [[ alive -ne 0 ]]; then
		echo run a command
	else
		echo Nothing to do
	fi
	sleep 5
done
```

to see if a network is active, relace the ip address with that of e.g. the ip address of your switch

---

### Post by brad_pitt on 2009-07-13
> **Martin Witte said:**
> 
```

    alive=$(ping -q -c1 192.168.2.1 > /dev/null 2>&1)
```to see if a network is active, relace the ip address with that of e.g. the ip address of your switch

I use DHCP network to connect to internet..so i dont think the above said test condition will be useful..Can i use the following commands?

**netsat** or **ifup** or **ifdown**

Thanks Martin for your time and suggestion :p

Regards
Brad

---

### Post by sanemanmad on 2009-07-13
That script would work if you substitute the IP for the IP of your gw or assign a variable to get your IP.

```
#!/bin/bash
while true; do
        IP=$(/sbin/ifconfig eth0|grep inet|awk {'print $2'}|cut -d: -f2)
	alive=$(ping -q -c1 $IP > /dev/null 2>&1)
        sleep 30
	if [[ alive -ne 0 ]]; then
		echo run a command
	else
		echo Nothing to do
	fi
	sleep 5
done

```

---

### Post by Martin Witte on 2009-07-13
> **sanemanmad said:**
> That script would work if you substitute the IP for the IP of your gw

You can find the address of your gateway with the *route* command, on my machine:
```
martin@toshibap200:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 ath0

```

the gateways address is the second column in the row where flag is set to *UG*, use a command like 
```
martin@toshibap200:~$ route -n|awk '$4 ~ /'UG'/ {print $2}'
192.168.2.1

```
to capture the address

---

### Post by sanemanmad on 2009-07-13
That works too, my DG is a linux server so I use the interface to get that information (assuming the script is ran from the server), your method works best in a standard environment on the client (which i believe the op is looking for anyway)

---

