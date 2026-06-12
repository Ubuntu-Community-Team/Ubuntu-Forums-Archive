---
title: "Need elegant bash syntax to test internet connection"
date: 2011-03-04
forum: Programming Talk
---

### Post by Jive Turkey on 2011-03-04
I have a USB wifi adapter that for whatever reason requires periodic resets in order to have a connection.  I have a script that will get it to connect once it goes down (requires resetting the device, not just the ubuntu built in networking commands).  I'd like to make a cron job that will test if the connection works or not and if not run the reconnect commands.

I was thinking of using a "ping|grep" type of thing but I'll bet there is something more elegant to test the connectivity than that.

Any suggestions?

---

### Post by doas777 on 2011-03-04
mabey use an nslookup instead of a ping (tests both connectivity and nameing res at the same time), but I was thinking the same as you.

---

### Post by Jive Turkey on 2011-03-05
nslookup is interesting I played with it a bit but ended up going back to ping.  Anyway, here's what I've got so far.  I'd love to get some feedback on how it could be better.
```
#!/bin/sh
# script to be run in root cron to keep connection established on janky hardware.
# use the command "conmon.sh &>/dev/null"
TESTHOST="192.168.1.1"

TEST=`ping -c1 $TESTHOST|grep "1 packets transmitted"|cut --delimiter="," -f 3`
PASS=" 0% packet loss"
USBUS=`lsusb |grep ZyDAS|cut -c 5-7`
USBDEVICE=`lsusb|grep ZyDAS|cut -c 16-18`

if [ "$TEST" = "$PASS" ]; then
        echo `date +%F` `date +%T` " Connection OK" >>/var/log/conmon.log
else
        /root/usbreset /dev/bus/usb/$USBUS/$USBDEVICE &>>/var/log/conmon.log
        sleep 2
        ifdown wlan0 &>>/var/log/conmon.log
        ifup wlan0 &>>/var/log/conmon.log
        echo    `date +%F` `date +%T` " Connection Reset" >>/var/log/conmon.log
fi

```

---

### Post by kepstein on 2011-11-08
Your script was useful. I had to make some minor modifications for my purposes, but it's simple and effective. Thanks.

---

