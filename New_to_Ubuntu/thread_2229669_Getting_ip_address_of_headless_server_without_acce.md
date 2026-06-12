---
title: "Getting ip address of headless server without access to dhcp server log files"
date: 2014-06-14
forum: New to Ubuntu
---

### Post by maurits2 on 2014-06-14
I installed linux on my server and want to run it in a headless configuration.
I need to know the ip address of this machine without having access to the client list of the DHCP server.
Call this network LAN1

What I can do is log into the server on a different LAN, say LAN2, using ssh from another machine. This LAN is not connected to the network mentioned earlier.
I thought of making some script that would automatically report ip addresses to my other computer computer but can't get it working. Any ideas?

---

### Post by pqwoerituytrueiwoq on 2014-06-14
why not make a static ip address? you know since you can ssh into it
edit: [FONT=courier new]/etc/network/interfaces[/FONT]
add this (change addresses as necessary)
```
iface eth0 inet static
address 10.0.0.25
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
gateway 10.0.0.1
dns-nameservers 8.8.8.8 8.8.4.4
```

---

### Post by maurits2 on 2014-06-15
I can't make a static IP address because when I connect the machine to the other LAN then the DHCP server assigns some fixed IP address to the computer.

---

### Post by steeldriver on 2014-06-15
I'm having trouble understanding what you are asking - are you saying you have a server that is going to be deployed on some arbitrary DHCP LAN segment over which you have no control, and you want it to phone home its DHCP-assigned IP once it gets deployed?

---

### Post by pqwoerituytrueiwoq on 2014-06-15
run this on your linux box, this will find the IPv4 address on every system on your network
```
sudo nmap -sP $(echo $(hostname -I)|cut -d'.' -f 1-3).*
```

---

### Post by maurits2 on 2014-06-16
Thanks for the replies, let me try to rephrase the question so that it is more understandable.
If have a private LAN over which I have full control. I have no trouble finding the ip address of my linux computer and can log in to the computer using ssh. But this linux machine has to run on the university network, so that my fellow students can access it. But the problem is that once I have connected it to the university network, I can no longer find it's IP Address because I do not have access to the router of the university network. I do however have an other computer on the university network, of which I know the IP address. My plan was to write some kind of program that runs automatically on the linux machine after boot that somehow tells my  other computer what its ip-address is. For example, I could write a program that tries to connect to my other computer using ssh after boot and then check the log file of that other computer to see the ip address of the clients that tried to connect to my computer. This however seemed to be somewhat of a difficult solution. Is my problem clearer now?

---

### Post by pqwoerituytrueiwoq on 2014-06-16
can you using the systems .local address?
you can get this address by running
echo $(cat /etc/hostname).local

---

### Post by bab1 on 2014-06-16
> **maurits2 said:**
> Thanks for the replies, let me try to rephrase the question so that it is more understandable.
If have a private LAN over which I have full control. I have no trouble finding the ip address of my linux computer and can log in to the computer using ssh. But this linux machine has to run on the university network, so that my fellow students can access it. But the problem is that once I have connected it to the university network, I can no longer find it's IP Address because I do not have access to the router of the university network. I do however have an other computer on the university network, of which I know the IP address. My plan was to write some kind of program that runs automatically on the linux machine after boot that somehow tells my  other computer what its ip-address is. For example, I could write a program that tries to connect to my other computer using ssh after boot and then check the log file of that other computer to see the ip address of the clients that tried to connect to my computer. This however seemed to be somewhat of a difficult solution. Is my problem clearer now?
The machine with the unknown address can use this line to find its own IP address ```
/sbin/ifconfig $1 | grep "inet addr" |grep -v 127| awk -F: '{print $2}' | awk '{print $1}'

```  You can write a script to pipe it to a file or an environment variable.  Write your program on that machine to use the data to tell the known machine what the variable (IP address) is.  It you run the script every time at boot up you will always know the current IP address of that machine.

---

### Post by MartyBuntu on 2014-06-16
It would be much easier to assign the machine a static IP, and then asking the network administrator to reserve that address for you...

...because they know you're running a server on their network...

...*right?*

---

### Post by maurits2 on 2014-06-22
thanks, that's what I was looking for.

---

