---
title: "Internet connection drops."
date: 2008-05-29
forum: New to Ubuntu
---

### Post by ehelle on 2008-05-29
I'm new to Ubuntu and so far everything is going pretty well except for my network connection drops. I was using XP previously and had to enter in my DNS numbers to view webpages. So I have to do the same thing for ubuntu.

I went to network settings and selected DNS and typed in my DNS numbers and saved my location as home. 

Every so often while i'm browsing the pages won't load so i go back to network settings my location is blank, I set it to home and i can connect again. It's very annoying to have to do this repeatedly. If fact i had to do it just to post this  message. 

Right now my wired network is set to roaming mode enabled and if I try and change it to DHCP, Static, or Local I loose my connection completely.  I don't know what to do can someone help.

---

### Post by Kobalt on 2008-05-29
You should try to deactivate the roaming mode. Go into System > Admin. > Networking, select the interface you want to configure and click on Properties. Uncheck the roaming mode to be able to enter your personal config, save it and exit.

---

### Post by ehelle on 2008-05-29
I've tried every setting there is and they all drop my internet connection completely.

---

### Post by superprash2003 on 2008-05-29
to set DNS permanently follow this [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by StOoZ on 2008-05-29
can you post the output of:
> cat /etc/network/interfaces

---

### Post by Kobalt on 2008-05-29
Can you please post the output of the following command line:
```
cat /etc/network/interfaces
```

Make sure to remove any credentials that might appear before posting.

---

### Post by cmnorton on 2008-05-29
Which version and Ubuntu distro is this, 8.04 Ubuntu or something else?

Is the connection wired or wireless?

Is your connection relying on static information (ip/dns), or is your connection DHCP?

If you have a DHCP connection, something is truly wrong, because DNS would be set for you along with your IP address. The same would be true for XP. I have both a KUbuntu and XP system, and I never have to adjust DNS settings.

I would start with this file /etc/network/interfaces, staying for the moment in "roaming" mode. You'll need to save the current /etc/network/interfaces file by copying it to something you'll remember, like 

sudo cp /etc/network/interfaces /etc/network/interfaces.install

Then edit the file as shown below, and reboot.

-------------------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
----------------------------------------------

If it is wireless, can you try a wired connection for a while and see if that drops?

---

### Post by ehelle on 2008-05-29
I tried the permanent DNS and it still drops the connection.

---

### Post by ehelle on 2008-05-29
desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by Kobalt on 2008-05-29
This seems OK. In your case you should use a manual configuration, in order to set static DNS using DHCP. [See this]("https://help.ubuntu.com/community/StaticDnsWithDhcp") for more info on how to proceed.

---

### Post by ehelle on 2008-05-29
> **cmnorton said:**
> Which version and Ubuntu distro is this, 8.04 Ubuntu or something else?

Is the connection wired or wireless?

Is your connection relying on static information (ip/dns), or is your connection DHCP?


I am using Ubuntu 7.10. I am wired. I am DHCP but I can only view pages if I have my DNS numbers entered in the computer.  I will have an internet connection without the DNS numbers but I won't be able to view pages without them.

---

### Post by ehelle on 2008-05-29
> **Kobalt said:**
> This seems OK. In your case you should use a manual configuration, in order to set static DNS using DHCP. [See this]("https://help.ubuntu.com/community/StaticDnsWithDhcp") for more info on how to proceed.

This seems to have fixed the problem... Thanks.

---

### Post by Kobalt on 2008-05-29
You're welcome :)

---

