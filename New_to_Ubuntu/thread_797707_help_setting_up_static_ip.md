---
title: "help setting up static ip"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by onearmedpanda on 2008-05-17
i need to set up a static ip address so that i can forward my ports for deluge, the bittorrent client.

i found this little snippet that i have to add to /etc/network/interfaces

# The primary network interface
auto eth0
iface eth0 inet static
        address 
        netmask 
        network 
        broadcast 
        gateway 

and i can find my address, netmask, and broadcast using ifconfig but i don't know how to find the network or gateway
can anyone help me find those two things?
thanks in advance

---

### Post by Baelus on 2008-05-17
The gateway address is the one your router uses. If you don't use a router then it's the address of the machine that's sharing its internet connection. 

Usually if you're using the 192.168.x.x address range the ip of your router is probably 192.168.1.1.

I find I don't need to give a network or broadcast address to get things going. These are the settings for eth0 that I use:

```
auto eth0
iface eth0 inet static
address 10.0.0.5
netmask 255.255.255.0
gateway 10.0.0.2
```

If you have a complex network setup you might need to use additional settings.

Good luck!

- B

---

