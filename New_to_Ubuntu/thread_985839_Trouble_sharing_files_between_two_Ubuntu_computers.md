---
title: "Trouble sharing files between two Ubuntu computers"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Glace on 2008-11-18
My main computer has two NICs; one to the internet and one linked to another ubuntu computer.

I can share files between them when they are both running windows, 
so it's not a hardware problem.

Using auto DHCP on everything makes the second computer say no network connection.

However if I manually put in these settings to the second computer;
```
Address 192.168.1.110
Netmask 255.255.255.0
Gateway 192.168.1.102 (IP of main computer)
DNS     192.168.0.1
```
the second computer says there is a connection, but it fails to ping 192.168.1.102 and the main computer cannot ping 192.168.110 either.

---

### Post by mapes12 on 2008-11-18
Here's a couple of suggestions that may help:

[https://help.ubuntu.com/7.10/internet/C/networking-shares.html](https://help.ubuntu.com/7.10/internet/C/networking-shares.html)

I use openssh to enable my 2 Ubuntu machines to see each other, move files around and the like. Very easy to use. To get it running I followed the thread posted by SpaceTeddy from here: [http://ubuntuforums.org/showthread.php?t=793308](http://ubuntuforums.org/showthread.php?t=793308) 

Although the thread says "wired" this solution also works over wireless LAN

Here's another one to enable windoze and Ubuntu boxes to talk to each other, but I haven't used it: [http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)

---

### Post by superprash2003 on 2008-11-18
install firestarter and enable Internet Connection sharing, this is a pretty easy way..

---

### Post by anubhavrocks on 2008-11-18
> **Glace said:**
> My main computer has two NICs; one to the internet and one linked to another ubuntu computer.

I can share files between them when they are both running windows, 
so it's not a hardware problem.

Using auto DHCP on everything makes the second computer say no network connection.

However if I manually put in these settings to the second computer;
```
Address 192.168.1.110
Netmask 255.255.255.0
Gateway 192.168.1.102 (IP of main computer)
DNS     192.168.0.1
```
the second computer says there is a connection, but it fails to ping 192.168.1.102 and the main computer cannot ping 192.168.110 either.

On the main computer with two NICs enable IP forwarding something like this:
```

echo 1|sudo tee /proc/sys/net/ipv4/ip_forward
```

---

### Post by Glace on 2008-11-19
I fixed it.

The IP of the second NIC card in the main PC was the same as the IP of the first NIC card, (even though it was on auto settings), and it turns out your not suppose to do that. (i know I'm a noob)

Once that was fixed file sharing was easy following the guides.

As for ICS, that's not what the topic was suppose to be about, but that works if i boot the main computer in vista which is good enough for me :).


Thanks for the replies.

---

