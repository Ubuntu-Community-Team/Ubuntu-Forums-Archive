---
title: "How to connect destop and laptop wirelessly at home"
date: 2014-09-07
forum: New to Ubuntu
---

### Post by cecilieaux on 2014-09-07
I feel very much a newbie in the area of home networking. I have tried a number of things and nothing works so I sense I need to go to square zero and pretend nothing happened. I appreciate advice, links to tutorials, anything really because I'm really, really lost.

I have a desktop running Ubuntu 14.04 LTS, a laptop running Linux Mint 17 Qiana. 

I've been using the desktop as a dual-boot with Windows for some time, but after the death of XP, I'm de-Windowizing. Besides, I like Linux better. The laptop is new and almost empty. There's the rub. I want to tap my documents on the desktop from my laptop so I can take music, pictures, some projects I'mn working on, etc. It's not a matter of needing to collaborate; it's just a matter of "I need file X that is in the desktop." (It may become the reverse, but not yet.)

Also, my gf has a Windows 7 laptop, which it would be nice to access from time to time, to send or receive files. Nothing fancy. This is much lower priority, however.

We all access the Internet through a router, to which we are connected wirelessly. I'm assuming, we can connect these three computers wirelessly as well. (Via Windows I was able to set up temporary shares; Win 7 would forget the link and it would be a pain.)

As I said, sharing with the Windows machine is low priority, the main thing is getting my own files. I've been using Dropbox a little, but I have a small, free account and I have an external drive for backup purposes and a USB stick. All a sneaker-net setup, really.

Ideas, anyone? Speak as if to a 2-year-old, please. I feel like one.

C

---

### Post by nerdtron on 2014-09-07
Transfer between two linux computers on the same network? Easy using SFTP!
1. Be sure you can ping each computer, back and forth.
2. Install openssh-server on both PC.
```
sudo apt-get install openssh-server
```
Just accept the defaults and don't provide a pass-phrase on the last step
3. Confirm that ssh is running on both PC.
```
ps -ef | grep ssh
```

Now on either PC, open the file manager and enter the following on the location bar.
```
sftp://user@ip_address
```

Where user is the username on the remote computer and ip_address is the ip of the remote computer.
Post here if you have problems.

---

### Post by cecilieaux on 2014-09-07
> **nerdtron said:**
> 
1. Be sure you can ping each computer, back and forth.


Ping?

---

### Post by cecilieaux on 2014-09-07
> **nerdtron said:**
> 
1. Be sure you can ping each computer, back and forth.

OK, you mean this, right?

> 
ping 192.168.1.104
PING 192.168.1.104 (192.168.1.104) 56(84) bytes of data.
64 bytes from 192.168.1.104: icmp_seq=1 ttl=64 time=102 ms
64 bytes from 192.168.1.104: icmp_seq=2 ttl=64 time=133 ms
64 bytes from 192.168.1.104: icmp_seq=3 ttl=64 time=2.62 ms
64 bytes from 192.168.1.104: icmp_seq=4 ttl=64 time=1.02 ms
64 bytes from 192.168.1.104: icmp_seq=5 ttl=64 time=1.14 ms
64 bytes from 192.168.1.104: icmp_seq=6 ttl=64 time=1.02 ms
64 bytes from 192.168.1.104: icmp_seq=7 ttl=64 time=1.07 ms
^C
--- 192.168.1.104 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6008ms
rtt min/avg/max/mdev = 1.021/34.805/133.778/53.496 ms


So I assume they can ping. or "see" each other.

---

### Post by cecilieaux on 2014-09-07
The connection worked!

The copying of files seems very slow. Will watch and report later. This is almost solved!

---

### Post by gifford on 2014-09-07
If this is a secure home network, you could use NitroShare. You cannot only send files but directories as well. It is slick, easy and surprisingly fast.

---

### Post by cecilieaux on 2014-09-07
> **gifford said:**
> If this is a secure home network, you could use NitroShare. You cannot only send files but directories as well. It is slick, easy and surprisingly fast.

Define "secure." (How do I know it is secure?)

Otherwise, yes, I would like a faster share. But at least this beats the sneakernet.

---

### Post by EuclideanCoffee on 2014-09-07
> **cecilieaux said:**
> Define "secure." (How do I know it is secure?)

Otherwise, yes, I would like a faster share. But at least this beats the sneakernet.

You would have a network connected by cables rather than Wifi. Cables are more secure than Wifi. It's all in tiers of security. ;)

---

