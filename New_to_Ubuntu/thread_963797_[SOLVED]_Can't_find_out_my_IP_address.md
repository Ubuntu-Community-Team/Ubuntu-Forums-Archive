---
title: "[SOLVED] Can't find out my IP address"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by dapissarenko on 2008-10-30
Hello!

I've installed ubuntu server 8.04 on my computer and now want to connect to it from my Windows machine.

In order to do so, I need to know the IP address of the ubuntu machine.

When I enter ifconfig, I get only an "inet6" address, but no normal IP address.

How can I find out the IP address of my ubuntu machine?

Thanks in advance

Dmitri

---

### Post by tuxxy on 2008-10-30
Heres [a guide]("http://ubuntuforums.org/showthread.php?t=526176")

---

### Post by Kevbert on 2008-10-30
Try [http://www.ip-adress.com/](http://www.ip-adress.com/)

---

### Post by earthpigg on 2008-10-30
> **tuxxy said:**
> Heres [a guide]("http://ubuntuforums.org/showthread.php?t=526176")

if he just wants to find his ip addres....

wouldn't [http://whatismyipaddress.com/]("http://whatismyipaddress.com/") be just fine? :)

---

### Post by aeiah on 2008-10-30
if it isnt showing in ifconfig its because you havent set one. if you want a static one then set it either with network manager or by changing the /etc/network/interfaces file. if you want it to be assigned by dhcp then connect to a dhcp server and that will assign an ip address for you (your dhcp server is probably your modem or router)

---

### Post by aeiah on 2008-10-30
the 'whats my ip' websites will only work if he is trying to connect the two machines over the internet. its my understanding that he's trying to get them networked together through a local area network.

---

### Post by adamogardner on 2008-10-30
could you/he look at the metadata of an email? either sent or recieved?

---

### Post by Sarmacid on 2008-10-30
If it doesn't show in ipconfig, it's because you don't have an ip address. To set one
```
sudo ifconfig <interface> <ip> netmask <netmask>
```

Usually interface is eth0 and you have to set the other parameters, here's an example
```
sudo ifconfig eth0 192.168.100.1 netmask 255.255.255.0
```

---

### Post by dapissarenko on 2008-10-30
Hello!

Thanks all for your answers!

> **aeiah said:**
> if you want a static one then set it either with network manager or by changing the /etc/network/interfaces file. if you want it to be assigned by dhcp then connect to a dhcp server and that will assign an ip address for you (your dhcp server is probably your modem or router)

At the moment, all I need is to connect the ubuntu machine to the Windows machine over a network cable, not over the internet.

So, I think that a static IP address would be fine.

Best regards

Dmitri

---

### Post by dapissarenko on 2008-10-30
Hello!

Now I have assigned to my ubuntu machine the static IP address 10.0.0.1, but I still can't connect to it via ssh (cygwin).

I'm getting the message "No route to host" message.

Notes:

1) I can't ping the ubuntu machine from Windows.
2) I tried to use putty on Windows, but it also fails to establish a connection to the ubuntu machine.
3) ssh client and server is installed on the ubuntu machine. When I run "ssh localhost" on the ubuntu machine, I get the login screen and hence I assume that ssh client and server are working.
4) I opened port 22 on my windows machine (windows firewall).

I appreciate any hint about how to solve this problem.

Thanks in advance

Dmitri Pissarenko

---

### Post by Sarmacid on 2008-10-31
> **dapissarenko said:**
> 
4) I opened port 22 on my windows machine (windows firewall).


No need to do that, port 22 should only be opened in the ssh host. Now are you sure you configured both machines with the right ips and masks? Sounds to me like that's the problem. And also, how are you connecting? crossover cable?

---

### Post by alphacrucis2 on 2008-10-31
> **dapissarenko said:**
> Hello!

Now I have assigned to my ubuntu machine the static IP address 10.0.0.1, but I still can't connect to it via ssh (cygwin).

I'm getting the message "No route to host" message.

Notes:

1) I can't ping the ubuntu machine from Windows.
2) I tried to use putty on Windows, but it also fails to establish a connection to the ubuntu machine.
3) ssh client and server is installed on the ubuntu machine. When I run "ssh localhost" on the ubuntu machine, I get the login screen and hence I assume that ssh client and server are working.
4) I opened port 22 on my windows machine (windows firewall).

I appreciate any hint about how to solve this problem.

Thanks in advance

Dmitri Pissarenko

The address you assign will need to be in the same subnet as the Windows machine. What is the ip address and subnet mask on the windows pc?

---

### Post by dapissarenko on 2008-11-04
Hello!

Thanks all for the help!

I solved the problem by connecting my computers via a network switch (and not directly).

Best regards

Dmitri

---

### Post by Ron G on 2008-11-04
The simplest way I did it was to use firestarter firewall. In the panel it will display the "destination" of hits. Thats you. Your Ip address is right there.

---

