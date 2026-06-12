---
title: "Perl ping script"
date: 2008-03-17
forum: Programming Talk
---

### Post by graabein on 2008-03-17
Hello, 

I don't know any perl at all but I need a script to automatically reconnect my wireless network if it's down. I keep loosing wireless network connection when the screensaver on Xubuntu 7.10 kicks in and I don't want to reboot every time this happens. 

:(

Here's what I've got thus far. I'm sick of googling. The examples I've found are mostly unreadable to me so I'm hoping some kind soul can help me out.

Basically I just want to ping google.com and if I get **unknown host** I want to reconnect.

```
#!/usr/local/bin/perl
#
# Auto reconnect 
#

$url = "jasdhfjasdhfasd.no";
$ping = `ping $url`;

if ($ping =~ m/unknown host/)
{
	print "Network is down.\n";
	# insert reconnect command 
}
else
{
	print "Network is up.\n";
	# do nothing
}
```

I can't seem to catch the output from ping when I try a bogus address.

> $ ping jasdhfjasdhfasd.no
ping: unknown host jasdhfjasdhfasd.no

---

### Post by ruy_lopez on 2008-03-17
Basic version
```

use IO::Socket::INET;

$socket = IO::Socket::INET->new("www.google.com:80")
  or die "Couldn't connect to port 80 of google: $!";

```

or

```

$socket = IO::Socket::INET->new("www.google.com:80");
if ($socket) {
       print "net up\n";
       close($socket); # just to be nice.
} else {
       print "net down\n";
}

```

---

### Post by graabein on 2008-03-17
Thanks! Now what command brings my wireless back up?

---

### Post by skeeterbug on 2008-03-17
> **graabein said:**
> Thanks! Now what command brings my wireless back up?

You could probably use ifconfig.

---

### Post by ruy_lopez on 2008-03-17
> **graabein said:**
> Thanks! Now what command brings my wireless back up?

```
ifup ethX
```

Where X is your interface number (it might not be "eth" either). You might have to use 'ifdown ethX' first, in case it's still up, but not responding.

---

### Post by graabein on 2008-03-17
Just like that? **iwconfig** without any parameters tries to reconnect my wireless? What output can I parse to see if it fails or succeeds?

---

### Post by ruy_lopez on 2008-03-17
> **graabein said:**
> Just like that? **iwconfig** without any parameters tries to reconnect my wireless? What output can I parse to see if it fails or succeeds?

if it succeeds, running ifconfig should show the interface. This tests if grep succeeds or fails. (kind of rudimentary)
```

$ret = `ifconfig | grep ethX`;
if ($ret) {
        print "worked\n";
} else {
        print "didn't work\n";
}

```

EDIT: or you could simply rerun the "ping" test.

---

### Post by graabein on 2008-03-18
OK, so something like this then? 

```
$ iwconfig | grep wlan0
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:<ESSID>  Nickname:<Nickname>
```

Thanks for the help guys. I'll add it to the script and see if it compiles. Then I'll try to wait for the net loss and run it!

Hmmm... 
```
$ ifup wlan0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
```

---

### Post by ruy_lopez on 2008-03-18
> **graabein said:**
> 
Hmmm... 
```
$ ifup wlan0
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
```

"ifup/down" needs "sudo".

---

### Post by graabein on 2008-03-18
I figured as much... I want to avoid having to input root password if it's possible so I'll go with just the iwconfig command, but how do I run it from the perl script?

---

### Post by skeeterbug on 2008-03-18
It seemed like this scrpt was going to be run as a cron task. Aren't those run as root anyways? You could also sudo the execution for development.

---

### Post by slavik on 2008-03-18
why do you need Perl for this?

```

#!/bin/bash

ping -c 1 google.com

if [[ $? eq 0 ]]
then
  echo "pinged successfuly!!!"
else
  echo "couldn't ping :("
fi

```

---

### Post by tr333 on 2008-03-18
If you're using perl, you should consider using the [Net::Ping](http://search.cpan.org/~smpeters/Net-Ping-2.35/lib/Net/Ping.pm) module.

```
    use Net::Ping;

    $p = Net::Ping->new();
    print "$host is alive.\n" if $p->ping($host);
    $p->close();
```

I agree with slavik though; why use perl when bash is much simpler for this task.

---

### Post by graabein on 2008-03-19
Don't matter much to me what language I use. Figured I could learn some bash/perl while I solve a continuing problem on this machine... It's not always me that use it, it's usually my mom.

Anyway I ran the commands after I lost connection last night and no go... Here's the output.

```
**$ ping www.google.com:80**
ping: unknown host www.google.com:80
**$ iwconfig**
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:<ESSID>  Nickname:<Nickname>
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=31/100  Signal level=3/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**$ ping www.google.com:80**
ping: unknown host www.google.com:80
**$ sudo ifup wlan0**
ifup: interface wlan0 already configured
**$ sudo ifdown wlan0**
There is already a pid file /var/run/dhclient.wlan0.pid with pid 3821
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:95:64:66:47
Sending on   LPF/wlan0/00:11:95:64:66:47
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
**$ sudo ifup wlan0**
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:95:64:66:47
Sending on   LPF/wlan0/00:11:95:64:66:47
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by tr333 on 2008-03-20
If you're using DHCP then maybe you could either do "sudo dhclient <wireless interface>" or "sudo /etc/init.d/networking restart".

If that doesn't help you connect, then maybe the wireless drivers are buggy.  Check [http://bugs.launchpad.net/ubuntu/](http://bugs.launchpad.net/ubuntu/) for possible bug reports relating to your wireless drivers.

---

### Post by graabein on 2008-03-20
Thank you, I'll be sure to try that next time this happens!

---

### Post by slavik on 2008-03-20
what card is this? if it uses bcm43xx, don't expect it to work great on some cards (there are issues they are working out) ...

---

### Post by graabein on 2008-03-21
No luck with those DHCP commands. 

```
**$ sudo dhclient wlan0**
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:95:64:66:47
Sending on   LPF/wlan0/00:11:95:64:66:47
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5

**$ sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 4776
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:95:64:66:47
Sending on   LPF/wlan0/00:11:95:64:66:47
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
SIOCSIFFLAGS: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set Nickname" (8B1C) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: No such device
SIOCSIFFLAGS: No such device
Listening on LPF/wlan0/00:11:95:64:66:47
Sending on   LPF/wlan0/00:11:95:64:66:47
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: Network is down
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
                                                                         [ OK ]
```

The card is a Texas Instruments ACX 111 54Mbps. I'll look at bug reports when I get the time...

---

