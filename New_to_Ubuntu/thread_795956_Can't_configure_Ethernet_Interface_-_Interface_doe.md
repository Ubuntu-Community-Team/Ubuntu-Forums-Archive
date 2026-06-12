---
title: "Can't configure Ethernet Interface - Interface does not exist"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by ssjwolf on 2008-05-16
Hi,

I'm new to the whole Linux/Ubuntu scene, so please bear with me. I can't seem to configure my Ethernet wired interface in Network Tools. It comes up with an error "The interface does not exist. Check that it is correctly typed and that it is correctly supported by your system."

Apologies for the ignorance.

---

### Post by sab0403 on 2008-05-16
Okey dokey... let's see...

can you go into a terminal and post the output of the following command:

```
sudo ifconfig
```

please?

If you don't know where to find the Terminal, it's under Applications | Accesories (or Tools, I'm not sure since I'm using the spanish version).

---

### Post by crashcoredump on 2008-05-16
Yes, that's right.

The terminal is in Applications --> Accessesories --> Terminal
Ifconfig is in /sbin on Ubuntu, english or spanish versions :)


```
papa@Painhu:~$ whereis ifconfig
ifconfig: **/sbin/ifconfig** /usr/share/man/man8/ifconfig.8.gz
papa@Painhu:~$ 

```

I am pretty sure you do not need sudo to see it, but always a good call.

---

### Post by ssjwolf on 2008-05-16
Thanks for the quick reply; here's the output you asked for.

```
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:50:16:cf  
          inet addr:192.168.1.52  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe50:16cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14412 (14.0 KB)  TX bytes:22136 (21.6 KB)
          Interrupt:20 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1766 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88300 (86.2 KB)  TX bytes:88300 (86.2 KB)
```

---

### Post by crashcoredump on 2008-05-16
Looks good, is this address acquired via DHCP?
192.168.etc?

Check to see if you can ping (from the console) both 127.0.0.1 (your local host address and then your IP (the 192. address) Then your default gateway.
Most likely 192.168.1.1 or 192.168.1.254

Type 

```
papa@Painhu:~$ ping -c5 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.056 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.045 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.044 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.043 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.046 ms

--- 127.0.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.043/0.046/0.056/0.009 ms
papa@Painhu:~$ 

```

Then test the others....

---

### Post by sab0403 on 2008-05-16
Sorry for the delay.

As CCD said, everything looks good, the interface seems configured. Now we gotta check what's going on with Network Tools.

Does the error appear when you select the eth0 interface on the drop-down box? Before? After?

If at all possible, post a screenshot (or link to one).

Thanks.

---

### Post by ssjwolf on 2008-05-16
No the addresses are manually set.

```
ping -c5 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.049 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.031 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.032 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.031 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.033 ms

--- 127.0.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 0.031/0.035/0.049/0.007 ms

ping -c5 192.168.1.52
PING 192.168.1.52 (192.168.1.52) 56(84) bytes of data.
64 bytes from 192.168.1.52: icmp_seq=1 ttl=64 time=0.060 ms
64 bytes from 192.168.1.52: icmp_seq=2 ttl=64 time=0.030 ms
64 bytes from 192.168.1.52: icmp_seq=3 ttl=64 time=0.029 ms
64 bytes from 192.168.1.52: icmp_seq=4 ttl=64 time=0.041 ms
64 bytes from 192.168.1.52: icmp_seq=5 ttl=64 time=0.030 ms

--- 192.168.1.52 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3996ms
rtt min/avg/max/mdev = 0.029/0.038/0.060/0.011 ms

ping -c5 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=4.11 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=1.12 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=1.01 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=64 time=1.02 ms
64 bytes from 192.168.1.254: icmp_seq=5 ttl=64 time=0.894 ms

--- 192.168.1.254 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 0.894/1.633/4.115/1.243 ms

```

Is that all ok? Thanks again.

---

### Post by crashcoredump on 2008-05-16
Great so far!

Can you now ping something external like 4.2.2.2?

Or ping google.com?

---

### Post by ssjwolf on 2008-05-16
> **sab0403 said:**
> Sorry for the delay.

As CCD said, everything looks good, the interface seems configured. Now we gotta check what's going on with Network Tools.

Does the error appear when you select the eth0 interface on the drop-down box? Before? After?

If at all possible, post a screenshot (or link to one).

Thanks.

The error appears when I click on "Configure" after I have chosen eth0 from the drop-down box. Cheers!

---

### Post by ssjwolf on 2008-05-16
I can ping both 4.2.2.2 and google.com with no problems. It seems I am quite connected, but I just can't configure the interface settings.

---

### Post by sab0403 on 2008-05-16
Well, you got me - I get the same exact error.

Are you using Hardy (8.04)? Or another version?

My suggestion would be to configure your interface either with the "Network" option within System | Administration, or via Network Manager (the little applet left of the clock which shows the connection details), though IIRC they both take you to the same place :)

