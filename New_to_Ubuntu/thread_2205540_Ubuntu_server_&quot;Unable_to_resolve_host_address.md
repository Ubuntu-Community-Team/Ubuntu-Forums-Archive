---
title: "Ubuntu server &quot;Unable to resolve host address&quot; problem"
date: 2014-02-14
forum: New to Ubuntu
---

### Post by david_brown on 2014-02-14
Hi, grateful for some help here. 

Complete newbie to ubuntu server. I'm trying to recycle my old PC as a server and simply want it to run a media server and backup for the home network. So far I've been following youtube tutorials and managed to install ubuntu server to a small hard disk. All the installation went fine including it going online to check and get updates. I've also managed to create a couple of test shared files that other pc's on the network can see and write to. I've also installed putty and can log into the server and use the terminal window.

My next goal is to install webmin to administer the server, add a big disk for storage etc. When I get to the stage where it wants to go online and find the webmin program I get the error "resolving (insert web address) failed: Temporary failure in name resolution. wget: unable to resolve host address 'some web address'

I've tried to resolve this but as a newbie I got stuck very quickly. I've tried to ping some addresses on another thread and I've tried to ping my router. I'm not sure if this is working or not. I type ping 192.168.1.1 in and get a load of lines 64 bytes from 192.168.1.1 icmp_req(numbers increase every line) ttl=64 time =0.401ms. It keeps adding line after line and the only way I seem to have of stopping this is to reboot.

Where do I go from here? It's a steep learning curve but worth persevering with I think. Many thanks.

---

### Post by Impavidus on 2014-02-14
Ping keeps running until killed. Try hitting control-C.

---

### Post by david_brown on 2014-02-14
Thanks. Pinging the router then hitting control c gives me 7 packets transmitted, 7 packets recieved, 0% packet loss, time 5999ms rtt min/avg/max/mdev 0.375/0.432/0.751/0.130ms
Similar figures when I ping my PC on the same router. pinging 8.8.8.8 gives me 5 packets transmitted 5 packets recieved 0% paxket loss time 4003ms.

So am I thinking that ping is working? What's the next step please?

---

### Post by david_brown on 2014-02-14
Been having a poke around the forum and found this post [http://ubuntuforums.org/showthread.php?t=770801](http://ubuntuforums.org/showthread.php?t=770801) 

I typed /ect/hosts and got the following:- > 

root@ubuntu:/home/david# ect/hosts
bash: ect/hosts: No such file or directory
root@ubuntu:/home/david#




I'm wondering if this helps?

---

### Post by steeldriver on 2014-02-14
Can you post the output of 

```
cat /etc/network/interfaces
```

please

---

### Post by david_brown on 2014-02-14
Hi,

I get the following:- 

```
root@ubuntu:/home/david# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.1.100
 netmask 255.255.255.0
 network 192.168.0.0
 broadcast 192.168.1.255
 gateway 192.168.1.1
root@ubuntu:/home/david#
```

---

### Post by Iowan on 2014-02-14
Well, that network configuration isn't gonna work... 
The third octet is different, so either the netmask or the network needs to change (actually, the network definition isn't strictly necessary)
What *appears* to be the fix would be to make it:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.[COLOR="#FF0000"]1[/COLOR].0
broadcast 192.168.1.255
gateway 192.168.1.1
 
```
Might not fix all the problems...
Probably just a typo - if the ping results from post #1 are accurate.
You're probably gonna need a nameserver definition somewhere...

---

### Post by david_brown on 2014-02-14
OK, thanks. How do I edit the file please?

---

### Post by Iowan on 2014-02-14
> **david_brown said:**
> OK, thanks. How do I edit the file please?
```
sudo nano /etc/network/interfaces
```
Here is a similar thread:
[http://ubuntuforums.org/showthread.php?t=1985170](http://ubuntuforums.org/showthread.php?t=1985170)

---

### Post by david_brown on 2014-02-14
Thanks for the similar thread - that solved it by adding the [COLOR=#000000][I]dns-nameservers 8.8.8.8 192.168.1.1 line and changing the other digit as above. No time to try to get further with it as it's late, but I will sleep better having moved on a step! Many thanks once again

[/I][/COLOR]

---

### Post by Iowan on 2014-02-14
Congrats on getting it fixed. Feel free to mark this thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").
A new problem will justify a new thread.

---

