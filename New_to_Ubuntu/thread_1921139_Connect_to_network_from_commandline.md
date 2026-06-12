---
title: "Connect to network from commandline"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by andyzammy on 2012-02-06
Hi,

I have server addition running in a VM, but I'm not sure how to connect it to the network (can't ping google). Please could someone tell me the minimum amount of command linage to get it going? I looked for documentation, but either there is none or its well hidden.

Thanks

---

### Post by Bodsda on 2012-02-06
> **andyzammy said:**
> Hi,

I have server addition running in a VM, but I'm not sure how to connect it to the network (can't ping google). Please could someone tell me the minimum amount of command linage to get it going? I looked for documentation, but either there is none or its well hidden.

Thanks

Have you enabled networking through Virtualbox?

Please paste the output of
```

ifconfig

``````

cat /etc/resolv.conf

``````

ping -c 3 www.google.co.uk

```Thanks,
Bodsda

---

### Post by andyzammy on 2012-02-06
> **Bodsda said:**
> Have you enabled networking through Virtualbox?

Please paste the output of
```

ifconfig

``````

cat /etc/resolv.conf

``````

ping -c 3 www.google.co.uk

```Thanks,
Bodsda

As I'm in a virtual machine, grabbing text will be a pain. I'm pretty sure all I did to get to this point was to type "ifconfig eth0 up" and "dhclient". AFAIK this is all I need? Using NAT (default) network setting in VirtualBox - proven to work (got Debian guest pinging google with a gui term)

[IMG]http://ubuntuforums.org/picture.php?albumid=2461&pictureid=8337[/IMG]

---

### Post by andyzammy on 2012-02-07
bump, still a mystery

---

### Post by lkraemer on 2012-02-07
Perhaps this will help....................

```

sudo /etc/init.d/networking start

```
**OR**
```

sudo /etc/init.d/networking restart

```

**Manual Choice:**
If you know the routers essid and the correct <interface>,
shown by using ifconfig & iwconfig ie. wlan0, ath0, etc....
replace that as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```

example......for Airlink and wlan0
sudo iwconfig wlan0 essid "Airlink"

This assumes you have the Wifi enabled by Hardware Switch or Keyboard
keystrokes that enable it (ALT F2 on some Computers).  Also it assumes you
have the Wifi Firmware installed on your *nix system for your Wifi Hardware.
You may need to connect via Ethernet and Enable the Hardware Drivers to get
the Firmware.  Or, just download the Firmware from the Internet.

Try the Ping test to see if you can Ping [www.Yahoo.com](www.Yahoo.com)
```

ping -c 3 www.yahoo.com

```
If you can't ping it isn't working............
 
lk

---