I'll see if a bug report has been filed yet; if not, I'll do it myself.

Thanks for the heads up, and if you need more help we're happy to help.

---

### Post by sab0403 on 2008-05-16
Well, it has indeed been filed as a bug report already. Take a look:

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/184711](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/184711)

In any event, there's no solution yet, so the obvious workarounds are to either follow any of the options I mentioned, or do it manually.

Should you be interested in doing it manually (via console commands), feel free to PM me and I'll guide you through via e-mail; alternatively, search the forums for this or open up a new thread in an appropiate subforum ('Network' comes to mind).

Good luck. and have fun! :popcorn:

---

### Post by ssjwolf on 2008-05-16
Yes I am using the latest, 8.04 just downloaded a couple of days ago. Setting the IPs and the like is easy enough (via your instructions), I was just hoping to find out how to configure the more advanced Ethernet settings like speed duplex and jumbo frames. Though thank you all for the assistance, it is much appreciated. Now I just have to figure out everything else concerning Ubuntu and Linux. :)

---

### Post by niteshifter on 2008-05-16
Hi,

> I was just hoping to find out how to configure the more advanced Ethernet settings like speed duplex and jumbo frames.

Bug or not, and even though I'm running Ubuntu 7.10 I doubt the GUI's network management would display MTU and speed/duplex settings - it hasn't on any *buntu from 5 onward. It would confuse most folks and breed more problems than it could solve.

However all is not lost, this is GNU/Linux after all, for pretty much anything networking related there's a command-line tool for the job. So here you go:

MTU - use ifconfig like this:
```
sudo ifconfig eth0 mtu 1200
```

Speed / duplex and assorted hardware related stuff use ethtool and mii-tool commands. They present a rich (very!) set of ways and means of configuring your hardware, to many to give here. They should already be installed in your system. To see what they can do look at the man pages on them:
```
man ethtool
man mii-tool
```

Google will be your friend here as well. Speed up that search on google for things Linux related by using this URL: [http://www.google.com/linux](http://www.google.com/linux)

But I gotta ask (and say): Given that for 99.9% of the hardware and usage patterns with desktops (vs server) the "default" settings work very well, why would you wish to change them? You've got my curiosity up ... (ignore the question if are setting up a server).

---

### Post by ssjwolf on 2008-05-16
Thanks for the info, I'll have to play around with it later on.

> **niteshifter said:**
> But I gotta ask (and say): Given that for 99.9% of the hardware and usage patterns with desktops (vs server) the "default" settings work very well, why would you wish to change them? You've got my curiosity up ... (ignore the question if are setting up a server).

Well it started when I had upgraded most of my home network to Gigabit standards. It was annoying the hell out of me that I couldn't get Gigabit speeds, heck I could hardly reach 100Mbit/s. I just wanted to play around with the settings a bit more before I start ruling hardware faults. :cool:

---

### Post by niteshifter on 2008-05-16
Hi,

Ah, got it. Don't be disappointed if you can't get screaming high rates: There's a difference between what a chip set is capable of and what an OS can drive it at. Desktops differ from pure servers, the CPU(s) are "busier" in a desktop OS (running the GUI, mail client, assorted deamons, etc), whereas a server install is usually tasked with the minimal overhead needed so as to give more CPU to networking. Your machine's structure will also matter (FSB speed and RAM speed in particular). Tweaking either type is fun, you've a capable kernel and the tools to do it with ... enjoy!

---

