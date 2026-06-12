---
title: "Lost internet connection after installing Static IP address"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by bernardfernando on 2013-10-30
Please help me I am an absolute beginner to UBUNTU: I lost internet connection I had when I installed a Static IP address.  I installed a Static IP address as I could not see the network activity arrows normally see at the top right hand corner of the screen.  I managed to install the Static IP address, but without internet I am crippled now.  Grateful if you could help me.  My Machine is a Dell Studio. I do not run Windows at all. Internet connection hardwired ethenet
Many thanks.

---

### Post by papibe on 2013-10-30
Hi bernardfernando. Welcome to the forum ):P

How did you set the static IP?
Did you use the NetworkManager (GUI tool)?
Did you edit config files (/etc/network/interfaces)?

Regards.

---

### Post by bernardfernando on 2013-10-30
Hi Papibe
Thanks for this swift reply.  I appreciate it.  I used /etc/network/interfaces.

Kind Regards
Bernard

---

### Post by papibe on 2013-10-30
Thanks.

Did you uninstall NetworkManager?

If not, there may a conflict there. I'd recommend restoring the file as it was, and using the GUI to set the static IP

/etc/network/interfaces should look like this:
```
auto lo
iface lo inet loopback
```
Then using the network graphic tool that is available on the top bar:
[LIST]
[*]Click Edit Connections
[*]Select either wired or wireless depending on what you are using.
[*]Select the interface (there's probably just one there).
[*]Press 'Edit'.
[*]Go to the 'IPv4 settings' tab.
[*]Select 'Manual' and then fill the addresses there.
[/LIST]

Once you are ready, save/close all windows related to networking and (just to be double sure) restart Network Manager:
```
sudo service network-manager restart
```
Let us know how it goes and if you need help with the addresses.
Regards.

---

### Post by bernardfernando on 2013-10-30
Hi Papibe

When I ran
sudo lshw -class network
I noticed *-network DISABLED

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)

Under configuring an Interface
sudo ip link set dev eth0 down
sudo dhclient eth0

Then 
sudo service smbd reload

<all this was done without understanding what was happening. I am impressed by the support of Ubuntu community and the docs for help on the internet.>

I thank you again for your help.

Now it works.

Kind Regards

---

