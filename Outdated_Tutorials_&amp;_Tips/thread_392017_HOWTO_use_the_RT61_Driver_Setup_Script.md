---
title: "HOWTO: use the RT61 Driver Setup Script"
date: 2007-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Frak on 2007-03-24
If your an edgy user, and have used edgy on an RT61 Wireless chipset, your aware that the driver is broken in the edgy install. Thus having to compile the driver yourself.

Most users would not compile the driver themselves (duh), so after I ranted for about a month about it, then I actually went and tried to compile, after I compiled the driver (successfully for once), I figured out all the steps and made an installation script.

To use this script, extract it anywhere and double click on "configure.sh", then click "run in terminal", assuming your using the Gnome Desktop Environment.
Or go to the terminal and navigate to the directory where the extracted folder is located,
For most it would be
```
cd ~/Desktop/RT61_Setup
sudo ./configure
```

The only other thing needed for the user to do is to create a startup script, that will tell Ubuntu where and how to connect to a/the wireless network.

These steps as stated below are slightly modified from an original post, that I have no idea where I got it from.

```
sudo gedit /etc/init.d/rt61up
```
Then enter the following lines.

```
#!/bin/sh
echo "Bringing up ra0"
# obtain an IP address from a DHCP server
dhclient ra0
sudo modprobe rt61
sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=<my wep key>
sudo iwpriv ra0 set SSID=<my essid>
dhclient ra0


# alternately, you can uncomment the following line to set a static IP address
# ifconfig ra0 {IP ADDRESS} up
# if you uncomment the line above, make sure to comment line #4
```

[center]--------------------DO NOT OPEN YOUR NETWORK MONITOR, IT WILL LOCKUP ON STARTUP--------------------[/center]
If you use WPAPSK
```
cd /etc/Wireless/RT61STA
sudo vi -b rt61sta.dat
```
And edit it to work. (as I only use WEP, I can't be much help with WPA or unsecured)

Hope this works :guitar:

---

### Post by lime4x4 on 2007-03-31
i just tried your driver script on a fresh install of edgy for like the 50th time..lol
i have the wmp54g v4.1 card.
This script didn't work for me.
if i run iwconfig this is the output

l0  no wireless extensions

ra0   no wireless extensions

eth0  no wireless extensions

sit0   no wireless extensions


I don't know what else to try anymore....lol
i've tried atleast 20 different how to's all with the same result no wireless connection

---

### Post by sblanzio on 2007-04-01
I had to face few troubles like downloading new kernel headers with another computer and installing them, but this script almost worked.

my final problem is that the connection doesn't completely go up on boot. I can see with iwconfig that the ra0 is up and connected to the SSID but i cannot open any ip connection (web...).

So i have to go in my:
/etc/init.d/
folder and submit
./rt61up

if i follow these steps the connection goes completely up and i can surf....

how can i make it available from boot?

This is my file configuration:
```

/etc/init.d$ ls -l rt*
-rwxr-xr-x 1 root root 307 2007-04-01 14:49 rt61up

```

```

/etc/rcS.d$ ls -l S33*
lrwxrwxrwx 1 root root 16 2007-04-01 14:21 S33rt61up -> ../init.d/rt61up

```

why doesn't it start at boot? thanks!
sblanzio

---

### Post by nlogax on 2007-05-06
> **sblanzio said:**
> 
if i follow these steps the connection goes completely up and i can surf....

how can i make it available from boot?

This is my file configuration:
```

/etc/init.d$ ls -l rt*
-rwxr-xr-x 1 root root 307 2007-04-01 14:49 rt61up

```

```

/etc/rcS.d$ ls -l S33*
lrwxrwxrwx 1 root root 16 2007-04-01 14:21 S33rt61up -> ../init.d/rt61up

```

why doesn't it start at boot? thanks!
sblanzio

Perhaps you should try giving it a higher number - on my system at least, rcS/S40networking is networking...  It's probably best to put re-link rt61up to /etc/rcS/S41rt61up or something.

---

### Post by Frak on 2007-05-06
I'll try that

---

