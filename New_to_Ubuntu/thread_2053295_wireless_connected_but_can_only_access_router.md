---
title: "wireless connected but can only access router"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by pkj5ue on 2012-09-05
New thread opened [ubuntuforums.org/showthread.php?p=12227222]("http://ubuntuforums.org/ubuntuforums.org/showthread.php?p=12227222") 
I have a new lenovo g580 laptop. The problem is with its wireless. Wireless Connection is defined as DHCP. /etc/network/interfaces is only about lo:
```

auto lo
iface lo inet loopback

```With this I can connect to my router with address 192.168.0.1 alright. But try pinging 8.8.8.8 and it gives network is unreachable. Various people across forums suggested changing God knows how many files.. but nothing changed. route -n showed:
```

Destination Gateway  Genmask ..... Iface
169.254.0.0  0.0.0.0   255.255.0.0   eth1
192.168.0.0 0.0.0.0  255.255.255.0  eth1

```ifconfig eth1 shows more or less(i m typing in :(  ):
```

inet addr: 192.168.0.108 Bcast 192.168.0.255 Mask 255.255.255.0

```So I figured adding a gateway might help so..
```

sudo route add default gw 192.168.0.1

```and it worked! But now I need to do it everytime i restart... 
If I change the /etc/network/interfaces file, it leads to a message after restart that network is not managed!! so what can I do.
I am a total newbie. I am from the windows world. And been brought out here with the assurance that you don't need to restart the system everytime you brainfart. So an explanation of what's going on here and how things work(just a little) will embolden me to continue. Thanks.

---

### Post by shreepads on 2012-09-05
The router should supply that as part of the DHCP request - response and should get automatically configured on Ubuntu....

Are you using a static or dynamic config?

Assuming its dynamic, can you check the DHCP setup on the router?

What do you see when in the TCP/IP settings when you double click on the networking icon in the top menu bar (before applying your fix)?

---

### Post by pkj5ue on 2012-09-05
Must be dynamic. Connection settings for wireless, ipv4 is set to DHCP automatic. No routes are specified. Right clicking the network icon->connection information shows no difference before and after the fix!

---

### Post by pkj5ue on 2012-09-05
And the ubuntu kernel is apparently 32 bit. found by uname -m shows i686. I don't know how the installation was messed up.

---

### Post by shreepads on 2012-09-05
Checked the DHCP setup on the router?

---

### Post by pkj5ue on 2012-09-05
DHCP router must be alright. The same machine logs on without problem on dual boot in win7. Besides there are others who are logged on without problem(including one with ubuntu). Router has dd-wrt. Any specific parameters?

---

### Post by nativehound on 2012-09-05
Check your router for the ip, dns and gw info
and then manual add it to the NM wireless connection ipv 4 settings.
reboot

---

### Post by pkj5ue on 2012-09-05
>>manual add it to the NM wireless connection.
I understand you mean editing wireless connection, changing to manual from dhcp auto, etc. I believe, it makes ip static. And it wasn't working. 
And no reboots please. That is why i m here. If things work as like windows where every whim, fancy and sundry needs one, then i m better off there as i know my way around in windows. 
Regards

---

### Post by shreepads on 2012-09-06
If the Router setup is fine then probably something wrong with the DHCP client daemon on your machine. Any errors showing up in the syslogs?

My suggestion would be to include more details (which Ubuntu version you're running, /etc/resolv.conf and /var/lib/dhcpc/dhcpcd*.info content and the network topology) and post on the Networking forum...

---

