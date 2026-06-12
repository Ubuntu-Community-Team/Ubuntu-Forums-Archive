---
title: "Where did my network drive go?"
date: 2014-02-13
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-02-13
I have recently updated from 10.04 to 12.04 and have not done a backup since (embarrassed grin). Went to do a back up to the NAS box and it isn't showing up on the network.

I ran ifconfig -a but not there either.

"Connection Information" doesn't show it.

Checked that NAS ethernet cable is tight in its connector on the box and at the switch.

How do I find it without either the device name or the IP address?

---

### Post by Odyssey1942 on 2014-02-13
Just checked again, and it is there. Maybe needs a few minutes to reveal itself?

But is there a command that shows all the devices on the lan?

The wheels turn slowly (often), but I just got thinking about mounting? a network storage device. Is it mounted per se? If not how do you find it in the terminal so that you can figure out how to script a backup that outputs to the NAS?

---

### Post by Dennis N on 2014-02-13
> But is there a command that shows all the devices on the lan?

Look here:

[http://itsfoss.com/how-to-find-what-devices-are-connected-to-network-in-ubuntu/](http://itsfoss.com/how-to-find-what-devices-are-connected-to-network-in-ubuntu/)

---

### Post by Odyssey1942 on 2014-02-13
Here were the results from my nmap scan:

> sudo nmap -sP 192.168.0.0/24

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2014-02-13 20:34 CST
Nmap scan report for router.xyz.com (192.168.0.1)
Host is up (0.00033s latency).

Nmap scan report for 192.168.0.101
Host is up (0.026s latency).

Nmap scan report for 192.168.0.102
Host is up (0.0065s latency).

Nmap scan report for 192.168.0.103
Host is up (0.0044s latency).

Nmap scan report for 192.168.0.105
Host is up (0.00037s latency).

Nmap scan report for 192.168.0.106
Host is up (0.0059s latency).

Nmap scan report for 192.168.0.107
Host is up (0.0013s latency).

Nmap scan report for 192.168.0.108
Host is up (0.0032s latency).

Nmap scan report for 192.168.0.110
Host is up.

Nmap scan report for 192.168.0.115
Host is up (0.00027s latency).

Nmap scan report for 192.168.0.131
Host is up (0.00014s latency).

Nmap scan report for 192.168.0.132
Host is up (0.0025s latency).

Nmap scan report for 192.168.0.134
Host is up (0.098s latency).

Nmap scan report for 192.168.0.142
Host is up (0.00020s latency).

Nmap scan report for 192.168.0.145
Host is up (0.079s latency).

Nmap scan report for 192.168.0.148
Host is up (0.000081s latency).

Nmap scan report for 192.168.0.152
Host is up (0.081s latency).

Nmap done: 256 IP addresses (17 hosts up) scanned in 4.41 seconds

How do I fit an IP# from the above to all of those except the desktops? 

Any suggestions, including how to identify the NAS (which is how this started out)?. E.g. if I turn it off, should it disappear from the list?

Now really confused

---

### Post by Odyssey1942 on 2014-02-14
geprt, thanks for reposting Dennis's post, although unsure why, since that post (nmap how-to) is how I got the data I posted.

Comparing the two, in each line of the referenced result, the device is identified (i.e., router [192.168.1.1], computer [192.168.1.91 as identified by ifconfig], and android device). ```
user@user-notebook:~$ sudo nmap -sP 192.168.1.0/24
Starting Nmap 5.21 ( http://nmap.org ) at 2012-09-01 21:59 CEST

Nmap scan report for neufbox (192.168.1.1)
Host is up (0.012s latency).
MAC Address: E0:A1:D5:72:5A:5C (Unknown)
Nmap scan report for takshak-bambi (192.168.1.91)
Host is up.
Nmap scan report for android-95b23f67te05e1c8 (192.168.1.93)
Host is up (0.36s latency).
```

As is evident in my list above, the only device identified in my lan is the router.

So the next step for me is to identify all of the listed devices, and that is my question. How to do that?

---

