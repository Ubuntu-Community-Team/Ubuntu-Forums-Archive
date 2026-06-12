---
title: "Unable to set static ip for port forwarding ubuntu 16.04"
date: 2017-04-07
forum: New to Ubuntu
---

### Post by mr-mister on 2017-04-07
Hi, i want to use transmission but it appears that my port is closed. Transmission says that i have to port forwards but i'm stuck trying to set the static ip. I did:
sudo nano /etc/network/interfaces

and typed: 
auto enp1s0
iface enp1s0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.255

when i do sudo ifup enp1s0 it shows:
RTNETLINK answers: Invalid argument
Failed to bring up enp1s0.

But an ubuntu message tells me that a connection was stablished, which confuses me. Appreciate help, tell me if you need for info

---

### Post by papibe on 2017-04-07
Hi mr-mister.

A couple of observations:

If this is a Desktop edition, use the GUI 'Networks' (part of NetworkManager) to setup the static IP.

You can't use 192.168.0.255 as a gateway since it is the broadcast address. May be you meant 192.168.0.254?

Make sure 192.168.0 it is your actual LAN's range.

Make sure  192.168.0.10 is outside the DHCP range of your router (or DHCP server).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Impavidus on 2017-04-08
Sounds more complicated than I had to do to enable Transmission. It was just a matter of accessing the router (the router's manual gave the IP address to access it via the web browser) and changing some settings there to forward a particular port to a particular host, using the host name of my computer. On my router it was all quite straightforward. No need to change any settings on my computer.

---

### Post by mr-mister on 2017-04-08
Oh, so your saying it's not necessary to set up an static ip.? Nonetheless, i tried that. My router is Cisco DPC3825 when i try to log in with the default user: cusadmin and pass: password  for cisco DPC3825 it says it's invalid. I've tried with all the other alternatives for cisco routers but none of then work.

---

### Post by mr-mister on 2017-04-08
So, i tried to set it up with gui networks with the gateway connection corrected (i  don't know how to make sure i have the right range for Lan and dhcp) but  nothing happened. But, i tried it again configuring /etc/networks/interfaces and a connection was established, but know i can't even load the router page.
i'm putting 192.168.0.1 ¿is that a right number? When i didn't have the ethernet connection on i could acces the page just fine (just coundn't enter with default user and pass)

---

### Post by SeijiSensei on 2017-04-08
I use Transmission without having made any changes to my routers.  I actually have two routers, one from the ISP and my own (an Archer C7), and didn't change either of them.  I can download and seed just fine.

---

### Post by mr-mister on 2017-04-08
The thing is mine didnt download, and apparently sometimes the port is closed for transmission. According to Ubuntu's transmission wiki the solution for opening the port is to port forward, which is my final goal ([https://help.ubuntu.com/community/TransmissionHowTo](https://help.ubuntu.com/community/TransmissionHowTo) section port forward)

---

