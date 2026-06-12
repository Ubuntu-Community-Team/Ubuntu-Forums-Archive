---
title: "HowTo: Novatel U720 Broadband"
date: 2007-02-20
forum: Outdated Tutorials &amp; Tips
---

### Post by jlc on 2007-02-20
[http://blog.justinconover.com/2007/02/20/novatel-u720-sprint-ubuntu-feisty-herd-4/](http://blog.justinconover.com/2007/02/20/novatel-u720-sprint-ubuntu-feisty-herd-4/)

Load the appropriate modules into the kernel:
```

$ sudo modprobe ppp_async
$ sudo modprobe usbserial product=0×2110 vendor=0×1410

```

To keep these the next time you boot, add them to /etc/modules
```

$ sudo vi /etc/modules

```
```

modprobe ppp_async
modprobe usbserial product=0×2110 vendor=0×1410

```

Once that is done, tail /var/log/messages

Tail the log and Plug in the USB card.
```

$ sudo tail -100f /var/log/messages

Feb 20 15:19:00 kainos kernel: [52240.740000] usb 4-1: airprime converter now attached to ttyUSB0

```

Now we need to add some ppp scripts
```

$ cd /etc/ppp/peers

```

```

$ sudo vi sprint

```

```

#the USB serial device of the EVDO PCMCIA card.
ttyUSB0
#your login information
user YOUR_NUMBER@sprintpcs.com
230400 # speed
#debug
defaultroute # use the cellular network for the default route
usepeerdns # use the DNS servers from the remote network
-detach # keep pppd in the foreground
crtscts # hardware flow control
#lock # lock the serial port
noauth # don’t expect the modem to authenticate itself
connect “/usr/sbin/chat -v -f /etc/ppp/peers/sprint-connect”
disconnect “/usr/sbin/chat -v -f /etc/ppp/peers/sprint-disconnect”

```

```

$ sudo vi sprint-connect

```

```

#time out is 20 because sometimes the card takes a little while to initalize
TIMEOUT 20
ABORT ‘BUSY’
ABORT ‘NO ANSWER’
ABORT ‘NO CARRIER’
SAY ‘Starting Sprint\n’

‘’ ‘AT’
‘OK’ ‘ATQ0V1E0&#8242;
‘OK’ ‘ATZ’
‘OK’ ‘AT&F’
# Dial the number
SAY ‘Connecting…\n’
‘OK’ ‘ATDT#777&#8242;
CONNECT CLIENT

```

```

$ sudo vi sprint-disconnect

```

```

“” “\K”
“” “+++ATH0&#8243;
SAY “Disconnected from Sprint.”

```


Now connect :

```

$ sudo pppd call sprint

```

```

Starting Sprint
Connecting…
Serial connection established.
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB0
not replacing existing default route through eth0
Cannot determine ethernet address for proxy ARP
local IP address 7x.x1x.xx.xxx
remote IP address x.x.x.x
primary DNS address 68.28.90.11
secondary DNS address 68.28.82.11

```

[IMG]http://www.dslreports.com/im/24541035/4198.png[/IMG]

:guitar:

---

### Post by mrjohnston on 2007-04-14
I was wondering if you can maintain high data rates with your modem?  With mine it seems to downgrade to about 500kbps after being used for a while (maybe an hour or so when I test again).

I know airprime is supposed to keep things going smooth, or at least I thought so.  I was wondering if this is something on my computer or a bigger problem in general with the linux support.

---

### Post by kgr132 on 2007-06-29
Great HOWTO. Worked like a charm. Just to add my two cents - I had trouble after copying and pasting directly from my browser into gedit while creating the sprint, sprint-connect and sprint-disconnect files. For some reason, everything that appears as quotation marks on the web page became other odd combinations like two single quotes or apostrophes in row. After going back into the three new files with the editor and replacing all of the "quote like" characters with actual double quotes, it worked perfectly.

---

### Post by krammer on 2008-07-17
I do not receive any feedback after executing the command "sudo pppd call sprint".  How would I change this so I can see that it connects?  Without typing ifconfig afterwards to see that I have gotten an IP?

---

### Post by krammer on 2008-07-17
Nevermind...I didn't have the "-detach" option.

---

### Post by koval.roma on 2008-10-30
Who can help me?
My modem disconect me after 3,4 sec after connect.
I don't know why?

---

