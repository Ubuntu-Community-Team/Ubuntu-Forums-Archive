---
title: "Setting up Static IP address with wifi (WEP) via terminal - 13.10"
date: 2013-11-24
forum: New to Ubuntu
---

### Post by wayne.polatkan on 2013-11-24
Hi there. I'm setting up a server in order to learn how to use linux, I'm using an old laptop and right now trying to set up a static ip address through wifi, and my router uses WEP. Unfortunately I've been working at this for about 8 hours today, the main forum posts I've been looking at were: [http://ubuntuforums.org/showthread.php?t=2182135](http://ubuntuforums.org/showthread.php?t=2182135); [http://www.unixli.com/q/answers-how-to-set-a-static-ip-in-ubuntu-16413.html](http://www.unixli.com/q/answers-how-to-set-a-static-ip-in-ubuntu-16413.html).

My issue is every time I reboot I have no connectivity (although funny enough my router says it can talk to my machine just fine). I've been able to assign a static ip through the Network Manager. But I think it's more important to learn to do a task through the terminal which is where I am right now.

I start by opening the terminal and entering:

```
>sudo nano /etc/network/interfaces
```

which gives me:

```
auto lo
iface lo inet loopback
```

so I add the lines:

```
auto wlan0
iface wlan0 inet static[INDENT]address 192.168.1.111
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1
wireless-key PASSWORD
wireless-essid SSID[/INDENT]

```

At first I tried restarting the interfaces file by typing:

```
>sudo /etc/init.d/networking restart
```

But that's been unsuccessful, giving me the following:

```
ERROR: Calling a sysvinit script on a system using upstart isn't supported. Please use the 'service' command instead
```

I have no clue what that means, and haven't been able to find anything about it, so I've been rebooting the machine after every edit to interfaces. Later I tried checking the resolve.conf file through:

```
cat /etc/resolv.conf
```

To see if I got my dns nameserver right... which was odd because the address listed there was different from that displayed in Network Manager and my router itself.

If I use DHCP everything is fine. If I try to use a static IP through the Network Manager, everything is fine, however when I try to use the terminal there must be something I'm missing or doing wrong. Any ideas? What's hilarious is about everything I find is about using ethernet or WPA/WPA2 ..which is a better option, but not an option for me right now.

Thanks

---

### Post by steeldriver on 2013-11-24
First thing, be aware that the /etc/network/interfaces file controls a completely different service from the Network Manager - that's not to say you can't run both, but it often cause problems and a 'real' server certainly wouldn't be running Network Manager concurrently with the older non-desktop networking service. By default, if you define an interface in /etc/network/interfaces then it will disappear from (become 'unmanaged' by) the newer network-manager service.

To restart an upstart service, you can use

```
sudo service *servicename* restart
```

e.g.

```
sudo service networking restart
```

You might want to consider doing

```
sudo service network-manager stop
```

first - NB this will only be temporary (until reboot), if you want to switch over to just /etc/network/interfaces permanently you will need to either uninstall network-manager or prevent it starting (e.g. using a /etc/init/network-manager.override file).

---

