---
title: "check the internet status.."
date: 2011-12-10
forum: New to Ubuntu
---

### Post by jpjohnj on 2011-12-10
i plan to write a program that will detect the internet connection as quick.

just consider ,

ping with google. as per my knowledge google server had a fast response time.

is there any setting available in ping to increase the fast response time?

please guide me

---

### Post by mikewhatever on 2011-12-10
... I thought ping was there to measure the time, not to change it.

---

### Post by haqking on 2011-12-10
you cant change how fast another server responds to your communication.

Regardless of your internet connection speed

---

### Post by hakermania on 2011-12-10
'man ping' says:
-c count
              Stop  after  sending  count  ECHO_REQUEST packets. With deadline
              option, ping waits for count ECHO_REPLY packets, until the time&#8208;
              out expires.

So, you can set the count to '1', also, it says:
-W timeout
              Time to wait for a response, in seconds. The option affects only
              timeout in absense of any responses, otherwise  ping  waits  for
              two RTTs.
So, providing that google replies at about 80 ms:
```

alex@MaD-pc:~$ ping -c 1 google.com
PING google.com (173.194.66.147) 56(84) bytes of data.
64 bytes from www.google.com (173.194.66.147): icmp_req=1 ttl=48 time=75.1 ms

--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 75.189/75.189/75.189/0.000 ms

```
you can set the timeout to 2 secs.

Hint: In the end, it would be nice to have a zenity dialog poping up saying whether the internet connection is on or off.
I have such a script to my unity panel, also I get the pid of the zenity dialog and kill it after sleeping one second, too lazy to push the Ok button (8))

---

### Post by haqking on 2011-12-10
that doesnt increase the response time.

Though i am a little unclear on what the OP actually wants.

Regardless of internet connection speed (bandwidth) that wont change latency

---

### Post by hakermania on 2011-12-10
> **haqking said:**
> that doesnt increase the response time.

Though i am a little unclear on what the OP actually wants.
 			 			 			 		   		 		 		_*i plan to write a program that will detect the internet connection as quick.*_

The way I'm suggesting replies in 1 sec or less if I have internet access (depending on my modem's traffic caused by other PCs connected to it), in about 2 if I am connected to a modem but I don't have internet access, and in 0.5 secs if I'm not connected to a modem at all.

---

### Post by haqking on 2011-12-10
> **hakermania said:**
> _*i plan to write a program that will detect the internet connection as quick.*_

The way I'm suggesting replies in 1 sec or less if I have internet access (depending on my modem's traffic caused by other PCs connected to it), in about 2 if I am connected to a modem but I don't have internet access, and in 0.5 secs if I'm not connected to a modem at all.

mmm ok i am misreading it then, the OP says response time (this is latency) no matter what you do with ping you cannot change the latency. 

perhaps i havent had enough coffee yet.

no worries

cheers

---

