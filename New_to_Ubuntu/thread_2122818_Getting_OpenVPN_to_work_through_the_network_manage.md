---
title: "Getting OpenVPN to work through the network manager gui"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by djpemberton on 2013-03-06
I have installed network-manager-openvpn and I am trying to connect through my VPN using the networkmanager gui in Kubuntu 12.10. I click "manage connections", click on the "VPN" tab, click "import" and select my .conf file. Though I don't know exactly how it should look, it seems to load all of the information and key locations correctly. It indicates that it is connected, but I have no internet connection at all at that point. Is there something I am missing?

Thanks

---

### Post by djpemberton on 2013-03-06
The owner of all the files is "root" and they are all in /etc/openvpn. Would any of those facts make any difference?

---

### Post by SeijiSensei on 2013-03-06
First, can you ping the other end of the tunnel?  If you don't know what it is, type the command "ifconfig" and look for the entry for tun0 or tap0.  You'll see the IP address of the tunnel on your end, and the IP address of the other end of the tunnel as "P-t-P" ("point-to-point").  The entry should look like this:
```
inet addr:10.1.1.20  P-t-P:10.1.1.1  Mask:255.255.255.255
```
This indicates my local machine has address 10.1.1.20 and connects over the tunnel to 10.1.1.1.  So to test the tunnel, I'd run "ping 10.1.1.1".  If it times out, the tunnel is not configured correctly.

If ping works, then run the command "route -n" and see where the default gateway points (the route for Destination 0.0.0.0).  Does it use the other end of the tunnel?

Preserving Internet connectivity on a machine using a VPN [can be tricky]("http://ubuntuforums.org/showthread.php?t=1625637&p=10135990&viewfull=1#post10135990").  You have to maintain a direct connection to the Internet so the tunnel can be constructed, but then send all the appropriate traffic over the tunnel.

---

