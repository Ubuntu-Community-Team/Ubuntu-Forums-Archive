---
title: "Wireless Ralink RT2860/D-Link 615 router problem"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by BRMan42 on 2012-06-06
Ok, I have a problem driving me crazy here. I have a D-link 615 router set up for my wireless internet connection. Nothing fancy, it's connected to the internet, and I connect my devices to that router.* I have 2 macs connected, 2 Iphones connected, and my windows 7 computer, all working fine. Just an SSID and a WPA/WPA2 password.

Now, on that same windows 7 computer, I have installed Ubuntu 12.04 LTS, and It finds my SSID, I connect to it, I get the "connection Established" message, but its JUST NOT WORKING. I cant access the net, I cant access the router (192.168.0.1).

The computer in question has a Ralink RT2860 network card (that works fine under Windows 7)

I can access my neighbours unencrypted wifi(I dont know what kind of router my neighbour has), and that works fine.

*There is only one special thing: My ISP requires the routers MAC address, So I've inputted that address on the router's settings.

I have tried doing this solution [http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

But I have no Idea what a "kernel" is , or where to find mine, so this sentence made no sense to me : "Attention: you need to replace the * with the actual directory name of your kernel, please check the folder name with Nautilus."

How the hell do I do that? I'm a complete linux newb, and have no idea how to use all this terminal stuff.

Anyway, I've tried all the usual stuff, unplugging everything and waiting etc to no avail.

Please, any help would be appreciated, but please be very specific. I have no idea how to "Check the directory name of my kernel", for example.

---

### Post by BRMan42 on 2012-07-13
bump, no takers on this?

---

### Post by steeldriver on 2012-07-13
I'm not familiar with the RT2860 - open a terminal window and paste in these commands,  let's see what detailed driver / firmware info they throw up

```
lspci -vnn | grep -A4 -e "\[0200\]" -e "\[0280\]"
```

and

```
lshw -c network
```

and

```
nm-tool
```

---

