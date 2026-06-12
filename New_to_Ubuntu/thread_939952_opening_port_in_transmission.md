---
title: "opening port in transmission"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by recycledhippy on 2008-10-06
I have tried searching for this problem but nothing seems to work with me. I am trying to open the port 51413 for transmission, I have gone into my modem(westell 2200) no router here just a dsl modem, and forward that port number. But when I run Transmission it still says that port is closed. I cant seem to figure out why. any one have any ideas? Please help. Thanks

---

### Post by Titan8990 on 2008-10-06
Just curious, is "Transmission" the name of a program you are attempting to use?

---

### Post by gandaran on 2008-10-06
have you installed any firewall like firestarter?

---

### Post by recycledhippy on 2008-10-06
yep it's for bit torrent

---

### Post by recycledhippy on 2008-10-06
nope no firewall

---

### Post by tjwoosta on 2008-10-06
i usually use this website if i have doubts that a port is being forwarded properly
[http://www.canyouseeme.org/]("http://www.canyouseeme.org/")

by the sounds of it you have done everything the right way

just be sure to double check the port numbers and double check the ip address that you are forwarding the ports to

(if you are unsure of your machines ip address do this to find out)
```
ifconfig
```

---

### Post by Titan8990 on 2008-10-06
You should not need to forward any ports. The only time you should need to forward a port is for hosting a server. I have seen it asked for by bittorrent clients but with ISPs closely watching uploads these days I would be careful with opening up bittorrent ports in order to upload.

Also, a modem does nothing other the modulates/demodulates. If you have multiple devices plugged in to the modem and can forward ports on it then it is also a router (if it could not forward ports then it might just be a switch).

---

### Post by gandaran on 2008-10-06
well if no firewall then all the ports should be open!
try installing this gufw firewall [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)
then setup transmission in the programs tab like this [http://img67.imageshack.us/my.php?image=example2pq6.png](http://img67.imageshack.us/my.php?image=example2pq6.png)
__________________

---

### Post by Titan8990 on 2008-10-06
With the default IPtables rules being the following:


Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    



He should not have any reason to change the default policy to get bittorrent to work.

---

### Post by mkvnmtr on 2008-10-06
I don't know if this will help you or not. I always had to port forward on my Mac OS. When I tried on Ubuntu I got my maximum speed on most every torrent without doing anything. Transmission even says the port is closed. Try just using it and see if your speeds are ok.

---

### Post by recycledhippy on 2008-10-07
sorry I havent got back to you guys, I had to go to work. I've had to do port forwarding when using windows so I'm pretty sure I have the dsl modem set up right, but I do not remember having to do anything with th IP address. Only when I had a router hooked up I had to do a static IP. but not when using only the modem.

---

### Post by recycledhippy on 2008-10-07
the canyouseeme site said the port is closed(51413) but I know
 I have it opened

---

### Post by recycledhippy on 2008-10-07
I just found out what was wrong. When I went to enable the port forwarding on the modems page it asks if you want to host service. I must have clicked on cancel instead of start. did that and now port is open. Thanks to all that tried to help

---

### Post by Titan8990 on 2008-10-07
<ignore> Post solved.

---

