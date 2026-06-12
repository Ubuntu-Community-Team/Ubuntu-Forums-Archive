---
title: "pxe booting one virtual box from another on different computers"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by Cluster Penguin on 2012-06-11
Hello everyone,

My set up is a follows:

1.  One one computer I have Ubuntu 10.10 running a virtalbox of Ubuntu 8.04  which is set as a DHCP server.
2. Another computer with Ubuntu 10.10 running a virtualbox  set up to pxe boot.
3. both computer are using a cat5 cable ruining through a switch box that had no dhcp server. 

My problem is that I can not get the two virtual boxes to see each other. I know that the 8.04 server works properly because if I run the second virtual box on the same computer they see each other and then the second one will pxe boot. 
[(VBox <-->VBox) same computer]

But once it's on another computer virtualbox sees nothing. 
Does anyone know what I can do to get the second box to pxe boot while it is on another computer other than the server?

---

### Post by mosaic2s on 2012-06-12
what is the network settings for the vboxed os?

---

### Post by Cheesemill on 2012-06-12
This should work if you are using bridged networks.

---

### Post by Cluster Penguin on 2012-06-12
@mosaic2s @Cheesemill

I have two Os(s) in a vbox One is a server and the other is a client.
On the server box and client box I have both set to use the bridge adapter on eth0.
(See photos vbox-server and vbox-client.)

One thing I should mention. The server box Is only set to distribute it's pxe boot to specific mac addressees. And the two real computes I am running the vbox on are not listed in the mac address list. Could this be the reason the second box can't see the first? That the second vbox's real computer has no address?  I was thinking that Vbox-server would skip the real computer an just go right to the vbox-client.

See graphical image of set up.

---

### Post by mosaic2s on 2012-06-15
ip address should be configured in host os.

in the sense, there must be a list of allowable IP addresses that your network has. so the vbox os must have the IP addresses in IPV4 settings.

---

### Post by Cluster Penguin on 2012-06-16
Thanks @Mosaic2s,

I'm using our wifi router to give the real computers there ip address and then I did some sub-netting on the virtual box server and it actually worked! The client virtual box got an ip address from the server virtual box! Now the only problem I have is that the tftp stalls out. I just have to google what to do in order to get the tftp to sub-net properly (I think.) Any advice is welcomed. 

Thanks again.

---

